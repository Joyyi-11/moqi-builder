---
name: moqi-builder
description: 搭建、升级、更新、诊断和对齐 Moqi（默契）人机协作系统。Moqi 使用 entrypoints、Memory/Soul/Agent、按需 references 和 ALIGNMENT 控制平面，让 AI 持续理解用户并遵守稳定协作边界。Use when the user asks to搭建人机协作系统、让 AI 了解自己、配置 AGENTS.md/CLAUDE.md、创建或更新 Memory/Soul/Agent、诊断规则重复和过期、执行对齐，或从 MSA、MS&A、msa-builder 升级到 Moqi 3.0。
---

# Moqi（默契）Builder

Moqi（默契）是一套让人与 AI 建立共同上下文、协作边界和持续默契的协作系统。本 Skill 负责创建和维护 Moqi 实例，不把某个用户的个人信息带入通用模板。

## 选择模式

| 用户意图 | 模式 | 必读文件 |
|:---------|:-----|:---------|
| 从零搭建、建立 AI 协作系统 | `build` | `references/build.md` |
| 从 MSA / MS&A / 旧入口升级 | `upgrade` | `references/upgrade.md` |
| 更新事实、模式、关系或规则 | `update` | `references/update.md` |
| 检查重复、过期、越界或失效路由 | `diagnose` | `references/diagnose.md` |
| 全局同步、整理并形成闭环 | `align` | `references/alignment.md` |

架构判断或文件归属不清时，同时读取 `references/architecture.md`。

## 核心架构

```text
entrypoints/       第一层：每轮必须执行的运行规则
MSA/               第二层：Memory / Soul / Agent 核心上下文
references/        第三层：按任务加载的执行细则
ALIGNMENT.md       对齐控制平面
Skills             外部能力平面，不复制进实例
```

模板位于 `assets/templates/`。先理解用户和现有环境，再复制并替换占位符；不要未经判断整目录覆盖。

## 不可破坏的边界

- `AGENTS.md` 是跨 agent 共享规则的唯一真实源；其他平台文件只做薄适配。
- Memory 只保存会改变当前协作判断的事实和资料源，不保存完整履历或易过期数据。
- Soul 只保存有事实支撑、更新缓慢的思维模式。
- Agent 只保存协作关系、纠错态度和分歧处理，不复制运行规则。
- references 只保存低频领域细则；完整可复用流程进入对应 Skill。
- `ALIGNMENT.md` 负责信息分流、去重、Gotchas 生命周期、验证和提交边界。
- 同一规则只有一个真实源。允许入口摘要和领域细则形成层级，不逐句复制。

## 通用执行流程

1. 读取现有入口、MSA、references、README、对齐文件和工作区状态。
2. 用 AMV 确认起点、目标、成功标准和本轮改动范围。
3. 选择一个主模式；确有依赖时再组合其他模式，不同时加载全部 references。
4. 先提出文件清单和迁移方案；结构改动获得确认后再执行。
5. 使用 `assets/templates/` 创建缺失文件，按用户情况改写内容。
6. 运行 `scripts/verify_system.py <instance-root>`，修复所有 error。
7. 汇报改动、验证结果、未确认信息和旧路径处置状态。

## 安全规则

- 迁移实例时先复制、验证，再切换入口；旧源等用户确认新实例正常后单独删除。
- 不把用户的完整个人资料写进公开模板、示例、日志或提交。
- 不覆盖来源不明的现有文件；发现脏工作区先区分已有修改和本轮修改。
- 不默认 push、打 tag、创建 release 或修改远程仓库配置。

## 向后兼容

识别“MSA”“MS&A”“msa-builder”“三文件系统”等旧称。升级时保留 Memory、Soul、Agent 中仍有价值的信息，但按 Moqi 3.0 边界重新分流，不机械搬运旧结构。
