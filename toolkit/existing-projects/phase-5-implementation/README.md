# Phase 5 — Implementation Tool Set (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Purpose

This tool set supports **Phase 5: Implementation** when applied to an
**existing codebase** that has completed Phases 1 (Information
Gathering), 2 (Analysis & Improvement Planning), 3 (Design & Technical
Analysis), and 4 (Architecture & Modular Design).

Phase 5's job here is **landing the specified changes inside working
code** — generating implementations from the Phase 4 module change
specifications and formal contracts, keeping the existing test suite
green at every increment, verifying every change against its
specification, running an independent AI-vs-AI review, scoring
continuously, and measuring actual effort against the estimates the
track has carried since Phase 2. Phase 6 (Testing & Audit) then applies
an independent lens to the result.

This is the existing-projects variant of Phase 5. The greenfield variant
(`toolkit/new-projects/phase-05-implementation/`) constructs modules from
scratch through a module → milestone → epic breakout hierarchy. The
existing-projects variant is different — the codebase, its conventions,
its tests, and its release discipline already exist. This toolkit
reconciles with them (provenance-tagged coding standards, semantic
commits inside the existing commit format, landing through the existing
pipeline), implements **deltas** whose depth follows each module's
disposition (NEW / CHANGED / UNTOUCHED / RETIRED), and treats the
regression surface as a first-class gate inside the implement loop.

> **Companion Skill.** This toolkit has a companion **AI-Centric
> Playbook Skill** at `skills/ai-centric-playbook/`. Load it when a
> decision benefits from depth on a Core Principle, the SDD mechanics, or
> the building-blocks model — the instructions file explains when.

---

## When to Use This Tool Set

Use this tool set when:

- The subject is an existing codebase, not a greenfield project
- Phase 4 is complete with an Architecture Blueprint Bundle whose Step 12
  readiness determination is READY or CONDITIONALLY READY
- Any Phase 4 amendment cycles (Blueprint §8/§9 packages) are resolved
- The practitioner has write access to the subject repository (or is
  prepared to run patch-mediated mode — see the instructions file's code
  access requirement)
- The team is ready to generate, test, verify, review, score, and land
  the specified changes

Do *not* use this tool set when:

- The project is greenfield — use the greenfield Phase 5 toolkit
- Phase 4 has not produced an Architecture Blueprint Bundle — run Phase 4
  first
- The Phase 4 gate returned NOT READY in any variant — resolve it first
- The intent is to change what Phase 4 specified — that routes through
  the amendment channels, not through implementation improvisation

---

## Tool Set Files

| File | Type | Purpose |
|------|------|---------|
| `implementation.existing-project.instructions.md` | Load-once context | Three shifts from the greenfield variant; per-module SDD cycle (Module → Work Package → Task); six principles applied; scorecard inheritance; four feedback channels; CS/WP/T ID series + traceability chain; code-access requirement; safety gates; behavioral rules; output standards; dependency graph; common pitfalls. The structural document — every step prompt references back to it. |
| `step-00-building-block-discovery.prompt.md` | Action prompt (with brief confirmation) | Capability inventory — living document (§7 amendments). Phase 5 carries the heaviest tooling dependency in the track: write access, test execution, scanners, CI access, and a **separate AI configuration for Step 07** are inventoried here. |
| `step-01-phase-4-input-validation.prompt.md` | Interview → Action | Validates the Architecture Blueprint Bundle (and the Phase 3/2/1 context behind it); hard blocking checks on the Phase 4 gate determination and unresolved amendment packages; Validation Gap Register with the two-scope split (Channel 1). |
| `step-02-implementation-plan-and-landing-sequence.prompt.md` | Action prompt (with clarification) | Module implementation order and parallelism from the Impact Map; landing discipline reconciled with the existing branch/release conventions; coordinated-landing cohorts; mock/stub decisions; the regression gate definition; effort-tracking method; the run's minimum viable path. |
| `step-03-coding-standards-and-conventions.prompt.md` | Action prompt (with clarification) | CS-NN standards codified from the codebase's actual conventions (style, lint, tests, commits, docs) plus the Phase 4 SP-NN patterns — provenance-tagged; produces the generation-session preamble every Step 05 session consumes. |
| `step-04-module-implementation-plan.prompt.md` | Parameterized action prompt (runs once per NEW/CHANGED module) | The module-level SDD pipeline in one session: scope confirmation against the change specification (spec gaps surface **before** coding), work-package breakdown (WP-NN) with regression checkpoints, implementation PRD, and the task list (M-NN.WP-N.T-NN) with acceptance criteria. |
| `step-05-module-implement-loop.prompt.md` | Parameterized action prompt (iterative per task) | The core loop: generate → run new tests **and the regression suite** → score → check conformance against the formal contracts and change spec → refine. Semantic commits inside the existing conventions; effort actuals per task; touchpoints built alongside features. Writes code to the repository; outputs the Implementation Report. |
| `step-06-module-correctness-verification.prompt.md` | Evaluation prompt (per module) | Conformance audit, preserved-invariant and property verification, regression-surface confirmation, formal verification (conditional on Phase 4 designation), and Phase 3 §3 verification-instrument readiness. Determination: VERIFIED / GAPS FOUND. |
| `step-07-ai-vs-ai-review.prompt.md` | Evaluation prompt (per module; **separate AI configuration**) | Independent audit of the generated changes — logic, security, spec drift, performance, maintainability — with a configuration-independence attestation and a practitioner arbitration record. Determination: CLEAR / FINDINGS OPEN. |
| `step-08-module-health-scoring-and-effort-actuals.prompt.md` | Action + Evaluation (per module) | Metrics summary, regression flags vs the Phase 4 baseline, the per-module scorecard contribution, and the three-quantity effort actuals vs the Phase 4 §9 estimate with deviation analysis (calibration signal vs amendment candidate). |
| `step-09-integration-and-regression-validation.prompt.md` | Evaluation prompt (project-level; per cohort where cohorts land separately) | Cohort assembly per the Step 02 plan, cross-module contract tests, the full regression suite, integration with UNTOUCHED modules, end-to-end validation against the Phase 1 measured baselines. Determination: INTEGRATED / ISSUES FOUND. |
| `step-10-implementation-synthesis-and-readiness-review.prompt.md` | Action + Evaluation (synthesis + the gate) | The Implementation Bundle, the scorecard refresh (inherited weights, Phase 4 baseline, target distribution check), the cost/capacity/calibration consolidation (BELIEVED → ESTIMATED multiplier table), the six-outcome readiness determination, and the Phase 4 / Phase 3 / Phase 2 Amendment Packages when channels fire. |
| `dogfooding-observations.md` | Living log | Captured during Phase 5 cycles for end-of-phase review. |

