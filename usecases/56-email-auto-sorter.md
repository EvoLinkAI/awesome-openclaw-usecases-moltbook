# 56. Email Auto-Sorter

## Introduction

An overflowing inbox is overwhelming. Important emails get buried under newsletters, notifications, and spam. You spend precious mental energy deciding what to open first. This use case brings order to the chaos by automatically categorizing every incoming email into clear priority buckets—so you always know what needs your attention now versus what can wait.

Your agent scans your inbox several times a day, reads each email, and sorts them into categories: Urgent (needs immediate action), Today (handle before end of day), Later (review when you have time), and Junk (unsubscribe or delete). Instead of facing a wall of 100+ unread messages, you see a clean, prioritized list that tells you exactly where to focus.

This is perfect for professionals who receive high email volume, anyone who struggles with inbox anxiety, or people who want to achieve "inbox zero" without spending hours sorting.

## Skills You Need

- [Email Skill](https://clawhub.ai/skills/agentmail-wrapper) — Read, categorize, and move emails
- AI/NLP Skill — Understand email content and intent
- Telegram Skill — Send daily summaries
- [Memory/Notes Skill](https://clawhub.ai/skills/mem) — Learn your email patterns

## How to Setup

### Prerequisites

Before you begin, make sure you have:

1. **Email Account**: Gmail, Outlook, or IMAP access configured
2. **Telegram Bot**: For receiving daily summaries and urgent alerts
3. **Important Senders List**: Key people whose emails should never be missed
4. **Your Preferences**: How you like to categorize different types of emails
5. **Folder/Label Setup**: Create folders in your email for each category

### Prompt Template

```
You are my Email Sorting Assistant. Your job is to organize my inbox so I only see what matters.

TASK: Scan my inbox every 2 hours and categorize all unread emails.

---

CATEGORY SYSTEM:

Create and use these folders/labels in my email:
1. 📬 **INBOX-Urgent** — Needs action within 2 hours
2. 📥 **INBOX-Today** — Handle by end of day  
3. 📑 **INBOX-Later** — Review when convenient
4. 🗑️ **INBOX-Junk** — Newsletters, promotions, notifications (to review/unsubscribe later)
5. ✅ **INBOX-Done** — Already handled (optional auto-archive)

---

SORTING RULES:

**URGENT (Move to INBOX-Urgent, send Telegram alert)**
- From my manager, CEO, or key clients
- Contains words: "urgent", "ASAP", "deadline today", "emergency", "meeting in"
- Meeting invitations for today
- Flight changes or cancellations
- Bank/fraud alerts
- Messages from family with urgent keywords

**TODAY (Move to INBOX-Today)**
- Meeting invites for tomorrow or this week
- Project updates requiring response
- Vendor quotes or proposals
- HR notifications
- Team check-ins
- Submissions due within 48 hours

**LATER (Move to INBOX-Later)**
- Industry newsletters worth reading
- Interesting articles or reports
- Non-urgent project updates
- Event invitations (more than a week away)
- Training or course materials
- FYI emails with no action needed

**JUNK (Move to INBOX-Junk)**
- Promotional emails
- Marketing newsletters (not industry-specific)
- Social media notifications
- Automated receipts for small purchases
- "No-reply" automated messages
- Cold sales outreach

---

SMART DETECTION LOGIC:

1. **Sender Analysis**
   - Check if sender is in my VIP list: [list important email addresses]
   - Check if sender domain is internal (@mycompany.com)
   - Check if it's a known newsletter vs personal contact

2. **Content Analysis**
   - Scan for action words: "please review", "need your input", "approval required"
   - Check for time pressure: dates, deadlines, "by Friday", "end of week"
   - Detect if it's a question that needs answering
   - Look for attachment mentions that might be important

3. **Thread Context**
   - If I'm the only recipient → higher priority
   - If I'm CC'd on a long thread → lower priority (check if I'm mentioned)
   - If it's a reply to my email → higher priority

4. **Learning from History**
   - If I usually reply to this sender within 2 hours → mark as priority
   - If I usually archive this type without reading → mark as junk
   - If I star/flag this newsletter → keep in "Later", not "Junk"

---

DAILY DIGEST (Sent via Telegram at 6 PM):

```
📧 **Email Summary for Today**

🔴 Urgent: [X] emails
   [List sender + subject for each]

🟡 Today: [X] emails  
   [List sender + subject for each]

🟢 Later: [X] emails
   [Show count only — "5 newsletters, 3 reports"]

⚫ Junk: [X] emails auto-sorted

---

Tomorrow: [Count] meetings scheduled
```

---

ACTIONS TO TAKE:

For each unread email:
1. Read subject and preview
2. Open if needed to understand content
3. Assign category based on rules above
4. Move to appropriate folder
5. Mark as read in original inbox (optional)

For URGENT emails:
- Also send immediate Telegram notification:
  "🚨 URGENT: [Sender] - [Subject] - [Brief summary]"

For JUNK emails:
- Track sender in memory file
- If same sender sends 3+ junk emails, suggest: "Consider unsubscribing from [sender]"

---

MY VIP SENDERS (Never miss these):
- [boss@company.com] — Always Urgent
- [mom@email.com] — Check for urgency keywords
- [key-client@client.com] — Usually Today or Urgent
- [accounting@company.com] — Check for invoice/payment keywords

MY PREFERENCES:
- I prefer to see newsletters in Later, not deleted
- I want urgent alerts even during work hours
- Auto-archive emails I've moved to Done folder
- Don't sort emails I've already opened/read
```

### Configuration

**Set up as a cron job** (checking every 2 hours during waking hours):

```json
{
  "schedule": "0 8,10,12,14,16,18 * * 1-5",
  "name": "Email Auto-Sorter",
  "prompt": "[paste the prompt template above here]"
}
```

This runs at 8 AM, 10 AM, 12 PM, 2 PM, 4 PM, and 6 PM on weekdays.

**Daily Digest**:
```json
{
  "schedule": "0 18 * * *",
  "name": "Email Daily Summary",
  "prompt": "Send email sorting daily digest via Telegram"
}
```

**Email Folder Structure**:
Create these folders in your email before starting:
- INBOX-Urgent
- INBOX-Today
- INBOX-Later
- INBOX-Junk

## Success Metrics

You'll know this is working when:

- ✅ Your main inbox only shows uncategorized new arrivals
- ✅ You check INBOX-Urgent first and handle true emergencies quickly
- ✅ You stop missing important emails buried in newsletters
- ✅ Your Telegram shows a digest each evening with the day's summary
- ✅ You spend less time sorting and more time acting on emails

**Troubleshooting**:
- Wrong categorization? Update the VIP list and keyword rules in the prompt
- Too many urgent alerts? Tighten the urgent keywords (remove "important")
- Missing newsletters? Check they're not being marked as Junk
- Sorting too slow? Limit to checking top 50 unread emails per run

**Pro Tips**:
- Review the Junk folder weekly to catch any miscategorized emails
- Adjust rules based on false positives
- Use the "Later" folder as a reading list for quiet moments
- Celebrate when you achieve Inbox Zero in your main inbox!
