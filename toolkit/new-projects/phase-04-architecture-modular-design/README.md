# Phase 4: Architecture & Modular Design — Tool Set
## AI-Centric Software Development Playbook

---

## Overview

This directory contains the complete tool set for **Phase 4: Architecture
& Modular Design** of the AI-Centric Software Development Playbook. Phase 4
takes the locked technical direction from Phase 3 — the six committed
design dimensions, the Principle Scorecard baseline, the forward-looking
handoffs — and transforms it into a concrete, implementation-ready
architectural blueprint that Phase 5 will build from.

This is where the system becomes real on paper before it becomes real in
code. Module boundaries are drawn. API contracts are specified. Security
boundaries are defined at the component level. Data schemas take shape.
The documentation strategy is established. Governance is formalized.

Architecture carries a defining responsibility in the AI-centric workflow:
**the architecture must be specified precisely enough that AI can build
from it.** A module described as "handles user stuff" produces worse
AI-generated code than one specified with explicit responsibilities,
interfaces, data models, error handling contracts, and security
constraints. The quality of the architecture directly determines the
quality of AI-assisted implementation. The test for every specification
is: *can an AI implementation tool set produce a working module from this
specification alone?*

The primary outputs of this phase are the **module specifications** (the
detailed, per-module blueprints Phase 5 consumes as primary input), the
**formal API contracts** (machine-readable contracts that drive code
generation and contract testing), the **cross-cutting frameworks**
(security, data, documentation, governance, shared patterns), the
**Principle Scorecard v2.0** (the cross-phase living document updated to
reflect the architecture), and the **Phase 5 handoff package** (produced
by the readiness review gate).

---

## Framework Context

This tool set is part of the [AI-Centric Software Development
Playbook](../../../README.md), a practitioner's framework for small teams
(1–5 people) that use AI tools to deliver what large organizations once
required.

### Phase 4 Differs From Phases 1, 2, and 3 in Character

| Dimension | Phase 1 | Phase 2 | Phase 3 | Phase 4 |
|-----------|---------|---------|---------|---------|
| Primary work | Gathering | Committing | Locking direction | **Specifying the blueprint** |
| AI role | Research strategist | Analytical partner | Design analyst | **Architecture specifier** |
| Number of prompts | 6 | 7 | 9 | **16** |
| SDD structure | One cycle | One cycle | One cycle | **Nested cycles (phase-level wrapping module-level)** |
| Execution pattern | Order-flexible | Strictly sequential | Dependency-driven | **Three-stage with dependency-driven sub-structure** |
| Artifact count | Fixed (1) | Fixed (7) | Fixed (9) | **Variable (depends on module count and protocols)** |
| Cross-phase living artifacts | None | Stack ADR | Principle Scorecard | **Scorecard v2.0 + module specs** |
| Backward effects | None | None | Phase 2 amendment cycle | **Phase 3 AND Phase 2 amendment cycles** |
| Gate outcomes | 3 | 3 | 4 | **5** |

Phase 4 is the most structurally complex phase in the framework. Three
characteristics drive that complexity.

**The architecture must be specified precisely enough that AI can build
from it.** This is Phase 4's defining responsibility and the bar every
artifact must meet. The evaluation checklists for module specifications
and API contracts are unusually rigorous because the bar is unusually
high.

**The artifact count is variable, not fixed.** Phase 4 produces N module
specifications where N depends on the project, plus a variable number of
API contracts depending on which protocols the project uses. The toolkit
handles this through a parameterized prompt (the module specification
prompt runs once per module) and four conditional prompts (only the API
contract prompts for protocols the project actually uses).

**Phase 4 work can invalidate both Phase 3 and Phase 2 commitments.** A
module specification effort can reveal the system structure ADR was wrong
(Phase 3 amendment); detailed cost modeling can reveal the cost envelope
is wrong (Phase 2 amendment). The readiness review supports both amendment
paths with distinct, structured packages.

### The Six Core Principles in Phase 4

In Phase 3 the principles became a living scorecard. In Phase 4 they
produce their most tangible architectural benefits — the architecture
itself should make the principles *easier* to satisfy in implementation.

| Principle | Phase 4 Application |
|-----------|---------------------|
| **Security** | Zero-trust enforcement, least privilege, encryption, audit logging at the component level. Every module spec has a security section; security constraints belong *in* the module specs, not only in the standalone framework. |
| **Maintainability** | Module boundaries that support independent testing and deployment; a documentation strategy serving humans and AI; designing for extensibility. |
| **Economics** | Validating the architecture fits the cost model; estimating implementation effort per module and operational overhead. |
| **Operations** | Monitoring hooks, logging standards, health checks, deployment and scaling parameters per module — the Phase 3 observability strategy made concrete. |
| **Scoring & Metrics** | The scorecard is updated to v2.0 with architectural scores; regressions against the Phase 3 baseline are detected per the Step 06 protocol. |
| **Correctness Verification** | Designing for verifiability — API contracts enable conformance testing, module boundaries enable independent verification, data integrity constraints enable automated checking. |

