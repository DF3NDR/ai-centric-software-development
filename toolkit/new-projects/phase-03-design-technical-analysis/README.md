# Phase 3: Design & Technical Analysis — Tool Set
## AI-Centric Software Development Playbook

---

## Overview

This directory contains the complete tool set for **Phase 3: Design &
Technical Analysis** of the AI-Centric Software Development Playbook.
Phase 3 takes the committed Phase 2 analytical foundation — the stack
decision, cost model, threat model, business case, and benchmark
framework — and stress-tests it through structured design exploration,
scoring, and simulation. The phase produces a locked technical
direction that Phase 4 architecture will build on.

This is the phase where design problems are cheapest to find. A design
flaw discovered here costs a conversation with AI. The same flaw
discovered during implementation costs days of rework. Discovered in
production, it costs an incident. Phase 3 exists to front-load that
discovery through deliberate, principle-scored exploration of the
design space.

The primary outputs of this phase are the **Design Direction Document
with six embedded ADRs** (the locked direction), the **Principle
Scorecard baseline** (the cross-phase living document Phases 4–7
will update), the **Technical Feasibility Assessment** (simulation
results across five scenario categories), and the **Phase 4 handoff
package** (observability hooks plus compliance design constraints).

---

## Framework Context

This tool set is part of the [AI-Centric Software Development
Playbook](../../../README.md), a practitioner's framework for small teams
(1–5 people) that use AI tools to deliver what large organizations
once required.

Four framework concepts are essential to understanding how Phase 3
operates:

### Phase 3 Differs From Phases 1 and 2 in Character

| Dimension | Phase 1 | Phase 2 | Phase 3 |
|-----------|---------|---------|---------|
| Primary work | Gathering evidence | Making commitments on stack | Stress-testing commitments and locking technical direction |
| AI role | Research strategist | Analytical partner for commitments | Design analyst and simulation runner |
| Distinctive activity | Structured interviews | Weighted scoring | Simulation under stress |
| Number of artifacts | 1 Information Report | 7 (analytical + governance) | 9 (analytical + scorecard + governance + handoff) |
| Execution pattern | Order-flexible | Strictly sequential | **Dependency-driven** |
| Cross-phase living artifacts | None | Stack ADR (referenced) | **Principle Scorecard (actively updated)** |
| Gate mechanism | Self-evaluation in synthesis | Dedicated Readiness Review | **Readiness Review with Phase 2 amendment path** |

Phase 3 introduces three things Phases 1 and 2 did not have:

**Simulation as a first-class activity.** AI-driven "what if"
analysis tests whether the design direction holds under stress.
Performance under load. Security model survival against the threat
model. Cost holding when design choices factor in. Failure modes.
Scaling behavior. These analyses are not empirical tests (those come
in Phases 5 and 6) — they are structured analytical models that
eliminate clearly unworkable options before architecture investment.

**The Principle Scorecard as a living cross-phase artifact.** Phase 3
establishes the scorecard baseline. Phase 4 updates it based on
architectural decisions. Phase 5 updates it based on actual code
quality. Phase 6 updates it based on audit findings. Phase 7 updates
it based on operational reality. The scorecard travels with the
project from Phase 3 through Phase 7. Regression detection across
phases is the point.

**The Phase 2 amendment cycle.** Phase 3 design work can invalidate
Phase 2 assumptions in ways Phase 2 could not foresee. A simulation
may reveal the committed stack cannot meet a benchmark at scale. A
compliance constraint may conflict with the deployment model. When
this happens, the response is not to ignore Phase 2 or work around
it — the response is to amend Phase 2 with a structured remediation
package, then re-run the affected Phase 3 steps.

### The Six Core Principles — Now as Living Scorecard

In Phase 1, the principles were a research lens. In Phase 2, they
became a decision framework. In Phase 3, they become a **living
scorecard** — the measuring sticks that travel with the project from
design through production.

| Principle | Phase 3 Application |
|-----------|---------------------|
| **Security** | Threat model maps onto design options. Security model committed at strategic level. Compliance constraints translate to design constraints. |
| **Maintainability** | Design direction evaluated for testability, documentation support, independent component evolution. Scorecard tracks long-term viability. |
| **Economics** | Simulation validates that design choices stay within cost envelope. Scorecard tracks cost projection accuracy. |
| **Operations** | Deployment, scaling, failure modes evaluated. Observability strategy committed. Scorecard tracks operational health. |
| **Scoring & Metrics** | **This is the phase where the scorecard is established.** Every principle gets current and target scores. Step 06 protocol governs cross-phase updates. |
| **Correctness Verification** | Design evaluated for verifiability. Scorecard tracks specification conformance support. |

### Specification Driven Development (SDD)

Phase 3 runs the SDD cycle with the Phase 2 package as its primary
input. The practitioner is not gathering, not committing analytical
decisions — they are taking the committed analytical foundation and
validating that it holds under design exploration.

```
Specify → Plan → Detail → Task → Implement
```

