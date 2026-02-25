# Voice Calling & SMS Agent

Enable OpenClaw to make phone calls, send SMS messages, and run AI-powered call missions.

---

## Introduction

**ClawdTalk** is a skill that gives OpenClaw real-world communication capabilities through voice calls and SMS. It's built on Telnyx's Voice AI and Messaging APIs, enabling AI agents to:

- Make outbound calls for appointments, reminders, and follow-ups
- Receive inbound calls for customer support or triage
- Send and receive text messages
- Run automated call missions with custom objectives
- Transcribe calls for documentation

This transforms OpenClaw from a chat-based assistant into a communication hub that can interact with anyone via phone or text.

---

## Skills You Need

| Skill | Install | Purpose |
|-------|---------|---------|
| ClawdTalk | `clawhub install clawdtalk-client` | Voice calls, SMS, call missions |

**Links:**
- GitHub: https://github.com/team-telnyx/clawdtalk-client
- Website: https://clawdtalk.com

---

## How to Setup

### 1. Install the Skill

```bash
clawhub install clawdtalk-client
```

### 2. Configure Telnyx Credentials

You'll need a Telnyx account with:
- API Key
- Messaging Profile ID
- Phone number(s)

Add to your OpenClaw config:

```json
{
  "skills": {
    "clawdtalk": {
      "api_key": "YOUR_TELNYX_API_KEY",
      "messaging_profile_id": "YOUR_PROFILE_ID",
      "phone_number": "+1234567890"
    }
  }
}
```

### 3. Basic Usage Examples

**Make a call:**
```
"Call John at +15551234567 and remind him about our meeting tomorrow at 3pm"
```

**Send an SMS:**
```
"Text Sarah: The package arrived, you can pick it up anytime"
```

**Run a call mission:**
```
"Call all pending appointment confirmations for tomorrow and confirm or reschedule"
```

### 4. Advanced: Call Missions

Call missions let you automate multi-call workflows:

```
Create a call mission for customer feedback:
1. Call customers from yesterday's service
2. Ask 3 rating questions
3. Record responses
4. Send summary to my email
```

---

## Success Metrics

| Metric | Before | After |
|--------|--------|-------|
| Appointment confirmations | Manual calls | Automated via AI |
| Customer response time | Hours | Minutes |
| SMS outreach | Manual copy-paste | Single command |
| Call documentation | Notes after call | Auto-transcribed |

---

## Real-World Applications

- **Healthcare**: Appointment reminders, prescription refill notifications
- **Sales**: Lead qualification calls, follow-up sequences
- **Support**: Inbound call handling, ticket creation
- **Personal**: Wake-up calls, medication reminders, event notifications

---

## Related Use Cases

- [Daily Morning Briefing](52-morning-briefing-telegram.md) - Could include voice call delivery
- [Email Auto-Sorter](56-email-auto-sorter.md) - SMS alerts for urgent emails
- [Booking & Appointment Agent](63-booking-appointment-agent.md) - Voice confirmation calls

---

*Source: [ClawdTalk](https://clawdtalk.com) by Telnyx*
