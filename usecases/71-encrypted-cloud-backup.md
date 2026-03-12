# Encrypted Cloud Backup and Disaster Recovery

## Introduction

Automated encrypted cloud backup of your entire OpenClaw workspace: memory, cron jobs, skills, credentials, and config. Scheduled backups run silently, snapshots are verifiable, and restore works across machines.

**Why it matters**: OpenClaw agents accumulate irreplaceable state over weeks and months: memory files, learned preferences, cron schedules, custom skills, and API credentials. A disk failure, botched update, or migration to new hardware without a backup means starting from zero.

**Real-world example**: Agent runs nightly encrypted backups to Cloudflare R2. When migrating to a new Mac Mini, operator restores the latest snapshot and the agent resumes with full memory, all cron jobs, and every skill intact. Zero re-onboarding.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `keepmyclaw` | [ClawHub](https://clawhub.com/Ryce/keepmyclaw) | Encrypted backup and restore |
| `cron` | Built-in | Schedule automatic backups |

## How to Setup

### 1. Install and Configure

```bash
clawhub install keepmyclaw
```

Subscribe at [keepmyclaw.com](https://keepmyclaw.com) to get an API key ($5/mo or $19/yr for up to 100 agents).

### 2. Prompt Template

```markdown
## Nightly Encrypted Backup

Set up keepmyclaw with:
- API key from success page
- Encryption passphrase (stored locally, never sent to server)
- Daily backup schedule via cron (e.g., 3 AM)

After first backup:
1. Verify with GET /v1/snapshots
2. Run a safe restore drill into /tmp/restore-check
3. Confirm workspace files match

Keep passphrase safe — it's the only way to decrypt backups.
```

### 3. Verify It Works

```bash
# Check your latest snapshot
curl -s -H "Authorization: Bearer YOUR_API_KEY" \
  https://api.keepmyclaw.com/v1/snapshots | jq '.[0]'

# Safe restore drill (non-destructive)
curl -s -H "Authorization: Bearer YOUR_API_KEY" \
  https://api.keepmyclaw.com/v1/snapshots/latest/download -o /tmp/backup.enc
# Decrypt and extract to temp directory to verify contents
```

## Success Metrics

- [ ] Daily backups completing on schedule
- [ ] Latest snapshot timestamp within 24 hours
- [ ] Restore drill passes monthly (files match working state)
- [ ] Cross-machine restore tested at least once

---

*Backup is the difference between "my agent has months of context" and "I'm starting over from scratch."*
