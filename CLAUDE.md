# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a personal accomplishment tracking system for managing daily tasks, projects, and team status reports. It uses markdown files with git version control for simplicity and portability.

## Core Architecture

### Directory Structure

- **`daily/`** - Daily task files named `YYYY-MM-DD.md` with standardized format
- **`projects/`** - Project tracking with `index.md` master list and individual project folders with `notes.md`
- **`team/`** - Team management files:
  - `daily-logs/` - Team daily logs (e.g., `january.md`)
  - `status-reports/` - Leadership and management status reports
- **`reviews/`** - Weekly and monthly review summaries
- **`recurring-tasks.md`** - Master list of recurring tasks by day of week
- **`bin/accomplish`** - Bash CLI tool for common operations
- **`.claude/agents/`** - Claude Code agent definitions for workflow automation

### Daily File Format

Each daily file follows this structure:
```markdown
# Daily Tasks - [Day], Month DD, YYYY

## Today's Focus
1. High priority item 1
2. High priority item 2

## Tasks

### Recurring
- [ ] Daily recurring tasks (auto-populated)
- [ ] Day-specific recurring tasks (auto-populated)

### Other
- [ ] One-time tasks
- [x] Completed tasks

## Notes
- Meeting notes, thoughts, observations

## Prioritized Task Order
(Optional section added by planning workflow)

## End of Day Summary
(Added at end of day with completed/carried forward tasks)
```

### Project Tracking Format

The `projects/index.md` file tracks all active projects with:
- **Status:** Active/Paused/Completed
- **Review Cadence:** daily/weekly (with specific day)/monthly
- **Last Reviewed:** YYYY-MM-DD (used to determine if review is due)
- **Remaining Estimate:** Time estimate or "ongoing"
- **Next Steps:** Checkbox list of actionable items

Individual projects can have sub-projects with their own status and next steps.

### Recurring Tasks System

`recurring-tasks.md` defines tasks that auto-populate daily files:
- **Daily Tasks** - appear every day
- **Monday/Tuesday/Wednesday/Thursday/Friday Tasks** - appear on specific weekdays
- **Weekend Tasks** - appear on Saturday/Sunday

The system supports day-specific project reviews (e.g., "Review Project Alpha" on Tuesdays).

## CLI Tool Usage

The `bin/accomplish` bash script provides commands:

```bash
./bin/accomplish new-day              # Create today's daily file with recurring tasks
./bin/accomplish add-task "Task"      # Add task to today's file
./bin/accomplish review-yesterday     # Display previous working day's file
./bin/accomplish review-projects      # Check which projects are due for review
./bin/accomplish weekly-summary       # Create weekly review file
./bin/accomplish monthly-summary      # Create monthly review file
./bin/accomplish list-days [n]        # List last n daily files
./bin/accomplish open-project <name>  # Open/create project notes
```

## Claude Code Agents

Five specialized agents in `.claude/agents/`:

1. **review-day** - Review yesterday and plan today (reads previous day, recurring tasks, project due dates)
2. **prioritize** - Prioritize tasks based on projects and commitments
3. **plan-day** - Structure the day with time blocks and realistic scheduling
4. **create-status-report** - Generate team status reports for leadership/management
5. **note-organizer** - Capture and structure meeting notes, ideas, and learning notes

## Workflow Patterns

### Daily Morning Workflow
1. Review yesterday's accomplishments and incomplete tasks
2. Check recurring tasks for today (by day of week)
3. Identify projects due for review based on cadence and last reviewed date
4. Create prioritized task order considering time estimates
5. Update daily file with focus areas and task list

### End of Day Workflow
1. Mark completed tasks with `[x]`
2. Add "End of Day Summary" section with:
   - Completed Today (with ✅)
   - Carried Forward (incomplete tasks)
   - Key Updates (important project notes)
3. Commit changes to git

### Project Review Workflow
1. Check `projects/index.md` for projects due based on review cadence
2. Review project next steps and status
3. Update "Last Reviewed" date after review
4. Add new next steps or update estimates as needed

### Team Status Reports
Status reports go in `team/status-reports/` with naming format:
`YYYY-MM-DD-to-YYYY-MM-DD-{leadership|management}.md`

Reports summarize accomplishments, project updates, and team activities for the reporting period.

## Key Concepts

### Task Carryover Logic
- Recurring tasks auto-populate daily (don't manually carry forward)
- One-time incomplete tasks are manually reviewed and carried forward if still relevant
- On Mondays, review Friday (last working day) instead of Sunday

### Project Review Cadence
Projects track when they were last reviewed. The system calculates if a review is due:
- **daily** - review if 1+ days since last reviewed
- **weekly** - review if 7+ days since last reviewed
- **monthly** - review if 30+ days since last reviewed

Day-specific reviews (e.g., "weekly (Tuesday)") are tracked via recurring tasks, not the projects file calculation.

### Date Handling
All dates use ISO format (YYYY-MM-DD). The bash tool handles date math including:
- Yesterday calculation
- Last working day (Friday if today is Monday)
- Day of week determination for recurring tasks

## Git Practices

This repository is meant to be committed frequently:
- Commit daily updates at end of day
- Use descriptive commit messages (e.g., "Daily update: 2025-01-15")
- Push regularly for backup

## Working with This Repository

When helping the user:
1. **Read yesterday's daily file** to understand context before planning today
2. **Check recurring-tasks.md** to know what tasks apply today based on day of week
3. **Review projects/index.md** to identify projects needing attention
4. **Follow the daily file format** consistently when creating or modifying files
5. **Update "Last Reviewed" dates** in projects/index.md after project reviews
6. **Use ISO date format** (YYYY-MM-DD) everywhere
7. **Preserve the prioritized task order** format when adding to daily files
8. **Mark tasks completed** with `[x]` when user confirms completion
