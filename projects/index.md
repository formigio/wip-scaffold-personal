# Projects Overview

Quick reference to all projects. See each project's `status.md` for full details.

**Two-tier structure:** this index is a slim summary table; each project has its own
folder with `status.md` (status, cadence, next steps, updates) and optional `notes.md`
(extended history, meeting notes, technical detail). `./bin/wip review-projects` scans
the `status.md` files to find reviews that are past cadence.

## Active Projects

| Project | Status | Review | Last Reviewed | Link |
|---------|--------|--------|---------------|------|
| Example Project Alpha | Active | weekly (Tuesday) | 2025-01-15 | [→](example-project-alpha/status.md) |

## Completed Projects

| Project | Completed | Link |
|---------|-----------|------|
| _(none yet)_ | | |

## Team WIPs

Shared collaborative projects live in `shared/<name>/` (separate git repos) and are
referenced here as pointers.

| Team | Status | Review | Last Reviewed | Link |
|------|--------|--------|---------------|------|
| _(none yet)_ | | | | |

## Workspaces (External Portfolios)

Dedicated external folders for scoped work on a portfolio of related initiatives. They
live outside this repo (e.g. `~/development/<workspace>/`) with their own `CLAUDE.md`.
Track them here as pointers; see CLAUDE.md → Workspaces for the full pattern.

| Workspace | Location | Status | Review | Link |
|-----------|----------|--------|--------|------|
| _(none yet)_ | | | | |

---

## Adding a New Project

1. Create a folder: `projects/<project-name>/`
2. Add `status.md` using the template below
3. Add a row to the appropriate table above with a link to the `status.md`
4. (Optional) Add `notes.md` for extended history and technical detail

### status.md Template

```markdown
# [Project Name]

- **Status:** [Active/Paused/Completed]
- **Review Cadence:** [daily/weekly/monthly, or weekly (specific day), or "as needed"]
- **Last Reviewed:** YYYY-MM-DD
- **Remaining Estimate:** [e.g., 2 weeks, ongoing, TBD]

## What it is
One or two sentences describing the project and its goal.

## Next Steps
- [ ] Task 1
- [ ] Task 2

## Recent Updates
- YYYY-MM-DD: What changed.

## Completed Tasks
- [x] Done item
```
