# ResearchOS

> **Give your AI a permanent memory. No code required. Just copy and paste.**

You chat with ChatGPT for an hour. Next time, it remembers nothing.

You work with Claude on code all day. New session, starting over.

You switch between 5 AI tools. Each one has its own memory. They don't know each other.

**ResearchOS fixes this.** One folder. Every AI tool shares the same brain.

**[中文版](README_CN.md)**

---

### ⭐ If this project helps you, please give it a Star!

- ⭐ **1 click, 0 cost** — just hit the Star button at the top right
- 🧑‍🎓 **Made for students & beginners** — no coding, no setup, just paste
- 🤖 **Works with ANY AI agent** — Claude, ChatGPT, Cursor, Copilot, Hermes, Codex
- 📦 **Obsidian-based** — your data stays local, readable, portable, forever

> *Your star = more people discover that AI memory can be this simple.*

---

## How it works in 30 seconds

```
You chat with your AI
        ↓
ResearchOS turns the conversation into structured notes
        ↓
Notes are sorted into the right folder (papers / experiments / todos / ideas)
        ↓
Next time you open any AI tool, it reads this folder and knows who you are
```

**No server. No database. No internet required.** Just a folder on your computer.

---

## Who is this for?

- **People new to AI** — no technical skills needed, just copy a folder
- **Students / Researchers** — papers, experiments, literature tracking
- **Developers** — project docs, code memory, bug tracking
- **Writers** — material collection, inspiration management, writing progress
- **Anyone who uses AI** — make your AI remember you instead of starting over every time

---

## Install (3 steps, 5 minutes)

### 1. Download

Click here → [Download ZIP](https://github.com/chuckT9/ResearchOS-Obsidian-Powered-Memory-for-Any-AI-Agent/archive/refs/heads/main.zip), unzip it.

(Git users: `git clone https://github.com/chuckT9/ResearchOS-Obsidian-Powered-Memory-for-Any-AI-Agent.git`)

### 2. Copy

Copy everything inside `template-vault/` into your Obsidian vault folder.

Don't have Obsidian? Download it free at [obsidian.md](https://obsidian.md) — takes 1 minute.

### 3. Tell your AI

Say this to your AI tool:

```
My knowledge base is at: /your/obsidian/vault/path
Read the 目录.md file at the start of every conversation.
```

**Done.** Just chat normally. Your AI will read and write to this folder automatically.

> Full setup guide for each AI tool → [docs/SETUP.md](docs/SETUP.md)

---

## What does it do?

### Auto-sort

AI-generated notes are automatically placed in the right folder:

| AI says... | Goes to... |
|-----------|-----------|
| "This paper uses regression analysis" | `论文笔记/` (Paper Notes) |
| "Experiment results: accuracy improved by 15%" | `实验记录/` (Experiments) |
| "Remember to fix this bug tomorrow" | `待办事项/` (Todos) |
| "What if we try this approach?" | `想法速记/` (Ideas) |
| "User doesn't like emoji" | `Agent记忆/` (Agent Memory) |

No manual sorting needed. It happens automatically when the AI writes.

### Memory Bifurcation

AI memory splits into two tracks that never mix:

- **Who you are** (preferences, habits, rules) → loaded every session, shapes AI behavior
- **What you know** (papers, experiments, data) → searched on demand, doesn't interfere with decisions

### Semantic Compaction

When a session ends, conversations are split into independent notes:

```
❌ "June 23: talked about experiment design, paper writing, and fixed a bug"
   → One diary entry, impossible to find later

✅ Split into 3 notes:
   → experiment-design.md (merged with existing note)
   → paper-writing-progress.md (new)
   → bug-fix-log.md (new)
   → searchable, linkable, mergeable
```

---

## Supported AI tools

| Tool | Support | How to configure |
|------|---------|-----------------|
| **Claude Code** | ✅ Full | Add path to CLAUDE.md |
| **Hermes Agent** | ✅ Full | Add path to config.yaml |
| **Cursor** | ✅ Basic | Add path to .cursorrules |
| **Codex CLI** | ✅ Basic | Reads AGENTS.md automatically |
| **ChatGPT** | ⚠️ Manual | Paste vault path at conversation start |
| **Copilot** | ⚠️ Limited | No persistent memory support |
| **Any AI that reads files** | ✅ | If it can read Markdown, it works |

**Switch tools without losing memory.** The knowledge base is Markdown files, independent of any AI tool.

---

## What's inside the vault?

```
your-vault/
├── Agent记忆/           # Who you are (preferences, rules)
├── 研究/               # Research plans and methodology
├── 论文笔记/           # Papers you've read (with template)
├── 实验记录/           # Experiments you've done (with template)
├── 待办事项/           # Your task list
├── 想法速记/           # Ideas and insights
├── 目录.md             # Master index
└── AGENTS.md           # AI behavior rules
```

All Markdown files, stored on your computer. Open with [Obsidian](https://obsidian.md) or any text editor.

---

## Why not vector databases?

| Approach | Pros | Cons |
|----------|------|------|
| Vector DB (mem0, Zep) | Semantic search | Cloud-only, opaque, can't audit |
| **Markdown + Git** | Transparent, auditable, free | Search by tags and keywords |

ResearchOS uses **structured metadata** (YAML tags + keywords) instead of embeddings. Less magical, but **100% transparent** — you can `git diff` to see exactly what the AI learned.

---

## How is this different?

| Feature | ResearchOS | claude-obsidian | obsidian-mind | mem0 |
|---------|-----------|-----------------|---------------|------|
| Beginner friendly | ✅ Copy-paste | ❌ Complex setup | ⚠️ Medium | ❌ Needs code |
| Works with any AI | ✅ | ❌ Claude only | ✅ | ✅ |
| Fully local | ✅ | ✅ | ✅ | ❌ Cloud |
| No vector DB | ✅ | ❌ | ✅ | ❌ |
| Auto-sort | ✅ | ❌ | ❌ | ❌ |
| Memory bifurcation | ✅ | ❌ | ❌ | ❌ |
| Semantic compaction | ✅ | ❌ | ❌ | ❌ |

---

## Advanced

- **Install Skills** → Make your AI use the knowledge base smarter ([Setup Guide](docs/SETUP.md))
- **Customize folders** → Add, remove, or rename folders ([Setup Guide](docs/SETUP.md))
- **Git version control** → Track changes to your knowledge base with git
- **Multi-device sync** → Use Syncthing / iCloud / OneDrive to sync the folder

---

## License

MIT — use it, modify it, distribute it.

## Citation

If ResearchOS helps your work:

```yaml
cff-version: 1.2.0
title: "ResearchOS: AI-Native Knowledge Operating System"
authors:
  - given-names: "Chuck"
    family-names: "Tarantino"
    orcid: "https://orcid.org/0009-0003-4650-6760"
```
