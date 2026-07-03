---
created: 2026-07-03
status: working
type: moc
---

# MOC - VLA

## 入口

VLA（Vision-Language-Action）是将预训练视觉-语言模型适配为机器人控制策略的研究方向。本 MOC 组织与 VLA 相关的核心概念、关键判断、待解决问题和相关文献。

## 核心概念

- [[Vision-Language-Action Model]] — VLA 的架构范式和基本定义
- [[Action Chunk]] — 动作块：一次推理输出多步连续控制命令的表示方式
- [[Flow Matching]] — 流匹配：用于训练 Action Expert 的生成式建模方法
- [[Asynchronous Inference]] — 异步推理：解耦感知/动作预测与动作执行的系统架构
- [[Community Datasets for Robotics]] — 社区数据集：来自低成本开源机器人平台的众包示教数据

## 关键判断

- [[Claim - 小模型VLA在特定任务上可媲美大10倍模型]] — 450M 参数 VLA 在标准操作任务上与 3.3B-7B 模型竞争
- [[Claim - 社区数据预训练可显著提升VLA下游任务性能]] — +26.6pp 的预训练收益
- [[Claim - 流匹配在VLA动作建模中优于L1回归]] — Flow Matching 比 Regression 平均高 5pp
- [[Claim - VLM前半层特征对机器人控制任务已足够]] — 前 L/2 层的特征几乎等同于全量层

## 待解决问题

- [[Question - VLA如何实现跨机器人平台和形态的泛化]] — 跨形态泛化是 VLA 走向通用基础模型的核心挑战
- [[Question - 社区机器人数据质量如何自动化评估与筛选]] — 社区数据规模化需要自动化质量管理

## 相关文献

- [[Paper - 2025 - SmolVLA]] — 小型高效社区驱动 VLA，450M 参数，完全开源

## 待扩展

- 加入更多 VLA 论文后补充：π0、OpenVLA、RT-2、TinyVLA、VLA-0 等
- 补充 Wiki 页面：VLA模型架构、VLA效率优化方法、VLA数据策略
