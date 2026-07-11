# Moqi（默契）Builder

**让 AI 不只记得你，而是逐步学会怎样与你协作。**

Moqi（默契）是一套可移植、可验证、可持续更新的人机协作系统。它通过三层架构和一个对齐控制平面，让 AI 获得必要的协作上下文、稳定关系和明确边界。

`moqi-builder` 通过对话搭建、更新、诊断和对齐 Moqi 实例。

## Moqi 3.0 架构

```text
entrypoints/       第一层：运行入口
MSA/               第二层：Memory.md / Soul.md / Agent.md
references/        第三层：按需执行细则
ALIGNMENT.md       对齐控制平面
```

| 文件 | 回答的问题 |
|:-----|:-----------|
| `Memory.md` | AI 当前必须知道哪些事实，才会采取不同的行动？ |
| `Soul.md` | 用户有哪些经过反复验证的思维和判断模式？ |
| `Agent.md` | 用户希望与 AI 建立怎样的协作关系？ |

入口负责每轮必须执行的规则，references 只在存在明确任务类型时创建，`ALIGNMENT.md` 负责持续减法和系统验证。

## 四种模式

- `build`：从零搭建，或整理已有协作系统。
- `update`：更新事实、模式、关系或运行规则。
- `diagnose`：检查重复、越界、过期和失效路由。
- `align`：完成全局对齐、验证和范围明确的提交。

## 安装

```bash
npx skills add Joyyi-11/moqi-builder -g
```

安装后可以说：

- “帮我搭建一套 Moqi。”
- “整理一下我现有的 AI 协作系统。”
- “诊断一下我的 AGENTS、Memory、Soul 和 Agent。”
- “更新我的 Moqi。”
- “[对齐]”

## 仓库结构

```text
SKILL.md                  模式路由和核心边界
references/               各模式的方法细则
assets/templates/         实例的最小核心骨架
assets/adapters/          按平台选用的入口适配器
scripts/verify_system.py  跨平台结构校验
agents/openai.yaml        Codex 界面元数据
```

## 作者

连漪（Joyyi-11）
