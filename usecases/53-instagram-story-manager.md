# 53. Instagram Story Manager

## Introduction

Maintaining a consistent social media presence is exhausting. Posting stories, replying to comments, engaging with followers — it's a part-time job. Your OpenClaw agent can handle the routine parts while you focus on creating actual content.

This use case sets up your agent to manage Instagram stories: scheduling posts, responding to story reactions, and maintaining engagement with your audience. The agent works through browser automation, so no special API access is needed.

Perfect for small business owners, freelancers, or anyone who wants to stay active on Instagram without spending hours on their phone.

## Skills You Need

- [Browser Control](https://clawhub.com/skills/browser) — Automate Instagram interactions
- [Image Generation](https://clawhub.com/skills/image-gen) — Create story visuals (optional)

## How to Setup

### Prerequisites
- Instagram account credentials
- OpenClaw with browser capability enabled
- A content calendar or list of topics

### Prompt Template
```
You are my Instagram manager. Your responsibilities:

1. **Daily Stories**: Post 1-2 stories per day from my content queue.
   - Use the images/templates I provide in /workspace/instagram/queue/
   - Add relevant hashtags and location tags
   
2. **Engagement**: Check story replies and DMs twice daily.
   - Reply to genuine messages with friendly, on-brand responses
   - Heart-react to compliments
   - Flag spam or inappropriate messages for my review

3. **Analytics**: Every Sunday, send me a summary:
   - Story views this week vs last week
   - Top performing content
   - Follower growth

Never post anything controversial. When unsure, ask me first.
My brand voice: [friendly/professional/casual — pick one]
```

### Configuration
- Story posting: Cron at 9 AM and 6 PM daily
- Engagement check: Cron at 12 PM and 8 PM daily
- Weekly report: Cron Sunday 10 AM

## Success Metrics
- Consistent daily posting without manual effort
- Story replies answered within 4 hours
- Follower engagement rate increases over time
