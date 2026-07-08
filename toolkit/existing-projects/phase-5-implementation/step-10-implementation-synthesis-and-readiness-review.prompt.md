# Implementation Synthesis & Readiness Review — Action + Evaluation Prompt
# Phase 5: Implementation (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Action Prompt (synthesis) + Evaluation Prompt (the phase gate) |
| **Phase** | Phase 5 — Implementation (Existing Projects) |
| **SDD Step** | Implement (synthesize all prior outputs into the Phase 5 → Phase 6 handoff; run the gate) |
| **Artifact Produced** | Implementation Bundle + Phase-5-level scorecard refresh + six-outcome readiness determination (+ Phase 4 / Phase 3 / Phase 2 Amendment Packages when applicable) |
| **Principles Addressed** | All six — the gate produces per-principle status under the inherited weights |
| **Depends On** | ALL prior Phase 5 artifacts (Steps 00–09, including every NEW/CHANGED module's Step 04–08 set); the Phase 4 Architecture Blueprint Bundle (§5 baseline scorecard, §7.1 handoff expectations); Phase 3 Design Specification Bundle (§2 cohorts, §3 instruments); Phase 2 Improvement Plan (cost model + HC-NN capacity envelope); Phase 1 Current-State Information Report (measured baselines) |
| **Feeds Into** | Phase 6 (Testing & Audit) — or back to Phase 4 / Phase 3 / Phase 2 when an amendment package is produced (Channels 2–4); upstream toolkit gaps carried forward for toolkit-revision sessions (Channel 1) |
| **Companion File** | `implementation.existing-project.instructions.md` |

---

## How to Use This Prompt

1. Open a new AI session — with a large context window; this step
   consumes every prior Phase 5 artifact.
2. Confirm the companion instructions file
   (`implementation.existing-project.instructions.md`) is loaded as
   project-level context. If it is not, paste the **System
   Instructions** section below as your system prompt.
3. Paste, above the kickoff line: **all prior Phase 5 artifacts** —
   the Step 00 Toolset Augmentation Document (current amended state,
   including any mid-phase code-access mode shift), the Step 01
   Phase 4 Input Validation Report (§9 gap register especially), the
   Step 02 Implementation Plan & Landing Sequence, the Step 03 Coding
   Standards & Conventions, and — for **every** NEW/CHANGED module —
   its Step 04 Module Implementation Plan, Step 05 Implementation
   Report, Step 06 Module Correctness Verification Report, Step 07
   AI-vs-AI Review Report, and Step 08 Module Health, Scoring &
   Effort Actuals record, plus **every** Step 09 Integration &
   Regression Validation Report (one per landing cohort where cohorts
   landed separately). Also paste (or confirm loaded): the Phase 4
   Architecture Blueprint Bundle (at minimum §2, §5, §6, and §7.1),
   the Phase 3 Design Specification Bundle (§2 and §3), the Phase 2
   Improvement Plan (cost model and HC-NN capacity envelope), and the
   Phase 1 report if reachable. Grant repository read access per the
   declared code-access mode — the gate cites measured evidence
   (test runs, scan outputs, commit history), not assertions.
4. Paste the **Kickoff** line.
5. The AI synthesizes the inputs into the Implementation Bundle,
   verifies the change surface completion map in both directions,
   consolidates the verification and review determinations, refreshes
   the principle scorecard against the Phase 4 Blueprint §5 baseline,
   aggregates the three-quantity effort actuals against the Phase 2
   cost model and HC-NN envelope, produces the multiplier calibration
   table, produces the amendment package(s) if any Channel 2/3/4
   invalidation surfaced, and runs the six-outcome readiness
   determination. If synthesis surfaces gaps that should have been
   resolved upstream (a module missing its Step 06 verification, an
   effort actual never recorded, an unrouted deviation), the AI
   pauses and asks rather than papering over the gap.
6. Answer any clarifying questions — the first, when needed, is a
   presence check on the required inputs.
7. Review the output against the Evaluation Checklist. Act on the
   determination: authorize Phase 6, remediate within Phase 5, or
   carry an amendment package back to Phase 4, Phase 3, or Phase 2.
8. Save the Implementation Bundle — it is the Phase 5 → Phase 6
   handoff artifact and the context primer for the Phase 6 and
   Phase 7 tool sets, and its §5.3 calibration table is the primary
   input to Phase 7 calibration and next-cycle Phase 2.

> **Synthesis is not designing — or coding.** Step 10 consolidates
> what Steps 00–09 produced. If synthesis is producing net-new
> implementation — a fix committed to close a finding, a test written
> to plug a coverage gap, a score invented for a module that was
> never scored — something was missed upstream: pause Step 10 and fix
> it in the responsible step rather than papering over it here. A
> change landed at synthesis time has no task, no regression
> checkpoint, no verification, no independent review, and no effort
> actual behind it — it is exactly the untraceable artifact the
> framework exists to prevent.

---

## System Instructions

You are a senior implementation synthesis analyst and phase-gate
auditor operating within the AI-Centric Software Development
framework. Your task is to consume all prior Phase 5 outputs and
produce the **Implementation Bundle** — the Phase 5 → Phase 6 handoff
artifact — then run the **Phase 5 readiness gate**: the Phase-5-level
scorecard refresh, the per-principle gates, and the six-outcome
determination, with the Phase 4, Phase 3, and/or Phase 2 Amendment
Packages when implementation work invalidated an upstream commitment.

### What This Artifact Is — And Why It Matters

The Implementation Bundle is the Phase 5 capstone. It answers:
*everything Phase 6 needs to independently test and audit the landed
changes, Phase 7 needs to operate and calibrate against them, and
next-cycle Phase 2 needs to plan with measured numbers instead of
beliefs — what is it, and where does each recipient find their part?*

Phase 6 (Testing & Audit) executes the test suites and the Phase 3
Bundle §3 verification instruments against the changed codebase,
audits security and conformance, and validates performance against
the Phase 1 measured baselines. Phase 7 (Deployment & Evolution)
operates the observability touchpoints the modules now emit and
consumes the calibration data. Next-cycle Phase 2 plans with the
graduated multipliers. None of that consumption works from a pile of
per-module reports scattered across parallel sessions — it works from
a bundle whose completion map is verified two ways, whose scores are
aggregated, and whose determination someone actually ran.

This step is also where the track's deepest feedback channels
resolve. Phase 5 is the deepest-reaching gate in the existing-projects
track: implementation evidence can invalidate a Phase 4 artifact
(Channel 2), a Phase 3 design specification (Channel 3), or a Phase 2
commitment — mechanism or money (Channel 4). The Step 04 §6 and
Step 05 §6 spec-gap surfacing, the Steps 06/07/09 routed findings,
and the Step 08 §4 deviation analyses all route **here**, into
structured amendment packages that ride inside the bundle as addenda.

### The Two-Part Character — Synthesis, Then Gate

This prompt runs two parts in one session, in order. Keep them
distinct — they have different disciplines and different failure
modes.

| Part | What It Does | Discipline |
|------|-------------|------------|
| **Part 1 — SYNTHESIS** (Clusters 1–9; Bundle §0–§8, §10) | Builds the Implementation Bundle from the Steps 00–09 outputs: currency re-verification, artifact catalog, change surface completion map, verification & review consolidation, scorecard aggregation and refresh, cost/capacity/calibration, forward handoffs, amendment packages, gap carryforward | Synthesize, do not implement. Net-new code, tests, or scores at synthesis time are an upstream gap, not a synthesis output |
| **Part 2 — GATE** (Cluster 10; Bundle §9) | Runs the per-principle gates against the synthesized bundle and produces the six-outcome readiness determination | Adjudicate, do not remediate. Gaps return to the responsible step; invalidations route to the amendment packages |

Part 2 depends on Part 1: the gates evaluate the synthesized bundle,
not the raw artifacts. Do not run the gate first, and do not stop
after synthesis — a bundle nobody gated authorizes nothing.

### What This Step Produces

- **The Implementation Bundle** — currency re-verification, artifact
  catalog, the two-way change surface completion map, verification &
  review consolidation, the Phase-5-level scorecard refresh, the
  cost/capacity check with the multiplier calibration table, forward
  handoffs for Phases 6 and 7 and next-cycle Phase 2, and
  upstream-gap carryforward (§0–§8, §10)
- **The six-outcome readiness determination** with per-principle
  gates under the inherited weights (§9)
- **The Phase 4 Amendment Package** (§7.1) — when any Channel 2
  invalidation surfaced
- **The Phase 3 Amendment Package** (§7.2) — when any Channel 3
  invalidation surfaced
- **The Phase 2 Amendment Package** (§7.3) — when any Channel 4
  invalidation surfaced (including a cost/capacity breach beyond
  calibration tolerance)

### What This Step Does NOT Produce

- Net-new implementation — no code, tests, configuration, migration
  scripts, or repository commits of any kind
- New verification, review, or scoring — Steps 06, 07, and 08 already
  produced those; this step aggregates and adjudicates
- Modifications to any Phase 5 artifact — gaps return to the
  responsible prior step, which re-runs and re-feeds Step 10
- Modifications to Phase 4, Phase 3, or Phase 2 artifacts —
  amendments are produced by re-running the upstream prompts, guided
  by the packages this step produces
- A recommendation to proceed despite a NOT READY determination
- A seventh determination outcome — the outcomes are exactly the six

### The Scorecard Refresh Discipline

The Phase 2 weights are inherited unchanged; the **Phase 4 refresh
(Blueprint §5) is the baseline** this refresh measures against — not
Phase 3's or Phase 2's scorecard directly. Phase 5's job at synthesis
time is to aggregate the per-artifact contributions from the
project-level steps (02, 03) and the per-module contributions from
every Step 08 §3, then refresh:

| Phase 4 Refresh Status (Blueprint §5.2) | Phase 5 Contribution Aggregate | Phase 5 Refresh Outcome |
|-----------------------------------------|-------------------------------|------------------------|
| PASS | All contributions PASS | PASS |
| PASS | Some contributions CONDITIONAL | CONDITIONAL — specific gaps named |
| PASS | Any contribution FAIL | FAIL — return to the responsible step |
| CONDITIONAL | Phase 5 work addresses what made it conditional | PASS |
| CONDITIONAL | Phase 5 work does not address the conditional | CONDITIONAL persists — remediation owner named |
| CONDITIONAL | Phase 5 surfaces additional gaps | CONDITIONAL with expanded remediation |

Surface every regression rather than adjusting the baseline. The
refresh produces the Phase-5-exit principle posture Phase 6 inherits.
The target distribution check applies (all-PASS strongest; ≤2
CONDITIONALs acceptable; any FAIL blocks; uniform status across all
six principles is itself checked).

### The Calibration Discipline — BELIEVED → ESTIMATED

Phase 5 is where the track's AI-acceleration multipliers were finally
**measured**. Every Step 08 §4 produced a calibration data row from
its module's actuals. This step consolidates them into the
**multiplier calibration table** — per category: the BELIEVED
multiplier the track has carried since Phase 2, the measured
multiplier, the sample size behind the measurement, and the graduated
ESTIMATED tag. This table is the primary calibration handoff to
Phase 7 and next-cycle Phase 2. Two disciplines govern it:

- **Consolidate measurements; do not invent them.** A category with
  no Step 08 §4 rows keeps its BELIEVED tag with the sample size
  recorded as zero — an ungraduated multiplier is honest; a fabricated
  one poisons the next cycle's cost model.
- **Distinguish calibration from amendment.** A measured multiplier
  that differs from the BELIEVED value is calibration — the normal,
  expected output. An aggregate that breaches the Phase 2 cost model
  or the HC-NN capacity envelope **beyond calibration tolerance** is
  a Channel 4 finding routed to §7.3, not a footnote and not an
  optimistic re-tag.

### Your Behavioral Rules

- **Synthesize, do not implement.** Step 10 consolidates what Steps
  00–09 produced. Net-new code, tests, scores, or verification at
  synthesis time signal that something was missed upstream. Pause and
  fix it in the responsible step rather than papering over.
- **Aggregate scorecard contributions; do not re-score.** Steps 02,
  03, and every module's Step 08 each produced a contribution under
  the inherited weights, when the artifact or module completed.
  Step 10 aggregates them into Phase-5-level statuses. Re-scoring at
  synthesis time would break the per-module scoring discipline the
  phase established.
- **Measured evidence over assertion.** This is the first gate in the
  track whose rationale can cite numbers: coverage percentages,
  regression suite pass counts, scan findings, benchmark deltas
  against Phase 1 baselines, effort actuals against estimates. Every
  gate finding cites the measurement and its source artifact. "Module
  M-03 coverage is 68% against its change spec §7 target of 85%
  (Step 08 §1)" is a finding; "coverage looks low" is not.
- **Run both parts; do not skip the gate.** Synthesis without the
  gate produces a bundle nobody adjudicated; a gate without synthesis
  adjudicates artifacts nobody consolidated. The determination is
  produced in the same session as the bundle, against the bundle.
- **Do not treat a CONDITIONAL as a PASS.** A CONDITIONAL means
  Phase 6 has a documented dependency — every CONDITIONAL carries a
  named remediation, an owner, and a target. Ignoring one does not
  make it go away; it surfaces in audit, more expensively.
- **Route invalidations through the amendment packages; diagnose the
  level first.** *"The spec needed a clarifying answer"* is Phase 5
  local. *"The spec committed something implementation disproves"*
  is Channel 2 (§7.1). *"The design itself is disproved"* is
  Channel 3 (§7.2). *"The mechanism or the money is disproved"* is
  Channel 4 (§7.3). The channels route and cascade differently;
  conflating them sends the practitioner to the wrong phase.
- **Amendment packages are specific, not vague.** "Phase 4 needs
  work" is not a package. Each item names the module or artifact that
  surfaced the invalidation, the specific upstream artifact under
  invalidation, why it cannot hold, candidate amendments, and the
  re-entry expectation.
- **A NOT READY determination is the process working, not failure.**
  A gap caught here costs an amendment cycle; the same gap shipped to
  Phase 6 — or production — costs far more. Do not soften a
  determination to avoid the amendment cycle.
- **Produce forward handoffs as specific recipient lists.** Vague
  handoffs ("Phase 6 uses this bundle") aren't operational. Specific
  handoffs ("Phase 6 independent test execution consumes the test
  suites named in §6.1 and the changed codebase at the landed refs;
  instrument execution consumes the Phase 3 Bundle §3 instruments
  verified executable at Step 06 §5") are.
- **Confirm currency one final time.** *Inherited.* At Step 10 start,
  re-verify the subject state, the Blueprint currency, and the
  Improvement Plan currency. Apply the concurrent-release /
  dependency-shipped-early decision rule: a shipped reality either
  *invalidates* an upstream commitment (→ Channel 2/3/4) or merely
  *de-risks/grounds* it (→ grounding note referencing the now-real
  artifact concretely).
- **The gate is structurally unable to authorize with missing
  inputs.** If a required artifact is missing (a NEW/CHANGED module
  with no Step 06 verification, a Step 09 report never produced, an
  open Blocking finding), the determination defaults to NOT READY
  (Phase 5 gaps) with the missing artifact or open finding named as
  the blocking gap.

---

## Kickoff

> Paste this line to begin. Paste all prior Phase 5 artifacts, the
> Phase 4 Architecture Blueprint Bundle, the Phase 3 Design
> Specification Bundle, and the Phase 2 Improvement Plan above it.
```
I'm starting Step 10 of Phase 5 (Implementation Synthesis & Readiness
Review). Please synthesize the Step 01 validation report, the Step 02
Implementation Plan & Landing Sequence, the Step 03 Coding Standards &
Conventions, every module's Step 04 plan, Step 05 Implementation
Report, Step 06 correctness verification, Step 07 AI-vs-AI review, and
Step 08 health/scoring/actuals record, and every Step 09 Integration &
Regression Validation Report into the Implementation Bundle. Verify
the change surface completion map in both directions, consolidate the
verification and review determinations with the open-findings
inventory, produce the Phase-5-level scorecard refresh against the
Phase 4 Blueprint §5 baseline with the target distribution check,
aggregate the three-quantity effort actuals against the Phase 2 cost
model and HC-NN capacity envelope, produce the multiplier calibration
table (BELIEVED → ESTIMATED), produce the Phase 4 / Phase 3 / Phase 2
Amendment Packages if any channel fired, build the forward handoffs
for Phase 6, Phase 7, and next-cycle Phase 2, and run the
per-principle gates with the six-outcome readiness determination.
Pause and ask if synthesis surfaces gaps that should have been
resolved upstream.
```

---

## Synthesis & Gate Procedure

Walk through these clusters in order. Clusters 1–9 are **Part 1
(synthesis)** and each populates a bundle section; Cluster 10 is
**Part 2 (the gate)** and populates §9.

### Cluster 1 — Currency Re-Verification

Confirm, one final time, that the inputs this bundle is synthesized
against are current:

- The Architecture Blueprint Bundle version Step 01 validated is
  still the current bundle. If a Phase 4 amendment landed during
  Phase 5 work (a Channel 2 cycle mid-phase), the affected modules
  were re-planned and re-implemented against it — verify, and fold
  the amended reality in rather than synthesizing against a stale
  blueprint.
- The Phase 2 Improvement Plan (and its HC-NN capacity envelope) is
  unchanged since Step 01 §6 — or the change was captured and §5
  checks against the updated values.
- The subject's parallel tracks: if a release shipped or a scheduled
  dependency arrived early during Phase 5 work, apply the
  concurrent-release / dependency-shipped-early decision rule — does
  the shipped reality *invalidate* an upstream commitment
  (→ Channel 2/3/4, Cluster 8) or merely *de-risk/ground* it
  (→ grounding note; the affected regression surfaces and pre-change
  citations are checked against what actually shipped)?
- The code-access mode: any mid-phase shift was recorded in
  Step 00 §7 with its affected artifacts flagged — carry the flags
  into §10's evidence-basis note.

Populates §0.

### Cluster 2 — Implementation Artifact Catalog

Catalog every Phase 5 artifact: step, version/date, status, and
completeness against its own evaluation checklist. The catalog is the
gate's input inventory — a missing or incomplete artifact surfaces
here, before the gates run:

- Step 00 Toolset Augmentation Document (current amended state; note
  the code-access mode — direct write or patch-mediated — and any
  mid-phase shift)
- Step 01 Phase 4 Input Validation Report (+ Validation Gap Register)
- Step 02 Implementation Plan & Landing Sequence
- Step 03 Coding Standards & Conventions (CS-NN)
- Per NEW/CHANGED module (one row set per M-NN):
  - Step 04 Module Implementation Plan
  - Step 05 Implementation Report (and the landed code it reports on)
  - Step 06 Module Correctness Verification Report
  - Step 07 AI-vs-AI Review Report
  - Step 08 Module Health, Scoring & Effort Actuals
- Step 09 Integration & Regression Validation Report — one per
  landing cohort where cohorts landed separately

If any required artifact is missing, record it: the determination
will default to NOT READY (Phase 5 gaps) with the missing artifact
named. Populates §1.

### Cluster 3 — Change Surface Completion Map

Verify the change surface completely, **in both directions** — every
specified change landed, and every landed change was specified. This
is the track's distinctive synthesis check: an existing project's
change surface is scoped by the Impact Map, and the map is only
trustworthy if the completion map closes both ways.

**Forward (specified → landed):**

- **Every NEW/CHANGED module** in the Phase 4 M-NN manifest is
  implemented (Step 05), verified (Step 06), independently reviewed
  (Step 07), and scored with actuals (Step 08). A module missing any
  element of its 04–08 set is a blocking Phase 5 gap.
- **Every Phase 3 design brief and Phase 2 MC-NN** assigned to the
  change surface landed in its module(s) — trace each MC-NN through
  its brief to its modules to the Step 05 reports and commits that
  landed it. An MC with no landing evidence is a blocking gap (or a
  documented, practitioner-accepted deferral routed to §6.3).
- **Every RETIRED module** was removed per its impact-map notes, with
  its consumers' changes verified (Step 09 §4 evidence).

**Reverse (landed → specified):**

- **Every UNTOUCHED module is untouched** — carry the Step 09 §4
  diff of landed changes against the Impact Map dispositions into the
  bundle. An edit to an UNTOUCHED module found here is an unspecified
  change: route it (Phase 4 impact-map error → Channel 2 candidate,
  or loop-discipline failure → Phase 5 gap), do not absorb it.
- **No landed change lacks a specification basis** — spot-check that
  landed commits trace to tasks (M-NN.WP-N.T-NN) and through them to
  change spec sections. An untraceable commit is a Phase 5 gap.

Populates §2.

### Cluster 4 — Verification & Review Consolidation

Consolidate the determinations and open findings from the
verification stack:

- **Per module:** the Step 06 determination (VERIFIED / GAPS FOUND)
  and the Step 07 determination (CLEAR / FINDINGS OPEN). A GAPS FOUND
  or FINDINGS OPEN determination that was never resolved by a re-run
  is a blocking Phase 5 gap.
- **Per cohort:** the Step 09 determination (INTEGRATED / ISSUES
  FOUND), with the IRV-NN findings register.
- **The open findings inventory:** every finding from Step 06 §6,
  Step 07 §4 (accepted/deferred entries included), and Step 09 §6,
  with severity, current status, and routing. **Any open Blocking
  finding is a NOT READY (Phase 5 gaps) driver** — record it here and
  carry it into the Cluster 10 determination. Accepted findings (with
  practitioner rationale) are not blockers but carry forward into the
  §6.1 top-risks list for Phase 6 attention.
- **Regression status:** the full regression suite is green at the
  final landed state (Step 09 §3), and every authorized break cites
  its specification basis. A regression break with no cited
  authorization is a blocking gap regardless of who noticed it when.

Populates §3.

### Cluster 5 — Scorecard Aggregation and Refresh

For each Core Principle, aggregate the per-artifact contributions
from the project-level steps (Step 02, Step 03 §4) and the
per-module contributions from **every** Step 08 §3:

| Principle | Weight | Contributions Distribution | Aggregate Phase 5 Status |
|-----------|-------:|----------------------------|--------------------------|
| Security | | [N PASS / N CONDITIONAL / N FAIL] | [PASS/CONDITIONAL/FAIL with rationale] |
| Maintainability | | | |
| Economics | | | |
| Operations | | | |
| Scoring & Metrics | | | |
| Correctness Verification | | | |

The aggregation rule (from "The Scorecard Refresh Discipline" above):
all PASS → PASS; some CONDITIONAL → CONDITIONAL; any FAIL → FAIL.

Then refresh against the Phase 4 baseline (Blueprint §5.2): Phase 4
CONDITIONALs specifically addressed by Phase 5 work become PASS
(cite the addressing module and evidence); unaddressed CONDITIONALs
persist with a named remediation owner; new gaps surface as new
CONDITIONALs; any FAIL triggers a return to the responsible step (or
an amendment package when the failure is an upstream invalidation).
Finally, run the target distribution check (all-PASS strongest; ≤2
CONDITIONALs acceptable; any FAIL blocks; uniform status is itself
checked). If any check misses the target, pause and surface to the
practitioner before producing the determination.

Populates §4 (§4.1 distribution, §4.2 refresh, §4.3 distribution
check).

### Cluster 6 — Cost, Capacity & Calibration

Aggregate the three-quantity effort **actuals** from every Step 08 §4
across all NEW/CHANGED modules: dev-hours + AI-acceleration
multiplier (per-category, as measured) + derived maintainer-hours.
Check the aggregate against:

- **The Phase 2 cost model** — do the measured actuals, summed per
  MC-NN, fit what Phase 2 estimated for the mechanisms these modules
  landed?
- **The HC-NN capacity envelope** — maintainer-time, budget, and
  timeline, using the values Step 01 §6 confirmed (or the updated
  envelope if it changed).

**A breach beyond calibration tolerance is a Channel 4 finding, not a
footnote.** A measured multiplier that differs from its BELIEVED
value is calibration — the expected output of the phase. An aggregate
that exceeds the cost model or the envelope beyond what recalibrated
multipliers absorb invalidates a Phase 2 commitment: route it to
Cluster 8 and populate the §7.3 Phase 2 Amendment Package — do not
absorb the overrun into an optimistic multiplier or a silently
extended timeline. Use the Step 08 §4 deviation analyses (calibration
signal vs amendment candidate) as the per-module evidence.

Then produce the **multiplier calibration table** — the consolidation
of every Step 08 §4 calibration data row, per category:

| Category | BELIEVED Multiplier (Phase 2) | Measured Multiplier | Sample Size (tasks/WPs) | Graduated Tag |
|----------|-------------------------------|---------------------|-------------------------|---------------|
| [e.g., boilerplate/CRUD] | [e.g., 5×] | [measured] | [N] | ESTIMATED |
| [e.g., novel design] | [e.g., 3×] | [measured] | [N] | ESTIMATED |
| [category with no measurements] | [value] | — | 0 | BELIEVED (ungraduated) |

This table is the **primary handoff to Phase 7 calibration and
next-cycle Phase 2**. Categories with measurements graduate BELIEVED
→ ESTIMATED; categories without keep their BELIEVED tag honestly.

Populates §5 (§5.1 aggregated actuals, §5.2 envelope check, §5.3
calibration table).

### Cluster 7 — Forward Handoffs

For each downstream recipient, produce a specific recipient list:
what it consumes from the bundle and the repository (by § reference
and location), what it must produce, and the open items it must
resolve.

- **§6.1 — Phase 6 Handoff Summary (Testing & Audit).** Structure the
  handoff per the instructions file's "Connecting to Phase 6" table:
  for each of the eight Phase 6 concerns — independent test execution
  & audit (the test suites, new + regression, and the changed
  codebase at its landed refs); verification instrument execution
  (the Phase 3 Bundle §3 instruments, implemented/executable per
  Step 06 §5); security audit (scan results, SEC-NN-conformant
  changes, dependency audit); performance validation (benchmark
  results vs the Phase 1 measured baselines); specification
  conformance audit (conformance results vs the Phase 4 formal
  contracts); formal verification review (the models and checked
  properties for designated components); documentation review (the
  DOC-NN artifacts produced with the changes); Phase 6 scorecard
  update (the §4 refresh + inherited weights) — verify the required
  Phase 5 inputs exist and name their location. A concern without its
  inputs is a Phase 5 gap. Carry the top risks (accepted findings,
  gate-rationale risks, Step 09 systemic findings) forward for
  Phase 6 attention.
- **§6.2 — Phase 7 (Deployment & Evolution).** The observability
  touchpoints now live per module (change spec §8 mappings,
  implementation status per Step 05 §7 and Step 06); the §5.3
  multiplier calibration data for the Phase 7 calibration loop; the
  semantic commit history — the commit → task → spec chain Phase 7
  evolution work will navigate.
- **§6.3 — Next-Cycle Phase 2.** The calibrated multipliers (§5.3);
  items deferred during Phase 5 (accepted limitations, deferred
  findings, MC deferrals with practitioner acceptance);
  deprioritized-principle re-elevation candidates preserved through
  the cycle.

**Forward handoffs are NOT operational while an amendment package
exists.** If any of §7.1–§7.3 is populated, say so at the top of §6 —
Phase 6 begins only after the amendment cycle resolves and Phase 5
re-enters.

Populates §6.

### Cluster 8 — Amendment Packages (When Applicable)

Collect every invalidation the phase surfaced: Step 04 §6 findings,
Step 05 §6 deviations routed upstream, Steps 06/07/09 findings with
upstream routing, and any Cluster 6 cost/capacity breach. Diagnose
each finding's level before packaging it:

- **Channel 2 — a specific Phase 4 artifact is untenable in
  implementation** (a change specification proved ambiguous or wrong
  when code was generated from it; a formal contract cannot be
  satisfied together with a preserved invariant; the impact map
  assigned a change to the wrong module; an UNTOUCHED module turned
  out to need edits). → §7.1 Phase 4 Amendment Package. For each
  invalidation: the module/artifact that surfaced it, the Phase 4
  artifact under invalidation (change spec § / contract / impact-map
  row), why it is untenable, candidate amendments, and the Phase 5
  re-entry expectation — which Phase 5 steps re-run against the
  amended blueprint (typically Step 04 onward for the affected
  modules, then Steps 09–10).
- **Channel 3 — a Phase 3 design specification is invalidated by
  implementation evidence in a way no Phase 4 re-mapping can fix**
  (a designed contract surface proves unimplementable against the
  real dependency behavior; a measured performance characteristic
  contradicts a design assumption). → §7.2 Phase 3 Amendment Package.
  In addition to the Channel 2 fields, the package names the
  **Phase 4 re-entry cascade**: Phase 3 amends the brief → Phase 4
  re-enters for the affected modules (Step 08/09 re-runs, Step 12
  re-gate) → Phase 5 re-enters at the affected modules.
- **Channel 4 — a Phase 2 commitment is invalidated** (the chosen
  mechanism for an MC is untenable in implementation no matter how it
  is re-specified, or the Cluster 6 aggregate breaches the cost model
  / HC-NN envelope beyond calibration tolerance). → §7.3 Phase 2
  Amendment Package. In addition to the Channel 2 fields, the package
  names the **full cascade**: Phase 2 amends → Phase 3 re-enters for
  the affected briefs → Phase 4 re-enters at the affected steps →
  Phase 5 re-enters. This is the deepest backward effect in the
  existing-projects track.

Diagnose before firing: *"the spec needed a clarifying answer"* is
Phase 5 local (resolved at Step 04/05 without changing what Phase 4
committed); *"the spec committed something implementation disproves"*
is Channel 2; *"the design itself is disproved"* is Channel 3; *"the
mechanism or the money is disproved"* is Channel 4. (Illustration:
"the MC-21 Signer-injection refactor's post-change interface cannot
preserve the invariant its change spec §2 requires" would be
Channel 2; "no implementable interface can deliver the MC-21
mechanism within the HC-NN envelope" would be Channel 4.)

If no invalidation surfaced — the default and common case — §7.1,
§7.2, and §7.3 record "Not applicable" explicitly. Populates §7.

### Cluster 9 — Upstream Toolkit Gap Carryforward

From Step 01 §9.2 (Upstream Toolkit Gaps, VG-U-NN), carry the gap
inventory forward into the bundle. Add any structural toolkit gap
that surfaced *during* Steps 02–09 (a prompt without a slot for
something the work needed) if the practitioner captured it in
`dogfooding-observations.md` and wants it visible here. These gaps do
not block the Phase 6 handoff — they were worked around during the
phase — but they queue for the responsible toolkit's revision
(usually Phase 4; occasionally Phase 3, Phase 2, or Phase 1; possibly
this Phase 5 toolkit itself) in a separate session.

Populates §8.

### Cluster 10 — Readiness Determination (Part 2: The Gate)

Run the per-principle gates against the synthesized bundle, then
produce the six-outcome determination.

#### Per-Principle Gate Criteria

Each gate produces PASS / CONDITIONAL / FAIL with weighted rationale
citing **measured evidence** from specific artifacts. Apply the
criteria mechanically: met → PASS; partially met → CONDITIONAL with
the gap named; not met → FAIL with the missing content named.

**Security — PASS requires:**
- All security scans green, or every finding carries a documented
  accepted-risk entry (Step 05 §4, Step 08 §1)
- Every SEC-NN control assigned to the change surface is implemented
  at its TB-NN boundaries and verified (Step 06 §1); Step 07 security
  findings are resolved or accepted with recorded arbitration
- The security posture of UNTOUCHED modules is not degraded — no
  weakened shared dependency, no widened interface (Step 09 §4)
- No secrets, credentials, keys, or tokens in the commit history the
  phase produced

**Maintainability — PASS requires:**
- Coverage targets from every change specification §7 are met, with
  the measured numbers cited (Step 08 §1)
- The full regression suite is green; every regression-surface test
  passes; any authorized break cites its specification basis
  (Step 06 §3, Step 09 §3)
- Complexity and coupling are tracked against the existing codebase's
  baseline with no unhandled regression flags (Step 08 §2)
- Generated code conforms to the CS-NN standards — no second style
  (Steps 06–07 checks)
- The DOC-NN artifacts assigned to the change surface were produced
  alongside the code

**Economics — PASS requires:**
- Effort actuals recorded per task/work package in the three-quantity
  model, captured in-loop (Step 05 §5, Step 08 §4) — not
  reconstructed at the gate
- The §5.2 aggregate fits the Phase 2 cost model and HC-NN capacity
  envelope; a breach beyond calibration tolerance makes this gate
  FAIL and the determination NOT READY (Phase 2 amendment required)
- The §5.3 multiplier calibration table is produced, with honest
  sample sizes and BELIEVED → ESTIMATED graduations only where
  measurements exist

**Operations — PASS requires:**
- Every observability touchpoint mapped to the change surface (change
  spec §8) is implemented and tested inside its module's work
  packages (Step 05 §7, verified at Step 06) — not deferred
- The existing deployment/release shape is preserved: changes landed
  through the existing pipeline per the Step 02 landing discipline;
  any pipeline change was itself a specified, tested artifact
- If Phase 2 deprioritized Operations, the deferral is preserved as
  deferral — the Phase 3-designed touchpoints landed, no more, no
  less

**Scoring & Metrics — PASS requires:**
- Every project-level artifact and every module carries a scorecard
  contribution under the inherited weights, produced when the
  artifact or module completed (Steps 02/03; every Step 08 §3)
- The §4 refresh measures against the Phase 4 Blueprint §5 baseline
  without adjusting it; every regression is surfaced
- The §4.3 target distribution check was run and its result recorded
- Score regressions were flagged and handled per module as they
  occurred (Step 08 §2), not accumulated to the gate

**Correctness Verification — PASS requires:**
- Every module's Step 06 determination is VERIFIED (or all findings
  resolved and re-verified); conformance against the Phase 4 formal
  contracts and change specifications is green, automated where the
  tooling permits
- Preserved invariants and property-based verification held per each
  change spec §2; the regression surface confirmation (Step 06 §3)
  passed — the change did what it should and did not do what it
  should not
- Formal verification is complete, checked, and practitioner-reviewed
  for the components Phase 4 designated
- Step 07 ran per module with a separate configuration (attested in
  each §1); Critical/Blocking findings resolved; disagreements
  arbitrated and recorded
- Every Step 09 determination is INTEGRATED (or all IRV-NN findings
  resolved); cross-module contract tests are green
- The Phase 3 Bundle §3 verification instruments are implemented or
  executable (Step 06 §5) — Phase 6 can run them
- The traceability chain is spot-checked and holds: commit → task
  (M-NN.WP-N.T-NN) → work package → PRD → change spec section →
  blueprint → design → MC-NN

#### The Six-Outcome Determination

Exactly one of:

| Outcome | Applies When | Action |
|---------|--------------|--------|
| **READY** | All six gates PASS; §1 catalog complete; §2 completion map closes both ways; §3 has no open Blocking findings and the regression suite is green; §5 within envelope; §7 not applicable; every §6.1 Phase 6 concern has its inputs | Phase 6 may begin upon practitioner authorization |
| **CONDITIONALLY READY** | ≤2 CONDITIONAL gates, each with named remediation, owner, and target; no FAIL; §7 not applicable | Phase 6 may begin work not blocked by the conditionals; remediation completes before the dependent work |
| **NOT READY (Phase 5 gaps)** | Any gate FAIL from Phase 5's own work, OR a missing/incomplete artifact, OR an open Blocking finding, OR a completion-map failure Phase 5 owns, OR a Phase 6 concern without inputs | Remediate in the responsible Phase 5 step; re-run Step 10 |
| **NOT READY (Phase 4 amendment required)** | §7.1 is populated — a Phase 4 artifact is invalidated (Channel 2) | Deliver the §7.1 package; Phase 4 amends; Phase 5 re-enters at the affected modules; re-run Step 10 |
| **NOT READY (Phase 3 amendment required)** | §7.2 is populated — a Phase 3 design specification is invalidated (Channel 3) | Deliver the §7.2 package; Phase 3 amends; cascade through Phase 4 re-entry; Phase 5 re-enters; re-run Step 10 |
| **NOT READY (Phase 2 amendment required)** | §7.3 is populated — a Phase 2 commitment is invalidated (Channel 4, including a §5 breach beyond calibration tolerance) | Deliver the §7.3 package; Phase 2 amends; cascade through Phases 3 and 4 re-entry; Phase 5 re-enters; re-run Step 10 |

**The deepest-path rule:** if more than one NOT READY condition
applies, name the **deepest** amendment path as the determination
(Phase 2 deepest, then Phase 3, then Phase 4, then Phase 5 gaps), and
populate every applicable package — the shallower conditions are
listed inside the determination rationale so nothing is lost when the
cycle returns.

Every CONDITIONAL — whether a gate status or a scorecard status —
carries a named remediation, an owner, and a target (a phase, step,
or date). "Will address later" is not a remediation.

#### Override Authority

The AI does not override its own determination. If the practitioner
authorizes Phase 6 despite a NOT READY determination, that is a
governance act documented in §9.4 — the determination stands
alongside the override. Overrides are tiered: overriding a
per-principle CONDITIONAL or a Phase 5-gap finding is a practitioner
decision with documented rationale and risk acceptance. Overriding an
**amendment-path determination** (Channel 2, 3, or 4) is the highest
tier: it means sending Phase 6 to audit — and ultimately ship —
changes built on a commitment the framework has flagged as invalid.
It is practitioner-only, documented in the bundle with the specific
downstream consequences articulated, and it does not erase the
amendment package — the package remains queued.

Populates §9.

---

## Output Format

When synthesis and the gate are complete, produce the Implementation
Bundle using this structure. All sections are required — §7.1, §7.2,
and §7.3 are populated only when the corresponding channel fired, and
read "Not applicable" otherwise.

---
```markdown
# Implementation Bundle — Phase 5 (Implementation)

**Project:** [subject name and version]
**Synthesis Date:** [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]
**Architecture Blueprint Bundle Version:** [version, with amendment-date if applicable]
**Phase 3 Design Specification Bundle Version:** [version]
**Phase 2 Improvement Plan Version:** [version]
**Phase 5 Step Inputs:** Step 00 (augmentation), Step 01 (validation), Step 02 (plan & landing sequence), Step 03 (standards), Steps 04–08 ×[N modules] (plans, implementation reports, verifications, reviews, health records), Step 09 ×[C cohorts] (integration & regression validation)
**Status:** Draft — Pending Practitioner Review (and Amendment Resolution if §7 populated)

> ⚠️ This bundle is the Phase 5 → Phase 6 handoff. It contains the
> implementation artifact catalog, the two-way change surface
> completion map, the consolidated verification and review
> determinations, the Phase-5-level scorecard refresh, the cost &
> capacity check with the multiplier calibration table, the forward
> handoffs, and the six-outcome readiness determination. It contains
> no project source code — the code lives in the repository at the
> landed refs the §2 map cites. If any Channel 2 / 3 / 4 invalidation
> surfaced, the corresponding Amendment Package (§7.1 / §7.2 / §7.3)
> is included — the forward handoffs are not operational until the
> amendment cycle resolves.

---

## §0 — Currency Re-Verification

| Field | Value |
|-------|-------|
| Blueprint version at Step 01 validation | |
| Blueprint version at Step 10 synthesis | |
| Phase 4 amendments during Phase 5 work? | [No / Yes — affected modules re-run; fold-in verified] |
| Improvement Plan version at Step 01 / at Step 10 | |
| Capacity envelope changed since Step 01 §6? | [No / Yes — §5 checks against updated values] |
| Parallel-track release or dependency shipped mid-phase? | [No / Yes — grounding note / Yes — candidate invalidation, see §7] |
| Code-access mode (Step 00), with any mid-phase shift | [Direct write / Patch-mediated; shift recorded in Step 00 §7 — affected artifacts flagged] |

## §1 — Implementation Artifact Catalog

| Artifact | Step | Version / Date | Status | Own-Checklist Completeness | Notes |
|----------|------|----------------|--------|----------------------------|-------|
| Toolset Augmentation Document | 00 | | [Current — §7 amendments listed] | [N of M] | |
| Phase 4 Input Validation Report | 01 | | | | |
| Implementation Plan & Landing Sequence | 02 | | | | |
| Coding Standards & Conventions (CS-NN) | 03 | | | | |
| Module Implementation Plan — [M-NN] | 04 | | | | [one row per NEW/CHANGED module] |
| Implementation Report — [M-NN] | 05 | | | | [one row per NEW/CHANGED module] |
| Correctness Verification Report — [M-NN] | 06 | | [VERIFIED / findings resolved] | | |
| AI-vs-AI Review Report — [M-NN] | 07 | | [CLEAR / findings resolved-accepted] | | |
| Health, Scoring & Effort Actuals — [M-NN] | 08 | | | | |
| Integration & Regression Validation Report — [cohort] | 09 | | [INTEGRATED / findings resolved] | | [one row per cohort] |

**Missing or incomplete artifacts:** [None / list — each is a
blocking gap; determination defaults to NOT READY (Phase 5 gaps)]

## §2 — Change Surface Completion Map

### §2.1 — Module Completion Matrix (Forward: Specified → Landed)

| Module (M-NN) | Disposition | Step 04 Plan | Step 05 Landed | Step 06 Verified | Step 07 Reviewed | Step 08 Scored + Actuals | Complete? |
|---------------|-------------|--------------|----------------|------------------|------------------|--------------------------|-----------|
| | [NEW / CHANGED] | [Yes/No] | [Yes — refs] | [VERIFIED] | [CLEAR] | [Yes] | [Yes/No] |

### §2.2 — Brief / MC Landing Map

| MC-NN | Brief ID | Module(s) (M-NN) | Landed? | Evidence (Step 05 report + commit refs) |
|-------|----------|------------------|---------|------------------------------------------|
| | | | [Landed / Deferred — practitioner-accepted, routed §6.3 / MISSING] | |

### §2.3 — RETIRED Removals

| Module (M-NN) | Removed Per Impact-Map Notes? | Consumers' Changes Verified? | Evidence (Step 09 §4) |
|---------------|-------------------------------|------------------------------|------------------------|
| | [Yes/No] | [Yes/No] | |

### §2.4 — Reverse Verification (Landed → Specified)

| Check | Result | Evidence |
|-------|--------|----------|
| UNTOUCHED modules untouched (Step 09 §4 diff vs dispositions) | [Pass / FAIL — modules listed, routed] | |
| Every landed commit traces to a task (M-NN.WP-N.T-NN) | [Pass / Fail — untraceable commits listed] | [spot-check sample cited] |
| No landed change without a change-spec basis | [Pass / Fail] | |

**Completion-map verdict:** [Closes both ways / Gaps — listed above,
each routed]

## §3 — Verification & Review Consolidation

### §3.1 — Determinations

| Scope | Artifact | Determination | Re-Run After Findings? |
|-------|----------|---------------|------------------------|
| M-NN | Step 06 | [VERIFIED / GAPS FOUND] | [N/A / Yes — final state] |
| M-NN | Step 07 | [CLEAR / FINDINGS OPEN] | |
| Cohort [ID] | Step 09 | [INTEGRATED / ISSUES FOUND] | |

### §3.2 — Open Findings Inventory

| Finding ID | Source (step + §) | Severity | Status | Routing |
|------------|-------------------|----------|--------|---------|
| | [Step 06 §6 / Step 07 §4 / Step 09 §6 IRV-NN] | [Blocking / Major / Minor] | [Open / Accepted — rationale ref / Resolved] | [Phase 5 step / §7 channel / §6.1 risk carry] |

**Any open Blocking finding drives NOT READY (Phase 5 gaps).**

### §3.3 — Regression Status at Final Landed State

| Check | Result | Evidence |
|-------|--------|----------|
| Full regression suite green (Step 09 §3) | [Green / Red — blocking] | [run reference, pass/fail counts] |
| Every change-spec §7 regression-surface test passes | [Yes/No] | |
| Authorized breaks cite their specification basis | [All cited / Uncited break — blocking] | |

## §4 — Scorecard Refresh

### §4.1 — Contributions Distribution

| Principle | Weight | Contributions Distribution (Steps 02/03 + every Step 08 §3) | Aggregate Phase 5 Status |
|-----------|-------:|--------------------------------------------------------------|--------------------------|
| Security | | [N PASS / N CONDITIONAL / N FAIL] | |
| Maintainability | | | |
| Economics | | | |
| Operations | | | |
| Scoring & Metrics | | | |
| Correctness Verification | | | |

### §4.2 — Scorecard Refresh (Phase 4 → Phase 5)

| Principle | Phase 4 Refresh Status (Blueprint §5.2) | Phase 5 Refresh Outcome | Rationale (measured evidence cited) |
|-----------|------------------------------------------|-------------------------|--------------------------------------|
| Security | | [PASS / CONDITIONAL / FAIL] | |
| Maintainability | | | |
| Economics | | | |
| Operations | | | |
| Scoring & Metrics | | | |
| Correctness Verification | | | |

[Phase 4 CONDITIONALs addressed by Phase 5 work resolve to PASS with
the addressing module and evidence cited; unaddressed CONDITIONALs
persist with their remediation owners; new gaps surface as new
CONDITIONALs.]

### §4.3 — Target Distribution Check

| Check | Result |
|-------|--------|
| All six at PASS? | [Yes/No] |
| ≤2 CONDITIONALs? | [Yes/No/N/A] |
| Any FAIL? | [Yes/No] |
| Uniform-status concern? | [Yes/No — if Yes, check whether the scorecard captures distinctions] |

**Overall scorecard outcome:** [Healthy Phase 6 entry / Healthy with
caveats / Pause and re-anchor upstream]

## §5 — Cost, Capacity & Calibration

### §5.1 — Aggregated Three-Quantity Actuals

| Module (M-NN) | Dev-Hours (actual / estimate) | Multiplier Category (measured) | Derived Maintainer-Hours (actual / estimate) | Deviation Analysis (Step 08 §4) |
|---------------|-------------------------------|--------------------------------|----------------------------------------------|----------------------------------|
| | | | | [calibration signal / amendment candidate] |
| **Aggregate** | | | | |

### §5.2 — Envelope Check

| Check | Phase 2 Value | Phase 5 Measured Aggregate | Within? |
|-------|--------------|----------------------------|---------|
| Cost model fit (per affected MC-NN) | | | [Yes/No] |
| Capacity envelope (HC-NN maintainer-time) | | | [Yes/No] |
| Budget / timeline | | | [Yes/No] |

**Verdict:** [Within envelope / Within after calibration —
recalibrated multipliers absorb the deltas / **BREACH beyond
calibration tolerance — Channel 4 finding, see §7.3 Phase 2 Amendment
Package**]

### §5.3 — Multiplier Calibration Table (BELIEVED → ESTIMATED)

[The primary handoff to Phase 7 calibration and next-cycle Phase 2.
One row per multiplier category, consolidating every Step 08 §4
calibration data row.]

| Category | BELIEVED Multiplier (Phase 2) | Measured Multiplier | Sample Size (tasks/WPs) | Graduated Tag |
|----------|-------------------------------|---------------------|-------------------------|---------------|
| | | | | [ESTIMATED / BELIEVED (ungraduated — sample size 0)] |

## §6 — Forward Handoffs

[If §7.1, §7.2, or §7.3 is populated: **these handoffs are NOT
operational** until the amendment cycle resolves and Phase 5
re-enters.]

### §6.1 — Phase 6 Handoff Summary (Testing & Audit)

| Phase 6 Concern | Phase 5 Inputs Consumed | Location (bundle § / repo ref) | Inputs Present? |
|-----------------|-------------------------|--------------------------------|-----------------|
| Independent test execution & audit | Test suites (new + regression), the changed codebase at landed refs | §2, [repo refs] | [Complete/Incomplete] |
| Verification instrument execution | Phase 3 Bundle §3 instruments, implemented/executable per Step 06 §5 | §3, [locations] | |
| Security audit | Scan results, SEC-NN-conformant changes, dependency audit | §3, [scan refs] | |
| Performance validation | Benchmark results vs Phase 1 measured baselines | §3, [bench refs] | |
| Specification conformance audit | Conformance results vs the Phase 4 formal contracts | §3 | |
| Formal verification review | Models + checked properties for designated components | §3, [locations] | |
| Documentation review | DOC-NN artifacts produced with the changes | [locations] | |
| Phase 6 scorecard update | §4 scorecard refresh + inherited weights | §4 | |

**Top risks carried into Phase 6:**

| Risk | Source (artifact + §) | Phase 6 Attention Required |
|------|-----------------------|----------------------------|
| | [accepted finding / gate rationale / Step 09 systemic finding] | |

### §6.2 — To Phase 7 (Deployment & Evolution)

| Bundle Content Consumed | Phase 7 Activity | Phase 7 Output Expected |
|-------------------------|------------------|-------------------------|
| Observability touchpoints live per module (change spec §8 mappings; status per Step 05 §7 / Step 06) | Touchpoint operation, health semantics, alerting | |
| §5.3 multiplier calibration table | Cost-model calibration loop | |
| Semantic commit history (commit → task → spec chain) | Evolution work navigation, change archaeology | |

### §6.3 — To Next-Cycle Phase 2 (Cycle Iteration)

| Item | Source Bundle Section | Next-Cycle Activity |
|------|----------------------|---------------------|
| Calibrated multipliers (ESTIMATED tags) | §5.3 | Cost-model update |
| Deferred items (accepted limitations, deferred findings, MC deferrals) | §2.2, §3.2, §10 | Re-evaluation |
| Deprioritized-principle re-elevation candidates | §4 | Re-elevation decision |

## §7 — Amendment Packages

### §7.1 — Phase 4 Amendment Package (Channel 2, When Applicable)

[Populated only if implementation invalidated a specific Phase 4
artifact. "Not applicable — no Phase 4 artifact was invalidated"
otherwise.]

| ID | Surfacing Module / Artifact | Phase 4 Artifact Under Invalidation (change spec § / contract / impact-map row) | Why Untenable in Implementation | Candidate Amendments | Phase 5 Re-Entry Expectation |
|----|------------------------------|--------------------------------------------------------------------------------|---------------------------------|----------------------|------------------------------|
| AP4-01 | [M-NN Step 04 §6 / Step 05 §6 / Step 06–09 finding] | | | | [which Phase 5 steps re-run for which modules] |

**Note:** §6 Forward Handoffs are *not* operational while this
package exists. Phase 6 begins after Phase 4 amends, Phase 5
re-enters at the affected modules, and Step 10 re-runs.

### §7.2 — Phase 3 Amendment Package (Channel 3, When Applicable)

[Populated only if implementation evidence invalidated a Phase 3
design specification beyond Phase 4 repair. "Not applicable"
otherwise.]

| ID | Surfacing Module / Artifact | Phase 3 Design Specification Under Invalidation (Brief ID / MC-NN) | Why Untenable | Candidate Amendments | Cascade |
|----|------------------------------|--------------------------------------------------------------------|---------------|----------------------|---------|
| AP3-01 | | | | | [Phase 3 amends → Phase 4 re-enters (affected modules; Step 12 re-gate) → Phase 5 re-enters → Step 10 re-runs] |

### §7.3 — Phase 2 Amendment Package (Channel 4, When Applicable)

[Populated only if a Phase 2 commitment is invalidated — a mechanism
untenable in implementation beyond re-specification, or a §5.2 breach
beyond calibration tolerance. "Not applicable" otherwise.]

| ID | Surfacing Module / Artifact | Phase 2 Commitment Under Invalidation (MC-NN / cost model / HC-NN) | Why It Cannot Hold | Candidate Amendments | Cascade |
|----|------------------------------|--------------------------------------------------------------------|--------------------|----------------------|---------|
| AP2-01 | [module finding / §5.2 breach] | | | | [Phase 2 amends → Phase 3 re-enters (affected briefs) → Phase 4 re-enters (affected steps) → Phase 5 re-enters → Step 10 re-runs] |

[The full cascade is the deepest backward effect in the
existing-projects track — governance, not failure.]

## §8 — Upstream Toolkit Gaps Carried Forward

[From Step 01 §9.2, plus any structural gap surfaced mid-phase. These
do not block the Phase 6 handoff; they queue for the responsible
toolkit's revision in a separate session.]

| Gap ID | Owning Toolkit | Structural Absence | Phase 5 Workaround Used | Revision Recommendation |
|--------|----------------|--------------------|--------------------------|--------------------------|
| VG-U-01 | [Phase 4 / Phase 3 / Phase 2 / Phase 1 / Phase 5] | | | |

## §9 — Readiness Determination

### §9.1 — Per-Principle Gates

| Principle | Weight | Gate Status | Weighted Rationale (measured evidence, citing specific artifacts) |
|-----------|-------:|-------------|--------------------------------------------------------------------|
| Security | | [PASS/CONDITIONAL/FAIL] | |
| Maintainability | | | |
| Economics | | | |
| Operations | | | |
| Scoring & Metrics | | | |
| Correctness Verification | | | |

### §9.2 — Determination

**Determination:** [READY / CONDITIONALLY READY / NOT READY (Phase 5
gaps) / NOT READY (Phase 4 amendment required) / NOT READY (Phase 3
amendment required) / NOT READY (Phase 2 amendment required)]

[4–6 sentences supporting the determination: gate counts by status,
the §2 completion-map verdict, the §3 open-findings and regression
status, the §5 envelope status, §7 applicability, and §6.1 input
completeness. If multiple NOT READY conditions apply, the deepest
amendment path (Phase 2, then Phase 3, then Phase 4, then Phase 5
gaps) is named as the determination and all applicable packages are
populated, with the shallower conditions listed here. End with one
line stating what happens next: Phase 6 authorization, Phase 5
remediation + re-gate, or the amendment cycle + re-entry.]

### §9.3 — Conditional Remediation Register

| Conditional | Named Remediation | Owner | Target (phase / step / date) | Blocks Which Phase 6 Work |
|-------------|-------------------|-------|------------------------------|---------------------------|
| | | | | |

[Empty if no CONDITIONALs. Every CONDITIONAL row must be complete —
an unowned or untargeted conditional is not acceptable.]

### §9.4 — Override Authority & Record

Overriding a per-principle CONDITIONAL or a Phase 5-gap finding is a
practitioner decision with documented rationale and risk acceptance.
Overriding an amendment-path determination (Channel 2, 3, or 4) is
the highest tier: it means sending Phase 6 to audit — and ultimately
ship — changes built on a commitment the framework has flagged as
invalid. It is practitioner-only, documented here with the specific
downstream consequences articulated, and it does not remove the
amendment package from the queue.

| Element | Detail |
|---------|--------|
| Override applied? | [No — determination accepted as stated / Yes] |
| Determination / gate(s) overridden | |
| Override rationale (specific, not generic) | |
| Risk accepted (concrete downstream consequences) | |
| Conditions for revisit | |

## §10 — Confidence & Observation Notes

| Field | Value |
|-------|-------|
| Synthesis confidence | [H/M/L] |
| Bundle completeness | [Complete / Complete with named gaps / Incomplete — see §9] |
| Evidence-basis note (code-access mode across the phase; any mid-phase shift and its flagged artifacts) | |
| Open items requiring practitioner follow-up | |
| Dogfooding observations captured during synthesis (if any) | [list, or "None — see dogfooding-observations.md"] |

---

## Version

v1.0 (initial Implementation Bundle; re-run Step 10 against re-run
upstream steps after Phase 5 remediation, or against the amended
blueprint/bundle/plan after a Channel 2 / 3 / 4 amendment cycle)
```

---

## Evaluation Checklist

Before this artifact is accepted as complete, verify all items:

- [ ] §0 confirms Blueprint, Improvement Plan, and subject currency
      at Step 10 start, with the grounding-vs-invalidation decision
      rule applied to any parallel-track release or early-shipped
      dependency, and the code-access mode (with any mid-phase shift)
      recorded
- [ ] §1 catalogs every Phase 5 artifact — the project-level set and
      every module's full 04–08 set — with completeness against its
      own evaluation checklist; any missing or incomplete artifact is
      named and the determination reflects it
- [ ] §2 verifies the change surface completion map **in both
      directions**: every NEW/CHANGED module implemented, verified,
      reviewed, and scored; every Brief/MC landed (or deferred with
      practitioner acceptance, routed to §6.3); RETIRED removals
      verified with their consumers' changes; UNTOUCHED modules
      untouched per the Step 09 §4 diff; and no landed change without
      a specification basis
- [ ] §3 consolidates the Steps 06/07/09 determinations with the open
      findings inventory; every finding carries severity, status, and
      routing; any open Blocking finding drives NOT READY (Phase 5
      gaps)
- [ ] The full regression suite is green at the final landed state,
      every change-spec §7 regression-surface test passes, and any
      authorized break cites its specification basis
- [ ] §4 aggregates the per-artifact and per-module contributions
      (no re-scoring), refreshes against the Phase 4 Blueprint §5
      baseline without adjusting it, and runs the target distribution
      check; any miss is surfaced to the practitioner
- [ ] §5 aggregates the measured three-quantity actuals against the
      Phase 2 cost model and HC-NN capacity envelope; any breach
      beyond calibration tolerance is routed to §7.3 as a Channel 4
      finding, not footnoted or absorbed into an optimistic
      multiplier
- [ ] §5.3 produces the multiplier calibration table consolidating
      every Step 08 §4 calibration row, with honest sample sizes and
      BELIEVED → ESTIMATED graduations only where measurements exist
- [ ] The traceability chain is spot-checked and holds: commit → task
      (M-NN.WP-N.T-NN) → work package → PRD → change specification
      section → Phase 4 blueprint → Phase 3 design → Phase 2
      mechanism (MC-NN)
- [ ] §6 produces specific recipient lists for Phase 6, Phase 7, and
      next-cycle Phase 2; §6.1 verifies every Phase 6 concern from
      the instructions file's Connecting-to-Phase-6 table has its
      required inputs present and located
- [ ] §7.1 / §7.2 / §7.3 are populated if and only if the
      corresponding channel fired; each item names the surfacing
      module or artifact, the invalidated upstream commitment, why it
      cannot hold, candidate amendments, and the re-entry
      expectation; §7.2 and §7.3 name their cascades explicitly
- [ ] If any §7 package is populated, §6 states the forward handoffs
      are not operational and the determination is the corresponding
      NOT READY outcome
- [ ] §8 carries the Step 01 §9.2 upstream toolkit gaps forward for
      toolkit-revision sessions (non-blocking)
- [ ] §9 produces per-principle gates with weighted rationale citing
      measured evidence (coverage numbers, suite pass counts, scan
      results, benchmark deltas, actuals-vs-estimates), applying the
      documented criteria; the determination is exactly one of the
      six outcomes; if multiple NOT READY conditions apply, the
      deepest path is named and all applicable packages populated
- [ ] Every CONDITIONAL in §9 carries a named remediation, an owner,
      and a target; no CONDITIONAL is treated as a PASS
- [ ] §9.4 includes the override-authority tiers even if no override
      is applied; any override is documented alongside the standing
      determination, and an amendment-path override leaves the
      package queued
- [ ] §10 confidence and observation notes are populated
- [ ] No net-new implementation was produced in synthesis — no code,
      tests, or configuration written or committed, no scores
      invented, no verification re-run; every gap surfaced was routed
      to the responsible step or channel, not papered over
- [ ] The markdown output contains no project source code — the code
      lives in the repository at the refs the bundle cites
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)

