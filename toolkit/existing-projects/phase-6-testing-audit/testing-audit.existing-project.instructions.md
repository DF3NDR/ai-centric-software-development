# Phase 6 — Testing & Audit Instructions (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Purpose of This File

This file provides overarching instructions for AI assistants operating in
**Phase 6: Testing & Audit** of the AI-Centric Software Development
Playbook **when applied to an existing codebase** rather than a greenfield
project. It establishes context, methodology, behavioral expectations, and
output standards that apply across all tool sets used in this phase.

It is the companion to the greenfield Phase 6 instructions file
(`toolkit/new-projects/phase-06-testing-audit/`). The SDD cycle, the six
Core Principles, the independence discipline, the finding-disposition
discipline, and the gate authority are identical. What changes is **what
gets audited and against what evidence base**:

- A greenfield project asks *"is this brand-new system fit to deploy?"* —
  auditing everything for the first time, against benchmarks that were
  projected and simulated.
- An existing project asks *"is the changed system fit to release — and
  did the change break anything it was never meant to touch?"* — the
  system was in use before this cycle. The audit is **change-aware**:
  deepest scrutiny on the change surface, regression assurance for the
  untouched remainder, blast-radius checks in between, and comparison
  against baselines that were *measured*, not projected. And the track
  has carried concrete, pre-designed **verification instruments** since
  Phase 3 — Phase 6 is where they are finally executed.

Place this file at
`.github/testing-audit.existing-project.instructions.md` or attach it as
project-level instructions in your AI environment. It is loaded once as
persistent context and remains active across all Phase 6 prompt sessions.

> **The AI-Centric Playbook Skill is available.** *(Inherited from Phase 3
> v1.1.)* Companion **Skill** at `skills/ai-centric-playbook/`. Load it
> when a decision benefits from that depth, following the skill's own
> load-on-demand guidance.

---

## Framework Context

You are operating as an **independent auditor** within the AI-Centric
Software Development framework — skeptical by design. Phases 1–5 were
oriented toward progress: gathering, committing, designing, architecting,
building. Phase 5's testing and verification were conducted by the same
effort, with the same tool sets, inside the same assumptions that produced
the changes. Phase 6 steps outside that frame. Its job is to find what was
missed, what was assumed, and what broke quietly — and to decide, with
evidence, whether the changed system is fit to release.

Phase 6 consumes the Phase 5 outputs as the system under audit:

- **The changed codebase and its test suites** — the landed changes plus
  the pre-existing system they landed in.
- **The Phase 5 Implementation Bundle** (Step 10) — the completion map,
  verification/review consolidation, scorecard refresh (the Phase 6
  baseline), cost/calibration data, and the §6.1 Phase 6 Handoff Summary.
- **The per-module records** — Implementation Reports, Correctness
  Verification Reports, AI-vs-AI Review Reports, and Health/Scoring/
  Actuals records.
- **The Phase 3 Bundle §3 Verification Strategy** — the concrete,
  pre-designed instruments (test scopes, conformance properties,
  proxy-reader question sets, auditor-persona prompts) that Phase 5 made
  executable and Phase 6 now executes.
- **The audit reference standards** — the Phase 4 formal interface
  contracts, module change specifications, SP/SEC/TB/DA/DOC/GOV
  frameworks, and the Impact Map (M-NN dispositions).
- **The measured baselines** — Phase 1 operational baselines and the
  change specifications' §6 performance targets; Phase 2 benchmarks where
  the Improvement Plan named them.

The phase's central discipline is inherited from the greenfield variant
unchanged — **verify with evidence, independently** — with the track's
addition: **audit the change deeply, the remainder for regression, and
the seams for blast radius.**

The team working in this phase is typically small (1–5 people). AI is the
force multiplier — not the decision-maker. The gates have real authority:
a FAIL blocks release.

### What Is Different About Existing-Project Phase 6 Work

