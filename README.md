# Claude Code Research Skills Workspace

这是一个面向学术研究、论文阅读、文献调研和技术排错记录的 Claude Code 工作区。

本项目的核心目标是：把常见的研究工作流沉淀成可复用的 Claude Code Skills 和 Slash Commands，包括领域调研、论文翻译、论文精读、arXiv 追踪，以及将 AI 交互过程整理成技术笔记。

---

## 1. 项目功能概览

当前项目包含以下 Skills：

| Skill                  | 短命令         | 主要用途                          |
| ---------------------- | ----------- | ----------------------------- |
| `field-survey`         | `/survey`   | 领域调研、文献综述、代表论文、趋势和开放问题        |
| `academic-translation` | `/trans`    | 严格学术翻译，逐段翻译论文并维护术语一致性         |
| `paper-deep-reading`   | `/deepread` | 单篇论文深度阅读，分析方法、假设、实验、局限和研究启发   |
| `arxiv-watch`          | `/watch`    | 追踪某个领域最近 arXiv 新论文，并筛选值得阅读的论文 |
| `session-note`         | `/note`     | 将 AI 交互、排错、环境配置过程整理成可复用笔记     |

此外，本项目还使用 `paper-search` 工具进行论文检索、元数据查询、PDF 下载和论文阅读辅助。

---

## 2. 项目目录结构

推荐目录结构如下：

```text
.
├── README.md
├── CLAUDE.md
├── papers/
│   └── <field-slug>/
│       └── <paper-file>.pdf
├── note/
│   ├── fields/
│   │   └── <field-slug>/
│   │       ├── survey.md
│   │       ├── paper-table.md
│   │       ├── reading-roadmap.md
│   │       └── open-problems.md
│   ├── papers/
│   │   └── <paper-slug>/
│   │       ├── metadata.md
│   │       ├── translation.md
│   │       ├── terminology.md
│   │       ├── translation-notes.md
│   │       ├── deep-reading.md
│   │       ├── qa.md
│   │       ├── experiment-analysis.md
│   │       └── research-ideas.md
│   └── sessions/
│       └── <session-slug>.md
├── watch/
│   └── arxiv/
│       └── <field-slug>/
│           └── <date>.md
├── prompts/
├── templates/
└── .claude/
    ├── skills/
    │   ├── field-survey/
    │   │   └── SKILL.md
    │   ├── academic-translation/
    │   │   └── SKILL.md
    │   ├── paper-deep-reading/
    │   │   └── SKILL.md
    │   ├── arxiv-watch/
    │   │   └── SKILL.md
    │   └── session-note/
    │       └── SKILL.md
    ├── commands/
    │   ├── survey.md
    │   ├── trans.md
    │   ├── deepread.md
    │   ├── watch.md
    │   └── note.md
    ├── settings.local.json
    └── tools/
```

---

## 3. 目录说明

### `papers/`

用于保存论文 PDF 原文。

推荐格式：

```text
./papers/<field-slug>/<paper-file>.pdf
```

示例：

```text
./papers/action-chunking/act.pdf
./papers/vla/openvla.pdf
./papers/diffusion-policy/diffusion-policy.pdf
```

---

### `note/fields/`

用于保存领域级调研结果。

推荐格式：

```text
./note/fields/<field-slug>/
```

常见文件：

```text
survey.md
paper-table.md
reading-roadmap.md
open-problems.md
```

示例：

```text
./note/fields/vla/survey.md
./note/fields/action-chunking/paper-table.md
```

---

### `note/papers/`

用于保存单篇论文相关的所有笔记。

推荐格式：

```text
./note/papers/<paper-slug>/
```

常见文件：

```text
metadata.md
translation.md
terminology.md
translation-notes.md
deep-reading.md
qa.md
experiment-analysis.md
research-ideas.md
```

示例：

```text
./note/papers/act/translation.md
./note/papers/act/deep-reading.md
./note/papers/openvla/terminology.md
```

---

### `note/sessions/`

用于保存技术排错、环境配置、工具安装、AI 协作过程的整理笔记。

推荐格式：

```text
./note/sessions/<session-slug>.md
```

示例：

```text
./note/sessions/claude-code-deepseek-vscode-setup.md
./note/sessions/paper-search-mcp-installation.md
./note/sessions/node-nvm-vscode-terminal-fix.md
```

---

### `watch/arxiv/`

用于保存 arXiv 追踪记录。

推荐格式：

```text
./watch/arxiv/<field-slug>/<date>.md
```

示例：

```text
./watch/arxiv/vla/2026-05-29.md
./watch/arxiv/action-chunking/2026-05-29.md
```

---

### `prompts/`

用于保存常用提示词模板。

