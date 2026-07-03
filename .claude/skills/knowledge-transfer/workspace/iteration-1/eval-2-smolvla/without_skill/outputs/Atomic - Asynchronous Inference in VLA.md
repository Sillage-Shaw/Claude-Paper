---
created: 2026-07-03
status: working
type: atomic
---

# Asynchronous Inference in VLA

## 定义

Asynchronous Inference（异步推理）是一种将策略模型的推理过程与机器人动作执行过程解耦的系统架构。在传统同步模式下，机器人"观测-推理-执行-等待"串行进行；在异步模式下，推理在独立线程/进程中运行，将预测的动作块放入共享队列，机器人执行端从队列消费动作。

## 核心机制

SmolVLA 的异步推理架构：

1. **PolicyServer**：运行模型推理，预测 action chunk 放入队列
2. **RobotClient**：从动作队列消费动作，逐步执行控制命令
3. **队列阈值 g**：当队列中的剩余动作低于阈值 g（0 < g < 1，相对于 chunk size），触发新的推理请求
4. **Similarity Filter**：基于 joint-space 相似度过滤近重复观测，避免浪费推理资源

## 关键参数

- g = 0：推理完全异步，预测完成立即放入队列（最激进）
- g = 1：几乎等同于同步模式，队列耗尽才触发推理
- g in (0, 1)：实用折中，平衡响应性和计算资源

## 优势与局限

优势：
- 提速约 30%（SmolVLA 实验中 9.7s vs 13.75s）
- 推理延迟被动作执行时间隐藏

局限：
- 长周期任务上成功率可能下降（Sorting：async 50% vs sync 70%）
- 对推理延迟波动敏感
- 队列调度失效可能导致机器人停滞

## 来源与依据

- [[Paper - 2025 - SmolVLA]] Section 3.5, Figure 5
- SmolVLA deep-reading Section 3.3, 4.2
