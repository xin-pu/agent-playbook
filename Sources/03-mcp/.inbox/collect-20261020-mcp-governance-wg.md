# 投递：MCP Governance WG 仓库落地（2026-10-20 daily）

> 本文件为未入箱投递，合箱由人工主流程处理。候选去向：`03-mcp` 域 mcp-spec-evolution 箱或 WG/生态治理主题箱，由人工判定主箱。

## E1 · modelcontextprotocol/governance-wg 建档，MCP 治理流程首次拥有独立工作仓

- 获取日期：2026-10-20
- 来源 URL：<https://github.com/modelcontextprotocol/governance-wg>
- 本地原件：`Sources/03-mcp/.inbox/originals/github-mcp-governance-wg-readme-2026-10-19.md`
- 适用范围：官方 GitHub 组织仓库（A 级一手，创建时间 2026-10-19T19:24Z）；覆盖 WG 使命、scope 清单与章程入口指针；不覆盖 WG 实际决议与章程正文条款（章程在 spec 主仓 `docs/community/working-groups/governance.mdx`，本块不复制其内容）。
- 证据等级：A
- 可提炼要点：
  1. 前情核对：Governance WG charter 曾于 10-08 合入 spec 主仓、上轮仅作台账线索登记（见 `collect-20261018-mcp-weekly.md` 台账登记节）；本轮 WG 实体建档，是「charter 通过 → WG 运作」的增量节点。access 仓提交 `dde11cc`（PR #222，2026-10-19T19:04Z）同步记录「Add Governance Working Group and create the governance-wg repository」。
  2. README 声明的 in-scope：`docs/community/` 下治理文档 stewardship、项目决策的记录口径（何谓决策/谁批准/如何记录）、Code of Conduct 文本与上报/升级文档、社区价值观与 values workshop 公开化、贡献者阶梯（contributor ladder）晋升文化与导师制、向 Core Maintainers 的非约束性意见通道、跨 WG/IG 协调（README §Scope，短句转述，不超过一段引文）。
  3. 定位措辞可核对：WG 自我定位为 advisory voice channel，远期志向是成为 contested decisions 的常设协商论坛并支持代表性社区参与（README Mission 节，转述）。
- 关闭条件：章程正文与首轮 WG 会议/产出未见（仓库建档 <24h）；等 WG 首次会议纪要或 charter 条款级 diff 入箱后可关。spec 主仓更名（301）已在前轮台账登记，本轮复查无增量，不重复开箱。

## 台账登记

- 03-mcp 其余窗内动态复查无开箱级增量：registry 最新提交 10-11（窗外）；spec 主仓窗内最新提交 `1155ca4`（10-18 docs 修链，窗外）；SDK 发布节奏 csharp 2.2.0（08-13）/kotlin 0.15.0（07-28）/go 1.8.0（09-14）均窗外，csharp-sdk、inspector、typescript-sdk 窗内仅代码推送无 release。
- 采集通道失败登记：`deepmind.google/discover/blog` 本轮 SSL_ERROR_SYSCALL 不可达（与可达性表 10-09 口径冲突，待 `automation/check-egress.sh` 复测）；`blog.langchain.dev/rss/` 现 301 至 JS 渲染站点无法解析条目（RSS 通道状态退化，同待复测回写）。