---

## Recommended Sequence

```
┌────────────────────────────────────────────────────────────────────┐
│ Phase 4 Architecture Blueprint Bundle (gate READY or CONDITIONALLY │
│ READY; §8/§9 amendment packages resolved)                          │
│ + Phase 3 Bundle (§2 cohorts, §3 instruments)                      │
│ + Phase 2 Improvement Plan + Phase 1 measured baselines            │
└────────────────────────────────────────────────────────────────────┘
                              │
                              ▼
            ═══ STAGE 1: PRE-IMPLEMENTATION SETUP ═══
                              │
                              ▼
                  ┌───────────────────────┐
                  │ Step 00: Building     │──→ Toolset Augmentation
                  │ Block Discovery       │    Document (living; incl.
                  └───────────┬───────────┘    separate AI config for 07)
                              ▼
                  ┌───────────────────────┐
                  │ Step 01: Phase 4      │──→ Validation Gap Register
                  │ Input Validation      │    (two-scope split)
                  └───────────┬───────────┘
                  ┌───────────┴────────────────────┐
                  ▼                                ▼
        ┌─────────────────────┐    ┌───────────────────────────┐
        │ Phase 5 local gaps  │    │ Upstream toolkit gaps →   │
        │ → continue Phase 5  │    │ queue for Phase 4 (or     │
        └─────────────────────┘    │ earlier) toolkit revision │
                              │    │ (Channel 1 firing)        │
                              ▼    └───────────────────────────┘
                  ┌───────────────────────┐
                  │ Step 02: Implementation│──→ Module order, landing
                  │ Plan & Landing Sequence│    discipline, cohorts,
                  └───────────┬───────────┘    regression gate, MVP
                              ▼
                  ┌───────────────────────┐
                  │ Step 03: Coding       │──→ CS-NN register +
                  │ Standards & Conventions│    generation preamble
                  └───────────┬───────────┘
                              ▼
        ═══ STAGE 2: PER-MODULE CHANGE IMPLEMENTATION ═══
              (per NEW/CHANGED module, in Step 02 order;
               independent modules in parallel sessions)
                              │
                              ▼
                  ┌───────────────────────┐
                  │ Step 04: Module       │── spec gap? ──► Step 10
                  │ Implementation Plan   │    (Channel 2 candidate)
                  └───────────┬───────────┘
                              ▼
                  ┌───────────────────────┐
                  │ Step 05: Implement    │ ◄── iterates per task;
                  │ Loop (+ regression    │     code lands in repo;
                  │ suite in-loop)        │     Implementation Report
                  └───────────┬───────────┘
                       ┌──────┴──────┐
                       ▼             ▼
            ┌─────────────────┐ ┌─────────────────┐
            │ Step 06: Module │ │ Step 07: AI-vs- │  (independent
            │ Correctness     │ │ AI Review       │   lenses; may run
            │ Verification    │ │ (separate config)│  in parallel)
            └────────┬────────┘ └────────┬────────┘
                     └─────────┬─────────┘
                               ▼
                  ┌───────────────────────┐
                  │ Step 08: Module Health,│──→ per-module scorecard
                  │ Scoring & Effort       │    contribution + effort
                  │ Actuals                │    actuals vs estimate
                  └───────────┬───────────┘
                              ▼ (all modules / a cohort complete)
              ═══ STAGE 3: INTEGRATION & HANDOFF ═══
                              │
                              ▼
                  ┌───────────────────────┐
                  │ Step 09: Integration &│──→ INTEGRATED /
                  │ Regression Validation │    ISSUES FOUND
                  └───────────┬───────────┘
                              ▼
                  ┌───────────────────────┐
                  │ Step 10: Implementation│──→ Implementation Bundle +
                  │ Synthesis & Readiness │    scorecard refresh +
                  │ Review (the gate)     │    six-outcome gate
                  └───────────┬───────────┘
      ┌─────────┬─────────────┼──────────────┬──────────────┐
      ▼         ▼             ▼              ▼              ▼
 ┌─────────┐┌─────────┐┌─────────────┐┌─────────────┐┌─────────────┐
 │ READY / ││NOT READY││ NOT READY — ││ NOT READY — ││ NOT READY — │
 │ CONDIT- ││(Phase 5 ││ Phase 4     ││ Phase 3     ││ Phase 2     │
 │ IONALLY ││ gaps) → ││ amendment   ││ amendment   ││ amendment   │
 │ READY → ││remediate││ (Channel 2) ││ (Channel 3, ││ (Channel 4, │
 │ Phase 6 ││+ re-gate││             ││ cascades)   ││ cascades)   │
 └─────────┘└─────────┘└─────────────┘└─────────────┘└─────────────┘
```

