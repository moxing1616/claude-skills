---
name: setup
description: 在新电脑上一键配置 Mr. Zhang 的 Claude 工作环境，包括 meitu-cli、AK/SK、meitu-skills、claude-skills 自动同步及 skills 迭代推送能力
---

# Setup — 新环境一键配置

按顺序执行以下步骤。每步完成后告知结果��失败则报错停止。

---

## Step 1：安装 meitu-cli

```bash
npm install -g meitu-cli@latest
meitu --version
```

---

## Step 2：配置 meitu AK/SK

询问用户提供 AK 和 SK，然后执行：

```bash
meitu config set-ak --value <AK>
meitu config set-sk --value <SK>
```

---

## Step 3：安装 meitu-skills

```bash
clawhub install meitu-skills --force
```

---

## Step 4：克隆 claude-skills 仓库

**Windows：**
```bash
git clone https://github.com/moxing1616/claude-skills.git "C:/Users/%USERNAME%/.claude/skills/claude-skills"
```

**Mac/Linux：**
```bash
git clone https://github.com/moxing1616/claude-skills.git ~/.claude/skills/claude-skills
```

如目录已存在，执行 `git pull` 即可。

---

## Step 5：配置 git 推送凭证

询问用户选择方式：

**方式 A（推荐）— GitHub Personal Access Token：**
1. 引导用户访问 https://github.com/settings/tokens/new
2. 勾选 `repo` 权限，生成 token
3. 执行：
```bash
git -C ~/.claude/skills/claude-skills remote set-url origin https://<用户名>:<token>@github.com/moxing1616/claude-skills.git
```

**方式 B — SSH Key（已有 SSH key 的用户）：**
```bash
git -C ~/.claude/skills/claude-skills remote set-url origin git@github.com:moxing1616/claude-skills.git
```

**验证推送权限：**
```bash
cd ~/.claude/skills/claude-skills && git push --dry-run
```

---

## Step 6：配置 SessionStart Hook（自动同步）

读取 `~/.claude/settings.json`，在 `hooks.SessionStart` 数组中追加（保留已有 hook）：

**Windows：**
```json
{
  "hooks": [{
    "type": "command",
    "command": "cd \"C:/Users/<用户名>/.claude/skills/claude-skills\" && git pull 2>&1 || true",
    "timeout": 30,
    "statusMessage": "同步 claude-skills..."
  }]
}
```

**Mac/Linux：**
```json
{
  "hooks": [{
    "type": "command",
    "command": "cd ~/.claude/skills/claude-skills && git pull 2>&1 || true",
    "timeout": 30,
    "statusMessage": "同步 claude-skills..."
  }]
}
```

---

## Step 7：验证

```bash
meitu --version
ls ~/.claude/skills/
cd ~/.claude/skills/claude-skills && git remote -v
```

输出应包含 `meitu-skills`、`claude-skills` 目录，及正确的 GitHub remote 地址。

---

## 完成提示

告知用户：
> 环境配置完成！现在你可以：
> - 每次对话开始自动同步最新 skills
> - 对话中我会主动识别并提炼新 skill，写入后自动 push 到 GitHub
> - 所有设备共享同一套 skills 库，实时同步
