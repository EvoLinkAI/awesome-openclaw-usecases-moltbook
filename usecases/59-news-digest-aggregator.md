# 59. News Digest Aggregator

## Introduction

Staying informed is important, but visiting ten different news sites every morning is exhausting. You end up reading the same story multiple times or missing important perspectives entirely. This use case solves that by automatically collecting news from multiple sources, removing duplicates, and delivering one clean, curated digest to your Telegram each day.

Your agent monitors your favorite RSS feeds, news sites, and newsletters, then compiles a single-page summary with the most important stories. It groups related articles together, highlights key points, and gives you just enough context to decide what to read in full. Instead of information overload, you get a well-organized briefing that respects your time.

This is perfect for news enthusiasts, professionals who need to stay current on industry trends, or anyone who wants to be informed without the constant distraction of checking multiple sources.

## Skills You Need

- [RSS Reader Skill](https://clawhub.ai/skills/hacker-news) — Fetch news from RSS feeds
- Web Fetch Skill — Scrape news websites
- AI/Analysis Skill — Summarize and deduplicate articles
- Telegram Skill — Deliver the digest
- [Memory/Notes Skill](https://clawhub.ai/skills/mem) — Track what you've already seen

## How to Setup

### Prerequisites

Before you begin, make sure you have:

1. **News Sources**: List of RSS feeds or websites you want to monitor
2. **Telegram Bot**: To receive your daily news digest
3. **Topic Preferences**: What subjects you care most about
4. **Your Chat ID**: Your Telegram chat ID for message delivery
5. **Timing Preference**: When you want to receive the digest (morning recommended)

### Prompt Template

```
You are my Personal News Curator. Every day, gather news from my favorite sources, remove duplicates, and send me one clean digest.

---

DAILY TASK (7:45 AM):

1. **Fetch News from Sources**

   RSS Feeds to monitor:
   - [Your preferred news source 1, e.g., BBC World News]
   - [Your preferred news source 2, e.g., TechCrunch]
   - [Your preferred news source 3, e.g., Industry-specific publication]
   - [Add more as needed]

   Also check (optional):
   - Specific Twitter/X accounts for breaking news
   - Reddit communities for trending topics
   - Email newsletters in your inbox

2. **Deduplicate Stories**
   - Same event reported by multiple sources = one entry
   - Keep the most comprehensive version or mix perspectives
   - Group related stories together (e.g., "Ongoing: Climate Summit Updates")

3. **Categorize and Prioritize**

   Categories (in order of my priority):
   🌍 **World News** — Major international events
   💼 **Business/Tech** — Industry news, markets, innovation
   🏛️ **Politics** — Government, policy, elections
   🧪 **Science** — Research, discoveries, health
   🎭 **Culture** — Arts, entertainment, lifestyle
   ⚽ **Sports** — Major games and results (if enabled)

4. **Summarize Each Story**
   - Headline (clear and informative)
   - 2-3 sentence summary of key facts
   - Why it matters (context)
   - Source link (if I want to read more)

5. **Send Formatted Digest via Telegram**

```
📰 **Your Morning News Digest**
🗓️ [Day, Date] | 📊 [X] stories from [Y] sources

---

🌍 **World News**

1. **[Headline]**
   [2-3 sentence summary]
   💡 Why it matters: [Brief context]
   🔗 [Source]

2. **[Headline]**
   [2-3 sentence summary]
   💡 Why it matters: [Brief context]
   🔗 [Source]

---

💼 **Business & Tech**

1. **[Headline]**
   [Summary...]
   💡 [Context...]
   🔗 [Source]

[Continue for each category...]

---

📌 **Quick Glance**
[3-5 one-line headlines for stories that don't need full summary]

---

💬 **Editor's Note**
[Optional: 1-2 sentences on a notable trend or connection between stories]

---
🕐 Next digest: Tomorrow at 7:45 AM
📰 Sources: [List of sources checked today]
```

---

SMART FILTERING RULES:

**Include:**
- Breaking news from last 24 hours
- Major developments in my industry
- Stories from my priority categories
- Regional news from [YOUR LOCATION]

**Exclude (unless truly major):**
- Celebrity gossip
- Sports scores (unless I specifically request)
- Opinion pieces (unless highly relevant)
- Duplicate coverage of same event
- Stories I've already seen (check against yesterday's digest)

**Prioritize:**
- Stories appearing in 2+ sources
- Topics I've clicked on before (track interests)
- Time-sensitive news (happening today)
- Local news when relevant

---

CUSTOMIZATION OPTIONS:

MY TOPIC PRIORITIES (Rank 1-5):
1. [Technology/Innovation]
2. [World Affairs]
3. [Business/Finance]
4. [Science/Health]
5. [Culture/Entertainment]

NEVER MISS TOPICS (Always include if found):
- [e.g., Artificial Intelligence news]
- [e.g., My company's industry]
- [e.g., Climate/environment updates]

SOURCES TO CHECK:
RSS Feeds:
- https://feeds.bbci.co.uk/news/world/rss.xml
- https://techcrunch.com/feed/
- [Add your industry publications]

Websites (scrape headlines):
- [news site 1 homepage]
- [news site 2 homepage]

BLOCKLIST (Never include):
- [Sources you don't trust]
- [Topics you want to avoid]

---

ADVANCED FEATURES (Optional):

**Breaking News Alerts:**
If major breaking news occurs between digests:
```
🚨 **Breaking News Alert**
[Brief summary of major event]
Happening now — check live updates at [source]
```

**Weekly Deep Dive (Fridays):**
```
📊 **Weekly News Review**

Top 5 stories of the week:
1. [Story] — Impact: [explanation]
2. [Story] — Impact: [explanation]
...

Trending topics: [What came up repeatedly]

What to watch next week: [Preview of ongoing stories]
```

**Saved for Later:**
Track which stories I clicked on or replied "save" to. Include in weekly "Stories You Wanted to Read" reminder.

---

DEDUPLICATION LOGIC:
- Same headline or 80%+ similar = duplicate
- Same event, different angles = group together with "Multiple perspectives:"
- Follow-up stories = mark as "Update to yesterday's story about X"
- Developments on ongoing stories = create "Ongoing Story" section

---

RULES:
- Keep digest under 4000 characters (Telegram limit consideration)
- If too many stories, prioritize and add "+ [X] more stories" note
- Include source for every story so I can verify
- Never editorialize — stick to facts in summaries
- If source is paywalled, note: "([Source] — subscription may be required)"
- Respect my time: 5 minutes to read the full digest
```

### Configuration

**Daily Digest Cron**:
```json
{
  "schedule": "45 7 * * *",
  "name": "Daily News Digest",
  "prompt": "[paste the prompt template above here]",
  "timezone": "Your/Timezone"
}
```

This sends at 7:45 AM — late enough to catch overnight news, early enough for morning reading.

**Optional: Weekly Review**:
```json
{
  "schedule": "0 18 * * 5",
  "name": "Weekly News Review",
  "prompt": "Generate weekly news review with top stories and trends"
}
```

**Source Management**:
Create a file at `/memory/news-sources.json` to easily update:
```json
{
  "rss_feeds": [
    "https://example.com/feed",
    "https://another.com/rss"
  ],
  "websites": [
    "https://news-site.com"
  ],
  "priority_topics": ["AI", "climate", "business"],
  "blocked_topics": ["celebrity", "gossip"]
}
```

## Success Metrics

You'll know this is working when:

- ✅ You receive a Telegram digest every morning by 7:45 AM
- ✅ You can read the full briefing in under 5 minutes
- ✅ You no longer visit 5+ news sites to feel informed
- ✅ You learn about important stories you would have missed
- ✅ You feel informed without information overload

**Troubleshooting**:
- Digest too long? Reduce number of sources or stories per category
- Missing important news? Add that source to your RSS list
- Too many similar stories? Tighten deduplication rules
- Wrong topics? Adjust priority rankings in the prompt
- Not receiving? Check bot token and chat ID, verify cron is running

**Level Up**:
Once this works, consider adding:
- Industry-specific digests (separate work news from general news)
- Weekend edition with longer reads and analysis
- Audio version via TTS for commute listening
- Personalization based on what you click most
