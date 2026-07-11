# Moqi（默契）：Claude Code 适配器

跨 agent 共享规则的唯一真实源是：

`{{MOQI_ROOT}}/entrypoints/AGENTS.md`

每次会话先读取并遵循该文件，再按其中要求读取 MSA。共享规则只修改 `AGENTS.md`，不在本文件复制。

## Claude Code 差异

- 全局入口：`{{CLAUDE_ENTRY_PATH}}`
- Skills 入口：`{{CLAUDE_SKILLS_PATH}}`
- Claude Code 项目专属规则写入项目 `CLAUDE.md`；跨 agent 项目规则写入项目 `AGENTS.md`。
