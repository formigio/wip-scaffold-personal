# Formigio WIP - Work In Progress

A simple, markdown-based system for tracking daily tasks, managing projects, and creating status reports. Everything is stored in plain text markdown files with git version control for simplicity and portability.

## Features

- **Daily Task Tracking** - Structured daily files with recurring task automation
- **Project Management** - Track active projects with next steps and review cadences
- **Collaborative Projects** - Work async with teammates using embedded git repos
- **Team Logs** - Daily logs and status reports for team leadership
- **Weekly/Monthly Reviews** - Summarize accomplishments and reflect on progress
- **CLI Tool** - Bash script for common operations
- **Claude Code Agents** - AI-powered workflow automation for planning, prioritizing, and reporting

## Quick Start

### 1. Clone and Customize

```bash
git clone <this-repo-url>
cd personal-accomplishment-tracker

# Make the CLI tool executable
chmod +x bin/accomplish
```

### 2. Customize Recurring Tasks

Edit `recurring-tasks.md` to define your regular tasks:

```markdown
## Daily Tasks
- [ ] Your daily task here

## Monday Tasks
- [ ] Weekly planning

## Tuesday Tasks
- [ ] Team sync
```

### 3. Create Your First Daily File

```bash
./bin/wip new-day
```

This creates a daily file for today (e.g., `daily/2025-01-15.md`) with:
- Today's date and day of week
- Recurring tasks for today
- Standard sections: Focus, Tasks, Notes, Summary

### 4. Set Up Your Projects

Edit `projects/index.md` to add your projects. Each project has:
- **Status:** Active/Paused/Completed
- **Review Cadence:** daily/weekly/monthly
- **Last Reviewed:** Track when you last reviewed it
- **Remaining Estimate:** Time estimate
- **Next Steps:** Checkbox list of actionable items

Example:
```markdown
## My Project
- **Status:** Active
- **Review Cadence:** weekly (Tuesday)
- **Last Reviewed:** 2025-01-15
- **Remaining Estimate:** 2 weeks
- **Next Steps:**
  - [ ] Complete design doc
  - [ ] Schedule review meeting
```

## Directory Structure

```
.
├── bin/
│   └── wip           # CLI tool for common operations
├── daily/                   # Daily task files (YYYY-MM-DD.md)
├── shared/                # Collaborative project repos (separate git histories)
├── projects/
│   ├── index.md            # Master project list
│   └── [project-name]/     # Individual project folders
│       └── notes.md        # Detailed project notes
├── team/
│   ├── daily-logs/         # Team daily logs by month
│   └── status-reports/     # Leadership status reports
├── reviews/
│   ├── weekly/             # Weekly review summaries
│   └── monthly/            # Monthly review summaries
├── .claude/
│   └── agents/             # Claude Code agent definitions
├── recurring-tasks.md      # Recurring task definitions
└── README.md               # This file
```

## Daily Workflow

### Morning
1. **Review yesterday** (manually or with Claude Code):
   ```bash
   ./bin/wip review-yesterday
   ```

2. **Check projects due for review**:
   ```bash
   ./bin/wip review-projects
   ```

3. **Plan your day** - Use Claude Code agents for help:
   - `/review-day` - Review yesterday and plan today
   - `/prioritize` - Prioritize tasks based on projects
   - `/plan-day` - Create time-blocked schedule

### During the Day
- Check off tasks as completed: `- [x] Completed task`
- Add notes as needed
- Update project next steps in `projects/index.md`

### End of Day
1. Mark completed tasks with `[x]`
2. Add "End of Day Summary" section:
   ```markdown
   ## End of Day Summary

   ### Completed Today
   - ✅ Task 1
   - ✅ Task 2

   ### Carried Forward
   - [ ] Incomplete task (still relevant)

   ### Key Updates
   - Important project updates or notes
   ```

3. Commit changes:
   ```bash
   git add .
   git commit -m "Daily update: $(date +%Y-%m-%d)"
   git push
   ```

## CLI Tool Reference

```bash
# Create today's daily file with recurring tasks
./bin/wip new-day

# Add a task to today's file
./bin/wip add-task "Task description"

# Review yesterday's file
./bin/wip review-yesterday

# Check which projects are due for review
./bin/wip review-projects

# Create weekly review
./bin/wip weekly-summary

# Create monthly review
./bin/wip monthly-summary

# List recent daily files
./bin/wip list-days [n]

# Open/create project notes
./bin/wip open-project <project-name>

# Collaborative Projects
./bin/wip clone-project <url> <name>    # Clone shared project
./bin/wip log-project <name>            # Log work (auto-commits)
./bin/wip sync-project <name>           # Pull teammate updates
./bin/wip team-status <name> [days]     # Show team activity
./bin/wip list-embedded-projects        # List all shared WIPs
```

## Collaborative Projects