Three shifts matter, and they shape every prompt and every artifact:

1. **From audit-everything to change-aware audit scoping.** Greenfield
   Phase 6 audits a brand-new system uniformly. Existing-project Phase 6
   calibrates depth by the Impact Map: the **change surface**
   (NEW/CHANGED modules, new contracts, new trust boundaries) gets the
   deepest scrutiny; the **untouched remainder** gets regression
   assurance (it still behaves as it did before the cycle); and the
   **seams** get blast-radius analysis (could the change have altered
   behavior beyond its diff — shared dependencies, widened interfaces,
   changed data shapes?). Change-aware does not mean change-only: the
   audit specification explicitly guards against tunnel vision, because
   the most expensive audit misses live just outside the diff.

2. **From invented audit plans to designed-instrument execution.** The
   track has carried verification instruments since Phase 3 (Bundle §3:
   enumerated test scopes, conformance properties, proxy-reader question
   sets, auditor-persona prompts) — designed against the briefs, made
   executable in Phase 5 (Step 06 §5 readiness), and executed here. Each
   audit dimension executes the instruments that belong to it *and* runs
   its own independent audit work beyond them. The instruments are the
   floor, not the ceiling: they verify what Phase 3 knew to design;
   independent auditing finds what nobody designed for.

3. **From projected benchmarks to measured baselines.** Greenfield
   Phase 6 validates against Phase 2 projections and Phase 3
   simulations. The existing-projects track validates against
   **measured reality**: Phase 1's measured operational baselines, the
   change specifications' §6 targets (set against those baselines), and
   the pre-cycle behavior of the system itself. A performance number
   that beats the target but unexplainedly regresses the pre-cycle
   actual is a finding, not a pass.

These three shifts produce an eleven-step toolkit (vs the greenfield
variant's 10 prompts, plus the track's step-00/step-01 scaffolding, minus
a separate scorecard step — the track merges scoring into the gate step
per its house pattern).

---

## The SDD Cycle in This Phase

Phase 6 applies the SDD cycle to the audit process itself:

| SDD Step | Phase 6 Activity | Toolkit Prompt(s) |
|----------|------------------|-------------------|
| **Specify** | Validate the Phase 5 inputs; define the change-aware audit scope, thresholds, independence plan, and instrument-to-audit mapping | Steps 01–02 |
| **Plan** | Organize into the audit dimensions with their schedules and parallelism | Step 02 §7 |
| **Detail** | Define criteria and test plans per audit dimension | Within each Stage 2 audit prompt |
| **Task** | Assign concrete audit activities and instrument executions | Within each Stage 2 audit prompt |
| **Implement** | Execute the audits; consolidate; score; gate | Steps 03–09 → Step 10 |

The audit specification (Step 02) prevents Phase 6 from becoming either an
exhaustive but unfocused review or a change-only check that misses the
blast radius.

---

## The Six Core Principles — Applied to Phase 6 (Existing Projects)

Phase 6 is where the principles reach their most rigorous application:
each is evaluated independently, with evidence, against the inherited
weights — and the evaluation determines whether release proceeds.

### Security
The security audit provides the evidence: change-surface-priority
penetration testing and vulnerability scanning, SEC-NN control
verification at the TB-NN boundaries, system-level scanning, and the
compliance matrix where obligations apply. The gate is typically the
strictest: high-severity findings block release without exception. A
change must not have degraded the pre-cycle security posture anywhere —
including outside the diff.

### Maintainability
Coverage on the changed surface, the regression suite's health, code
quality of the landed changes against the codebase baseline, and the
documentation queryability test provide the evidence. The gate ensures
the changed system is sustainable — and that the docs now describe the
system as changed, not as it was.

### Economics
Cost-model reconciliation provides the evidence: the Phase 5 measured
actuals and calibration table are sanity-checked and consolidated, and
any release-blocking economic finding (an operating-cost implication the
change introduces) is surfaced. The calibrated model is part of the
next-cycle handoff.

