# 投递：KV 缓存与状态空间压缩（2026-10-28 daily）

> 巡检通道：arXiv API（mixture of experts / quantization 查询）。窗口 2026-10-27T00:00Z~2026-10-28T01:10Z。判重：2610.36950 / 2610.36617 均未见于 `Sources/`。本轮 01-dl 无原件下载（全轮原件实际落盘 4 份：00-rl×3 PDF、03-mcp×1 JSON；04 域 kw-bench 原件两次截断放弃，见该投递头部）。

## E1 · DCKV：端到端训练的可微 KV 缓存编解码器

- 获取日期：2026-10-28
- 来源 URL：<https://arxiv.org/abs/2610.36950>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖混合注意力（hybrid）语言模型中全注意力层 KV 缓存的压缩存储与迁移；不覆盖注意力机制本身的替换方案，不覆盖训练期显存优化。
- 证据等级：A
- 可提炼要点：
  1. 定位：hybrid 模型只在少量全注意力层保留 KV 缓存，但该缓存仍是 prompt 状态中随长度增长、复用时必须存储或搬运的部分；DCKV 自称首个端到端训练的 KV-cache codec。
  2. 方法：变换、量化器与熵模型（以 prompt token 与已解码相邻位置为条件）对冻结语言模型联合优化，目标同时是熵模型给出的码长与模型输出变化——「码长 + 输出失配」双目标区别于纯失真压缩。
  3. 实验面：在 Qwen3.5-2B 上评测；摘要中压缩倍数句在抓取文本截断（"more than 55 times f…"），定量口径登记前必须回原文，本轮不采信任何倍数结论。
- 关闭条件：无原件；下轮补 PDF 核对 55× 类指标的分子分母定义（对比基线是什么）后方可引用。

## E2 · Mamba-2 状态压缩的盲区：能量方向与读出方向不重合

- 获取日期：2026-10-28
- 来源 URL：<https://arxiv.org/abs/2610.36617>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖训练后 Mamba-2 递归状态的几何分析与「按坐标独立打分」类压缩器的失效机理；不覆盖新压缩算法的定量收益，不覆盖其它 SSM 架构。
- 证据等级：A
- 可提炼要点：
  1. 经验观察：Mamba-2 把全部上下文压进固定尺寸递归状态（主导解码内存与带宽）；检查训练后状态发现能量近乎 rank-one，但集中在校准器累积出的「偏置型方向」，而输出真正读取的内容位于与状态坐标不正提的低维子空间。
  2. 推论：现有对状态值量化或按坐标剪枝的压缩器逐坐标独立打分，即使 output-aware 也漏掉决定输入-输出映射的方向——压缩应在坐标系变换/子空间层面做，与既有「量化注意/attention-KV 压缩」线（10-26 投递 quantization-attention-compression）在状态空间模型上的延伸点吻合。
  3. 本轮未下原件（配额所限），具体子空间维度、能量占比数字未登记。
- 关闭条件：无原件，定量口径未核；若后续要支撑「state-space 压缩需换基」的正文判断，须补 PDF 并复现其状态分析图。

## 台账登记（未过开箱门槛或配额所限，暂不建块）

- BellowsKV: One Latent for Many Layers, Expanded on Demand（2610.35023，published 2026-10-26）<https://arxiv.org/abs/2610.35023>——KV 线相邻证据，与本轮 E1 同主题积累后再并箱。
- Efficient Quantization Training with Stochastic Rounding via Structured Subspace（2610.36587，published 2026-10-27）<https://arxiv.org/abs/2610.36587>——量化训练线，与 10-24 lowbit-quantization 投递同主题，单轮每域 6 来源上限所限降级台账。
- End-to-End MXFP8 Reinforcement Learning on Blackwell（2610.34915，published 2026-10-26）<https://arxiv.org/abs/2610.34915>——低精度 RL 训练系统，归属 00-rl 或 01-dl 待定，先登记链接。