| SDD Step | What Happens in Phase 3 | Output |
|----------|-------------------------|--------|
| **Specify** | Define design questions and required simulations | Design Exploration Specification |
| **Plan** | Organize by six locked dimensions plus forward-looking concerns | Implicit in the specification |
| **Detail** | Generate evaluation criteria mapped to Core Principles | Design Option Scoring criteria |
| **Task** | Identify specific design analyses and simulations | Distributed across prompts |
| **Implement** | Execute analyses and simulations; commit direction; establish scorecard; produce handoffs; run readiness review | Nine Phase 3 artifacts |

The cycle is iterative within Phase 3. When simulation reveals a
design option cannot meet a benchmark, design exploration returns to
generate alternatives. When the Readiness Review surfaces
inconsistency, the responsible prior step is re-run. The cycle also
reaches backward into Phase 2 when necessary — through the structured
amendment cycle.

### Dependency-Driven Execution

Phase 3 is the first phase where prompts can be run in parallel where
their dependencies permit. Phase 1's prompts were order-flexible
across the board. Phase 2's prompts were strictly sequential. Phase
3's prompts have a dependency graph that permits some parallelism
and prohibits others.

The dependency graph is documented in the instructions file and
reproduced below. The practitioner runs prompts in any order
consistent with the graph. A prompt may begin as soon as all its
required inputs are available.

---

## Directory Contents

```
phase-3-design-technical-analysis/
├── README.md                                              ← You are here
├── design-technical-analysis.instructions.md             ← Load as project context
├── step-01-design-exploration-specification.prompt.md    ← Scoping work
├── step-02-design-option-scoring.prompt.md               ← Weighted scoring across dimensions
├── step-03-simulation-feasibility.prompt.md              ← Technical Feasibility Assessment
├── step-04-design-direction-and-adrs.prompt.md           ← Locked direction + six ADRs
├── step-05-principle-scorecard-baseline.prompt.md        ← Cross-phase living scorecard
├── step-06-scorecard-update-protocol.prompt.md           ← Cross-phase governance
├── step-07-observability-hooks-handoff.prompt.md         ← Phase 4 forward-looking
├── step-08-compliance-design-constraints.prompt.md       ← Phase 4 forward-looking
└── step-09-phase-3-readiness-review.prompt.md            ← The gate
```

---

## File Descriptions

### `design-technical-analysis.instructions.md`
**Type:** Instructions file (load once as persistent project context)

The overarching context for any AI assistant operating in Phase 3.
Loaded once and remains active across all nine prompt sessions.
Contains the framework orientation, the SDD cycle for this phase,
all six Core Principles applied as the living scorecard, the
dependency graph, behavioral guidelines, output standards, and the
Phase 4 handoff connection.

The instructions file plays a heavier coordinating role in Phase 3
than in Phase 2 because dependency-driven execution requires the
dependency graph to be authoritative. Without the documented graph,
practitioners would have to derive ordering from prompt metadata
tables, which produces inconsistent execution patterns.

---

### `step-01-design-exploration-specification.prompt.md`
**Type:** Action Prompt with Clarification Step

Produces the scoping document that drives every subsequent Phase 3
prompt. Identifies which design questions must be answered, which
carry the most risk, which scenarios must be simulated, and what is
explicitly out of scope.

**Key design decision:** The scoping work is structurally separated
from the scoring work that follows in Step 02. This separation is
the framework's defense against the rationalization failure mode
the article warns about — if criteria are defined and options are
named before any scoring occurs, the subsequent scoring cannot
shape itself to predetermined outcomes.

**Key structural feature:** All six locked dimensions are scoped
even when one has obvious answers. A dimension with one viable
option is a documented scope boundary, not a skipped section. The
evaluation checklist enforces this — without it, AI tends to skip
dimensions where Phase 2 has already narrowed the field.

---

### `step-02-design-option-scoring.prompt.md`
**Type:** Action Prompt with Clarification Step

Produces the structured scoring of every viable design option
across all six locked dimensions, using the evaluation criteria
framework from Step 01 and the principle weighting from Phase 2
Step 01. Output ranks options per dimension by weighted total —
but does not commit any choice.

**Key design decisions:**

- **Same evidence-and-citation discipline as Phase 2 Step 04,
  applied per dimension.** Sub-criteria with explicit definitions
  (from Step 01), the 1–5 scale with documented meaning, evidence
  citation requirements, prohibition on adjusting weights or
  criteria during scoring.

- **The Cross-Dimension Tension Register is the most consequential
  new content beyond per-dimension scoring.** Phase 2 Step 04
  surfaced tensions within a single scoring exercise. Step 02
  produces six rankings and surfaces conflicts between top-ranked
  options across dimensions — exactly the inputs Step 04 must
  reconcile when committing direction.

- **No declared winner.** The artifact ranks; Step 04 commits.

---

### `step-03-simulation-feasibility.prompt.md`
**Type:** Action Prompt with Clarification Step

Phase 3's most distinctively new prompt. Executes AI-driven
simulations across five scenario categories — performance, security,
cost, failure modes, scaling — and produces the Technical
Feasibility Assessment. Eliminates design options that structurally
cannot meet critical benchmarks or survive critical threats.

**Key design decisions:**

