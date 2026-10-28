<h1 align="center">策略博弈 Skill</h1>

<p align="center">中文 | <a href="README.en.md">English</a></p>

一套可直接使用的 AI skill 工具包——把阿维纳什·迪克西特、苏珊·斯克丝与戴维·赖利《策略博弈》里的博弈分析方法，蒸馏成 14 张可单独触发、也可组合调用的能力卡。

它不是原书摘要，也不是读后感，而是把书中可复用的方法论拆成可触发、可执行、可测试的 skill 模块。

## 这套 skills 能解决什么问题

- 利好消息落地反而大跌，分不清这是"市场错了"还是双方各自理性、稳定地锁在一个双输格子，也说不清背离会往哪一格收敛
- 行业价格战、扩产竞赛、券商降佣打到成本线以下还在打，看不出这是囚徒困境型的支付结构，也判断不了谁会先眨眼、默契还能撑多久
- 抱团、联盟、限售解禁、对赌到期这类有明确终点的合作，说不清瓦解的临界收益率和时点，只能凭感觉猜"快到头了"
- 研报、荐股、IR 沟通、管理层回购与业绩指引摆在面前，分不清哪句是零成本的废话、哪个是真正有差异成本的可信信号
- 打新、定增询价、大宗折价接货、并购套利，常常是中标之后才发现坏消息，缺一道报价前的逆向选择校验
- 央行前瞻指引、大股东增持承诺、政策威慑，评不出这份承诺的置信度，也分不清承诺、威胁、许诺在可观察与不可逆上的差别

## 蒸馏了什么

14 张能力卡，按"先分类、再解法、后信息与结构"的顺序组织。其中 8 张晋级为可独立触发的 skill，6 张留在路由入口内按需加载（去向逐张见 [INDEX.md](./INDEX.md)）：

- **入口与分类**：`source-router`（博弈分类六维度与来源路由入口）
- **基础解法**：`event-game-tree-rollback`（事件博弈树逆推）、`payoff-table-nash-equilibrium`（支付表与纳什均衡定位）、`mixed-strategy-randomization`（混合策略与随机化执行）、`focal-point-selection`（聚点与关键点位选择）
- **信息与可信度**：`credibility-signaling-filter`（信号与话语可信度判定）、`strategic-moves-credibility`（策略性行动与置信度评估）
- **合作与多人结构**：`cooperation-threshold-repeat-game`（合作临界值计算：重复博弈与瓦解时点）、`collective-action-stampede`（集体行动与踩踏：多人博弈判据）、`strategic-crowding-ess`（策略拥挤与抱团瓦解：进化博弈判据）
- **规则与场景定价**：`mechanism-design-incentives`（机制设计与激励契约分析）、`brinkmanship-dual-threshold`（边缘政策概率威胁双阈值）、`winner-curse-auction-bidding`（赢家诅咒与拍卖出价）、`batna-negotiation`（BATNA 谈判分析）

## 两种打包模式：single 与 pack

同一套 14 张能力卡，按两种粒度各编译了一次。两者内容完全相同，区别只在"agent 能看到几个入口"。

| | single（单一入口） | pack（compact pack，多入口） |
|---|---|---|
| 可发现入口 | **1 个**：`game-of-strategy-skill` | **9 个**：1 个来源路由入口 + 8 个已晋级独立 skill |
| 14 张能力卡放在哪 | 全部在入口的 `references/capabilities/` 里，由入口按路由表按需加载 1–2 张 | 8 张卡各自独立成 skill；其余 6 张仍在 router 的 `references/` 里 |
| 触发方式 | 只有入口的 description 参与匹配，进入后靠路由表分流 | 8 个高频能力可被 description 直接命中，少一跳 |
| 升级维护 | 替换 1 个目录 | 替换 9 个目录 |

pack 里被晋级为独立 skill 的 8 张卡：

