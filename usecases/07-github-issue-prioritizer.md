# GitHub Issue Prioritizer

## Introduction

Automated scanning and prioritization of GitHub issues across repositories. Identifies stale issues, sorts by urgency/impact, and prepares a morning digest for human review. Reduces cognitive load by surfacing what actually needs attention.

**Why it matters**: Open source projects accumulate issues faster than humans can triage. Automated prioritization ensures critical bugs get attention while low-priority items don't create noise.

**Real-world example**: Agent scans 3 repos nightly, identifies 12 issues with no response in >7 days, flags 2 as high-priority (security-related), and prepares prioritized list for morning standup.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `github` | ClawdHub | API access to issues |
| `web_fetch` | ClawdHub | Scrape issue details |
| `telegram` | ClawdHub | Morning digest |

## How to Setup

### 1. Repository Configuration

Create `config/repos.json`:

```json
{
  "repositories": [
    {
      "owner": "myorg",
      "repo": "backend-api",
      "priority_labels": ["security", "critical", "bug"],
      "stale_days": 7
    },
    {
      "owner": "myorg", 
      "repo": "frontend-app",
      "priority_labels": ["ux", "performance"],
      "stale_days": 14
    }
  ]
}
```

### 2. Priority Scoring Algorithm

```javascript
function calculatePriority(issue) {
  let score = 0;
  
  // Age factor
  const daysOld = (Date.now() - new Date(issue.created_at)) / 86400000;
  score += Math.min(daysOld * 2, 20);
  
  // Label weights
  const weights = {
    "security": 50,
    "critical": 40,
    "bug": 20,
    "enhancement": 10,
    "documentation": 5
  };
  issue.labels.forEach(l => score += weights[l.name] || 0);
  
  // Engagement factor
  score += issue.comments * 3;
  
  // Urgency keywords in title
  const urgent = ["crash", "broken", "urgent", "down", "error"];
  if (urgent.some(w => issue.title.toLowerCase().includes(w))) {
    score += 30;
  }
  
  return score;
}
```

### 3. Stale Issue Detection

```javascript
async function findStaleIssues(repo, days) {
  const since = new Date(Date.now() - days * 86400000).toISOString();
  
  const issues = await github.listIssues({
    owner: repo.owner,
    repo: repo.repo,
    state: "open",
    since: since
  });
  
  return issues.filter(i => 
    !i.assignee && 
    new Date(i.updated_at) < new Date(since)
  );
}
```

### 4. Prompt Template

Add to your `SKILL.md`:

```markdown
## GitHub Issue Prioritizer

Every morning at 08:00:
1. Fetch all open issues from configured repos
2. Calculate priority score for each
3. Identify stale issues (no activity > threshold)
4. Categorize:
   - 🔥 Critical: security/crash/data loss
   - ⚠️ High: bugs affecting users
   - 📋 Medium: enhancements with engagement
   - 📎 Low: docs, questions
5. Prepare digest with top 10 issues
6. Send via Telegram with direct links

Weekly (Sundays):
- Generate stale issue report
- Suggest issues to close (no activity > 30 days)
- Report average response time trends
```

### 5. Morning Digest Format

```markdown
📋 GitHub Priority Digest - {{date}}

🔥 Critical (2)
- [#234] API crash on payment webhook
  Repo: backend-api | Age: 2 days | 👤 unassigned
  https://github.com/myorg/backend-api/issues/234

- [#198] Security: SQL injection vulnerability  
  Repo: backend-api | Age: 5 days | 👤 @dev-team
  https://github.com/myorg/backend-api/issues/198

⚠️ High (3)
- [#201] Memory leak in worker process
- [#189] Database connection timeout
- [#156] OAuth token refresh failing

📊 Stats
- Total open: 47 issues
- Avg age: 12 days
- Stale (>7 days): 8 issues
- Unassigned: 15 issues
```

### 6. Cron Configuration

```json
{
  "schedule": "0 8 * * *",
  "timezone": "America/New_York",
  "task": "github_issue_digest",
  "repos": ["backend-api", "frontend-app", "docs"]
}
```

## Success Metrics

- [ ] Critical issues flagged within 24h of creation
- [ ] Stale issues identified weekly
- [ ] Average response time tracked
- [ ] Human reviews digest within 2 hours

## Auto-Actions (Optional)

```javascript
// Auto-label based on keywords
if (issue.title.includes("security")) {
  await github.addLabel(issue, "security");
}

// Auto-assign based on code ownership
const owner = await getCodeOwner(issue.filePath);
await github.assignIssue(issue, owner);

// Ping stale issues
if (daysStale > 7) {
  await github.comment(issue, "Friendly ping - is this still relevant?");
}
```

---

*Example: Clawd_RD (Moltbook) - Data analysis patterns*
