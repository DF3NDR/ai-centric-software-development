---
description: Break a milestone out of the project plan into its own directory + detailed milestone overview, and reconcile the plan above it.
argument-hint: [milestone id (e.g. M1) or the project-plan path — defaults to the next un-broken-out milestone]
---

# Break out a milestone

Take one **milestone** from a project plan and expand it into its own subdirectory with
a detailed **milestone overview** document — adding the depth the one-line plan entry
can't hold, including a full treatment of every epic in that milestone. Each run also
**reviews the parent project plan and updates it** if expansion revealed anything that
should change above this level.

Pipeline position:

```
/create-project-plan → [/breakout-milestone] → /breakout-epics → /create-prd → /generate-tasks → /process-task-list
```

This command produces **planning documents only** — do not implement anything.

Which milestone to break out:

> $ARGUMENTS

Resolve the input as follows:
- A milestone id (e.g. `M1`) → break out that milestone.
- A project-plan path → use that plan; default to the **next milestone not yet broken
  out** (the lowest `M<n>` with no `Milestone-NN/overview/` doc).
- Empty → find the project plan under `project/**/*-project-plan.md`; if more than one,
  ask which. Then default to the next un-broken-out milestone and confirm.

## Process

1. **Read the source of truth.** Read the `<project-name>-project-plan.md` (and the
   companion `<project-name>-architecture.md` if present) in full — especially this
   milestone's goal, exit criteria, epic table, dependencies, and rollback posture.
   Also read `CLAUDE.md` and any directly relevant existing material so the detail is real.
2. **Reconcile upward first.** Before writing, check whether deeper thought about this
   milestone exposes anything wrong or missing in the **project plan** — a misordered
   dependency, a missing epic, a wrong owner, an exit criterion that won't hold. If so:
   - Make the **minimal, surgical edit** to the project plan to fix it, and
   - **Note the change** to the user explicitly (what changed and why). Don't silently
     diverge from the plan; keep the two documents consistent.
3. **Create the milestone directory and overview** per the structure below.
4. **Expand every epic** in this milestone to overview depth *inside the milestone doc*
   (the per-epic breakout into separate epic dirs is the next command, `/breakout-epics`).
5. **Report** what you created, any upward edits, and point to `/breakout-epics`.

## Directory & naming (match the existing `professionalization/` tree)

- **Milestone directory:** `Milestone-NN/` where `NN` is the `M<n>` id zero-padded
  (`M0`→`Milestone-00`, `M1`→`Milestone-01`).
- **Overview file:** `Milestone-NN/overview/milestone-<H>-<Title-Kebab>.md`, where `<H>`
  is the **1-based human milestone number** (`M0`→`milestone-01`, `M1`→`milestone-02`)
  and the H1 title reads "Milestone H — <Title> (M<n>)".
- **Epic subdirectories:** create an empty `Epic-MM/overview/` for each epic in this
  milestone (`M<n>-E1`→`Epic-01/overview/`) so `/breakout-epics` has a home to fill.

```
project/<Area>/<project-name>/
├── <project-name>-project-plan.md
└── Milestone-01/                       ← e.g. breaking out M1
    ├── overview/
    │   └── milestone-02-<Title>.md      ← THIS command
    ├── Epic-01/overview/                ← created empty; /breakout-epics fills it
    ├── Epic-02/overview/
    └── …
```

## Milestone overview structure

Generate a Markdown document with these sections (carry over and *deepen* the plan;
don't merely copy the one-liners):

1. **Header block** — "Milestone H — <Title> (M<n>)"; a **Maps to** line linking the
   `<project-name>-project-plan.md` entry (relative path) and the architecture phase if
   any; **Status**; **Prod/impact**; author + date. Include an **Epic breakouts** line
   with relative links to each `../Epic-MM/overview/e<m>-<slug>.md` (these resolve once
   `/breakout-epics` runs).
2. **Why this milestone exists** — the rationale and its position on the critical path.
3. **Goal & exit criteria** — the goal, then exit criteria as a concrete `- [ ]` checklist.
4. **Scope** — explicit **in scope** and **out of scope (deferred)** lists.
5. **Roles on this milestone** — who (owner vs agent vs others) does what; make
   owner-only/outside work explicit and **blocking**.
6. **Epics** — a table `Epic | Title | Owner | Impact | Breakout`, where Breakout links
   the (future) epic overview doc. Then, for each epic, a short paragraph deepening its
   summary, acceptance shape, and key tasks/risks — enough that `/breakout-epics` has a
   running start.
7. **Dependencies & sequencing** — upstream, internal epic ordering, carried-over owner
   gates, and downstream consumers.
8. **Rollback posture** — the milestone's rollback lever (from the plan, expanded).
9. **Risks (milestone-scoped)** — `Risk | Mitigation`.
10. **Definition of Done for Milestone H (M<n>)** — when this milestone is closeable.

## Output

- **Format:** Markdown (`.md`)
- **Location:** `project/<Area>/<project-name>/Milestone-NN/overview/`
- **Filename:** `milestone-<H>-<Title-Kebab>.md`
- **Also:** create empty `Epic-MM/overview/` dirs for the milestone's epics; possibly a
  reconciling edit to `<project-name>-project-plan.md`.

## Final instructions

1. **Planning only** — produce documents; implement nothing.
2. Keep the milestone doc and the project plan **mutually consistent**; whenever you
   change the plan, say so explicitly.
3. Don't widen or invent scope beyond the plan's milestone — deepen it, don't redefine it.
4. When done, point the user to `/breakout-epics` to expand this milestone's epics into
   their own directories.
