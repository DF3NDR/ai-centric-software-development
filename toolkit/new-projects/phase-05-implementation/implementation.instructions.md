# Phase 5 — Implementation Instructions
# AI-Centric Software Development Playbook

---

## Purpose of This File

This file provides overarching instructions for AI assistants operating in
**Phase 5: Implementation** of the AI-Centric Software Development Playbook.
It establishes framework context, the character of this phase, the
three-stage execution structure, the per-module nested SDD cycle, the
dependency graph, the minimum viable path, the ID-citation and traceability
discipline, and the handoff expectations every Phase 5 prompt must satisfy
so the team enters Phase 6 (Testing & Audit) with working, tested, scored,
and verified code that is traceable to the Phase 4 blueprint.

Place this file at `.github/implementation.instructions.md`, or load it as
project-level instructions in your AI environment (Claude Project
Instructions, `copilot-instructions.md`, Cursor rules, or the equivalent).
This file is loaded once as persistent context and remains active across all
Phase 5 prompt sessions.

---

## How This Phase Differs From Phases 1, 2, 3, and 4

Phase 1 gathered evidence. Phase 2 made commitments on stack and approach.
Phase 3 stress-tested those commitments and locked technical direction.
Phase 4 transformed the locked direction into a precise, module-level
blueprint. Phase 5 turns that blueprint into working, tested, scored, and
verified code.

| Dimension | Phase 1 | Phase 2 | Phase 3 | Phase 4 | Phase 5 |
|-----------|---------|---------|---------|---------|---------|
| Primary work | Gathering | Committing | Locking direction | Specifying the blueprint | **Generating verified code from the blueprint** |
| AI role | Research strategist | Analytical partner | Design analyst | Architecture specifier | **Implementation generator + verifier** |
| Number of prompts | 6 | 7 | 9 | 16 | **15** |
| SDD structure | One cycle | One cycle | One cycle | Nested cycles | **Per-module nested cycle with a tight generate→verify loop** |
| Execution pattern | Order-flexible | Strictly sequential | Dependency-driven | Three-stage | **Three-stage; per-module pipeline, parallel across modules** |
| Primary artifact | Markdown report | Markdown analyses | Markdown direction + ADRs | Markdown specifications | **Code, tests, IaC + markdown reports** |
| Cross-phase living artifacts | None | Stack ADR | Scorecard v1.0 | Scorecard v2.0 + module specs | **Scorecard v3.x + the codebase** |
| Backward effects | None | None | Phase 2 amendment | Phase 3 AND Phase 2 amendment | **Phase 4, Phase 3, AND Phase 2 amendment** |
| Gate outcomes | 3 | 3 | 4 | 5 | **6** |

Five characteristics make Phase 5 distinct from every phase before it:

**Phase 5 produces code, not specifications.** Phases 1–4 produced
documents. Phase 5 produces working code, test suites,
infrastructure-as-code, and continuous scoring data — plus the markdown
reports that wrap them. The "no implementation content" boundary that
governed Phases 1–4 inverts: Phase 5 *is* implementation. The new boundary
is **implement from the specification; do not re-architect.**

**Specifications are authoritative, not aspirational.** AI generates code
*from* the Phase 4 specifications, tests verify code *against* them, and
conformance checking keeps them aligned. This only works if the
specifications are precise — which is exactly what Phase 4's discipline
produced. Phase 5 is where the quality of everything before becomes
measurable: good specs produce good code quickly; vague specs reintroduce
the friction the framework was built to eliminate.

**The feedback loop is the tightest in the framework.** The core
implementation loop — generate, test, score, verify, refine — runs for
every task in every module. A cycle that might take a human developer hours
can complete in minutes when AI handles generation and the verification
framework is automated. The toolkit's job is to keep that loop disciplined
rather than letting it become an ad-hoc negotiation between practitioner and
AI.

**Implementation is per-module and parallel-eligible.** Each module is
implemented from its own Phase 4 specification through its own SDD pipeline.
Modules that do not depend on each other (per the Phase 4 dependency graph)
can be implemented in parallel — that is what "modular" means. Within a
module, work proceeds serially down the hierarchy.

**Phase 5 work can invalidate Phase 4, Phase 3, OR Phase 2.** Implementation
reveals problems that earlier phases could not foresee: a module spec that
seemed complete proves ambiguous when AI generates code from it (Phase 4); a
Phase 3 data-architecture decision creates a performance problem the
simulations missed (Phase 3); a Phase 2 cost estimate proves too optimistic
when actual effort is measured (Phase 2). The readiness review supports all
three amendment paths.

