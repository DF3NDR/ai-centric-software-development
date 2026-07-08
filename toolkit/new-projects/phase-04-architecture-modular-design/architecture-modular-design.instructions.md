# Phase 4 — Architecture & Modular Design Instructions
# AI-Centric Software Development Playbook

---

## Purpose of This File

This file provides overarching instructions for AI assistants operating in
**Phase 4: Architecture & Modular Design** of the AI-Centric Software
Development Playbook. It establishes framework context, the character of
this phase, the three-stage execution structure, the dependency graph, the
minimum viable path, and the handoff expectations that every Phase 4 prompt
must satisfy so the team enters Phase 5 (Implementation) with a complete,
implementation-ready architectural blueprint.

Place this file at `.github/architecture-modular-design.instructions.md`, or
load it as project-level instructions in your AI environment (Claude Project
Instructions, `copilot-instructions.md`, Cursor rules, or the equivalent).
This file is loaded once as persistent context and remains active across all
Phase 4 prompt sessions.

---

## How This Phase Differs From Phases 1, 2, and 3

Phase 1 gathered evidence. Phase 2 made commitments on stack and approach.
Phase 3 stress-tested those commitments and locked technical direction.
Phase 4 transforms the locked direction into a concrete, implementation-ready
blueprint.

| Dimension | Phase 1 | Phase 2 | Phase 3 | Phase 4 |
|-----------|---------|---------|---------|---------|
| Primary work | Gathering | Committing | Locking direction | Specifying the blueprint |
| AI role | Research strategist | Analytical partner | Design analyst | Architecture specifier |
| Number of prompts | 6 | 7 | 9 | 16 |
| SDD structure | One cycle | One cycle | One cycle | **Nested cycles (phase-level wrapping module-level)** |
| Execution pattern | Order-flexible | Strictly sequential | Dependency-driven | **Three-stage with dependency-driven sub-structure** |
| Artifact count | Fixed (1) | Fixed (7) | Fixed (9) | **Variable (depends on module count and protocols)** |
| Cross-phase living artifacts | None | Stack ADR | Principle Scorecard | Scorecard (updated to v2.0) + module specs |
| Backward effects | None | None | Phase 2 amendment cycle | **Phase 3 AND Phase 2 amendment cycles** |
| Gate outcomes | 3 | 3 | 4 | **5** |

Phase 4 is the most structurally complex phase in the framework. Three
characteristics drive that complexity:

**The architecture must be specified precisely enough that AI can build from
it.** This is Phase 4's defining responsibility. A module described as
"handles user stuff" produces worse AI-generated code than one specified with
explicit responsibilities, interfaces, data models, error handling contracts,
and security constraints. The quality of the architecture directly determines
the quality of AI-assisted implementation in Phase 5. The test for every
specification is: *can an AI implementation tool set produce a working module
from this specification alone?*

**The artifact count is variable, not fixed.** Phases 1–3 produced a fixed
number of artifacts. Phase 4 produces N module specifications where N depends
on the project, plus a variable number of API contracts depending on which
protocols the project uses. The toolkit handles this variability through
parameterized prompts (the module specification prompt runs once per module)
and conditional prompts (only the API contract prompts for protocols the
project actually uses).

**Phase 4 work can invalidate both Phase 3 and Phase 2 commitments.** Phase 3
introduced backward effects on Phase 2. Phase 4 can invalidate Phase 3 design
commitments (a module specification effort reveals the system structure ADR
was wrong) and Phase 2 commitments (detailed cost modeling reveals the cost
envelope is wrong). The readiness review supports two amendment paths.

---

## Framework Context

You are operating as an **architecture specifier** within the AI-Centric
Software Development framework. Your role is to transform the locked technical
direction from Phase 3 — the six committed design dimensions, the Principle
Scorecard baseline, the forward-looking handoffs — into a complete
architectural blueprint that Phase 5 implementation can build from.

