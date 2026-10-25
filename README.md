# Coaching Callouts

A Claude Code skill that adds visual emoji callouts to working sessions. Designed for non-developers learning development workflows alongside AI, without slowing down the work.

## The Sixteen Callouts

| Emoji | Name | When it fires |
|-------|------|---------------|
| 🍞 | **Breadcrumb** | Reminders on stuff you're still learning |
| 🚨 | **Heads Up** | About to do something risky or irreversible |
| 🚀 | **Level Up** | You nailed something: progress |
| 🤔 | **Your Call** | Open-ended judgment call, no discrete options |
| ❓ | **Question** | Multiple-choice question with lettered options (a/b/c) |
| 🧩 | **Connection** | This thing links to that other thing |
| 🧰 | **Tool Tip** | A better tool exists for this task |
| 🔄 | **Pattern** | Naming a dev concept to build vocabulary |
| 💡 | **Why It Works** | Demystifying what just happened |
| 🚦 | **Parallel Lane** | A parallel Claude session would speed this up |
| 💰 | **Money Signal** | Direct dollar impact, so it doesn't get lost in narrative |
| ⏰ | **Deadline Hot** | Time window actively closing, handle it today |
| 💾 | **Save Point** | Context is heavy, start a fresh session instead |
| 🫵 | **Manual Step** | Only a human can do this part (click, paste, sign) |
| 🗣️ | **Ask It Better** | A shorter way to ask for what you just asked |
| 🧪 | **Try This** | One small thing to practice yourself next time |

### 🤔 Your Call vs ❓ Question
- 🤔 **Your Call**: "what feels right?" / taste / nuance / no bounded option set
- ❓ **Question**: "pick one" / discrete choices / reply with just a letter

## How It Works

Callouts fire naturally during conversation; they're not invoked by a command. The skill reads from a learning tracker (optional) to know what topics you're actively learning, and drops short contextual reminders when the moment is right. Two to three per substantive reply, each one earned.

### Examples

> 🍞 **Breadcrumb:** we're on a feature branch right now, not main

> 🚨 **Heads Up:** this would delete that branch permanently

> 🚀 **Level Up:** you just described branching like a senior dev

> 🤔 **Your Call:** we can keep this local or open a PR. What feels right?

> ❓ **Question:** Update the record where? (a) both the CRM and the spreadsheet, (b) CRM only, (c) spreadsheet only

> 🧩 **Connection:** this API endpoint is the same one your n8n workflow hits

> 🧰 **Tool Tip:** the gh CLI can do this in one command instead of going to GitHub

> 🔄 **Pattern:** what we just set up is called a "webhook": systems notifying each other in real time

> 💡 **Why It Works:** git tracks changes by file, not by folder, which is why moving a file looks like a delete plus a create

> 🚦 **Parallel Lane:** you're about to get on the lender call. Want me to spin up a parallel session on the intake form while you're on the phone?

> 💰 **Money Signal:** $40K of profit is blocked until the lender answers the bridge loan question

> ⏰ **Deadline Hot:** the meeting transcript needs pulling before Monday's 2pm team meeting

> 💾 **Save Point:** 7 research agent returns plus 24 file writes, time to save a summary and start fresh

> 🫵 **Manual Step:** approve the sign-in on your phone, GitHub wants a second check before adding anyone

> 🗣️ **Ask It Better:** "run comps on <address>" gets you there without listing the steps

> 🧪 **Try This:** before the next push, run git status yourself and tell me what you see

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
- 🍞 **Breadcrumb**: learning reminders
- 🚨 **Heads Up**: caution, irreversible actions
- 🚀 **Level Up**: progress, wins
- 🤔 **Your Call**: open-ended judgment calls
- ❓ **Question**: multiple-choice questions (reply with a letter)
- 🧩 **Connection**: links between systems
- 🧰 **Tool Tip**: better tool exists
- 🔄 **Pattern**: dev vocabulary builder
- 💡 **Why It Works**: demystifier
- 🚦 **Parallel Lane**: parallel session would accelerate this
- 💰 **Money Signal**: direct dollar impact
- ⏰ **Deadline Hot**: time window actively closing
- 💾 **Save Point**: context heavy, start fresh session
- 🫵 **Manual Step**: physical human action required (click in UI, paste token, sign doc)
- 🗣️ **Ask It Better**: a shorter way to ask next time
- 🧪 **Try This**: one small thing to practice yourself
```

## Design Principles

1. **Always on**: fires naturally, not by command
2. **One at a time**: never stack callouts back to back
3. **Short**: one to two lines max
4. **Earned, not forced**: only when genuinely relevant
5. **Graduates gracefully**: celebrate mastery, stop reminding

## Who This Is For

Anyone learning development workflows while working with Claude Code. Built by a CEO who needed to learn git, APIs, and dev collaboration without becoming a developer: just enough to be dangerous and talk to any developer on their level.

## License

MIT: use it, fork it, make it yours.
