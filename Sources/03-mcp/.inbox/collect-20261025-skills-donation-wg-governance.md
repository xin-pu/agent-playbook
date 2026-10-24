# 投递：MCP 与协议生态——Skills 捐赠 AAIF、Tasks & Events WG、A2A 治理扩容（2026-10-25 weekly）

建议主箱：`03-mcp/agent-protocols-landscape`（协议治理线）；E1 与 `mcp-spec-evolution` 亦有交叉，合箱时二选一为主箱。其中 E1 为 10-24 daily 台账显式留给 weekly 档补采的两条之一。

## E1 · Anthropic 将 Agent Skills 开放标准捐赠给 Linux 基金会旗下 Agentic AI Foundation

- 获取日期：2026-10-25
- 来源 URL：https://www.anthropic.com/news/donating-agent-skills-to-the-agentic-ai-foundation
- 本地原件：—（官方公告为 HTML 单页，已存档可再生成，不入库二进制）
- 适用范围：官方发布（A 级一手），发布日 2026-10-22；覆盖 Anthropic 单方口径的捐赠决定、采纳规模与治理承诺；不覆盖 AAIF 章程细节与其他成员表态。
- 证据等级：A
- 可提炼要点：
  1. 事实：Agent Skills（SKILL.md 文件夹教 agent 特定任务/域、可附脚本与参考资料）自 2025-12 作为开放标准发布后，已有 70+ agent 平台集成（公告点名 ChatGPT、Cursor、GitHub Copilot、VS Code）；官方口径称已发布 100 万个 skills、安装近 2.8 亿次（企业自报数字，未见独立审计）。
  2. 治理动作：标准捐赠给 Linux 基金会下的 Agentic AI Foundation（Anthropic 为联创方之一），承诺保持开放、社区驱动、厂商中立。
  3. 生态判断依据：这是「单厂商标准 → 基金会托管」路径在 skills 层的实例，与 10-18 档 MCP 扩展「WG→独立仓→规范快照」通道同构，可作协议扩展治理模式化的第二证据（跨箱引用 `03-mcp/mcp-spec-evolution#E1`，不复述）。
- 关闭条件：缺 AAIF 侧公告/章程与第三方对采纳规模的核数；AAIF 官方发布或中立统计出现后可关。

## E2 · MCP 规范仓合并 Tasks & Events WG 分支：任务/事件扩展进入规范治理轨道

- 获取日期：2026-10-25
- 来源 URL：https://github.com/modelcontextprotocol/modelcontextprotocol/pull/3440
- 本地原件：—（GitHub API 元数据可复查）
- 适用范围：官方仓库提交记录（A 级一手），合并时间 2026-10-20；覆盖「tasks-events-wg 分支经评审并入规范仓（Agents IG 范围措辞与名册、Tasks 范围）」这一治理事实；不覆盖 tasks/events 的条款级设计内容与目标规范版本。
- 证据等级：A
- 可提炼要点：
  1. 治理事实：规范主仓在 2026-07-28 stable 之后出现 tasks & events 工作组轨道的结构性合并（同窗另有 Agents Interest Group 范围/名册的评审修订，见 commit 761239a3）。
  2. 判断价值：与 File Uploads WG（10-14 开仓，见 `03-mcp/.inbox/collect-20261018-mcp-weekly.md#E1`，跨箱引用不复述）并列，说明扩展议题按「IG/WG 立项→范围评审→规范仓合并」节奏推进，tasks/events 是当前最活跃的下一候选扩展。
- 关闭条件：未读 PR diff，无法给出条款级要点；需拉取 contents 原文核对合并内容，或在 2026-07-28 后首个 changelog 出现 Tasks 条目后升级为条款证据。

## E3 · A2A 技术指导委员会吸收 Bloomberg 为新成员

- 获取日期：2026-10-25
- 来源 URL：https://github.com/a2aproject/A2A/pull/2308
- 本地原件：—
- 适用范围：官方仓库提交记录（A 级一手），2026-10-20 并入；覆盖 A2A 协议 TSC 成员变更这一治理事实；不覆盖 TSC 决策内容与版本路线影响。
- 证据等级：A
- 可提炼要点：
  1. 事实：金融数据机构 Bloomberg 加入 A2A（Agent2Agent 协议）技术指导委员会；提交为 chore 类，无版本号变动（A2A 最近 release 仍是 2026-05-28 v1.0.1）。
  2. 判断价值：TSC 成员从模型厂商向金融机构扩展，是 A2A 治理面扩宽的低强度信号；与 E2 合看，「agent 协议治理机构化」在 MCP 与 A2A 两侧同窗出现。
- 关闭条件：单一 chore 提交，信息面窄；需 A2A 官方新闻稿或后续 TSC 议程记录来确认其实际决策影响。

## E4 · MCP Apps 示例仓新增 get-screenshot app tool（map-server 例）

- 获取日期：2026-10-25
- 来源 URL：https://github.com/modelcontextprotocol/ext-apps/pull/821
- 本地原件：—
- 适用范围：官方仓库提交记录（A 级一手），2026-10-23 并入；覆盖 ext-apps 示例集扩充这一工程事实；不覆盖 Apps 协议本身条款变更（最近版本动作仍是 09-25 的 2.0.3）。
- 证据等级：A
- 可提炼要点：
  1. 事实：ext-apps 的 map-server 示例加入名为 get-screenshot 的 app tool，说明「app 侧工具声明 + host 截图能力」组合在参考实现中被当作标准样例沉淀。
  2. 判断价值：示例先行是该扩展仓的既有节奏（此前 pdf-server 依赖治理亦先在示例层出现），可作为观察 Apps 扩展 API 稳定性的低风险前哨。
- 关闭条件：仅示例层变更；需 Apps 规范文本或 SDK 类型出现对应字段后再升级为协议证据。

---

## 台账登记

- `10-22` 出窗补采清单：`open-call-guest-investigators-life-sciences`（10-22 公告，生命科学客座调查员开放申请）——主题偏机构合作，未达开箱门槛，仅登记标题与链接：https://www.anthropic.com/news/open-call-guest-investigators-life-sciences
- python-sdk 复查（不入块）：#3719（10-16 目录读缓存字段与 Skill `_meta`）、#3726（10-17 SSE 独立 header）、#3752（10-24 security bump）均在窗边或信息面窄，前两条在 7 天窗（10-18 起）之外，第三条为依赖升级；如后续发版再登记。
- npm `@modelcontextprotocol/sdk` latest=1.32.2（2026-10-23 发布）与 GitHub typescript-sdk 1.32.2/v2.4.0 release 同源，已由 10-24 daily（`collect-20261024-ts-sdk-240-registry-184.md`）登记，不重复。
