# AgriMind: An Optimized Logic Layer for FreshAgent Alpha Ⅱ

> **Note:** This project is a **logic-layer refactor** based on the open-source [FreshAgent Alpha II](https://github.com/CyanCQC/FreshAgent-Alpha-II) architecture. It focuses on optimizing **Task Planning** and **Prompt Engineering** for better intent understanding.

## Motivation

在主导 FreshAgent 项目商业落地的过程中，我发现原始的基础模型在处理用户非线性、多步骤的复杂需求时，往往表现出任务规划僵化的问题。

作为项目负责人之一，为了验证更灵活的调度逻辑，我基于原有的底层架构（视觉/数据库模块），**独立重构了核心 Agent 的决策层代码 (`CoreAgent` Class)**。本项目即为该优化实验的成果展示。

## My Contributions

本项目主要针对 `AgriMind.py` 进行了以下核心算法改进：

1.  **Dynamic Task Scheduling (动态任务规划):**
    *   重写了 `_query_process` 和 `_dynamic_task_schedule` 函数。
    *   引入了“预分解 -> 执行 -> 动态调整”的闭环逻辑，使 Agent 能根据中间步骤的结果实时增删后续任务。

2.  **Advanced Prompt Engineering (提示词工程):**
    *   优化了 `tpl_prompt` 的结构，增加了 Supervisor（监管者）角色约束。
    *   在 System Prompt 中重新定义了工具调用的边界条件，减少了模型幻觉。

3.  **Logic-Business Alignment (业务逻辑对齐):**
    *   将商业场景中的实际需求（如成本计算、合规检查）转化为代码中的约束逻辑。

## Architecture Note

*   **Logic Layer (My Focus):** `AgriMind.py` (Core reasoning & dispatching).
*   **Infrastructure Layer (Legacy):** `DBHandler`, `FastSAM`, `GUI` (Inherited from the original team's robust implementation).
