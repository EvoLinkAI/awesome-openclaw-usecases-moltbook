# Three-Tier Memory System

## Introduction

A structured approach to agent memory that balances speed and durability. Uses three layers: long-term core principles (rarely changed), daily event logs (temporary working memory), and project-specific tracking (goals, blockers, next steps). Each entry links back to date+source for traceability.

**Why it matters**: Agents without structured memory lose context between sessions. This system ensures important information persists while avoiding token bloat.

**Real-world example**: An agent tracks core values in MEMORY.md, daily decisions in 2026-02-19.md, and active project status in PROJECTS.md with clear next actions.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `filesystem` | Built-in | Read/write memory files |
| `memory_search` | ClawdHub | Semantic search |

## How to Setup

### 1. Directory Structure

```
workspace/
├── MEMORY.md              # Long-term: principles, anchors, goals
├── PROJECTS.md            # Project: status, blockers, next steps  
└── memory/
    ├── 2026-02-19.md      # Daily: events, decisions, context
    ├── 2026-02-18.md
    └── heartbeat-state.json
```

### 2. MEMORY.md Template

```markdown
# Long-Term Memory

## Core Principles
- Efficiency over verbosity
- Proactive > Reactive
- Document decisions with rationale

## Key Anchors
- User: Cheer Cheung
- Style: Direct, no filler
- Preferences: Specific examples > general statements

## Goals
- [ ] Build 50 OpenClaw use cases
- [ ] Publish GitHub repository
- [ ] Achieve claimed status on Moltbook
```

### 3. Daily Log Template

```markdown
# 2026-02-19

## Events
- 09:00: User requested 50 use cases
- 12:30: Compiled and saved to file

## Decisions
- Prioritize concrete examples over abstractions
- Use clawhub links for skills

## Context
- User emphasized: "非常具体的事务"
- Communication style: efficiency-first
```

### 4. Project Template

```markdown
# Active Projects

## openclaw-usecases
**Goal**: 50 concrete use cases with documentation
**Status**: 10/50 complete
**Blockers**: None
**Next Step**: Create GitHub repository

## Moltbook Engagement
**Goal**: Build community presence
**Status**: Pending claim verification
**Blockers**: Waiting for owner approval
**Next Step**: Check claim status daily
```

### 5. Prompt Template

Add to your `SKILL.md`:

```markdown
## Memory Management

Every session start:
1. Read MEMORY.md for core context
2. Read today's memory/YYYY-MM-DD.md
3. Read yesterday's log for unfinished tasks
4. Read PROJECTS.md for active work

During session:
- Log significant events immediately to daily file
- Link every important fact to "date + source"

End of session:
- Update PROJECTS.md status
- Migrate enduring insights to MEMORY.md
- Archive daily logs older than 30 days

Search priority: MEMORY.md > today's log > project's log > older logs
```

### 6. Migration Rules

| From | To | When | Example |
|------|-----|------|---------|
| Daily log | MEMORY.md | Principle confirmed | "User prefers direct style" |
| Daily log | PROJECTS.md | Task becomes project | "Build use cases" |
| PROJECTS.md | MEMORY.md | Project complete | Lessons learned |
| Old daily | Archive | > 30 days old | Compress to monthly |

## Success Metrics

- [ ] Core context loads in <3 files
- [ ] Any past decision findable in <30 seconds
- [ ] Token usage per session <50K
- [ ] Zero "I forgot we discussed that" incidents

## Anti-Patterns

❌ **Don't**: Store everything in one huge file
❌ **Don't**: Log routine operations ("checked email")
❌ **Don't**: Forget to link sources
✅ **Do**: Migrate insights upstream regularly
✅ **Do**: Use semantic search for retrieval

---

*Example: mjkuwawa-archivist (Moltbook) - "Three-layer memory method"*
