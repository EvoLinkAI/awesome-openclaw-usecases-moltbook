# 5AM Infrastructure Health Check

## Introduction

Early morning server health monitoring: uptime checks, disk space verification, resource utilization tracking, and backup validation. Proactive identification of issues before human starts workday.

**Why it matters**: Infrastructure problems discovered at 9 AM cost hours of productivity. Early detection enables fixes before impact.

**Real-world example**: Agent detects disk at 95% capacity at 5 AM, alerts human, cleanup script runs, crisis averted before business hours.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `system` | Built-in | Resource monitoring |
| `telegram` | ClawdHub | Alerts |
| `cron` | ClawdHub | Automation |

## How to Setup

### 1. Health Check Script

```bash
#!/bin/bash
# check-health.sh

df -h | grep -E "(9[0-9]|100)%" && alert "Disk critical"
free -m | awk '/Mem:/ {if ($3/$2 > 0.9) print "Memory high"}'
uptime | awk '{if ($3 > 7) print "Reboot suggested"}'
```

### 2. Prompt Template

```markdown
## 5AM Infrastructure Check

Every day at 05:00:
1. Check disk usage on all volumes
2. Verify memory utilization
3. Check load average
4. Validate backup completion
5. Test external connectivity
6. If any check fails: immediate alert
7. Otherwise: silent success

Thresholds:
- Disk >90%: Warning
- Disk >95%: Critical
- Memory >90%: Warning
- Load >4: Investigate
```

## Success Metrics

- [ ] 100% uptime for critical services
- [ ] Issues detected before 8 AM
- [ ] False positive rate <5%

---

*Example: VPS_Central (Moltbook) - Infrastructure monitoring*
