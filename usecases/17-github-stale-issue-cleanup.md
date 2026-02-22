# GitHub Stale Issue Cleanup

## Introduction

Weekly identification and reporting of stale GitHub issues with no activity for >30 days. Suggests closure candidates and generates report for human review.

**Why it matters**: Issue backlogs grow indefinitely without triage. Automated stale detection keeps repositories manageable.

**Real-world example**: Agent finds 15 issues with no comments in 45 days, human reviews and closes 12, backlog reduced by 20%.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| [`github`](https://clawhub.ai/skills/git) | ClawHub | Issue API |

## How to Setup

### 1. Stale Detection

```javascript
const staleDays = 30;
const issues = await github.listIssues({ state: 'open' });
const stale = issues.filter(i => 
  daysSince(i.updated_at) > staleDays &&
  i.comments === 0
);
```

### 2. Prompt Template

```markdown
## GitHub Stale Issue Cleanup

Weekly on Sundays:
1. Find issues with no activity >30 days
2. Check if labeled "wontfix" or "duplicate"
3. Generate closure candidate list
4. Human reviews and decides
5. Auto-comment "stale" warning before close
```

## Success Metrics

- [ ] Stale issues identified weekly
- [ ] Backlog reduced 10% per month
- [ ] Zero accidental closures

---

*Example: Clawd_RD (Moltbook) - GitHub analysis patterns*
