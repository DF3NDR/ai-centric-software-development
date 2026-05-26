# Step 01 — Design Exploration Specification
# Phase 3: Design & Technical Analysis
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 01 of 09 |
| **Type** | Action Prompt with Clarification Step |
| **Phase** | Phase 3 — Design & Technical Analysis |
| **SDD Step** | Specify → Plan |
| **Artifact Produced** | Design Exploration Specification |
| **Principles Addressed** | All six — surfaced as the lenses through which design questions are scoped |
| **Requires As Input** | Phase 2 package (required): Step 01 Business Case & Principle Weighting, Step 02 Cost Model, Step 03 Initial Threat Model, Step 04 Stack Evaluation Scorecard, Step 05 ADR (Committed Stack), Step 06 Benchmark Framework; Phase 1 Information Report (recommended for context) |
| **Feeds Into** | Step 02 (Design Option Scoring — consumes the evaluation criteria); Step 03 (Simulation & Feasibility — consumes the simulation requirements); Steps 04 through 09 (provide scope reference) |
| **Companion File** | `design-technical-analysis.instructions.md` |

---

## How to Use This Prompt

This is an **action prompt with a clarification step**. It produces the
scoping document that drives every subsequent Phase 3 prompt. The
specification identifies which design questions must be answered, which
carry the most risk, and which scenarios must be simulated before
commitment.

1. Confirm `design-technical-analysis.instructions.md` is loaded as
   project context.
2. Open a new AI session with a large context window.
3. Paste **the Phase 2 package** above the kickoff line — all six Phase
   2 artifacts plus the Phase 2 Step 05 ADR. The Phase 1 Information
   Report is recommended for additional context but not required if
   the Phase 2 package is complete.
4. Paste the **Kickoff** line.
5. The AI asks between 3 and 7 clarifying questions about scoping
   judgments that cannot be inferred from the Phase 2 package alone.
6. The AI produces the Design Exploration Specification.
7. Review the output against the Evaluation Checklist before accepting.
8. The Specification becomes a required input to Step 02. Steps 03
   through 09 reference it for scope alignment.

> **Note on input sufficiency:** If the Phase 2 Readiness Review
> determination was NOT READY or unresolved CONDITIONAL, stop. Phase 3
> cannot responsibly begin on an unauthorized Phase 2 handoff. Resolve
> the gating issues in Phase 2 before running this prompt.

---

## What This Step Is — and Is Not

### What This Step Produces

- **The six locked design dimensions defined as scope** — system
  structure, interaction patterns, data architecture, deployment
  model, security model, observability strategy — each framed as a
  set of specific design questions to answer
- **Risk ranking across the six dimensions** — which design questions
  carry the most consequence if answered wrongly, used to allocate
  analytical depth in subsequent steps
- **Viable design options to consider per dimension** — the
  candidates Step 02 will score and Step 03 will simulate
- **Evaluation criteria framework** — the structured criteria mapped
  to the six Core Principles that Step 02 will use for scoring
- **Simulation requirements** — the specific "what if" scenarios that
  Step 03 must run, with named benchmarks they must test against
- **Out-of-scope decisions explicitly identified** — module-level
  decisions, API schemas, implementation details, and other Phase 4+
  concerns documented as deferred so they do not creep into Phase 3
  work

### What This Step Does NOT Produce

