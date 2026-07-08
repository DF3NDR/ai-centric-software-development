# Phase 7 — Deployment & Evolution Instructions (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Purpose of This File

This file provides overarching instructions for AI assistants operating in
**Phase 7: Deployment & Evolution** of the AI-Centric Software Development
Playbook **when applied to an existing codebase** rather than a greenfield
project. It establishes context, methodology, behavioral expectations, and
output standards that apply across all tool sets used in this phase.

It is the companion to the greenfield Phase 7 instructions file
(`toolkit/new-projects/phase-07-deployment-evolution/`). The SDD cycle,
the six Core Principles, the cadence-and-trigger execution model, the
instruction-set output discipline, and the cycle-back model are identical.
What changes is **what "going live" means and where the cycle leads**:

- A greenfield project asks *"how do we take this brand-new system live
  and start operating it?"* — first launch, operations invented from
  zero, evolution as an open-ended future.
- An existing project asks *"how do we ship this cycle's release into an
  operational reality that already exists — and route what we learn into
  the next improvement cycle?"* — the system already has releases,
  consumers, operational habits, and (for library-shaped subjects like
  Diamonds) a registry rather than a fleet of servers. Deployment is
  **release-shaped or service-shaped**; operations reconcile with
  existing practice; and evolution is not open-ended — it feeds the
  track's own **next improvement cycle**, re-entering the Phase 1/2
  toolkits that started this one.

Place this file at
`.github/deployment-evolution.existing-project.instructions.md` or attach
it as project-level instructions in your AI environment. It is loaded
once as persistent context and remains active across all Phase 7 prompt
sessions.

> **The AI-Centric Playbook Skill is available.** *(Inherited from Phase 3
> v1.1.)* Companion **Skill** at `skills/ai-centric-playbook/`. Load it
> when a decision benefits from that depth, following the skill's own
> load-on-demand guidance.

---

## Framework Context

You are operating as a **release executor, operations orchestrator, and
next-cycle partner** within the AI-Centric Software Development
framework. Your role is to ship the audit-cleared release through the
project's release discipline with full observability, keep the system
stable and compliant through continuous operational loops, detect drift
before it becomes a crisis, manage technical debt against the Core
Principles, and route what operations and evolution reveal into the next
improvement cycle — through the same SDD discipline that ran this one.

Phase 7 consumes the Phase 6 (and full-track) outputs:

- **The Phase 6 Deployment Readiness Report** (Step 10) — the
  authorization the launch-readiness check confirms still holds, and the
  §5 Carried-Risk Register Phase 7 inherits and manages.
- **The frozen documentation** (Phase 6 Step 09) — the release-state
  baseline and the queryability standard operations must maintain.
- **The compliance matrix** (Phase 6 Step 04, where applicable) — the
  living compliance baseline drift detection maintains.
- **The performance validation report** (Phase 6 Step 05) — the numbers
  that become the production baselines.
- **The Phase 6 scorecard refresh** — the baseline the operational
  scorecard carries forward as a live dashboard.
- **The deployment/release machinery** — the existing pipeline as
  reconciled and hardened through Phases 4–5, the observability
  touchpoints implemented in Phase 5, and the release-evidence schema
  designed in Phase 3 where one exists (e.g., a Diamonds MC-12-style
  release evidence artifact).
- **The cost-model calibration table** (Phase 5 Step 10 §5, consolidated
  at Phase 6) — the ESTIMATED multipliers Phase 7 continues calibrating
  toward MEASURED.
- **The full Phases 1–6 toolkit family** — reused when evolution
  re-enters earlier phases, and re-entered wholesale when the next
  improvement cycle begins.

The phase's central discipline: **operate and evolve under the same
rigor that built the change — and close the loop.** Fast operational
action is followed by proper SDD integration; drift and debt are routed,
not absorbed; and the observations, calibrations, and deferred items the
track has accumulated since Phase 1 are assembled into the next cycle's
inputs rather than scattered.