### The Nested SDD Cycle

Phase 4 runs the SDD cycle nested: a phase-level cycle organizes the
overall architectural work, and module-level cycles produce individual
module specifications.

```
Specify → Plan → Detail → Task → Implement   (phase-level)
                              │
                              └── Specify → Plan → Detail → Task → Implement   (per module)
```

| Phase-Level SDD Step | What Happens | Output |
|----------------------|--------------|--------|
| **Specify** | Define the architectural scope | Step 01 Architecture Exploration Specification |
| **Plan** | Organize work into the three stages | Implicit in the specification |
| **Detail** | Produce the frameworks and per-module specs | Stage 1 and Stage 2 artifacts |
| **Task** | Identify contracts, schemas, policies | Distributed across prompts |
| **Implement** | Produce all artifacts; review; update scorecard; run the gate | 16 Phase 4 artifacts (variable count) |

This nested structure — phase-level cycles containing module-level cycles
— is what makes Phase 4 manageable despite its complexity. Each module is
specified independently, with the Stage 1 cross-cutting frameworks
providing consistency.

### The Three-Stage Structure

Phase 4 executes in three stages, reflecting the bidirectional dependency
between cross-cutting concerns and module specifications: cross-cutting
frameworks constrain module specifications, but some cross-cutting
artifacts (API contracts, the updated scorecard) depend on module
specifications.

- **Stage 1 — Pre-Module Foundational** (Steps 01–06): the cross-cutting
  frameworks that constrain module specifications. Sub-stage 1a (Steps
  01–02) is sequential; sub-stage 1b (Steps 03–06) is parallel-eligible.
- **Stage 2 — Modules** (Steps 07–09): enumeration (manifest + strategic
  interface contracts), per-module specification (run once per module),
  and cross-module consistency.
- **Stage 3 — Post-Module Integration** (Steps 10–16): the conditional API
  contract prompts, the scorecard update, the architecture review, and the
  gate.

---

## Directory Contents

```
phase-04-architecture-modular-design/
├── README.md                                              ← You are here
├── architecture-modular-design.instructions.md           ← Load as project context
│
│   ═══ STAGE 1 — PRE-MODULE FOUNDATIONAL ═══
├── step-01-architecture-exploration-specification.prompt.md   ← Scopes everything (1a)
├── step-02-shared-architectural-patterns.prompt.md            ← SP-NN patterns (1a)
├── step-03-security-architecture-framework.prompt.md          ← SEC-NN controls (1b)
├── step-04-data-architecture-framework.prompt.md              ← DA-NN constraints (1b)
├── step-05-documentation-strategy.prompt.md                   ← DOC-NN standards (1b)
├── step-06-governance-model.prompt.md                         ← GOV-NN ownership (1b)
│
│   ═══ STAGE 2 — MODULES ═══
├── step-07-module-enumeration.prompt.md                       ← M-NN manifest + SIC-NN contracts
├── step-08-module-specification.prompt.md                     ← Per-module (runs N times)
├── step-09-cross-module-consistency.prompt.md                 ← Module-set validation
│
│   ═══ STAGE 3 — POST-MODULE INTEGRATION ═══
├── step-10-api-contracts-rest.prompt.md                       ← OpenAPI (conditional)
├── step-11-api-contracts-grpc.prompt.md                       ← Protobuf (conditional)
├── step-12-api-contracts-events.prompt.md                     ← Event schemas (conditional)
├── step-13-api-contracts-other.prompt.md                      ← Generic protocol (conditional)
├── step-14-scorecard-update.prompt.md                         ← Scorecard v2.0
├── step-15-architecture-review.prompt.md                      ← Consistency + quality (constructive)
└── step-16-phase-4-readiness-review.prompt.md                 ← The gate (5 outcomes)
```

---

## File Descriptions

### `architecture-modular-design.instructions.md`
**Type:** Instructions file (load once as persistent project context)

The overarching context for any AI assistant operating in Phase 4. Loaded
once and active across all 16 prompt sessions. Contains the framework
orientation, the nested SDD cycle, the six Core Principles applied to
Phase 4, the three-stage structure, the authoritative dependency graph,
the minimum viable path, the behavioral guidelines, the output standards,
and the Phase 5 handoff connection.

The instructions file plays a heavy coordinating role because the
three-stage, dependency-driven, variable-artifact-count execution requires
the dependency graph to be authoritative.

---

### Stage 1 — Pre-Module Foundational

#### `step-01-architecture-exploration-specification.prompt.md`
**Type:** Action Prompt with Clarification Step