The diagram shows all **four Phase 5 feedback channels**: Channel 1
(upstream toolkit gaps — non-blocking, queued for toolkit revision) and
Channels 2–4 (run amendments to Phase 4, Phase 3, or Phase 2 — blocking,
with cascading re-entry for the deeper paths).

---

## The Minimum Viable Path

All eleven steps are mandatory. What scales is repetition and depth:

| Step | Repetition |
|------|-----------|
| 00–03 | Once (project-level) |
| 04–08 | Once per NEW/CHANGED module (N from the Phase 4 Impact Map) |
| 09 | Once (or per coordinated-landing cohort) |
| 10 | Once |

The one conditional element: **Step 06's formal-verification section**
runs only for components Phase 4 designated. There is no "lightweight"
mode — a single-module change surface still confirms scope, plans,
implements, verifies, reviews independently, scores, integrates, and
gates. Skipping verification or scoring for a "simple" change produces
exactly the regression and traceability gaps the pitfalls warn against.

---

## MCP Server Recommendations

Phase 5 carries the heaviest tooling dependency in the track:

- **Direct write access to the repository** (filesystem MCP, Claude
  Code, IDE integration) — required for the Step 05 loop (or explicit
  patch-mediated mode, which is slower and recorded at Step 00).
- **Test execution** — running the new tests and the regression suite
  inside the loop is the phase's core discipline; a test-runner
  connection (or practitioner-run results in patch-mediated mode) is
  essential.
- **Security scanners, dependency audit, lint/format, coverage** — the
  continuous scoring inputs; prefer the project's existing tooling,
  codified at Step 03.
- **Version control operations** — semantic commits inside the existing
  conventions; CI status visibility for the landing discipline.
- **A separate AI configuration for Step 07** — a different model or
  differently-configured session for the independent review; inventoried
  at Step 00, attested in Step 07 §1.
- **Library documentation lookup** (Context7 or equivalent) — for
  dependency APIs cited during generation.

### Capabilities Can Shift Mid-Phase

*Inherited from Phases 2–4.* When capability availability changes during
the run, **amend the Step 00 document with a dated §7 entry** — record
reliability posture (usable-on-demand / needs-warm-up / intermittent),
flag artifacts produced before the shift, and do not silently work
around the change.

---

## Dogfooding & Calibration Guidance

This toolkit is at v1.0. Every Phase 5 run on a real project is a
dogfooding cycle producing observations for v1.x+ revisions.

### Observation Capture Protocol

During the run, capture observations in `dogfooding-observations.md`
(IDs `P5-Obs-NN`) whenever:

- A prompt's structure forced a workaround or lacked a slot
- The Module → Work Package → Task hierarchy felt over- or under-fitted
  to a real change