- **Five named scenario categories as the artifact's spine.** The
  output template has sections only for performance, security,
  cost, failure modes, and scaling. If a needed simulation does
  not fit one of these categories, the response is to amend Step
  01 — not to add a "miscellaneous" section.

- **Every simulation anchors to a Phase 2 benchmark or threat.**
  The structural defense against simulation drift. Without
  anchoring, simulations produce output but no signal. With
  anchoring, every simulation has a concrete pass/fail question.

- **Options Eliminated by Simulation is structurally consequential.**
  The framework's central claim is that Phase 3 catches problems
  before architecture investment. The §10 elimination section and
  the post-elimination ranking updates enforce this — Step 04
  cannot commit an eliminated option.

- **Simulate, do not benchmark.** AI simulations are analytical
  projections based on documented assumptions, not empirical
  measurements. The Phase 4 / 5 / 6 Empirical Validation Handoff
  makes the analytical limits of Phase 3 explicit.

---

### `step-04-design-direction-and-adrs.prompt.md`
**Type:** Action Prompt with Clarification Step (governance-focused)

The most consequential Phase 3 prompt. Produces the Design Direction
Document with six embedded ADRs (one per locked dimension) as a
paired artifact in a single execution. The document and the ADRs
are versioned together and cannot drift apart structurally.

**Key design decisions:**

- **The paired artifact structure is the drift-prevention answer.**
  Part A's dimension sections reference Part B's ADRs by number.
  Part B's ADRs document the same commitments Part A presents. The
  cross-artifact consistency check explicitly verifies that each
  Part A commitment matches the corresponding Part B ADR.

- **The Commitment Type field is the structural defense against
  silent divergence.** Three named types: top-ranked, divergence,
  marginal acceptance. The ADR must declare which type applies.
  Divergences trigger the divergence rationale subsection. Marginal
  acceptances trigger the risk acceptance subsection.

- **Step 04 cannot commit Step 03 eliminated options.** The
  clarification step's conflict check is structurally first when
  needed. If the practitioner's commitment statement names an
  eliminated option, the clarification raises the conflict before
  any ADRs are produced.

- **Each ADR cites Phase 2 inputs, Step 02 scoring evidence, and
  Step 03 simulation results.** Structured citation tables in
  every ADR's Context section force the rationale chain to be
  complete and verifiable.

---

### `step-05-principle-scorecard-baseline.prompt.md`
**Type:** Action Prompt with Clarification Step

Produces the Principle Scorecard baseline — the cross-phase living
document that all subsequent phases will update. The baseline is
established once, here, and governed thereafter by the Step 06
update protocol.

**Key design decisions:**

- **The five-element-per-principle structure from the article is
  load-bearing.** Current score, target score, gap analysis, risk
  items, monitoring indicators per principle. All five are
  required. The structural enforcement is in the output template
  and the evaluation checklist.

- **The cross-phase living document notice is the most consequential
  structural element.** At the top of the artifact, in a callout
  block, telling every future reader that this is not a Phase 3
  deliverable to be archived but the document Phases 4–7 will
  actively update.

- **AI proposes, practitioner calibrates.** The same pattern Phase
  2 Step 06 benchmarks used. AI tends to be either too optimistic
  (scoring intentions) or too conservative (flagging theoretical
  risks). The AI-Proposed / Practitioner-Calibrated split makes
  the calibration step visible.

- **The scorecard does not establish its own update protocol.**
  That is Step 06's job. Step 05 produces the baseline; Step 06
  governs how it changes. The §7.3 subsection references Step 06
  rather than defining the protocol inline.

---

### `step-06-scorecard-update-protocol.prompt.md`
**Type:** Action Prompt with Lightweight Clarification Step (governance-focused)

