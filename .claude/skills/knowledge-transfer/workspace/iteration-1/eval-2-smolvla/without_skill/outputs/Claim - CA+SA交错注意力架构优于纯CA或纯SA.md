---
created: 2026-07-03
status: working
type: claim
---

# Claim - CA+SA交错注意力架构优于纯CA或纯SA

## 判断

在 VLA 的 Action Expert 中，交错使用 Cross-Attention（查阅 VLM 特征）和 Self-Attention（动作序列内部建模）的架构设计，在控制成功率上优于仅使用其中一种注意力机制。

## 支持证据

- SmolVLA Table 6 消融结果：
  - CA+SA 交错：avg 85.5
  - 仅 CA：avg 79.0
  - 仅 SA：avg 74.5
- 差异一致且显著（CA+SA vs SA：+11.0 百分点）
- 直觉解释：CA 让 actions 可以"查阅"VLM 的感知特征，SA 让动作序列内部平滑，两者功能互补
- 对比设计：pi0 使用纯 SA，GR00T N1 使用纯 CA，SmolVLA 的结合似乎取两者之长

## 反对证据 / 例外情况

- 该结论仅在 SmolVLA 的特定架构下验证（SmolVLM-2 backbone + LIBERO benchmark）
- CA+SA 带来了额外的参数量和计算开销，在极致效率场景下可能不是最优
- 交错的次序（先 CA 后 SA 还是先 SA 后 CA）和交错频率未做详细消融

## 适用边界

- 已验证：LIBERO 模拟基准，SmolVLM-2 VLM backbone
- 可能适用：其他 VLA 架构中需要将 VLM 特征融合到 action 生成的场景
- 需谨慎：计算资源极度受限的场景

## 来源与依据

- [[Paper - 2025 - SmolVLA]] Table 6, Section 3.3
- SmolVLA deep-reading Section 3.3, 3.5
