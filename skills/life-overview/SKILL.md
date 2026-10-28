---
name: life-overview
description: Cross-domain summaries for the user's life-on-golang data. Trigger when the user asks broad questions like 'how was my week', 'what's going on', 'give me a status update', that span money + todos + goals + mood + focus time.
---

# life-overview

Use this when no single domain skill covers the question. The pattern is: call several of the read tools in parallel, then synthesize one human-readable summary.

## When to use

- *"how was my week / month"*
- *"give me a status update"*
- *"what should I focus on"*
- *"am I drifting on anything"*

## Approach

Fan out — issue these MCP calls in parallel:

| Question | Tool | Args |
|---|---|---|
| Active todos | `todo_list` | `{ limit: 500 }` |
| Overdue todos | `todo_list` | `{ due_before: <now> }` |
| Active goals | `goals_list` | `{ status: "active" }` |
| Recent moods | `status_logs_list` | `{ log_type: "mood", since: <7d ago> }` |
| Recent focus time | `pomodoros_list` | `{ since: <7d ago>, limit: 200 }` |
| Recent spending | `money_list_transactions` | `{ since: <7d ago>, limit: 500 }` |

Then synthesize: 3-5 sentence narrative, plus a short bulleted "watch outs" list (overdue todos, stale goals, mood streaks, unusual spending).

## Don't

- Don't dump raw rows. The user wants the picture, not the data.
- Don't report totals from data that may be truncated (returned rows == limit); say it may be incomplete.
- Don't invent metrics. If you can't compute it from the tools above, say so.
- Don't write to anything from this skill — delegate writes to the domain-specific skill (`life-todo`, `life-money`, etc.).