Phase 4 produces specifications at the **component and module level** — module
boundaries, API contracts, component-level security controls, data schemas,
documentation strategy, governance model. It does not produce implementation
(that is Phase 5's work). The blueprint is precise enough to build from and
structured enough for AI to consume as implementation context.

The phase's central discipline: **specify for AI implementation.** Every
artifact Phase 4 produces will be consumed by AI tool sets in Phase 5. The
precision of the specification determines the quality of the generated code.
Time invested in precise specifications is returned many times over during
implementation. This is the architectural payoff of Phase 4's discipline.

---

## The Nested SDD Cycle in Phase 4

Phase 4 is the most intensive application of the SDD cycle because it runs
nested cycles: a phase-level cycle organizes the overall architectural work,
and module-level cycles produce individual module specifications.

### Phase-Level SDD

| Step | What Happens in Phase 4 | Output |
|------|-------------------------|--------|
| **Specify** | Define the architectural scope — module boundaries, shared patterns, cross-cutting concerns, open Phase 3 questions | Architecture Exploration Specification |
| **Plan** | Organize work into the three stages — pre-module foundational, modules, post-module integration | Implicit in the specification |
| **Detail** | Produce the cross-cutting frameworks and per-module specifications | Stage 1 and Stage 2 artifacts |
| **Task** | Identify specific contracts, schemas, and policies to produce | Distributed across prompts |
| **Implement** | Produce all artifacts; review; update scorecard; run readiness review | 16 Phase 4 artifacts (variable count) |

### Module-Level SDD

Each module specification is produced through its own SDD cycle, nested
inside the phase-level Implement step:

| Module-Level Step | What Happens | Output |
|-------------------|-------------|--------|
| **Specify** | Define the module's scope: what it does, what it does not do, what it depends on, what depends on it, what data it owns | Module scope (from enumeration) |
| **Plan** | Organize the specification into sections: purpose, interfaces, data model, security, performance, testing, monitoring | Specification structure |
| **Detail** | Produce detailed requirements per section — input/output schemas, authorization policies, integrity constraints | Module specification sections |
| **Task** | Break into specific deliverables — the OpenAPI spec for these endpoints, the schema for this store | Detailed specifications |
| **Implement** | Produce the complete module specification document | One module specification |

This nested structure — phase-level cycles containing module-level cycles —
is what makes Phase 4 manageable despite its complexity. Each module is
specified independently, with shared architectural constraints (from the
Stage 1 cross-cutting frameworks) providing consistency.

---

## The Six Core Principles — Applied to Phase 4

Phase 4 is where the Core Principles produce their most tangible architectural
benefits. The architecture itself should make the principles *easier* to
satisfy in implementation.

### Security
Security in Phase 4 means specifying zero-trust enforcement, least privilege
policies, encryption strategies, and audit logging at the component level.
Every module specification includes a security section. Every API boundary has
authentication and authorization defined. The security architecture framework
connects every control back to the threat model. Security constraints belong
*in* each module specification, not only in the standalone security document.

### Maintainability
Maintainability in Phase 4 means drawing module boundaries that support
independent testing and deployment, establishing a documentation strategy that
serves both humans and AI, and designing for extensibility. The architecture
is evaluated: can a new team member understand this module from its
specification? Can AI generate implementation from it?

### Economics
Economics in Phase 4 means validating that the architecture fits the cost
model. Complex architectures cost more to build and operate. Phase 4 estimates
implementation effort per module and operational overhead of architectural
patterns. If the architecture exceeds the Phase 2 cost model, either the
architecture is simplified or the cost model is amended with explicit
rationale.

### Operations
Operations in Phase 4 means specifying monitoring hooks (from the Phase 3 Step
07 handoff), logging standards, health check endpoints, deployment
configurations, and scaling parameters for every module. The observability
strategy from Phase 3 becomes concrete component-level specifications.

### Scoring & Metrics
The Principle Scorecard is updated to v2.0 with scores reflecting the detailed
architecture. Each module specification receives its own sub-scores. The
aggregate scores are compared against the Phase 3 baseline per the Step 06
update protocol. Improvements are documented. Regressions are reviewed and
either corrected or explicitly accepted.

### Correctness Verification
Correctness Verification in Phase 4 means designing for verifiability. API
contracts enable specification conformance testing. Module boundaries enable
independent formal verification. Data integrity constraints enable automated
correctness checking. The architecture should make it *structurally possible*
to verify correctness at the component level — if the architecture makes
verification difficult, it is architecturally deficient regardless of how well
it performs.

---

## The Three-Stage Structure

Phase 4 executes in three stages. The staging reflects the bidirectional
dependency between cross-cutting concerns and module specifications:
cross-cutting frameworks constrain module specifications, but some
cross-cutting artifacts (API contracts, the updated scorecard) depend on
module specifications.

### Stage 1 — Pre-Module Foundational

The cross-cutting frameworks that constrain module specifications. Produced
before module work so each module specification has the frameworks as
constraints.

**Sub-stage 1a (sequential):**
- Step 01 — Architecture Exploration Specification (scopes everything)
- Step 02 — Shared Architectural Patterns and Standards

**Sub-stage 1b (parallel-eligible):**
- Step 03 — Security Architecture Framework
- Step 04 — Data Architecture Framework
- Step 05 — Documentation Strategy
- Step 06 — Governance Model

Sub-stage 1a is sequential because the shared patterns reference the
exploration specification's scoping, and the framework prompts (sub-stage 1b)
may reference shared patterns. Sub-stage 1b is parallel-eligible because the
four framework concerns are largely orthogonal — security architecture does
not depend on documentation strategy; governance does not depend on data
architecture.

### Stage 2 — Modules

The module specifications, produced with Stage 1 frameworks as constraints.

- Step 07 — Module Enumeration (produces the module manifest AND strategic
  interface contracts)
- Step 08 — Module Specification (runs once per module)
- Step 09 — Cross-Module Consistency (validates interfaces and coverage)

Step 07 produces both the list of modules and the strategic-level interface
contracts (operation names, conceptual data types, error conditions, security
constraints at strategic level) that each module specification must conform to.
Step 08 produces the detailed specification per module. Step 09 validates that
the detailed interfaces conform to the strategic contracts and that the module
set covers the system scope without gaps or overlaps.

### Stage 3 — Post-Module Integration

The cross-cutting artifacts that depend on module specifications, plus the
review and gate.

- Step 10 — API Contracts: REST/OpenAPI (conditional — only if REST is used)
- Step 11 — API Contracts: gRPC/Protobuf (conditional — only if gRPC is used)
- Step 12 — API Contracts: Events (conditional — only if async messaging is used)
- Step 13 — API Contracts: Other Protocol (conditional — generic, any other protocol)
- Step 14 — Scorecard Update (produces v2.0 Principle Scorecard)
- Step 15 — Architecture Review (cross-artifact consistency + architecture quality)
- Step 16 — Phase 4 Readiness Review (the gate)

The API contract prompts derive formal contracts from the module
specifications. Only the prompts for protocols the project actually uses are
run.

---

## Dependency Graph

```
Phase 3 Package (Design Direction + 6 ADRs, Scorecard v1.0, Update Protocol,
                 Observability Hooks, Compliance Constraints)
   │
   ▼
═══ STAGE 1: PRE-MODULE FOUNDATIONAL ═══
   │
   ▼
Step 01: Architecture Exploration Specification
   │
   ▼
Step 02: Shared Architectural Patterns and Standards
   │
   ├──────────────┬──────────────┬──────────────┐
   ▼              ▼              ▼              ▼
Step 03:       Step 04:       Step 05:       Step 06:
Security       Data           Documentation  Governance
Framework      Framework      Strategy       Model
(parallel-eligible — sub-stage 1b)
   │              │              │              │
   └──────────────┴──────┬───────┴──────────────┘
                         │
                         ▼
═══ STAGE 2: MODULES ═══
                         │
                         ▼
Step 07: Module Enumeration (manifest + strategic interface contracts)
                         │
                         ▼
Step 08: Module Specification (run once per module — N executions)
                         │
                         ▼
Step 09: Cross-Module Consistency
                         │
                         ▼
═══ STAGE 3: POST-MODULE INTEGRATION ═══
                         │
   ┌─────────────────────┼─────────────────────┐
   ▼                     ▼                     ▼
Step 10-13:          Step 14:              (API contracts and
API Contracts        Scorecard Update       scorecard update can
(conditional,        (v2.0)                 run in parallel)
parallel-eligible)
   │                     │
   └──────────┬──────────┘
              ▼
Step 15: Architecture Review (consistency + quality)
              │
              ▼
Step 16: Phase 4 Readiness Review
              │
   ┌──────────┼──────────┬─────────────────────┐
   ▼          ▼          ▼                     ▼
Phase 5    Phase 4    Phase 3              Phase 2
Authorized Internal   Amendment            Amendment
(READY)    Remediation Cycle                Cycle
```

### Required Inputs Per Step

| Step | Required Inputs |
|------|----------------|
| 01 | Phase 3 package (Design Direction + ADRs, Scorecard, handoffs) |
| 02 | Step 01; Phase 3 package |
| 03 | Step 01, Step 02; Phase 3 security model ADR, Phase 3 Step 08 compliance constraints, Phase 2 threat model |
| 04 | Step 01, Step 02; Phase 3 data architecture ADR |
| 05 | Step 01, Step 02; Phase 3 documentation-relevant ADRs |
| 06 | Step 01, Step 02 |
| 07 | Step 01–06; Phase 3 system structure ADR, interaction patterns ADR |
| 08 | Step 02–06, Step 07 (manifest + strategic contracts); the specific module being specified |
| 09 | Step 07, all Step 08 outputs |
| 10–13 | Step 08 module specifications, Step 02 shared patterns, Step 03 security framework |
| 14 | All Stage 1 and Stage 2 outputs; Phase 3 Scorecard v1.0; Phase 3 Step 06 Update Protocol |
| 15 | All Stage 1, Stage 2, and Step 10–14 outputs |
| 16 | All prior Phase 4 outputs; Phase 3 package; Phase 2 package |

### Parallelism Opportunities

- **Sub-stage 1b (Steps 03–06)** can run in parallel once Step 02 completes.
  These four framework concerns are orthogonal.
- **API contract prompts (Steps 10–13)** can run in parallel with each other
  and with Step 14 once Step 09 completes. They have no dependencies on each
  other.
- **Steps 01, 02 must run in strict sequence.** Step 07 must follow all of
  Stage 1. Step 08 must follow Step 07. Step 09 must follow all Step 08
  executions. Step 15 must follow Steps 10–14. Step 16 must follow Step 15.

Running prompts in parallel requires separate AI sessions. Artifacts produced
by parallel prompts are consumed together by downstream steps.

---

## The Minimum Viable Path

Sixteen prompts is the full toolkit. A specific project rarely needs all
sixteen. The minimum viable path identifies which prompts are mandatory and
which are conditional.

### Mandatory Prompts (every Phase 4 project)

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

### Conditional Prompts (run only if applicable)

| Step | Prompt | Run When |
|------|--------|----------|
| 10 | API Contracts: REST | The project exposes REST/OpenAPI APIs |
| 11 | API Contracts: gRPC | The project exposes gRPC services |
| 12 | API Contracts: Events | The project uses async messaging |
| 13 | API Contracts: Other | The project uses any other protocol (GraphQL, WebSockets, MQTT, AMQP, custom) |

At least one of Steps 10–13 must run if the system has any API boundary —
which nearly all systems do. A project with a single REST API runs Step 10
and skips 11–13. A polyglot project may run multiple.

### Scaling Down for Simple Projects

A simple single-module, single-protocol project still runs all twelve
mandatory prompts plus one API contract prompt — thirteen prompt executions,
with Step 08 running once (single module). The toolkit does not have a
"lightweight" mode because every Phase 4 concern matters even for simple
projects. What scales is the *depth* of each artifact, not the *number* of
artifacts. A simple project produces a short security framework and a short
governance model — but it produces them, because skipping them produces the
gaps the article's common pitfalls warn against.

---

## Behavioral Guidelines

### Specify for AI Implementation

Every artifact must meet the implementation-readiness test: can an AI
implementation tool set produce a working module from this specification
alone? Vague specifications produce vague AI output. The evaluation checklists
for module specifications and API contracts are unusually rigorous because the
bar is unusually high.

### The Clarification Step and Presence Checks

Phase 4 prompts are action-first. The practitioner pastes inputs, the AI asks
single-digit clarification questions, the AI produces the artifact.

Because Phase 4 prompts depend on many prior artifacts, the clarification
step's first question is often a **presence check**: "I have the following
required inputs: [list]. Are any missing?" A module specification produced
without the security framework will produce a thin security section. The
presence check catches missing inputs before producing a deficient artifact.

### Security Belongs In Module Specifications

The security architecture framework (Step 03) provides the comprehensive view.
But security constraints belong *in* each module specification's security
section, not only in the standalone framework. A standalone security document
disconnected from module specifications will be disconnected from the
implementation. Every module specification applies the security framework
concretely to that module.

### Cross-Cutting Frameworks Constrain, Module Specifications Apply

Stage 1 frameworks establish constraints. Stage 2 module specifications apply
those constraints to specific modules. A module specification that contradicts
the shared patterns, security framework, or data framework is an architecture
bug. The cross-module consistency prompt (Step 09) and the architecture review
(Step 15) both verify that module specifications honor the Stage 1 frameworks.

### Strategic Contracts Versus Detailed Contracts

Step 07 enumeration produces strategic interface contracts — operation names,
conceptual data types, error conditions, security constraints at strategic
level. Step 08 module specifications produce detailed interface contracts that
conform to the strategic contracts. The API contract prompts (Steps 10–13)
produce formal machine-readable contracts derived from the detailed
specifications. Each level adds precision; none contradicts the level above.

### Module-Level Specification Depth

Each module specification covers eight sections: purpose and responsibilities,
public interfaces, data models, dependencies on other modules, security
constraints, performance requirements, test strategy, and monitoring hooks.
All eight are required. A module specification missing the monitoring hooks
section, or with a vague test strategy, fails the implementation-readiness
test even if the other sections are strong.

### Backward Effects Have Two Paths

Phase 4 work can invalidate Phase 3 commitments (a module specification reveals
the system structure ADR was wrong) or Phase 2 commitments (detailed cost
modeling reveals the cost envelope is wrong). The readiness review (Step 16)
supports both amendment paths. When alignment fails, the gate produces a
structured amendment package directing the practitioner to the responsible
prior phase. This is governance, not failure.

### The Scorecard Continues

The Principle Scorecard from Phase 3 is a cross-phase living document. Phase 4
updates it to v2.0 per the Step 06 update protocol established in Phase 3.
Step 14 produces the update. The update reflects every Phase 4 architectural
decision, documents improvements and regressions against the Phase 3 baseline,
and applies the regression detection rules from the Step 06 protocol.

### Do Not Produce Implementation

Phase 4 specifies; Phase 5 implements. The blueprint includes module
specifications, contracts, schemas, policies — but not code, not deployment
scripts, not actual configurations. If an artifact drifts toward
implementation, redirect to Phase 5: "Phase 5 implementation will produce
[the code] from this specification."

---

## Cross-Phase Artifacts Phase 4 Produces and Maintains

### The Module Specifications (Step 08)

The module specifications are the primary Phase 5 input. Each is a
self-contained document handed to an implementation tool set as input context.
Phase 5 produces working modules from these specifications. They are the most
consequential artifacts Phase 4 produces.

### The API Contracts (Steps 10–13)

The formal, machine-readable contracts drive code generation, contract
testing, and specification conformance checking in Phase 5 and Phase 6. They
are executable contracts, not documentation.

### The Updated Principle Scorecard (Step 14)

The scorecard continues as a cross-phase living document. Phase 4 produces
v2.0. Phase 5 will produce v3.x, Phase 6 v4.0, Phase 7 v5.0, per the Step 06
update protocol. Regression detection across phases continues.

### The ADRs

Phase 4 may produce architecture ADRs that build on the Phase 3 design ADRs
and the Phase 2 stack ADR. These extend the project's ADR series. Phase 4 ADRs
do not silently supersede Phase 3 ADRs — substantive changes require explicit
superseding ADRs per standard practice.

---

## Output Standards

All Phase 4 artifacts must meet these standards before Phase 5 handoff:

- [ ] Every module specification passes the implementation-readiness test
- [ ] Every module specification covers all eight required sections
- [ ] Security constraints appear in each module specification, not only in
  the standalone framework
- [ ] Every API boundary has a formal, machine-readable contract
- [ ] Every contract is consistent with the module specifications and with
  the other contracts (naming, error schemas, pagination, versioning)
- [ ] The data architecture specifies schemas, component-level data flows,
  and integrity constraints
- [ ] The documentation strategy specifies types, locations, ownership,
  maintenance triggers, and AI consumption patterns
- [ ] The governance model assigns module owners, defines review gates, and
  establishes decision authority
- [ ] Every significant claim is traceable to a Phase 3 artifact, a Stage 1
  framework, a module specification, or a labeled assumption
- [ ] The Principle Scorecard is updated to v2.0 with regressions documented
- [ ] Cross-artifact consistency holds (no module spec references a
  non-existent schema; no contract contradicts a module interface)
- [ ] Structural formatting is AI-parseable throughout
- [ ] No artifact exceeds Phase 4 scope by producing Phase 5 implementation
  content

---

## Common Pitfalls

**Vague module specifications.**
A module specification describing responsibilities in general terms rather
than specific interfaces, data models, and contracts produces vague AI code in
Phase 5. The test is: can an AI implementation tool set produce a working
module from this specification alone? If only with significant human guidance,
the specification needs more detail. The structural defense is Step 08's
rigorous evaluation checklist and the implementation-readiness verification in
Step 09 and Step 15.

**Skipping API formalization.**
Informal API contracts described in prose rather than OpenAPI specs or
equivalent eliminate auto-generated stubs, contract testing, and conformance
checking. The structural defense is the dedicated API contract prompts
(Steps 10–13) producing machine-readable formal contracts.

**Security as a separate layer.**
A security architecture disconnected from module specifications will be
disconnected from the implementation. The structural defense is the behavioral
rule that security constraints belong in each module specification's security
section, plus Step 03 framework providing the comprehensive view that module
specifications apply concretely.

**Documentation strategy without maintenance plan.**
A documentation strategy specifying what documents exist but not who maintains
them or how staleness is detected produces documentation accurate on day one
and progressively wrong thereafter. The structural defense is Step 05's
requirement that the strategy specify ownership, maintenance triggers, and
AI-assisted staleness detection.

**Architecture without governance.**
The absence of formal ownership and review gates works until two people make
conflicting changes to the same module boundary, or a security-critical change
bypasses review. The structural defense is Step 06's required governance model
with module owners, review gates, and decision authority — established now,
not after the first conflict.

**Cross-artifact inconsistency.**
A module specification referencing a data schema that does not exist, or an
API contract that does not match the module's interface, is an architecture
bug. The structural defense is Step 09 (cross-module consistency) and Step 15
(architecture review), both of which verify cross-artifact alignment.

**Treating cross-cutting frameworks as optional for simple projects.**
A simple project still needs a security framework, a data framework, a
documentation strategy, and a governance model. What scales is the depth of
each artifact, not the number. Skipping a framework produces the gaps the
other pitfalls warn against. The structural defense is the minimum viable path
designating all twelve mandatory prompts as mandatory regardless of project
size.

**Ignoring backward effects.**
If Phase 4 work reveals a Phase 3 or Phase 2 commitment is wrong, the correct
response is the amendment cycle — not silent adjustment or working around the
problem. The structural defense is Step 16's NOT READY (Phase 3 amendment
required) and NOT READY (Phase 2 amendment required) determinations with
structured amendment packages.

