# 投递：ollama v0.40.11 stable 发布（2026-10-26 daily）

> 巡检通道：GitHub API（api.github.com）。本块关闭 2026-10-24 投递 `collect-20261024-ollama-v04010-rc.md#E2` 的关闭条件（「v0.40.11 stable 发布后与本 RC 差异核对」）。v0.40.11 stable 发布于 2026-10-24T00:30:13Z，其 stable tag URL 判重未见于 `Sources/`（RC URL 已登记，两个 tag 不视为同源）。其余清单仓库（vllm、transformers、pytorch、langchain、llama_index、openai-agents-python、两个 MCP SDK）在窗口内均无新 release。

## E1 · ollama v0.40.11：macOS 语音生成 GA 与 d3 决策模型进库

- 获取日期：2026-10-26
- 来源 URL：<https://github.com/ollama/ollama/releases/tag/v0.40.11>
- 本地原件：—
- 适用范围：官方 release 说明原文（发布页），覆盖 v0.40.11 stable 相对 v0.40.10 的用户可见能力；不覆盖逐条 commit 级修复清单（以官方 compare 页为索引）。
- 证据等级：A
- 可提炼要点：
  1. 语音生成登 macOS：`ollama run` 可在生成同时播放文本或模型回复，应用可经 OpenAI 兼容 `/v1/audio/speech` 端点流式取音频（官方示例模型 phonon）。
  2. 新增 d3 决策模型系列：引入 vLLM Semantic Router 的 decision models，支持分类/是否判断/带概率打分，含 2B、4B、9B、27B 四档；用法为 `ollama run d3 ... --ask`。
  3. 与 2026-10-24 RC 登记的差异：RC 笔记覆盖 qwen3coder 闭合标签、llama.cpp b11845、Phonon 语音目录；stable 的发布说明把 Phonon 语音与 d3 列为正式特性——stable 口径为功能 GA，RC 口径为预发布目录准备。
- 关闭条件：d3 与 vLLM Semantic Router 上游实现的一致性未核对；如需引用「推理路由/决策模型生态」结论须回指 vllm-project/semantic-router 原件。