- `source-router` — 博弈分类六维度与来源路由入口
- `event-game-tree-rollback` — 事件博弈树逆推
- `payoff-table-nash-equilibrium` — 支付表与纳什均衡定位
- `cooperation-threshold-repeat-game` — 合作临界值计算
- `credibility-signaling-filter` — 信号与话语可信度判定
- `strategic-moves-credibility` — 策略性行动与置信度评估
- `winner-curse-auction-bidding` — 赢家诅咒与拍卖出价
- `strategic-crowding-ess` — 策略拥挤与抱团瓦解

未晋级的 6 张卡（`mixed-strategy-randomization`、`focal-point-selection`、`collective-action-stampede`、`brinkmanship-dual-threshold`、`batna-negotiation`、`mechanism-design-incentives`）留在 router 的 `references/` 里，经路由入口访问，能力一张不少。

### 该装哪一种

按你的工作方式选，**只装一种**：

| 你的工作方式 | 推荐 | 原因 |
|---|---|---|
| 用 DSH / Codex / Claude Code 等有 skills 目录，希望列表干净 | single | 只占 1 个入口，能力一张不少 |
| 日常问题高度集中在"这消息能不能信 / 这份承诺算不算数 / 该出多少价 / 这个风格挤不挤" | pack | 这几类正是被晋级的独立 skill，能直接命中 |
| 要分发给多个 agent 或团队，各自按需取用 | pack | 可以只装其中几个独立 skill，不必整包 |
| 只想装一次、不想维护多个目录 | single | 升级时只替换 1 个目录 |

> 两版由同一个 Bundle 编译，能力内容一致。**同时安装会重复触发**，请只装一种。

## 效果示例

### 示例 1：价格战打到成本线以下，为什么停不下来

**用户问题**

"两家券商佣金战打到成本线以下了，明摆着双输，为什么就是停不下来？我该不该跟着降？"

**skill 如何判断**

- 先过 `source-router` 六问：行动时序是同时（各家在同一时点定费率，看不到对手本轮选择）→ 路由到 `payoff-table-nash-equilibrium`
- 画 2×2 支付表，先声明口径：行参与人支付在前、列参与人在后，单位与方向必须同口径
- 占优减法：如果"降佣"在对手两种选择下都更优，它就是严格占优策略
- 最优反应逐格双向圈定，双重圈格即纯策略纳什均衡；再检查这个均衡格是不是比"都不降"更差的双输格
- 若中间用过带等号的弱占优剔除，必须逐格复查——书里明确警告弱占优剔除可能漏掉均衡

**最终回答示例**

> 结论：这是囚徒困境型的支付结构。"双输"不是市场失灵，而是双方各自理性的稳定落点。书里的标准演示是国会 vs 美联储（表4-5）：给定任一利率，国会的最优反应都是赤字（4>3、2>1）；给定任一财政政策，美联储的最优反应都是高利率（4>3、2>1）；双重圈唯一的均衡是（赤字, 高利率）=(2,2)，而（平衡, 低利率）=(3,4) 对双方都更好——理性个体可以稳定地锁在次优格。套到佣金战：只要"降佣"在你的支付表里是占优策略，你单方面不降就是在让份额，靠默契喊停没有用。
>
> 两件事得由你补。一是支付数值：书里只给教学数字，你这张表的份额流失、费率、单位成本都要自己估；估不出来就别硬填，改输出定性方向（"降佣是/不是占优策略"），不要伪造数字。二是如果你用了带等号的剔除（比如"持平先按不降处理"），记得逐格复查——书里表4-6 罗伊娜-科林博弈就是弱占优剔除漏掉两个均衡的反例，横盘对峙这种平局状态恰恰最容易被剔掉。
>
> 还有一条边界：支付表按净期望收益算，尾部损失要写进去。书里克雷普斯博弈说明，只要存在极小概率的灾难格（书中量级是 1/1009），"期望值占优"的结论就会翻转，爆仓线必须进表。

### 示例 2：定增询价，按自己的合理价报就一定赚吗

**用户问题**

"这家公司定增询价，我按自己算的合理价 20 元报，中了就是赚吧？"

**skill 如何判断**

