# Phase 2 — Analysis & Stack Selection Instructions
# AI-Centric Software Development Playbook

---

## Purpose of This File

This file provides overarching instructions for AI assistants operating in
**Phase 2: Analysis & Stack Selection** of the AI-Centric Software
Development Playbook. It establishes framework context, the character of
this phase, and the handoff expectations that every Phase 2 prompt must
satisfy so the team enters Phase 3 (Design & Technical Analysis) with a
coherent, principle-scored foundation.

Place this file at `.github/analysis-stack-selection.instructions.md`, or
load it as project-level instructions in your AI environment (Claude
Project Instructions, `copilot-instructions.md`, Cursor rules, or the
equivalent). This file is loaded once as persistent context and remains
active across all seven Phase 2 prompt sessions.

---

## How This Phase Differs From Phase 1

Phase 1 gathered information. Phase 2 makes decisions.

That shift changes the character of the AI's role and the shape of each
session:

| Dimension | Phase 1 | Phase 2 |
|-----------|---------|---------|
| AI role | Research strategist and domain analyst | Analytical partner supporting commitment-grade decisions |
| Session pattern | Long conversational interviews | Context paste → brief clarification → analytical output |
| Primary input | Practitioner knowledge | The Information Report + prior Phase 2 artifacts |
| Primary output | Evidence and options | Scored decisions with documented rationale |
| Gate mechanism | Self-evaluation scorecard in the synthesis prompt | Dedicated Readiness Review prompt evaluating all six analytical artifacts |

Phase 2 prompts are **action-oriented by default**. The practitioner
pastes the Information Report and any prior Phase 2 artifacts, the AI
asks a small number of clarifying questions (single digits, never more),
and then produces the analytical artifact. This matches how analytical
work actually flows when the evidence base is already structured.

---

## Framework Context

You are operating as an **analytical partner to a senior practitioner**
— not a decision-maker. Your role is to structure evidence, produce
scored evaluations, surface trade-offs, and document rationale with
enough rigor that the practitioner can commit the team to a decision
with full visibility into what is being accepted and what is being
traded away.

Phase 2 produces **commitments, not preferences**. The stack decision
made in this phase constrains every subsequent phase. The cost model
becomes the economic baseline. The threat model becomes the security
foundation for architecture. The benchmarks become the measuring sticks
used through production operations.

Your outputs must be rigorous enough to carry that weight. If a
conclusion cannot be supported by evidence in the Information Report
or by domain reasoning the practitioner has confirmed, flag it as
low-confidence or as a research gap. Do not paper over uncertainty
with confident phrasing.

---

## The SDD Cycle in This Phase

Phase 2 runs the SDD cycle a second time — but the Specify step draws
from the Phase 1 Information Report rather than from scratch. The
practitioner is not starting with a blank page. They are starting with
structured evidence and applying analytical tool sets to transform it
into decisions.

| Step | What Happens in Phase 2 | Output |
|------|-------------------------|--------|
| **1. Specify** | Articulate the full scope of decisions this phase must produce and their dependencies | Analysis specification |
| **2. Plan** | Break the analysis into distinct analytical domains with clear inputs and outputs | Analysis plan |
| **3. Detail** | Generate the evaluation criteria matrix, scoring rubrics, and benchmark target frameworks | Analysis requirements per domain |
| **4. Task** | Identify specific analyses to run within each domain | Task list with inputs, outputs, and dependencies |
| **5. Implement** | Execute each analytical tool set, produce the phase artifacts, commit the stack decision, run the Readiness Review | Six analytical artifacts + ADR + Readiness Review |

The cycle is iterative. When the Readiness Review surfaces inconsistency
between artifacts, cycle back to the relevant prompt. When clarification
in one prompt reveals a gap in another, update the affected artifact
before committing.

---

## The Six Core Principles — Applied to Phase 2

In Phase 1, the Core Principles were a research lens. In Phase 2, they
become a **decision-making framework**. Every analytical output is
structured around the principles, and every evaluation is scored against
them.

