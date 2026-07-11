# Moqi（默契）Builder

**让 AI 不只记得你，而是逐步学会怎样与你协作。**

Moqi（默契）是一套可移植、可验证、可持续更新的人机协作系统。它通过三层架构和一个对齐控制平面，让 AI 获得必要的用户上下文、稳定的协作关系和明确的执行边界。

`moqi-builder` 是 Moqi 的搭建与维护 Skill，支持从零创建，也支持从 MSA / MS&A 旧系统升级到 3.0。

## 解决的问题

- 每次新对话都要重新介绍背景。
- AI 的答案正确，却不符合用户的判断方式和协作偏好。
- 规则持续增加，最后彼此重复、冲突或失效。
- Claude Code、Codex 等平台各有入口，内容难以保持一致。
- 个人信息、项目规则、工具流程混在一起，既浪费上下文又难以复用。

## Moqi 3.0 架构

```text
entrypoints/       第一层：运行入口
MSA/               第二层：Memory / Soul / Agent
references/        第三层：按需执行细则
ALIGNMENT.md       对齐控制平面
Skills             外部能力平面
```

Moqi 保留 MSA 作为核心认知模型：

| 文件 | 回答的问题 |
|:-----|:-----------|
| Memory | AI 当前必须知道哪些事实，才会采取不同的行动？ |
| Soul | 用户有哪些经过反复验证的思维和判断模式？ |
| Agent | 用户希望与 AI 建立怎样的协作关系？ |

入口负责每轮必须执行的规则，references 负责低频细则，完整工作流进入 Skills，ALIGNMENT 负责持续减法和系统验证。

## 五种模式

- `build`：从零搭建 Moqi。
- `upgrade`：从 MSA 1.0 / 2.0 或其他个人规则系统升级。
- `update`：更新事实、模式、关系或运行规则。
- `diagnose`：检查重复、越界、过期和失效路由。
- `align`：完成全局对齐、验证和范围明确的提交。

## 安装

```bash
npx skills add Joyyi-11/moqi-builder -g
```

安装后可以说：

- “帮我搭建一套 Moqi。”
- “把我的 MSA 升级到 Moqi 3.0。”
- “诊断一下我的 AGENTS、Memory、Soul 和 Agent。”
- “更新我的 Moqi。”
- “[对齐]”

## 仓库结构

```text
SKILL.md                模式路由和核心边界
references/             各模式的方法细则
assets/templates/       生成 Moqi 实例的通用模板
scripts/verify_system.py  跨平台结构校验
agents/openai.yaml      Skill 界面元数据
```

## 版本

Moqi 3.0 从原 MS&A Builder 逐步演化而来，完整保留原仓库 Git 历史。MSA 不再代表整个系统，而是 Moqi 的核心认知层。

## 作者

连漪（Joyyi-11）