- The in-loop regression gate, the patch-mediated mode, or the semantic
  commit integration produced friction worth naming
- The effort-actuals capture felt miscalibrated (too granular, too
  coarse)
- A cross-step handoff lost or duplicated information
- An upstream inheritance (weights, baselines, estimates, cohorts) felt
  miscalibrated

Capture is **fast and incomplete by design**; the end-of-phase
three-pass review (cluster → decide → revise) does the analysis. The
protocol is inherited from Phase 1 v1.3 / Phase 2 v1.1 / Phase 3 v1.1.

### The First Phase 5 Dogfood Will Calibrate the Multipliers

Phase 5 is where the track's BELIEVED AI-acceleration multipliers meet
measured actuals for the first time. Expect the effort-actuals discipline
itself to draw observations — and expect the Step 10 §5 calibration table
to be the single most valuable artifact the first dogfood produces for
the rest of the framework (it feeds Phase 7 calibration and next-cycle
Phase 2 cost modeling).

---

## Common Pitfalls

*These are pitfalls specific to running this toolkit. The instructions
file has the comprehensive list.*

**Starting Step 05 without Step 04.** "Implement the change spec" is not
a task list. The loop is only disciplined when tasks are small,
verifiable, and acceptance-criteria'd first.

**Running only the new tests in the loop.** The regression suite runs
inside the loop, per the Step 02 regression gate. Breaks found at Step
09 that Step 05 should have caught are loop-discipline failures.

**"Just a small edit" to an UNTOUCHED module.** That is an unspecified
change with no regression surface and no review gate. Stop and surface
it as a Channel 2 candidate.

**Skipping Step 07 because Step 06 passed.** They are different lenses:
Step 06 verifies conformance to the spec; Step 07 independently audits
what conformance checking cannot see (logic, security, drift). The gate
requires both.

**Reconstructing effort actuals at the gate.** Actuals are recorded
per-task in the Step 05 report as work happens. Retrospective guesses
cannot calibrate the multipliers.

**Landing cohort members separately.** Coordinated-landing cohorts from
the Phase 3 Coordination Map exist because those changes are only
coherent together. The Step 02 plan names them; Step 09 verifies them.

**Treating the Step 10 gate as a formality after Step 09 passes.** Step
09 validates integration; Step 10 validates the *phase* — completion
map, scorecard refresh, cost/capacity/calibration, traceability, and
upstream alignment. They are different questions.

---

## What's Available, What's Not

### Available in v1.0

- All eleven step prompts with output formats and evaluation checklists
- Instructions file with the three shifts, four feedback channels, ID
  series and traceability chain, code-access requirement, safety gates,
  behavioral rules, dependency graph, and output standards
- This README
- `dogfooding-observations.md` template (empty, ready for the first
  Phase 5 cycle)

### Not Yet Available (Queued for v1.1+ Based on Dogfooding)

- **Worked examples** — a Diamonds-derived worked example for Step 04
  (module implementation plan) and a Step 05 Implementation Report;
  deferred to keep v1.0 lean
- **Language/stack-specific generation-preamble variants** — if dogfoods
  show the Step 03 preamble needs per-stack specializations (TypeScript
  library vs Solidity vs service), v1.1+ adds them
- **Effort-actuals capture tooling guidance** — a lighter-weight
  capture convention if the per-task discipline proves too granular in
  practice
- **Cohort-scoped Step 09 variant** — if multi-cohort runs recur, a
  dedicated per-cohort integration checklist may graduate from the
  current note

---

## Version History

| Version | Date | Source | Summary |
|---------|------|--------|---------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Phase 5 existing-projects toolkit. Fourteen files (instructions + 11 step prompts + README + dogfooding template). Three-stage structure (setup / per-module pipeline / integration & gate) with the Module → Work Package → Task hierarchy replacing the greenfield module/milestone/epic breakout. v1.0-original disciplines: the in-loop regression gate; disposition-scoped implementation (UNTOUCHED modules not edited); provenance-tagged CS-NN codified from the existing codebase; semantic commits integrated into existing commit conventions; per-task effort actuals graduating BELIEVED multipliers to ESTIMATED (Step 10 §5 calibration table). Four feedback channels and the six-outcome readiness gate. Code-access hard requirement for Step 05 (direct write or patch-mediated). Scorecard inheritance, two-scope validation split, multi-repo scoping, currency rules, safety gates, and dogfooding protocol inherited from Phase 1 v1.3 / Phase 2 v1.1 / Phase 3 v1.1 / Phase 4 v1.0. |

---

*Part of the Phase 5 (Existing Projects) Implementation Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `implementation.existing-project.instructions.md`*
