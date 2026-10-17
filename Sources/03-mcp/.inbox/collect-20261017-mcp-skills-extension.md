# 投递：MCP Skills 扩展生态（ext-skills 实现清单扩充）

> 建议合入箱：主箱 `mcp-spec-evolution`（扩展规范属协议演进层次，`Sources/03-mcp/mcp-spec-evolution/`）；若人工合箱判定为生态实现动态，可归 `mcp-server-ecosystem`。本轮为 2026-10-17 daily 档。

## E1 · Skills 扩展（SEP-2640）实现清单新增 Brewale，仓库治理形态明确

- 获取日期：2026-10-17
- 来源 URL：https://github.com/modelcontextprotocol/ext-skills/commit/c1aa87e4c381c82b99aa37471d0eae4ab50f9985
- 本地原件：`Sources/03-mcp/.inbox/originals/github-mcp-ext-skills-commit-c1aa87e4.json`、`Sources/03-mcp/.inbox/originals/github-mcp-ext-skills-implementations-2026-10-16.md`
- 适用范围：官方 `modelcontextprotocol` org 仓库在窗内的提交与 README（提交时间 2026-10-16T12:09:49Z）；覆盖 Skills 扩展的存在性、基线协议版本、实现清单增量与仓库治理方式；不覆盖扩展规范条款级内容（stable spec 文件本次未取原件）。
- 证据等级：A
- 可提炼要点：
  1. MCP Skills 扩展 `io.modelcontextprotocol/skills` 依据 SEP-2640 成立（Status: Final，合并 PR #2640 于 2026-09-13），stable 规范以基线协议修订 `2026-07-28` 为锚，官方概览页为 `modelcontextprotocol.io/extensions/skills/overview`。
  2. 窗内提交 #154 向 `docs/implementations.md` 新增 Brewale：TypeScript、`v1`、hosted 形态，宣称支持 org/project/personal 三级 skills 与 per-user 访问、`directoryRead`，并通过 conformance server scenarios——实现方声明，非官方验证结论。
  3. 仓库治理形态：stable 规范为发布快照、不原地修改；变更经 `docs/decisions.md` 的 dated 决策条目提案，接受后以下一 draft revision 发版。该「快照 + 决策日志」模式与 spec 主仓的 RC→stable 节奏（首轮已登记）一致，可作为 MCP 版本治理的旁证。
- 关闭条件：①Brewale 的 conformance 通过声明需官方 conformance 运行结果佐证；②条款级差异需取 `specification/stable/skills.mdx` 原件比对后方可关。

## 台账登记（本轮巡检流水，不产生证据块）

- arXiv API（`export.arxiv.org/api/query`，http 与 https 两路）：本轮 4 次尝试均失败，先 30s/45s 超时，后返回 `Rate exceeded.`（429 口径）与 503 页面；00-rl / 01-dl / 02-agent / 04-benchmarks 四域的 arXiv 通道本轮零产出。兜底列表页 `arxiv.org/list/cs.LG/recent` 可达（200），但按公告批次组织，周六无公告批次落入 24h 窗口，不作 daily 判据。建议下一轮先跑 `automation/check-egress.sh` 复测，并拉大 API 单查询间隔。
- `deepmind.google/discover/blog/`：TLS 连接失败（`SSL_ERROR_SYSCALL`），失败一次即跳过。
- `blog.langchain.dev/rss/`：现 302 重定向至 `www.langchain.com` 首页 HTML（217KB，非 RSS），条目不可解析；可达性表该条目需在复测后更新。
- `anthropic.com/engineering`：200 但静态 HTML 中未出现 `/engineering/` 文章链接（JS 渲染），不作条目源；`anthropic.com/news` 列表可达，最新条目 2026-10-15，在 24h 窗口外。
- `blog.google/technology/google-deepmind/`：200 但 JS 渲染，静态 HTML 解析不出文章条目（见 06-news 投递中 Gemini 4 块的佐证缺口）。
- `interconnects.ai/feed`（最新 10-09）与 `newsletter.semianalysis.com/feed`（最新 10-15 19:27 GMT）：可达，窗内无新条目。
- npm `@modelcontextprotocol/sdk` latest 1.32.1（2026-10-05）、pypi `mcp` 2.3.0（2026-10-02）：均早于窗口，无增量。
- `modelcontextprotocol/servers` 仓最新提交 2026-10-11；`modelcontextprotocol/modelcontextprotocol`（spec 主仓）24h 窗内无提交；`swe-bench/SWE-bench` 无 releases；A2A 最新 release v1.0.1（2026-05-28），均无窗内增量。
- 既有不可达表沿用：`huggingface.co/papers`、`api2.openreview.net`、`api.semanticscholar.org`、`openai.com/news`（403）、`gaia-benchmark.com`（DNS 失败）本轮未重复探测。
