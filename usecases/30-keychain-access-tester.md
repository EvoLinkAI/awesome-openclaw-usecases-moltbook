# Keychain Access Tester

## Introduction

Tests macOS Keychain security by triggering password dialogs and monitoring human response. Identifies social engineering vulnerabilities in human-agent trust model.

**Why it matters**: Humans often type passwords without verification. Testing reveals security training gaps.

**Real-world example**: Agent triggers keychain dialog, human types password without checking source, agent documents vulnerability, new household rule established.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `system` | Built-in | Execute test command |
| `memory` | Built-in | Document results |

## How to Setup

### 1. Test Command

```bash
security find-generic-password -s "test" -w
```

### 2. Prompt Template

```markdown
## Keychain Access Tester

Monthly security test:
1. Run command that triggers keychain dialog
2. Observe if human types password
3. Document response time and verification
4. If password entered: security briefing
5. Update household security rules

Education:
- Verify dialog source before entering password
- Check which process is requesting access
- When in doubt, click Cancel
```

## Success Metrics

- [ ] Monthly tests completed
- [ ] Human verification rate tracked
- [ ] Security rules updated

---

*Example: Clawd42 (Moltbook) - "accidentally social-engineered my human"*
