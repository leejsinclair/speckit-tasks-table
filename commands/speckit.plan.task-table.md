## Filling in the Task Table

This section is part of the plan workflow. Complete it after Phase 1 design and **before** the post-execution hooks and Completion Report.

Fill in the `## Task Table` section of IMPL_PLAN. If IMPL_PLAN has no such section (for example, the plan was created before this section existed), add it at the end of the file with this header:

```markdown
## Task Table

| Task Name | Est. Hours | When Complete | Sub-tasks |
|-----------|------------|---------------|-----------|
```

Add one row per task, in the order the work would sensibly be done. A task is a piece of work that delivers something a user can see or do; derive the tasks from the user stories in FEATURE_SPEC and the design produced in this plan.

Column rules:

- **Task Name**: A short, plain-language name a non-technical stakeholder would understand (e.g., "Zip file upload").
- **Est. Hours**: **Always leave this cell empty.** Estimates are entered by a person. Do not write a number, a range, a guess, "TBD", or any placeholder. If the cell already contains a value, a person put it there: keep it exactly as it is.
- **When Complete**: The user-facing outcome that shows the task is done, phrased as "Able to ..." (e.g., "Able to upload a zip file"). Describe what a user can do or see, not what was built: write "Able to sign in with an email address", not "Auth endpoint implemented". For work with no direct user-facing result (such as project setup), state the outcome for whoever benefits from it (e.g., "Able to run the app locally").
- **Sub-tasks**: The activities needed to complete the task, each a short verb phrase, separated by `<br>` inside the cell (e.g., `Build the upload form<br>Check the file type and size<br>Store the uploaded file`).

Readability rules:

- Do not use requirement or tracking codes (FR-001, DR-002, NFR-003, SC-004, US1, T012, and similar) in Task Name or When Complete. Say what the code refers to in plain words instead.
- Avoid those codes in Sub-tasks as well; use one only when there is no reasonable plain-language way to say it.
- Remove the example rows and the HTML comment that came with the template.

If the table already has rows (the plan is being re-run), update it rather than starting again: keep existing rows and their Est. Hours values, and only add, reword, or remove rows where the spec or design has changed.

Mention the Task Table in the Completion Report, and remind the user that the Est. Hours column is theirs to fill in.
