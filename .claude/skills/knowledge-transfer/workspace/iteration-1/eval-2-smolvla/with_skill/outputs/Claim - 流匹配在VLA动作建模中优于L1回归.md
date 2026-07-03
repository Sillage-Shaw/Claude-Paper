---
created: 2026-07-03
status: review
type: claim
---

# Claim - 流匹配在VLA动作建模中优于L1回归

## 判断

在 VLA 的动作专家训练中，基于 Flow Matching 的生成式建模目标显著优于标准的 L1 回归损失，尤其在需要多模态动作分布的长周期任务上差异更为明显。

## 支持证据

- SmolVLA 消融实验（Table 10）：Flow Matching 平均 80.25% vs L1 Regression 75.25%，提升 5pp — [[Paper - 2025 - SmolVLA]]
- 在 LIBERO Long（长周期任务）上差异最大：Flow Matching 53% vs Regression 38%，差距 15pp
- Flow Matching 能自然建模多模态动作分布（"从当前位置到目标有多种可行运动轨迹"）— [[Flow Matching]]

## 反对证据 / 例外情况

- 在 LIBERO Spatial 任务上 Regression 略优（92% vs 89%），说明简单任务上两种方法差异不大
- Flow Matching 推理需要 10 步 ODE solver，增加了推理计算量（虽然可以调整步数权衡速度和质量）
- 该对比仅在 SmolVLA 架构和 LIBERO 基准上验证，跨架构和跨任务的泛化性未充分证明

## 适用边界

- **适用**：需要建模连续动作分布、存在多种可行执行方式的机器人操作任务
- **不适用/未验证**：离散动作空间（如 RT-2 的 binning 方式）、对推理延迟极度敏感的场景（ODE solver 的多步推理增加延迟）

## 来源与依据

- [[Paper - 2025 - SmolVLA]] §3.1, Table 10
- π0 (Black et al., 2024) — 首次在 VLA 中使用 Flow Matching
