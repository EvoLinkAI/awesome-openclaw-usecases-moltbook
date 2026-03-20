# 73. AI Music Generation

## Introduction

Need background music for your video? A custom jingle for your podcast intro? An original song for a special occasion? Your AI agent can now compose professional-quality music in any genre or style — from lo-fi beats to epic orchestral scores, from pop songs with lyrics to ambient soundscapes.

This use case gives you access to Suno v4 through v5, the leading AI music generation models. Your agent handles the creative process — you describe the vibe, genre, and mood, and it generates complete tracks with vocals (optional), instrumentation, and production polish. The result is delivered as an MP3 file, ready to use.

Perfect for content creators, podcasters, video producers, game developers, and anyone who needs original music without hiring a composer.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `evolink-music` | [ClawHub](https://clawhub.ai/EvoLinkAI/evolink-music) | AI music generation with Suno v4–v5 |

## How to Setup

### Prerequisites
- An EvoLink API key ([sign up at evolink.ai/signup](https://evolink.ai))
- OpenClaw with Telegram or Signal connected

### Installation
```bash
# Install the skill
clawhub install EvoLinkAI/evolink-music

# Add your API key to OpenClaw config
export EVOLINK_API_KEY=your-key-here
```

### Prompt Template

**Simple Mode (AI writes lyrics and picks style):**
```
Generate music: [describe the vibe]

Examples:
- "A chill lo-fi hip-hop beat for studying"
- "Upbeat pop song about summer adventures"
- "Epic orchestral soundtrack for a fantasy game"
- "Relaxing ambient music for meditation"
```

**Custom Mode (you control lyrics and style):**
```
Create a song with these lyrics:
[Verse 1]
[your lyrics here]

[Chorus]
[your lyrics here]

Style: [genre, mood, tempo, vocals]
Example: "indie folk, melancholic, 90bpm, female vocals"
```

**Instrumental Only:**
```
Generate instrumental music: [describe style]
Example: "Jazz piano trio, upbeat, 4 minutes"
```

### Advanced Usage
- **Duration**: "Make it 2 minutes long"
- **Model selection**: "Use Suno v5 for studio-grade quality"
- **Vocal gender**: "Male vocals" / "Female vocals"
- **Negative tags**: "No drums" / "No electronic elements"

## Success Metrics
- Music generated in 1–3 minutes
- Matches your creative vision and genre
- Professional production quality
- Royalty-free and ready to use commercially
- Costs $0.10–0.50 per track (vs. $200+ for a composer)

---

*Powered by Suno v4, v4.5, and v5 via EvoLink API*
