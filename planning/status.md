# status.md · `planning/`

**Last updated:** 2026-09-29
**Updated by:** Claude (planning rollout with gabriel)
**Covers:** all of `planning/`, including `reports/`

## Current state

Planning folder per DS-STD-001-006: data only (`status.md`, `ideas.md`, `data/`, `reports/`).
Workflows and builders are served by darwin-agent-center (`kb_planning_workflow()`,
`kb_planning_builders()`); nothing of the engine lives here. `data/items.csv` holds the header only: the root `IDEAS.md` had no entries (empty template
tables), so nothing was migrated on 2026-09-29; the file was removed (git history keeps it).

## Open items

| Item | Status | Notes |
|---|---|---|
| Migrated rows without owner / importance / size | done | none (no rows) |
| Old planning material: `PENDING.md` | open | Website restructure proposal (sections, services, industries); how to migrate is pending |

## Project facts the workflows point to

| Fact | Detail |
|---|---|
| Retired ids | none |
| Confidentiality | see `AGENTS.md` |

## Last completed work

2026-09-29: planning folder created, empty IDEAS.md removed (no entries to migrate), dashboard built.

## Downstream status files

none (this file covers the report folders too).