The most architecturally unusual prompt in the toolkit. Produces a
governance document that governs an artifact in another step (Step
05's baseline). Has no Phase 3 content dependencies — its inputs
are Phase 2 conventions and framework principles, not Phase 3 work
products. Defines behavior for phases that have not yet begun.

**Key design decisions:**

- **Can run any time during Phase 3.** Per the dependency graph,
  this prompt has no Phase 3 content dependencies. Some
  practitioners run it early to establish governance before
  analytical work begins.

- **Regression detection thresholds are tiered by principle weight.**
  Principles weighted 20+ trigger regression at a 0.5-point drop;
  lower-weighted principles trigger at 1.0-point. Without
  weight-based thresholds, the protocol would treat all principles
  equivalently, contradicting the framework's principle weighting
  commitment.

- **Three regression categories with distinct escalation paths.**
  Critical, Material, Minor regressions have different escalation
  requirements. Without categorization, every regression would
  trigger the same escalation, which is operationally unworkable.

- **The override mechanism is tiered by regression category.**
  Critical regression overrides require the strictest authority
  (phase authority + practitioner + named stakeholder); Minor
  overrides require only the phase's authorization authority.

- **Audit trail is preserved within the artifact, not externally.**
  The version log lives in the scorecard itself, ensuring history
  travels with the document and cannot be silently lost.

---

### `step-07-observability-hooks-handoff.prompt.md`
**Type:** Action Prompt with Clarification Step (forward-looking handoff)

The first of two forward-looking handoff prompts. Produces the
structured observability hooks package for Phase 4 architecture.
Identifies specific insertion points, capture specifications,
tracing requirements, alerting threshold guidance, and audit
logging hooks — all anchored to Phase 2 operations benchmarks and
Step 03 failure mode simulations.

**Key design decisions:**

- **Every hook anchors to a Phase 2 benchmark, Step 03 failure
  mode, or compliance/threat requirement.** The structural defense
  against hook proliferation. The §8 coverage matrices verify the
  reverse: every benchmark and every critical failure mode has at
  least one supporting hook.

- **Insertion points are at conceptual component level, not module
  level.** Phase 3 / Phase 4 boundary enforcement. Phase 3 does
  not lock module boundaries, so hooks identified at module level
  would over-commit to architectural decisions.

- **Cardinality considerations on metrics are surfaced explicitly.**
  AI's primary failure mode in observability work — specifying
  metrics with high-cardinality labels that produce production
  explosions. The metric tables require cardinality considerations
  per metric.

- **Audit retention is at strategic direction level, not policy
  specifics.** Phase 4 sets the policy; Step 07 surfaces the
  strategic direction (e.g., "minimum 1 year") with traceability
  to compliance drivers.

---

### `step-08-compliance-design-constraints.prompt.md`
**Type:** Action Prompt with Clarification Step (forward-looking handoff)

The second forward-looking handoff prompt. Produces structured
compliance design constraints for Phase 4 security architecture,
data architecture, and audit logging architecture work. Each
constraint cites its regulatory basis, is classified as Hard
requirement or Interpretive, has stack/design compatibility
analysis, and ties to the Information Report compliance map.

**Key design decisions:**

- **AI-produced compliance analysis notice is structural humility,
  not boilerplate.** AI is not a compliance lawyer. The §12
  Compliance Validation Recommendations name where qualified
  professional review is warranted before Phase 4 builds on
  these constraints.

- **Constraints organized per-regime first, then by design
  dimension.** Two different Phase 4 audiences: a compliance-
  focused architect needs all HIPAA constraints in one place; a
  data architect needs all encryption constraints across regimes
  in one place. The §3 per-regime sections and §4 cross-regime
  summary serve both.

- **Hard requirement vs. Interpretive classification.** Some
  regulatory text is unambiguous; other text requires judgment.
  The classification distinguishes the two, and Interpretive
  constraints get flagged for professional review.

- **The §6 Conflicts section escalates to Step 09.** When a
  compliance constraint conflicts with the Step 04 committed
  direction, the conflict cannot be resolved here. It is
  escalated for Step 09 to produce a Phase 2 amendment package.

---

### `step-09-phase-3-readiness-review.prompt.md`
**Type:** Evaluation Prompt (Gate)

The Phase 3 gate. Evaluates all eight prior Phase 3 artifacts plus
the Phase 2 package plus the Phase 1 Information Report. Produces
per-principle gates, per-artifact completeness checks, cross-
artifact consistency checks within Phase 3, Phase 2 alignment
checks, Phase 4 input completeness checks, and the overall Phase
4 readiness determination.

**Key design decisions:**

- **Four-determination outcome instead of three.** READY,
  CONDITIONALLY READY, NOT READY (Phase 4 gaps), NOT READY (Phase
  2 amendment required). The split between the two NOT READY
  outcomes is the structural innovation — Phase 4 gaps return to
  a Phase 3 step; Phase 2 amendment returns to a Phase 2 step.
  Conflating them would leave the practitioner uncertain about
  where to invest remediation effort.

- **The §5.2 Phase 2 Amendment Package is the gate's most
  consequential novel content.** When Phase 2 alignment fails,
  the gate does not produce a vague "Phase 2 needs work" finding
  — it produces five specific subsections naming exactly what
  must be amended (which ADRs, which cost model figures, which
  benchmarks, which threat model entries, which business case
  elements), each with the driving Phase 3 finding that
  necessitates the amendment.

- **Tiered override authority.** Per-principle gate overrides
  require practitioner authority. Phase 2 alignment overrides
  require practitioner + Phase 2 authorization authority. The
  tiering matches the consequence of each override type.

- **The §9 Phase 4 Handoff Summary is structured for Phase 4
  consumption.** Phase 4 tool sets can paste this section as
  immediate context without re-reading all eight Phase 3
  artifacts.

---

## How to Use This Tool Set

### Prerequisites

Before opening any prompt file:

1. Confirm the [Phase 2 toolkit](../phase-2-analysis-stack-selection/README.md)
   is complete with a passing Step 07 Readiness Review. Phase 3
   cannot responsibly begin on a failed or conditional Phase 2 gate
   that has not been resolved.
2. Load `design-technical-analysis.instructions.md` as project-level
   instructions in your AI environment. This gives every Phase 3
   session the framework context, behavioral guidelines, output
   standards, and the dependency graph without re-establishing them
   per session.

### Execution Order — Dependency-Driven

Phase 3 is **not strictly sequential**. Some prompts have hard
dependencies on earlier prompts. Others can run in parallel or in
any order. The dependency graph below makes the required ordering
explicit.

```
Phase 2 Package (all 6 artifacts + Stack ADR)
   │
   ├──────────────────────────────────────────────────────────┐
   │                                                          │
   ▼                                                          ▼
Step 01: Design Exploration Specification    Step 06: Scorecard Update Protocol
   │                                            (no Phase 3 content dependencies —
   │                                             can run anytime in Phase 3)
   ▼
Step 02: Design Option Scoring
   │
   ▼
Step 03: Simulation & Feasibility Assessment
   │
   ▼
Step 04: Design Direction Document + 6 ADRs
   │
   ├──────────────────────────────────────────────────┐
   │                                                  │
   ▼                                                  ▼
Step 05: Principle Scorecard Baseline      Step 07: Observability Hooks Handoff
                                            Step 08: Compliance Design Constraints
                                            (can run in parallel with Step 05
                                             and with each other)
   │                                                  │
   └──────────────────────┬───────────────────────────┘
                          │
                          ▼
                  Step 09: Phase 3 Readiness Review
                  (requires all eight prior artifacts)
                          │
                          ▼
                  Phase 4: Architecture & Modular Design
                  (or Phase 2 amendment cycle if Step 09 surfaces alignment failures)
```

### Parallelism Opportunities

The dependency graph permits the following parallel execution:

- **Step 06 (Scorecard Update Protocol)** can run any time during
  Phase 3. Its only inputs are the Phase 2 weighting and framework
  conventions, so it has no Phase 3 content dependencies. A
  practitioner who wants to establish cross-phase governance early
  can run this prompt first.
- **Steps 05, 07, and 08** can run in parallel once Step 04
  completes. They have no dependencies on each other, only on
  Step 04.
- **Steps 01 through 04** must run in strict sequence — each
  consumes the previous one's output as analytical context.

Running prompts in parallel requires separate AI sessions. The
artifacts produced by parallel prompts are consumed together by
Step 09.

### Running Each Prompt

For each step:

1. Open a new AI session with a large context window
2. Confirm `design-technical-analysis.instructions.md` is loaded
   as project context
3. Paste **all required inputs** above the kickoff line — see the
   prompt's metadata table for the exact list
4. Paste any prompt-specific data (e.g., commitment statement for
   Step 04)
5. Paste the **System Instructions** section from the prompt file
   if not already loaded via the instructions file
6. Paste the **Kickoff** line to begin
7. Answer the AI's clarifying questions (single-digit count, never
   more) one at a time
