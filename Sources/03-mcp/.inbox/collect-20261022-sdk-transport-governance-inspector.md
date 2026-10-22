# 投递：MCP 生态窗内动态（rust-sdk 传输修复、治理名单、inspector v2.12.0）（2026-10-22 daily）

## E1 · rust-sdk #1341：Streamable HTTP 上保留 401/403 语义

- 获取日期：2026-10-22
- 来源 URL：https://github.com/modelcontextprotocol/rust-sdk/pull/1341
- 本地原件：—
- 适用范围：官方仓库已合并 PR（2026-10-21T23:34Z 合入 main）；覆盖 rmcp Streamable HTTP 客户端传输层错误语义；不覆盖规范层鉴权条款本身。
- 证据等级：A
- 可提炼要点：
  1. 修复对象（#1339）：server 以 401/403 + JSON-RPC error body 响应 POST 且无 `WWW-Authenticate` 头时，reqwest 客户端把它当普通 `JsonRpcError` 返回，调用方无法识别这是鉴权拒绝。
  2. 修复方向：在传输层保留 HTTP 401/403 状态语义，使 initialize 与后续请求路径都能区分「服务拒绝」与「协议错误」。
  3. 对 OAuth/resource server 生态有意义：客户端可据状态码触发 token 刷新/授权流程而非透传错误。
- 关闭条件：等 rmcp 下一 release tag 收录该修复（当前最新 tag 为 2026-10-20 的 rmcp-v3.6.0，未含此 PR）即可关并更新版本号。

## E2 · access 仓库：金融服务 Interest Group 扩容与 Swift SDK 维护者调整

- 获取日期：2026-10-22
- 来源 URL：https://github.com/modelcontextprotocol/access/commits/main
- 本地原件：—
- 适用范围：官方治理仓库 2026-10-21 合并的三个提交（#223、#228、#229）；覆盖 WG/IG 人员台账变化；不覆盖任何规范条款变动。
- 证据等级：A
- 可提炼要点：
  1. #223：Vinay Ramesh 与 kziemski 加入 Financial Services Interest Group。
  2. #228：movetz 与 stallent 移出 Swift SDK maintainers 名单。
  3. 与 `collect-20261020-mcp-governance-wg` 投递同谱系（治理台账增量），建议人工合箱时并块登记。
- 关闭条件：无遗留缺口；下一次合箱并入即可关。

## E3 · inspector：v2.12.0 milestone 合并窗与两个客户端修复

- 获取日期：2026-10-22
- 来源 URL：https://github.com/modelcontextprotocol/inspector/commit/0cac110a
- 本地原件：—
- 适用范围：官方仓库 2026-10-21 提交序列（v2 分支 milestone merge 窗）；覆盖 MCP Inspector v2 工具链行为；不覆盖规范语义。
- 证据等级：A
- 可提炼要点：
  1. v2.12.0 milestone 合并进行中（#2769/#2776/#2767/#2770/#2771 系列 merge 提交）。
  2. fix(core)：请求 POST 被 HTTP 层拒绝时保持连接不断开（6b108c3d，经 #2777 合入）。
  3. fix(mcpdo)：`resources/directory/read` 补上 URI 与 cursor 参数（3a174cb0，经 #2775 合入）——反映 directory/read 实验性方法的参数面仍在收敛。
- 关闭条件：v2.12.0 正式 release 发布后核对 release notes 即可关。

## 台账登记（本轮窗内 03-mcp 未开箱项）

- registry 仓库 pushed_at 更新到 2026-10-21T23:34Z，但默认分支窗内无新提交（疑似 PR 分支推送）：https://github.com/modelcontextprotocol/registry
- npm `@modelcontextprotocol/sdk` latest 仍为 1.32.1（2026-10-05），pypi `mcp` 仍为 2.3.0（2026-10-02）：无发布节奏增量。
- typescript-sdk pushed_at 2026-10-21T15:14Z，默认分支窗内无提交：无增量。
