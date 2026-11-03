# ZCode 工具说明

ZCode（智谱 ADE）的基本词汇与基准一致：`Agent` 表示分派子智能体、`Skill` 调用技能、`TodoWrite` 管理待办。这份说明只讲与基准不同的几处。

## 并行分派

多个独立任务写在**同一个回复的多个 Agent 调用**里，它们会并发执行。长任务用 `run_in_background: true` 放到后台，完成时会收到通知——通知到达之前不要编造或臆测后台任务的结果。

## 与子智能体续聊

每个 Agent 调用会返回一个子智能体 id。需要给已分派的子智能体补充信息或追加任务时，用 `SendMessage` 续聊，它会带着原有上下文继续；不要另派一个全新的子智能体重做一遍。

## 平台内建能力

- 计划模式是内建的（`EnterPlanMode` / `ExitPlanMode`），直接用，不要自建流程。
- ZCode 自带一批领域技能（文档、表格、PDF、演示文稿、浏览器、可视化等）。它们与本套流程技能**叠加使用**：流程技能决定"怎么做"，领域技能决定"用什么载体交付"。
- pptx / docx / xlsx / pdf / 图表类交付物的视觉验收交给内建的 `visual-judge` 子智能体，不要自己翻看页面图片下结论。

## 子智能体类型

`subagent_type` 从会话提供的类型列表中选择（如 `general-purpose`、`Explore`），不是自由指定模型。requesting-code-review 派审查员时用 `general-purpose`。