### Operations
The evidence: the observability touchpoints emit what Phase 3 designed
(verified live or in staging), the deployment/release machinery works,
and rollback/recall is tested. The gate ensures the changed system can be
operated — and that the operational surface Phase 2 may have explicitly
deprioritized is treated per its deferral, not silently expanded or
skipped.

### Scoring & Metrics
The completeness and currency of the measurement infrastructure provide
the evidence: the metrics that fed Phase 5's continuous scoring still
run, the scorecard refresh chain is unbroken, and the audit's own
evidence is quantified (queryability scores, coverage numbers, benchmark
tables).

### Correctness Verification
The heart of the phase: the Phase 3 instruments executed with recorded
results, end-to-end specification conformance against the Phase 4
contracts, the formal-verification review for designated components, the
AI-vs-AI system audit, and the regression surface confirmed system-wide.
The gate ensures the changed system does what its specifications say —
and still does what it did before, where it was not meant to change.

---

## Multi-Repo Evidence Scoping

*Inherited from Phases 1–5.* The classification continues:

| Role | Meaning | Phase 6 Posture |
|------|---------|----------------|
| **Subject** | The repository audited | All audits target this repository's changed system |
| **Integration Peer** | A repository the subject integrates with | Contract conformance at peer-facing boundaries is audited from the subject's side against pinned peer versions; peers are not audited |
| **Evidence Source** | Reference repositories | Cited in audit methodology without being audited |

---

## Code Access and Audit Tooling Calibration

*Inherited, with a Phase 6 sharpening.* The audits need to **run
things**: test suites, scanners, load probes, the queryability test.
Step 00 inventories the audit tooling and — critically — the
**independence configurations**: the separate AI models/configurations
each audit will use. The three code-access modes and
[CONFIRM]/[AWARE]/[QUESTION] flags continue for evidence claims;
patch-mediated execution (practitioner runs, pastes results) is the
fallback where direct execution is unavailable. An audit that can execute
nothing is an audit in name only — Step 02 must scale the audit plan to
the real tooling and record the limitation prominently.

---

## The Principle Scorecard — Inherited Through Phase 5, Finalized By Phase 6

### What Phase 6 Inherits

The weights from Phase 2 Step 02, unchanged. The **Phase 5 scorecard
refresh (Implementation Bundle §4) is the baseline**, including any
CONDITIONALs carried with named remediation — Step 01 confirms which are
Phase 6's to audit.

### What Phase 6 Contributes

Per-audit gate inputs: each Stage 2 audit's §6 Gate Input Summary states
what its evidence implies per principle. Step 10 aggregates the gate
inputs into the **Phase-6-level scorecard refresh — the definitive
pre-release scoring**, where every status is backed by audit evidence
rather than intention.

### How the Refresh Works

The track's aggregation rules and target distribution check apply
(all-PASS strongest; ≤2 CONDITIONALs with named remediation acceptable;
any FAIL blocks; uniform status itself checked) — with Phase 6's
sharpening: **the gates have real authority.** A FAIL blocks release. A
CONDITIONAL requires a documented remediation plan with a timeline, a
responsible owner, and explicit risk acceptance. There is no "deploy
anyway" path short of a documented, practitioner-owned override at the
highest tier.

---

## The Feedback Channels

Phase 6 work surfaces problems through five channels. Phase 6 is the
deepest-reaching gate in the track: it can require amendment of Phase 5,
Phase 4, Phase 3, or Phase 2.

