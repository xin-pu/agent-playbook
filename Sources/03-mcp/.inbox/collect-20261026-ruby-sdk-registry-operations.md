# 投递：MCP SDK 与 registry 生态 24h 窗口（2026-10-26 daily）

> 巡检通道：GitHub API（api.github.com）。窗口 2026-10-25 00:00Z~2026-10-26 01:00Z，另含上一轮运行后未登记的同周提交。`modelcontextprotocol/servers v2.1.0` 已于 2026-10-25 投递（判重命中）；`specification` 无新 release（最新仍为 2026-07-28）。

## E1 · ruby-sdk：会话通知失败改为经 server error handler 上报

- 获取日期：2026-10-26
- 来源 URL：<https://github.com/modelcontextprotocol/ruby-sdk/commit/fc41daeb5>
- 本地原件：—
- 适用范围：官方仓库一手提交记录（非 release），覆盖 ruby-sdk 对「无法送达的 session notification」的错误处理路径变更（PR #631，2026-10-25 18:32Z merge；前置 PR #630 丢弃无法生成的缓冲通知）；不覆盖其它语言 SDK 的对应实现。
- 证据等级：A
- 可提炼要点：
  1. 行为变更：失败的 session notification 从静默丢弃改为通过 server configuration error handler 上报（PR #631 标题口径）。
  2. 关联变更（PR #630）：明确「无法生成的缓冲通知」直接丢弃，界定通知管道的失败语义边界——缓冲≠必达。
  3. 与 2026-10-19 投递的 ruby-sdk conformance 主题同线演进，合箱时并入同一箱追加。
- 关闭条件：未核对 CHANGELOG 与版本号归属（该改动落在哪个 gem 版本）；需 release 注明后升级为版本级结论。

## E2 · MCP registry 生产部署：ingress 稳定性修复与 GKE 磁盘升级上线

- 获取日期：2026-10-26
- 来源 URL：<https://github.com/modelcontextprotocol/registry/commit/e47b29ec6>
- 本地原件：—
- 适用范围：官方仓库一手提交记录，覆盖 registry 生产环境运维变更（2026-10-25 22:38~23:24Z 三连 deploy：ingress 重启修复、GKE boot disk 升 50GB balanced）；不涉及协议、API 面或数据模式变更。
- 证据等级：A
- 可提炼要点：
  1. `fix(deploy): reduce ingress restarts under load`（PR #1737）经 #1738 promote 到生产——registry 公开服务此前存在负载下 ingress 重启的稳定性缺陷。
  2. GKE boot disk 统一升级到 50GB balanced 存储（#1739/#1740）——索引规模增长的运维侧信号。
  3. 运维类证据，仅支撑「registry 服务成熟度」叙述，不构成任何接口或规范结论。
- 关闭条件：无用户可见事故报告佐证影响面；若后续 registry 发布状态页事故复盘，回引本块。

## 台账登记

- 2026-10-26：npm `@modelcontextprotocol/sdk` latest 1.32.2，10-24 后无新版本；pypi `mcp` 10-24 后无新版本；`a2aproject/A2A` 最新仍 v1.0.1（2026-05-28）；python-sdk/ts-sdk/inspector/swift-sdk 最新提交均早于窗口且已见于 2026-10-25 投递（判重排除）。
