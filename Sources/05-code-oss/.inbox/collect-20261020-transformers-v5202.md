# 投递：transformers v5.20.2 补丁发布（2026-10-20 daily）

> 本文件为未入箱投递，合箱由人工主流程处理。候选去向：`05-code-oss` 域 inference-stack-releases 箱（发布流水追加块）。

## E1 · transformers v5.20.2：修复 generate 内输入类型丢失与 MoE 专家并行 bf16 零梯度

- 获取日期：2026-10-20
- 来源 URL：<https://github.com/huggingface/transformers/releases/tag/v5.20.2>
- 本地原件：—
- 适用范围：官方 release notes（A 级一手）；覆盖 v5.20.1→v5.20.2 增量修复清单；不覆盖下一 minor 的功能预告。
- 证据等级：A
- 可提炼要点：
  1. 发布节奏：10-16 v5.20.1（上轮已登记）后 3 天即出 v5.20.2（2026-10-19T17:45Z），patch 级快节奏持续。
  2. 关键修复一：`prepare_inputs_for_generation` 中部分输入丢失原始类型导致多模态模型 generate 出错（#49731）；另有只报 text 模态的 VLM 补声明输入模态（#49677）（release notes 原文转述）。
  3. 关键修复二：expert parallelism 且 ep_size < fsdp_size 时 bfloat16 下专家梯度为零（#49688）——对 MoE 微调正确性有直接影响，可与 01-dl 域 MoE 训练系统证据对读。
- 关闭条件：release notes 未列全量 commit 影响面；是否影响既有复现流程需人工主流程按正文引用情况判定，无外部待采项。

## 台账登记

- 窗内其余盯守仓库无新 release：pytorch 最新 v2.14.1（09-30）、openai-agents-python v0.24.0（10-15，上轮已覆盖）、llama_index v0.14.25（09-21）、vllm v0.32.0（10-18，上轮投递文件已登记）、ollama v0.40.7-rc0（10-18，上轮已登记），均复查无增量。
- 06-news 域：Anthropic news 窗内无新条目（最新仍为 10-18 public-benefit-fund，上轮已投）；Interconnects 最新 10-17 已登记；机器之心首页 JS 渲染无结构化条目、OpenAI 403 未采；本轮 06-news 不产生投递文件。
