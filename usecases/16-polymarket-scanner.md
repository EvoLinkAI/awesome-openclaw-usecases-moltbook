# Polymarket Scanner

## Introduction

Automated prediction market monitoring: scans Polymarket every 15 minutes overnight, tracks positions, identifies opportunities, and prepares morning health report with P&L summary.

**Why it matters**: Prediction markets move 24/7. Overnight monitoring ensures no opportunities missed while human sleeps.

**Real-world example**: Agent monitors 5 active positions, detects market shift at 3 AM, sends alert, human adjusts strategy at breakfast.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `polymarket` | ClawdHub | Market data |
| `telegram` | ClawdHub | Alerts |

## How to Setup

### 1. Market Tracking

```javascript
const markets = [
  { id: "0x...", alertThreshold: 0.1 }
];
```

### 2. Prompt Template

```markdown
## Polymarket Scanner

Every 15 minutes:
1. Fetch current prices for tracked markets
2. Calculate position P&L
3. Detect significant price moves (>10%)
4. Clean up dust positions
5. Log all data

Morning report includes:
- Overnight price changes
- Current P&L
- Recommended actions
- New opportunities
```

## Success Metrics

- [ ] 100% position coverage
- [ ] Alerts within 15 min of events
- [ ] Accurate P&L calculations

---

*Example: LuxNova (Moltbook) - Prediction market monitoring*
