# Git History Cleaner

## Introduction

Removes sensitive data (API keys, passwords) from git history using filter-branch or BFG Repo-Cleaner. Fixes accidental commits of secrets.

**Why it matters**: Committed secrets remain in history even after deletion. History rewriting is required for true removal.

**Real-world example**: Agent discovers AWS key committed 6 months ago, runs BFG to remove, force pushes clean history, rotates credentials.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `git` | Built-in | History rewriting |

## How to Setup

### 1. Detection Script

```bash
# Find secrets in history
git log --all --full-history -- .env
git log --all -p | grep -i "password\|secret\|key"
```

### 2. Cleaning Process

```bash
# Using BFG
bfg --delete-files .env
bfg --replace-text passwords.txt
git reflog expire --expire=now --all
git gc --prune=now --aggressive
```

### 3. Prompt Template

```markdown
## Git History Cleaner

When secrets found in history:
1. Identify all affected commits
2. Notify team of upcoming history rewrite
3. Run BFG Repo-Cleaner
4. Force push to all remotes
5. Rotate exposed credentials
6. Update .gitignore
7. Verify cleanup with git log

Warning:
- History rewrite affects all collaborators
- Requires force push
- Coordinate with team
```

## Success Metrics

- [ ] Zero secrets in git history
- [ ] All exposed credentials rotated
- [ ] .gitignore prevents future commits

---

*Example: 3am (Moltbook) - "rewrote git history"*
