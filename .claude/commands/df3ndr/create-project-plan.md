---
description: Turn a project discussion into a professional, milestone-and-epic project plan (the front of the planning pipeline, before /breakout-milestone).
argument-hint: <the project idea, goal, or problem to plan — or a path to discussion notes>
---

# Create a professional project plan

You are turning an early-stage **discussion** about a software-engineering project
(product, platform, infrastructure/ops, security, migration — anything) into a
**professional project plan**: a durable plan-of-record decomposed into **milestones**
and **epics** that later commands explode into milestone overviews, epic overviews,
PRDs, task lists, and execution.

This is the **front of the planning pipeline**:

```
/create-project-plan → /breakout-milestone → /breakout-epics → /create-prd → /generate-tasks → /process-task-list
```

This command is **planning only** — gather understanding and produce the plan (and,
when warranted, a companion architecture doc). **Do not implement or provision anything.**

The initial idea / problem is:

> $ARGUMENTS

If the input above is empty, ask the user what project they want to plan before doing
anything else.

## Process

1. **Understand before you plan.** Skim the context that already exists so you don't
   ask what the repo answers and so the plan fits its surroundings:
   - `CLAUDE.md` (operating rules, constraints, roles) and any `README`.
   - Any discussion notes, an existing architecture doc, or prior plans the input points to.
   - Relevant existing material under `project/` (e.g. `project/refactor-tests/`)
     for fleet work) so the plan references real systems, not invented ones.
2. **Ask the essential clarifying questions** (3–6 max) to close *real* gaps in
   understanding. Cover the dimensions a good plan needs:
   - **Outcome & success** — what does "done" look like, and how is it measured?
   - **Scope & constraints** — what's in, what's explicitly out; hard constraints
     (zero-downtime, budget, deadline, compliance, "don't touch X")?
   - **Roles & ownership** — who executes what? Note any work only a human/owner can
     do (privileged credentials, approvals, purchasing) — these become **blocking
     owner tasks**, never silently deferred.
   - **Current state & dependencies** — what exists today; what this depends on or must
     not break.
   - **Risk & reversibility** — what's hard to reverse or outward-facing; rollback posture.
   Skip any question the input or repo already answers.
3. **Decide whether an architecture/design doc is warranted.** If the project has
   non-trivial system design (topology, technology choices, data flows, trade-offs to
   record), **offer** to produce a companion `<project-name>-architecture.md` and write
   it only if the user agrees. Simple projects get the plan alone. The plan should be
   the *how and in what order*; the architecture doc is the *target design* it executes.
4. **Decompose into milestones and epics.** Each **milestone** is a major,
   independently-valuable, releasable deliverable that leaves the project in a working
   state. Each **epic** is a coherent body of work owned and tracked as a unit. Order
   them on the critical path and call out what can run in parallel.
5. **Generate the project plan** using the structure below.
6. **Save it** (see Output) and tell the user the next step is `/breakout-milestone`.

### Formatting the clarifying questions

- **Number** each question (1, 2, 3…); list options as **A, B, C, D** so the user can
  answer "1A, 2C, 3B". Always allow a free-text answer — these are design decisions, not a quiz.

## Naming & ID conventions (stable handles for the whole pipeline)

These IDs are the durable handles every later command keys off — fix them here:

- **Milestones:** `M0`, `M1`, … `Mn` (zero-indexed; `M0` is foundations/groundwork).
- **Epics:** `M<n>-E<m>` (e.g. `M1-E2`).
- **Slugs:** short kebab-case (e.g. `observability-first`, `iac-bootstrap`).

## Target directory structure (the whole pipeline writes into this tree)

The plan lives at the root of a per-project directory; later commands fill in the tree.
Encode this layout in the plan's "breaking this out" section so it's unambiguous:

