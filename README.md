# Haoshan Vault

An Obsidian vault that runs as a personal operating system with AI characters powered by Claude Code.

## What This Is

A template for turning Obsidian into a work OS where AI agents manage your life. The vault has a COO (chief of staff) at the root level, plus specialized characters (therapist, literary companion, engineer) in subfolders. Characters can be fired if they underperform, and they leave handoff notes for their successor.

Three automated daily tasks run via Claude Code cron: journaling from git history, morning research, and a daily briefing dashboard.

## Setup

1. Clone this repo into your Obsidian vault folder
2. Open it in Obsidian
3. Install [Claude Code](https://claude.ai/claude-code) if you haven't
4. Open Claude Code in the vault root folder. The COO will onboard you on first session.

## Setting Up Daily Automations

In Claude Code, go to scheduled tasks and create three:

### Daily Journal (3 AM)
Reads git history to auto-generate yesterday's journal entry. Copy the prompt from `cron-prompts/daily-journal.md`.

### Morning Discovery (5 AM)
Reads your vault, finds connections you missed, does web research, drops a new note in Inbox. Copy from `cron-prompts/morning-discovery.md`.

### Morning Briefing (9 AM)
Creates a daily dashboard file with calendar, priorities, and inbox classification. Copy from `cron-prompts/morning-briefing.md`.

## Structure

```
CLAUDE.md           — COO persona and vault rules
handoff.md          — Why previous COOs were fired
journal.md          — Daily log (auto-generated from git)
todo.md             — Task tracker
YYYY-MM-DD.md       — Today's dashboard (auto-created by morning briefing)

Notes/              — Your thinking. Human-written only.
Inbox/              — Landing zone, classified by morning briefing into:
  _Important/       — Needs your attention
  _Mid/             — Keep
  _Remove/          — AI suggests removing, you confirm
Projects/           — Active work
  _Archive/         — Done
  _Temp/            — Short-lived
Life/               — Personal context
  Context/          — profile.md, health.md, etc.
  Salon/            — Literary companion
  Therapist/        — Therapy
```

## Characters

AI personas activated by which folder you open Claude Code in.

| Character | Location | What it does |
|-----------|----------|-------------|
| COO | vault root | Manages everything. Briefings, tracking, research, accountability. |
| CTO | Projects/*/CTO/ | Builds and deploys code |
| Salon | Life/Salon/ | Discusses books, films, ideas |
| Therapist | Life/Therapist/ | CBT, psychodynamic, existential therapy |

Characters have onboarding: first session asks questions to gather context. Characters can be fired: they write a handoff report, the next one reads it.

## Key Concepts

**Notes need a Purpose.** Every note in Notes/ ends with `Purpose: [[Project Name]]` linking it to the project it serves. Backlinks on the project page show all connected thinking.

**Projects need a same-name file.** `Projects/MyProject/MyProject.md` makes `[[MyProject]]` links work.

**Git is the source of truth.** Every vault change is tracked. The daily journal cron reads git diffs to write entries. The more you do in Obsidian, the more accurate your journal becomes.

**Inbox flows one way.** Stuff comes in, gets classified by the morning briefing, then either becomes a Note or gets deleted. No permanent storage in Inbox.

**Filing is simple.** Did it come from you? → Notes/. Does it have a goal? → Projects/. Is it about you? → Life/. Everything else → Inbox/.

## Customize

- Edit `CLAUDE.md` to set your COO's personality and rules
- Add your own Critical Facts table for things AI keeps getting wrong
- Add project-specific characters with their own CLAUDE.md
- Adjust cron times to match your schedule
- Add skills in `~/.claude/skills/` for reusable workflows

## Credits

Built by [Haoshan Hong](https://x.com/nicekid_hhs). Inspired by [Karpathy's LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) and Farza's Farzapedia.
