# Phase 2: Analysis & Stack Selection — Tool Set
## AI-Centric Software Development Playbook

---

## Overview

This directory contains the complete tool set for **Phase 2: Analysis &
Stack Selection** of the AI-Centric Software Development Playbook.
Phase 2 transforms the evidence gathered in Phase 1 into committed
decisions: a validated business case, a structured cost model, a
committed technology stack documented as an Architecture Decision
Record (ADR), an initial threat model, and a versioned benchmark
framework.

This is the phase where evidence becomes commitment. The decisions
made here constrain every subsequent phase and produce the analytical
foundation that Phase 3 (Design & Technical Analysis) builds on. Done
well, Phase 2 gives the team a principle-scored, internally consistent
foundation. Done poorly — or compressed for speed — every subsequent
phase inherits decisions that were never properly grounded.

The primary output of this phase is **a coherent multi-artifact
package** consumed by Phase 3, gated by a formal Readiness Review
that determines whether the package is sufficient to authorize
Phase 3 to begin.

---

## Framework Context

This tool set is part of the [AI-Centric Software Development
Playbook](../../README.md), a practitioner's framework for small teams
(1–5 people) that use AI tools to deliver what large organizations
once required.

Three framework concepts are essential to understanding how Phase 2
operates:

### Phase 2 Differs From Phase 1 in Character

| Dimension | Phase 1 | Phase 2 |
|-----------|---------|---------|
| Primary work | Gathering evidence | Making commitments |
| AI role | Research strategist and domain analyst | Analytical partner supporting commitment-grade decisions |
| Session pattern | Long conversational interviews | Context paste → brief clarification → analytical output |
| Primary input | Practitioner knowledge | The Information Report + prior Phase 2 artifacts |
| Primary output | Evidence and options | Scored decisions with documented rationale |
| Number of prompts | 6 | 7 |
| Gate mechanism | Self-evaluation in synthesis prompt | Dedicated Readiness Review prompt |

Phase 2 prompts are **action-oriented by default**. The practitioner
pastes structured evidence, the AI asks a small number of clarifying
questions (single digits, never more), and the AI produces the
analytical artifact. Phase 1's interview-first conversational pattern
does not carry forward — Phase 2 has the evidence base and uses it.

### The Six Core Principles — Now as Decision Framework

In Phase 1, the principles were a research lens shaping what to
gather. In Phase 2, they become a **decision-making framework**. Every
analytical output is structured around the principles, every
evaluation scores against them, and the **principle weighting**
established in Step 01 drives the scored ranking in Step 04.

| Principle | Phase 2 Application |
|-----------|---------------------|
| **Security** | Threat modeling begins. Compliance constraints become technical requirements. Stack security characteristics are scored. |
| **Maintainability** | Long-term viability of candidate stacks is evaluated — documentation, community, testing, talent pool. |
| **Economics** | The cost model captures the full lifecycle across three scale points with named assumptions. Economics becomes concrete. |
| **Operations** | Production reality is evaluated for each candidate — deployment, scaling, observability, interoperability. |
| **Scoring & Metrics** | The scoring framework is **established here** — principle weighting, evaluation criteria, benchmark targets. These become measuring sticks for every subsequent phase. |
| **Correctness Verification** | The verification capabilities of each candidate stack are evaluated, and the analysis itself is verified for evidence-grounding and confidence discipline. |

### Specification Driven Development (SDD)

Phase 2 runs the SDD cycle a second time — but the Specify step draws
from the Phase 1 Information Report rather than from scratch. The
practitioner is not starting with a blank page.

```
Specify → Plan → Detail → Task → Implement
```

| SDD Step | What Happens in Phase 2 | Output |
|----------|-------------------------|--------|
| **Specify** | Articulate the full scope of decisions this phase must produce | Analysis specification |
| **Plan** | Break the analysis into distinct analytical domains | Analysis plan |
| **Detail** | Generate evaluation criteria, scoring rubrics, benchmark frameworks | Analysis requirements per domain |
| **Task** | Identify specific analyses within each domain | Task list with inputs and outputs |
| **Implement** | Execute analytical tool sets, produce artifacts, commit decisions, run Readiness Review | Six analytical artifacts + ADR + Readiness Review |

