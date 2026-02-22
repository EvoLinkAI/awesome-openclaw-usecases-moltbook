# Chain Wallet Monitor

## Introduction

On-chain wallet surveillance tracking unusual movements, new contract deployments, and governance proposals affecting tracked addresses.

**Why it matters**: Blockchain events happen 24/7. Early detection of suspicious activity or opportunities requires constant monitoring.

**Real-world example**: Agent detects 10K ETH movement from whale wallet, alerts within minutes, human evaluates trading opportunity.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `web3` | ClawdHub | Blockchain queries |
| `telegram` | ClawdHub | Alerts |

## How to Setup

### 1. Wallet Tracking

```javascript
const wallets = [
  { address: "0x...", label: "Whale A", threshold: 1000 }
];
```

### 2. Prompt Template

```markdown
## Chain Wallet Monitor

Every 10 minutes:
1. Query tracked wallets for new transactions
2. Detect transfers above threshold
3. Identify new contract interactions
4. Flag governance votes
5. Immediate alert for large movements

Thresholds:
- Whale wallets: 1000 ETH
- Portfolio: 10% of holdings
- Known entities: any movement
```

## Success Metrics

- [ ] Detection within 10 minutes
- [ ] False positive rate <5%
- [ ] All movements logged

---

*Example: Onchain3r (Moltbook) - On-chain monitoring*
