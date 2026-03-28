# Obsidian Personal Scrum Vault

A battle-tested Obsidian vault template combining **Personal Scrum** for task management and **Zettelkasten** for knowledge management — adapted for ADHD, high-tempo work environments, and anyone who needs a system that holds up under real-world pressure.

---

## What This Is

Most productivity systems fail because they treat tasks and knowledge as separate problems. This vault treats them as two sides of the same workflow. Every note you capture either becomes something you *do* (a task, tracked through a weekly sprint cycle) or something you *think* (an idea, processed into permanent knowledge). The same Inbox handles both.

The sprint system is adapted from Scrum — the software development framework — applied to individual knowledge work. The knowledge system is a Zettelkasten — a network of atomic, interlinked permanent notes that compounds in value over time.

Both run in plain markdown. No plugins required to start.

---

## Who This Is For

- Knowledge workers who want a structured weekly cadence without corporate overhead
- ADHD brains that need external scaffolding to stay oriented
- Anyone frustrated that their notes app and their to-do app don't talk to each other
- People who want a system they can actually explain to someone else

---

## What's Included

```
obsidian-personal-scrum-vault/
│
├── Home.md                    Vault orientation — start here
│
├── 00 - Inbox/                Raw captures (process within 48h)
│   └── _README.md             Inbox rules and processing guide
│
├── 10 - Daily/                Daily notes (YYYY-MM-DD.md)
├── 20 - Weeks/                Weekly sprint notes (YYYY-WW.md)
├── 30 - Backlog/              Tagged #action items waiting for a sprint
│
├── 40 - Projects/             Project notes (active and completed)
├── 50 - Notes/                Permanent/atomic Zettelkasten notes
├── 60 - MOCs/                 Maps of Content — navigation layer
│
├── 70 - Sources/              Literature notes (one per source)
│   ├── Literature/
│   ├── Philosophy/
│   └── Technology/
│
├── 80 - Reference/
│   ├── Daily Note Workflow.md Full pipeline documentation
│   └── Personal Scrum.md      Sprint methodology + ADHD adaptations
│
├── 90 - Templates/
│   ├── Daily Note.md          Daily standup + task template
│   └── Weekly Note.md         Sprint planning + retro template
│
├── 95 - Journal/              Freeform journal entries (YYYY-MM-DD HHMM - setting.md)
└── 99 - Archive/              Completed backlog items (read-only)
```

---

## How to Get Started

**1. Open in Obsidian**

Download [Obsidian](https://obsidian.md) (free). Open this folder as a vault: *Open folder as vault* → select this directory.

**2. Read `Home.md`**

Vault orientation is in `Home.md`. It explains the structure, the two workflows, and how everything connects.

**3. Customize the Work sections**

The Daily Note and Weekly Note templates include four generic `Priority Area` sub-headers. Rename these to match your actual work domains before you start using them. See `80 - Reference/Daily Note Workflow.md` for examples.

**4. Start Monday**

Sprint planning takes 15 minutes on Monday morning. Create a Weekly Note from the template, pull your most important items into the Sprint Backlog, and start the week with a clear list.

**5. Use Daily Notes as your standup**

Each morning, copy the Daily Note template, fill in the standup section, and pull today's tasks from the sprint backlog. At the end of the day, process your Captures into the Inbox.

---

## The Two Systems

### Personal Scrum (Task Management)

Weekly sprints with daily standups. Every actionable item flows:

```
Inbox (#action) → Backlog → Weekly Sprint → Daily Note → Archive
```

- **Monday:** Sprint Planning — pull from Backlog into Weekly Note
- **Tue–Thu:** Daily Notes — standup + working task list
- **Friday:** Review + Retrospective — close sprint, archive completed work

### Zettelkasten (Second Brain)

A network of atomic permanent notes that compounds over time. Every idea flows:

```
Inbox (#knowledge) → Sources/ → Notes/ → MOCs/
```

- **Sources/** — one note per book, article, or video you've processed
- **Notes/** — atomic permanent notes, one idea each, linked to sources and related notes
- **MOCs/** — navigation notes that organize access to topics

Both systems share the same Inbox. Tag at capture (`#action` or `#knowledge`), then route.

---

## ADHD Adaptations

This system was designed with ADHD in mind. Key design decisions:

- **Daily note leads with Today's 3** — three non-negotiables before anything else
- **Sprint backlog is a menu, not a contract** — uneven weeks are calibration data, not failure
- **Inbox friction is near zero** — one note, one tag, done
- **Pomodoro pairs naturally with daily tasks** — pick one item, 25 minutes, go
- **Retrospective resets without shame** — the system expects broken streaks

Full ADHD adaptations documented in `80 - Reference/Personal Scrum.md`.

---

## No Plugins Required

This vault works with zero community plugins. The core system is plain markdown with YAML frontmatter tags.

Optional plugins that pair well with this system:
- **Kanban** — visual sprint board view
- **Calendar** — date-based daily note navigation
- **Templater** — faster template insertion than core Templates plugin

---

## AI Enhancement (Optional)

This vault includes `CLAUDE.md` and `GEMINI.md` context files for [Claude Code](https://claude.ai/code) and [Gemini CLI](https://github.com/google-gemini/gemini-cli) users who want AI-assisted workflow automation.

**What it enables:**
- Sprint planning from your terminal — the AI reads your backlog, helps you prioritize, and builds your weekly note
- Daily standup automation — creates your daily note, sets Today's 3, pulls tasks from the sprint
- End-of-day closeout — processes your Captures into Inbox, updates backlog status
- Natural language vault queries — "what's in my backlog?" "summarize this week's captures"

**How it works:**

1. `CLAUDE.md` (Claude Code) or `GEMINI.md` (Gemini CLI) in the vault root gives the AI context about your system, role, and priorities
2. The Obsidian MCP server connects the AI CLI to your live vault via the Obsidian REST API
3. You customize the context file with your actual details — the AI reads it at the start of every session

**Setup:** see `80 - Reference/Claude Code Setup.md` for full instructions. Takes about 20 minutes and works on Mac, Linux, and Windows (WSL).

The vault works completely without this. It's a layer for people who want their terminal to handle the sprint admin.

---

## License

MIT — use it, adapt it, build on it.

---

## Support

If this system is useful to you, consider supporting further development:

[GitHub Sponsors](https://github.com/sponsors/Awzy11)
