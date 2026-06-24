# 部署指南

> 从零开始，10 分钟搞定 ResearchOS-Obsidian-Powered-Memory-for-Any-AI-Agent。
> 不需要会编程，不需要命令行，不需要懂 Git。

## 你需要什么

| 工具 | 必须吗 | 去哪里装 |
|------|--------|---------|
| **Obsidian**（免费笔记软件） | ✅ 必须 | [obsidian.md](https://obsidian.md) 下载安装 |
| **任意 AI 工具** | ✅ 必须 | Claude / ChatGPT / Cursor / Copilot，随便哪个 |
| **Git**（版本控制） | 可选 | 会用 GitHub 网页版也行，不需要装 Git |

## 方法一：网页下载（最简单，不需要命令行）

### Step 1：下载模板

1. 打开 [github.com/chuckT9/ResearchOS-Obsidian-Powered-Memory-for-Any-AI-Agent](https://github.com/chuckT9/ResearchOS-Obsidian-Powered-Memory-for-Any-AI-Agent)
2. 点绿色 **Code** 按钮
3. 点 **Download ZIP**
4. 解压 ZIP 文件

### Step 2：创建 Obsidian Vault

1. 打开 Obsidian
2. 点 **Open folder as vault**
3. 选一个空文件夹（比如 `Documents/MyKnowledge`）
4. 把解压出来的 `template-vault/` 里的**所有文件**复制到这个文件夹

你的文件夹应该长这样：
```
MyKnowledge/
├── AGENTS.md
├── 目录.md
├── Agent记忆/
├── 研究/
├── 论文笔记/
├── 实验记录/
├── 待办事项/
└── 想法速记/
```

### Step 3：配置你的 AI 工具

打开你的 AI 工具，告诉它知识库在哪里。

**如果你用 Claude Code / Cursor / Codex：**

在你的项目文件夹根目录创建一个 `CLAUDE.md`（或 `.cursorrules`），写：

```markdown
## 知识库

知识库路径: /Users/你的名字/Documents/MyKnowledge

每次会话开始时：
1. 读 /Users/你的名字/Documents/MyKnowledge/目录.md
2. 遵循 /Users/你的名字/Documents/MyKnowledge/AGENTS.md 中的规则
```

**如果你用 ChatGPT / Claude 网页版：**

每次对话开始时，粘贴这段话：

```
我有一个知识库在 Obsidian 里。规则如下：
1. 你写的笔记要按类型放到对应文件夹（论文笔记/实验记录/待办事项/想法速记）
2. 每个笔记要有 YAML frontmatter（date, tags, keywords）
3. 会话结束时，把对话按主题拆分成独立笔记，不要写流水账
4. 你的记忆分两条轨道：我的偏好（行为）和研究内容（事实），不要混在一起
```

**如果你用 Hermes Agent：**

在 `~/.hermes/config.yaml` 里加：

```yaml
knowledge_base: /Users/你的名字/Documents/MyKnowledge
```

### Step 4：开始用

正常跟 AI 聊天就行。它会：
- 读你的知识库了解上下文
- 把新知识自动写到正确的文件夹
- 会话结束时帮你整理笔记

---

## 方法二：Git 克隆（适合会用命令行的人）

### Step 1：克隆仓库

```bash
git clone https://github.com/chuckT9/ResearchOS-Obsidian-Powered-Memory-for-Any-AI-Agent.git
cd ResearchOS-Obsidian-Powered-Memory-for-Any-AI-Agent
```

### Step 2：复制到你的 Vault

```bash
cp -r template-vault/* /你的/obsidian/vault/路径/
```

### Step 3：配置 AI 工具

同方法一的 Step 3。

### Step 4：保持更新

```bash
cd ResearchOS-Obsidian-Powered-Memory-for-Any-AI-Agent
git pull  # 拉取最新模板和技能
```

---

## 方法三：直接 Fork（适合想贡献/魔改的人）

1. 在 GitHub 上 Fork ResearchOS-Obsidian-Powered-Memory-for-Any-AI-Agent 仓库
2. Clone 你自己的 Fork
3. 在 `template-vault/` 里自定义你的文件夹结构
4. 改 `AGENTS.md` 里的规则
5. 如果你改得好，可以发 Pull Request 回来

---

## 高级：安装 Skills（可选）

Skills 是给特定 AI 工具的"技能包"，让它更聪明地使用知识库。

### Claude Code

把 `skills/` 文件夹复制到 `~/.claude/skills/`：

```bash
cp -r skills/* ~/.claude/skills/
```

然后在 `CLAUDE.md` 里加：

```markdown
## Skills

使用以下技能管理知识库：
- memo: 会话结束时按主题拆分笔记
- knowledge-router: 自动分类笔记到正确的文件夹
- semantic-compaction: 合并碎片笔记，去重
```

### Hermes Agent

把 `skills/` 文件夹复制到 `~/.hermes/skills/`：

```bash
cp -r skills/* ~/.hermes/skills/
```

### 其他工具

Skills 的本质就是 Markdown 文件，里面写了"怎么做某件事"的步骤。你可以把 `skills/` 里的内容复制粘贴到任何 AI 工具的配置里，它都能理解。

---

## 自定义

### 改文件夹结构

模板里的 6 个文件夹是建议，你可以随意增删：

- 加一个 `会议记录/` → 在 AGENTS.md 的分类表里加一行
- 删掉 `想法速记/` → 删文件夹，删 AGENTS.md 里的对应行
- 改名字 → 改文件夹名，同步改 AGENTS.md

### 改规则

`AGENTS.md` 是纯 Markdown，直接编辑就行。常见改动：

- 改分类信号词 → 在"Intent Classification Rules"表格里加词
- 改 frontmatter 要求 → 在"Frontmatter Requirements"里改
- 改行为规则 → 在"Agent Behavior Rules"里加减

### 改模板

论文笔记模板和实验记录模板都在对应文件夹里，直接改。

---

## 常见问题

**Q: 我不会用 Obsidian，难吗？**
A: 不难。Obsidian 就是一个记笔记的软件，跟 Notion 类似。你只需要会：创建文件夹、创建笔记、打标签。ResearchOS-Obsidian-Powered-Memory-for-Any-AI-Agent 的模板已经帮你把结构搭好了。

**Q: 我的知识存在哪里？安全吗？**
A: 全部存在你自己的电脑上。Obsidian vault 就是一个普通文件夹，里面有 Markdown 文件。不上传到任何云端（除非你主动用 iCloud/Dropbox 同步）。

**Q: 我换了一个 AI 工具，知识库还在吗？**
A: 在。知识库是 Markdown 文件，跟 AI 工具无关。换工具只需要重新配置路径。

**Q: 我能用中文吗？**
A: 能。文件夹名、笔记内容、标签都可以用中文。AGENTS.md 里的信号词也是中英双语的。

**Q: 需要联网吗？**
A: 不需要。ResearchOS-Obsidian-Powered-Memory-for-Any-AI-Agent 完全离线工作。AI 工具本身可能需要联网，但知识库不需要。

**Q: 我能跟别人共享知识库吗？**
A: 可以。用 Git 仓库管理 vault，多人 push/pull 就行。或者用 Syncthing/iCloud/OneDrive 同步文件夹。
