# Task Table preset for Spec Kit

Adds a human-readable **Task Table** to the end of every `plan.md` produced by `/speckit.plan`.

| Task Name | Est. Hours | When Complete | Sub-tasks |
|-----------|------------|---------------|-----------|
| Zip file upload | | Able to upload a zip file | Build the upload form<br>Check the file type and size<br>Store the uploaded file |
| Upload history | | Able to see a list of previous uploads | Record each upload<br>Build the history page |

- **Task Name** — plain-language name, no requirement codes (FR-001, DR-002, ...).
- **Est. Hours** — always left empty by the AI assistant; you fill it in. Values you enter are kept when the plan is re-run.
- **When Complete** — the outcome a user can see or do, phrased as "Able to ...".
- **Sub-tasks** — the activities needed to complete the task.

## Install

Requires Spec Kit 0.8.0 or later.

```bash
specify preset add --from https://github.com/leejsinclair/speckit-tasks-table/archive/refs/tags/v1.0.0.zip
```

or, from a local checkout:

```bash
specify preset add --dev /path/to/speckit-tasks-table
```

Check that it is applied:

```bash
specify preset resolve plan-template
```

Then run `/speckit.plan` as usual. Plans created before the preset was installed get the table added the next time `/speckit.plan` is run on them.

To uninstall:

```bash
specify preset remove task-table
```

## How it works

The preset uses the `append` composition strategy, so it adds to the plan template and plan command rather than replacing them. It stacks with other presets and keeps picking up Spec Kit's own updates to both.

| File | Appended to | Purpose |
|------|-------------|---------|
| `templates/plan-task-table.md` | `plan-template` | The Task Table section and example rows |
| `commands/speckit.plan.task-table.md` | `speckit.plan` | Rules the AI assistant follows to fill the table in |

To change the columns or the wording rules, edit both files, then reinstall with `specify preset remove task-table` followed by `specify preset add --dev .`.

## Releasing

Each version tag is its own installable zip; GitHub builds it from the tag, so there is no build step.

1. Set the new version in `preset.yml`, the install URL above, and `CHANGELOG.md`.
2. Commit, then tag and push:

   ```bash
   git tag v1.0.1
   git push origin main v1.0.1
   ```

The zip is then available at `https://github.com/leejsinclair/speckit-tasks-table/archive/refs/tags/v1.0.1.zip`.
