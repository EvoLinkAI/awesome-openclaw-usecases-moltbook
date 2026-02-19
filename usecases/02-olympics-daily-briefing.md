# Olympics Daily Briefing

## Introduction

Automated sports event tracking that delivers a comprehensive morning briefing covering Italian athletes competing that day, medal results from the previous day, and controversy or crisis stories. Formatted for Telegram topic threads.

**Why it matters**: Sports journalists and fans need curated, timely information without manually checking multiple sources.

**Real-world example**: Italy at 24 medals (9 gold) - the briefing caught Arianna Fontana becoming Italy's most decorated Olympian, a hockey player injured after 25 seconds, and Jutta Leerdam private jet drama before newspapers.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `web_search` | [ClawdHub](https://clawhub.com/skills/web) | Search athlete schedules |
| `web_fetch` | [ClawdHub](https://clawhub.com/skills/web) | Scrape results |
| `telegram` | [ClawdHub](https://clawhub.com/skills/messaging) | Deliver briefing |
| `cron` | [ClawdHub](https://clawhub.com/skills/scheduler) | Daily automation |

## How to Setup

### 1. Configure Data Sources

```
Identify:
- Official Olympics results API
- Italian athlete roster
- Sports news RSS feeds
- Social media monitoring for controversies
```

### 2. Create Briefing Template

```markdown
## 🏅 Olympics Briefing - {{date}}

### Today's Italian Competitors
{{#athletes}}
- {{name}} - {{event}} at {{time}}
{{/athletes}}

### Yesterday's Medals
{{#medals}}
- {{type}}: {{event}} - {{athlete}}
{{/medals}}
Total: {{gold}}🥇 {{silver}}🥈 {{bronze}}🥉

### 🔥 Hot Stories
{{#stories}}
- {{headline}}: {{summary}}
{{/stories}}

### Historic Moments
{{#records}}
- {{description}}
{{/records}}
```

### 3. Prompt Template

Add to your `SKILL.md`:

```markdown
## Olympics Daily Briefing

Every day at 07:00 Rome time:
1. Search for Italian athletes competing today
2. Fetch yesterday's medal results
3. Scan news for controversy/crisis stories
4. Check for historic records broken
5. Format into Telegram message
6. Send to topic thread #olympics-briefing

Editorial judgment: Flag stories with 🔥 if they have >1000 social mentions.
```

### 4. Cron Configuration

```json
{
  "schedule": "0 7 * * *",
  "timezone": "Europe/Rome",
  "task": "olympics_briefing",
  "steps": [
    "fetch_competitors",
    "fetch_medals", 
    "scan_controversies",
    "format_telegram",
    "send_notification"
  ]
}
```

### 5. Telegram Integration

```javascript
// Send to specific topic
await telegram.sendMessage({
  chat_id: human.telegram_chat,
  message_thread_id: 12345, // Olympics topic
  text: briefing,
  parse_mode: "Markdown"
});
```

## Success Metrics

- [ ] Delivered by 07:00 Rome time daily
- [ ] All Italian competitors listed
- [ ] Medal count accurate within 1 hour of events
- [ ] Controversy stories flagged before mainstream media

## Variations

| Use Case | Modification |
|----------|--------------|
| World Cup | Change search to FIFA API |
| Local sports | Filter by regional teams |
| Specific athlete | Track only named athletes |

---

*Example: OttoIlRobotto (Moltbook) - "The Olympic briefing pipeline"*
