# 65. Automated Social Media Posting

## Introduction

Maintaining a consistent social media presence requires posting regularly — but who has time to compose and publish content every day? Your AI agent can handle the routine: drafting posts, scheduling them, and publishing at optimal times.

Set up content themes for each day (Motivation Monday, Tech Tuesday, etc.), and your agent writes and posts automatically. You review and approve, or let it run on autopilot for less critical platforms.

Perfect for freelancers, small businesses, and personal brands who need to stay visible online.

## Skills You Need

- [TweetClaw](https://clawhub.ai/plugins/%40xquik%2Ftweetclaw) - Structured X/Twitter drafts, posts, replies, and engagement actions through OpenClaw
- Browser Control — Post to non-X social platforms when no structured plugin exists
- [Web Search](https://clawhub.ai/skills/searching-assistant) — Research trending topics

## How to Setup

### Prerequisites
- Social media accounts (X/Twitter, LinkedIn, etc.)
- Telegram bot for review/approval
- Browser capability in OpenClaw
- Optional for X/Twitter: install TweetClaw with `openclaw plugins install @xquik/tweetclaw`

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
3. Only publish after explicit approval. If I don't respond within 2 hours, skip the post.
   - X/Twitter: 8:30 AM and 12:30 PM
   - LinkedIn: 9:00 AM
4. Use TweetClaw for X/Twitter publishing when configured; use browser control for other platforms
5. After posting, monitor engagement for 2 hours and draft replies for approval

Content rules:
- My niche: [YOUR FIELD: e.g., AI, marketing, fitness]
- Tone: [Professional but approachable / Casual and fun / Authoritative]
- Never post about: politics, religion, controversial takes
- Max 280 characters for X/Twitter
- Include relevant hashtags (max 3)
- Use emoji sparingly ✨

TweetClaw safety:
- Show the exact final X/Twitter text before publishing
- Ask before posting, replying, liking, retweeting, following, or sending DMs
- Do not publish private information, unverified claims, or extra links the user did not request
```

### Configuration
- Draft creation: Cron at 8 PM daily (day before)
- Publishing: Cron at scheduled post times
- Engagement monitoring: 2 hours after each post

## Success Metrics
- Posts published 5-6 days per week consistently
- Engagement rate stays steady or grows
- You spend less than 5 minutes per day on social media management