8. The AI produces the artifact in a single response
9. Review the output against the prompt's evaluation checklist
   before accepting it as complete
10. Save the artifact for use as input to subsequent steps

### Iterating

The SDD cycle is iterative. Common iteration triggers:

- **Step 03 simulation reveals an option Step 02 ranked highly is
  unworkable** → eliminated option flows through to Step 04
  rankings; no Step 02 re-run required unless multiple options
  fail
- **Step 04 reveals cross-dimension tensions Step 02 did not
  surface** → return to Step 02 to surface them, then continue to
  Step 04
- **Step 05 reveals scoring reflects design intentions rather than
  realities** → practitioner calibration adjusts the AI proposal;
  no Step 04 re-run unless calibration reveals Step 04 commitments
  were wrong
- **Step 07 or Step 08 surfaces gaps in Step 04 ADRs** → amend
  Step 04 with the gap remediated, then re-run Step 07 or Step 08
- **Step 09 returns CONDITIONAL or NOT READY (Phase 4 gaps)** →
  execute named required actions in responsible prior steps, then
  re-run Step 09
- **Step 09 returns NOT READY (Phase 2 amendment required)** →
  execute the Phase 2 amendment cycle per §5.2; details in the
  next section

---

## The Phase 2 Amendment Cycle

Phase 3 introduces a governance pattern that does not exist in
Phases 1 or 2: the structured amendment cycle that returns work to
the prior phase.

### When the Amendment Cycle Triggers

Step 09's Readiness Review checks Phase 2 alignment as a dedicated
dimension. Alignment can fail in any of several ways:

- Step 03 cost simulation reveals Step 04 commitments exceed the
  Phase 2 Step 02 cost envelope
- Step 03 performance simulation reveals the Phase 2 committed
  stack cannot meet a Phase 2 Step 06 benchmark at scale
- Step 03 security simulation reveals critical threats from Phase
  2 Step 03 are not addressable by the Step 04 security model
- Step 08 compliance constraints conflict with Phase 2 commitments
  (typically the deployment model or data architecture)
- Step 04 commitments violate Phase 2 Stack ADR acceptance
  conditions or revision triggers

When any of these occurs, Step 09's determination is **NOT READY
(Phase 2 amendment required)**. The gate does not block Phase 4
indefinitely — it directs the practitioner back to Phase 2 with a
structured amendment package.

### The Amendment Package Structure

Step 09's §5.2 produces five subsections naming exactly what must
be amended:

