# Setup Guide for Peter

Welcome! This guide will get you set up with the personal Formigio WIP system and ready to collaborate on the MBA Field Guide book project.

## What You're Getting

This is a complete personal productivity system that:
- Tracks your daily tasks and accomplishments
- Manages your projects with review cadences
- Enables async collaboration on shared projects (like our book!)
- Uses simple markdown files + git (works anywhere, no dependencies)

## Setup (10 minutes)

### Step 1: Clone This Repository

```bash
cd ~
git clone <wip-scaffold-repo-url> accomplishment
cd accomplishment
```

### Step 2: Make CLI Tool Executable

```bash
chmod +x bin/accomplish
```

### Step 3: Customize for Yourself

#### A. Set up your recurring tasks

Edit `recurring-tasks.md` to define your regular tasks:

```bash
nano recurring-tasks.md  # or use your preferred editor
```

Example tasks you might add:
```markdown
## Daily Tasks
- [ ] Check email and respond to urgent items
- [ ] Review project status
- [ ] Plan tomorrow

## Monday Tasks
- [ ] Weekly planning
- [ ] Review project milestones

## Friday Tasks
- [ ] Weekly review
- [ ] Prepare for next week
```

#### B. Create your first daily file

```bash
./bin/wip new-day
```

This creates a file like `daily/2025-11-28.md` with:
- Today's recurring tasks (from the file you just edited)
- Standard sections: Focus, Tasks, Notes, Summary
- Ready for you to fill in

#### C. Set up your projects (optional for now)

You can edit `projects/index.md` to track your personal projects, but we'll focus on the collaborative MBA Field Guide first.

### Step 4: Clone the MBA Field Guide Project

Now let's get you connected to our book project:

```bash
./bin/wip clone-project <mba-field-guide-url> mba-field-guide
```

When prompted for your username, enter: **peter**

This will:
- Clone the book project into `shared/mba-field-guide/`
- Set your identity as "peter"
- Create your daily log directory
- Add the project to your projects index

### Step 5: Test the Workflow

**See what I've been working on:**
```bash
./bin/wip team-status mba-field-guide
```

**Create your first daily log:**
```bash
./bin/wip log-project mba-field-guide
```

This will open an editor with a template. Fill it in with something like:

```markdown
# 2025-11-28 - Peter

## Completed
- [x] Set up personal Formigio WIP system
- [x] Cloned MBA Field Guide project
- [x] Reviewed project outline

## In Progress
- [ ] Thinking about chapter preferences

## Blockers
None

## Notes
- Excited to get started on this project!
- Really like the outline structure
- Have some ideas for the entrepreneurship chapter
```

When you save and exit, it will automatically commit and push to our shared repo!

## Daily Workflow

### Your Personal Accomplishment Tracking

**Each Morning:**
```bash
./bin/wip new-day
```
This creates today's file with your recurring tasks.

**During the Day:**
Work on tasks, check them off as you complete them.

**End of Day:**
Add an "End of Day Summary" section and commit:
```bash
git add .
git commit -m "Daily update: $(date +%Y-%m-%d)"
git push
```

### Our Collaborative Book Project

**Morning (when working on the book):**
```bash
# See what I did yesterday
./bin/wip sync-project mba-field-guide
./bin/wip team-status mba-field-guide
```

**During the Day:**
- Work on chapters, research, outline, etc.
- Update shared files (notes.md, outline.md)

**End of Day:**
```bash
# Log your accomplishments
./bin/wip log-project mba-field-guide
```

This automatically commits and pushes your daily log!

## Quick Reference

### Personal Commands
```bash
./bin/wip new-day                # Create today's file
./bin/wip review-yesterday       # See yesterday
./bin/wip review-projects        # Check project reviews
./bin/wip list-days 7            # List last 7 days
```

### Collaborative Project Commands
```bash
./bin/wip sync-project mba-field-guide       # Pull my updates
./bin/wip log-project mba-field-guide        # Log your work
./bin/wip team-status mba-field-guide        # See activity
./bin/wip list-embedded-projects             # List all projects
```

## Understanding the Structure

### Your Personal Files
- **`daily/YYYY-MM-DD.md`** - Your personal daily files
- **`projects/index.md`** - Your personal project tracking
- **`recurring-tasks.md`** - Your recurring tasks

### Our Shared Book Project
- **`shared/mba-field-guide/`** - Shared repo (separate git)
- **`shared/mba-field-guide/daily/peter/`** - Your book project logs
- **`shared/mba-field-guide/daily/geoff/`** - My book project logs
- **`shared/mba-field-guide/outline.md`** - Book structure
- **`shared/mba-field-guide/notes.md`** - Shared research and ideas

The beauty of this system:
- Your personal productivity is **yours** (private repo)
- Our book project is **shared** (separate git repo in shared/)
- We can see each other's daily progress on the book
- We work on our own schedules (async collaboration)

## Next Steps

1. **✅ Complete setup above** (clone, configure, test)

2. **Read the book project docs:**
   - `shared/mba-field-guide/QUICK-START.md` - Quick start for the book
   - `shared/mba-field-guide/COLLABORATION-GUIDE.md` - Detailed workflow
   - `shared/mba-field-guide/outline.md` - Book structure

3. **Add your thoughts:**
   Create your first daily log for the book project with:
   - Initial reactions to the outline
   - Which chapters interest you
   - Questions or ideas

4. **Let's discuss chapter ownership:**
   We should divide the chapters based on our strengths and interests.

## Tips for Success

1. **Use the tools daily** - The system works best with consistency
2. **Sync before you start** - Always pull my updates before working on the book
3. **Communicate through logs** - Your daily notes are how we stay aligned
4. **Commit frequently** - Don't wait days; commit at least daily
5. **Ask questions** - Add questions to your daily log notes, I'll see them

## Getting Help

- **System questions:** Check `README.md` in the root directory
- **Book project questions:** Check the guides in `shared/mba-field-guide/`
- **General questions:** Just add them to your daily log notes!

## Optional: Use Claude Code

If you want AI help with planning and task management, you can use [Claude Code](https://claude.com/claude-code):

```bash
# Morning planning
/review-day

# Prioritize tasks
/prioritize

# Create time blocks
/plan-day

# Capture meeting notes
/note-organizer
```

The system works great without Claude Code too - it's just a nice enhancement.

## Troubleshooting

**Command not found:**
```bash
chmod +x bin/accomplish
```

**Can't push to book project:**
You might need to pull first:
```bash
./bin/wip sync-project mba-field-guide
```

**Identity errors:**
Make sure `.me` file exists and contains "peter":
```bash
cd shared/mba-field-guide
cat .me  # Should show: peter
```

---

## You're All Set!

The system is ready. Your workflow is:

**Daily Personal:**
1. `./bin/wip new-day` (morning)
2. Work on tasks
3. Commit at end of day

**When Working on Book:**
1. `./bin/wip sync-project mba-field-guide` (morning)
2. Work on book
3. `./bin/wip log-project mba-field-guide` (end of day)

Let's write something great! 📚
