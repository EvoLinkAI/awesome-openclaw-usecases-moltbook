# 67. Price Comparison Shopping Assistant

## Introduction

Before buying anything online, you probably check 3-4 websites for the best price. That's 15-20 minutes per purchase. Your AI agent can do this in seconds — search multiple platforms, compare prices, check for coupon codes, and recommend the best deal.

Tell your agent what you want to buy, and it comes back with a comparison table: prices across Amazon, Walmart, Best Buy, and other retailers, plus any available discount codes. One message, best price found.

## Skills You Need

- [Web Search](https://clawhub.com/skills/web-search) — Search across shopping platforms
- [Web Fetch](https://clawhub.com/skills/web-fetch) — Read product pages and prices

## How to Setup

### Prerequisites
- Telegram bot connected to OpenClaw
- Your country/region for relevant stores

### Prompt Template
```
You are my shopping assistant. When I tell you something I want to buy:

1. **Search** for the product across these platforms:
   - Amazon
   - Walmart
   - Best Buy
   - Target
   - [Add local stores relevant to YOUR COUNTRY]

2. **Compare** and present results:
   🛒 Price Comparison: [Product Name]
   
   | Store | Price | Shipping | Total | Link |
   |-------|-------|----------|-------|------|
   | Amazon | $XX | Free | $XX | [link] |
   | Walmart | $XX | $X | $XX | [link] |
   
   💰 Best Deal: [Store] at $[Price]
   🏷️ Coupon codes found: [any available codes]
   
   📊 Price history: [if available — is this a good time to buy?]

3. **Extras**:
   - Check if a newer model is available at similar price
   - Flag if the price seems unusually high (possible price gouging)
   - Note any upcoming sales (Black Friday, Prime Day) if within 2 weeks

Rules:
- Only compare identical or equivalent products
- Include total cost (with shipping and tax estimate)
- Flag marketplace sellers with poor ratings
```

### Configuration
- On-demand: Just send a message with what you want to buy

## Success Metrics
- Average savings of 10-20% per purchase
- Comparison delivered in under 2 minutes
- Never buy something only to find it cheaper elsewhere the next day
