# 阶段1.5 三重验证产出：coverage-audit.md
- 审计基准：BOOK_OVERVIEW.md 第5节"原书关键任务清单" T01-T15。
- 判定列含义：covered=任务有 verified 候选承接；partial=任务有承接但存在缺口（附补读建议）。
- 输入候选总量：63条（f16 + p18 + c16 + s03 + x13 = 66编号，其中候选池实际共63条主编号+3条S类备用；本审计按实际交付记录）。

## T01-T15 逐条审计

| task_id | 任务 | 对应候选ID | 判定 | 实际交付去向 |
|---|---|---|---|---|
| T01 | 判断决策vs博弈并按六维度分类 | f01 | covered | 能力卡"博弈分类六维度路由"（verified f01） |
| T02 | 构建博弈树并用逆推法求解 | f02、p01(并入f02)、x01、c15、c16、s03 | covered | 能力卡"事件博弈树逆推"（verified f02+x01；references c15/c16）；s03 待NR-02修复后补入 |
| T03 | 画支付表并求纳什均衡 | f03、f04、p02、p03、x04、x05、c03 | covered | 能力卡"支付表与纳什均衡"（verified f03/f04/p02/p03/x04/x05；references c01/c03例证段） |
| T04 | 识别囚徒困境结构并计算合作临界R | f12、p13、p14(并入f12)、x10、c01、c08、c09、c10 | covered | 能力卡"合作临界值"（verified f12/p13/x10；references c08/c09/c10例证） |
| T05 | 混合策略均衡计算与随机化执行 | f05、p04/p05(并入f05)、x03、x12、c05、c06 | covered | 能力卡"混合策略与随机化"（verified f05/x03/x12；references c05/c06） |
| T06 | 判定直接沟通何时可信 | f07、p06(并入f07)、x07、c11 | covered | 能力卡"话语可信度分级"（verified f07/x07；references c11核心同构例） |
| T07 | 可信信号与甄别机制（差异成本、激励相容） | f08、p07(并入f08)、p08、x13、c12、c13 | covered | 能力卡"信号可信度判定"（verified f08/p08/x13；references c12/c13） |
| T08 | 设计与评估策略性行动（承诺/威胁/许诺+置信度） | f09、f10、f11、p09/p10/p11(各并入)、x06、c02、c14(部分) | covered | 能力卡"策略性行动评估"（verified f09/f10/f11/p12/x06；references c02） |
| T09 | 反制他人的策略性行动 | p12、c14(边缘政策反制部分) | covered | 并入"策略性行动评估"卡反制段（verified p12） |
| T10 | 用概率威胁建模危机求可行域 | f14、p15(并入f14)、x09、c14 | covered | 能力卡"边缘政策概率威胁"（verified f14/x09；references c14完整演算） |
| T11 | 共同价值拍卖识别赢家诅咒并调整出价 | f15、p17(并入f15)、p18、x08 | covered | 能力卡"赢家诅咒与拍卖出价"（verified f15/p18/x08） |
| T12 | 纳什合作解与轮流出价；BATNA与不耐烦 | f16、p16(并入f16)、x02、s02 | covered | 能力卡"BATNA谈判分析"（verified f16/x02；references s02） |
| T13 | 多人集体行动分析 | f13、x11 | partial | 能力卡"集体行动与踩踏"（verified f13/x11）；缺口见下 |
| T14 | 进化框架判断策略种群稳定与入侵（ESS） | 无直接候选 | partial | 无能力卡承接 |
| T15 | 机制设计者立场（契约/披露/激励合约） | p08(部分)、x13(部分)、f08(甄别设计半边) | partial | 仅以"信号可信度判定"卡的甄别菜单段间接覆盖 |

## 缺口与补读建议

### G1（T13）：支付函数族不全
- 已交付：囚徒困境型（P(n+1)=2n+2 vs S(n)=2n+4，n=0均衡）与 T(n) 社会最优核算；懦夫博弈型仅目录级提及（11.5"有混合策略的懦夫博弈"）。
- 未交付：安全博弈型与懦夫博弈型的曲线族判据细节、"中间均衡不稳定"的具体数值（候选摘要中的 n=48 未在转写稿检得）。
- 补读建议：精读 11.2.3-11.5（重点图11-7/11-8区域），补齐"临界质量/安全博弈"两型判据后再扩卡；关键词回查"临界质量""懦夫博弈 混合"。

