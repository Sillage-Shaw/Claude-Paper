# Knowledge Transfer: SmolVLA -- Created Files

## Summary

- **Total created**: 13 files (1 Source + 5 Atomic + 4 Claim + 2 Question + 1 MOC)
- **Total skipped (existing)**: 0
- **Source paper**: SmolVLA (arXiv:2506.01844, 2025-06-02)
- **Source path**: D:\Development\Claude-Paper\note\papers\smolvla\
- **Target vault**: D:\Obsidian

---

## Source Notes

| # | File | Path |
|---|------|------|
| 1 | Paper - 2025 - SmolVLA.md | D:\Obsidian\40-Sources\Literature\vla\ |

## Knowledge Notes

### Atomic (5)

| # | File | Path |
|---|------|------|
| 1 | Action Chunk.md | D:\Obsidian\30-Knowledge\Atomic\ |
| 2 | Flow Matching.md | D:\Obsidian\30-Knowledge\Atomic\ |
| 3 | Asynchronous Inference.md | D:\Obsidian\30-Knowledge\Atomic\ |
| 4 | Vision-Language-Action Model.md | D:\Obsidian\30-Knowledge\Atomic\ |
| 5 | Community Datasets for Robotics.md | D:\Obsidian\30-Knowledge\Atomic\ |

### Claim (4)

| # | File | Path |
|---|------|------|
| 1 | Claim - 小模型VLA在特定任务上可媲美大10倍模型.md | D:\Obsidian\30-Knowledge\Claim\ |
| 2 | Claim - 社区数据预训练可显著提升VLA下游任务性能.md | D:\Obsidian\30-Knowledge\Claim\ |
| 3 | Claim - 流匹配在VLA动作建模中优于L1回归.md | D:\Obsidian\30-Knowledge\Claim\ |
| 4 | Claim - VLM前半层特征对机器人控制任务已足够.md | D:\Obsidian\30-Knowledge\Claim\ |

### Question (2)

| # | File | Path |
|---|------|------|
| 1 | Question - VLA如何实现跨机器人平台和形态的泛化.md | D:\Obsidian\30-Knowledge\Question\ |
| 2 | Question - 社区机器人数据质量如何自动化评估与筛选.md | D:\Obsidian\30-Knowledge\Question\ |

### MOC (1)

| # | File | Path |
|---|------|------|
| 1 | MOC - VLA.md | D:\Obsidian\30-Knowledge\MOC\ |

---

## Content Extraction Map

| Knowledge Note | deep-reading Source | Evidence |
|---------------|-------------------|----------|
| Action Chunk | deep-reading §3.2, Table 12 | Chunk size n=50 optimal |
| Flow Matching | deep-reading §3.1, Table 10 | FM 80.25 vs L1 75.25 |
| Asynchronous Inference | deep-reading §3.3, §4.6, Figure 5 | 30% faster, success comparable |
| Vision-Language-Action Model | terminology, deep-reading §2.1 | VLA = VLM + Action Expert |
| Community Datasets for Robotics | deep-reading §3.2, §2.1, §2.3 | 481 datasets, 23K trajectories |
| Claim - 小模型VLA可媲美大模型 | deep-reading §4.2, Table 2/3, §3.5 | 0.45B matches 3.3B π0 |
| Claim - 社区数据预训练提升性能 | deep-reading Table 5, §3.5 | +26.6pp pretraining gain |
| Claim - Flow Matching优于回归 | deep-reading Table 10, §3.5 | 5pp avg improvement |
| Claim - VLM前半层特征足够 | deep-reading Table 8, §6.1 | N=16 vs N=32 close |
| Question - 跨平台泛化 | deep-reading §7.1, §7.3 | SO100 only pretraining |
| Question - 数据质量自动化 | deep-reading §7.3, §1.1 Q4 | Manual camera naming |

---

## Quality Notes

- All Knowledge notes set to `status: review` (AI-generated, needs human verification)
- Source note set to `status: working`
- MOC set to `status: working` (will expand as more papers are added)
- All notes use valid metadata: only `created`, `status`, `type`
- All notes use Obsidian wikilinks for internal cross-references
- No existing notes were found in target vault -- all 13 are new creations

## Next Steps

1. Review all Knowledge notes in Obsidian; verify claims against source paper
2. Promote verified notes from `status: review` to `status: ready`
3. Add more VLA papers (π0, OpenVLA, RT-2) to expand the MOC and create Wiki pages
4. Consider creating a VLA Project in `10 Projects/` if planning to research VLA
