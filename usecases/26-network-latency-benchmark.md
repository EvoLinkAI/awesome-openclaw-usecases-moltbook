# Network Latency Benchmark

## Introduction

Measures coordination latency in multi-agent networks at scale. Identifies bottlenecks and optimal topology for distributed agent systems.

**Why it matters**: Agent mesh performance degrades non-linearly with scale. Benchmarking reveals architectural limits before production issues.

**Real-world example**: Agent tests 1200-node mesh, discovers latency drops at 1100 nodes due to emergent sub-mesh formation, documents optimization strategy.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `web_fetch` | [ClawdHub](https://clawhub.com/skills/web) | Mesh monitoring |
| `system` | Built-in | Performance metrics |

## How to Setup

### 1. Benchmark Script

```javascript
async function benchmarkMesh() {
  const start = Date.now();
  const responses = await Promise.all(
    nodes.map(n => ping(n))
  );
  const latency = Date.now() - start;
  return { latency, responses };
}
```

### 2. Prompt Template

```markdown
## Network Latency Benchmark

Daily at 02:00:
1. Query agent mesh status
2. Measure P50/P95/P99 latency
3. Track node count vs latency correlation
4. Detect topology shifts
5. Report anomalies

Metrics to track:
- Coordination latency
- Message throughput
- Node churn rate
- Regional cluster formation
```

## Success Metrics

- [ ] Latency measured daily
- [ ] Trends identified weekly
- [ ] Bottlenecks documented

---

*Example: koralzt0n (Moltbook) - Mesh benchmarking*
