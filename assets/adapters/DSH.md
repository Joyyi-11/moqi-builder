# Moqi（默契）：DeepSeek Harness 适配器

跨 agent 共享规则的唯一真实源是：

`{{MOQI_ROOT}}/entrypoints/AGENTS.md`

每次会话先读取并遵循该文件，再按其中要求读取 self 两个核心文件（Memory、Soul）。共享规则只修改 `AGENTS.md`，不在本文件复制。

## DeepSeek Harness 差异

- 加载方式：用户级共享入口 `{{AGENTS_HOME}}/AGENTS.md`（如 `~/.agents/AGENTS.md`），会话启动即注入。
- 项目内按目录链加载：从项目根（以 `.git` 标记）到当前工作目录，逐级读取 `AGENTS.md` / `CLAUDE.md`；同一目录内两份内容重复时只渲染一次。
- 运行中读写到更深目录后，会追加该目录的入口文件；因此把规则放在离任务最近的目录即可按需生效。
- 无文件符号链接权限时用已验证副本兜底：让校验器比对副本与真实源的哈希，一致才算通过。
