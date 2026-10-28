# 能力索引（完整版）

| capability_id | 标题 | 重要度 | 意图 | 关键词 | 能力卡 |
|---|---|---|---|---|---|
| celue-00-source-router | 博弈分类六维度与来源路由入口 | high（全书入口，分类错误则后续解法全错；f01验证V3结论） | 我遇到的这个问题是决策问题还是博弈问题？；这个博弈是序贯还是同时、一次性还是重复、信息对称吗？；该按哪张能力卡来分析这个局面？ | 博弈分类、六维度、行动时序、信息不对称、重复博弈、路由、入口 | capabilities/source-router.md |
| celue-01-event-game-tree-rollback | 事件博弈树逆推 | high（事件驱动分析底座；c15幸存者例0.54>0.48数值评测通过） | 这个事件链条接下来会怎么走？；从终点倒推，各方现在的最优行动是什么？；含不确定性的多阶段事件怎么定价？ | 博弈树、逆推、rollback、序贯博弈、均衡路径、事件驱动、自然节点 | capabilities/event-game-tree-rollback.md |
| celue-02-payoff-table-nash-equilibrium | 支付表与纳什均衡定位 | high（最高频结构工具；表4-5数值评测通过；x04/x05双失效证据） | 双方会落到哪个格子？为什么理性还双输？；怎么画支付表、怎么找全部纳什均衡？；剔除劣势策略会不会漏掉均衡？ | 支付表、纳什均衡、最优反应分析、占优策略、重复剔除、弱占优、风险态度 | capabilities/payoff-table-nash-equilibrium.md |
| celue-03-cooperation-threshold-repeat-game | 合作临界值计算（重复博弈与瓦解时点） | high（行业默契/OPEC/抱团崩盘时点预判；110%数值评测通过） | 这个抱团/联盟能维持多久？何时会瓦解？；维持合作需要的最低收益率/延续概率是多少？；限售解禁、对赌到期这类时点有什么风险？ | 重复博弈、触发策略、合作临界、有效收益率、以牙还牙、瓦解时点、终点效应 | capabilities/cooperation-threshold-repeat-game.md |
| celue-04-mixed-strategy-randomization | 混合策略与随机化执行 | medium（计算严谨但严格零和前提在市场少有满足，x03自警"慎之又慎"） | 对手下一步会怎么随机化？我该押哪个方向？；怎么防止自己的模式被识别？ | 混合策略、对手无差异、随机化、零和、秒针法、模式识别 | capabilities/mixed-strategy-randomization.md |
| celue-05-credibility-signaling-filter | 信号与话语可信度判定 | high（研报/公告/IR解读的日频缺省过滤器；教育信号7-11与f<0.65评测通过） | 这份研报/这篇荐股能信几分？；管理层的回购/指引是真是假？；这个市场什么时候会发生逆向选择崩盘？ | 可信度、廉价磋商、差异成本、信号、甄别、分离均衡、混同均衡、柠檬市场、废话均衡 | capabilities/credibility-signaling-filter.md |
| celue-06-focal-point-selection | 聚点与关键点位选择 | medium（解释力强但原书自认"艺术"、无计算契约，判定不可复算） | 多重均衡下市场会收敛到哪个？；整数关口/前高为什么有效？何时失效？ | 聚点、多重均衡、协调、关口、自我实现、参照系 | capabilities/focal-point-selection.md |
| celue-07-strategic-moves-credibility | 策略性行动与置信度评估 | high（公告与博弈行为解读的主框架；三级声明复演评测通过） | 央行/大股东/庄家这个表态算数吗？；这份承诺公告的含金量怎么打分？；对手的策略性行动怎么反制？ | 承诺、威胁、许诺、可观察、不可逆、置信度、烧桥、声誉、腊肠策略、反制 | capabilities/strategic-moves-credibility.md |
| celue-08-collective-action-stampede | 集体行动与踩踏（多人博弈判据） | high（拥挤度与踩踏的机制刻画；通勤例6000/3000全链数值评测通过；需外部标定P/S曲线故入router） | 这个抱团/挤兑处在什么阶段？临界人数到了吗？；策略使用者还有多少涌入空间？；流动性挤兑的底部在哪里？ | 集体行动、三型判别、囚徒型、懦夫型、安全型、边际社会获益、责任分散、临界规模、锁定、踩踏、拥挤度 | capabilities/collective-action-stampede.md |
| celue-09-brinkmanship-dual-threshold | 边缘政策概率威胁双阈值 | medium（地缘/债务上限事件偶发且p/q须主观赋值，x09显示三重误判风险） | 这个风险事件的概率威胁可行吗？；事件溢价该怎么给、撤退线画在哪？ | 边缘政策、概率威胁、可行域、双阈值、失控、债务上限、地缘风险 | capabilities/brinkmanship-dual-threshold.md |
| celue-10-winner-curse-auction-bidding | 赢家诅咒与拍卖出价 | high（打新/定增/并购套利强制校验；0.75b<b评测通过） | 打新/定增/大宗该出多少价？；中了标是不是反而意味着坏消息？；这个拍卖机制对应什么出价策略？ | 赢家诅咒、共同价值、拍卖、出价、英式、一价、二价、全支付、收益等价、维克里 | capabilities/winner-curse-auction-bidding.md |
| celue-11-batna-negotiation | BATNA谈判分析 | medium（并购/重组场景有效但v/a/b难标定、二级投资占比小；x02公平偏好边界） | 这单并购/定增的成交区间在哪？；弱势方怎么改进谈判结果？；对方拖得起吗？ | BATNA、纳什合作解、轮流出价、不耐烦、谈判实力、剩余分配、移动威胁点 | capabilities/batna-negotiation.md |
| celue-12-strategic-crowding-ess | 策略拥挤与抱团瓦解（进化博弈判据） | high（风格轮动/抱团监控的进化论刻画；四式阈值族数值评测全部通过） | 这个风格/策略现在挤不挤？何时瓦解？；我的策略能抵抗抢跑变异吗？；趋势的临界持仓占比是多少？ | ESS、进化稳定、适应度、临界比例、鹰鸽博弈、V/C、多态型、单态型、策略拥挤、抱团瓦解、风格轮动、临界持仓占比 | capabilities/strategic-crowding-ess.md |
| celue-13-mechanism-design-incentives | 机制设计与激励契约分析 | medium | 设计或评估激励机制/契约条款；分析信息披露规则与说真话条件；判断契约是否满足激励相容与参与约束 | 机制设计、激励相容、参与约束、契约、信息披露、道德风险、mechanism design、incentive contract | capabilities/mechanism-design-incentives.md |
