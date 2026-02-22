# 51. Email Newsletter to Podcast

## Introduction

You subscribe to interesting newsletters — industry updates, medical news, tech roundups — but rarely find time to read them. What if your AI agent could turn those emails into a personal podcast you listen to while commuting, cooking, or exercising?

This use case converts email newsletters into audio briefings automatically. Your agent monitors your inbox, detects newsletters, writes a conversational script, and generates audio using text-to-speech. The result lands in your Telegram or Signal chat as a voice message, ready to play.

No technical skills required. Just forward an email and say "make a podcast," or set it up to run automatically every morning.

## Skills You Need

- [TTS / ElevenLabs](https://clawhub.ai/skills/beware-piper-tts) — Text-to-speech audio generation
- [Email Access](https://clawhub.ai/skills/agentmail-wrapper) — Read incoming emails (Gmail, Outlook)

## How to Setup

### Prerequisites
- An email account your agent can access (Gmail with app password)
- A Telegram or Signal channel connected to OpenClaw
- (Optional) ElevenLabs API key for higher-quality voices

### Prompt Template
```
You are my personal podcast producer. Every morning at 7 AM:

1. Check my email for newsletters received in the last 24 hours
2. Pick the most interesting 3-5 stories
3. Write a conversational podcast script (3-5 minutes reading time)
4. Convert to audio using TTS
5. Send the audio to me via Telegram

Style: Warm, conversational, like a friend catching you up over coffee.
Keep it under 5 minutes. Skip ads and promotional content.
```

### Configuration
Set up a cron job to run daily at 7:00 AM:
```
Schedule: 0 7 * * *
Action: Check email → Generate script → TTS → Send audio
```

## Success Metrics
- Audio briefing delivered before your commute starts
- Covers the most relevant stories from your subscriptions
- Takes less than 5 minutes to listen to
- You actually look forward to hearing it
