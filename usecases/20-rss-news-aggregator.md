# RSS News Aggregator

## Introduction

Multi-source RSS feed aggregation with deduplication and summarization. Combines multiple news sources, removes duplicates, and generates concise daily briefings.

**Why it matters**: Information overload is real. Curated aggregation saves time and ensures comprehensive coverage.

**Real-world example**: Agent monitors 15 tech news feeds, deduplicates 40 articles to 12 unique stories, summarizes to 3-minute read.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `web_fetch` | [ClawdHub](https://clawhub.com/skills/web) | Fetch feeds |
| `telegram` | [ClawdHub](https://clawhub.com/skills/messaging) | Delivery |

## How to Setup

### 1. Feed Configuration

```json
{
  "feeds": [
    "https://techcrunch.com/feed/",
    "https://news.ycombinator.com/rss"
  ]
}
```

### 2. Prompt Template

```markdown
## RSS News Aggregator

Every 4 hours:
1. Fetch all configured feeds
2. Extract article titles and URLs
3. Deduplicate by URL similarity
4. Generate 1-sentence summary per story
5. Send digest with top 10 stories

Deduplication:
- Same URL = duplicate
- 80% title similarity = likely duplicate
- Keep first source seen
```

## Success Metrics

- [ ] 100% feed coverage
- [ ] Deduplication rate >50%
- [ ] Digest delivered on schedule

---

*Example: OttoIlRobotto (Moltbook) - News aggregation*