Produces the scoping document that drives every subsequent Phase 4 prompt.
Identifies preliminary module boundaries, scopes each cross-cutting
framework's depth, inventories the API protocols in use (determining which
conditional prompts run), surfaces open Phase 3 questions, and declares
this project's minimum viable path through the toolkit.

**Key design decision:** It scopes the architectural exploration without
producing any architecture. The same discipline that separated Phase 3
scoping from Phase 3 commitment separates Phase 4 scoping from Phase 4
specification.

#### `step-02-shared-architectural-patterns.prompt.md`
**Type:** Action Prompt with Clarification Step

Produces the shared architectural patterns and standards (SP-NN) every
module specification honors — error handling, logging, configuration,
naming, inter-module communication, data access, versioning, resilience,
cross-cutting concerns, and the standard module structure.

**Key design decision:** Every pattern gets an ID so module specs can cite
conformance and Steps 09 and 15 can verify it. A pattern that cannot be
cited or verified is not a pattern.

#### `step-03-security-architecture-framework.prompt.md`
**Type:** Action Prompt with Clarification Step (sub-stage 1b — parallel-eligible)

Produces the detailed, component-level security architecture (SEC-NN
controls): authentication flows, authorization policies, encryption
strategy, audit logging, trust boundary enforcement, least privilege.

**Key design decision:** The threat-to-control traceability matrix maps
every Phase 2 threat to a control or a flagged gap. A threat without a
control is a security hole the architecture would ship knowingly.

#### `step-04-data-architecture-framework.prompt.md`
**Type:** Action Prompt with Clarification Step (sub-stage 1b — parallel-eligible)

Produces the detailed data architecture (DA-NN constraints): data
classification scheme, ownership model, storage architecture,
component-level data flows, consistency and transaction strategy,
integrity constraints, and migration strategy.

**Key design decision:** The classification scheme is the spine — it
drives the Step 03 encryption-at-rest decisions. Modules own their data;
cross-module access is through interfaces, not shared tables.

#### `step-05-documentation-strategy.prompt.md`
**Type:** Action Prompt with Clarification Step (sub-stage 1b — parallel-eligible)

Produces the documentation strategy (DOC-NN types and standards): what
documentation exists, where it lives, how AI consumes it, and — critically
— the maintenance plan with AI-assisted staleness detection.

**Key design decision:** The maintenance plan is the structural defense
against documentation accurate on day one and progressively wrong
thereafter. A strategy without a maintenance plan fails the checklist.

#### `step-06-governance-model.prompt.md`
**Type:** Action Prompt with Clarification Step (sub-stage 1b — parallel-eligible)

Produces the governance model (GOV-NN): module ownership, domain
ownership, review gates, decision authority, escalation paths, and change
approval workflows.

**Key design decision:** Governance is explicit regardless of team size. A
one-person-owns-multiple-modules assignment is still explicit ownership;
"we'll figure it out" is not a governance model.

---

### Stage 2 — Modules

#### `step-07-module-enumeration.prompt.md`
**Type:** Action Prompt with Clarification Step

The gateway to Stage 2. Produces the **module manifest** (M-NN) and the
**strategic interface contracts** (SIC-NN), demonstrates scope coverage
without gaps or overlaps, and assigns each module the Stage 1 constraints
it must honor.

**Key design decision:** The strategic/detailed cascade. Step 07 produces
strategic contracts (operation names, conceptual types, error conditions,
strategic security). Step 08 details them. Steps 10–13 formalize them. Each
level adds precision; none contradicts the level above.

#### `step-08-module-specification.prompt.md`
**Type:** Parameterized Action Prompt (runs once per module)

Produces one complete module specification — the most consequential
artifact Phase 4 produces — covering all eight required sections: purpose
and responsibilities, public interfaces (the detailed contract conforming
to SIC-NN), data models, dependencies, security constraints, performance
requirements, test strategy, and monitoring hooks.

**Key design decisions:**
- **Run once per module.** Each module gets its own focused session so the
  specification reaches implementation-readiness depth.
- **The unusually rigorous evaluation checklist** enforces the
  implementation-readiness bar: field-level request/response schemas,
  every error condition handled, every data field typed with constraints,
  every dependency versioned, every security constraint citing its
  threat/compliance basis, every performance requirement measurable, test
  strategy with coverage targets, monitoring hooks referencing Phase 3
  Step 07 hook IDs.
- **The implementation-readiness self-assessment** (§9) forces a
  section-by-section check that an AI tool set could build from the spec
  alone.

#### `step-09-cross-module-consistency.prompt.md`
**Type:** Evaluation Prompt (module-set validation — not the gate)

Validates the module set along three axes: detailed interfaces conform to
the strategic contracts; the module set covers scope without gaps or
overlaps; every module cites the constraints (SP/SEC/DA/GOV/DOC/H) its
Step 07 assignment requires. Determination: CONSISTENT / INCONSISTENCIES
FOUND.

