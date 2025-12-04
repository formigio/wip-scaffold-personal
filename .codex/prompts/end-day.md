---
name: End Day
description: Create end-of-day summary and commit changes
---

Help me close out my work day using the Formigio WIP system:

## Steps to Follow:

1. **Review Today's File**: Read today's daily file at `daily/[today's date].md`
2. **Ask for Accomplishments**: Ask me what I accomplished today
3. **Update Tasks**: Mark completed tasks with `[x]` based on what I tell you
4. **Create Summary**: Add an "End of Day Summary" section with:
   - **Completed Today** (list with ✅ emoji)
   - **Carried Forward** (incomplete tasks that are still relevant)
   - **Key Updates** (important notes or insights from today)
5. **Update Team WIPs**: If I worked on any shared projects today, use `./bin/wip log-project <name>` to update my daily log
6. **Commit Changes**: Create a git commit with message format: "Daily update: YYYY-MM-DD"
7. **Push**: Push the changes to the remote repository

## Output Format:

After creating the summary, show me:
- What was completed
- What's being carried forward
- The commit message you'll use

Then ask for confirmation before committing and pushing.

---

Let me tell you what I accomplished today:
