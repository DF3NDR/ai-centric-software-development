# Phase 7: Deployment & Evolution — Tool Set
## AI-Centric Software Development Playbook

---

## Overview

This directory contains the complete tool set for **Phase 7: Deployment &
Evolution** of the AI-Centric Software Development Playbook — the **final
phase**. Phase 6 cleared the system for deployment; Phase 7 takes it live and
keeps it alive. The framework shifts from **building to sustaining**.

Phase 7 is unlike every phase before it. It is **continuous, not a one-pass
phase**: the deployment event recurs per release, the operational loops
(runbooks, drift detection, scorecard) run on cadences and triggers, and
evolution runs on demand. It has **no terminal gate and no next phase** — the
article is explicit that Phase 7 "does not have a validation checkpoint in the
same sense as earlier phases." Instead, the phases stop being a pipeline and
become a **cycle**: operational signals (drift, debt, new features, new
compliance requirements) re-enter the earlier phases through the same SDD
discipline that built the system.

Its dual nature — **operational stability** and **continuous evolution** — is
the defining theme, both first-class, powered by the same toolkit, measured by
the same Core Principles, and driven by the same SDD methodology.

The outputs are continuous: a **deployed, observable system**; **operational
runbooks as AI orchestration scripts**; **continuous compliance**; a living
**technical-debt inventory**; **evolution artifacts**; and a continuously
updated **Principle Scorecard** (v5.0 at launch, v5.x ongoing — a live
dashboard).

---

## Framework Context

This tool set is part of the [AI-Centric Software Development
Playbook](../../../README.md), a practitioner's framework for small teams
(1–5 people) that use AI tools to deliver what large organizations once
required.

### Phase 7 Differs From Phases 4–6 in Character

| Dimension | Phase 4 | Phase 5 | Phase 6 | Phase 7 |
|-----------|---------|---------|---------|---------|
| Primary work | Specifying the blueprint | Generating verified code | Auditing the system | **Deploying, operating, and evolving the live system** |
| AI role | Architecture specifier | Implementation generator | Independent auditor | **Deployment executor + operations orchestrator + evolution partner** |
| Number of prompts | 16 | 15 | 10 | **8** |
| Lifespan | One pass | One pass | One pass | **Continuous (ongoing)** |
| Execution model | Dependency graph | Per-module pipeline | Stage + parallel audits | **Cadence & trigger (recurring loops)** |
| Terminal gate | 5-outcome | 6-outcome | 7-outcome | **None — front launch-check + cycle-back** |
| Backward effects | Phase 3 + 2 | Phase 4 + 3 + 2 | Phase 5 + 4 + 3 + 2 | **Cycle-back into any earlier phase** |
| Cross-phase living artifact | Scorecard v2.0 | Scorecard v3.x | Scorecard v4.0 | **Scorecard v5.0/v5.x (live dashboard)** |
| Distinctive artifacts | Specs, contracts | Code, tests | Audit reports | **AI-executable orchestration scripts (checklist, runbooks, rollback)** |

Five things make Phase 7 distinct:

**It is continuous, not a one-pass phase.** There is no completion — there is
steady state: deploy per release, operate on cadences/triggers, evolve on
demand.

**It has no terminal gate.** The escalating readiness-gate pattern (Phase 6
ended at seven outcomes / four amendment paths) does not continue. Phase 7's
only gate is at the *front* — a lightweight launch-readiness go/no-go.

**The phases become a cycle.** Operational findings route back into the
responsible earlier phase through **cycle-back triggers**, not amendment
packages to a downstream gate.

**Its signature artifacts are AI-executable orchestration scripts.** Deployment
checklists, runbooks, and rollback procedures are structured instruction sets
(trigger → steps → decision branches → human checkpoints → escalation), not
prose.

**It is dual-natured.** Operational stability and continuous evolution are
equally first-class.

### The Six Core Principles in Phase 7 (steady-state mode)

| Principle | Phase 7 Steady-State Application |
|-----------|----------------------------------|
| **Security** | Continuous threat/vulnerability/compliance monitoring; periodic pen testing; maintained incident runbooks. |
| **Maintainability** | Documentation stays current (continuous queryability); tests stay green; debt stays managed. |
| **Economics** | Actual costs tracked against the Phase 2 model; optimization opportunities identified. |
| **Operations** | The home territory — uptime, MTTR, deployment frequency, rollback success; runbooks exercised and refined. |
| **Scoring & Metrics** | The scorecard is a **live dashboard**, not a periodic report. |
| **Correctness Verification** | Scheduled production conformance checks; drift detection; formal models maintained alongside the code. |

---

## Directory Contents

```
phase-07-deployment-evolution/
├── README.md                                              ← You are here
├── deployment-evolution.instructions.md                   ← Load as project context
│
│   ═══ STAGE 1 — DEPLOYMENT (per-release, one-time ordered) ═══
├── step-01-launch-readiness-confirmation.prompt.md         ← GO / CONDITIONAL GO / NO-GO (front check)
├── step-02-deployment-execution-and-verification.prompt.md ← INSTRUCTION SET: deployment checklist; observability from day one
├── step-03-rollback-procedure.prompt.md                    ← INSTRUCTION SET: trigger + procedure + verification (first-class)
│
│   ═══ STAGE 2 — CONTINUOUS OPERATIONS (recurring / scheduled / per-incident) ═══
├── step-04-operational-runbooks.prompt.md                  ← INSTRUCTION SETS: runbooks-as-orchestration-scripts + feedback loop
├── step-05-drift-detection.prompt.md                       ← spec / scorecard / compliance drift + continuous compliance; cycle-back
├── step-06-operational-scorecard.prompt.md                 ← v5.0 launch + v5.x ongoing (live dashboard)
│
│   ═══ STAGE 3 — EVOLUTION (triggered / on-demand) ═══
├── step-07-technical-debt-management.prompt.md             ← living TD inventory → principle prioritization → SDD resolution
└── step-08-evolution-and-change-orchestration.prompt.md    ← new features + refactoring; routes back through Phases 1–6 (the cycle's hinge)
```

**8 step prompts + instructions + README = 10 files** — the leanest toolkit,
fitting a continuous operational phase.

---

## File Descriptions

### `deployment-evolution.instructions.md`
**Type:** Instructions file (load once as persistent project context)

The overarching context: the six-phase comparison, the steady-state principles,
the three-stage structure, the **Cadence & Trigger Map** (replacing the
dependency graph), the **cycle-back routing** (replacing amendment packages),
the instruction-set output discipline, the living-registry IDs (RB/DR/TD/CB-NN),
the behavioral guidelines, and "the framework continues."

### Stage 1 — Deployment (per-release, one-time ordered)

#### `step-01-launch-readiness-confirmation.prompt.md`
The front go/no-go. Confirms Phase 6's authorization still holds for this
deployment (gates intact, no material un-audited commits, infra provisioned,
rollback ready). **GO / CONDITIONAL GO / NO-GO.** A material change since the
audit is a NO-GO routed back to Phase 6 — not a re-audit performed here.

#### `step-02-deployment-execution-and-verification.prompt.md`
Produces and executes the **Deployment Checklist** as an AI-executable
instruction set (pre-deploy verification → execution → post-deploy verification
→ rollback readiness), with human checkpoints and **observability live from day
one**. The checklist evolves with each deployment.

#### `step-03-rollback-procedure.prompt.md`
Rollback as a **first-class, routine** instruction set: measurable trigger
criteria, AI monitors and proposes, human authorizes execution, verification
confirms return to baseline. A fired rollback routes the underlying defect to
Phase 5 (CB-NN).

### Stage 2 — Continuous Operations (recurring)

#### `step-04-operational-runbooks.prompt.md`
The signature idea: **runbooks as AI orchestration scripts** (trigger →
diagnostics → decision branches → human checkpoints → escalation), grounded in
the real topology/baselines, with the mandatory **incident feedback loop** and
staleness flagging. RB-NN.

