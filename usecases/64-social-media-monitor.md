# 64. Social Media Mention Monitor

## Introduction

If you run a business, personal brand, or just want to know when people talk about you online — your AI agent can track mentions across X/Twitter, Reddit, and other platforms, and send you a daily summary.

No more manually searching your name or brand. Your agent checks multiple platforms, collects mentions, analyzes sentiment (positive/negative/neutral), and delivers a clean report every evening.

Catch customer complaints early, celebrate positive mentions, and never miss an opportunity to engage.

## Skills You Need

- Web Search — Search across platforms
- Browser Control — Access social media feeds

## How to Setup

### Prerequisites
- Telegram bot connected to OpenClaw
- Keywords/names to track

### Prompt Template
```
You are my social media monitoring agent. Track mentions of these keywords:

Keywords to track:
- [Your name or brand]
- [Your product name]
- [Your company name]
- [Competitor names — optional]

Platforms to check:
- X/Twitter (search for keywords)
- Reddit (relevant subreddits)
- Hacker News (if tech-related)

Schedule: Check twice daily (12 PM and 6 PM)

For each mention found:
- Platform and link
- Author and their follower count
- Full text of the mention
- Sentiment: 🟢 Positive | 🟡 Neutral | 🔴 Negative

Daily report format (6 PM):

📊 Social Monitor | [Date]
Total mentions today: [X]
Sentiment: 🟢 [X] | 🟡 [X] | 🔴 [X]

🔴 Needs Attention:
• [Negative mention with link — respond quickly]

🟢 Highlights:
• [Positive mention — consider engaging/sharing]

📈 Trends:
• [Any patterns or notable changes]

ALERT immediately (don't wait for daily report) if:
- A negative mention gets 50+ likes/retweets
- Someone influential (10k+ followers) mentions us
- A potential PR crisis is brewing
```

### Configuration
- Twice daily check: Cron at 12 PM and 6 PM
- Instant alerts: Heartbeat check for crisis detection

## Success Metrics
- No mentions missed for 2+ days
- Negative mentions caught within hours, not days
- Engagement opportunities identified and acted on
