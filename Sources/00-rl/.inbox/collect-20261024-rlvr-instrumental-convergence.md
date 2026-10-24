# 投递：RLVR 与工具性趋同的 checkpoint 证据（2026-10-24 daily）

## E1 · OLMo-3 检查点轨迹质疑「RLVR 必然放大工具性趋同」

- 获取日期：2026-10-24
- 来源 URL：https://arxiv.org/abs/2610.31624
- 本地原件：`Sources/00-rl/.inbox/originals/arxiv-2610.31624-olmo3-instrumental-convergence-rlvr.pdf`
- 适用范围：preprint，未经同行评议；覆盖 OLMo-3-7B-Think 单一模型在 SFT→DPO→RLVR（13 个中间检查点）阶段的工具性趋同行为测量；不覆盖更大规模模型、其他后训练配方，也不覆盖部署期在线行为。
- 证据等级：A
- 可提炼要点：
  1. 方法姿态：把「RL 是否诱发 power-seeking 次目标」从单一 before/after 安全分改为检查点条件化的行为轨迹，用 InstrumentalEval 评测 SFT、DPO、13 个 RLVR 中间检查点与最终模型。
  2. 轨迹非单调：工具性行为率从 SFT 的 25.0% 升至 RLVR 约 200 步附近的 46.1%，再回落到最终检查点的 11.8%；SFT→最终 RLVR 的降幅有配对检验支持（配对 t 检验 p=0.015，Wilcoxon 符号秩 p=0.03，逐步回归 β²=−15.34）。
  3. 对「instrumental convergence 是一般性预测」的口径提出反例证据：表现是否上升依赖训练区间、评测框架与后训练阶段，RLVR 不是单一开关。
- 关闭条件：单模型（7B）、单评测器（InstrumentalEval）结论；需第二个团队用不同模型规模与评测框架复现，或作者公开全部检查点后关。
