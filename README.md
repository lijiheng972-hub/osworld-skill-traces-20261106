# OSWorld 文字参考与视觉技能轨迹

[打开材料下载页](https://github.com/lijiheng972-hub/osworld-skill-traces-20261106/releases/tag/traces-2026-11-06)

本仓库公开保存 OSWorld 技能实验的轨迹材料。材料跨多个模型、实验批次和环境版本，共1864条任务运行记录，包含475条满分、1337条零分、19条部分得分和33条未评分记录。条目数包含重复运行与试跑，不能视为1864个独立任务。

## 下载内容

| 文件 | 内容 | 大小 |
|---|---|---:|
| `01_trace_reader.zip` | 对话、动作、日志、原评分、索引及RRSI中间分析 | 约88 MiB |
| `02_skill_library.zip` | 本地和服务器现存技能参考库快照 | 约127 MiB |
| `FULL_local.zip.part01` 至 `part03` | 早期Qwen3-VL-8B的完整轨迹，包含现存截图和录像 | 合并后约4.29 GB |
| `FULL_server.zip.part01` 至 `part09` | 服务器图文对照、后续修复及分析材料，包含现存截图和录像 | 合并后约16.96 GB |
| `all_trials.csv` | 每条任务运行的实验、条件、原评分与完整性清单 | 约780 KiB |
| `experiment_summary.csv` | 按实验和参考条件汇总 | 约2 KiB |

文字阅读包可独立使用。完整截图和录像位于FULL附件中。GitHub页面自动生成的Source code压缩包包含目录说明和清单，轨迹文件请在Release的Assets中下载。

## 合并完整包

下载同一个FULL压缩包的全部分片到同一文件夹，再合并后解压。每片均小于2 GiB。

macOS或Linux可以在下载文件夹运行以下命令。

```bash
cat FULL_local.zip.part* > FULL_local.zip
cat FULL_server.zip.part* > FULL_server.zip
```

也提供 `merge_archives.command`，检查分片并核对合并文件SHA256。Windows下载 `merge_archives.cmd` 和 `merge_archives.ps1` 到分片文件夹，运行CMD文件即可合并和校验。合并工具会检查两份FULL压缩包，因此使用工具时需备齐12个分片。

合并后分别解压两个FULL包，避免它们各自的INDEX同名文件覆盖。每个文件的校验值见Release中的 `SHA256SUMS.txt`。

## 清单与评分口径

- `text_reference` 表示文字化技能参考，执行者同时看到实时屏幕。
- `visual_skill` 表示带参考图的技能条件。
- `supplementary_analysis_or_repair` 为后续修复和分析记录，按各自manifest解释条件。
- `unclassified_smoke` 为少量早期试跑，单独保留。

原分数等于1标为pass，等于0为fail，介于两者之间为partial，缺少或异常评分为unscored。图片和文字组的轨迹均包含成功与失败。

后续A/B/C修复中，A为原MMSkills，B为A加修复文字，C为B加直接提供给执行者的参考图，因此B不能等同于纯文字参考条件。

## 原始材料局限

旧实验中存在环境快照、取证送达和记录完整性问题，按批次审查。清单标出缺少步骤、评分、对话及截图的情况。部分对话只保存图像占位符，未保存的原始请求图像无法无损恢复。技能库快照是整理时版本，不能自动视为每次历史运行使用的精确版本。

固定时刻重放的人工动作评分和完整任务的OSWorld评分分别存放。RRSI中间报告、摘要和人工审查一并保留，其中部分摘要未正常完成，部分原因判断已经被截图核查纠正。

更详细说明见 [DATA_GUIDE.md](DATA_GUIDE.md)。材料包含历史失败和不完整记录，汇总数量不构成方法效果结论。
