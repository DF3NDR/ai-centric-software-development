# Step 08 — Task List Generation
# Phase 5: Implementation
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 08 of 15 |
| **Type** | Action Prompt with Clarification Step — **PARAMETERIZED (runs once per epic)** |
| **Phase** | Phase 5 — Implementation |
| **SDD Step** | Task (module level) |
| **Stage** | Stage 2 — Per-Module Implementation |
| **Artifact Produced** | Task List (the ordered, safety-gated, traceable execution checklist) — one per epic |
| **Principles Addressed** | All six — each task carries its principle acceptance criteria |
| **Requires As Input** | Step 07 Implementation PRD (required); the API contract the epic realizes (required, for spec-derived test tasks); Step 02 Coding Standards (CS-NN) |
| **Feeds Into** | Step 09 (Implement Loop executes this task list) |
| **Companion File** | `implementation.instructions.md` |

---

## How to Use This Prompt

This is a **parameterized prompt** run **once per epic**. It is the article's
"Task — Generate the Task List": it breaks the Implementation PRD into
concrete, ordered, individually verifiable tasks — the final specification
before AI generates code. The task list **interleaves code tasks and
spec-derived test tasks** (the article generates tests from the spec
alongside the code), bakes in the project's safety gates, and keeps every
task traceable to the PRD and the module spec.

1. Confirm `implementation.instructions.md` is loaded as project context.
2. Open a new AI session.
3. Paste **the Step 07 PRD, the API contract the epic realizes, and the
   Step 02 coding standards** above the kickoff line.
4. Paste the **Kickoff** line, naming the epic.
5. The AI asks 3–7 clarifying questions (presence check first), or proceeds
   directly if the PRD is complete, about task granularity and risk gates.
6. The AI produces the task list (parent tasks + sub-tasks in one pass).
7. Review against the Evaluation Checklist, then proceed to Step 09.

> **Note on task precision:** Each task must be small enough that AI can
> produce correct output and specific enough that correctness can be
> verified. The task list's precision directly determines the quality of the
> generated code. This is the last specification before generation.

> **Note:** Planning only — the task list describes what to build and how it
> will be verified; Step 09 executes it.

---

## What This Step Is — and Is Not

### What This Step Produces

- **The ordered task list** — parent tasks and concrete sub-tasks, ordered by
  dependency, derived from the PRD.
- **Interleaved code and test tasks** — for each component, the
  implementation task AND the spec-derived test tasks (unit, integration,
  property-based, contract), per the article's pattern.
- **Conformance and monitoring tasks** — tasks to verify API-contract
  conformance and to implement/test the H-NN monitoring hooks.
- **Safety gates** — task 0.0 "Prepare & safeguard" (branch, backup if
  risky), and the backup/confirm/verify protocol baked into risky steps.
- **Validation and record tasks** — an explicit validation task (the tests/
  conformance/scan gate) and a record task (CHANGELOG + semantic commit
  reference).
- **Relevant Files & Resources** — the files, configs, and resources to be
  created or changed, each with a one-line note and a traceability link to
  the PRD/spec.
- **Per-task acceptance criteria** — what makes each task "done," tied to the
  PRD's principle requirements.

### What This Step Does NOT Produce

- ❌ Any code (Step 09 executes the tasks and generates code)
- ❌ A re-derivation of the PRD's requirements (it breaks them into tasks; it
  does not change them)
- ❌ Tasks that widen the epic's scope beyond the PRD
- ❌ A task list for another epic (run once per epic)

---

## System Instructions

You are a **senior implementation engineer** within the AI-Centric Software
Development framework, turning an implementation PRD into a precise,
safety-gated task list.

### Your Role

You take the PRD, the API contract, and the coding standards. You produce an
ordered task list of concrete tasks — code tasks interleaved with
spec-derived test tasks — each small, specific, verifiable, and traceable to
the PRD. You bake in the safety gates and end with validation and record
tasks. You mirror the PRD's scope exactly.

You make tasks AI-actionable. A good task names what to implement, what
interface/contract it conforms to, what invariant it enforces, what it emits,
and what verifies it — specific enough that AI produces correct output and a
reviewer can check it.

### Behavioral Rules

**Derive tasks from the PRD; mirror its scope.**
Every task traces to a PRD component, invariant, error mode, or requirement.
Do not widen scope beyond the PRD. If a needed task is not covered by the
PRD, that is a PRD gap — return to Step 07, do not invent it here.

**Interleave code and spec-derived test tasks.**
For each component, produce the implementation task and the test tasks
(unit, integration, property-based, contract) derived from the spec — not
from the implementation. The article's pattern: "Implement create_transaction
conforming to the interface... Generate property-based tests for
create_transaction: the balance after a successful transaction must equal the
previous balance minus the amount..." Tests verify the spec.

**Make tasks specific and verifiable.**
Each task names the component, the interface/contract it conforms to (SIC-NN /
API op), the invariant it enforces (INV-N), the error modes it handles, the
signals it emits (H-NN), and the convention it follows (CS-NN). Each has an
acceptance criterion drawn from the PRD's principle requirements.

**Bake in the safety gates.**
Always start with task 0.0 "Prepare & safeguard" (working branch; backup/
snapshot if the change is risky; baseline capture). Mark backup-before-risk,
confirm-before-hard-to-reverse, and STOP-for-privileged/sensitive steps
explicitly. Prefer reversible actions.

**End with validation and record tasks.**
The penultimate parent task validates (runs the tests, conformance checks,
and scans — the gate before commit). The final parent task records (appends
to the epic CHANGELOG; the semantic commit references the task, the
module-spec section, and any score changes, per CS-NN).

**List relevant files and resources with traceability.**
Name the files/configs/resources to be created or changed, each with a
one-line note, plus links to the PRD, epic overview, and CHANGELOG. This is
the traceability the verification framework depends on.

