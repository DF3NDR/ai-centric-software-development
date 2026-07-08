---
description: Turn a Change Plan (PRD) into a step-by-step, safety-gated task list.
argument-hint: [path to prd-*.md, or a description of the change]
---

# Generate a task list from a Change Plan

Create a detailed, ordered task list — in Markdown — that walks an operator through
executing a piece of work (a feature, change, hardening, migration, or operational
task) for the project described in `CLAUDE.md`. The task list is the execution
checklist for a Change Plan (PRD); it bakes in this project's safety conventions so
safeguard steps aren't an afterthought.

Input:

> $ARGUMENTS

Resolve the input as follows:
- If it points to a Change Plan (`…/Milestone-NN/Epic-MM/prd-e<m>-<slug>.md`, or a one-off
  `project/tasks/prd-*.md`), read that plan and build from it.
- If it's a free-text description, work from that (and offer to run `/create-prd`
  first if the request is non-trivial and under-specified).
- If empty, ask which Change Plan or task to break down.

## Output

- **Format:** Markdown (`.md`)
- **Location:** the **same directory as the PRD** —
  `project/<Area>/<project-name>/Milestone-NN/Epic-MM/` (fallback for one-offs: `project/tasks/`).
- **Filename:** `tasks-e<m>-<slug>.md` (match the PRD's epic number + slug, e.g.
  `tasks-e1-iac-bootstrap.md`). One-off fallback: `tasks-<slug>.md`.

## Process

1. **Receive the plan / request** (resolved as above).
2. **Analyze it** — affected components/services, blast radius, reversibility, and
   what "done" means. Read any relevant component, service, or environment notes the
   project keeps so tasks reference real config.
3. **Phase 1 — parent tasks.** Create the file and generate the high-level tasks.
   **Always start with task 0.0 "Prepare & safeguard"** (branch + backup/snapshot if the
   change is risky) unless the user says otherwise. Use judgement on the rest —
   usually ~5 parent tasks. End the plan with an explicit **validation** task and a
   **record the change** task.
4. **Phase 2 — sub-tasks.** Break each parent task into concrete, actionable
   sub-tasks. Make safety and verification explicit: backup-before-risk,
   confirm-before-hard-to-reverse, run the change reversibly, then verify. Call out
   any step that needs **elevated privileges or touches sensitive resources**
   (credentials, keys, certificates, production data, infrastructure config) — that's
   a STOP-and-ask-for-approval step, not something to route around.
5. **Identify relevant files & resources.** List the files, configs, services, and
   resources that will be created or changed, each with a one-line note.
6. **Generate the final output** in the structure below.
7. **Save** beside the PRD as
   `project/<Area>/<project-name>/Milestone-NN/Epic-MM/tasks-e<m>-<slug>.md` (one-off
   fallback: `project/tasks/tasks-<slug>.md`).

## Output format

```markdown
## Relevant Files & Resources

- `…/Milestone-NN/Epic-MM/prd-e<m>-<slug>.md` - The Change Plan this task list executes.
- `…/Milestone-NN/Epic-MM/overview/e<m>-<slug>.md` - The epic overview both docs expand.
- `path/to/config.file` - Config file to be edited.
- Service / container `<name>` - restarted as part of the change.
- `path/to/component-notes.md` - notes to update after the change.
- `…/Milestone-NN/Epic-MM/CHANGELOG.md` - epic change log to append.

### Notes

- Prefer reversible actions (graceful reload, rolling restart) over destructive ones.
- Take a backup or snapshot before any risky step and confirm it succeeded.
- Validation commands are read-only health checks (e.g. a request/probe, a status
  command, a service listing) — list the exact command per check.

## Tasks

- [ ] 0.0 Prepare & safeguard
  - [ ] 0.1 Create and checkout a working branch (e.g. `git checkout -b ops/[slug]`)
  - [ ] 0.2 If the change is risky, take a backup or snapshot of the affected resource(s) and confirm success
  - [ ] 0.3 Capture a pre-change baseline (service status / config / metric) to compare against later
- [ ] 1.0 Parent Task Title
  - [ ] 1.1 [Sub-task]
  - [ ] 1.2 [Sub-task]
- [ ] 2.0 Parent Task Title
  - [ ] 2.1 [Sub-task]
- [ ] 3.0 Validate the change
  - [ ] 3.1 Run the validation checks from the plan and record the results
- [ ] 4.0 Record the change
  - [ ] 4.1 Append what changed to the epic's `…/Milestone-NN/Epic-MM/CHANGELOG.md` and update the relevant component/service notes
```

## Interaction model

Generate the parent tasks and sub-tasks in one pass — no confirmation pause. Mirror
the PRD's scope exactly — don't quietly widen it.

## Instructions for completing tasks

As tasks are executed, they get checked off in this file by changing `- [ ]` to
`- [x]`, one sub-task at a time. Execution itself is driven by `/process-task-list`,
which enforces the backup / confirm / verify / record protocol.
