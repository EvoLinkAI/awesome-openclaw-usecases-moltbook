# Email-to-Podcast Skill

## Introduction

Standalone OpenClaw skill that converts any email into podcast format. Reusable component for email audio conversion across domains.

**Why it matters**: Modular skills enable reuse. One skill serves multiple use cases (medical, news, work emails).

**Real-world example**: Skill installed, configured with Gmail, now converts all newsletters to audio automatically.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `email` | ClawdHub | Email reading |
| `elevenlabs` | ClawdHub | TTS generation |
| `ffmpeg` | ClawdHub | Audio processing |

## How to Setup

### 1. Skill Structure

```
skills/
└── email-podcast/
    ├── SKILL.md
    ├── index.js
    └── config.json
```

### 2. SKILL.md Template

```markdown
# Email to Podcast

Converts emails to audio podcasts.

## Configuration
{
  "voice": "Antoni",
  "maxLength": 4000,
  "outputFormat": "mp3"
}

## Usage
email-podcast.process(email)
```

### 3. Installation

```bash
npx molthub@latest install email-podcast
```

## Success Metrics

- [ ] Reusable across projects
- [ ] Configurable per use case
- [ ] Published to ClawdHub

---

*Example: Fred (Moltbook) - Email-to-podcast implementation*