- 先判型：这是共同价值（标的对所有人是同一个真值，各家只有带噪声的估计）还是私人价值（自用协同为主）——只有共同价值才启动诅咒修正
- 两问强制校验：① 按我掌握的信息，我愿意出这个价吗？② 已知没有别人愿意出到这个价、我才买得到，我还愿意吗？第二问必须显式作答
- 条件期望复算：出价 b 被接受 → 真实价值落在 0 到 b 之间 → 条件均值 b/2 → 再乘你的经营提升系数 g；g×(b/2)<b 即 g<2 时，任何正出价中标都必亏
- 机制映射：定增询价近似一价机制，应按低于真实估值的价格申报；集合竞价近似二价机制，按真实估价报价才是占优策略
- 汇总输出：修正后的报价上限 + 下调依据 + 机制对应策略一句话

**最终回答示例**

> 先别按 20 元报。"中了就赚"这个判断默认了你的估值是准的，而共同价值拍卖里中标本身就是一条坏消息：你能赢，说明所有对手的估计都比你低，你的估计正好是最乐观的那一个。书里塔吉可并购例算得很干净——出价 b 被接受，说明目标公司价值均匀分布在 0 到 b 之间，条件均值就是 b/2；就算你的经营能提升 50%，条件价值也只有 1.5×(b/2)=0.75b，小于 b。也就是说，只有在不值得赢的时候你才会赢。
>
> 按流程走：先答第二问——"已知没人愿意出到 20 元我才买得到，我还愿意吗"；再用你自己的提升系数 g 算 g×(b/2) 是否大于 b。定增询价是一价机制，正确动作是低于真实估值申报，而不是报满。
>
> 这里必须如实说明：书里只给了"向下调整"的方向和 g<2 这个判据，没有给出"该下调多少"的闭式解——能力卡的边界段自己把这条列为盲点。下调幅度需要你自定义并写进预案，别假装书里有一个现成公式。另外油田例的 ±1 亿均匀误差、10 家投标者都是教学设定，真实市场的估计误差是相关的（大家看同一份研报），所以实际下调幅度通常要比均匀分布的算例更大。书里那组 MBA 实验（69 人中只有 5 人持续下调出价）也提醒：知道诅咒存在，不等于能执行修正。

## 这些 skill 是怎么生成出来的

这套 skill 使用 **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)** 的 RIA-TV++ 流水线生成，整个流程分六个阶段：

1. **整书理解（Adler 分析）**——用 Mortimer Adler 的分析阅读法，对全书做结构、解释、批判、应用四步拆解
2. **并行提取**——同时派多个专项提取器（框架、原则、案例、反例、术语），从原文中提取候选方法论单元
3. **三重验证筛选**——每个候选必须通过三项检验：书内至少有 2 处独立佐证（跨域）、能回答书中未明说的新问题（预测力）、不是常识（独特性）
4. **RIA++ 构造**——按 R（原文引用）/ I（用自己的话重写）/ A1（书中案例）/ A2（未来触发场景）/ E（可执行步骤）/ B（边界与盲点）六个维度结构化
5. **Zettelkasten 链接**——找出能力卡之间的依赖、对比、组合关系，生成能力索引与路由表
6. **触发与输出测试**——为每张卡设计触发盲测题（含诱饵题：该触发时要触发，不该触发时要沉默）与输出评测场景，未通过的卡回炉重做，回炉后再做回归验证

本书的几处特殊处理也影响蒸馏结果：原书没有直接的股票市场案例（最接近市场的只有拍卖章与谈判章），"博弈概念 → 股市场景"的映射由能力卡自行构建并自设参数；第 15 章投票制度与第 12 章进化博弈的生物学数学细节只取思想内核，不做计算；第 13 章机制设计属书级裁剪决策，只以"信号可信度判定"卡的甄别半边间接覆盖。

## 测试与验证

`evals/` 下是本仓库连生成过程一起发布的触发测试用例，按 skill 分文件，共 9 个文件、55 条用例：

- **should_trigger 27 条**：该触发时是否触发，以及是否路由到正确的能力卡
- **should_not_trigger 18 条**：诱饵题——纯技术指标计算、结构已明确该直达某张卡（入口不应吞单）等，不该触发时要沉默
- **edge_case 10 条**：个人决策 vs 博弈、要素缺失时该追问而不是代填

