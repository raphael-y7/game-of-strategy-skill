---
name: game-of-strategy-skill-router
description: |
  《策略博弈（第4版）》博弈分析来源路由入口：用行动时序/利益冲突/次数/信息/规则/协调六问给股票投资情境分类，路由到博弈树逆推、纳什均衡、合作临界值、信号可信度、策略性行动、赢家诅咒、策略拥挤等13张能力卡。当用户的问题不明确属于哪个具体博弈分析任务时由此入口分类分派。
metadata:
  cangjie.generated-by: cangjie-tools v2.5.0
  cangjie.variant: router
  cangjie.bundle-id: bundle.celue-boyi-v4
  cangjie.capability-count: 14
  cangjie.entrypoint-count: 9
---
# 策略博弈（第4版） — 来源路由入口（compact pack）

## 触发与不触发

**适用**：与本书能力域相关的咨询与任务（见下方路由表的意图列）。
**不适用**：
- 不预测股价涨跌方向，只输出博弈结构与行为预测
- 不处理与多人策略互动无关的纯技术指标问题
- 投票制度与生物进化数学细节不做计算（第12/15章仅取思想）

## 核心原则（常驻速览，概览类问题读到这里即可回答）

1. 先判结构再求解：时序、冲突度、重复性、信息结构、规则可否操纵、协调维度六问分类（第2章）
2. 序贯博弈逆推：向前看、向后推理，从终点结剪枝（第3章）
3. 同时行动找纳什均衡：互为最优反应，弱占优剔除须复查（第4-5章）
4. 行动胜于语言：信号须差异成本，威胁须互相伤害且可置信（第8-9章）
5. 合作靠未来：重复博弈用有效收益率对照临界值判断瓦解风险（第10章）
6. 中标即坏消息：共同价值拍卖向下调整防赢家的诅咒（第16章）

## 能力路由（先读本表，按意图加载 1 张能力卡）

| 用户意图 | 先读 | 补读/备注 |
|---|---|---|
| 我遇到的这个问题是决策问题还是博弈问题？；这个博弈是序贯还是同时、一次性还是重复、信息对称吗？；该按哪张能力卡来分析这个局面？ | references/capabilities/source-router.md | 已晋级为独立 Skill `source-router`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 这个事件链条接下来会怎么走？；从终点倒推，各方现在的最优行动是什么？；含不确定性的多阶段事件怎么定价？ | references/capabilities/event-game-tree-rollback.md | 已晋级为独立 Skill `event-game-tree-rollback`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 双方会落到哪个格子？为什么理性还双输？；怎么画支付表、怎么找全部纳什均衡？；剔除劣势策略会不会漏掉均衡？ | references/capabilities/payoff-table-nash-equilibrium.md | 已晋级为独立 Skill `payoff-table-nash-equilibrium`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 这个抱团/联盟能维持多久？何时会瓦解？；维持合作需要的最低收益率/延续概率是多少？；限售解禁、对赌到期这类时点有什么风险？ | references/capabilities/cooperation-threshold-repeat-game.md | 已晋级为独立 Skill `cooperation-threshold-repeat-game`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 对手下一步会怎么随机化？我该押哪个方向？；怎么防止自己的模式被识别？ | references/capabilities/mixed-strategy-randomization.md | references/capabilities/payoff-table-nash-equilibrium.md、references/capabilities/strategic-crowding-ess.md、references/capabilities/brinkmanship-dual-threshold.md |
| 这份研报/这篇荐股能信几分？；管理层的回购/指引是真是假？；这个市场什么时候会发生逆向选择崩盘？ | references/capabilities/credibility-signaling-filter.md | 已晋级为独立 Skill `credibility-signaling-filter`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 多重均衡下市场会收敛到哪个？；整数关口/前高为什么有效？何时失效？ | references/capabilities/focal-point-selection.md | references/capabilities/payoff-table-nash-equilibrium.md、references/capabilities/collective-action-stampede.md、references/capabilities/strategic-crowding-ess.md |
| 央行/大股东/庄家这个表态算数吗？；这份承诺公告的含金量怎么打分？；对手的策略性行动怎么反制？ | references/capabilities/strategic-moves-credibility.md | 已晋级为独立 Skill `strategic-moves-credibility`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 这个抱团/挤兑处在什么阶段？临界人数到了吗？；策略使用者还有多少涌入空间？；流动性挤兑的底部在哪里？ | references/capabilities/collective-action-stampede.md | references/capabilities/strategic-crowding-ess.md、references/capabilities/cooperation-threshold-repeat-game.md、references/capabilities/payoff-table-nash-equilibrium.md、references/capabilities/focal-point-selection.md |
| 这个风险事件的概率威胁可行吗？；事件溢价该怎么给、撤退线画在哪？ | references/capabilities/brinkmanship-dual-threshold.md | references/capabilities/strategic-moves-credibility.md、references/capabilities/event-game-tree-rollback.md、references/capabilities/batna-negotiation.md、references/capabilities/mixed-strategy-randomization.md |
| 打新/定增/大宗该出多少价？；中了标是不是反而意味着坏消息？；这个拍卖机制对应什么出价策略？ | references/capabilities/winner-curse-auction-bidding.md | 已晋级为独立 Skill `winner-curse-auction-bidding`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 这单并购/定增的成交区间在哪？；弱势方怎么改进谈判结果？；对方拖得起吗？ | references/capabilities/batna-negotiation.md | references/capabilities/strategic-moves-credibility.md、references/capabilities/winner-curse-auction-bidding.md、references/capabilities/brinkmanship-dual-threshold.md、references/capabilities/event-game-tree-rollback.md |
| 这个风格/策略现在挤不挤？何时瓦解？；我的策略能抵抗抢跑变异吗？；趋势的临界持仓占比是多少？ | references/capabilities/strategic-crowding-ess.md | 已晋级为独立 Skill `strategic-crowding-ess`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 设计或评估激励机制/契约条款；分析信息披露规则与说真话条件；判断契约是否满足激励相容与参与约束 | references/capabilities/mechanism-design-incentives.md | references/capabilities/credibility-signaling-filter.md、references/capabilities/strategic-moves-credibility.md、references/capabilities/winner-curse-auction-bidding.md、references/capabilities/payoff-table-nash-equilibrium.md |

**非能力类查询**：
- 书名/作者/章节/整书概览 → references/overview.md
- 术语解释 → references/glossary.md
- 决策规则速查（不需要原文依据时） → references/cheatsheet.md
- 完整意图与关键词索引（本表未覆盖的意图先查这里） → references/capability-index.md

## 加载规则

- 每次任务先读本文件，再按路由表加载 **1** 张能力卡；任务明确跨域时最多加载 2 张。
- 概览/书名类问题不加载能力卡，用「核心原则」与 overview.md 回答。
- 路由表与 capability-index.md 都无法命中的意图，明确告知超出本书范围，不要硬套。

## 边界与判停

- 输入缺失参与人/支付/时序等关键要素时先询问，不代填
- 支付数值无法估计且用户不提供时，输出定性方向而非伪造数值
- 局面不构成策略互动（无交叉效应）时明确退出并说明
