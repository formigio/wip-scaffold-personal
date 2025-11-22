# Recurring Tasks

This file defines tasks that automatically appear on specific days.

## Daily Tasks

- [ ] Review email and respond to urgent items
- [ ] Update project status

## Monday Tasks

- [ ] Weekly team sync
- [ ] Review weekly goals

## Tuesday Tasks

- [ ] One-on-one meetings
- [ ] Review project milestones

## Wednesday Tasks

- [ ] Mid-week progress check

## Thursday Tasks

- [ ] Prepare for Friday deliverables

## Friday Tasks

- [ ] Weekly review and planning
- [ ] Submit timesheets

---

## Format Guide

Tasks are organized by frequency:
- **Daily Tasks** - Appear every day
- **Monday/Tuesday/Wednesday/Thursday/Friday Tasks** - Appear on specific weekdays
- **Weekend Tasks** - Appear on Saturday/Sunday
- **Monthly Tasks** - Appear on the 1st of each month
- **First Monday** - Appear on the first Monday of each month
- **Last Friday** - Appear on the last Friday of each month

Use standard markdown checkbox format: `- [ ] Task description`

To disable a recurring task temporarily, comment it out with `<!-- -->`:
```markdown
<!-- - [ ] Temporarily disabled task -->
```

To add context or reminders, use sub-bullets:
```markdown
- [ ] Main recurring task
  - Note: Remember to check X before doing Y
```
