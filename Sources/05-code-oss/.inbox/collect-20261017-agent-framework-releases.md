# 投递：Agent 框架发布（langchain-core 1.6.12）

> 建议合入箱：`agent-framework-releases`（`Sources/05-code-oss/agent-framework-releases/agent-framework-releases-source.md`）。本轮为 2026-10-17 daily 档。

## E1 · langchain-core 1.6.12：流式事件 extras 字段传播修复

- 获取日期：2026-10-17
- 来源 URL：https://github.com/langchain-ai/langchain/releases/tag/langchain-core%3D%3D1.6.12
- 本地原件：`Sources/05-code-oss/.inbox/originals/github-langchain-core-release-1.6.12.json`
- 适用范围：官方 GitHub release 页（发布 2026-10-16T19:28:44Z，非预发布标签）；仅覆盖 langchain-core 包 1.6.11 → 1.6.12 的增量；不覆盖 langchain / langchain-openai 等同仓其他包。
- 证据等级：A
- 可提炼要点：
  1. 实质变更只有一条：`fix(core): propagate extras on content-block-start events`（PR #41272），即流式消息协议层的 `content-block-start` 事件现在会向下游传播 extras 字段。
  2. 发布节奏：1.6.11（2026-10-15T18:32:35Z）→ 1.6.12 间隔约 25 小时，core 包维持接近每日一 patch 的节奏（release chore PR #41277）。
- 关闭条件：extras 传播对下游消息流的具体兼容性影响需对照 langchain 官方 API 文档（`reference/core`）确认；确认前不写成行为变更结论。
