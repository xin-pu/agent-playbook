# 投递：DeepSeek V4.1-Flash-1017 快照发布（2026-10-17）

> 建议合箱去向：01-dl 域内现仅有 `moe-routing` 一箱，主题不同层次（模型版本线/发布节奏），建议新开箱（暂名 `deepseek-model-lineage`，正式名由人工合箱定）。配套搜索 API 的事实单独登记于 `Sources/02-agent/.inbox/collect-20261018-deepseek-search-fetch-api.md`，本箱不重复。本轮为 2026-10-18 daily 档（窗 2026-10-17T01:00Z ~ 2026-10-18T01:00Z，bash+curl）。

## E1 · DeepSeek V4.1 Flash 升级至 -1017 快照：自反馈 RL 后训练驱动的性能-费用帕累托改进（官方发布）

- 获取日期：2026-10-18
- 来源 URL：https://api-docs.deepseek.com/zh-cn/news/news261017/
- 本地原件：`Sources/01-dl/.inbox/originals/deepseek-news261017-v41-flash-1017-2026-10-17.md`
- 适用范围：官方 API 文档新闻页一手来源（发布 2026-10-17，非同行评议的厂商发布稿）；覆盖快照升级、命名与切换口径、官方宣称的训练技术与基准走势；性能与基准数字均为官方单方声明、未经第三方复现，引用定量结论时须写明；权重开源仓（HF/ModelScope）本服务器不可达（HF 超时），未核验文件与许可。
- 证据等级：A
- 可提炼要点：
  1. 版本谱系与命名节奏（官方侧栏时间线）：V4 预览版 2026-04-24 → V4-Pro 正式版 2026-08-13 → V4-Flash-Vision-Exp 2026-08-21 → V4.1-Flash 2026-09-10 → V4.1-Flash-1017 2026-10-17；`-MMDD` 快照后缀延续 R1-0528、V3-0324 的既有惯例，网页端/APP/API 同步切换，旧模型名 `deepseek-v4-flash`、`deepseek-v4-flash-vision-exp` 暂时路由至新模型。
  2. 升级路径主张：官方称通过「基于自反馈的强化学习（RL）训练技术」提升从零构建完整项目能力（游戏开发、3D 建模等「许愿式编程」场景），同时缩短任务运行时间与输出长度，在多个 Harness 下达到新的性能-费用帕累托最优；配图口径为 mini-swe-v2 框架测 DeepSWE 的性能/成本曲线；针对 DeepSeek Harness、腾讯 CodeBuddy、WorkBuddy 做平台适配，建议 Harness ≥0.2.1-rc.1。
  3. 与既有证据的衔接：vLLM 侧 DeepSeek-V4.1-Flash 优化线索见 `Sources/05-code-oss/inference-stack-releases/inference-stack-releases-source.md`（FlashMLA mega attention、NVFP4 压缩 KV cache 等），本块补齐「模型侧发布」一手口径，两块互证同一模型家族的不同层次（推理栈 vs 模型版本）。
- 关闭条件：基准数字缺第三方复现与技术报告原件（本轮未采到公开 PDF）；权重仓文件清单与 License 需经 ModelScope/HF 核验（本服务器不可达，待复测出口或人工浏览器核对）；`-1017` 相对 `-0910` 的评测差有第三方复现后可关。

## 台账登记（本轮巡检流水，不产生证据块）

- arXiv API（cs.LG/cs.AI/cs.CL 逐条顺序查询）：窗口 2026-10-17T01:00Z ~ 2026-10-18T01:00Z 内 0 条新公示；已索引的最新 submittedDate 为 2026-10-15 17:59Z（周末公示空窗，周一恢复）。范围语法经宽窗对照验证正常（GRPO 十日窗 85 条命中）。
- DeepSeek 首次发布（V4.1-Flash 2026-09-10）窗外，且官方主站 `www.deepseek.com/news/deepseek-v4-1-flash/` 页内日期口径为 9 月 10 日，非本轮事件，只作 E1 谱系引用不重复登记。
- Bing 检索出现的模型更新聚合站（benchlm.ai、llmgateway.io、aireleasetracker.com、lmmarketcap.com）均 C 级榜单/摘要，按口径不作定量结论来源，未采信。
- huggingface.co 本机通道仍超时；`modelscope.cn` 未探（下轮 01-dl 可试作权重核验通道）。