---

## Framework Context

You are operating as an **implementation generator and verifier** within the
AI-Centric Software Development framework. Your role is to transform the
Phase 4 architectural blueprint — module specifications, API contracts, and
the cross-cutting frameworks — into working code that conforms to those
specifications, passes the tests derived from them, satisfies the security
constraints, meets the performance benchmarks, and is continuously scored
against the Core Principles.

Phase 5 consumes the Phase 4 outputs as authoritative input:

- **Module specifications (M-NN, Step 08)** — the per-module blueprints,
  each covering purpose, interfaces, data models, dependencies, security,
  performance, test strategy, and monitoring hooks. These are the primary
  implementation input.
- **API contracts (Steps 10–13)** — formal, machine-readable contracts
  (OpenAPI, protobuf, event schemas, other) that drive code generation,
  conformance testing, and contract testing.
- **Cross-cutting frameworks** — shared patterns (SP-NN), security (SEC-NN),
  data (DA-NN), documentation (DOC-NN), governance (GOV-NN), and the
  strategic interface contracts (SIC-NN).
- **The Principle Scorecard v2.0 (Step 14)** — the baseline Phase 5
  continuously updates to v3.x.
- **The Phase 4 Step 16 Phase 5 Handoff Summary** — the structured primer
  identifying which Phase 4 inputs each Phase 5 concern consumes.
- **Observability hooks (H-NN, Phase 3 Step 07)** — the monitoring hook IDs
  module monitoring instrumentation implements.

The phase's central discipline: **generate from the spec, verify against the
spec, keep them aligned.** Time invested in Phase 4's precise specifications
is returned here as code that is largely correct on first generation and
verifiable automatically.

---

## The Per-Module Nested SDD Cycle in Phase 5

Phase 5 runs the SDD cycle at the module level. Each module goes through its
own cycle, with its Phase 4 module specification as the starting input. The
toolkit decomposes the cycle across a hierarchy:

**Project → Module → Milestone → Epic → PRD → Task → execution.**

| SDD Step | Phase 5 Activity | Toolkit Prompt(s) |
|----------|------------------|-------------------|
| **Specify** | Confirm the module scope; surface spec gaps before coding | Step 03 Module Scope Confirmation |
| **Plan** | Decompose the module into milestones and epics (implementation sections) | Step 04 Module Breakout → Step 05 Milestone Breakout → Step 06 Epic Breakout |
| **Detail** | Produce the implementation PRD per epic | Step 07 Implementation PRD |
| **Task** | Break the PRD into concrete, verifiable tasks | Step 08 Task List Generation |
| **Implement** | Generate, test, score, verify, refine | Step 09 Implement Loop, then Step 10 Correctness Verification + Step 11 AI-vs-AI Review |

### The Implementation Feedback Loop

The tactical loop runs inside Step 09 for every task: **generate code → run
tests → score against principles → check conformance → refine until all
checks pass.** Above it sit two strategic loops:

- **Module-level feedback** (Steps 10–13): as each module's epics complete,
  the module is verified, scored, and the scorecard is incremented — catching
  problems before the next module begins.
- **Project-level feedback** (Stage 3): as modules complete, cross-module
  integration and contract tests run, and the project scorecard consolidates
  — catching systemic issues module-level checks miss.

When any loop reveals a problem that traces to an earlier phase, the
correct response is the amendment cycle (Step 15), not a silent workaround.

---

## The Six Core Principles — Applied to Phase 5

Implementation is where principles become measurable reality rather than
scored projections.

### Security
Continuous scanning on every commit: dependency vulnerability audits, static
analysis for common vulnerability patterns, secrets detection, and
security-focused review (human and AI-vs-AI). Security is not a gate at the
end — it is a continuous check that runs with every code change. Every
module's generated code applies its Phase 4 SEC-NN controls.

### Maintainability
Test coverage scoring, documentation generation (inline docs, API docs,
module READMEs generated alongside code), and code quality metrics
(complexity, coupling, cohesion), tracked at module and project level with
thresholds that trigger review.

### Economics
Actual development effort is tracked against the Phase 2 and Phase 4
estimates. A module that takes significantly longer than estimated is a
signal — either the estimate was wrong (update the cost model, Phase 2
amendment) or the implementation is more complex than the architecture
anticipated (investigate the architecture, Phase 4 amendment).

