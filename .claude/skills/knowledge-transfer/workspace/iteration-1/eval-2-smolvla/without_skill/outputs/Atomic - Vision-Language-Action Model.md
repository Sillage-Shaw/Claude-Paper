---
created: 2026-07-03
status: review
type: atomic
---

# Vision-Language-Action Model

Vision-Language-Action Model（VLA，视觉-语言-动作模型）是一种将预训练视觉-语言模型（VLM）适配为机器人控制策略的架构范式，使其能接收多模态输入（RGB 图像 + 自然语言指令 + 本体感知状态）并输出连续控制动作。

## 基本定义

VLA 的典型架构包含两个核心组件：

1. **VLM 骨干（感知 + 语言理解）**：基于预训练视觉-语言模型，处理图像和语言指令，提取富含世界知识的特征表示
2. **Action Expert（动作生成）**：在 VLM 特征条件下生成动作输出，可采用离散 token（如 RT-2）、回归（如 ACT）或生成式建模（如 Flow Matching）方式

VLA 的核心价值在于利用预训练 VLM 中编码的世界知识（物体识别、空间关系、语义理解）来增强机器人策略的泛化能力，避免从零训练。

## 为什么重要

VLA 代表了从专门化机器人策略向通用机器人基础模型演进的关键范式。通过将 VLM 的通用知识迁移到机器人控制，VLA 有望实现跨任务、跨场景、甚至跨机器人本体的泛化。SmolVLA 的工作进一步证明了这一范式可以在大幅缩减模型规模（从 3B-7B 到 ~450M）的情况下仍然有效。

## 来源与依据

- [[Paper - 2025 - SmolVLA]] — §2.1 综述 VLA 发展脉络
- RT-2 (Brohan et al., 2023) — 首个将 VLM 适配为 VLA 的工作
- OpenVLA (Kim et al., 2024) — 首个大规模开源 VLA
- π0 (Black et al., 2024) — 首个结合 Flow Matching 的大规模 VLA