例如：

```text
prompts/survey-prompts.md
prompts/translation-prompts.md
prompts/deepread-prompts.md
prompts/watch-prompts.md
```

---

### `templates/`

用于保存输出模板。

例如：

```text
templates/field-survey.md
templates/translation-batch.md
templates/deep-reading.md
templates/session-note.md
```

---

### `.claude/skills/`

用于保存 Claude Code Skills。

每个 Skill 是一个独立目录，核心文件是：

```text
.claude/skills/<skill-name>/SKILL.md
```

---

### `.claude/commands/`

用于保存 Slash Commands。

每个 `.md` 文件对应一个短命令，例如：

```text
.claude/commands/survey.md     -> /survey
.claude/commands/trans.md      -> /trans
.claude/commands/deepread.md   -> /deepread
.claude/commands/watch.md      -> /watch
.claude/commands/note.md       -> /note
```

---

### `CLAUDE.md`

项目级统一规则文件。

它负责定义：

* 项目文件结构
* 各 Skill 的默认输出路径
* 文件创建规则
* append / overwrite 规则
* slug 命名规则
* final response 规则
* 安全规则

原则：

```text
CLAUDE.md 负责全局路径和项目规范。
SKILL.md 负责具体任务流程。
commands/*.md 负责短命令入口。
```

---

## 4. Skills 说明

## 4.1 `field-survey`

用途：领域调研、文献综述、研究路线梳理。

适合场景：

* 调研一个新方向
* 找经典论文和近期代表工作
* 梳理核心概念、benchmark、dataset
* 总结趋势和开放问题
* 建立阅读路线

短命令：

```text
/survey
```

示例：

```text
/survey VLA 领域的核心概念、经典工作、近期代表论文、benchmark、趋势和开放问题。
```

```text
/survey action chunking 在机器人模仿学习中的作用。请筛选 10 篇以内代表论文，并给出阅读顺序。
```

默认输出位置由 `CLAUDE.md` 决定，通常为：

```text
./note/fields/<field-slug>/
```

---

## 4.2 `academic-translation`

用途：严格学术翻译论文。

适合场景：

* 逐段翻译 Abstract / Introduction / Method / Experiments
* 保持术语一致
* 保留公式、引用、图表编号
* 翻译后续章节并追加到同一文档

短命令：

```text
/trans
```

示例：

```text
/trans 请逐段翻译 ./papers/action-chunking/act.pdf 的 Abstract 和 Introduction，保持严格学术表达，并建立术语表。
```

```text
/trans 继续翻译 ./papers/action-chunking/act.pdf 的 Method 部分，复用已有术语表，并追加到已有翻译后面。
```

默认输出位置由 `CLAUDE.md` 决定，通常为：

```text
./note/papers/<paper-slug>/translation.md
./note/papers/<paper-slug>/terminology.md
```

同一篇论文的不同章节应追加到同一个 `translation.md`，不要默认创建多个分散的翻译文件。

---

## 4.3 `paper-deep-reading`

用途：深度理解和分析单篇论文。

适合场景：

* 分析论文方法机制
* 分析核心假设
* 判断实验是否支撑结论
* 总结局限和失败场景
* 生成 research ideas
* 回答论文相关深度问题
* 比较两篇或多篇论文

短命令：

```text
/deepread
```

示例：

```text
/deepread 请基于 ./papers/action-chunking/act.pdf 和已有翻译笔记，分析 ACT 为什么 action chunking 有效。
```

```text
/deepread 请重点分析这篇论文的实验设计是否足以支撑作者结论，并指出缺失的实验。
```

默认输出位置由 `CLAUDE.md` 决定，通常为：

```text
./note/papers/<paper-slug>/deep-reading.md
./note/papers/<paper-slug>/qa.md
./note/papers/<paper-slug>/experiment-analysis.md
./note/papers/<paper-slug>/research-ideas.md
```

文件按需创建，不会在一次 deep reading 中默认生成所有文件。

---

## 4.4 `arxiv-watch`

用途：追踪某个领域近期 arXiv 新论文。

适合场景：

* 检索最近几天或最近一周的新论文
* 生成 arXiv watch note
* 筛选值得翻译或精读的论文
* 对比本次结果和历史追踪记录
* 定期跟踪研究方向

短命令：

```text
/watch
```

示例：

```text
/watch VLA 最近一周的新论文。最多筛选 10 篇，不下载全部 PDF，只标出最值得精读的论文。
```

```text
/watch action chunking 最近 7 天的新论文，并判断哪些值得加入阅读列表。
```

默认输出位置由 `CLAUDE.md` 决定，通常为：

```text
./watch/arxiv/<field-slug>/<date>.md
```

