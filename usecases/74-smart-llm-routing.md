# 74. Smart LLM Routing

## Introduction

Running an AI agent 24/7 can get expensive fast. Every task — from simple Q&A to complex code generation — costs money. But here's the thing: most tasks don't need your most powerful (and expensive) model. A quick status check doesn't need Claude Opus. A simple translation doesn't need GPT-5.

This use case implements intelligent model routing that automatically picks the cheapest model capable of handling each task. Your agent analyzes the request, routes it to the optimal model (Claude, GPT, Gemini, DeepSeek, Kimi, or Doubao), and escalates only when needed. The result? **60–85% cost reduction** with no quality loss.

Perfect for anyone running OpenClaw agents at scale — developers, businesses, power users, or anyone who wants to keep their AI costs under control.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `oc-skill-router` | [ClawHub](https://clawhub.ai/EvoLinkAI/oc-skill-router) | Smart LLM routing across 20+ models |

## How to Setup

### Prerequisites
- An EvoLink API key ([sign up at evolink.ai/signup/signup](https://evolink.ai))
- OpenClaw configured with at least one agent

### Installation
```bash
# Install the skill
clawhub install EvoLinkAI/oc-skill-router

# Add your API key to OpenClaw config
export EVOLINK_API_KEY=your-key-here
```

### Configuration
Add the Evolink provider to your `~/.openclaw/openclaw.json`:
```json
{
  "providers": {
    "evolink": {
      "type": "openai",
      "baseURL": "https://direct.evolink.ai/v1",
      "apiKey": "${EVOLINK_API_KEY}"
    }
  }
}
```

### How It Works

The router automatically analyzes every task and picks the optimal model:

**Tier 1 — Lightweight (60% of tasks)**
- Quick Q&A, status checks, simple translations
- Routes to: Claude Haiku, Gemini Flash
- Cost: ~$0.001 per request

**Tier 2 — Balanced (30% of tasks)**
- Content creation, coding, data analysis
- Routes to: Claude Sonnet, GPT-5.1, Gemini Pro
- Cost: ~$0.01 per request

**Tier 3 — Flagship (10% of tasks)**
- Deep reasoning, architecture design, security audits
- Routes to: Claude Opus, GPT-5.2, DeepSeek Reasoner
- Cost: ~$0.05 per request

### Prompt Template
```
# No special prompts needed — routing is automatic!

# But you can override when needed:
"Use Opus for this — it's important"
"Quick answer, keep it simple" (forces Tier 1)
"Think carefully about this" (forces Tier 3)

# Preview routing decision without executing:
/route [describe your task]
```

## Success Metrics
- **60–85% cost reduction** compared to always using flagship models
- No quality loss on routine tasks
- Automatic escalation when complexity increases
- Transparent routing decisions (you see which model was picked and why)
- Works across 6 providers: Claude, GPT, Gemini, DeepSeek, Kimi, Doubao

### Example Savings
**Before (always Claude Opus):**
- 1000 requests/day × $0.05 = **$50/day** = **$1,500/month**

**After (smart routing):**
- 600 requests → Haiku ($0.001) = $0.60
- 300 requests → Sonnet ($0.01) = $3.00
- 100 requests → Opus ($0.05) = $5.00
- **Total: $8.60/day** = **$258/month**
- **Savings: $1,242/month (83%)**

---

*Powered by Evolink Smart Router — 20+ models, one API key*
