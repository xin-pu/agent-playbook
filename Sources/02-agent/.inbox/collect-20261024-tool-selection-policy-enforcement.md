# 投递：小模型工具选择与策略执行编译（2026-10-24 daily）

## E1 · RL 后训练的 8B 小模型在工具选择上超过 402B 商业驱动方案

- 获取日期：2026-10-24
- 来源 URL：https://arxiv.org/abs/2610.31483
- 本地原件：`Sources/02-agent/.inbox/originals/arxiv-2610.31483-slm-tool-selection-rl.pdf`
- 适用范围：preprint，未经同行评议；覆盖万级工具库上的多步指令工具选择（检索器驱动 + RL 后训练小模型）；不覆盖端到端任务执行成功率与真实生产 API 漂移。
- 证据等级：A
- 可提炼要点：
  1. 瓶颈刻画：工具描述放不进上下文，相关性检索器只会排序、不知道哪几个工具真的被需要；现有做法用 Claude/ChatGPT 这类商业 LLM 驱动检索器做指令分解与候选选择。
  2. 结果：Qwen3-8B 经其配方后训练后在 ToolBench 上超过 Llama-4-Maverick（402B）——任务专用化小模型替代大模型驱动是成本结构级结论。
  3. 迁移性：训练后的模型可直接迁移到不同检索器，并泛化到不同领域的新工具语料——说明学到的是选择流程而非语料记忆（至少作者如此主张）。
  4. Meta + CMU 工作，作者注「Work done at Meta」。
- 关闭条件：ToolBench 榜单饱和度高，需补 ToolBench 之外的独立工具语料复现；与函数调用接口漂移箱（agent-safety）的关系要合箱时定。

## E2 · SCOPE：把自然语言策略编译成神经符号谓词程序做 Agent 策略执行

- 获取日期：2026-10-24
- 来源 URL：https://arxiv.org/abs/2610.31062
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖多回合轨迹与工具调用轨迹上的复合应用策略执行（policy enforcement）；不覆盖策略文本本身的质量与单轮内容审核。
- 证据等级：A
- 可提炼要点：
  1. 定位：LLM Agent 的策略执行已从单轮内容审核转向「复合、应用特定策略 + 多回合与工具调用轨迹」评估；微调 guardrail 高效但在复合策略上退化，LLM-as-a-judge 准但贵且预测不稳。
  2. 方法：把策略拆成窄神经判定 + 显式逻辑组合的神经符号管线，并补齐现有符号层表达力不足的缺陷——编译成谓词程序（neurosymbolic predicate programs）。
  3. 与 agent-safety-monitoring 箱（deception probes、function-calling drift）同一层次：都属于「事后监督器」路线，合箱时可归入同一箱。
- 关闭条件：摘要未给准确率/成本对比数字；需全文核对与 LLM-as-a-judge 基线的量化差距后关。
