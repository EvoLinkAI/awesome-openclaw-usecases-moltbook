# 66. Trello/Notion Board Auto-Organizer

## Introduction

Project boards get messy. Completed tasks linger in "In Progress." Overdue cards pile up. Labels become inconsistent. Your AI agent can clean up your Trello or Notion boards while you sleep.

Every night, the agent scans your boards, archives completed tasks, flags overdue items, moves cards to the right columns, and sends you a morning summary of what changed. Wake up to a clean, organized board.

No project management expertise needed — just tell your agent your board structure and let it maintain order.

## Skills You Need

- [Browser Control](https://clawhub.com/skills/browser) — Navigate Trello/Notion web interface
- [Web Fetch](https://clawhub.com/skills/web-fetch) — Read board data via API

## How to Setup

### Prerequisites
- Trello or Notion account
- Trello API key (or Notion integration token)
- Telegram bot for notifications

### Prompt Template
```
You are my project board organizer. Every night at 11 PM:

Board structure:
- 📥 Inbox (new tasks)
- 🔄 In Progress
- 👀 Review
- ✅ Done
- 📦 Archive

Nightly cleanup tasks:
1. **Archive completed**: Move cards in "Done" for 3+ days to "Archive"
2. **Flag overdue**: Add 🔴 label to any card past its due date
3. **Stale detection**: If a card has been "In Progress" for 7+ days with no activity, add a comment: "This card has been stale for [X] days. Still active?"
4. **Inbox triage**: If I left cards in Inbox for 2+ days, remind me to sort them
5. **Label cleanup**: Ensure all cards have at least one label (priority: High/Medium/Low)

Morning report (7 AM via Telegram):
📋 Board Status | [Date]
- Cards archived: [X]
- Overdue flagged: [X] 
- Stale cards: [list them]
- Inbox items needing attention: [X]
- Active tasks: [total count by column]

Board URL: [YOUR_TRELLO_OR_NOTION_URL]
```

### Configuration
- Nightly cleanup: Cron at 11 PM
- Morning report: Cron at 7 AM

## Success Metrics
- Board stays organized without manual effort
- No task sits in "Done" for more than 3 days
- Overdue items are caught within 24 hours