注意：`arxiv-watch` 本身只定义如何执行一次追踪任务，不会自动定时运行。定期执行需要额外配置 cron、scheduled task、loop 或其他自动化触发方式。

---

## 4.5 `session-note`

用途：将 AI 交互过程整理成可复用技术笔记。

适合场景：

* bug 排查记录
* 环境配置记录
* GitHub 项目安装过程
* 工具安装过程
* 模型接入过程
* Claude Code 配置过程
* 多轮 AI 协作后的总结沉淀

短命令：

```text
/note
```

示例：

```text
/note 请把刚才解决 VS Code Claude Code terminal mode 找不到 node 的过程整理成排错笔记。
```

```text
/note 请把这次安装 paper-search-mcp 并配置 skill 的过程整理成可复用配置文档。
```

默认输出位置由 `CLAUDE.md` 决定，通常为：

```text
./note/sessions/<session-slug>.md
```

`session-note` 不应该记录完整聊天流水账，而是提炼：

* 背景 / 目标
* 问题现象
* 报错信息
* 环境信息
* 排查过程
* 根因
* 最终方案
* 验证方式
* 可复用命令
* 注意事项
* 后续任务

---

## 5. 推荐工作流

### 5.1 进入一个新研究方向

```text
/survey VLA 领域的核心概念、经典工作、近期代表论文、benchmark、趋势和开放问题。
```

输出领域综述后，选择值得读的论文。

---

### 5.2 翻译一篇核心论文

```text
/trans 请逐段翻译 ./papers/vla/openvla.pdf 的 Abstract 和 Introduction，保留专业术语并建立术语表。
```

后续继续翻译：

```text
/trans 继续翻译 ./papers/vla/openvla.pdf 的 Method 部分，复用已有术语表，并追加到已有 translation.md。
```

---

### 5.3 深读一篇论文

```text
/deepread 请基于 ./papers/vla/openvla.pdf 和已有翻译笔记，分析这篇论文的方法机制、核心假设、实验支撑和局限。
```

---

### 5.4 追踪最新论文

```text
/watch VLA 最近一周的新论文，筛选最值得翻译或精读的 5 篇。
```

---

### 5.5 记录一次排错或配置过程

```text
/note 请把刚才配置 Claude Code + DeepSeek + VS Code terminal mode 的过程整理成 troubleshooting note。
```

---

## 6. 文件创建原则

本项目采用“按需创建”原则。

不会因为某个论文目录存在，就自动生成所有文件。

例如：

### 翻译任务通常只会创建或更新：

```text
translation.md
terminology.md
translation-notes.md
```

### 深读任务通常只会创建或更新：

```text
deep-reading.md
qa.md
experiment-analysis.md
research-ideas.md
```

### 领域调研通常只会创建或更新：

```text
survey.md
paper-table.md
reading-roadmap.md
open-problems.md
```

具体创建哪些文件由当前任务决定。

---

## 7. Append 规则

默认不要覆盖已有研究笔记。

以下文件通常使用追加模式：

```text
translation.md
deep-reading.md
qa.md
research-ideas.md
experiment-analysis.md
```

例如，同一篇论文的多个翻译批次都应追加到：

```text
./note/papers/<paper-slug>/translation.md
```

每次追加时使用清晰分隔符，例如：

```markdown
---

# Translation Batch: <section-or-range>

Source: <paper path, section name, page range, or pasted text>

---
```

深读内容也类似追加到：

```text
./note/papers/<paper-slug>/deep-reading.md
```

---

## 8. Slug 命名规则

使用 lowercase kebab-case。

示例：

```text
Vision-Language-Action -> vla
Action Chunking -> action-chunking
Action Chunking Transformer -> act
Diffusion Policy -> diffusion-policy
OpenVLA -> openvla
RAG Evaluation -> rag-evaluation
```

论文 slug 优先使用简短、稳定、易识别的名称。

例如：

```text
Action Chunking Transformer -> act
OpenVLA: An Open Vision-Language-Action Model -> openvla
Diffusion Policy: Visuomotor Policy Learning via Action Diffusion -> diffusion-policy
```

---

## 9. 注意事项

### 9.1 不要只凭记忆做文献调研

涉及论文检索、最新论文、SOTA、arXiv 追踪时，应优先使用 `paper-search` 或可用论文检索工具。

---

### 9.2 不要随意声称 SOTA

只有在有明确 benchmark、实验结果或来源支持时，才能声称某篇论文是 SOTA。

更推荐使用保守表述：

```text
从当前检索结果看，它可能是近期代表工作。
是否为严格 SOTA 仍需进一步验证 benchmark 结果。
```

---

### 9.3 不要把翻译变成深度分析

