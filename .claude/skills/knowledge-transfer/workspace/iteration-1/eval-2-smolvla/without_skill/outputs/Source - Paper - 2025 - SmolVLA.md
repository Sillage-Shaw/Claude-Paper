---
created: 2026-07-03
status: ready
type: source
---

# Paper - 2025 - SmolVLA

## 基本信息

- 标题：SmolVLA: A Vision-Language-Action Model for Affordable and Efficient Robotics
- 作者 / 机构：Mustafa Shukor, Dana Aubakirova, Francesco Capuano, Pepijn Kooijmans, Steven Palma, Adil Zouitine, Michel Aractingi, Caroline Pascal, Martino Russi, Andres Marafioti, Simon Alibert, Matthieu Cord, Thomas Wolf, Remi Cadene / Hugging Face, Sorbonne University, valeo.ai, ENS Paris-Saclay
- 年份 / 日期：2025-06-02
- 来源：arXiv preprint
- 原文链接 / 文件：https://arxiv.org/abs/2506.01844

## 一句话总结

SmolVLA 是一个小型、高效、社区驱动的视觉-语言-动作模型，使用 SmolVLM-2 作为冻结感知骨干加轻量 Flow Matching Action Expert，在 481 个社区数据集上预训练，可在消费级 GPU 甚至 CPU 上部署，性能与 10 倍于己的大模型相当。

## 核心问题

如何在保持竞争力的前提下，将 VLA 缩小到可以在消费级 GPU 甚至 CPU 上训练和推理，使之惠及社区研究者？

## 主要内容

SmolVLA 由三部分组成：

1. **VLM 骨干（SmolVLM-2，冻结，仅用前 N=L/2 层）**：SigLIP 视觉编码器，每帧 64 个 visual token，无 image tiling；语言 tokenizer；本体感知状态投影层。
2. **Action Expert（可训练，Flow Matching Transformer）**：交错 Cross-Attention + Causal Self-Attention，从 VLM 中间特征预测动作块的速度场。输入为多视角 RGB 图像 + 语言指令 + 本体感知状态，输出为 n=50 个连续低层控制命令。
3. **异步推理栈**：将策略推理从动作执行中解耦。RobotClient 消费动作队列，低于阈值 g 时触发非阻塞推理，引入 joint-space similarity filter 避免重复处理。

四项核心效率选择：
- Layer skipping：N=16 层 vs 全量 32 层，性能几乎相同
- Visual token reduction：64 token/frame，无 image tiling
- Action expert 宽度缩小：hidden dim = 0.75 x VLM dim
- 社区数据预训练：481 datasets，~23K 条轨迹

## 主要结论

1. 小模型 VLA 可行：SmolVLA (0.45B) 在 LIBERO 上 avg 87.3% vs pi0 (3.3B) 86.0%，Meta-World 上 57.3% vs 47.9%
2. 真实世界多任务 fine-tune 78.3% vs pi0 61.7% vs ACT 48.3%
3. 社区数据预训练效果巨大：78.3% vs 无预训练 51.7%（+26.6 百分点）
4. CA+SA 交错注意力最优：85.5 avg vs CA 79.0 vs SA 74.5
5. Flow Matching 优于回归：80.25 vs 75.25 avg，长周期任务差距更大
6. 异步推理提速约 30%，但长周期任务存在退化（Sorting async 50% vs sync 70%）

## 关键证据

- Table 2：LIBERO 和 Meta-World 模拟基准对比
- Table 5：社区数据预训练消融
- Table 6：注意力机制消融
- Table 8：层数消融
- Table 10：Flow Matching vs Regression
- Figure 5：同步 vs 异步推理对比

## 局限性

- 预训练数据仅含 SO100 类低成本臂，跨形态泛化未验证
- 长周期任务上异步推理退化严重
- 无方差、误差棒、统计显著性检验
- 完全未展示和分析失败案例
- CPU 推理延迟未定量报告
- 未讨论安全性问题

## 与我当前问题的关系

- 提供高效 VLA 架构设计参考和基线
- 验证了社区数据预训练路线的可行性
- 异步推理的工程实践经验可复用
- 可延伸方向：多形态 VLA、社区数据质量评估、VLM 层级对控制的重要性分析

## 可沉淀到 Knowledge 的内容

- Atomic：[[Vision-Language-Action Model]]、[[Flow Matching]]、[[Action Chunk]]、[[Asynchronous Inference in VLA]]、[[Layer Skipping]]、[[Community Datasets]]
- Claim：[[Claim - 小模型VLA可在消费级GPU上训练并匹敌大规模VLA]]、[[Claim - 社区预训练数据显著提升VLA任务性能]]、[[Claim - VLM前半层特征对机器人控制比后半层更有效]]、[[Claim - CA+SA交错注意力架构优于纯CA或纯SA]]、[[Claim - Flow Matching作为动作生成目标优于回归]]
- Question：[[Question - VLA如何实现跨机器人形态的泛化]]、[[Question - 异步推理是否适合长周期复杂机器人任务]]

## 我的评价

工程价值高、可复现性强，学术创新中等。核心贡献在于证明"小模型 + 社区数据可行"而非提出新理论。七维度的消融实验扎实，完全开源，适合作为高效机器人学习方向的参考基线。

## 待补充

- [ ] 阅读 pi0 论文进行完整对比
- [ ] 阅读 OpenVLA 论文理解数据规模差异
- [ ] 追踪社区数据质量评估相关工作