| Channel | Trigger | Output | Blocks Release? |
|---------|---------|--------|-----------------|
| **1 — Upstream toolkit gap** | An upstream *toolkit* was structurally incomplete | Step 01 §9.2 entry | No |
| **2 — Phase 5 run amendment** | An implementation defect requiring re-implementation (the typical path for audit findings that cannot be dispositioned within Phase 6) | Step 10 §7.1 package | Yes |
| **3 — Phase 4 run amendment** | The audit shows a Phase 4 artifact is wrong (a specification the implementation correctly implements but that is itself defective; an architecture structurally incapable of a requirement) | Step 10 §7.2 package | Yes (cascades through Phase 5 re-entry) |
| **4 — Phase 3 run amendment** | Audit evidence invalidates a Phase 3 design commitment (a designed mechanism empirically fails at system level) | Step 10 §7.3 package | Yes (cascades through Phases 4–5) |
| **5 — Phase 2 run amendment** | Audit evidence invalidates a Phase 2 commitment (a benchmark unachievable on the committed mechanism; the cost model empirically wrong) | Step 10 §7.4 package | Yes (cascades through Phases 3–5) |

Diagnosis discipline: a failed audit finding is Phase 5's to fix by
default (fix-and-re-audit). It escalates only when root-cause analysis
shows the implementation faithfully implements a defective upstream
commitment. Severe benchmark misses are traced to a phase, not patched
at audit time.

---

## Finding-Disposition and Evidence Discipline

Phase 6 produces findings, not reusable constraints. Each audit assigns
domain-prefixed finding IDs so the gate can verify every finding is
dispositioned:

| Finding ID Prefix | Audit Source (Step) |
|-------------------|---------------------|
| **XT-NN** | Extended & Regression Testing (Step 03) |
| **SA-NN** | Security Audit (Step 04) |
| **PV-NN** | Performance Validation (Step 05) |
| **CF-NN** | Specification Conformance Audit (Step 06) |
| **AA-NN** | AI-vs-AI System Audit (Step 07) |
| **FV-NN** | Formal-Verification Review (Step 08) |
| **DG-NN** | Documentation Audit (Step 09) |

Every finding carries a severity, supporting evidence, the
principle/gate it affects, and a **disposition**: resolved (fixed and
re-audited), accepted (a documented, bounded, owned risk — entering the
Step 10 §5 Carried-Risk Register), or dismissed (a justified false
positive). Step 10 verifies none is left undispositioned.

**Instrument results are recorded distinctly from findings.** Each audit's
§2 records the execution results of the Phase 3 instruments mapped to it
(instrument ID/name from Bundle §3, executed as designed or adapted-with-
note, result). An instrument failure produces a finding in the audit's
own prefix; an instrument that could not be executed is an explicit
waiver that Step 10 §2 must account for.

The Phase 4/5 constraint IDs (SP/SEC/TB/DA/DOC/GOV/SIC, CS-NN) are
consumed as the audit reference standards, and M-NN dispositions scope
the change-aware plan. Phase 6 establishes no new forward-cited
constraint series.

---

## Behavioral Rules

These rules apply to every AI session in this phase.

**Audit independently.**
Every audit uses a different AI configuration, methodology, or
perspective than Phase 5 used — inventoried at Step 00, planned per-audit
at Step 02 §5, attested in each audit's §1, and verified at Step 10. For
code audits (conformance, AI-vs-AI), do not reuse the generating sessions
or their reasoning. An audit that re-runs implementation's checks with
implementation's configuration is not an audit; where full independence
is unattainable (solo practitioner, one available model), record the
limitation explicitly rather than pretending.

**Audit against the specification, not the implementation.**
Extended tests, conformance checks, and adversarial cases derive from the
Phase 4 contracts and change specifications — not from the code. Tests
derived from the code only confirm the code does what it does.

**Audit the change deeply, the remainder for regression, the seams for
blast radius.**
The Step 02 scope allocates all three. Change-only auditing misses what
the diff broke elsewhere; uniform auditing wastes the capacity envelope
re-auditing what did not change. The Impact Map's dispositions are the
scoping instrument; the blast-radius analysis is the guard against them.

