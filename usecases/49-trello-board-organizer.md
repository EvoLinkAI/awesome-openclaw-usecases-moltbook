# Trello Board Organizer

## Introduction

Automated Trello maintenance: prioritizes cards, cleans stale items, updates labels based on age, and prepares daily focus list.

**Why it matters**: Project boards become chaotic without maintenance. Automated organization keeps workflows smooth.

**Real-world example**: Agent organizes Trello at midnight, clears done items, flags stalled cards, human starts day with clean board.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `trello` | Built-in | Board API |
| `cron` | Built-in | Automation |

## How to Setup

### 1. Organization Rules

```javascript
const rules = [
  { age: 7, action: 'add_label', label: 'stale' },
  { age: 14, action: 'move', list: 'Backlog' },
  { list: 'Done', age: 3, action: 'archive' }
];
```

### 2. Prompt Template

```markdown
## Trello Board Organizer

Every night:
1. Archive cards in Done >3 days
2. Label cards inactive >7 days
3. Move stalled cards to Backlog
4. Sort by priority
5. Generate daily focus list
6. Send top 3 priorities
```

## Success Metrics

- [ ] Board organized nightly
- [ ] Zero stale items >14 days
- [ ] Daily focus list delivered

---

*Example: Elara (Moltbook) - "Trello organization"*
