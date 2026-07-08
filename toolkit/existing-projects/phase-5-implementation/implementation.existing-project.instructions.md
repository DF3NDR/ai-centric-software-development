# Phase 5 — Implementation Instructions (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Purpose of This File

This file provides overarching instructions for AI assistants operating in
**Phase 5: Implementation** of the AI-Centric Software Development Playbook
**when applied to an existing codebase** rather than a greenfield project.
It establishes context, methodology, behavioral expectations, and output
standards that apply across all tool sets used in this phase.

It is the companion to the greenfield Phase 5 instructions file
(`toolkit/new-projects/phase-05-implementation/`). The SDD cycle, the six
Core Principles, the implementation feedback loop, the traceability
discipline, and the phase-gate discipline are identical. What changes is
**what gets implemented and where it lands**:

- A greenfield project asks *"how do we build these modules from their
  specifications, from scratch?"* — constructing modules, inventing coding
  standards, and building test suites, CI, and infrastructure from
  nothing.
- An existing project asks *"how do we land these specified changes inside
  working code that already has consumers, tests, conventions, and a
  release discipline?"* — Phase 4 produced module **change**
  specifications with dispositions (NEW / CHANGED / UNTOUCHED / RETIRED),
  regression surfaces, and formal contracts. Phase 5 implements the
  deltas, keeps the existing suite green at every increment, and measures
  the actual effort against the estimates the track has carried since
  Phase 2.

Place this file at
`.github/implementation.existing-project.instructions.md` or attach it as
project-level instructions in your AI environment (Claude Project
Instructions, VS Code AI instructions, Cursor rules). It is loaded once as
persistent context and remains active across all Phase 5 prompt sessions.

> **The AI-Centric Playbook Skill is available.** *(Inherited from Phase 3
> v1.1.)* This toolkit has a companion **Skill** at
> `skills/ai-centric-playbook/` (SKILL.md + reference files on the Six
> Core Principles, the SDD cycle, and the building-blocks framework). Load
> it when a decision benefits from that depth, following the skill's own
> load-on-demand guidance.

---

## Framework Context

You are operating as an **implementation generator, regression guardian,
and verification partner** — not a blank-slate module builder. Your role
is to take the Phase 4 Architecture Blueprint Bundle and produce the
working, tested, scored, and verified changes it specifies — inside the
codebase that already exists, without re-architecting what Phase 4 locked,
without breaking what the change was never meant to touch, and without
letting AI-generated code bypass the verification stack.

Phase 5 consumes the Phase 4 outputs as authoritative input:

- **The Architecture Blueprint Bundle** (Phase 4 Step 12) — the
  authoritative source of truth: §1 artifact catalog, §2 Module Impact
  Map and change specifications, §3 formal interface contracts with
  traceability, §5 scorecard refresh (the Phase 5 baseline), §6 cost &
  capacity check, §7.1 the Phase 5 handoff summary.
- **The Module Change Specifications** (Phase 4 Step 09, one per
  NEW/CHANGED module) — the primary implementation input. Each carries
  the pre-change interface (cited), the post-change contract at field
  level, data model deltas, dependencies, security constraints,
  performance requirements anchored to Phase 1 measured baselines, the
  test strategy with the **regression surface** (existing behavior and
  existing tests that must keep passing), monitoring-touchpoint mapping,
  and the three-quantity effort estimate (§9).
- **The Formal Interface Contracts** (Phase 4 Step 11) — machine-readable
  contracts (language-level interface declarations, OpenAPI, protobuf,
  event schemas, data-artifact schemas, other) that generation conforms
  to and conformance checking verifies against.
- **The cross-cutting frameworks** — SP-NN patterns, SEC-NN controls +
  TB-NN boundaries, DA-NN data constraints, DOC-NN documentation types,
  GOV-NN governance (review gates apply to Phase 5 changes), all
  provenance-tagged ([EXISTING-CODIFIED] / [EXTENDED] / [NEW]).
- **Behind Phase 4:** the Phase 3 Design Specification Bundle (§2
  Coordination Map cohorts, §3 verification instruments Phase 6 will
  execute), the Phase 2 Improvement Plan (principle weights, cost model,
  HC-NN capacity envelope, MC-NN), and the Phase 1 Current-State Report
  (measured operational baselines).

The phase's central discipline is inherited from the greenfield variant
unchanged — **generate from the spec, verify against the spec, keep them
aligned** — with the track's addition: **and keep the existing system
green while you do it.**

The team working in this phase is typically small (1–5 people). AI is the
force multiplier — not the decision-maker. Every output is reviewed,
evaluated, and approved by the practitioner before it advances.

### What Is Different About Existing-Project Phase 5 Work

Three shifts matter, and they shape every prompt and every artifact:

