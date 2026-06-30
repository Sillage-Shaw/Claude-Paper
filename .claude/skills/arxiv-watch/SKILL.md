---
name: arxiv-watch
description: "Use this skill when the user wants to monitor, search, track, filter, or summarize recent arXiv papers in a specific academic field. This skill focuses on recent-paper discovery, relevance filtering, deduplication, concise summaries, reading priority, and follow-up recommendations. Follow the root CLAUDE.md for all output paths and file rules."
---

# ArXiv Watch Skill

This skill is for tracking recent arXiv papers in a specific research field.

Use this skill when the user asks to:

* 追踪某个领域最新论文
* 检索最近几天或最近一周的 arXiv 论文
* 生成 arXiv 日报、周报或追踪笔记
* 找最近值得读的新论文
* 判断哪些新论文值得翻译或精读
* 对比本次新论文和之前追踪结果

Examples:

* “帮我检索 VLA 最近一周的 arXiv 新论文”
* “追踪 action chunking 方向最近几天的新论文”
* “找最近关于 robot foundation model 的新论文，并判断哪些值得精读”

## Output Rule

Before creating or modifying any file, follow the project file layout, file creation rules, append rules, and final response rules defined in the root `CLAUDE.md`.

Do not define independent output paths inside this skill.

If this skill conflicts with `CLAUDE.md`, follow `CLAUDE.md` unless the user explicitly specifies another path.

Create only the files needed for the current tracking task. Do not pre-create empty files.

## Core Principles

1. Focus on recent papers and new developments.
2. Use `paper-search` or other available paper search tools when possible.
3. Search with multiple query variants.
4. Deduplicate papers across queries.
5. Prioritize relevance over quantity.
6. Distinguish title/abstract-level judgment from full-paper judgment.
7. Do not claim a paper is important, novel, or SOTA without evidence.
8. Mark papers worth later `academic-translation` or `paper-deep-reading`.
9. Download PDFs only when useful or explicitly requested.

## Workflow

### Step 1: Identify the watch scope

Identify or infer:

* research field
* time window
* keywords
* inclusion criteria
* exclusion criteria
* maximum number of papers
* whether to download PDFs
* whether to compare with previous watch notes

If the user does not specify a time window, use a recent window such as the last few days or last week.

If the topic is too broad, ask one concise clarification question or make a reasonable assumption and state it.

### Step 2: Build search queries

Create multiple query variants.

The query set should usually include:

* broad field query
* common acronym query
* method-specific query
* application-specific query
* related terminology query
* benchmark or dataset query if relevant

Example for VLA:

* `vision language action`
* `VLA robot manipulation`
* `vision-language-action model`
* `robot foundation model`
* `embodied AI manipulation`

Example for action chunking:

* `action chunking`
* `ACT robot manipulation`
* `bimanual manipulation action chunking`
* `long horizon imitation learning action chunking`

### Step 3: Search recent papers

Use `paper-search` or available paper search tools.

Prefer arXiv-focused search for this skill.

If search results are weak:

1. broaden the query
2. use synonyms or related terms
3. search by known model names, task names, benchmark names, or authors
4. relax overly narrow constraints
5. clearly state if no strong recent papers were found

### Step 4: Deduplicate and filter

Deduplicate papers by:

* title
* arXiv ID
* DOI
* URL
* near-duplicate title

Classify results into:

* highly relevant
* possibly relevant
* background reading
* out of scope
* duplicate / already seen

Keep borderline papers only if they may be useful, and mark them as “possibly relevant”.

### Step 5: Summarize selected papers

For each selected paper, summarize:

* title
* authors if available
* date or year
* link
* one-sentence summary
* relevance to the watched field
* likely contribution
* reading priority
* suggested next action

Suggested next actions may include:

* ignore for now
* add to reading list
* download PDF
* translate abstract / introduction
* deep read method
* compare with known papers
* update field survey

### Step 6: Compare with previous watch results when useful

If previous watch notes exist, check whether each paper is:

* new
* already seen
* related to a previously tracked paper
* part of an emerging trend

Do not fabricate historical tracking results.

If comparison is not possible, say so.

### Step 7: Write the watch note

A standard watch note should include:

1. Watch scope
2. Time window
3. Search queries
4. Inclusion / exclusion criteria
5. Highly relevant papers
6. Possibly relevant papers
7. Duplicates or already-seen papers if applicable
8. Emerging trends
9. Recommended reading priority
10. Suggested follow-up actions
11. Search limitations

Keep the note concise and actionable.

## Relevance Judgment

When judging relevance, consider:

* direct match with the watched topic
* task setting
* method similarity
* benchmark or dataset relevance
* whether it introduces a new model, dataset, benchmark, or evaluation method
* whether it is likely to affect the user's research direction

Use conservative labels:

* Highly relevant
* Possibly relevant
* Background reading
* Out of scope
* Duplicate / already seen

## Quality Requirements

Before finishing, ensure that:

* multiple query variants were used
* papers were deduplicated
* relevance judgments are explicit
* uncertain judgments are marked
* no unsupported SOTA claims are made
* papers worth translation or deep reading are clearly marked
* output paths and file creation follow root `CLAUDE.md`

## Important Limitation

This skill defines how to perform arXiv tracking when invoked.

It does not create an automatic schedule by itself.

If the user wants periodic execution, set up a separate scheduled task, cron job, loop, or Claude Code scheduled workflow that invokes this skill.
