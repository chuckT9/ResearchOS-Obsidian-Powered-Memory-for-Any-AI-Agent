# ResearchOS — Agent Configuration

> This file defines how AI agents interact with the knowledge base.
> Place this in the root of your Obsidian vault.

## 1. Semantic Dispatch Layer

### Intent Classification Rules

When writing to the vault, classify the content by intent and route to the correct folder:

| Intent Signal | Destination | Frontmatter Template |
|---------------|-------------|---------------------|
| Paper, literature, citation, DOI | `论文笔记/` | tags: [论文, topic] |
| Experiment, result, observation, data | `实验记录/` | tags: [实验, topic] |
| Todo, task, deadline, fix | `待办事项/` | tags: [待办] |
| Idea, insight, hypothesis, "what if" | `想法速记/` | tags: [想法, topic] |
| User preference, behavior rule, correction | `Agent记忆/` | tags: [系统] |
| Research plan, methodology, design | `研究/` | tags: [研究, topic] |

### Classification Algorithm

```
1. Check keywords in the content
2. Match against the signal table above
3. If confident (>80%) → write to matched folder
4. If uncertain → write to 想法速记/ with tag #待归类
5. Always append to 目录.md in the target folder
```

### Frontmatter Requirements

Every note must have YAML frontmatter:

```yaml
---
date: 'YYYY-MM-DD'
tags: [tag1, tag2]
keywords: [keyword1, keyword2, keyword3]
---
```

Keywords must include:
- Chinese and English synonyms (e.g., `CNN` + `卷积神经网络`)
- Abbreviations and full names (e.g., `PCA` + `主成分分析`)
- Related method names

## 2. Memory Bifurcation Protocol

### Behavioral Track (Agent Configuration)

Write to this track when:
- User corrects the agent
- User states a preference
- User says "remember this" or "don't do that"
- Agent discovers a stable environment fact

**Target files:**
- `MEMORY.md` (agent's own notes, < 200 lines)
- Agent config file (`CLAUDE.md` / `.cursorrules` / `config.yaml`)

**Rules:**
- Declarative facts only, not instructions
- "User prefers X" ✓ — "Always do X" ✗
- Stable facts only, no temporary state
- Max 200 lines — if full, merge/compress old entries

### Factual Track (Knowledge Base)

Write to this track when:
- Research data is generated
- Paper is read and summarized
- Experiment results are recorded
- Literature is reviewed

**Target files:**
- Folders per the dispatch table above
- Always update `目录.md` in the target folder

**Rules:**
- Atomic notes — one topic per file
- Never mix behavioral and factual content
- Update index after every write
- Use merge mode for existing topics, overwrite for metadata

## 3. Semantic Compaction

### Session End Protocol

When a session ends (or user says "memo" / "总结"):

```
Step 1: Identify distinct topics in the conversation
Step 2: For each topic:
   a. Search existing notes for a match
   b. If match found → append/merge (max 200 chars, no confirmation needed)
   c. If no match → create new note (show outline, wait for confirmation)
Step 3: Update 目录.md in each affected folder
Step 4: Update 关键文件路径.md if new files were created
```

### Merge Rules

- **Overwrite mode**: For metadata files (目录.md, 总览.md, config files)
  - Precise in-place edit, no duplication
- **Merge mode**: For content files (research notes, experiment logs)
  - Search first, restructure if updating, append if new
  - Never rewrite/abbreviate original text

## 4. Search Protocol

### Two-Step Retrieval

```
Step 1: Search by filename (exact match, zero cost)
Step 2: If no hit → search by keywords in frontmatter
```

Always search before creating new notes. Never create duplicates.

## 5. Update Rules

### Atomic Updates

Every note write must be followed immediately by:
1. Update `目录.md` in the affected folder
2. Update root `目录.md` if new folder was created
3. Update `关键文件路径.md` if new file path was created

### Dual-Link Requirement

Every note must have:
- A forward link in the relevant `目录.md`
- A back-link in the note itself (if referencing another note)

## 6. Agent Behavior Rules

### General

- Never guess when you can read a file
- After every file edit: state what changed and why
- If same task fails twice: stop, ask for help
- Review before act: read and report first, implement after confirmation

### Writing Style

- Chinese for conversation, English for code/configs
- Direct and concise, no filler
- When uncertain about permissions: try the tool, don't assume

### Safety

- Never write secrets to the knowledge base
- Never delete without confirmation
- Always backup before major changes
