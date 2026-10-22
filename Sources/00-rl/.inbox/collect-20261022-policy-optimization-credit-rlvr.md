# 投递：长程 agent 策略优化与 RLVR 分布平坦化（2026-10-22 daily）

## E1 · One Act, Many Masks：效果边缘化策略优化（credit-update misalignment）

- 获取日期：2026-10-22
- 来源 URL：https://arxiv.org/abs/2610.29427
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖多轮 LLM agent 的细粒度 credit assignment 与策略比更新的结构问题；不覆盖具体环境基准数字（摘要窗内未给）。
- 证据等级：A
- 可提炼要点：
  1. 即使 credit assignment 变细，策略优化仍按 response-specific 概率比施加学习信号；不同文本响应可诱导同一可执行效果，credit 却绑在文本实现上。
  2. 作者将该失配命名为 credit-update misalignment，并指出 credit-text 配对直接塑造策略更新方向。
  3. 提出 effect-marginal（效果边缘化）的策略优化：把 credit 从文本实现解绑、按可执行效果聚合。
- 关闭条件：未读全文（无原件），方法的具体估计器与实验规模未知；补 PDF 原件并核对基准表后可关。

## E2 · Flat-RLVR：sharpness-aware RLVR 缓解推理分布锐化

- 获取日期：2026-10-22
- 来源 URL：https://arxiv.org/abs/2610.29281
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖 GRPO 系 RLVR 后训练中策略分布过度尖锐化、稀有正确轨迹被抑制的问题；不覆盖非 verifiable reward 场景。
- 证据等级：A
- 可提炼要点：
  1. RLVR（尤其 GRPO）常见副作用是 distribution sharpening：策略分布过尖导致样本多样性与推理能力容量受损。
  2. 主张在 RLVR 中寻求 flat-reward optima 以平滑策略分布，并给出 flat reward 与分布性质的理论关联（摘要口径）。
  3. 与既有 00-rl 箱中 rollout 多样性/熵坍缩线索（`collect-20261020-rlvr-rollout-diversity-efficiency`、`collect-20261021-policy-optimization-distillation-theory`）同谱系，可并案合箱。
- 关闭条件：未读全文，理论结果与实验数字（模型规模、基准）未知；补 PDF 原件后关。

## 台账登记（本轮窗内其余 00-rl 相关但不开块项）

- 2610.29498 A Strong MoE Is All You Need for Process Supervision（process supervision 属奖励建模侧，与 01-dl 的 MoE 箱跨域，仅登记）：https://arxiv.org/abs/2610.29498
- 2610.29264 Training in Deployment: Human-in-the-loop Online Post-Training for Robot Manipulation（机器人域，主线外）：https://arxiv.org/abs/2610.29264
