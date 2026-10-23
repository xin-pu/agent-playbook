# 投递：MCP SDK 认证与传输互操作窗口动态（2026-10-23 daily）

## E1 · rust-sdk（rmcp）v3.7.0：OIDC 主体与跨域 resource_metadata

- 获取日期：2026-10-23
- 来源 URL：https://github.com/modelcontextprotocol/rust-sdk/releases/tag/rmcp-v3.7.0
- 本地原件：`Sources/03-mcp/.inbox/originals/github-mcp-rust-sdk-rmcp-v3.7.0-release.json`
- 适用范围：官方 SDK 发布记录（一手仓库 release），覆盖 rmcp 3.6.0→3.7.0 增量（2026-10-22T20:07Z 发布）；不覆盖规范条款本身变更。
- 证据等级：A
- 可提炼要点：
  1. Added：企业交换流程支持 OIDC ID-token 主体（#1385），扩大 auth 场景下可对接的身份提供方类型。
  2. Fixed：允许跨域的 resource_metadata URL（#1302）；JSON-RPC 错误体携带 401/403 时保留 HTTP 状态（#1341）——两条都直接影响 OAuth 发现链路的互操作性。
  3. 发布节奏参考：3.6.0（10-20）到 3.7.0（10-22）间隔两天，release 后主干继续合入 transport 错误暴露改动（#1386，10-23 01:08Z），版本迭代处于高频段。
- 关闭条件：无独立 changelog 逐条核对；待人工合箱时并入 mcp-server-ecosystem 或 SDK 生态箱。

## E2 · csharp-sdk：取消与 OAuth 元数据误报的行为级修复

- 获取日期：2026-10-23
- 来源 URL：https://github.com/modelcontextprotocol/csharp-sdk/pull/1917
- 本地原件：—（GitHub PR 页未存原件，要点取自 API 返回的标题与合并时间）
- 适用范围：官方 SDK 主干合并记录，覆盖请求取消路径的两个缺陷修复（#1917、#1891，均 2026-10-22 合并）；不覆盖该仓库窗口内的测试基建改动（#1950、#1946）。
- 证据等级：A
- 可提炼要点：
  1. #1917：请求被取消时会丢失 notifications/cancelled——修复合并后取消语义不再吞通知。
  2. #1891：取消场景被误报为「missing OAuth metadata」，与 rust-sdk E1 的 401/403 状态保留问题同型：auth 失败原因在异常路径上被错误归类，跨 SDK 复现，可作为「MCP 授权链路健壮性」证据链登记。
- 关闭条件：未读 PR diff 验证修复方式；与 20261022-sdk-transport-governance-inspector 投递的 transport 错误处理线索是否并箱，由人工合箱定。

## E3 · typescript-sdk：Skills over MCP 指南与 SEP-2640 e2e 覆盖

- 获取日期：2026-10-23
- 来源 URL：https://github.com/modelcontextprotocol/typescript-sdk/pull/3068
- 本地原件：—
- 适用范围：官方 SDK 文档与测试合并记录（#3068、#3065，2026-10-22 合并）；覆盖 Skills 扩展（SEP-2640）在 TS SDK 的落地信号，不覆盖规范正文。
- 证据等级：A
- 可提炼要点：
  1. #3068 把 Skills over MCP 指南以「agent skill」形式发布——指南本身转为可被 agent 加载的技能包，是 Skills 分发形态的首个官方 SDK 样例（摘要级判断，需合箱时核对内容）。
  2. #3065 为 SEP-2640 Skills 扩展补 e2e 测试，延续 20261021-ts-sdk-skills-merge 投递的实现线。
- 关闭条件：SEP-2640 扩展仍为实验态，规范页无对应条款；等 specification 仓库出现 Skills 相关 release 再更新。

## 台账登记（未达开箱门槛，仅流水）

- ext-apps、experimental-ext-interceptors、java-sdk、servers 仓库 2026-10-22 的 pushed_at 事件经查为 PR 分支活动，主干无窗口内增量（ext-apps 最新主干提交 10-13，interceptors 10-13）。
- MCP spec releases 窗口内无新版本；npm `@modelcontextprotocol/sdk` latest 1.32.1、pypi `mcp` 2.3.0（10-02）均旧版；A2A 无新 release（最近 v1.0.1，10-22 前已登记）。