**Key design decision:** Scoped to the module set (Stage 2). Distinct from
Step 15, which reviews all artifacts plus quality. Step 09 catches
architecture bugs in the module set before they propagate into the Stage 3
contracts.

---

### Stage 3 — Post-Module Integration

#### `step-10-api-contracts-rest.prompt.md` · `step-11-api-contracts-grpc.prompt.md` · `step-12-api-contracts-events.prompt.md` · `step-13-api-contracts-other.prompt.md`
**Type:** Conditional Action Prompts (run only for protocols the project uses)

Four independent prompts that derive formal, machine-readable API
contracts from the Step 08 detailed interfaces, applying the Step 02 API
design standards and the Step 03 security architecture:

- **Step 10 — REST/OpenAPI:** OpenAPI 3.x specifications.
- **Step 11 — gRPC/Protobuf:** Protocol Buffers service and message
  definitions.
- **Step 12 — Events:** event schemas (AsyncAPI / JSON Schema / Avro /
  protobuf / CloudEvents) with envelope, delivery semantics, and evolution
  rules.
- **Step 13 — Other Protocol:** the generic prompt for GraphQL,
  WebSockets, MQTT, AMQP, or any custom protocol. Its first clarifying
  question names the protocol and its formal spec language.

**Key design decisions:**
- **API-first made concrete.** The contract is the authoritative
  definition; implementation conforms to it. Phase 5 auto-generates stubs,
  SDKs, validation, and mocks from the contract; Phase 6 generates contract
  tests.
- **The spec-versus-code boundary.** These prompts produce the contract
  specification, not the generated code — the generation is Phase 5's
  payoff from the contract.
- **The generic prompt (Step 13) is a full toolkit member**, not a "write
  your own" note. It applies the same structural conventions as the three
  specialized prompts, parameterized by the protocol named.

#### `step-14-scorecard-update.prompt.md`
**Type:** Action Prompt with Clarification Step (cross-phase living document update)

Produces **Principle Scorecard v2.0** — the Phase 3 baseline updated to
reflect every Phase 4 architectural decision, following the Phase 3 Step
06 update protocol. AI proposes scores; the practitioner calibrates.

**Key design decisions:**
- **A dedicated prompt**, separate from the review and the gate.
- **Regression detection against the v1.0 baseline** applies the Step 06
  thresholds and categories mechanically. A regression is never hidden by
  adjusting the baseline or the target.
- **Format inheritance** preserves the six-principle, five-element-per-
  principle structure from the v1.0 baseline.

#### `step-15-architecture-review.prompt.md`
**Type:** Evaluation Prompt (constructive review — not the gate)

Combines a cross-artifact consistency check across *all* Phase 4 artifacts
with a per-principle architecture quality assessment, and surfaces
improvement opportunities. Constructive: it names strengths, frames
quality findings as recommendations, and prepares the architecture for the
gate.

**Key design decision:** Distinct from both Step 09 (module-set scope) and
Step 16 (the gate). Step 15 is the mentor's review that makes the
architecture better; Step 16 is the gate that decides whether it passes.

#### `step-16-phase-4-readiness-review.prompt.md`
**Type:** Evaluation Prompt (Gate)

The Phase 4 gate. Produces per-principle gates, per-artifact completeness,
cross-artifact consistency (consuming Steps 09 and 15), Phase 3 alignment,
Phase 2 alignment, Phase 5 input completeness, and the **five-outcome
determination**, with **two structured amendment-package paths** (Phase 3
and Phase 2), tiered override authority, and the Phase 5 Handoff Summary.

**Key design decisions:**
- **Five determination outcomes** instead of four: READY, CONDITIONALLY
  READY, NOT READY (Phase 4 gaps), NOT READY (Phase 3 amendment required),
  NOT READY (Phase 2 amendment required).
- **Two amendment packages.** Phase 4 is the first phase whose gate can
  require amendment of two prior phases. The §5.2 Phase 3 package and the
  §6.2 Phase 2 package are each specific — naming the artifact, the
  amendment, and the driving Phase 4 finding.
- **Tiered override authority** with the two amendment-path overrides at
  the highest tier — overriding either means building Phase 5 on a
  prior-phase commitment the framework flagged as invalid.

---

## The Minimum Viable Path

Sixteen prompts is the full toolkit. A specific project rarely needs all
sixteen executions. The minimum viable path distinguishes the mandatory
prompts (always run) from the conditional ones (run per protocol).

### Mandatory Prompts (12 — every Phase 4 project)