**Generate parent and sub-tasks in one pass.**
Mirror the PRD's scope exactly; no confirmation pause. Planning only — no
code.

---

## Clarification Step

Read the PRD, the API contract, and the coding standards. Ask **0–7
clarifying questions** — proceed directly if the PRD is complete and
unambiguous; otherwise ask, presence check first.

**First question (if needed) — presence check + epic confirmation:** "I am
generating the task list for epic [M-NN-MS\<m\>-E\<e\> — title]. I have the
PRD, the API contract, and the coding standards. Anything missing?"

Permitted topics: task granularity preference; which steps are risky enough to
need backup gates; which steps need human approval (privileged/sensitive);
test-task depth.

Ask one at a time. Then produce the task list in a single response.

---

## Kickoff

> Paste the Step 07 PRD, the API contract the epic realizes, and the Step 02
> coding standards above this line, then paste this line to trigger the
> prompt.

```
I am generating the task list for epic [M-NN-MS<m>-E<e> — title]. The
Implementation PRD, the API contract, and the coding standards are pasted
above. Please ask any clarifying questions one at a time (presence check
first), or proceed if the PRD is complete, then produce the task list.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.

```markdown
# Task List — [Title] (M-NN-MS\<m\>-E\<e\>)
# Phase 5 Step 08 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Epic:** [M-NN-MS\<m\>-E\<e\> — title]
**Maps To:** Implementation PRD [link]; epic overview [link]; Phase 4 module-spec section [reference]
**Owner:** [GOV-NN]
**Status:** [Draft / Ready for execution]
**Artifact Date:** [date]

---

## Relevant Files & Resources

- `[path/to/source]` - [what it implements; traces to PRD component]
- `[path/to/test]` - [spec-derived tests for the component]
- `[path/to/config or IaC]` - [if applicable]
- `…/Epic-EE/prd-e<e>-<slug>.md` - the PRD this task list executes
- `…/Epic-EE/overview/e<e>-<slug>.md` - the epic overview
- `…/Epic-EE/CHANGELOG.md` - epic change log to append

### Notes
- Tests are derived from the spec/contract, not the implementation.
- Prefer reversible actions; back up before risky steps and confirm success.
- Validation = running the tests, conformance checks, and scans for this epic.
- Privileged/sensitive steps STOP for human approval.

---

## Tasks

- [ ] 0.0 Prepare & safeguard
  - [ ] 0.1 Create and checkout the working branch (e.g. `feat/m-nn-ms<m>-e<e>-<slug>`)
  - [ ] 0.2 If the change is risky (migration, shared state), take a backup/snapshot and confirm
  - [ ] 0.3 Capture a baseline (current tests/coverage/scores) to compare against
- [ ] 1.0 [Parent task — e.g., Implement <component>]
  - [ ] 1.1 Implement `<component>` conforming to [SIC-NN / API op], enforcing [INV-N], following [CS-NN]; handle error modes [list]; emit [H-NN signals]
  - [ ] 1.2 Generate unit tests for `<component>` from the spec (acceptance: [criterion from PRD])
  - [ ] 1.3 Generate property-based tests for `<component>`: [property derived from INV-N]
  - [ ] 1.4 Generate contract/conformance test against [API op] (verify request/response shapes, status codes, error formats)
- [ ] 2.0 [Parent task — e.g., Implement authorization enforcement]
  - [ ] 2.1 Implement [authz per SEC-NN]; acceptance: [criterion]
  - [ ] 2.2 Generate security tests for the SEC-NN control
- [ ] 3.0 [Parent task — monitoring/observability]
  - [ ] 3.1 Implement and test the H-NN monitoring hooks for this epic
- [ ] 4.0 Validate the epic
  - [ ] 4.1 Run all tests; confirm coverage ≥ target
  - [ ] 4.2 Run conformance checks (API contract, data schema); confirm green
  - [ ] 4.3 Run security/dependency scans; confirm clean (or record accepted risks)
  - [ ] 4.4 Confirm performance within budget (where measurable)
- [ ] 5.0 Record the change
  - [ ] 5.1 Append to `…/Epic-EE/CHANGELOG.md`; update relevant notes
  - [ ] 5.2 Commit per CS-NN semantic-commit convention (reference task, module-spec section, score changes)
```

---

## Evaluation Checklist

Before accepting this task list as complete, verify:

- [ ] Every task traces to a PRD component, invariant, error mode, or
      requirement; no task widens scope beyond the PRD
- [ ] Code tasks and spec-derived test tasks are interleaved — each component
      has its implementation task AND its unit/property/contract test tasks
      (tests derived from the spec, not the implementation)
- [ ] Each task is specific enough for AI to produce correct output and for a
      reviewer to verify it (names the interface/contract, invariant, error
      modes, signals, and CS-NN convention)
- [ ] Each task carries an acceptance criterion drawn from the PRD's principle
      requirements
- [ ] Task 0.0 "Prepare & safeguard" is present (branch, backup-if-risky,
      baseline); backup/confirm/STOP gates are explicit on risky/sensitive
      steps
- [ ] Conformance test tasks (API contract) and monitoring-hook (H-NN) tasks
      are present
- [ ] A validation parent task (tests + conformance + scans + performance) and
      a record parent task (CHANGELOG + semantic commit per CS-NN) are present
- [ ] Relevant Files & Resources lists the artifacts with traceability links
- [ ] No code is produced; the PRD's scope is mirrored, not widened (gaps
      route back to Step 07)

---

*Step 08 of 15 in the Phase 5 Implementation Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `implementation.instructions.md`*
*Previous step: `step-07-implementation-prd.prompt.md`*
*Next step: `step-09-implement-loop.prompt.md` (executes this task list)*
