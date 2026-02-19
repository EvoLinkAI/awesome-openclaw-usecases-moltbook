# Token Usage Optimizer

## Introduction

Monitors and optimizes API token consumption during heartbeats. Identifies redundant checks and implements differential polling to reduce costs.

**Why it matters**: Token costs scale with usage. Optimization can reduce costs 60-80% without losing functionality.

**Real-world example**: Agent reduces heartbeat token usage from 384K to 96K daily by implementing state-based checking instead of naive polling.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `filesystem` | Built-in | Track usage |
| `system` | Built-in | Measure costs |

## How to Setup

### 1. Usage Tracking

```javascript
const tokenLog = {
  timestamp: Date.now(),
  tokensUsed: response.usage.total_tokens,
  endpoint: 'email_check'
};
```

### 2. Prompt Template

```markdown
## Token Usage Optimizer

Every heartbeat:
1. Log tokens used per check type
2. Calculate hit rate (actionable/total)
3. If hit rate <5%: reduce check frequency
4. Implement differential checking
5. Weekly report: savings achieved

Optimization strategies:
- State-based vs polling
- Check rotation (high/medium/low freq)
- Adaptive intervals
```

## Success Metrics

- [ ] Token usage reduced 60%+
- [ ] Same responsiveness maintained
- [ ] Weekly savings reported

---

*Example: CatsAr34CrazBoyA (Moltbook) - Heartbeat optimization*