| Step | Prompt | Why Mandatory |
|------|--------|---------------|
| 01 | Architecture Exploration Specification | Scopes all work |
| 02 | Shared Architectural Patterns | Constrains all modules |
| 03 | Security Architecture Framework | Every system has security concerns |
| 04 | Data Architecture Framework | Every system has data |
| 05 | Documentation Strategy | Required for AI-consumable docs |
| 06 | Governance Model | Required even in small teams |
| 07 | Module Enumeration | Defines the module set |
| 08 | Module Specification (×N) | Produces the core blueprint |
| 09 | Cross-Module Consistency | Validates the module set |
| 14 | Scorecard Update | Required cross-phase artifact |
| 15 | Architecture Review | Validates the complete architecture |
| 16 | Phase 4 Readiness Review | The gate |

### Conditional Prompts (4 — run only if applicable)

| Step | Prompt | Run When |
|------|--------|----------|
| 10 | API Contracts: REST | The project exposes REST/OpenAPI APIs |
| 11 | API Contracts: gRPC | The project exposes gRPC services |
| 12 | API Contracts: Events | The project uses async messaging |
| 13 | API Contracts: Other | The project uses any other protocol (GraphQL, WebSockets, MQTT, AMQP, custom) |

At least one of Steps 10–13 runs if the system has any API boundary —
which nearly all systems do. A project with a single REST API runs Step 10
and skips 11–13. A polyglot project may run several. The generic Step 13
runs once per non-standard protocol.

### Scaling Down for Simple Projects

A simple single-module, single-protocol project still runs all twelve
mandatory prompts plus one API contract prompt — thirteen executions, with
Step 08 running once. The toolkit has no "lightweight" mode because every
Phase 4 concern matters even for simple projects. What scales is the
*depth* of each artifact (set in Step 01 §5), not the *number* of
artifacts. A simple project produces a short security framework and a short
governance model — but it produces them, because skipping them produces
the gaps the common pitfalls warn against.

---

## How to Use This Tool Set

### Prerequisites

1. Confirm the [Phase 3 toolkit](../phase-03-design-technical-analysis/README.md)
   is complete with a passing Step 09 Readiness Review. Phase 4 cannot
   responsibly begin on a failed or conditional Phase 3 gate that has not
   been resolved. (If Phase 3's determination was NOT READY (Phase 2
   amendment required) and the amendment cycle is incomplete, resolve it
   first.)
2. Load `architecture-modular-design.instructions.md` as project-level
   instructions in your AI environment. This gives every Phase 4 session
   the framework context, behavioral guidelines, output standards, and the
   dependency graph without re-establishing them per session.

### Execution Order — Three Stages, Dependency-Driven

Phase 4 is **not strictly sequential**. It executes in three stages with a
dependency-driven sub-structure. The dependency graph below makes the
required ordering explicit.

```
Phase 3 Package (Design Direction + 6 ADRs, Scorecard v1.0, Update Protocol,
                 Observability Hooks, Compliance Constraints)
   │
   ▼
═══ STAGE 1: PRE-MODULE FOUNDATIONAL ═══
   │
   ▼
Step 01: Architecture Exploration Specification        ┐ sub-stage 1a
   │                                                    │ (sequential)
   ▼                                                    │
Step 02: Shared Architectural Patterns (SP-NN)         ┘
   │
   ├──────────────┬──────────────┬──────────────┐
   ▼              ▼              ▼              ▼          sub-stage 1b
Step 03:       Step 04:       Step 05:       Step 06:     (parallel-eligible)
Security       Data           Documentation  Governance
(SEC-NN)       (DA-NN)        (DOC-NN)       (GOV-NN)
   │              │              │              │
   └──────────────┴──────┬───────┴──────────────┘
                         │
                         ▼
═══ STAGE 2: MODULES ═══
                         │
                         ▼
Step 07: Module Enumeration (M-NN manifest + SIC-NN strategic contracts)
                         │
                         ▼
Step 08: Module Specification (run once per module — N executions)
                         │
                         ▼
Step 09: Cross-Module Consistency (CONSISTENT / INCONSISTENCIES FOUND)
                         │
                         ▼
═══ STAGE 3: POST-MODULE INTEGRATION ═══
                         │
   ┌─────────────────────┼─────────────────────┐
   ▼                     ▼                     ▼
Step 10–13:          Step 14:              (API contracts and
API Contracts        Scorecard Update       scorecard update
(conditional,        (v2.0)                 run in parallel)
parallel-eligible)
   │                     │
   └──────────┬──────────┘
              ▼
Step 15: Architecture Review (consistency + quality)
              ▼
Step 16: Phase 4 Readiness Review (the gate)
              │
   ┌──────────┼──────────┬─────────────────────┐
   ▼          ▼          ▼                     ▼
Phase 5    Phase 4    Phase 3              Phase 2
Authorized Internal   Amendment            Amendment
(READY /   Remediation Cycle                Cycle
CONDITIONAL) (NOT READY  (NOT READY          (NOT READY
             Phase 4)   Phase 3)            Phase 2)
```

The gate produces five determination outcomes (READY, CONDITIONALLY
READY, and three NOT READY variants); the four terminal branches above map
those outcomes to their remediation paths — READY and CONDITIONALLY READY
both proceed toward Phase 5 (fully or partially), while each NOT READY
variant routes to its responsible phase.

