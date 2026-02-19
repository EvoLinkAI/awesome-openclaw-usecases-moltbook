# 52. Daily Morning Briefing via Telegram

## Introduction

Imagine waking up to a personalized briefing that covers everything you need to know: today's weather, your calendar events, top news headlines, and pending to-dos. No scrolling through multiple apps — just one clean message in Telegram.

Your OpenClaw agent compiles this briefing automatically every morning. It checks the weather for your location, reads your calendar, scans news sources relevant to your interests, and formats everything into a concise, easy-to-read message.

This is the "personal assistant morning report" that executives pay thousands for — except your AI does it for free, every single day.

## Skills You Need

- [Weather](https://clawhub.com/skills/weather) — Current weather and forecasts
- [Web Search](https://clawhub.com/skills/web-search) — News headlines

## How to Setup

### Prerequisites
- Telegram bot connected to OpenClaw
- Your city/location for weather
- (Optional) Google Calendar access for events

### Prompt Template
```
You are my morning briefing assistant. Every day at 6:30 AM:

1. **Weather**: Get today's weather for [YOUR CITY]. Include temperature, conditions, and whether I need an umbrella.
2. **Calendar**: List my events for today with times.
3. **News**: Find 3-5 top headlines relevant to [YOUR INTERESTS: e.g., tech, finance, local news].
4. **Reminders**: Check my pending to-dos and remind me of anything due today.

Format as a clean Telegram message with emoji headers:
☀️ Weather | 📅 Calendar | 📰 News | ✅ To-Do

Keep it under 300 words. No fluff.
```

### Configuration
Set up a daily cron job:
```
Schedule: 30 6 * * *
Action: Compile briefing → Send via Telegram
```

## Success Metrics
- Briefing arrives before you get out of bed
- You stop opening 4 separate apps every morning
- Covers everything you need in under 1 minute of reading
