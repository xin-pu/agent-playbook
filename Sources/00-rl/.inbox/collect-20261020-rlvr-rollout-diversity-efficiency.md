# 投递：RLVR 的 rollout 多样性保持与预算效率（2026-10-20 daily）

> 本文件为未入箱投递，合箱由人工主流程处理。候选去向：`00-rl` 域 policy-optimization 箱（与既有 RLVR rollout 窗口/批处理证据同主题）。

## E1 · Adaptive Replay：有限样本动力学解释 RLVR 模式坍缩并保多样性

- 获取日期：2026-10-20
- 来源 URL：<https://arxiv.org/abs/2610.24236>
- 本地原件：`Sources/00-rl/.inbox/originals/arxiv-2610.24236-adaptive-replay-rlvr-diversity.pdf`
- 适用范围：preprint，未经同行评议；Cornell 团队，覆盖 RLVR 后训练输出多样性下降的机理分析与自适应重放修正；不覆盖无 verifier 的开放生成。
- 证据等级：A
- 可提炼要点：
  1. 理论口径：对等奖励的两个回复在最优解中的概率比与参考策略中一致（引 Korbak et al. 2022 等），即目标函数本身不歧视任何模式；实践中模式消失源于有限 on-policy rollout 的随机涨落在更新间累积，把概率质量推向部分推理模式（摘要与 §分析节）。
  2. 由此识别「不同正确推理模式的覆盖度」是不稳定的关键因素，提出 adaptive replay 在训练动力学中补足被欠采样的模式以抑制坍缩（摘要）。
- 关闭条件：重放比例与「模式」判定（语义等价聚类口径）需全文核对；多样性提升与准确率的权衡量化待第三方复现后可关。

## E2 · LIFT：用部分 rollout 的隐状态做 training-free prompt 选择

- 获取日期：2026-10-20
- 来源 URL：<https://arxiv.org/abs/2610.24229>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖 RLVR 训练数据（prompt 级）选择以省 rollout 预算；不覆盖样本内 token 级权重调整。
- 证据等级：A
- 可提炼要点：
  1. 动机测量：其数据集中 26%–32% 的完整 greedy rollout 无法在生成预算内终止，基于完整 rollout 隐状态的既有 training-free 选择法因此不可用（预印本数据，未复现）。
  2. LIFT 仅用未完成的局部 rollout，以 Partial Rollout Context Lift 从隐状态估计 prompt 价值，避免为选择而付完整生成成本（摘要）。
- 关闭条件：选择质量的对照实验规模与所对比的完整-rollout 基线具体方法名需全文核对；第三方复现后可关。
