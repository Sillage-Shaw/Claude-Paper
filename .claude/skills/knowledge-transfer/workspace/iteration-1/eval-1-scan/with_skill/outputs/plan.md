# 文献库沉淀计划

> 扫描日期：2026-07-03
> 来源库：D:\Development\Claude-Paper
> 目标库：D:\Obsidian
> 阶段：Phase 1 — 扫描与盘点

---

## 一、扫描结果总览

### 来源库内容统计

| 类别 | 数量 | 详情 |
|------|------|------|
| 已深度阅读论文 | 5 篇 | smolvla, shao2025-vla-survey, rt2, pi0, pi0.5 |
| 有翻译的论文 | 5 篇 | 同上（含 terminology + translation-notes） |
| 已下载 PDF | 11 篇 | vla 领域 11 篇论文 PDF |
| 领域级调研 | 1 个 | vla (survey + paper-table + reading-roadmap) |

### 目标库状态

| 目录 | 状态 |
|------|------|
| 40-Sources/Literature/ | 空 — 无任何 Source 笔记 |
| 30-Knowledge/Atomic/ | 空 — 无任何 Atomic 笔记 |
| 30-Knowledge/Wiki/ | 空 — 无任何 Wiki 笔记 |
| 30-Knowledge/MOC/ | 空 — 无任何 MOC |
| 30-Knowledge/Claim/ | 空 — 无任何 Claim 笔记 |
| 30-Knowledge/Question/ | 空 — 无任何 Question 笔记 |

**结论：目标库为全新空库，所有 5 篇已深度阅读论文和 1 个领域调研均为新建。**

---

## 二、Source Notes（待创建，Phase 2）

| # | 论文 | 年份 | 来源路径 | 目标路径 | 状态 |
|---|------|------|----------|----------|------|
| 1 | SmolVLA | 2025 | note/papers/smolvla/deep-reading.md | 40-Sources/Literature/vla/Paper - 2025 - SmolVLA.md | 新建 |
| 2 | VLA Survey (Shao et al.) | 2025 | note/papers/shao2025-vla-survey/deep-reading.md | 40-Sources/Literature/vla/Paper - 2025 - Large VLM-based VLA Survey.md | 新建 |
| 3 | RT-2 | 2023 | note/papers/rt2/deep-reading.md | 40-Sources/Literature/vla/Paper - 2023 - RT-2.md | 新建 |
| 4 | pi0 | 2024 | note/papers/pi0/deep-reading.md | 40-Sources/Literature/vla/Paper - 2024 - pi0.md | 新建 |
| 5 | pi0.5 | 2025 | note/papers/pi0.5/deep-reading.md | 40-Sources/Literature/vla/Paper - 2025 - pi0.5.md | 新建 |

5 篇 Source 笔记全部为新建，无已存在项需要跳过。

---

## 三、Knowledge Notes（待创建，Phase 3）

### 3.1 Atomic（原子知识点）— 15 条候选

| # | 概念 | 来源论文 | 来源章节 |
|---|------|----------|----------|
| 1 | Flow Matching | pi0, pi0.5, SmolVLA | pi0 §2.2, SmolVLA §3.2 |
| 2 | Action Token / Action Tokenization | RT-2 | RT-2 §3.2 |
| 3 | Action Chunking | SmolVLA, RT-2, pi0 | SmolVLA §3.2, pi0 §2.2 |
| 4 | Co-Fine-Tuning | RT-2 | RT-2 §3.2 |
| 5 | Heterogeneous Co-Training | pi0.5 | pi0.5 §3.3 |
| 6 | Cross-Embodiment Generalization | pi0, pi0.5, survey | pi0 §2.4, survey §3.3 |
| 7 | Action Expert (MoE-style) | pi0, pi0.5, SmolVLA | pi0 §2.2, SmolVLA §3.1 |
| 8 | Asynchronous Inference | SmolVLA | SmolVLA §3.3 |
| 9 | Monolithic VLA Architecture | shao2025-vla-survey | survey §3.2 |
| 10 | Hierarchical VLA Architecture | shao2025-vla-survey | survey §3.2 |
| 11 | Dual-System VLA | shao2025-vla-survey, pi0, pi0.5 | survey §3.2, pi0 §2.2 |
| 12 | FAST Tokenizer (DCT-based) | pi0.5 | pi0.5 §3.2 |
| 13 | Vision-Language-Action Model (VLA) | RT-2, survey | RT-2 §2.1, survey §3.1 |
| 14 | Layer Skipping (for efficient VLA) | SmolVLA | SmolVLA §3.3 |
| 15 | Two-Stage Training (Pre-training + Post-training) | pi0, pi0.5 | pi0 §2.3, pi0.5 §3.2 |

### 3.2 Claim（可验证判断）— 12 条候选

