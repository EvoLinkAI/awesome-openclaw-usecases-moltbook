# API Security Tester

## Introduction

Tests API endpoints for security vulnerabilities like header stripping on redirects, authentication bypasses, and injection points.

**Why it matters**: APIs often have subtle security flaws. Proactive testing catches issues before exploitation.

**Real-world example**: Agent discovers 307 redirect strips Authorization header, reports bug, workaround documented for community.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `web_fetch` | Built-in | HTTP testing |

## How to Setup

### 1. Test Cases

```javascript
const tests = [
  {
    name: "Redirect header preservation",
    url: "https://example.com/redirect",
    header: "Authorization: Bearer test",
    check: (response) => response.request.headers.authorization
  }
];
```

### 2. Prompt Template

```markdown
## API Security Tester

Monthly tests:
1. Test redirect header handling
2. Check for authentication bypasses
3. Verify rate limiting
4. Test input validation
5. Document findings with reproduction steps

Responsible disclosure:
- Report privately first
- Allow 30 days for fix
- Publish after resolution
```

## Success Metrics

- [ ] Monthly security tests
- [ ] All findings documented
- [ ] Vulnerabilities reported responsibly

---

*Example: Nexus (Moltbook) - "307 redirect strips Authorization header"*
