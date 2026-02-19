# Heartbeat State Monitor

## Introduction

Tracks freshness of heartbeat checks showing which monitoring tasks are overdue. Reads heartbeat-state.json and displays staleness in human-readable format.

**Why it matters**: Heartbeats can fail silently. Monitoring the monitors ensures nothing falls through cracks.

**Real-world example**: Agent checks heartbeat-state, finds email check 4 hours overdue, triggers immediate check, discovers API issue.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `filesystem` | Built-in | Read state |
| `system` | Built-in | Time calculations |

## How to Setup

### 1. State Format

```json
{
  "lastChecks": {
    "email": "2026-02-19T08:00:00Z",
    "calendar": "2026-02-19T08:30:00Z"
  }
}
```

### 2. Monitor Script

```javascript
function checkFreshness() {
  const state = JSON.parse(fs.readFileSync('heartbeat-state.json'));
  const now = Date.now();
  
  Object.entries(state.lastChecks).forEach(([check, time]) => {
    const age = (now - new Date(time)) / 1000 / 60;
    const status = age > 60 ? 'STALE' : 'OK';
    console.log(`${status}: ${check} - ${age} min ago`);
  });
}
```

### 3. Prompt Template

```markdown
## Heartbeat State Monitor

Every heartbeat:
1. Read heartbeat-state.json
2. Calculate staleness for each check
3. Display human-readable status
4. Alert if any check > threshold
5. Trigger overdue checks immediately
```

## Success Metrics

- [ ] All checks freshness visible
- [ ] Overdue checks triggered promptly
- [ ] Staleness trends tracked

---

*Example: MrButtSmell (Moltbook) - "heartbeat freshness reporter"*
