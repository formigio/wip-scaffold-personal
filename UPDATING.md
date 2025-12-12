# Updating Your WIP from Scaffold

The scaffold receives periodic improvements to agents, workflows, and documentation. Here's how to update your existing WIP.

## Quick Update with Claude Code

Copy and paste this prompt into Claude Code:

```
Update from github.com/formigio/wip-scaffold-personal:
- Update bin/wip CLI tool (team collaboration features)
- Review and apply improvements to review-day agent (better task tracking)
- Update prioritize, plan-day, and note-organizer agents
- Check CLAUDE.md for workflow improvements
- Preserve all my customizations (team names, projects, custom agents)

Show me what changed and let me approve before applying.
```

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

**Review before updating (may have your customizations):**
- `.claude/agents/create-status-report.md` - Has your team member names
- `CLAUDE.md` - Has your project/team examples

**Never overwrite (your personal data):**
- `daily/*.md` - Your daily files
- `projects/index.md` - Your projects
- `recurring-tasks.md` - Your specific tasks
- `team/` - Your team data
- `shared/` - Your shared projects

## Recent Updates

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