#### `step-05-drift-detection.prompt.md`
Detects **specification / scorecard / compliance drift** against live
production, verifies compliance continuously with auto-generated evidence, and
classifies and routes every drift (update impl / update spec / accepted
exception) via cycle-back. DR-NN.

#### `step-06-operational-scorecard.prompt.md`
The cross-phase scorecard's terminal **live-dashboard** form — v5.0 at launch,
v5.x ongoing — scored from production telemetry, regression-checked against v4.0
and prior v5.x, with the full v1.0→v5.x trend. Never frozen.

### Stage 3 — Evolution (triggered)

#### `step-07-technical-debt-management.prompt.md`
A living, signal-derived **debt inventory** (TD-NN), characterized per item,
**principle-weighted** prioritization, with SDD-cycle bypasses captured as debt
and prioritized items resolved *through the SDD cycle* (CB-NN), never patched.

#### `step-08-evolution-and-change-orchestration.prompt.md`
The **cycle's hinge**: characterizes a change, assesses impact across
modules/contracts/data/security/scorecard, decides abbreviated vs. full cycle,
triggers an **architecture review** when warranted, and routes the work back
through Phases 1–6 (CB-NN) to be developed to the same standard as the original
system.

---

## The Minimum Viable Path

Eight prompts is the full toolkit. Phase 7's variability is not which prompts to
skip — for any deployed, evolving system all eight are standing capabilities —
but **cadence** (when each runs) and one section-level conditional.

### The Launch Path (one-time, per release)

Steps 01 → 02 → 03 run as an ordered sequence for each deployment.

### The Standing Loops (recurring, from launch onward)

Steps 04–08 are continuous capabilities, each on its cadence/trigger,
established at launch and run for the life of the system. A team that deploys
but never establishes these loops has the "observable on paper, blind in
practice" problem.

### The One Section-Level Conditional

| Conditional | Applies When |
|-------------|--------------|
| Compliance drift / continuous-compliance section of Drift Detection (Step 05) | Only if the system has compliance obligations. Otherwise marked Not applicable; spec and scorecard drift still run. |

### Scaling

A small system runs lighter loops (less frequent drift checks, a smaller debt
inventory, simpler runbooks) — but it runs them. What scales is cadence and
depth, not the set of capabilities.

---

## How to Use This Tool Set

### Prerequisites

1. Confirm the [Phase 6 toolkit](../phase-06-testing-audit/README.md) is
   complete with a passing Step 10 Deployment Readiness Review (READY or
   CONDITIONALLY READY). Phase 7 deploys the authorized system.
2. Load `deployment-evolution.instructions.md` as project-level instructions.
3. Have the tool connections the operational loops need (CI/CD, monitoring,
   logging, infra, compliance evidence, code-quality/dependency tools).

### Execution Model — Cadence & Trigger (not a pipeline)

```
Phase 6 Deployment Readiness Report (authorization) + frozen docs +
compliance matrix + performance baselines + Scorecard v4.0 + IaC/CI-CD + H-NN
   │
   ▼
═══ STAGE 1: DEPLOYMENT (per release — one-time ordered) ═══
Step 01 Launch-Readiness  ──NO-GO→ fix prerequisites / re-enter Phase 6
   ▼ (GO / CONDITIONAL GO)
Step 02 Deployment Execution & Verification  ──(observability live day one)
   ▼
Step 03 Rollback Procedure  ──(readied; fires on trigger)
   ▼  system LIVE
═══ STAGE 2: CONTINUOUS OPERATIONS (standing loops) ═══
   ├─ Step 04 Runbooks            — continuous; per-incident; post-incident review
   ├─ Step 05 Drift Detection     — scheduled + per-change
   └─ Step 06 Operational Scorecard — v5.0 launch; v5.x scheduled + per-incident
═══ STAGE 3: EVOLUTION (triggered) ═══
   ├─ Step 07 Technical Debt      — continuous inventory; scheduled review
   └─ Step 08 Evolution           — on new-feature / refactoring / change request
        │
        └── CYCLE-BACK (CB-NN) ──► re-enter Phases 1–6, return via Phase 7 Steps 01–03
```