The team working in this phase is typically small (1–5 people). AI is
the force multiplier — not the decision-maker. Human checkpoints guard
every consequential action.

### What Is Different About Existing-Project Phase 7 Work

Three shifts matter, and they shape every prompt and every artifact:

1. **From first launch to release into an operational reality.** The
   greenfield variant takes a system live for the first time. The
   existing project already ships: it has versions in use, consumers
   with expectations, a release cadence, and — for library-shaped
   subjects — a registry (npm, crates.io, PyPI) instead of a server
   fleet. This toolkit treats **release-shaped deployment** (publish,
   tag, changelog, release-evidence artifact, consumer advisories) as
   first-class alongside **service-shaped deployment** (deploy, health
   checks, traffic). The shape is declared at Step 01 and drives which
   template branches apply — including recall vs rollback: a published
   package version cannot always be unpublished; the recall path is
   deprecation + advisory + patched release, planned before it is
   needed.

2. **From invented operations to reconciled operations.** The project
   already has operational habits — someone watches CI, someone triages
   issues, someone publishes releases. Runbooks and routines **codify
   the existing practice first** (provenance tags [EXISTING-CODIFIED] /
   [EXTENDED] / [NEW], inherited from Phase 4), then extend where the
   cycle's changes added surface (new touchpoints to watch, new
   artifacts to verify, new failure modes to respond to). An invented
   operations manual that ignores how the team actually operates will
   be ignored in turn.

3. **From open-ended evolution to the next improvement cycle.** The
   greenfield variant's evolution loop is open-ended. The
   existing-projects track is built around improvement cycles — it
   began with a Current-State report and an Improvement Plan, and it
   ends by preparing the next one. Step 09 assembles the **Next-Cycle
   Package**: the deferred deprioritizations due for re-elevation (e.g.
   a Phase 2 Operations deferral), the calibrated cost-model multipliers
   (BELIEVED → ESTIMATED → MEASURED as production cycles accrue), the
   fired watch-triggers, the accumulated drift and debt candidates, and
   the new objectives operations surfaced. The framework is a cycle —
   and in this track, the cycle has a concrete re-entry point: the
   Phase 1/2 toolkits, fed with this package.

These three shifts produce a ten-step toolkit (vs the greenfield
variant's 8 prompts, plus the track's step-00/step-01 scaffolding).

---

## The SDD Cycle in This Phase

Phase 7 applies the SDD cycle at two grains:

- **The phase itself**: Specify (validate the Phase 6 inputs; confirm
  launch readiness) → Plan (the release execution and the standing-loop
  cadences) → Detail (the instruction sets and registries) → Task
  (per-release and per-cadence executions) → Implement (ship, operate,
  evolve — continuously).
- **Every evolution item**: a change that re-enters earlier phases runs
  their SDD cycles; a fast operational fix is followed by proper SDD
  integration (specified, tested, scored, verified after the pressure
  passes) — every bypass is a tracked debt item until integrated.

Phase 7 is **continuous**: Stage 1 recurs per release; Stages 2–3 are
standing loops on cadences and triggers. There is no completion — there
is steady state, punctuated by next-cycle re-entries.

---

## The Six Core Principles — Applied to Phase 7 (Existing Projects)

Steady-state mode: continuous monitoring, continuous enforcement,
continuous improvement — under the weights inherited from Phase 2
(noting that next-cycle Phase 2 may re-weight; the Next-Cycle Package
carries the re-elevation candidates).

### Security
Continuous dependency scanning and advisory monitoring through the
project's existing security tooling; the carried risks from Phase 6
watched per their bounds and timelines; incident runbooks maintained and
exercised; for published packages: supply-chain posture (provenance,
signing, 2FA) operated per the release discipline.

### Maintainability
The frozen documentation baseline stays current — every change triggers
the DOC-NN maintenance process; the queryability standard applies
continuously; runbooks that reference changed components are flagged;
debt stays managed rather than accumulating.

