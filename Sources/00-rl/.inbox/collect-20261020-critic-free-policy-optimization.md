# 投递：critic-free 策略优化与 RLVR 信用再分配（2026-10-20 daily）

> 本文件为未入箱投递，合箱由人工主流程处理。候选去向：`00-rl` 域 policy-optimization 箱（终端奖励稀疏与 group-relative advantage 的粒度问题同主题）。

## E1 · ProbePO：稀疏探针 + 预算化测量再分配 GRPO token 级信用

- 获取日期：2026-10-20
- 来源 URL：<https://arxiv.org/abs/2610.24515>
- 本地原件：`Sources/00-rl/.inbox/originals/arxiv-2610.24515-probepo-critic-free-rl.pdf`
- 适用范围：preprint，未经同行评议；覆盖 1.5B–7B 模型（DeepSeekMath 与 Qwen 系）数学推理 RLVR 下的 token 级信用分配；不覆盖多轮 agentic 环境与通用 RL。
- 证据等级：A
- 可提炼要点：
  1. 把「终端奖励到整条轨迹」的信用缺失问题重述为预算化测量（budgeted measurement）：在有限 rollout 预算内选择要评估的部分解状态，用其价值估计细化信用，而非生成新训练数据（摘要与 §1）。
  2. 方法要点：用 reward-free 的不确定性分数选择部分解状态，在封顶延续预算下估计其期望 verifier 奖励；对 GRPO 的轨迹级 advantage 做再分配而非替换，保持每条轨迹的 token 级 advantage 均值不变，探针延续只作测量用（摘要）。
  3. 结果口径：三个 1.5B–7B 模型上稳定优于 GRPO，四方法对比中 16/18 个模型–基准组合取得最高准确率（预印本数据，未复现）。
- 关闭条件：v1 未见第三方复现；不确定性分数选点策略与封顶预算的消融需全文精读核对；会议版或复现报告出现后可关。

## E2 · 用神经双 critic 直接学习 general-utility RL 的伪奖励

- 获取日期：2026-10-20
- 来源 URL：<https://arxiv.org/abs/2610.24880>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖凹的 RL with General Utilities（RLGU，占用测度的非线性泛函目标）的 actor-critic 构造与样本复杂度分析；不覆盖 LLM 后训练实证。
- 证据等级：A
- 可提炼要点：
  1. 路线差异：不先估计占用测度再构造 policy-gradient 伪奖励，而是用神经 critic 把伪奖励直接学成 state-action 的函数；critic 用投影随机更新训练（摘要）。
  2. 用多层蒙特卡洛（multilevel MC）跨训练时域组合输出，把 critic 偏差控制在期望对数级成本内；分析分离了条件 actor 偏差与估计器偏差（摘要）。
- 关闭条件：理论口径（对数成本、偏差分解）需读全文定理核对；无 LLM 侧实验，是否可迁移到 RLVR 场景未验证。

## E3 · RLVR 增益的定位：约 4% 生成位置的换词即恢复 90.5% pass@1 增益

- 获取日期：2026-10-20
- 来源 URL：<https://arxiv.org/abs/2610.24663>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖 Qwen3-4B-Base 与其 RL 变体在 120 道 AIME 题上的生成时干预分析；不覆盖训练算法设计与非数学域。
- 证据等级：A
- 可提炼要点：
  1. 同为 8,192 token 输出上限下的 power sampling 相对 greedy 解码几乎没有增益；仅在两模型 greedy 选择不同的位置（约 4% 的生成位置）借用 RL 模型的 token，即可恢复 pass@1 增益的 90.5%，三个模型对在 MATH-500 上恢复率相近（预印本数据，未复现）。
  2. 单点开路效应：强制 base 模型以特定起始 token 开头即产生显著影响，提示 RLVR 增益集中在少数决策点而非分布性能力提升（摘要）。
- 关闭条件：4% 位置与 90.5% 恢复率的测量口径（逐题还是聚合）待全文核对；需要跨模型族复现后可关。
