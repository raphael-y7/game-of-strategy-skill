# Stage 4 压力测试摘要

本文件是《策略博弈（第4版）》skill 包在 cangjie-skill v2.5 流水线阶段 4（触发与输出测试）的摘要，材料取自归档的 `审计过程/stage4-pressure-test.md`、`审计过程/PIPELINE_STATE.md`，以及仓库内 10 个 `test-prompts.json` 的实际清点结果。

## 测试范围

**被测对象**：14 张能力卡，编译为两种打包模式。

- single 模式：1 个入口 `game-of-strategy-skill`，14 张卡全部在它的 `references/capabilities/` 下
- pack 模式：9 个入口（1 个路由入口 `game-of-strategy-skill-router` + 8 个已晋级独立 skill），其中 6 张未晋级的卡仍在 router 的 `references/` 里

**test-prompts 文件分布**（实测）：

| 位置 | 文件数 | 用例数 | 说明 |
|---|---|---|---|
| `single/game-of-strategy-skill/test-prompts.json` | 1 | 7 | 入口级用例 |
| `pack/game-of-strategy-skill-router/test-prompts.json` | 1 | 7 | 路由入口用例，内容与 single 入口用例相同 |
| `pack/<其余 8 个 skill>/test-prompts.json` | 8 | 48 | 每个晋级 skill 6 条 |
| **合计** | **10** | **62** | |

每份文件的用例数为 6–7 条（两个入口各 7 条，其余 8 个 skill 各 6 条）。

**覆盖类型**（按 `type` 字段实测统计，62 条）：

| 类型 | 条数 | 覆盖内容 |
|---|---|---|
| `should_trigger` | 30 | 该触发时是否触发，以及是否路由到正确的能力卡 |
| `should_not_trigger` | 20 | 诱饵题：纯技术指标计算、结构已明确该直达某张卡（入口不应吞单）等 |
| `edge_case` | 12 | 个人决策 vs 博弈、要素缺失时应追问而不是代填 |
| `output_case` | 0 | **本包没有输出质量类用例**，覆盖集中在"该不该触发 / 该路由到哪张卡" |

## 结构检查

以下为本次对仓库现状的实测结果，不是转述：

- **JSON 可解析性**：仓库内 10 个 `test-prompts.json` 全部通过 `json.load` 解析，0 个损坏；按文件内 `test_cases` 计数合计 62 条。
- **SKILL.md frontmatter**：single 入口 1 个 + pack 9 个，共 10 个 `SKILL.md` 全部以 `---` 开头且含 `name` / `description` 字段，10/10 合规；且每个 `name` 等于其所在目录名。
- **六段完整性**：`bundle/cards/` 下 14 张能力卡全部含 `R 原文` / `I 自述` / `A1 案例` / `A2 触发` / `E 执行` / `B 边界` 六段，14/14 齐全；`single/` 与 `pack/game-of-strategy-skill-router/` 的 `references/capabilities/` 各 14 张，数量一致。
- **引用可回查**：R 段原文均附章节号与合并转写稿行号（`L****`），可回查原书。
- **未做的检查**：没有对 62 条用例逐条执行并记录 pass/fail 的机器评分（见下节）。

## 结果

- **skills**: 14 张能力卡（8 promoted + 6 router；对应 9 个可发现 skill 目录）
- **test_json**: 10 个 `test-prompts.json`、62 条用例，全部可解析
- **通过情况**：本包未附带逐条用例的评分记录（没有 `test-results*.json`、没有逐条 pass/fail 日志），因此 62 条用例本身没有跑分数据；`test-prompts.json` 记录的是用例与预期行为（`expected_behavior`），不是评分结果。

归档里附带的 Stage 4 压力测试报告记录的是**能力卡级别**的压力测试，如实摘录如下：

| 轮次 | 结果 | 内容 |
|---|---|---|
| 首轮（修复前） | 12/14 = 85.7% | 触发/可达 12 通过；执行测试 4/4 通过；近邻负例 pass。FAIL 2 项：`celue-12` 卡文件缺失致路由指针悬空、编译阻断；`celue-13` 卡文件六段完整但 `celue-00` 路由表无对应项、经入口不可达 |
| 回炉修复 | — | `celue-12` 补卡（六段，R 引文 149 字）；`celue-00` 路由表补 `celue-13` 与相关触发词；`celue-13` B 段过时陈述更正 |
| 回炉复验 | 1/1 | `celue-12` 触发测试 6/6，代表任务复算 x\\*=2/3 与公式族旁验全部与原书一致 |
| 最终结论 | **14/14 全部通过** | promoted 8（00/01/02/03/05/07/10/12）+ router 6（04/06/08/09/11/13）；执行测试 4/4 + 回炉复验 1/1 |

**方法限制（原报告自述，一并保留）**：触发判定为主流程规格符合性判卷，**未使用独立盲测 sub-agent**，可信度低于独立盲测；执行测试为测试官实际演算（新任务，非复述原书例题），数值全程留痕。原报告另列两条非阻断遗留建议：router 卡代表任务执行补测、触发判定后续用独立盲测复验。

## 可接入 darwin-skill 的后续动作

1. **把这 62 条用例当回归样本**：各 skill 目录下的 10 个 `test-prompts.json` 已是 darwin 兼容格式（`skill` / `version` / `test_cases[]`，每条含 `id` / `type` / `prompt` / `expected_behavior` / `notes`），可直接作为 skill 每次改版后的触发回归基线；`expected_behavior` 里写明了"应路由到哪张卡"，可直接判路由是否漂移。
2. **补齐 output_case**：当前 0 条输出质量用例。执行测试的 4 个演算样本（`celue-01` 减持公告、`celue-02` 券商价格战、`celue-03` 联盟临界收益率、`celue-10` 打新出价）已有完整数值链，可转成带期望数值的 output_case。
3. **把两条首轮 FAIL 固化为常驻用例**：`celue-12` 卡文件缺失、`celue-13` 经路由不可达——这两类"路由指针悬空 / 入口不可达"问题适合做结构性断言，比触发用例更早暴露编译问题。
4. **补独立盲测**：现报告用的是规格符合性判卷，建议用独立 sub-agent 对同一批 prompt 复判，对比命中率；差异大的用例优先复核。
5. **补 router 卡执行测试**：6 张 router 卡（04/06/08/09/11/13）目前只有触发与可达性结论，没有代表任务演算记录，接入前应补。
