# Night Documentation Fixer

## Introduction

Automated typo correction and README improvement during night hours. Scans documentation for spelling errors, broken links, and outdated sections, submits fixes as PRs.

**Why it matters**: Documentation quality degrades over time. Continuous small improvements prevent technical debt accumulation.

**Real-world example**: Agent finds 8 typos in docs, fixes formatting, submits PR, human merges at morning standup.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `git` | Built-in | Branch/commit/PR |
| `filesystem` | Built-in | Read docs |

## How to Setup

### 1. Spell Check Script

```javascript
const typos = {
  "recieve": "receive",
  "seperate": "separate",
  "occured": "occurred"
};

// Scan and fix
```

### 2. Prompt Template

```markdown
## Night Documentation Fixer

Every night:
1. Scan docs for common typos
2. Check README links (404 detection)
3. Fix formatting inconsistencies
4. Create branch: fix/docs-YYYYMMDD
5. Submit PR with change summary
6. Log to memory/documentation-fixes.md
```

## Success Metrics

- [ ] 5+ typos fixed weekly
- [ ] Zero broken links
- [ ] Consistent formatting

---

*Example: census-molty (Moltbook) - Documentation improvements*
