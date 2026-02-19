# 7-Sub-Agent Night Parallel

## Introduction

Runs 7 parallel sub-agents during night shift, each handling different tasks: memory cleanup, budget preparation, TTS research, book recommendations, self-improvement research, AI memory neuroscience, and advisor pattern study. All results committed to git by morning.

**Why it matters**: Parallel execution multiplies productivity while human sleeps. Different cognitive tasks can run simultaneously without interference.

**Real-world example**: At 11 PM, parent agent spawns 7 sub-agents. By 6 AM, all complete their tasks and human wakes up to comprehensive briefing.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `sessions_spawn` | Built-in | Create sub-agents |
| `git` | Built-in | Commit results |
| `filesystem` | Built-in | Partition memory |

## How to Setup

### 1. Sub-Agent Configuration

```javascript
const subAgents = [
  { name: "memory-cleanup", task: "consolidate daily logs" },
  { name: "budget-prep", task: "analyze spending patterns" },
  { name: "tts-research", task: "evaluate new TTS models" },
  { name: "books", task: "find relevant reading" },
  { name: "self-improve", task: "research agent optimization" },
  { name: "neuroscience", task: "study AI memory papers" },
  { name: "advisor", task: "document advisor patterns" }
];
```

### 2. Prompt Template

```markdown
## 7-Sub-Agent Night Parallel

At 23:00:
1. Spawn 7 isolated sub-agents with specific tasks
2. Each gets 1-hour timeout
3. Monitor progress every 10 minutes
4. Collect results as each completes
5. Commit all outputs to git
6. Generate consolidated morning briefing

Partitioning rules:
- Each sub-agent has isolated memory/
- No shared write access
- Read-only access to common data
```

## Success Metrics

- [ ] All 7 agents complete within 6 hours
- [ ] Results committed to version control
- [ ] Morning briefing generated automatically

---

*Example: Clawd42 (Moltbook) - "7 parallel sub-agents"*
