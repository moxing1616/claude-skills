---
name: setup
description: 在新电脑上一键配置 Mr. Zhang 的 Claude 工作环境，包括 meitu-cli、AK/SK、meitu-skills、claude-skills 自动同步
---

# Setup — 新环境一键配置

## 你的任务

按顺序执行以下步骤，帮用户在新电脑上完整配置 Claude 工作环境。每步完成后告知结果，失败则报错并停止。

---

## Step 1：安装 meitu-cli

```bash
npm install -g meitu-cli@latest
meitu --version
```

验证版本号输出正常后继续。

---

## Step 2：配置 meitu AK/SK

询问用户：
> 请提供你的 meitu AK 和 SK（可在美图开放平台控制台查看）

获取后执行：

```bash
meitu config set-ak --value <用户提供的AK>
meitu config set-sk --value <用户提供的SK>
```

---

## Step 3：安装 meitu-skills

```bash
clawhub install meitu-skills --force
```

---

## Step 4：克隆 claude-skills 仓库

```bash
git clone https://github.com/moxing1616/claude-skills.git ~/.claude/skills/claude-skills
```

如果目录已存在，执行：
```bash
cd ~/.claude/skills/claude-skills && git pull
```

---

## Step 5：配置 SessionStart Hook（自动同步）

读取 `~/.claude/settings.json`，在 `hooks.SessionStart` 数组中追加以下 hook（保留已有 hook，不替换）：

```json
{
  "hooks": [
    {
      "type": "command",
      "command": "cd \"~/.claude/skills/claude-skills\" && git pull 2>&1 || true",
      "timeout": 30,
      "statusMessage": "同步 claude-skills..."
    }
  ]
}
```

> 注意：Windows 路径用 `C:/Users/<用户名>/.claude/skills/claude-skills`，根据实际用户名替换。

---

## Step 6：验证

```bash
meitu --version
ls ~/.claude/skills/
```

输出应包含 `meitu-skills` 和 `claude-skills` 两个目录。

---

## 完成提示

告知用户：
> 环境配置完成！每次对话开始会自动同步最新 skills。如需更新 meitu AK/SK，运行：
> `meitu config set-ak --value <新AK>`
> `meitu config set-sk --value <新SK>`