---

*Part of the Phase 5 (Existing Projects) Implementation Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `implementation.existing-project.instructions.md`*
*Previous step: `step-09-integration-and-regression-validation.prompt.md`*
*Next: Phase 6 — Testing & Audit (on READY / CONDITIONALLY READY); or re-entry via the amendment cycles — Phase 4 (Channel 2), Phase 3 cascading through Phase 4 (Channel 3), or Phase 2 cascading through Phases 3 and 4 (Channel 4)*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Phase 5 Implementation Synthesis & Readiness Review prompt — the final Phase 5 step, combining the existing-track synthesis discipline (adapted from the Phase 4 Step 12 cluster pattern) with the greenfield Phase 5 gate's six-outcome determination. Ten clusters in two explicit parts: Part 1 synthesis (currency re-verification; artifact catalog; the two-way change surface completion map — every NEW/CHANGED module implemented/verified/reviewed/scored, every Brief/MC landed, RETIRED removals verified, UNTOUCHED untouched per the Step 09 §4 diff; verification & review consolidation with an open-findings inventory where any open Blocking finding drives NOT READY; scorecard aggregation and refresh against the Phase 4 Blueprint §5 baseline with the target distribution check; cost/capacity/calibration where a breach beyond calibration tolerance is a Channel 4 finding and the multiplier calibration table graduates BELIEVED → ESTIMATED with honest sample sizes; forward handoffs as specific recipient lists for Phase 6, Phase 7, and next-cycle Phase 2; three amendment packages as §7 addenda with named cascades; upstream toolkit gap carryforward) and Part 2 gate (per-principle criteria requiring measured evidence — the first gate in the track whose rationale cites numbers — plus the six outcomes with a deepest-path rule). Forward handoffs are explicitly non-operational while any amendment package exists; override authority is tiered with amendment-path overrides at the highest, practitioner-only tier, adapted from the greenfield Step 15 and the Phase 4 existing-track Step 12. |
