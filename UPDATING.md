# Updating Your WIP from Scaffold

The scaffold receives periodic improvements to agents, workflows, and documentation. Here's how to update your existing WIP.

## Quick Update with Claude Code

Copy and paste this prompt into Claude Code:

```
Update from github.com/formigio/wip-scaffold-personal:
- Update bin/wip CLI tool (status.md-based review-projects, overdue reviews in new-day)
- Add the backlog system: create backlog.md and adopt the backlog-centric daily/EOD workflow
- Add the add-task agent (triage: today / future date / backlog)
- Add journeys/ (_template.md + README.md) for multi-step initiatives
- Migrate projects to the two-tier structure (slim index.md table + per-project status.md)
- Update review-day, prioritize, plan-day agents (backlog-aware)
- Check CLAUDE.md / AGENTS.md for workflow improvements
- Preserve all my customizations (team names, projects, custom agents)

Show me what changed and let me approve before applying.
```

> **⚠️ Two-tier projects migration (required for `review-projects`):** the CLI now scans
> per-project `projects/<name>/status.md` files. If your projects still live inline in a
> single `projects/index.md`, `review-projects` will silently find nothing until you split
> each project into its own `status.md` and slim `index.md` down to a summary table. Ask
> Claude to migrate your existing projects to the two-tier layout.

Claude will:
1. Fetch the latest scaffold from GitHub
2. Compare with your current files
3. Show you the differences
4. Apply updates you approve while preserving your customizations

## Manual Update Process

If you prefer to update manually:

```bash
# 1. Clone scaffold to temporary location
cd /tmp
git clone https://github.com/formigio/wip-scaffold-personal.git

# 2. Navigate to your WIP
cd ~/path/to/your/wip

# 3. Copy safe files (these have no customizations)
cp /tmp/wip-scaffold-personal/.claude/agents/review-day.md .claude/agents/
cp /tmp/wip-scaffold-personal/.claude/agents/prioritize.md .claude/agents/
cp /tmp/wip-scaffold-personal/.claude/agents/plan-day.md .claude/agents/
cp /tmp/wip-scaffold-personal/.claude/agents/note-organizer.md .claude/agents/
cp /tmp/wip-scaffold-personal/bin/wip bin/wip

# 4. For customized files, compare and merge manually:
diff -u .claude/agents/create-status-report.md /tmp/wip-scaffold-personal/.claude/agents/create-status-report.md
# Copy workflow improvements but keep your team names

# 5. Commit
git add .claude/agents/ bin/wip
git commit -m "Update agents and CLI from scaffold"
```

## What Gets Updated vs. Preserved

**Always safe to update:**
- `bin/wip` - CLI tool with team collaboration features
- `.claude/agents/review-day.md` - Planning and task tracking logic
- `.claude/agents/prioritize.md` - Prioritization logic
- `.claude/agents/plan-day.md` - Time blocking logic
- `.claude/agents/note-organizer.md` - Note organization logic
- `.claude/agents/add-task.md` - Task triage logic (new)
- `journeys/_template.md`, `journeys/README.md` - Journey format (new)

**Review before updating (may have your customizations):**
- `.claude/agents/create-status-report.md` - Has your team member names
- `CLAUDE.md` / `AGENTS.md` - Have your project/team examples
- `backlog.md` - New file; safe to add, but review the categories to fit your work
- `projects/` - Two-tier migration changes the layout (see the ⚠️ note above)

**Never overwrite (your personal data):**
- `daily/*.md` - Your daily files
- `backlog.md` - Once you've populated it
- `projects/index.md` and `projects/<name>/status.md` - Your projects
- `journeys/*.md` - Your journeys (except `_template.md` / `README.md`)
- `recurring-tasks.md` - Your specific tasks
- `team/` - Your team data
- `shared/` - Your shared projects

## Recent Updates

### July 2026: Backlog, Two-Tier Projects, Journeys & Task Triage
**Files:** `backlog.md` (new), `bin/wip`, `projects/` (restructured), `journeys/` (new), `.claude/agents/add-task.md` (new), `review-day.md`, `prioritize.md`, `plan-day.md`, `CLAUDE.md`, `AGENTS.md`, `.codex/prompts/`
**New:**
- **Backlog system** — `backlog.md` is the source of truth for all pending work; daily files hold only realistic commitments. Morning pulls from backlog; end-of-day returns incomplete items to it.
- **Two-tier projects** — slim `projects/index.md` summary table + per-project `status.md` (full details) + optional `notes.md`. `review-projects` now scans `status.md` files and `new-day` surfaces reviews past cadence.
- **Journeys** — `journeys/` for multi-step initiatives where the path isn't clear upfront (Goal Posts, Journal, Next Step).
- **add-task agent** — triages new tasks to today, a future date, or the backlog.

**Impact:** Nothing gets dropped (everything has a home in the backlog), project reviews scale without a bloated index, and exploratory work has a dedicated format. See the ⚠️ migration note above for the two-tier projects change.

### December 2025: Team Collaboration Features
**Files:** `bin/wip`
**New Commands:**
- `team-log <project> <task>` - Post structured work entry with estimates and challenges
- `add-request <project> <member> <task>` - Create todo for team member
- `sync-requests <project>` - Pull team requests into personal daily

**Improvements:**
- Auto-detect git config when cloning projects
- Offer to add user to team.md automatically
- Enhanced display name extraction from team.md

**Impact:** Full async team coordination - request tasks from teammates, track work with estimates, sync requests into your daily file.

### December 2025: Enhanced Task Tracking
**Files:** `review-day.md`, `CLAUDE.md`
**Improvement:** Prevents dropped tasks, especially Team Requests
**Details:** Explicit 5-day task tracking, critical priority for team commitments

Recommended for all users to improve task accountability.

## Questions?

Use the Claude Code prompt above - it handles the update process safely while preserving your customizations.
