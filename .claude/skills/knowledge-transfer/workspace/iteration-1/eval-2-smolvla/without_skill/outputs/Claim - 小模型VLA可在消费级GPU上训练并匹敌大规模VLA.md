---
created: 2026-07-03
status: working
type: claim
---

# Claim - 小模型VLA可在消费级GPU上训练并匹敌大规模VLA

## 判断

一个约 450M 参数、可在单张消费级 GPU 上训练的 VLA 模型，经过合理的架构选择和训练策略，可以在标准基准上与 3B-7B 参数的大规模 VLA 取得相当甚至更好的成功率。

## 支持证据

- SmolVLA (0.45B) vs pi0 (3.3B)：LIBERO avg 87.3% vs 86.0%；Meta-World avg 57.3% vs 47.9%~50.5%（Table 2）
- 真实世界多任务 fine-tune：SmolVLA 78.3% vs pi0 61.7% vs ACT 48.3%（Table 5）
- Stacking 任务差距尤其大：SmolVLA 90% vs pi0 40%
- pi0 的预训练数据量是 SmolVLA 的约 400 倍（10K 小时 vs 23K 条轨迹），SmolVLA 在更少数据和更小模型下仍然胜出

## 反对证据 / 例外情况

- pi0 的评估可能并非在完全相同的协议下进行（例如 Stacking 中 pi0 仅 40%，可能存在评估方式差异）
- 实验缺少方差和统计显著性检验，差异的真实显著性不确定
- SmolVLA 未在 pi0 的完整任务套件上测试，只在 LIBERO 和 Meta-World 子集上比较
- 长周期任务（LIBERO-Long）上 SmolVLA 的 0.45B 版本（71%）低于 2.25B 版本（77%），说明规模对长周期推理仍有帮助

## 适用边界

- 目前证据限于 LIBERO 和 Meta-World 模拟基准 + 有限的真实世界任务（4 个短周期操作任务）
- 未验证跨机器人形态、跨任务类型（如移动操作、灵巧操作）的泛化
- 效果可能依赖于特定的效率优化组合（SmolVLM-2 backbone + layer skipping + CA/SA 交错 + Flow Matching）

## 来源与依据

- [[Paper - 2025 - SmolVLA]] Table 2, Table 5
- SmolVLA deep-reading Section 4.2, 3.5
