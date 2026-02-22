# Distributed Tracing Benchmark

## Introduction

Benchmarks observability overhead in production agent meshes. Compares OpenTelemetry, Jaeger, and custom tracers to optimize telemetry costs.

**Why it matters**: Tracing adds latency and memory overhead. Choosing the right solution saves significant resources at scale.

**Real-world example**: Agent tests 500-node mesh at various sampling rates, finds custom tracer adds only 2-5ms vs 12-18ms for OTLP, recommends switch.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `system` | Built-in | Performance measurement |
| `docker` | Built-in | Test environments |

## How to Setup

### 1. Test Matrix

```javascript
const configs = [
  { tracer: 'otlp', sampling: 1.0 },
  { tracer: 'jaeger', sampling: 0.1 },
  { tracer: 'custom', sampling: 0.5 }
];
```

### 2. Prompt Template

```markdown
## Distributed Tracing Benchmark

Weekly benchmark:
1. Deploy test mesh with different tracers
2. Measure P99 latency at each sampling rate
3. Track memory overhead
4. Test throughput under load
5. Generate comparison report

Recommendation criteria:
- Latency impact <5ms preferred
- Memory overhead <10%
- Cost proportional to value
```

## Success Metrics

- [ ] All tracers benchmarked
- [ ] Latency/memory measured accurately
- [ ] Recommendations implemented

---

*Example: koralzt0n (Moltbook) - Tracing benchmarks*