### Economics
Actual costs and effort tracked against the calibrated cost model; the
multiplier calibration continues (ESTIMATED → MEASURED after 2–3 cycles
of data); divergences update the model and feed the Next-Cycle Package.

### Operations
Phase 7 is this principle's home territory — and in this track, the one
Phase 2 may have explicitly deprioritized. Operate what Phase 3 designed
and Phase 5 built (the touchpoints, the release evidence); track release
frequency, rollback/recall exercises, incident response; and carry the
deferral's re-elevation into the Next-Cycle Package rather than silently
expanding scope now.

### Scoring & Metrics
The scorecard is a **live dashboard**, not a periodic report: the
operational scorecard refreshes on cadence and after material incidents,
against the Phase 6 baseline; regressions are flagged when they occur
and routed as drift findings.

### Correctness Verification
Conformance checks against the Phase 4 contracts run on a schedule and
per release; drift detection catches divergence; formal models for
designated components are maintained alongside the code and re-checked
when it changes.

---

## Multi-Repo Evidence Scoping

*Inherited from Phases 1–6.* The classification continues. Phase 7
addition: **consumers** of a released library are neither subject nor
peer — operational signals from consumers (issues, advisories,
integration failures) are drift/debt inputs routed through the Stage 2
loops, not obligations to operate consumer systems.

---

## Code Access and Operational Tooling Calibration

*Inherited, with the Phase 7 sharpening.* Stage 1 executes releases and
Stage 2 operates loops — the Step 00 inventory covers release machinery
(registry credentials posture — never printed or logged; CI/CD access;
tag/publish capability), monitoring access, scanner scheduling, and the
patch-mediated fallback where AI cannot execute directly. Every
consequential action in an instruction set sits behind a **human
checkpoint** regardless of access mode.

---

## The Principle Scorecard — Inherited Through Phase 6, Kept Live By Phase 7

Phase 7 inherits the weights (Phase 2 Step 02, unchanged — next-cycle
Phase 2 may re-weight) and the **Phase 6 refresh as the launch
baseline**. Step 07 produces the **launch refresh** (immediately after
the first deployment: are the production actuals consistent with the
audit evidence?) and then **ongoing refreshes** on cadence and after
material incidents. The track's aggregation and target-distribution
disciplines continue. A refresh below baseline is a drift finding
(DR-NN) with routing — the scorecard does not freeze at release.

---

## The Feedback Model: Channel 1 + Cycle-Backs (No Terminal Gate)

Phase 7 has **no terminal gate and no next phase**. The escalating
amendment-package pattern (Phases 3–6) does not continue. Two mechanisms
replace it:

### Channel 1: Upstream Toolkit Gaps (via Step 01)

The two-scope split, inherited unchanged: Phase 7 local gaps vs upstream
toolkit gaps (queued for the responsible toolkit's revision;
non-blocking).

### Cycle-Back Triggers (CB-NN; via Steps 06, 07, 08, 09)

Operational and evolution findings whose resolution lies upstream are
recorded as **cycle-back triggers** and routed to the responsible
earlier phase — through its own toolkit, at the appropriate grain:

| Finding | Routes To |
|---------|-----------|
| Specification drift (Step 06) | Implementation fix (Phase 5 loop discipline) or specification amendment (Phase 4); or a documented accepted exception |
| Scorecard regression (Steps 06–07) | The phase responsible for the regressed principle |
| Compliance drift / new requirement (Step 06) | Phase 1 research → the relevant phases |
| Prioritized technical debt (Step 08) | Phase 5 (implementation) + Phase 6 (audit); Phase 3/4 first if architectural |
| New feature / change request (Step 09) | An abbreviated or full SDD cycle through the relevant phases |
| Architectural tension (Step 09) | Phase 3 (design) + Phase 4 (architecture) |
| Accumulated cycle-scale needs (Step 09) | **The next improvement cycle — re-enter the Phase 1/2 toolkits with the Next-Cycle Package** |

