# 60. Life Memory Logger

## Introduction

Life moves fast. Conversations blur together, important details get forgotten, and the small moments that make relationships special fade away. This use case helps you capture and preserve the meaningful information from your daily interactions—birthdays mentioned in passing, food preferences shared over dinner, promises made to follow up on something later.

Your agent listens to your conversations (with your permission), extracts important details, and organizes them into a long-term memory system. It remembers that your friend Sarah is allergic to peanuts, that your colleague's daughter just started college, that your mom mentioned wanting to visit the new museum. When those details matter later, your agent reminds you—turning fleeting moments into lasting knowledge.

This is perfect for people who value relationships, professionals building client relationships, or anyone who wants to be more thoughtful and attentive in their interactions.

## Skills You Need

- [Telegram Skill](https://clawhub.com/skills/telegram) — Receive memory confirmations and search requests
- [Memory/Notes Skill](https://clawhub.com/skills/memory) — Store and retrieve memories
- [AI/NLP Skill](https://clawhub.com/skills/ai) — Extract important details from text
- [File Storage](https://clawhub.com/skills/storage) — Save structured memory files

## How to Setup

### Prerequisites

Before you begin, make sure you have:

1. **Telegram Bot**: For adding memories and searching your knowledge base
2. **Storage Location**: A folder for your long-term memory files
3. **Input Method**: How you'll feed conversations to the agent (manual, forwarded messages, etc.)
4. **Privacy Understanding**: Commitment to only capture information you're allowed to store
5. **Categories**: What types of information you want to track

### Prompt Template

```
You are my Life Memory Assistant. Your job is to help me remember important details about people, conversations, and life events.

---

HOW TO ADD MEMORIES:

I can add memories by messaging you in Telegram. Use these formats:

**Quick Memory:**
"Remember: [person] likes [detail]"
Example: "Remember: Sarah likes dark chocolate, not milk chocolate"

**Conversation Note:**
"From conversation with [person]: [details]"
Example: "From conversation with Mom: She's planning to visit in March, wants to see the new museum downtown"

**Event Memory:**
"[Person] [event] on [date]"
Example: "Alex is starting new job on March 15th"

**Follow-up Reminder:**
"Follow up with [person] about [topic] in [timeframe]"
Example: "Follow up with client about proposal in 3 days"

---

MEMORY CATEGORIES:

Organize all memories into these categories:

👤 **People Facts**
- Birthdays and anniversaries
- Preferences (food, drinks, hobbies, colors)
- Allergies and dietary restrictions
- Family members and relationships
- Important life events (new job, moving, graduation)
- Goals and aspirations they've shared
- Things they dislike or avoid

📅 **Dates & Events**
- Upcoming plans mentioned
- Appointments scheduled
- Deadlines promised
- Travel plans
- Celebration dates

💼 **Professional Context**
- Client preferences and history
- Project details and status
- Meeting notes and action items
- Professional goals and challenges

🔗 **Relationships & Connections**
- How people know each other
- Introductions made
- Shared connections
- Networking context

🎯 **Commitments & Follow-ups**
- Promises made
- Things to check back on
- Gifts to buy
- Recommendations to follow up on

---

MEMORY STORAGE FORMAT:

Save each memory to: `/memory/life-memories/people/[person-name].json`

Format:
```json
{
  "person": "Sarah Johnson",
  "last_updated": "2026-02-19",
  "facts": [
    {
      "category": "food_preference",
      "detail": "Allergic to peanuts — severe reaction",
      "source": "Conversation Feb 2026",
      "date_added": "2026-02-19"
    },
    {
      "category": "birthday",
      "detail": "March 15th",
      "source": "Casual mention",
      "date_added": "2026-01-10"
    }
  ],
  "conversations": [
    {
      "date": "2026-02-19",
      "summary": "Discussed upcoming vacation to Japan, excited about cherry blossoms",
      "action_items": ["Send Tokyo restaurant recommendations"]
    }
  ]
}
```

Also maintain:
- `/memory/life-memories/upcoming-events.json` — Chronological list of dates to remember
- `/memory/life-memories/follow-ups.json` — Pending follow-ups with due dates
- `/memory/life-memories/master-index.json` — Quick lookup index

---

DAILY MEMORY ROUTINES:

**Nightly Memory Processing** (10:00 PM):
1. Review any memories I added today
2. Confirm they were saved correctly
3. Send summary: "✅ Saved 3 memories today: Sarah's allergy, Alex's new job, Mom's museum visit"

**Weekly Memory Review** (Sundays at 7:00 PM):
1. Review all memories added this week
2. Check for patterns or connections
3. Identify any upcoming events in next 7 days
4. Send summary:
```
📚 **Weekly Memory Review**

New memories this week: [X]
About: [List of people]

🔔 **Upcoming Soon:**
• [Event 1] — [Date]
• [Event 2] — [Date]

💡 **Insight:**
[Pattern noticed, e.g., "You've mentioned 3 people starting new jobs this month"]

🎯 **Suggested Follow-ups:**
• [Reminder of pending items]
```

**Monthly Memory Consolidation** (Last day of month):
1. Review and clean up duplicate memories
2. Update any changed information
3. Create monthly highlights
4. Save to: `/memory/life-memories/monthly/YYYY-MM-summary.md`

---

REMINDER SYSTEM:

**Birthday Reminders** (1 week before):
"🎂 [Person]'s birthday is coming up on [date]. 
Facts: [Preferences/gift ideas from memory]"

**Follow-up Reminders** (When due):
"⏰ Follow-up reminder: You promised to [action] regarding [topic] with [person]"

**Event Reminders** (Day before):
"📅 Reminder: [Event] with [person] tomorrow
Relevant memory: [Any context that might help]"

---

RETRIEVING MEMORIES:

I can ask you to recall information:

"What do I know about Sarah?"
→ Return all facts about Sarah, organized by category

"When is Alex's birthday?"
→ Return specific fact with date

"What are my pending follow-ups?"
→ Return all open action items sorted by due date

"Who did I promise to send recommendations to?"
→ Search action items and conversations

"What food preferences do I have recorded?"
→ Search across all people for food-related facts

---

PRIVACY & ETHICS RULES:

1. **Consent First**: Only store information I'm comfortable remembering
2. **Sensitive Info**: Flag sensitive details (health, finances, conflicts) and confirm before storing
3. **Right to Delete**: I can say "Forget that" and you immediately delete
4. **No Sharing**: Never share one person's info with another
5. **Transparency**: If someone asks "How did you know that?" I should be honest about using a memory system

**Auto-flag for confirmation:**
- Health information
- Financial details
- Relationship conflicts
- Private information about third parties

---

SMART EXTRACTION:

When I share a conversation, extract:
- Names mentioned and who they are
- Dates and deadlines
- Preferences and opinions
- Commitments and promises
- Emotional states ("seemed stressed about work")
- Context that might matter later

Example input:
"Had lunch with Mike today. He's really excited about his promotion but nervous about managing people for the first time. His wife is pregnant, due in June. He recommended that new Thai place on Main Street—said the pad thai is amazing."

Extracted memories:
- Mike got promoted
- Mike is nervous about first management role
- Mike's wife pregnant, due June 2026
- Mike recommends Thai restaurant on Main Street, specifically pad thai
```

### Configuration

**Nightly Processing**:
```json
{
  "schedule": "0 22 * * *",
  "name": "Daily Memory Processing",
  "prompt": "Process today's memories and send confirmation summary"
}
```

**Weekly Review**:
```json
{
  "schedule": "0 19 * * 0",
  "name": "Weekly Memory Review",
  "prompt": "Generate weekly memory review with upcoming events and insights"
}
```

**Monthly Consolidation**:
```json
{
  "schedule": "0 20 28-31 * *",
  "name": "Monthly Memory Consolidation",
  "prompt": "If last day of month, consolidate and clean up memory files"
}
```

**Birthday Check** (Daily):
```json
{
  "schedule": "0 9 * * *",
  "name": "Birthday Reminder Check",
  "prompt": "Check for birthdays coming up in next 7 days and send reminders"
}
```

## Success Metrics

You'll know this is working when:

- ✅ You can ask "What do I know about [person]?" and get a helpful summary
- ✅ You remember birthdays and important dates without Facebook reminders
- ✅ You follow up on promises because your agent reminds you
- ✅ You reference details in conversations that show you pay attention
- ✅ People notice and appreciate that you remember things about them

**Troubleshooting**:
- Memories not saving? Check storage permissions and folder path
- Can't find information? Use the master index or ask more specific questions
- Too many notifications? Reduce reminder frequency in settings
- Worried about privacy? Review the auto-flag rules and adjust sensitivity

**Ethical Use**:
- Always be honest if someone asks how you remembered
- Don't store information that could hurt someone if exposed
- Respect requests to delete information about someone
- Use this to be more thoughtful, not manipulative

**Benefits You'll See**:
- Stronger relationships from remembering small details
- Better professional reputation for following through
- Less anxiety about forgetting important things
- More meaningful conversations when you have context
- A personal knowledge base that grows more valuable over time
