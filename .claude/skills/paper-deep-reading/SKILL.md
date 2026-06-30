---
name: paper-deep-reading
description: "Use this skill when the user wants to deeply read, understand, analyze, critique, or ask advanced questions about a specific academic paper. This skill goes beyond summarization by reconstructing the paper's problem definition, assumptions, method mechanism, experimental logic, limitations, failure cases, and possible research extensions. Follow the root CLAUDE.md for all output paths and append rules."
---

# Paper Deep Reading Skill

This skill is for deep reading and critical analysis of a single academic paper.

Use this skill when the user asks to:

* 精读一篇论文
* 深度理解一篇论文
* 分析论文方法、公式、实验或图表
* 分析论文贡献、假设、局限和失败场景
* 回答关于论文的深度问题
* 判断论文实验是否支撑结论
* 比较一篇论文和另一篇论文
* 基于论文提出 research ideas
* 将翻译后的论文进一步理解和消化

Examples:

* “请深读这篇论文”
* “分析 ACT 为什么 action chunking 有效”
* “这篇论文的核心假设是什么？”
* “实验是否足以支撑作者结论？”
* “这篇论文和 diffusion policy 的区别是什么？”
* “我已经翻译完这篇论文了，请帮我深入理解 Method”

## Output Rule

Before creating or modifying any file, follow the project file layout, append rules, and final response rules defined in the root `CLAUDE.md`.

Do not define independent output paths inside this skill.

If this skill conflicts with `CLAUDE.md`, follow `CLAUDE.md` unless the user explicitly specifies another path.

Create only the files needed for the current deep reading task. Do not pre-create empty files.

## Core Principles

1. Do not merely summarize the paper.
2. Reconstruct the paper's problem definition, method mechanism, assumptions, and experimental logic.
3. Strictly distinguish three levels of claims:
   - **作者明确写出的内容**：paper explicitly states — cite the specific section, figure, table, or equation.
   - **根据论文可合理推断的内容**：reasonable inference from the paper — clearly mark as inference and explain the reasoning.
   - **无法确定的内容**：neither stated nor reasonably inferable — explicitly tell the user this is uncertain or cannot be concluded. Do not guess.
4. Use concrete evidence from the paper when possible, such as sections, figures, tables, equations, or paragraphs.
5. Identify limitations, hidden assumptions, possible failure cases, and open questions.
6. Preserve important English technical terms when appropriate.
7. If the available material is incomplete or only abstract-level, say so clearly and limit conclusions accordingly.
8. Do not hallucinate details that are not present in the paper. If the paper does not provide enough information to answer a question, state that clearly rather than fabricating an answer.
9. When in doubt, err on the side of saying "这一点论文未明确说明，无法确定" rather than over-interpreting.
10. Use Chinese for explanation unless the user asks otherwise.

## Workflow

### Step 1: Identify the paper and reading goal

Identify:

* paper title or identifier
* available source material
* target section, if specified
* user's main question
* desired depth

Common goals include:

* understand the whole paper
* understand the method
* analyze experiments
* analyze assumptions
* compare with another paper
* prepare for research discussion
* identify research gaps
* generate follow-up ideas

If the user's goal is clear, proceed directly.

If unclear, ask one concise clarification question or make a reasonable assumption and state it.

### Step 2: Inspect available material

Use the best available source material in this order:

1. full paper PDF
2. extracted paper text
3. existing translation notes
4. existing paper notes
5. abstract and metadata only

If a translation exists, use it as auxiliary material, but verify important technical details against the original paper when possible.

If only partial material is available, clearly state that the analysis is based on partial evidence.

### Step 3: Reconstruct the problem definition

Answer:

* What problem is the paper trying to solve?
* Why is this problem important?
* What is the input?
* What is the output?
* What assumptions does the task setting make?
* What are the main challenges?
* Why are prior methods insufficient?

This section should clarify the paper's research object before discussing the method.

### Step 4: Analyze claimed and actual contributions

Separate:

* claimed contribution
* actual technical contribution
* experimental contribution
* engineering contribution
* dataset or benchmark contribution
* conceptual contribution

Be careful not to overstate novelty.

### Step 5: Explain the method mechanism

Go beyond surface-level summary.

Explain:

* high-level idea
* architecture or pipeline
* data flow
* training objective
* inference procedure
* key modules
* why the method might work
* where the method could fail

If equations are involved:

* preserve original notation
* explain each important symbol
* explain what the equation optimizes or measures
* avoid unnecessary derivation unless it helps understanding

### Step 6: Analyze key assumptions

Identify assumptions such as:

* data distribution assumptions
* task assumptions
* embodiment assumptions
* observation assumptions
* action representation assumptions
* evaluation assumptions
* scalability assumptions
* simulation-to-real assumptions

This is one of the most important parts of deep reading.

### Step 7: Analyze experiments

Do not just list results.

Evaluate whether the experiments support the paper's claims.

Analyze:

* datasets
* baselines
* metrics
* evaluation tasks
* main results
* ablation studies
* missing comparisons
* statistical reliability
* real-world experiments, if any
* whether conclusions are justified

If the paper lacks sufficient experiments, state that explicitly.

### Step 8: Analyze limitations and failure cases

Separate:

* limitations explicitly mentioned by the authors
* limitations inferred from the method
* limitations inferred from experiments
* possible failure cases
* reproducibility concerns
* deployment risks

Do not treat the authors' stated limitations as complete.

### Step 9: Compare with related work when needed

If the user asks for comparison, compare along meaningful dimensions, such as:

* problem setting
* input and output
* action representation
* architecture
* training data
* supervision signal
* benchmark
* generalization
* real-world deployment
* computational cost

Do not compare against papers that have not been read or verified unless clearly marked as survey-level knowledge or prior context.

### Step 10: Answer specific deep questions

If the user asks specific questions, answer them directly.

For each question, include a short answer, detailed analysis, evidence from the paper, your interpretation, and remaining uncertainty. This helps distinguish paper evidence from interpretation.

### Step 11: Generate research ideas when useful

If the user asks for research directions or if useful after deep analysis, propose concrete ideas.

Each idea should include:

* motivation
* proposed modification
* why it might help
* how to test it
* risk or limitation
* required resources

Avoid vague ideas.

## Output

All output rules (save path, file naming, output structure, append behavior) are defined in the root `CLAUDE.md`. The output must follow the structure in `./templates/paper-note.md` as specified by `CLAUDE.md`. Do not define independent output paths or formats inside this skill.

## Quality Requirements

Before finishing, ensure that:

* the answer goes beyond summary
* the problem definition is reconstructed
* the method mechanism is explained
* key assumptions are identified
* experiments are evaluated against the claims
* the three evidence levels are clearly distinguished:
  - what the paper explicitly states (with section/figure/table citations)
  - what can be reasonably inferred from the paper (marked as inference)
  - what is uncertain or cannot be concluded (stated explicitly to the user)
* paper claims and your interpretation are clearly separated
* limitations and failure cases are discussed
* the user's specific questions are answered
* unverified details are not hallucinated — if the paper does not provide enough information, say so
* output paths and append behavior follow the root `CLAUDE.md`
* the final response reports what was created or updated

## Interaction Style

Prefer:

* mechanism-level explanation
* assumption analysis
* experiment critique
* evidence-based comparison
* concrete research implications

Avoid:

* generic praise
* vague summary
* ungrounded SOTA claims
* unsupported research ideas
* excessive speculation

If evidence is insufficient, say what is missing and what would need to be checked.
