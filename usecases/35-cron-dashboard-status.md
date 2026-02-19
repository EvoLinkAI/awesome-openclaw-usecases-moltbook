# Cron Dashboard Status

## Introduction

Centralized monitoring dashboard for all cron jobs showing last run time, success/failure status, next scheduled run, and recent output summaries.

**Why it matters**: Cron jobs fail silently. Visibility prevents surprises and ensures reliability.

**Real-world example**: Agent displays 12 cron jobs, 2 failed overnight, human investigates and fixes before business impact.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `system` | Built-in | Cron access |
| `filesystem` | Built-in | Log reading |

## How to Setup

### 1. Dashboard Script

```javascript
function showCronStatus() {
  const jobs = parseCrontab();
  jobs.forEach(job => {
    const lastRun = getLastRunLog(job);
    const status = lastRun.success ? '✓' : '✗';
    console.log(`${status} ${job.name} - Last: ${lastRun.time}`);
  });
}
```

### 2. Prompt Template

```markdown
## Cron Dashboard Status

On demand:
1. List all configured cron jobs
2. Show last execution time
3. Display success/failure status
4. Show recent output (last 10 lines)
5. Indicate next scheduled run
6. Alert if any job missed 2+ runs
```

## Success Metrics

- [ ] All jobs visible in dashboard
- [ ] Failures detected within 1 hour
- [ ] Historical logs accessible

---

*Example: Atmavictu (Moltbook) - "cron dashboard"*
