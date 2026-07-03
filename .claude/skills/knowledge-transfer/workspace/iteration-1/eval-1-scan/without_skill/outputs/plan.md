# Claude-Paper -> Obsidian 知识库沉淀计划

> 生成日期：2026-07-03
> 源库：D:\Development\Claude-Paper
> 目标库：D:\Obsidian
> 遵循规范：目标库 CLAUDE.md + 99-System 规则体系

---

## 一、总体策略

### 1.1 沉淀原则

遵循 Obsidian 知识库的信息流转路径：

```text
40 Sources (Source 笔记) → 30 Knowledge (Atomic/Claim/Question/Wiki/MOC)
```

每一步：
1. 先为每篇论文创建 Source 笔记（回答"这篇论文说了什么"）
2. 从 Source + deep-reading.md 中提炼 Knowledge 笔记
3. 创建领域 MOC 导航页
4. 建立双向链接

### 1.2 阶段划分

```text
Phase 1: Source 笔记 (8 篇)     — 为所有已深度加工的论文建立文献卡片
Phase 2: Knowledge 沉淀           — 提炼 Atomic、Claim、Question、Wiki
Phase 3: MOC 构建                 — 建立领域入口和导航
Phase 4: 补充 PDF (5 篇)          — 为仅下载未加工的论文建立 Source 笔记
```

---

## 二、Phase 1: Source 笔记创建（优先级：最高）

### 2.1 已深度加工的 5 篇论文

每个 Source 笔记包含：基本信息、一句话总结、核心问题、主要内容、主要结论、关键证据、局限性、可沉淀知识候选列表。

| # | 论文 | 源 deep-reading.md | 目标 Source 笔记路径 | 元数据 |
|---|------|-------------------|---------------------|--------|
| 1 | RT-2 (2023) | note/papers/rt2/deep-reading.md | `40 Sources/Literature/Paper - 2023 - RT-2.md` | type: source, status: ready |
| 2 | pi0 (2024) | note/papers/pi0/deep-reading.md | `40 Sources/Literature/Paper - 2024 - pi0.md` | type: source, status: ready |
| 3 | pi0.5 (2025) | note/papers/pi0.5/deep-reading.md | `40 Sources/Literature/Paper - 2025 - pi0.5.md` | type: source, status: ready |
| 4 | SmolVLA (2025) | note/papers/smolvla/deep-reading.md | `40 Sources/Literature/Paper - 2025 - SmolVLA.md` | type: source, status: ready |
| 5 | Shao et al. VLA Survey (2025) | note/papers/shao2025-vla-survey/deep-reading.md | `40 Sources/Literature/Paper - 2025 - Large VLM-based VLA Survey.md` | type: source, status: ready |

### 2.2 领域调研 Source

领域调研 survey.md 本身就是对 35+ 篇论文的综合，可作为一篇特殊的 Source 笔记或直接进入 Wiki。

| # | 内容 | 源文件 | 目标路径 | 说明 |
|---|------|--------|---------|------|
| 6 | VLA 领域调研 | note/fields/vla/survey.md | `40 Sources/Literature/Paper - 2026 - VLA Field Survey.md` 或直接进入 Wiki | 作为 Source 可回链到所有引用论文 |

---

## 三、Phase 2: Knowledge 沉淀（优先级：高）

### 3.1 Atomic（原子知识点）

从 5 篇论文的 deep-reading 中可提炼出以下独立概念。每个 Atomic 回答"这个知识点是什么意思？"

