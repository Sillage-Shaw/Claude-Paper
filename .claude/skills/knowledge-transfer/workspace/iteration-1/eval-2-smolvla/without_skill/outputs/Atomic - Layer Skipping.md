---
created: 2026-07-03
status: working
type: atomic
---

# Layer Skipping

## 定义

Layer Skipping（层跳跃）是在 VLA 中使用预训练 VLM 作为感知骨干时的一种效率策略：仅使用 VLM 的前 N 层（通常为前一半）来提取中间特征，丢弃剩余层的输出。

## 直觉

VLM 的浅层倾向于编码低级视觉特征（纹理、边缘、空间关系），深层倾向于编码高级语义特征（对象类别、文本语义）。对于机器人控制任务，空间关系和视觉细节可能比抽象语义更重要，因此跳过深层既节省计算又不显著损失控制性能。

## 实验证据

SmolVLA (Table 8):
- N=16 层（前一半）：avg 80.3
- N=32 层（全量）：avg 80.3
- 性能完全相同，但计算量减半

## 注意事项

- 这一发现可能与特定 VLM（SmolVLM-2）的层级特征分布有关，尚未验证是否适用于其他 VLM
- 对于需要深层语义理解的任务（如复杂指令理解），层跳过可能有害
- pi0 使用 VLM 的后几层特征，与 SmolVLA 相反，说明最优层位置可能依赖于具体 VLM 和任务

## 来源与依据

- [[Paper - 2025 - SmolVLA]] Section 3.3, Table 8
- SmolVLA deep-reading Section 3.3, 6.4