### Per-Prompt Cadence & Trigger

| Step | Cadence / Trigger |
|------|-------------------|
| 01 Launch-Readiness | Per release, before each deployment |
| 02 Deployment Execution | Per release |
| 03 Rollback | Readied per release; executed on a trigger |
| 04 Runbooks | Continuous; executed per-incident; reviewed after each incident |
| 05 Drift Detection | Scheduled (e.g., weekly) + on significant change |
| 06 Operational Scorecard | v5.0 at launch; v5.x scheduled + after material incidents |
| 07 Technical Debt | Continuous inventory; scheduled prioritization review |
| 08 Evolution | On demand — new feature, refactoring, change request |

### Running Each Prompt

For each step: open a new AI session with `deployment-evolution.instructions.md`
loaded and the relevant tool connections; paste the required inputs (see the
prompt's metadata table); answer the clarifying questions (presence check
first); review the output against the prompt's evaluation checklist. Steps 02,
03, 04 produce AI-executable instruction sets with human checkpoints; honor the
checkpoints and the safety conventions (never print/log/commit secrets; STOP for
privileged/sensitive operations).

---

## Cycle-Back Routing (replaces amendment packages)

Phase 7 has no downstream gate to escalate to. Findings route back into the
responsible earlier phase, recorded as cycle-back triggers (CB-NN).

| Finding (source step) | Routes To |
|-----------------------|-----------|
| Specification drift (05) | Update implementation (Phase 5) or specification (Phase 4); or document an accepted exception |
| Scorecard regression (05/06) | The phase responsible for the regressed principle |
| Compliance drift / new requirement (05) | Phase 1 (research) → Phase 3/4 (controls) |
| Technical debt prioritized for resolution (07) | The SDD cycle — Phase 5 (impl) + Phase 6 (test); Phase 3/4 if architectural |
| New feature (08) | Phases 1–6 (full or abbreviated cycle) → re-deploy via Phase 7 |
| Architectural tension (08) | Phase 3 (design) + Phase 4 (architecture) |
| Rollback's underlying defect (03) | Phase 5 (impl) + Step 02 checklist evolution |

This routing is what makes the framework a cycle rather than a pipeline.

---

## Living-Registry ID Conventions

Phase 7 produces continuously-maintained registries, not forward-cited
constraints (it is the end of the chain).

| ID Series | Registry / Artifact | Source Step |
|-----------|---------------------|-------------|
| **RB-NN** | Operational runbooks | Step 04 |
| **DR-NN** | Drift findings (tagged spec/scorecard/compliance) | Step 05 |
| **TD-NN** | Technical-debt items | Step 07 |
| **CB-NN** | Cycle-back triggers (routing to an earlier phase) | Steps 03, 04, 05, 07, 08 |

Phase 7 *consumes* the prior-phase IDs as references — the API contracts and
SIC-NN, SEC-NN, DA-NN, SP-NN, DOC-NN, GOV-NN, CS-NN, and the H-NN observability
hooks are the standards drift detection checks against and the substrate
evolution builds on. It establishes no new forward-cited constraint series.

---

## The Scorecard Reaches Its Terminal Form

The Principle Scorecard — established as the v1.0 baseline in Phase 3 and
updated every phase since — reaches its terminal, operational form in Phase 7:
v5.0 at launch, v5.x ongoing, a **live production health dashboard**, per the
Phase 3 Step 06 protocol.

| Version | Phase | Form |
|---------|-------|------|
| v1.0 | Phase 3 | Design baseline |
| v2.0 | Phase 4 | Architecture |
| v3.x | Phase 5 | Implementation |
| v4.0 | Phase 6 | Final pre-deployment |
| **v5.0 / v5.x** | **Phase 7** | **Live operational dashboard (ongoing)** |

There is no further phase version — v5.x continues for the life of the system.

---

