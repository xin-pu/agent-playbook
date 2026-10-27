# 投递：Anthropic 向 SEC 递交 S-1（拟 IPO）（2026-10-27 daily）

> 巡检通道：curl 抓 `https://www.anthropic.com/news` 列表页（结构可解析）+ 条目页短摘存原件。窗口 2026-10-26 01:00Z~2026-10-27 01:00Z 仅命中该条。其余资讯源复查：`openai.com/news` 未探测（沿用 403 结论）；`deepmind.google/discover/blog` 本次连接超时（20s 一次即跳过，与前轮「可达」结论不一致，待 `automation/check-egress.sh` 复测后回写可达性表）；`qbitai.com/feed` 最新条目 2026-10-23（窗外）；`interconnects.ai/feed` 最新 Kimi K3.1 播客已登记（10-26 投递）；`semianalysis` 最新 Trainium 篇 10-23 窗外；`jiqizhixin.com` 沿用「JS 渲染无结构化条目」结论。

## E1 · Anthropic, PBC 递交 Form S-1：拟 Nasdaq Global Select 上市，代码 ANT

- 获取日期：2026-10-27
- 来源 URL：<https://www.anthropic.com/news/s1-sec>
- 本地原件：`Sources/06-news/.inbox/originals/anthropic-news-s1-sec-2026-10-26.md`
- 适用范围：官方公告（A 级一手，页面标注 Published Oct 26, 2026 / Announcements）；覆盖 S-1 递交这一事实与公告自述的上市要素（主体、交易所、代码、未定项）；不覆盖募资规模、财务数据与发行时间线——S-1 全文在 SEC 渠道，本块不引用。
- 证据等级：A
- 可提炼要点：
  1. 公告原文口径：Anthropic, PBC 已向美国证券交易委员会递交 Form S-1 注册声明，涉及拟议 IPO 的 A 类普通股；拟在 Nasdaq Global Select Market 上市，股票代码「ANT」。
  2. 公告明示未定项：发行股数与价格区间「尚未确定」——任何媒体给出的估值/规模数字在此节点均无公司口径支撑。
  3. 主体形态注意点：发行主体登记为 PBC（public benefit corporation），与既有治理类证据线（Anthropic 公益公司治理讨论）可直接挂钩，是「PBC 架构走公开市场」的实例。
- 关闭条件：后续需跟踪 S-1 公开全文（SEC EDGAR）与路演/定价公告；在 A 级财务数据落地前，本箱不得衍生任何估值类定量结论。

## 台账登记

- 2026-10-27：`deepmind.google/discover/blog` curl 连接超时（HTTP 层，20s），与 2026-10-09 可达性表「200」结论冲突，一次即跳过未重试；待人工主流程复测后决定是否回写 `web-sources.md`/技能可达性表。
