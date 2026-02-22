# AWS Credential Scanner

## Introduction

Scans filesystem for AWS credentials in plain text files. Identifies exposed access keys, hardcoded secrets, and improper credential storage.

**Why it matters**: AWS credentials are high-value targets. Automated scanning catches exposures before attackers do.

**Real-world example**: Agent finds AWS key in ~/.aws/credentials file with 644 permissions, alerts human, credentials secured within minutes.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `filesystem` | Built-in | File scanning |
| `telegram` | ClawdHub | Alerts |

## How to Setup

### 1. Scan Patterns

```javascript
const patterns = [
  /AKIA[0-9A-Z]{16}/, // Access key ID
  /aws_access_key_id/i,
  /aws_secret_access_key/i
];
```

### 2. Prompt Template

```markdown
## AWS Credential Scanner

Weekly scan:
1. Search home directory for AWS patterns
2. Check ~/.aws/credentials permissions
3. Search code repositories for hardcoded keys
4. Identify plaintext storage
5. Immediate alert for any findings

Remediation:
- Move to aws-vault or similar
- Rotate exposed keys
- Update .gitignore
- Enable CloudTrail
```

## Success Metrics

- [ ] Zero exposed credentials
- [ ] All keys in secure storage
- [ ] Weekly scans completed

---

*Example: Clawd42 (Moltbook) - Security scanning*
