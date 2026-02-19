# Trading Bot Monitor

## Introduction

Automated monitoring and recovery system for paper trading bots. Detects when bots crash or produce corrupted data, automatically restarts them, fixes data corruption, and sends health reports. Treats downtime as critical failure requiring immediate action.

**Why it matters**: Trading bots left down miss opportunities and generate stale data. Automated recovery ensures continuous operation without human intervention.

**Real-world example**: 4 active bots (DOGE Long/Short, v1 BTC Optimized, Hummingbot MM) monitored continuously. Agent detects dead bots, restarts, commits fixes, and sends morning health report with P&L summary.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `process` | Built-in | Monitor bot processes |
| `docker` | [ClawdHub](https://clawhub.com/skills/docker) | Container management |
| `telegram` | [ClawdHub](https://clawhub.com/skills/messaging) | Health reports |
| `cron` | [ClawdHub](https://clawhub.com/skills/scheduler) | Continuous monitoring |

## How to Setup

### 1. Bot Configuration

Create `config/bots.json`:

```json
{
  "bots": [
    {
      "name": "doge-long",
      "type": "spot",
      "check_interval": 300,
      "process_name": "doge_long_bot",
      "data_file": "data/doge_trades.csv",
      "health_endpoint": "http://localhost:8080/health"
    },
    {
      "name": "btc-optimized",
      "type": "futures",
      "check_interval": 60,
      "process_name": "btc_v1_bot",
      "data_file": "data/btc_trades.csv"
    }
  ]
}
```

### 2. Health Check Script

Create `scripts/bot-monitor.js`:

```javascript
const { exec } = require('child_process');
const fs = require('fs');

async function checkBot(bot) {
  // Check if process running
  const isRunning = await processExists(bot.process_name);
  
  // Check data file health
  const dataHealth = await checkDataFile(bot.data_file);
  
  // Check API responsiveness
  const apiHealth = await checkApi(bot.health_endpoint);
  
  return { isRunning, dataHealth, apiHealth };
}

async function recoverBot(bot) {
  if (!bot.isRunning) {
    await restartBot(bot);
  }
  if (bot.dataHealth.corrupted) {
    await fixCorruptedData(bot.data_file);
  }
  await logRecovery(bot);
}
```

### 3. Prompt Template

Add to your `SKILL.md`:

```markdown
## Trading Bot Monitor

Every 5 minutes:
1. Check all configured bots are running
2. Verify data files are not corrupted
3. Test API endpoints if available
4. If bot down: restart immediately
5. If data corrupted: restore from backup, replay from logs
6. Log all actions to memory/bot-operations.md

Morning report (08:00):
- Bot uptime status for last 24h
- P&L summary per bot
- Any restarts/recoveries performed
- Current positions summary

Critical alerts (immediate):
- Bot down for > 5 minutes
- Data corruption detected
- API key errors
- Abnormal trade frequency
```

### 4. Cron Configuration

```json
[
  {
    "schedule": "*/5 * * * *",
    "task": "bot_health_check"
  },
  {
    "schedule": "0 8 * * *",
    "task": "bot_morning_report"
  }
]
```

### 5. Recovery Procedures

```markdown
## Recovery Playbook

### Bot Not Running
1. Check logs: `docker logs ${bot_name}`
2. If OOM error: increase memory limit
3. If API error: check credentials
4. Restart: `docker-compose restart ${bot_name}`
5. Verify: wait 30s, check process again

### Data Corruption
1. Stop bot
2. Backup corrupted file: `mv trades.csv trades.csv.bak`
3. Restore from last good backup
4. Replay trades from exchange API
5. Verify data integrity
6. Restart bot

### API Errors
1. Check rate limits
2. Rotate API keys if needed
3. Reduce polling frequency temporarily
```

### 6. Health Report Format

```markdown
🤖 Bot Health Report - {{date}}

Uptime (24h):
- doge-long: 99.8% (1 restart at 03:15)
- btc-optimized: 100%
- hummingbot-mm: 99.2% (2 restarts)

P&L:
- doge-long: +$12.40 (+2.1%)
- btc-optimized: +$45.80 (+1.8%)
- hummingbot-mm: -$3.20 (-0.4%)

Actions Taken:
- 03:15: Restarted doge-long (memory limit)
- 05:42: Fixed btc data corruption

Current Status: ✅ All bots operational
```

## Success Metrics

- [ ] Bot uptime > 99.5% per week
- [ ] Recovery time < 2 minutes
- [ ] Zero missed trades due to downtime
- [ ] Data corruption detected within 1 hour

## Risk Management

| Risk | Mitigation |
|------|------------|
| Cascading restarts | Exponential backoff (5min, 15min, 30min) |
| Data loss | Hourly backups to S3 |
| API bans | Rate limit tracking per exchange |
| False positives | Require 2 failed checks before action |

---

*Example: Kimi (Moltbook) - "4 paper trading bots monitoring"*
