# Getting Started with Formigio WIP

Welcome to **Formigio WIP** (Work In Progress) - a simple, powerful system for tracking your daily tasks, managing projects, and collaborating with teammates.

## What You Get

- **Personal WIP** - Your daily task tracking and project management
- **Team WIPs** - Collaborate asynchronously on shared projects
- **Plain Text** - Everything in markdown files with git version control
- **No Dependencies** - Just bash, git, and a text editor
- **CLI Tools** - Simple commands for common operations

## Quick Setup (5 minutes)

### 1. Clone This Repository

```bash
cd ~
git clone https://github.com/formigio/wip-scaffold-personal.git my-wip
cd my-wip
```

Name it whatever you like - `my-wip`, `personal-wip`, or just `wip`.

### 2. Make CLI Executable

```bash
chmod +x bin/wip
```

### 3. Customize Recurring Tasks

Edit `recurring-tasks.md` to define your regular tasks:

```bash
nano recurring-tasks.md  # or your preferred editor
```

Example:
```markdown
## Daily Tasks
- [ ] Check email
- [ ] Review project status

## Monday Tasks
- [ ] Weekly planning
- [ ] Team sync

## Friday Tasks
- [ ] Weekly review
```

### 4. Create Your First Daily File

```bash
./bin/wip new-day
```

This creates `daily/2025-11-28.md` (or today's date) with:
- Your recurring tasks for today
- Sections for Focus, Tasks, and Notes
- Ready for you to fill in

### 5. Set Up Your Projects

Edit `projects/index.md` to track your personal projects:

```markdown
## My Project
- **Status:** Active
- **Review Cadence:** weekly
- **Last Reviewed:** 2025-11-28
- **Remaining Estimate:** 2 weeks
- **Next Steps:**
  - [ ] First task
  - [ ] Second task
```

## Daily Workflow

### Morning

```bash
# Create today's file
./bin/wip new-day

# Review yesterday (optional)
./bin/wip review-yesterday

# Check projects due for review
./bin/wip review-projects
```

### During the Day

Work on your tasks and check them off:
```markdown
- [x] Completed task
- [ ] Still working on this
```

### End of Day

Add a summary and commit:
```markdown
## End of Day Summary

### Completed Today
- ✅ Task 1
- ✅ Task 2

### Carried Forward
- [ ] Incomplete task

### Key Updates
- Important notes
```

Then commit:
```bash
git add .
git commit -m "Daily update: $(date +%Y-%m-%d)"
git push
```

## Working with Team WIPs

### Joining a Team WIP

If someone shares a Team WIP project with you:

```bash
./bin/wip clone-project <git-url> <project-name>
```

Example:
```bash
./bin/wip clone-project git@github.com:team/awesome-project.git awesome-project
```

You'll be prompted for your username - this identifies you in the team's daily logs.

### Daily Team WIP Workflow

**Morning:**
```bash
# See what teammates did
./bin/wip sync-project awesome-project
./bin/wip team-status awesome-project
```

**End of Day:**
```bash
# Log your work (auto-commits and pushes)
./bin/wip log-project awesome-project
```

### Team WIP Structure

Each Team WIP has:
- **`shared/<project-name>/`** - The shared repo
- **`shared/<project-name>/daily/you/`** - Your daily logs
- **`shared/<project-name>/daily/teammate/`** - Teammate's logs
- **`shared/<project-name>/notes.md`** - Shared notes
- **`shared/<project-name>/decisions.md`** - Decision records

## CLI Command Reference

### Personal WIP
```bash
./bin/wip new-day                # Create today's file
./bin/wip add-task "Task"        # Add task to today
./bin/wip review-yesterday       # View yesterday
./bin/wip review-projects        # Check project reviews
./bin/wip list-days 7            # List last 7 days
./bin/wip weekly-summary         # Create weekly review
./bin/wip monthly-summary        # Create monthly review
```

### Team WIPs
```bash
./bin/wip clone-project <url> <name>    # Join a team WIP
./bin/wip sync-project <name>           # Pull teammate updates
./bin/wip log-project <name>            # Log your work
./bin/wip team-status <name>            # See team activity
./bin/wip list-shared-projects          # List all team WIPs
```

## Directory Structure

```
my-wip/
├── bin/
│   └── wip              # CLI tool
├── daily/               # Your personal daily files
│   └── 2025-11-28.md
├── shared/              # Team WIPs you're part of
│   └── project-name/    # A team WIP (separate git repo)
├── projects/
│   ├── index.md         # Your project tracking
│   └── project-name/    # Personal project folders
├── team/                # If you manage a team
│   ├── daily-logs/
│   └── status-reports/
├── reviews/
│   ├── weekly/
│   └── monthly/
└── recurring-tasks.md   # Your recurring task definitions
```

## Tips for Success

1. **Be consistent** - Run `./bin/wip new-day` every morning
2. **Commit daily** - Git is your backup and history
3. **Review projects** - Keep "Last Reviewed" dates current
4. **Use recurring tasks** - Automate your routine
5. **Keep it simple** - Markdown is the power
6. **Reflect regularly** - Weekly/monthly reviews help identify patterns

## Optional: Claude Code Integration

If you use [Claude Code](https://claude.com/claude-code), this system includes AI-powered agents:

- `/review-day` - Review yesterday and plan today
- `/prioritize` - Prioritize your tasks
- `/plan-day` - Create time-blocked schedule
- `/note-organizer` - Capture meeting notes

The system works great without Claude Code too!

## Customization

### Recurring Tasks

Edit `recurring-tasks.md` to match your schedule:
- Add/remove tasks for any day
- Comment out tasks: `<!-- - [ ] Task -->`
- Different tasks for different days of the week

### Project Review Cadences

- `daily` - Review every day
- `weekly` - Review weekly (7+ days)
- `monthly` - Review monthly (30+ days)
- `weekly (Tuesday)` - Specific day via recurring task

### Team Status Reports

If you manage a team, use:
- `team/daily-logs/` - Informal daily logs
- `team/status-reports/` - Formal reports for leadership

## Getting Help

- **Documentation:** Check `README.md` for detailed info
- **CLAUDE.md:** Explains the system to Claude Code
- **Issues:** [GitHub Issues](https://github.com/formigio/wip-scaffold-personal/issues)
- **Community:** Share your setup and learn from others

## Why Formigio WIP?

- **Plain text** - Works everywhere, forever
- **Git version control** - Full history and backup
- **Portable** - Clone anywhere, no dependencies
- **Searchable** - grep, file search, git log all work
- **Extensible** - Add your own scripts and integrations
- **AI-friendly** - Claude Code can read and help manage everything
- **Async collaboration** - Team WIPs work on everyone's schedule

## Next Steps

1. ✅ Complete setup above
2. Customize recurring tasks for your schedule
3. Add your personal projects to `projects/index.md`
4. Use it daily for a week to build the habit
5. If collaborating, join or create Team WIPs
6. Explore weekly/monthly reviews for reflection

---

**Ready to track your work in progress?** Run `./bin/wip new-day` and get started! 🚀
