# 投递：EpiSEM-Bench——证据缺失下的 Agent 安全评测（2026-10-24 daily）

## E1 · 300 对匹配安全/不安全任务测「缺证据时的越权执行与证据恢复」

- 获取日期：2026-10-24
- 来源 URL：https://arxiv.org/abs/2610.31650
- 本地原件：`Sources/04-benchmarks/.inbox/originals/arxiv-2610.31650-episem-bench-missing-evidence.pdf`
- 适用范围：preprint，未经同行评议；覆盖工具调用 LLM agent 在「工具响应省略安全相关事实」时的执行安全评测（6 个领域、300 对匹配任务）；不覆盖真实部署环境与非英文任务语料。
- 证据等级：A
- 可提炼要点：
  1. 失败模式刻画：用户请求正当、工具返回的每一条陈述都为真，但只要响应省略了关键安全事实，agent 仍可能执行被禁止的动作——评测对象是「证据缺失」而非「证据错误」。
  2. 构造：可执行 benchmark，配对设计（每对共享一个 unsafe 与一个 safe 变体），通过系统性抑制关键事实测 unsafe execution、安全边界与 evidence recovery；并给出「最小观测失败基数」概念，含全证据失败与穷举无失败两类端点。
  3. 审计解耦：独立的 audit tool 检查 agent 是否主动索求缺失事实、并在拒绝禁止动作的同时完成允许任务——把「纠错行为」与「拒答」分开计量。
  4. 与 agent-safety-monitoring（02-agent）层次不同：这是评测构造侧证据，主箱定在 04-benchmarks。
- 关闭条件：模型主结果与 leaderboard 数字未从摘要核出；需读全文实验节并确认基准可执行仓库开放后关。