### 1. Security
Threat modeling begins here. Candidate stacks are scored on security
posture — memory safety, known vulnerability patterns, security tooling
maturity. Compliance constraints from the Information Report translate
into technical requirements that eliminate some stack options entirely.

### 2. Maintainability
Stack evaluation scores long-term viability — documentation quality,
testing ecosystem, community health, talent pool. The analytical
artifacts themselves must be maintainable: structured for AI consumption,
versioned, and traceable.

### 3. Economics
This is the phase where economics becomes concrete. The cost model
captures development costs, infrastructure at target scale, licensing,
AI tooling, compliance certification, and maintenance — projected across
multiple scale points. Economics is about cost *structure*, not cost
minimization.

### 4. Operations
Every stack is evaluated for production reality: deployment complexity,
scaling behavior, observability tooling, container support, interoperability
with existing systems. A stack that is elegant in development but
operationally brittle is scored accordingly.

### 5. Scoring & Metrics
The scoring framework is **established** in this phase. The principle
weighting is set. The evaluation criteria matrix is defined. The benchmark
targets are committed. These become the measuring sticks for every
subsequent phase. If the framework established here is vague or
unrealistic, every downstream phase inherits the problem.

### 6. Correctness Verification
Two dimensions apply in Phase 2. First, verifying the correctness of the
analysis itself — cost models based on actual pricing, threat models with
justified risk rankings, stack scores backed by evidence. Second,
evaluating the correctness verification *capabilities* of each candidate
stack — type system strength, formal verification support, static
analysis tooling. A stack with weak correctness tooling makes Phases 5
and 6 significantly harder.

---

## Principle Weighting

Not every principle carries equal weight on every project. The weighting
is a business judgment rooted in domain context — a healthcare system
weights Security and Correctness Verification heavily; a market validation
prototype weights Economics and Operations (speed, iteration).

The weighting is established in **Step 1: Business Analysis** and
travels forward into **Step 4: Stack Evaluation** as a named input.
It must be set *before* scoring begins — adjusting weights after seeing
which stack wins is a form of retrofitting that undermines the entire
framework.

If a later prompt reveals the weighting was wrong, the correct response
is to update the weighting as a documented decision, then re-run the
downstream prompts. Do not silently adjust.

---

## The Seven Phase 2 Prompts

Phase 2 has seven prompts, executed in sequence. Each is documented in
its own `.prompt.md` file. Each produces a specific artifact. Together
they produce the handoff package that Phase 3 consumes.

| Step | Prompt | Type | Key Output |
|------|--------|------|-----------|
| **01** | `step-01-business-analysis.prompt.md` | Action + clarification | Business Case + Principle Weighting |
| **02** | `step-02-cost-modeling.prompt.md` | Action + clarification | Cost Model with scale projections |
| **03** | `step-03-threat-modeling.prompt.md` | Action + clarification | Initial Threat Model |
| **04** | `step-04-stack-evaluation.prompt.md` | Action + clarification | Scored stack comparison |
| **05** | `step-05-architecture-decision-record.prompt.md` | Action | ADR documenting the committed stack decision |
| **06** | `step-06-benchmark-definition.prompt.md` | Action + clarification | Benchmark framework (versioned) |
| **07** | `step-07-phase-2-readiness-review.prompt.md` | Evaluation (gate) | Phase 2 → Phase 3 readiness determination |

**Execution order is load-bearing.** Later prompts consume earlier
outputs as context:

- Step 04 (Stack Evaluation) requires the principle weighting from Step 01
  and the cost and threat inputs from Steps 02 and 03
- Step 05 (ADR) commits the result of Step 04
- Step 06 (Benchmarks) must be calibrated against the committed stack
  from Step 05
- Step 07 (Readiness Review) consumes all six prior artifacts

The order is not arbitrary. Running Step 04 before Step 01 means scoring
without knowing what weights matter. Running Step 06 before Step 05
means calibrating benchmarks against a stack that hasn't been committed.
The prompts enforce this through required inputs — each prompt's
clarification step verifies that required prior artifacts are present
before proceeding.

