# 投递：多教师 on-policy 蒸馏与约束/鲁棒策略优化的理论进展

## E1 · 多教师 on-policy 蒸馏与 Fisher 模型合并的二阶等价

- 获取日期：2026-10-21
- 来源 URL：https://arxiv.org/abs/2610.26525
- 本地原件：`Sources/00-rl/.inbox/originals/arxiv-2610.26525-fisher-multi-teacher-distillation.pdf`
- 适用范围：preprint，未经同行评议（页眉自标 Preprint，v1 提交 2026-10-19）；覆盖同源（homologous）专家模型处于同一损失盆地时，多教师 on-policy 蒸馏与 Fisher 合并的目标函数关系；不覆盖异构教师、非共享盆地或需大量 rollout 的在线蒸馏工程细节。
- 证据等级：A
- 可提炼要点：
  1. 核心结论：在共享盆地的同源专家之间，多教师 on-policy 蒸馏目标在二阶近似下精确等于 Fisher-merging 目标，因此其最优解就是 Fisher 合并——合并可作为蒸馏的一个闭式阶段。
  2. 该等价把「快但启发式」的模型合并与「对齐分布但 rollout 计算昂贵、跨任务梯度冲突」的多教师蒸馏统一为同一目标的不同阶展开。
  3. 在此基础上提出 Residual-Governed Branch-and-Merge 方法（摘要截断处未展开细节，需全文核对算法流程与实验规模）。
- 关闭条件：需全文精读补实验数字（模型规模、任务数、对比基线）；作者公开代码或第三方复现后可关。

## E2 · LOCU：CMDP 多约束策略优化的正交化约束更新

- 获取日期：2026-10-21
- 来源 URL：https://arxiv.org/abs/2610.26256
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖约束马尔可夫决策过程（CMDP）中多约束同时生效时的策略更新数值稳定性；不覆盖单约束场景与具体 LLM 对齐任务的落地配方。
- 证据等级：A
- 可提炼要点：
  1. 问题定位：多个约束梯度相互作用导致更新方向病态、约束修正相互抵消或冗余叠加，步长数值脆弱。
  2. 方法：在 Fisher-Rao 度量下对奖励与约束的自然梯度做对称 Löwdin 正交化，配合 Fisher 几何筛选与近共线压缩，得到降维空间使信赖域成为欧氏球，约束由低维 active-set 求解对称处理。
  3. 对不可行迭代点，LOCU 构造 Pareto 下降方向，在同一降维形式内保持已满足约束的局部可行性；实验称在高约束耦合、窄可行域与不可行起点下保持稳定，并跨 cost critic 结构泛化（摘要级信息，未读正文图表）。
- 关闭条件：缺全文实验数据与第三方复现；正文表格数字与复现实验补齐后可关。

## E3 · 鲁棒 (PO)MDP：奖励目标与不完全观测博弈的律不变等价

- 获取日期：2026-10-21
- 来源 URL：https://arxiv.org/abs/2610.26568
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖 RL 理论——鲁棒 POMDP 在四类奖励目标（折扣和、长期平均、有限/无限时域累积）与律不变风险度量（期望、均值-方差、CVaR、熵风险）下的可解性与复杂度；不覆盖算法实现与大规模实验。
- 证据等级：A
- 可提炼要点：
  1. 形式化了包含上述四种风险度量的律不变风险度量类，并给出统一框架：将 RPOMDP 归约为部分可观测随机博弈（POSG）求解。
  2. 证明 (s,a)-rectangular RPOMDP（多面体不确定集）在每种奖励目标与任意律不变风险度量下与 POSG 等价，等价由 logspace 归约构造、保持奖励目标分布（至常数缩放）。
  3. 复杂度推论：求解 (s,a)-rectangular RMDP 与求解简单随机博弈（SSG）一样难，为该类问题给出新的复杂度定位。
- 关闭条件：纯理论结果，需同行评议版本（会议/期刊录用）确认证明无误后可关。

## 台账登记（未过开箱门槛）

以下候选本轮只有单一来源且无可用原件（Agima PDF 29MB 下载超时截断，弃），不建证据块，留待积累：

- Agentic Imagination (Agima): Train An Imaginative Agent — SFT+agentic RL 统一策略与世界模型，先想象后行动，https://arxiv.org/abs/2610.26845
- Agent World Model in the Wild: Computer-Use Agent Environment Synthesis，https://arxiv.org/abs/2610.26828