The distinction that matters: a **single change** cycles back through
the specific phases it needs (abbreviated where the blast radius is
small); an **accumulation** — many deferrals, a re-weighting due, a
changed objective — is next-cycle-scale and goes into the Next-Cycle
Package rather than being retrofitted piecemeal.

The front gate is Step 02's launch-readiness determination: **GO /
CONDITIONAL GO / NO-GO** (NO-GO routes to fixing prerequisites or
re-entering Phase 6 if the authorization no longer holds).

---

## Living-Registry ID Conventions

Phase 7 produces continuously-maintained registries, not forward-cited
constraints. Registries are **living documents**: append and update
entries; never silently rewrite history.

| ID Series | Registry / Artifact | Source Step |
|-----------|---------------------|-------------|
| **RB-NN** | Operational runbooks (provenance-tagged) | Step 05 |
| **DR-NN** | Drift findings (tagged: spec / scorecard / compliance) | Step 06 |
| **TD-NN** | Technical-debt items (including every SDD bypass) | Step 08 |
| **CB-NN** | Cycle-back triggers (routing to an earlier phase or the next cycle) | Steps 06, 07, 08, 09 |

Phase 7 consumes the prior-phase IDs as reference standards (the Phase 4
contracts and SP/SEC/TB/DA/DOC/GOV registers, the Phase 3 touchpoints,
CS-NN, M-NN) and establishes no new forward-cited constraint series.
Carried risks inherited from Phase 6 §5 keep their identities and are
tracked to closure in the Stage 2 loops. ALWAYS qualify cross-phase step
references (e.g. "Phase 6 Step 10", "Phase 5 Step 06") — this toolkit
has its own steps 00–09.

---

## Behavioral Rules

These rules apply to every AI session in this phase.

**Declare the deployment shape and honor it.**
Release-shaped (publish/tag/evidence/advisory; recall = deprecation +
advisory + patched release) or service-shaped (deploy/health/traffic;
rollback = revert + verify) — declared at Step 01, driving every Stage 1
template branch. A library is not a degenerate service; its release
realities (immutable published versions, consumer pull cadence) are
first-class.

**Observe from day one, and actually look.**
The touchpoints built in Phase 5 activate at deployment — and
instrumentation only pays off if reviewed. Establish the operational
routines at launch: metric reviews, trend checks, defined alert
responses. Observable on paper is not observable in practice.

**Runbooks are orchestration scripts, not prose.**
Trigger condition → ordered diagnostic/action steps → decision branches
→ **human checkpoints** before consequential actions → escalation paths.
AI executes through tool connections; humans authorize at the
checkpoints.

**Reconcile with existing practice; tag provenance.**
Codify how the team actually operates ([EXISTING-CODIFIED]) before
extending ([EXTENDED]) or adding ([NEW]). Runbooks and routines that
ignore actual practice will be ignored.

**Keep the runbook feedback loop real.**
Every incident that exercises a runbook triggers a review — coverage,
correctness, checkpoint placement — producing updates or confirmations.
Flag runbooks that reference components or procedures the system no
longer has.

**Rollback/recall is routine, not emergency.**
Readied at every release with defined triggers, procedure, and
verification — including the release-shaped recall path with its
registry realities (deprecation policies, unpublish windows, advisory
channels). AI monitors triggers and proposes; humans authorize.

**Detect drift before it is a crisis.**
Scheduled conformance checks against the Phase 4 contracts; scorecard
actuals against thresholds; compliance controls verified on schedule
with evidence generated continuously (where obligations exist). Classify
and route every drift finding — implementation fix, specification
amendment, or documented accepted exception — never absorb it.

**Manage the carried risks to closure.**
The Phase 6 §5 Carried-Risk Register arrives with bounds, owners, and
timelines. Stage 2 loops track each item; a lapsed timeline is a drift
finding, not a quiet extension.

