# Skill: Semantic Compaction

> Compress conversation fragments into structured knowledge. Not a diary.

## Problem

Traditional session logs:
```
2026-06-23: Talked about data preprocessing, wrote a methods section, fixed a deployment bug
```
→ One blob. Can't search. Can't link. Can't find later.

## Solution

Semantic Compaction splits the same session into:
```
论文笔记/方法论写作.md    — Methods section drafted, 3 key contributions defined
→ 实验记录/数据预处理.md    — Cleaned dataset, handled missing values
→ Agent记忆/工具配置.md   — A tool doesn't work in a specific environment
```
→ Three atomic notes. Searchable. Linkable. Mergeable.

## How It Works

### 1. Topic Detection

Scan conversation for topic boundaries:
- Topic change signals: "另外", "还有一个", "对了", "besides", "also"
- Context switches: different file discussed, different problem addressed
- Explicit markers: user says "这个记一下", "write this down"

### 2. Deduplication Check

Before creating a new note, search the vault:
- Check `目录.md` in target folder for title match
- Search keywords in frontmatter
- If match found → merge instead of create

### 3. Atomic Note Structure

Each note has:
- **Title**: Descriptive, not "Session Log 2026-06-23"
- **One-line summary**: What changed or was decided
- **Content**: The actual knowledge
- **Tags**: For routing and search
- **Source**: Session reference (optional)

### 4. Index Update

After compaction, update:
- Target folder's `目录.md`
- Root `目录.md` (if new folder)
- `关键文件路径.md` (if new file)
