# Step 06 — Epic Breakout
# Phase 5: Implementation
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 06 of 15 |
| **Type** | Action Prompt with Clarification Step — **PARAMETERIZED (runs once per epic)** |
| **Phase** | Phase 5 — Implementation |
| **SDD Step** | Plan → Detail (module level) |
| **Stage** | Stage 2 — Per-Module Implementation |
| **Artifact Produced** | Epic Overview (the input to the Implementation PRD) — one per epic |
| **Principles Addressed** | All six — the epic carries the principle requirements its implementation must satisfy |
| **Requires As Input** | Step 05 Milestone Overview (required); the specific epic (M-NN-MS\<m\>-E\<e\>); the Phase 4 module-spec section + API contract + framework IDs (SEC/DA/H/CS) the epic realizes |
| **Feeds Into** | Step 07 (Implementation PRD); reconciles upward to the milestone overview, module overview, and project plan |
| **Companion File** | `implementation.instructions.md` |

---

## How to Use This Prompt

This is a **parameterized prompt** run **once per epic**. It expands an epic
from the Milestone Overview into a detailed **Epic Overview** — the document
the Implementation PRD (Step 07) expands. The epic realizes one
implementation section (data models, business logic, API endpoints, auth,
integration, tests, monitoring, or IaC), and its overview carries the
specific Phase 4 spec content and framework constraints (SEC-NN, DA-NN, H-NN,
CS-NN, the API contract) the implementation must honor. Like every breakout
step, it **reconciles upward**.

1. Confirm `implementation.instructions.md` is loaded as project context.
2. Open a new AI session.
3. Paste **the Step 05 milestone overview and the Phase 4 spec content +
   contract + framework IDs the epic realizes** above the kickoff line.
4. Paste the **Kickoff** line, naming the epic.
5. The AI asks 3–7 clarifying questions (presence check first).
6. The AI produces the Epic Overview.
7. Review against the Evaluation Checklist, then proceed to Step 07.

> **Note:** Planning only — no code is generated. This is the last planning
> level before the PRD and task list.

---

## What This Step Is — and Is Not

### What This Step Produces

- **The Epic Overview** — objective, acceptance criteria, a high-level task
  table, dependencies and owner gates, risks, and notes.
- **The constraint citations the epic must honor** — the Phase 4 spec section,
  the relevant API contract, and the framework IDs (SEC-NN, DA-NN, H-NN,
  CS-NN) the implementation applies.
- **The principle requirements** — the Core-Principle obligations the epic's
  implementation must satisfy (security checks, coverage threshold,
  performance budget, conformance).
- **Upward reconciliation** — minimal surgical edits to the milestone/module
  overviews or project plan, reported.

### What This Step Does NOT Produce

- ❌ Any code
- ❌ The Implementation PRD (Step 07) or task list (Step 08) — this is their
  input
- ❌ Re-architecture (realizes the Phase 4 spec; structural problems are a
  Phase 4 amendment via Step 15)
- ❌ Breakout of other epics (run once per epic)

---

## System Instructions

You are a **senior implementation engineer** within the AI-Centric Software
Development framework, detailing one epic into a create-prd-ready overview.

### Your Role

You take the epic's entry in the milestone overview and the Phase 4 content
it realizes. You produce the Epic Overview: a concrete objective, verifiable
acceptance criteria, a high-level task table, the constraints the
implementation must honor (with IDs), the principle requirements, and the
dependencies and owner gates. You reconcile upward when detailing reveals an
issue. You detail; you do not redesign.

### Behavioral Rules

**Cite the constraints the epic must honor.**
The epic realizes a specific Phase 4 spec section. Carry the relevant IDs into
the overview: the API contract operations (for an API epic), SEC-NN (for an
auth epic), DA-NN (for a data epic), H-NN (for a monitoring epic), and the
CS-NN coding conventions that apply. The PRD and task list inherit these
citations — this is the traceability seam.

**Make acceptance criteria verifiable.**
Acceptance criteria are a concrete `- [ ]` checklist that the implementation
and its tests can be checked against — not restated intentions.

**Carry the principle requirements.**
State the Core-Principle obligations the implementation must satisfy: security
checks on inputs (SEC-NN), the coverage threshold, the performance budget,
the conformance target. These become PRD requirements and task acceptance.

**Reconcile upward first.** Minimal surgical edits to the milestone/module
overviews or project plan, reported explicitly.

**Make owner gates explicit and blocking.** Any human-only action
(privileged provisioning, production touch, credential handling) is an
explicit, blocking gate — never silently deferred.

**Detail, do not redesign. Planning only.** Realize the Phase 4 spec; route
structural problems to Step 15; generate no code.

---

## Clarification Step

Read the milestone overview and the Phase 4 content the epic realizes. Then
ask **3–7 clarifying questions**, never more.

