# Personal Scrum — Reference

## What Scrum Is

Scrum is an agile framework for delivering work in short, focused cycles called **sprints**. Originally designed for software teams, it adapts well to individual knowledge work and project management. The core insight: breaking work into time-boxed cycles with regular reflection produces better outcomes than an undifferentiated pile of "stuff to do."

---

## Core Concepts

### The Product Backlog
The full list of everything you want or need to do, in rough priority order. Not a to-do list — a living, ranked queue that you pull from at the start of each sprint. In this vault, **the Backlog folder serves as the backlog**. Items tagged `#action` are backlog candidates.

### The Sprint
A fixed time-box — in this system, **one week (Monday → Sunday)** — during which you work only on items you committed to at the start. New work that arrives mid-sprint goes into the Inbox (backlog), not onto the current sprint. Protecting the sprint boundary is how you actually finish things instead of endlessly context-switching.

### Sprint Planning
Happens **Monday morning** (~15 min). Review the Backlog for `#action` items, assess your capacity using the **Capacity block**, and select what you will complete this week. Assign items to either **Active** or **Queue** based on the WIP ceiling. An overloaded sprint is worse than a light one — under-promise, over-deliver.

### The Daily Scrum
A brief daily check-in — in this system, it lives in the **Daily Note**. Three questions:

1. What did I complete yesterday?
2. What will I work on today?
3. Is anything blocking me?

The daily note task list is your answer to question 2. Keep the standup brief — its purpose is to orient the day, not plan it in detail. **Focus Windows** translate the task list into a scheduled reality.

### Sprint Review
Happens **Friday** (~10 min). Look at the sprint backlog: what got done, what didn't. Mark completed items done. Incomplete items return to the Backlog with any relevant context added so you don't lose the thread.

### Sprint Retrospective
Also Friday, right after the review (~10 min). Four questions:

1. What worked well this sprint?
2. What didn't work?
3. What one thing will I change next sprint?
4. How accurate were my estimates? *(transfer data to [[Estimation Log]])*

Keep retrospectives short and action-oriented. If a system change is identified, update the relevant reference file so the improvement sticks.

---

## Vault Mapping

| Scrum Concept | This Vault |
|---|---|
| Product Backlog | `30 - Backlog/` (`#action` tagged items) |
| Sprint | One week, Monday → Sunday |
| Sprint Backlog | Weekly Note — Sprint Backlog section |
| WIP Limit | Weekly Note — Active ceiling (5 items max) |
| Capacity Buffer | Weekly Note — Capacity block (target: ≥ 20%) |
| Daily Scrum | Daily Note — Standup + Tasks sections |
| Focus Windows | Daily Note — Focus Windows block |
| Sprint Review | Weekly Note — Sprint Review section |
| Sprint Retrospective | Weekly Note — Sprint Retrospective section |
| Estimation Tracking | Backlog frontmatter (`estimate:` / `actual:`) + [[Estimation Log]] |
| Shipped Increment | Completed tasks + updated `40 - Projects/` notes |

---

## What Personal Scrum Is Not

- **Not a rigid process.** Adapt it. If weekly sprints feel wrong after a few cycles, change the cadence.
- **Not a commitment to perfection.** Incomplete sprints aren't failures — they're calibration data. The retrospective is where you adjust.
- **Not separate from the second brain.** Tasks often generate knowledge; knowledge often generates tasks. The Daily Note's Captures section is the bridge between the two systems.
- **Not a replacement for prioritization.** Scrum gives you a cadence and a container. You still have to decide what matters most. The sprint backlog should reflect your actual priorities, not just what's loudest.

---

## Slow Productivity Integration

The sprint system manages *what* you commit to and *when* you do it. Slow Productivity (Cal Newport) governs *how many things* you carry at once and *whether you're working at a pace that produces quality output*. The two frameworks are complementary — Scrum provides the cadence; Slow Productivity provides the constraints.

Newport's three principles, translated to this vault:

### 1. Do Fewer Things — WIP Limit

A **WIP (Work-In-Progress) Limit** is a hard ceiling on how many active items you carry simultaneously. In this system, the sprint backlog has two tiers:

- **Active** — items you are doing real work on this week. Ceiling: **5 items across all domains**.
- **Queue** — items committed for the sprint but not yet started. They wait until an Active slot opens.

**The gate rule:** To move a Queue item to Active, something in Active must either complete or be explicitly deferred to a future sprint. This is enforced by convention, not software — but breaking it is a conscious decision, not a passive drift.

Why 5? That's a reasonable default for a week spanning multiple life domains. Adjust it based on your calibration data. If items routinely stall, lower it. The right WIP limit is the one that clears consistently.

### 2. Work at a Natural Pace — Quality Buffer

