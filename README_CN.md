# ResearchOS

> **让你的 AI 永远记住你。不需要写代码，不需要懂技术，复制粘贴就行。**

[English](README.md)

---

### ⭐ 如果这个项目对你有帮助，请给个 Star！

- ⭐ **1 秒，0 成本** — 点右上角 Star 按钮就行
- 🧑‍🎓 **专为学生和初学者设计** — 不用写代码，不用配置，粘贴就完事
- 🤖 **兼容任意 AI Agent** — Claude、ChatGPT、Cursor、Copilot、Hermes、Codex
- 📦 **基于 Obsidian** — 数据本地存储，可读、可迁移、永久保存

> *你的 Star = 让更多人知道 AI 记忆可以这么简单。*

---

你跟 ChatGPT 聊了一小时。下次打开，它什么都不记得。

你跟 Claude 改了半天代码。新会话，又从零开始。

你试了 5 个 AI 工具。每个都独立记忆，互相不认识。

**ResearchOS-Obsidian-Powered-Memory-for-Any-AI-Agent 解决这个问题。** 一个文件夹，让所有 AI 工具共享同一个大脑。

---

## 30 秒了解 ResearchOS-Obsidian-Powered-Memory-for-Any-AI-Agent

```
你跟 AI 聊天
      ↓
ResearchOS-Obsidian-Powered-Memory-for-Any-AI-Agent 自动把对话拆成结构化笔记
      ↓
笔记自动分类到正确的文件夹（论文/实验/待办/想法）
      ↓
下次打开任何 AI 工具，它读这个文件夹，就知道你是谁、在做什么
```

**不需要服务器。不需要数据库。不需要联网。** 就是你电脑上的一个文件夹。

---

## 谁适合用？

- **刚开始用 AI 的人** — 不用学任何技术，复制文件夹就行
- **学生 / 研究者** — 论文管理 + 实验记录 + 文献追踪
- **开发者** — 项目文档 + 代码记忆 + bug 追踪
- **写作者** — 素材收集 + 灵感管理 + 写作进度
- **任何用 AI 做事情的人** — 让 AI 记住你，而不是每次都重新认识你

---

## 安装（3 步，5 分钟）

### 1. 下载