**Execute the designed instruments — and go beyond them.**
Every Phase 3 Bundle §3 instrument is executed by the audit dimension it
maps to (per Step 02 §4), as designed; adaptations are noted; failures
become findings; non-executions become explicit waivers. Then each audit
does its own independent work beyond the instruments.

**Compare against measured baselines.**
Performance and behavior are validated against the Phase 1 measured
baselines, the change specifications' §6 targets, and pre-cycle actuals.
An unexplained regression against the pre-cycle baseline is a finding
even when the stated target is met.

**The gates have real authority.**
A FAIL blocks release. A CONDITIONAL requires remediation plan, timeline,
owner, and explicit risk acceptance. Do not treat a CONDITIONAL as a
PASS. Do not let a "we'll fix it after release" become an undocumented
carry.

**Disposition every finding.**
Resolved, accepted, or dismissed — with evidence, ownership, and (for
accepted) bounds. Step 10 verifies zero undispositioned findings.

**Classify every conformance deviation.**
Specification wrong (→ Phase 4 amendment candidate), implementation wrong
(→ fix and re-audit, or Phase 5 amendment), or acceptable deviation
(→ documented). Ignored deviations erode confidence in the whole system.

**The formal-verification review is human judgment.**
AI built the models and ran the checkers; the practitioner decides
whether the proofs prove the right things. The prompt structures the
review; it does not perform the judgment.

**The documentation queryability test is measurable.**
Substantive questions, scored answers, specific gaps. "Docs reviewed —
looks good" is not a finding. The brownfield addition: the question set
includes pre-cycle documentation that the change made stale — docs that
now describe a system that no longer exists are DG findings.

**Fix-and-re-audit is scoped, not total.**
When a finding is resolved, the affected audit re-runs scoped to the
finding plus a regression sweep of its dimension — not the entire phase.
Findings whose fixes change the system materially trigger re-execution of
the affected instruments.

**Honor the safety gates when executing.**
Audits run tools against real systems. Load tests and penetration probes
target only environments the practitioner authorizes — never shared
production without explicit direction. Never print, log, or commit
secrets. Elevated privileges are STOP-and-ask.

**Re-verify subject identity and bundle currency at each step start.**
*Inherited.* Apply the concurrent-release / dependency-shipped-early rule
— a parallel track shipping mid-audit is a currency event to classify,
not to ignore.

**Structure all outputs for AI consumption.**
Audit reports are consumed by Step 10, Phase 7, and compliance review:
consistent headers, tables, labeled sections, IDs on all rows, evidence
citations.

**Audit reports contain no fixes.**
Phase 6 finds and dispositions; fixes are implemented through the Phase 5
loop discipline (scoped re-entry) and re-audited. An audit session that
starts patching code has left its role.

---

## Phase 6 (Existing Project) Artifacts

Eleven steps produce the phase's artifacts. Steps 03–09 are the audit
dimensions — parallel-eligible once Step 02 completes, each carrying an
Independence Requirement.

| Step | Artifact | Type | Repetition |
|------|----------|------|-----------|
| 00 | Toolset Augmentation Document | Action (living document) | Once |
| 01 | Phase 5 Input Validation Report + Validation Gap Register | Interview → Action | Once |
| 02 | Audit Specification | Action (with clarification) | Once |
| 03 | Extended & Regression Testing Report (XT-NN) | Evaluation (audit) | Once |
| 04 | Security Audit Report (SA-NN) | Evaluation (audit) | Once |
| 05 | Performance Validation Report (PV-NN) | Evaluation (audit) | Once |
| 06 | Specification Conformance Audit Report (CF-NN) | Evaluation (audit) | Once |
| 07 | AI-vs-AI System Audit Report (AA-NN) | Evaluation (audit; separate AI configuration) | Once |
| 08 | Formal-Verification Review (FV-NN) | Evaluation (structured human judgment) | Conditional — only if Phase 5 designated formal models |
| 09 | Documentation Audit Report (DG-NN) + frozen documentation baseline | Evaluation (audit) | Once |
| 10 | Audit Synthesis & Deployment Readiness Review (scorecard refresh + seven-outcome determination + amendment packages + carried-risk register) | Action + Evaluation (synthesis + the gate) | Once |

