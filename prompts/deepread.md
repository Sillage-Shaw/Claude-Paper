# 完整精读一篇论文
```
/deepread 请完整深读 ./papers/action-chunking/ACT.pdf。

要求：
1. 重建论文的问题定义；
2. 分析作者声称的贡献和实际贡献；
3. 解释方法机制，而不是只复述摘要；
4. 分析关键假设；
5. 判断实验是否支撑作者结论；
6. 总结局限、失败场景和可复现风险；
7. 给出 3-5 个可能的后续研究方向；
8. 保存到 ./notes/act/deep-reading.md。
```
# 只分析一篇论文的方法
```
/deepread 请重点分析 ./papers/action-chunking/ACT.pdf 的 Method 部分。

要求：
1. 解释整体 pipeline；
2. 说明输入、输出、训练目标和推理过程；
3. 分析每个关键模块为什么这样设计；
4. 解释公式中的变量和优化目标；
5. 分析这个方法可能在哪些场景失败；
6. 保存到 ./notes/act/method-analysis.md。
```
# 分析实验是否可信
```
/deepread 请重点分析 ./papers/action-chunking/ACT.pdf 的实验部分。

要求：
1. 总结实验设置、任务、数据集、baseline 和 metrics；
2. 分析主实验是否支撑作者的核心 claim；
3. 检查 ablation study 是否充分；
4. 找出缺失的实验对比；
5. 判断结论是否可能过度外推；
6. 保存到 ./notes/act/experiment-analysis.md。
```
# 基于翻译笔记深度阅读
```
/deepread 我已经翻译了这篇论文，翻译文件在 ./translation/act/translation.md，术语表在 ./translation/act/terminology.md。

请基于翻译内容深读这篇论文，重点分析：
1. 论文的核心问题；
2. 方法为什么可能有效；
3. 作者的关键假设；
4. 实验是否支持结论；
5. 这篇论文对我后续研究有什么启发。

请保存到 ./notes/act/deep-reading.md。
```
# 对比两篇论文
```
/deepread 请比较 ./papers/action-chunking/ACT.pdf 和 ./papers/diffusion-policy/diffusion-policy.pdf。

重点比较：
1. 问题设定；
2. 动作表示；
3. policy 建模方式；
4. 训练目标；
5. 推理过程；
6. 泛化能力；
7. 实验设置；
8. 局限和适用场景。

请保存到 ./notes/act-vs-diffusion-policy.md。
```