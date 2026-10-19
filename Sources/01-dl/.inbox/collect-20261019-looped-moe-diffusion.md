# 投递：MoE 蒸馏与 looped / diffusion 架构设计（2026-10-19 daily）

> 本文件为未入箱投递，合箱由人工主流程处理。候选去向：`01-dl` 域 moe-routing 箱及架构类箱。

## E1 · 用激活预算扩张在 MoE 内部构造更强 teacher 的同策略双向蒸馏

- 获取日期：2026-10-19
- 来源 URL：<https://arxiv.org/abs/2610.23185>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖 RLVR 稀疏监督之下 MoE 的同策略蒸馏（on-policy distillation）teacher 来源问题；不覆盖 dense 模型蒸馏全流程。
- 证据等级：A
- 可提炼要点：
  1. RLVR 的结果级奖励对 MoE 只提供稀疏监督，on-policy 蒸馏能给稠密 token 级反馈但需要更强且兼容的 teacher；作者观察到提高每 token 激活预算可暴露模型内部潜在专家容量，即在模型内部得到更强 teacher（摘要）。
  2. 朴素地扩大共激活专家集合会掉点：新共激活的专家从未被优化过协同工作；据此提出 on-policy bidirectional distillation 处理该失配（摘要）。
- 关闭条件：激活预算阈值与协同失配的量化边界需全文核对；同组会议版或第三方复现后可关。

## E2 · Looped 模型设计三轴解耦（拓扑、输入注入、递归状态）

- 获取日期：2026-10-19
- 来源 URL：<https://arxiv.org/abs/2610.23036>
- 本地原件：`Sources/01-dl/.inbox/originals/arxiv-2610.23036-looped-models-part1.pdf`
- 适用范围：preprint，未经同行评议；覆盖 looped transformer 在匹配参数/逻辑深度/token 预算下从零训练的架构消融，并测向 MoE 的迁移；不覆盖大规模生产模型。
- 证据等级：A
- 可提炼要点：
  1. 既有 looped 架构把递归位置、输入注入、递归状态组织三者纠缠；本文在三轴解耦下从零训练对比，prelude–recurrent block–coda 三明治结构在上下文抽取与推理密集任务上一致更优，且设计原则可迁移到 resident/active 参数匹配的 MoE（摘要）。
  2. 输入注入主要提升知识检索与上下文利用；随机初始化与递归状态的具体影响分轴报告（摘要、§实验）。
  3. 代码开源于 `https://github.com/ifm-ai/xllm-loop`（PDF 首页），Institute of Foundation Models / USC / CMU 团队，Part I 暗示后续卷。
- 关闭条件：Part I 只覆盖三轴中的架构设计，训练配方与更大规模验证待后续卷；放大规模结果发布后可关。

## E3 · Lookahead Editing 弥合 masked 与 uniform 扩散语言模型的训练-表达力权衡

- 获取日期：2026-10-19
- 来源 URL：<https://arxiv.org/abs/2610.23122>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖 dLLM 两大家族（MDM/UDM）的优化难度与表达力权衡及解码期编辑策略；不覆盖 AR 模型对比之外的图像扩散。
- 证据等级：A
- 可提炼要点：
  1. 理论论证 MDM 因 mask 转移调度更易优化但计算表达力较低，UDM 支持迭代状态修订、表达力更强但显著更难训练（摘要）。
  2. LED（Lookahead Editing）在不放弃 MDM 易优化性的前提下引入迭代修订的编辑能力（摘要）。
- 关闭条件：与并行解码加速比的具体权衡未在摘要给出；需全文核对基准后可关。
