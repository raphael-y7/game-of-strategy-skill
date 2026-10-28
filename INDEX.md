# Skill 地图 — 策略博弈

《策略博弈》共蒸馏出 14 张能力卡：8 张晋级为可独立触发的 skill，6 张留在路由入口内按需加载。本文件是这张地图的全量索引，列出每张卡的标识、去向，以及卡与卡之间的 `also_read` 依赖关系。

## 能力总表

| capability_id | slug | 中文标题 | 重要度 | 去向 |
|---|---|---|---|---|
| `celue-00-source-router` | `source-router` | 博弈分类六维度与来源路由入口 | high | promoted → 独立 skill |
| `celue-01-event-game-tree-rollback` | `event-game-tree-rollback` | 事件博弈树逆推 | high | promoted → 独立 skill |
| `celue-02-payoff-table-nash-equilibrium` | `payoff-table-nash-equilibrium` | 支付表与纳什均衡定位 | high | promoted → 独立 skill |
| `celue-03-cooperation-threshold-repeat-game` | `cooperation-threshold-repeat-game` | 合作临界值计算（重复博弈与瓦解时点） | high | promoted → 独立 skill |
| `celue-04-mixed-strategy-randomization` | `mixed-strategy-randomization` | 混合策略与随机化执行 | medium | router → 路由入口 |
| `celue-05-credibility-signaling-filter` | `credibility-signaling-filter` | 信号与话语可信度判定 | high | promoted → 独立 skill |
| `celue-06-focal-point-selection` | `focal-point-selection` | 聚点与关键点位选择 | medium | router → 路由入口 |
| `celue-07-strategic-moves-credibility` | `strategic-moves-credibility` | 策略性行动与置信度评估 | high | promoted → 独立 skill |
| `celue-08-collective-action-stampede` | `collective-action-stampede` | 集体行动与踩踏（多人博弈判据） | high | router → 路由入口 |
| `celue-09-brinkmanship-dual-threshold` | `brinkmanship-dual-threshold` | 边缘政策概率威胁双阈值 | medium | router → 路由入口 |
| `celue-10-winner-curse-auction-bidding` | `winner-curse-auction-bidding` | 赢家诅咒与拍卖出价 | high | promoted → 独立 skill |
| `celue-11-batna-negotiation` | `batna-negotiation` | BATNA谈判分析 | medium | router → 路由入口 |
| `celue-12-strategic-crowding-ess` | `strategic-crowding-ess` | 策略拥挤与抱团瓦解（进化博弈判据） | high | promoted → 独立 skill |
| `celue-13-mechanism-design-incentives` | `mechanism-design-incentives` | 机制设计与激励契约分析 | medium | router → 路由入口 |

> 去向为 `promoted → 独立 skill` 的卡在 `pack/` 下各有一个同名目录，可被 skill 列表直接命中；
> 去向为 `router → 路由入口` 的卡只存在于入口的 `references/capabilities/` 里，经路由入口访问。

## 依赖关系

下表是 `verified.yaml` 中每张卡的 `also_read` 字段，表示“主卡之外建议补读的卡”。
它是补读建议，不是前置条件——任何一张卡都能单独使用。

