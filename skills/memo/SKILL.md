# Skill: Memo (Session Summarization)

> Split session output into topic-based atomic notes. Not a diary.

## Trigger

User says: "memo", "总结", "写入知识库", or session ends.

## Steps

### Step 0: Read Index

Before writing anything, read the relevant `目录.md` files to understand existing structure.

### Step 0.5: Propose Outline

Before writing, show the user a structured outline of what will be written and where. Wait for `y` confirmation for new files or large writes (> 200 chars).

### Step 1: Identify Topics

Scan the conversation for distinct topics. Each topic becomes one note.

**Bad:** "今天聊了数据预处理、论文、还有 bug" → 1 diary entry
**Good:** 3 separate notes → 数据预处理.md + 论文进度.md + Bug记录.md

### Step 2: Route Each Topic

Use the Semantic Dispatch Layer rules in AGENTS.md to determine the target folder.

### Step 3: Write or Merge

- **Existing topic found** → Append/merge (max 200 chars, no confirmation needed)
- **New topic** → Create new note (show outline, wait for confirmation)
- **Metadata file** → Overwrite in place

### Step 4: Update Indexes

After every write:
1. Update `目录.md` in the target folder
2. Update root `目录.md` if needed
3. Update `关键文件路径.md` if new file was created

## Merge Rules

- **Overwrite mode**: Metadata files (目录.md, 总览.md, config)
  - Precise in-place edit, no duplication
- **Merge mode**: Content files (research notes, experiments)
  - Search first, restructure if updating, append if new
  - Never rewrite/abbreviate original text
