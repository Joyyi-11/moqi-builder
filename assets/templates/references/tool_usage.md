# Skills 使用与源码纪律

- 触发以 `SKILL.md` description 为准，不维护第二份快捷词表。
- 先匹配已安装 Skill，再搜索可安装 Skill，仍找不到才自行实现。
- 第三方 Skill 可以安装到统一入口；自建 Skill 使用独立 Git 源目录。
- 统一入口只作聚合，工具通过 symlink / junction 读取同一份源码。
- 完整工作流进入 Skill，不在 Moqi references 中复制全文。
