# 65. Automated Social Media Posting

## Introduction

Maintaining a consistent social media presence requires posting regularly — but who has time to compose and publish content every day? Your AI agent can handle the routine: drafting posts, scheduling them, and publishing at optimal times.

Set up content themes for each day (Motivation Monday, Tech Tuesday, etc.), and your agent writes and posts automatically. You review and approve, or let it run on autopilot for less critical platforms.

Perfect for freelancers, small businesses, and personal brands who need to stay visible online.

## Skills You Need

- [Browser Control](https://clawhub.com/skills/browser) — Post to social platforms
- [Web Search](https://clawhub.com/skills/web-search) — Research trending topics

## How to Setup

### Prerequisites
- Social media accounts (X/Twitter, LinkedIn, etc.)
- Telegram bot for review/approval
- Browser capability in OpenClaw

### Prompt Template
```
You are my social media content manager. Manage posting for:
- X/Twitter: @[YOUR_HANDLE]
- LinkedIn: [YOUR_PROFILE]

Content calendar:
- Monday: Motivational/mindset post
- Tuesday: Industry insight or tip
- Wednesday: Behind-the-scenes or personal story
- Thursday: Engage with trending topic in my field
- Friday: Weekend recommendation (book/tool/article)
- Saturday: Repost/engage with community content
- Sunday: Rest (no posting)

Workflow:
1. Draft the post the evening before
2. Send me the draft via Telegram for approval
3. If I approve (or don't respond within 2 hours), publish at optimal time:
   - X/Twitter: 8:30 AM and 12:30 PM
   - LinkedIn: 9:00 AM
4. After posting, monitor engagement for 2 hours and reply to any comments

Content rules:
- My niche: [YOUR FIELD: e.g., AI, marketing, fitness]
- Tone: [Professional but approachable / Casual and fun / Authoritative]
- Never post about: politics, religion, controversial takes
- Max 280 characters for X/Twitter
- Include relevant hashtags (max 3)
- Use emoji sparingly ✨
```

### Configuration
- Draft creation: Cron at 8 PM daily (day before)
- Publishing: Cron at scheduled post times
- Engagement monitoring: 2 hours after each post

## Success Metrics
- Posts published 5-6 days per week consistently
- Engagement rate stays steady or grows
- You spend less than 5 minutes per day on social media management
