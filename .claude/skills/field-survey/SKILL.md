---

name: field-survey
description: "Use this skill when the user asks for a literature survey, field survey, research overview, 技术调研, 领域综述, literature map, research landscape, classic papers, SOTA papers, trends, open problems, representative works, or reading roadmap in a specific academic or technical field. This skill should use paper-search when available and follow the root CLAUDE.md for all output paths."
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Field Survey Skill

This skill is for structured academic field surveys and literature research.

Use this skill when the user asks to:

* 调研某个研究领域
* 写领域综述
* 梳理核心概念、经典工作、近期代表工作、SOTA 趋势和开放问题
* 找某个方向的代表论文
* 做 literature review / literature map / research landscape
* 建立某个方向的阅读路线
* 判断某个研究方向是否值得深入

Examples:

* “帮我调研 VLA 领域”
* “整理 action chunking 在机器人模仿学习中的经典论文和最新工作”
* “帮我做 diffusion policy for robot manipulation 的文献综述”
* “找 RAG evaluation 的核心概念、代表论文和趋势”

## Output Rule

Before creating or modifying any file, follow the project file layout defined in the root `CLAUDE.md`.

Do not define independent output paths inside this skill.

If this skill conflicts with `CLAUDE.md`, follow `CLAUDE.md` unless the user explicitly specifies another path.

Create only the files needed for the current task. Do not pre-create empty files.

## Core Principles

1. Do not rely only on memory.
2. Use `paper-search` when available.
3. Define the field boundary before doing a deep survey.
4. Separate classic works, representative methods, recent works, surveys, benchmarks, datasets, trends, and open problems.
5. Be conservative when claiming SOTA.
6. Preserve standard English technical terms when appropriate.
7. Do not hallucinate paper titles, arXiv IDs, venues, benchmark scores, or conclusions.
8. If evidence is incomplete, explicitly mark uncertainty.

## Workflow

### Step 1: Clarify or infer the scope

Identify the research field, time range, user intent, and expected depth.

Common depth levels:

* quick overview
* standard survey
* detailed survey
* reading roadmap
* SOTA tracking
* benchmark / dataset summary

If the request is clear, proceed directly.

If the topic is too broad, either ask one concise clarification question or make a reasonable assumption and state it.

### Step 2: Build a search plan

Create multiple query variants instead of relying on a single keyword.

The query set should usually cover:

* broad field query
* core concept query
* classic paper query
* recent representative work query
* benchmark / dataset query
* survey / review query
* application-specific query
* related terminology query

For example, for VLA, search not only `VLA`, but also phrases such as:

* `vision language action robot manipulation`
* `vision-language-action model embodied AI`
* `robot foundation model action prediction`
* `OpenVLA RT-2 Octo robot manipulation`

### Step 3: Search with paper-search

Use `paper-search` for paper search, metadata lookup, and paper discovery when available.

Prefer multiple small searches over one broad search.

If search results are poor:

1. broaden the query
2. narrow the query
3. change source selection
4. reduce result count
5. search by known title, arXiv ID, DOI, or author if available

If search still fails, explain the limitation and continue only with clearly marked uncertainty.

### Step 4: Decide whether PDFs are needed

Do not download every paper by default.

Download or read full PDFs only when:

* the user explicitly asks
* a paper is central to the survey
* the abstract is insufficient
* method, experiment, formula, or benchmark details need verification
* the paper is selected for later translation or deep reading

When saving downloaded PDFs, follow the root `CLAUDE.md`.

### Step 5: Organize the literature

Classify papers into meaningful groups, such as:

* surveys / overviews
* foundational or classic works
* representative method papers
* recent representative works
* benchmark / dataset / evaluation papers
* applications
* related but out-of-scope works
* papers worth later deep reading

For important papers, extract:

* title
* year
* authors
* source or venue if available
* link
* problem addressed
* core idea
* main contribution
* limitation
* why it matters
* whether it is worth later deep reading

### Step 6: Write the survey

A standard survey should usually include:

1. 调研目标与范围
2. 一句话概览
3. 核心概念
4. 研究问题定义
5. 技术路线图
6. 经典工作
7. 近期代表工作 / SOTA 候选
8. Benchmarks / Datasets / Evaluation
9. 方法分类
10. 领域趋势
11. 开放问题
12. 推荐阅读顺序
13. 后续可执行任务
14. 检索记录

Adjust the structure based on the user's requested depth.

If the user asks for a short survey, keep it compact.

If the user asks for a detailed survey, include tables and more structured comparisons.

If the user asks only for a paper list, focus on paper table and reading priority.

### Step 7: Use cautious academic judgment

When discussing novelty, importance, or SOTA status:

* distinguish confirmed facts from interpretation
* do not overclaim
* state when a conclusion is based only on title/abstract
* state when benchmark evidence is missing
* mark uncertain or unverified information clearly

Useful phrases:

* “从当前检索结果看……”
* “可能是近期代表工作，但是否为严格 SOTA 仍需进一步验证……”
* “该判断基于摘要和元数据，尚未完整阅读论文……”
* “目前证据不足以支持强 SOTA 结论……”

## Quality Requirements

Before finishing, ensure that:

* the field boundary is clear
* multiple query variants were used
* classic works and recent works are distinguished
* benchmarks or datasets are identified if relevant
* paper details are not hallucinated
* uncertainty is explicitly marked
* trends and open problems are summarized
* the output path follows root `CLAUDE.md`
* the final response reports what was created or updated

## Final Response

After completing the task, respond concisely with:

1. what was created or updated
2. exact file path, following root `CLAUDE.md`
3. whether content was created or appended
4. number of papers searched or selected, if applicable
5. 3-5 key conclusions
6. recommended next step

Recommended next steps may include:

* use `academic-translation` for a selected paper
* use `paper-deep-reading` for a selected paper
* use `arxiv-watch` for periodic tracking
* expand the survey with more papers or benchmarks
