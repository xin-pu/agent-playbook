# 投递：长程 agentic RL 的信用分配与蒸馏（2026-10-19 daily）

> 本文件为未入箱投递，合箱由人工主流程处理。候选去向：`00-rl` 域 policy-optimization / agentic RL 相关箱。

## E1 · 树感知后验蒸馏做长程 agentic RL 的轮级信用分配

- 获取日期：2026-10-19
- 来源 URL：<https://arxiv.org/abs/2610.23181>
- 本地原件：`Sources/00-rl/.inbox/originals/arxiv-2610.23181-tree-aware-posterior-distillation.pdf`
- 适用范围：preprint，未经同行评议；清华 + Tencent 基模部门合作，覆盖长多轮交互下 RLVR 后训练的信用分配与策略陈旧问题；不覆盖在线部署与多模态。
- 证据等级：A
- 可提炼要点：
  1. 指出长程 agentic RLVR 的两个耦合困难：只用终端奖励使轮级信用分配稀疏且高方差；对固定 rollout batch 做序贯 mini-batch 更新会引入当前策略与行为策略漂移（policy staleness）（摘要）。
  2. 提出 Tree-Aware Posterior Distillation：从 rollout 树结构内部获得更密的信用，不依赖 value network、step-level 标注或更强的外部 teacher，省去这三类组件的训练开销（摘要）。
- 关闭条件：v1 全文精读未见公开第三方复现；实验规模与可复现性待核，会议版或第三方复现后可关。

## E2 · 多轮搜索 agent 的 grounded credit assignment（GCA）

- 获取日期：2026-10-19
- 来源 URL：<https://arxiv.org/abs/2610.23148>
- 本地原件：`Sources/00-rl/.inbox/originals/arxiv-2610.23148-grounded-credit-assignment.pdf`
- 适用范围：preprint，未经同行评议；覆盖检索增强 QA 上 GRPO 类结果奖励的 token 级信用分配缺陷；不覆盖开放域任务。
- 证据等级：A
- 可提炼要点：
  1. GRPO 把同一条 rollout 的所有 token 赋同一 advantage，无法区分「找到证据」与「使用证据」两种能力；Search-R1 在 7 个 QA 基准上升准确率，但 Bamboogle 上正确答案中「证据支撑」的比例反而从 84.0% 跌到 42.9%（预印本数据，未复现）。
  2. 作者归因：检索到含答案证据的 rollout 只按相对准确率增益被聚合偏好，凭记忆作答或误用证据可缩小甚至反转这一「grounding gap」；GCA 用可验证的子结果修正每段信用，无需辅助模型、额外 rollout 或分阶段训练（摘要与 §方法节）。
- 关闭条件：仅 QA 检索域验证；需在更多 agentic 检索/工具环境复现后可关。

## E3 · RLVR 是否真的需要长 rollout 窗口（BCR-II / CCR）

- 获取日期：2026-10-19
- 来源 URL：<https://arxiv.org/abs/2610.22887>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖 RLVR 训练成本与 rollout 截断下 group-relative advantage 失效问题；不覆盖推理时（test-time）长度控制。
- 证据等级：A
- 可提炼要点：
  1. 单纯截短 rollout 窗口会移除正确性信号：单题 rollout 全部在给出答案前被截断时，组内相对准确率 advantage 消失（摘要）。
  2. Concurrent Constraint Reinforcement（CCR）把 3 个可独立验证的问题放进一个封顶 completion：截断前完成的正确答案保留 credit，共享预算在无显式长度惩罚的情况下鼓励更短的有效推理（摘要）。
- 关闭条件：并发题数（3）与封顶预算的敏感性分析需全文核对；同组后续版本或第三方复现后可关。

## E4 · 不完美的 verifier 下 test-time compute 的采样/混合/验证分配

- 获取日期：2026-10-19
- 来源 URL：<https://arxiv.org/abs/2610.23255>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖 best-of-N/自验证类 test-time scaling 的预算分配建模；verifier 为单作者理论+实验框架，不覆盖特定模型的定量排名。
- 证据等级：A
- 可提炼要点：
  1. 成功率需两个条件同时成立：候选中存在正确解（随采样数可预测增长）与 verifier 选中它（不保证）：真实 verifier（单元测试、多数投票、LLM judge、reward model）会接受错误答案、拒绝正确答案，并犯相关性错误（摘要）。
  2. 把「采多少、从哪些模型采、花多少在验证上」从经验规则改为固定预算下的显式分配问题（摘要）。
- 关闭条件：单作者预印本，社区引用与复现情况未定；出现独立复核或会议版后可关。

## E5 · 可靠性与保守性联合建模的贝叶斯过程奖励模型（BayesianPRM）

- 获取日期：2026-10-19
- 来源 URL：<https://arxiv.org/abs/2610.23223>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖 PRM 在 test-time scaling 中的奖励不确定性来源分解；不覆盖结果级 ORM。
- 证据等级：A
- 可提炼要点：
  1. 把 PRM 过程奖励不准拆成两类不确定性：监督数据不足与训练不完备造成的 PRM uncertainty；采集数据策略与 test-time 策略错配造成的 policy uncertainty（导致系统性奖励高估）（摘要）。
  2. BayesianPRM 将过程奖励视为随机变量，做 reliability- 与 conservatism-aware 的贝叶斯 belief 推断，此前工作未同时考虑两者（摘要）。
- 关闭条件：定量增益幅度未在摘要给出，需全文精读；第三方复现后可关。
