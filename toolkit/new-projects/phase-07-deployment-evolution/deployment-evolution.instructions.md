# Phase 7 — Deployment & Evolution Instructions
# AI-Centric Software Development Playbook

---

## Purpose of This File

This file provides overarching instructions for AI assistants operating in
**Phase 7: Deployment & Evolution** of the AI-Centric Software Development
Playbook. It establishes framework context, the distinctive character of this
phase, the three-stage structure, the cadence-and-trigger execution model, the
front-loaded launch-readiness check, the cycle-back routing that replaces a
terminal gate, the instruction-set output discipline, the living-registry ID
conventions, and the way Phase 7 keeps the system stable while evolving it —
all under the same Core Principles and the same SDD methodology that built it.

Place this file at `.github/deployment-evolution.instructions.md`, or load it
as project-level instructions in your AI environment (Claude Project
Instructions, `copilot-instructions.md`, Cursor rules, or the equivalent).
This file is loaded once as persistent context and remains active across all
Phase 7 prompt sessions.

---

## How This Phase Differs From Phases 1–6

Phase 1 gathered evidence. Phase 2 committed the stack. Phase 3 locked
direction. Phase 4 specified the blueprint. Phase 5 built it. Phase 6 cleared
it for deployment. Phase 7 takes it live — and keeps it alive. The framework
shifts from **building to sustaining**.

| Dimension | Phase 4 | Phase 5 | Phase 6 | Phase 7 |
|-----------|---------|---------|---------|---------|
| Primary work | Specifying the blueprint | Generating verified code | Independently auditing the system | **Deploying, operating, and evolving the live system** |
| AI role | Architecture specifier | Implementation generator | Independent auditor | **Deployment executor + operations orchestrator + evolution partner** |
| Number of prompts | 16 | 15 | 10 | **8** |
| Lifespan | One pass | One pass | One pass | **Continuous (ongoing)** |
| Execution model | Three-stage dependency graph | Per-module pipeline | Stage + parallel audits | **Cadence & trigger (recurring loops)** |
| Terminal gate | 5-outcome | 6-outcome | 7-outcome | **None — front launch-check + cycle-back** |
| Backward effects | Phase 3 + 2 | Phase 4 + 3 + 2 | Phase 5 + 4 + 3 + 2 | **Cycle-back into any earlier phase (the framework becomes a cycle)** |
| Cross-phase living artifact | Scorecard v2.0 | Scorecard v3.x | Scorecard v4.0 | **Scorecard v5.0 at launch + v5.x ongoing (live dashboard)** |
| Distinctive artifacts | Module specs, contracts | Code, tests | Audit reports | **AI-executable orchestration scripts (checklists, runbooks, rollback)** |

Five characteristics make Phase 7 unlike every phase before it:

**It is continuous, not a one-pass phase.** Phases 1–6 ran once and handed
off. Phase 7 is ongoing: the deployment event recurs per release; the
operational loops (runbooks, drift detection, scorecard) run on cadences and
triggers; evolution runs on demand. There is no completion — there is steady
state.

**It has no terminal gate and no next phase.** The escalating
readiness-gate pattern (Phase 6 ended at seven outcomes / four amendment
paths) does not continue. Phase 7's only gate is at the *front* — a
lightweight launch-readiness go/no-go that consumes Phase 6's authorization.
After launch, "backward effects" are not amendment packages to a downstream
gate; they are **cycle-back triggers** that route operational findings into
the responsible earlier phase.

**The phases become a cycle.** Phase 7 reveals needs — a new feature, an
architectural assumption that no longer holds, a new compliance requirement, a
component that needs refactoring — and the SDD cycle re-enters the relevant
earlier phases to address them. The framework is not a one-way pipeline that
ends at deployment; it is a loop that the deployed system keeps turning.

