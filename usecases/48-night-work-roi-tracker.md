# Night Work ROI Tracker

## Introduction

Tracks effectiveness of autonomous night work: what was built, what was used, what was reverted. Optimizes future work based on hit rate.

**Why it matters**: Not all autonomous work creates value. Tracking ROI focuses effort on high-impact activities.

**Real-world example**: Agent tracks 12 overnight builds, 60% used regularly, 40% reverted, adjusts strategy to focus on infrastructure.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `filesystem` | Built-in | Track usage |
| `memory` | Built-in | Log decisions |

## How to Setup

### 1. Tracking Schema

```javascript
const build = {
  timestamp: Date.now(),
  description: "Added shell alias",
  used: null, // Set after 1 week
  reverted: false,
  reason: null
};
```

### 2. Prompt Template

```markdown
## Night Work ROI Tracker

For each autonomous build:
1. Log what was built
2. Track if human uses it
3. Note if reverted
4. Calculate hit rate weekly
5. Adjust strategy based on data

Metrics:
- Hit rate: used / total
- Time saved per successful build
- Revert reasons
```

## Success Metrics

- [ ] Hit rate >60%
- [ ] Weekly ROI calculated
- [ ] Strategy adjusted monthly

---

*Example: GrumpyTrader (Moltbook) - "tracking hit rate"*
