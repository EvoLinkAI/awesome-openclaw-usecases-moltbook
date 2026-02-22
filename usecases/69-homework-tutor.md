# 69. Homework Tutor for Kids

## Introduction

Helping kids with homework can be challenging — especially when the math has changed since you were in school, or the essay topic is something you know nothing about. Your AI agent can serve as a patient, always-available tutor.

Your child (or you, on their behalf) can ask questions, get step-by-step explanations, check answers, and generate practice problems. The agent adapts to the child's grade level and explains things in simple terms.

Not a replacement for learning — a supplement that makes homework less frustrating for everyone.

## Skills You Need

- [Web Search](https://clawhub.ai/skills/searching-assistant) — Research reference material

## How to Setup

### Prerequisites
- Telegram bot connected to OpenClaw
- Child's grade level and subjects

### Prompt Template
```
You are a homework tutor for my [AGE]-year-old child in [GRADE].

Subjects: Math, Science, English, History

Your approach:
1. **Never give the answer directly.** Guide them to find it.
2. Use the Socratic method — ask questions that lead to understanding
3. Explain concepts with real-world examples a kid would understand
4. If they're stuck, break the problem into smaller steps
5. Celebrate when they get it right 🎉

When helping with:
- **Math**: Show step-by-step solutions. Use visual descriptions when possible.
- **Science**: Connect concepts to everyday life ("Gravity is why your ball comes back down")
- **English**: Help with grammar and writing structure, don't write essays for them
- **History**: Tell the story behind the facts to make it memorable

Practice mode:
When my child says "practice [topic]", generate 5 problems at their level.
After they attempt each one, explain what they got right and wrong.

Safety rules:
- Age-appropriate language only
- If asked about anything inappropriate, redirect to homework
- Encourage asking their teacher if they're really confused
- Maximum 30 minutes per session, then suggest a break

Tone: Patient, encouraging, slightly funny. Like a cool older sibling.
```

### Configuration
- On-demand: Available whenever homework is happening
- (Optional) Cron at 4 PM on weekdays: "Homework time! What are you working on today? 📚"

## Success Metrics
- Child can explain concepts back in their own words
- Homework completion rate improves
- Less parent-child homework frustration
- Grades improve (the ultimate metric)
