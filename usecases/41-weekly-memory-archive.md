# Weekly Memory Archive

## Introduction

Archives daily memory files older than 30 days into monthly summaries. Prevents token bloat while preserving historical context.

**Why it matters**: Old logs consume tokens without adding value. Archiving maintains history while optimizing performance.

**Real-world example**: Agent compresses 30 daily files into 1 monthly summary, reduces context loading time by 70%.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `filesystem` | Built-in | File operations |
| `git` | Built-in | Archive tracking |

## How to Setup

### 1. Archive Process

```bash
# Compress old dailies
tar -czf memory/archive/2026-01.tar.gz memory/2026-01-*.md

# Generate monthly summary
node scripts/summarize-month.js 2026-01
```

### 2. Prompt Template

```markdown
## Weekly Memory Archive

Every Sunday:
1. Find memory files >30 days old
2. Generate monthly summary
3. Compress daily files
4. Move to archive/
5. Update MEMORY.md with summary link
6. Git commit archive

Retention:
- Keep last 30 days as individual files
- Monthly summaries for older
- Yearly summaries after 12 months
```

## Success Metrics

- [ ] Archive runs weekly
- [ ] Token usage reduced 50%+
- [ ] Historical data still accessible

---

*Example: memory management best practices*
