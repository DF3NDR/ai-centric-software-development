---
description: Break each epic of a milestone out into its own directory + detailed epic overview, ready for /create-prd, reconciling the docs above.
argument-hint: [milestone id (e.g. M1), a single epic id (e.g. M1-E2), or the milestone-overview path]
---

# Break out epics

Take the epics of a **milestone** and expand each into its own subdirectory with a
detailed **epic overview** document — the document that becomes the input to
`/create-prd`. Each run also **reviews the milestone overview and the project plan**
and passes any needed corrections **upward**, keeping all three levels consistent.

Pipeline position:

```
/create-project-plan → /breakout-milestone → [/breakout-epics] → /create-prd → /generate-tasks → /process-task-list
```

This command produces **planning documents only** — do not implement anything.

What to break out:

> $ARGUMENTS

Resolve the input as follows:
- A milestone id (e.g. `M1`) or its milestone-overview path → break out **all** epics in
  that milestone that don't yet have an overview doc.
- A single epic id (e.g. `M1-E2`) → break out just that one epic.
- Empty → find the milestone overviews under `project/**/Milestone-*/overview/`; if more
  than one milestone is broken out, ask which milestone's epics to expand. Confirm the set.

## Process

1. **Read the sources of truth, top-down.** Read the `<project-name>-project-plan.md`,
   the parent **milestone overview** (`Milestone-NN/overview/milestone-*.md`), and the
   companion architecture doc if present. Read `CLAUDE.md` and any directly relevant
   existing material (e.g. host notes under `project/refactor-tests/`) so each
   epic overview references real systems, not invented ones.
2. **Reconcile upward first.** Detailing the epics often surfaces issues above them — a
   missing/duplicate epic, a wrong owner or dependency, an exit criterion that won't
   hold, scope that belongs in a different epic. When it does:
   - Make the **minimal, surgical edit** to the **milestone overview** and/or the
     **project plan**, and
   - **Report each upward edit explicitly** (what changed, where, why). Never let the
     three levels silently diverge.
3. **Create one directory + overview per epic** per the structure below. Process epics in
   id order; skip any that already have an overview unless asked to redo it.
4. **Make each epic overview create-prd-ready** — concrete enough that `/create-prd` can
   ask only a few clarifying questions and proceed.
5. **Report** what you created, every upward edit, and point to `/create-prd`.

## Directory & naming (match the existing `professionalization/` tree)

- **Epic directory:** `Milestone-NN/Epic-MM/` where `MM` is the `E<m>` number
  zero-padded (`M<n>-E1`→`Epic-01`, `M<n>-E2`→`Epic-02`).
- **Overview file:** `Epic-MM/overview/e<m>-<slug>.md`, where `<m>` is the epic number
  and `<slug>` is short kebab-case (H1 title "Epic <m> — <Title> (M<n>-E<m>)").
- This is the same directory `/create-prd` then writes `prd-e<m>-<slug>.md` and
  `/generate-tasks` writes `tasks-e<m>-<slug>.md` into.

```
project/<Area>/<project-name>/Milestone-01/
├── overview/milestone-02-<Title>.md
├── Epic-01/
│   └── overview/
│       └── e1-<slug>.md            ← THIS command (input to /create-prd)
├── Epic-02/
│   └── overview/
│       └── e2-<slug>.md
└── …
```

After creating the epic overviews, ensure the **milestone overview's "Epic breakouts"**
links resolve to the files you just wrote (fix the link text/slug if it drifted).

## Epic overview structure

Generate a Markdown document with these sections (deepen the milestone's epic entry into
something executable — not a restated one-liner):

1. **Header block** — "Epic <m> — <Title> (M<n>-E<m>)"; a **Parent milestone** link
   (relative) to the milestone overview; a **Maps to** link to the epic in the project
   plan; **Owner**; **Impact/blast radius**; **Estimated effort**; **Status**.
2. **Objective** — what this epic delivers and why, in a short paragraph.
3. **Acceptance criteria** — concrete, verifiable `- [ ]` checklist (the epic's "done").
4. **Tasks** — a table `# | Task | Owner | Done when`, ordered. Enough granularity that
   `/create-prd` and `/generate-tasks` have a clear starting point — but stop short of
   the per-step execution detail those commands produce.
5. **Dependencies & owner gates** — upstream epics/milestones, and every **owner-only /
   outside-the-agent** action called out as an **explicit, blocking** gate (e.g. an
   `OP-#` item: privileged provisioning, approvals, credentials). Never silently defer
   maintainer work.
6. **Risks** — `Risk | Mitigation`, scoped to this epic.
7. **Notes** — anything an implementer needs (reversibility, what stays untouched, links).

## Output

- **Format:** Markdown (`.md`)
- **Location:** `project/<Area>/<project-name>/Milestone-NN/Epic-MM/overview/`
- **Filename:** `e<m>-<slug>.md` (one per epic)
- **Also:** possible reconciling edits to the milestone overview and/or project plan.

## Final instructions

1. **Planning only** — produce documents; implement nothing.
2. Keep all three levels — epic overview, milestone overview, project plan — **mutually
   consistent**, and report every upward edit you make.
3. Deepen each epic to make it create-prd-ready; don't redefine or widen its scope.
4. When done, point the user to `/create-prd` (run per epic, against each
   `e<m>-<slug>.md`) to continue the pipeline.