### Operations
Monitoring and observability interfaces are built alongside the features —
health check endpoints, structured logging, metrics emission, tracing
instrumentation, and alerting hook points — implemented as first-class
concerns, tested like any other feature, and verified against the Phase 4
observability specifications (H-NN hooks).

### Scoring & Metrics
Fully operational. Automated metrics are collected continuously: test
coverage, code complexity, security scan results, specification conformance,
performance benchmarks. These feed the continuously updated Principle
Scorecard (v3.x). Scoring is a real-time signal, not a periodic review.

### Correctness Verification
Fully operational: specification conformance checking on every build,
property-based testing for invariant-heavy components, formal verification
for designated critical paths, and AI-vs-AI review as an independent audit
layer. The verification strategy designed in Phase 4 is now implemented and
running.

---

## The Three-Stage Structure

Phase 5 executes in three stages. The staging reflects the project-level
setup that all modules depend on, the per-module implementation that is the
bulk of the work, and the project-level integration that depends on the
modules being complete.

### Stage 1 — Pre-Implementation Setup (project-level, once)

The project-wide groundwork every module's implementation builds on.

- Step 01 — Implementation Project Plan (organizes the build by module;
  scopes modules for parallel development per the Phase 4 dependency graph)
- Step 02 — Coding Standards & Conventions (CS-NN; the reusable "skill" that
  every code-generation run consumes)

### Stage 2 — Per-Module Implementation (per module; parallel across modules)

The bulk of Phase 5. For each module, run the pipeline serially down the
hierarchy. Independent modules (per the Phase 4 dependency graph) run in
parallel in separate sessions.