## Common Pitfalls

**Observable on paper, blind in practice.** Instrumentation with no review habit
is not observability. *Defense:* day-one operational routines (Step 02) and the
Stage 2 loops.

**Runbooks that rot.** *Defense:* Step 04's mandatory incident feedback loop and
staleness flagging.

**Debt accumulation through "quick fixes."** *Defense:* Step 07's living
inventory captures every bypass; fast action is followed by scheduled SDD
integration.

**Evolution without architecture review.** *Defense:* Step 08's impact
assessment and architecture-review cycle-back trigger.

**Compliance as a one-time event.** *Defense:* Step 05's continuous compliance
verification and audit-evidence generation.

**Treating Phase 7 as a one-pass phase with an end.** *Defense:* the cadence-
and-trigger model and cycle-back routing — standing loops, not a sequence with a
finish line.

**Letting the scorecard freeze.** *Defense:* Step 06's v5.x live-dashboard
cadence and Step 05's scorecard-drift comparison.

---

## The Framework Continues

Phase 7 has no validation checkpoint and no next phase. It operates
continuously, with the Core Principles, the live Principle Scorecard, and the
SDD cycle providing ongoing structure. The phases are a **cycle**, not a
pipeline:

- Operations reveals a new feature is needed → the SDD cycle runs through the
  relevant phases for that feature (Step 08).
- Drift detection reveals an architectural assumption no longer holds →
  Phase 3 and Phase 4 are revisited (Step 05 → CB-NN).
- Compliance monitoring reveals a new regulatory requirement → Phase 1
  researches it and the framework cycles through (Step 05 → CB-NN).
- Technical-debt management identifies a component to refactor → the SDD cycle
  runs through implementation and testing (Step 07 → CB-NN).

The toolkit, the tool sets, and the SDD methodology are assets that keep
producing value for as long as the system is maintained and evolved.

---

## The Framework Is Complete

Phase 7 is the final phase of the seven-phase AI-Centric Software Development
framework. With the full phase-by-phase walkthrough now in place —
**Phase 1: Information Gathering → Phase 2: Analysis & Stack Selection →
Phase 3: Design & Technical Analysis → Phase 4: Architecture & Modular Design →
Phase 5: Implementation → Phase 6: Testing & Audit → Phase 7: Deployment &
Evolution** — the framework provides a structured, principle-driven,
specification-first approach to building software with AI as the primary
interface, from first research through live operation and continuous evolution.

The series' **Introduction — The Manifesto** is written last, because it could
only be written with the full weight of the framework behind it. It is the front
door to the series, framing why small teams orchestrating AI tools will build
the software that matters, why the fundamentals of computer science remain
essential as the interface changes, and why the time to build this capability
is now.

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | [date] | Initial release — instructions file plus eight prompts (completes the seven-phase framework) |

---

## Related Resources

- [AI-Centric Software Development Playbook — Full Series](../../../README.md)
- [Part 1 — Core Principles](../../../docs/part-01-core-principles.md)
- [Part 2 — Building Your Toolkit](../../../docs/part-02-building-your-toolkit.md)
- [Part 9 — Phase 7: Deployment & Evolution](../../../docs/part-09-deployment-evolution.md)
- [Phase 1 Tool Set](../phase-01-information-gathering-toolset/README.md)
- [Phase 2 Tool Set](../phase-02-analysis-stack-selection/README.md)
- [Phase 3 Tool Set](../phase-03-design-technical-analysis/README.md)
- [Phase 4 Tool Set](../phase-04-architecture-modular-design/README.md)
- [Phase 5 Tool Set](../phase-05-implementation/README.md)
- [Phase 6 Tool Set](../phase-06-testing-audit/README.md)
- [The Manifesto — Small Teams, Big AI, New Paradigm](../../../docs/part-00-manifesto.md) *(the series introduction)*

---

*Part of the AI-Centric Software Development Playbook — the final phase*
*This tool set is a living artifact — it will be refined as the methodology
matures and use in practice reveals improvements.*