### G2（T14）：第12章进化博弈整体缺候选
- 现状：63条候选中无一条对应 ESS/单态型/多态型/鹰鸽博弈/三种表现型；而转写稿第12章内容存在（L7888-7905 ESS与多态型定义、12.5三种表现型、12.6鹰鸽博弈目录），且 BOOK_OVERVIEW 应用15把"策略拥挤"列为潜力卡。
- 补读建议：对第12章补跑一次阶段1提取（重点 12.1 定义、12.2-12.3 复制者动态直觉、12.6 鹰鸽混合均衡）；若维持"思想内核即可"的裁剪方针，至少在 glossary 增加"ESS/单态型/多态型"三条术语并注明"无能力卡，思想由T13/T04卡借用"。

### G3（T15）：机制设计只有"被拆用"的碎片
- 现状：13.1价格歧视、13.3成本加成vs固定价格契约、13.4信息披露机制、13.5-13.6努力激励/道德风险均无直接候选；现有内容仅甄别菜单（f08半边）与道德风险术语。
- 补读建议：若坚持"与二级市场关联最弱"的裁剪（OVERVIEW已预告），在 coverage-audit 与 overview"不适合skill化"清单间保持一致口径即可，无需补卡；若后续要解读监管/公司治理，补读 13.3（契约类型与激励）与 13.4（信息披露）两节。

### G4（跨任务）：转写稿残缺项（回查清单）
- x08 棒球自由球员超额支付、x11 n=48、f13"临界质量"术语、x10"连锁店悖论"术语名、p02 三人博弈"页"维、c07 的 6.3 序贯变体、c04/s01 两处来源冲突（见 needs-review.md）——共8项，均已在 verified.md/references.md 对应条目就地标注"删去或回查原书"。

## 末尾统计
- 输入候选：63条主候选（f01-f16、p01-p18、c01-c16、x01-x13）+ 3条S类备用（s01-s03）= 66条记录。
- verified：35条（f01-f16 计16，p02/p03/p08/p12/p13/p18 计6，x01-x13 计13）。
- reference：17条（c01-c03、c05-c16 计15，s02、s03 计2）。
- needs_review：2条（c04、s01）。
- rejected：12条（p01、p04、p05、p06、p07、p09、p10、p11、p14、p15、p16、p17，均为被覆盖去重，保留ID见verified.md末尾）。
- 合计 35+17+2+12 = 66，与输入记录数一致，无遗漏。
- 覆盖结论：T01-T12、T09、T10、T11 全部 covered；T13 partial（缺两型曲线族判据）；T14 partial（无候选，需补提取）；T15 partial（碎片化间接覆盖，属书级裁剪决策）。

---

# 阶段1.5收尾+1.6晋级门补充审计（2026-10-27）

## T13/T14 补齐记录
- T13 集体行动博弈：partial → covered。补充候选 f17（双人三型判别框架）、f18（P(n+1) vs S(n) 与边际社会获益三分解）、p19（责任分散 P=(C/B)^{1/(N-1)}）、p20（临界规模I与锁定），全部三重验证通过（见 verified.md 第五节）。G1 缺口（懦夫型/安全型曲线族判据）已补齐：懦夫型交点 n=40（P(n+1)=4n+40、S(n)=5n）、安全型交点 n=48（P(n+1)=4n+4、S(n)=2n+100），均可复算。
- T14 进化博弈/ESS：partial → covered。补充候选 f19（三假定+ESS双准则）、f20（进化-理性对应定理）、p21（适应度阈值族 x>2/3、x>2/n、x<1/2）、p22（鹰鸽 V-C 结构 h=V/C），全部三重验证通过。
- G1 更正：此前审计记"x11 原摘要 n=48 未在转写稿检得"——复核确认 n=48 作为【安全博弈型交点】在 L7335 数值核对行存在（原摘要错误在于把它标成"不稳定均衡"而非安全型交点）；"临界质量"术语全稿仍未检得（0处），卡片继续用曲线相对位置表述。
- G3（T15）维持书级裁剪决策不变，无变化。
- G4 回查清单更新：c04 已处置（见 needs-review.md NR-01），s01 保留待回查；其余6项不变。

