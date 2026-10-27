# 投递：LangChain company harness 组件文（漏报补登）与通道更新（2026-10-27 daily）

> 巡检通道：`curl https://www.langchain.com/blog/rss.xml`（旧地址 `blog.langchain.dev/rss/` 仍 302 到 Webflow HTML 列表页，无 `<item>` 结构；新地址 2026-10-24 台账已记，待人工回写 `web-sources.md`，本代理不改）。
>
> 时间口径警示：Webflow RSS 的 `pubDate` 为批次页面刷新时间（三条同显 2026-10-26T15:32Z），实际发布时间以条目页 JSON-LD `datePublished` 为准。据此核对：`context-engineering-starts-with-retrieval`（页内 JSON-LD datePublished 2026-10-23T17:00Z）与 `context-engineering-deep-agents-remember` **已于 2026-10-24 投递**（`collect-20261024-agent-context-engineering.md` E1/E2），本轮复查无增量，不重复登记；`components-building-company-harness`（JSON-LD datePublished 2026-10-24T23:49Z）属 2026-10-25 窗口漏报（该轮 langchain 通道失效未取到条目），本轮补登。

## E1 · company harness 的五组件：identity、memory、code execution、scheduled runs

- 获取日期：2026-10-27
- 来源 URL：<https://www.langchain.com/blog/components-building-company-harness>
- 本地原件：—
- 适用范围：官方博客实践总结（B 级；条目页 JSON-LD datePublished 2026-10-24T23:49Z，属 10-25 窗口漏报补登）；覆盖 LangChain 内部跨 marketing/sales/engineering 的「multiplayer harness」建设经验按问题域拆解；不覆盖通用 harness 评测方法与量化对比。
- 证据等级：B
- 可提炼要点：
  1. 文章按五个 Problem 维度组织组件：User Experience、Identity、Memory、Code Execution、Scheduled Runs（页面正文结构口径）。
  2. Identity 维度：agent 需区分「代用户行事（OBO, on-behalf-of，对部分服务用用户身份、对另一些用自身身份）」——多人共享 harness 的权限边界问题。
  3. Scheduled Runs 维度：相当比例的内部 agent 运行是计划任务而非显式调用（原文称 ambient agents），以 GTM 场景为例：监控邮件与新增合格线索、发日报、可执行 outbound 流程。
  4. 与既有证据线的关系：与 `2610.32483`（When Agents Fail，五度量 harness 归因，2026-10-26 投递 E1）互为「实践清单 vs 评测框架」两面，合箱时互设引用不复制事实。
- 关闭条件：厂商自述实践，无第三方验证与量化口径；若要支撑正文「harness 组件」结论，需补 A 级评测证据（已有 2610.32483 可交叉），本块仅作工程实践参考。

## 台账登记

- 2026-10-27：`www.langchain.com/blog/rss.xml` 可直取且含结构化条目（供人工主流程回写 `web-sources.md` 时参考）；同轮复查两条旧文（见头部时间口径警示），同源已登记不重复落块。
- 06-news 侧 `qbitai.com/feed`（RSS 可直取、条目带 pubDate，可作中文资讯源）与 `www.anthropic.com/news` 列表页结构确认正常，均已在 `06-news` 投递头部登记复查结果。
