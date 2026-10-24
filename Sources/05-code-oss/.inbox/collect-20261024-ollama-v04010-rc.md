# 投递：ollama v0.40.10 与 v0.40.11-rc0（2026-10-24 daily）

## E1 · ollama v0.40.10：Nemotron 3.5 Bolt E4B 上架本地运行

- 获取日期：2026-10-24
- 来源 URL：https://github.com/ollama/ollama/releases/tag/v0.40.10
- 本地原件：—
- 适用范围：官方 release 说明（A 级），发布 2026-10-23T15:03Z；覆盖该版本新增模型支持声明；不覆盖性能与量化后的实测质量。
- 证据等级：A
- 可提炼要点：
  1. 版本主题：接入 NVIDIA Nemotron 3.5 Bolt E4B——官方描述为 Gemma 4 基座的较小视觉-语言模型，面向快速本地对话、图像理解与工具使用，支持 128K token 上下文。
  2. 结构细节：模型带 DFlash draft 用于 speculative decoding——本地推理栈把投机解码草稿模型作为发行单元之一，与 vllm 线（10-19 已登记）证据互补。
  3. 版本节奏：已登记序列 v0.40.6→v0.40.8（10-18 轮）之后，本窗口新增 v0.40.10；中间的 v0.40.9（2026-10-22T01:33Z）落在 24 小时窗外且此前未登记，见文末台账。
- 关闭条件：`ollama run nemotron-3.5-bolt:e4b` 的实测吞吐与内存占用公开资料未给；需要一次本地或第三方实测引用后关。

## E2 · ollama v0.40.11-rc0：qwen3coder 闭合标签保持、llama.cpp b11845、Phonon 语音目录

- 获取日期：2026-10-24
- 来源 URL：https://github.com/ollama/ollama/releases/tag/v0.40.11-rc0
- 本地原件：—
- 适用范围：官方 RC release 说明（A 级），发布 2026-10-24T00:30Z；覆盖 RC 变更清单（6 条 PR 摘要）；不覆盖 stable 版最终内容。
- 证据等级：A
- 可提炼要点：
  1. 工具调用正确性修复：`qwen3coder: preserve literal function closing tags in parameters`（#19228）——函数闭合标签被吞/改写属于工具调用解析层缺陷，RC 阶段修复。
  2. 集成线：`launch: use allocated context for OpenCode`（#19193）说明 OpenCode 类编码 agent 已进入 ollama 的启动适配清单；`llama.cpp version bump b11845`（#19250）。
  3. 新硬件/运行时面：mlxrunner 出现 `Phonon` 语音相关两条 PR（#19234、#19242，语音目录与发音处理）——MLX 后端在语音任务上的扩展值得与 05-code-oss 既有推理栈箱并看。
- 关闭条件：RC 未 stable（发布不足 12 小时）；关闭条件为 v0.40.11 stable 发布后与本 RC 差异核对。
