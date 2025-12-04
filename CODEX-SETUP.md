# Using Formigio WIP with OpenAI Codex

This guide explains how to use the Formigio WIP productivity system with OpenAI Codex CLI.

## Quick Start

1. **Install Codex** (if not already installed):
   ```bash
   npm i -g @openai/codex
   # or
   brew install --cask codex
   ```

2. **Install custom prompts**:
   ```bash
   # Copy the WIP workflow prompts to Codex prompts directory
   cp -r .codex/prompts/* ~/.codex/prompts/
   ```

3. **Configure Codex** for WIP:
   ```bash
   # Append recommended settings to your Codex config
   cat .codex-config.toml >> ~/.codex/config.toml
   ```

4. **Launch Codex** in your WIP directory:
   ```bash
   cd ~/my-wip
   codex
   ```

5. **Try a workflow**:
   ```
   /prompts:review-day
   ```

## What's Been Set Up

### ✅ AGENTS.md
Codex will automatically read `AGENTS.md` when it starts in this directory. This file contains all the instructions for managing your WIP system.

### ✅ Custom Slash Commands
Four workflow prompts are included in `.codex/prompts/` (copy to `~/.codex/prompts/` during setup):

- **`/prompts:review-day`** - Review yesterday and plan today
- **`/prompts:end-day`** - Create end-of-day summary and commit
- **`/prompts:project-update`** - Update project status and next steps
- **`/prompts:weekly-review`** - Generate weekly review summary

### ✅ Configuration Template
The `.codex-config.toml` file contains recommended Codex settings for the WIP system. You can append it to `~/.codex/config.toml` or manually copy the settings you want.

### ✅ All Existing Tools
All the bash scripts in `bin/wip` work unchanged:
- `./bin/wip new-day`
- `./bin/wip review-yesterday`
- `./bin/wip review-projects`
- `./bin/wip weekly-summary`
- And all other commands...

## Daily Workflow with Codex

### Morning Planning

**Option 1 - Use slash command:**
```
/prompts:review-day
```

**Option 2 - Natural language:**
```
Help me plan my day
```

Codex will:
1. Review yesterday's work
2. Check recurring tasks for today
3. Identify projects due for review
4. Create a prioritized task list
5. Update today's daily file

### During the Day

Just talk naturally to Codex:

```
Add a task: Research soil moisture sensor options
```

```
Mark "Write project proposal" as complete
```

```
Add a note that the client wants dark mode support
```

### End of Day

**Option 1 - Use slash command:**
```
/prompts:end-day
```

**Option 2 - Natural language:**
```
I'm done for the day. I completed:
- Finished the proposal
- Reviewed sensor options
- Met with the design team
```

Codex will:
1. Mark tasks complete
2. Create end-of-day summary
3. Update Team WIP logs (if applicable)
4. Commit and push changes

## Project Management

### Update Project Status
```
/prompts:project-update
```

### Review Projects Due Today
```
What projects are due for review today?
```

### Add New Project
```
Add a new project called "Mobile App Redesign"
```

## Weekly/Monthly Reviews

### Weekly Review
```
/prompts:weekly-review
```

### Monthly Review
```
Help me create a monthly review for November
```

## Built-in Codex Commands

Useful Codex TUI commands:

- **`/model`** - Switch between models (e.g., GPT-4 vs GPT-4o-mini)
- **`/approvals`** - Change approval mode (auto/write/read/ask)
- **`/status`** - Check current model, approval mode, and token usage
- **`/help`** - Show all available commands

## Configuration Options

The `.codex-config.toml` file includes several settings you can customize:

### Model Selection
```toml
default_model = "gpt-4o"  # Use gpt-4o-mini for faster/cheaper responses
```

### Approval Mode
```toml
approval_mode = "write"   # Options: auto, write, read, ask
```
- **auto**: Fastest, Codex runs everything automatically
- **write**: Codex asks before writing files or running commands
- **read**: Codex asks before any file operations
- **ask**: Codex asks before every action

### Reasoning Effort
```toml
default_reasoning_effort = "medium"  # Options: low, medium, high
```
Higher reasoning = better planning but slower responses

## Using Both Claude Code and Codex

This repository now supports **both** Claude Code and Codex:

- **CLAUDE.md** - Instructions for Claude Code (original)
- **AGENTS.md** - Instructions for Codex (new)
- **Both files** contain the same WIP system instructions
- **All bash scripts** work with both
- **File formats** are identical

You can switch between them freely based on your needs:
- Use Claude Code for interactive planning sessions
- Use Codex for quick updates and automation
- Both maintain the same file structure

## Troubleshooting

### Codex doesn't see AGENTS.md
Make sure you're running `codex` from the `/Users/peter/my-wip` directory.

### Slash commands don't show up
Check that the prompts were created:
```bash
ls ~/.codex/prompts/
```
You should see: `review-day.md`, `end-day.md`, `project-update.md`, `weekly-review.md`

### Config changes don't apply
Restart Codex after changing `~/.codex/config.toml`:
1. Exit Codex (Ctrl+C or type `/exit`)
2. Restart: `codex`

### Codex asks for approval too often
Change approval mode:
```toml
approval_mode = "auto"  # In ~/.codex/config.toml
```
Or in the TUI: `/approvals` → select "Auto"

## Advanced Usage

### Non-Interactive Mode
Run Codex commands from scripts:
```bash
codex exec "Help me plan my day" | tee plan.txt
```

### Scheduled Daily Planning
Add to your crontab for automatic morning planning:
```bash
0 8 * * 1-5 cd ~/my-wip && codex exec "$(cat ~/.codex/prompts/review-day.md)"
```

### GitHub Actions Integration
Use Codex in CI/CD:
```yaml
- uses: openai/codex-action@v1
  with:
    prompt: "Update project status based on merged PRs"
```

## Resources

- **Codex Documentation**: https://developers.openai.com/codex/cli/
- **AGENTS.md Guide**: https://developers.openai.com/codex/guides/agents-md/
- **Slash Commands**: https://developers.openai.com/codex/guides/slash-commands/
- **Codex GitHub**: https://github.com/openai/codex
- **WIP System (CLAUDE.md)**: See original instructions in this repo

## Getting Help

### For Codex Issues
- GitHub Issues: https://github.com/openai/codex/issues
- Documentation: https://developers.openai.com/codex/

### For WIP System Questions
See `CLAUDE.md` or `GETTING-STARTED.md` for detailed workflow documentation.

---

**You're all set!** Launch Codex in this directory and try `/prompts:review-day` to get started.
