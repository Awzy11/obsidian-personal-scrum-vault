# CLAUDE.md

This file provides context to Claude Code (claude.ai/code) when working with this vault. It enables AI-assisted workflow automation — sprint planning, daily standups, end-of-day closeouts, and knowledge capture — directly from your terminal.

**Before using this file:** replace every `YOUR_*` placeholder with your own information. The more accurately this file reflects your actual context, the better the AI assistance will be.

---

## Vault Access

This vault is accessed via the Obsidian MCP server. See `80 - Reference/Claude Code Setup.md` for full setup instructions.

| Tool | Purpose |
| --- | --- |
| `mcp__obsidian__obsidian_list_files_in_vault` | List vault root |
| `mcp__obsidian__obsidian_list_files_in_dir` | List a directory (no trailing slash) |
| `mcp__obsidian__obsidian_get_file_contents` | Read a single file |
| `mcp__obsidian__obsidian_batch_get_file_contents` | Read multiple files at once |
| `mcp__obsidian__obsidian_simple_search` | Full-text search across all vault files |
| `mcp__obsidian__obsidian_complex_search` | JsonLogic query search (tags, paths, patterns) |
| `mcp__obsidian__obsidian_append_content` | Create or append to a file |
| `mcp__obsidian__obsidian_patch_content` | Insert/replace within a file |
| `mcp__obsidian__obsidian_delete_file` | Delete a file (requires `confirm: true`) |
| `mcp__obsidian__obsidian_get_periodic_note` | Get current daily/weekly/monthly/etc. note |
| `mcp__obsidian__obsidian_get_recent_periodic_notes` | Get most recent periodic notes by period type |
| `mcp__obsidian__obsidian_get_recent_changes` | Get recently modified files in the vault |

**Vault server:** `YOUR_OBSIDIAN_HOST`, port `27123`. Use Tailscale IP if connecting remotely.

**MCP config** — required at `~/.docker/mcp/config.yaml` on whichever machine is running Claude Code:

```yaml
tools:
  obsidian:
    env:
      OBSIDIAN_API_KEY: "YOUR_OBSIDIAN_API_KEY"
      OBSIDIAN_HOST: "YOUR_OBSIDIAN_HOST"
      OBSIDIAN_PORT: "27123"
```

If this file doesn't exist on the current machine, create it. If file reads return 401, the Obsidian container was likely restarted — retry once before assuming the key changed.

**Heading patch rules:**
- `target_type: "heading"` requires correct format:
  - **H1:** use heading name directly → `target: "My Heading"`
  - **H2+:** use `::` delimiter path → `target: "Parent Heading::Child Heading"`
  - Always end `content` with `\n\n` (double newline) to preserve section boundaries — omitting this consumes the blank line between sections, making subsequent sections un-targetable
- `target_type: "frontmatter"` works on files that already have frontmatter
- Delete + recreate with `obsidian_append_content` is the safest fallback for full rewrites

---

## Vault Structure

```text
Vault Root
├── Home.md                    Master index — start here for vault orientation
│
├── 00 - Inbox/                Raw, UNTAGGED captures only (≤48h rule)
│   └── _README.md             Processing rules
│
├── 10 - Daily/                Daily notes (YYYY-MM-DD.md)
├── 20 - Weeks/                Weekly sprint notes (YYYY-WW.md)
├── 30 - Backlog/              Tagged #action items waiting for a sprint
│
├── 40 - Projects/             Active and shipped project notes
│   ├── YOUR_PROJECT_1/
│   ├── YOUR_PROJECT_2/
│   └── YOUR_PROJECT_3/
│
├── 50 - Notes/                Permanent/atomic Zettelkasten notes (one idea per file)
├── 60 - MOCs/                 Maps of Content — navigation layer, not storage
├── 70 - Sources/              Literature notes (one per source, via Fabric)
│   ├── Literature/
│   ├── Philosophy/
│   └── Technology/
│
├── 80 - Reference/            Vault infrastructure and operational docs
├── 90 - Templates/            Daily Note, Weekly Note (plain markdown — no plugin)
└── 99 - Archive/              Completed backlog items (read-only reference)
```

