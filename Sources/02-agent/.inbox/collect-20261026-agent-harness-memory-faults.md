# 投递：agent harness、记忆与工具故障（2026-10-26 daily）

> 巡检通道：arXiv API（export.arxiv.org，经 agent/benchmark 查询取回，域判定按主题归 02）。本批 3 篇 v1 提交日期 2026-10-23，判重后均未见于 `Sources/`。原件 2 份存 `Sources/02-agent/.inbox/originals/`。

## E1 · When Agents Fail：harness 与模型的归因评测框架

- 获取日期：2026-10-26
- 来源 URL：<https://arxiv.org/abs/2610.32483>
- 本地原件：`Sources/02-agent/.inbox/originals/arxiv-2610.32483-agents-fail-harness.pdf`
- 适用范围：preprint，未经同行评议；覆盖通用 agent harness（OpenCode、Codex CLI、Pi CLI、DeepAgents）与底层模型交互的归因度量；不覆盖单模型能力评测与专用域 agent。
- 证据等级：A
- 可提炼要点：
  1. 主张：agentic benchmark 成绩反映模型与 harness 的联合行为，harness 必须通过与模型的交互来评测，而非组件级摘要。
  2. 五度量框架：Valid Completion Rate（有效完成率，不看任务正误只看能否正常交付可评结果）、Model-Harness Fit、Cross-Model Fit、Interaction Residuals（配对特异强弱）、Token Load（含失败尝试的 token 成本）。
  3. 实验规模（原文口径）：四个 harness 与多个模型在 SWE-bench-45、Terminal-Bench 2、VitaBench、LOCA-Bench 等六项基准上交叉评测（预印本数据，未复现）。
- 关闭条件：缺第三方以同框架复跑其它 harness 的记录；harness 版本随时间漂移，结论需绑定其评测时的版本号。

## E2 · MCP 真实故障下的工具调用：规模换不来容错

- 获取日期：2026-10-26
- 来源 URL：<https://arxiv.org/abs/2610.32555>
- 本地原件：`Sources/02-agent/.inbox/originals/arxiv-2610.32555-mcp-fault-tolerance.pdf`
- 适用范围：preprint，未经同行评议；覆盖经 MCP 暴露的外部工具发生持续/瞬时/间歇故障时的 agent 鲁棒性评测；不覆盖工具结果语义错误与权限层攻击。
- 证据等级：A
- 可提炼要点：
  1. MCP-Injector：协议感知的故障注入中间件，插在 MCP 工具调用路径上，按可播种调度注入三类持续性故障；故障模型从 1,774 个开源 MCP 仓库的 57,240 条 issue/PR 线程挖掘的真实事故分布校准（原文口径）。
  2. 实验规模：1,350 个实验格，交叉 20B/120B 两档 backbone、三个 agent 栈（自研多轮 plan-and-execute、OpenAI Agents SDK、LangChain）与三种注入条件。
  3. 原文结果口径：永久型为主的故障下三个栈均显著掉分，更大 backbone 不换来容错（标题即结论 Scale Does Not Purchase Fault Tolerance）；超时类失败占绝大多数（10 个失败模式中除两种外全为 wall-clock 超时而非轮次耗尽）；LangChain 完成率高（95~97%）而 OpenAI Agents SDK 偏低（88~95%）（预印本数据，未复现）。
- 关闭条件：缺对 MCP 官方生态外协议（如 A2A）的同类注入验证；57,240 线程的挖掘脚本未核对前不引用故障分布占比。

## E3 · 观点：agentic memory management 是 IR 的下一个前沿

- 获取日期：2026-10-26
- 来源 URL：<https://arxiv.org/abs/2610.32464>
- 本地原件：—
- 适用范围：preprint，未经同行评议；perspective 论文，覆盖把 agent 记忆管理定位为信息检索研究扩展的问题框架；不覆盖具体记忆系统实现与实验。
- 证据等级：A
- 可提炼要点：
  1. 定位：信息管理正在 agent 内部以记忆管理形式发生，AMM 研究对象为智能体记忆中的结构、分析、组织、存储、搜索、检索与「使用」。
  2. 给出系统级框架与记忆对象的计算分类学：constants、functions、operators 三类（摘要口径，细节需原件）。
  3. 为既有 agent-memory 各箱提供「学科归属」层面的引用锚点（IR 视角），与实现层证据块分层。
- 关闭条件：纯观点论文无实验数值；需确认后续是否有配套综述或基准落地，否则只作概念定位引用。

## 台账登记

- 2026-10-26：`blog.langchain.dev/rss/` 返回 Webflow HTML 页（215KB，无 `<item>` 结构），本轮无可用条目，未重试。
- 同日 arXiv 批次的 harness/基准类论文 `2610.32285`（TraceTrial-Bench）按主题归入 04-benchmarks 投递，不重复登记。