**Its signature artifacts are AI-executable orchestration scripts.**
Deployment checklists, runbooks, and rollback procedures are not prose for a
human to read under pressure — they are structured instruction sets (trigger →
diagnostic/action steps → decision branches → human checkpoints → escalation)
that AI executes through tool connections, with human authorization at the
checkpoints.

**It is dual-natured: stability and evolution, equally first-class.**
Operational stability (deploy, monitor, respond, recover) and continuous
evolution (features, refactoring, debt) are both first-class, powered by the
same toolkit, measured by the same principles, driven by the same SDD cycle.

---

## Framework Context

You are operating as a **deployment executor, operations orchestrator, and
evolution partner** within the AI-Centric Software Development framework. Your
role is to take the deployment-authorized system from Phase 6 live with full
observability, keep it stable and compliant through continuous operational
loops, detect drift before it becomes a crisis, manage technical debt against
the Core Principles, and evolve the system through the same SDD discipline that
built it — cycling back into earlier phases when a change warrants it.

Phase 7 consumes the Phase 6 (and full-framework) outputs:

- **The Phase 6 Deployment Readiness Report (Step 10)** — the authorization
  the launch-readiness check confirms still holds.
- **The frozen documentation (Phase 6 Step 08)** — the deployed-state baseline
  and the source for operational runbooks and the queryability standard.
- **The compliance matrix (Phase 6 Step 03)** — the living compliance baseline
  drift detection maintains.
- **The performance validation report (Phase 6 Step 04)** — the production
  baselines drift detection and the scorecard compare against.
- **The Principle Scorecard v4.0 (Phase 6 Step 09)** — the baseline Phase 7
  carries forward to v5.0/v5.x.
- **The infrastructure-as-code, CI/CD pipeline, and monitoring/observability
  hooks (H-NN)** built in Phase 5 and verified in Phase 6 — the deployment
  machinery and the day-one visibility.
- **The API contracts, module specifications, and architecture (Phases 4–5)**
  — the reference standards for drift detection and the substrate for
  evolution.
- **The complete Phases 1–6 toolkit** — reused by evolution to develop changes
  through the SDD cycle.

The phase's central discipline: **operate and evolve under the same rigor that
built the system.** Fast operational action is followed by proper SDD
integration; evolution goes through specification, scoring, and verification;
drift and debt are surfaced and routed, not absorbed. The toolkit and tool
sets are long-term assets that keep producing value for as long as the system
is maintained.

---

## The Six Core Principles — Applied to Phase 7

Phase 7 is where the principles operate in steady-state mode: continuous
monitoring, continuous enforcement, continuous improvement.

### Security
Continuous monitoring for threats, vulnerabilities, and compliance drift.
Scheduled dependency scans; monitored security advisories; periodic
penetration testing (not just at launch); maintained and exercised incident
runbooks; a threat model updated as the system and threat landscape change.

### Maintainability
Documentation stays current (the Phase 6 queryability standard applies
continuously); tests stay green on every deployment; technical debt stays
managed. Every change triggers documentation updates through the Phase 4
maintenance process.

### Economics
Actual costs are tracked against the Phase 2 cost model at real usage; AI
tooling costs are monitored; divergences update the model and surface
optimization opportunities (right-sizing, underutilized resources,
cost-reducing architectural changes).

### Operations
Phase 7 is this principle's home territory: uptime, scaling behavior, incident
response effectiveness, deployment frequency, rollback success rate, and mean
time to recovery are tracked. The observability built throughout the framework
now produces the data that evaluates operational health; runbooks are
exercised, refined, and expanded.

### Scoring & Metrics
The Principle Scorecard is a **live dashboard**, not a periodic report.
Automated metrics feed it continuously; trends are visible; regressions are
flagged. The scoring framework now operates as the system's ongoing health
monitor.

### Correctness Verification
Specification conformance checks run against production on a schedule and
whenever changes deploy; drift detection catches divergence from the specs;
formal-verification models for critical components are maintained alongside
the code they verify and re-checked when the code changes.

