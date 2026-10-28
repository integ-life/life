# integ.life — Claude Skills

*[中文](README.zh-CN.md) · English*

> **Your Personal OS for Thinking & Doing**
>
> Capture thoughts. Extract insights. Execute with focus. Sync everywhere — offline-first, always in sync.
>
> 🌐 **[integ.life](https://integ.life)** · 🤖 AI-powered productivity · 📱 Web · macOS · Android · Wear OS

---

This repo ships the **Claude Code skills** that let an AI agent drive your [integ.life](https://integ.life) data — money, todos, notes, goals, mood, focus time — through natural conversation.

The skills live alongside an MCP (Model Context Protocol) server inside integ.life's backend. Together they turn *"I spent 35 on lunch"*, *"what's on my plate this week"*, or *"how have I been feeling"* into the right call against your own data.

## 🧠 What's inside

Seven skills, one per life domain. Each `SKILL.md` tells Claude *when* to trigger and *which* tool to call.

| Skill | Trigger |
|---|---|
| 💰 [`life-money`](skills/life-money/SKILL.md) | "I spent X" · "how much did I spend on Y" · "show last week's transactions" |
| ✅ [`life-todo`](skills/life-todo/SKILL.md) | "add a todo" · "what's due today" · "mark X done" |
| 📝 [`life-idea`](skills/life-idea/SKILL.md) | "jot this down" · "find my notes on Y" |
| 🎯 [`life-goal`](skills/life-goal/SKILL.md) | "what are my active goals" · "log a check-in on Y" |
| 🌤️ [`life-mood`](skills/life-mood/SKILL.md) | "I'm feeling tired" · "how have I been this week" |
| ⏱️ [`life-pomodoro`](skills/life-pomodoro/SKILL.md) | "how much focused time did I get today" |
| 🔭 [`life-overview`](skills/life-overview/SKILL.md) | "how was my week" · "give me a status update" |

## 🚀 Install

```bash
git clone git@github.com:integ-life/life.git ~/code/life-skills
mkdir -p ~/.claude/skills
for d in ~/code/life-skills/skills/life-*; do
  ln -sfn "$d" ~/.claude/skills/
done
```

Then point Claude Code at your integ.life MCP endpoint (`POST <your-host>/mcp/v1`) with a bearer token created from the app's *Settings → API Tokens* screen.

Example registration (keep the token in an environment variable, never commit it):

```bash
claude mcp add --transport http life-on-golang https://api.integ.life/mcp/v1 --header "Authorization: Bearer $INTEGLIFE_API_TOKEN"
```

## 🌐 Related

- 🏠 **[integ.life](https://integ.life)** — sign up, web/macOS/Android/Wear OS apps
- ⌨️ **[life-cli](https://github.com/integ-life/life-cli)** — command-line client for the same backend

---

<sub>Built to pair with Go, React, Swift, and Kotlin clients · © integ.life</sub>