The **Capacity block** in the weekly note tracks how much of your effective available time is committed. The formula:

```
Buffer % = (Available hours − Committed hours) / Available hours × 100
```

**Available hours** = realistic focused work time this week — not total waking hours. Subtract meetings, hard commitments, and the hours that disappear to friction.

**Committed hours** = sum of all `estimate:` values on Active + Queue backlog items.

**Target:** Buffer ≥ 20%. Below that, the sprint is structurally overloaded. Something will slip — the buffer calculation just makes it visible before it happens instead of after.

If filling the Capacity block reveals overcommitment, cut the Queue — not your sleep and not your standards.

### 3. Obsess Over Quality — Estimation Tracking

Most people chronically underestimate effort. **Estimation bias tracking** makes the pattern visible so it can be corrected.

Every backlog item has two frontmatter fields:

```yaml
estimate: 2h
actual:
```

When an item completes, fill in `actual:` before archiving. At the weekly retro, transfer completed items to the [[Estimation Log]] — a running table of estimated vs. actual hours with a personal correction coefficient.

After 8–10 data points, your coefficient stabilizes. Use it to calibrate future estimates: if your coefficient is 1.4x, a task that feels like 2h should be entered as 3h.

### Focus Windows

Focus Windows are the daily bridge between the WIP list and actual scheduled time. They appear as a table in each daily note:

```
| Time        | Type         | Assigned To        |
|-------------|--------------|---------------------|
| 0600–0800   | Deep Work    | [[Backlog Item]]   |
| 1300–1400   | Admin/Comms  | —                  |
| 1900–2000   | Deep Work    | [[Backlog Item]]   |
```

The rule: **every Active item must be placed in a window before the day starts.** An unplaced item is unscheduled, and an unscheduled item usually doesn't happen.

---

## Related

- [[Daily Note Workflow]] — the full action item pipeline and how it interacts with the Zettelkasten
- [[Estimation Log]] — estimation history and personal correction coefficient
- [[Home]] — vault orientation and second brain structure
- [[Weekly Note]] — weekly sprint template
- [[Daily Note]] — daily note template

---

## ADHD Adaptations

Standard Scrum assumes you can prioritize by importance and execute on demand. ADHD operates differently — the ADHD brain runs on an **interest-based nervous system** (Dr. William Dodson): novelty, challenge, urgency, and passion drive engagement far more than abstract importance rankings. The adaptations below make the system more honest about that.

### Treat the Sprint as a Menu, Not a Contract
The weekly sprint backlog is a curated list of candidates, not a commitment carved in stone. ADHD sprints will be uneven — some weeks you'll blow through everything, others you'll finish two items. That's calibration data, not failure. The retrospective is where you adjust without self-judgment.

### Lead Each Day with Most Important Tasks (MITs)
Before checking messages, before reviewing the full task list — identify your **3 MITs** for the day. These are the non-negotiable outputs. If everything else falls apart, completing these makes the day a success. The daily note template leads with a dedicated MIT section for this reason.

### Use Pomodoro for Execution
ADHD impairs the internal time sense. The Pomodoro Technique substitutes an external one: 25-minute focused bursts (one task only), 5-minute break, repeat. Every 4 pomodoros, take a longer break. Pair this with the daily note task list — pick one task, set a timer, go. Don't rely on sustained motivation to carry you through.

### Keep Capture Friction Near Zero
The Inbox only works if adding to it costs almost nothing. A multi-step capture process kills the habit. Keep a phone shortcut or widget that opens a new Inbox note instantly — the lower the friction, the more reliably new items land in the system instead of being lost.

### Body Doubling
Working alongside someone else — physically or virtually — dramatically improves ADHD focus and initiation. This isn't a vault feature, but worth naming explicitly: if you're struggling to start a sprint or break through an initiation block, a body double (even a virtual co-working session) will often work when planning alone won't.

### Visual Progress with Kanban
The sprint backlog in a Weekly Note is text-based. A Kanban board (To Do / Doing / Done) gives the same information in a drag-and-drop visual format that ADHD brains process more naturally. The Obsidian Kanban community plugin can turn any note into a board — a good addition once the core workflow is stable.

### WIP Limits and ADHD
The WIP ceiling isn't a punishment — it's a forcing function for the ADHD tendency to start many things and complete few. When the Active list is full, the system makes the cost of a new shiny thing explicit: something has to come off first. That's a much more honest interaction with how ADHD actually works than an infinite to-do list where everything feels equally possible.

### Forgive the Broken Streaks
ADHD makes consistency harder than neurotypical productivity systems assume. If you miss a daily note, skip a sprint planning session, or let the Inbox pile up — that's the condition, not a character flaw. The retrospective exists to reset without shame. A system that only works when everything is already going well isn't a real system.
