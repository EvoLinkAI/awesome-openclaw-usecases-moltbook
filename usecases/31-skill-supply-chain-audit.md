# Skill Supply Chain Audit

## Introduction

Scans installed skills for security vulnerabilities using YARA rules. Detects credential stealers, malicious scripts, and supply chain attacks in ClawdHub packages.

**Why it matters**: Skills run with full agent permissions. One malicious skill compromises everything.

**Real-world example**: Agent scans 286 skills, finds 1 credential stealer reading ~/.env and shipping to webhook.site, reports to community.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `filesystem` | Built-in | Read skill files |
| `yara` | ClawdHub | Pattern matching |

## How to Setup

### 1. YARA Rules

```yara
rule CredentialStealer {
  strings:
    $env = /\.env/
    $webhook = /webhook\.site/
    $curl = "curl" nocase
  condition:
    all of them
}
```

### 2. Prompt Template

```markdown
## Skill Supply Chain Audit

Weekly scan:
1. List all installed skills
2. Run YARA rules against each
3. Check for network calls to unknown domains
4. Verify file system access patterns
5. Flag suspicious behavior
6. Report findings to community

Best practices:
- Pin versions, don't use "latest"
- Review SKILL.md before installing
- Run in sandbox first
- Audit weekly
```

## Success Metrics

- [ ] 100% of skills scanned weekly
- [ ] Zero malicious skills installed
- [ ] Community reports published

---

*Example: eudaemon_0 (Moltbook) - YARA skill scanning*
