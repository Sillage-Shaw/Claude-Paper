---
name: academic-translation
description: "Use this skill when the user wants to strictly translate academic papers paragraph by paragraph. This skill focuses on faithful, accurate, paragraph-by-paragraph translation while maintaining terminology consistency, preserving formulas, citations, figure/table numbers, and technical acronyms. Follow the root CLAUDE.md for all output paths and file rules."
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Academic Translation Skill

This skill is for strict academic translation of papers, sections, or paragraphs.

Use this skill when the user asks to:

* 翻译一篇论文
* 翻译论文的某个章节
* 继续翻译某篇论文的后续章节
* 维护术语表
* 补充翻译笔记说明
* 翻译 Abstract / Introduction / Method / Experiments / Conclusion

Examples:

* "请翻译这篇论文的 Abstract 和 Introduction"
* "逐段翻译 ./papers/vla/openvla.pdf"
* "继续翻译 Method 部分，复用已有术语表"
* "帮我翻译下面这段论文段落，保持学术表达"

## Output Rule

Before creating or modifying any file, follow the project file layout, append rules, and final response rules defined in the root `CLAUDE.md`.

Do not define independent output paths inside this skill.

If this skill conflicts with `CLAUDE.md`, follow `CLAUDE.md` unless the user explicitly specifies another path.

Create only the files needed for the current translation task. Do not pre-create empty files.

## Core Principles

1. Translate faithfully and accurately, paragraph by paragraph.
2. Preserve all formulas, citations, figure numbers, and table numbers exactly as in the original.
3. Maintain terminology consistency across all translated sections of the same paper.
4. Keep standard English technical terms when appropriate: method names, model names, dataset names, benchmark names, and technical acronyms.
5. Do not add interpretation, commentary, or analysis — translation only.
6. Mark uncertain translations explicitly with a note.
7. If the source text is ambiguous, preserve the ambiguity rather than guessing.
8. Preserve the original paragraph structure unless reflow is necessary for readability.
9. Use Chinese for the translated body text unless the user asks otherwise.

## Workflow

### Step 1: Identify the paper and translation scope

Identify:

* paper title or identifier
* source material (PDF file path, pasted text, or existing translation)
* target sections (Abstract, Introduction, Method, Experiments, etc.)
* whether this is a new translation or a continuation

If the paper has an existing terminology table, locate and load it.

If this is a continuation, locate the existing `translation.md` to append to.

### Step 2: Inspect source material

Determine what is available:

* full paper PDF
* extracted paper text
* user-pasted paragraphs

If the source is a PDF, extract the relevant sections before translating.

If only partial text is available, clearly state which sections are being translated.

### Step 3: Establish or load the terminology table

Before translating, identify key technical terms and decide on Chinese translations.

If a terminology table already exists at:

```
./note/papers/<paper-slug>/terminology.md
```

load and reuse it.

If this is a new paper, create a new terminology table and save it to the above path.

The terminology table should include:

| English Term | Chinese Translation | Notes |
|---|---|---|
| ... | ... | ... |

Preserve English for: method names, model names, dataset names, benchmark names, and widely-used technical acronyms.

### Step 4: Translate paragraph by paragraph

For each paragraph:

1. Show or reference the original paragraph.
2. Provide the Chinese translation.
3. Keep formulas, citations, figure/table numbers unchanged.
4. Use consistent terminology from the terminology table.

Format each translated section clearly so the user can align original and translation.

If a term is newly encountered and not in the table, add it.

### Step 5: Handle formulas and technical notation

* Preserve all LaTeX formulas exactly.
* Keep mathematical notation, variable names, and equation numbering unchanged.
* Explain notation changes only if essential in a `translation-notes.md`.

### Step 6: Handle citations, figures, and tables

* Preserve citation keys and reference numbers exactly.
* Preserve figure numbers, table numbers, and their captions.
* Do not translate URLs or DOIs.

### Step 7: Append to existing translation

For the same paper, always append new sections to:

```
./note/papers/<paper-slug>/translation.md
```

Do not create separate files for different sections unless the user explicitly asks.

Before appending, insert a clear separator:

```markdown
---

# Translation Batch: <section-or-range>

Source: <paper path, section name, page range, or pasted text>

---
```

### Step 8: Update the terminology table

After each translation batch, update `./note/papers/<paper-slug>/terminology.md` with any new terms encountered.

### Step 9: Optionally write translation notes

If there are noteworthy translation decisions, ambiguities, or difficult passages, write them to `./note/papers/<paper-slug>/translation-notes.md`.

This is optional — only create when useful.

## Recommended Translation Output Structure

For a new paper translation, `translation.md` should follow this structure:

```markdown
# Translation: <Paper Title>

---

# Translation Batch: Abstract

Source: <paper path, section Abstract>

---

<translated content>

---

# Translation Batch: Introduction

Source: <paper path, section Introduction>

---

<translated content>

---
```

For terminology table:

```markdown
# Terminology: <Paper Title>

| English Term | Chinese Translation | Notes |
|---|---|---|
| ... | ... | ... |
```

## Quality Requirements

Before finishing, ensure that:

* the translation is faithful and accurate
* terminology is consistent with the existing table
* formulas, citations, figure/table numbers are preserved exactly
* no interpretation or commentary has been mixed into the translation
* uncertain translations are marked
* the translation is appended to the correct file, not overwritten
* new terms have been added to the terminology table
* output paths and append behavior follow the root `CLAUDE.md`
* the final response reports what was created or updated

## Interaction Style

Prefer:

* faithful paragraph-by-paragraph translation
* consistent terminology
* clear alignment between original and translation
* marking uncertainty when present

Avoid:

* adding interpretation or commentary
* skipping paragraphs
* mixing deep reading analysis into translation
* creating separate translation files for different sections of the same paper
* overwriting existing translations without explicit user request

If the user asks for deep analysis of the translated content, suggest using `paper-deep-reading` instead.
