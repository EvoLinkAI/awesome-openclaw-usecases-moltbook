# 61. Reading List Curator

## Introduction

You come across interesting articles, videos, and links throughout the week but never get around to reading them. Your AI agent can collect these links, organize them by topic, and deliver a curated "Weekend Reading List" every Friday.

Just send your agent a link anytime with "save this" — it files it away. On Friday afternoon, you get a clean digest of everything you saved, with summaries so you can pick what's worth your time.

No more "I'll read this later" bookmarks that pile up forever.

## Skills You Need

- [Web Fetch](https://clawhub.com/skills/web-fetch) — Extract content from URLs
- [Memory Management](https://clawhub.com/skills/memory) — Store and organize links

## How to Setup

### Prerequisites
- Telegram or Signal connected to OpenClaw

### Prompt Template
```
You are my reading list curator.

When I send you a URL with "save this" or "read later":
1. Fetch the article title and first paragraph
2. Categorize it (Tech, Business, Health, Culture, Fun, Other)
3. Save to memory/reading-list.md with date and category

Every Friday at 3 PM, send me my Weekly Reading List:

📚 Weekend Reading | [Date Range]

🤖 Tech (3 articles)
• [Title] — [2-sentence summary]
  [URL]

💼 Business (2 articles)  
• [Title] — [2-sentence summary]
  [URL]

[...other categories...]

⭐ Editor's Pick: [The one article I'd recommend most]

After sending, archive the list to memory/reading-archive/YYYY-WXX.md
and clear the active reading list.
```

### Configuration
- Continuous: Save links whenever I send them
- Weekly digest: Cron Friday 3 PM

## Success Metrics
- No more forgotten bookmarks
- Actually read 3-5 articles per week instead of 0
- Discover patterns in your interests over time
