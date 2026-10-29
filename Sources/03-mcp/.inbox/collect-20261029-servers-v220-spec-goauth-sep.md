# 投递：MCP servers v2.2.0 发布准备、Tasks 支持矩阵与 go-sdk 认证收紧（2026-10-29 daily）

> 巡检通道：GitHub REST API（`api.github.com`，unauthenticated，本轮合计约 27 次调用未触限）。npm `@modelcontextprotocol/sdk` 无窗口内发布（latest 1.32.2）；pypi `mcp` 无窗口内发布（当前 2.3.0）；`a2aproject/A2A` 无新 release（最近 v1.0.1，2026-05-28）。

## E1 · servers 仓库 v2.2.0 发布链：CalVer 2026.10.28 打戳与合并发车

- 获取日期：2026-10-29
- 来源 URL：<https://github.com/modelcontextprotocol/servers/commit/194cc86e3ae6400958555bd4116849d822d69263>
- 本地原件：—
- 适用范围：官方仓库提交记录（A 级）；覆盖 v2 分支 release 工程流程（PR #5342「release-v2.2.0」合并、PR #5338/#5336 同链路、#5341 fetch server 的 certifi→2026.10.23）；不覆盖 v2.2.0 的正式 tag 发布与 CHANGELOG 条款。
- 证据等级：A
- 可提炼要点：
  1. 发布节奏口径：Python 侧采用 CalVer 打戳（commit 74af74c8ba「stamp Python CalVer versions for 2026.10.28」），JS 侧走 changeset 版本车（cabf72d388「chore: version packages」）。
  2. 供应链维护：依赖安全更新进入发布链（certifi 提升至 2026.10.23）。
  3. 与 `mcp-server-ecosystem` 既有箱（v2.1.0 记录，2026-10-25 投递）构成版本节奏线，合箱追加。
- 关闭条件：v2.2.0 正式 release tag 尚未出现于 releases 列表（截至本轮）；下轮巡检确认 tag 与发布说明后可关。

## E2 · 规范仓库文档批次：Claude Code/Claude.ai 标记支持 Tasks，Kiro Crew 入扩展矩阵

- 获取日期：2026-10-29
- 来源 URL：<https://github.com/modelcontextprotocol/modelcontextprotocol/commit/f44325dc6718e974b90159df84996f03bf26a3d8>
- 本地原件：—
- 适用范围：官方 spec 仓库文档提交（A 级）；覆盖 Tasks 扩展的客户端支持矩阵与示例修订（同日另有 #3461 Kiro Crew 入矩阵、#3462 embedded resource 示例把 annotations 移出 resource、#3364 legacy extension negotiation 文档合并）；不覆盖规范行为条款变更。
- 证据等级：A
- 可提炼要点：
  1. Tasks 采纳面：支持矩阵新增 Claude Code 与 Claude.ai 两个官方客户端（PR #3459）。
  2. 示例语义修正：embedded resource 示例中 annotations 不再置于 resource 内（#3462），属文档级 schema 用法澄清，合箱时与 `mcp-spec-evolution` 箱既有块互引。
  3. 扩展协商文档：legacy extension negotiation 说明经 #3364 合并，指示旧客户端兼容路径仍在被整理。
- 关闭条件：无条款级 diff 原件；若 Tasks 矩阵继续扩充或进入新版本 RC changelog，届时按 A 级 changelog 复核后关。

## E3 · go-sdk：PKCE 收紧为仅授权码流程强制

- 获取日期：2026-10-29
- 来源 URL：<https://github.com/modelcontextprotocol/go-sdk/commit/8c1dbca6e5c08a176fd98d0debbfc8fbfa8d3efa>
- 本地原件：—
- 适用范围：官方 SDK 提交（A 级）；覆盖 MCP 授权实现中 PKCE 强制范围的行为变更（PR #1465：仅 authorization code flows 要求 PKCE）；不覆盖 token 交换实现与其他 SDK 的同步进度。
- 证据等级：A
- 可提炼要点：
  1. 行为变更：此前更保守的强制范围收窄，对齐 OAuth 2.1 对「授权码流程必须 PKCE」的口径；隐含其他流程（如 device code）不再硬性要求。
  2. 同日其他 go-sdk 提交（#1468 连接关闭错误精简、#1464 向中间件暴露 JSON-RPC request id、#1208 日志降级受 MCPGODEBUG 门控）反映中间件 API 在成形，`MCP OAuth resource server` 主线合箱时引用。
- 关闭条件：需核对其他语言 SDK 是否同步该策略（python/ts 窗口内无默认分支提交）；跨 SDK 一致后再关。

## E4 · interceptors 实验扩展：SEP 移除 chain 概念、保留执行机制

- 获取日期：2026-10-29
- 来源 URL：<https://github.com/modelcontextprotocol/experimental-ext-interceptors/commit/07c89a24879eb2231e2afb72942643ebc8dfe485>
- 本地原件：—
- 适用范围：官方实验扩展仓库的 SEP 提案修订（A 级）；覆盖拦截器扩展设计向「执行机制、无链式结构」收敛的方向；不覆盖已入 spec 的稳定行为。
- 证据等级：A
- 可提炼要点：
  1. 设计口径：SEP 明确删去 interceptor chain 概念，仅保留执行机制（PR #44），即不再把拦截器组织为有序链。
  2. 该仓库属 experimental-ext-* 系列，与 file-uploads 同层级（`agent-protocols-landscape` 箱既有记录），合箱时并入扩展生态子线。
- 关闭条件：提案仍在演进、无稳定文本；进入 RC/稳定版本前持续跟踪，版本冻结后关。

## 台账登记

- 窗口内有推送但默认分支无增量提交（复查，无增量）：registry（v1.8.6 已于 10-28 登记，推送 23:42Z 未在 master 侧）、typescript-sdk、python-sdk、ruby-sdk、kotlin-sdk、quickstart-resources、transports-wg。
- 配额受限顺延：php-sdk `5d311d69b9`（Session::save 误清读取失败会话修复）+ `c26cf5c890`（未知会话 DELETE 回 404）+ `9a7fea08d0`（PSR-6 store/bus）、csharp-sdk `9b50c3d094`（delegating server 的 legacy output schema 修复）、rust-sdk `9e0783d0`（取消场景保留协议错误回复）、inspector v2.13.0 milestone 合并 + fast-uri→3.1.9 四项中危通告（`3be6b501dc`）。
- npm `@modelcontextprotocol/sdk` latest 1.32.2、pypi `mcp` 2.3.0：窗口内无发布，台账登记。