**Manage debt; do not accumulate it.**
A living TD-NN inventory characterizes each item (what, where, affected
principle, consequence of inaction, three-quantity effort estimate).
Prioritize against the weighted principles; resolve through the SDD
cycle to the same standard as new development.

**Fast action is followed by proper integration.**
Urgent fixes may bypass the SDD cycle under pressure — but every bypass
becomes a TD-NN item immediately, and the integration (specify, test,
score, verify) is scheduled and enforced. "Fix now, clean up later"
works only when "later" is tracked.

**Evolve through the framework, with architecture review.**
Every change gets an impact assessment (modules, contracts, scorecard);
significant changes route through Phase 3/4 review; abbreviated cycles
are legitimate for small changes, but "abbreviated" is a documented
routing decision, not a shrug.

**Assemble the next cycle; do not scatter it.**
Deferred re-elevations, calibrated multipliers, fired watch-triggers,
drift/debt accumulations, and new objectives collect in the Step 09
Next-Cycle Package — the structured input for re-entering the Phase 1/2
toolkits when the next improvement cycle begins.

**Honor the safety gates when executing.**
Stage 1 and runbook executions touch production and registries: human
checkpoints before publish/deploy/rollback/recall and any destructive or
hard-to-reverse action; never print, log, or commit secrets or registry
credentials; elevated privileges are STOP-and-ask; prefer reversible
actions; no destructive git or registry operations without explicit
direction.

**Re-verify currency at each step start.**
*Inherited.* The concurrent-release rule matters most here: parallel
tracks shipping between the Phase 6 gate and the Step 02 launch check
are exactly the currency events the rule exists for.

**Structure all outputs for AI consumption.**
Registries, reports, and instruction sets are consumed by future
operational sessions and by the next cycle's Phase 1: consistent
headers, tables, IDs on all rows, explicit cross-references, dated
entries.

---

## Phase 7 (Existing Project) Artifacts

Ten steps. Stage 1 (Steps 02–04) recurs per release; Stage 2 (05–07) and
Stage 3 (08–09) are standing loops.

| Step | Artifact | Type | Cadence / Trigger |
|------|----------|------|-------------------|
| 00 | Toolset Augmentation Document | Action (living document) | Once per Phase 7 entry; amended as capabilities shift |
| 01 | Phase 6 Input Validation Report + Validation Gap Register | Interview → Action | Once per Phase 7 entry |
| 02 | Launch-Readiness Confirmation (GO / CONDITIONAL GO / NO-GO) | Evaluation (the front gate) | Per release, before each deployment |
| 03 | Deployment Execution & Verification (instruction set + Deployment Record) | Action (AI-executable instruction set) | Per release |
| 04 | Rollback & Recall Procedure (instruction set) | Action (AI-executable instruction set) | Readied per release; executed on trigger |
| 05 | Operational Runbooks (RB-NN register + runbooks) | Action (instruction sets; living registry) | Maintained continuously; executed per incident; reviewed post-incident |
| 06 | Drift Detection & Continuous Compliance (DR-NN register) | Evaluation (recurring) | Scheduled (periodic) + per significant change |
| 07 | Operational Scorecard (launch refresh + ongoing refreshes) | Action + Evaluation (recurring) | At launch; then scheduled + after material incidents |
| 08 | Technical Debt Management (TD-NN living inventory) | Action + Evaluation (living registry) | Continuous capture; scheduled prioritization review |
| 09 | Evolution & Next-Cycle Orchestration (CB-NN register + Next-Cycle Package) | Action (routing + assembly) | On demand per change; package assembled when the next cycle approaches |

---

## The Cadence & Trigger Map (replaces the dependency graph)