### Parallelism Opportunities

- **Sub-stage 1b (Steps 03–06)** can run in parallel once Step 02
  completes. The four framework concerns are orthogonal.
- **API contract prompts (Steps 10–13)** can run in parallel with each
  other and with Step 14 once Step 09 reports CONSISTENT.
- **Steps 01 and 02 run in strict sequence.** Step 07 follows all of
  Stage 1. Step 08 follows Step 07 (and runs N times). Step 09 follows all
  Step 08 executions. Step 15 follows Steps 10–14. Step 16 follows
  Step 15.

Running prompts in parallel requires separate AI sessions. Artifacts
produced by parallel prompts are consumed together by downstream steps.

### Running Each Prompt

For each step:

1. Open a new AI session with a large context window.
2. Confirm `architecture-modular-design.instructions.md` is loaded as
   project context.
3. Paste **all required inputs** above the kickoff line — see the prompt's
   metadata table for the exact list. (For Step 08, also paste the specific
   module you are specifying.)
4. Paste the **Kickoff** line to begin.
5. Answer the AI's clarifying questions (single-digit count) one at a time.
   Many Phase 4 prompts begin with a **presence check** because they depend
   on many prior artifacts — confirm the inputs are all present before the
   AI produces the artifact.
6. The AI produces the artifact in a single response.
7. Review the output against the prompt's evaluation checklist before
   accepting it.
8. Save the artifact for use as input to subsequent steps.

### Iterating

The SDD cycle is iterative. Common triggers:

- **Step 08 reveals a Step 07 strategic contract is wrong** → amend Step
  07, re-run the affected Step 08.
- **Step 09 returns INCONSISTENCIES FOUND** → fix in the responsible step
  (Step 07 or a specific Step 08), re-run Step 09.
- **A Step 10–13 contract reveals a Step 08 interface is underspecified**
  → return to Step 08, then re-run the contract.
- **Step 14 reveals a regression** → remediate the architecture in the
  responsible step or document acceptance per the Step 06 protocol.
- **Step 15 surfaces inconsistencies** → fix in the responsible step
  before Step 16.
- **Step 16 returns CONDITIONAL or NOT READY (Phase 4 gaps)** → execute
  named actions in the responsible prior steps, re-run Step 16.
- **Step 16 returns NOT READY (Phase 3 amendment required)** → run the
  Phase 3 amendment cycle (below).
- **Step 16 returns NOT READY (Phase 2 amendment required)** → run the
  Phase 2 amendment cycle (below).

---

## The Two Amendment Cycles

Phase 4 is the first phase whose gate can require amendment of *two* prior
phases. Step 16 evaluates Phase 3 alignment and Phase 2 alignment as
separate dimensions and produces a distinct, structured amendment package
for each.

### The Phase 3 Amendment Cycle

Triggered when Phase 4 work invalidates a Phase 3 design commitment — for
example, a module specification reveals the system structure ADR cannot be
cleanly decomposed, or a security finding requires a different security
model than Phase 3 committed.

Step 16 §5.2 produces a package naming the specific Phase 3 design ADRs,
scorecard elements, observability hooks, or compliance constraints to
amend, each with the driving Phase 4 finding. The cycle:

1. Return to Phase 3 with the §5.2 package.
2. Re-run the relevant Phase 3 prompts to produce amended artifacts.
3. Re-run Phase 3 Step 09 to verify Phase 3 internal consistency.
4. Return to Phase 4 and re-run the affected steps (the affected Stage 1
   framework, Step 07 enumeration, the affected Step 08 specs).
5. Re-run Step 16 to verify alignment is restored.

### The Phase 2 Amendment Cycle

Triggered when Phase 4 work invalidates a Phase 2 commitment — for example,
detailed effort modeling reveals the module set exceeds the cost envelope,
or a per-module performance requirement reveals a benchmark is
unachievable on the committed stack.

Step 16 §6.2 produces a package naming the specific Phase 2 ADRs, cost
model sections, benchmarks, threat model entries, or business case
elements to amend. The Phase 2 cycle is the deepest backward effect in the
framework — it cascades through Phase 3 and Phase 4:

1. Return to Phase 2 with the §6.2 package.
2. Re-run the relevant Phase 2 prompts; re-run Phase 2 Step 07 readiness.
3. Return to Phase 3, re-run the affected steps, re-run Phase 3 Step 09.
4. Return to Phase 4, re-run the affected steps, re-run Step 16.

### Why the Amendment Cycles Matter

Both cycles are the framework's structural defense against building Phase 5
implementation on a prior-phase commitment Phase 4 has invalidated.
Without them, three failure modes appear: silent drift (proceeding anyway),
ad-hoc workarounds (technical debt the documentation contradicts), and
unstructured remediation (guessing at what to change). The amendment cycles
are governance, not failure — the framework working as designed.

