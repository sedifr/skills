# skills (自建)

这个仓库用于存放自建 Skill, 通过 Skills CLI (`npx skills`) 安装到支持 Skills 的 Agent/客户端中使用。

## 当前技能

- `storyboard-dialog-skill-audit/` (`storyboard-dialog-skill-audit`)
  - 目标: 把“分镜协作对话”转成结构化能力复盘
  - 产出: 已体现技能、待加强技能、下一轮可执行动作
  - 方法: 仅基于当前会话证据, 避免空泛夸奖和臆测

## 适用场景

当用户提到以下意图时使用:

- "我在这段分镜对话里做了什么技能/能力?"
- "帮我复盘分镜协作能力"
- "把当前对话能力沉淀为技能清单"
- "使用 storyboard-dialog-skill-audit"

不适用场景:

- 用户想要的是“系统工具能力列表”, 而非“用户自身对话能力复盘”
- 用户请求直接生成分镜图/镜头表, 不是复盘协作能力

## 复盘维度与判定

默认优先按以下维度提炼:

- 需求澄清
- 目标对齐
- 镜头语言意识
- 节奏控制
- 审片标准
- 协作反馈质量

成熟度分层:

- 已稳定: 多次出现, 且表达清晰、可复用
- 已出现但不稳定: 有表现, 但偶发或不成体系
- 尚未体现: 当前会话缺少直接证据

## 输出格式（建议）

每次复盘建议保持以下三段结构:

1. 已体现技能
2. 待加强技能
3. 下一轮可执行动作（最多 3 条）

每个技能点都应包含:

- 一句话定义
- 对话证据（原话或关键行为）
- 判断理由（为什么归到该成熟度）

## 快速安装

安装单个技能到全局 (推荐):

```bash
npx skills add https://github.com/sedifr/skills --skill storyboard-dialog-skill-audit -g -y
```

查看已安装技能:

```bash
npx skills list -g
```

说明:

- `-g`: 安装到全局技能目录 (通常为 `~/.agents/skills/`)
- `-y`: 跳过交互确认

## 目录结构

```text
storyboard-dialog-skill-audit/
  SKILL.md
  agents/
    openai.yaml
```

字段说明:

- `SKILL.md`: 技能主说明, 含触发描述与执行流程
- `agents/openai.yaml`: UI 展示元信息 (`display_name` / `short_description` / `default_prompt`)

## 维护建议

- 每次优化复盘口径后, 同步更新 `SKILL.md` 与本 README
- 若新增维度或评分方法, 优先在 `SKILL.md` 里定义“证据规则”
- 提交前确保技能结构可通过本地校验脚本

## 发布说明

只要仓库可访问且用户通过 `npx skills add ...` 安装, 即可被 Skills CLI 生态使用; 通常不需要额外手工上传网站。

## 许可证

MIT License (见 `LICENSE`).
