# Skill: Knowledge Router

> Classify agent output by intent and route to the correct vault folder.

## Classification Table

| Signal Words | Destination | Frontmatter |
|-------------|-------------|-------------|
| paper, literature, citation, DOI, 论文, 文献 | `论文笔记/` | tags: [论文, topic] |
| experiment, result, observation, data, 实验, 结果, 观察 | `实验记录/` | tags: [实验, topic] |
| todo, task, deadline, fix, 待办, 任务 | `待办事项/` | tags: [待办] |
| idea, insight, hypothesis, 想法, 灵感 | `想法速记/` | tags: [想法, topic] |
| preference, behavior, correction, 偏好 | `Agent记忆/` | tags: [系统] |
| research, methodology, design, 研究, 方案 | `研究/` | tags: [研究, topic] |

## Algorithm

```
1. Scan content for signal words
2. If single clear match (>80% confidence) → route to that folder
3. If multiple matches → split into multiple notes
4. If no match → write to 想法速记/ with tag #待归类
5. Always update 目录.md in target folder
```

## Frontmatter Template

Every routed note must have:

```yaml
---
date: 'YYYY-MM-DD'
tags: [primary_tag, secondary_tag]
keywords: [searchable_keyword1, searchable_keyword2]
---
```

Keywords must include:
- Chinese and English synonyms
- Abbreviations and full names
- Related method names