| 主卡 | 补读（also_read） |
|---|---|
| `source-router` — 博弈分类六维度与来源路由入口 | `event-game-tree-rollback`、`payoff-table-nash-equilibrium`、`credibility-signaling-filter`、`strategic-crowding-ess` |
| `event-game-tree-rollback` — 事件博弈树逆推 | `source-router`、`brinkmanship-dual-threshold`、`cooperation-threshold-repeat-game`、`strategic-moves-credibility` |
| `payoff-table-nash-equilibrium` — 支付表与纳什均衡定位 | `source-router`、`mixed-strategy-randomization`、`focal-point-selection`、`collective-action-stampede` |
| `cooperation-threshold-repeat-game` — 合作临界值计算（重复博弈与瓦解时点） | `event-game-tree-rollback`、`strategic-crowding-ess`、`collective-action-stampede`、`payoff-table-nash-equilibrium` |
| `mixed-strategy-randomization` — 混合策略与随机化执行 | `payoff-table-nash-equilibrium`、`strategic-crowding-ess`、`brinkmanship-dual-threshold` |
| `credibility-signaling-filter` — 信号与话语可信度判定 | `strategic-moves-credibility`、`source-router`、`mechanism-design-incentives`、`winner-curse-auction-bidding` |
| `focal-point-selection` — 聚点与关键点位选择 | `payoff-table-nash-equilibrium`、`collective-action-stampede`、`strategic-crowding-ess` |
| `strategic-moves-credibility` — 策略性行动与置信度评估 | `credibility-signaling-filter`、`brinkmanship-dual-threshold`、`batna-negotiation`、`mechanism-design-incentives` |
| `collective-action-stampede` — 集体行动与踩踏（多人博弈判据） | `strategic-crowding-ess`、`cooperation-threshold-repeat-game`、`payoff-table-nash-equilibrium`、`focal-point-selection` |
| `brinkmanship-dual-threshold` — 边缘政策概率威胁双阈值 | `strategic-moves-credibility`、`event-game-tree-rollback`、`batna-negotiation`、`mixed-strategy-randomization` |
| `winner-curse-auction-bidding` — 赢家诅咒与拍卖出价 | `credibility-signaling-filter`、`payoff-table-nash-equilibrium`、`mechanism-design-incentives`、`batna-negotiation` |
| `batna-negotiation` — BATNA谈判分析 | `strategic-moves-credibility`、`winner-curse-auction-bidding`、`brinkmanship-dual-threshold`、`event-game-tree-rollback` |
| `strategic-crowding-ess` — 策略拥挤与抱团瓦解（进化博弈判据） | `collective-action-stampede`、`cooperation-threshold-repeat-game`、`mixed-strategy-randomization`、`focal-point-selection` |
| `mechanism-design-incentives` — 机制设计与激励契约分析 | `credibility-signaling-filter`、`strategic-moves-credibility`、`winner-curse-auction-bidding`、`payoff-table-nash-equilibrium` |

被引用次数最多的卡（跨卡枢纽）：

- `payoff-table-nash-equilibrium` — 支付表与纳什均衡定位（被 7 张卡列为补读）
- `strategic-moves-credibility` — 策略性行动与置信度评估（被 5 张卡列为补读）
- `strategic-crowding-ess` — 策略拥挤与抱团瓦解（进化博弈判据）（被 5 张卡列为补读）
- `event-game-tree-rollback` — 事件博弈树逆推（被 4 张卡列为补读）
- `credibility-signaling-filter` — 信号与话语可信度判定（被 4 张卡列为补读）

## 加载顺序

1. **先读入口 SKILL.md**。single 模式读 `single/game-of-strategy-skill/SKILL.md`；pack 模式读 `pack/game-of-strategy-skill-router/SKILL.md`。入口里有触发条件、核心原则、路由表与加载规则，是唯一的必经环节。
2. **按路由表加载 1 张能力卡**。用路由表的“用户意图”列命中主卡；single 模式的路径是 `references/capabilities/<slug>.md`，pack 模式里已晋级的卡直接读它自己的 `SKILL.md`。
3. **跨域时最多补读 1 张**。依据上表的 `also_read` 选补读卡，总计不超过 2 张能力卡——一次分析里堆三张以上，判断会互相污染。
4. **概览与术语类问题不加载能力卡**。书名/章节/整书概览读 `references/overview.md`，术语读 `references/glossary.md`，只要规则速查读 `references/cheatsheet.md`。
5. **路由表与 `capability-index.md` 都命中不了的意图**，明确告知超出本书范围，不要硬套。

## 两种打包模式下的入口数量

| | 入口数 | 具体入口 |
|---|---|---|
| single | 1 | `game-of-strategy-skill`（内含全部 14 张卡） |
| pack | 9 | `game-of-strategy-skill-router`（路由入口，内含全部 14 张卡）+ 8 个晋级独立 skill |

pack 里被晋级为独立 skill 的 8 张卡：

- `source-router` — 博弈分类六维度与来源路由入口
- `event-game-tree-rollback` — 事件博弈树逆推
- `payoff-table-nash-equilibrium` — 支付表与纳什均衡定位
- `cooperation-threshold-repeat-game` — 合作临界值计算（重复博弈与瓦解时点）
- `credibility-signaling-filter` — 信号与话语可信度判定
- `strategic-moves-credibility` — 策略性行动与置信度评估
- `winner-curse-auction-bidding` — 赢家诅咒与拍卖出价
- `strategic-crowding-ess` — 策略拥挤与抱团瓦解（进化博弈判据）

留在路由入口 `references/capabilities/` 下的 6 张卡：

- `mixed-strategy-randomization` — 混合策略与随机化执行
- `focal-point-selection` — 聚点与关键点位选择
- `collective-action-stampede` — 集体行动与踩踏（多人博弈判据）
- `brinkmanship-dual-threshold` — 边缘政策概率威胁双阈值
- `batna-negotiation` — BATNA谈判分析
- `mechanism-design-incentives` — 机制设计与激励契约分析
