# CLAUDE.md

This file provides context to Claude Code (claude.ai/code) when working with this vault. It enables AI-assisted workflow automation — sprint planning, daily standups, end-of-day closeouts, and knowledge capture — directly from your terminal.

**Before using this file:** replace every `YOUR_*` placeholder with your own information. The more accurately this file reflects your actual context, the better the AI assistance will be.

---

## Vault Access

This vault is accessed via the Obsidian MCP server. See `80 - Reference/Claude Code Setup.md` for full setup instructions.

| Tool | Purpose |
| --- | --- |
| `mcp__obsidian__obsidian_list_files_in_vault` | List vault root |
| `mcp__obsidian__obsidian_list_files_in_dir` | List a directory |
| `mcp__obsidian__obsidian_get_file_contents` | Read a single file |
| `mcp__obsidian__obsidian_batch_get_file_contents` | Read multiple files at once |
| `mcp__obsidian__obsidian_simple_search` | Full-text search across vault |
| `mcp__obsidian__obsidian_complex_search` | JsonLogic query (tags, paths, patterns) |
| `mcp__obsidian__obsidian_append_content` | Create or append to a file |
| `mcp__obsidian__obsidian_patch_content` | Insert/replace within a file |
| `mcp__obsidian__obsidian_delete_file` | Delete a file (requires `confirm: true`) |
| `mcp__obsidian__obsidian_get_periodic_note` | Get current daily/weekly/monthly note |
| `mcp__obsidian__obsidian_get_recent_changes` | Get recently modified files |

**Known quirk:** `obsidian_patch_content` with `target_type: "heading"` is unreliable. The reliable workaround is to delete the file and recreate it with `obsidian_append_content`. Use `patch_content` only for `target_type: "frontmatter"` on files that already have frontmatter.

---

## Vault Structure

```text
Vault Root
├── Home.md                    Master index
│
├── 00 - Inbox/                Raw captures (≤48h rule)
│   └── _README.md
│
├── 10 - Daily/                Daily notes (YYYY-MM-DD.md)
├── 20 - Weeks/                Weekly sprint notes (YYYY-WW.md)
├── 30 - Backlog/              #action items waiting for a sprint
│
├── 40 - Projects/             Active and completed project notes
│
├── 50 - Notes/                Permanent/atomic Zettelkasten notes
├── 60 - MOCs/                 Maps of Content — navigation layer
├── 70 - Sources/              Literature notes (one per source)
│   ├── Literature/
│   ├── Philosophy/
│   └── Technology/
│
├── 80 - Reference/            Vault workflow and reference docs
├── 90 - Templates/            Daily Note, Weekly Note templates
└── 99 - Archive/              Completed backlog items (read-only)
```

---

## The Two Workflows

### 1. Personal Scrum (Task System)

```text
00 - Inbox/ (raw capture, untagged)
  ↓ triage within 48h
30 - Backlog/ (#action items, tagged)
  ↓ Monday sprint planning
20 - Weeks/YYYY-WW.md (sprint backlog)
  ↓ daily pull
10 - Daily/YYYY-MM-DD.md (daily note)
  ↓ completed
99 - Archive/
```

Sprint cadence: Monday → Sunday. Daily note = standup artifact.

### 2. Zettelkasten (Second Brain)

```text
00 - Inbox/ (#knowledge captures)
  ↓
70 - Sources/ (literature notes)
  ↓
50 - Notes/ (permanent atomic notes)
  ↓
60 - MOCs/ (navigation)
```

---

## Conventions

### Frontmatter Tagging

```yaml
---
tags: [action]      # actionable task → moves to 30 - Backlog/
---
tags: [knowledge]   # idea/insight → processes to 50 - Notes/
---
tags: [action, knowledge]  # both
---
```

### File Naming

- Daily notes: `10 - Daily/YYYY-MM-DD.md`
- Weekly notes: `20 - Weeks/YYYY-WW.md`
- Backlog items: descriptive title (e.g. `Learn Rust Async.md`)
- Permanent notes: assertive title stating the idea (e.g. `Virtue Requires Habituation.md`)

### Daily Note Structure

1. **Today's 3** — MITs, filled in before anything else
2. **Standup** — yesterday / today / blockers
3. **Tasks** — Work (4 priority sub-headers) / Home / Personal Admin / Projects & Research
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

---

## Your Context

*Customize this section with your actual situation. The more specific you are, the better the AI can assist with sprint planning, prioritization, and daily standups.*

### Role & Work Context

```
Role: YOUR_ROLE
Organization: YOUR_ORGANIZATION
Current priorities (in order):
1. YOUR_PRIORITY_1
2. YOUR_PRIORITY_2
3. YOUR_PRIORITY_3
4. YOUR_PRIORITY_4
```

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
| `Home.md` | Master vault index |
| `80 - Reference/Daily Note Workflow.md` | Full pipeline documentation |
| `80 - Reference/Personal Scrum.md` | Sprint methodology |

---

## Tech Stack Preferences

*Add your preferred tools here so Claude doesn't suggest alternatives.*

| Domain | Tool |
| --- | --- |
| YOUR_DOMAIN | YOUR_TOOL |

---

## Today's Date

Add a line like this to keep Claude oriented — update it or let Claude update it at the start of each session:

```
# currentDate
Today's date is YYYY-MM-DD.
```
