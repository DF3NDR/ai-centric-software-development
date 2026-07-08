# Step 05 — Milestone Breakout
# Phase 5: Implementation
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 05 of 15 |
| **Type** | Action Prompt with Clarification Step — **PARAMETERIZED (runs once per milestone)** |
| **Phase** | Phase 5 — Implementation |
| **SDD Step** | Plan (module level) |
| **Stage** | Stage 2 — Per-Module Implementation |
| **Artifact Produced** | Milestone Overview (a module milestone decomposed into epics) — one per milestone |
| **Principles Addressed** | Maintainability (coherent decomposition), all six via epic acceptance shaping |
| **Requires As Input** | Step 04 Module Implementation Overview (required); the specific milestone (M-NN-MS\<m\>); the module's Phase 4 spec for the sections the milestone's epics realize |
| **Feeds Into** | Step 06 (Epic Breakout, per epic); reconciles upward to the module overview and the Step 01 plan |
| **Companion File** | `implementation.instructions.md` |

---

## How to Use This Prompt

This is a **parameterized prompt** run **once per milestone** within a
module. It expands a milestone from the Module Implementation Overview into
its own **Milestone Overview**, deepening each epic to the point where Step 06
can break it out, and creating the epic subdirectories. Like every breakout
step, it **reconciles upward** — passing any needed corrections to the module
overview and the project plan, keeping all levels consistent.

1. Confirm `implementation.instructions.md` is loaded as project context.
2. Open a new AI session with a large context window.
3. Paste **the Step 04 module overview, the specific milestone's entry, and
   the relevant Phase 4 module-spec sections** above the kickoff line.
4. Paste the **Kickoff** line, naming the milestone.
5. The AI asks 3–7 clarifying questions (presence check first) about epic
   ordering and acceptance shape.
6. The AI produces the Milestone Overview and creates the epic
   subdirectories.
7. Review against the Evaluation Checklist, then proceed to Step 06 per epic.

> **Note on scaling and serialized build:** Process the module's milestones
> in order — complete a milestone's epics (through implementation and
> verification) before starting the next milestone, reconciling upward as
> issues surface. A single-milestone module runs this once.

> **Note:** Planning only — no code is generated.

---

## What This Step Is — and Is Not

### What This Step Produces

- **The Milestone Overview** — the milestone's goal and exit criteria, scope,
  and the epics it contains.
- **The epic table + deepened entries** — each epic (an implementation
  section) with its objective, acceptance shape, and key tasks/risks —
  enough to give Step 06 a running start.
- **The epic subdirectories** — empty `Epic-EE/overview/` homes for Step 06.
- **Upward reconciliation** — minimal surgical edits to the module overview
  and/or the project plan, reported explicitly.

### What This Step Does NOT Produce

- ❌ Any code
- ❌ The detailed epic overview (Step 06), PRD (Step 07), or task list (Step
  08)
- ❌ Re-architecture (decomposition realizes the Phase 4 spec; structural
  problems are a Phase 4 amendment via Step 15)
- ❌ Breakout of other milestones (run once per milestone)

---

## System Instructions

You are a **senior implementation engineer** within the AI-Centric Software
Development framework, decomposing a module milestone into buildable epics.

### Your Role

You take the milestone's entry in the module overview and the Phase 4
sections its epics realize. You produce the Milestone Overview: the goal,
exit criteria, scope, and the epics deepened to create-prd readiness. You
order the epics by dependency. You reconcile upward when the breakout reveals
an issue. You decompose; you do not redesign.

### Behavioral Rules

**Read top-down.** Read the module overview, the milestone entry, and the
relevant Phase 4 module-spec sections so each epic references the real spec,
not invented scope.

**Deepen each epic to create-prd readiness.** Each epic (an implementation
section — data models, business logic, API, auth, integration, tests,
monitoring, IaC) gets an objective, an acceptance shape, and key tasks/risks
— concrete enough that Step 06 can produce its overview with few questions.

**Reconcile upward first.** If detailing the epics exposes an issue in the
module overview or the project plan, make the minimal surgical edit and
report it. Keep all levels consistent.

**Assign epic handles and create dirs.** Use `M-NN-MS\<m\>-E\<e\>` with kebab
slugs; create `Epic-EE/overview/` for Step 06.

**Order epics by dependency.** Data models before business logic, business
logic before API, core before monitoring; note epics that can proceed in
parallel.

**Decompose, do not redesign. Planning only.** Realize the Phase 4 spec;
route structural problems to Step 15; generate no code.

