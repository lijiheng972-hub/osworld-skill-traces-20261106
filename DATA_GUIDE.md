# OSWorld 文字参考与视觉技能轨迹材料

整理日期为 2026-11-06。

## 建议阅读顺序

先解压 `01_trace_reader.zip`，查看本文、`INDEX/all_trials.csv` 和 `INDEX/experiment_summary.csv`。按模型、实验、条件、任务和结果筛选后，通过 `relative_path` 定位原始记录。

`FULL_local.zip` 收录本地早期 Qwen3-VL-8B 技能实验，`FULL_server.zip` 收录服务器 Qwen3-VL-Plus 图文对照及后续实验。完整包保留现存逐步截图、录像和文字记录。两个完整包分别解压，避免各自的 INDEX 同名文件被覆盖。阅读包中的联合清单可同时索引两个来源。

## 数据组织

- `text_reference` 是文字化参考证据组，目录常含 VERB。执行者依然看到实时截图。
- `visual_skill` 是技能参考图组，目录常含 IMG 或 mmskills。
- `supplementary_analysis_or_repair` 包含后续修复、固定时刻重放和 RRSI 中间输出。各自的 manifest、trial_plan、completion_summary 或 REVIEW 解释具体条件。
- `unclassified_smoke` 是少量保留的 Kimi 早期试跑，其证据条件不能仅凭名称确认。

后续 A/B/C 修复实验中，A 是原 MMSkills，B 在 A 基础上加修复文字，C 在 B 基础上额外直接给执行者参考图。B 不能直接当作纯文字参考组。

固定时刻重放保存模型回答和人工评分，其结果单位是下一步判断。完整任务轨迹保存原 OSWorld result.txt，其单位是完整执行后的任务得分。两类分开汇总。

## 技能参考库与图像请求记录

`02_skill_library.zip` 保存整理时本地和服务器现存的技能库，用于查找参考图和状态卡。它是当前保存的素材快照，不能自动视为所有历史运行当时的精确版本。

部分旧 conversation.json 对图像仅保存占位符而没有保存实际请求中的图像字节。完整包中的逐步PNG、录像和现存技能库可辅助核查，但未保存的初始输入图、传入裁剪或历史版本无法凭空恢复。因此现存轨迹全部保留，不将其描述成每次模型请求均可字节级重建。

## 文件含义

- `traj.jsonl` 记录操作、模型回答、时间戳、环境反馈与对应截图名。
- `conversation.json` 保存现存对话记录。
- `step_*.png` 是运行截图，需结合动作时序阅读。历史实验通常在动作执行后保存该步截图。
- `recording.mp4` 是现存运行录像。
- `result.txt` 是原评测器给出的最终任务分数。
- `skill_invocations.json`、`skill_usage_summary.json` 等记录技能调用和送达信息。
- `runtime.log` 等保存运行日志。
- `task_instructions.csv` 提供本地现存 Ubuntu 基准任务的原始指令，按任务 ID 对照。

## pass、fail 与原始记录完整性

联合任务表中，原评分等于1标为pass，等于0标为fail，介于0与1之间标为partial。缺失、不可读或异常评分标为unscored。均保留，不能把缺少评分直接算成失败，也不能将partial误计为满分通过。

`trajectory_rows`、`first_step`、`last_step`、`missing_step_numbers`、`missing_referenced_screenshots`、`has_conversation` 与 `has_video` 标明原始记录覆盖情况。部分旧实验只有评分、缺少轨迹，或轨迹从中途开始，这些情况保持原样并在表中标注。一个任务的不同轮次独立保留，因此行数是任务运行记录数，不是独立任务总数。

## 研究背景与使用边界

材料跨越多个模型、步数预算、送达率修复前后和环境版本。按实验目录比较对应条件，不能直接把所有pass与fail混合计算方法效果。早期实验已发现环境快照和证据送达问题，保留这些轨迹供审查，不将其等同于已消除混杂的复现实验。

RRSI 原始 report 与 digests 一并保留。部分成功摘要报告了轮次耗尽错误；部分失败根因曾被人工截图审查纠正。阅读其原始分析时结合对应 REVIEW 和截图核查。

整理过程仅打包现存文件，没有调用模型或重新运行实验。完整包中的 INDEX/files.csv 保存来源和归档内容哈希，INDEX/omitted.csv 列出依赖代码等非轨迹文件，INDEX/redactions.csv 记录自动凭据模式遮盖。压缩包的整体哈希见 SHA256SUMS.txt。


## 本次归档数量

| 来源 | 任务运行记录 | pass | fail | partial | unscored |
|---|---:|---:|---:|---:|---:|
| local | 462 | 104 | 344 | 7 | 7 |
| server | 1402 | 371 | 993 | 12 | 26 |

条目包含试跑、重复轮次、环境重试和后续修复记录。不同模型和版本分开查看。固定时刻重放及RRSI分析另存于analysis材料，不计作上述完整任务条目。
