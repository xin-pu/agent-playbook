# 投递：编码 agent 基准的完整性维护（2026-10-20 daily）

> 本文件为未入箱投递，合箱由人工主流程处理。候选去向：`04-benchmarks` 域 agent-benchmarks 箱（SWE-bench 系与评测方法学同主题）。

## E1 · SWE-Bench Pro V2：代理审计+双工程师验证翻新 480/731 任务并硬化评测协议

- 获取日期：2026-10-20
- 来源 URL：<https://arxiv.org/abs/2610.24206>
- 本地原件：`Sources/04-benchmarks/.inbox/originals/arxiv-2610.24206-swe-bench-pro-v2.pdf`
- 适用范围：preprint，未经同行评议；Scale AI + Reflection AI，覆盖长程软件工程任务基准的维护与防作弊协议；不覆盖非编码类 agent 基准。
- 证据等级：A
- 可提炼要点：
  1. 维护工艺：agentic audits + 专家仲裁 + 盲重实现，修复或退役 731 任务中的 480 个；23 名合同工程师 404 小时，每条修订指令由第二名工程师仅凭题面解出验证（预印本数据，未复现；480 退役口径与 V2 public split 642 任务的关系需全文核对，疑为增补了新任务）。
  2. 协议硬化：网络访问限制到模型端点、每个 patch 在干净容器重新判分，阻断拉取上游修复与补丁外改判分（摘要）。
  3. 区分度结果：V2 上 frontier agent 最高解出 99.4% 而其余系统明显分层；另设 51 任务 Hard split 把系统拉开在 52.9%–98.0%（预印本数据，未复现）。
- 关闭条件：642/731 任务集关系与 Hard split 构造规则待全文核对；leaderboard 是否随 V2 重置未见说明，官方发布页确认后可关。

## E2 · HSPR：用层次后验从少量题恢复软件 agent 基准全分

- 获取日期：2026-10-20
- 来源 URL：<https://arxiv.org/abs/2610.24611>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖基准评测预算受限时的「保留排名但恢复准确分数」统计方法；不覆盖基准本身的题面质量治理。
- 证据等级：A
- 可提炼要点：
  1. 问题：小任务子集能保 agent 排名但分数失真；源 agent 响应结构可借用，但同一源响应对新 target agent 可能有不同结局（摘要）。
  2. 方法：HSPR 组合 source-fitted response factors 与不确定组成功率，观测结果更新 target 潜状态与组率先验；采集准则等价于「全分后验方差的一步期望降幅」，用观测成功 + 未问题目的后验预测计数外推全分（摘要）。
- 关闭条件：外推分数与真全分的相关性/误差界数值未从摘要取得，需全文；在 SWE-bench 之外的可迁移性未验证，复现后可关。

## E3 · Spoilers vs Guesswork：题面过规范缩短基准寿命，欠规范诱发抄袭与 reward hacking

- 获取日期：2026-10-20
- 来源 URL：<https://arxiv.org/abs/2610.22760>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖编码基准的题面规范度设计张力（方法学/立场类论文）；不覆盖非 repository-level 基准。
- 证据等级：A
- 可提炼要点：
  1. 概念对：under-specification 导致 guesswork（含走污染/reward hacking 捷径）；over-specification 导致 spoilers（可绕过本应测量的难点），后者直接缩短面向未来基准的采用寿命（摘要）。
  2. 现状批评：SWE-bench Pro、FEA-bench、Doc2Feat-bench 与 Multi-SWE-bench 都以增补题面治欠规范，但双侧重复返工（churn）未解（摘要列举，未复现验证）。
- 关闭条件：作者替代方案（规范度度量或协议）未从摘要取得，需全文定位其提案节；作为方法学立场文，与 E1 的实证维护工艺对读后由人工决定进哪篇正文。