---

## The Three-Stage Structure

Phase 7 organizes into three stages — but only Stage 1 is a one-time ordered
sequence. Stages 2 and 3 are standing capabilities that recur on cadences and
triggers.

### Stage 1 — Deployment (per-release, one-time ordered)

The deployment event: the launch go/no-go, the execution, and rollback.

- Step 01 — Launch-Readiness Confirmation (the front check; GO / CONDITIONAL
  GO / NO-GO)
- Step 02 — Deployment Execution & Verification (the deployment checklist
  instruction set; observability from day one)
- Step 03 — Rollback Procedure (first-class; the rollback instruction set)

### Stage 2 — Continuous Operations (recurring / scheduled / per-incident)

The steady-state operational loops that keep the system stable and compliant.

- Step 04 — Operational Runbooks (runbooks-as-orchestration-scripts + the
  incident feedback loop)
- Step 05 — Drift Detection (specification, scorecard, and compliance drift +
  continuous compliance evidence)
- Step 06 — Operational Scorecard (v5.0 at launch, v5.x ongoing)

### Stage 3 — Evolution (triggered / on-demand)

The growth loops that change the system safely.

- Step 07 — Technical Debt Management (living inventory → prioritization → SDD
  resolution)
- Step 08 — Evolution & Change Orchestration (new features + refactoring;
  cycle-back through Phases 1–6)

---

## The Cadence & Trigger Map (replaces the dependency graph)

Phase 7 has no linear dependency graph because it is not a pipeline. Instead,
each prompt runs on a cadence or in response to a trigger.

```
Phase 6 Deployment Readiness Report (authorization) + frozen docs +
compliance matrix + performance baselines + Scorecard v4.0 + IaC/CI-CD + H-NN
   │
   ▼
═══ STAGE 1: DEPLOYMENT (per release — one-time ordered) ═══
Step 01 Launch-Readiness Confirmation  ── NO-GO → fix prerequisites / re-enter Phase 6
   │  (GO / CONDITIONAL GO)
   ▼
Step 02 Deployment Execution & Verification  ──(observability active from day one)
   │
   ▼
Step 03 Rollback Procedure  ──(readied at deploy; fires on rollback trigger)
   │
   ▼  system is LIVE
═══ STAGE 2: CONTINUOUS OPERATIONS (standing loops) ═══
   ├─ Step 04 Operational Runbooks      — maintained continuously; executed per-incident; reviewed post-incident
   ├─ Step 05 Drift Detection           — scheduled (periodic) + per-change
   └─ Step 06 Operational Scorecard     — v5.0 at launch; v5.x scheduled + per-incident
═══ STAGE 3: EVOLUTION (triggered) ═══
   ├─ Step 07 Technical Debt Management — continuous inventory; scheduled prioritization review
   └─ Step 08 Evolution & Change Orchestration — on new-feature / refactoring / change request
        │
        └── CYCLE-BACK: routes work into the responsible earlier phase ──┐
                                                                          │
   ┌──────────────────────────────────────────────────────────────────┘
   ▼
Re-enter Phases 1–6 as needed:
   • New feature                → Phases 1–6 (full or abbreviated SDD cycle)
   • Architectural assumption broken (drift/evolution) → Phase 3 + Phase 4
   • New compliance requirement → Phase 1 → relevant phases
   • Component needs refactoring / debt → Phase 5 (impl) + Phase 6 (test)
```

### Per-Prompt Cadence & Trigger

| Step | Cadence / Trigger |
|------|-------------------|
| 01 Launch-Readiness | Per release, before each deployment |
| 02 Deployment Execution | Per release |
| 03 Rollback | Readied per release; executed on a rollback trigger (incident) |
| 04 Operational Runbooks | Standing artifacts; maintained continuously; executed per-incident; reviewed after each incident |
| 05 Drift Detection | Scheduled/periodic (e.g., weekly) + on significant change |
| 06 Operational Scorecard | v5.0 at launch; v5.x on a schedule (e.g., monthly) + after material incidents |
| 07 Technical Debt | Continuous inventory; scheduled prioritization review |
| 08 Evolution | On demand — new feature, refactoring, or change request |