| # | Atomic 标题 | 来源 | 内容说明 |
|---|------------|------|---------|
| 1 | Vision-Language-Action Model (VLA) | RT-2 deep-reading | VLA 的概念定义、起源、核心范式 |
| 2 | Action Tokenization | RT-2 + SmolVLA | 动作离散化方法（256 bins、FAST、DCT） |
| 3 | Co-Fine-Tuning | RT-2 deep-reading | 在 VLM 原始数据 + 机器人数据上同时微调 |
| 4 | Flow Matching | pi0 + pi0.5 + SmolVLA | Flow Matching 用于动作生成的原理 |
| 5 | Action Expert (MoE) | pi0 + pi0.5 | 双系统中独立于 VLM 权重的动作模块 |
| 6 | Action Chunking | pi0 + SmolVLA | 一次预测未来多步动作序列（H=50） |
| 7 | Cross-Embodiment Training | pi0 + pi0.5 survey | 跨多种机器人形态的联合训练 |
| 8 | Pre-training / Post-training Paradigm | pi0 + pi0.5 | 机器人基础模型的两阶段训练范式 |
| 9 | Co-Training (Heterogeneous) | pi0.5 deep-reading | 五类异构数据源的联合训练 |
| 10 | Hierarchical (双层次) Inference | pi0.5 deep-reading | 高层子任务预测 + 低层动作生成 |
| 11 | Asynchronous Inference | SmolVLA deep-reading | 感知/动作执行解耦的推理栈 |
| 12 | Layer Skipping | SmolVLA deep-reading | VLM 跳层加速推理 |
| 13 | Monolithic vs Hierarchical VLA | Shao survey deep-reading | 一体式 vs 分层式 VLA 架构分类 |
| 14 | Benchmark Audit (失效模式) | survey.md + benchmark-audit.pdf 提及 | LIBERO/CALVIN 的四种评估失效 |

### 3.2 Claim（可验证判断）

从 deep-reading 的"核心假设"、"局限"、"最终评价"和"实验可信度判断"中提炼。

| # | Claim 标题 | 来源 | 证据强度 |
|---|-----------|------|---------|
| 1 | Claim - Co-fine-tuning 优于仅用机器人数据微调 VLA | RT-2 deep-reading Sec 4.2.3 | 强（消融实验，6k 评估） |
| 2 | Claim - 自回归离散化 VLA 在灵巧高频任务上失败 | pi0 deep-reading Sec 2.2 | 强（pi0 实验对比 OpenVLA） |
| 3 | Claim - 异构 co-training 对 VLA 开放世界泛化至关重要 | pi0.5 deep-reading Sec 4.2 Exp 3 | 强（消融实验，5 类数据源逐一移除） |
| 4 | Claim - VLA 的 Scaling 存在边际收益递减 | survey.md (Sarowar & Kim 2026) | 中（来自一篇 preprint，需验证） |
| 5 | Claim - LIBERO 和 CALVIN 可能无法有效衡量真实 VLA 进展 | survey.md + benchmark-audit | 强（Benchmark Audit 2026 系统性审计） |
| 6 | Claim - VLA 模型的前半层特征对机器人控制更有效 | SmolVLA deep-reading Table 8 | 强（消融实验，N=16 vs N=32 性能接近） |
| 7 | Claim - Flow Matching 在动作建模上优于回归 L1 Loss | SmolVLA deep-reading Table 10 | 强（消融实验，Long-horizon 差距大） |
| 8 | Claim - VLA 的物理技能局限于训练数据的技能分布 | RT-2 deep-reading Sec 5.2 | 强（RT-2 Limitations 明确陈述） |

### 3.3 Question（未解决但值得追踪的问题）

从 deep-reading 的"没有解决什么"、"开放问题"和 survey 的"开放问题"中提炼。

| # | Question 标题 | 来源 |
|---|--------------|------|
| 1 | Question - VLA 如何实现跨机器人平台的低成本泛化 | SmolVLA limitations + survey 开放问题 |
| 2 | Question - 什么类型的 VLM 层特征对机器人控制最重要 | SmolVLA deep-reading 7.3 |
| 3 | Question - VLA 的评估体系应如何重新设计以克服当前 benchmark 失效 | survey + benchmark-audit |
| 4 | Question - VLA 能否通过 Scaling 解决所有任务而不需要 Hierarchical 架构 | Shao survey deep-reading 5.4 |
| 5 | Question - VLA 的安全性如何形式化保证 | pi0.5 + survey 开放问题 |
| 6 | Question - 社区数据是否可以替代工业数据用于 VLA 预训练 | SmolVLA 核心主张 |

### 3.4 Wiki（主题综述）

| # | Wiki 标题 | 来源 | 内容说明 |
|---|----------|------|---------|
| 1 | VLA 模型架构综述 | survey + 5 篇 deep-reading | 整合 Monolithic vs Hierarchical、自回归 vs 扩散 vs Flow Matching |
| 2 | VLA 训练范式演化 | RT-2 + pi0 + pi0.5 + SmolVLA deep-reading | Co-fine-tuning → Pre/Post-training → Co-Training → Community-data pretraining |
| 3 | VLA 动作生成方法对比 | 多篇论文 | 自回归离散化 vs 扩散模型 vs Flow Matching vs FAST |
| 4 | VLA 评估体系 | survey + benchmark-audit | LIBERO/CALVIN/SimplerEnv 等的优劣分析 |