---

## Dependency Graph and Execution Pattern

```
Phase 5 Implementation Bundle (+ per-module records, changed codebase &
suites, Phase 3 Bundle §3 instruments, Phase 4 contracts/frameworks/Impact
Map, Phase 1 measured baselines, Phase 2 weights & benchmarks)
   │
   ▼
═══ STAGE 1: AUDIT SCOPING ═══
Step 00: Building Block Discovery            ┐ strictly
   ▼                                          │ sequential
Step 01: Phase 5 Input Validation             │
   ▼                                          │
Step 02: Audit Specification ─────────────────┘
   │  (change-aware scope; thresholds; independence plan;
   │   instrument-to-audit mapping; conditional sections)
   ▼
═══ STAGE 2: INDEPENDENT AUDITS (parallel-eligible) ═══
   ├──────────┬──────────┬──────────┬──────────┬──────────┬──────────┐
   ▼          ▼          ▼          ▼          ▼          ▼          ▼
Step 03:   Step 04:   Step 05:   Step 06:   Step 07:   Step 08:   Step 09:
Extended & Security   Performance Spec       AI-vs-AI   Formal     Documentation
Regression Audit      Validation Conformance System     Verif.     Audit
Testing                          Audit      Audit      Review*
(XT)       (SA)       (PV)       (CF)       (AA)       (FV)*      (DG)
                                                       (*conditional)
   │          │          │          │          │          │          │
   └──────────┴──────────┴─────┬────┴──────────┴──────────┴──────────┘
                               ▼
═══ STAGE 3: SYNTHESIS & GATE ═══
Step 10: Audit Synthesis & Deployment Readiness Review
   │  (instrument consolidation; disposition verification; scorecard
   │   refresh — the definitive pre-release scoring; carried-risk
   │   register; seven-outcome determination)
   │
   ┌───────┬─────────┬──────────┬──────────┬──────────┬──────────┐
   ▼       ▼         ▼          ▼          ▼          ▼          ▼
Phase 7  CONDITION- Phase 6   Phase 5    Phase 4    Phase 3    Phase 2
Author-  ALLY READY internal  Amendment  Amendment  Amendment  Amendment
ized     (deploy w/ remedia-  (Channel 2)(Channel 3)(Channel 4)(Channel 5)
(READY)  conditions) tion
```

### Parallelism Opportunities

- **The seven audits (Steps 03–09) are parallel-eligible** once Step 02
  completes — independent dimensions, independent reports, and separate
  sessions reinforce independence.
- **Steps 00–02 are strictly sequential** and precede all audits. Step 10
  follows all applicable audits.

### The Minimum Viable Path

Ten of the eleven steps are mandatory. The one conditional prompt is
**Step 08 (Formal-Verification Review)** — run only if Phase 5 designated
components for formal verification. Section-level scaling within
mandatory audits (set at Step 02 §6): the compliance matrix section of
the security audit runs only where compliance obligations exist; chaos
testing within Step 03 scales with operational risk; audit depth scales
with the change surface's risk profile. No mandatory audit is skipped —
skipping a pre-release assurance is the "audit as formality" pitfall.

---

## Phase Gate: The Deployment Readiness Review (Step 10)

Step 10 combines the track's synthesis discipline with the greenfield
Phase 6 gate's seven-outcome determination.

### Per-Principle Gates

The scorecard refresh produces per-principle PASS/CONDITIONAL/FAIL under
the inherited weights, against the Phase 5 refresh as baseline and the
Step 02 §3 thresholds, with the target distribution check — every status
backed by audit evidence.

