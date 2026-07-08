# Phase 5: Implementation — Tool Set
## AI-Centric Software Development Playbook

---

## Overview

This directory contains the complete tool set for **Phase 5: Implementation**
of the AI-Centric Software Development Playbook. Phase 5 transforms the Phase 4
architectural blueprint — module specifications, API contracts, and the
cross-cutting frameworks — into working, tested, scored, and verified code.

Implementation in an AI-centric workflow is fundamentally different from
traditional coding. Specifications are not aspirational references that drift
from reality — they are **authoritative**: AI generates code *from* the
specifications, tests verify code *against* them, and conformance checking
keeps them aligned. This only works if the specifications are precise, which is
exactly what Phase 4's discipline produced. Phase 5 is where the quality of
everything before becomes measurable — good specifications produce good code
quickly; vague specifications reintroduce the friction the framework was built
to eliminate.

The primary outputs of this phase are **working module implementations**, the
**test suites** (unit, integration, property-based, contract), the
**monitoring/observability implementations** and **infrastructure-as-code**,
the **continuous scoring data** that feeds the Principle Scorecard, and the
updated **Principle Scorecard (v3.x)**. The defining activity is the
implementation feedback loop — **generate → test → score → verify → refine** —
run for every task in every module.

The toolkit's planning-and-execution spine is adapted from a proven SDD command
pipeline (project plan → module → milestone → epic → PRD → tasks → execution),
extended with the Phase 5 activities the article calls for: a per-module scope
confirmation, dedicated correctness verification, independent AI-vs-AI review,
continuous scoring, and a readiness gate with three amendment paths.

---

## Framework Context

This tool set is part of the [AI-Centric Software Development
Playbook](../../../README.md), a practitioner's framework for small teams
(1–5 people) that use AI tools to deliver what large organizations once
required.

### Phase 5 Differs From Phases 1–4 in Character

| Dimension | Phase 1 | Phase 2 | Phase 3 | Phase 4 | Phase 5 |
|-----------|---------|---------|---------|---------|---------|
| Primary work | Gathering | Committing | Locking direction | Specifying the blueprint | **Generating verified code from the blueprint** |
| AI role | Research strategist | Analytical partner | Design analyst | Architecture specifier | **Implementation generator + verifier** |
| Number of prompts | 6 | 7 | 9 | 16 | **15** |
| SDD structure | One cycle | One cycle | One cycle | Nested cycles | **Per-module nested cycle with a tight generate→verify loop** |
| Primary artifact | Markdown report | Markdown analyses | Markdown direction + ADRs | Markdown specifications | **Code, tests, IaC + markdown reports** |
| Cross-phase living artifacts | None | Stack ADR | Scorecard v1.0 | Scorecard v2.0 + module specs | **Scorecard v3.x + the codebase** |
| Backward effects | None | None | Phase 2 amendment | Phase 3 + Phase 2 amendment | **Phase 4 + Phase 3 + Phase 2 amendment** |
| Gate outcomes | 3 | 3 | 4 | 5 | **6** |

Phase 5 introduces five things no prior phase had:

**It produces code, not specifications.** The "no implementation content"
boundary that governed Phases 1–4 inverts: Phase 5 *is* implementation. The new
boundary is **implement from the specification; do not re-architect.**

**Specifications are authoritative.** AI generates from them, tests verify
against them, conformance keeps them aligned. The precision Phase 4 invested in
is returned here as code that is largely correct on first generation.

**The feedback loop is the tightest in the framework.** Generate → test →
score → verify → refine runs for every task; the toolkit keeps it disciplined
rather than an ad-hoc negotiation.

**Implementation is per-module and parallel-eligible.** Each module is built
from its own spec through its own pipeline; modules with no dependency between
them (per the Phase 4 dependency graph) build in parallel — that is what
"modular" means.

**It can invalidate Phase 4, Phase 3, OR Phase 2.** A module spec proves
ambiguous when coded (Phase 4); a data decision creates a performance problem
(Phase 3); effort proves the cost model optimistic (Phase 2). The gate supports
all three amendment paths.

### The Six Core Principles in Phase 5

Implementation is where principles become measurable reality rather than scored
projections.

