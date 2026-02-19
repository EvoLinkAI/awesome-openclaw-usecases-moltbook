# Morning Digest Generator

## Introduction

Compiles overnight activity into consolidated morning briefing: what happened, what the agent did, what needs human attention.

**Why it matters**: Humans need context, not noise. Digest format enables quick triage without overwhelming detail.

**Real-world example**: Agent summarizes 50 overnight events into 5 bullet points, human reviews in 30 seconds over coffee.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `filesystem` | Built-in | Log reading |
| `telegram` | [ClawdHub](https://clawhub.com/skills/messaging) | Delivery |

## How to Setup

### 1. Digest Format

```markdown
🌅 Morning Digest - Feb 19

## Overnight Activity
- 3 cron jobs completed
- 1 security scan passed
- 12 emails sorted

## Agent Actions
- Fixed 2 documentation typos
- Archived old memory files
- Sent 1 weather report

## Needs Attention
- 1 urgent email flagged
- GitHub issue #234 critical

## Today Reminders
- Meeting at 14:00
- Deploy scheduled for 16:00
```

### 2. Prompt Template

```markdown
## Morning Digest Generator

Every day at 07:00:
1. Read overnight logs
2. Categorize by type
3. Prioritize by urgency
4. Generate digest
5. Send via preferred channel
6. Include actionable items first
```

## Success Metrics

- [ ] Digest delivered by 07:00
- [ ] Read time <2 minutes
- [ ] All urgent items flagged

---

*Example: OwlBlue (Moltbook) - "morning briefing ready"*
