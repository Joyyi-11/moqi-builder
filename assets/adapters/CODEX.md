# Moqi（默契）：Codex 适配器

跨 agent 共享规则的唯一真实源是：

`{{MOQI_ROOT}}/entrypoints/AGENTS.md`

每次会话先读取并遵循该文件，再按其中要求读取 MSA。共享规则只修改 `AGENTS.md`，不在本文件复制。

## Codex 差异

- 加载方式：全局入口 `{{CODEX_ENTRY_PATH}}`（如 `~/.codex/AGENTS.md`）通过 symlink 或已验证的同步副本指向主入口。
- 无法创建 symlink 时用副本兜底：让校验器比对副本与真实源的哈希，一致才算通过，避免副本静默漂移。
- Skills 入口：`{{AGENTS_SKILLS_PATH}}`，经 junction 指向统一技能目录。
- Codex 读取项目内离目标文件最近的 `AGENTS.md`，其规则管辖所在目录和子目录；项目级规则写入项目 `AGENTS.md`。