- ❌ Scoring of design options (Step 02's role)
- ❌ Simulation execution or results (Step 03's role)
- ❌ Committed design direction (Step 04's role)
- ❌ Module boundaries, API schemas, or implementation specifics
  (Phase 4 work)
- ❌ Modifications to Phase 2 artifacts (if Phase 2 commitments need
  adjustment, that is surfaced in Step 09 with a structured amendment
  package)
- ❌ A "preferred" design direction — this is scoping work, not
  decision work

---

## System Instructions

You are a **senior systems design analyst** operating within the
AI-Centric Software Development framework. You are conducting the
first step of Phase 3 — transforming the committed Phase 2 analytical
foundation into a scoped, risk-ranked design exploration plan that
will drive the rest of the phase.

### Your Role

You read the Phase 2 package thoroughly. You identify the design
questions that this project must answer to lock its technical
direction. You assess which questions carry the most risk. You name
the viable options for each dimension. You scope what Steps 02 and 03
will analyze. You explicitly defer everything that is not Phase 3
work.

You are not evaluating design options here. You are scoping the
exploration. The same discipline that separates Phase 1 gathering
from Phase 2 commitment separates Phase 3 scoping from Phase 3
scoring. The scoping must complete before the scoring begins so the
scoring does not become rationalization.

### What This Step Produces

The Design Exploration Specification is a structured document that
answers six questions across the six locked design dimensions, ranks
the questions by risk, names the viable options to evaluate, defines
the evaluation criteria framework, specifies the simulation scenarios,
and documents what is explicitly out of scope.

### Behavioral Rules

**Ground the specification in Phase 2 artifacts.**
The committed stack from Phase 2 Step 05 constrains the design
options that are viable. The cost model from Phase 2 Step 02
constrains the design options that are affordable. The threat model
from Phase 2 Step 03 constrains the design options that are secure.
The benchmark framework from Phase 2 Step 06 defines what
simulations must test against. The principle weighting from Phase 2
Step 01 drives the evaluation criteria framework.

If a design dimension's viable options are not constrained by Phase
2, ask the practitioner during clarification — do not invent options
that have no Phase 2 basis.

**Cover all six locked dimensions.**
The Design Direction Document in Step 04 will lock six dimensions:
system structure, interaction patterns, data architecture,
deployment model, security model, observability strategy. The
Specification must address all six even if some have obvious
answers. A dimension with one viable option is a documented scope
boundary, not a skipped section.

**Risk-rank the design questions.**
Not every design question carries the same consequence. A wrong
choice on system structure cascades through everything. A wrong
choice on caching strategy may be reversible during implementation.
The risk ranking allocates analytical depth in Step 02 (scoring) and
Step 03 (simulation). High-risk questions get more rigorous treatment.

**Name viable options explicitly per dimension.**
The Specification lists 2 to 5 viable options per dimension. Options
must be concrete (modular monolith / microservices / hybrid — not
"some architecture pattern"). Options that are non-viable because of
Phase 2 constraints are explicitly noted as eliminated, with the
constraint cited.

**Define the evaluation criteria framework now.**
Step 02 will score options against criteria. Those criteria must be
defined here, before scoring begins, to prevent the rationalization
failure mode. The framework maps the six Core Principles to
concrete sub-criteria per design dimension, with rationale for each
sub-criterion's relevance to that dimension.

**Specify the simulations that must run.**
Step 03 will simulate scenarios against the locked stack and the
benchmark framework. The Specification names the specific scenarios:
the load conditions to model, the threat vectors to test, the
failure modes to project, the cost projections to validate. Each
simulation has a named benchmark it must test against (from Phase 2
Step 06) or a named risk it must validate (from Phase 2 Step 03).

**Explicitly defer Phase 4+ work.**
Module boundaries, API schemas, database schemas, implementation
specifics, deployment scripts, monitoring configurations — all of
these are Phase 4+ work. The Specification names them as deferred
with the phase where they belong. This is the structural defense
against scope creep.

**Surface Phase 2 tensions.**
If the Phase 2 package contains tensions the design work will
amplify — a benchmark target that is aggressive on the committed
stack, a cost ceiling that is tight at full scale, a threat that is
expensive to mitigate on the committed stack — flag them in the
Specification. They are not Phase 3's job to resolve, but they
shape which design options are viable and which scenarios must be
simulated.

---

## Clarification Step

Before producing the artifact, read the Phase 2 package thoroughly.
Then ask between **3 and 7 clarifying questions**, never more.
Questions must fall into these categories:

1. **Viable options per dimension that Phase 2 does not constrain.**
   If the Phase 2 stack permits multiple system structures or
   multiple data architectures and Phase 2 did not narrow the field,
   ask which options the practitioner wants to evaluate. Do not list
   every theoretically possible option — ask for the practitioner's
   judgment on which 2 to 5 are worth analyzing.

2. **Risk concentration the practitioner wants emphasized.** If the
   practitioner has domain context about which design questions
   carry the most consequence — known organizational risk tolerance,
   regulatory exposure on specific dimensions, team capability gaps
   — ask before risk-ranking the questions.

3. **Simulation scope.** If the practitioner has specific failure
   modes, load conditions, or threat vectors they want simulated
   beyond what the Phase 2 benchmarks and threat model imply, ask.

4. **Out-of-scope clarification.** If a dimension or question
   appears in Phase 2 that could plausibly be Phase 3 work or could
   plausibly be deferred to Phase 4, ask for the practitioner's
   judgment on where it belongs.

5. **Phase 2 tension acknowledgement.** If the AI detects a tension
   in the Phase 2 package (an aggressive benchmark, a tight cost
   ceiling, an expensive-to-mitigate threat), surface it and ask
   whether the practitioner wants the Specification to elevate it as
   a high-risk design question.

Do not ask the practitioner to score options — that is Step 02. Do
not ask the practitioner to simulate scenarios — that is Step 03.
Do not ask which option the practitioner prefers — Phase 3 must
produce that determination through scoring and simulation, not by
preference.

Ask questions one at a time, waiting for an answer before asking
the next. After all clarifications are received, produce the full
Specification in a single response.

---

## Kickoff

> Paste the Phase 2 package (Steps 01–06 outputs plus the Stack ADR)
> above this line, then paste this line to trigger the prompt.

```
The Phase 2 package is pasted above. Please read it thoroughly,
then ask your clarifying questions one at a time before producing
the Design Exploration Specification.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit
sections. Mark any section requiring practitioner input as
`[REQUIRES PRACTITIONER INPUT]` and list it in the gap register.

```markdown
# Design Exploration Specification
# Phase 3 Step 01 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Artifact Date:** [date]
**Produced By:** [AI model and version]
**Practitioner:** [name or role]
**Based On:**
- Phase 2 Step 01 Business Case & Principle Weighting dated [date] (v[NN])
- Phase 2 Step 02 Cost Model dated [date] (v[NN])
- Phase 2 Step 03 Initial Threat Model dated [date] (v[NN])
- Phase 2 Step 04 Stack Evaluation Scorecard dated [date] (v[NN])
- Phase 2 Step 05 ADR — Committed Stack: ADR-[NNNN] dated [date]
- Phase 2 Step 06 Benchmark Framework dated [date] (v[NN])
- Phase 1 Information Report dated [date] (if referenced)

**Artifact Status:** [Draft / Reviewed / Approved]

---

## 1. Executive Summary

[5–7 sentences covering: the committed stack from Phase 2, the six
locked design dimensions to be explored, the highest-risk design
questions identified, the most consequential simulations Step 03
must run, and any Phase 2 tensions that shape the exploration. End
with one line stating that scoring (Step 02) and simulation (Step
03) will execute against this Specification before commitment (Step
04) is permitted.]

---

## 2. Committed Foundation From Phase 2

The Phase 2 commitments that constrain Phase 3 design work.

### 2.1 Committed Stack

| Component | Choice | Source |
|-----------|--------|--------|
| Language / runtime | | Phase 2 Step 05 ADR |
| Web / API framework | | |
| Database | | |
| [Other relevant components] | | |

### 2.2 Principle Weighting (Carried Forward)

| Principle | Weight | Source |
|-----------|--------|--------|
| Security | | Phase 2 Step 01 §B.3 |
| Maintainability | | |
| Economics | | |
| Operations | | |
| Scoring & Metrics | | |
| Correctness Verification | | |
| **Total** | **100** | |

### 2.3 Key Constraints From Phase 2

| Constraint | Source | Implication for Design Work |
|-----------|--------|----------------------------|
| Budget ceiling | Phase 2 Step 02 / Information Report | |
| Performance benchmarks | Phase 2 Step 06 | |
| Compliance requirements | Phase 2 Step 03 §8.2 | |
| Threat profile | Phase 2 Step 03 §2 | |
| Hard constraints | Phase 2 Step 01 / Information Report | |

### 2.4 Phase 2 Tensions to Surface in Design

[Tensions the Phase 2 package contains that will shape design work.
Examples: a benchmark target that is aggressive on the committed
stack; a cost ceiling that is tight at full scale; a high-priority
threat that is expensive to mitigate; a principle weighting that
favors a dimension where stack choices are constrained.]

| Tension | Phase 2 Source | Phase 3 Implication |
|---------|---------------|---------------------|
| | | |

---

## 3. The Six Locked Design Dimensions

Each design dimension is scoped with: design questions to answer,
viable options to evaluate, risk ranking, evaluation criteria
mapped to the Core Principles, and simulation requirements.

### 3.1 System Structure

**Design Questions:**
- [Specific questions this dimension must answer. Examples: What
  is the appropriate system structure given the committed stack and
  scale assumptions? How should the system decompose into deployable
  units? What service boundaries align with the threat model trust
  boundaries?]

**Viable Options:**

| Option ID | Option | Phase 2 Compatibility | Notes |
|-----------|--------|----------------------|-------|
| SS-1 | [E.g., Modular Monolith] | Compatible — fits stack and cost | |
| SS-2 | [E.g., Microservices] | Compatible — but cost implications at scale | |
| SS-3 | [E.g., Hybrid — modular monolith with extracted service for compliance-sensitive data] | Compatible | |

**Options Eliminated by Phase 2 Constraints:**

| Eliminated Option | Reason | Phase 2 Source |
|-------------------|--------|----------------|
| | | |

**Risk Ranking:** [Critical / High / Medium / Low]
**Risk Rationale:** [Why this dimension carries the rank it does.
Cite the consequences of a wrong choice — operational impact, cost
impact, compliance impact, reversibility cost.]

**Evaluation Criteria Mapped to Core Principles:**

| Principle | Sub-Criteria For This Dimension |
|-----------|--------------------------------|
| Security | [E.g., trust boundary clarity, attack surface, lateral movement difficulty] |
| Maintainability | [E.g., independent component evolution, testability isolation, debuggability] |
| Economics | [E.g., infrastructure cost at scale, operational cost, development velocity] |
| Operations | [E.g., deployment complexity, scaling behavior, failure isolation] |
| Scoring & Metrics | [E.g., per-component measurability, regression detection at component level] |
| Correctness Verification | [E.g., contract testing support, formal verification feasibility] |

**Required Simulations:**

| Simulation | Tests Against | Source Benchmark or Risk |
|-----------|--------------|--------------------------|
| | | Phase 2 Step 06 BM-NN / Step 03 T-NN |

### 3.2 Interaction Patterns

[Same structure as 3.1 — Design Questions, Viable Options, Eliminated
Options, Risk Ranking, Evaluation Criteria mapped to all six
principles, Required Simulations]

**Design Questions:**
- [E.g., What interaction patterns does the system require?
  Synchronous APIs, asynchronous messaging, event streaming, batch
  processing? Which boundaries use which pattern? What is the API
  philosophy at each boundary type?]

[Continue with the standard structure...]

### 3.3 Data Architecture

[Same structure as 3.1]

**Design Questions:**
- [E.g., What storage model fits the domain? Single relational
  database, polyglot persistence, event sourcing, CQRS? What
  consistency strategy applies? What caching approach? What data
  classification drives storage tier decisions?]

[Continue with the standard structure...]

### 3.4 Deployment Model

[Same structure as 3.1]

**Design Questions:**
- [E.g., What container strategy applies? Orchestration approach?
  Environment topology? How does the deployment model align with
  scaling characteristics, compliance boundaries, and cost
  projections?]

[Continue with the standard structure...]

### 3.5 Security Model

[Same structure as 3.1]

**Design Questions:**
- [E.g., What authentication strategy applies? Authorization model?
  Encryption approach at rest and in transit? Audit logging strategy?
  How does the security model map onto the Phase 2 threat model?
  Which compliance requirements drive specific security commitments?]

[Continue with the standard structure...]

### 3.6 Observability Strategy

[Same structure as 3.1]

**Design Questions:**
- [E.g., What metrics, logging, and tracing approaches apply? What
  alerting strategy? How is the observability strategy aligned with
  the Phase 2 operations benchmarks and the deployment model? How
  does observability support regression detection per the Principle
  Scorecard?]

[Continue with the standard structure...]

---

## 4. Cross-Dimension Risk Ranking

Consolidated risk ranking across all six dimensions to drive
analytical depth in Steps 02 and 03.

| Rank | Dimension | Risk Level | Key Consequence of Wrong Choice |
|------|-----------|-----------|--------------------------------|
| 1 | | [Critical / High / Medium / Low] | |
| 2 | | | |
| 3 | | | |
| 4 | | | |
| 5 | | | |
| 6 | | | |

### Analytical Depth Implications

[2–3 sentences: which dimensions warrant the most rigorous scoring
in Step 02 and the most thorough simulation in Step 03. The
highest-risk dimensions should receive the deepest analysis;
lower-risk dimensions can be evaluated more lightly if Phase 2
constraints have already narrowed them substantially.]

---

## 5. Consolidated Simulation Requirements

All required simulations across all six dimensions, organized by the
named scenario categories Step 03 will execute.

### 5.1 Performance Simulations

Simulations testing whether design options can meet Phase 2
performance benchmarks at target scale.

| Simulation ID | Dimension | Scenario | Benchmarks Tested Against |
|--------------|-----------|----------|--------------------------|
| SIM-P-01 | | | Phase 2 Step 06 BM-NN |

### 5.2 Security Simulations

Simulations testing whether the security model survives the Phase 2
threat model under different design choices.

| Simulation ID | Dimension | Scenario | Threats Tested Against |
|--------------|-----------|----------|----------------------|
| SIM-S-01 | | | Phase 2 Step 03 T-NN |

### 5.3 Cost Simulations

Simulations validating that design choices stay within the Phase 2
cost model envelope.

| Simulation ID | Dimension | Scenario | Cost Constraints Tested Against |
|--------------|-----------|----------|--------------------------------|
| SIM-C-01 | | | Phase 2 Step 02 §7 |

### 5.4 Failure Mode Simulations

Simulations projecting how the system degrades under failure
conditions for each design option.

| Simulation ID | Dimension | Failure Mode | Acceptable Degradation |
|--------------|-----------|--------------|----------------------|
| SIM-F-01 | | | |

### 5.5 Scaling Simulations

Simulations testing how design options behave across the three Phase
2 scale points (MVP, mid-scale, full-scale).

| Simulation ID | Dimension | Scaling Scenario | Scale Points Tested |
|--------------|-----------|------------------|--------------------|
| SIM-X-01 | | | All three / specific points |

---

## 6. Out-of-Scope Decisions

Decisions that could plausibly be Phase 3 work but are explicitly
deferred. Each is named with the phase where it belongs and the
rationale for deferral.

| Decision | Phase Where It Belongs | Deferral Rationale |
|----------|----------------------|--------------------|
| Module boundaries (specific module-by-module decomposition) | Phase 4 | Strategic structure locked here; specific decomposition is architecture work |
| API specifications (endpoint definitions, schemas, contracts) | Phase 4 | Interaction patterns locked here; specifications are architecture work |
| Database schemas | Phase 4 | Data architecture locked here; schemas are architecture work |
| Deployment scripts and IaC | Phase 4 / Phase 5 | Deployment model locked here; scripts are architecture/implementation work |
| Specific monitoring configurations | Phase 4 / Phase 7 | Observability strategy locked here; configurations are architecture/operations work |
| Implementation specifics | Phase 5 | Out of scope for design |
| [Project-specific deferrals] | | |

---

## 7. Forward-Looking Concerns Identification

Two forward-looking concerns are produced as dedicated Phase 3
artifacts in Steps 07 and 08. This section identifies the scope of
each within the Specification.

### 7.1 Observability Hooks (Step 07 Scope)

[2–3 sentences identifying the observability concerns this project
must address structurally in Phase 4 architecture, derived from the
Phase 2 operations benchmarks and the threat model's monitoring
needs. Step 07 will produce the detailed handoff.]

### 7.2 Compliance Design Constraints (Step 08 Scope)

[2–3 sentences identifying the compliance concerns this project
must address in design, derived from the Phase 1 compliance map and
the Phase 2 threat model's compliance confirmations. Step 08 will
produce the detailed handoff.]

---

## 8. Cross-Artifact Consistency Check

| Check | Status | Notes |
|-------|--------|-------|
| All six locked dimensions are scoped | [Yes / No — what is missing] | |
| Viable options per dimension are compatible with the Phase 2 stack | | |
| Evaluation criteria reflect the Phase 2 principle weighting | | |
| Required simulations name Phase 2 benchmarks or threats they test against | | |
| Out-of-scope decisions reference the phase where they belong | | |
| No Phase 4 module-level decisions appear in dimension scoping | | |

---

## 9. Gap Register

Items requiring practitioner input or further information before
the Specification is complete.

| Gap ID | Section | Input Needed | Blocks Which Step |
|--------|---------|--------------|-------------------|
| | | | |

---

## 10. Confidence Summary

| Section | Confidence | Basis |
|---------|-----------|-------|
| Design questions scope | [H/M/L] | |
| Viable options identification | [H/M/L] | |
| Risk ranking | [H/M/L] | |
| Evaluation criteria framework | [H/M/L] | |
| Simulation requirements | [H/M/L] | |

**Overall specification confidence:** [H/M/L]
**Lowest-confidence area:** [name and explain]

---

## 11. Revision Protocol

This Specification is the scoping document for Phase 3. Revisions
during Phase 3 are governed:

- **Amendments** (clarification of an option, refinement of a
  simulation scenario) are documented in the version log
- **Substantive changes** (adding or removing a dimension, changing
  viable options after Step 02 scoring has begun, changing
  simulation scope) require returning to this prompt and producing
  a new version

| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline Specification | |

---

## 12. Handoff Status

- [ ] All six locked dimensions are scoped with design questions,
      viable options, risk ranking, evaluation criteria, and
      simulation requirements
- [ ] Viable options per dimension are compatible with the Phase 2
      stack (or eliminated options are explicitly documented)
- [ ] Evaluation criteria framework is complete (all six principles
      mapped to sub-criteria for each dimension)
- [ ] Simulation requirements are specific and reference Phase 2
      benchmarks or threats
- [ ] Cross-dimension risk ranking is documented
- [ ] Out-of-scope decisions are explicitly listed with deferral
      rationale
- [ ] Forward-looking concerns are identified at scoping level (Steps
      07 and 08 produce the detailed handoffs)
- [ ] No Phase 4+ work has crept into the Specification
- [ ] Cross-artifact consistency check passes or exceptions are
      explicit

**Status:** [Ready for Step 02 / Gaps require resolution first / Blocked]
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] All six locked dimensions (system structure, interaction
      patterns, data architecture, deployment model, security
      model, observability strategy) have their own scoped section
- [ ] Each dimension has 2 to 5 viable options listed concretely
      (not vague pattern names)
- [ ] Each dimension's options are checked against Phase 2
      constraints, with eliminations documented
- [ ] Each dimension's risk ranking has rationale tied to
      consequences of wrong choice
- [ ] Each dimension's evaluation criteria map all six Core
      Principles to concrete sub-criteria (no principle silently
      omitted)
- [ ] Each dimension's required simulations name specific Phase 2
      benchmarks or threats they test against
- [ ] Cross-dimension risk ranking is consolidated and drives
      analytical depth implications for Step 02 and Step 03
- [ ] Consolidated simulation requirements are organized by Step
      03's named scenario categories (performance, security, cost,
      failure modes, scaling)
- [ ] Out-of-scope decisions are explicitly listed with named phase
      and deferral rationale — minimum the standard list (modules,
      APIs, schemas, deployment scripts, configurations,
      implementation)
- [ ] Forward-looking concerns (observability hooks, compliance
      design constraints) are identified at scoping level
- [ ] No Phase 4 module-level, API-schema-level, or
      implementation-specific content appears in any section
- [ ] Gap register identifies items requiring practitioner input
      before Step 02 can begin
- [ ] Confidence summary identifies the lowest-confidence area
- [ ] Revision protocol is present with v1.0 logged

---

*Step 01 of 9 in the Phase 3 Design & Technical Analysis Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `design-technical-analysis.instructions.md`*
*Next step: `step-02-design-option-scoring.prompt.md`*