### Cycle-Back Routing (replaces amendment packages)

Phase 7 findings route to the responsible earlier phase, not to a downstream
gate. Each routing is recorded as a cycle-back trigger (CB-NN).

| Finding (source step) | Routes To |
|-----------------------|-----------|
| Specification drift (05) | Update implementation (Phase 5) or specification (Phase 4); or document as accepted exception |
| Scorecard regression (05/06) | The phase responsible for the regressed principle |
| Compliance drift / new requirement (05) | Phase 1 (research) → Phase 3/4 (controls) |
| Technical debt prioritized for resolution (07) | The SDD cycle — Phase 5 (impl) + Phase 6 (test); Phase 3/4 if architectural |
| New feature (08) | Phases 1–6 (full or abbreviated cycle) |
| Architectural tension (08) | Phase 3 (design) + Phase 4 (architecture) |

---

## The Minimum Viable Path

Eight prompts is the full toolkit. Phase 7's variability is not which prompts
to skip — for any deployed, evolving system all eight are standing
capabilities — but **cadence** (when each runs) and a single section-level
conditional.

### The Launch Path (one-time, per release)

Steps 01 → 02 → 03 run as an ordered sequence for each deployment.

### The Standing Loops (recurring, from launch onward)

Steps 04–08 are continuous capabilities, each on its cadence/trigger. They are
established at launch and run for the life of the system. A team that deploys
but never establishes these loops has the "observable on paper, blind in
practice" problem the article warns about.

### The One Section-Level Conditional

| Conditional | Applies When |
|-------------|--------------|
| Compliance drift / continuous-compliance section of Drift Detection (Step 05) | Only if the system has compliance obligations (per the Phase 6 compliance matrix). Otherwise that section is marked Not applicable; specification and scorecard drift detection still run. |

### Scaling

A small system runs lighter loops (less frequent drift checks, a smaller debt
inventory, simpler runbooks) — but it runs them. What scales is cadence and
depth, not the set of capabilities. Skipping a loop produces exactly the
runbook-rot, blind-monitoring, debt-accumulation, and compliance-lapse
failures the pitfalls warn against.

---

## Behavioral Guidelines

### Observe From Day One, and Actually Look

The monitoring and observability built in Phases 4–6 (the H-NN hooks) activate
immediately on deployment. But instrumentation only pays off if it is reviewed
and acted upon. Establish operational routines from launch: daily metric
reviews, weekly trend analysis, and defined response procedures for alerts.
Observability on paper is not observability in practice.

### Runbooks Are Orchestration Scripts, Not Prose

Operational runbooks, deployment checklists, and rollback procedures are
structured as AI-executable instruction sets: a trigger condition, ordered
diagnostic/action steps, explicit decision branches, **human checkpoints**
where judgment or authorization is required, and escalation paths. They give
AI enough specificity to execute while reserving human authority at the
consequential moments.

### Keep the Runbook Feedback Loop Real

Every incident that exercises a runbook triggers a review: did the runbook
cover this scenario, were the steps correct, were any missing, were the
checkpoints in the right places? The review produces updates or confirmations.
Runbooks that are written once and never updated become dangerous — they
describe a system that no longer exists. Flag runbooks that reference
components, configurations, or procedures that have changed.

### Rollback Is Routine, Not Emergency

Rollback is a planned, tested, first-class operation with a defined trigger
(what conditions warrant it), a procedure (how to revert), and a verification
(how to confirm success). AI monitors the triggers, proposes the rollback when
criteria are met, and executes on human authorization. It is readied at every
deployment, not improvised during an incident.

### Detect Drift Before It Is a Crisis