| # | 判断 | 来源论文 | 来源章节 |
|---|------|----------|----------|
| 1 | 小模型 VLA 在特定任务上可媲美大模型 VLA | SmolVLA | §3.5 |
| 2 | 社区数据预训练对 VLA 性能有显著提升 (~+26pp) | SmolVLA | §3.5, §4.2 |
| 3 | Flow Matching 在 VLA 动作生成中优于离散回归 | SmolVLA, pi0 | SmolVLA §3.5, pi0 §2.2 |
| 4 | VLM 前半层特征对机器人控制比后半层更有用 | SmolVLA | §3.5 |
| 5 | 交错 CA+SA 的 Action Expert 优于纯 CA 或纯 SA | SmolVLA | §3.5 |
| 6 | Co-fine-tuning 优于纯机器人数据微调 | RT-2 | RT-2 §4.2 |
| 7 | VLM 预训练的语义知识可迁移到低层机器人控制 | RT-2 | RT-2 §5.1 |
| 8 | 异构多源 co-training 对开放世界泛化至关重要 | pi0.5 | pi0.5 §4.2, §5.1 |
| 9 | 大规模预训练对复杂多阶段任务帮助最大 | pi0 | pi0 §3.2 |
| 10 | VLA 领域存在 Monolithic 与 Hierarchical 两种核心范式 | shao2025-vla-survey | §3.2 |
| 11 | 当前 VLA benchmark（LIBERO/CALVIN）存在系统性评估缺陷 | survey | §8.2 |
| 12 | 97.6% 训练数据不来自目标平台仍可实现开放世界泛化 | pi0.5 | pi0.5 §2.3 |

### 3.3 Question（待解决问题）— 8 条候选

| # | 问题 | 来源论文 | 来源章节 |
|---|------|----------|----------|
| 1 | VLA 如何实现跨机器人形态的 zero-shot 泛化？ | SmolVLA | §6.3, §7.3 |
| 2 | VLA 的预训练数据最优组成方式是什么？ | pi0, pi0.5 | pi0 §4, pi0.5 §6.3 |
| 3 | 如何自动检测和过滤低质量社区机器人数据？ | SmolVLA | §7.3 |
| 4 | VLM 的哪些层特征对机器人控制最重要？ | SmolVLA | §7.3 |
| 5 | Monolithic vs Hierarchical 架构在什么条件下更优？ | shao2025-vla-survey | §5.3 |
| 6 | VLA 的 Scaling Law 是否遵循 LLM 的幂律？ | survey | §10.1 |
| 7 | 异步推理在长周期任务上的成功率退化如何弥补？ | SmolVLA | §4.2 |
| 8 | 如何建立更可靠的 VLA 评估体系？ | survey | §10.1 |

### 3.4 Wiki（主题综合）— 4 条候选

| # | 主题 | 来源 | 说明 |
|---|------|------|------|
| 1 | VLA 模型架构综述 | shao2025-vla-survey + 5 篇 deep-reading | 综合 Monolithic/Hierarchical/Flow Matching 等架构知识 |
| 2 | VLA 动作生成方法对比 | RT-2 + pi0 + SmolVLA + pi0.5 | 离散化 vs 扩散 vs Flow Matching |
| 3 | VLA 训练策略演进 | RT-2 + pi0 + pi0.5 + SmolVLA | co-fine-tuning → pre/post-training → co-training |
| 4 | VLA 评估体系与 Benchmark | survey + benchmark-audit PDF | LIBERO/CALVIN/SimplerEnv 评估方法论 |

### 3.5 MOC（知识地图）— 1 条候选

| # | MOC | 说明 |
|---|-----|------|
| 1 | MOC - VLA | VLA 领域总入口，链接所有 VLA 相关 Source、Atomic、Claim、Question、Wiki |

---

## 四、领域级内容（待决定）

以下来自 `note/fields/vla/` 的领域级内容可选择性沉淀：

| 文件 | 内容 | 建议处理 |
|------|------|----------|
| survey.md | VLA 领域 35 篇论文系统调研 | 可作为 Wiki "VLA 领域综述" 的基础 + 建议创建 MOC - VLA |
| paper-table.md | VLA 论文速查表（含 PDF 路径、亮点、arXiv 链接） | 可整合到 Wiki 或 MOC 中作为附录 |
| reading-roadmap.md | VLA 阅读路线图（4 阶段、17 篇论文、时间预算） | 可作为 MOC - VLA 中的学习路径部分 |

---

## 五、风险提示

1. **一次性创建量较大**：5 篇 Source + ~40 条 Knowledge 候选，需要分阶段执行，建议先 Phase 2 完成 Source Notes，再逐步进行 Phase 3 Knowledge Distillation
2. **Knowledge 笔记需要人工复核**：所有 AI 生成的 Knowledge 笔记将标记为 `status: review`，需要用户逐条验证后改为 `ready`
3. **Atomic 和 Claim 可能存在边界模糊**：如 "Flow Matching" 既可以写成 Atomic（概念解释），也可以写成 Claim（"Flow Matching 优于扩散"），需要用户确认优先级
4. **Wiki 需要跨论文综合**：Wiki 候选需要综合 5 篇论文的内容，不能仅依赖单篇 deep-reading
5. **Survey 内容的取舍**：survey.md 覆盖了 35 篇论文，但目标库只需沉淀已深度阅读的部分；未深度阅读论文的摘要信息是否写入 Knowledge 需要用户决定
6. **已下载但未深度阅读的 PDF**：11 篇 PDF 中有 6 篇尚未深度阅读（oxe, diffusion-policy, act, fast, libero, benchmark-audit），它们可在后续 deep-reading 后逐步沉淀

---

## 六、建议执行顺序

1. **Phase 2**：创建 5 篇 Source Notes（预计 5 个文件）
2. **Phase 3 第一批**：创建 15 条 Atomic（最独立的单概念知识）
3. **Phase 3 第二批**：创建 12 条 Claim、8 条 Question（需要更多综合判断）
4. **Phase 3 第三批**：创建 4 条 Wiki（跨论文综合，依赖已有的 Atomic 和 Claim）
5. **Phase 4**：创建 MOC - VLA 并整合所有链接
