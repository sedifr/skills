# skills (自建)

这个仓库用于存放自建 Skill, 通过 Skills CLI (`npx skills`) 安装到支持 Skills 的 Agent/客户端中使用。

## 当前技能

- `storyboard-director/` (`storyboard-director`)
  - 目标: 把剧本稳定转成可执行分镜流程
  - 流程: 文字分镜冻结 -> 参考图冻结 -> 分镜图分批生成与审片 -> 回填/嵌图 -> 按需导出
  - 特点: one-question-per-turn、先文字后出图、强制一致性检查与成本控制

## 适用场景

当用户提到以下意图时使用:

- "我要做分镜"
- "帮我拆分镜"
- "把这段剧本做成分镜"
- "分镜导演"

## 关键规则

- 每回合只问一个关键问题。
- 文字分镜未通过前, 不开始生图。
- 参考图未通过前, 不开始分镜帧图。
- 每次生图前必须先确认生成范围（例如 `01-03` / `05,07` / `全部` / `仅新增`）。
- 每次生图前固定 6 轮复盘。
- 每次出图后固定做现实一致性检查并记录问题闭环。

## 快速安装

安装到全局技能目录:

```bash
npx skills add https://github.com/sedifr/skills --skill storyboard-director -g -y
```

查看已安装技能:

```bash
npx skills list -g
```

说明:

- `-g`: 安装到全局技能目录 (通常为 `~/.agents/skills/`)
- `-y`: 跳过交互确认

## 技能结构

```text
storyboard-director/
  SKILL.md
  references/
    fields.md
    state-machine.json
```

文件说明:

- `SKILL.md`: 技能触发描述、核心规则、流程总览
- `references/fields.md`: 文字分镜表字段清单（默认列 + 可选列）
- `references/state-machine.json`: 逐步状态机（提问节点、自动步骤、冻结审查点）

## 发布说明

只要仓库可访问且用户通过 `npx skills add ...` 安装, 即可在 Skills CLI 生态中使用; 通常不需要额外手工上传网站。

## 许可证

MIT License (见 `LICENSE`).
