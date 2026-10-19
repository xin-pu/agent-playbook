# 投递：函数调用鲁棒性、记忆充分性与 agent 轨迹标注（2026-10-19 daily）

> 本文件为未入箱投递，合箱由人工主流程处理。候选去向：`02-agent` 域 agent-memory-state 箱、工具调用与可观测性相关箱。

## E1 · 接口漂移下的轻量无训练函数调用修复层（SchemaShield-Lite）

- 获取日期：2026-10-19
- 来源 URL：<https://arxiv.org/abs/2610.23342>
- 本地原件：`Sources/02-agent/.inbox/originals/arxiv-2610.23342-function-calling-interface-drift.pdf`
- 适用范围：preprint，未经同行评议；独立研究者三作者，仅 Qwen3.5-9B 一个底座模型上的 DICE-300 / BFCL-200 切片实验；不覆盖跨模型族与生产网关场景。
- 证据等级：A
- 可提炼要点：
  1. 把部署后工具描述、参数 schema、候选工具列表在语义不变时发生文本变化导致的失稳定义为 interface drift，作为 function-calling 系统的实用可靠性故障模式（摘要）。
  2. SchemaShield-Lite = schema 校验 + 缺工具名时的候选集重试 + 一次性受约束修复，training-free；Qwen3.5-9B 上 DICE-300 准确率 0.717 → 0.813（预印本数据，未复现）（摘要与 §实验）。
- 关闭条件：单一底座模型、无代码仓库链接确认；需跨模型验证与复现后才可关。

## E2 · 决策级记忆充分性：交互感知的 agent 记忆选择（JointCore / JointCoreBench）

- 获取日期：2026-10-19
- 来源 URL：<https://arxiv.org/abs/2610.23266>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖冗余或联合必要证据下的最小子集选择，构造了带精确充分集 oracle 的合成+工作流基准；不覆盖开放式长会话记忆。
- 证据等级：A
- 可提炼要点：
  1. 基于记录相关性或单条影响的检索排名无法识别「充分子集」：存在冗余证据与联合必要证据时，per-decision memory sufficiency 是独立问题（摘要）。
  2. JointCoreBench 含 9 个交互族、6 个工作流域、精确 sufficient-set oracle；JointCore 以相关性代价排序做 group-deletion（先测块后测单条），在 6,912 个精确条件上恢复最小代价充分集（摘要，预印本数据，未复现）。
- 关闭条件：oracle 为人工构造，真实会话记忆上的近似充分性判定缺证据；真实场景扩展实验发布后可关。

## E3 · 查询条件化的记忆编译：把检索命中转成可回答证据（MemCompile）

- 获取日期：2026-10-19
- 来源 URL：<https://arxiv.org/abs/2610.23313>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖长期会话记忆的寻址与证据呈现解耦；不覆盖跨用户共享记忆。
- 证据等级：A
- 可提炼要点：
  1. 现有系统常把检索或扩展后的单元直接交给 reader，使记忆寻址与证据呈现耦合，最终上下文冗余或不完整（摘要）。
  2. MemCompile 用 Address Plane（紧凑 source-linked descriptors + 容量感知 Cells）定位支持材料，再用归一化边界把异构检索命中规约为稳定 Source 表示（摘要）。
- 关闭条件：与既有记忆框架的端到端指标差异未在摘要给出；全文核对后可关。

## E4 · Agent 轨迹步级标注工作台（Annotrace）

- 获取日期：2026-10-19
- 来源 URL：<https://arxiv.org/abs/2610.23284>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖 agent 失败研究中的 trace 结构化标注工具链；不覆盖自动标注质量的定论。
- 证据等级：A
- 可提炼要点：
  1. 现状断层：可观测平台记录 trace 但无结构化标注，标注工具处理文本但不理解 step / delegation / tool call，最小可标注执行单元不明（摘要）。
  2. Annotrace 读 6 种 trace 格式（含 OpenTelemetry GenAI、LangSmith、Langfuse），把 run 转为有序嵌套步骤列表；标注者自写 codebook，由前沿模型基于样本 trace 先给起始集合再回答同样问题（摘要）。
- 关闭条件：步级标注与人工一致性（IAA）数字未在摘要给出；工具开链与评估实验全文核对后可关。

## 台账登记（未过开箱门槛或判重跳过）

- AgentOnto（<https://arxiv.org/abs/2610.23317>）：本体驱动的企业数据分析 agent，与既有箱层次重叠且本轮未取原件，仅登记标题与链接，等积累。
- OfficeTown（<https://arxiv.org/abs/2610.23194>）：生成式组织模拟，与既有箱主题距离远，单来源不建块。
