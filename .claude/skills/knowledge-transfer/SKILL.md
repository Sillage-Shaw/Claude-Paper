---
name: knowledge-transfer
description: "Transfer and distill research content from the Claude-Paper literature vault (D:\\Development\\Claude-Paper) into the main Obsidian knowledge base (D:\\Obsidian). Use this skill whenever the user wants to sync, transfer, migrate, or distill their paper reading notes into their permanent knowledge base. Triggers on: 沉淀文献/论文/知识到知识库, 同步文献库, 迁移论文笔记, knowledge transfer, sync papers to vault, 把研究笔记写进知识库. This is a multi-phase workflow: scan → recommend → create Source notes → distill Knowledge notes → update MOCs. Always follows the target vault's CLAUDE.md and 99-System rules."
---
# Knowledge Transfer Skill

Transfer research content from `D:\Development\Claude-Paper` into `D:\Obsidian`, following the target vault's rules.

## Target Vault Rules

Before operating, read these key files (if not in context):

- `D:\Obsidian\CLAUDE.md`
- `D:\Obsidian\99-System\Documentation\Directory Rules.md`
- `D:\Obsidian\99-System\Documentation\Note Type Rules.md`
- `D:\Obsidian\99-System\Documentation\Naming Rules.md`
- `D:\Obsidian\99-System\Workflows\Source Ingest Workflow.md`
- `D:\Obsidian\99-System\Workflows\Knowledge Distillation Workflow.md`

### Absolute Rules (no exceptions)

| Rule | Detail |
|------|--------|
| **Metadata** | Only `created`, `status`, `type`. No `tags`, `source`, `updated`, etc. |
| **Status** | `inbox` / `working` / `ready` / `review` / `archived` |
| **Type** | `source` / `atomic` / `claim` / `question` / `wiki` / `moc` / `project` / `area` / `writing` / `weekly` / `system` / `inbox` |
| **AI content** | Knowledge notes always `status: review`, never `ready`. Source notes `status: working`. |
| **Wikilinks** | Internal links use `[[Note Name]]`. External links use `[text](URL)` — never bare URLs. |
| **Math** | All formulas in `$...$` (inline) or `$$...$$` (block). Never bare `a_t`, `θ`, `L(θ)=...`. |
| **Naming** | `Paper - YYYY - Title`, `Claim - 判断句`, `Question - 问题句`, `MOC - 主题`, concept name for Atomic/Wiki |
| **No overwrite** | Check existing notes first. Update > duplicate. Move to `80 Archive/` > delete. |
| **No fabricate** | Missing info → `待补充`. Never guess authors, years, DOIs. |

---

## Workflow

```
Phase 1: Scan → Phase 2: Source Notes → Phase 3: Knowledge Notes → Phase 4: MOC Update
```

Complete one phase before starting the next. Present results after each phase.

### Phase 1: Scan & Recommend

1. Scan `note/papers/` and `note/fields/` in source vault. For each paper, read at minimum `deep-reading.md`.
2. Check target vault for existing notes in `40-Sources/Literature/` and `30-Knowledge/` (all subdirs).
3. Present a transfer plan:

```markdown
## 文献库沉淀计划

### Source Notes（待创建）
| # | 论文 | 目标路径 | 状态 |
|---|------|----------|------|
| 1 | SmolVLA (2025) | 40-Sources/Literature/vla/ | 新建 |

### Knowledge Notes（待创建）
| # | 类型 | 标题 | 来源 | 状态 |
|---|------|------|------|------|

### 已存在（跳过）
...

### 风险提示
...
```

Wait for user confirmation before proceeding.

### Phase 2: Source Notes

Create one Source note per paper at `D:\Obsidian\40-Sources\Literature\<field-slug>\Paper - YYYY - Title.md`.

#### Template

```markdown
---
created: YYYY-MM-DD
status: working
type: source
---

# Paper - YYYY - Title

## 基本信息
- 标题 / 作者 / 机构 / 年份 / 来源：[arXiv:XXXX](https://arxiv.org/abs/XXXX)
- 原文：[filename.pdf](D:\Development\Claude-Paper\papers\<field>\<file>.pdf)

## 一句话总结
## 核心问题
## 主要内容
## 主要结论
## 关键证据
## 局限性
## 与我当前问题的关系
## 可沉淀到 Knowledge 的内容
- Atomic / Claim / Question / Wiki / MOC：（列出候选项）
## 我的评价
## 待补充
```

Synthesize from deep-reading.md, don't copy verbatim. Chinese narrative, English technical terms.

### Phase 3: Knowledge Notes

From each paper's deep-reading.md, extract knowledge into `30-Knowledge/`:

| From deep-reading.md | → Type | → Path |
|---------------------|--------|--------|
| §3.2-3.3 core mechanisms, concepts | **Atomic** | `Atomic/ConceptName.md` |
| §3.5 claims with evidence, §6, §8 | **Claim** | `Claim/Claim - 判断句.md` |
| §1.1 open questions, §7.3 | **Question** | `Question/Question - 问题句.md` |
| Cross-paper synthesis | **Wiki** | `Wiki/TopicName.md` |
| Field navigation | **MOC** | `MOC/MOC - Topic.md` |

Before creating: check for existing/similar notes. Prefer updating over duplicating.

#### Templates (YAML only — body follows Note Type Rules)

```yaml
# Atomic
created: YYYY-MM-DD | status: review | type: atomic
# Body: 基本定义 / 为什么重要 / 来源与依据 (→ [[Source]])

# Claim
created: YYYY-MM-DD | status: review | type: claim
# Body: 判断 / 支持证据 / 反对证据 / 适用边界 / 来源与依据

# Question
created: YYYY-MM-DD | status: review | type: question
# Body: 问题 / 为什么重要 / 当前理解 / 可能方向 / 相关笔记

# Wiki
created: YYYY-MM-DD | status: review | type: wiki
# Body: 概述 / 核心方法 / 关键工作表 / 趋势 / 来源与依据

# MOC
created: YYYY-MM-DD | status: working | type: moc
# Body: 入口 / 核心概念 / 关键判断 / 待解决问题 / 相关文献
```

**Key rules**: status always `review` for AI content; always link back to Source with `[[Paper - YYYY - Title]]`; one concept per Atomic; Claims need evidence or demote to Question.

### Phase 4: MOC Update

- Check `D:\Obsidian\30-Knowledge\MOC\` for relevant MOCs. Update with new note links.
- If 5+ related notes and no MOC exists, suggest creating one. Create only with user confirm.

---

## Post-Transfer

```markdown
## 沉淀完成

### Source: N 新建, N 跳过
### Knowledge: Atomic N | Claim N | Question N | Wiki N | MOC N
### 需复核: 所有 Knowledge 为 review，优先确认 Claim 证据
### 下一步: Obsidian 打开 MOC → 逐条确认 → 继续沉淀剩余论文
```

## Hard Constraints

1. No target vault modification without user confirmation of the plan.
2. Source notes before Knowledge notes — always.
3. Knowledge notes always `status: review` (AI-generated).
4. Never delete — archive instead.
5. Never fabricate — `待补充` for missing info.
6. All URLs in `[text](URL)`, all math in `$...$` / `$$...$$`.
