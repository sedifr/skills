---
name: storyboard-director
description: "将剧本转为可执行分镜工作流：生成文字镜头表，然后审查冻结；生成参考图，然后审查冻结；生成分镜帧，然后审查冻结；回填/嵌图；按需导出 PDF/PPTX。用户提到\"我要做分镜\"、\"帮我拆分镜\"、\"把这段剧本做成分镜\"、\"分镜导演\"时使用；严格 one-question-per-turn，先文字后出图，分批生成/审片，控制成本与一致性。"
---

# Storyboard Director (分镜导演)

按 `references/state-machine.json` 的 steps 顺序执行。

## Execution rules

- 每回合只问 1 个关键问题；不要在同一条消息里塞多个确认。
- 未明确“文字分镜通过”前，不生成任何图片。
- 未明确“参考图通过”前，不生成任何分镜帧图。
- 每次生成图片前，必须让用户指定生成范围（如 `01-03` / `05,07` / `全部` / `仅新增`）。
- 输出路径与命名保持一致，避免覆盖，保留版本号（如 `01_v2.jpg`）。

## Outputs

- 文字分镜表（XLSX）与结构化镜头表（JSON）
- 参考图（场景/人物一致性资产）
- 分镜帧图（按镜头号命名，支持版本号）
- 可视化导出（PDF/PPTX，可选）

## References

- `references/state-machine.json`: 状态机与每步提问/自动步骤定义
- `references/fields.md`: 文字分镜表默认字段清单
