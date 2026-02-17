# skills (自建)

这个仓库用于存放自建 Skill, 以便通过 Skills CLI (`npx skills`) 安装到多种支持 Skills 的 Agent/客户端中使用。

## 包含的技能

- `storyboard-dialog-skill-audit/` (`storyboard-dialog-skill-audit`)
  - 用途: 复盘分镜协作对话, 识别用户已体现的能力动作并沉淀为技能画像
  - 特点: 基于证据提炼、能力分层评估(稳定/不稳定/未体现)、输出可执行改进动作

## 环境要求

- Node.js (用于运行 `npx skills`)
- Git (用于从 GitHub 拉取)

## 安装

安装单个技能到全局 (推荐):

```bash
npx skills add https://github.com/sedifr/skills --skill storyboard-dialog-skill-audit -g -y
```

查看已安装的全局技能:

```bash
npx skills list -g
```

提示:

- `-g` 表示安装到全局技能目录 (通常是 `~/.agents/skills/`), 多个 Agent 会共享这份安装。
- `-y` 表示跳过确认提示。

## 使用方式 (触发示例)

不同平台的 UI/交互方式略有差异, 但在对话中直接表达意图通常就能触发。

建议的触发说法:

- "我在这段分镜对话里做了什么技能?"
- "帮我复盘分镜协作能力"
- "把当前对话能力沉淀为技能清单"
- "使用 storyboard-dialog-skill-audit"

## 技能目录结构约定

每个技能是一个独立目录, 以 `SKILL.md` 作为入口文件:

```text
<skill-name>/
  SKILL.md
  agents/
    openai.yaml
  references/   (可选)
    ...
  scripts/      (可选)
  assets/       (可选)
```

其中:

- `SKILL.md` 必须存在, 且包含 frontmatter (`name` / `description`)。
- `references/` 放长文档/规范/字段表/状态机等, 由 Agent 按需读取。

## 发布到 skills.sh (说明)

skills.sh 本质是对 Skills CLI 生态的索引与展示。一般不需要手动"上传"到网站:

- 只要仓库在 GitHub 上可访问, 并且用户通过 `npx skills add ...` 安装
- 安装的匿名统计会逐步让技能在 skills.sh 上可被发现

## 许可证

MIT License (见 `LICENSE`).
