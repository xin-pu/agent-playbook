# 投递：低比特量化与嵌入表压缩（2026-10-24 daily）

## E1 · SQuAT：把 lattice 向量量化 QAT 扩展到十亿参数

- 获取日期：2026-10-24
- 来源 URL：https://arxiv.org/abs/2610.31412
- 本地原件：`Sources/01-dl/.inbox/originals/arxiv-2610.31412-squat-lattice-vq-qat.pdf`
- 适用范围：preprint，未经同行评议；覆盖低比特 LLM 的向量量化感知训练（shape-gain 分解 + E8 球面码本）；不覆盖部署侧反量化开销与硬件实测吞吐。
- 证据等级：A
- 可提炼要点：
  1. 问题：lattice VQ 的 rate-distortion 好，但 VQ-QAT（量化感知训练）行为在十亿参数规模上缺少刻画。
  2. 方法：SQuAT 把权重分解为方向 + 幅度——归一化方向用 E8 派生球面码本量化，gain 用低比特标量量化独立处理，并对 shape 与 gain 各用一个 straight-through estimator。
  3. 机理结论：与忽略 shape-gain 结构的标准 STE 不同，分离 STE 对方向产生切空间更新，等价于隐式的球面（Riemannian）优化——这是可写进正文的机制级论断。
- 关闭条件：与 round-to-lattice 类 PTQ 基线和 GPTQ/AWQ 的端到端困惑度对比未从摘要核出；需读全文实验表并确认训练 token 预算后关。

## E2 · 低比特存储 n-gram 嵌入表（Engram 类记忆的成本压缩）

- 获取日期：2026-10-24
- 来源 URL：https://arxiv.org/abs/2610.31646
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖用低位宽存储 n-gram 嵌入表以压缩记忆开销的方法空间；不覆盖训练框架改动与推理延迟测量。
- 证据等级：A
- 可提炼要点：
  1. 动机数值：开放权重模型开始用 n-gram 嵌入表换性能，作者点名 DeepSeek-V4.1-Flash 为 Engram n-gram 记忆分配了 196B 参数——表本身是显存大头。
  2. 提议：以低精度存储这些嵌入（配合系统化压缩），保住查表带来的性能增益同时砍掉记忆成本，与 01-dl moe-routing 箱的「容量换稀疏」讨论互补。
  3. 具体量化位宽、恢复精度的方法与评测模型规模摘要未给全，不下定量结论。
- 关闭条件：需下载全文核量化位宽-损失曲线与对照模型；确认是否覆盖 V4.1-Flash 同架构复现后可关。