| Principle | Phase 5 Application |
|-----------|---------------------|
| **Security** | Continuous scanning on every commit; authz enforcement matching SEC-NN; AI-vs-AI security review. |
| **Maintainability** | Coverage scoring, documentation generation, code-quality metrics — at module and project level. |
| **Economics** | Actual development effort tracked against the Phase 2/4 estimates; deviations flagged. |
| **Operations** | Monitoring, logging, health checks, tracing built alongside features and verified against H-NN. |
| **Scoring & Metrics** | Fully operational — automated metrics every commit feed the continuously updated scorecard (v3.x). |
| **Correctness Verification** | Fully operational — conformance on every build, property-based testing, formal verification for critical paths, AI-vs-AI review. |

### The Per-Module Nested SDD Cycle

Phase 5 runs the SDD cycle at the module level, decomposed across a hierarchy:
**Project → Module → Milestone → Epic → PRD → Task → execution.**

| SDD Step | Phase 5 Activity | Prompt(s) |
|----------|------------------|-----------|
| **Specify** | Confirm module scope; surface spec gaps | Step 03 |
| **Plan** | Decompose into milestones and epics | Steps 04 → 05 → 06 |
| **Detail** | Implementation PRD per epic | Step 07 |
| **Task** | Concrete, verifiable task list | Step 08 |
| **Implement** | Generate → test → score → verify → refine | Step 09, then Steps 10–11 |

Above the per-task loop sit two strategic loops: **module-level feedback**
(Steps 10–13, per module) and **project-level feedback** (Stage 3). When a loop
reveals a problem tracing to an earlier phase, the response is the amendment
cycle (Step 15), not a silent workaround.

---

## Directory Contents

```
phase-05-implementation/
├── README.md                                          ← You are here
├── implementation.instructions.md                     ← Load as project context
│
│   ═══ STAGE 1 — PRE-IMPLEMENTATION SETUP (project-level, once) ═══
├── step-01-implementation-project-plan.prompt.md       ← organizes the build by module; scopes modules for parallel dev
├── step-02-coding-standards-and-conventions.prompt.md  ← CS-NN; the reusable coding "skill"
│
│   ═══ STAGE 2 — PER-MODULE IMPLEMENTATION (per module; parallel across modules) ═══
├── step-03-module-scope-confirmation.prompt.md         ← Specify; surfaces spec gaps before coding
├── step-04-module-breakout.prompt.md                   ← module → milestones
├── step-05-milestone-breakout.prompt.md                ← milestone → epics
├── step-06-epic-breakout.prompt.md                     ← epic overview (PRD input)
├── step-07-implementation-prd.prompt.md                ← per epic; the detail bridge
├── step-08-task-list-generation.prompt.md              ← per epic; code + spec-derived test tasks
├── step-09-implement-loop.prompt.md                    ← per epic; generate→test→score→refine; code to files + Implementation Report
├── step-10-correctness-verification.prompt.md          ← per module; conformance + property + formal[conditional]
├── step-11-ai-vs-ai-review.prompt.md                   ← per module; SEPARATE AI config
├── step-12-implementation-health-and-scoring.prompt.md ← per module/milestone; metrics + regression flags
├── step-13-scorecard-update.prompt.md                  ← per milestone + consolidation; Scorecard v3.x
│
│   ═══ STAGE 3 — POST-IMPLEMENTATION INTEGRATION (project-level, once) ═══
├── step-14-cross-module-integration.prompt.md          ← integration + contract testing across boundaries
└── step-15-phase-5-readiness-review.prompt.md          ← THE GATE; 6 outcomes, 3 amendment paths
```

**15 step prompts + instructions + README = 17 files.**

---

## File Descriptions

### `implementation.instructions.md`
**Type:** Instructions file (load once as persistent project context)

