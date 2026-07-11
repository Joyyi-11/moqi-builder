---
name: moqi-builder
description: 搭建、更新、诊断和对齐 Moqi（默契）人机协作系统。通过对话提炼必要的协作事实、稳定思维模式、协作关系和运行边界，并组织为 AGENTS.md、Memory.md、Soul.md、Agent.md、按需 references 和 ALIGNMENT.md。Use when the user asks to搭建个人 AI 协作系统、让 AI 持续了解自己、配置或整理 AGENTS.md/CLAUDE.md、创建或更新 Memory/Soul/Agent、检查规则重复和过期，或执行系统对齐。
---

# Moqi（默契）Builder

Moqi（默契）是一套让人与 AI 建立共同上下文、协作边界和持续默契的协作系统。本 Skill 负责通过对话搭建和维护一个可运行、可验证、能持续减法的 Moqi 实例。

## 选择模式

| 用户意图 | 模式 | 必读文件 |
|:---------|:-----|:---------|
| 从零搭建，或整理已有协作系统 | `build` | `references/build.md` |
| 更新事实、模式、关系或规则 | `update` | `references/update.md` |
| 检查重复、过期、越界或失效路由 | `diagnose` | `references/diagnose.md` |
| 全局同步、清理并形成闭环 | `align` | `references/alignment.md` |

文件归属或架构判断不清时，同时读取 `references/architecture.md`。

## 核心架构

```text
entrypoints/       第一层：每轮必须执行的运行规则
MSA/               第二层：Memory.md / Soul.md / Agent.md
references/        第三层：有明确触发条件的按需细则
ALIGNMENT.md       对齐控制平面
```

## 不可破坏的边界

- `AGENTS.md` 是跨 agent 共享运行规则的唯一真实源；平台适配器只记录加载方式和平台差异。
- `Memory.md` 只保存会改变当前协作判断的事实、优先级和资料真实源。
- `Soul.md` 只保存有多个真实场景支撑、更新缓慢的思维模式。
- `Agent.md` 只保存协作关系、主动程度、纠错方式和分歧处理。
- `references/*.md` 只在存在明确任务类型和加载路由时创建。
- `ALIGNMENT.md` 负责信息分流、去重、Gotchas 生命周期、验证和提交边界。
- 同一规则只在一个位置完整表达；入口摘要和领域细则可以形成层级，但不能逐句复制。

## 通用执行流程

1. 读取目标环境、现有文件、入口关系和工作区状态。
2. 用 AMV 对齐理解：A 是当前状态与已有条件，V 是目标与成功标准，M 是实现路径。
3. 选择一个主模式，只加载对应 reference；确有架构疑问时再加载 `architecture.md`。
4. 先说明将修改的文件、链接和验证方式；结构性或高风险操作获得确认后再执行。
5. 通过对话形成内容，不把模板占位符直接当作用户答案。
6. 运行 `scripts/verify_system.py <instance-root>`，修复全部 error。
7. 汇报实际改动、验证结果、未确认判断和旧路径状态。

## 安全规则

- 迁移时先复制、验证和切换入口；旧源在用户确认新实例正常后再单独删除。
- 不覆盖来源不明的文件；发现未提交内容先区分已有修改和本轮修改。
- 不默认提交、push、打 tag、创建 release 或修改远程仓库配置。
- 未经用户确认，不把推测写成稳定事实或思维模式。