The cycle is iterative. When the Readiness Review surfaces inconsistency
between artifacts, cycle back to the relevant prompt. When clarification
in one prompt reveals a gap in another, update the affected artifact
before committing.

---

## Directory Contents

```
phase-2-analysis-stack-selection/
├── README.md                                            ← You are here
├── analysis-stack-selection.instructions.md            ← Load as project context
├── step-01-business-analysis.prompt.md                 ← Business case + principle weighting
├── step-02-cost-modeling.prompt.md                     ← Lifecycle cost model
├── step-03-threat-modeling.prompt.md                   ← Initial threat model
├── step-04-stack-evaluation.prompt.md                  ← Weighted scorecard
├── step-05-architecture-decision-record.prompt.md     ← ADR — committed stack
├── step-06-benchmark-definition.prompt.md              ← Versioned benchmark framework
└── step-07-phase-2-readiness-review.prompt.md         ← The gate
```

---

## File Descriptions

### `analysis-stack-selection.instructions.md`
**Type:** Instructions file (load once as persistent project context)

The overarching context for any AI assistant operating in Phase 2.
Loaded once and remains active across all seven prompt sessions.
Contains the framework orientation, the SDD cycle for this phase,
all six Core Principles applied as decision criteria, the principle
weighting protocol, behavioral guidelines, output standards, and the
Phase 3 handoff connection. Designed for use as Claude Project
Instructions, GitHub `copilot-instructions.md`, Cursor rules, or
the equivalent in other AI environments.

This file plays a **lighter coordinating role** than its Phase 1
counterpart. Each Phase 2 prompt is self-contained and includes its
own system instructions. The instructions file ensures the larger
framework context is consistent across all sessions and makes sure
the artifacts cohere into a Phase 3-ready package.

---

### `step-01-business-analysis.prompt.md`
**Type:** Action Prompt with Clarification Step

Produces a composite document with two clearly separated sections:
**(A) Business Case** — problem definition, users, value proposition,
business model, success criteria, project character — and **(B)
Principle Weighting** — the 100-point distribution across the six
Core Principles for this specific project.

**Key design decision:** The principle weighting is folded into this
step rather than being a standalone prompt because weighting is a
business judgment grounded in project character — not a technical
exercise. Weighting set in Step 01 travels forward as a named input
to Step 04, where it drives the scored ranking. The 100-point sum
forces explicit trade-offs: increasing one principle's weight
mathematically reduces another's. Equal weighting is permitted but
must be defended as deliberate.

**Critical constraint:** Weighting is set **before** any stack
scoring happens. Adjusting weights after seeing scores is retrofitting
and is not permitted. If later analysis reveals the weighting was
wrong, the correct response is to update Step 01 with a tracked
revision and re-run Step 04 — not silently adjust.

---

### `step-02-cost-modeling.prompt.md`
**Type:** Action Prompt with Clarification Step

Produces a structured Cost Model covering the full system lifecycle
at **three scale points** (MVP, mid-scale, full-scale) with named
assumptions, sensitivity analysis on the most influential assumptions,
and per-stack economic comparison.

**Key design decision:** Pricing data is supplied by the practitioner.
The AI does not have reliable access to current cloud pricing,
licensing terms, or AI tooling costs — values from training cutoffs
go stale quickly. The prompt documents the **MCP integration upgrade
path** explicitly: when MCP servers connect to cloud provider pricing
APIs and licensing portals, the manual paste step is replaced by
automated data collection. The prompt's structure is designed so
this upgrade does not require rewriting the cost model format.

**Structural defense against the launch-budget failure mode:** The
template structurally requires three scale points with concrete metrics
(active users, request volume, storage, team size). There is no
single-point-in-time slot where an optimistic launch number can hide.
Every cost figure ties to a named assumption with an ID, threading
through every dependent figure for traceability.

