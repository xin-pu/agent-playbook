# 投递：MCP registry 1.8.6 与 csharp/php SDK、progressive-disclosure WG 增量（2026-10-28 daily）

> 巡检通道：GitHub API（api.github.com）。窗口 2026-10-27T00:00Z~2026-10-28T01:10Z。判重：v1.8.6、三个 commit SHA（4a955063/9bbb82e4/2c93da5f）与 PR 号 #1849/#1956/#614/#21 均未见于 `Sources/`；registry 1.8.5 已由昨日 `collect-20261027-mcp-tasks-matrix-ruby-sdk-registry.md` E4 登记，本文件只推版本线增量。窗口内无新增事实：specification 无新 release（最新仍 2026-07-28）、A2A 无新 release（v1.0.1，2026-05-28）、npm `@modelcontextprotocol/sdk` 与 pypi `mcp` 无新发布、servers 最新提交停在 10-24、transports-wg 主干最新提交停在 10-09（10-27 的 pushed 时间来自非默认分支，暂不建块）。原件 1 份（release JSON）存 `.inbox/originals/`。

## E1 · registry v1.8.6：混合负载搜索性能版，搜索词强制 ≥3 Unicode 字符

- 获取日期：2026-10-28
- 来源 URL：<https://github.com/modelcontextprotocol/registry/releases/tag/v1.8.6>
- 本地原件：`Sources/03-mcp/.inbox/originals/github-mcp-registry-v1.8.6-release.json`
- 适用范围：官方 release 说明一手文本（v1.8.6，published 2026-10-27T14:42Z，tag 由 promote 提交 `9c4a96c9` 同刻记录）；覆盖搜索性能、验证流程与部署注意事项；不覆盖 API 面破坏性变更声明，不覆盖 registry 数据模式迁移细节。
- 证据等级：A
- 可提炼要点：
  1. 性能路线：搜索分页先用 covering index 选键再回表取完整记录；按实际参数值做查询计划以同时稳住「宽泛词与稀有词」；namespace 后缀搜索优化——三者都是 10-25 起容量调优线的延续（对照 10-27 投递 E4）。
  2. 用户可见行为变更：非空搜索词要求至少 3 个 Unicode 字符，短查询直接 HTTP 422——这是本轮唯一可能影响第三方客户端的版本条目。
  3. 工程姿态：发布说明包含「可复现 cyclic-load 基准 + 对公开生产数据快照的重复 staging 验证」，promote 提交标题自证「tested 3-CPU database quota」（#1752/#1753 同日合入）；版本线 1.8.4（10-23）→ 1.8.5（10-26，昨日已登记）→ 1.8.6（10-27）。
- 关闭条件：422 短词限制未见面向使用者公告，需在 registry 文档/CHANGELOG 核对是否 breaking；下轮检查是否回滚或放宽。

## E2 · csharp-sdk：AutoDetect 的 405 回退、discover 探针与 OAuth 兜底三连收紧

- 获取日期：2026-10-28
- 来源 URL：<https://github.com/modelcontextprotocol/csharp-sdk/commit/4a95506350afba430abd22aee948855a60cadb47>
- 本地原件：—
- 适用范围：官方 SDK 仓库三个主干提交（另两枚 `52219393` 2026-10-27T02:18Z、`8487dfc8` 2026-10-27T00:45Z 边界窗口内）；覆盖 .NET 实现侧 streamable-HTTP 传输协商与 OAuth 元数据回退的合规性修复；不覆盖协议文本变更，不覆盖其它语言 SDK 行为。
- 证据等级：A
- 可提炼要点：
  1. `#1849`：AutoDetect 探针收到 405 且响应体为 JSON-RPC error 时应回退 SSE——把「405 语义」从裸 HTTP 状态码升级为「状态码 + JSON-RPC 错误体」联合判定，直接充实 streamable HTTP transport 参考层的实现口径。
  2. `#1956`：`server/discover` 探针不得提交（commit）协商出的协议版本——防止能力探测副作用改写会话状态，属协议状态机严格化。
  3. `#1952`：legacy OAuth metadata fallback 改为显式 opt-in——安全默认值收紧，与 10-23 投递 `sdk-auth-transport-skills.md`（ts-sdk auth 线）同方向；三提交均未落任何 release tag，引用需绑 commit SHA。
- 关闭条件：nuget 版本号归属待发布后回填；405 回退与 spec 正式文本是否一致未核对。

## E3 · php-sdk：重连时客户端 transport 泄漏修复等主干三连

- 获取日期：2026-10-28
- 来源 URL：<https://github.com/modelcontextprotocol/php-sdk/commit/9bbb82e4f8bdbd3a04d5c0d585329e74f7dc9d1e>
- 本地原件：—
- 适用范围：官方 php-sdk 主干提交（`9bbb82e4` #614，2026-10-27T21:14Z；另有 `ed8098cb` #613 数组形状类型修复、`e4cb8253` #632 依赖 bump）；覆盖 PHP 实现客户端长会话资源管理缺陷；不覆盖 server 侧，不覆盖 v0.9.0 已发布版本行为。
- 证据等级：A
- 可提炼要点：
  1. 事实：#614 修复 client transport 在 reconnect 时的泄漏——SDK 生态长连接稳定性线新增一例（与 10-27 ruby-sdk E3 通知语义修复同类）；php-sdk 为 `Sources/` 首次登记的语言实现。
  2. 节奏：当前最新 release 仍是 v0.9.0（2026-10-18），三枚主干提交未发版；合箱时并入 SDK 生态箱按 commit 线登记。
- 关闭条件：修复落入哪个 tag 未定；下轮查 releases 回填归属版本。

## E4 · progressive-disclosure-wg 建立 WG 决策台账（decisions 文档合入）

- 获取日期：2026-10-28
- 来源 URL：<https://github.com/modelcontextprotocol/progressive-disclosure-wg/commit/2c93da5f1622ca76a63555d4007a1632922a9466>
- 本地原件：—
- 适用范围：官方 WG 仓库一手提交（PR #21 于 2026-10-27T21:12Z 合入，分支 helloeve/decisions）；覆盖该 WG 从讨论转入决策记录的程序性动作；不覆盖任何具体决策内容（正文未抓取）。
- 证据等级：A
- 可提炼要点：
  1. 主题定位：progressive disclosure（渐进披露工具/资源）此前公开记录见 10-05 提交「limits of tool search」；本轮新增 tracking decisions 文档，标志该 WG 进入有正式决议的治理阶段——与本域 10-20 governance-wg、10-27 治理线投递同族不同 WG，勿并成一条。
  2. 合箱线索：待决策正文拉取（contents API）后再决定是并入 mcp-spec-evolution 还是独立成「工具发现/披露」箱。
- 关闭条件：未读 decisions 文件内容，无法登记任何决议口径；合箱前必须补读原文。
