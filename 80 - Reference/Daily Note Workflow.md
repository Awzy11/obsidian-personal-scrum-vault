# Daily Note Workflow

This document formalizes how actionable work moves through the vault — from initial capture to completion — and how that flow interacts with the Zettelkasten second brain.

---

## The Two Workflows

This vault runs two parallel information flows that share a single entry point: the **Inbox**.

```
                    INBOX (front door)
                          |
           +--------------+--------------+
           |                             |
        #action                     #knowledge
           |                             |
   Sprint Backlog               Zettelkasten Pipeline
   (Weekly Note)            Sources/ → Notes/ → MOCs/
           |
      Daily Note
  (tasks + standup)
           |
   End-of-Day Captures ──────────────────> back to Inbox
```

**`#action` items** are tasks — things that require you to *do* something. They flow into the sprint system and surface in daily notes.

**`#knowledge` items** are ideas, observations, quotes, and questions — things you want to *think* about. They flow into the Zettelkasten pipeline.

Some items are both. A research task (`#action`) may produce a permanent note (`#knowledge`). Let them split when they need to — tag with both.

---

## Tagging at Capture

When you drop something in the Inbox, add YAML frontmatter at the very top of the note:

```yaml
---
tags: [action]
---
```

or

```yaml
---
tags: [knowledge]
---
```

For items that are both:

```yaml
---
tags: [action, knowledge]
---
```

YAML frontmatter makes items filterable from Obsidian's tag pane and searchable across the vault. Add the tag at capture — don't leave it for later.

---

## The Four-Stage Action Pipeline

```
00 - Inbox/ (raw captures — process within 48h)
     |
     | triage: add frontmatter tag + move
     |
     +--> 30 - Backlog/  (#action items — triaged, waiting for a sprint)
     |
     +--> Zettelkasten pipeline  (#knowledge items — Sources/ → Notes/ → MOCs/)

30 - Backlog/ --> 20 - Weeks/ (sprint backlog — committed this week)
             --> 10 - Daily/ (doing today)
             --> 99 - Archive/ (completed)
```

**Inbox** is strictly a raw capture zone. Once an item is tagged `#action`, it moves to `30 - Backlog/`. The 48-hour processing rule applies only to Inbox — Backlog items persist until worked or deprioritized.

---

## The Weekly Cycle

### Monday — Sprint Planning (~20 min)

1. Open `30 - Backlog/`. Scan for items tagged `#action`.
2. Create this week's Weekly Note: copy `90 - Templates/Weekly Note.md`, save as `20 - Weeks/YYYY-WW.md`.
3. Pull actionable items into the Sprint Backlog, ranked by priority.
4. **Calculate the Capacity block:** estimate your effective available hours this week. Sum the `estimate:` fields on your planned items. Calculate Buffer % = (Available − Committed) / Available × 100. If buffer is below 20%, cut items before the week starts.
5. **Set Active / Queue split:** designate up to 5 items as Active (working now). Everything else goes to Queue (committed but waiting for a slot).
6. Link to source backlog notes rather than duplicating content — one click gets you full context.

### Tuesday–Thursday — Daily Notes

Each day, copy `90 - Templates/Daily Note.md` and save as `10 - Daily/YYYY-MM-DD.md`.

- Fill in the **Standup** section (yesterday's actuals / today's commitments / blockers).
- Populate **Focus Windows** — assign each Active item to a specific time block. Unplaced = unscheduled.
- Pull today's specific tasks from the Sprint Backlog into the **Tasks** section.
- Work. Check off tasks as done.
- At end of day, dump any fleeting thoughts into the **Captures** section.
- Before closing: note est vs actual for any completed items. Process Captures into Inbox.

### Friday — Sprint Review + Retrospective (~20 min)

1. Open this week's Weekly Note.
2. **Review:** mark completed items done (with est vs actual noted). For anything incomplete, move it back to Backlog with a note on why.
3. **Retrospective:** answer the four questions honestly. Update the [[Estimation Log]] with completed items.
4. Process any Captures from the week's daily notes not yet moved to Inbox.

---

## The Daily Note

The daily note is the tactical layer — it answers "what am I doing today?" It has five parts:

**Today's 3** — Three non-negotiable outputs for the day. Fill these in before anything else.

**Standup** — Three questions, answered briefly before you start work:
- *Yesterday:* what you actually completed (not what you planned — be honest)
- *Today:* what you're committing to for this day
- *Blockers:* anything actively preventing forward progress

**Focus Windows** — A time-block table mapping Active WIP items to specific windows. Every Active item needs a window before the day starts. This is the bridge between intention and schedule.

**Tasks** — The working task list for the day, organized by area (Work / Home / Personal / Projects). Customize the Work sub-headers to match your actual priority areas. Check off as you go.

**Captures** — A scratch pad at the bottom of the note. Anything that comes up during the day that belongs in the vault goes here first. Process into Inbox before end of day.

**End of Day** — A brief close-out: what actually got done (with est vs actual for completed backlog items), what moves back to backlog, any notes worth keeping.

---

## Backlog Item Convention

Every `30 - Backlog/` file should include `estimate:` and `actual:` in its frontmatter:

```yaml
---
tags: [action]
created: YYYY-MM-DD
estimate: 2h
actual:
---
```

Fill in `actual:` when the item is completed, before archiving. These fields feed the [[Estimation Log]] and make the Capacity block meaningful.

---

## How the Two Workflows Interact

**Daily work → second brain**
The Captures section of every daily note is a Zettelkasten feeder. Observations made while doing task work often contain ideas worth keeping permanently. Process them into the Inbox as `#knowledge` items, then through the Zettelkasten pipeline.

**Second brain → daily work**
While processing a source or writing a permanent note, you may identify something actionable. Drop it in the Inbox tagged `#action`. It enters the sprint system at the next planning session.

**Projects sit at the intersection**
Project work generates both tasks and knowledge. A single piece of project work might produce a task completion *and* an update to a project note *and* a permanent note in `50 - Notes/`. All three are valid outputs of the same work.

---

## File Naming Conventions

| File type | Location | Format |
|---|---|---|
| Daily notes | `10 - Daily/` | `YYYY-MM-DD.md` |
| Weekly notes | `20 - Weeks/` | `YYYY-WW.md` (e.g. `2026-W09.md`) |
| Backlog items | `30 - Backlog/` | Descriptive title |
| Daily note template | `90 - Templates/` | `Daily Note.md` |
| Weekly note template | `90 - Templates/` | `Weekly Note.md` |

---

## Customizing the Work Section

The Daily Note and Weekly Note templates include four `Priority Area` sub-headers under **Work**. Rename these to match your actual work domains before you start using the vault. Examples:

- A manager might use: `Team Leadership` / `Stakeholder Comms` / `Process Improvement` / `Admin`
- A developer might use: `Deep Work` / `Code Review` / `Meetings` / `Learning`
- A freelancer might use: `Client A` / `Client B` / `Business Dev` / `Admin`

The number of areas isn't fixed — add or remove headers to fit your reality.

---

## Related

- [[Personal Scrum]] — the methodology behind the sprint system, including full Slow Productivity doctrine
- [[Estimation Log]] — estimation history and correction coefficient
- [[Home]] — vault orientation and second brain structure
- [[Daily Note]] — daily note template
- [[Weekly Note]] — weekly sprint template
