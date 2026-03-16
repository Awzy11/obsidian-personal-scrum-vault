# Home

Welcome to your vault. Start here.

---

## Quick Navigation

| | |
| --- | --- |
| **Today** | `10 - Daily/` → today's note |
| **This Week** | `20 - Weeks/` → current sprint note |
| **Backlog** | `30 - Backlog/` → all active action items |
| **Inbox** | `00 - Inbox/` → unprocessed captures (≤48h) |
| **Projects** | `40 - Projects/` → active and completed projects |

---

## Second Brain

### Maps of Content

*Add your MOC links here as you build them. Each MOC is a navigation note that organizes access to a topic without containing content itself.*

| MOC | What it covers |
|---|---|
| — | — |

### Permanent Notes

*Your permanent notes will appear here, organized by cluster or topic. Each note contains one atomic idea, written assertively.*

---

## Active Work

### Projects
`40 - Projects/` → your active project notes

### This Sprint
`20 - Weeks/` → current weekly note → sprint backlog and goal

### Reference

| Doc | Purpose |
|---|---|
| [[Daily Note Workflow]] | Full action item pipeline — 4-stage flow, weekly cycle |
| [[Personal Scrum]] | Sprint methodology + ADHD adaptations |

---

## How This Vault Works

### The Three Note Types

**1. Fleeting Notes** → `00 - Inbox/`
Raw, unprocessed captures. Speed matters here; quality does not. Process within 48 hours: promote each item to a permanent note, absorb it into an existing one, or discard it. An empty Inbox means the system is working.

**2. Literature Notes** → `70 - Sources/`
Processed notes *about* a specific source — a book, video, paper, or article — distilled into its key ideas in structured form.

**3. Permanent Notes** → `50 - Notes/`
The heart of the Zettelkasten. Each note contains **one atomic idea**, written assertively as if explaining it to a thoughtful stranger — not "Author says X" but "X is true, and here is why." Every permanent note links to its sources and to related notes.

### MOCs — the Navigation Layer
A **Map of Content** organizes *access* to knowledge without containing knowledge itself. MOCs link to the permanent notes, sources, and sub-MOCs belonging to a topic. They sit on top of the Zettelkasten web and live in `60 - MOCs/`.

### Vault Structure

```
Home.md  ← you are here
│
├── 00 - Inbox/         ← fleeting notes (process within 48h; #action or #knowledge)
│
├── 10 - Daily/         ← daily notes (YYYY-MM-DD.md) — standup + working task list
├── 20 - Weeks/         ← weekly sprint notes (YYYY-WW.md) — sprint backlog + retro
├── 30 - Backlog/       ← active #action items waiting for a sprint
│
├── 40 - Projects/      ← active and completed project notes
│
├── 50 - Notes/         ← permanent/atomic Zettelkasten notes (one idea per file)
│
├── 60 - MOCs/          ← navigation layer (not storage — sits across all topics)
│
├── 70 - Sources/       ← literature notes (one per source)
│   ├── Literature/
│   ├── Philosophy/
│   └── Technology/
│
├── 80 - Reference/     ← vault workflow and reference docs
├── 90 - Templates/     ← Daily Note, Weekly Note templates
└── 99 - Archive/       ← completed backlog items (read-only reference)
```

### The Task & Sprint System

**Triage at capture:** every Inbox item gets a frontmatter tag — `#action` for tasks, `#knowledge` for ideas. Items can be both.

```
00 - Inbox/ (raw captures, ≤48h)
  │
  ├── #action  →  30 - Backlog/  →  20 - Weeks/ (sprint)  →  10 - Daily/
  │                                                                │
  │                                                   completed → 99 - Archive/
  │
  └── #knowledge  →  70 - Sources/  →  50 - Notes/  →  60 - MOCs/
```

**The weekly cycle:**
- **Monday** — Sprint Planning: pull from Backlog into Weekly Note
- **Tue–Thu** — Daily Notes: standup artifact + working task list
- **Friday** — Sprint Review + Retrospective: close sprint, archive completed items
