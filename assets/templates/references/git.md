# Git 规则

- 进入仓库先查看状态，区分已有修改、本轮修改、未跟踪文件和生成物。
- 未经确认不删除、回滚、覆盖或擅自暂存已有修改。
- status、diff、log、show 等只读操作可直接执行。
- push、reset、restore、clean、rebase、改历史、tag 和 release 必须先确认。
- 只暂存本轮获准文件，不使用无边界的 `git add .`。
- 提交前检查 staged diff，提交后报告剩余状态。