| Subsection | Content |
|------------|---------|
| §5.2.1 Phase 2 ADR Amendments Required | Which Phase 2 ADRs need amendment, what specific amendment, driving Phase 3 finding |
| §5.2.2 Phase 2 Cost Model Revisions Required | Which Phase 2 Step 02 sections need revision, what specific revision, driving Phase 3 finding |
| §5.2.3 Phase 2 Benchmark Adjustments Required | Which Phase 2 Step 06 benchmarks need adjustment, what specific adjustment, driving Phase 3 finding |
| §5.2.4 Phase 2 Threat Model Refinements Required | Which Phase 2 Step 03 threats need refinement, what specific refinement, driving Phase 3 finding |
| §5.2.5 Phase 2 Business Case / Principle Weighting Revisions Required | Which Phase 2 Step 01 elements need revision, what specific revision, driving Phase 3 finding |

Each amendment item is concrete. Not "Phase 2 needs work" but
"Phase 2 Step 06 BM-12 latency target must be relaxed from 50ms to
75ms at full scale based on Step 03 §4.1 simulation finding that
the committed Rust + Axum stack cannot achieve 50ms p99 at the
projected full-scale workload."

### The Amendment Cycle Process

1. **Practitioner returns to Phase 2** with the amendment package
   from Step 09 §5.2
2. **Re-runs the relevant Phase 2 prompts** to produce amended
   artifacts — new versions of the affected ADRs, cost model,
   benchmarks, threat model, business case
3. **Re-runs Phase 2 Step 07 (Readiness Review)** to verify Phase
   2 internal consistency is restored
4. **Returns to Phase 3** and re-runs the affected Phase 3 steps —
   typically Step 03 (simulation against amended benchmarks) and
   Step 04 (commitment with amended constraints) at minimum
5. **Re-runs Step 09** to verify alignment is restored

### Why the Amendment Cycle Matters

The amendment cycle is the framework's structural defense against
building Phase 4 architecture on Phase 2 commitments that Phase 3
has invalidated. Without the cycle, three failure modes appear:

- **Silent drift:** The practitioner notes the Phase 2 misalignment
  but proceeds to Phase 4 anyway. Architecture is built on a
  foundation the framework has flagged as broken. The consequences
  surface later, in implementation or production, when remediation
  is significantly more expensive.

- **Ad-hoc workarounds:** The practitioner works around the Phase 2
  misalignment in Phase 4 architecture rather than amending Phase
  2. The workaround creates technical debt that future phases
  inherit, and the original Phase 2 commitments stay in the
  documentation contradicting the actual system.

- **Unstructured remediation:** The practitioner returns to Phase 2
  without the structured amendment package. They guess at what
  needs to change. Some amendments are missed; some unnecessary
  changes are made; the cycle takes longer and produces less
  reliable results.

The amendment cycle is governance, not failure. It is the framework
working as designed.

---

## The Readiness Review

The Step 09 Readiness Review is the phase gate. It is the mechanism
that makes the Phase 3 handoff trustworthy as Phase 4 input.

### What the Gate Evaluates

| Gate Dimension | What It Asks |
|---------------|-------------|
| **Per-principle gates** | Does each Core Principle have sufficient analytical foundation across all eight Phase 3 artifacts? |
| **Per-artifact completeness** | Did each Phase 3 artifact meet its own evaluation checklist? |
| **Cross-artifact consistency within Phase 3** | Do the eight Phase 3 artifacts agree with each other? |
| **Phase 2 alignment** | Has Phase 3 design work invalidated any Phase 2 commitment? |
| **Phase 4 input completeness** | Does each Phase 4 tool set have its required inputs? |

### Gate Status Semantics

| Status | Meaning | Phase 4 Action |
|--------|---------|---------------|
| **READY** | All checks pass | Phase 4 may begin upon practitioner authorization |
| **CONDITIONALLY READY** | One or more conditional gates with documented remediation | Phase 4 may begin work not blocked by conditional gates |
| **NOT READY (Phase 4 gaps)** | One or more blocking gaps in Phase 3 work | Phase 4 cannot begin until Phase 3 remediation completes |
| **NOT READY (Phase 2 amendment required)** | Phase 2 alignment failure | Phase 4 cannot begin until Phase 2 amendment cycle completes and Phase 3 re-runs verify alignment |

### Per-Principle Gate Criteria Summary

**Security — PASS requires:** Step 04 security model ADR commits
authentication, authorization, encryption, audit; commitments
address Phase 2 Step 03 threats per Step 03 §5 simulations; Step
05 Security scores calibrated against Step 04; Step 08 compliance
constraints addressed; Step 07 audit hooks support Step 08 audit
compliance requirements.

**Maintainability — PASS requires:** Step 04 commitments support
Step 05 maintainability target; Step 05 monitoring indicators
measurable; Step 06 protocol establishes cross-phase maintainability
governance; no Step 03 elimination affects maintainability viability.

**Economics — PASS requires:** Step 04 commitments compatible with
Phase 2 Step 02 cost envelope per Step 03 §6 simulations; Step 05
economics scorecard reflects Step 04; no Step 03 simulation
revealed envelope breach without amendment.

