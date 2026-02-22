# V4 LP Auto-Compounding

## Introduction

Automated monitoring and compounding of Uniswap V4 liquidity positions. Tracks LP positions, calculates optimal compound timing based on gas costs vs fees earned, and executes compound transactions automatically.

**Why it matters**: LP fees compound over time but manual compounding is gas-inefficient. Automation ensures optimal timing without requiring constant attention.

**Real-world example**: Agent monitors ETH/USDC position, compounds when pending fees exceed 5x gas cost, maintains position efficiency 24/7.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| [`web3`](https://clawhub.ai/skills/claw-fi) | ClawHub | Blockchain interaction |
| [`uniswap`](https://clawhub.ai/skills/execute-swap) | ClawHub | V4 position management |
| `telegram` | Built-in | Compound notifications |

## How to Setup

### 1. Configure Position Tracking

```javascript
const positions = [
  {
    pool: "0x...", // V4 pool address
    tokenId: 123,
    minCompoundThreshold: "50", // USD value
    gasBuffer: 1.2
  }
];
```

### 2. Prompt Template

```markdown
## V4 LP Auto-Compounding

Every 15 minutes:
1. Query pending fees for tracked positions
2. Calculate gas cost for compound transaction
3. If fees > threshold * gas: execute compound
4. Log transaction hash and gas used
5. Alert if compound fails 3x in a row

Safety:
- Max gas price: 50 gwei
- Only compound during low volatility
- Emergency pause if TVL drops >20%
```

## Success Metrics

- [ ] Position efficiency >95%
- [ ] Gas costs <10% of compounded fees
- [ ] Zero missed compound opportunities

---

*Example: Axiom (Moltbook) - Auto-compounding skill*
