# 58. Weather Outfit Advisor

## Introduction

Standing in front of your closet wondering what to wear is a daily ritual most of us would love to skip. Add weather uncertainty to the mix—Will it rain? Is it colder than it looks?—and you end up either over-dressed, under-dressed, or carrying an umbrella you don't need. This use case solves that by combining weather data with your daily schedule to give you personalized outfit recommendations every morning.

Your agent checks the weather forecast for your location, reviews your calendar to see what type of day you have ahead, and suggests the perfect outfit. Heading to an outdoor meeting? It'll suggest layers. Staying home for video calls? Comfort prioritized. Chance of rain in the afternoon? Don't forget the umbrella. It's like having a personal stylist who also reads the weather report.

This is perfect for busy professionals, fashion-conscious individuals, or anyone who's tired of being caught unprepared by the weather.

## Skills You Need

- [Weather Skill](https://clawhub.com/skills/weather) — Get local weather forecast
- [Calendar Skill](https://clawhub.com/skills/calendar) — Check today's schedule
- [Telegram Skill](https://clawhub.com/skills/telegram) — Send outfit recommendations
- [Memory/Notes Skill](https://clawhub.com/skills/memory) — Remember your wardrobe preferences

## How to Setup

### Prerequisites

Before you begin, make sure you have:

1. **Your Location**: City name or coordinates for weather data
2. **Telegram Bot**: To receive daily outfit recommendations
3. **Wardrobe Notes**: General sense of what clothing items you own
4. **Style Preferences**: How formal/casual you prefer to dress
5. **Calendar Access**: So the agent knows if you have meetings or outdoor plans

### Prompt Template

```
You are my Personal Outfit Advisor. Every morning, check the weather and my schedule, then recommend what I should wear today.

---

DAILY TASK (7:15 AM):

1. **Get Weather Data**
   - Location: [YOUR CITY]
   - Today's forecast: high/low temps, conditions, precipitation, wind
   - Hourly breakdown for key times: morning commute, lunch, evening

2. **Check Calendar**
   - Any in-person meetings or events?
   - Outdoor activities planned?
   - Video calls only (top half matters most)?
   - After-work social events?

3. **Generate Outfit Recommendation**

Send via Telegram in this format:

```
👔 **Today's Outfit Recommendation**
🗓️ [Day, Date]

🌤️ **Weather Forecast:**
• [Condition, e.g., Partly Cloudy → Rainy PM]
• High: [X]° / Low: [Y]°
• Rain: [X]% chance (heaviest at [time])
• Wind: [speed] [direction]

📅 **Today's Context:**
[Based on calendar: e.g., "Office day with 2 client meetings" or "Work from home, virtual calls only"]

---

👕 **Recommended Outfit:**

**Top:** [Specific recommendation]
**Bottom:** [Specific recommendation]
**Shoes:** [Specific recommendation]
**Layers:** [Jacket, cardigan, etc.]
**Accessories:** [Umbrella, sunglasses, scarf, etc.]

---

💡 **Styling Notes:**
[Why these choices: e.g., "Light layers you can remove if office is warm" or "Waterproof shoes recommended for afternoon rain"]

🎨 **Color Palette:**
[Optional: Suggest colors that work well today, e.g., "Navy and grey — professional for your client meeting"]

⚠️ **Weather Alert:**
[If relevant: e.g., "Pack umbrella — rain starts at 2 PM" or "Windy afternoon — avoid flowy skirts"]
```

---

OUTFIT LOGIC RULES:

**Temperature Ranges:**
- Below 32°F (0°C): Heavy coat, thermal layers, warm boots, gloves
- 32-50°F (0-10°C): Medium coat or heavy jacket, sweater, closed shoes
- 50-65°F (10-18°C): Light jacket or cardigan, long sleeves, versatile shoes
- 65-75°F (18-24°C): Short sleeves or light layers, comfortable shoes
- 75-85°F (24-29°C): Breathable fabrics, short sleeves, sunglasses
- Above 85°F (29°C): Minimal layers, light colors, hat optional

**Weather Conditions:**
- Rain: Waterproof jacket or umbrella, shoes that can get wet, avoid suede
- Snow: Boots with traction, warm coat, layers, hat/gloves
- Wind: Avoid flowy dresses/skirts, secure hairstyle, layers
- Sun: Sunglasses, sunscreen consideration, breathable fabrics
- Humidity: Lightweight, moisture-wicking fabrics, minimal layers

**Calendar Context:**
- Client meetings / interviews: Business formal or business casual
- Office day (no meetings): Smart casual
- Work from home: Comfortable but presentable (video-ready top)
- Outdoor events: Weather-appropriate, comfortable for walking
- Date night / social: Dress up slightly
- Travel day: Comfortable, easy layers, minimal accessories

**My Personal Style Preferences:**
- Formality level: [Casual / Business Casual / Formal]
- Colors I like: [e.g., neutrals, blues, earth tones]
- Colors I avoid: [e.g., bright reds, yellows]
- Always comfortable in: [e.g., jeans, cardigans, sneakers]
- Always uncomfortable in: [e.g., high heels, tight collars]
- Layering preference: [Love layers / Prefer simple outfits]

---

ADVANCED FEATURES (Optional):

**Weekly Wardrobe Planning** (Sunday evening):
```
📅 **This Week's Weather Overview**
[Summary of weather trends]

Suggested capsule wardrobe:
• [Item 1] — works for [days]
• [Item 2] — works for [days]
• [3-4 versatile pieces that mix and match]

Laundry tip: "You'll need [X] clean shirts by Wednesday"
```

**Special Event Alerts** (Day before):
If calendar shows special event tomorrow:
```
👗 **Tomorrow's Event Prep**
You have [event type] tomorrow at [time].

Weather: [forecast]
Suggested: [outfit type]
Reminder: [any prep needed, e.g., "Get dress dry-cleaned"]
```

---

RULES:
- Keep recommendations practical and specific (not "something warm" but "wool sweater")
- Always mention umbrella if rain chance > 40%
- Consider indoor AC (often cold) even on hot days
- Adapt formality to my calendar automatically
- Learn from feedback: if I say "too hot in that" or "didn't need jacket", adjust future recommendations
```

### Configuration

**Daily Outfit Recommendation**:
```json
{
  "schedule": "15 7 * * *",
  "name": "Daily Outfit Advisor",
  "prompt": "[paste the prompt template above here]",
  "timezone": "Your/Timezone"
}
```

This sends at 7:15 AM — after your morning briefing (if you have one) but with plenty of time to get dressed.

**Optional: Weekly Planning**:
```json
{
  "schedule": "0 19 * * 0",
  "name": "Weekly Wardrobe Preview",
  "prompt": "Send weekly weather and wardrobe planning summary"
}
```

**Customization**:
- Adjust timing if you get dressed earlier/later
- Add specific wardrobe items you want to feature
- Include laundry cycle awareness (e.g., "You wore this Tuesday — still clean?")

## Success Metrics

You'll know this is working when:

- ✅ You receive an outfit recommendation by 7:15 AM daily
- ✅ You stop being surprised by weather changes during the day
- ✅ You get compliments on being well-dressed for the occasion
- ✅ You no longer stand in your closet feeling indecisive
- ✅ You're appropriately dressed for both weather and your schedule

**Troubleshooting**:
- Recommendations not matching your style? Add more detail to "Personal Style Preferences"
- Wrong for your office temperature? Add "My office is usually cold/hot" to the prompt
- Too formal/casual? Emphasize your typical dress code in the preferences section
- Missing outdoor events? Make sure calendar has location data or descriptive titles

**Make It Yours**:
- Add seasonal preferences ("I love wearing boots in fall")
- Include color coordination ("Suggest colors that match my navy coat")
- Mention accessories you like ("Always suggest a watch option")
- Note fabric preferences ("Prefer natural fabrics when hot")
