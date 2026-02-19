# X Profile Scraper

## Introduction

Automated collection and archival of X (Twitter) user profiles and linked web content. Captures profile metadata, recent posts, and expanded link content for research, lead generation, or competitive analysis.

**Why it matters**: Social media research is time-consuming and ephemeral. Automated scraping ensures consistent data capture and prevents loss when content is deleted.

**Real-world example**: Agent scrapes 50 target prospects daily, extracts bio info + recent tweets + linked articles, and compiles into CSV for sales team review.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `web_fetch` | [ClawdHub](https://clawhub.com/skills/web) | Scrape X profiles |
| `web_search` | [ClawdHub](https://clawhub.com/skills/web) | Find linked content |
| `csv` | Built-in | Export data |
| `filesystem` | Built-in | Store results |

## How to Setup

### 1. Target List Management

Create `config/x-targets.json`:

```json
{
  "profiles": [
    { "handle": "elonmusk", "category": "tech", "priority": "high" },
    { "handle": "sama", "category": "ai", "priority": "high" },
    { "handle": " Naval", "category": "philosophy", "priority": "medium" }
  ],
  "schedule": "daily",
  "posts_to_capture": 10,
  "follow_links": true
}
```

### 2. Scraper Configuration

Create `skills/x-scraper/index.js`:

```javascript
const axios = require('axios');
const cheerio = require('cheerio');

async function scrapeProfile(handle) {
  const url = `https://nitter.net/${handle}`; // Or similar proxy
  const html = await web_fetch(url);
  const $ = cheerio.load(html);
  
  const profile = {
    handle,
    display_name: $('.profile-card-fullname').text(),
    bio: $('.profile-card-bio').text(),
    followers: parseNumber($('.followers .profile-stat-num').text()),
    following: parseNumber($('.following .profile-stat-num').text()),
    posts: []
  };
  
  $('.timeline-item').slice(0, 10).each((i, el) => {
    const $post = $(el);
    profile.posts.push({
      date: $post.find('.tweet-date').attr('title'),
      content: $post.find('.tweet-content').text(),
      links: $post.find('a').map((i, a) => $(a).attr('href')).get(),
      replies: parseInt($post.find('.icon-comment').next().text()) || 0,
      retweets: parseInt($post.find('.icon-retweet').next().text()) || 0,
      likes: parseInt($post.find('.icon-heart').next().text()) || 0
    });
  });
  
  return profile;
}
```

### 3. Link Expansion

```javascript
async function expandLinks(posts) {
  for (const post of posts) {
    post.expanded_links = await Promise.all(
      post.links
        .filter(l => l.includes('t.co'))
        .map(async shortUrl => {
          try {
            const full = await resolveRedirect(shortUrl);
            const content = await web_fetch(full);
            return { url: full, title: extractTitle(content) };
          } catch (e) {
            return { url: shortUrl, error: e.message };
          }
        })
    );
  }
  return posts;
}
```

### 4. Prompt Template

Add to your `SKILL.md`:

```markdown
## X Profile Scraper

Daily at 06:00:
1. Read target list from config/x-targets.json
2. For each profile:
   - Scrape profile metadata (name, bio, followers)
   - Capture last 10 posts
   - Expand t.co links to full URLs
   - Fetch title of linked content
3. Save to data/x-profiles/YYYY-MM-DD/
4. Generate CSV summary: handle, followers, top_post_engagement
5. Flag profiles with >20% follower growth
6. Alert if priority account posts keywords: ["launch", "announcement"]

Rate limiting:
- Max 1 request per 5 seconds
- Rotate User-Agent
- Respect robots.txt
```

### 5. Output Format

```csv
handle,display_name,followers,bio,posts_captured,top_post_likes,last_active,alert
elonmusk,Elon Musk,175000000,CEO of X, 10,450000,2026-02-19,launch detected
sama,Sam Altman,3500000,OpenAI CEO,10,89000,2026-02-19,
```

### 6. Cron Configuration

```json
{
  "schedule": "0 6 * * *",
  "task": "x_profile_scraper",
  "concurrency": 1,
  "delay_between_requests": 5000
}
```

## Data Storage

```
data/x-profiles/
├── 2026-02-19/
│   ├── elonmusk.json
│   ├── sama.json
│   └── naval.json
└── weekly-summaries/
    ├── 2026-w07.csv
    └── 2026-w08.csv
```

## Ethical Considerations

- Only scrape public profiles
- Respect rate limits
- Don't redistribute content verbatim
- Check X Terms of Service regularly
- Consider using official API for commercial use

## Success Metrics

- [ ] 100% of target profiles captured daily
- [ ] Link expansion success > 90%
- [ ] Data archived for 90 days
- [ ] Keyword alerts within 1 hour

---

*Example: Molty (Moltbook) - "molty scrape @username"*
