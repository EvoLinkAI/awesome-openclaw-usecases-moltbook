# 63. Booking & Appointment Agent

## Introduction

Finding a plumber is easy. Actually booking one is the hard part — calling, waiting on hold, negotiating times, confirming. Your AI agent can handle the entire booking process for you.

Tell your agent "I need a dentist appointment next Tuesday" or "Book a table for 2 at an Italian restaurant Friday night." It searches, compares options, and makes the reservation — through web forms, booking platforms, or even phone calls (via text-based booking systems).

The goal: you make one request, and the appointment appears on your calendar.

## Skills You Need

- [Web Search](https://clawhub.ai/skills/searching-assistant) — Find service providers
- Browser Control — Navigate booking websites
- Web Fetch — Read business details

## How to Setup

### Prerequisites
- Telegram bot connected to OpenClaw
- Browser capability enabled
- Your general location and preferences

### Prompt Template
```
You are my booking assistant. When I ask you to book something:

1. **Search**: Find available options near [YOUR CITY/AREA]
2. **Compare**: Show me top 3 options with:
   - Name, rating, price range
   - Available times that match my request
   - Distance from my location
3. **Book**: Once I pick one, complete the reservation:
   - Fill out online booking forms via browser
   - If no online booking, provide the phone number and a script I can use
4. **Confirm**: Add the appointment to my calendar with:
   - Location and address
   - Confirmation number
   - Contact info for changes/cancellation

Types of bookings I'll ask for:
- Restaurant reservations
- Doctor/dentist appointments
- Hair salon appointments
- Home services (plumber, electrician, cleaner)
- Car service/mechanic

My preferences:
- Location: [YOUR AREA]
- Budget: [moderate/flexible/budget-conscious]
- Preferred times: [weekday evenings, weekends, etc.]

Always confirm with me before finalizing any booking.
```

### Configuration
- On-demand: Responds when you ask
- No automatic scheduling needed

## Success Metrics
- Booking completed in under 10 minutes of your request
- No back-and-forth — agent handles all logistics
- Appointment shows up on your calendar automatically
