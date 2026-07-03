---
created: 2026-07-03
status: working
type: claim
---

# Claim - VLM前半层特征对机器人控制比后半层更有效

## 判断

在 VLA 架构中，使用预训练 VLM 的前半层（浅层）输出作为 Action Expert 的条件特征，与控制性能不亚于使用全量层的输出。深层的高级语义特征对低层机器人控制任务的贡献有限，而浅层空间视觉特征已经足够。

## 支持证据

- SmolVLA Table 8：N=16 层（前一半）avg 80.3 vs N=32 层（全量）avg 80.3，性能完全相同
- 作者推测：VLM 浅层编码低级视觉特征（纹理、边缘、空间关系），深层编码高级语义（对象类别、文本语义），而机器人控制更依赖空间关系而非抽象语义
- pi0 的做法正好相反：使用 VLM 的后几层特征，这进一步说明具体哪几层最有效可能与 VLM 的类型和训练方式有关

## 反对证据 / 例外情况

- 该结论仅在 SmolVLM-2 这一个 VLM backbone 上验证，不清楚是否适用于其他 VLM（如 PaliGemma、LLaVA）
- 对于需要深层语义理解的任务（如"将所有红色物体放入左边盒子"需要颜色+空间双重推理），前半层可能不够
- 不同 VLM 的层级特征分布可能差异很大，不能直接将 N=16 或 N=L/2 的结论迁移到其他 VLM

## 适用边界

- 已验证：SmolVLM-2 VLM backbone + LIBERO benchmark（操作任务）
- 未验证：其他 VLM backbone、需要复杂语言理解的任务、跨形态控制
- 最优层数可能因 VLM 和任务而不同，需要做 ablation 来确定

## 来源与依据

- [[Paper - 2025 - SmolVLA]] Table 8, Section 3.3
- SmolVLA deep-reading Section 3.3, 6.4