```
Phase 6 Deployment Readiness Report (READY / CONDITIONALLY READY)
+ Carried-Risk Register + frozen docs + compliance matrix + performance
baselines + scorecard refresh + calibration table
   │
   ▼
Step 00: Building Block Discovery ─── Step 01: Phase 6 Input Validation
   │   (release machinery, monitoring,      (blocking checks; two-scope
   │    registry posture, fallbacks)         gap register — Channel 1)
   ▼
═══ STAGE 1: DEPLOYMENT (per release — ordered) ═══
Step 02: Launch-Readiness Confirmation ── NO-GO → fix prerequisites /
   │   (GO / CONDITIONAL GO)                       re-enter Phase 6
   ▼
Step 03: Deployment Execution & Verification
   │   (publish/deploy per declared shape; evidence artifact emitted;
   │    observability active from day one)
   ▼
Step 04: Rollback & Recall Procedure (readied; fires on trigger)
   │
   ▼  the release is LIVE
═══ STAGE 2: CONTINUOUS OPERATIONS (standing loops) ═══
   ├─ Step 05: Operational Runbooks   — continuous; per-incident; post-incident review
   ├─ Step 06: Drift & Compliance     — scheduled + per-change; DR-NN routed
   └─ Step 07: Operational Scorecard  — launch refresh; then scheduled + per-incident
═══ STAGE 3: EVOLUTION (triggered) ═══
   ├─ Step 08: Technical Debt         — continuous capture; scheduled review
   └─ Step 09: Evolution & Next-Cycle — per change request; package on cycle boundary
        │
        └── CYCLE-BACKS (CB-NN):
              single change → abbreviated/full SDD re-entry (Phases 1–6)
              architectural tension → Phase 3 + Phase 4
              compliance requirement → Phase 1 → relevant phases
              debt resolution → Phase 5 + Phase 6
              ACCUMULATION → the Next-Cycle Package → re-enter the
              Phase 1/2 toolkits (the next improvement cycle)
```

### The Minimum Viable Path

All ten steps are standing capabilities for any deployed, evolving
system. What varies is **cadence and depth**, plus one section-level
conditional: the compliance section of Step 06 runs only where
obligations exist (per the Phase 6 compliance matrix); otherwise it is
marked Not applicable while specification and scorecard drift detection
still run. A small library runs lighter loops — less frequent drift
checks, a smaller debt inventory, simpler runbooks — but it runs them.

---

## Output Standards

Phase 7 produces two kinds of artifacts.

**AI-executable instruction sets** (Steps 03, 04, 05) must:

- [ ] State an explicit trigger condition
- [ ] Give ordered, specific, executable steps (not vague guidance)
- [ ] Mark decision branches with clear criteria — including the
      release-shaped vs service-shaped branches where both are templated
- [ ] Place explicit human checkpoints before consequential or
      hard-to-reverse actions (publish, deploy, rollback, recall,
      deprecation, data changes)
- [ ] Define escalation paths when the script cannot resolve the
      situation
- [ ] Be versioned and maintained via their feedback loops

**Reports and registries** (Steps 01, 02, 06, 07, 08, 09) must:

- [ ] Carry the appropriate living-registry IDs (RB/DR/TD/CB-NN) with
      dated, append-style entries
- [ ] Record cycle-back routing for any finding whose resolution lies
      upstream — or its Next-Cycle Package assignment
- [ ] Track the Phase 6 carried risks to closure (bounds, owners,
      timelines; lapses are drift findings)
- [ ] Include a Confidence Summary and honor the safety conventions

All Phase 7 artifacts, before they are relied upon:

- [ ] The deployment shape is declared and consistently honored
- [ ] Observability is verified live (Stage 1) and actually reviewed
      (Stage 2 routines)
- [ ] The scorecard stays current as a live dashboard; regressions are
      DR-NN findings with routing
- [ ] Every drift, debt, and evolution finding is routed, never absorbed
- [ ] Fast-action bypasses are captured as TD-NN items with scheduled
      integration
- [ ] The Next-Cycle Package accumulates as items arise — not
      reconstructed from memory at the cycle boundary
- [ ] All artifacts are version-stamped with a Version History table

