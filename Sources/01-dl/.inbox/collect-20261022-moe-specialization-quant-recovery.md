# 投递：MoE 专家特化与低比特推理恢复（2026-10-22 daily）

## E1 · GaP-MoE：梯度正交投影诱导专家特化

- 获取日期：2026-10-22
- 来源 URL：https://arxiv.org/abs/2610.29355
- 本地原件：`Sources/01-dl/.inbox/originals/arxiv-2610.29355-gap-moe-expert-specialization.pdf`
- 适用范围：preprint，未经同行评议（页面标注 October 22, 2026 v1）；覆盖 SMoE 表征坍缩（专家功能趋同）的优化动力学干预；实验规模为 BERT/GLUE 微调与 GPT-2/WikiText-103、enwik8、text8 预训练，不覆盖大规模 MoE 生产模型。
- 证据等级：A
- 可提炼要点：
  1. 路线区分：router 改进法仍受 routing collapse 影响，auxiliary loss 法会与任务目标冲突；GaP-MoE 直接操纵专家输出梯度，不改损失函数。
  2. 机制：每步按归一化路由分从 TopK 专家中随机选 leader，把 follower 专家梯度投影到 leader 近期梯度子空间的正交补，消除方向重叠。
  3. 结果口径：性能与标准 SMoE 可比或更好（预印本数据，未复现），且可作为现有 SMoE 架构的 drop-in 模块。
  4. 与既有 moe-routing 箱（探索漂移、路由分数分析）互补：这是「梯度层」特化手段，可并案合箱。
- 关闭条件：缺 1B+ 参数或生产级 MoE 上的验证；作者给出更大规模实验或第三方复现后关。

## E2 · Right On Q：自生成轨迹下的量化推理恢复

- 获取日期：2026-10-22
- 来源 URL：https://arxiv.org/abs/2610.29378
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖低比特 LLM 的 QAT 中长程推理能力恢复；不覆盖量化硬件部署细节。
- 证据等级：A
- 可提炼要点：
  1. 现有 QAT 配方用全精度模型对固定响应序列做监督，训练前缀与学生自生成前缀失配，轨迹分歧随推理链增长而放大。
  2. 症状：低比特模型在长程推理任务上难以在全精度模型可用的 token 预算内终止。
  3. 方法方向：以学生自生成轨迹作为监督载体（self-generated trajectories）弥合 exposure-style 失配。
- 关闭条件：未读全文，位宽/模型规模/基准数字未知；补 PDF 原件并核对实验表后关。
