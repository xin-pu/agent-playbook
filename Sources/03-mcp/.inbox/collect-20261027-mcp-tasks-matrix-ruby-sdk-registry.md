# 投递：MCP Tasks 支持矩阵、file-uploads charter 与 SDK/registry 增量（2026-10-27 daily）

> 巡检通道：GitHub API（api.github.com）。窗口 2026-10-26 00:00Z~2026-10-27 01:00Z。specification 无新 release（最新仍 2026-07-28）；A2A 无新 release（最新 v1.0.1，2026-05-28）；npm `@modelcontextprotocol/sdk` 与 pypi `mcp` 窗口内无新发布；servers/conformance/ext-apps/ext-server-card/triggers-events 窗口内无新提交。判重：PR #3446、Tasks 支持矩阵、`1.8.5`、`shared buffers` 均未见于 `Sources/`（`1.8.2` 字串命中为 registry 1.8.2 无关版本，ruby-sdk 1.8.2 本体未登记）。

## E1 · 规范文档站 client 支持矩阵新增 Tasks 列：14 客户端中仅 1 家勾选

- 获取日期：2026-10-27
- 来源 URL：<https://github.com/modelcontextprotocol/modelcontextprotocol/commit/54b91cdb8f21825ce586c452704f319d49866ef8>
- 本地原件：—
- 适用范围：官方规范文档仓库一手提交（2026-10-26T21:57Z，标题原文含拼写错误 `suport`；修改 `docs/extensions/client-matrix.mdx`，+16/−16），覆盖 Tasks 扩展在既有社区维护支持矩阵中的状态登记；不覆盖 Tasks 语义本身变更。
- 证据等级：A
- 可提炼要点：
  1. 矩阵原本已含 MCP Apps / OAuth Client Credentials / Enterprise Auth / Skills 四列，本提交追加 Tasks 列——Tasks 扩展进入「按客户端跟踪落地进度」阶段。
  2. 提交后口径：跟踪 14 个客户端（Claude web/Desktop、VS Code GitHub Copilot、Microsoft 365 Copilot、Goose、Postman、MCPJam、ChatGPT、Cursor、Archestra.AI、PostHog Code、fast-agent、MCP Inspector、mcpc MCP CLI），Tasks 列仅 MCPJam 勾选，其余为空（MCP Apps 列则 11/14 勾选，可作扩展扩散速度对照）。
  3. 合箱线索：03-mcp 既有 mcp-spec-evolution 箱可引用本块作扩展落地节奏证据；矩阵由社区维护，勾选状态随时间漂移，引用需绑定该 commit SHA。
- 关闭条件：勾选口径（完整/部分支持如何判定）未核对页头说明；后续客户端新增 Tasks 支持时需复查矩阵文件最新版而不是本 commit。

## E2 · file-uploads 扩展章程（charter）合入规范仓库

- 获取日期：2026-10-27
- 来源 URL：<https://github.com/modelcontextprotocol/modelcontextprotocol/pull/3446>
- 本地原件：—
- 适用范围：官方仓库 PR 合并记录（merge commit `d2419e78`，2026-10-26T21:15Z），覆盖 experimental `file-uploads` 扩展的工作组建章程序列入规范文档站；不覆盖扩展 API 面。
- 证据等级：A
- 可提炼要点：
  1. 与 2026-10-18 已投递的 `experimental-ext-file-uploads` README（原件已存 `.inbox/originals/`）构成「孵化仓库 → 规范侧章程」推进链，合箱时并入同一箱追加。
  2. 同日另有治理类提交：社区会议禁止第三方 notetaker bots（PR #3457，commit `e4a92815`）——治理流程收紧，与 10-20/10-25 governance-wg 线同源，此处不重复登记，仅留指针。
- 关闭条件：章程正文（scope、交付物、里程碑）未取原文核对；需拉取合并文件确认后再决定是否升格独立证据块。

## E3 · ruby-sdk 1.8.2 发布：昨日 E1 关闭条件部分满足

- 获取日期：2026-10-27
- 来源 URL：<https://github.com/modelcontextprotocol/ruby-sdk/commit/ab55a8ec4169ae47ec2eb80be590a98083972321>
- 本地原件：—
- 适用范围：官方 SDK 仓库一手提交（Release 1.8.2，2026-10-26T16:29Z 提交、23:53Z 前经 PR #634 合入主干），覆盖 ruby-sdk 版本归属确认与 OAuth/资源订阅两处增量；不覆盖其它语言 SDK。
- 证据等级：A
- 可提炼要点：
  1. 2026-10-26 投递（`collect-20261026-ruby-sdk-registry-operations.md` E1）的关闭条件「该改动落在哪个 gem 版本」已由 Release 1.8.2 回答：PR #630/#631 的 notification 失败语义变更归入 1.8.2。
  2. 增量一（PR #632，`26eabbc5`）：resource subscriptions 改为按列表逐项授权（authorize the resource subscriptions of a list）。
  3. 增量二（PR #633，`f8fbeb7e` + `de9d5395`）：token endpoint 错误文档收窄到「设置 readers 的场景」——OAuth 错误路径文档精确化，属实现参考层。
- 关闭条件：rubygems 侧版本号与 git tag 对齐情况未核对；合箱时把「版本归属」从待核对项中划掉。

## E4 · MCP registry 生产升 1.8.5 并按环境配置数据库/节点容量

- 获取日期：2026-10-27
- 来源 URL：<https://github.com/modelcontextprotocol/registry/commit/c3ad9588082302a8cffd1c3acab8e311aaf0ab99>
- 本地原件：—
- 适用范围：官方 registry 仓库一手部署提交（2026-10-26T14:20Z promote 生产至 1.8.5；随后 16:13Z~18:14Z 四个容量配置 PR #1745~#1748），覆盖运维节奏；不涉及 API 面与数据模式。
- 证据等级：A
- 可提炼要点：
  1. 五连发部署（原文标题口径）：promote 1.8.5（#1744）→ 按环境配置 GCP 节点尺寸（#1745）→ 提升生产节点 CPU 容量（#1746）→ 按环境配置 PostgreSQL shared_buffers（#1747）→ 进一步提升生产 shared_buffers（#1748）。
  2. 与昨日 E2（ingress 重启修复 + boot disk 50GB）连续：registry 公开服务在 10-25/10-26 两天内密集做容量调优，索引规模增长压力的运维侧信号增强；仅支撑「registry 服务成熟度」叙述。
  3. registry 版本线可核对：1.8.4（10-23，昨日已登记）→ 1.8.5（10-26）。
- 关闭条件：无用户可见状态页事故报告佐证影响面；若后续 registry 发版说明含功能变更，回引本块区分「运维 vs 功能」。