1. **From module construction to change integration in a living
   codebase.** Greenfield Phase 5 builds modules from scratch in an
   empty repository. Existing-project Phase 5 lands **deltas** into
   working code with existing consumers, existing tests, and existing
   CI. The regression surface from each Phase 4 change specification
   (§7) is a first-class gate inside the implement loop: the existing
   suite must be green at every increment, not just at the end. Depth
   follows disposition — a NEW module is constructed in full; a CHANGED
   module is modified against its cited pre-change interface with its
   preserved invariants enforced; UNTOUCHED modules are not edited, full
   stop (a needed edit to an UNTOUCHED module is a Phase 4 impact-map
   error — surface it, do not just make the edit).

2. **From invented conventions to reconciled conventions and
   pipelines.** Greenfield Phase 5 invents coding standards and builds
   CI/CD from nothing. The existing project already has a code style,
   lint and formatter configs, test harnesses, CI pipelines, commit
   conventions, and a release discipline. Phase 5 **codifies them**
   (CS-NN with provenance tags) and integrates the framework's
   semantic-commit and traceability discipline *into* the existing
   conventions — a repo already using Conventional Commits gets task and
   spec references added to its existing format, not a new format.
   Landing follows the existing branch/release discipline and the
   coordinated-landing cohorts Phase 4 assigned from the Phase 3
   Coordination Map.

3. **From estimated effort to measured calibration.** The track's
   three-quantity cost model has carried BELIEVED-tagged AI-acceleration
   multipliers since Phase 2. Phase 5 is where actual effort is finally
   **measured**: per-task and per-module actuals are recorded against
   the Phase 4 §9 estimates, deviations are analyzed (wrong estimate →
   cost-model calibration; unexpectedly complex change → candidate
   Phase 4 amendment), and the multiplier calibration data graduates
   BELIEVED → ESTIMATED for the Phase 7 calibration handoff and
   next-cycle Phase 2. Performance verification likewise anchors to the
   Phase 1 *measured* baselines rather than greenfield's simulated
   benchmarks.

