# `[对齐]` 工作流

精确触发 `[对齐]` 后，对入口、MSA、references、README 和项目文档做全局检查。

## 信息分流

- 每轮必须执行的行为、红线和路由：`entrypoints/AGENTS.md`
- 当前协作事实和资料源：`MSA/Memory.md`
- 稳定思维模式：`MSA/Soul.md`
- 协作关系和分歧处理：`MSA/Agent.md`
- 低频领域细则：对应 `references/`
- 完整可复用流程：对应 Skill
- 一次性过程、流水和未验证信息：不写入

## 更新

- 优先改写和删除过期内容，不只追加。
- Memory 不复制履历和动态数字，Soul 不写临时观察，Agent 不复制运行规则。
- 每个 reference 必须有入口路由，已安装 Skill 不保留第二份 prompt。

## Gotchas

Gotcha 必须写清发生、原因和以后怎么做，最多保留 3 条。严重事故可以暂时与稳定规则并存，但必须有退出条件；原因消失后删除，历史由 Git 保存。

## 验证和提交

运行实例校验器，确认没有覆盖已有修改。只有获得授权时才按文件暂存、检查 staged diff 并创建本地 commit；不自动 push、tag 或 release。