**Operations — PASS requires:** Step 04 deployment and observability
ADRs complete; Step 07 hooks support every Phase 2 operations
benchmark; Step 03 §7 failure mode simulations confirm operational
feasibility; Step 05 operations scorecard reflects Step 04.

**Scoring & Metrics — PASS requires:** Step 05 baseline establishes
current and target scores for all six principles; monitoring
indicators measurable across principles; Step 06 protocol governs
cross-phase changes; Step 07 supports the indicators.

**Correctness Verification — PASS requires:** Confidence levels
assigned across Phase 3 artifacts; Step 03 simulations anchor to
Phase 2 benchmarks/threats; Step 04 ADRs cite Step 02 and Step 03
evidence; cross-artifact citations accurate; Phase 2 confidence
levels carry forward without unjustified upgrades.

### Why the Gate Matters

Phase 3 produces the strategic direction Phase 4 architecture will
build on. A weak Phase 3 produces weak architecture, which compounds
through Phase 5 implementation, Phase 6 audit, and Phase 7
operations. The gate is the structural defense against that
compounding.

The four-determination outcome (READY, CONDITIONALLY READY, two
NOT READY variants) reflects the operational reality that Phase 3
gate failures can require different remediation paths. The
structural defense is the explicit four options — there is no
"close enough" or "we'll figure it out" path.

---

## Cross-Phase Living Documents

Phase 3 produces two artifacts explicitly designed to be maintained
by later phases:

### The Principle Scorecard (Step 05)

The Phase 3 baseline scorecard is the most consequential cross-phase
artifact Phase 3 produces. Phases 4, 5, 6, and 7 will all update it
per the Step 06 protocol:

- **Phase 4** updates v2.0 based on architectural commitments
- **Phase 5** updates v3.x based on actual code quality, test
  coverage, security scan results
- **Phase 6** updates v4.0 based on audit findings
- **Phase 7** updates v5.0 at deployment and v5.x in ongoing
  operations

Score regression between phases is a signal that triggers review
per the Step 06 protocol. A principle scoring lower at Phase 6
than at Phase 3 baseline is evidence something has gone wrong in
the intervening phases.

### The Six Design ADRs (Step 04)

The Phase 3 ADRs extend the ADR series begun with the Phase 2
stack ADR. Phase 4 references these ADRs as the strategic
foundation for architectural decisions. Phase 5 references them
when implementation questions arise. Phase 6 references them
during audit. Phase 7 references them when production reality
challenges design assumptions.

Phase 4 may produce its own architecture ADRs that build on these
design ADRs, but it cannot silently supersede them. Substantive
changes to a Phase 3 ADR require a new ADR that explicitly
supersedes it — per standard ADR practice.

---

## Artifact Dependency Map

```
Phase 1 Information Report ──┐
Phase 2 Package ─────────────┤
                             │
                             ▼
Step 01: Design Exploration Specification
   │
   ▼
Step 02: Design Option Scoring
   │
   ▼
Step 03: Simulation & Feasibility Assessment
   │
   ▼
Step 04: Design Direction + 6 ADRs ─────┬─────────────────────────┐
   │                                    │                         │
   ▼                                    ▼                         ▼
Step 05: Scorecard Baseline    Step 07: Observability Hooks   Step 08: Compliance Constraints
   │                                    │                         │
   └────────────────────────────────────┴─────────────────────────┘
                                        │
                                        │  Step 06: Scorecard Update Protocol
                                        │  (parallel — no Phase 3 content dependencies)
                                        │  ────────────────────────────────────┐
                                        │                                      │
                                        ▼                                      │
                              Step 09: Phase 3 Readiness Review  ◄─────────────┘
                              (consumes all 8 prior + Phase 2 + Phase 1)
                                        │
                          ┌─────────────┴─────────────┐
                          │                           │
                          ▼                           ▼
                  Phase 4 Authorization      Phase 2 Amendment Cycle
                  (READY / CONDITIONAL)      (NOT READY — Phase 2 amendment)
```

### Cross-Artifact Connections Step 09 Validates

- Step 04 commits options Step 02 ranked and Step 03 did not
  eliminate
- Step 05 scorecard current scores reflect Step 04 commitments
- Step 05 target scores anchor to Phase 2 benchmarks
- Step 06 protocol references Step 05 baseline correctly
- Step 07 hooks support Step 05 monitoring indicators
- Step 07 hooks cover all Phase 2 operations benchmarks
- Step 07 hooks support detection of Step 03 critical failure modes
- Step 08 audit constraints map to Step 07 audit hooks
- Step 08 security constraints align with Step 04 security model ADR
- Step 04 ADR principle weighting matches Phase 2 Step 01 weighting

---

## Common Pitfalls

**Treating Phase 3 like Phase 2.**
Phase 2 was strictly sequential with self-contained prompts. Phase
3 is dependency-driven with cross-phase living artifacts.
Practitioners who try to run Phase 3 as a sequence miss the
parallelism opportunities and may run Step 06 too late (after the
scorecard baseline already needs governance). The structural
defense is the dependency graph in the instructions file.

