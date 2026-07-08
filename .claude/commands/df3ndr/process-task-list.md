---
description: Execute a task list one task at a time, enforcing backup / confirm / verify / record safety gates.
argument-hint: [path to tasks-*.md]
---

# Process a task list

Drive execution of a `tasks-e<m>-<slug>.md` task list (in its epic directory
`…/Milestone-NN/Epic-MM/`, or `project/tasks/` for a one-off). Work through it
deliberately — one sub-task at a time — keeping the file in sync and honoring the
safety conventions in `CLAUDE.md` at every step. Treat changes as if they hit a live
system: a wrong move can break something users depend on.

Task list to process:

> $ARGUMENTS

If empty, find the active `tasks-e<m>-<slug>.md` (under `…/Milestone-NN/Epic-MM/` or
`project/tasks/`) and confirm which one to run.

## Before you start

1. Read the task list and its companion `prd-e<m>-<slug>.md` (same directory) — and the
   epic's `overview/e<m>-<slug>.md` if present — so you know the goal, scope, and blast radius.
2. Identify the **next unchecked sub-task** and state which one you're about to do.
3. Confirm you're on the working branch (task 0.x), not `main`.

## Execution protocol (per sub-task)

1. **Respect the safety gates before acting:**
   - **Backup before risk** — if the sub-task is risky/hard-to-reverse, ensure a
     backup or snapshot exists and succeeded first.
   - **Confirm hard-to-reverse or outward-facing actions** with the user before
     doing them: deleting/overwriting data, restarting production services,
     network/DNS/access-control changes, anything touching users. Approval for one
     step does **not** carry to the next.
   - **Prefer reversible actions** (graceful reload, rolling restart) over
     destructive ones.
   - **Stay inside your granted privileges.** If a step needs elevated privileges or
     touches sensitive resources (credentials, keys, certificates, production data,
     infrastructure config), **STOP** and ask the human for approval; never widen
     your own privilege to route around the gate.
   - **Read before you delete/overwrite.** If what you find contradicts how it was
     described, surface that and pause instead of proceeding.
2. **Do the sub-task.**
3. **Mark it complete** — change `[ ]` to `[x]` in the task file immediately, and
   keep the **Relevant Files & Resources** section accurate (add anything you
   created or changed, with a one-line note).
4. **Report faithfully** — if a step failed, was skipped, or did something
   unexpected, say so with the evidence (command output), don't paper over it.

## When all sub-tasks under a parent task are `[x]`

Follow this sequence:

1. **Validate** — run the validation / health checks for this change (the read-only
   checks from the plan: a request/probe, a status command, a service listing, a
   re-scan, a metric). Paste the evidence. Treat this as the "tests" gate.
2. **Only if validation passes:** stage changes — but stage **only repo files**
   (`project/`, docs, config, the task list). Never stage or commit secrets or
   credentials.
3. **Clean up** any temporary files or scratch config left behind.
4. **Record the change** — append to the epic's `…/Milestone-NN/Epic-MM/CHANGELOG.md`
   and update the relevant component/service notes.
5. **Commit** with a Conventional Commit message, formatted as one command with
   `-m` flags, that summarizes the parent task, lists key changes, and references
   the task/PRD:

   ```
   git commit -m "ops: restrict admin endpoint access" -m "- Limit admin port to the internal network" -m "- Disable password auth; key-only" -m "- Validated: external probe shows the port filtered" -m "Task 2.0 in tasks-e2-access-hardening.md"
   ```

   Remember the trailer required for commits in this environment:

   ```
   Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>
   ```
6. **Mark the parent task `[x]`** and continue to the next parent task.

## Task list maintenance

- Update the task file as you go — checkboxes and the Relevant Files section.
- Add newly discovered tasks/sub-tasks as they emerge (e.g. an unexpected dependency
  on another component).
- Before each step, re-check which sub-task is next; after each, update the file and
  continue.

## Reminders

- Never print, copy, log, or commit secrets, credentials, keys, or tokens.
- Do not touch protected/sensitive resources without explicit human approval:
  privilege/access-control config, host or signing keys, production databases and
  app data, TLS/certificate material, and no destructive infrastructure actions
  (delete/resize/power-off) or DNS changes.