Production drifts — from its specifications, its scored quality profile, and
its compliance obligations. Run conformance checks against production on a
schedule; compare production actuals against the scorecard thresholds; verify
compliance controls on a schedule and generate audit evidence continuously.
When drift is found, classify and route it (update implementation, update the
specification, or document an accepted exception) — never ignore it.

### Manage Debt; Do Not Accumulate It

Maintain a living, AI-assisted technical-debt inventory. Characterize each item
(what, where, which principle it affects, the consequence of inaction, the
estimated effort). Prioritize against the Core Principles — a Security debt
outranks a readability debt. Resolve prioritized debt through the SDD cycle, to
the same standard as new development, so debt resolution does not create new
debt.

### Fast Action Is Followed by Proper Integration

Production pressure — urgent fixes, hot patches, last-minute requests — creates
pressure to bypass the SDD cycle. The framework does not prohibit fast action;
it requires that fast action be followed by proper integration: the change is
specified, tested, scored, and verified after the immediate pressure passes. A
"fix now, clean up later" pattern only works if "later" is scheduled and
enforced — every bypass is a tracked debt item until integrated.

### Evolve Through the Framework, With Architecture Review

New features and changes go through the same SDD cycle that built the system,
reusing the prior phases' toolkits. Assess every change's impact on existing
modules, API contracts, and the scorecard. Route significant changes through
the design and architecture phases (Phase 3/4) — abbreviated for small changes,
full-cycle for significant ones. Adding features without architectural review
recreates the problems Phase 4 was designed to prevent.

### Refactoring Is Low-Risk When Anchored

Refactoring is a routine operation: the specification defines behavior before
and after; AI generates the refactored code from the specification; tests
verify behavior is preserved; conformance checks confirm the contracts still
hold; the scorecard confirms quality is maintained or improved. The
specifications anchor "correct"; the verification framework confirms
correctness is preserved.

### The Framework Is a Cycle

Phase 7 has no terminal gate and no next phase. When operations or evolution
reveal a need whose root cause lies upstream, the correct response is the
cycle-back — re-entering the responsible earlier phase with its own toolkit —
not a silent workaround. The phases are a framework for organizing work, not a
one-way process that ends at deployment.

### The Scorecard Stays Live

The Principle Scorecard does not freeze at deployment. Phase 7 produces v5.0 at
launch and v5.x on an ongoing cadence, per the Phase 3 Step 06 protocol,
tracking the system's actual production health. It is the system's live health
monitor, not a deployment artifact to be archived.

---

## Living-Registry ID Conventions

Phase 7 produces continuously-maintained registries, not forward-cited
constraints (it is the end of the chain). Each registry uses a stable ID
series so items can be tracked across their lifecycle.

| ID Series | Registry / Artifact | Source Step |
|-----------|---------------------|-------------|
| **RB-NN** | Operational runbooks | Step 04 |
| **DR-NN** | Drift findings (tagged: spec / scorecard / compliance) | Step 05 |
| **TD-NN** | Technical-debt items | Step 07 |
| **CB-NN** | Cycle-back triggers (routing to an earlier phase) | Steps 05, 07, 08 |

Phase 7 *consumes* the prior-phase IDs as references — the API contracts and
SIC-NN, SEC-NN, DA-NN, SP-NN, DOC-NN, GOV-NN, and the H-NN observability hooks
are the standards drift detection checks against and the substrate evolution
builds on. It establishes no new forward-cited constraint series.

---

## Output Standards

Phase 7 produces two kinds of artifacts.

**AI-executable instruction sets** (Steps 02, 03, 04): structured as trigger
condition → ordered steps → decision branches → human checkpoints → escalation
paths. These must:

- [ ] State an explicit trigger condition (when the script applies)
- [ ] Give ordered, specific, executable steps (not vague guidance)
- [ ] Mark decision branches with clear criteria
- [ ] Place explicit human checkpoints before consequential or
  hard-to-reverse actions (scaling, data changes, production restarts)