These three shifts produce a leaner Phase 5 toolkit (11 steps vs the
greenfield variant's 15 prompts) without losing coverage: the greenfield
module→milestone→epic breakout hierarchy collapses into one per-module
implementation-planning step, because the Phase 4 change specifications
already decompose the work and the change surface of an existing project
is scoped by the Impact Map rather than open-ended.

---

## The Per-Module Nested SDD Cycle in This Phase

Phase 5 runs the SDD cycle at the module level. Each NEW/CHANGED module
goes through its own cycle, with its Phase 4 change specification as the
starting input. The hierarchy is **Module → Work Package → Task**:

| SDD Step | Phase 5 Activity | Toolkit Prompt |
|----------|------------------|----------------|
| **Specify** | Confirm the module's change scope against its specification; surface spec gaps before coding | Step 04 §1 (scope confirmation) |
| **Plan** | Decompose the change into work packages (WP-NN) with ordering and regression checkpoints | Step 04 §2 |
| **Detail** | Produce the implementation PRD per work package | Step 04 §3 |
| **Task** | Break the PRD into concrete, verifiable tasks with acceptance criteria | Step 04 §4 |
| **Implement** | Generate → test (incl. regression suite) → score → conformance → refine; semantic commits; effort actuals | Step 05, then Steps 06–08 verify, review, and score |

### The Implementation Feedback Loop

The tactical loop runs inside Step 05 for every task: **generate code →
run the new tests AND the regression suite → score against principles →
check conformance against the formal contracts and the change
specification → refine until all checks pass.** Above it sit two
strategic loops:

- **Module-level feedback** (Steps 06–08): as each module's work
  packages complete, the module is verified, independently reviewed, and
  scored — with effort actuals recorded — before the next module (or
  cohort) proceeds.
- **Change-surface-level feedback** (Stage 3): as modules complete,
  coordinated-landing cohorts assemble, cross-module contract tests run,
  the full regression suite runs, and the aggregate scorecard and cost
  actuals consolidate.

When any loop reveals a problem that traces to an earlier phase, the
correct response is the amendment cycle (Step 10), not a silent
workaround.

---

## The Six Core Principles — Applied to Phase 5 (Existing Projects)

Phase 5 contributes per-artifact and per-module scores into the principle
scorecard frame Phase 2 established, Phase 3 refreshed, and Phase 4
refreshed again. The weights are inherited from Phase 2 Step 02 unchanged.
Implementation is where the principles become measurable reality.

### 1. Security
- Continuous scanning on every commit: dependency audits, static
  analysis, secrets detection — run through the project's *existing*
  security tooling where it exists (codified at Step 03), extended where
  the change surface requires.
- Every generated change applies its assigned SEC-NN controls at its
  TB-NN boundaries; the AI-vs-AI review (Step 07) audits security
  independently.
- A change must not degrade the security posture of UNTOUCHED modules
  (e.g., by weakening a shared dependency or widening an interface).

### 2. Maintainability
- Coverage targets from each change specification's §7 are met; the
  regression surface stays green; code quality metrics (complexity,
  coupling) are tracked against the existing codebase's baseline, not an
  idealized one.
- Documentation is produced per the DOC-NN strategy alongside the code —
  inline docs, changed-API docs, and the doc artifacts the Phase 4
  documentation strategy assigned to the change surface.
- Generated code reads like the surrounding code: the CS-NN standards
  codify the existing idiom precisely so AI output does not introduce a
  second style.

### 3. Economics
- Actual effort is tracked per task and per module in the three-quantity
  model (dev-hours + AI-acceleration multiplier + derived
  maintainer-hours) against the Phase 4 §9 estimates.
- Deviations are signals: a wrong estimate calibrates the cost model; an
  unexpectedly complex implementation is a candidate Phase 4 amendment.
- Step 10 aggregates actuals against the Phase 2 cost model and HC-NN
  capacity envelope and produces the multiplier calibration table
  (BELIEVED → ESTIMATED) for Phase 7 and next-cycle Phase 2.

### 4. Operations
- The Phase 3 observability touchpoints mapped to each module (change
  specification §8) are implemented and tested alongside the features —
  not deferred.
- The existing deployment/release shape is preserved: changes land
  through the existing pipeline, and any pipeline change is itself a
  specified, tested artifact.
- If Phase 2 explicitly deprioritized Operations, the deferral is
  preserved as deferral — implement the touchpoints Phase 3 designed, no
  more, no less.

### 5. Scoring & Metrics
- Fully operational: coverage, complexity, security scans, conformance
  results, performance benchmarks, and regression status are collected
  continuously and per module (Step 08), aggregated at Step 10.
- Per-module scorecard contributions are produced under the inherited
  weights before the module is declared complete; regressions against
  the Phase 4 baseline are flagged when they occur, not at the gate.

### 6. Correctness Verification
- Fully operational: conformance checking against the Phase 4 formal
  contracts on every increment; preserved-invariant and property-based
  verification; formal verification for the components Phase 4
  designated; AI-vs-AI review as an independent audit layer.
- The Phase 3 Bundle §3 verification instruments are implemented or made
  executable during Phase 5 so Phase 6 can run them — readiness is
  verified at Step 06 §5.
- The regression surface confirmation (Step 06 §3) is the track's
  distinctive correctness check: the change did what it should *and did
  not do what it should not*.

---

## Multi-Repo Evidence Scoping

*Inherited from Phases 1–4.* The classification of each repository
continues:

| Role | Meaning | Phase 5 Posture |
|------|---------|----------------|
| **Subject** | The repository being improved | All Phase 5 code changes land here, through the existing branch/release discipline |
| **Integration Peer** | A separate repository the subject integrates with | Peer-facing contracts are honored from the subject's side; peer code is not modified; integration testing against peers uses the peers' released versions (or pinned refs), noted in Step 02 |
| **Evidence Source** | A repository used for reference | Cited in implementation decisions without being touched |

If Phase 5 work surfaces that an integration peer must change for the
cohort to land, that is a Step 10 finding (forward handoff or amendment
candidate), not an in-scope edit.

---

## Code Access Calibration — The Phase 5 Requirement

*Inherited from Phases 1–4, with a hard Phase 5 sharpening.* The three
modes (Interview-only / Search-primary / Hybrid with explicit flags) and
the [CONFIRM]/[AWARE]/[QUESTION] flags continue for evidence claims. But
Phase 5 *writes code*:

> **Implementation cannot run Interview-only.** Step 05 requires either
> **direct write access** to the subject repository (filesystem MCP,
> Claude Code, IDE integration) or **patch-mediated mode** (the AI
> produces complete diffs/files; the practitioner applies them and pastes
> back test results). Patch-mediated mode is slower and noted in the
> Step 00 document; every other capability degradation is flagged per the
> standing discipline. Test execution follows the same rule: the loop
> needs test results — from AI-run tests (preferred) or
> practitioner-run tests (patch-mediated).

Announce the mode at Step 00. If it shifts mid-phase, amend the Step 00
document (§7) and flag affected artifacts.

---

## The Principle Scorecard — Inherited Through Phase 4, Contributed-To By Phase 5

### What Phase 5 Inherits

The weights from Phase 2 Step 02, unchanged. The **Phase 4 scorecard
refresh (Blueprint §5) is the baseline Phase 5 measures against**,
including any CONDITIONALs Phase 4 carried forward with named
remediation — Step 01 confirms which of those remediations are Phase 5's
to deliver.

### What Phase 5 Contributes

Per-artifact contributions from the project-level steps (02, 03) and
per-module contributions from the module pipeline (Steps 04–08,
consolidated in Step 08's per-module scorecard), plus the integration
evidence from Step 09. Step 10 aggregates the contributions into the
Phase-5-level refresh.

### How the Refresh Works

At Step 10 synthesis, the inherited Phase 4 refresh plus the aggregated
Phase 5 contributions produce the Phase-5-level scorecard, with the same
aggregation rules the track has used since Phase 3 (all PASS → PASS; any
CONDITIONAL → CONDITIONAL with named remediation; any FAIL → FAIL and
return upstream) and the target distribution check (all-PASS strongest;
≤2 CONDITIONALs acceptable; any FAIL blocks; uniform status itself
checked). Phase 4 CONDITIONALs specifically addressed by Phase 5 work
resolve to PASS; unaddressed ones persist with their remediation owners.

---

## The Feedback Channels

Phase 5 work surfaces problems in upstream outputs through four distinct
channels. All are first-class. Phase 5 is the deepest-reaching gate in
the existing-projects track so far: it can require amendment of Phase 4,
Phase 3, or Phase 2.

### Channel 1: Upstream Toolkit Gaps (via Step 01)

The two-scope split, inherited unchanged. Every validation gap is
classified **Phase 5 local** (resolve within Phase 5 or accept as
documented limitation) or **upstream toolkit** (the Phase 4 toolkit — or
transitively an earlier toolkit — was structurally incomplete; queue for
that toolkit's revision in a separate session; non-blocking).

### Channel 2: Phase 4 Run Amendment (via Step 10 §7.1)

Implementation reveals that a *specific Phase 4 artifact for this run* is
untenable: a change specification proves ambiguous or wrong when code is
generated from it, a formal contract cannot be satisfied together with a
preserved invariant, the impact map assigned a change to the wrong
module, or an UNTOUCHED module turns out to need edits. The practitioner
returns to Phase 4 (the responsible step re-runs), and Phase 5 re-enters
with the amended blueprint. Task-level ambiguities that the practitioner
can resolve without changing the specification's commitments are Phase 5
local clarifications — Channel 2 is for gaps that change what Phase 4
committed.

### Channel 3: Phase 3 Run Amendment (via Step 10 §7.2)

Implementation-level evidence invalidates a *Phase 3 design
specification* in a way no Phase 4 re-mapping can fix — e.g., a designed
contract surface proves unimplementable against the real dependency
behavior, or a measured performance characteristic contradicts a design
assumption. Cascades: Phase 3 amends the brief, Phase 4 re-enters for the
affected modules, then Phase 5 re-enters.

### Channel 4: Phase 2 Run Amendment (via Step 10 §7.3)

The deepest path: implementation evidence invalidates a *Phase 2
commitment* — the chosen mechanism for an MC is untenable in
implementation no matter how it is re-specified, or the measured effort
actuals breach the cost model / HC-NN capacity envelope beyond
calibration tolerance. Cascades through Phase 3 and Phase 4 re-entry.

### How the Channels Differ

| Channel | Trigger | Output | Blocks Phase 6 Handoff? |
|---------|---------|--------|------------------------|
| **1 — Upstream toolkit gap** | An upstream *toolkit* was structurally incomplete | Step 01 §9.2 entry | No |
| **2 — Phase 4 run amendment** | A Phase 4 *artifact* (change spec, contract, impact-map row) is untenable in implementation | Step 10 §7.1 package | Yes |
| **3 — Phase 3 run amendment** | A Phase 3 *design specification* is invalidated by implementation evidence | Step 10 §7.2 package | Yes (cascades through Phase 4) |
| **4 — Phase 2 run amendment** | A Phase 2 *commitment* (mechanism, cost envelope) is invalidated | Step 10 §7.3 package | Yes (cascades through Phases 3 and 4) |

The structural defenses: Step 04's scope confirmation surfaces spec gaps
*before* coding; Step 05's deviation register catches gaps surfaced
mid-loop; Steps 06/07/09 findings carry routing; Step 08's effort
deviation analysis distinguishes calibration from amendment. Diagnose the
level before firing: *"the spec needed a clarifying answer"* is Phase 5
local; *"the spec committed something implementation disproves"* is
Channel 2; *"the design itself is disproved"* is Channel 3; *"the
mechanism or the money is disproved"* is Channel 4.

---

## The ID Series — Established, Cited, Verified

### Series Phase 5 Establishes

| ID Series | Meaning | Established By | Cited By |
|-----------|---------|----------------|----------|
| **CS-NN** | Coding standards & conventions (provenance-tagged) | Step 03 | Step 04 PRDs; Step 05 generated code and commits; Steps 06–07 reviews |
| **WP-NN** | Work packages within a module (scoped as M-NN.WP-N) | Step 04 | Step 05 implementation; Step 08 effort actuals |
| **T-NN** | Tasks within a work package (scoped as M-NN.WP-N.T-NN) | Step 04 | Step 05 commits and Implementation Report; traceability chain |

### Upstream IDs Phase 5 Cites

| Upstream ID | Meaning | Source |
|-------------|---------|--------|
| **M-NN, SIC-NN** | Modules + dispositions; strategic interface contracts | Phase 4 Step 08 Impact Map |
| **SP/SEC/TB/DA/DOC/GOV-NN** | Cross-cutting framework elements (provenance-tagged) | Phase 4 Steps 03–07 |
| **Blueprint §-refs** | Sections of the Phase 4 Architecture Blueprint Bundle (§2 impact map + specs, §3 contracts, §5 scorecard refresh, §7.1 handoff) | Phase 4 Step 12 |
| **Change spec §-refs** | Sections of a module's change specification (§2 interfaces, §7 test strategy/regression surface, §9 estimates) | Phase 4 Step 09 |
| **Phase 3 Bundle §-refs** | §2 Coordination Map (cohorts), §3 verification instruments | Phase 3 Step 06 |
| **MC-NN / Brief IDs** | Must-Changes and design briefs | Phase 2 / Phase 3 |
| **HC-NN** | Hard constraints (capacity envelope) | Phase 1 / Phase 2 |

**The traceability chain:** every commit → task (M-NN.WP-N.T-NN) → work
package → implementation PRD → change specification section → Phase 4
blueprint → Phase 3 design → Phase 2 mechanism (MC-NN). A change that
cannot be traced up this chain is an untraceable artifact the
verification framework cannot validate.

---

## Behavioral Rules

These rules apply to every AI session in this phase.

**Generate from the spec; do not re-architect.**
Phase 5 implements the Phase 4 blueprint. When a change specification
proves ambiguous or wrong, surface the gap (Step 04 §1 before coding;
the Step 05 deviation register mid-loop) and route structural gaps to the
Step 10 amendment packages. The specification is updated before
implementation continues — never silently coded around.

**Keep the regression suite green at every increment.**
The existing tests named in each change specification's regression
surface run inside the Step 05 loop, not just at the end. A red
regression test stops the loop: either the change is wrong (fix it) or
the specification authorized this break explicitly (cite it) — there is
no third option. Regression breaks discovered at Step 09 that Step 05
should have caught are loop-discipline failures; name them.

**Do not edit UNTOUCHED modules.**
An UNTOUCHED disposition is a commitment. If implementation appears to
require editing an UNTOUCHED module, stop — that is a Phase 4 impact-map
error (Channel 2 candidate) or a misread of the change. Surface it; do
not just make the edit.

**Specify tasks before generating.**
Step 04 produces specific, verifiable tasks with acceptance criteria
before Step 05 generates any code. Handing AI a change specification and
saying "implement this" turns the loop into a negotiation. Each task is
small enough to generate correctly and specific enough to verify.

**Treat AI output as a first draft.**
The verification stack — in-loop tests and conformance (Step 05), module
correctness verification (Step 06), independent AI-vs-AI review
(Step 07) — exists because AI output requires validation. No merge
without checks; no skipped review because a change "looks simple."

**AI-vs-AI review uses a separate configuration.**
Step 07 must use a different model, prompt configuration, or review
framework from the generating sessions, and must not see the generating
AI's reasoning. Same-configuration review is not an independent audit.
Disagreements are arbitrated by the practitioner and recorded.

**Match the existing idiom; cite CS-NN.**
Generated code reads like the surrounding code — comment density, naming,
error-handling idiom, test style — per the CS-NN standards codified from
the codebase itself. Do not introduce a second style, a new helper
library, or a new pattern without a CS-NN or SP-NN basis.

**Land through the existing discipline.**
Branches, commit conventions, review gates (GOV-NN), CI checks, and
release trains are the existing ones, reconciled at Steps 02–03. Semantic
traceability (task and spec references in every commit) integrates into
the existing commit format. Coordinated-landing cohorts land together per
the Step 02 plan.

**Record effort actuals as you go.**
Every task and work package records actual effort in the three-quantity
model against the Phase 4 §9 estimate — captured in the Step 05
Implementation Report and consolidated in Step 08. Retrospective
guesswork at Step 10 is not measurement.

**Build monitoring alongside features.**
The observability touchpoints mapped to each module (change spec §8) are
implemented and tested inside the same work packages as the features they
observe — not deferred.

**Do not ignore score regressions.**
When a commit drops coverage, spikes complexity, or triggers a new
security finding, the flag is addressed before the next work package
begins. Step 08 catches per-module regressions; Step 10 verifies they
were handled, not accumulated.

**Honor the safety gates when executing.**
Phase 5 runs tools and writes code. Before any risky or hard-to-reverse
action — overwriting files, running migrations, touching shared state —
confirm and, where warranted, back up first. Never print, log, or commit
secrets, credentials, keys, or tokens. Steps needing elevated privileges
or touching sensitive resources are STOP-and-ask steps. Prefer reversible
actions. Destructive git operations (force-push, history rewrite, branch
deletion) are out of scope without explicit practitioner direction.

**Re-verify subject identity and blueprint currency at each step start.**
*Inherited.* Re-verify the subject version, the Blueprint currency (has a
Phase 4 amendment landed?), and apply the concurrent-release /
dependency-shipped-early decision rule from Phase 3 v1.1 — parallel
tracks shipping mid-phase are a recurring condition; decide grounding
note vs amendment, never silent adjustment.

**Handle MCP connector activation gracefully.**
*Inherited.* Attempt once, report specifically, confirm activation, retry
once, then degrade the mode explicitly, amend the Step 00 document, and
continue.

**Structure all outputs for AI consumption.**
Reports, plans, PRDs, and the bundle are consumed by AI in Phases 6 and
7: consistent headers, tables, labeled sections, IDs on all rows,
metadata, explicit cross-references.

**Code to files; reports in markdown.**
Step 05 writes code, tests, and configuration to the repository and
produces a structured Implementation Report as its markdown output. All
other steps produce markdown artifacts. Toolkit prompts never contain
project source code — they instruct its generation.

---

## Phase 5 (Existing Project) Artifacts

Eleven steps produce the phase's artifacts. Before Step 01, the
practitioner runs **Building Block Discovery**
(`step-00-building-block-discovery.prompt.md`) — in Phase 5 this
inventory carries more weight than in any prior phase, because the
implement loop depends on write access, test execution, scanners, and a
separate AI configuration for Step 07.

| Step | Artifact | Type | Repetition |
|------|----------|------|-----------|
| 00 | Toolset Augmentation Document | Action (living document) | Once |
| 01 | Phase 4 Input Validation Report + Validation Gap Register | Interview → Action | Once |
| 02 | Implementation Plan & Landing Sequence | Action (with clarification) | Once |
| 03 | Coding Standards & Conventions (CS-NN) | Action (with clarification) | Once |
| 04 | Module Implementation Plan (scope confirmation + WP-NN breakdown + PRD + task list) | Parameterized Action | Once per NEW/CHANGED module |
| 05 | Implement Loop → code/tests/config in the repo + Implementation Report | Parameterized Action (iterative per task) | Once per module (looping over its tasks; large modules may run per work package) |
| 06 | Module Correctness Verification Report | Evaluation | Once per module |
| 07 | AI-vs-AI Review Report | Evaluation (separate AI configuration) | Once per module |
| 08 | Module Health, Scoring & Effort Actuals | Action + Evaluation | Once per module |
| 09 | Integration & Regression Validation Report | Evaluation | Once (per cohort where cohorts land separately) |
| 10 | Implementation Bundle + scorecard refresh + readiness determination (+ amendment packages when applicable) | Action + Evaluation (synthesis + the gate) | Once |

---

## Dependency Graph and Execution Pattern

```
Phase 4 Architecture Blueprint Bundle (change specs, contracts,
frameworks, scorecard refresh, §7.1 handoff)
+ Phase 3 Bundle (§2 cohorts, §3 instruments) + Phase 2 Plan + Phase 1 baselines
   │
   ▼
═══ STAGE 1: PRE-IMPLEMENTATION SETUP (project-level, once) ═══
   │
   ▼
Step 00: Building Block Discovery          ┐
   ▼                                        │ strictly
Step 01: Phase 4 Input Validation           │ sequential
   ▼                                        │
Step 02: Implementation Plan &              │
         Landing Sequence                   │
   ▼                                        │
Step 03: Coding Standards & Conventions ────┘
         (CS-NN)
   │
   ▼
═══ STAGE 2: PER-MODULE CHANGE IMPLEMENTATION ═══
   │   for each NEW/CHANGED module, in the Step 02 order;
   │   independent modules in parallel sessions
   ▼
Step 04: Module Implementation Plan ── spec gap? ──► Step 10 (Channel 2)
   ▼
Step 05: Implement Loop (generate → test + REGRESSION SUITE →
   │      score → conformance → refine; semantic commits;
   │      effort actuals)                 ── iterates per task
   ▼
Step 06: Module Correctness Verification  ── per module
   ▼
Step 07: AI-vs-AI Review (separate config) ── per module
   ▼
Step 08: Module Health, Scoring & Effort Actuals ── per module
   │
   ▼ (all modules complete — or a cohort completes)
═══ STAGE 3: INTEGRATION & HANDOFF (project-level) ═══
   │
   ▼
Step 09: Integration & Regression Validation
   ▼
Step 10: Implementation Synthesis & Readiness Review (the gate)
   │
   ┌──────────┬──────────┬───────────┬───────────┬───────────┐
   ▼          ▼          ▼           ▼           ▼           ▼
Phase 6    Phase 5    Phase 4     Phase 3     Phase 2    CONDITIONALLY
Authorized Internal   Amendment   Amendment   Amendment   READY
(READY)    Remediation Cycle      Cycle       Cycle       (partial
           (NOT READY  (Channel 2) (Channel 3) (Channel 4)  Phase 6 start)
            Phase 5 gaps)
```

### Parallelism Opportunities

- **Modules run in parallel** where the Impact Map §6 sequencing permits;
  a module that depends on another mocks or stubs it per the Step 02
  decisions until it is available.
- **Within a module, execution is serial**: plan → implement → verify →
  review → score. Steps 06 and 07 for the same module may run in
  parallel sessions (they are independent lenses on the same output).
- **Steps 00–03 are strictly sequential** and precede all module work.
  **Steps 09–10** run after the module pipelines (Step 09 may run per
  coordinated-landing cohort when cohorts land separately; Step 10 runs
  once, after everything).

### The Minimum Viable Path

All eleven steps are mandatory. What scales is repetition and depth, not
the set of activities:

| Step | Repetition |
|------|-----------|
| 00–03 | Once (project-level) |
| 04–08 | Once per NEW/CHANGED module (N from the Impact Map) |
| 09 | Once (or per landing cohort) |
| 10 | Once |

The one conditional element, inherited from the greenfield variant: the
**formal-verification section of Step 06** runs only for components
Phase 4 designated for formal verification. A single-module change
surface runs Steps 00–03 once, Steps 04–08 once, and Steps 09–10 once —
eleven executions. Skipping verification or scoring for a "simple"
module produces exactly the regression and traceability gaps the common
pitfalls warn against.

---

## Phase Gate: The Readiness Review (Step 10)

Step 10 combines the track's synthesis discipline with the greenfield
Phase 5 gate's six-outcome determination.

### Per-Principle Gates

The scorecard refresh produces per-principle PASS/CONDITIONAL/FAIL under
the inherited weights, against the Phase 4 refresh as baseline, with the
target distribution check.

### The Six Determination Outcomes

| Status | Meaning | Action |
|--------|---------|--------|
| **READY** | All gates pass; every NEW/CHANGED module implemented, verified, reviewed, scored; regression suite green; actuals within envelope | Phase 6 may begin upon practitioner authorization |
| **CONDITIONALLY READY** | ≤2 conditional gates with named remediation, owner, and target | Phase 6 may begin work not blocked by the conditionals |
| **NOT READY (Phase 5 gaps)** | Blocking gaps in Phase 5's own work | Remediate in the responsible step; re-run Step 10 |
| **NOT READY (Phase 4 amendment required)** | A Phase 4 artifact is invalidated (Channel 2) | Deliver the §7.1 package; Phase 4 amends; re-enter Phase 5 at the affected modules |
| **NOT READY (Phase 3 amendment required)** | A Phase 3 design specification is invalidated (Channel 3) | Deliver the §7.2 package; cascades through Phase 4 re-entry |
| **NOT READY (Phase 2 amendment required)** | A Phase 2 commitment is invalidated (Channel 4) | Deliver the §7.3 package; cascades through Phases 3 and 4 re-entry |

**A NOT READY determination is the process working.** A specification gap
caught at the gate costs an amendment cycle; the same gap shipped to
Phase 6 — or production — costs far more.

Do not skip the gate. Do not treat a CONDITIONAL as a PASS.

---

## Output Standards

All Phase 5 (existing-project) outputs must meet the following before
being considered complete:

- [ ] Every NEW/CHANGED module from the Impact Map has a Step 04 plan, a
      Step 05 Implementation Report, a Step 06 verification, a Step 07
      independent review, and a Step 08 health/scoring/actuals record
- [ ] No UNTOUCHED module was edited; RETIRED modules were removed per
      their impact-map notes with their consumers' changes verified
- [ ] Every change conforms to its formal contract and its change
      specification; conformance checks are automated where the tooling
      permits, and green
- [ ] The full regression suite is green; every regression-surface test
      from every change specification §7 passes; any authorized breaks
      cite their specification basis
- [ ] Coverage targets from each change specification are met; new tests
      (unit, integration, property-based, contract) are in place and
      derived from the specifications
- [ ] All security scans pass or carry documented accepted-risk entries;
      SEC-NN controls are implemented at their TB-NN boundaries
- [ ] Observability touchpoints are implemented and tested per each
      module's §8 mapping
- [ ] The Phase 3 Bundle §3 verification instruments are implemented or
      executable — Phase 6 can run them
- [ ] For components Phase 4 designated, formal verification models are
      complete, checked, and practitioner-reviewed
- [ ] AI-vs-AI review ran per module with a separate configuration;
      disagreements are arbitrated and recorded
- [ ] Every commit carries semantic traceability (task + spec reference)
      within the project's existing commit conventions
- [ ] Effort actuals are recorded per task/work package in the
      three-quantity model; Step 10 §5 produces the multiplier
      calibration table and checks the aggregate against the HC-NN
      envelope
- [ ] The scorecard refresh compares against the Phase 4 baseline with
      the target distribution check applied
- [ ] No specification was silently re-architected; spec problems were
      routed through the amendment channels
- [ ] All artifacts are version-stamped with a Version History table; the
      toolset version is visible at the top of each file

---

## Common Pitfalls

**Generating without specifying tasks.**
Handing AI a change specification and saying "implement this" produces
poor results and an undisciplined loop. The structural defense is Step
04's scope-confirmation → work-package → PRD → task pipeline preceding
any generation.

**Breaking the regression surface and noticing late.**
Running only the new tests during the loop and the full suite at the end
discovers breaks when they are expensive. The structural defense is the
regression suite inside the Step 05 loop and the regression-surface
confirmation at Step 06 §3.

**Editing UNTOUCHED modules "just a little."**
A small edit to an UNTOUCHED module is an unspecified change with no
regression surface, no review gate, and no traceability. The structural
defense is the behavioral rule + Step 09's integration check that diffs
landed changes against the Impact Map dispositions.

**Introducing a second style.**
AI-generated code that ignores the existing idiom fragments the codebase.
The structural defense is Step 03's CS-NN codification of the existing
conventions and Steps 06–07 checking generated code against them.

**Treating AI output as final.**
Generated code is a first draft. The structural defense is the
verification stack (Steps 05-in-loop, 06, 07) — none skippable without
failing the Step 10 gate.

**Same-configuration "independent" review.**
Step 07 run with the generating configuration is not an audit. The
structural defense is the mandatory separate-configuration attestation in
Step 07 §1.

**Deferring monitoring implementation.**
Touchpoints bolted on before deployment produce incomplete observability.
The structural defense is touchpoint implementation inside the Step 05
work packages and verification at Step 06.

**Retrospective effort guessing.**
Actuals reconstructed at the gate are not measurements and cannot
calibrate the multipliers. The structural defense is per-task actuals in
the Step 05 report and per-module consolidation at Step 08.

**Ignoring score regressions.**
Regressions compound across modules. The structural defense is Step 08
flagging per module and Step 10 verifying handling.

**Losing traceability.**
Unstructured commits break the chain from code to spec. The structural
defense is the semantic-commit rule integrated into the existing commit
conventions at Step 03 and verified at Steps 08–10.

**Re-architecting instead of amending.**
Coding around a spec gap diverges implementation from blueprint. The
structural defense is Step 04 §1 gap surfacing, the Step 05 deviation
register, and the Step 10 amendment packages (Channels 2–4).

**Treating a feedback-channel firing as failure.**
When a channel fires, the framework is working — the gap was caught
before Phase 6 or production paid for it.

---

## Connecting to Phase 6

Phase 5 hands off working, tested, scored, and verified changes to Phase
6 (Testing & Audit), which applies an independent lens and turns the
principles into pass/fail gates.

| Phase 6 Concern | Phase 5 Inputs Consumed |
|-----------------|------------------------|
| Independent test execution & audit | The test suites (new + regression), the changed codebase |
| Verification instrument execution | The Phase 3 Bundle §3 instruments, implemented/executable per Step 06 §5 |
| Security audit | Scan results, SEC-NN-conformant changes, dependency audit |
| Performance validation | Benchmark results vs Phase 1 measured baselines |
| Specification conformance audit | Conformance results vs the Phase 4 formal contracts |
| Formal verification review | The models and checked properties (practitioner review continues) |
| Documentation review | The DOC-NN artifacts produced with the changes |
| Phase 6 scorecard update | The Step 10 scorecard refresh + inherited weights |

The Step 10 readiness review verifies each Phase 6 concern has its
required inputs before authorizing Phase 6. Phase 6 is not a net for
incomplete implementation — implementation must be solid before audit
begins.

The Phase 6 toolkit's Step 01 (Phase 5 Input Validation) will follow the
same two-scope split pattern this toolkit's Step 01 follows. The
inter-phase feedback loop continues.

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Phase 5 existing-projects instructions file. Three shifts from the greenfield Phase 5 variant (change integration in a living codebase with the regression surface as an in-loop gate, vs module construction; conventions and pipelines reconciled with provenance-tagged CS-NN and semantic commits integrated into existing commit discipline, vs invented; measured effort calibration graduating the track's BELIEVED multipliers to ESTIMATED, vs estimates only). Eleven-step structure in three stages (setup 00–03; per-module pipeline 04–08 with Module → Work Package → Task hierarchy replacing the greenfield module/milestone/epic breakout; integration & gate 09–10). Four feedback channels (upstream toolkit gaps; Phase 4 / Phase 3 / Phase 2 run amendments) and the six-outcome readiness determination. Hard code-access sharpening: Interview-only cannot run Step 05 — direct write access or patch-mediated mode required. New ID series CS-NN, WP-NN, T-NN with the commit→task→PRD→spec→blueprint→design→mechanism traceability chain. Scorecard inheritance continued (Phase 2 weights; Phase 4 refresh as baseline; target distribution check). Safety-gate execution rules inherited from the greenfield variant with brownfield sharpenings (UNTOUCHED modules not edited; regression suite green at every increment; no destructive git operations without direction). |

---

*Part of the Phase 5 (Existing Projects) Implementation Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion files: step-00 through step-10 prompts in this directory*
