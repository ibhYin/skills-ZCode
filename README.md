# ZCode Skills

本仓库即 ZCode 的技能发现目录 `~/.zcode/skills/`，用于版本管理本机的 ZCode skills。

当前内容：[superpowers-zh](https://github.com/jnMetaCode/superpowers-zh) v1.8.0 的 21 个 skills（15 个翻译 + 4 个中文原创 + 2 个上游历史保留），并已做 ZCode 本地适配。

## ZCode 本地适配（相对官方 superpowers-zh 的改动）

- `requesting-code-review/SKILL.md`、`requesting-code-review/code-reviewer.md`：分派审查员 `Task tool` → ZCode 的 `Agent` 工具
- `dispatching-parallel-agents/SKILL.md`：并行分派示例 `Task(...)` → `Agent(...)`
- `using-superpowers/SKILL.md`：平台适配列表新增 ZCode 条目
- `using-superpowers/references/zcode-tools.md`：**新增**，ZCode 工具差异说明（Agent 并行分派、SendMessage 续聊、EnterPlanMode、visual-judge 等）
- `workflow-runner/SKILL.md`：描述中支持平台加入 ZCode

## 升级注意

重跑 `npx superpowers-zh --global --tool zcode` 会用官方版本**覆盖**上述适配：

1. 覆盖后先 `git diff` 审查改动
2. 满意 → `git add -A && git commit`；不满意 → `git restore .` 回滚
3. 重装后确认 `using-superpowers/references/zcode-tools.md` 是否还在（新文件官方包里没有，不会被覆盖，但也可能被整体清空后重建——必要时从 git 历史找回：`git checkout HEAD -- <path>`）

## 恢复

误删或改坏某个 skill：

```bash
git restore <skill>/           # 回滚未提交的改动
git checkout HEAD -- <skill>/  # 恢复到最近一次提交
git log --oneline              # 查看历史
```
