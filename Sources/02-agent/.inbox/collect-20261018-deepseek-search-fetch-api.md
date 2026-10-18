# 投递：DeepSeek 开放自研 Search/Fetch API（2026-10-17）

> 建议合箱去向：并入 weekly 轮已建议新开的 `tool-use-function-calling` 箱（见 `collect-20261018-tool-use-openbox.md` 抬头；若人工决定分箱，本块亦可独立入「模型厂商自带工具层」主题）。模型侧事实登记于 `Sources/01-dl/.inbox/collect-20261018-deepseek-v41-flash-1017.md#E1`，本箱不重复。本轮为 2026-10-18 daily 档（窗 2026-10-17T01:00Z ~ 2026-10-18T01:00Z，bash+curl）。

## E1 · 厂商自带搜索栈的产品化：DeepSeek Search/Fetch 接口开放，免费期至 2026-11-01

- 获取日期：2026-10-18
- 来源 URL：https://api-docs.deepseek.com/updates/
- 本地原件：—（同页正文抽取随 01-dl 投递的原件登记，此处不复制文件）
- 适用范围：官方 Change Log 页 `Date: 2026-10-17` 条目一手来源（厂商文档，非独立评测）；覆盖接口开放事实、定价与计费切换时间；不覆盖接口参数级 schema 与限流规则（官方 API 指南页本轮未采）。
- 证据等级：A
- 可提炼要点：
  1. DeepSeek API 新增 Search 与 Fetch 两个正式接口，能力由自研搜索引擎提供；官方称索引千亿级网页、支持多语言、日处理数亿次请求，并对 SEO 作弊/GEO 操纵/低质 AIGC 做识别过滤——Agent 的工具层（检索）开始由模型厂商以原生 API 形式内置，第三方检索服务（Tavily 类）的生态位需按此重估。
  2. 定价 5 元/千次（Search 与 Fetch 同价）；当前 DeepSeek Harness、Claude Code、Codex 经 Server 端工具调用访问 Search/Fetch 尚未计费，2026-11-01 00:00（北京时间）起按次收费——用 DeepSeek 做 agent 后端的框架，工具调用成本模型将在两周内从「默认免费」变为「按次计量」，缓存与检索策略需要提前提炼口径。
  3. 事件耦合：搜索 API 开放与 V4.1-Flash-1017 模型快照同日发布，官方将二者写为同一更新的两节——「模型 + 自带工具」打包演进是本轮可核对的结构性信号。
- 关闭条件：接口参数、限流与计费的条款级细节缺官方 API 指南页原件（缺什么：Search/Fetch 指南页快照；从哪里补：`api-docs.deepseek.com` 指南路径下轮补采；关闭条件：补齐后本块「适用范围」去掉未覆盖声明即可关）。

## 台账登记（本轮巡检流水，不产生证据块）

- `blog.langchain.dev/rss/`：302 至营销站 HTML（非 RSS，沿用 2026-10-17/18 前轮结论）；页面卡片最新日期 2026-10-15，窗外。
- `www.interconnects.ai/feed`：窗内唯一新文（10-17）已由 weekly 档登记，判重跳过。
- `deepmind.google/discover/blog/`：头条 `accelerating-antimicrobial-discovery` 的 datePublished=2026-10-15T16:00Z，窗外；周末无新页。
- arXiv agent 查询（cs.AI/cs.CL/cs.MA 相关）：窗内 0 条新公示（同 01-dl 台账的周末空窗结论）。
