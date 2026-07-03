---
created: 2026-07-03
status: working
type: claim
---

# Claim - Flow Matching作为动作生成目标优于回归

## 判断

在 VLA 的动作生成中，使用 Flow Matching（生成式建模，预测速度场）作为训练目标，在成功率上优于传统的 L1/L2 回归目标，尤其在动作分布多模态的长周期任务上优势更明显。

## 支持证据

- SmolVLA Table 10 消融：Flow Matching avg 80.25 vs Regression avg 75.25，整体提升 +5.0 百分点
- 长周期任务（Long-horizon）差距更大：53 vs 38，提升 +15 百分点
- 直觉解释：L1 回归在遇到多模态动作分布时倾向于预测"平均"动作（可能是不可行的），而 Flow Matching 的生成性质能自然捕获多模态性
- pi0 也使用 Flow Matching 生成动作，间接验证了这一方向

## 反对证据 / 例外情况

- Flow Matching 的推理成本更高（需要 10 步 ODE solver），在极致低延迟场景下不适用
- 在简单的短周期任务上，回归的差距可能较小（LIBERO-Spatial 等简单任务上差异可能不大）
- Flow Matching 的训练需要额外的噪声调度设计（如 Beta 分布采样 tau），超参数更多

## 适用边界

- 在需要建模多模态动作分布的任务上优势最明显
- 长周期、高精度需求的任务受益最大
- 如果不关心动作多模态性或任务非常简单，L1 回归可能已足够
- 推理步数（K=10）是效率-质量的权衡参数

## 来源与依据

- [[Paper - 2025 - SmolVLA]] Table 10, Section 3.2
- SmolVLA deep-reading Section 3.2, 3.5
- [[Flow Matching]]
