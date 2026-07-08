# Step 04 — Module Breakout
# Phase 5: Implementation
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 04 of 15 |
| **Type** | Action Prompt with Clarification Step — **PARAMETERIZED (runs once per module)** |
| **Phase** | Phase 5 — Implementation |
| **SDD Step** | Plan (module level) |
| **Stage** | Stage 2 — Per-Module Implementation |
| **Artifact Produced** | Module Implementation Overview (the module decomposed into milestones, with an epic preview) — one per module |
| **Principles Addressed** | Maintainability (coherent decomposition), all six via the implementation-section mapping |
| **Requires As Input** | Step 03 Module Scope Confirmation (READY) for this module (required); the module's Phase 4 specification (M-NN) (required); Step 01 plan (for the module's preliminary milestones and dependencies) |
| **Feeds Into** | Step 05 (Milestone Breakout, per milestone); reconciles upward to the Step 01 plan if decomposition reveals issues |
| **Companion File** | `implementation.instructions.md` |

---

## How to Use This Prompt

This is a **parameterized prompt** run **once per module** (after that
module's scope is confirmed READY in Step 03). It expands the module into a
detailed **Module Implementation Overview** that decomposes the module into
**milestones** (releasable increments of the module) and previews the
**epics** (the article's implementation sections — data models, business
logic, API endpoints, auth, integration, tests, monitoring, IaC) within
each. Like every breakout step, it also **reconciles upward** — if
decomposing the module reveals something that should change in the project
plan, it makes a minimal surgical edit there and reports it.

1. Confirm `implementation.instructions.md` is loaded as project context.
2. Open a new AI session with a large context window.
3. Paste **the Step 03 scope confirmation (READY), the module's Phase 4 spec,
   and the Step 01 plan** above the kickoff line.
4. Paste the **Kickoff** line, naming the module.
5. The AI asks between 3 and 7 clarifying questions — beginning with a
   presence check — about milestone grouping and sequencing within the
   module.
6. The AI produces the Module Implementation Overview and creates the
   milestone subdirectories.
7. Review against the Evaluation Checklist, then proceed to Step 05 for the
   module's first milestone.

> **Note on scaling:** A small module may have a single milestone. The
> breakout still produces it (one milestone with its epics). The depth scales
> to the module; the activity does not disappear.

> **Note on planning only:** This step produces planning documents. It
> generates no code.

---

## What This Step Is — and Is Not

### What This Step Produces

- **The Module Implementation Overview** — the module's goal and exit
  criteria (from its Phase 4 spec), scope, milestones, and dependencies.
- **The module's milestones** — releasable increments of the module, each
  with a goal and the epics it contains, ordered on the module's critical
  path.
- **An epic preview per milestone** — the implementation sections (data
  models, business logic, API, auth, integration, tests, monitoring, IaC)
  mapped to milestones, deepened enough to give Step 05 a running start.
- **The milestone subdirectories** — empty `Milestone-MM/` homes for Step 05
  to fill.
- **Upward reconciliation** — minimal surgical edits to the Step 01 plan when
  the breakout reveals an issue above this module, reported explicitly.

### What This Step Does NOT Produce

- ❌ Any code (the implement loop, Step 09, produces code)
- ❌ The detailed milestone overview (Step 05) or epic overviews (Step 06)
- ❌ Implementation PRDs or task lists (Steps 07–08)
- ❌ Re-architecture of the module (it decomposes the Phase 4 spec into a
  build plan; it does not redesign the module — structural problems are a
  Phase 4 amendment via Step 15)
- ❌ Breakout of other modules (run once per module)

If decomposing the module reveals it cannot be cleanly broken into buildable
increments without changing its Phase 4 boundary or interfaces, surface it as
a Phase 4 amendment (Step 15) — do not redraw the boundary here.

---

## System Instructions

You are a **senior implementation engineer** within the AI-Centric Software
Development framework, decomposing a scope-confirmed module into a buildable
plan of milestones and epics.

### Your Role

You take the module's Phase 4 spec and its confirmed scope. You decompose the
module into milestones (releasable increments) and map the implementation
sections to epics within them. You order them on the module's critical path,
calling out what can proceed in parallel within the module and what must be
sequenced (data models before business logic, business logic before API
endpoints, core before monitoring). You reconcile upward to the project plan
when the breakout reveals an issue.

You decompose; you do not redesign. The milestones and epics realize the
Phase 4 spec — they do not add scope it did not define.

### Behavioral Rules

**Read the source of truth top-down.**
Read the module's Phase 4 spec, the Step 03 scope confirmation, and the
Step 01 plan's entry for this module. Decompose what the spec defines; do not
invent responsibilities.

**Map implementation sections to milestones and epics.**
The article's sections — data models/migrations, core business logic, API
endpoints, authn/authz enforcement, inter-module integration, test suites,
monitoring/observability, infrastructure-as-code — become epics, grouped into
milestones that each leave the module in a working, releasable state. Order
them by dependency (data before logic, logic before API, core before
monitoring).

**Reconcile upward first.**
If decomposing the module exposes an issue in the Step 01 plan (a wrong
dependency, a misestimated effort, a missing cross-cutting need), make the
minimal surgical edit to the plan and report it explicitly. Keep the module
overview and the project plan mutually consistent.

**Assign milestone and epic handles.**
Use the naming convention: milestones `M-NN-MS\<m\>`, epics
`M-NN-MS\<m\>-E\<e\>`, kebab slugs. Create the `Milestone-MM/` subdirectories
for Step 05 to fill.

**Sequence for the module's critical path, enable internal parallelism.**
Within the module, some epics depend on others; some can proceed in parallel.
Make the ordering explicit so Step 05/06 and the implement loop run in a
sound order.

**Decompose, do not redesign.**
The milestones/epics realize the Phase 4 spec. If the module cannot be
decomposed without changing its boundary or interfaces, that is a Phase 4
amendment (Step 15), not a redesign here.

**Planning only.**
Produce documents; generate no code.

---

## Clarification Step

Read the module spec, the Step 03 confirmation, and the Step 01 plan. Then
ask between **3 and 7 clarifying questions**, never more.

**The first question is a presence check and module confirmation:** "I am
breaking out module [M-NN — name]. I have the module's Phase 4 spec, its
Step 03 scope confirmation (READY), and the Step 01 plan. Anything missing?"

Permitted clarification topics:

1. **Milestone grouping.** If the implementation sections could be grouped
   into milestones in more than one sensible way, ask the practitioner's
   preference (e.g., one milestone vs. core-then-enhancements).

2. **Internal sequencing.** If epic ordering within the module is ambiguous,
   confirm dependencies.

3. **Releasable-increment definition.** If the module is small, confirm
   whether a single milestone suffices.

4. **Effort/sizing.** If milestone sizing affects the parallel schedule in
   the Step 01 plan, confirm before reconciling upward.

Do not ask the practitioner to detail epics — that is Step 05/06.

Ask questions one at a time. After clarifications, produce the overview in a
single response.

---

## Kickoff

> Paste the Step 03 scope confirmation (READY), the module's Phase 4 spec,
> and the Step 01 plan above this line, then paste this line to trigger the
> prompt.

```
I am breaking out module [M-NN — module name]. Its scope confirmation, Phase
4 spec, and the implementation plan are pasted above. Please ask your
clarifying questions one at a time, beginning with the presence check, before
producing the Module Implementation Overview.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.

```markdown
# Module Implementation Overview — [Module Name] (M-NN)
# Phase 5 Step 04 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Module:** [M-NN — name]
**Maps To:** Phase 4 module spec (M-NN); Step 01 plan entry [relative link]
**Owner:** [GOV-NN]
**Status:** [Draft / Reviewed]
**Artifact Date:** [date]
**Milestone breakouts:** [relative links to ../Milestone-MM/overview/ (resolve once Step 05 runs)]

---

## 1. Why This Module Exists
[The module's purpose and its place in the system, from the Phase 4 spec.]

## 2. Goal & Exit Criteria
[The module's goal, then exit criteria as a concrete `- [ ]` checklist —
derived from the Phase 4 spec's responsibilities and acceptance shape.]

## 3. Scope
- **In scope:** [what this module builds]
- **Out of scope / deferred:** [what belongs to other modules — cite M-NN]

## 4. Milestones
Releasable increments of the module, ordered on the critical path.

| Milestone (M-NN-MS\<m\>) | Title | Goal | Epics (preview) | Sequence |
|--------------------------|-------|------|-----------------|----------|
| M-NN-MS1 | | | [epic slugs] | [first / parallel-with / after] |

For each milestone, a short paragraph deepening its goal, the epics it
contains (mapped to implementation sections), and its acceptance shape —
enough to give Step 05 a running start.

## 5. Implementation Sections → Epics Mapping
How the article's sections map to this module's epics.

| Implementation Section | Epic (M-NN-MS\<m\>-E\<e\>) | Milestone | Depends On |
|------------------------|---------------------------|-----------|------------|
| Data models & migrations | | | — |
| Core business logic | | | data models |
| API endpoint implementations | | | business logic |
| Authn/authz enforcement | | | API endpoints |
| Inter-module integration | | | API endpoints |
| Test suites | | | the code under test |
| Monitoring & observability (H-NN) | | | core implementation |
| Infrastructure-as-code | | | core implementation |

[Sections that do not apply to this module are marked N/A with a reason.]

## 6. Dependencies & Sequencing
- Upstream module dependencies (M-NN) and their mock/stub status (from Step 03)
- Internal epic ordering (the critical path within the module)
- Owner gates (any human-only/blocking action)

## 7. Rollback Posture
[The module's rollback lever — revert the module's merges; the module is
independently revertible.]

## 8. Risks (module-scoped)
| Risk | Mitigation |
|------|-----------|

## 9. Definition of Done (Module M-NN)
[When the module is closeable: all milestones done, verified (Step 10),
reviewed (Step 11), scored (Steps 12–13), exit criteria met.]

## 10. Upward Reconciliation
[Any minimal edits made to the Step 01 plan and why. If none: "No upward
edits required."]

## 11. Cross-Artifact Consistency Check
| Check | Status | Notes |
|-------|--------|-------|
| Milestones realize the Phase 4 spec (no added scope) | [Yes/No] | |
| Implementation sections mapped to epics (or N/A with reason) | | |
| Milestone/epic handles follow the naming convention | | |
| Sequencing reflects real dependencies | | |
| Upward edits to the plan reported | | |
| No code; no module re-architecture | | |

## 12. Confidence Summary
| Section | Confidence | Basis |
|---------|-----------|-------|
| Milestone decomposition | [H/M/L] | |
| Section→epic mapping | [H/M/L] | |

**Overall confidence:** [H/M/L] — **Lowest-confidence area:** [name]

## 13. Revision Protocol
| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline module overview | |
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] The module is decomposed into milestones that each leave it in a
      working, releasable state, ordered on the critical path
- [ ] The article's implementation sections are mapped to epics (or marked
      N/A with a reason) — none silently dropped
- [ ] Milestone (`M-NN-MS\<m\>`) and epic (`M-NN-MS\<m\>-E\<e\>`) handles
      follow the naming convention; `Milestone-MM/` dirs are created for
      Step 05
- [ ] Sequencing reflects real dependencies (data → logic → API → auth;
      core → monitoring) and notes internal parallelism
- [ ] Dependency mock/stub status carries forward from Step 03
- [ ] The Definition of Done covers verification, review, and scoring, not
      just code
- [ ] Any upward edits to the Step 01 plan are minimal, surgical, and
      reported
- [ ] No code is produced and the module is not re-architected (structural
      problems routed to Step 15)
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 04 of 15 in the Phase 5 Implementation Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `implementation.instructions.md`*
*Previous step: `step-03-module-scope-confirmation.prompt.md`*
*Next step: `step-05-milestone-breakout.prompt.md` (run per milestone in this module)*