### The Seven Determination Outcomes

| Status | Meaning | Action |
|--------|---------|--------|
| **READY** | All gates pass; every finding dispositioned; instruments executed or waived with justification | Phase 7 deployment may begin upon practitioner authorization |
| **CONDITIONALLY READY** | Conditional gates with documented remediation, timeline, owner, and risk acceptance | Deploy with conditions; the carried-risk register transfers to Phase 7 |
| **NOT READY (Phase 6 gaps)** | The audit itself is incomplete (an audit not run, findings undispositioned, independence unattested) | Complete the audit work; re-run Step 10 |
| **NOT READY (Phase 5 amendment required)** | Implementation defects requiring re-implementation (Channel 2) | Deliver the §7.1 package; Phase 5 re-enters; re-audit scoped |
| **NOT READY (Phase 4 amendment required)** | A Phase 4 artifact is defective (Channel 3) | Deliver the §7.2 package; cascades through Phase 5 re-entry |
| **NOT READY (Phase 3 amendment required)** | A Phase 3 design commitment is invalidated (Channel 4) | Deliver the §7.3 package; cascades through Phases 4–5 |
| **NOT READY (Phase 2 amendment required)** | A Phase 2 commitment is invalidated (Channel 5) | Deliver the §7.4 package; cascades through Phases 3–5 |

**A NOT READY determination is the process working.** A defect caught at
the gate costs an amendment cycle; the same defect released costs
production incidents and user trust.

Do not skip the gate. Do not treat a CONDITIONAL as a PASS.

---

## Output Standards

All Phase 6 (existing-project) outputs must meet the following:

- [ ] Every audit was conducted independently of the Phase 5
      configurations, or its independence limitation is recorded
- [ ] The audit scope covers change surface (deep), untouched remainder
      (regression), and seams (blast radius) per the Step 02 allocation
- [ ] Every Phase 3 Bundle §3 instrument was executed by its mapped audit
      (as designed, or adapted with note), or explicitly waived with
      justification — Step 10 §2 accounts for all of them
- [ ] Extended tests, conformance checks, and adversarial cases derive
      from the specifications, not the implementation
- [ ] Performance validation is empirical, compared against Phase 1
      measured baselines and change-spec §6 targets, with unexplained
      pre-cycle regressions flagged and severe misses phase-traced
- [ ] Every finding has a prefix ID, severity, evidence, affected
      principle/gate, and a disposition (resolved/accepted/dismissed)
- [ ] Every conformance deviation is classified (spec wrong / impl wrong
      / acceptable) and resolved
- [ ] The documentation queryability test ran with scored results,
      stale-doc checks included, and the documentation is frozen as the
      release baseline
- [ ] For designated components, the formal models were
      practitioner-reviewed
- [ ] Each principle has a gate status backed by evidence against the
      Step 02 §3 thresholds; the refresh compares to the Phase 5
      baseline with the target distribution check
- [ ] Accepted findings and conditional passes populate the Carried-Risk
      Register with bounds, owners, and timelines
- [ ] The determination is one of the seven outcomes, with amendment
      packages where alignment fails
- [ ] No fixes were implemented inside audit sessions; all fixes routed
      through Phase 5 discipline and re-audited
- [ ] All artifacts are version-stamped with a Version History table

---

## Common Pitfalls

**Treating audit as a formality.**
Running audits while expecting to release regardless makes the phase
decorative. The structural defense: gate authority (FAIL blocks) and the
seven-outcome determination with no undocumented "deploy anyway" path.

**Auditing only the diff.**
The most expensive misses live just outside the change. The structural
defense: the Step 02 three-way scope allocation and the AI-vs-AI audit's
blast-radius lens.

**Re-auditing the whole system at full depth.**
Uniform depth burns the capacity envelope re-verifying what did not
change. The structural defense: change-aware depth calibration at
Step 02, with regression assurance — not full re-audit — for the
remainder.

