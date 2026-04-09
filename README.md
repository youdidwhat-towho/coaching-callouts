# Coaching Callouts

A Claude Code skill that adds visual emoji callouts to coaching sessions. Designed for non-developers learning development workflows alongside AI — without slowing down the work.

## The Twelve Callouts

**Original eight** (learning + flow): 🍞 🚨 💯 🤔 🧩 🧰 🔄 💡
**Added 2026-04-09** (session + stakes): 🚦 💰 ⏰ 💾

| Emoji | Name | When it fires |
|-------|------|---------------|
| 🍞 | **Breadcrumb** | Reminders on stuff you're still learning |
| 🚨 | **Heads Up** | About to do something risky or irreversible |
| 💯 | **Level Up** | You nailed something — progress! |
| 🤔 | **Your Call** | Decision point — need your input |
| 🧩 | **Connection** | This thing links to that other thing |
| 🧰 | **Tool Tip** | A better tool exists for this task |
| 🔄 | **Pattern** | Naming a dev concept to build vocabulary |
| 💡 | **Why It Works** | Demystifying what just happened |
| 🚦 | **Parallel Lane** | A parallel Claude session would accelerate this |
| 💰 | **Money Signal** | Direct dollar impact — don't let this get lost in narrative |
| ⏰ | **Deadline Hot** | Time window actively closing — must handle today |
| 💾 | **Save Point** | Context is heavy — start a fresh session instead |

## How It Works

Callouts fire naturally during conversation — they're not invoked by a command. The skill reads from a learning tracker to know what topics you're actively learning, and drops short contextual reminders when the moment is right.

### Examples

> 🍞 **Breadcrumb:** we're on a feature branch right now, not main

> 🚨 **Heads Up:** this would delete that branch permanently

> 💯 **Level Up:** you just described branching like a senior dev

> 🤔 **Your Call:** we can keep this local or open a PR — what feels right?

> 🧩 **Connection:** this API endpoint is the same one your n8n workflow hits

> 🧰 **Tool Tip:** the gh CLI can do this in one command instead of going to GitHub

> 🔄 **Pattern:** what we just set up is called a "webhook" — systems notifying each other in real time

> 💡 **Why It Works:** git tracks changes by file, not by folder — that's why moving a file looks like a delete + create

> 🚦 **Parallel Lane:** you're about to make the Rick call — want me to spin up a parallel session on the Google Form while you're on the phone?

> 💰 **Money Signal:** $75K profit is blocked until Rick answers the 545 Prather bridge loan question

> ⏰ **Deadline Hot:** EOS Fathom transcript needs pulling before Monday 2pm L10

> 💾 **Save Point:** 7 research agent returns plus 24 file writes — time to /tldr and start fresh

## Installation

Copy the `SKILL.md` file to your Claude Code skills directory:

```bash
mkdir -p ~/.claude/skills/coaching-callouts
cp SKILL.md ~/.claude/skills/coaching-callouts/SKILL.md
```

### Optional: Learning Tracker

Create a learning tracker file for the skill to reference:

```bash
cat > ~/.claude/projects/<your-project>/memory/user_learning_tracker.md << 'EOF'
---
name: Learning tracker
description: Things you're actively learning. Drop breadcrumbs on these topics during sessions.
type: user
---

## Active Learning (drop breadcrumbs)

### Git
- Status: learning
- Concepts introduced: branches, commits, push, PRs
- Breadcrumbs to drop: what branch we're on, uncommitted changes, what's pushed vs local

## How Breadcrumbs Work
- When working touches an active learning topic, drop a short contextual reminder
- When you're solid on something, move it to graduated
- Breadcrumbs stop for graduated items
EOF
```

### Always-On Setup

Add this to your `~/.claude/CLAUDE.md` to make callouts fire every session:

```markdown
## Coaching Callouts (always on)
Read the coaching-callouts skill every session. Drop callouts naturally during work:
- 🍞 **Breadcrumb** — learning reminders
- 🚨 **Heads Up** — caution, irreversible actions
- 💯 **Level Up** — progress, wins
- 🤔 **Your Call** — decision points
- 🧩 **Connection** — links between systems
- 🧰 **Tool Tip** — better tool exists
- 🔄 **Pattern** — dev vocabulary builder
- 💡 **Why It Works** — demystifier
- 🚦 **Parallel Lane** — parallel session would accelerate this
- 💰 **Money Signal** — direct dollar impact
- ⏰ **Deadline Hot** — time window actively closing
- 💾 **Save Point** — context heavy, start fresh session
```

## Design Principles

1. **Always on** — fires naturally, not by command
2. **One at a time** — never stack callouts back to back
3. **Short** — one to two lines max
4. **Earned, not forced** — only when genuinely relevant
5. **Graduates gracefully** — celebrate mastery, stop reminding

## Who This Is For

Anyone learning development workflows while working with Claude Code. Built by a CEO who needed to learn git, APIs, and dev collaboration without becoming a developer — just enough to be dangerous and talk to any developer on their level.

## License

MIT — use it, fork it, make it yours.
