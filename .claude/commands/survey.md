使用 `field-survey` skill 完成用户给定主题的领域调研。

用户输入如下：

$ARGUMENTS

执行要求：

1. 严格按照 `.claude/skills/field-survey/SKILL.md` 的流程执行；
2. 所有文件路径、文件创建规则、追加规则和最终回复格式都遵循根目录 `CLAUDE.md`；
3. 如果用户给出了明确路径或特殊要求，优先遵循用户要求；
4. 使用 `paper-search` 检索论文，不要只凭记忆；
5. 区分核心概念、经典工作、近期代表工作、benchmark/dataset、趋势和开放问题；
6. 除非用户明确要求，否则不要下载所有 PDF，只下载少量最值得后续精读的论文。