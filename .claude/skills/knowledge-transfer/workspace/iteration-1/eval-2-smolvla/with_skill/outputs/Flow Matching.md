---
created: 2026-07-03
status: review
type: atomic
---

# Flow Matching

Flow Matching（流匹配）是一种生成式建模方法，通过训练神经网络预测从噪声到真实数据之间的"速度场"（vector field），在推理时从纯噪声出发沿 ODE 轨迹逐步去噪生成目标数据。

## 基本定义

在 VLA 的语境中，Flow Matching 用于训练 Action Expert 生成连续动作块。训练时，给定部分噪声化的动作 A_t^τ = τ A_t + (1-τ) ε 和 VLM 特征 o_t，模型预测速度场 v_θ 使得从噪声 ε 指向真实动作 A_t。损失函数为 L(θ) = E[||v_θ(A_t^τ, o_t) - (ε - A_t)||^2]。推理时从纯噪声开始，经 10 步 ODE solver 逐步去噪到达最终动作块。

与 L1 回归相比，Flow Matching 能自然地建模多模态动作分布（同一个起点可以通过多种不同轨迹到达目标），这在机器人控制中尤为重要。

## 为什么重要

Flow Matching 为 VLA 提供了比离散动作 token（如 RT-2 的 binning）和 L1 回归更优的连续动作建模方式。在 SmolVLA 的消融中，Flow Matching 比回归平均提升 5 个百分点（80.25 vs 75.25），在长周期任务上差异更大（53 vs 38）。

## 来源与依据

- [[Paper - 2025 - SmolVLA]] — Table 10 消融验证 Flow Matching 优于回归，§3.1 详述训练目标公式
- π0 (Black et al., 2024) — 首次在 VLA 中大规模使用 Flow Matching 进行动作生成
- Lipman et al. (2022), Liu (2022) — Flow Matching 的理论基础