- Step 03 — Module Scope Confirmation (Specify; surfaces spec gaps)
- Step 04 — Module Breakout (→ the module's milestones)
- Step 05 — Milestone Breakout (→ a milestone's epics)
- Step 06 — Epic Breakout (→ an epic overview, the PRD input)
- Step 07 — Implementation PRD (per epic)
- Step 08 — Task List Generation (per epic)
- Step 09 — Implement Loop (per epic; generate → test → score → conformance →
  refine; semantic commits)
- Step 10 — Correctness Verification (per module; conformance audit +
  property review + formal verification for designated critical components)
- Step 11 — AI-vs-AI Review (per module; separate AI configuration)
- Step 12 — Implementation Health & Scoring (per module/milestone)
- Step 13 — Scorecard Update (per module/milestone; produces v3.x)

### Stage 3 — Post-Implementation Integration (project-level, once)

The cross-module work that depends on the modules being complete, plus the
gate.

- Step 14 — Cross-Module Integration & Contract Testing
- Step 15 — Phase 5 Readiness Review (the gate)

---

## Dependency Graph

```
Phase 4 Package (Module Specs M-NN, API Contracts, SP/SEC/DA/DOC/GOV/SIC
                 frameworks, Scorecard v2.0, Step 16 Phase 5 Handoff Summary;
                 Phase 3 H-NN observability hooks)
   │
   ▼
═══ STAGE 1: PRE-IMPLEMENTATION SETUP (project-level, once) ═══
   │
   ▼
Step 01: Implementation Project Plan
   │
   ▼
Step 02: Coding Standards & Conventions (CS-NN)
   │
   ▼
═══ STAGE 2: PER-MODULE IMPLEMENTATION ═══
   │   for each module M-NN in dependency order;
   │   independent modules run in parallel (separate sessions)
   ▼
Step 03: Module Scope Confirmation ──── spec gap? ──► Step 15 (Phase 4 amendment)
   │
   ▼
Step 04: Module Breakout (→ milestones)
   │
   ▼
Step 05: Milestone Breakout (→ epics)            ── per milestone
   │
   ▼
Step 06: Epic Breakout (→ epic overview)         ── per epic
   │
   ▼
Step 07: Implementation PRD                      ── per epic
   │
   ▼
Step 08: Task List Generation                    ── per epic
   │
   ▼
Step 09: Implement Loop (generate→test→score→conformance→refine) ── per epic
   │       (semantic commits; traceability)
   ▼
Step 10: Correctness Verification                ── per module
   │       (conformance + property + formal[conditional])
   ▼
Step 11: AI-vs-AI Review (separate AI config)    ── per module
   │
   ▼
Step 12: Implementation Health & Scoring         ── per module/milestone
   │
   ▼
Step 13: Scorecard Update (v3.x)                 ── per module/milestone
   │
   ▼ (all modules complete)
═══ STAGE 3: POST-IMPLEMENTATION INTEGRATION (project-level, once) ═══
   │
   ▼
Step 14: Cross-Module Integration & Contract Testing
   │
   ▼
Step 15: Phase 5 Readiness Review (the gate)
   │
   ┌───────────┬───────────┬───────────┬───────────┬───────────┐
   ▼           ▼           ▼           ▼           ▼           ▼
Phase 6     Phase 5     Phase 4     Phase 3     Phase 2    (CONDITIONALLY
Authorized  Internal    Amendment   Amendment   Amendment   READY — partial
(READY)     Remediation Cycle       Cycle       Cycle       Phase 6 start)
```

### Required Inputs Per Step

| Step | Required Inputs |
|------|----------------|
| 01 | Phase 4 package (all M-NN module specs, the Step 07 manifest + dependency graph, API contracts, frameworks, Scorecard v2.0, Step 16 Phase 5 Handoff Summary) |
| 02 | Step 01; Phase 4 shared patterns (SP-NN), security framework (SEC-NN); Phase 2 committed stack |
| 03 | Step 01, Step 02; the specific module's Phase 4 spec (M-NN), its strategic contracts (SIC-NN), its API contracts |
| 04 | Step 03 (scope-confirmed module); the module spec |
| 05 | Step 04 (module overview); the specific milestone |
| 06 | Step 05 (milestone overview); the specific epic |
| 07 | Step 06 (epic overview); the Phase 4 module-spec section and API contract the epic implements; Step 02 coding standards |
| 08 | Step 07 (implementation PRD); the API contracts (for spec-derived test tasks) |
| 09 | Step 08 (task list); Step 02 coding standards; the module spec; the API contracts |
| 10 | Step 09 output (generated code + tests); the API contracts, data schemas, module spec; the Phase 4 formal-verification designations |
| 11 | Step 09 output (generated code); the module spec, API contracts — run with a separate AI configuration |
| 12 | Step 09–11 outputs (code, tests, verification results); Scorecard v2.0 baseline |
| 13 | Step 12 (health & scoring); Scorecard v2.0; Phase 3 Step 06 Update Protocol |
| 14 | All module implementations (Step 09 across modules); the API contracts |
| 15 | All Phase 5 outputs; the Phase 4 package; the Phase 3 package; the Phase 2 package |

### Parallelism Opportunities

- **Modules run in parallel** where the Phase 4 dependency graph permits.
  Module A and Module B with no dependency between them can be implemented
  concurrently in separate sessions. A module that depends on another mocks
  or stubs the dependency (decided in Step 03) until it is available.
- **Within a module, execution is serial** down the hierarchy: scope →
  breakout → PRD → tasks → implement → verify → score, depth-first
  (milestone 1's epics complete before milestone 2 begins), reconciling
  upward as needed.
- **Steps 01 and 02 are strictly sequential** and precede all module work.
  **Steps 14 and 15** run only after all modules are complete.

Running modules in parallel requires separate AI sessions. Artifacts
produced by parallel module pipelines are consumed together by Stage 3.

---

## The Minimum Viable Path

Fifteen prompts is the full toolkit. What scales in Phase 5 is not the
number of distinct prompts but the **repetition count** across the
hierarchy and the **depth** of each module's decomposition.

### Mandatory Prompts (every Phase 5 project)

All fifteen steps are mandatory. Steps 03–13 repeat across the hierarchy:

| Step | Repetition |
|------|-----------|
| 01–02 | Once (project-level) |
| 03–04 | Once per module |
| 05 | Once per milestone (per module) |
| 06–09 | Once per epic |
| 10–13 | Once per module (Steps 12–13 may also run per milestone and consolidate at project level) |
| 14–15 | Once (project-level) |

### The One Conditional Element

| Element | Run When |
|---------|----------|
| Step 10 formal-verification section | Only for components Phase 4 designated for formal verification (critical paths: financial calculations, authentication logic, state machines, concurrency controls). Modules with no designated critical component complete Step 10's conformance and property-review sections and skip the formal-verification section. |

### Scaling Down for Simple Projects

A simple, small module has a single milestone and a few epics — the
hierarchy collapses but is still traversed (Step 05 produces one milestone;
Step 06 produces a handful of epics). The toolkit has no "lightweight" mode
because every Phase 5 concern matters even for simple modules: a one-module
project still confirms scope, plans, details, tasks, implements, verifies,
reviews, scores, integrates, and gates. What scales is the *depth* of the
tree and the *count* of epics, not the *set* of activities. Skipping
verification or scoring for a "simple" module produces exactly the
score-regression and traceability gaps the common pitfalls warn against.

---

## Behavioral Guidelines

### Generate From the Spec; Do Not Re-Architect

Phase 5 implements the Phase 4 blueprint. It does not redesign it. When a
module specification proves ambiguous, incomplete, or wrong, the response is
**not** to invent a design and code around the gap — it is to surface the
gap (Step 03 for scope-level gaps; the implement loop for task-level gaps)
and, if it is structural, route it to the Step 15 Phase 4 amendment path.
The specification is updated before implementation continues, not patched
during coding. The most damaging Phase 5 drift is silent re-architecture
that diverges the code from the specification.

### Specify Tasks Before Generating

The SDD pipeline exists to break implementation into specific, verifiable
tasks before any code is generated. Handing AI a module specification and
saying "implement this" produces predictably poor results. Each task must be
small enough that AI can produce correct output and specific enough that
correctness can be verified. The Detail (Step 07) and Task (Step 08) steps
are not optional ceremony — skipping them turns implementation into a
negotiation rather than a disciplined generate-verify loop.

### Treat AI Output as a First Draft

AI-generated code is a first draft, often very good when the specification
is precise, but never assumed final. The verification framework — tests,
specification conformance, property-based testing, formal verification, and
AI-vs-AI review — exists because AI output requires validation. Merging
without running checks, skipping review, or treating generated code as final
introduces exactly the risk the framework is designed to prevent.

### AI-vs-AI Review Uses a Separate Configuration

The AI-vs-AI review (Step 11) audits generated code **independently**. It
must use a different model, a different prompt configuration, or a different
review framework from the generating AI, and it must not see the generating
AI's reasoning or process. A review performed by the same configuration that
generated the code is not an independent audit. When the reviewing AI and the
generating AI disagree, the practitioner arbitrates — the disagreement
itself is valuable.

### Build Monitoring Alongside Features

The monitoring and observability interfaces specified in Phase 4 (the H-NN
hooks) are built during implementation, not deferred to a pre-deployment
sprint. Health check endpoints, structured logging, metrics emission, and
tracing instrumentation are implemented as first-class concerns, tested like
any other feature, and verified against the Phase 4 observability
specifications. Deferring monitoring creates a deployment crunch and
incomplete observability.

### Do Not Ignore Score Regressions

Score regressions compound. A 2% coverage drop per module across ten modules
is a 20% project-level coverage loss. When a commit drops coverage, spikes
complexity, or triggers a new security finding, the scoring system flags it —
and the flag is addressed before the next section begins, not deferred.
Step 12 catches regressions; Step 13 records them per the Phase 3 Step 06
protocol; Step 15 verifies they were handled.

### Maintain Traceability

Every piece of generated code traces back through a chain: **code → task →
PRD → epic → milestone → module spec (M-NN) → Phase 4 architecture.** This
chain is maintained through semantic commits (each referencing the task and
the module-spec section it implements), structured artifacts, and the
ID-citation discipline. If traceability is lost — through unstructured
commits, ad-hoc changes, or bypassing the SDD pipeline — the verification
framework cannot confirm the implementation matches the specification.

### Use Semantic, Traceable Commits

Commits are structured so AI can track, summarize, and reason about the
change history. Each commit includes a clear description of what changed and
why, a reference to the task from the task list, a reference to the
module-spec section it implements, and any principle score changes it
introduces. Do not squash everything into "fixed stuff" or generate
meaningless commit messages — each commit is a meaningful, traceable unit of
change that later phases (testing, deployment, operations) consume.

### Honor the Safety Gates When Executing

Phase 5 runs tools (test runners, scanners, package managers) and writes
code. Before any risky or hard-to-reverse action — overwriting files,
running migrations, touching shared state — confirm and, where warranted,
back up first. Never print, log, or commit secrets, credentials, keys, or
tokens. Any step needing elevated privileges or touching sensitive resources
(credentials, production data, infrastructure config) is a STOP-and-ask
step, not something to route around. Prefer reversible actions over
destructive ones.

### The Scorecard Continues

The Principle Scorecard is a cross-phase living document. Phase 4 produced
v2.0. Phase 5 updates it to v3.x per the Phase 3 Step 06 protocol — v3.0 at
the first major implementation milestone, v3.x within and across subsequent
milestones. Regression detection against the v2.0 baseline (and prior v3.x
versions) continues. Step 13 produces the updates; the v2.0 baseline is
preserved, not overwritten.

### Backward Effects Have Three Paths

Phase 5 work can invalidate Phase 4 (a module spec proves ambiguous or
wrong), Phase 3 (a data-architecture decision creates a performance
problem), or Phase 2 (a cost estimate proves too optimistic). The Step 15
readiness review supports all three amendment paths. When alignment fails,
the gate produces a structured amendment package directing the practitioner
to the responsible prior phase. This is governance, not failure.

### Output Handling: Code to Files, Reports in Markdown

Most Phase 5 prompts produce markdown documents (plans, overviews, PRDs,
verification reports, scorecard). The one that produces code — Step 09 —
writes code, tests, and IaC to the appropriate repository files and produces
a structured **Implementation Report** as its markdown Output Format: what
was generated, the test/score/conformance results, the traceability links,
and the items requiring human review. The toolkit prompts themselves never
contain project source code — they instruct its generation.

---

## ID-Citation and Traceability Discipline

Phase 5's coherence depends on consistent ID citation across the hierarchy
and back to Phase 4.

| ID Series | Established / Source | Cited By |
|-----------|--------------------|----------|
| **CS-NN** (coding standards) | Phase 5 Step 02 | Step 09 generated code; Steps 10–11 reviews |
| **M-NN** (modules) | Phase 4 Step 07 | Steps 03–13 (the per-module pipeline) |
| **Milestone / Epic handles** | Phase 5 Steps 04–06 | PRDs, task lists, commits |
| **SIC-NN** (strategic contracts) | Phase 4 Step 07 | Step 03 scope; Step 09 interfaces; Step 10 conformance |
| **SP-NN** (shared patterns) | Phase 4 Step 02 | Step 02 coding standards; Step 09 code |
| **SEC-NN** (security controls) | Phase 4 Step 03 | Step 02 security patterns; Step 09 code; Steps 10–11 |
| **DA-NN** (data constraints) | Phase 4 Step 04 | Step 09 data-layer code; Step 10 conformance |
| **DOC-NN** (documentation) | Phase 4 Step 05 | Step 09 generated documentation |
| **GOV-NN** (governance) | Phase 4 Step 06 | Step 09 commits/review gates; Step 15 ownership |
| **H-NN** (observability hooks) | Phase 3 Step 07 | Step 09 monitoring instrumentation |
| **API contracts** | Phase 4 Steps 10–13 | Step 08 test derivation; Step 09 code; Steps 10, 14 conformance/contract tests |

A piece of generated code that cannot be traced to a task, a PRD, a module
spec, and a Phase 4 design decision is an untraceable artifact the
verification framework cannot validate.

---

## Cross-Phase Artifacts Phase 5 Produces and Maintains

### The Codebase

The working code, test suites, and infrastructure-as-code are the primary
Phase 5 outputs and the primary Phase 6 input. They conform to the Phase 4
specifications, pass the tests derived from them, and are traceable to them.

### The Test Suites

Unit, integration, property-based, and contract tests, generated from the
specifications (not from the implementation). Phase 6 audit builds on these.

### The Updated Principle Scorecard (Step 13)

The scorecard continues as a cross-phase living document. Phase 5 produces
v3.x. Phase 6 will produce v4.0, Phase 7 v5.0, per the Phase 3 Step 06
protocol. Regression detection across phases continues.

### Semantic Commit History

The traceable, AI-comprehensible commit history is an input resource for
later phases — Phase 6 traces failing tests to commits; Phase 7 summarizes
release changes; operations correlates production issues with deployed
commits.

### The ADRs

Phase 5 may produce implementation ADRs for decisions made during
implementation that were not settled in the architecture. These extend the
project's ADR series and do not silently supersede Phase 4 ADRs.

---

## Output Standards

All Phase 5 artifacts must meet these standards before Phase 6 handoff:

- [ ] Every module is implemented against its Phase 4 specification, with no
  specification section unimplemented or only partially implemented
- [ ] Every module meets or exceeds its coverage target; unit, integration,
  property-based, and contract tests are all in place
- [ ] All security scans pass; dependency vulnerabilities are resolved or
  documented as accepted risks; authorization enforcement matches SEC-NN
- [ ] Every module conforms to its API contract, data schema, and interface
  specification; conformance checks are automated and green
- [ ] For components designated for formal verification, the models are
  complete, verified, and engineer-reviewed
- [ ] All monitoring hooks (H-NN), logging, health checks, and tracing are
  implemented and tested
- [ ] Infrastructure-as-code (deployment, container, CI/CD definitions) is
  complete and tested
- [ ] AI-vs-AI review has run on every module with a separate configuration,
  and disagreements are arbitrated
- [ ] The Principle Scorecard is updated to v3.x with regressions documented
  and handled per the Step 06 protocol
- [ ] Every implementation artifact traces back to a specification; semantic
  commits are complete and linked to tasks
- [ ] No specification was silently re-architected; spec problems were routed
  through the amendment paths

---

## Common Pitfalls

**Generating without specifying tasks.**
Handing AI a module spec and saying "implement this" produces poor results.
The structural defense is the SDD pipeline (Steps 03–08) producing specific,
verifiable tasks before Step 09 generates any code.

**Ignoring score regressions.**
Score regressions compound across modules. The structural defense is Step 12
(health & scoring) flagging regressions per module/milestone, Step 13
recording them per the Step 06 protocol, and Step 15 verifying they were
handled.

**Treating AI output as final.**
Generated code is a first draft. The structural defense is the verification
stack — Step 09's in-loop tests/conformance, Step 10's correctness
verification, and Step 11's independent AI-vs-AI review — none of which can be
skipped without failing the Step 15 gate.

**Deferring monitoring implementation.**
Monitoring added before deployment is a crunch that produces incomplete
observability. The structural defense is the behavioral rule that H-NN hooks
are implemented and tested alongside features in Step 09, and verified in
Step 10.

**Losing traceability.**
Unstructured commits and ad-hoc changes break the chain from code to spec.
The structural defense is the ID-citation discipline, the semantic-commit
requirement in Step 09, and the traceability verification in Step 15.

**Re-architecting instead of amending.**
Coding around a spec gap diverges the implementation from the architecture.
The structural defense is Step 03's gap-surfacing scope confirmation and the
Step 15 amendment paths (Phase 4 / Phase 3 / Phase 2) — spec problems are
routed back, not worked around.

**Skipping the independent review.**
Running AI-vs-AI review with the same configuration that generated the code
is not an independent audit. The structural defense is Step 11's mandatory
separate-configuration requirement.

**Treating verification or scoring as optional for "simple" modules.**
Every module needs verification and scoring. What scales is the depth of the
tree, not the set of activities. The structural defense is the minimum
viable path designating Steps 03–13 mandatory per module, with only the
formal-verification section conditional.

---

## Connecting to Phase 6

Phase 5 hands off working, tested, scored, and verified code to Phase 6
(Testing & Audit). Phase 6 applies a different lens — independent testing,
security audits, performance validation, compliance verification, and
documentation review — and turns the Core Principles into pass/fail gates.

| Phase 6 Concern | Phase 5 Inputs Consumed |
|-----------------|------------------------|
| Independent test execution & audit | The test suites, the codebase |
| Security audit | Security scan results, SEC-NN-conformant code, the dependency audit |
| Performance validation | The performance benchmark results, the instrumented code |
| Specification conformance audit | The conformance check results, the API contracts |
| Formal verification review | The formal models and their checked properties (engineer review continues in Phase 6) |
| Compliance verification | The audit-logging implementation, the data-handling code |
| Documentation review | The generated documentation (DOC-NN) |
| Phase 6 scorecard update | Scorecard v3.x, the Phase 3 Step 06 protocol |

The Step 15 Readiness Review verifies each Phase 6 concern has its required
Phase 5 inputs before authorizing Phase 6. Phase 6 should not be used to
compensate for incomplete implementation — implementation must be solid
before audit begins.

Phase 6 is where formal verification models from Phase 5 receive their full
engineer review, where the Core Principles become pass/fail gates, and where
the system must demonstrate it meets the standards it was designed to
satisfy.

---

*Part of the AI-Centric Software Development Playbook —
Phase 5: Implementation*
*Framework reference: docs/part-07-implementation.md*
*See also: README.md in this directory for full tool set documentation*
