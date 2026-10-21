# 投递：MCP TypeScript SDK 落地 Skills 扩展与转发参数修复

## E1 · SEP-2640 Skills 扩展合入 TypeScript SDK（server + client）

- 获取日期：2026-10-21
- 来源 URL：https://github.com/modelcontextprotocol/typescript-sdk/commit/46d9c9921b6542e813c1ecc5f9fc964085e8e3bb
- 本地原件：—（GitHub commit 页面为公开直链，未另存快照）
- 适用范围：官方仓库 main 分支 commit（2026-10-20T14:31:27Z，PR #3047），属代码层实现进度证据；不等同于规范发版——Skills 扩展（SEP-2640）尚未随 spec release 冻结；仅覆盖 TypeScript SDK 的 server 与 client 两侧。
- 证据等级：A
- 可提炼要点：
  1. `feat: Skills extension (SEP-2640) for server and client (#3047)` 合入 TypeScript SDK，是该扩展从「规范提案」进入「官方 SDK 实现」的节点。
  2. 与既有箱增量衔接：`03-mcp/.inbox/collect-20261017-mcp-skills-extension.md` 与原件 `github-mcp-ext-skills-implementations-2026-10-16.md` 中，TypeScript SDK 状态还是 `in progress`（PR #2818，Phase 1: schemas/client ops/server handlers，tracking issue #2798）；本 commit 表明该路线已合并落地，实现清单应把 TS 行从 in progress 升级为 available。
  3. commit 含 Co-authored-by（社区贡献者与 Cloudflare 工程师），说明该 SEP 的参考实现由跨组织协作完成。
- 关闭条件：待 Skills 扩展进入 spec 版本发布（changelog 条目）后关闭；在此之前需跟踪是否出现 breaking 修订或 PR revert。

## E2 · server 侧 forwarded params 保持与低层连接支持修复

- 获取日期：2026-10-21
- 来源 URL：https://github.com/modelcontextprotocol/typescript-sdk/commit/c05225a636c679870b65f8ca4fe83a76ea1cf113
- 本地原件：—
- 适用范围：官方仓库 main 分支 commit（2026-10-20T22:09:57Z，PR #3057），覆盖 TypeScript SDK server 传输层的 `_meta`/forwarded params 传递行为与现代低层连接支持；不构成规范文本变化，仅实现行为修正。
- 证据等级：A
- 可提炼要点：
  1. `fix(server): preserve forwarded params and support modern low-level connections (#3057)`：修复转发参数在 server 侧丢失的问题，属于 streamable HTTP 传输实现正确性一类缺陷。
  2. 与 06 commit 同仓库同日两笔合入，TypeScript SDK 处于活跃发版前窗口（最近 release 仍为 2026-10-05 的 v2.3.1），后续应关注 release 节奏以确认该 fix 进入哪个版本。
- 关闭条件：该 fix 被包含进下一个带 changelog 的 release 后关闭；若未发布即关闭则需引用 release 页链接。