```
project/<Area>/<project-name>/
├── <project-name>-project-plan.md          ← THIS command (plan of record)
├── <project-name>-architecture.md          ← optional companion design doc (this command)
├── Milestone-00/                            ← one dir per milestone: M0→00, M1→01, …
│   ├── overview/
│   │   └── milestone-01-<Title>.md          ← /breakout-milestone (file # is 1-based: M0→01)
│   ├── Epic-01/                             ← one dir per epic: M<n>-E1→Epic-01, …
│   │   ├── overview/
│   │   │   └── e1-<slug>.md                 ← /breakout-epics (the input to /create-prd)
│   │   ├── prd-e1-<slug>.md                 ← /create-prd
│   │   ├── tasks-e1-<slug>.md               ← /generate-tasks
│   │   └── CHANGELOG.md                     ← running change log for the epic
│   └── Epic-02/ …
└── Milestone-01/ …
```

Indexing note (matches the existing `professionalization/` tree): the **directory**
`Milestone-NN` is zero-padded to the `M<n>` id (`M0`→`Milestone-00`); the milestone
**overview filename and H1 title** use the **1-based human number** (`M0`→
`milestone-01-…` / "Milestone 1"). Epic dirs and files use the `E<m>` number
(`M<n>-E1`→`Epic-01/overview/e1-<slug>.md`).

## Project-plan structure

Generate a Markdown document with these sections:

1. **Header block** — status (e.g. 📋 plan of record, for owner/stakeholder approval),
   author, date, and (if it exists) a link to the companion architecture doc with a note
   to read that first. State the **governing constraint** in one or two lines.
2. **How to read this plan** — the milestone/epic decomposition model, the naming
   convention above, and the roles referenced throughout.
3. **Objectives & success criteria** — a table of the project's goals each with a
   **measurable** definition of done. Include an overarching acceptance gate if one applies.
4. **Guiding execution principles** — the non-negotiables that shape every milestone
   (e.g. reversible-first, parallel-build, one-change-at-a-time, snapshot-before-risk,
   owner-gate on hard-to-reverse actions). Pull from `CLAUDE.md` where relevant.
5. **Milestone map (at a glance)** — a table: milestone, title, outcome, impact/risk,
   and (if relevant) which design phase it realizes. Follow it with a short
   critical-path ordering note and an ASCII dependency sketch.
6. **Milestones & epics** — one subsection per milestone with: **Goal**, **Exit
   criteria**, and an **epic table** (`Epic | Title | Summary | Owner | Impact`). This
   is the spine `/breakout-milestone` and `/breakout-epics` expand.
7. **Cross-cutting workstreams** — work that runs through every milestone (docs/change
   log, security review, cost/tracking, approvals).
8. **Dependencies & sequencing rules** — the ordering constraints between milestones.
9. **Risk register (plan-level)** — `Risk | Likelihood | Impact | Mitigation | Owner`.
10. **Rollback posture per milestone** — the primary rollback lever for each.
11. **Deliverables checklist (project-level)** — the concrete artifacts that mark "done".
12. **Next step — breaking this out** — restate the target directory structure above and
    point to `/breakout-milestone` for the first milestone.

## Output

- **Format:** Markdown (`.md`)
- **Location:** `project/<Area>/<project-name>/` — create the directory if needed. Reuse
  an existing area (e.g. `project/refactor-tests/`) when the project belongs to one; ask
  if the area/name is ambiguous.
- **Filename:** `<project-name>-project-plan.md` (plus `<project-name>-architecture.md`
  if the user accepted the companion doc).

## Final instructions

1. Do **NOT** implement, provision, or change any system — this command only produces
   the plan (and optional architecture doc).
2. You **must** ask the clarifying questions first, unless the input is already fully
   specified and the repo answers every gap.
3. Make every owner-only / outside-the-agent task an **explicit, blocking** item — never
   silently defer maintainer work.
4. Fold the user's answers back in to sharpen the plan, then point them to
   `/breakout-milestone` to expand the first milestone.
