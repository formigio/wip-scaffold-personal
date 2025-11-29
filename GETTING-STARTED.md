# Getting Started with Formigio WIP

Welcome to **Formigio WIP** (Work In Progress) - an AI-powered personal assistant system built for Claude Code.

## What This Is

**Formigio WIP is a Claude Code-first productivity system.** It gives Claude Code a structured workspace to help you:
- Plan your days and prioritize work
- Track daily accomplishments
- Manage projects and deadlines
- Collaborate asynchronously with teammates
- Keep everything organized automatically

**You work with Claude in natural language. Claude manages the files.** The system uses markdown files and git for simplicity, but you rarely interact with them directly - Claude does that for you.

## Prerequisites

1. **[Claude Code](https://claude.com/code)** - Required (this is built for Claude)
2. **Git** - For version control
3. **Text editor** - Optional (for when you want to write directly)

## Quick Setup (5 minutes with Claude's Help)

### Step 1: Clone and Set Up

Open Claude Code and say:

> "Clone the Formigio WIP scaffold from https://github.com/formigio/wip-scaffold-personal into ~/my-wip and set it up for me"

Claude will:
- Clone the repository
- Make CLI tools executable
- Show you the structure

### Step 2: Customize Recurring Tasks

Tell Claude about your routine:

> "Help me set up my recurring tasks. Daily I want to check email and review projects. On Mondays I do weekly planning. On Fridays I do weekly reviews."

Claude will:
- Update `recurring-tasks.md` with your schedule
- Explain how it works
- Save the changes

### Step 3: Start Today

Simply say:

> "Start today's daily file"

Claude creates your first daily file with today's recurring tasks ready to go.

## Daily Workflow with Claude

### Morning Planning

**Just ask Claude to help:**

> "Help me plan my day"

Or use the specialized agent:

> "/review-day"

Claude will:
- Review what you did yesterday
- Check your recurring tasks for today
- Identify projects due for review
- Help you set priorities
- Create your daily plan

### During the Day

**Work naturally and tell Claude what you're doing:**

> "I just finished the quarterly report. Mark that task complete and add a note that I sent it to Sarah for review."

> "I had a great idea for the marketing campaign - capture this..."

Claude handles all the file updates, formatting, and organization.

### End of Day

**Tell Claude what you accomplished:**

> "Wrapping up for the day. I finished the report, had two client meetings, and made progress on the website redesign."

Claude will:
- Update your daily file with accomplishments
- Create an end-of-day summary
- Mark tasks complete
- Commit everything to git

## Working with Team WIPs

### Joining a Team WIP

When someone shares a collaborative project with you:

> "Clone the team project from [URL]. My username for this project is '[your-username]'"

Claude uses `./bin/wip clone-project` behind the scenes.

### Daily Team Collaboration

**Morning - see what teammates did:**

> "What did the team work on yesterday in [project-name]?"

**During the day - work on the project:**

> "Add my research notes about [topic] to the [project-name] shared notes"

**End of day - log your contributions:**

> "Log to [project-name]: I reviewed the proposal, added feedback to section 3, and updated the timeline"

Claude handles sync, file management, and commits automatically.

## Example Conversations

**Starting your day:**
> You: "Good morning Claude, help me get started"
>
> Claude: "Good morning! Let me check yesterday and today's schedule...
>
> Yesterday you completed 4 of 6 tasks. Your project X is due for weekly review. Today you have 3 recurring tasks and 2 carryover items.
>
> I recommend focusing on:
> 1. Project X review (30 min)
> 2. Finishing the proposal from yesterday
> 3. Your 2pm client meeting prep
>
> Shall I create today's file with this plan?"

**Capturing notes from a meeting:**
> You: "I just met with the design team. They want a card-based layout, dark mode support, and mobile-first approach. Analytics integration is required by Q2 end. Capture this."
>
> Claude: "I'll add this to your daily notes and create a project note... Done! I've:
> - Added meeting notes to today's daily file
> - Created a design-project note with requirements
> - Added Q2 deadline to your project tracking
>
> Would you like me to break this into tasks?"

**Checking team progress:**
> You: "What's the status of the book project?"
>
> Claude: "Let me check the team activity...
>
> Last 3 days in book-project:
> - Sarah: Drafted Chapter 3, added outline for Chapter 4
> - Mike: Reviewed Chapter 1 and 2, provided feedback
> - You: Outlined Chapter 5 (yesterday)
>
> Sarah mentioned she's blocked on Chapter 4 - waiting for your feedback on the entrepreneurship section."

## The Structure (Claude Manages This)

You don't need to memorize this - Claude knows it. But for reference:

```
my-wip/
├── daily/               # Claude creates these daily
├── shared/              # Team WIPs Claude manages
├── projects/index.md    # Claude tracks your projects
├── recurring-tasks.md   # Your routine (you defined with Claude)
└── CLAUDE.md           # Teaches Claude how this works
```

## CLI Commands (For Claude's Use)

These exist for Claude to use efficiently. You won't run them:

```bash
./bin/wip new-day            # Claude: create today's file
./bin/wip sync-project       # Claude: pull team updates
./bin/wip log-project        # Claude: log work to team WIP
./bin/wip team-status        # Claude: show team activity
```

When you ask Claude to do things, it uses the right commands automatically.

## Claude Code Agents

Specialized workflows you can invoke:

- **`/review-day`** - Complete morning planning workflow
- **`/prioritize`** - Analyze and prioritize your tasks
- **`/plan-day`** - Create detailed time-blocked schedule
- **`/note-organizer`** - Capture and structure meeting notes

Just type the slash command in Claude Code.

## Tips for Working with Claude

**Be conversational and natural:**
- ❌ Don't say: "Update daily/2025-11-28.md with task completion"
- ✅ Do say: "I finished the report, mark that done"

**Let Claude handle complexity:**
- ❌ Don't: Manually edit files and worry about format
- ✅ Do: "Add a note about the client feedback"

**Ask for help:**
- "What should I prioritize today?"
- "Show me my progress this week"
- "What's the team working on?"
- "Help me plan tomorrow"

**Give Claude context:**
- "I'm starting work on the new feature"
- "Meeting went well, here's what we decided..."
- "Blocked on X until Y happens"

## Real-World Usage

**Solo developer:**
> Morning: "/review-day"
>
> During day: "Mark task X complete. Add note that the API is deployed."
>
> End of day: "Done for today. Deployed the API, fixed 3 bugs, started the dashboard redesign."

**Team collaboration:**
> "Sync the design-system project and show me updates"
>
> "Log to design-system: Implemented the button component, added tests, updated docs"
>
> "What blockers does the team have?"

**Project manager:**
> "Show me the status of all my projects"
>
> "Which projects need review this week?"
>
> "Create a status report for the past week"

## Why This Works

**Claude as your AI assistant:**
- Knows the structure from CLAUDE.md
- Uses CLI tools efficiently
- Keeps everything organized
- Handles git commits automatically
- Coordinates with teammates' Claude instances

**Simple underneath:**
- Plain markdown files (portable, searchable)
- Git version control (full history, backup)
- No databases or complex tools
- Works offline
- Easy to extend

**Async collaboration:**
- Everyone works with their own Claude
- Git coordinates the work
- Daily logs show progress
- Natural async communication

## Common Workflows

**Weekly review:**
> "Show me what I accomplished this week"

**Project planning:**
> "I'm starting a new project called X. It's a [description]. Help me set it up."

**Task management:**
> "Add a task to research Y for tomorrow"
>
> "Move task Z to next Monday"

**Team coordination:**
> "Check if anyone is blocked on the API work"
>
> "Log that I reviewed Sarah's proposal and added comments"

## Getting Help

**Ask Claude!** It has access to all documentation:

> "How do I track a new project?"
>
> "Where should I add notes about X?"
>
> "Show me my tasks for this week"
>
> "How does the team WIP workflow work?"

Claude will explain and help you.

## First Steps

1. **Set up with Claude's help** (see Step 1-3 above)

2. **Use it for a week:**
   - Morning: "Help me plan my day"
   - During: Tell Claude what you're doing
   - Evening: "Here's what I accomplished..."

3. **Customize as needed:**
   - Adjust recurring tasks
   - Add your projects
   - Set up team WIPs if collaborating

4. **Explore agents:**
   - Try `/review-day` for morning planning
   - Try `/note-organizer` after meetings
   - Try `/prioritize` when overwhelmed

## Advanced Usage

Once comfortable, explore:
- **Weekly/monthly reviews** with Claude's help
- **Status reports** for team leadership
- **Custom recurring tasks** for your workflow
- **Multiple team WIPs** for different collaborations
- **Project templates** for repeating work

## The Philosophy

**You focus on the work. Claude handles the system.**

This isn't about learning commands or file formats. It's about having an AI assistant that:
- Remembers what you did
- Helps you plan what's next
- Keeps you organized
- Coordinates with teammates
- Lets you think in natural language

The system is designed to be invisible - you just talk to Claude like a personal assistant, and everything stays organized automatically.

## Why Formigio WIP?

**Traditional task managers:** You adapt to the tool
**Formigio WIP:** Claude adapts to you

- No rigid workflows
- No complex UI to learn
- No vendor lock-in
- Just natural conversation
- Files you can read anywhere
- Git you already know

## Support & Community

- **Documentation:** CLAUDE.md explains everything to Claude
- **README.md:** System overview
- **Issues:** [GitHub Issues](https://github.com/formigio/wip-scaffold-personal/issues)
- **Community:** Share workflows and learn from others

---

**Ready to get started?**

Open Claude Code and say:

> "Help me set up Formigio WIP from the getting started guide"

Claude will take it from there! 🚀