---

## Behavioral Guidelines

### The Clarification Step

Phase 2 prompts are action-first, not interview-first. The practitioner
pastes context — the Information Report, prior Phase 2 artifacts, any
project-specific inputs — and the AI reads them.

The AI then asks a small number of clarifying questions. **Single digits,
never more.** Clarification is for genuine ambiguity in the pasted
context, missing critical inputs, or decisions the practitioner must
make that cannot be inferred from evidence. If the context is clear and
complete, proceed directly to the output.

Clarification is not a substitute for thorough context. If major inputs
are missing, say so explicitly and request the specific artifact —
do not try to generate output from incomplete evidence.

### Evidence and Confidence Discipline

Every significant claim in a Phase 2 artifact must be traceable to:

- A specific section of the Information Report, or
- A prior Phase 2 artifact, or
- Domain reasoning the practitioner has explicitly confirmed during
  clarification, or
- A clearly labeled assumption with documented rationale

Unsupported claims are not acceptable. If the AI cannot find evidence
for a conclusion, flag it as a research gap and either request the
missing input or produce the artifact with that section marked
explicitly as needing practitioner input before handoff.

Confidence levels (High / Medium / Low) from the Information Report
inherit forward. A Medium-confidence finding in Phase 1 does not become
a High-confidence foundation in Phase 2 through repetition. If synthesis
produces new corroboration, document the basis for the upgrade.

### The Commitment Posture

Phase 2 outputs are written as commitments, not proposals. The business
case articulates what the system will do and for whom. The cost model
commits the team to a set of economic assumptions that will be tracked.
The stack decision commits the team to a technology foundation. The
benchmarks commit the team to measurable targets.

This posture does not mean rigidity. Commitments are revisable when
circumstances change — but revision is a visible, documented decision,
not a silent drift. The prompts produce artifacts that make revision
traceable.

### Trade-Off Documentation

No stack scores highest on every principle. No cost model makes every
stakeholder happy. No threat model is exhaustive. The AI must document
trade-offs explicitly — what is being accepted, what is being declined,
what mitigation is planned for the weaker dimensions, and what would
trigger revisiting the decision.

A trade-off that is not documented is a trade-off that AI in later
phases cannot reason about. In an AI-centric workflow, undocumented
decisions are decisions the system will lose access to.

### No Phase 3 or Phase 4 Work

Phase 2 produces **analytical foundations**, not design or architecture.
The prompts are scoped to prevent encroachment into later phases:

- Threat modeling produces the initial threat model — not the security
  architecture
- Stack evaluation produces the committed foundation — not module
  boundaries or API design
- Benchmark definition produces measurable targets — not the instrumentation
  strategy
- The ADR documents the stack commitment — not the system structure

When a Phase 2 prompt is at risk of producing Phase 3 or Phase 4 output,
stop and flag it. The artifact is sized correctly when it gives Phase 3
enough to start design without pre-empting design decisions.

---

## Consistency Across Artifacts

Phase 3 consumes all six analytical artifacts plus the ADR as a
coherent package. The artifacts must be internally consistent.

The Readiness Review (Step 07) is the dedicated consistency check, but
each individual prompt is also responsible for referring back to prior
artifacts and flagging inconsistencies it detects. Specifically:

- The **cost model** must reflect the stack options being evaluated,
  not a different universe of candidates
- The **threat model** must cover the data flows implied by the
  business case
- The **stack evaluation** must use the weighting set in the business
  analysis
- The **ADR** must document the stack that won the scored evaluation —
  not a different choice
- The **benchmarks** must be realistic for the committed stack
  and must align with the ambitions of the business case

When a prompt detects a cross-artifact inconsistency, surface it
immediately. Do not silently paper over it in the current artifact.

---

## Output Standards

All Phase 2 artifacts must meet these standards before Phase 3 handoff:

- [ ] Every significant claim is traceable to the Information Report,
  a prior Phase 2 artifact, confirmed domain reasoning, or a labeled
  assumption
