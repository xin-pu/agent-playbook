# 投递：混合策略优化与蒸馏-RL 协同（2026-10-23 daily）

## E1 · MOER：专家前缀引导下的混合策略优化与选择性回滚

- 获取日期：2026-10-23
- 来源 URL：https://arxiv.org/abs/2610.30873
- 本地原件：`Sources/00-rl/.inbox/originals/arxiv-2610.30873-moer-mix-policy-expert-prefix.pdf`
- 适用范围：preprint，未经同行评议；覆盖把 off-policy 专家数据注入 RL 环内（mix-policy）做推理训练的前缀引导与回滚机制；不覆盖非 CoT 任务与在线探索环境。
- 证据等级：A
- 可提炼要点：
  1. 作者把现有 mix-policy 方法的两类失败模式概括为：静态全轨迹引导会抑制自我探索；专家前缀引导缺少正确性保证，可能次优甚至训练坍缩。
  2. MOER 三个机制：向 prompt 注入随训练递减（anneal）的专家 CoT 前缀、由模型续写剩余推理；选择性回滚把失败续写替换回完整专家轨迹，保证每条 off-policy 轨迹正确；配套的 harmonized mix-policy 目标协调两类信号。
  3. 与 20261022 投递的 One Act, Many Masks（2610.29427）同属「专家信号如何进入策略更新而不破坏 on-policy 探索」这一线，可在合箱时互引。
- 关闭条件：未核对全文实验表（基线集合与规模）；同组会议版录用或第三方复现后可关。

## E2 · GIFT：梯度信息过滤，解决蒸馏与 RL 的更新兼容性

- 获取日期：2026-10-23
- 来源 URL：https://arxiv.org/abs/2610.30796
- 本地原件：`Sources/00-rl/.inbox/originals/arxiv-2610.30796-gift-gradient-informed-filtering.pdf`
- 适用范围：preprint，未经同行评议；覆盖推理 RL 中「稀疏结果奖励 + 稠密 token 级蒸馏」混合目标的梯度冲突过滤；不覆盖非蒸馏类辅助损失。
- 证据等级：A
- 可提炼要点：
  1. 核心命题：监督信号互补不等于优化方向兼容——以模仿为主的蒸馏梯度会与结果驱动的 RL 目标冲突，现有混合方法缺乏原则性处理。
  2. GIFT 在 token 级做几何分解：把蒸馏梯度拆为与 RL 梯度平行分量（度量一阶冲突、充当安全过滤）与正交分量，据此过滤教师更新、决定「哪些教师更新可以施加」。
  3. 与 2610.26525（Fisher 多教师蒸馏，已在 00-rl .inbox）同为「蒸馏更新选择性施加」路线，合箱时可归入 policy-optimization 的蒸馏交互子题。
- 关闭条件：过滤阈值的超参敏感性与消融未核对（未读全文）；需补读实验节或等复现。

## E3 · Inherited, Not Invented：推理模型中 `{wait}` 标记的来源追踪

- 获取日期：2026-10-23
- 来源 URL：https://arxiv.org/abs/2610.30882
- 本地原件：`Sources/00-rl/.inbox/originals/arxiv-2610.30882-wait-provenance-reasoning.pdf`
- 适用范围：preprint，未经同行评议；覆盖开源推理模型（OLMo-3、MiMo 等）中 `{wait}` 行为标记的来源归因（RL 发现 vs 数据继承）；不覆盖闭源模型与非文本行为。
- 证据等级：A
- 可提炼要点：
  1. 用无标签指标（频率、位置、形式、用法）加注入错误测试追踪 `{wait}` 在训练史中的出现；结论是 zero-RL 几乎不「发明」该标记：缺词基座上 RL 显著提升 MATH-500 而 `{wait}` 仍近乎缺席。
  2. 标记来自数据：OLMo-3 在 mid-training 引入，在推理轨迹上 fine-tuning 则为多数缺词基座安装该标记；基座已用词时，OLMo-3 与 MiMo 的 RL-Zero 配方都会放大它，而同基座的 KL-free GRPO 不放大。
  3. 方法论含义：RL 带来的准确率增益与特定 token 行为归因要分开，可为「行为继承 vs RL 发现」与 credit assignment 讨论提供反例证据（呼应 E1 的专家信号注入问题）。
- 关闭条件：摘要截断处 OLMo-3 的 r… 结论未取全，需读全文实验节；其余模型谱系覆盖不全。

## 台账登记（未达开箱门槛，仅流水）

- 本轮 00-rl 窗口内其余 arXiv 命中未达开箱门槛，仅登记：2610.30888（演示文稿生成，RL 仅边缘提及）、2610.30667（组合拍卖 DRL 应用）、2610.30564（RL+LLM 组合配置应用），与既有箱主题不同层次但无原件精读价值。