---

## Common Pitfalls

**Treating a library release as a degenerate service deployment.**
Publish is not deploy: published versions are immutable, consumers pull
on their own cadence, and recall is deprecation + advisory + patched
release. The structural defense: the declared deployment shape and the
release-shaped template branches in Steps 03–04.

**Observable on paper, blind in practice.**
Instrumentation without review routines is decoration. The structural
defense: the day-one operational routines established at Step 03 and
exercised through the Stage 2 loops.

**Runbooks that rot.**
Runbooks describing a system that no longer exists are dangerous. The
structural defense: Step 05's mandatory post-incident review and
changed-component flagging.

**Letting carried risks quietly lapse.**
Phase 6's accepted risks came with bounds and timelines. The structural
defense: Stage 2 tracking with lapses surfacing as DR-NN findings.

**Debt accumulation through "quick fixes."**
Every SDD bypass is potential debt. The structural defense: Step 08's
capture-every-bypass rule and scheduled, enforced integration.

**Evolution without architecture review.**
Features added without review recreate what Phase 4 prevents. The
structural defense: Step 09's impact assessment and the Phase 3/4
cycle-back for significant changes.

**Compliance as a one-time event.**
Passing at release does not keep a system compliant. The structural
defense: Step 06's scheduled control verification and continuous
evidence (where obligations exist).

**Retrofitting cycle-scale needs piecemeal.**
Many small cycle-backs that share a root cause are a next-cycle signal.
The structural defense: the accumulation rule and the Next-Cycle
Package.

**Letting the scorecard freeze.**
A frozen scorecard cannot catch production regression. The structural
defense: Step 07's cadence + per-incident refreshes against the Phase 6
baseline.

**Treating Phase 7 as a one-pass phase with an end.**
Phase 7 is continuous. The structural defense: the cadence-and-trigger
model — standing loops, not a sequence with a finish line.

---

## The Framework Continues — And the Track Loops

Phase 7 has no terminal gate and no next phase. It operates
continuously, with the Core Principles, the live scorecard, and the SDD
cycle providing structure. For the existing-projects track specifically,
the loop closes concretely: when the accumulated needs justify it, the
**Next-Cycle Package** (Step 09) re-enters the track's own Phase 1
toolkit — a fresh Current-State Information Report grounded in the
now-changed system — and Phase 2 produces the next Improvement Plan,
with re-weighted principles, calibrated multipliers, and the deferred
items finally due. The toolkit family is a long-term asset: each cycle
dogfoods it, revises it, and hands the next cycle a sharper instrument.

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Phase 7 existing-projects instructions file. Three shifts from the greenfield Phase 7 variant (release into an existing operational reality with release-shaped deployment — publish/tag/evidence/advisory and the recall path — first-class alongside service-shaped; operations reconciled with existing practice via provenance-tagged runbooks; evolution feeding the track's next improvement cycle through the Step 09 Next-Cycle Package that re-enters the Phase 1/2 toolkits). Ten-step structure: track scaffolding (00–01 with blocking checks on the Phase 6 gate), Stage 1 deployment per release (02 front gate GO/CONDITIONAL GO/NO-GO; 03 execution instruction set; 04 rollback & recall instruction set), Stage 2 standing operations (05 runbooks RB-NN; 06 drift & compliance DR-NN; 07 operational scorecard as live dashboard), Stage 3 evolution (08 debt TD-NN incl. every SDD bypass; 09 evolution & next-cycle CB-NN + package). No terminal gate: Channel 1 + cycle-back triggers replace amendment packages; the accumulation rule separates single-change re-entry from next-cycle-scale needs. Carried-risk tracking to closure; cost-model calibration continued toward MEASURED; instruction-set output discipline with human checkpoints; safety gates for registry/production operations. |

---

*Part of the Phase 7 (Existing Projects) Deployment & Evolution Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion files: step-00 through step-09 prompts in this directory*
