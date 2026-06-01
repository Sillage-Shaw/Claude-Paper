# 快速了解版
```
/survey 【研究领域】

请做一个快速领域调研，目标是帮我在短时间内建立整体认知。

要求：

1. 用 3-5 句话解释这个领域研究什么、为什么重要；
2. 梳理核心概念和常见术语，重要英文术语保留原文；
3. 使用 paper-search 检索相关论文，不要只凭记忆；
4. 找 5-8 篇代表论文即可，不需要下载所有 PDF；
5. 区分经典工作和近期代表工作；
6. 总结主要技术路线、发展趋势和开放问题；
7. 给出推荐阅读顺序；
8. 把结果保存到 ./notes/【topic-slug】/survey.md。

最后请告诉我最值得后续精读的 3 篇论文。
```relaod
---
# 标准调研版
```
/survey 【研究领域】

请做一份系统性领域调研。我希望了解这个方向的核心问题、技术路线、经典工作、近期代表工作、SOTA 趋势、benchmark/dataset 和开放问题。

具体要求：

1. 先定义这个领域的研究边界：它解决什么问题，输入输出是什么，和相邻领域有什么区别；
2. 使用 paper-search 设计多组关键词检索，不要只凭模型记忆；
3. 检索并筛选 10-20 篇代表论文；
4. 将论文分成以下类别：

   * survey / overview；
   * foundational / classic works；
   * representative method papers；
   * recent SOTA / representative works；
   * benchmark / dataset / evaluation；
   * related but out-of-scope works；
5. 对每篇重要论文整理：标题、年份、作者、链接、核心思想、主要贡献、局限、为什么重要；
6. 梳理该领域的技术演化路线；
7. 总结当前趋势和仍未解决的开放问题；
8. 给出推荐阅读顺序，并标注哪些论文适合后续 deep reading；
9. 把完整结果保存到 ./notes/【topic-slug】/survey.md；
10. 如有必要，额外生成 ./notes/【topic-slug】/paper-table.md 和 ./notes/【topic-slug】/reading-roadmap.md。

注意：

* 不要随意声称某篇论文是 SOTA，除非有明确 benchmark 或证据支持；
* 如果只读到摘要，要明确说明；
* 如果某些信息无法验证，要标注为“待确认”；
* 中文解释为主，标准英文术语保留。
```
---
# 深度调研版
```
/survey 【研究领域】

请对这个方向做一份深度领域综述。我希望把它作为后续研究主题，因此需要的不只是论文列表，而是一个可用于选题、开题和后续精读的研究地图。

请按以下流程完成：

第一阶段：界定问题

1. 定义该领域的核心研究问题；
2. 说明它和相关领域的区别与联系；
3. 总结该领域的典型输入、输出、任务设定、评价方式和主要挑战。

第二阶段：检索与筛选

1. 使用 paper-search 检索，不要只凭记忆；
2. 设计多组关键词，覆盖：

   * broad field query；
   * core concept query；
   * classic paper query；
   * recent SOTA query；
   * benchmark / dataset query；
   * survey / review query；
   * application-specific query；
3. 检索经典论文、近期论文、survey、benchmark 和 dataset；
4. 筛选 20 篇左右代表论文；
5. 不要默认下载全部 PDF，只下载最值得精读或需要验证细节的论文到 ./papers/【topic-slug】/。

第三阶段：结构化综述
请输出并保存到 ./notes/【topic-slug】/survey.md，结构包括：

1. 调研目标与范围；
2. 一句话概览；
3. 核心概念和术语表；
4. 研究问题定义；
5. 技术路线图；
6. 经典工作；
7. 近期代表工作 / SOTA 候选；
8. Benchmark、Dataset 和 Evaluation；
9. 方法分类与对比；
10. 领域趋势；
11. 开放问题；
12. 可能的研究机会；
13. 推荐阅读顺序；
14. 后续精读候选论文；
15. 检索记录。

第四阶段：批判性分析
请进一步分析：

1. 这些方法背后的共同假设是什么；
2. 当前方法主要受限于数据、模型、任务设定、评估方式还是部署条件；
3. 哪些论文真正推动了问题定义或方法范式变化；
4. 哪些工作可能只是增量改进；
5. 如果我要进入这个方向，最值得切入的 3-5 个研究问题是什么。

最终回复请告诉我：

1. 结果保存路径；
2. 检索了多少条结果；
3. 筛选了多少篇论文；
4. 下载了哪些 PDF；
5. 最值得精读的 5 篇论文；
6. 下一步建议使用哪个 skill：academic-translation、paper-deep-reading 或 arxiv-watch。

```