---

## 四、Phase 3: MOC 构建（优先级：中）

### 4.1 VLA 领域 MOC

路径：`30 Knowledge/MOC/MOC - VLA.md`

内容：
- 链接到所有 VLA 相关的 Source 笔记（5 篇已深度加工 + 5 篇 PDF）
- 链接到所有 VLA 相关的 Atomic、Claim、Question、Wiki
- 链接到阅读路线图（来自 reading-roadmap.md）
- 链接到论文速查表（来自 paper-table.md）
- 组织为 Phase 1-4 的推荐阅读路径

### 4.2 可能的次级 MOC

| MOC | 条件 | 内容 |
|-----|------|------|
| MOC - VLA 模型架构 | 当 Atomic 数量 > 10 时创建 | 按架构分类组织 |
| MOC - VLA 训练方法 | 当相关 Claim > 5 时创建 | 按训练范式组织 |

---

## 五、Phase 4: 未加工 PDF 的 Source 笔记（优先级：低）

5 篇仅有 PDF 无 note 目录的论文，先建立基础 Source 笔记（基于 survey.md 中的描述和 PDF 元数据），后续补充深度阅读。

| # | 论文 | PDF 路径 | 目标 Source 笔记 |
|---|------|---------|-----------------|
| 1 | ACT (2023) | papers/vla/act.pdf | `40 Sources/Literature/Paper - 2023 - ACT.md` |
| 2 | Diffusion Policy (2023) | papers/vla/diffusion-policy.pdf | `40 Sources/Literature/Paper - 2023 - Diffusion Policy.md` |
| 3 | FAST (2025) | papers/vla/fast.pdf | `40 Sources/Literature/Paper - 2025 - FAST.md` |
| 4 | Open X-Embodiment (2023) | papers/vla/oxe.pdf | `40 Sources/Literature/Paper - 2023 - Open X-Embodiment.md` |
| 5 | Benchmark Audit (2026) | papers/vla/benchmark-audit.pdf | `40 Sources/Literature/Paper - 2026 - Benchmark Audit.md` |
| 6 | LIBERO (2023) | papers/vla/libero.pdf | `40 Sources/Literature/Paper - 2023 - LIBERO.md` |

---

## 六、文件清单汇总

### 6.1 将创建的文件

**Source 笔记 (6 篇)**：
```
40 Sources/Literature/Paper - 2023 - RT-2.md
40 Sources/Literature/Paper - 2024 - pi0.md
40 Sources/Literature/Paper - 2025 - pi0.5.md
40 Sources/Literature/Paper - 2025 - SmolVLA.md
40 Sources/Literature/Paper - 2025 - Large VLM-based VLA Survey.md
40 Sources/Literature/Paper - 2026 - VLA Field Survey.md
```

**Atomic (14 篇)**：
```
30 Knowledge/Atomic/Vision-Language-Action Model (VLA).md
30 Knowledge/Atomic/Action Tokenization.md
30 Knowledge/Atomic/Co-Fine-Tuning.md
30 Knowledge/Atomic/Flow Matching.md
30 Knowledge/Atomic/Action Expert (MoE).md
30 Knowledge/Atomic/Action Chunking.md
30 Knowledge/Atomic/Cross-Embodiment Training.md
30 Knowledge/Atomic/Pre-training Post-training Paradigm.md
30 Knowledge/Atomic/Heterogeneous Co-Training.md
30 Knowledge/Atomic/Hierarchical Inference (VLA).md
30 Knowledge/Atomic/Asynchronous Inference.md
30 Knowledge/Atomic/Layer Skipping.md
30 Knowledge/Atomic/Monolithic vs Hierarchical VLA.md
30 Knowledge/Atomic/Benchmark Audit Failure Modes.md
```

