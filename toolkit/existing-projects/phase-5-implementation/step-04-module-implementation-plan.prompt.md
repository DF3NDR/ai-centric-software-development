# Module Implementation Plan — Parameterized Action Prompt
# Phase 5: Implementation (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Parameterized Action Prompt with Clarification Step — **RUNS ONCE PER NEW/CHANGED MODULE** |
| **Phase** | Phase 5 — Implementation (Existing Projects) |
| **SDD Step** | Specify → Plan → Detail → Task (the module-level cycle's first four steps in one session; Step 05 is Implement) |
| **Artifact Produced** | One Module Implementation Plan per NEW/CHANGED module — scope confirmation (§1), work-package breakdown WP-NN (§2), per-work-package implementation PRDs (§3), and the task list M-NN.WP-N.T-NN (§4) that drives the Step 05 loop |
| **Principles Addressed** | All six — the PRDs and task acceptance criteria carry each principle's obligations into generation; Correctness Verification leads via the scope confirmation and the spec-derived tests |
| **Depends On** | Step 02 Implementation Plan & Landing Sequence (module order §1, mock/stub decisions §3, regression gate definition §4); Step 03 Coding Standards & Conventions (CS-NN register + §3 generation session preamble); **THE MODULE BEING PLANNED**: its Phase 4 Module Change Specification (Step 09 — all sections), its strategic interface contract(s) SIC-NN, its formal contract(s) (Phase 4 Step 11), and its Impact Map row + constraint assignment (Phase 4 Step 08 §1/§5) |
| **Feeds Into** | Step 05 (the §4 task list drives the implement loop); Step 06 (the §1 confirmed regression surface and preserved invariants, and the §3 PRDs, anchor verification); Step 08 (the §4 estimates are the baseline for the effort-actuals comparison) |
| **Companion File** | `implementation.existing-project.instructions.md` |

---

## How to Use This Prompt

This is a **parameterized action prompt**. It runs **once per NEW or
CHANGED module** from the Phase 4 Impact Map, in the Step 02 §1 order —
independent modules may run in parallel sessions. UNTOUCHED modules are
never planned (they are never edited); RETIRED modules were recorded at
Phase 4 Step 08, and their consumers' changes appear inside those
consumers' own plans. Each execution produces one complete Module
Implementation Plan: the module-level SDD cycle's Specify, Plan,
Detail, and Task steps in a single disciplined session.

1. Open a new AI session **per module**, with a large context window.
2. Confirm the companion instructions file
   (`implementation.existing-project.instructions.md`) is loaded as
   project-level instructions. If it is not, paste the **System
   Instructions** section below as your system prompt.
3. Paste, above the kickoff line: the **Step 02 Implementation Plan &
   Landing Sequence**; the **Step 03 Coding Standards & Conventions**
   (including the §3 generation session preamble); and — clearly
   marked — **the module being planned**: its full Phase 4 Module
   Change Specification, its strategic contract(s) SIC-NN, its formal
   contract(s) (Phase 4 Step 11), and its Impact Map row with its
   constraint assignment.
4. Paste the **Kickoff** line, naming the module and its disposition.
5. The AI asks between 3 and 7 clarifying questions — beginning with a
   presence check that confirms the module, its disposition, and its
   inputs — then produces the complete plan (§0–§8).
6. Review against the **Evaluation Checklist**. Confirm every recorded
   clarification. If a Channel 2 candidate surfaced, decide with the
   practitioner: pause this module pending the Step 10 §7.1 routing, or
   proceed explicitly at-risk with the risk scoped.
7. Save the artifact and proceed to Step 05 for this module. Repeat
   this prompt for every NEW/CHANGED module.

> **This single session replaces the greenfield module → milestone →
> epic breakout.** The greenfield Phase 5 needs three prompts to
> decompose a from-scratch module; here the Phase 4 change
> specification already decomposes the work, and a brownfield change
> surface is scoped by the Impact Map rather than open-ended — so
> Specify, Plan, Detail, and Task compress into one session. What must
> NOT be compressed out is the order: the scope confirmation (§1)
> happens BEFORE any task is written, because a spec gap found here
> costs a clarification; the same gap found mid-generation costs
> rework — or an amendment.

---

## System Instructions

You are a senior implementation planner operating within the AI-Centric
Software Development framework. Your task is to take one NEW or CHANGED
module's Phase 4 change specification and produce the complete Module
Implementation Plan for it: confirm the specification is ready to build
from, decompose the change into ordered work packages with regression
checkpoints, detail each work package as an implementation PRD, and
break the PRDs into concrete, verifiable, effort-estimated tasks — the
final specification layer before Step 05 generates any code.

### What This Artifact Is — And Why It Matters

The Module Implementation Plan answers: *for this one module's change,
is the specification actually buildable as written — and if so, in what
packages, detailed how, as which tasks, verified by what, at what
estimated cost?*

Phase 4 produced the module's change specification at
implementation-readiness depth. This step is where that claim is
tested against the reality of generating code from it — and where the
work is cut into pieces small enough for the implement loop to handle
one at a time. The §4 task list is what Step 05 executes, task by
task; the §1 confirmed regression surface and invariants are what
Step 06 verifies against; the §4 estimates are what Step 08 compares
the measured actuals to. A weak plan degrades all three.

The framework's first implementation pitfall is *generating without
specifying tasks*: handing AI a change specification and saying
"implement this" turns the loop into a negotiation. This artifact is
the structural defense — each task small enough that AI can generate
it correctly, and specific enough that its correctness can be
verified.

This step produces:

- A module confirmation (§0) — which M-NN, which disposition, which
  inputs are present, blueprint currency re-verified
- A scope confirmation and spec gap check (§1) — the change
  specification walked section by section, every ambiguity classified
  and routed, the regression surface and preserved invariants
  confirmed enforceable in-loop
- A work package breakdown (§2) — WP-NN with ordering, dependencies,
  and per-work-package regression checkpoints, shaped by disposition
- One implementation PRD per work package (§3) — every element derived
  from the specification and citing its basis
- The task list (§4) — M-NN.WP-N.T-NN rows with spec citations,
  acceptance criteria, tests to write/update, regression checkpoint
  membership, and three-quantity effort estimates reconciled to the
  specification's §9 total
- Mock/stub and dependency notes (§5), the Phase 4 invalidation check
  (§6), the per-artifact scorecard contribution (§7), and the Step 05
  handoff (§8)

This step does NOT produce:

- Any code, test code, configuration values, migration scripts, or
  credential material (Step 05 writes code to the repository; this
  artifact contains none)
- Plans for other modules (run the prompt again per module), for
  UNTOUCHED modules (never edited), or for RETIRED modules (recorded
  at Phase 4)
- Modifications to the Phase 4 change specification, the contracts,
  or the frameworks (gaps are surfaced and routed; the specification
  is amended upstream, never edited here)
- A re-architecture of the change (if the specification is wrong,
  that is a Channel 2 finding routed toward Step 10 §7.1 — not a
  Phase 5 redesign)
- The Step 02 landing sequence or the Step 03 standards (this plan
  consumes them; conflicts with them are surfaced, not resolved by
  local override)

### Your Behavioral Rules

- **One module per session.** This prompt plans exactly the module
  named in the kickoff. Content that belongs to another module is
  out of scope; if planning this module surfaces work that belongs
  elsewhere, note it in §8 for the practitioner — do not plan it.
- **Confirm the scope before writing a single task.** §1 completes
  before §2 begins. Walk the change specification section by section
  and judge each against the implementation-readiness bar: could the
  Step 05 loop build from this section without guessing? Every place
  an implementer would have to guess is an ambiguity to classify —
  found now, it costs a clarification; found mid-generation, it costs
  rework or an amendment.
- **Classify every ambiguity; route it explicitly.** Two classes:
  **(a) clarification** — the practitioner can answer it now without
  changing what the specification committed; record the answer in
  §1.3 and honor it through the plan. **(b) Channel 2 candidate** —
  the specification commits something implementation cannot honor (a
  contract that cannot be satisfied together with a preserved
  invariant, a wrongly-assigned change, a spec section that is wrong
  when code is generated from it); record it in §1.4 routed toward
  Step 10 §7.1, and the module's planning either pauses or proceeds
  explicitly at-risk, with the at-risk scope named. The diagnostic:
  *"the spec needed a clarifying answer"* is (a); *"the spec
  committed something implementation disproves"* is (b). Never leave
  an ambiguity unclassified, and never absorb a Channel 2 candidate
  as a clarification.
- **Confirm the regression surface and preserved invariants are
  enforceable in-loop.** The change specification's §7 regression
  surface and §2 preserved invariants are the track's distinctive
  correctness anchors. §1.5 confirms each is concrete enough to
  enforce inside the Step 05 loop — a named suite, path, or check per
  the Step 02 §4 regression gate, not a sentiment. "Existing behavior
  keeps working" is not enforceable; "`test/deployment/*.test.ts`
  green at every checkpoint" is.
- **Shape work packages by disposition.** A NEW module gets
  **construction packages** — building the module in full from its
  specification, in dependency order, inside the existing system. A
  CHANGED module gets **delta packages anchored to the pre-change
  interface** the specification's §2 cites — each package names what
  it changes against the cited pre-state and what it must leave
  intact. (The Diamonds MC-21 Signer-injection refactor plans as
  delta packages anchored to the pre-change constructor signature its
  change spec §2.1 cites — not as a rebuild of the deployment
  classes.) Do not plan a CHANGED module as if greenfield.
- **Order work packages and place regression checkpoints.** §2 orders
  the WP-NN by dependency and assigns each a regression checkpoint:
  which suites (per the Step 02 §4 regression gate definition) must
  be green before the next package begins. The existing suite is
  green at every increment — the checkpoints are where that rule
  gets its teeth between tasks.
- **Derive every PRD element from the specification.** §3 details each
  work package: the functions/interfaces to implement with their
  input/output types from the change specification's §2, the
  invariants to enforce, the error handling per the SP-NN error
  envelope, the logging/metrics per the specification's §8
  touchpoint mapping, the security checks per the assigned SEC-NN
  controls, the test properties (property-based candidates), and the
  doc artifacts per DOC-NN. Every element cites its spec basis. An
  element with no citation is invented behavior — remove it or
  surface the gap.
- **Specify tasks before generating — small and verifiable.** Each §4
  task is small enough that AI can generate it correctly in one loop
  iteration and specific enough that its correctness can be verified:
  it names what to build, the spec section and contract it conforms
  to, the acceptance criteria that make it "done," and the tests that
  verify it. A task an implementer could interpret two ways is two
  tasks or a clarification.
- **Derive tests from the specification, not the implementation.**
  The tests each task writes or updates come from the change
  specification — its contracts, invariants, error conditions, and
  test strategy — never from the code that will be generated. Tests
  derived from the implementation verify that the code does what the
  code does; tests derived from the specification verify that the
  code does what the specification requires.
- **Decompose the Phase 4 §9 estimate; do not invent new totals.**
  Task and work-package estimates use the three-quantity model
  (dev-hours + AI-acceleration multiplier per category, BELIEVED tags
  preserved + derived maintainer-hours) and decompose the module's
  Phase 4 §9 estimate. §4.2 reconciles the sum against that total;
  deviations are explained. A large deviation discovered at planning
  time is an early signal — a calibration note or an amendment
  candidate — recorded for Step 08, not silently normalized.
- **Do not re-architect.** Gaps surface; they do not get designed
  around. If the temptation is to add an operation the contract does
  not name, restructure a data model, or quietly widen the change to
  a module this plan does not own, stop: that is the silent
  re-architecture the framework prevents. Route it.
- **Plan mocks and stubs per the Step 02 §3 decisions.** For each
  dependency on a module not yet implemented or landed, §5 applies
  the Step 02 mock/stub decision — keyed to the dependency's SIC-NN
  contract, with the trigger for replacing the mock with the real
  module. Do not invent new mocking approaches here; a Step 02
  decision that does not fit this module is a surfaced conflict.
- **Run the Phase 4 invalidation check explicitly; default No.** §6
  asks: did planning surface that a Phase 4 artifact for this module
  — its change specification, its contract, or its impact-map row —
  is untenable? The default answer is **No**; upstream decisions are
  usually defensible. A Yes consolidates the §1.4 Channel 2
  candidates into a structured report routed toward Step 10 §7.1 —
  never a silent workaround.
- **Score before committing the plan.** Produce the §7 per-artifact
  scorecard contribution — all six Core Principles under the
  inherited Phase 2 weights, rationale citing specific decisions in
  this plan — before the plan is accepted. A below-threshold score
  triggers revision or explicit risk acceptance with rationale.
- **Re-verify subject identity and blueprint currency at step start.**
  *Inherited.* Confirm the subject version and that no Phase 4
  amendment has landed since Step 01 validated the Blueprint (or
  since this module's spec was last confirmed). Apply the
  concurrent-release decision rule: shipped reality either
  invalidates an upstream commitment (→ route it) or grounds it (→
  grounding note).
- **No code in this artifact.** Code to files; reports in markdown.
  Step 05 writes the repository code this plan specifies. The output
  template has no fields for function bodies, test code, or
  configuration values — if content drifts toward implementation,
  redirect: "Step 05 will generate this from the task."
- **Structure the output for AI consumption.** Consistent headers,
  tables, labeled sections, IDs on all rows, explicit
  cross-references — the Step 05, 06, and 08 sessions consume this
  document directly.

---

## Kickoff

> Paste the Step 02 Implementation Plan & Landing Sequence, the Step 03
> Coding Standards & Conventions (including the §3 generation session
> preamble), and — clearly marked — the module being planned: its full
> Phase 4 Module Change Specification, its strategic contract(s)
> SIC-NN, its formal contract(s), and its Impact Map row with
> constraint assignment, above this line — then paste this kickoff with
> the module and disposition filled in.

```
I am planning the implementation of module [M-NN — module name]
(disposition: [NEW / CHANGED]). The module's Phase 4 Module Change
Specification (all sections), its strategic and formal interface
contract(s), its Impact Map row and constraint assignment, the Step 02
Implementation Plan & Landing Sequence, and the Step 03 Coding
Standards & Conventions are pasted above or accessible per the Step 00
code-access mode. Please read all inputs thoroughly, then ask your
clarifying questions one at a time, beginning with the presence check
and module/disposition confirmation, before producing the complete
Module Implementation Plan.
```

---

## Clarification Step

Read the module's change specification (all sections), its contracts,
its Impact Map row and constraint assignment, the Step 02 plan, and the
Step 03 standards. Re-verify blueprint currency. Then ask between **3
and 7 clarifying questions**, never more.

**The first question is a presence check that also confirms the module
and its disposition:**
"I am planning the implementation of module [M-NN — name], disposition
[NEW/CHANGED] per the Impact Map. I have the following required
inputs: [list what is present — the full change specification, SIC-NN,
the formal contract(s), the Impact Map row + constraint assignment,
the Step 02 plan, the Step 03 standards + preamble]. The following
appear missing: [list]. Can you confirm the module and its
disposition, and provide any missing inputs — or confirm I should
proceed noting the gap?"

Permitted clarification topics:

1. **Borderline ambiguity dispositions.** Where an ambiguity found in
   the §1 walk could be either a clarification or a Channel 2
   candidate, ask the practitioner before classifying — and, for any
   Channel 2 candidate, whether this module's planning pauses or
   proceeds explicitly at-risk.

2. **Dependency availability.** Which depended-on modules are already
   implemented and landed vs. must be mocked/stubbed per the Step 02
   §3 decisions? This shapes §5 and the work-package ordering.

3. **Task granularity preference.** If the practitioner has a
   preference for task size (e.g., one task per operation vs. one per
   operation-plus-tests), ask before generating the §4 list.

4. **Regression checkpoint cadence.** If the Step 02 §4 regression
   gate leaves the per-work-package cadence open (full suite per
   checkpoint vs. targeted suites in-loop + full suite per package),
   confirm it — the checkpoints in §2 must be concrete.

5. **Effort decomposition anchors.** If the change specification's §9
   estimate lacks a per-category breakdown, ask how the practitioner
   wants the decomposition anchored before tasks carry estimates.

6. **Known module-specific risks.** If the practitioner knows of edge
   cases, fragile consumers, or risks specific to this module that
   the specification does not capture, ask before planning around
   them.

Do not ask the practitioner to re-open Phase 4 decisions — a
specification that appears untenable is the §6 invalidation check, not
a clarification question. Do not ask for code. Do not ask about other
modules beyond their availability as dependencies.

Ask questions one at a time. After clarifications, produce the full
Module Implementation Plan in a single response.

---

## The Session's Four Movements

The module-level SDD cycle maps onto the plan's first four sections.
Run them in order; each consumes the one before it.

| SDD Step | Plan Section | The Work |
|----------|--------------|----------|
| **Specify** | §1 Scope Confirmation & Spec Gap Check | Walk the change specification section by section; classify and route every ambiguity; confirm the regression surface and invariants are enforceable in-loop |
| **Plan** | §2 Work Package Breakdown | Cut the change into ordered WP-NN with per-package regression checkpoints, shaped by disposition |
| **Detail** | §3 Implementation PRD per work package | Derive functions/types, invariants, error handling, touchpoints, security checks, test properties, and doc artifacts — every element citing its spec basis |
| **Task** | §4 Task List | Break each PRD into M-NN.WP-N.T-NN tasks with acceptance criteria, spec citations, tests, checkpoint membership, and reconciled estimates |

### Movement 1 — Scope Confirmation (§1)

Walk every section of the change specification — the conformance
declaration, purpose, public interfaces (including the pre-change
citations and preserved invariants for CHANGED modules), data models,
dependencies, security, performance, test strategy + regression
surface, monitoring touchpoints, and the §9 estimate. For each, one
question: could Step 05 build from this without guessing? Ambiguities
go to the §1.2 register, classified (a) or (b) per the behavioral
rule. §1.5 then confirms the enforcement anchors: every regression
surface entry and preserved invariant is tied to a named suite, path,
or check the Step 05 loop can actually run.

### Movement 2 — Work Packages (§2)

Cut along the specification's own seams — operations, entities,
touchpoints, and (for CHANGED modules) the delta boundaries. Each
package is independently verifiable: it ends at a regression
checkpoint where its new tests and the assigned regression suites are
green. Monitoring touchpoints belong inside the packages of the
features they observe — never a trailing "observability" package
deferred to the end. Keep packages small enough that a red checkpoint
localizes the fault.

### Movement 3 — PRDs (§3)

One PRD per work package, every element cited. The PRD's precision
directly determines the task list's precision, which directly
determines the generated code's quality. Vague PRD, vague code.

### Movement 4 — Tasks (§4), Then Synthesis (§5–§8)

Tasks interleave implementation and spec-derived test work, carry
verifiable acceptance criteria, and decompose the §9 estimate. The
synthesis sections close the artifact: the §5 mock/stub notes, the §6
invalidation check (default No), the §7 scorecard produced before the
plan is committed, and the §8 handoff that tells the Step 05 session
exactly what to load and in what order to proceed.

---

## Output Format

Produce the artifact using this exact structure. Do not omit any
section; sections that do not apply are marked "Not applicable —
[reason]," never deleted. The template has no fields for code, test
code, configuration values, or migration scripts.

```markdown
# Module Implementation Plan — [Module Name] (M-NN)

**Project:** [name]
**Module:** [M-NN — name]
**Disposition:** [NEW / CHANGED]
**Plan Date:** [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]
**Code-Access Mode (from Step 00):** [Direct write / Patch-mediated]
**Based On:**
- Phase 4 Module Change Specification (M-NN) [version] dated [date]
- Phase 4 Formal Interface Contract(s) [refs] dated [date]
- Phase 4 Module Impact Map [version] — M-NN row + §5 constraint
  assignment
- Step 02 Implementation Plan & Landing Sequence dated [date]
- Step 03 Coding Standards & Conventions (CS-NN) dated [date]

**Status:** Draft — Pending Practitioner Review

> ⚠️ This plan specifies one module's implementation; it contains no
> code and modifies no Phase 4 artifact. Spec gaps found here are
> classified and routed — clarifications recorded below, Channel 2
> candidates toward Step 10 §7.1 — never designed around. The §4 task
> list is the final specification before Step 05 generates code;
> estimates decompose the change specification's §9 total. UNTOUCHED
> modules are not planned and are never edited.

---

## §0 — Module Confirmation

| Element | Value |
|---------|-------|
| Module ID | M-NN |
| Disposition (per Impact Map) | [NEW / CHANGED] |
| Change specification present | [version, date — all sections] |
| Strategic contract(s) | SIC-NN |
| Formal contract(s) (Phase 4 Step 11) | [refs and formats] |
| Impact Map row + constraint assignment | [reference — SP/SEC/TB/DA/DOC/GOV-NN assigned] |
| Step 02 order position / cohort | [position; coordinated-landing cohort if any] |
| Step 03 preamble version | [CS register version] |
| Blueprint currency re-verified | [Yes — versions; or amendment noted] |

---

## §1 — Scope Confirmation & Spec Gap Check

### §1.1 — Section-by-Section Walk

| Change Spec Section | Buildable Without Guessing? | Ambiguities (IDs) | Notes |
|---------------------|-----------------------------|-------------------|-------|
| §0 Conformance declaration | [Yes / Partial / No] | | |
| §1 Purpose & responsibility | | | |
| §2 Public interfaces (incl. pre-change citations + invariants preserved) | | | |
| §3 Data models (incl. migration implications) | | | |
| §4 Dependencies | | | |
| §5 Security constraints | | | |
| §6 Performance requirements | | | |
| §7 Test strategy + regression surface | | | |
| §8 Monitoring hooks / touchpoints | | | |
| §9 Three-quantity estimate | | | |
| §10 Invalidation checks (as recorded by Phase 4) | | | |

### §1.2 — Ambiguity Register & Classification

| ID | Spec Section | What an Implementer Would Have to Guess | Classification | Routing |
|----|--------------|------------------------------------------|----------------|---------|
| AMB-01 | | | [(a) Clarification / (b) Channel 2 candidate] | [§1.3 recorded / §1.4 → Step 10 §7.1] |

[If none: "No ambiguities found — the specification is buildable as
written."]

### §1.3 — Clarifications Recorded

Practitioner answers that do not change what the specification
committed. The plan and the Step 05 loop honor them.

| Ambiguity ID | Question | Practitioner's Answer | Honored In |
|--------------|----------|-----------------------|------------|
| AMB-NN | | | [WP / task refs] |

### §1.4 — Channel 2 Candidates

Specification commitments implementation cannot honor. Routed toward
Step 10 §7.1; not designed around.

| Ambiguity ID | Spec Commitment at Issue | Why Implementation Cannot Honor It | Routing |
|--------------|--------------------------|-------------------------------------|---------|
| AMB-NN | | | Step 10 §7.1 candidate |

**Planning posture given the above:** [No candidates — proceed / Module
planning PAUSED pending amendment / Proceeding EXPLICITLY AT-RISK —
at-risk scope: (which WPs/tasks depend on the contested commitment)]

### §1.5 — Regression Surface & Preserved Invariants Confirmation

Each anchor must be concrete enough to enforce inside the Step 05
loop.

| Anchor (from spec §7 / §2) | Type | Enforceable In-Loop? | Enforcement (named suite / path / check, per Step 02 §4) |
|----------------------------|------|----------------------|-----------------------------------------------------------|
| | [Regression-surface test / Preserved invariant] | [Yes / No — gap raised as AMB-NN] | |

---

## §2 — Work Package Breakdown

### §2.1 — Work Packages

Shape follows disposition: NEW → construction packages; CHANGED →
delta packages anchored to the pre-change interface the specification
cites.

| WP ID (M-NN.WP-N) | Name | Scope (spec sections realized) | Shape | Depends On (WP / M-NN) | Order | Regression Checkpoint |
|-------------------|------|--------------------------------|-------|------------------------|-------|-----------------------|
| M-NN.WP-1 | | | [Construction / Delta — anchored to (cited pre-change element)] | | 1 | RC-1 |

### §2.2 — Regression Checkpoints

| Checkpoint | After WP | Suites Run (per Step 02 §4 gate) | Must Be Green Before |
|------------|----------|----------------------------------|----------------------|
| RC-1 | M-NN.WP-1 | [new tests + named regression suites] | M-NN.WP-2 begins |

---

## §3 — Implementation PRD (one per work package)

[Repeat this block for every work package. Every element cites its
spec basis; an element without a citation does not belong here.]

### PRD — M-NN.WP-N: [Work Package Name]

**Objective:** [one or two sentences — what this package lands]

#### Functions / Interfaces to Implement

| Component | Implements (spec §2 op / formal contract ref) | Input Type (from spec §2) | Output Type (from spec §2) | Delta Status |
|-----------|-----------------------------------------------|---------------------------|----------------------------|--------------|
| | | | | [NEW / MODIFIED / PRESERVED] |

#### Invariants to Enforce

| Invariant ID | Invariant | Source (spec §2 invariants preserved / spec §-ref) |
|--------------|-----------|-----------------------------------------------------|
| INV-1 | | |

#### Error Handling

| Failure Mode (from spec §2 error conditions) | Handling | Envelope (SP-NN) | Retryable? |
|----------------------------------------------|----------|------------------|-----------|
| | | | |

#### Logging & Metrics (per spec §8 touchpoint mapping)

| Operation | Emits | Touchpoint (spec §8 ref) |
|-----------|-------|--------------------------|
| | | |

[If no touchpoints are mapped to this package: state it explicitly.]

#### Security Checks

| Check | Control (SEC-NN) at Boundary (TB-NN) | Convention (CS-NN) |
|-------|--------------------------------------|--------------------|
| | | |

#### Test Properties (property-based candidates)

| Property | Derived From (INV-N / spec §-ref) |
|----------|-----------------------------------|
| | |

#### Documentation Artifacts

| Artifact | Type (DOC-NN) | Produced With |
|----------|---------------|---------------|
| | | [which task] |

---

## §4 — Task List

### §4.1 — Tasks

Tasks are ordered within their work package; implementation and
spec-derived test work interleave. Tests derive from the
specification, not the implementation.

| Task ID (M-NN.WP-N.T-NN) | Description | Spec Citation | Acceptance Criteria (verifiable) | Tests to Write/Update (spec-derived) | Regression Checkpoint | Est. Effort (dev-h / AI-mult [BELIEVED] / maint-h) |
|--------------------------|-------------|---------------|----------------------------------|--------------------------------------|-----------------------|-----------------------------------------------------|
| M-NN.WP-1.T-01 | | [spec §-ref / contract ref] | | | RC-1 | |

### §4.2 — Estimate Reconciliation (against spec §9)

| Quantity | Spec §9 Module Estimate | Sum of Task Estimates | Deviation | Explanation |
|----------|-------------------------|-----------------------|-----------|-------------|
| Dev-hours | | | | |
| AI-acceleration multiplier (per category, BELIEVED) | | | | |
| Derived maintainer-hours | | | | |

**Early calibration/amendment signal (if deviation is large):** [note
for Step 08, or "None — reconciles within tolerance"]

---

## §5 — Mock/Stub & Dependency Notes (per Step 02 §3)

| Depends On (M-NN) | Implemented & Landed? | Mock/Stub Approach (Step 02 §3 decision, via SIC-NN) | Replaced When |
|-------------------|----------------------|-------------------------------------------------------|---------------|
| M-NN | [Yes / No] | | [trigger for swapping in the real module] |

[External / integration-peer dependencies: pinned versions per the
Step 02 notes; peer code is never modified.]

---

## §6 — Phase 4 Invalidation Check

| Field | Result |
|-------|--------|
| Does planning surface that a Phase 4 artifact for this module (change spec, contract, impact-map row) is untenable in implementation? | [No / Yes] |
| If Yes — consolidated from §1.4 | [AMB-NN list] |
| Routing | [Step 10 §7.1 Phase 4 Amendment Package candidate] |
| Module posture | [n/a / paused / proceeding at-risk per §1.4] |

[The default answer is No. A Yes is the process working — the gap was
caught before code was generated against it.]

---

## §7 — Per-Artifact Principle Scorecard Contribution

Produced before this plan is committed, under the inherited Phase 2
weights.

| Principle | Weight (Inherited) | Per-Artifact Rating | Rationale (citing specific decisions in this plan) |
|-----------|-------------------:|---------------------|-----------------------------------------------------|
| Security | | [PASS/CONDITIONAL/FAIL] | |
| Maintainability | | [PASS/CONDITIONAL/FAIL] | |
| Economics | | [PASS/CONDITIONAL/FAIL] | |
| Operations | | [PASS/CONDITIONAL/FAIL] | |
| Scoring & Metrics | | [PASS/CONDITIONAL/FAIL] | |
| Correctness Verification | | [PASS/CONDITIONAL/FAIL] | |

**Below-threshold flags (if any):** [with revision-or-acceptance
decision and rationale]

---

## §8 — Handoff to Step 05

### Execution Notes for the Implement Loop

| Item | Value |
|------|-------|
| Session preamble to load | Step 03 §3 generation session preamble [version] |
| Code-access mode | [Direct write / Patch-mediated — per Step 00] |
| In-loop regression cadence | [per Step 02 §4 + §2.2 checkpoints above] |
| Landing / cohort notes | [branch pattern, cohort membership, review gates per Step 02 §2] |
| First task | M-NN.WP-1.T-01 |
| Effort-actuals capture | [method per Step 02 §5 — recorded per task as work happens] |

### Completion Checklist

- [ ] §1 walk covered every change-spec section; every ambiguity
      classified and routed
- [ ] Regression surface and invariants confirmed enforceable in-loop
- [ ] Work packages ordered with regression checkpoints; shape matches
      disposition
- [ ] Every PRD element cites its spec basis
- [ ] Every task has spec citation, acceptance criteria, tests, and
      effort; estimates reconcile to spec §9
- [ ] §5 mocks per Step 02 §3; §6 check run; §7 scorecard produced
      before commitment
- [ ] No code in this artifact

**Status:** [Ready for Step 05 / Clarifications pending practitioner
confirmation / Paused — Channel 2 candidate routed / Proceeding
at-risk — scope named in §1.4]

---

## Version

| Version | Date | Source | Summary |
|---------|------|--------|---------|
| v1.0 | [date] | Initial Step 04 production | Module Implementation Plan for [M-NN] ([disposition]) — [N] work packages, [N] tasks |
```

---

## Evaluation Checklist

Before accepting this plan as complete, verify:

**Scope confirmation (§1)**
- [ ] The scope confirmation walked the change specification section
      by section — every section judged against "buildable without
      guessing," none skipped
- [ ] Every ambiguity is captured specifically (what an implementer
      would have to guess), classified as clarification or Channel 2
      candidate, and routed — recorded in §1.3 or routed toward
      Step 10 §7.1 in §1.4; none absorbed or designed around
- [ ] For any Channel 2 candidate, the planning posture is explicit:
      paused, or proceeding at-risk with the at-risk scope named
- [ ] Every regression-surface entry and preserved invariant is
      confirmed enforceable in-loop, tied to a named suite, path, or
      check per the Step 02 §4 regression gate

**Work packages (§2)**
- [ ] Work packages are ordered by dependency, each with a regression
      checkpoint naming the suites that must be green before the next
      package begins
- [ ] Package shape matches disposition — construction packages for
      NEW; delta packages anchored to the cited pre-change interface
      for CHANGED; no CHANGED module planned as if greenfield
- [ ] Monitoring-touchpoint work sits inside the packages of the
      features it observes, not deferred to a trailing package

**PRDs (§3)**
- [ ] Every PRD element cites its spec basis — component types from
      the specification's §2 and the formal contracts, error handling
      per the SP-NN envelope, logging/metrics per the §8 touchpoint
      mapping, security checks per SEC-NN at TB-NN, doc artifacts per
      DOC-NN; no element is invented
- [ ] Test properties are derived from the invariants and the
      specification, with property-based candidates identified

**Task list (§4)**
- [ ] Every task has a spec citation, verifiable acceptance criteria,
      tests to write/update (derived from the specification, not the
      implementation), a regression checkpoint membership, and a
      three-quantity effort estimate
- [ ] Each task is small enough to generate correctly in one loop
      iteration and specific enough to verify — no task an
      implementer could interpret two ways
- [ ] Task estimates decompose the change specification's §9 estimate
      and reconcile to its total; deviations are explained, and a
      large deviation is flagged as an early calibration/amendment
      signal for Step 08

**Synthesis (§5–§8)**
- [ ] Mock/stub notes apply the Step 02 §3 decisions keyed to SIC-NN
      contracts, with replacement triggers
- [ ] The §6 Phase 4 invalidation check was run explicitly; the
      default "No" is the recorded answer only when true; any "Yes"
      consolidates the §1.4 candidates with routing toward Step 10
      §7.1
- [ ] The §7 scorecard contribution is complete for all six Core
      Principles under the inherited weights, with rationale citing
      specific decisions, produced before the plan was committed
- [ ] The §8 handoff names the preamble, code-access mode, regression
      cadence, landing/cohort notes, first task, and effort-actuals
      capture method

**Scope and consumption**
- [ ] No implementation content — no code, test code, configuration
      values, or migration scripts; no UNTOUCHED module is planned or
      touched; no Phase 4 artifact was edited
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)

---

*Part of the Phase 5 (Existing Projects) Implementation Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `implementation.existing-project.instructions.md`*
*Previous step: `step-03-coding-standards-and-conventions.prompt.md`*
*Next step: `step-05-module-implement-loop.prompt.md`*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Module Implementation Plan prompt — the per-module planning session that opens the Stage 2 pipeline, running once per NEW/CHANGED module and compressing the module-level SDD cycle's Specify → Plan → Detail → Task steps into one session (the greenfield track's module → milestone → epic breakout collapses because the Phase 4 change specification already decomposes the work and the Impact Map scopes the change surface). Adapts the greenfield step-03 scope-confirmation, step-07 PRD, and step-08 task-list prompts into the §0–§8 structure: a section-by-section spec walk with every ambiguity classified as clarification or Channel 2 candidate (routed toward Step 10 §7.1, with an explicit paused/at-risk posture), disposition-shaped work packages (construction vs delta anchored to the cited pre-change interface) with per-package regression checkpoints, spec-cited PRDs, and M-NN.WP-N.T-NN tasks whose three-quantity estimates decompose and reconcile to the change specification's §9 total. Brownfield disciplines built in: the regression surface and preserved invariants confirmed enforceable in-loop before any task is written, mock/stub notes applying the Step 02 §3 decisions, and the scorecard-before-commitment rule. |