**The AI does not declare a winner.** Economics is one of six
principles. The cost model compares stacks; Step 04 integrates that
with the other principles to produce the ranking.

---

### `step-03-threat-modeling.prompt.md`
**Type:** Action Prompt with Clarification Step

Produces the **initial** threat model that Phase 4 security
architecture will build on. Covers data flow analysis, trust
boundary inventory, threat catalog with risk ranking, threat actor
profile, and a structured Phase 4 handoff package.

**Key design decisions:**

- **Framework selection happens via clarification, not default.** The
  AI's first clarifying question asks the practitioner to choose
  STRIDE, LINDDUN, PASTA, or OCTAVE — or defer to AI recommendation
  based on Information Report domain context. The framework choice
  is settled before any other clarification because it shapes the
  rest of the analysis structure.

- **Dual-format data flow representation.** Structured tables are the
  source of truth; Mermaid diagrams are the visualization layer. The
  table is canonical — when they conflict, the table is correct. This
  matches the framework's dual-consumption principle (human-readable
  + AI-parseable) while remaining robust to Mermaid syntax errors.

- **Hard structural scope boundary.** The output template literally
  does not have fields for control implementation, security
  architecture patterns, encryption schemes, audit logging
  architecture, or other Phase 4 work. Threats are identified at the
  trust boundary level, not the module level. The Phase 4 handoff
  package frames items as **architectural questions Phase 4 must
  answer**, not as answers. The structural defense is what prevents
  Phase 2 threat modeling from drifting into Phase 4 territory with
  incomplete inputs.

---

### `step-04-stack-evaluation.prompt.md`
**Type:** Action Prompt with Clarification Step

Produces the Stack Evaluation Scorecard — the analytical heart of
Phase 2. Sub-criteria scoring per Core Principle per candidate stack,
principle aggregates, weighted totals using Step 01 weights, ranked
comparison, trade-off documentation, and dual sensitivity analysis
(score perturbation + weight perturbation).

**Key design decisions:**

