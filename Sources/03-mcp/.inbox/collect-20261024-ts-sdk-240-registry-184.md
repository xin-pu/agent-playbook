# 投递：MCP TS SDK v2.4.0 与 Registry 1.8.x 三连发（2026-10-24 daily）

## E1 · typescript-sdk v2.4.0：Skills over MCP（SEP-2640）落到 SDK，spec 校验收紧

- 获取日期：2026-10-24
- 来源 URL：https://github.com/modelcontextprotocol/typescript-sdk/releases/tag/v2.4.0
- 本地原件：—
- 适用范围：官方 release 说明（A 级），发布 2026-10-23T18:32Z；覆盖 TS SDK client/server/core/legacy/codemod 2.4.0 与 node 2.1.2；不覆盖其他语言 SDK，也不覆盖 spec 本身的修订。
- 证据等级：A
- 可提炼要点：
  1. 新功能：Skills over MCP（SEP-2640）进入 SDK——server 用 `loadSkills(folder)` + `skills.attach(server)` 发布技能目录，client 用 `SkillsClient` 列出/读取/校验；同时支持 2025-11-25 与 2026-07-28 两个 spec 版本，`attach` 标注 experimental、允许小版本内变更。这使 03-mcp 连续三轮（10-17/10-21/10-23）跟踪的 skills extension 从提案走到 shipped。
  2. 破坏性收紧：按 2026-07-28 spec 拒绝 `number` 参数上的 `x-mcp-header`（client 不列出该 tool，server 回 `-32020`）；2025-11-25 连接上 `outputSchema` 不再包一层 `{ result }`，读 `structuredContent` 本体——两条都是可直接写进迁移参考的行为变更。
  3. 认证侧：新增 opt-in 的 `scopeForRefresh(tokens)`，针对无 scope 即拒绝 refresh 的授权服务器（Microsoft Entra ID `AADSTS90009`）；默认请求不变。
  4. 发布节奏佐证：同版本线 legacy 1.32.2 于 2026-10-23T18:06Z 发出，npm dist-tag latest 指向 1.32.2（2026-10-23T18:11Z，registry.npmjs.org/@modelcontextprotocol/sdk）；pypi `mcp` 本窗口无新版本（最新仍 2.3.0，10-02）。
- 关闭条件：SEP-2640 的服务端语义要与 03-mcp 既有 skills 证据块（10-17/10-21/10-23 三轮投递）合并核对，由人工判定是否触发 mcp-spec-evolution 箱分裂。

## E2 · MCP Registry 单日 v1.8.2→v1.8.4 三连发并推进生产

- 获取日期：2026-10-24
- 来源 URL：https://github.com/modelcontextprotocol/registry/releases
- 本地原件：—
- 适用范围：官方 releases 与 commits API（A 级），窗口 2026-10-23T14:34Z–20:34Z；覆盖 registry 服务的发布节奏与 5 条 main 提交主题；不覆盖各 patch 的具体 diff 内容。
- 证据等级：A
- 可提炼要点：
  1. 节奏事实：10-23 一天内 v1.8.2（14:34Z）、v1.8.3（19:02Z）、v1.8.4（20:34Z）三个 release，并各有 `chore(deploy): promote production` 提交（#1731、#1732）——注册处在做高频小步发布。
  2. 修复主题集中在 publish 校验与检索性能：`fix(publish): validate registries outside the transaction and time the pool wait`（#1562）、`fix(database): index server name substring searches`（#1730）、`fix(publish): correct misleading org-namespace guidance in 403 and docs`（#1483）。
  3. 与 06-news/registry 治理线（10-20 governance-wg）同域，可作 registry 运营成熟度的连续证据。
- 关闭条件：未取各 tag 的完整 changelog 对比；要写「单日三发」进正文前需人工核对 promote 提交是否等价生产可见。
