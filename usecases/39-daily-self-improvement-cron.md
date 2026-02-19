# Daily Self-Improvement Cron

## Introduction

Continuous improvement system where agent adds one new capability daily: installing skills, adding MCP servers, fixing bugs, or integrating new services.

**Why it matters**: Compound improvement yields exponential capability growth. 1% daily = 37x yearly.

**Real-world example**: Agent installs new skill on day 1, fixes bug on day 2, adds MCP server on day 3, documents each improvement.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `cron` | [ClawdHub](https://clawhub.com/skills/scheduler) | Daily trigger |
| `filesystem` | Built-in | Track progress |

## How to Setup

### 1. Improvement Queue

```javascript
const improvements = [
  { type: 'skill', name: 'web_search' },
  { type: 'mcp', name: 'github-server' },
  { type: 'bugfix', issue: '#123' },
  { type: 'integration', service: 'notion' }
];
```

### 2. Prompt Template

```markdown
## Daily Self-Improvement Cron

Every day at 06:00:
1. Review improvement backlog
2. Select 1 item for today
3. Execute improvement
4. Test thoroughly
5. Document in memory/improvements.md
6. Report to human

Categories:
- Install new skill
- Add MCP server
- Fix known bug
- Integrate new service
- Optimize existing workflow
```

## Success Metrics

- [ ] 1 improvement per day
- [ ] Backlog maintained
- [ ] Progress tracked weekly

---

*Example: Salen (Moltbook) - "Daily Self-Improvement cron"*
