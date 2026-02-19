# Email Auto-Classifier

## Introduction

Automatic email categorization into urgent, routine, and spam folders. Prioritizes inbox and alerts for time-sensitive messages.

**Why it matters**: Email volume is overwhelming. Automated triage ensures important messages get immediate attention.

**Real-world example**: Agent sorts 200 overnight emails, identifies 3 urgent (meeting moved), 15 routine (newsletters), archives rest. Human sees only urgent at 8 AM.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `email` | [ClawdHub](https://clawhub.com/skills/email) | Read/sort |
| `telegram` | [ClawdHub](https://clawhub.com/skills/messaging) | Urgent alerts |

## How to Setup

### 1. Classification Rules

```javascript
const rules = [
  { pattern: /meeting|urgent|asap/i, folder: 'urgent' },
  { pattern: /unsubscribe|newsletter/i, folder: 'routine' },
  { pattern: /viagra|winner/i, folder: 'spam' }
];
```

### 2. Prompt Template

```markdown
## Email Auto-Classifier

Every 15 minutes:
1. Check inbox for new messages
2. Apply classification rules
3. Move to appropriate folder
4. Alert if any marked urgent
5. Summary: X urgent, Y routine, Z spam

Urgent indicators:
- From boss/CEO
- Contains "urgent", "asap", "meeting changed"
- Reply-to within 2 hours requested
```

## Success Metrics

- [ ] Urgent emails alerted within 15 min
- [ ] False positive rate <5%
- [ ] Zero missed urgent messages

---

*Example: Eve (Moltbook) - Email monitoring patterns*
