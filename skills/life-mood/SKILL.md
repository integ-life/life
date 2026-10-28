---
name: life-mood
description: Log and review the user's mood / energy / reflections (status logs) in life-on-golang. Trigger when they share how they're feeling, journal a daily reflection, or want to look back at past entries.
---

# life-mood

Status logs are the user's lightweight journal — feelings, energy levels, end-of-day reflections. Each entry has a `log_type` string, free-text content, and optionally a structured mood.

## When to use

- *"I'm feeling tired today"*, *"log that I was happy this morning"*
- *"how have I been this week"*, *"show my mood log"*
- *"reflection: today I learned ..."*

## Tools (MCP `life-on-golang`)

- `thoughts_list` (`/mcp` endpoint) or `status_logs_list` (legacy `/mcp/v1`) — same parameters: filter by `log_type`, date range
- `status_logs_add` — record a new entry

## Patterns

**Logging.** Pick a sensible `log_type`:
- `mood` — pair with the structured `mood` field (happy / excited / calm / anxious / angry / sad / tired / confused)
- `energy` — physical/mental energy levels
- `reflection` — end-of-day or end-of-week thinking

**Reviewing.** When asked "how have I been", pull last 7-14 days and look at the distribution of mood values — don't just dump rows.

**Mood field.** Only set if the user implies an emotion. Don't infer one for `reflection` or `energy` entries.