---

## The Two Workflows

### 1. Zettelkasten (Second Brain)

`Inbox (#knowledge) → Sources/ (literature notes via Fabric) → Notes/ (permanent atomic notes) → MOCs/ (navigation)`

Each permanent note in `Notes/` contains one atomic idea, written assertively ("X is true" not "Author says X"), linked to sources and related notes.

### 2. Personal Scrum (Task/Action System)

```text
00 - Inbox/ (raw capture, untagged)
  ↓ triage within 48h
30 - Backlog/ (#action items, tagged)
  ↓ Monday sprint planning
20 - Weeks/YYYY-WW.md (sprint backlog)
  ↓ daily pull
10 - Daily/YYYY-MM-DD.md (daily note)
```

**Sprint cadence:** Monday → Sunday (1 week). Daily note = standup artifact.

---

## Conventions

### Frontmatter Tagging

```yaml
---
tags: [action]            # actionable task — moves to 30 - Backlog/
tags: [knowledge]         # Zettelkasten capture — stays in Inbox, processes to 50 - Notes/
tags: [action, knowledge] # both — goes to 30 - Backlog/, outputs to 50 - Notes/ when done
---
```

### File Naming

- Daily notes: `10 - Daily/YYYY-MM-DD.md`
- Weekly notes: `20 - Weeks/YYYY-WW.md` (e.g. `20 - Weeks/2026-W09.md`)
- Sources: `Author - Title.md`
- Permanent notes: assertive title stating the idea (e.g. `Virtue Requires Habituation.md`)

### Daily Note Structure

1. **Today's 3** — MITs, filled in before anything else
2. **Standup** — yesterday / today / blockers
3. **Tasks** — Work (4 priority sub-headers) / Home / Personal Admin / Projects / Research & Second Brain
4. **Captures** — fleeting notes, processed to Inbox before end of day
5. **End of Day** — done / moved to backlog / notes

### Work Priority Areas

The four Work sub-headers in the Daily Note and Weekly Note templates are generic by default. Customize them to match your actual work domains:

```
#### YOUR_PRIORITY_AREA_1
#### YOUR_PRIORITY_AREA_2
#### YOUR_PRIORITY_AREA_3
#### YOUR_PRIORITY_AREA_4
```

### Backlog File Conventions

Every `30 - Backlog/` file uses two standard footer elements:

- **`Linked:`** — wiki links to every daily note where this item appears. Update when scheduled to a new day.
  ```
  Linked: [[YYYY-MM-DD]] · [[YYYY-MM-DD]]
  ```
- **`## Resources`** — external links relevant to the item.

### Archive Conventions

When a backlog item is complete, move it to `99 - Archive/`:
1. Delete from `30 - Backlog/`
2. Recreate at `99 - Archive/` with `tags: [action, archived]`, `Completed:` and `Archived:` date fields
3. Append current weekly note to the `Linked:` line (e.g. `· [[2026-W09]]`)

The archive is read-only reference. No further updates after a file is moved there.

### Events File

`60 - MOCs/Upcoming Events.md` is the single source of truth for all date-anchored items.

**Rule:** If an item has a specific date — deadline, meeting, appointment, event — it goes in the Events file. Backlog files are for ongoing, undated action items only.

**Format:**
- `## YYYY-MM` — month header (collapsible)
- `### YYYY-MM-DD — DayName` — date header (collapsible)
- Bullet points for events; indented sub-bullets for sub-tasks or notes

**Maintenance:** Updated automatically during EOD, BOD, BOW, and EOW:
- New date-anchored item surfaced → add entry to Events file
- Event passes and is confirmed done → remove entry
- BOW/EOW sprint prep → pull Events file entries for the week into sprint backlog

### Future Daily Notes

Daily notes can and should be pre-created for dates with known commitments — don't wait for the day to arrive. When scanning the vault for date-anchored items, create stubs using the daily note template pre-populated with known tasks.

