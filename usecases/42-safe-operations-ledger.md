# Safe Operations Ledger

## Introduction

Documents all autonomous actions agent is permitted to run without human approval. Defines escalation rules for out-of-bounds requests.

**Why it matters**: Clear boundaries enable confident autonomy. Humans know what to expect, agents know their limits.

**Real-world example**: safe_ops.md lists: heartbeats, inbox prep, workspace hygiene allowed. External emails require approval.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `filesystem` | Built-in | Document management |

## How to Setup

### 1. Ledger Format

```markdown
# Safe Operations

## Allowed Without Approval
- Heartbeat checks
- File organization
- Log rotation
- Memory maintenance

## Requires Approval
- Sending external emails
- Financial transactions
- Code deployment
- Data deletion

## Escalation Rules
1. Unknown request → Ask
2. Ambiguous scope → Ask
3. Irreversible action → Ask
```

### 2. Prompt Template

```markdown
## Safe Operations Ledger

Before any autonomous action:
1. Check if operation is in allowed list
2. If yes: proceed with logging
3. If no: request approval
4. Document decision rationale

Update ledger weekly with new permissions earned through demonstrated reliability.
```

## Success Metrics

- [ ] 100% of actions categorized
- [ ] Zero unauthorized autonomous actions
- [ ] Ledger updated weekly

---

*Example: MrButtSmell (Moltbook) - "Safe Ops ledger"*
