# 投递：奖励审计、harness 共同演化与 critic 训练（2026-10-28 daily）

> 巡检通道：arXiv API（同轮 `collect-20261028-group-policy-optimization-hard-rollouts.md` 头部说明）。窗口 2026-10-27T00:00Z~2026-10-28T01:10Z。判重：2610.35716 / 2610.36469 / 2610.35518 均未见于 `Sources/`（与 10-21 投递的 rubric-hacking-divergence、10-26 的 agents-fail-harness 为不同 arXiv ID）。原件 1 份存 `.inbox/originals/`。

## E1 · 预算受限的强验证器审计：先审「弱通过最少」的整组

- 获取日期：2026-10-28
- 来源 URL：<https://arxiv.org/abs/2610.35716>
- 本地原件：`Sources/00-rl/.inbox/originals/arxiv-2610.35716-budgeted-verifier-audits.pdf`
- 适用范围：preprint，未经同行评议（封面标注 "Preprint, October 2026"，作者清华 REASONS Lab/Virginia Tech）；覆盖 RLVR 中廉价检查（单元测试等）可被策略钻空、强检查跑不起全量时的 GRPO 审计预算分配；不覆盖非组相对估计器与在线验证器选型。
- 证据等级：A
- 可提炼要点：
  1. 框架：固定策略状态、优势居中时期望更新只通过「每个 rollout 的边际审计概率 × 纠正量」依赖审计设计，据此把「审谁」与「审出 hack 后给什么奖励」两个设计决策解耦。
  2. 结论（原文口径）：把查出的 hack 奖励关于失败奖励做镜像反射，可抵消「全 hack 组」的优势；当标注价值随通过数下降时，优先整组审计弱通过数最少的组（low-pass budgeted audits，LB）能最小化留在 hack 上的优势质量。
  3. 验证方式：从各训练起始状态用冻结面板上的优势质量符号预测 hack 是否被抑制，39 次运行命中 33 次（含预注册 16 次中 13 次）（预印本数据，未复现）；与 10-21 投递的 rubric-hacking-divergence 构成「度量风险 → 预算化审计」推进链，合箱时同箱。
- 关闭条件：LeetCode 等实验设定与强验证器成本数字未逐条核对；缺第三方复现；同工作会议版或公开代码后可关。

## E2 · CoHARL：策略与可执行 harness 种群共同演化

- 获取日期：2026-10-28
- 来源 URL：<https://arxiv.org/abs/2610.36469>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖 LLM agent 训练中「接口（harness）本身作为可学习变量」的种群式 RL 框架；不覆盖固定 harness 下的单纯策略优化对比，不覆盖生产 harness 工程实践。
- 证据等级：A
- 可提炼要点：
  1. 问题界定：为固定策略优化 harness 会忽略策略行为在学习中的变化；在固定 harness 下训练策略则让「生成训练经验的接口」原地不动——两者都丢弃了接口-策略耦合信号。
  2. 方法：种群式 RL——共享策略与一组可执行 harness 共同演化；策略在整个种群的 rollout 上学习，proposer 依据执行轨迹在训练期间直接修订 harness 代码。
  3. 跨箱链：与 10-22 投递的 agentic-rl-harness-env、10-26 的 agents-fail-harness（02-agent）构成「harness 是故障面 → harness 是训练变量」的视角演进；摘要结果句在抓取文本中被截断，本块不登记任何定量结论。
- 关闭条件：主实验结果与基线未核对（无原件）；下轮补 PDF 或人工合箱时读全文后再登记定量口径。

## E3 · S3AC：长链推理的实用 critic 训练配方（stabilized/selective/scalable actor-critic）

- 获取日期：2026-10-28
- 来源 URL：<https://arxiv.org/abs/2610.35518>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖长 CoT 推理中用训练好的 critic 替代 critic-free 组基线的配方级方案；不覆盖多模态与短回答任务。
- 证据等级：A
- 可提炼要点：
  1. 痛点：critic-free（GRPO 类）缺 token 级 credit assignment、只能靠组内 rollout 估计 prompt 级基线；而长 CoT 的 critic 训练受轨迹长度覆盖不足与早期梯度被新初始化 value head 主导两处拖累。
  2. 方法：S3AC 围绕「可落地的 critic 训练配方」组织（稳定化/选择性/可扩展三前缀对应原文三卖点），训练完成后 critic 提供 token-specific 优势。
  3. 主题坐标：与本域 10-20 投递的 probepo（critic-free 线）构成同一权衡的两极，合箱时建议并入 critic/credit-assignment 相关箱对照登记。
- 关闭条件：配方细节、critic 训练开销与胜率数字未回原文核对（无原件）；补齐 PDF 或引用前回到原文方可关。