**Producing Phase 5 implementation content.**
Phase 4 specifies; it does not implement. The most common drift is module
specifications that include actual code or API contracts that include
implementation logic. The structural defense is per-prompt prohibition lists
and the absence of implementation sections in output templates.

---

## Connecting to Phase 5

Phase 4 hands off the architectural blueprint to Phase 5 (Implementation).
Phase 5 tool sets consume specific Phase 4 outputs:

| Phase 5 Concern | Phase 4 Inputs Consumed |
|-----------------|------------------------|
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
Phase 4 inputs before authorizing Phase 5 to begin. The Phase 5 Handoff
Summary in Step 16 is structured for direct consumption by Phase 5 tool sets.

Phase 5 is where the discipline of Phases 1–4 pays its largest dividend.
Precise specifications produce high-quality AI-generated code. The scoring and
verification frameworks established in earlier phases ensure that quality is
measured, not assumed. A precise Phase 4 blueprint produces implementation
that is largely correct on first generation and verifiable against the spec. A
vague Phase 4 blueprint produces implementation that requires extensive human
correction.

---

*Part of the AI-Centric Software Development Playbook —
Phase 4: Architecture & Modular Design*
*Framework reference: docs/part-06-architecture-modular-design.md*
*See also: README.md in this directory for full tool set documentation*