---
name: skills-index-cn
description: 常用 skills 中文索引，按使用场景分类，按需积累
---

# Skills 中文索引

> 使用方式：找到你想做的事，复制对应的 skill 名称，告诉 Claude 使用它。
> 持续积累：每次用到一个有效的 skill，追���到对应分类里。

---

## 提示词 & 规划

| 我想做什么 | skill 名称 | 备注 |
|-----------|-----------|------|
| 优化一段提示词 | `everything-claude-code:prompt-optimize` | 分析意图、填补漏洞、输出优化版本 |
| 项目开始前头脑风暴 | `superpowers:brainstorming` | 创意/功能/方案，做之前先想清楚 |
| 写一个实现计划 | `superpowers:writing-plans` | 多步骤任务，先规划再动手 |
| 执行一个已写好的计划 | `superpowers:executing-plans` | 按计划逐步执行，带检查节点 |

---

## 项目管理（GSD 系列）

| 我想做什么 | skill 名称 | 备注 |
|-----------|-----------|------|
| 初始化一个新项目 | `gsd:new-project` | 深度收集上下文，生成 PROJECT.md |
| 规划某个阶段的任务 | `gsd:plan-phase` | 生成 PLAN.md，带验证循环 |
| 执行某个阶段 | `gsd:execute-phase` | 并行执行阶段内所有计划 |
| 查看项目进度 | `gsd:progress` | 显示当前状态，路由到下一步 |
| 调试一个 bug | `gsd:debug` | 系统化调试，跨上下文保持状态 |
| 快速执行一个小任务 | `gsd:fast` | 无子 agent，无规划开销 |
| 保存当前工作上下文 | `gsd:pause-work` | 暂停时创建交接文档 |
| 恢复上次工作 | `gsd:resume-work` | 读取上下文，从上次中断处继续 |

---

## 开发辅助

| 我想做什么 | skill 名称 | 备注 |
|-----------|-----------|------|
| 查某个库的最新文档 | `everything-claude-code:docs` | 用 Context7 拉取实时文档 |
| 做前端页面 | `frontend-dev` | 高质量 UI，含动画和设计 |
| 做全栈应用 | `fullstack-dev` | 前后端一体架构 |
| 写实现计划（代码层面） | `everything-claude-code:plan` | 评估风险，出步骤，等确认再动手 |
| 系统性调试 | `superpowers:systematic-debugging` | 遇到 bug 先用这个，别瞎改 |
| 安全审查 | `everything-claude-code:security-review` | 涉及用户输入/鉴权/API 时用 |

---

## 会话管理

| 我想做什么 | skill 名称 | 备注 |
|-----------|-----------|------|
| 保存当前会话 | `everything-claude-code:save-session` | 保存到 ~/.claude/session-data/ |
| 恢复上次会话 | `everything-claude-code:resume-session` | 加载最近一次会话，恢复上下文 |

---

## Skills 库自身维护

| 我想做什么 | skill 名称 | 备注 |
|-----------|-----------|------|
| 升级一个下载来的 skill | 参考 `skill-upgrade.md` | 本库内置流程 |
| 写一个新 skill | 参考 `skills-workflow.md` | 本库内置模板 |

---

## 积累记录

> 每次用完一个 skill 觉得有效，在这里追加一行。

| 日期 | skill | 用在什么场景 |
|------|-------|------------|
| 2026-03-28 | `everything-claude-code:prompt-optimize` | 优化 OpenClaw 顾问提示词 |
| 2026-03-28 | `gsd:debug` | （待用） |