## 晋级门评审结果（阶段1.6）
- 评审对象：43条 verified 候选（原35+补充8），逐条过五判据（独立意图/契约/运行必须过；独立复用/评测至少1条过）。
- promoted：8个去向（符合软预算8），聚合为7张能力卡+1个路由入口：
  1. celue-00-source-router 博弈分类六维度与来源路由入口（f01）
  2. celue-01-event-game-tree-rollback 事件博弈树逆推（f02+x01）
  3. celue-02-payoff-table-nash-equilibrium 支付表与纳什均衡定位（f03+f04+p02+p03+x04+x05）
  4. celue-03-cooperation-threshold-repeat-game 合作临界值计算（f12+p13+x10）
  5. celue-05-credibility-signaling-filter 信号与话语可信度判定（f07+f08+p08+x07+x13）
  6. celue-07-strategic-moves-credibility 策略性行动与置信度评估（f09+f10+f11+p12+x06）
  7. celue-10-winner-curse-auction-bidding 赢家诅咒与拍卖出价（f15+p18+x08）
  8. celue-12-strategic-crowding-ess 策略拥挤与抱团瓦解（f19+f20+p21+p22）
- router（能力卡，经 celue-00 路由入口访问，不淘汰）5张：celue-04 混合策略（零和前提限制）、celue-06 聚点（无计算契约）、celue-08 集体行动与踩踏（P/S需外部标定）、celue-09 边缘政策（参数主观、偶发）、celue-11 BATNA（参数难标定、低频）。
- rejected 12条要点归属已双重复核，全部并入对应canonical（p01→f02、p04/p05→f05、p06→f07、p07→f08、p09→f09、p10→f10、p11→f11、p14→f12、p15→f14、p16→f16、p17→f15），无需补记。

## 重跑统计（2026-10-27，含 T13/T14 补充）
- 输入候选：66条主记录+3条S类备用+8条补充候选=74条记录（66+8，其中 s01 仍挂 needs_review）。
- verified：43条候选（f01-f20 计20、p02/p03/p08/p12/p13/p18/p19/p20/p21/p22 计10、x01-x13 计13），聚合为13张能力卡。
- promoted 去向：8（7能力卡+路由入口，达成软预算8）；router 能力卡：5。
- reference：17条（c01-c03、c05-c16 计15，s02、s03 计2）；c04 经修复主体后升级为例证（映射 celue-02/celue-08，计入 reference 后 reference 为18条；c04 原状态从 needs-review 移除）。
- needs_review：1条（s01，保留，注明"均衡方向须回查原书"）。
- rejected：12条（p01、p04、p05、p06、p07、p09、p10、p11、p14、p15、p16、p17）。
- 合计 43+18+1+12 = 74，与输入记录数一致，无遗漏。
- 覆盖结论：T01-T14 全部 covered；T15 partial（书级裁剪决策，维持口径）。
- 产物：.cangjie/capabilities/verified.yaml（13条能力登记）、.cangjie/capabilities/destinations.json（13条去向）。

---

# 参考内容实际交付路径（阶段3追加，2026-10-27）

- also_read 定稿：.cangjie/capabilities/verified.yaml 14条能力卡的 also_read 字段已回写（每卡2-4条，依据 cards/*.md A2/B 段的相互引用与串联关系）。
- 相邻区分定稿：11张存在明显竞争关系的卡（celue-01/03/04/05/06/07/08/09/10/11/13）A2段末尾已追加"**相邻区分（定稿）**"一行。
- 术语定稿：GLOSSARY.md（65条，9主题分组，每条含 → 相关能力卡 指向）写入 books/策略博弈第4版/GLOSSARY.md。
- Bundle：BOOK_OVERVIEW.md → .cangjie/capabilities/book/overview.md；GLOSSARY.md → .cangjie/capabilities/book/glossary.md。
- 参考内容交付路径：
  - 映射到 overview 的条目（c01、c06、c08、c11）→ .cangjie/capabilities/book/overview.md 末尾"## 参考内容"节。
  - 映射到 glossary 的条目（c03、c07、c09、c10、c11/x07、维克里说真话）→ .cangjie/capabilities/book/glossary.md 末尾"## 参考内容"节。
  - 源文件 books/策略博弈第4版/references.md 保留不变，行号核验以该文件为准。

