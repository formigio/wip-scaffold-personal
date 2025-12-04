---
name: Weekly Review
description: Generate weekly review summary
---

Help me create a weekly review using the Formigio WIP system:

## Steps to Follow:

1. **Determine Week Range**: Calculate the date range for the past week (Monday through Sunday, or custom range if specified)
2. **Gather Daily Files**: Run `./bin/wip list-days 7` to see the past week's files
3. **Read Daily Files**: Read each daily file from the past week
4. **Generate Summary**: Run `./bin/wip weekly-summary` to create the review file
5. **Analyze Patterns**: Identify:
   - Major accomplishments
   - Recurring themes or focus areas
   - Projects that got significant attention
   - Tasks that were frequently carried forward (potential blockers)
   - Wins and challenges
6. **Ask for Reflection**: Ask me:
   - Any highlights I want to emphasize?
   - Any challenges or blockers to note?
   - Goals for next week?
7. **Update Review File**: Add my reflections to the weekly review file in `reviews/`
8. **Commit**: Create a git commit with message: "Weekly review: [date range]"

## Output Format:

Present:
- Week date range
- Summary of accomplishments by day
- Key themes and patterns
- Projects worked on
- Suggested goals for next week

Then incorporate my feedback and finalize the review.

---

Let's review the past week. Should I use the default range (last 7 days) or would you like a custom date range?