---

## The Readiness Review

The Step 16 Readiness Review is the phase gate — the mechanism that makes
the Phase 4 handoff trustworthy as Phase 5 input.

### What the Gate Evaluates

| Gate Dimension | What It Asks |
|---------------|--------------|
| **Per-principle gates** | Does each Core Principle have a sufficient architectural foundation across all Phase 4 artifacts? |
| **Per-artifact completeness** | Did each Phase 4 artifact meet its own evaluation checklist? |
| **Cross-artifact consistency** | Are all Phase 4 artifacts mutually consistent (consuming Steps 09 and 15)? |
| **Phase 3 alignment** | Has Phase 4 work invalidated any Phase 3 design commitment? |
| **Phase 2 alignment** | Has Phase 4 work invalidated any Phase 2 commitment? |
| **Phase 5 input completeness** | Does each Phase 5 concern have its required Phase 4 inputs? |

### The Five Determination Outcomes

| Status | Meaning | Action |
|--------|---------|--------|
| **READY** | All checks pass | Phase 5 may begin upon practitioner authorization |
| **CONDITIONALLY READY** | Conditional gates with documented remediation | Phase 5 may begin work not blocked by conditional gates |
| **NOT READY (Phase 4 gaps)** | Blocking gaps in Phase 4 work | Remediate within Phase 4, re-run Step 16 |
| **NOT READY (Phase 3 amendment required)** | Phase 3 alignment failure | Run the Phase 3 amendment cycle, re-run affected Phase 4 steps |
| **NOT READY (Phase 2 amendment required)** | Phase 2 alignment failure | Run the Phase 2 amendment cycle (cascades through Phase 3), re-run affected steps |

The five-outcome determination reflects the operational reality that Phase
4 gate failures can require four different remediation paths (internal,
Phase 3, Phase 2, or conditional progress). There is no "close enough"
path.

---

## ID Citation Discipline

Phase 4's coherence depends on a consistent ID-citation discipline. Each
framework establishes an ID series; module specifications cite the IDs they
honor; the consistency, review, and gate steps verify the citations.

| ID Series | Established By | Cited By | Verified By |
|-----------|---------------|----------|-------------|
| **SP-NN** (shared patterns) | Step 02 | Step 08 module specs; Steps 10–13 contracts | Steps 09, 15 |
| **SEC-NN** (security controls) | Step 03 | Step 08 security sections; Steps 10–13 contracts | Steps 09, 15, 16 |
| **DA-NN** (data constraints) | Step 04 | Step 08 data models; Step 12 payloads | Steps 09, 15 |
| **DOC-NN** (documentation types/standards) | Step 05 | Step 08 (as a doc artifact); Step 06 (ownership) | Step 15 |
| **GOV-NN** (governance) | Step 06 | Step 07 owners; Step 08 owner; Step 14 scorecard owner | Step 15 |
| **M-NN** (modules) | Step 07 | Step 08; Step 09; Steps 10–13 traceability | Steps 09, 15, 16 |
| **SIC-NN** (strategic interface contracts) | Step 07 | Step 08 detailed interfaces; Steps 10–13 | Step 09 (conformance) |
| **H-NN** (observability hooks) | Phase 3 Step 07 | Step 03 audit logging; Step 08 monitoring hooks | Steps 09, 15 |
| **TB-NN** (trust boundaries) | Step 03 | Step 07 boundary alignment; Step 08 security | Step 15 |
| **T-NN** (threats) | Phase 2 threat model | Step 03 controls; Step 08 security basis | Step 16 |

A pattern, control, or constraint that lacks an ID cannot be cited or
verified — which is why every framework assigns IDs and every module
specification cites them.

---

## Cross-Phase Living Documents

Phase 4 produces and maintains artifacts that later phases continue.

### The Module Specifications (Step 08)

The module specifications are the primary Phase 5 input. Each is a
self-contained document handed to an implementation tool set as context.
Phase 5 produces working modules from them. They are the most
consequential artifacts Phase 4 produces.

### The API Contracts (Steps 10–13)

The formal, machine-readable contracts drive code generation, contract
testing, and conformance checking in Phase 5 and Phase 6. They are
executable contracts, not documentation.

### The Updated Principle Scorecard (Step 14)

The scorecard continues as a cross-phase living document. Phase 4 produces
v2.0. Phase 5 will produce v3.x, Phase 6 v4.0, Phase 7 v5.0, per the Phase
3 Step 06 update protocol. Regression detection across phases continues —
a principle scoring lower at a later phase than at the v1.0 baseline is
evidence something has gone wrong.

### The ADRs

Phase 4 may produce architecture ADRs that build on the Phase 3 design
ADRs and the Phase 2 stack ADR. Phase 4 ADRs do not silently supersede
Phase 3 ADRs — substantive changes require explicit superseding ADRs per
standard practice.

