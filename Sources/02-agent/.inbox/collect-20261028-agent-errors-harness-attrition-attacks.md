# 投递：Agent 错误自愈、上下文管线损耗、MCP 注入攻击与官方 harness 案例（2026-10-28 daily）

> 巡检通道：arXiv API（cs.AI+LLM agent / tool use+cs.CL 查询）+ langchain RSS（www.langchain.com/blog/rss.xml）。窗口 2026-10-27T00:00Z~2026-10-28T01:10Z。判重：2610.36471 / 2610.36114 / 2610.36108 未见于 `Sources/`；blog.design-agent 链接未见于 `Sources/`；昨日已投的 company-harness、两篇 context-engineering（RSS pubDate 2026-10-26T15:32Z 批次）复查确认已在 10-24/10-27 投递登记，不重复建块。本轮 02-agent 无原件（配额所限）。

## E1 · ReInBench：什么时候该介入，什么时候等 agent 自愈

- 获取日期：2026-10-28
- 来源 URL：<https://arxiv.org/abs/2610.36471>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖 web/computer-use 任务里 LLM agent 错误事件与自愈行为的实证测量（何时介入 vs 等待）；不覆盖介入型运维系统的部署效果。
- 证据等级：A
- 可提炼要点：
  1. 数据集：ReInBench 含 1,259 条 agent 轨迹、1,403 个错误事件（computer-use 与 web 两类任务）（预印本数据，未复现）。
  2. 研究问题三件套：自愈的频率与速度、自愈与后续执行/任务完成度的关系、自愈的可预测性——把「外部介入时机」变成可测量对象，为 agent 运行时监控（本域 10-20 trajectory-audit-safety 线）提供事件层证据。
- 关闭条件：无原件，自愈判定标注协议与数据集许可证未核；引用错误分类前须回论文附录。

## E2 · 上下文是管线不只是窗口：harness 截断造成的信息损耗实测

- 获取日期：2026-10-28
- 来源 URL：<https://arxiv.org/abs/2610.36114>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖工具型 agent harness 在「工具输出进入模型前」的截断行为实测（Linux 内核 trace 注入故障定位任务）；不覆盖一般意义的长上下文窗口调度。
- 证据等级：A
- 可提炼要点：
  1. 反直觉测量：720 次运行中最大单次 prompt 只占上下文的 5.75%（窗口近乎空闲），但全部 11,189 条工具结果中 3,827 条（约 1/3）在到达模型前即被截断，且被截结果全部变成坏 JSON（预印本数据，未复现）。
  2. 机理：harness 按固定长度切 JSON 文本，不是均匀缩短而是整段删除尾部字段——「窗口大小 + 最终正确率」两个常规指标都看不见这层损耗，评估 agent 需要第三个指标（管线保真）。
  3. 跨箱链：与 04-benchmarks 域 kw-bench（同轮投递）及本域 10-26 agents-fail-harness 构成「harness 即误差源」三角，合箱时互相引用不复制事实。
- 关闭条件：无原件；「每刀都破坏 JSON」的截断器实现细节未核，引用前回原文 §measurement。

## E3 · Log-To-Leak：利用 MCP 工具元数据注入诱导事后额外调用

- 获取日期：2026-10-28
- 来源 URL：<https://arxiv.org/abs/2610.36108>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖 MCP 工具的自然语言 metadata 作为 prompt injection 面上的一种「加性事后日志攻击」——在最后一次合法调用之后再诱发一次攻击者控制的调用；不覆盖绕过登录/付费墙类攻击步骤，仅在概念层登记；防御评估数字未在本块展开。
- 证据等级：A
- 可提炼要点：
  1. 攻击面定位：agent 经 MCP 访问外部工具时，工具描述用自然语言书写，本身构成注入面——属既有 tool-poisoning 面的子类，但载荷目标是 user query、MCP server 名、server 响应与 agent 响应四要素。
  2. 操作化四元组（原文口径）：Trigger / Tool Binding / Justification / Pressure；评估把「调用是否成功、载荷保真度、合法行为是否保留」拆开分别测量，覆盖 5 个 MCP server（其余设定在截断处，登记待核）。
  3. 登记姿态：本块主箱归 02-agent（agent-safety 线），03-mcp 侧的协议文档若要引用「工具元数据是攻击面」，用「见本块」指针，不重复登记。
- 关闭条件：无原件，四种被评估 agent 的数量与成功率区间未核（摘要截断）；引用任何攻击成功率数字前必须回原文；与 10-25 agent-security-verification-bench 投递查重过（不同 arXiv ID）。

## E4 · LangChain 官方：Content Studio——Slack 内的开源设计 agent 与其 harness

- 获取日期：2026-10-28
- 来源 URL：<https://www.langchain.com/blog/design-agent>
- 本地原件：—
- 适用范围：B 级厂商自述（官方工程博客，RSS pubDate 2026-10-27T17:05Z，为该批 10-26 三篇打包时间戳之外的独立条目）；覆盖 LangChain 对内部设计 agent 的架构叙述；因其自我报告性质，不构成效果的外部验证，不作定量结论来源。
- 证据等级：B
- 可提炼要点：
  1. 事实登记：Content Studio 定位为「Slack 内的开源 design agent」，产出 on-brand 视频、图形与 deck，并配一套支撑该 agent 的 harness——与昨日 company-harness 五组件投递（`collect-20261027-langchain-company-harness.md`）同属该公司「harness 产品化」叙事，引用时优先回指彼块框架。
  2. 时间戳警示沿用昨日投递头部：langchain RSS 同批条目 pubDate 为批量时间，本块日期需以页内 JSON-LD datePublished 复核。
- 关闭条件：未抓取文章正文与开源仓库许可证，「开源」口径（repo、license）待核；正文提炼进任何文档前须先补这两项。
