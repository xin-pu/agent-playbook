# 投递：MCP ruby-sdk 协议一致性修复（2026-10-19 daily）

> 本文件为未入箱投递，合箱由人工主流程处理。候选去向：`03-mcp` 域 mcp-server-ecosystem 箱。

## E1 · ruby-sdk 在 24 小时窗口内合入 Accept 头解析与错误响应一致性修复

- 获取日期：2026-10-19
- 来源 URL：<https://github.com/modelcontextprotocol/ruby-sdk/commits/main>
- 本地原件：—
- 适用范围：官方仓库 main 分支公开提交记录（2026-10-18T16:10~16:34Z），覆盖 header 解析容错与 JSON-RPC 错误响应形态；不覆盖发版（ruby-sdk 无窗口内 release）。
- 证据等级：A
- 可提炼要点：
  1. PR #616（merge 4559336ee）：忽略 Accept 头中的空成员，提升对宽松/畸形 header 的解析容错（commit message）。
  2. PR #622（merge 06d537280，fix 8c68fcbc6）：对不可读的 request id 拒绝时响应不带 `id`，与 JSON-RPC「无法关联请求 id 时 id 为 null/缺省」的错误响应形态对齐（commit message）。
  3. 窗口前一日（2026-10-17）rust-sdk main 分支合入 session-less 非 initialize POST 返回 400 的修复（提交 50fba5c28，见 GitHub API 抓取记录），与本轮 ruby-sdk 两处修复构成同一趋势：官方各语言 SDK 正在收紧 spec conformance 的边界行为。
- 关闭条件：需核对 python/typescript-sdk 是否有对应条款的同类修复以确认是跨 SDK 一致化运动；spec FAQ/errata 出现对应条款说明后可关。
