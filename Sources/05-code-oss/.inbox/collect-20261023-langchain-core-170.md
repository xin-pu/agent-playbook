# 投递：langchain-core 1.7.0 流式工具调用语义变更（2026-10-23 daily）

## E1 · langchain-core==1.7.0：tool-call 增量从快照改为切片

- 获取日期：2026-10-23
- 来源 URL：https://github.com/langchain-ai/langchain/releases/tag/langchain-core%3D%3D1.7.0
- 本地原件：—（release 正文较短，已在要点内提炼；原件链接见来源 URL）
- 适用范围：官方发布记录（release notes），覆盖 langchain-core 1.6.13→1.7.0 增量（2026-10-22T17:47Z 发布）；不覆盖 langchain 主包与其他集成包。
- 证据等级：A
- 可提炼要点：
  1. 行为变更（breaking-adjacent）：工具调用参数现在以 `tool-call-delta` 事件切片流式输出，取代此前 `block-delta` 的「已生成参数快照」语义；直接消费原始流事件与中途 `block-delta` 参数的下游需改读 `tool-call-delta`。
  2. 官方给出的兼容边界：`.tool_calls.get()` 与 `.output` 接口不变；`ChatModelStream.tool_calls` 迭代自 1.6.13 起产出每次新增切片而非累积快照；需保留快照语义的用户可钉 `langchain-core<1.7`。
  3. 唯一新功能提交为 #41257（feat: emit `tool-call-delta`），对 agent harness 类消费方（02-agent 工具调用轨迹采集）是解析器需适配的信号。
- 关闭条件：未核对 SDK 迁移指南是否另行给出 block-delta 到 tool-call-delta 的等价转换示例；人工合箱时并入 agent-framework-releases 箱。

## 台账登记（未达开箱门槛，仅流水）

- 窗口内 vllm / transformers / ollama / openai-agents-python 的 GitHub releases 无新条目（列表已查，最新均早于 2026-10-22T09:00Z）。
