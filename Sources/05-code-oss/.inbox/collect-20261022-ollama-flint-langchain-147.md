# 投递：开源栈窗内发布（ollama v0.40.8、langchain 1.4.7/core 1.6.13）（2026-10-22 daily）

## E1 · ollama v0.40.8：收录 Recursive Flint 编码模型

- 获取日期：2026-10-22
- 来源 URL：https://github.com/ollama/ollama/releases/tag/v0.40.8
- 本地原件：—
- 适用范围：官方 release 页（2026-10-21T16:20Z 发布）；覆盖 ollama 运行时的模型收录与修复节奏；不覆盖模型权重本身（仅登记链接）。
- 证据等级：A
- 可提炼要点：
  1. 版本主题为 "Recursive Flint"：把 Recursive 的编码模型引入 Ollama 库（https://ollama.com/library/flint），面向仓库级 agent 工作（读不熟代码、追 bug、实现特性、补测试）。
  2. Flint 规格口径：支持 reasoning 与多轮 tool use，上下文窗口 262K token。
  3. 上一版 v0.40.7（10-18）已在 `collect-20261018-ollama-v0407-rc` 登记，本块为其 stable 化跟进，建议人工合箱时并块。
- 关闭条件：release notes 全文未存档（仅取首段），且 Flint 的量化档位/性能对比缺独立评测；下一版发布或出现第三方评测后关。

## E2 · langchain==1.4.7 与 langchain-core==1.6.13：tool-call-delta 流入消费侧

- 获取日期：2026-10-22
- 来源 URL：https://github.com/langchain-ai/langchain/releases/tag/langchain%3D%3D1.4.7
- 本地原件：—
- 适用范围：官方 release 页（2026-10-21T21:39Z 发布）；覆盖 langchain v1 包的增量变更清单；不覆盖 langsmith 平台侧。
- 证据等级：A
- 可提炼要点：
  1. 功能增量 #41246：core、langchain、standard-tests 的流消费者（stream consumers）开始读取 `tool-call-delta` 事件——工具调用参数的增量流式传输进入稳定消费面。
  2. 其余为 lockfile 与依赖 bump（certifi 2026.10.19、aiohttp 3.14.5 等），无 breaking change 标注。
  3. 同日 `langchain-core==1.6.13`（20:43Z）与 `langchain-perplexity==1.4.2`（17:31Z）随车发布，节奏型条目见台账。
- 关闭条件：无遗留缺口；1.4.8+ 出现或该特性写入迁移文档时并块更新即可关。

## 台账登记（本轮窗内 05-code-oss 未开箱项）

- langchain-perplexity==1.4.2（2026-10-21T17:31Z，伙伴包随车发布）：https://github.com/langchain-ai/langchain/releases/tag/langchain-perplexity%3D%3D1.4.2
- vllm 最新仍为 v0.32.0（10-18，已登记）；transformers 最新仍为 v5.20.2（10-19，已登记）；pytorch 无新版；openai-agents-python 无新版（复查，无增量）。