`academic-translation` 的主要任务是忠实、准确、逐段翻译。

深度分析、批判性评价、研究想法生成应交给 `paper-deep-reading`。

---

### 9.4 不要把 session-note 写成聊天记录

`session-note` 只提炼可复用知识，不记录完整对话。

重点是：

```text
问题是什么
为什么发生
怎么解决
怎么验证
下次如何快速处理
```

---

### 9.5 敏感信息要脱敏

不要保存：

```text
API Key
access token
password
SSH private key
.env 内容
个人敏感路径或私密服务地址
```

应使用占位符：

```text
<API_KEY>
<TOKEN>
<PASSWORD>
<PRIVATE_PATH>
```

---

### 9.6 谨慎修改配置文件

除非明确需要，不要让 Claude Code 自动修改：

```text
.env
.env.*
.vscode/
.git/
.claude/settings*
```

---

## 10. 权限建议

建议在 `.claude/settings.local.json` 中允许 Claude Code 读写项目的研究笔记目录，例如：

```json
{
  "permissions": {
    "allow": [
      "Read(/note/**)",
      "Write(/note/**/*.md)",
      "Edit(/note/**/*.md)",
      "Read(/papers/**)",
      "Bash(mkdir -p note)",
      "Bash(mkdir -p note/fields)",
      "Bash(mkdir -p note/papers)",
      "Bash(mkdir -p note/sessions)",
      "Bash(mkdir -p watch)",
      "Bash(mkdir -p watch/arxiv)"
    ]
  }
}
```

同时建议继续限制敏感文件：

```json
{
  "permissions": {
    "deny": [
      "Read(.env)",
      "Read(**/.env)",
      "Read(**/.env.*)",
      "Write(.env)",
      "Write(**/.env)",
      "Write(**/.env.*)",
      "Edit(.env)",
      "Edit(**/.env)",
      "Edit(**/.env.*)"
    ]
  }
}
```

具体权限应根据实际项目风险调整。

---

## 11. VS Code 使用说明

本项目可以在 Claude Code CLI 或 VS Code Claude Code 插件中使用。

如果使用第三方 Anthropic-compatible API，例如 DeepSeek 或其他兼容接口，图形化 UI 可能存在兼容性差异。

更稳定的方式通常是启用 terminal mode：

```json
{
  "claudeCode.useTerminal": true
}
```

如果 terminal mode 找不到 Node.js，请确认右侧 terminal 环境能运行：

```bash
which node
node -v
which claude
claude
```

如果普通终端能找到 Node，但 VS Code Claude Code terminal mode 找不到，通常是因为 nvm 没有在该 shell 中加载。可以将 nvm 初始化放到更早加载的 shell 配置中，例如 `~/.zshenv`。

---

## 12. 测试命令

### 测试 Skill 是否可用

```text
/survey 请不要开始调研，只确认 field-survey skill 可用。
```

```text
/trans 请不要翻译，只确认 academic-translation skill 可用。
```

```text
/deepread 请不要分析论文，只确认 paper-deep-reading skill 可用。
```

```text
/watch 请不要检索论文，只确认 arxiv-watch skill 可用。
```

```text
/note 请不要整理笔记，只确认 session-note skill 可用。
```

---

### 测试一个小任务

```text
/survey action chunking 在机器人模仿学习中的作用。只做小型测试，最多筛选 5 篇论文，不下载 PDF。
```

```text
/trans 请严格学术翻译下面这段论文内容，并说明术语处理方式：

<粘贴论文段落>
```

```text
/note 请把刚才这个测试过程整理成一篇简短 session note。
```

---

## 13. 维护原则

本项目推荐遵循以下维护原则：

1. `CLAUDE.md` 只放全局共用规则。
2. `SKILL.md` 只放某个 skill 独有的任务流程。
3. `commands/*.md` 只作为短命令入口，不重复复杂规则。
4. 路径规则统一放在 `CLAUDE.md`。
5. 常用提示词放在 `prompts/`。
6. 输出格式模板放在 `templates/`。
7. 不要在多个文件里重复定义同一条规则，避免冲突和 token 浪费。

---

## 14. 快速参考

| 任务       | 命令                     |
| -------- | ---------------------- |
| 领域调研     | `/survey <研究领域>`       |
| 论文翻译     | `/trans <论文或章节>`       |
| 论文深读     | `/deepread <论文或问题>`    |
| arXiv 追踪 | `/watch <研究领域和时间范围>`   |
| 过程整理     | `/note <需要整理的交互或排错过程>` |

推荐完整流程：

```text
/survey 先调研领域
/trans 翻译核心论文
/deepread 深度理解论文
/watch 持续追踪新论文
/note 沉淀排错和配置过程
```