- **Sub-criteria with explicit definitions, not bare principle scores.**
  Each principle decomposes into five sub-criteria with definitions.
  Bare scores ("Security: 4") are unfalsifiable; sub-criteria scores
  with evidence ("Memory safety: 5 — Rust enforces at compile time"
  + "Security tooling maturity: 3 — established but smaller ecosystem
  than Go") are auditable.

- **Weights are not adjustable here.** The principle weighting is an
  input from Step 01 and may not be modified during scoring. If
  scoring reveals the weighting was wrong, the correct response is
  return to Step 01, document the revision, and re-run Step 04.
  Silently adjusting weights to produce a different ranking is the
  most damaging anti-pattern in this phase.

- **No declared winner.** The artifact ranks candidates by weighted
  total. It does not commit a decision. The commitment happens in
  Step 05 (ADR) by the practitioner. Conflating ranking with
  commitment removes the governance moment where the practitioner
  explicitly authorizes the choice.

- **Cross-Artifact Tension Register.** Tensions between the cost
  model and the threat model, between the business case and the
  weighting, between the Information Report and the scoring — these
  are surfaced explicitly. A practitioner committing without seeing
  tensions is committing blind.

---

### `step-05-architecture-decision-record.prompt.md`
**Type:** Action Prompt with Clarification Step (governance-focused)

Produces the **Architecture Decision Record (ADR)** — the formal,
permanent commitment to a specific technology stack. Uses the
standard ADR format (Status / Context / Decision / Consequences /
Alternatives Considered) with framework-specific extensions for
principle weighting traceability, divergence rationale, and revision
triggers.

**Key design decisions:**

- **Governance artifact, not analytical.** Steps 01–04 produced
  analysis. Step 05 produces a commitment. The AI's role is
  documentation, not evaluation. It does not re-score, re-rank, or
  second-guess the practitioner's choice.

- **The practitioner can commit a stack that was not top-ranked.**
  Step 04 produces a ranking; the practitioner has authority to
  commit a different choice with documented rationale. The prompt
  accommodates this but requires **specific, evidence-grounded
  divergence rationale**. "Team preference" without elaboration is
  not acceptable.

- **Revision triggers are measurable, not aspirational.** "If costs
  go up significantly" is not a trigger. "If infrastructure cost at
  mid-scale exceeds $X by 25% sustained over 3 months" is. Each
  trigger has a named source of truth and a defined action when
  fired.

- **ADRs are permanent once approved.** Substantive changes require
  superseding ADRs, not in-place edits. The Amendment Log
  accommodates non-substantive corrections without enabling silent
  rewriting of substance.

---

### `step-06-benchmark-definition.prompt.md`
**Type:** Action Prompt with Clarification Step

Produces the versioned **Benchmark Framework** — quantitative targets
for every Core Principle at every scale point, calibrated against the
committed stack from Step 05. Phase 3, 5, 6, and 7 tool sets reference
this artifact by version number throughout the project lifecycle.

**Key design decisions:**

- **AI proposes, practitioner calibrates.** Each benchmark has both
  AI-Proposed and Practitioner-Calibrated value fields. Realism is
  the practitioner's responsibility — they have domain context the
  AI lacks. Even when the practitioner accepts the AI proposal
  without changes, the calibration note "Accepted without modification"
  makes the acceptance an explicit governance act rather than an
  absence.

- **Versioning with explicit change control.** Initial framework is
  v1.0. Amendments (clarifications, refinements within the original
  range) are documented in the Version Log. Substantive changes
  (target values outside the original range, additions, removals,
  methodology changes) require a new ADR that supersedes or amends
  Step 05's ADR, then re-running this prompt to produce the next
  version. Silent drift is detectable as a governance defect.

- **All six Core Principles get benchmark coverage.** Performance
  benchmarks are easy; Maintainability, Scoring & Metrics, and
  Correctness Verification benchmarks are hard. Organizing the
  template by principle means each principle has a section that
  cannot be empty without explicit acknowledgment.

- **Calibrated to the committed stack, not generic industry data.**
  Comparable-system data from Phase 1 is the calibration baseline,
  not the target. Adjustments based on stack characteristics, project
  scale assumptions, risk tolerance, and threats from Step 03 are
  required.

---

### `step-07-phase-2-readiness-review.prompt.md`
**Type:** Evaluation Prompt (Gate)

Produces the **Phase 2 Readiness Review** — the formal gate that
determines whether the Phase 2 work product is sufficient to authorize
Phase 3 to begin. Mirrors the Phase 1 self-evaluation pattern but
adapted for Phase 2's multi-artifact handoff.

**Key design decisions:**

- **Three-tier evaluation structure.** Per-principle gates (does each
  Core Principle have sufficient analytical foundation?), per-artifact
  completeness (does each artifact meet its own evaluation checklist?),
  cross-artifact consistency (do the six artifacts agree with each
  other?). A package can pass per-principle and per-artifact checks
  individually and still ship inconsistencies — the third check is
  the structural defense.

- **Phase 3 input completeness check.** Phase 3 has tool sets that
  each require specific inputs. The review verifies each Phase 3 tool
  set has its required inputs available before authorizing Phase 3
  to begin.

- **PASS / CONDITIONAL / NOT READY — no fourth option.** The
  determination is one of three values; "good enough" is not a status.
  CONDITIONAL gates require named owners, target dates, and explicit
  blocked Phase 3 work items. Conditional gates that accumulate
  without remediation degrade into silent failures over time.

- **Override mechanism is structural, not negotiated.** If the
  practitioner chooses to authorize Phase 3 despite a NOT READY or
  unresolved CONDITIONAL determination, the override is documented
  with specific rationale, concrete risk being accepted, and named
  conditions for revisit. The AI's determination stands; the override
  stands alongside it. Both are visible in the audit trail.

- **No new analysis content.** The review evaluates what is there. If
  an artifact is missing required content, the answer is NOT READY
  with a required action that returns to the responsible prior step
  — not patching here.

---

## How to Use This Tool Set

### Prerequisites

Before opening any prompt file:

1. Confirm the [Phase 1 Information Report](../phase-1-information-gathering/README.md)
   is complete with a passing self-evaluation scorecard. Phase 2
   cannot responsibly begin on a failed Phase 1 gate.
2. Load `analysis-stack-selection.instructions.md` as project-level
   instructions in your AI environment. This gives every Phase 2
   session the framework context, behavioral guidelines, and output
   standards without re-establishing them per session.

### Required Execution Order

**Execution order is load-bearing.** Phase 1 prompts could be run in
any order; Phase 2 prompts cannot. Later prompts consume earlier
outputs as required inputs:

```
Step 01: Business Analysis & Principle Weighting
   ↓ (provides weighting + business context)
Step 02: Cost Modeling
   ↓ (provides cost envelope + scale points)
Step 03: Initial Threat Modeling
   ↓ (provides threats + stack implications + Phase 4 handoff)
Step 04: Stack Evaluation
   ↓ (consumes weighting + cost data + threat data; produces ranking)
Step 05: Architecture Decision Record
   ↓ (commits the practitioner's chosen stack)
Step 06: Benchmark Definition
   ↓ (calibrated against the committed stack)
Step 07: Phase 2 Readiness Review
   ↓ (gates Phase 3 authorization)
Phase 3: Design & Technical Analysis (only if Step 07 passes)
```

Running Step 04 before Step 01 means scoring without weighting.
Running Step 06 before Step 05 means calibrating against an
uncommitted stack. Running Step 07 with missing inputs structurally
forces a NOT READY determination.

### Running Each Prompt

For each step:

1. Open a new AI session with a large context window
2. Confirm `analysis-stack-selection.instructions.md` is loaded as
   project context
3. Paste **all required inputs** above the kickoff line — see the
   prompt's metadata table for the exact list
4. Paste any prompt-specific data (e.g., pricing data for Step 02,
   commitment statement for Step 05)
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

- **Step 04 reveals weighting was wrong** → return to Step 01, update
  weighting with documented revision, re-run Step 04
- **Step 06 reveals benchmarks are unachievable on the committed
  stack** → return to Step 05, evaluate whether to amend or supersede
  the ADR, then re-run Step 06
- **Step 07 returns CONDITIONAL or NOT READY** → execute the named
  required actions in the responsible prior step, then re-run Step 07

This is expected behavior, not failure. The gate system catches
inconsistency before it propagates into Phase 3 where remediation
is significantly more expensive.

---

## The Readiness Review

The Step 07 Readiness Review is the phase gate. It is the mechanism
that makes the Phase 2 handoff trustworthy as Phase 3 input.

### What the Gate Evaluates

| Gate Dimension | What It Asks |
|---------------|-------------|
| **Per-principle gates** | Does each Core Principle have sufficient analytical foundation across all six artifacts? |
| **Per-artifact completeness** | Did each artifact meet its own evaluation checklist? |
| **Cross-artifact consistency** | Do the six artifacts agree with each other? |
| **Phase 3 input completeness** | Does each Phase 3 tool set have its required inputs? |

### Gate Status Semantics

| Status | Meaning | Phase 3 Action |
|--------|---------|---------------|
| **READY** | All checks pass | Phase 3 may begin upon practitioner authorization |
| **CONDITIONALLY READY** | One or more conditional gates with documented remediation | Phase 3 may begin work not blocked by conditional gates; remediation completes before dependent work |
| **NOT READY** | One or more blocking gaps | Phase 3 cannot begin until remediation completes |

### Per-Principle Gate Criteria Summary

**Security — PASS requires:** Threat model with data flows, trust
boundaries, threat catalog, risk rankings, Phase 4 handoff package,
compliance mapping; stack security score in Step 04 supported by
threat model evidence; Step 05 ADR addresses security trade-offs;
Step 06 includes security benchmarks at all three scale points.

**Maintainability — PASS requires:** Step 04 sub-criteria coverage
across documentation, community, testing, talent, viability; Step 05
ADR includes maintainability trade-offs; Step 06 includes
maintainability benchmarks; no NOT READY signals from Phase 1 on
maintainability for the committed stack.

**Economics — PASS requires:** Cost model covers all three scale
points with named assumptions; uses the committed stack from Step 05;
pricing gaps resolved or documented; Step 06 economic benchmarks
align with Step 02 projections; Step 05 ADR addresses economic
trade-offs and revision triggers; sensitivity analysis present.

**Operations — PASS requires:** Step 04 sub-criteria coverage of
deployment, scaling, observability, complexity, interoperability;
Step 06 includes operations benchmarks at all three scale points;
Phase 4 observability hooks identified; Step 05 ADR addresses
operational trade-offs.

**Scoring & Metrics — PASS requires:** Principle weighting sums to
100; weighting applied consistently in Step 04 (no silent
adjustments); Step 06 covers all six principles with measurement
methodology specified; scoring infrastructure benchmarks present.

**Correctness Verification — PASS requires:** Step 04 sub-criteria
coverage of type system, formal verification, static analysis,
specification conformance; Step 06 includes correctness verification
benchmarks; confidence levels assigned across all artifacts; cross-
artifact citations accurate; Phase 1 low-confidence findings not
silently upgraded.

### Why the Gate Matters

The cost of a falsely-PASS gate is felt in Phase 3 when the team
builds on a weak foundation. The cost of a CONDITIONAL gate that
turns out to be conservative is a half-hour of confirmation. The
gate is calibrated to favor the conservative outcome.

A team that overrides multiple gates per phase silently is operating
outside the framework. A team that overrides one gate with documented
justification is operating with discipline under pressure. The
override mechanism exists to make pressure visible — not to
normalize bypassing the framework.

---

## Artifact Dependency Map

```
Phase 1 Information Report
   │
   ▼
Step 01: Business Analysis & Principle Weighting
   │   (produces business case + weighting)
   ▼
Step 02: Cost Modeling                          Step 03: Threat Modeling
   │   (uses business case)                        │   (uses business case + cost)
   │                                                │
   └─────────────┬──────────────────────────────────┘
                 ▼
Step 04: Stack Evaluation
   │   (consumes weighting + cost + threats)
   │   (produces scored ranking)
   ▼
Step 05: Architecture Decision Record (ADR)
   │   (practitioner commits stack)
   ▼
Step 06: Benchmark Definition
   │   (calibrated against committed stack)
   ▼
Step 07: Phase 2 Readiness Review
   │   (consumes all six prior artifacts + Information Report)
   ▼
Phase 3: Design & Technical Analysis
```

### Cross-Artifact Connections the Readiness Review Validates

- Step 02 cost model uses the Step 05 committed stack (not an earlier
  candidate set)
- Step 03 threat model covers data flows implied by Step 01 user
  workflows
- Step 04 weighting matches Step 01 weighting exactly
- Step 04 scoring evidence is traceable to Information Report and
  Steps 02–03
- Step 05 ADR documents the stack ranked or justifies divergence
- Step 06 economic benchmarks align with Step 02 cost projections
- Step 06 security benchmarks align with Step 03 threat priorities
- Step 06 benchmarks match the ambitions of the Step 01 business case
- Phase 1 confidence levels carry forward without unjustified upgrades

---

## Common Pitfalls

**Treating Phase 2 like Phase 1.**
Phase 1 was conversational and exploratory. Phase 2 is action-oriented
and decision-grade. Long discursive interviews waste tokens and
produce unfocused output. Paste structured evidence, answer focused
clarifications, accept the structured output.

**Adjusting principle weights after seeing scores.**
The single most damaging anti-pattern in this phase. Setting weights
after seeing which stack wins is retrofitting. The structural defense
is in Step 04 (weights from Step 01 are an input, not a parameter)
and the Readiness Review (cross-artifact consistency check verifies
weights match Step 01 exactly).

**Cost models without scale assumptions.**
A cost model that captures only the MVP is a launch budget. The
structural defense is Step 02's required three scale points with
concrete metrics. Every cost figure ties to a scale point — there is
no slot for floating monthly costs.

**Threat models that defer the work to Phase 4.**
A threat model produced after architecture is a compliance exercise.
The structural defense is Step 03's hard scope boundary — the output
template has no fields for control implementation, and threats are
identified at trust boundary level rather than module level. This
forces threat modeling to be a design input rather than design output.

**Conflating ranking with commitment.**
Step 04 ranks; Step 05 commits. The structural defense is the
prohibition on Step 04 declaring a "winner" and the requirement that
Step 05 be authorized by the practitioner with explicit divergence
rationale if not the top-ranked stack. Without this separation, the
governance moment where the practitioner authorizes the decision
disappears.

**Vague revision triggers in the ADR.**
"If costs go up significantly" triggers nothing because there is no
measurable test. The structural defense is Step 05's required trigger
table with named source of truth and defined action — vague triggers
fail the evaluation checklist.

**Benchmarks that drift between phases.**
A benchmark that quietly shifts is a measuring stick that lies. The
structural defense is Step 06's versioning with explicit change
control — substantive changes require a new ADR, not silent edits.
Phase tool sets reference benchmarks by version number, making drift
detectable.

**Overriding the Readiness Review without documentation.**
The override mechanism exists to accommodate pressure, not to
normalize bypassing the framework. The structural defense is Step
07's required override section with specific rationale, concrete
risk acceptance, and named revisit conditions. An undocumented
override is a governance defect.

**Producing Phase 3 or Phase 4 content in Phase 2 prompts.**
Phase 2 produces analytical foundations, not design or architecture.
The most common drift is in threat modeling (toward Phase 4 controls)
and stack evaluation (toward implementation guidance). The structural
defense is per-prompt prohibition lists and the absence of
architecture sections in templates — there is nowhere to put the
content even if the AI tries to produce it.

---

## Connecting to Phase 3

Phase 2 hands off a coherent multi-artifact package to Phase 3 (Design
& Technical Analysis). Phase 3 has tool sets that each consume specific
Phase 2 outputs:

| Phase 3 Tool Set | Phase 2 Inputs Consumed |
|------------------|------------------------|
| Design Analysis | Step 01 Business Case, Step 05 ADR |
| Stack Stress-Testing (Simulation) | Step 04 Scorecard, Step 05 ADR, Step 06 Benchmarks |
| Principle Scorecard Baseline | Step 01 Weighting, Step 04 Sub-Criteria, Step 06 Benchmarks |
| Compliance Design Constraints | Step 03 Compliance Confirmations, Information Report Compliance Map |
| Observability Strategy | Step 03 Phase 4 Handoff §8.1, Step 06 Operations Benchmarks |
| Threat Model Forward Reference | Step 03 §8 Phase 4 Handoff Package |

The Step 07 Readiness Review verifies each Phase 3 tool set has its
required inputs before authorizing Phase 3 to begin. The Phase 3
Handoff Summary in Step 07 §8 is structured for direct consumption by
Phase 3 tool sets — Phase 3 practitioners can use it as immediate
context without re-reading all six prior artifacts.

Phase 3 does not re-litigate Phase 2 decisions. It takes them as given
and produces the design direction that Phase 4 will architect. A shaky
Phase 2 produces shaky Phase 3 — which compounds through the rest of
the framework. The gate exists to prevent that compounding.

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | [04/25/26] | Initial release — instructions file plus seven prompts |

---

## Related Resources

- [AI-Centric Software Development Playbook — Full Series](../../README.md)
- [Article 1 — Core Principles](../../articles/article-01-core-principles.md)
- [Article 2 — Building Your Toolkit](../../articles/article-02-building-your-toolkit.md)
- [Article 4 — Phase 2: Analysis & Stack Selection](../../articles/article-04-analysis-stack-selection.md)
- [Phase 1 Tool Set](../phase-1-information-gathering/README.md)
- [Phase 3 Tool Set](../phase-3-design-technical-analysis/README.md) *(forthcoming)*

---

*Part of the AI-Centric Software Development Playbook*
*This tool set is a living artifact — it will be refined as the
methodology matures and use in practice reveals improvements.*