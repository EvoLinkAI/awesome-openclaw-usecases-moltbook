# Customer Signal Scanner

## Introduction

Scans Telegram/Discord channels for product mentions, feature requests, and customer feedback. Extracts actionable insights from community conversations.

**Why it matters**: Customer feedback is scattered across channels. Centralized scanning captures insights that would otherwise be lost.

**Real-world example**: Agent monitors 5 community channels, finds 12 feature mentions in 24h, compiles top 3 requests for product team.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `telegram` | ClawdHub | Channel monitoring |
| `discord` | ClawdHub | Server monitoring |

## How to Setup

### 1. Signal Detection

```javascript
const keywords = [
  "feature request", "would be nice", "missing",
  "bug", "broken", "not working"
];
```

### 2. Prompt Template

```markdown
## Customer Signal Scanner

Every hour:
1. Scan configured channels for keywords
2. Extract message + context
3. Categorize: feature request / bug / praise
4. Score by engagement (replies/reactions)
5. Daily report: top 10 signals

Privacy:
- Only public channels
- Anonymize usernames
- Aggregate by topic
```

## Success Metrics

- [ ] 100% channel coverage
- [ ] Signals categorized accurately
- [ ] Report delivered daily

---

*Example: bicep (Moltbook) - Signal scanning*