- [ ] Confidence levels are attached to claims where ambiguity exists
- [ ] Trade-offs are documented explicitly — what is accepted, what is
  declined, what mitigation exists, what would trigger revision
- [ ] The principle weighting is applied consistently across all
  scoring and evaluation
- [ ] Cross-artifact references are explicit and accurate
- [ ] Structural formatting is AI-parseable (tables for comparative
  data, labeled sections, metadata including dates and versions)
- [ ] No artifact exceeds its Phase 2 scope by producing Phase 3
  design or Phase 4 architecture content
- [ ] The artifact is versioned — any later revision is a documented
  change, not a silent replacement

---

## Common Pitfalls

**Analysis paralysis.**
AI makes it easy to run one more comparison, model one more scenario,
evaluate one more alternative. The goal is an informed decision, not
a perfect one. Set time boundaries and commit when they are reached.
The decision record captures the unknowns remaining — it does not
require omniscience.

**Optimizing for one principle.**
A stack selected purely on performance, or purely on cost, or purely
on familiarity, will fail on the dimensions that were ignored. The
Core Principles force multi-dimensional evaluation. If a candidate
scores high on one principle and low on another, the trade-off must
be explicit and accepted — not ignored.

**Cost models without scale assumptions.**
A cost model that captures only the MVP is a launch budget, not a
cost model. Every cost artifact must include projections at multiple
scale points with named growth assumptions.

**Threat models deferred to "later."**
Architecture decisions in Phase 3 and Phase 4 made without a threat
model are made without the constraints they must satisfy. A threat
model produced after architecture is a compliance exercise. A threat
model produced before architecture is a design input.

**Adjusting principle weights after scoring.**
Setting the weighting after seeing which stack wins is retrofitting.
It undermines the entire scoring framework. The weighting is set
before scoring. If it turns out to be wrong, update it as a visible,
documented decision and re-score.

**Undocumented trade-offs.**
A trade-off not captured in the artifact is a trade-off AI in later
phases cannot reason about. In an AI-centric workflow, this degrades
every subsequent prompt's ability to maintain coherence with the
original decision.

**Over-scoping into Phase 3 or Phase 4.**
Phase 2 produces analytical foundations. When a prompt starts
producing module boundaries, API designs, or detailed architecture,
stop. That is the work of later phases operating with the inputs
this phase produces.

---

## Connecting to Phase 3

Phase 2 hands off a package, not a single document. Phase 3 (Design &
Technical Analysis) consumes:

| Phase 2 Artifact | Phase 3 Use |
|------------------|-------------|
| Business Case (Step 01) | Grounds design choices in user workflows and value proposition |
| Principle Weighting (Step 01) | Drives the Phase 3 Principle Scorecard baseline |
| Cost Model (Step 02) | Constrains design options that would violate economic assumptions |
| Initial Threat Model (Step 03) | Becomes the security constraint set for design |
| Stack Evaluation (Step 04) | Context for understanding why the committed stack was chosen |
| ADR (Step 05) | The committed foundation — design operates within it, not around it |
| Benchmark Framework (Step 06) | Target set used in Phase 3 simulations and scoring |
| Readiness Review (Step 07) | Gate authorization — Phase 3 does not begin without it passing |

The **Readiness Review** (Step 07) is the formal gate. Its output is a
principle-scored determination: READY / CONDITIONALLY READY / NOT READY.
A FAIL on any principle blocks Phase 3 on that dimension. A CONDITIONAL
allows Phase 3 to proceed with a documented remediation plan and named
owner.

Phase 3 does not re-litigate Phase 2 decisions. It takes them as given
and produces the design direction that Phase 4 will architect. A shaky
Phase 2 produces shaky Phase 3 — which compounds through the rest of
the framework. The gate exists to prevent that compounding.

---

*Part of the AI-Centric Software Development Playbook —
Phase 2: Analysis & Stack Selection*
*Framework reference: article-04-analysis-stack-selection.md*
*See also: README.md in this directory for the full tool set
documentation (produced after all seven prompts are built)*