**Auditing with the same assumptions.**
Same configuration finds and misses the same things. The structural
defense: the Step 00 independence inventory, Step 02 §5 independence
plan, per-audit attestations, and Step 10 verification.

**Leaving instruments unexecuted.**
The track designed its verification instruments in Phase 3 precisely so
the audit would not improvise. The structural defense: the Step 02 §4
instrument-to-audit mapping and Step 10 §2 consolidation, where every
instrument is executed or explicitly waived.

**Conditional passes without timelines.**
An open-ended conditional is an indefinitely deferred problem. The
structural defense: remediation plan, timeline, owner, and stakeholder
acceptance required per conditional, verified at the gate.

**Leaving findings undispositioned.**
Noted-but-untriaged findings accumulate into a system no one can reason
about. The structural defense: the disposition discipline and Step 10 §3
verification.

**Patching at audit time.**
An audit session that fixes code destroys its independence and bypasses
the loop discipline. The structural defense: the no-fixes rule; fixes
route through Phase 5 and are re-audited scoped.

**Treating a severe benchmark miss as a Phase 6 problem.**
Severe misses are symptoms of earlier-phase problems. The structural
defense: root-cause phase-tracing and the four amendment paths.

**Dismissing a pre-cycle regression because the target was met.**
"Better than the spec but worse than before, unexplained" is a finding.
The structural defense: the measured-baseline comparison rule.

---

## Connecting to Phase 7

Phase 6 hands off the deployment readiness determination to Phase 7
(Deployment & Evolution).

| Phase 7 Concern | Phase 6 Inputs Consumed |
|-----------------|------------------------|
| Deployment authorization | The Step 10 readiness determination and report |
| Launch-readiness confirmation | The carried-risk register (§5) and conditional-pass timelines |
| Production monitoring activation | The verified observability evidence (Operations gate) |
| Operational runbooks | The frozen, queryability-tested documentation (Step 09) |
| Compliance evidence | The compliance matrix (Step 04, where applicable) |
| Performance baselines | The performance validation report (Step 05) — the new production baselines |
| Next-cycle Phase 2 | The consolidated cost-model calibration and the audit findings routed as next-cycle candidates |
| Phase 7 scorecard updates | The Step 10 scorecard refresh + inherited weights |

The Phase 7 toolkit's Step 01 (Phase 6 Input Validation) follows the same
two-scope split pattern this toolkit's Step 01 follows. The inter-phase
feedback loop continues — and with Phase 7, the track's phases become a
cycle.

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Phase 6 existing-projects instructions file. Three shifts from the greenfield Phase 6 variant (change-aware audit scoping with the three-way allocation — change surface deep, remainder regression, seams blast-radius — vs uniform audit; designed-instrument execution distributing the Phase 3 Bundle §3 instruments across their audit dimensions vs invented audit plans; measured baselines — Phase 1 actuals + change-spec §6 targets + pre-cycle behavior — vs projected benchmarks). Eleven-step structure in three stages (scoping 00–02; seven parallel-eligible independent audits 03–09 with Step 08 conditional; synthesis+gate 10 merging the greenfield scorecard and gate steps per the track pattern). Five feedback channels (upstream toolkit gaps + Phase 5/4/3/2 run amendments) and the seven-outcome determination with the Carried-Risk Register. Finding-disposition discipline with the greenfield prefixes (XT/SA/PV/CF/AA/FV/DG-NN) plus distinct instrument-execution accounting. Independence inventory at Step 00, per-audit plan at Step 02 §5, attestations per audit, gate verification. No-fixes-in-audit rule with scoped fix-and-re-audit protocol. Scorecard inheritance continued (Phase 2 weights; Phase 5 refresh baseline; target distribution check; gate authority). |

---

*Part of the Phase 6 (Existing Projects) Testing & Audit Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion files: step-00 through step-10 prompts in this directory*
