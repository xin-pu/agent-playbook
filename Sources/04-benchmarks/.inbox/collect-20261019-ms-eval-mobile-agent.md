# 投递：MCP 编排评测与移动 agent 注入基准（2026-10-19 daily）

> 本文件为未入箱投递，合箱由人工主流程处理。候选去向：`04-benchmarks` 域 agent-benchmarks 箱。

## E1 · MS-Eval：MCP 密集场景下子 agent 委派与编排的统一评测套件

- 获取日期：2026-10-19
- 来源 URL：<https://arxiv.org/abs/2610.22869>
- 本地原件：`Sources/04-benchmarks/.inbox/originals/arxiv-2610.22869-ms-eval-mcp-orchestration.pdf`
- 适用范围：preprint，未经同行评议；覆盖主 agent 委派 + 子 agent 并行执行（MAD-SAE）范式下的委派与编排质量度量；不覆盖单 agent 顺序工具调用的既有基准对比结论。
- 证据等级：A
- 可提炼要点：
  1. 动机：复杂多子任务问题用顺序工具调用解决效率低且上下文膨胀严重；MAD-SAE 范式把子任务委派给专职子 agent 在隔离上下文中并行执行，但委派与编排质量此前无量化手段（摘要）。
  2. 交付物是统一评测套件而非单一榜单：MCP 密集型基准 + 受控执行 harness + 委派/编排专用指标 + 综合 MSQ 指数（摘要）。
  3. 作者来自浙江大学 / 西湖大学工程研究生院（PDF 首页），与 03-mcp 域的协议生态主题互为补充。
- 关闭条件：MSQ 指数的定义与可复核性需全文核对；评测套件开源仓库地址公开并可运行后可关。

## E2 · MobileInject：跨模态一致性注入下的移动 agent reasoning-to-action 安全评测

- 获取日期：2026-10-19
- 来源 URL：<https://arxiv.org/abs/2610.23307>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖 MLLM 移动 agent 的间接多模态提示注入攻击面（跨应用内容携带恶意目标）；不覆盖桌面/web 注入的既有结论迁移。
- 证据等级：A
- 可提炼要点：
  1. 定位差异：prompt injection 在桌面与 web 环境已有研究，移动生态中跨模态属性（reasoning 与 action 的一致性被劫持）此前理解不足（摘要）。
  2. MobileInject 自称首个针对移动 agent、以跨模态一致性注入为攻击原语的评测基准，考察感知-推理-行动链的安全落点（摘要）。
- 关闭条件：攻击成功率等定量结论未在本轮抓取范围内；全文核对基准构成与模型覆盖清单后可关。

## 台账登记（未过开箱门槛或判重跳过）

- MobileJailBench（<https://arxiv.org/abs/2610.23303>）：移动 agent 越狱基准，与 E2 同域且本轮未取原件，登记待积累，可与 E2 合并评估是否成箱。
- KiranaBench（<https://arxiv.org/abs/2610.22980>）、FLARE（<https://arxiv.org/abs/2610.23251>）：单来源、层次与既有箱重叠度待判，暂不建块。
