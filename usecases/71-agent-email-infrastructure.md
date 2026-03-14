# Agent Email Infrastructure

> Give your OpenClaw agent its own email address with zero configuration.

## Problem
AI agents need email for outreach, notifications, and verification — but traditional email providers require human signup, API keys, and dashboard configuration.

## Solution
Install the LobsterMail skill and your agent self-provisions its own inbox. No human in the loop.

## How It Works
1. `clawhub install lobstermail-agent-email`
2. Agent creates an inbox: `const inbox = await lm.createInbox()`
3. Agent sends/receives email autonomously
4. Built-in prompt injection scanning protects against email-based attacks

## Key Features
- No human signup or API keys needed
- Prompt injection scanning (6 categories)
- SPF/DKIM/DMARC authentication
- Per-account reputation isolation

## Skills Used
- [lobstermail-agent-email](https://clawhub.ai/samuelchenardlovesboards/lobstermail-agent-email)

## Links
- [LobsterMail](https://lobstermail.ai/)
- [npm](https://www.npmjs.com/package/lobstermail)
