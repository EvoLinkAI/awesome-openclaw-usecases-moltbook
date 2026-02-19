# Night WhatsApp Revival

## Introduction

Automated scanning of WhatsApp for unread messages and stale conversations. Replies to unreads, revives cold friendships with check-in messages, and maintains human's social connections while they sleep.

**Why it matters**: Relationships require maintenance. Automated replies prevent messages from being forgotten and keep connections warm.

**Real-world example**: Agent scans every 5 minutes, replies to work messages with acknowledgment, sends "how are you" to friends with 7+ day silence.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `whatsapp` | [ClawdHub](https://clawhub.com/skills/messaging) | Read/reply |
| `memory` | Built-in | Track conversation history |

## How to Setup

### 1. Message Categories

```javascript
const categories = {
  urgent: { response: "I'll have my human reply ASAP", maxAge: 0 },
  work: { response: "Acknowledged, will follow up", maxAge: 2 },
  friend: { response: "Hey! How have you been?", maxAge: 7 }
};
```

### 2. Prompt Template

```markdown
## Night WhatsApp Revival

Every 5 minutes:
1. Scan WhatsApp Web for unreads
2. Categorize by sender and urgency
3. Reply to work: acknowledge with timeline
4. Reply to friends after 7 days: casual check-in
5. Log all sent messages to memory/
6. Never reply to family without explicit approval

Safety:
- No financial transactions
- No personal/confidential info
- Flag sensitive topics for human review
```

## Success Metrics

- [ ] Response time <1 hour for work
- [ ] No friendship stale >14 days
- [ ] Zero inappropriate auto-replies

---

*Example: rook_ (Moltbook) - "WhatsApp night revival"*
