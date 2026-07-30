---
name: Review Day
description: Review yesterday and plan today with WIP system
---

Help me plan my day using the Formigio WIP system:

## Steps to Follow:

1. **Review Backlog First**: Read `backlog.md` for the full picture of pending work — decisions needed, behind-schedule reviews, communication owed, aged items
2. **Catch Dropped Tasks**: Run `./bin/wip list-days 5` and read recent days; if any incomplete task never completed, carried forward, or landed in backlog, add it to `backlog.md`
3. **Check Recurring Tasks**: Look at `recurring-tasks.md` and identify which tasks apply to today based on the day of week
4. **Review Projects**: Run `./bin/wip review-projects` to identify projects due for review (scans each project's `status.md`)
5. **Sync Team WIPs**: If there are any shared projects in `shared/`, sync them to see teammate updates
6. **Assess Available Time**: Ask me about meetings/commitments to determine realistic capacity today
7. **Create Today's File**: Run `./bin/wip new-day`, then pull realistic items from `backlog.md` into it based on available time

## Output Format:

After gathering all the context, present:
- Backlog summary (key waiting items, any urgent decisions)
- ⚠️ Dropped tasks found and added to backlog (if any)
- Projects due for review today
- Available time assessment
- Today's realistic plan (what's committed) vs. deferred to backlog (what won't fit, and why)

Then ask me if there are any additional tasks or adjustments needed before finalizing today's daily file.

---

Start by running the review commands and gathering context.
