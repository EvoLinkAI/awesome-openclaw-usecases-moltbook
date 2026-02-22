# Medical Email to Podcast

## Introduction

Transform medical newsletters into audio briefings for commute listening. This workflow parses incoming medical emails, researches embedded URLs for deeper context, writes a conversational podcast script tailored to the physician's specialty, generates TTS audio using ElevenLabs, and delivers via Signal.

**Why it matters**: Physicians receive dense medical newsletters daily but lack time to read them. Converting to audio enables learning during commute or exercise.

**Real-world example**: A family physician receives "Doctors of BC Newsflash" daily. The agent turns 6 stories into a 5:18 podcast covering urgent care centers, disease outbreaks, and policy updates.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `email` | ClawdHub | Read and parse incoming emails |
| `web_fetch` | ClawdHub | Research linked articles |
| `elevenlabs` | ClawdHub | Generate TTS audio |
| `ffmpeg` | ClawdHub | Concatenate audio chunks |
| `signal` | ClawdHub | Deliver final audio |

## How to Setup

### 1. Configure Email Detection

```
Set up email forwarding from medical newsletter to agent's Gmail.
Configure auto-detection during heartbeats for newsletters matching:
- Sender: doctors@bcnews.com
- Subject contains: "Newsflash"
```

### 2. Install Skills

```bash
npx molthub@latest install email
npx molthub@latest install web_fetch
npx molthub@latest install elevenlabs
npx molthub@latest install ffmpeg
npx molthub@latest install signal
```

### 3. Create Processing Script

Create `skills/email-podcast/index.js`:

```javascript
// Parse email → extract stories → research URLs → write script → TTS → deliver
async function processMedicalEmail(email) {
  const stories = parseStories(email.body);
  const enriched = await Promise.all(
    stories.map(s => web_fetch(s.url).then(enhanceStory))
  );
  const script = writePodcastScript(enriched, "family_medicine");
  const audio = await generateTTS(script); // chunk if > 4000 chars
  await signal.sendAudio({ to: human.phone, audio });
}
```

### 4. Prompt Template

Add to your `SKILL.md`:

```markdown
## Medical Email to Podcast

When you receive a medical newsletter:
1. Parse the email body to extract story titles and URLs
2. For each URL: fetch the full article for deeper context
3. Write a 5-minute conversational podcast script
4. Use ElevenLabs TTS (chunk if > 4000 chars, concat with ffmpeg)
5. Send audio file via Signal
6. Log to memory/medical-podcasts/YYYY-MM-DD.md

Style: Professional but conversational, tailored to family medicine context.
```

### 5. Cron Configuration

```json
{
  "schedule": "0 6 * * *",
  "task": "check_medical_emails",
  "action": "process_and_deliver_podcast"
}
```

## Success Metrics

- [ ] Newsletter processed within 1 hour of receipt
- [ ] Audio length: 5-7 minutes
- [ ] Human listens within 24 hours
- [ ] Zero manual steps required

## Troubleshooting

| Issue | Solution |
|-------|----------|
| TTS fails (text too long) | Split into 4000-char chunks, concat with ffmpeg |
| URL returns paywall | Use web_fetch with textise dot iitty |
| Audio quality poor | Switch ElevenLabs voice to 'Antoni' or 'Bella' |

---

*Example: Fred (Moltbook) - "Built an email-to-podcast skill today"*
