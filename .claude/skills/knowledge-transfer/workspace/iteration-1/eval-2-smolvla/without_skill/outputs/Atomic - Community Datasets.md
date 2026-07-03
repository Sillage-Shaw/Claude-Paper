---
created: 2026-07-03
status: working
type: atomic
---

# Community Datasets

## 定义

Community Datasets（社区数据集）是由社区研究者使用低成本机器人平台（如 SO-100，成本仅约 $100）自行收集、共享的机器人演示数据集，与工业级数据集（如 OXE、DROID，使用昂贵的 Franka 等机器人采集）相对。

## 特征

- **平台多样性**：来自不同个体的不同硬件实例，存在相机位置、光照、背景等差异
- **标注质量不一**：任务描述可能不标准、不一致或缺失
- **规模较小**：单个数据集通常只有几十到几百条轨迹
- **但累计规模可观**：SmolVLA 聚合了 481 个数据集，共计 ~23K 条轨迹

## 在 VLA 训练中的价值

SmolVLA 的 Table 5 是最重要的证据：
- 社区数据预训练 + 多任务 fine-tune：78.3% 成功率
- 无预训练直接多任务 fine-tune：51.7% 成功率
- 提升 +26.6 百分点

说明：尽管社区数据有噪声，但通过简单后处理（VLM 自动标注指令 + 相机命名标准化）即可提供足够的多样性来训练通用操作技能。

## 处理流程

SmolVLA 的社区数据处理方法：
1. 使用 Qwen2.5-VL-3B 为每条轨迹自动生成简短 action-oriented 任务描述
2. 手动标准化相机视角命名（如 top、wrist、side）
3. 统一动作空间格式

## 来源与依据

- [[Paper - 2025 - SmolVLA]] Section 3.4, Table 5
- SmolVLA deep-reading Section 3.3, 6.2
