# 投递：蚂蚁百灵开源 Ling-3.1-flash-1019、Anthropic AI for Science 扩围与基准行业检视（2026-10-29 daily）

> 巡检通道：`www.anthropic.com/news`（列表页正常）、`www.interconnects.ai/feed`、`www.qbitai.com/feed`→条目页直取。失败通道：`deepmind.google/discover/blog/` 连接超时 1 次即跳过；`newsletter.semianalysis.com` 首页为 JS 渲染未取到结构化条目；`openai.com/news` 与 `jiqizhixin.com` 按已知不可达/无结构化口径跳过未探。

## E1 · 量子位：蚂蚁百灵开源 Ling-3.1-flash-1019，主打 Personal Agent 长程任务

- 获取日期：2026-10-29
- 来源 URL：<https://www.qbitai.com/2026/10/505928.html>
- 本地原件：—
- 适用范围：中文科技新闻转述（C 级，不得作为定量结论来源）；报道口径为 10-28 开源 Ling-3.1-flash-1019 并同步开源 base 模型 Ling-3.1-flash-base，关联 10-27「灵光 2.0」产品升级；所有分数为报道引述，未核官方模型卡。
- 证据等级：C
- 可提炼要点：
  1. 报道口径：新版本在 Artificial Analysis Intelligence Index v4.3.2 得 44 分、较上一版 +3；AA-Briefcase 约 1400→1524 Elo、GDPval-AA 约 1618→1644 Elo、AutomationBench-AA 62%→68%、CritPt 18%→26%、SciCode 54%→57%（以上全部为二手转述，待官方渠道核对，不作定量结论）。
  2. 定位口径：面向 Personal Agent 场景（跨会话记忆、长程任务调度、独立云主机），与 `2610.36967`（ProactMem，02-agent 本轮 E3）同一「主动式长程 agent」叙事的两端（产品 vs 学术）。
  3. 命名含日期后缀（-1019），提示滚动快照式发布节奏，与 DeepSeek V4.1 Flash 1017（`01-dl` 2026-10-18 投递）同一模式。
- 关闭条件：需官方发布渠道（Hugging Face 模型卡/公司博客/技术报告）出现后才能升为可引用事实；若 A/B 级原件在后续窗口出现，替换本块口径并关本块。

## E2 · Anthropic：AI for Science 计划扩展至基金会与科研机构

- 获取日期：2026-10-29
- 来源 URL：<https://www.anthropic.com/news/ai-for-science-expands-foundations-research-institutions>
- 本地原件：—
- 适用范围：官方发布（A 级，公告正文；日期为列表页 `<time>` 口径 Oct 28, 2026）；覆盖合作对象范围声明；不覆盖具体算力/资金条款与科学产出评估。
- 证据等级：A
- 可提炼要点：
  1. 事实：AI for Science 计划扩围，公告集中列出全球 20 家科学基金会、机构与研究组作为合作伙伴。
  2. 与 `2610.37081`（OpenGray，见 04-benchmarks 台账）与 `2610.37649`（LongChang，02-agent 台账）构成「科学 agent 评测↔产业投入」对照线，资讯层单条不重复登记。
- 关闭条件：公告无量化条款（资助额度、算力口径「公开资料未给」）；出现可核对的条款级原件（合作机构公告/报告）后关。

## E3 · Interconnects：Artificial Analysis v5 与「基准制定者困境」

- 获取日期：2026-10-29
- 来源 URL：<https://www.interconnects.ai/p/artificial-analysis-v5-and-the-benchmarkers>
- 本地原件：—
- 适用范围：深度分析 newsletter（B 级，作者为行业分析者，非一手评测机构数据）；feed 时间戳 2026-10-28；覆盖对基准行业（含 Artificial Analysis v5 改版）的方法论批评；不替代 AA 官方方法论文档。
- 证据等级：B
- 可提炼要点：
  1. 主旨口径：「爬坡容易，知道该往哪爬难」——提分有清晰剧本，而真正的 frontier 上「有意义的基准」反而缺方法（文首 puff 段落原话提炼）。
  2. 与 `04-benchmarks` 本轮 E3（LiveSearch 的时效/泄漏问题）及既有 contamination 主线同题，作为方法论二手分析登记，定量部分不引用。
- 关闭条件：观点性材料无「关闭」意义上的验证需求；若 AA v5 方法论文档发布（A 级），以该文档另立证据块并停止引用本块作依据。

## 台账登记

- 顺延候选：`2610.37364`（EmbeddingGemma 2，Google 官方模型发布，属 01-dl 与资讯边界，下轮定域）。
- 通道记录：`qbitai.com` 条目页含精确到分钟的发布时间（本轮据此判日）；`anthropic.com/news` 列表页 `<time>` 结构稳定；`deepmind.google` 超时应在下次 `check-egress.sh` 复测中回写可达性表。
