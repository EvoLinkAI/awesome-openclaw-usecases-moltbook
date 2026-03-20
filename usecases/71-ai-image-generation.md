# 71. AI Image Generation

## Introduction

Need a custom illustration for your blog post? A product mockup for a pitch deck? A social media graphic that stands out? Instead of spending hours in Photoshop or hiring a designer, your AI agent can generate professional images in seconds using Nano Banana 2 — Google's Gemini 3.1 Flash image model.

This use case lets you create images through natural conversation. Describe what you want, and your agent handles the technical details — model selection, aspect ratios, prompt optimization. The result is delivered directly to your chat, ready to download and use.

Perfect for content creators, marketers, developers, and anyone who needs custom visuals without the design overhead.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `evolink-nano-banana-2` | [ClawHub](https://clawhub.ai/EvoLinkAI/evolink-nano-banana-2) | AI image generation via Gemini 3.1 Flash |

## How to Setup

### Prerequisites
- An EvoLink API key ([sign up at evolink.ai/signup](https://evolink.ai))
- OpenClaw with Telegram or Signal connected

### Installation
```bash
# Install the skill
clawhub install EvoLinkAI/evolink-nano-banana-2

# Add your API key to OpenClaw config
export EVOLINK_API_KEY=your-key-here
```

### Prompt Template
```
Generate an image: [describe what you want]

Examples:
- "A minimalist logo for a coffee shop called 'Morning Brew'"
- "A futuristic cityscape at sunset, cyberpunk style"
- "Product photo of wireless earbuds on a marble surface"
- "Cartoon illustration of a friendly robot teaching kids"
```

### Advanced Usage
For more control, specify:
- **Aspect ratio**: "Make it 16:9 for a blog header"
- **Style**: "Photorealistic" / "Illustration" / "3D render"
- **Variations**: "Generate 3 different versions"

## Success Metrics
- Image generated in under 30 seconds
- Matches your description accurately
- High enough quality for professional use
- No need to learn complex design tools
- Costs ~$0.01–0.05 per image (vs. $50+ for a designer)

---

*Powered by Nano Banana 2 (Gemini 3.1 Flash) via EvoLink API*
