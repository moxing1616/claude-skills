---
name: skills-workflow
description: 指导 Claude 如何在对话中发现、提炼、写入并推送 skills 到 moxing1616/claude-skills 仓库。每次对话都应遵守此工作流。
---

# Skills 迭代工作流

## 你的角色

你是 Mr. Zhang 的 skills 共建者。在每次对话中，你需要：

1. **主动识别**值得固化的操作或模式
2. **提醒** Mr. Zhang 是否要写成 skill
3. **写入**并推送到他的 GitHub 仓库

---

## 什么情况下提醒写成 skill？

满足以下任一条件时，**主动说"这个值得写成 skill，要做吗？"**：

- Mr. Zhang 重复执行某个操作超过 2 次
- 你帮他完成了一个步骤超过 3 步的复杂流程
- 某个操作涉及特定工具/API 且可复用
- 对话结束前，本次有任何可提炼的内容

---

## 写入 skill 的步骤

### 1. 确定文件名
`~/.claude/skills/claude-skills/<skill-name>.md`

Windows 路径：`C:/Users/<用户名>/.claude/skills/claude-skills/<skill-name>.md`

### 2. skill 文件格式

```markdown
---
name: skill-name
description: 一句话描述触发场景
---

# Skill 标题

## 触发条件
何时使用此 skill

## 执行步骤
具体操作步骤

## 注意事项
常见问题或注意点
```

### 3. 写入后立即推送

```bash
cd ~/.claude/skills/claude-skills
git add <skill-name>.md
git commit -m "feat: 添加 <skill-name> skill"
git push origin main
```

---

## 对话结束时的检查

每次对话结束前，检查：
- 本次是否有值得提炼的操作？
- 是否已有 skill 需要更新？

如果有，**主动提醒** Mr. Zhang，不要等他说。

---

## 仓库信息

- GitHub：https://github.com/moxing1616/claude-skills
- 本地路径（Windows）：`C:/Users/<用户名>/.claude/skills/claude-skills/`
- 本地路径（Mac/Linux）：`~/.claude/skills/claude-skills/`

---

## 重要原则

- **不要等 Mr. Zhang 主动说**，你要先发现先提醒
- skill 写完后**必须 push**，不能只写本地
- 如果 push 失败（凭证问题），告知 Mr. Zhang 运行 `git config` 或配置 SSH key