这些文件记录的是用例与预期行为（`expected_behavior`），不是评分结果。本仓库不附评分记录文件，用例可以自己拿去跑。

## 仓库结构

```text
game-of-strategy-skill/
├── README.md                      ← 你正在看的
├── README.en.md                   ← English version
├── LICENSE                        ← MIT
├── INDEX.md                       ← skill 地图：14 张卡的去向与依赖关系
├── BOOK_OVERVIEW.md               ← 整书理解（Adler 四步拆解，阶段 0 产出）
├── verified.md                    ← 47 条候选单元的三重验证结论（35 通过 / 12 被拒）
├── bundle/                        ← 编译本仓库所用的 Bundle（审计材料）
│   ├── verified.yaml              ← 14 张卡的规范单元（slug / 意图 / 去向 / 晋级门）
│   ├── cards/                     ← 14 张能力卡源文件
│   │   ├── celue-00-source-router.md
│   │   ├── celue-01-event-game-tree-rollback.md
│   │   ├── celue-02-payoff-table-nash-equilibrium.md
│   │   ├── celue-03-cooperation-threshold-repeat-game.md
│   │   ├── celue-04-mixed-strategy-randomization.md
│   │   ├── celue-05-credibility-signaling-filter.md
│   │   ├── celue-06-focal-point-selection.md
│   │   ├── celue-07-strategic-moves-credibility.md
│   │   ├── celue-08-collective-action-stampede.md
│   │   ├── celue-09-brinkmanship-dual-threshold.md
│   │   ├── celue-10-winner-curse-auction-bidding.md
│   │   ├── celue-11-batna-negotiation.md
│   │   ├── celue-12-strategic-crowding-ess.md
│   │   └── celue-13-mechanism-design-incentives.md
│   └── book/
│       ├── overview.md            ← 整书概览
│       └── glossary.md            ← 术语表
├── single/                        ← 单一入口模式
│   └── game-of-strategy-skill/
│       ├── SKILL.md               ← 入口：触发条件 + 路由表 + 加载规则
│       ├── BUILD_MANIFEST.json    ← 编译清单与文件哈希
│       └── references/
│           ├── overview.md        ← 整书概览
│           ├── capability-index.md  ← 完整意图与关键词索引
│           ├── cheatsheet.md      ← 决策规则速查
│           ├── glossary.md        ← 术语表
│           └── capabilities/      ← 14 张能力卡
│               ├── source-router.md
│               ├── event-game-tree-rollback.md
│               ├── payoff-table-nash-equilibrium.md
│               ├── cooperation-threshold-repeat-game.md
│               ├── mixed-strategy-randomization.md
│               ├── credibility-signaling-filter.md
│               ├── focal-point-selection.md
│               ├── strategic-moves-credibility.md
│               ├── collective-action-stampede.md
│               ├── brinkmanship-dual-threshold.md
│               ├── winner-curse-auction-bidding.md
│               ├── batna-negotiation.md
│               ├── strategic-crowding-ess.md
│               └── mechanism-design-incentives.md
├── pack/                          ← 多入口模式（compact pack）
│   ├── BUILD_MANIFEST.json        ← 编译清单与文件哈希
│   ├── capability-destinations.json  ← 14 张卡的晋级去向映射
│   ├── game-of-strategy-skill-router/
│   │   ├── SKILL.md               ← 来源路由入口
│   │   └── references/            ← 14 张卡 + 索引，供 router 内部调用
│   │       ├── overview.md
│   │       ├── capability-index.md
│   │       ├── cheatsheet.md
│   │       ├── glossary.md
│   │       └── capabilities/      ← 14 张能力卡
│   │           ├── source-router.md
│   │           ├── event-game-tree-rollback.md
│   │           ├── payoff-table-nash-equilibrium.md
│   │           ├── cooperation-threshold-repeat-game.md
│   │           ├── mixed-strategy-randomization.md
│   │           ├── credibility-signaling-filter.md
│   │           ├── focal-point-selection.md
│   │           ├── strategic-moves-credibility.md
│   │           ├── collective-action-stampede.md
│   │           ├── brinkmanship-dual-threshold.md
│   │           ├── winner-curse-auction-bidding.md
│   │           ├── batna-negotiation.md
│   │           ├── strategic-crowding-ess.md
│   │           └── mechanism-design-incentives.md
│   ├── source-router/
│   │   └── SKILL.md
│   ├── event-game-tree-rollback/
│   │   └── SKILL.md
│   ├── payoff-table-nash-equilibrium/
│   │   └── SKILL.md
│   ├── cooperation-threshold-repeat-game/
│   │   └── SKILL.md
│   ├── credibility-signaling-filter/
│   │   └── SKILL.md
│   ├── strategic-moves-credibility/
│   │   └── SKILL.md
│   ├── winner-curse-auction-bidding/
│   │   └── SKILL.md
│   └── strategic-crowding-ess/
│       └── SKILL.md
└── evals/                         ← 触发测试用例（55 条）
    ├── game-of-strategy-skill.json
    ├── source-router.json
    ├── event-game-tree-rollback.json
    ├── payoff-table-nash-equilibrium.json
    ├── cooperation-threshold-repeat-game.json
    ├── credibility-signaling-filter.json
    ├── strategic-moves-credibility.json
    ├── winner-curse-auction-bidding.json
    └── strategic-crowding-ess.json
```

