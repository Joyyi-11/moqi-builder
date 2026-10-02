# Moqi（默契）：OpenCode 适配器

跨 agent 共享规则的唯一真实源是：

`{{MOQI_ROOT}}/entrypoints/AGENTS.md`

每次会话先读取并遵循该文件，再按其中要求读取 MSA。共享规则只修改 `AGENTS.md`，不在本文件复制。

## OpenCode 差异

- 加载方式：全局配置 `{{OPENCODE_CONFIG_PATH}}` 的 `instructions` 数组，直接列出主入口与 MSA 三文件（`AGENTS.md`、`Memory.md`、`Soul.md`、`Agent.md`），会话启动即注入全文，不需要模型主动读取。
- 该字段是启动时的静态快照：修改文件内容后重启即生效；新增文件、改名或调整路径后，必须同步更新数组并重启，否则新文件不会被注入。
- `references/` 仍按主入口的条件路由按需加载，不进 `instructions`。
- OpenCode 的项目专属规则写入项目 `AGENTS.md`。
