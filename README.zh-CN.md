# integ.life — Claude 技能集

*中文 · [English](README.md)*

> **你的个人操作系统：思考 × 执行**
>
> 记录想法。提取洞察。专注执行。处处同步——离线优先，永远同步。
>
> 🌐 **[integ.life](https://integ.life)** · 🤖 AI 驱动的生产力 · 📱 网页 · macOS · Android · Wear OS

---

这个 repo 提供了一套 **Claude Code skills**，让 AI 助手通过自然对话驱动你在 [integ.life](https://integ.life) 上的数据——记账、待办、笔记、目标、心情、专注时间。

技能与 integ.life 后端里的 MCP（Model Context Protocol）服务配套使用。两者一起，可以把*"午饭花了 35"*、*"这周还有哪些待办"*、*"我最近心情怎么样"*这样的话，翻译成对你自己数据的精准调用。

## 🧠 包含哪些技能

七个技能，每个对应生活里的一个域。每份 `SKILL.md` 告诉 Claude *何时* 触发，以及 *该调用哪个* 工具。

| 技能 | 触发场景 |
|---|---|
| 💰 [`life-money`](skills/life-money/SKILL.md) | "花了多少钱" · "上周交易记录" · "记一笔账" |
| ✅ [`life-todo`](skills/life-todo/SKILL.md) | "加个待办" · "今天要做什么" · "把 X 标记完成" |
| 📝 [`life-idea`](skills/life-idea/SKILL.md) | "记一下这个想法" · "找我之前关于 X 的笔记" |
| 🎯 [`life-goal`](skills/life-goal/SKILL.md) | "我有哪些目标" · "给 X 目标记个 check-in" |
| 🌤️ [`life-mood`](skills/life-mood/SKILL.md) | "我今天有点累" · "我这周心情怎么样" |
| ⏱️ [`life-pomodoro`](skills/life-pomodoro/SKILL.md) | "今天专注了多久" |
| 🔭 [`life-overview`](skills/life-overview/SKILL.md) | "我这周怎么样" · "给我一份状态汇报" |

## 🚀 安装

```bash
git clone git@github.com:integ-life/life.git ~/code/life-skills
mkdir -p ~/.claude/skills
for d in ~/code/life-skills/skills/life-*; do
  ln -sfn "$d" ~/.claude/skills/
done
```

然后在 Claude Code 里配置你的 integ.life MCP 端点（`POST <your-host>/mcp/v1`），bearer token 在 app 的 *设置 → API Tokens* 页面里生成。

注册示例（token 放在环境变量里，切勿提交到仓库）：

```bash
claude mcp add --transport http life-on-golang https://api.integ.life/mcp/v1 --header "Authorization: Bearer $INTEGLIFE_API_TOKEN"
```

## 🌐 相关项目

- 🏠 **[integ.life](https://integ.life)** — 注册账号，网页 / macOS / Android / Wear OS 客户端
- ⌨️ **[life-cli](https://github.com/integ-life/life-cli)** — 同一套后端的命令行客户端

---

<sub>配套 Go、React、Swift、Kotlin 多端客户端使用 · © integ.life</sub>