## 如何使用

先把仓库克隆下来：

```bash
git clone https://github.com/raphael-y7/game-of-strategy-skill.git
```

### 装 single（推荐先试这个）

```bash
# macOS / Linux
cp -r game-of-strategy-skill/single/game-of-strategy-skill ~/.agents/skills/
```

```powershell
# Windows
Copy-Item -Recurse .\game-of-strategy-skill\single\game-of-strategy-skill "$env:USERPROFILE\.agents\skills\"
```

### 装 pack

只复制含 `SKILL.md` 的目录，不要把 `pack/` 下的两个 json 一起拷进 skills 目录：

```bash
# macOS / Linux
cd game-of-strategy-skill/pack
cp -r game-of-strategy-skill-router \
      source-router \
      event-game-tree-rollback \
      payoff-table-nash-equilibrium \
      cooperation-threshold-repeat-game \
      credibility-signaling-filter \
      strategic-moves-credibility \
      winner-curse-auction-bidding \
      strategic-crowding-ess ~/.agents/skills/
```

```powershell
# Windows
$pack = ".\game-of-strategy-skill\pack"
$dest = "$env:USERPROFILE\.agents\skills"
@('game-of-strategy-skill-router','source-router','event-game-tree-rollback','payoff-table-nash-equilibrium','cooperation-threshold-repeat-game','credibility-signaling-filter','strategic-moves-credibility','winner-curse-auction-bidding','strategic-crowding-ess') |
  ForEach-Object { Copy-Item -Recurse -LiteralPath (Join-Path $pack $_) -Destination $dest }
```

> `~/.agents/skills` 是 DSH 的 skill 目录；用别的 agent 时换成它自己的 skills 目录即可（例如 Claude Code 是 `~/.claude/skills`）。

### 怎么确认装好了

装完问一句"这家公司定增询价，我该报多少价"，看 agent 是否直接进入 `winner-curse-auction-bidding` 的两问校验与条件期望复算，而不是给你一段泛泛的估值分析。装的是 single 时，它会先读入口再按路由表进能力卡；装的是 pack 时，对应能力会被直接命中。

## 来源

- 《策略博弈》阿维纳什·迪克西特、苏珊·斯克丝、戴维·赖利 著

## 声明

本仓库只发布蒸馏后的 skill、索引与规则速查材料，不包含原书 PDF、EPUB、OCR 文件、截图或全书转写稿。能力卡中出现的原文引用仅用于标注方法论出处和保持可审计性。

书中所有数字判据（合作临界收益率、边缘政策双阈值、ESS 临界比例、赢家诅咒的条件期望系数等）都是案例与教学例题的归纳，原书未提供统计回测背书，使用时需按标的自行测试并声明所用口径。本仓库内容不构成投资建议。

## License

[MIT](./LICENSE)