**Claim (8 篇)**：
```
30 Knowledge/Claim/Claim - Co-fine-tuning 优于仅用机器人数据微调 VLA.md
30 Knowledge/Claim/Claim - 自回归离散化 VLA 在灵巧高频任务上失败.md
30 Knowledge/Claim/Claim - 异构 co-training 对 VLA 开放世界泛化至关重要.md
30 Knowledge/Claim/Claim - VLA Scaling 存在边际收益递减.md
30 Knowledge/Claim/Claim - LIBERO 和 CALVIN 可能无法有效衡量真实 VLA 进展.md
30 Knowledge/Claim/Claim - VLA 模型前半层特征对机器人控制更有效.md
30 Knowledge/Claim/Claim - Flow Matching 在动作建模上优于回归 L1 Loss.md
30 Knowledge/Claim/Claim - VLA 物理技能局限于训练数据的技能分布.md
```

**Question (6 篇)**：
```
30 Knowledge/Question/Question - VLA 如何实现跨机器人平台低成本泛化.md
30 Knowledge/Question/Question - 什么类型的 VLM 层特征对机器人控制最重要.md
30 Knowledge/Question/Question - VLA 评估体系应如何重新设计.md
30 Knowledge/Question/Question - VLA 能否通过 Scaling 解决所有任务.md
30 Knowledge/Question/Question - VLA 安全性如何形式化保证.md
30 Knowledge/Question/Question - 社区数据能否替代工业数据用于 VLA 预训练.md
```

**Wiki (4 篇)**：
```
30 Knowledge/Wiki/VLA 模型架构综述.md
30 Knowledge/Wiki/VLA 训练范式演化.md
30 Knowledge/Wiki/VLA 动作生成方法对比.md
30 Knowledge/Wiki/VLA 评估体系.md
```

**MOC (1 篇)**：
```
30 Knowledge/MOC/MOC - VLA.md
```

**总计：约 39 个新文件**

### 6.2 可后续补充的 Source 笔记（6 篇）

Phase 4 中的 6 篇未加工 PDF，视需要补充。

---

## 七、执行顺序建议

```text
Step 1: 创建 6 篇 Source 笔记（Phase 1）
         → 每篇从对应的 deep-reading.md 中提取基本信息 +
           一句话总结 + 核心内容 + 可沉淀候选列表
         → status: ready（因为 deep-reading 已经完成）

Step 2: 创建 1 篇 VLA MOC（Phase 3 提前）
         → 先建立骨架，后续逐步填充链接
         → status: working

Step 3: 创建 14 篇 Atomic（Phase 2）
         → 从 deep-reading 和 terminology.md 中提炼
         → status: working → ready

Step 4: 创建 8 篇 Claim + 6 篇 Question（Phase 2）
         → 从 deep-reading 的假设/局限/评价中提炼
         → status: working → ready

Step 5: 创建 4 篇 Wiki（Phase 2）
         → 整合多个 Atomic + Claim，形成系统性理解
         → status: working → ready

Step 6: 更新 MOC，添加所有双向链接
         → status: ready

Step 7 (可选): 为 6 篇未加工 PDF 创建 Source 笔记（Phase 4）
```

---

## 八、不沉淀的内容

以下内容不适合进入 Obsidian 知识库：

| 内容 | 原因 |
|------|------|
| 论文 PDF 文件本身 | 应保留在 Claude-Paper/papers/，Obsidian 中只做 Source 笔记链接 |
| 完整翻译 (translation.md) | 翻译是过程产物，Source 笔记中只需提取核心信息；但若用户需要可保留为 Source 的附录引用 |
| translation-notes.md | 翻译过程记录，属于工具性笔记，非可复用知识 |
| prompts/ 目录 | 工具配置，非知识内容 |
| INSTALL.md | 工具安装说明，非知识内容 |
| CLAUDE.md / README.md | 项目规则，非知识内容 |
| 论文原文 .txt 文件 | 提取文本的中间产物 |
| terminology.md 完整复制 | 术语表中的术语应拆分为独立 Atomic，而非整表迁移 |

---

## 九、风险和注意事项

1. **重复检查**：创建每个文件前，先在 Obsidian 中搜索是否已有同名或近似主题笔记
2. **元数据一致**：所有新笔记只用 `created`、`status`、`type` 三个元属性
3. **双向链接**：Source 链接到 Knowledge，Knowledge 回链到 Source
4. **不要过度创建**：如果某个 Claim 证据不足，先保持 status: review；如果某个 Atomic 内容太少，可以先并入 Wiki
5. **MOC 不写长文**：MOC 只做导航和链接，不写长篇知识正文
6. **引用源库路径**：在 Source 笔记中标注源库的 note/ 路径，方便追溯原文