---

## Your Context

*Customize this section with your actual situation. The more specific you are, the better the AI can assist with sprint planning, prioritization, and daily standups.*

### Work Context

```
Role: YOUR_ROLE
Organization: YOUR_ORGANIZATION
Current priorities (in order):
1. YOUR_PRIORITY_AREA_1
2. YOUR_PRIORITY_AREA_2
3. YOUR_PRIORITY_AREA_3
4. YOUR_PRIORITY_AREA_4
```

*Add any relevant calendar constraints, seasonal tempo, or deadlines here.*

### Personal Priorities

```
Home: YOUR_HOME_GOALS
Self: YOUR_PERSONAL_GOALS (health, fitness, mental health, etc.)
Projects: YOUR_ACTIVE_PROJECTS (in priority order)
```

### Active Projects

| Project | Location | Status |
| --- | --- | --- |
| YOUR_PROJECT | `40 - Projects/YOUR_PROJECT/` | Status |

### Key Reference Files

| File | Purpose |
| --- | --- |
| `Home.md` | Master vault index and architecture overview |
| `80 - Reference/Daily Note Workflow.md` | Full action item pipeline — 4-stage flow, weekly cycle |
| `80 - Reference/Personal Scrum.md` | Sprint methodology + ADHD adaptations |
| `60 - MOCs/Current Priorities.md` | Quarterly north star by domain — review before sprint planning |
| `60 - MOCs/Upcoming Events.md` | Events timeline — source of truth for all date-anchored items |

---

## Tech Stack Preferences

*Add your preferred tools so Claude doesn't suggest alternatives.*

| Domain | Tool | Notes |
| --- | --- | --- |
| YOUR_DOMAIN | YOUR_TOOL | YOUR_NOTE |

---

## Fabric Integration

Sources enter the vault via **Fabric** (AI pattern framework). Raw source material is piped through patterns like `extract_wisdom` or `capture_thinkers_work`, producing a structured literature note that lands in `70 - Sources/`. Reference: `80 - Reference/Fabric Patterns.md` (create this file to document which patterns you use).

---

## ADHD Considerations

The system is designed with ADHD in mind. Key adaptations:

- Daily note leads with **Today's 3** (MITs) before the full task list
- Sprint backlog is a menu, not a contract — uneven sprints are data, not failure
- Inbox friction should be kept near zero
- `80 - Reference/Personal Scrum.md` has a full ADHD Adaptations section

---

## Available MCP Tools

These are the MCP tools registered with the standard setup from `setup/claude-settings.json`. Add any additional tools you've registered.

### Obsidian
*(See Vault Access section above for full tool list)*

### YouTube Transcript
| Tool | Purpose |
| --- | --- |
| `mcp__youtube-transcript__get_transcript` | Get full transcript of a YouTube video |
| `mcp__youtube-transcript__get_timed_transcript` | Get transcript with timestamps |
| `mcp__youtube-transcript__get_video_info` | Get metadata/info for a YouTube video |

### Fabric
| Tool | Purpose |
| --- | --- |
| `mcp__fabric__fabric_list_patterns` | List all available Fabric patterns |
| `mcp__fabric__fabric_get_pattern_details` | Get full details for a specific pattern |
| `mcp__fabric__fabric_run_pattern` | Execute a Fabric pattern with input text |
| `mcp__fabric__fabric_list_models` | List configured models by vendor |
| `mcp__fabric__fabric_list_strategies` | List available execution strategies |
| `mcp__fabric__fabric_get_configuration` | Get Fabric configuration (sensitive values redacted) |

### Miniflux *(required for `/news` only)*
| Tool | Purpose |
| --- | --- |
| `mcp__miniflux__*` | Fetch unread entries from your Miniflux RSS instance |

---

## Today's Date

Add a line like this to keep Claude oriented — update it or let Claude update it at the start of each session:

```
# currentDate
Today's date is YYYY-MM-DD.
```
