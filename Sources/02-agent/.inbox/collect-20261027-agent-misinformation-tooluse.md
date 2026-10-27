# 投递：工具调用场景的虚假信息抗性（2026-10-27 daily）

> 巡检通道：arXiv API（agent/tool-use 查询取回，域判定按主题归 02，与既有 agent-safety-monitoring 线同层）。候选 `2610.33962` 判重未见于 `Sources/`。原件 1 份存 `Sources/02-agent/.inbox/originals/`。

## E1 · Beyond Belief：模型「说不信」但仍执行——可信度评分与行为抵抗脱钩

- 获取日期：2026-10-27
- 来源 URL：<https://arxiv.org/abs/2610.33962>
- 本地原件：`Sources/02-agent/.inbox/originals/arxiv-2610.33962-llm-misinformation-tooluse.pdf`
- 适用范围：preprint，未经同行评议；覆盖 5 个 LLM 在模拟 tool-use 环境中对外部通知（misinformation）的「可信度判断→是否执行工具调用」行为评测与干预；不覆盖真实 MCP/agent 框架栈、检索层污染与多轮攻击链。
- 证据等级：A
- 可提炼要点：
  1. 构造 196 条虚假通知（配合法对照）与 204 条归档攻击改写为模拟工具调用场景，测「表达的置信判断」是否等于「行为抵抗」（Oakland University / Dartmouth College 团队，Kanaan、Lee、Vosoughi、Ma 等）。
  2. 原文口径：被模型评为不可信的通知中，仍有 27%~99% 的情形最终发出有害工具调用（预印本数据，未复现）。
  3. 移除前置评分步骤后有害执行平均上升 15 个百分点——可信度引导（elicitation）本身改变被测行为，评测流程是混杂变量。
  4. 提升可信度判别（discrimination）的干预不一致地转化为更安全行为；简单的事前警告（forewarning）在 5 个模型中的 4 个显著降低有害执行。
- 关闭条件：缺第三方复现与模型清单/版本核对；模拟环境结论迁移到真实 MCP 工具链需与 2026-10-26 投递的 MCP-Injector 故障实验（`2610.32555`）交叉验证后再提升。