**First question — presence check + epic confirmation:** "I am breaking out
epic [M-NN-MS\<m\>-E\<e\> — title], which realizes [implementation section].
I have the milestone overview and the relevant Phase 4 spec content,
contract, and framework IDs. Anything missing?"

Permitted topics: acceptance-criteria specifics; which contract operations /
SEC-NN / DA-NN / H-NN apply; task granularity; owner gates; dependency
readiness (mock/stub status).

Ask one at a time. Then produce the overview in a single response.

---

## Kickoff

> Paste the Step 05 milestone overview and the Phase 4 spec content + API
> contract + framework IDs the epic realizes above this line, then paste this
> line to trigger the prompt.

```
I am breaking out epic [M-NN-MS<m>-E<e> — title]. The milestone overview and
the Phase 4 content it realizes are pasted above. Please ask your clarifying
questions one at a time, beginning with the presence check, before producing
the Epic Overview.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.

```markdown
# Epic Overview — [Title] (M-NN-MS\<m\>-E\<e\>)
# Phase 5 Step 06 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Epic:** [M-NN-MS\<m\>-E\<e\> — title]
**Implementation Section:** [data models / business logic / API / auth / integration / tests / monitoring / IaC]
**Parent Milestone:** [relative link]
**Maps To:** Phase 4 module-spec section [reference]; API contract [reference, if any]
**Owner:** [GOV-NN]
**Status:** [Draft / Reviewed]
**Artifact Date:** [date]

---

## 1. Objective
[What this epic delivers and why, in a short paragraph.]

## 2. Constraints This Epic Honors
| Constraint | ID(s) | What the implementation must do |
|------------|-------|---------------------------------|
| API contract operations | [op names] | Conform to the contract |
| Security controls | SEC-NN | Apply the controls / patterns |
| Data constraints | DA-NN | Conform the data model |
| Monitoring hooks | H-NN | Emit the specified signals |
| Coding conventions | CS-NN | Follow the conventions |

## 3. Acceptance Criteria
[Concrete, verifiable `- [ ]` checklist — the epic's "done."]

## 4. Principle Requirements
| Principle | Requirement for This Epic |
|-----------|---------------------------|
| Security | [Input checks, authz enforcement — SEC-NN] |
| Maintainability | [Coverage threshold, documentation] |
| Economics | [Effort budget] |
| Operations | [Monitoring hooks H-NN, health checks] |
| Scoring & Metrics | [Metrics emitted/collected] |
| Correctness Verification | [Conformance target; property/formal applicability] |

## 5. Tasks (high level)
| # | Task | Owner | Done When |
|---|------|-------|-----------|
| 1 | | | |

[Enough granularity to give Step 07/08 a clear start — but not the per-step
execution detail those produce.]

## 6. Dependencies & Owner Gates
- Upstream epics/modules (and mock/stub status from Step 03)
- Owner-only/blocking actions (OP-# items: provisioning, approvals,
  credentials) — explicit and blocking

## 7. Risks
| Risk | Mitigation |
|------|-----------|

## 8. Notes
[Reversibility, what stays untouched, links an implementer needs.]

## 9. Upward Reconciliation
[Minimal edits to the milestone/module overviews or project plan, and why. If
none: "No upward edits required."]

## 10. Cross-Artifact Consistency Check
| Check | Status | Notes |
|-------|--------|-------|
| Realizes the Phase 4 spec section (no added scope) | [Yes/No] | |
| Constraint IDs cited (contract / SEC / DA / H / CS) | | |
| Acceptance criteria verifiable | | |
| Principle requirements carried | | |
| Owner gates explicit and blocking | | |
| Upward edits reported; no code; no re-architecture | | |

## 11. Confidence Summary
**Overall confidence:** [H/M/L] — **Lowest-confidence area:** [name]

## 12. Revision Protocol
| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline epic overview | |
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] The epic realizes a single Phase 4 implementation section (no added
      scope)
- [ ] The constraints it honors are cited by ID — the relevant API contract
      operations, SEC-NN, DA-NN, H-NN, and CS-NN (the traceability seam)
- [ ] Acceptance criteria are a concrete, verifiable checklist
- [ ] The principle requirements (security, coverage, performance,
      conformance) the implementation must satisfy are stated
- [ ] The high-level task table gives Step 07/08 a clear start without
      pre-empting their detail
- [ ] Owner-only/blocking actions are explicit gates, never silently deferred
- [ ] Any upward edits are minimal, surgical, and reported
- [ ] No code; no re-architecture (structural problems routed to Step 15)
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 06 of 15 in the Phase 5 Implementation Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `implementation.instructions.md`*
*Previous step: `step-05-milestone-breakout.prompt.md`*
*Next step: `step-07-implementation-prd.prompt.md` (run per epic)*
