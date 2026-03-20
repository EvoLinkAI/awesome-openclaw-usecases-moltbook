# 72. AI Video Generation

## Introduction

Creating video content used to require cameras, editing software, and hours of production time. Now your AI agent can generate professional videos from a simple text description or a reference image — product demos, social media clips, explainer animations, or cinematic B-roll.

This use case gives you access to 37 cutting-edge video models including Sora, Kling, Veo 3, Seedance, Hailuo, and WAN. Your agent handles model selection, parameter tuning, and progress tracking. You just describe what you want, and the video appears in your chat minutes later.

Perfect for marketers, content creators, educators, and anyone who needs video content without the production overhead.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `evolink-video` | [ClawHub](https://clawhub.ai/EvoLinkAI/evolink-video) | AI video generation with 37 models |

## How to Setup

### Prerequisites
- An EvoLink API key ([sign up at evolink.ai/signup/signup](https://evolink.ai))
- OpenClaw with Telegram or Signal connected

### Installation
```bash
# Install the skill
clawhub install EvoLinkAI/evolink-video

# Add your API key to OpenClaw config
export EVOLINK_API_KEY=your-key-here
```

### Prompt Template

**Text-to-Video:**
```
Generate a video: [describe the scene]

Examples:
- "A drone shot flying over a misty mountain range at sunrise"
- "Product demo: wireless earbuds rotating on a clean white background"
- "Time-lapse of a flower blooming, macro photography style"
- "Cinematic shot of a futuristic city with flying cars"
```

**Image-to-Video:**
```
Animate this image: [attach or describe image]
Make it [describe motion/effect]

Example:
- "Animate this product photo — add a slow 360° rotation"
- "Make this landscape photo come alive with moving clouds and swaying trees"
```

### Advanced Usage
- **Duration**: "Make it 10 seconds long"
- **Model selection**: "Use Sora for cinematic quality" / "Use Kling for fast generation"
- **Audio**: "Add auto-generated background audio"
- **First-last frame**: Provide 2 images to control start and end frames

## Success Metrics
- Video generated in 1–5 minutes (depending on model and duration)
- Matches your creative vision
- High enough quality for social media or presentations
- No need for video editing software
- Costs $0.10–2.00 per video (vs. $500+ for professional production)

---

*Powered by 37 video models (Sora, Kling, Veo 3, Seedance, Hailuo, WAN, Grok) via EvoLink API*
