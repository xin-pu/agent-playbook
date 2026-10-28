# 投递：Anthropic 官方双发布（药研合作与 GSA 扩展）（2026-10-28 daily）

> 巡检通道：curl 抓 www.anthropic.com/news 列表页 + 文章页（正文 JSON payload 含 publishedOn 字段）。窗口 2026-10-27T00:00Z~2026-10-28T01:10Z。判重：`early-progress-drug-development`、`expanding-partnership-gsa` 两个 slug 均未见于 `Sources/`；`s1-sec` 昨日已投（`collect-20261027-anthropic-s1-ipo.md`），复查无增量。

## E1 · Anthropic 官宣：用 Claude 加速药物研发的早期进展

- 获取日期：2026-10-28
- 来源 URL：<https://www.anthropic.com/news/early-progress-drug-development>
- 本地原件：—
- 适用范围：官方新闻发布（列表页与文章页 publishedOn 一致，均为 2026-10-27，A 级一手「官方发布」）；覆盖公司叙事层——把「AI 制药」定位在常用讨论（如文献挖掘）之外的机会上；不含经同行评议的效果证据，任何命中率/周期缩短类数字在拿到原始合作研究前不得引用。
- 证据等级：A
- 可提炼要点：
  1. 事实登记：Anthropic 于窗口内（10-27）发布该新闻页，正文首句自述「存在许多加速药物开发的机会，超出 AI 最常被讨论的应用之外」——属公司应用侧布局叙事，与本域 10-19 `collect-20261019-anthropic-public-benefit.md`、02-agent 域 10-24 UK AISI 投递构成「前沿模型公共部门/公益应用」官方叙事线，合箱时可互指不复制。
  2. 使用姿态：本块按官方发布登记「已发布 + 定位」两个事实；具体合作方、模型与指标未抓取正文核对，暂不登记。
- 关闭条件：文章正文与合作研究细节未读；若后续给出可核对的基准/试验数据，回指原件升级；纯叙事发布则维持本块并关闭于「无定量内容」。

## E2 · Anthropic 扩大与 GSA 的合作：面向美国各级政府提供 Claude

- 获取日期：2026-10-28
- 来源 URL：<https://www.anthropic.com/news/expanding-partnership-gsa>
- 本地原件：—
- 适用范围：官方新闻发布（A 级一手，但日期字段两处不一致：文章页 publishedOn=2026-10-27，列表页 JSON 记录 2026-10-26，本块按窗口内处理并在要点标注）；覆盖政府渠道合作的公开宣告；不覆盖合同金额、覆盖机构数等未公开的条款细节。
- 证据等级：A
- 可提炼要点：
  1. 事实登记：标题口径为「expanding our partnership with GSA to bring Claude to all levels of government」——在既有 GSA OneGov 类合作上扩展至「各级政府」；本 slug 在 `Sources/` 首次登记，未检索到先前投递覆盖同一 URL。
  2. 日期矛盾须带：列表页与文章页日期字段相差一天，引用「发布时间」时写明矛盾，待页面缓存或新闻稿原件定标。
- 关闭条件：GSA 侧公告或合同公示未取得——单侧官宣按「来源自述」处理；后续若 Anthropic 公布量化采用数据，回到原件核对再登记。

## 台账登记（未过开箱门槛或通道失败，暂不建块）

- openai.com/news 返回 403 拦截页（本轮实测，页面 9.9KB 无结构化条目）——不可达源，持续只登记索引可达性。
- deepmind.google/discover/blog 连接超时（本轮实测，连续第二轮失败）——建议下轮巡检档跑 `automation/check-egress.sh` 复测后回写可达性表。
- interconnects.ai/feed 最新条目为 2026-10-25 播客（已于 10-26 投递 `collect-20261026-interconnects-kimi-k31-podcast.md`），窗口内无增量。
- 量子位（www.qbitai.com，URL 见 10-17/10-18 两份早期投递，不重复登记）：本轮首页可达且条目丰富，但文章页日期解析不稳（部分 URL 404、正文无 ISO 时间戳），逐条时间不可靠，暂不建块。
- 机器之心：首页 JS 渲染未取到结构化条目（延续既有口径）。
