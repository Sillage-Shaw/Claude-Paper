---
name: session-note
description: "Use this skill when the user wants to turn an AI interaction, debugging process, environment setup, tool installation, configuration process, or troubleshooting session into a concise reusable Markdown note. This skill extracts symptoms, errors, causes, failed attempts, final solution, verification steps, and lessons learned. Follow the root CLAUDE.md for all output paths and file rules."
---

# Session Note Skill

This skill is for converting an AI-assisted interaction process into a concise, reusable technical note.

Use this skill when the user asks to:

* 整理刚才的对话过程
* 总结一次 bug 排查过程
* 记录一次环境配置过程
* 记录一个 GitHub 项目的安装配置过程
* 整理一次工具安装、模型接入、插件配置或系统调试过程
* 将多轮 AI 交互提炼成可复用文档
* 生成排错笔记、配置笔记、踩坑记录或操作备忘

Examples:

* "把刚才解决这个 bug 的过程整理成笔记"
* "把安装 paper-search-mcp 的过程整理一下"
* "把这次配置 Claude Code + DeepSeek 的过程写成可复用文档"
* "帮我把刚才的环境配置过程提炼成一篇 troubleshooting note"

## Output Rule

Before creating or modifying any file, follow the project file layout, file creation rules, append rules, and final response rules defined in the root `CLAUDE.md`.

Do not define independent output paths inside this skill.

If this skill conflicts with `CLAUDE.md`, follow `CLAUDE.md` unless the user explicitly specifies another path.

Create only the files needed for the current note. Do not pre-create empty files.

## Core Principles

1. Do not record the full conversation transcript by default.
2. Extract reusable knowledge, not every interaction detail.
3. Focus on symptoms, evidence, cause, solution, and verification.
4. Preserve exact error messages, commands, paths, versions, and configuration snippets when useful.
5. Clearly distinguish confirmed causes from guesses.
6. Do not include sensitive information such as API keys, tokens, passwords, private URLs, or personal secrets.
7. Do not claim a cause was confirmed unless there was evidence.
8. If the conversation context is incomplete, state what is missing.
9. Use Chinese unless the user asks otherwise.
10. Keep the final note concise and practical.

## Workflow

### Step 1: Identify the session topic

Infer or ask for:

* what problem or task this session was about
* what system, tool, project, or environment was involved
* whether the user wants a bug note, setup note, installation note, or general session summary
* whether the note should be brief or detailed

If the topic is clear, proceed directly.

If unclear, ask one concise clarification question or choose a reasonable title and mention it.

### Step 2: Extract key facts

Extract only useful facts from the interaction:

* goal or background
* environment information
* commands used
* configuration files changed
* error messages
* observed symptoms
* attempted solutions
* failed attempts and why they failed
* final working solution
* verification steps
* remaining risks or unresolved issues

Do not include irrelevant conversation turns.

### Step 3: Analyze the root cause

Explain the root cause using evidence from the session.

Use cautious wording:

* "最终判断原因是……"
* "证据包括……"
* "这个原因较可能，但仍需……验证"
* "此前尝试失败是因为……"

Do not invent missing evidence.

### Step 4: Write the note

Use a structure suitable for the session type.

Default structure:

```markdown
# <Session Title>

## 1. Background / Goal

## 2. Problem Symptoms

## 3. Environment

## 4. Error Messages

## 5. Investigation Process

## 6. Root Cause

## 7. Final Solution

## 8. Verification

## 9. Reusable Commands / Config

## 10. Lessons Learned

## 11. Follow-up Tasks
```

For simple cases, use a shorter structure:

```markdown
# <Session Title>

## Problem

## Cause

## Solution

## Verification

## Notes
```

### Step 5: Handle commands and configuration

When including commands or config snippets:

* keep them minimal
* remove secrets
* mark placeholders clearly
* prefer reproducible commands
* explain where each command should be run

Examples:

```bash
node -v
which node
which claude
```

```json
{
  "claudeCode.useTerminal": true
}
```

### Step 6: Sanitize sensitive content

Before saving, remove or mask:

* API keys
* access tokens
* passwords
* private SSH keys
* personal account secrets
* private service URLs if sensitive

Use placeholders such as:

```text
<API_KEY>
<TOKEN>
<PRIVATE_PATH>
```

### Step 7: Final check

Before finishing, ensure that:

* the note is not a raw transcript
* problem, cause, solution, and verification are clear
* failed attempts are summarized only when useful
* commands and config snippets are reusable
* sensitive information is removed
* uncertain conclusions are marked
* output paths and file behavior follow the root `CLAUDE.md`
* the final response reports what was created or updated
