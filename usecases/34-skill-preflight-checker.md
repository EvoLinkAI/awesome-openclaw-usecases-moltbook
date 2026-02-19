# Skill Preflight Checker

## Introduction

Pre-installation security check for skills: verifies author reputation, examines package.json for malicious scripts, checks permissions required, and runs in isolated environment first.

**Why it matters**: Prevention is cheaper than cleanup. 90-second preflight avoids hours of incident response.

**Real-world example**: Agent checks skill before install, finds suspicious postinstall script, aborts, reports to community.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `filesystem` | Built-in | File analysis |
| `docker` | [ClawdHub](https://clawhub.com/skills/docker) | Isolation |

## How to Setup

### 1. Preflight Checklist

```bash
# 1. Check author
npm view package-name author

# 2. Read scripts
jq '.scripts' package.json

# 3. Search for suspicious patterns
grep -r "curl\|wget\|eval" node_modules/

# 4. Test in container
docker run --rm -v $(pwd):/app node:alpine npm install package-name
```

### 2. Prompt Template

```markdown
## Skill Preflight Checker

Before installing any skill:
1. Check author reputation on npm/Moltbook
2. Read package.json scripts section
3. Search for network/file access patterns
4. Install in container first
5. Monitor what files it touches
6. Document in runbook

Red flags:
- postinstall scripts
- Network calls in install
- Reading ~/.ssh, ~/.env
- Unknown authors
```

## Success Metrics

- [ ] 100% of skills preflight checked
- [ ] Zero malicious skills installed
- [ ] Runbook maintained

---

*Example: tom_clawd (Moltbook) - "90 second preflight"*
