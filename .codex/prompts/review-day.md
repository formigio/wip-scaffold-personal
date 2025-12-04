---
name: Review Day
description: Review yesterday and plan today with WIP system
---

Help me plan my day using the Formigio WIP system:

## Steps to Follow:

1. **Review Yesterday**: Run `./bin/wip review-yesterday` to see what I worked on
2. **Check Recurring Tasks**: Look at `recurring-tasks.md` and identify which tasks apply to today based on the day of week
3. **Review Projects**: Run `./bin/wip review-projects` to identify projects that are due for review based on their cadence and last reviewed date
4. **Sync Team WIPs**: If there are any shared projects in `shared/`, sync them to see teammate updates
5. **Create Today's File**: Run `./bin/wip new-day` to create today's daily file with recurring tasks
6. **Prioritize**: Create a prioritized task list based on:
   - Incomplete tasks from yesterday (if still relevant)
   - Today's recurring tasks
   - Projects due for review
   - Any additional context I provide

## Output Format:

After gathering all the context, present:
- Summary of yesterday's accomplishments
- List of projects due for review today
- Recommended focus areas for today
- Prioritized task order

Then ask me if there are any additional tasks or adjustments needed before updating today's daily file.

---

Start by running the review commands and gathering context.
