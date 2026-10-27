# 投递：经验学习与第一视角助手两类新基准（2026-10-27 daily）

> 巡检通道：arXiv API（benchmark/agent 与 agent 查询双路命中）。两篇 v1 提交于 2026-10-25，本批随 2026-10-26/27 公告可见，判重均未见于 `Sources/`。原件 2 份存 `Sources/04-benchmarks/.inbox/originals/`（其中 CLE 原件无版本 URL 首次返回 "No file"，改 `v1` 直链断点续传成功，记入运行注意事项）。

## E1 · Continual Learning Exam：120 任务五层阶梯测「从经验中持续进步」

- 获取日期：2026-10-27
- 来源 URL：<https://arxiv.org/abs/2610.33956>
- 本地原件：`Sources/04-benchmarks/.inbox/originals/arxiv-2610.33956-continual-learning-exam.pdf`
- 适用范围：preprint，未经同行评议；覆盖 LLM agent 在真实职业工作流中「积累经验—改进—保留旧知识」的长程评测；不覆盖单任务一次性求解能力与训练期 continual learning（防灾难遗忘）研究。
- 证据等级：A
- 可提炼要点：
  1. 构造（原文口径）：50+ 领域专家出题，120 个人工任务组织成五层阶梯，共 600 个 level，跨 12 个职业域、89 种职业角色；须通过前一层才能解锁下一层，后层依赖前层积累的经验；由 evaluation agent 按人工评分细则（rubric）判定每次提交。
  2. 两种设定对比：单次提交 vs 失败后给诊断反馈并允许一次修订；17 个 harness-model 配置（frontier LLM）中，反馈+修订仅带来中位 +5.3 个百分点的完成率增益（预印本数据，未复现）。
  3. 难度锚点：最佳系统只清掉 47.7% 的 level，五个 level 全通的任务仅占 23.3%——「从经验中持续学习」仍是显著开放缺口。
  4. 与既有箱关系：为 agent-benchmarks 线补上「长程经验改进」维度，与 10-26 登记的 TraceTrial-Bench、rubric 类评测互补，合箱时互设引用不复制事实。
- 关闭条件：缺第三方复现与 leaderboard 记录；17 个 harness-model 配置清单和评分 agent 的 rubric 稳定性需核对附录后再引用逐配置数值。

## E2 · InteractiveWorld/InteractiveBench：人本位可验证闭环环境，第一视角助手基准

- 获取日期：2026-10-27
- 来源 URL：<https://arxiv.org/abs/2610.33966>
- 本地原件：`Sources/04-benchmarks/.inbox/originals/arxiv-2610.33966-interactiveworld-mllm.pdf`
- 适用范围：preprint，未经同行评议；覆盖可穿戴场景下第一视角 MLLM 助手与自然语言引导驱动「人类 agent」交互的闭环模拟与多轮评测；不覆盖真实人体在环实验与机器人本位仿真（论文明确区别于 robot-centric simulators）。
- 证据等级：A
- 可提炼要点：
  1. 环境设定（原文口径）：Meta 与 Duke 团队提出首个「可验证的人本位交互环境」——助手的自然语言指引驱动 human agent 行动并改变世界状态，用于替代昂贵稀少的真人交互数据；基准 InteractiveBench 为多轮闭环，含 120 个 multi-turn 任务、六大类（Guidance、Planning、Accessibility 等），成功以可验证的状态奖励（state-based rewards，模拟器最终物体状态判定）度量。
  2. 结果口径：12 个 frontier MLLM 参测；最强模型（原文点名 Claude Fable 5.1）也仅成功 41.7% 的任务，其余模型全部 ≤33.3%；细项 Guidance 与 Planning 两个维度最佳模型仅 20.0% 与 25.0%，长程交互任务仍普遍表现差（预印本数据，未复现）。
  3. 方法论信号：把「评测者=环境状态机」的做法从代码/终端基准迁移到第一视角生活任务，与 10-26 的 harness 归因线（2610.32483）共同支撑「以可验证状态而非文本相似度判分」的评测趋势。
- 关闭条件：缺第三方复现；human agent 的行为模型如何构造（LLM 扮演还是脚本）需核对实现章节，否则「人本位」结论只按作者口径引用。
