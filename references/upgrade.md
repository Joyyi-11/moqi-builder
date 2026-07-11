# Upgrade 模式

## 目标

把已有 MSA、MS&A、CLAUDE.md 规则集或个人 AI 说明书升级到 Moqi 3.0，同时保留有效信息和 Git 历史。

## 一、建立基线

1. 读取全部入口、Memory、Soul、Agent、references、prompt、README 和对齐文件。
2. 记录 Git 状态、symlink / junction 和全局入口真实目标。
3. 列出旧系统的真实源、重复副本、过期路径和平台耦合。

## 二、信息迁移

| 旧内容 | Moqi 3.0 位置 |
|:-------|:--------------|
| 每轮必须执行的共享规则 | `entrypoints/AGENTS.md` |
| Claude Code 独有差异 | `entrypoints/CLAUDE.md` |
| 当前有用事实和资料源 | `MSA/Memory.md` |
| 稳定思维模式 | `MSA/Soul.md` |
| 协作关系和分歧处理 | `MSA/Agent.md` |
| 代码、Git、调试等低频细则 | 根目录 `references/` |
| 对齐流程 | 根目录 `ALIGNMENT.md` |
| 完整 prompt 工作流 | 对应 Skill |
| 履历和易过期数据 | 外部真实源 |

删除已被稳定规则吸收的旧 Gotchas；严重且反复的事故可以临时保留，但必须有退出条件。

## 三、安全迁移

1. 复制旧实例到新目录，不直接重命名或删除。
2. 在新目录完成结构调整、路由更新和内容去重。
3. 运行结构校验并核对关键文件。
4. 切换全局入口后，从 Codex 和 Claude Code 分别验证加载。
5. 报告新实例正常状态，等待用户确认后再删除旧目录。

## 四、兼容处理

- 识别旧触发词“搭建 MSA”“更新 MSA”“对齐 MSA”。
- README 首次出现写“Moqi（默契）”，后文简称 Moqi。
- MSA 名称继续用于核心三文件，不再代表完整系统。
- 版本用 Git tag / release 管理，不在 `SKILL.md` frontmatter 写自定义 `version`。
