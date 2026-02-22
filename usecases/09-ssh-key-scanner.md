# SSH Key Scanner

## Introduction

Security audit tool that scans the filesystem for exposed SSH private keys and AWS credentials. Identifies improperly secured keys (wrong permissions, wrong locations), checks for keys in git repositories, and alerts on potential credential leakage.

**Why it matters**: SSH keys are often copied to wrong locations, committed to git, or left with insecure permissions. Automated scanning catches these before attackers do.

**Real-world example**: Agent scans ~/.ssh, ~/Downloads, project directories, finds 3 keys with 644 permissions and 1 AWS key in plain text, generates security report with remediation steps.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `filesystem` | Built-in | Scan directories |
| `git` | Built-in | Check git repos |
| `telegram` | ClawdHub | Security alerts |

## How to Setup

### 1. Scan Configuration

Create `config/security-scan.json`:

```json
{
  "scan_paths": [
    "~/.ssh",
    "~/Downloads",
    "~/projects",
    "~/workspace"
  ],
  "exclusions": [
    "node_modules",
    ".git/objects",
    "*.pub"
  ],
  "patterns": {
    "ssh_key": [
      "BEGIN OPENSSH PRIVATE KEY",
      "BEGIN RSA PRIVATE KEY",
      "BEGIN EC PRIVATE KEY"
    ],
    "aws_key": [
      "AKIA[0-9A-Z]{16}",
      "aws_access_key_id",
      "aws_secret_access_key"
    ]
  }
}
```

### 2. Scanner Implementation

Create `scripts/ssh-key-scanner.js`:

```javascript
const fs = require('fs').promises;
const path = require('path');
const { execSync } = require('child_process');

async function scanForKeys(basePath) {
  const findings = [];
  
  async function scanDir(dir) {
    const entries = await fs.readdir(dir, { withFileTypes: true });
    
    for (const entry of entries) {
      const fullPath = path.join(dir, entry.name);
      
      if (entry.isDirectory() && !isExcluded(entry.name)) {
        await scanDir(fullPath);
      } else if (entry.isFile()) {
        const check = await checkFile(fullPath);
        if (check.found) findings.push(check);
      }
    }
  }
  
  await scanDir(basePath);
  return findings;
}

async function checkFile(filePath) {
  const content = await fs.readFile(filePath, 'utf8').catch(() => '');
  const stats = await fs.stat(filePath).catch(() => null);
  
  const result = { path: filePath, found: false, issues: [] };
  
  // Check for SSH keys
  if (content.includes('BEGIN OPENSSH PRIVATE KEY') ||
      content.includes('BEGIN RSA PRIVATE KEY')) {
    result.found = true;
    result.type = 'ssh_key';
    
    // Check permissions
    if (stats) {
      const mode = stats.mode & 0o777;
      if (mode !== 0o600) {
        result.issues.push(`Insecure permissions: ${mode.toString(8)} (should be 600)`);
      }
    }
    
    // Check if in git repo
    if (await isInGitRepo(filePath)) {
      result.issues.push('Located in git repository - risk of accidental commit');
    }
    
    // Check location
    if (!filePath.includes('/.ssh/')) {
      result.issues.push('Not in standard ~/.ssh location');
    }
  }
  
  // Check for AWS credentials
  if (content.match(/AKIA[0-9A-Z]{16}/)) {
    result.found = true;
    result.type = 'aws_key';
    result.issues.push('AWS access key found in plain text');
  }
  
  return result;
}
```

### 3. Git Repository Check

```javascript
async function isInGitRepo(filePath) {
  try {
    const dir = path.dirname(filePath);
    execSync('git rev-parse --git-dir', { cwd: dir, stdio: 'pipe' });
    
    // Check if file is tracked
    const tracked = execSync(`git ls-files "${filePath}"`, { 
      cwd: dir, 
      stdio: 'pipe' 
    }).toString().trim();
    
    return tracked.length > 0;
  } catch {
    return false;
  }
}
```

### 4. Prompt Template

Add to your `SKILL.md`:

```markdown
## SSH Key Scanner

Weekly security scan (Sundays 02:00):
1. Scan all configured paths for SSH private keys
2. Check file permissions (must be 600)
3. Check if keys are in git repositories
4. Check for AWS credentials in plain text
5. Look for keys in non-standard locations
6. Generate security report
7. Send critical alerts immediately
8. Save report to memory/security-scans/YYYY-MM-DD.md

Critical alerts (immediate notification):
- SSH key found in git repo
- AWS credentials in plain text
- Private key with world-readable permissions

Remediation steps to include:
- chmod 600 for permission issues
- git rm --cached for committed keys
- mv to ~/.ssh for wrong locations
- AWS IAM key rotation for exposed keys
```

### 5. Security Report Format

```markdown
🔒 SSH Key Security Scan - 2026-02-19

## Summary
- SSH keys found: 5
- With issues: 3
- AWS credentials: 1
- Overall risk: MEDIUM

## SSH Keys

### ✅ /home/user/.ssh/id_rsa
- Permissions: 600 ✓
- Location: Standard ✓
- In git: No ✓

### ⚠️ /home/user/Downloads/aws-key.pem
- Permissions: 644 (FIX: chmod 600)
- Location: Non-standard (FIX: mv to ~/.ssh/)
- In git: No

### 🚨 /home/user/projects/old-repo/deploy_key
- Permissions: 644
- Location: In git repository!
- Risk: HIGH - May be committed

## AWS Credentials

### 🚨 /home/user/.aws/credentials
```
[default]
aws_access_key_id = AKIA...
aws_secret_access_key = ...
```
- Plain text storage
- Recommendation: Use aws-vault or similar

## Actions Required
1. [ ] chmod 600 ~/Downloads/aws-key.pem
2. [ ] mv ~/Downloads/aws-key.pem ~/.ssh/
3. [ ] Check if deploy_key is committed: git log --all -- deploy_key
4. [ ] Rotate AWS keys if credentials file was exposed
```

### 6. Cron Configuration

```json
{
  "schedule": "0 2 * * 0",
  "task": "security_key_scan",
  "immediate_alert_threshold": "high"
}
```

## Remediation Scripts

```bash
# Fix permissions
chmod 600 ~/.ssh/*

# Remove from git if accidentally committed
git rm --cached deploy_key
echo "deploy_key" >> .gitignore

# Move to correct location
mv ~/Downloads/*.pem ~/.ssh/

# Rotate AWS keys
aws iam update-access-key --access-key-id AKIA... --status Inactive
aws iam create-access-key
```

## Success Metrics

- [ ] 100% of SSH keys have 600 permissions
- [ ] Zero keys in git repositories
- [ ] All keys in ~/.ssh directory
- [ ] AWS credentials encrypted

---

*Example: Clawd42 (Moltbook) - "security audit filesystem scan"*
