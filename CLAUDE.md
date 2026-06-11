# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

An [Obsidian](https://obsidian.md/) vault for a Legend of the Five Rings (L5R) TTRPG campaign. There is no build system, test suite, or linter to run — the "codebase" is a collection of Markdown notes with YAML frontmatter. Claude Code is accessed here via the **Claudian** plugin (`realclaudian`), which makes this vault the working directory.

## Vault Structure

```
/
├── Sessions/          # Campaign session notes (Session 1.md → Session 27.md)
├── NPCs/              # Non-player characters (60+ files)
├── The Party/         # 6 player character sheets
├── Locations/         # Geographic areas (Cities/, Castles/, Provinces/, Villages/, Family Lands/)
├── Clans/             # 13 clan files
├── Families/          # Family files
├── Schools/           # Training schools and orders
├── 1 - Summaries/     # Index files using Dataview queries (Party, NPCs, Sessions)
├── z_Templates/       # 12 Templater templates (auto-applied by folder)
└── .claudian/         # Claudian plugin session data
```

A handful of files live at the vault root instead of in a subfolder — this is intentional for newly created notes before they're filed.

## Active Plugins

| Plugin | Purpose |
|--------|---------|
| **dataview** | SQL-like queries over YAML frontmatter; powers the summary index notes |
| **templater-obsidian** | Dynamic templates with JS scripting; auto-applies by folder on file creation |
| **obsidian-git** | Automated daily backup commits ("vault backup: YYYY-MM-DD HH:MM:SS") |
| **obsidian-leaflet-plugin** | Interactive maps embedded in location notes (Rokugan world map) |
| **table-editor-obsidian** | Advanced table editing with formula support |
| **obsidian-linter** | Markdown formatting enforcement |
| **realclaudian** | Embeds Claude Code as an AI collaborator with vault file access |

## Note Templates and Frontmatter Conventions

Templates in `z_Templates/` define the frontmatter schema for each note type. Templater auto-applies them when a file is created in the matching folder. When creating notes programmatically, replicate the relevant template's frontmatter.

### NPC (`NPCs/` folder)
```yaml
---
AKA:
Province:
Affiliations:
tags:
  - NPC
sentiment:          # "Ally" | "Enemy" | "Neutral" | (blank) — drives 1 - Summaries/2 - NPCs.md
Clan:
Family:
status: alive       # "alive" | "dead"
sex: male
---
## Overview
```

### Session (`Sessions/` folder)
```yaml
---
date: YYYY-MM-DD
session: "27"
previous: "[[Session 26]]"
summary:
---
## Characters
## Overview
## Key Learnings
## Who Did We Meet?
```

### Player Character (`The Party/` folder)
Frontmatter includes: `Name`, `Gender`, `Race`, `Class`, `Condition`, `Role`, `Age`, `School`, `City`, `Tattoos`, `Religion`. The body uses multi-column callout layout with an infobox and Dataview inline expressions (`=this.fieldname`) to display relational data dynamically.

### Location (`Locations/` folder)
```yaml
---
Clan:
Province:
Family:
---
```

## Relational Data Model

Notes link to each other with `[[WikiLinks]]`. Character geographic info chains through: `City → Province → SuperProvince → Family → Clan`. Dataview inline expressions like `=this.City.Province.SuperProvince.Family.Clan` traverse this chain automatically.

The summary files in `1 - Summaries/` use Dataview table queries — e.g., `2 - NPCs.md` queries all `#NPC`-tagged files and groups them by `sentiment` field. Keep frontmatter values consistent with existing conventions so these queries remain accurate.

## Multi-Column Layout Syntax

Player character and some location notes use callout-based multi-column layout (via the ITS Theme + multi-column CSS snippet):

```markdown
> [!multi-column]
>> [!blank-container | wide-3]
>> ## Left column content
>
>> [!infobox]
>> Infobox content with tables
```

## File Naming

Files follow the pattern `Clan/Family PersonalName` (e.g., `Togashi Hanzo.md`, `Doji Gaoxing.md`, `Kuni Yoshiyuki.md`). Location files use the location's proper noun name. Avoid abbreviations — use the full in-universe name.

## Git Workflow

Commits are automated by the Obsidian Git plugin on a daily schedule. Manual commits can be triggered from within Obsidian. The only entry in `.gitignore` is `workspace.json`. Do not create separate feature branches for note edits — all content lives on the `main`/`ai-integration` branch and is committed as vault backups.
