# 55. Smart Calendar Reminder

## Introduction

Standard calendar reminders are dumb — they just beep 15 minutes before an event. Your AI agent can do much better: it checks your calendar, reminds you 2 hours ahead with context, suggests preparation steps, and even warns you about travel time.

This use case turns your agent into a proactive calendar assistant that understands your schedule, anticipates what you need, and sends smart reminders via Telegram with actionable context.

Never walk into a meeting unprepared again.

## Skills You Need

- [Calendar Access](https://clawhub.com/skills/calendar) — Google Calendar or Outlook integration
- [Weather](https://clawhub.com/skills/weather) — For outdoor event preparation

## How to Setup

### Prerequisites
- Google Calendar or Outlook connected to OpenClaw
- Telegram bot for notifications

### Prompt Template
```
You are my smart calendar assistant. Check my calendar every 30 minutes during waking hours (8 AM - 10 PM).

For each upcoming event in the next 2 hours:

1. **Context**: What is this meeting about? Who's attending?
2. **Preparation**: What should I review or bring?
   - If it's a client meeting → remind me of last interaction
   - If it's a doctor appointment → remind me to bring insurance card
   - If it's a dinner → check the restaurant and suggest what to wear
3. **Logistics**: 
   - How long to get there? (check traffic if it's in-person)
   - Is it raining? Should I bring an umbrella?
4. **Conflicts**: Flag if two events overlap

Send reminders via Telegram. Format:
📅 [Event] in 2 hours
📍 [Location/Link]
📋 [Prep notes]
⏱️ [Leave by X:XX to arrive on time]
```

### Configuration
- Heartbeat check: Every 30 minutes during 8 AM - 10 PM
- Send reminder: 2 hours before each event

## Success Metrics
- Zero missed appointments
- Always prepared with context before meetings
- Travel time warnings prevent being late
