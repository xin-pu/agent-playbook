# 投递：评测基准——长程交互与「任务完成之外」的连续性度量（2026-10-25 weekly）

建议主箱：`04-benchmarks/agent-benchmarks`（与 τ 家族、GUI/视频基准同族）。

## E1 · UserArena：以真实电商长程轨迹校准「交互式用户模拟」并对接线上 A/B 验证

- 获取日期：2026-10-25
- 来源 URL：https://arxiv.org/abs/2610.30932
- 本地原件：—
- 适用范围：preprint，未经同行评议；仅摘要可得；覆盖长程导购 agent 的用户模拟器评测（真实轨迹规模、五层评分、离线-线上对照）；不覆盖推荐算法本身的排序质量。
- 证据等级：A
- 可提炼要点：
  1. 资源口径：64,729 条会话轨迹、11,010 用户、566,102 商品、13 种动作类型；既有资源缺长程细粒度真实用户轨迹、也缺轨迹级评测与线上对照。
  2. 方法特点：把交互式环境与「对照受控生产 A/B 结果的离线验证」绑定，评测分五层（输出有效性、局部决策、序列行为、persona…，摘要截断处待核）。
  3. 提炼价值：为「用户模拟可信度」提供可复用的校准协议——模拟器的行为保真度用真实轨迹+线上实验双向锚定。
- 关闭条件：未取全文，五层指标定义与 A/B 吻合度数字未核；数据可得性（是否公开轨迹）亦需核对后方可进提炼清单。

## E2 · ProductWebBench：前端编码 agent 的「网站连续性」第二义务——28.2% 通过全部需求检查的 run 仍破坏其他功能

- 获取日期：2026-10-25
- 来源 URL：https://arxiv.org/abs/2610.31118
- 本地原件：—
- 适用范围：preprint，未经同行评议；仅摘要可得；覆盖在真实（活体）前端仓库上做变更任务时的回归/连续性度量（320 Change + 80 Build 任务，13 模型 8,737 runs）；不覆盖非前端域的代码 agent。
- 证据等级：A
- 可提炼要点：
  1. 概念：把「其余站点继续可用」命名为 website continuity，作为 task completion 之外的第二义务单独计分。
  2. 协议：每个任务冻结仓库快照+分阶段需求+浏览器证据+确定性检查，参考解通过全部检查、 plausible-wrong 解必须失败才入库；模拟用户按阶段揭示需求，早期通过的检查在后续全程保持「armed」。
  3. 定量口径（预印本，未复现）：通过全部「_requested work_」检查的 Change runs 中 28.2% 仍栽在连续性检查上——任务完成分数系统性掩盖回归破坏。
  4. 关系：与 00-rl HarnessAdapt-RL（2610.28069，10-20，本轮未入块，登记在 04 侧作线索）同向——agent 评测正从「单轮做对」转向「与持续演化的环境/代码库共存」。
- 关闭条件：未取全文，13 模型明细与两类任务（Change/Build）差异未核；需补 PDF 后再决定是否与 SWE-bench 家族并表比较。

---

## 台账登记

- HarnessAdapt-RL《Training the Whole Agent, Not Just the Model》（https://arxiv.org/abs/2610.28069）：SWE-bench Verified/多语言/Pro 上 9B 基座相对 GRPO +9.8/+12.6/+6.4pp、与 OpenHands 人设 harness 对比、skill 移除后增益保持等要点见摘要；主题归属 `00-rl` 的 agentic-RL harness 线，因本轮 00-rl 域配额（6 来源）已满，登记于此待下轮或人工并箱时补块。
- 本轮 05-code-oss 无新增可登记：ollama v0.40.11-rc0、npm sdk 1.32.2、registry 1.8.4 已由 10-23/10-24 daily 覆盖；vllm（v0.32.0）、transformers（v5.20.2）、pytorch（2.14.1）、openai-agents（v0.24.0）、llama-index（0.14.25）窗内无新 release（GitHub API releases 复查）。
