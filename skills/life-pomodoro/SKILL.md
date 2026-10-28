---
name: life-pomodoro
description: Inspect the user's pomodoro / focus sessions in life-on-golang. Trigger when they ask about focused time, recent pomodoros, or productivity by todo.
---

# life-pomodoro

Pomodoros sit on top of `events` (which carry the time range). The phone, Mac, Windows, and Wear OS apps all create them; this MCP only reads them — starting/stopping a pomodoro is a phone/watch action.

## When to use

- *"how much focused time did I get today / this week"*
- *"show recent pomodoros"*
- *"what was I working on in my last sessions"*

## Tools (MCP `life-on-golang`)

- `pomodoros_list` — date range + optional todo filter, `limit` (default 50, max 200); returns aligned `pomodoros` and `events` arrays

## Patterns

**Total focus time.** Sum `event.end_at - event.start_at` for the returned events. There's no pre-aggregated endpoint yet. Always pass `since`/`until` and `limit: 200`; if exactly 200 rows come back the result may be truncated, so split the range and query again (or tell the user the total may be incomplete) instead of reporting a total.

**Per-todo.** Pass `todo_uuid` to scope to a single task. Useful for *"how long did the X task actually take"*.

**Read-only for now.** If the user wants to start a pomodoro, tell them to do it from the watch or phone app — there's no `pomodoros_start` tool yet.
