# Moqi（默契）：WorkBuddy 适配器

跨 agent 共享规则的唯一真实源是：

`{{MOQI_ROOT}}/entrypoints/AGENTS.md`

每次会话先读取并遵循该文件，再按其中要求读取 MSA（Memory / Soul / Agent）。共享规则只修改 `AGENTS.md`，不在本文件复制。

## WorkBuddy 差异

- 加载方式：**身份层常驻载体**（如 `{{WORKBUDDY_IDENTITY_PATH}}`）里的常驻指令要求每次会话读取主入口与 MSA；WorkBuddy 没有全局 symlink 入口，加载入口在常驻载体。
- 载体选择有一条实测结论：能每次会话**完整注入**的载体才可靠。体积过大、注入时会被截断的文件不适合承担规则或红线副本——一旦被截断，规则等于没写。
- 指令要求每次会话读取主入口 + MSA 三件套；references 按 `AGENTS.md` 的条件路由加载；`[对齐]` 精确触发时再读 `ALIGNMENT.md`。
- Skills 走产品内机制，不接 `{{AGENTS_SKILLS_PATH}}` 的 junction。
- 如需把「WorkBuddy 也读 Moqi」写成仓库内公开事实，可在 `entrypoints/` 放本薄适配器，供校验器登记保护（见 `references/adapter.md` 的校验兼容一节）。