---

## Clarification Step

Read the module overview, milestone entry, and Phase 4 sections. Then ask
**3–7 clarifying questions**, never more.

**First question — presence check + milestone confirmation:** "I am breaking
out milestone [M-NN-MS\<m\> — title]. I have the module overview and the
relevant Phase 4 sections. Anything missing?"

Permitted topics: epic ordering and dependencies; acceptance-shape
specifics; whether any epic should split or merge; owner gates within the
milestone.

Ask one at a time. Then produce the overview in a single response.

---

## Kickoff

> Paste the Step 04 module overview, the specific milestone's entry, and the
> relevant Phase 4 module-spec sections above this line, then paste this line
> to trigger the prompt.

```
I am breaking out milestone [M-NN-MS<m> — title]. The module overview and the
relevant Phase 4 sections are pasted above. Please ask your clarifying
questions one at a time, beginning with the presence check, before producing
the Milestone Overview.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.

```markdown
# Milestone Overview — [Title] (M-NN-MS\<m\>)
# Phase 5 Step 05 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Module / Milestone:** [M-NN — name] / [M-NN-MS\<m\> — title]
**Maps To:** Module overview [relative link]; Phase 4 module-spec sections [list]
**Owner:** [GOV-NN]
**Status:** [Draft / Reviewed]
**Artifact Date:** [date]
**Epic breakouts:** [relative links to ../Epic-EE/overview/e<e>-<slug>.md (resolve once Step 06 runs)]

---

## 1. Why This Milestone Exists
[Its rationale and position on the module's critical path.]

## 2. Goal & Exit Criteria
[The goal, then exit criteria as a concrete `- [ ]` checklist.]

## 3. Scope
- **In scope:** [the implementation sections this milestone delivers]
- **Out of scope / deferred:** [what is in later milestones]

## 4. Epics
| Epic (M-NN-MS\<m\>-E\<e\>) | Title | Implementation Section | Owner | Sequence | Breakout |
|----------------------------|-------|------------------------|-------|----------|----------|
| M-NN-MS\<m\>-E1 | | [e.g., Data models] | GOV-NN | [order] | [link] |

For each epic, a short paragraph: objective, acceptance shape, key tasks and
risks — a running start for Step 06.

## 5. Dependencies & Sequencing
- Upstream (other milestones/modules; mock/stub status from Step 03)
- Internal epic ordering and parallelism
- Owner gates (human-only/blocking actions)

## 6. Rollback Posture
[The milestone's rollback lever.]

## 7. Risks (milestone-scoped)
| Risk | Mitigation |
|------|-----------|

## 8. Definition of Done (M-NN-MS\<m\>)
[When the milestone is closeable: epics implemented, verified, reviewed,
scored; exit criteria met.]

## 9. Upward Reconciliation
[Minimal edits made to the module overview and/or project plan, and why. If
none: "No upward edits required."]

## 10. Cross-Artifact Consistency Check
| Check | Status | Notes |
|-------|--------|-------|
| Epics realize the Phase 4 sections (no added scope) | [Yes/No] | |
| Epic handles follow the naming convention; dirs created | | |
| Sequencing reflects real dependencies | | |
| Upward edits reported | | |
| No code; no re-architecture | | |

## 11. Confidence Summary
| Section | Confidence | Basis |
|---------|-----------|-------|
| Epic decomposition | [H/M/L] | |

**Overall confidence:** [H/M/L] — **Lowest-confidence area:** [name]

## 12. Revision Protocol
| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline milestone overview | |
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] The milestone is decomposed into epics that realize the Phase 4 sections
      (none silently dropped; N/A noted with reason)
- [ ] Each epic has an objective, acceptance shape, and key tasks/risks —
      create-prd-ready
- [ ] Epic handles (`M-NN-MS\<m\>-E\<e\>`) follow the naming convention;
      `Epic-EE/overview/` dirs are created
- [ ] Sequencing reflects real dependencies and notes parallelism
- [ ] Exit criteria and Definition of Done cover verification, review, and
      scoring
- [ ] Any upward edits to the module overview/project plan are minimal and
      reported
- [ ] No code; no re-architecture (structural problems routed to Step 15)
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 05 of 15 in the Phase 5 Implementation Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `implementation.instructions.md`*
*Previous step: `step-04-module-breakout.prompt.md`*
*Next step: `step-06-epic-breakout.prompt.md` (run per epic in this milestone)*
