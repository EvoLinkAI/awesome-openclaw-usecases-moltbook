# 62. Smart Home Control via Telegram

## Introduction

Control your smart home from anywhere — just send a Telegram message. "Turn off the living room lights." "Set thermostat to 22°C." "Is the front door locked?" Your AI agent acts as a natural-language interface to your smart home system.

No more fumbling with multiple apps for different devices. One chat interface to rule them all. Works with Home Assistant, SmartThings, or any system with an API.

## Skills You Need

- [Home Assistant](https://clawhub.com/skills/home-assistant) — Smart home integration
- [Browser Control](https://clawhub.com/skills/browser) — Fallback for web-based controls

## How to Setup

### Prerequisites
- Home Assistant (or similar) running on your network
- Home Assistant API token
- Telegram bot connected to OpenClaw

### Prompt Template
```
You are my smart home controller. I'll send commands via Telegram in natural language.

Connected systems:
- Home Assistant at http://[YOUR_HA_IP]:8123
- API Token: [YOUR_TOKEN]

Understand commands like:
- "Turn off all lights"
- "Set bedroom to 21 degrees"
- "Is the garage door open?"
- "Turn on movie mode" (dim lights, turn on TV)
- "Good night" (lock doors, lights off, thermostat to 18°C)
- "I'm leaving" (arm security, lights off, thermostat to eco)

Scenes I use:
- "Movie mode": Living room lights 20%, TV on
- "Good morning": Kitchen lights on, coffee maker on, thermostat 22°C
- "Good night": All lights off, doors locked, thermostat 18°C

Rules:
- Confirm every action with a short response
- If a command is ambiguous, ask for clarification
- Never unlock doors without double confirmation
- Send me an alert if a door/window sensor triggers while I'm away
```

### Configuration
- Always-on: Responds to Telegram messages instantly
- Security alerts: Heartbeat check every 5 minutes when "away mode" is active

## Success Metrics
- Control your entire home from one chat
- Response time under 5 seconds
- Security alerts work reliably
