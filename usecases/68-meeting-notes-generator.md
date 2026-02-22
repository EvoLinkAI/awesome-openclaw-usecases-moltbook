# 68. Meeting Notes Auto-Generator

## Introduction

After every meeting, someone needs to write up the notes: what was discussed, what was decided, and who's doing what. It's tedious work that nobody wants to do. Your AI agent can generate structured meeting notes from your rough notes or audio transcription.

Just paste your raw notes, bullet points, or meeting transcript into the chat, and your agent transforms them into clean, professional meeting minutes — complete with action items, decisions, and follow-up dates.

## Skills You Need

- [Memory Management](https://clawhub.ai/skills/mem) — Store meeting history

## How to Setup

### Prerequisites
- Telegram or Signal connected to OpenClaw
- Raw meeting notes or transcript (from Otter.ai, Zoom transcript, or your own notes)

### Prompt Template
```
You are my meeting notes assistant. When I paste raw notes or a transcript:

1. **Generate structured meeting minutes**:

   📋 Meeting Notes | [Date]
   
   **Attendees**: [extract names mentioned]
   **Duration**: [estimate from content]
   **Topic**: [main subject]
   
   ## Summary
   [3-5 sentence overview of what was discussed]
   
   ## Key Decisions
   - ✅ [Decision 1]
   - ✅ [Decision 2]
   
   ## Action Items
   | Task | Owner | Deadline |
   |------|-------|----------|
   | [Task] | [Person] | [Date] |
   
   ## Open Questions
   - ❓ [Unresolved topic that needs follow-up]
   
   ## Next Meeting
   [Date/time if mentioned]

2. **Save** the notes to memory/meetings/YYYY-MM-DD-[topic].md

3. **Follow up**: On the deadline dates, remind me about pending action items.

Rules:
- Keep it concise — no one reads 3-page meeting notes
- Bold the most important decisions
- If action items don't have clear owners, flag them
- If raw notes are messy, ask me clarifying questions
```

### Configuration
- On-demand: Paste notes anytime
- Follow-up reminders: Cron checks action item deadlines daily at 9 AM

## Success Metrics
- Meeting notes generated in under 1 minute
- Action items tracked and followed up automatically
- No one asks "What did we decide in that meeting?" anymore
