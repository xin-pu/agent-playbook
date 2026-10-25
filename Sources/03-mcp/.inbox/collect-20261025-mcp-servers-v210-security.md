# 投递：MCP 参考服务器 v2.1.0 安全修复发布（2026-10-25 daily）

## E1 · servers v2.1.0：三个参考服务器修掉 8 个漏洞，含文件系统逃逸与 SSRF 判定链

- 获取日期：2026-10-25
- 来源 URL：https://github.com/modelcontextprotocol/servers/releases/tag/v2.1.0
- 本地原件：`Sources/03-mcp/.inbox/originals/github-mcp-servers-v2.1.0-release.json`
- 适用范围：官方 release 说明（一手发布记录，2026-10-25T00:03:20Z 发布），覆盖 `@modelcontextprotocol/server-filesystem`、`@modelcontextprotocol/server-everything`、`mcp-server-fetch` 三个包的修复范围与版本边界；不含各 GHSA advisory 的补丁实现细节，也未覆盖 Windows 路径的完整修复状态。
- 证据等级：A
- 可提炼要点：
  1. 影响面：`server-filesystem` 1.0.0–2.0.0 与 date 版本至 2026.8.31、`server-everything` 1.0.0–2.0.0 与 2025.9.24–2026.8.31、`mcp-server-fetch` 至 2026.10.19，分别修复于 2.0.1 / 2.0.1 / 2026.10.24。
  2. `server-filesystem` 四类路径绕过：检查与写入之间的 TOCTOU 符号链接重定向（GHSA-53mr）、访问检查剥离了文件操作保留的尾部引号/空白（GHSA-7rgq）、大小写不敏感卷上不同拼写的符号链接通过检查且系 2026.8.31 回归（GHSA-4gxg）、`list_directory_with_sizes` 未逐项检查即读取大小泄露目录外文件元数据（GHSA-hhwq）；Windows 仅部分修复，剩余暴露面写入 advisory。
  3. `server-everything` HTTP/SSE 传输改为校验 `Origin` 且不再发送 `Access-Control-Allow-Origin: *`（GHSA-mvf5）——网页可对本地调试服务器发起工具调用的旧行为被关闭。
  4. `mcp-server-fetch` SSRF 判定链三修：IDNA 主机名「检查一个形态、连接另一个形态」（GHSA-v38p）、NAT64 前缀 `64:ff9b::/96` 内嵌私有/回环/链路本地 IPv4 现按内嵌地址拒绝（GHSA-66qx）、robots.txt 改为每次重定向后复查（GHSA-3jqg）。
  5. 升级陷阱：TS 服务器从 date 版本迁到 semver 后，包管理器会把 2.0.1 排在 2025.x/2026.x 之下而不主动升级，date 版本用户须显式 `npm install @2.0.1`——分发层与版本语义错位的直接案例。
  6. 同 release 附带主干变更：TS SDK 依赖升到 2.4.0、Node adapter 2.1.2（#5245），延续 10-24 投递的 ts-sdk v2.4.0 落地线。
- 关闭条件：未读 8 条 GHSA advisory 正文与 diff 验证修复方式；待人工合箱并入 mcp-server-ecosystem 或安全线相关箱，advisory 逐条核对后本块可关。

## 复查（不入块）

- 上一版 v2.0.0 发布于 2026-10-19T06:46Z，各轮投递均未登记该 tag；合箱时建议以 v2.0.0→v2.1.0 compare（full changelog 见 release 正文）一并补记版本节奏，本块只登记 v2.1.0 增量。
- 本窗口 `modelcontextprotocol/specification` 无新 release；`typescript-sdk` 无新版本（v2.4.0 已在 10-24 daily 入块）。
- release 正文含一个 claude.ai artifact 链接（release ledger），属外部一次性页面，未抓取、不作证据。
