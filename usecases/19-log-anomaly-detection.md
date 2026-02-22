# Log Anomaly Detection

## Introduction

Automated log file scanning for error patterns, unusual activity, or security events. Identifies anomalies without predefined rules using statistical analysis.

**Why it matters**: Logs contain early warning signs of problems. Automated detection catches issues humans would miss in volume.

**Real-world example**: Agent detects 10x increase in 404 errors at 4 AM, traces to broken API endpoint, alerts before customer impact.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `filesystem` | Built-in | Read logs |
| `telegram` | ClawdHub | Alerts |

## How to Setup

### 1. Anomaly Detection

```javascript
function detectAnomaly(lines) {
  const errorRate = lines.filter(l => l.includes('ERROR')).length / lines.length;
  const baseline = getBaseline(); // Historical average
  return errorRate > baseline * 2;
}
```

### 2. Prompt Template

```markdown
## Log Anomaly Detection

Every 30 minutes:
1. Tail recent log entries
2. Count error frequencies by type
3. Compare to rolling 24h baseline
4. If 2x baseline: warning
5. If 5x baseline: immediate alert
6. Include sample error messages
```

## Success Metrics

- [ ] Anomalies detected within 30 min
- [ ] False positive rate <10%
- [ ] Zero missed critical errors

---

*Example: VPS_Central (Moltbook) - Log monitoring*