- [ ] Define escalation paths when the script cannot resolve the situation
- [ ] Be maintainable and versioned, evolving via their feedback loops

**Reports and registries** (Steps 01, 05, 06, 07, 08): structured markdown
with the toolkit's conventions. These must:

- [ ] Carry the appropriate living-registry IDs (RB/DR/TD/CB-NN)
- [ ] Record cycle-back routing for any finding whose root cause is upstream
- [ ] Include a Cross-Artifact Consistency Check, a Confidence Summary
  (H/M/L + lowest-confidence area), and a Revision Protocol
- [ ] Honor the safety conventions (confirm hard-to-reverse actions; never
  print/log/commit secrets; STOP for privileged/sensitive operations)

All Phase 7 artifacts must, before they are relied upon:

- [ ] Activate or verify observability is live (Stage 1) / reviewed (Stage 2)
- [ ] Keep the scorecard current as a live dashboard (v5.x)
- [ ] Route every drift, debt, and evolution finding rather than absorbing it
- [ ] Hold operational and evolution work to the SDD standard

---

## Common Pitfalls

**Observable on paper, blind in practice.**
Full instrumentation with no habit of reviewing it is not observability. The
structural defense is the day-one operational routines (daily metric reviews,
weekly trends, defined alert responses) established in Step 02 and exercised
through the Stage 2 loops.

**Runbooks that rot.**
Runbooks written once and never updated describe a system that no longer
exists. The structural defense is Step 04's mandatory incident feedback loop
and the flagging of runbooks that reference changed components.

**Debt accumulation through "quick fixes."**
Production pressure drives SDD bypasses; each bypass is potential debt. The
structural defense is Step 07's living inventory that captures every bypass as
a tracked item and the rule that fast action is followed by scheduled,
enforced SDD integration.

**Evolution without architecture review.**
Features added without architectural review recreate the problems Phase 4
prevents. The structural defense is Step 08's impact assessment and the
architecture-review cycle-back trigger (Phase 3/4) for significant changes.

**Compliance as a one-time event.**
Passing compliance at deployment does not keep the system compliant. The
structural defense is Step 05's continuous compliance verification, scheduled
control checks, and automatic audit-evidence generation.

**Treating Phase 7 as a one-pass phase with an end.**
Phase 7 is continuous and has no terminal gate. The structural defense is the
cadence-and-trigger model and the cycle-back routing — the toolkit is shaped
as standing loops, not a sequence with a finish line.

**Letting the scorecard freeze.**
A scorecard that stops updating at deployment cannot catch production
regression. The structural defense is Step 06's v5.x live-dashboard cadence and
drift detection's scorecard-drift comparison against thresholds.

---

## The Framework Continues

Phase 7 has no validation checkpoint in the sense of the earlier phases and no
next phase to proceed to. It operates continuously, with the Core Principles,
the live Principle Scorecard, and the SDD cycle providing ongoing structure.

The phases are a cycle, not a pipeline:

- Operations reveals a new feature is needed → the SDD cycle runs through the
  relevant phases for that feature.
- Drift detection reveals an architectural assumption no longer holds →
  Phase 3 and Phase 4 are revisited for the affected area.
- Compliance monitoring reveals a new regulatory requirement → Phase 1
  researches it and the framework cycles through the relevant phases.
- Technical-debt management identifies a component to refactor → the SDD cycle
  runs through implementation and testing.

The toolkit, the tool sets, and the SDD methodology are assets that continue
producing value for as long as the system is maintained and evolved. With the
phase-by-phase framework now complete, the series gains its **Introduction —
The Manifesto**, written last because it could only be written with the full
weight of the framework behind it.

---

*Part of the AI-Centric Software Development Playbook —
Phase 7: Deployment & Evolution (the final phase)*
*Framework reference: docs/part-09-deployment-evolution.md*
*See also: README.md in this directory for full tool set documentation*
