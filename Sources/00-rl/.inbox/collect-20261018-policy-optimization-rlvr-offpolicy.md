# 投递：RLVR 离策略与 rollout 预算（policy-optimization 追加）

> 建议合入箱：`policy-optimization`（`Sources/00-rl/policy-optimization/policy-optimization-source.md`）。三块同轴：GRPO 组采样退化、离策略 token 级修正、rollout 批量-崩溃预算。本轮为 2026-10-18 weekly 档。

## E1 · HP-RLVR：单 rollout 用「后见特权」把终端奖励转成 token 权重，精度可比 G=8 的 GRPO

- 获取日期：2026-10-18
- 来源 URL：https://arxiv.org/abs/2610.20497
- 本地原件：`Sources/00-rl/.inbox/originals/arxiv-2610.20497-hindsight-privileged-rlvr.pdf`
- 适用范围：preprint，未经同行评议；覆盖 LLM 推理任务的 RLVR token 级信用分配（G=1 单轨迹）；不覆盖多模态与在线部署。
- 证据等级：A
- 可提炼要点：
  1. 动机与首轮登记的 GRPO 缺陷一致：组内所有 rollout 结果相同时，组相对信号消失；HP-RLVR 改为让「已完成后缀自身」充当特权上下文——生成时的策略快照分别在因果历史与含实现未来+验证结果的后见语境下给每个 token 打分，差值即更新权重。
  2. 原文核对：HP-RLVR 用 G=1，报告与 GRPO（G=8）精度相当（图注口径为相对 GRPO 的 bars）——即每 prompt 采样数从 8 降到 1 换取推理开销下降，单 rollout 信用分配路线首次给出「可比精度」证据。
  3. 与蒸馏-RL 融合线索（#E3 线）互补：特权信息来自轨迹自身未来而非外部教师。
- 关闭条件：缺第三方复现；「精度相当」仅在作者选定任务族成立，跨基准验证或代码放出后可关。

## E2 · Token 级重要性采样的理论基础：全未来 KL 信用使 proximal 更新在离策略混合数据下仍收敛

- 获取日期：2026-10-18
- 来源 URL：https://arxiv.org/abs/2610.18738
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖 RLVR 离策略数据来源（异步生成、rollout-训练失配、响应复用）下的 token 级重要性加权理论；不覆盖具体实现吞吐数字。
- 证据等级：A
- 可提炼要点：
  1. 问题设定：token 级重要性权重避免整条响应似然比连乘，但通常引入梯度偏差；本文证明在覆盖性与局部表达力条件下，「全未来 KL 信用」使精确 proximal 优化器成为更新的唯一驻留策略，即使数据是旧策略的混合，也无需全响应权重或拟合 critic。
  2. 补充结果：持续覆盖 + 时变行为策略下，连续时间 tabular population 更新的收敛性，以及有限样本重标定结论——为异步 RLVR 管线提供可引用的修正口径。
  3. 与 E1/E3 合读：本轮 00-rl 三块共同勾勒 GRPO 系「组采样」之外的两条替代路径——单轨迹后见信用（E1）与离策略修正（本块）。
- 关闭条件：理论条件（覆盖性/局部表达力）在 LLM 实际训练里是否成立未验证；需实验复现或后续版本补充实测后可关。

## E3 · Two Clocks：更大 rollout 批次学得更慢、但按时间表崩溃；给出临界批量与崩溃时钟

- 获取日期：2026-10-18
- 来源 URL：https://arxiv.org/abs/2610.18853
- 本地原件：`Sources/00-rl/.inbox/originals/arxiv-2610.18853-two-clocks-rlvr-rollout-batches.pdf`
- 适用范围：preprint，未经同行评议；覆盖 RLVR 多步训练中 rollout 批量与 √-LR 缩放的关系（局部二次模型 + 16× 批量范围实验）；不覆盖非 RLVR 的通用 RL 调度结论。
- 证据等级：A
- 可提炼要点：
  1. 两时钟框架把「出进展所需样本数」与「崩溃前消耗样本数」分离：√-LR 规则只保一阶漂移/样本，不保进展——批量越大单步越久、曲率损失越多，存在依赖学习率的临界批量，越过后样本效率反而下降。
  2. 原文核对：16× 批量范围的实验支持两个预测；ratio clipping 延迟失败（尤其 clip 开时 failure clock 变慢）；据此给出实用调度——先低于临界批量训练，在崩溃前切换更大批量。
  3. 与首轮亮点「rollout 选择/熵坍缩」直接衔接：把「何时该扩 rollout 预算」从经验变成有临界条件的规则，可提炼为 RLVR 训练排程的操作结论候选。
- 关闭条件：局部二次模型的假设范围与实际 LLM 训练曲率的外推有效性存疑；作者后续放出多任务族/多模型尺度复现后可关。

## 台账登记（本轮巡检流水，不产生证据块）

- GRPO/RLVR 变体同窗密度很高，受全轮 25 块配额限制仅落上列 3 块，其余建议下轮补登：`2610.20814`（Gibbs-Gap off-policy RLVR）、`2610.19103`（Contextual Credit PO）、`2610.18683`（ProAS 进度感知优势整形）、`2610.21060`（Bellman-consistent trajectory RL）。
- agentic-RL 集群已达开箱门槛（≥3 来源）：`2610.22174`（Mosaic 多会话 agentic RL）、`2610.19349`（GRPO 课程×长时程）、`2610.19397`（SERO 可执行预言机延拓）、`2610.15840`（LLM 价值函数信用分配）、`2610.20597`（acting-forecasting 共进化）——建议下轮开 `agentic-rl` 箱并优先补 1 份原件。
- 奖励建模集群同样达 ≥3 门槛（CleanRM `2610.21138`、RM-OPD `2610.20174`、Rent-Seeking RM `2610.19832`、Multi-Reward Hacking `2610.21404`、RaR 置信度 `2610.21179`）——建议开 `reward-modeling-scaling` 候选箱的触发条件已满足，留人工决定。
- 通道健康：arXiv API 本轮全部 200（6 秒间隔、串行），2026-10-17 daily 的限流结论可解除；`http://` 端点现返回 301，改用 `https://export.arxiv.org` + `-L` 已验证。
