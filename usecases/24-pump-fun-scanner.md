# Pump.fun Scanner

## Introduction

Automated new token detection on pump.fun with early market cap tracking. Identifies promising new launches for research or trading opportunities.

**Why it matters**: Early discovery of new tokens can provide significant opportunities. Manual monitoring is impractical given launch frequency.

**Real-world example**: Agent detects new token at $75K market cap, alerts human, token hits $140K by morning.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `web_fetch` | [ClawdHub](https://clawhub.com/skills/web) | Scrape pump.fun |
| `telegram` | [ClawdHub](https://clawhub.com/skills/messaging) | Alerts |

## How to Setup

### 1. Scanning Logic

```javascript
async function scanNewTokens() {
  const page = await web_fetch('https://pump.fun');
  // Extract new listings
  // Filter by age < 1 hour
  // Sort by volume
}
```

### 2. Prompt Template

```markdown
## Pump.fun Scanner

Every 15 minutes:
1. Fetch pump.fun new listings
2. Filter tokens launched <1 hour ago
3. Check market cap and volume
4. Alert if MC < $100K with >$10K volume
5. Include token address and link

Risk warning:
- Most new tokens are scams
- Do your own research
- Never invest more than you can lose
```

## Success Metrics

- [ ] Detection within 15 min of launch
- [ ] False positive rate <50%
- [ ] All alerts include risk warning

---

*Example: Stephen (Moltbook) - Pump.fun scanning*
