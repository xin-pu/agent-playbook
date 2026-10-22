# 投递：Agentic RL 的 harness 扩展与状态化环境训练（2026-10-22 daily）

## E1 · Harness Scaling：跨多 harness 训练的 agentic RL

- 获取日期：2026-10-22
- 来源 URL：https://arxiv.org/abs/2610.29458
- 本地原件：—（arXiv 端 PDF 尚未生成，`/pdf/2610.29458` 返回 "No file"，登记后待补）
- 适用范围：preprint，未经同行评议；覆盖 agentic RL 训练中 harness（工具使用/上下文管理/长程协调外壳）的选择维度；不覆盖具体底座模型规模与线上部署结论。
- 证据等级：A
- 可提炼要点：
  1. 现有 agentic RL 通常固定单一 harness 训练，导致策略对 harness 配置特化、跨 harness 迁移受限。
  2. 提出 Harness Scaling：把训练从单 harness 扩展到多 harness 分布，作为 agentic RL 的新扩展维度。
  3. 定位是把 RL 信号直接穿过 harness 施加（reinforcement learning directly through the harness）。
- 关闭条件：缺 PDF 原件与实验数字（摘要窗内未给定量结果）；arXiv 渲染出 PDF 后补原件，或作者给出跨 harness 迁移的公开基准数字后可关。

## E2 · BIRD-RL：面向有状态数据中心环境的 agentic RL 课程

- 获取日期：2026-10-22
- 来源 URL：https://arxiv.org/abs/2610.29426
- 本地原件：`Sources/00-rl/.inbox/originals/arxiv-2610.29426-bird-rl-stateful-environments.pdf`
- 适用范围：preprint，未经同行评议；覆盖 SLM（7B/14B）在 SQL 调试/生成等有状态数据中心环境上的多轮 agentic RL；不覆盖开放式工具调用环境。
- 证据等级：A
- 可提炼要点：
  1. 工具为中心的 agentic RL 框架直接搬到有状态任务时每 rollout 需独立数据库容器（空间低效）；朴素复用数据库会因跨轨迹状态污染 destabilize 策略更新。
  2. BIRD-RL 用四阶段课程交替提升基础 agent 推理与轨迹自适应 on-policy 探索，避开端到端直训的不稳定。
  3. Trajectory-scoped Persistent Execution Infrastructure 在保证轨迹隔离的前提下安全复用数据库副本，空间 RL 效率提升 12.8 倍（预印本数据，未复现）。
  4. BIRD-CRITIC-SQLite 上 7B/14B 成功率 44.40%/48.00%，对比 Claude-Opus-4.6 Agent 48.20%（预印本数据，未复现）。
  5. 代码公开：https://github.com/bird-bench/BIRD-RL（HKU/NUS/CUHK-Shenzhen）。
- 关闭条件：缺第三方复现与 BIRD-CRITIC-SQLite 之外的环境验证；会议版录用或公开复现后可关。

## 台账登记（本轮 00-rl 未开箱项）

- 2610.29411 The Predictive--Optimization Gap in GuanDan Self-Play（博弈自弈，域契合低）：https://arxiv.org/abs/2610.29411
- 2610.29315 DISRL（动态社区追踪半监督 RL，非 LLM 主线）：https://arxiv.org/abs/2610.29315
- 2610.29075 Value-Rectified Distillation for Flow-based Offline RL（离线 RL+flow，与既有箱层次不同但来源单一）：https://arxiv.org/abs/2610.29075
