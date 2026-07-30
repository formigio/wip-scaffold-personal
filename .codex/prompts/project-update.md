---
name: Project Update
description: Update project status, next steps, and review date
---

Help me update a project in the Formigio WIP system:

## Steps to Follow:

1. **List Projects**: Show me the current projects from the `projects/index.md` summary table
2. **Select Project**: Ask which project I want to update
3. **Show Current State**: Read `projects/[project-name]/status.md` and display the project's current:
   - Status (Active/Paused/Completed)
   - Review Cadence
   - Last Reviewed date
   - Remaining Estimate
   - Next Steps (checkbox list)
4. **Gather Updates**: Ask me:
   - What next steps have been completed?
   - What new next steps should be added?
   - Has the status changed?
   - Should the estimate be updated?
   - Any notes to add to the project's notes.md file?
5. **Update Files**:
   - Update `projects/[project-name]/status.md` with the changes and today's "Last Reviewed" date
   - Add a dated entry under "Recent Updates" in status.md
   - Update the `projects/index.md` table row if status or cadence changed
   - If there are extended notes, update `projects/[project-name]/notes.md`
6. **Commit**: Create a git commit with message: "Update [project name]: [brief summary of changes]"

## Output Format:

After gathering information, show me:
- The updated project entry
- What will be added to notes (if applicable)
- The commit message

Then ask for confirmation before updating and committing.

---

Which project would you like to update?
