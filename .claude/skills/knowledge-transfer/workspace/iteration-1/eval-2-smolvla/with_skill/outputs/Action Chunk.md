---
created: 2026-07-03
status: review
type: atomic
---

# Action Chunk

Action Chunk（动作块）是机器人视觉运动策略中一种动作表示方式，指策略在一次推理中输出一段包含 n 个连续低层控制命令的序列 A_t = (a_t, a_{t+1}, ..., a_{t+n})，而非单个动作。

## 基本定义

Action Chunk 将动作预测从单步扩展到多步序列，使得机器人可以在不重新推理的情况下连续执行多个动作。块大小 n 是关键的效率-响应性权衡参数：n 太小（如 n=1）导致推理开销大，n 太大（如 n=100）降低对环境变化的响应能力。SmolVLA 使用 n=50。

## 为什么重要

Action Chunk 是连接模型推理速度和机器人控制频率的关键桥梁。较长的 chunk 可以通过摊销推理成本提高效率（sync 模式下每 n 步才推理一次），但也引入了开环控制的风险。它与异步推理配合时，可通过 queue threshold g 实现推理和执行的重叠，进一步隐藏推理延迟。

## 来源与依据

- [[Paper - 2025 - SmolVLA]] — SmolVLA 使用 chunk size n=50，并通过消融（Table 12）表明 10-50 之间的 chunk size 在反应性和效率之间取得最佳平衡
- ACT (Zhao et al., 2023) — 最早大规模采用 action chunk 的模仿学习工作