Work on shared projects with teammates using embedded git repositories. Each embedded project has its own git history and allows async collaboration.

### Setup a Collaborative Project

1. **Clone an existing collaborative project:**
   ```bash
   ./bin/wip clone-project git@github.com:team/project.git project-name
   ```
   This will prompt you for your username and set up your identity.

2. **Or manually set up:**
   ```bash
   cd shared/project-name
   echo "your-username" > .me
   mkdir -p daily/your-username
   ```

### Daily Workflow for Collaborative Projects

**Morning:**
```bash
# See what teammates did
./bin/wip sync-project project-name
./bin/wip team-status project-name
```

**End of Day:**
```bash
# Log your work (auto-commits and pushes)
./bin/wip log-project project-name
```

### Embedded Project Structure

Each collaborative project has:
- **`daily/<username>/`** - Personal daily logs for each team member
- **`team.json`** - Team configuration and member list
- **`notes.md`** - Shared project notes
- **`decisions.md`** - Architecture decision records
- **`.me`** - Local identity file (gitignored)

Daily logs use a simplified format focused on project work:
```markdown
# YYYY-MM-DD - Your Name

## Completed
- [x] What you finished

## In Progress
- [ ] What you're working on

## Blockers
None (or list blockers)

## Notes
- Context for teammates
```

## Claude Code Agents

If you use [Claude Code](https://claude.com/claude-code), specialized agents in `.claude/agents/` can help automate workflows:

### `/review-day`
Reviews yesterday's accomplishments and creates today's plan:
- Reads previous working day's file
- Checks recurring tasks for today
- Identifies projects due for review
- Creates structured plan for today

### `/prioritize`
Prioritizes tasks based on projects and commitments:
- Analyzes task list and project deadlines
- Creates prioritized order with time estimates
- Explains rationale for prioritization

### `/plan-day`
Creates time-blocked schedule:
- Reviews prioritized tasks
- Blocks time realistically
- Accounts for meetings and breaks
- Creates structured daily plan

### `/create-status-report`
Generates status reports for leadership:
- Reviews recent daily logs
- Summarizes accomplishments
- Highlights project updates
- Creates polished report document

### `/note-organizer`
Captures and structures notes:
- Processes meeting notes, ideas, or learnings
- Creates daily log entry
- Creates detailed note file in appropriate location

## Customization Tips

### Adjust Recurring Tasks
Edit `recurring-tasks.md` to match your schedule. You can:
- Add/remove tasks for any day
- Comment out tasks temporarily: `<!-- - [ ] Task -->`
- Add context with sub-bullets
- Define monthly or first/last day of month tasks

### Project Review Cadences
Projects support flexible review cadences:
- `daily` - Review every day
- `weekly` - Review once per week (7+ days)
- `weekly (Tuesday)` - Review on specific day (via recurring task)
- `monthly` - Review once per month (30+ days)

The `review-projects` command checks if projects are overdue based on "Last Reviewed" date.

### Team Logs & Status Reports
If you manage a team:
- Use `team/daily-logs/` for informal daily logs (one file per month)
- Use `team/status-reports/` for formal reports to leadership
- Name reports: `YYYY-MM-DD-to-YYYY-MM-DD-leadership.md`

### Create Project Folders
For detailed projects, create a folder:
```bash
mkdir -p projects/my-project
touch projects/my-project/notes.md
```

Use the notes file for:
- Meeting notes
- Technical details
- Research and references
- Decision logs

## Git Workflow

This system is designed for frequent commits:

```bash
# At end of day
git add .
git commit -m "Daily update: 2025-01-15"
git push

# For project updates
git add projects/
git commit -m "Update Project Alpha status and next steps"
git push
```

Consider:
- Committing daily updates at end of day
- Committing project changes when significant updates occur
- Pushing regularly for backup

## Tips for Success

1. **Be consistent** - Use the daily file format consistently
2. **Review regularly** - Actually review projects on their cadence
3. **Keep it simple** - Don't over-engineer, markdown is the power
4. **Capture everything** - Use notes sections liberally
5. **Reflect weekly/monthly** - Reviews help identify patterns
6. **Update projects** - Keep "Last Reviewed" dates current
7. **Commit often** - Git is your backup and history

## Why This System?

- **Plain text** - Markdown files work everywhere, forever
- **Git version control** - Full history, branching, backup
- **Portable** - Clone anywhere, no dependencies
- **Searchable** - Grep, file search, git log all work
- **Extensible** - Add your own scripts, integrations, formats
- **AI-friendly** - Claude Code can read, analyze, and help manage everything

## License

This is a personal tool template. Use it however you'd like. No attribution needed.

## Contributing

This is a personal accomplishment tracker template. Fork it, customize it, make it your own!

If you have ideas for improvements to the template itself, feel free to submit issues or pull requests.

---

**Get started:** Run `./bin/wip new-day` and start tracking!
