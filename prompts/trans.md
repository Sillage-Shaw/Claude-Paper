# 快速翻译摘要：判断论文是否值得阅读
```
/trans 请逐段翻译【PDF路径】的 Abstract。

要求：

1. 使用 academic-translation skill；
2. 严格学术翻译，不要口语化；
3. 保留方法名、模型名、数据集名、benchmark 名称和常见英文术语；
4. 建立或更新术语表；
5. 如果 ./translation/【paper-slug】/translation.md 已存在，请把本次 Abstract 翻译追加到文档末尾，不要覆盖；
6. 使用清晰分隔符标记为 “Translation Batch: Abstract”；
7. 保存到 ./translation/【paper-slug】/translation.md；
8. 术语表保存到 ./translation/【paper-slug】/terminology.md。

最后请用 3 句话告诉我这篇论文是否值得继续翻译 Introduction。
```

# 标准逐段翻译：适用于翻译介绍、相关工作或方法
```
/trans 请逐段翻译【PDF路径】的【章节】部分。

要求：

1. 使用 academic-translation skill；
2. 按 paragraph 逐段翻译，不要整段合并成摘要；
3. 每段保留段落编号；
4. 默认格式为：

   * Original
   * Translation
   * Notes
5. 公式、变量、引用、Figure/Table/Section 编号保持原样；
6. 方法名、模型名、数据集名、benchmark 名称默认保留英文；
7. 如果术语首次出现，请在 Notes 中简要解释；
8. 复用已有术语表 ./translation/【paper-slug】/terminology.md；
9. 新术语追加到术语表，不要重复已有术语；
10. 把本次翻译追加到 ./translation/【paper-slug】/translation.md 末尾，不要覆盖之前内容；
11. 用分隔符标记为 “Translation Batch: 【章节】”。

保存路径：

* 翻译正文：./translation/【paper-slug】/translation.md
* 术语表：./translation/【paper-slug】/terminology.md
```
# 粘贴文本翻译版：适用于只复制了一段论文内容
```
/trans 请严格学术翻译下面粘贴的论文内容。

论文标识：【paper-slug】
翻译批次：【章节或段落范围】

要求：

1. 使用 academic-translation skill；
2. 按段落逐段翻译；
3. 保留专业术语、模型名、方法名、数据集名、引用和公式；
4. 对不确定术语不要强行意译，保留英文并说明原因；
5. 如果 ./translation/【paper-slug】/translation.md 已存在，请追加到末尾，不要覆盖；
6. 使用分隔符标记为 “Translation Batch: 【章节或段落范围】”；
7. 术语表保存或更新到 ./translation/【paper-slug】/terminology.md。

原文如下：

【在这里粘贴论文段落】
```
# 连续翻译：适用于之前已经翻译过的章节
```
/trans 继续翻译【PDF路径】的【下一章节】部分。

背景：
我之前已经翻译过这篇论文的部分内容，保存在：
./translation/【paper-slug】/translation.md

术语表保存在：
./translation/【paper-slug】/terminology.md

要求：

1. 使用 academic-translation skill；
2. 先读取已有 translation.md 和 terminology.md，保持术语一致；
3. 不要重复翻译已经翻译过的章节；
4. 逐段翻译【下一章节】；
5. 新内容追加到 translation.md 末尾，不要覆盖；
6. 使用分隔符标记为 “Translation Batch: 【下一章节】”；
7. 如果发现新术语，追加到 terminology.md；
8. 如果发现之前术语翻译可能不一致，不要擅自重写旧内容，只在本次 Notes 中指出。

最后请告诉我：

1. 本次追加了哪个章节；
2. 追加到了哪个文件；
3. 新增了哪些术语；
4. 下一节建议翻译什么。
```
# 全文翻译：适用于翻译一篇完整的论文
```
/trans 我想分批翻译【PDF路径】这篇论文，请先制定翻译计划，不要立即翻译全文。

要求：

1. 使用 academic-translation skill；
2. 先识别论文结构，包括 Abstract、Introduction、Related Work、Method、Experiments、Conclusion、Appendix 等；
3. 给出推荐翻译批次；
4. 说明每一批建议保存到同一个文件：
   ./translation/【paper-slug】/translation.md
5. 术语表统一维护在：
   ./translation/【paper-slug】/terminology.md
6. 每次翻译新章节时都追加到 translation.md 末尾，不要覆盖；
7. 每批之间使用清晰分隔符；
8. 第一批建议只翻译 Abstract + Introduction，等待我确认后再继续 Method。

请输出：

1. 论文结构；
2. 推荐翻译顺序；
3. 每批预计内容；
4. 文件保存路径；
5. 第一批建议使用的具体 /trans 提示词。
```