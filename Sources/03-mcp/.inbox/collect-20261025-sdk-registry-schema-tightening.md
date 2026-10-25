# 投递：MCP SDK 与 Registry 的接口语义收紧（2026-10-25 daily）

## E1 · python-sdk：工具 schema 生成三改——裸容器注解进结构化输出、去生成标题、兼容 typing.Dict

- 获取日期：2026-10-25
- 来源 URL：https://github.com/modelcontextprotocol/python-sdk/pull/3758
- 本地原件：—（GH API 返回的提交标题与合并时间，未存 PR diff 原件）
- 适用范围：官方 Python SDK 主干合并记录，覆盖工具入参/出参 schema 的生成规则（2026-10-24 一天内三条），不覆盖 transport 与 auth 逻辑；同日另有 #3755 代码扫描告警清理与 #3752 security group 依赖升级，属维护性改动，本块不重复登记。
- 证据等级：A
- 可提炼要点：
  1. #3758（20:19Z）：返回类型标注为裸 `dict` / `set` / `frozenset` 时也纳入 structured output 路径，此前需要具体泛型参数才生效——SDK 对「有返回结构」的判定放宽。
  2. #3756（17:53Z）：`typing.Dict[str, X]` 与 `dict[str, X]` 同等处理，旧式 typing 注解不再被区别对待。
  3. #3757（17:39Z）：不再为工具入参与出参 schema 生成 `title` 字段，减少自动生成的冗余元数据。
  4. 三条合并均发生在 ts-sdk v2.4.0（10-24 已入块）之后、python-sdk 下一个 release 之前；当前 pypi `mcp` 仍为 2.3.0（10-02），接口收紧尚未落到发布版本，客户端可见行为未变。
- 关闭条件：需 python-sdk 发新版本并在 changelog 确认这三条的对外影响面；合箱时与 mcp-server-ecosystem 的 SDK 线并块。

## E2 · registry：校验器与 publisher 同日 6 处收紧，含 ECDSA P-384 签名补齐

- 获取日期：2026-10-25
- 来源 URL：https://github.com/modelcontextprotocol/registry/pull/1457
- 本地原件：—（提交标题与合并时间取自 GH API）
- 适用范围：官方 Registry 仓库主干合并记录，覆盖服务器元数据校验与 `mcp-publisher` 发布链路（2026-10-24 单日 8 条提交）；不覆盖已部署服务实例的实际配置，也不与 10-24 已入块的 v1.8.x release 混记。
- 证据等级：A
- 可提炼要点：
  1. #1457（20:52Z）：`mcp-publisher` 把 ECDSA P-384 签名按固定宽度补齐——签名定长化直接影响注册表条目可验证性。
  2. #1570（21:32Z）：初始化时记录 `repository.id`，使源仓库改名后条目仍可解析，解决重命名导致链接失效。
  3. #1583（21:22Z）拒绝非法参数类型与空位置参数；#1555（21:07Z）拒绝不完整的 repository 元数据；#1361（21:14Z）放行 GitLab 嵌套子组 URL——校验面「一收一放」，说明此前校验逻辑既漏判也误判。
  4. #1640（21:51Z）把 HTTP 验证要求写入文档并加测试固定；#1523（21:44Z）将 `mcp-publisher` 安装器版本固定并校验；#1268（22:00Z）补 DNS/HTTP 认证排障文档。
  5. 时间分布：8 条集中在 20:52–22:00Z 一小时内，形似批量清理积压 PR，而非渐进式开发，可作为 registry 运营节奏证据。
- 关闭条件：未读各 PR diff 与 issue 上下文；需 registry 侧公开部署版本变更记录后再核这些收紧是否生效，合箱时并入 registry 治理线。

## E3 · swift-sdk：data URL 解码两条修复，base64 判定改看头部

- 获取日期：2026-10-25
- 来源 URL：https://github.com/modelcontextprotocol/swift-sdk/pull/310
- 本地原件：—（提交标题与合并时间取自 GH API）
- 适用范围：官方 Swift SDK 主干合并记录，覆盖 data URL 解析行为（#309、#310，均 2026-10-24T23:10Z 合并）；同日合入的 CODEOWNERS（#308）与若干 README 修正属文档，不在本块。
- 证据等级：A
- 可提炼要点：
  1. #310：非 base64 data URL 现在解码任意 percent-encoded 字节，此前存在未覆盖的转义形态。
  2. #309：base64 判定改为读 data URL 头部标记，不再靠 payload 内容猜——与 #310 同日合入，构成同一处解析逻辑的成对修正。
  3. 两条改动与 10-24 入块的 ts-sdk spec 校验收紧、E1 的 python-sdk schema 收紧同日出现，跨 SDK 呈现「实现层向规范字面语义收敛」的一致方向；此为归纳性观察，结论层需正文另行论证。
- 关闭条件：未验证修复前后行为差异的具体输入样例；待 swift-sdk 下次 release 或补测样例后关闭。

## 台账登记（未达开箱门槛，仅流水）

- 00-rl／01-dl／02-agent／04-benchmarks：arXiv API 11 条查询（RL、RLHF、policy optimization、MoE、quantization、SSM/diffusion、LLM agent、tool use、multi-agent、agent benchmark、SWE-bench）在 24 小时窗内均无新增；库内最新条目仍为 2026-10-22 提交的 `2610.316xx` 系列（已登记）。周末提交空档，属常态。
- 05-code-oss：`vllm`、`transformers`、`pytorch`、`langchain`、`llama_index`、`openai-agents-python`、`ollama` 窗内均无新 release；npm `@modelcontextprotocol/sdk` latest 1.32.2（modified 2026-10-23T18:11Z，窗边旧值）、pypi `mcp` 2.3.0（10-02）不变。
- 06-news：`anthropic.com/news` 与 `/research` 列表页取到 21 个 research 与 40+ news slug，逐一查重后窗内无未登记项（`alignment-assessment-ukaisi` 已 10-24 入块）；另有 3 个未登记 slug 经查发布日在窗外——singapore-office-opening（10-14）、model-hardware-standard-research-preview（10-13）、enterprise-frontier-safeguards（10-21），早于本周 weekly 窗起点，提请人工主流程下一周度档补录；`newsletter.semianalysis.com/feed` 最新为 10-23 Trainium（已 10-24 入块）；`interconnects.ai/feed` 最新 10-20 已登记；`langchain.com/blog/rss.xml` 最新两条 10-23/10-24 已登记，其后为 10-22 LLM Gateway（已登记）；`deepmind.google/discover/blog/` 首页 `datetime` 仅到月（"October 2026"），无逐条日期，本轮未取到结构化条目；量子位首页 5 条均落在 10-24，但均为厂商发布类新闻稿、单一来源且无原件，不满足开箱门槛，只此登记：`https://www.qbitai.com/2026/10/505083.html`（星辰 TaaS）、`505032`（两个世界模型）、`504931`（5090 跑 34B 世界模型）、`504930`（5B 生图模型海外爆火）、`504915`（南京物理 AI）。
- 通道异常记录：`api.deepseek.com/news` 返回 401（本轮首次遇到，与 10-25 weekly 档通过 news 列表页成功取条目不同），未重试；`langchain.com/blog/rss.xml` 为可用订阅路径，`blog.langchain.dev/rss/` 现重定向到主站首页（非 feed），建议人工合箱时把巡检清单的订阅地址改指 `/blog/rss.xml`（本会话不改动 `web-sources.md`）。