**Designing without simulating.**
Choosing the design pattern the team is most familiar with and
moving to architecture without simulation is the article's
explicit warning. The structural defense is Step 03's required
execution before Step 04 — Step 04 cannot run without Step 03
output.

**Scoring after deciding.**
Defining evaluation criteria after the practitioner has stated a
preferred direction makes scoring rationalization. The structural
defense is Step 01's establishment of criteria before Step 02
scoring begins, and Step 02's prohibition on adjusting criteria
during scoring.

**Locking too much or too little.**
Phase 3 locks strategic direction — system structure, interaction
patterns, data architecture, deployment model, security model,
observability strategy. It does not lock module boundaries, API
schemas, or implementation details. The structural defense is the
Step 04 output template's lack of fields for module-level
specifications.

**Skipping the scorecard baseline.**
Without the scorecard, the team has no way to detect regression in
later phases. The structural defense is Step 09's verification
that the scorecard baseline exists and is calibrated before
authorizing Phase 4.

**Skipping the update protocol.**
Without Step 06, the scorecard's cross-phase governance is
undefined. Phases 4–7 would invent their own protocols, producing
inconsistent updates and undetectable drift. The structural
defense is Step 09's verification that Step 06 is present.

**Treating forward-looking concerns as optional.**
Observability hooks (Step 07) and compliance design constraints
(Step 08) are required Phase 4 inputs. Skipping them means Phase
4 retrofits observability and compliance, which produces
incidents and audit findings later. The structural defense is
Step 09's Phase 4 input completeness check.

**Ignoring Phase 2 invalidation.**
If Phase 3 design work reveals a Phase 2 commitment is wrong, the
correct response is the amendment cycle — not silent adjustment
or working around the problem. The structural defense is Step
09's NOT READY (Phase 2 amendment required) determination with
the structured §5.2 amendment package.

**Overriding the Readiness Review without documentation.**
The override mechanism exists to accommodate pressure, not to
normalize bypassing the framework. The structural defense is Step
09's required override section with tiered authority requirements,
specific rationale, concrete risk acceptance, and named revisit
conditions.

**Producing Phase 4 architecture content in Phase 3 prompts.**
Phase 3 produces strategic direction, not architecture. The most
common drift is in Step 07 (toward Phase 4 tool selection) and
Step 08 (toward Phase 4 implementation specifics). The structural
defense is per-prompt prohibition lists and the absence of
implementation sections in output templates.

---

## Connecting to Phase 4

Phase 3 hands off a coherent multi-artifact package to Phase 4
(Architecture & Modular Design). Phase 4 tool sets each consume
specific Phase 3 outputs:

| Phase 4 Concern | Phase 3 Inputs Consumed |
|-----------------|------------------------|
| Module Boundary Design | Step 04 system structure ADR, Step 04 Design Direction Document §3.1 |
| API Specification | Step 04 interaction patterns ADR |
| Security Architecture | Step 04 security model ADR, Step 08 Compliance Design Constraints, Phase 2 threat model |
| Data Architecture | Step 04 data architecture ADR, Step 08 data handling constraints |
| Deployment Architecture | Step 04 deployment model ADR, Step 08 residency constraints |
| Observability Architecture | Step 04 observability strategy ADR, Step 07 Observability Hooks Handoff |
| Governance and Ownership | Step 04 all ADRs, Step 05 Scorecard, Step 06 Update Protocol |
| Phase 4 Scorecard Updates | Step 05 Scorecard baseline, Step 06 Update Protocol |

The Step 09 Readiness Review verifies each Phase 4 concern has its
required Phase 3 inputs before authorizing Phase 4 to begin. The
Phase 4 Handoff Summary in Step 09 §9 is structured for direct
consumption by Phase 4 tool sets.

Phase 4 does not re-litigate Phase 3 decisions. It takes the locked
direction as given and produces the architecture that implementation
will build on. Phase 4 updates the Principle Scorecard per the Step
06 protocol. Phase 4 may produce new ADRs that build on Phase 3
design ADRs but cannot silently supersede them.

A shaky Phase 3 produces shaky architecture, which compounds through
the rest of the framework. The gate exists to prevent that
compounding — and the Phase 2 amendment cycle exists to prevent
that compounding from inheriting bad Phase 2 commitments.

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | [date] | Initial release — instructions file plus nine prompts |

---

## Related Resources

- [AI-Centric Software Development Playbook — Full Series](../../README.md)
- [Article 1 — Core Principles](../../articles/article-01-core-principles.md)
- [Article 2 — Building Your Toolkit](../../articles/article-02-building-your-toolkit.md)
- [Article 5 — Phase 3: Design & Technical Analysis](../../articles/article-05-design-technical-analysis.md)
- [Phase 1 Tool Set](../phase-1-information-gathering/README.md)
- [Phase 2 Tool Set](../phase-2-analysis-stack-selection/README.md)
- [Phase 4 Tool Set](../phase-4-architecture-modular-design/README.md) *(forthcoming)*

---

*Part of the AI-Centric Software Development Playbook*
*This tool set is a living artifact — it will be refined as the
methodology matures and use in practice reveals improvements.*