点这里 → [下载 ZIP](https://github.com/chuckT9/ResearchOS-Obsidian-Powered-Memory-for-Any-AI-Agent/archive/refs/heads/main.zip)，解压。

（会用 Git 的人：`git clone https://github.com/chuckT9/ResearchOS-Obsidian-Powered-Memory-for-Any-AI-Agent.git`）

### 2. 复制

把解压出来的 `template-vault/` 里的所有文件，复制到你的 Obsidian 文件夹。

没有 Obsidian？去 [obsidian.md](https://obsidian.md) 免费下载，1 分钟装好。

### 3. 告诉你的 AI

在你的 AI 工具里说一句话：

```
我的知识库在这个路径：/你的/obsidian/文件夹/
每次对话开始时，先读里面的 目录.md。
```

**完了。** 正常跟 AI 聊天，它会自动读写这个文件夹。

> **详细部署指南（含每种 AI 工具的配置方法）：** [docs/SETUP.md](docs/SETUP.md)

---

## 它做了什么？

### 自动分类

AI 写的笔记自动放进正确的文件夹：

| AI 说了什么 | 放到哪里 |
|------------|---------|
| "这篇论文用了回归分析" | `论文笔记/` |
| "实验结果：准确率提升了 15%" | `实验记录/` |
| "明天记得改这个 bug" | `待办事项/` |
| "突然想到可以试试这个方法" | `想法速记/` |
| "用户不喜欢用 emoji" | `Agent记忆/` |

你不需要手动整理。AI 写入时自动归类。

### 记忆分叉

AI 的记忆分两条线，互不干扰：

- **你是谁**（偏好、习惯、规则）→ 每次对话自动加载，影响 AI 的行为
- **你知道什么**（论文、实验、数据）→ 按需搜索，不干扰 AI 的决策

两条线永远不混在一起。

### 语义压缩

会话结束时，自动把对话拆成独立笔记：

```
❌ "2026-06-23: 今天聊了实验设计、论文写作、还修了个 bug"
   → 一条流水账，以后找不到

✅ 拆成 3 条笔记：
   → 实验设计.md（合并到已有笔记）
   → 论文写作进度.md（新建）
   → Bug修复记录.md（新建）
   → 可搜索、可链接、可合并
```

---

## 支持的 AI 工具

| 工具 | 支持 | 备注 |
|------|------|------|
| **Claude Code** | ✅ 完整 | 配置 CLAUDE.md 即可 |
| **Hermes Agent** | ✅ 完整 | 配置 config.yaml 即可 |
| **Cursor** | ✅ 基础 | 配置 .cursorrules 即可 |
| **Codex CLI** | ✅ 基础 | 自动读取 AGENTS.md |
| **ChatGPT** | ⚠️ 手动 | 每次对话开始时粘贴知识库路径 |
| **Copilot** | ⚠️ 有限 | 不支持持久记忆 |
| **任何能读文件的 AI** | ✅ | 只要它能读 Markdown 就行 |

**换工具不丢记忆。** 知识库是 Markdown 文件，跟 AI 工具无关。

---

## 知识库长什么样？

```
你的vault/
├── Agent记忆/           # AI 记住的"你是谁"（偏好、规则）
├── 研究/               # 你的研究方案和方法
├── 论文笔记/           # 你读过的论文（带模板）
├── 实验记录/           # 你做过的实验（带模板）
├── 待办事项/           # 你的任务清单
├── 想法速记/           # 你的灵感碎片
├── 目录.md             # 总索引
└── AGENTS.md           # AI 的行为规则
```

全部是 Markdown 文件，存在你自己电脑上。可以用 [Obsidian](https://obsidian.md) 打开，也可以用任何文本编辑器。

---

## 为什么不用向量数据库？

| 方案 | 优点 | 缺点 |
|------|------|------|
| 向量数据库（mem0, Zep） | 语义搜索 | 要云端、看不懂、不透明 |
| **Markdown + Git** | 透明、可审计、可回退、免费 | 搜索靠标签和关键词 |

ResearchOS-Obsidian-Powered-Memory-for-Any-AI-Agent 用**标签 + 关键词**代替向量嵌入。没有那么"魔法"，但**100% 透明** — 你可以用 `git diff` 看 AI 到底学到了什么。

---

## 跟其他方案的区别

| 特性 | ResearchOS-Obsidian-Powered-Memory-for-Any-AI-Agent | claude-obsidian | obsidian-mind | mem0 |
|------|-----------|-----------------|---------------|------|
| 新手友好 | ✅ 复制粘贴就行 | ❌ 需要配置 | ⚠️ 一般 | ❌ 要写代码 |
| 任何 AI 都能用 | ✅ | ❌ 只有 Claude | ✅ | ✅ |
| 纯本地 | ✅ | ✅ | ✅ | ❌ 要云端 |
| 不需要向量数据库 | ✅ | ❌ | ✅ | ❌ |
| 自动分类 | ✅ | ❌ | ❌ | ❌ |
| 记忆分叉 | ✅ | ❌ | ❌ | ❌ |
| 语义压缩 | ✅ | ❌ | ❌ | ❌ |

---

## 进阶用法

- **安装 Skills** → 让 AI 更聪明地使用知识库（[部署指南](docs/SETUP.md)）
- **自定义文件夹** → 增删改文件夹结构（[部署指南](docs/SETUP.md)）
- **Git 版本控制** → 用 Git 管理知识库，随时回退
- **多设备同步** → 用 Syncthing/iCloud/OneDrive 同步文件夹

---

## 许可

MIT — 随便用，随便改，随便分发。

## 引用

如果 ResearchOS-Obsidian-Powered-Memory-for-Any-AI-Agent 对你有帮助：

```yaml
cff-version: 1.2.0
title: "ResearchOS-Obsidian-Powered-Memory-for-Any-AI-Agent: AI-Native Knowledge Operating System"
authors:
  - given-names: "Chuck"
    family-names: "Tarantino"
    orcid: "https://orcid.org/0009-0003-4650-6760"
```
