# 54. Cold Relationship Revival

## Introduction

We all have friends we've lost touch with. The "I should text them" thought that comes and goes for weeks until it feels too awkward to reach out. Your AI agent can help bridge that gap — naturally and thoughtfully.

This use case programs your agent to identify contacts you haven't messaged in a while and draft personalized, warm messages to reconnect. It runs during quiet hours (late evening or early morning), checks your messaging history, and sends genuine check-ins that don't feel robotic.

The goal isn't to automate friendship — it's to remove the friction of reaching out so real connections can restart.

## Skills You Need

- Messaging — WhatsApp/Telegram/Signal integration

## How to Setup

### Prerequisites
- A messaging platform connected to OpenClaw (WhatsApp, Telegram, or Signal)
- A list of contacts you'd like to stay in touch with

### Prompt Template
```
You are my relationship maintenance assistant. Your job is to help me stay connected with people I care about.

Contact list (check in monthly):
- [Name 1] — old college friend, loves hiking
- [Name 2] — former colleague, into photography  
- [Name 3] — cousin, just had a baby

Rules:
1. Check who I haven't messaged in 30+ days
2. Draft a natural, warm message referencing something specific about them
3. Show me the draft BEFORE sending — never send without my approval
4. Keep it casual: "Hey! Been thinking about you..." not "Dear Sir/Madam"
5. If they reply, notify me immediately so I can continue the conversation

Examples of good messages:
- "Hey [Name]! Saw this hiking trail and thought of you 🏔️ How've you been?"
- "Just came across an amazing photo and remembered your photography. What have you been shooting lately?"

Never send more than 2 revival messages per week.
```

### Configuration
- Weekly check: Cron every Sunday at 10 AM
- Draft review: Agent sends drafts to you for approval

## Success Metrics
- At least 2 dormant friendships reactivated per month
- Messages feel natural (friends don't suspect AI involvement)
- You actually follow up on the conversations that restart
