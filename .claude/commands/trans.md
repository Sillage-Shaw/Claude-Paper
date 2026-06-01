使用 `academic-translation` skill 翻译用户指定的论文、章节或段落。

用户输入如下：

$ARGUMENTS

执行要求：

1. 严格按照 `.claude/skills/academic-translation/SKILL.md` 的流程执行；
2. 所有文件路径、追加规则、文件创建规则和最终回复格式都遵循根目录 `CLAUDE.md`；
3. 如果用户给出了明确路径或特殊要求，优先遵循用户要求；
4. 保持逐段学术翻译，保留术语、公式、引用和图表编号；
5. 如果已有术语表或翻译文件，请按 `CLAUDE.md` 的项目结构查找并复用。