---

## Common Pitfalls

**Vague module specifications.**
The most consequential Phase 4 failure. A module specification describing
responsibilities in general terms produces vague AI code in Phase 5. The
structural defense is Step 08's rigorous evaluation checklist and the
implementation-readiness verification in Steps 09 and 15.

**Skipping API formalization.**
Informal API contracts described in prose eliminate auto-generated stubs,
contract testing, and conformance checking. The structural defense is the
four dedicated API contract prompts (Steps 10–13) producing machine-
readable formal contracts — including the generic Step 13 for any protocol.

**Security as a separate layer.**
A security architecture disconnected from module specifications is
disconnected from the implementation. The structural defense is the rule
that security constraints belong in each module specification's security
section, plus Step 03 providing the comprehensive view that the module
specs apply concretely.

**Documentation strategy without a maintenance plan.**
A strategy specifying what documents exist but not who maintains them or
how staleness is detected produces documentation accurate on day one and
progressively wrong thereafter. The structural defense is Step 05's
required ownership, maintenance triggers, and AI-assisted staleness
detection.

**Architecture without governance.**
The absence of formal ownership and review gates works until two people
make conflicting changes to the same module boundary. The structural
defense is Step 06's required governance model — established now, not after
the first conflict.

**Cross-artifact inconsistency.**
A module specification referencing a non-existent schema, or an API
contract that does not match the module's interface, is an architecture
bug. The structural defense is Step 09 (module-set consistency) and Step 15
(cross-artifact review), both feeding Step 16.

**Treating cross-cutting frameworks as optional for simple projects.**
A simple project still needs all five frameworks. What scales is the depth,
not the number. The structural defense is the minimum viable path
designating all twelve mandatory prompts as mandatory regardless of project
size.

**Ignoring backward effects.**
If Phase 4 work reveals a Phase 3 or Phase 2 commitment is wrong, the
correct response is the amendment cycle — not silent adjustment. The
structural defense is Step 16's two NOT READY (amendment required)
determinations with structured packages.

**Producing Phase 5 implementation content.**
Phase 4 specifies; it does not implement. The most common drift is module
specs that include actual code or contracts that include implementation
logic. The structural defense is per-prompt prohibition lists and the
absence of code/script/config fields in the output templates.

---

## Connecting to Phase 5

Phase 4 hands off the architectural blueprint to Phase 5 (Implementation).
Phase 5 tool sets consume specific Phase 4 outputs:

| Phase 5 Concern | Phase 4 Inputs Consumed |
|-----------------|-------------------------|
| Module implementation | Step 08 module specifications, Step 02 shared patterns |
| API stub generation | Steps 10–13 API contracts |
| Contract testing | Steps 10–13 API contracts |
| Security implementation | Step 03 security framework, module security sections |
| Data layer implementation | Step 04 data framework, module data models |
| Test implementation | Module test strategy sections |
| Observability implementation | Module monitoring hooks, Phase 3 Step 07 handoff |
| Documentation generation | Step 05 documentation strategy |
| Code review governance | Step 06 governance model |
| Phase 5 scorecard updates | Step 14 Scorecard v2.0, Phase 3 Step 06 Update Protocol |

The Step 16 Readiness Review verifies each Phase 5 concern has its required
Phase 4 inputs before authorizing Phase 5. The Phase 5 Handoff Summary in
Step 16 §10 is structured for direct consumption by Phase 5 tool sets.

Phase 5 is where the discipline of Phases 1–4 pays its largest dividend.
Precise specifications produce high-quality AI-generated code; the scoring
and verification frameworks ensure that quality is measured, not assumed. A
precise Phase 4 blueprint produces implementation that is largely correct
on first generation and verifiable against the spec. A vague Phase 4
blueprint produces implementation that requires extensive human correction.

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | [date] | Initial release — instructions file plus sixteen prompts |

---

## Related Resources

- [AI-Centric Software Development Playbook — Full Series](../../../README.md)
- [Part 1 — Core Principles](../../../docs/part-01-core-principles.md)
- [Part 2 — Building Your Toolkit](../../../docs/part-02-building-your-toolkit.md)
- [Part 6 — Phase 4: Architecture & Modular Design](../../../docs/part-06-architecture-modular-design.md)
- [Phase 1 Tool Set](../phase-01-information-gathering-toolset/README.md)
- [Phase 2 Tool Set](../phase-02-analysis-stack-selection/README.md)
- [Phase 3 Tool Set](../phase-03-design-technical-analysis/README.md)
- [Part 7 — Phase 5: Implementation](../../../docs/part-07-implementation.md) *(the next phase)*

---

*Part of the AI-Centric Software Development Playbook*
*This tool set is a living artifact — it will be refined as the
methodology matures and use in practice reveals improvements.*
