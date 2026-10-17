# 投递：MCP 周窗动态（File Uploads WG 开仓 · servers v1.0.0 发布工程 · Skills 规范对齐）

> 建议合入箱：E1/E2 → `mcp-server-ecosystem`；E3 → `mcp-spec-evolution`。本轮为 2026-10-18 weekly 档（窗 2026-10-11 ~ 2026-10-18）。

## E1 · File Uploads WG 实验仓 `experimental-ext-file-uploads` 开仓（2026-10-14）

- 获取日期：2026-10-18
- 来源 URL：https://github.com/modelcontextprotocol/experimental-ext-file-uploads
- 本地原件：`Sources/03-mcp/.inbox/originals/github-mcp-experimental-ext-file-uploads-2026.json`（仓库元数据 API 快照）、`Sources/03-mcp/.inbox/originals/github-mcp-experimental-ext-file-uploads-readme-2026-10-18.md`（README raw 快照）
- 适用范围：官方 `modelcontextprotocol` org 仓库元数据与 README（created 2026-10-14T06:05:24Z，pushed 2026-10-17T14:40:49Z）；覆盖扩展立项、工作组归属与仓库定位；不覆盖扩展条款内容（开仓仅 Initial commit，规范正文尚未成形）。
- 证据等级：A
- 可提炼要点：
  1. MCP 官方以独立实验仓承载「文件上传」扩展：定位为 *Experimental MCP extension for uploading files to tools over MCP*，由 File Uploads Working Group 维护——与 Skills 扩展（SEP-2640 → ext-skills 仓）相同的「WG 孵化 → 独立仓 → 规范快照」路径再现，说明该模式已是扩展固化的标准通道。
  2. 时间线：开仓 10-14 当天仅 Initial commit，10-17 已有推送——处于起草早期，尚无条款可提炼。
- 关闭条件：条款级内容缺失（正常，处 draft 前）；待该仓出现 draft spec/SEP 编号后另开证据块，届时可关本块（立项事实已被后续规范块覆盖）。

## E2 · `servers` 仓 v1.0.0 发布工程落地：main-source 守卫 + SDK 1.x 对齐合入主干（2026-10-10 ~ 10-11）

- 获取日期：2026-10-18
- 来源 URL：https://github.com/modelcontextprotocol/servers/pull/5090
- 本地原件：—
- 适用范围：官方仓库合并记录（PR #5090 `v2/chore/5080-release-v1.0.0-sdk1`，2026-10-11 合入；同窗还有 #5113、#5106 发布工程 PR 与 main-source guard CI）；覆盖发布管线与版本对齐动作；不覆盖 v1.0.0 面向用户的功能清单（未取 release notes）。
- 证据等级：A
- 可提炼要点：
  1. 官方参考 servers 仓在 10-10 ~ 10-11 连续合入多条 release 工程 PR（v1.0.0-sdk1 命名显示与 SDK 1.x 主线绑定），并引入「main-source guard」CI 守卫——参考实现与规范/SDK 主干版本联动的工程化约束在加强。
  2. 与首轮登记的「固定工具层（MCP server）作为评测控制变量」范式衔接：servers 仓进入 1.0.0 版本线后，评测可引用稳定版本锚点，减少「参考实现漂移」这一混淆变量。
- 关闭条件：需抓 v1.0.0 正式 release tag 页确认发布日与内容清单；抓取后本块由 release 级证据替代。

## E3 · Skills 扩展规范类型与 `2026-07-28` 基线 schema 对齐（提交 4ad2d3a8，2026-10-15）

- 获取日期：2026-10-18
- 来源 URL：https://github.com/modelcontextprotocol/ext-skills/commit/4ad2d3a8
- 本地原件：—
- 适用范围：官方 ext-skills 仓提交（PR #157，2026-10-15T13:03:08Z）；覆盖 Skills 扩展类型定义/示例向 stable 基线协议修订对齐这一治理动作；不覆盖对齐后的条款级差异清单。同窗另有 #159/#160 实现清单维护（FastMCP 标注 in progress、mcpkit 归入 v1 并删除其 host 行），主线索 Brewale 已在 2026-10-17 daily 投递登记，不重复。
- 证据等级：A
- 可提炼要点：
  1. 扩展规范以「类型与示例跟随基线 schema」方式维护一致性（提交标题 Align skills spec types and examples with the 2026-07-28 base schema）——印证首轮结论：扩展不定义独立版本轴，锚定主协议修订号。
  2. 实现清单持续演进的治理信号：标注「in progress」与「drop the host row」表明清单区分完成度档位且会移除不合规条目，非单纯收录。
- 关闭条件：条款级 diff 仍未取原件（同 `mcp-spec-evolution#E1` 关闭条件）；抓到 `specification/stable/skills.mdx` 与主协议 schema 比对后合并关闭。

## 台账登记（本轮巡检流水，不产生证据块）

- `modelcontextprotocol/modelcontextprotocol`（spec 主仓）：窗内以依赖 bump 与文档为主；两条治理线索——Progressive Disclosure WG charter（PR #3376，10-13 合入）与 Governance WG charter（10-08 合入，窗外）——建议与 WG 相关证据合并时人工判定是否值得落块。
- spec releases：最新仍为 `2026-07-28` stable，窗内无新修订。
- npm `@modelcontextprotocol/sdk` latest 1.32.1（10-05）、pypi `mcp` 2.3.0（10-02）、typescript-sdk `v2.3.1`（10-05）：均早于窗口，无增量（与 2026-10-17 daily 台账一致）。
- `api.github.com/repos/modelcontextprotocol/specification/releases` 返回 301：仓库已更名，规范主仓路径应为 `modelcontextprotocol/modelcontextprotocol`（可达性表下轮更新时建议修订）。
- A2A releases：最新 v1.0.1（2026-05-28），窗内无增量。
- `modelcontextprotocol/conformance`：最新提交 10-01（窗外），DPoP/SEP-1932 线索待下轮跟进。
