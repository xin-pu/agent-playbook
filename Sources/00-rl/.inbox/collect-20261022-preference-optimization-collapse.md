# 投递：偏好优化的共模偏移与词表坍缩（2026-10-22 daily）

## E1 · ECHO：DPO/SimPO 的 common-mode offset 与 generation collapse

- 获取日期：2026-10-22
- 来源 URL：https://arxiv.org/abs/2610.29410
- 本地原件：`Sources/00-rl/.inbox/originals/arxiv-2610.29410-echo-vocabulary-collapse-dpo.pdf`
- 适用范围：preprint，未经同行评议；覆盖 per-token ranking loss 类偏好优化（DPO/SimPO）在 UltraFeedback 类训练中的表示层退化诊断；不覆盖 pair-wise 之外的偏好目标与在线 RLHF 回路。
- 证据等级：A
- 可提炼要点：
  1. 偏好优化可在全部 ranking 指标上升的同时累积一个跨位置、跨 prompt、chosen/rejected 共享的隐藏表示偏移（common-mode offset），相对损失对其几乎不敏感。
  2. offset 投影到输出层形成 vocabulary well，抬升单一 token 概率直至解码主导，即 generation collapse；干预实验证明因果性（单独注入学到的 offset 可在未处理基座上复现坍缩，norm-matched 随机方向不能）。
  3. 定量口径（预印本数据，未复现）：同一 per-token ranking loss 下 17 个基座模型谱系中 14 个出现坍缩，且为全参微调；textbook DPO 在 3 倍预算下 offset 仍弱对齐，全参 SimPO 在 Llama-2 与 Llama-3.1 上均驱动坍缩。
  4. 跨 17 个 UltraFeedback run：held-out ranking 越好的 run，两个公开 reward model 对其样本的偏好胜率越低——ranking 指标存在盲区。
  5. 从损失中 mask 掉共模分量可在 flagship 设置下阻止 vocabulary well 形成，构成一个早于坍缩的可监控信号。
- 关闭条件：缺第三方复现与 reward model 偏好-排名负相关的外推验证；公开复现或 camera-ready 后关。作者含 Huawei/Tokyo/TIER IV 混合署名，机构口径待核。
