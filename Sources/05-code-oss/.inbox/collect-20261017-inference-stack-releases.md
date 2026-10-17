# 投递：推理栈发布（transformers v5.20.1 / ollama v0.40.6）

> 建议合入箱：`inference-stack-releases`（`Sources/05-code-oss/inference-stack-releases/inference-stack-releases-source.md`）。本轮为 2026-10-17 daily 档，时间窗 2026-10-16 01:00 UTC ~ 2026-10-17 01:00 UTC。

## E1 · transformers v5.20.1 补丁版并入 Reflection AI 的 Beam 模型

- 获取日期：2026-10-17
- 来源 URL：https://github.com/huggingface/transformers/releases/tag/v5.20.1
- 本地原件：`Sources/05-code-oss/.inbox/originals/github-transformers-release-v5.20.1.json`
- 适用范围：官方 GitHub release 页（发布 2026-10-16T13:02:29Z，非预发布标签）；覆盖 v5.20 线补丁说明与 Beam 模型收录的官方定位；不覆盖 Beam 自身技术报告与能力基准验证。
- 证据等级：A
- 可提炼要点：
  1. v5.20.1 收录 Reflection AI 的新模型 Beam，官方定位为 token 高效、面向 coding 与 agentic 用例的前沿规模模型，主打自有硬件/基础设施/云上的自托管部署与定制；文档入口 `huggingface.co/docs/transformers/main/en/model_doc/beam`。
  2. 补丁主线是修复回归：v5.20.0（2026-10-15T18:05:36Z）破坏了在旧版 torch 上加载模型的能力，v5.20.1 声明修复；另含 auto mappings 修复（PR #49664）与 HunYuan-VL 图像加载修复。
  3. 版本节奏：v5.20.0 → v5.20.1 间隔约 19 小时，minor 发布后补丁紧随，合入 `inference-stack-releases` 时可作为「v5.20 小版本线」连续条目处理。
- 关闭条件：Beam 的定量能力声明需补 Reflection AI 模型卡/技术报告（A 级）或第三方评测后回写；未补齐前不得引用其性能表述。

## E2 · ollama v0.40.6（预发布标签）：q2_0 GGUF 类型与云端 clef 模型

- 获取日期：2026-10-17
- 来源 URL：https://github.com/ollama/ollama/releases/tag/v0.40.6
- 本地原件：`Sources/05-code-oss/.inbox/originals/github-ollama-release-v0.40.6.json`
- 适用范围：官方 GitHub release 页（2026-10-16T22:00:46Z，API 标记 `prerelease: true`，changelog 对比区间为 `v0.40.5...v0.40.6-rc0`）；仅覆盖 4 条合入项；不代表 v0.40.6 正式版发布口径。
- 证据等级：A
- 可提炼要点：
  1. GGUF 格式新增 `q2_0` 张量与文件类型（PR #18967），为 2-bit 量化档位补充显式类型。
  2. Windows 平台修复：阻止孤儿 runner 进程（PR #18500）。
  3. Ollama Cloud 上线名为 `clef` 的模型服务（PR #19036）；`--ask` 模式改用标识符作为问题键（PR #19041）。
- 关闭条件：需 ollama.com 云端模型页或正式 release（非预发布）佐证 `clef` 身份与 v0.40.6 正式口径；补齐后可关。