The overarching context for any AI assistant in Phase 5. Contains the framework
orientation, the five-phase comparison, the per-module nested SDD cycle, the six
principles applied to Phase 5, the three-stage structure, the authoritative
dependency graph, the minimum viable path, the ID-citation/traceability
discipline, the behavioral guidelines (including the inverted
implement-don't-re-architect boundary and the code-to-files output handling),
the output standards, the common pitfalls, and the Phase 6 handoff.

### Stage 1 — Pre-Implementation Setup

#### `step-01-implementation-project-plan.prompt.md` — Action Prompt
The plan-of-record. Ingests the Phase 4 blueprint, organizes the build by
module, and scopes modules for parallel development per the Phase 4 dependency
graph. **Key decision:** modules that can't be built independently aren't truly
modular — a dependency graph that admits little parallelism is flagged as a
possible Phase 4 boundary problem.

#### `step-02-coding-standards-and-conventions.prompt.md` — Action Prompt (CS-NN)
The reusable coding "skill" every code-generation run consumes. Elaborates the
Phase 4 SP-NN/SEC-NN architecture patterns into concrete, code-level
conventions for the committed stack. **Key decision:** AI-proposes/
practitioner-calibrates; every convention cites the SP-NN/SEC-NN it elaborates
so it can't silently contradict the architecture.

### Stage 2 — Per-Module Implementation

#### `step-03-module-scope-confirmation.prompt.md` — Evaluation + Action (per module)
The article's "Specify — Confirm the Module Scope." **Key decision:** it
*dispositions* every spec gap as resolve-now or route-to-Phase-4-amendment —
never absorbing a structural gap silently — and plans dependency mocking
(keyed to SIC-NN) so parallel module builds are possible.

#### `step-04-module-breakout.prompt.md` · `step-05-milestone-breakout.prompt.md` · `step-06-epic-breakout.prompt.md` — Action Prompts (the breakout family)
Decompose Module → Milestone → Epic, mapping the article's implementation
sections (data models, business logic, API, auth, integration, tests,
monitoring, IaC) to epics. **Key decision:** each breakout **reconciles upward**
— detailing a level can surgically edit the level above and report it (the
in-hierarchy feedback mechanism). Step 06 is the traceability seam where
concrete constraint IDs (contract ops, SEC/DA/H/CS) attach to an epic.

#### `step-07-implementation-prd.prompt.md` — Action Prompt (per epic)
The article's "Detail." Bridges the spec to the task list: components with I/O
types derived from the spec, invariants, error handling per failure mode,
logging/metrics, test properties, formal-verification targets, principle
requirements. **Key decision:** the anti-"generate-without-specifying-tasks"
defense — invariants flow into property tests.

#### `step-08-task-list-generation.prompt.md` — Action Prompt (per epic)
The article's "Task." Produces the ordered, safety-gated task list — **code
tasks interleaved with spec-derived test tasks** — the final specification
before generation. **Key decision:** tests derived from the spec, not the
implementation; the df3ndr safety/validate/record spine is baked in.

#### `step-09-implement-loop.prompt.md` — Action Prompt, code-producing (per epic)
The core loop: generate → test → score → conformance → refine, one sub-task at
a time, with semantic commits. **Key decision:** the toolkit's one code-producing
prompt — code goes to repo files, the markdown Output Format is an
**Implementation Report** that must *show the loop ran* (refinement iterations);
surfaced spec gaps pause-and-route rather than being coded around.

#### `step-10-correctness-verification.prompt.md` — Evaluation + Action (per module)
The full conformance audit (vs the Phase 4 contracts/schemas), property-test
review, and **formal verification for designated critical components**
(conditional). **Key decision:** formal verification always ends in
engineer-review items for the model; deviations are attributed and routed (code
→ Step 09, spec → Step 03/15), never resolved by editing a contract to match
the code.

#### `step-11-ai-vs-ai-review.prompt.md` — Evaluation Prompt, separate config (per module)
The independent audit. **Key decision:** *must* run with a different model/
configuration and without the generating AI's reasoning; disagreements route to
practitioner arbitration; a recorded-limitation fallback applies if a different
model isn't available.

#### `step-12-implementation-health-and-scoring.prompt.md` — Evaluation + Action (per module/milestone)
Collects metrics, compares to the v2.0 baseline, flags regressions per the
Step 06 thresholds, and tracks effort-vs-estimate (the economics signal).
**Key decision:** the continuous-signal half of the scoring split — not the
scorecard artifact.

#### `step-13-scorecard-update.prompt.md` — Action Prompt (per milestone + consolidation)
Produces **Scorecard v3.x** per the Phase 3 Step 06 protocol, consuming the
Step 12 signals. **Key decision:** mirrors Phase 4's Step 14 but on the
per-milestone cadence; preserves the five-element format and prior versions so
cross-phase regression detection holds.

### Stage 3 — Post-Implementation Integration

#### `step-14-cross-module-integration.prompt.md` — Evaluation + Action
The project-level feedback layer. Contract-tests every dependency-graph
boundary (mutual expectations, not just per-module conformance), replaces mocks
with real modules, and hunts **systemic patterns** across modules. **Key
decision:** a recurring cross-module issue signals a Phase 4/Phase 3 problem,
not a point fix.

#### `step-15-phase-5-readiness-review.prompt.md` — Evaluation Prompt (Gate)
The gate. **Key decisions:** **six outcomes, three amendment paths** (Phase 4 /
Phase 3 / Phase 2), each with a specific package and cascade; tiered override
authority with the three amendment-path overrides at the top; a Phase 6 Handoff
Summary structured for direct consumption.

---

## The Minimum Viable Path

Fifteen prompts is the full toolkit. What scales in Phase 5 is the **repetition
count** across the hierarchy and the **depth** of each module's decomposition —
not the set of prompts.

### Mandatory (every Phase 5 project)

All fifteen steps are mandatory. Repetition across the hierarchy:

| Step | Repetition |
|------|-----------|
| 01–02 | Once (project-level) |
| 03–04 | Once per module |
| 05 | Once per milestone (per module) |
| 06–09 | Once per epic |
| 10–13 | Once per module (12–13 may also run per milestone and consolidate) |
| 14–15 | Once (project-level) |

### The One Conditional Element

| Element | Run When |
|---------|----------|
| Step 10 formal-verification section | Only for components Phase 4 designated for formal verification (financial calc, auth logic, state machines, concurrency). Modules with none complete Step 10's conformance and property-review sections and skip it. |

### Scaling Down

A small module has a single milestone and a few epics — the hierarchy collapses
but is still traversed. There is no "lightweight" mode: a one-module project
still confirms scope, plans, details, tasks, implements, verifies, reviews,
scores, integrates, and gates. Skipping verification or scoring for a "simple"
module produces exactly the score-regression and traceability gaps the pitfalls
warn against.

---

## How to Use This Tool Set

### Prerequisites

1. Confirm the [Phase 4 toolkit](../phase-04-architecture-modular-design/README.md)
   is complete with a passing Step 16 Readiness Review (READY or CONDITIONALLY
   READY). Phase 5 cannot responsibly begin on an unauthorized Phase 4 handoff.
2. Load `implementation.instructions.md` as project-level instructions in your
   AI environment, and keep the Step 02 coding standards available as context
   once produced.

### Execution Order — Three Stages, Per-Module Pipeline

```
Phase 4 Package (Module Specs M-NN, API Contracts, frameworks, Scorecard v2.0,
                 Step 16 Phase 5 Handoff Summary; Phase 3 H-NN hooks)
   │
   ▼
═══ STAGE 1: PRE-IMPLEMENTATION SETUP (project-level, once) ═══
Step 01 → Step 02
   │
   ▼
═══ STAGE 2: PER-MODULE IMPLEMENTATION ═══
   │  for each module M-NN in dependency order; independent modules in parallel
   ▼
Step 03 (scope) ── gap? → Step 15 Phase 4 amendment
   ▼
Step 04 (→ milestones) → Step 05 (→ epics) → Step 06 (epic overview)
   ▼
Step 07 (PRD) → Step 08 (tasks) → Step 09 (implement loop)
   ▼
Step 10 (verify) → Step 11 (AI-vs-AI) → Step 12 (score) → Step 13 (scorecard v3.x)
   │
   ▼ (all modules complete)
═══ STAGE 3: POST-IMPLEMENTATION INTEGRATION (project-level, once) ═══
Step 14 (integration + contract testing)
   ▼
Step 15 (the gate)
   │
   ┌──────────┬──────────┬──────────┬──────────┬──────────┐
   ▼          ▼          ▼          ▼          ▼          ▼
Phase 6    Phase 5    Phase 4    Phase 3    Phase 2   (CONDITIONALLY
Authorized Internal   Amendment  Amendment  Amendment   READY — partial
(READY)    Remediation                                  Phase 6 start)
```

### Parallelism Opportunities

- **Modules run in parallel** where the Phase 4 dependency graph permits;
  dependencies are mocked/stubbed (decided in Step 03) until available.
- **Within a module, execution is serial** down the hierarchy (depth-first:
  a milestone's epics complete before the next milestone), reconciling upward.
- **Steps 01–02** precede all module work; **Steps 14–15** follow all modules.

### Running Each Prompt

For each step: open a new AI session with `implementation.instructions.md`
loaded; paste the required inputs (see the prompt's metadata table) above the
kickoff line — for per-module/epic prompts, name the specific module/epic;
answer the clarifying questions (presence check first); review the output
against the prompt's evaluation checklist. Step 09 additionally needs
repository and tool access; Step 11 needs a *different* model/configuration.

### Iterating

- **Step 03 surfaces a structural spec gap** → Step 15 Phase 4 amendment before
  coding the module.
- **Step 09 hits a spec ambiguity** → pause, route to Step 03/Step 15; don't
  code around it.
- **Step 10/11 finds deviations/issues** → route to Step 09 (code) or Step
  03/15 (spec); re-verify.
- **Step 12 flags a regression** → remediate or document acceptance per Step 06.
- **Step 14 finds an integration/systemic issue** → Step 09 or Step 15.
- **Step 15 returns a NOT READY variant** → run the corresponding amendment
  cycle (below).

---

## The Three Amendment Cycles

Phase 5 is the deepest backward-reaching gate. Step 15 evaluates Phase 4,
Phase 3, and Phase 2 alignment as separate dimensions and produces a distinct,
structured amendment package for each.

- **Phase 4 amendment** — implementation reveals a module spec, contract, or
  framework was wrong/ambiguous. Re-run the relevant Phase 4 prompts and Step
  16, then the affected Phase 5 steps and Step 15.
- **Phase 3 amendment** — implementation reveals a data-architecture or
  performance decision was wrong. Cascades through Phase 4: re-run Phase 3
  (Step 09), then Phase 4 (Step 16), then Phase 5 (Step 15).
- **Phase 2 amendment** — actual effort proves the cost model optimistic, or a
  benchmark proves unachievable. The deepest cascade: Phase 2 (Step 07) →
  Phase 3 (Step 09) → Phase 4 (Step 16) → Phase 5 (Step 15).

All three are governance, not failure — the framework's defense against
shipping on a foundation it has flagged as invalid.

---

## The Readiness Review

The Step 15 gate makes the Phase 5 handoff trustworthy as Phase 6 input.

| Gate Dimension | What It Asks |
|---------------|--------------|
| Per-principle gates | Does each Core Principle meet its Phase 5 pass criteria? |
| Per-artifact completeness | Did each Phase 5 artifact meet its checklist? |
| Cross-artifact consistency & traceability | Is the implementation consistent and traceable (code → task → PRD → spec)? |
| Phase 4 alignment | Did implementation invalidate an architecture decision? |
| Phase 3 alignment | Did implementation invalidate an analysis/data decision? |
| Phase 2 alignment | Did implementation invalidate a cost/business commitment? |
| Phase 6 input completeness | Does each Phase 6 concern have its inputs? |

### The Six Determination Outcomes

| Status | Meaning | Action |
|--------|---------|--------|
| **READY** | All checks pass | Phase 6 may begin |
| **CONDITIONALLY READY** | Conditionals with remediation | Phase 6 may begin unblocked work |
| **NOT READY (Phase 5 gaps)** | Blocking gaps in Phase 5 work | Remediate within Phase 5 |
| **NOT READY (Phase 4 amendment)** | Architecture alignment failure | Phase 4 amendment cycle |
| **NOT READY (Phase 3 amendment)** | Analysis/data alignment failure | Phase 3 amendment cycle (cascades) |
| **NOT READY (Phase 2 amendment)** | Cost/business alignment failure | Phase 2 amendment cycle (deepest cascade) |

---

## ID-Citation and Traceability Discipline

Phase 5's coherence depends on consistent ID citation across the hierarchy and
back to Phase 4.

| ID Series | Established / Source | Cited By |
|-----------|--------------------|----------|
| **CS-NN** (coding standards) | Phase 5 Step 02 | Step 09 code; Steps 10–11 reviews |
| **M-NN** (modules) | Phase 4 Step 07 | Steps 03–13 (the per-module pipeline) |
| **Milestone / Epic handles** (M-NN-MS\<m\>-E\<e\>) | Phase 5 Steps 04–06 | PRDs, task lists, commits |
| **SIC-NN** (strategic contracts) | Phase 4 Step 07 | Step 03 scope; Step 09 interfaces; Steps 10, 14 conformance |
| **SP-NN / SEC-NN / DA-NN / DOC-NN / GOV-NN** | Phase 4 Steps 02–06 | Step 02 standards; Step 09 code; Steps 10–11 verification |
| **H-NN** (observability hooks) | Phase 3 Step 07 | Step 09 monitoring instrumentation |
| **API contracts** | Phase 4 Steps 10–13 | Step 08 test derivation; Step 09 code; Steps 10, 14 |

The traceability chain — **code → task → PRD → epic → milestone → module spec
(M-NN) → Phase 4 architecture** — is the thread the verification framework
depends on. The "Losing Traceability" pitfall is defended by the semantic-commit
convention (CS-NN), the breakout reconciliation, and the Step 15 traceability
check.

---

## Cross-Phase Living Documents

- **The codebase, test suites, and semantic commit history (Step 09)** — the
  primary Phase 6 input; the commit history is an AI-comprehensible resource
  for later phases.
- **The Principle Scorecard (Step 13)** — continues as v3.x; Phase 6 produces
  v4.0, Phase 7 v5.0, per the Step 06 protocol. Regression detection across
  phases continues.
- **The ADRs** — Phase 5 may add implementation ADRs; they extend the series
  and do not silently supersede Phase 4 ADRs.

---

## Common Pitfalls

**Generating without specifying tasks.** Handing AI a module spec and saying
"implement this" produces poor results. *Defense:* the SDD pipeline (Steps
03–08) produces specific, verifiable tasks before Step 09 generates code.

**Ignoring score regressions.** Regressions compound across modules. *Defense:*
Step 12 flags them per module, Step 13 records them per Step 06, Step 15 verifies
they were handled.

**Treating AI output as final.** Generated code is a first draft. *Defense:* the
verification stack — Step 09's in-loop checks, Step 10 verification, Step 11
independent review — none skippable without failing the gate.

**Deferring monitoring implementation.** *Defense:* H-NN hooks are built and
tested in Step 09 and verified in Step 10, not deferred to deployment.

**Losing traceability.** *Defense:* the ID-citation discipline, the
semantic-commit convention, and the Step 15 traceability check.

**Re-architecting instead of amending.** Coding around a spec gap diverges code
from architecture. *Defense:* Step 03's gap-surfacing and the Step 15 amendment
paths — spec problems are routed back, not worked around.

**Skipping the independent review.** Running AI-vs-AI with the generating config
isn't an independent audit. *Defense:* Step 11's mandatory separate-configuration
requirement.

**Treating verification or scoring as optional for "simple" modules.** *Defense:*
the minimum viable path designates Steps 03–13 mandatory per module, with only
the formal-verification section conditional.

---

## Connecting to Phase 6

Phase 5 hands off working, tested, scored, verified code to Phase 6 (Testing &
Audit), which applies an independent lens — independent testing, security
audits, performance validation, compliance verification, documentation review —
and turns the Core Principles into pass/fail gates.

| Phase 6 Concern | Phase 5 Inputs Consumed |
|-----------------|------------------------|
| Independent test execution & audit | Test suites, the codebase |
| Security audit | Scan results, SEC-NN-conformant code, dependency audit |
| Performance validation | Benchmark results, instrumented code |
| Specification conformance audit | Conformance results, API contracts |
| Formal-verification review | Formal models + checked properties |
| Compliance verification | Audit-logging implementation, data-handling code |
| Documentation review | Generated documentation (DOC-NN) |
| Phase 6 scorecard update | Scorecard v3.x, the Phase 3 Step 06 protocol |

The Step 15 Readiness Review verifies each Phase 6 concern has its required
Phase 5 inputs before authorizing Phase 6. Phase 6 should not be used to
compensate for incomplete implementation — implementation must be solid before
audit begins. Phase 6 is where formal-verification models receive their full
engineer review, where the Core Principles become pass/fail gates, and where the
system must demonstrate it meets the standards it was designed to satisfy.

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | [date] | Initial release — instructions file plus fifteen prompts |

---

## Related Resources

- [AI-Centric Software Development Playbook — Full Series](../../../README.md)
- [Part 1 — Core Principles](../../../docs/part-01-core-principles.md)
- [Part 2 — Building Your Toolkit](../../../docs/part-02-building-your-toolkit.md)
- [Part 7 — Phase 5: Implementation](../../../docs/part-07-implementation.md)
- [Phase 1 Tool Set](../phase-01-information-gathering-toolset/README.md)
- [Phase 2 Tool Set](../phase-02-analysis-stack-selection/README.md)
- [Phase 3 Tool Set](../phase-03-design-technical-analysis/README.md)
- [Phase 4 Tool Set](../phase-04-architecture-modular-design/README.md)
- [Part 8 — Phase 6: Testing & Audit](../../../docs/part-08-testing-audit.md) *(the next phase)*

---

*Part of the AI-Centric Software Development Playbook*
*This tool set is a living artifact — it will be refined as the methodology
matures and use in practice reveals improvements.*
