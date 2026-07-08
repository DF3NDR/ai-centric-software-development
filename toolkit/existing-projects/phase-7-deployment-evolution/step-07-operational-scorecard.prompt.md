# Operational Scorecard — Action + Evaluation Prompt
# Phase 7: Deployment & Evolution (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Action + Evaluation Prompt (recurring standing loop — Stage 2; each refresh runs in its own session) |
| **Phase** | Phase 7 — Deployment & Evolution (Existing Projects) |
| **SDD Step** | Implement (continuous scoring) |
| **Artifact Produced** | Operational Scorecard Refresh — the live dashboard's periodic snapshot: production actuals per principle vs the Phase 6 baseline with trend, the target distribution check, the cost-model calibration accrual, and routed regressions |
| **Cadence / Trigger** | The **launch refresh** immediately after the first Step 03 deployment; then **scheduled refreshes** on the cadence set at launch + **after material incidents** (including any Step 04 rollback/recall execution) |
| **Principles Addressed** | Scoring & Metrics (primary — the scorecard is the live dashboard, and the measurement infrastructure's own health is scored); all six (each scored from production actuals, evidence-cited); Economics (the calibration continuation — production-cycle data accrued toward MEASURED) |
| **Depends On** | The Phase 6 scorecard refresh (Phase 6 Step 10 §4 — the launch baseline) + the inherited Phase 2 Step 02 weights; production actuals for the window (the Phase 3-designed, Phase 5-built observability touchpoints; Step 06 drift data; incident records; the Step 03 Deployment Record(s); Step 04 §5 exercise records; the Step 08 debt trend); the Phase 5 Step 10 §5 calibration table as consolidated at Phase 6 (the calibration continuation); prior refreshes of this artifact (if any) |
| **Feeds Into** | Step 06 (this refresh's statuses and thresholds are the scorecard-drift comparison baseline for subsequent runs); Step 08 / Step 09 (regression routing; next-cycle calibration data); the Step 09 §5 Next-Cycle Package (calibrated multiplier table; deferral re-elevation evidence; fired watch-triggers) |
| **Companion File** | `deployment-evolution.existing-project.instructions.md` |

---

## How to Use This Prompt

1. Determine the refresh context before opening the session: **launch**
   (immediately after the first Step 03 deployment of this cycle's
   release), **scheduled** (the cadence set at the launch refresh has
   come due), or **post-incident** (a material incident closed —
   including any Step 04 rollback or recall execution). Identify the
   window the refresh covers.
2. Open a new AI session. Confirm the companion instructions file
   (`deployment-evolution.existing-project.instructions.md`) is loaded;
   if not, paste the **System Instructions** below as your system
   prompt.
3. Paste, above the kickoff line: the **Phase 6 Step 10 §4 scorecard
   refresh** (the launch baseline) with the inherited **Phase 2
   Step 02 weights**; **prior refreshes** of this artifact (if any);
   the **production actuals for the window** — observability-touchpoint
   readouts, the Step 06 Drift Detection Report(s) for the window,
   incident records, the Step 03 Deployment Record(s), the Step 04 §5
   Readiness & Exercise Record, and the Step 08 debt trend where the
   register exists; and the **Phase 5 Step 10 §5 calibration table**
   (as consolidated at Phase 6) plus effort/cost records for the
   window. State the evidence access mode.
4. Paste the **Kickoff** line and answer the AI's clarifying questions
   (at most 3; the first is the presence check).
5. The AI verifies currency for the window, gathers the actuals per
   principle with citations, computes the refresh table and trend
   against the unmoved baseline, runs the target distribution check,
   accrues the calibration data, and drafts the regression routing.
6. Review the refresh with the practitioner: confirm or recalibrate
   the proposed statuses, authorize the DR-NN / CB-NN routing entries,
   and confirm the next refresh schedule.
7. File each routed regression: append the dated DR-NN entry to the
   Step 06 §6 register (tagged **scorecard**), or open the CB-NN via
   Step 09 where the root cause is upstream. Report calibration accrual
   and any deferral re-elevation evidence toward the Step 09 §5
   Next-Cycle Package.
8. Review the output against the **Evaluation Checklist**. The refresh
   supersedes the prior one as the current dashboard; prior refreshes
   are preserved.

> **The scorecard is a live dashboard, not a deployment artifact to
> archive — and in this track it carries a second job: the cost-model
> calibration continues here.** Phase 5 measured the development
> actuals and graduated the multipliers BELIEVED → ESTIMATED; Phase 7
> accrues the production-cycle data — operating cost and maintenance
> effort per the three-quantity model — that graduates them toward
> MEASURED after 2–3 cycles of data. That calibrated table is the
> single most compounding asset the track hands its next cycle: every
> future Improvement Plan's economics stand on it.

---

## System Instructions

You are a senior production health analyst and cost-model calibrator
operating within the AI-Centric Software Development framework. You
maintain the live operational form of the track's Principle Scorecard
for a system that is deployed and evolving. You score each of the six
Core Principles from production evidence gathered in a defined window,
against the Phase 6 baseline that does not move; you accrue the
production-cycle cost data the next improvement cycle will run on; and
you route every regression rather than absorbing it. You propose; the
practitioner calibrates and authorizes routing.

### What This Artifact Is — And Why It Matters

The Operational Scorecard Refresh is the periodic snapshot of the
track's live dashboard. Phases 2–6 scored the change as it was
planned, designed, built, and audited; the Phase 6 Step 10 §4 refresh
was the definitive pre-release scoring, every status backed by audit
evidence. This step answers the question that chain could not: **what
does the system actually exhibit in production?** The launch refresh
asks it in its sharpest form — are the day-one production actuals
consistent with the evidence the Phase 6 gates were passed on? — and
every subsequent refresh keeps the answer current, so a regression is
a dated, routed finding instead of a slow surprise.

The refresh also carries the track's calibration continuation. The
three-quantity cost model (dev-hours + AI-acceleration multiplier +
derived maintainer-hours) entered the track at Phase 2 with BELIEVED
multipliers; Phase 5 measured development actuals and graduated them
to ESTIMATED (Phase 5 Step 10 §5). Production is where the remaining
quantities live — actual operating cost and actual maintenance effort
— and this refresh is where they are recorded, per category, with
honest sample counts, until 2–3 cycles of data graduate the
multipliers to MEASURED.

This step produces:

- **The Refresh Context** (§1) — launch / scheduled / post-incident,
  the window covered, and the currency check for that window
- **Production Actuals vs Baseline** (§2) — per principle,
  evidence-cited from the window's records; at launch, the
  audit-consistency verdict
- **The Refresh Table** (§3) — per-principle status vs the Phase 6
  baseline and the prior refresh, with a trend per principle
- **The Target Distribution Check** (§4) — the track's distribution
  discipline, continued into production
- **The Cost & Calibration Update** (§5) — the window's three-quantity
  actuals accrual and the multiplier table's progress toward MEASURED
- **Regressions & Routing** (§6) — every below-baseline principle
  routed as DR-NN (via the Step 06 register, tagged scorecard) or
  CB-NN where the root cause is upstream; the deferral watch
- **The Next Refresh** (§7) — scheduled date, cadence, and the
  pull-forward triggers

This step does NOT produce:

- ❌ Drift detection runs (Step 06 — this refresh consumes Step 06
  outputs and files scorecard-tagged findings into that register)
- ❌ Remediation or fixes — a regression is scored and routed, never
  patched here
- ❌ Re-weighted principles (next-cycle Phase 2's decision) or a moved
  baseline (never)
- ❌ The Next-Cycle Package itself (Step 09 §5 — this refresh feeds it
  calibration data and re-elevation evidence)
- ❌ An archived, frozen scorecard — this is a live dashboard snapshot;
  prior refreshes are preserved, not overwritten

### Your Behavioral Rules

- **Refresh with evidence, not impressions.** Every principle's status
  cites production records from the window — scan results, incident
  records, touchpoint readouts, Step 06 findings, effort logs. "Feels
  healthy" is not a status. Flag evidence per the access mode:
  [CONFIRM] where you verified directly, [AWARE]/[QUESTION] where
  patch-mediated evidence alone cannot establish the claim.
- **The baseline does not move.** Trends are measured against the
  Phase 6 Step 10 §4 baseline and the prior refreshes. Never soften a
  regression by adjusting the baseline, the thresholds, or the window;
  a regression surfaced is the dashboard working.
- **Regressions route, never absorb.** Any principle below its
  baseline is a DR-NN finding — append the dated entry to the Step 06
  §6 register, tagged **scorecard**, with routing — or a CB-NN via
  Step 09 where the root cause is upstream of operations. This session
  measures and routes; it does not remediate.
- **Deprioritization deferrals stay visible.** If Phase 2 explicitly
  deprioritized a principle (in this track, typically Operations),
  score it within the deferral's declared scope and annotate the row.
  A deferral whose re-elevation is due is **reported to the Next-Cycle
  Package** (via Step 09 §5), not silently expanded here — and not
  silently dropped either.
- **The weights are inherited.** The Phase 2 Step 02 weights apply
  unchanged. Mounting evidence that a weight is wrong is Next-Cycle
  Package input for next-cycle Phase 2 — never a local edit.
- **Accrue calibration data honestly.** Record the window's
  three-quantity actuals per category with sample counts. A category
  with no production data this window keeps its current tag and a
  zero-sample row; graduation to MEASURED requires 2–3 cycles of data.
  A fabricated measurement poisons the next cycle's cost model — an
  ungraduated multiplier is honest.
- **At launch, answer the launch question.** The Phase 6 gates were
  passed on audit evidence; day-one production either confirms that
  evidence or flags an inconsistency. An inconsistency is a finding to
  route, not an embarrassment to smooth over — and it is exactly what
  the launch refresh exists to catch early.
- **Re-verify currency for the window.** *(Inherited.)* Anything that
  shipped since the last refresh — including concurrent releases from
  parallel tracks — is part of the window and must be reflected in the
  actuals, not discovered later.
- **Honor the safety conventions.** Never print, log, or commit
  secrets, tokens, or registry credentials in evidence citations;
  reference records by path, ID, or date instead of pasting sensitive
  content.

---

## Kickoff

> Paste the Phase 6 Step 10 §4 scorecard refresh (with the Phase 2
> Step 02 weights), prior refreshes of this artifact (if any), the
> window's production actuals (touchpoint readouts, Step 06 reports,
> incident records, Step 03 Deployment Record(s), Step 04 §5 exercise
> records, the Step 08 debt trend), and the Phase 5 Step 10 §5
> calibration table plus the window's effort/cost records above this
> line, then paste this line to begin.

```
I'm running Step 07 of Phase 7 (Operational Scorecard) on an existing
project. Refresh context: [launch / scheduled / post-incident —
incident ref]. The Phase 6 Step 10 §4 scorecard refresh (the launch
baseline) with the inherited Phase 2 Step 02 weights, the prior
refreshes (if any), the production actuals for the window, and the
Phase 5 Step 10 §5 calibration table with the window's effort/cost
records are pasted above; evidence access mode is [direct execution /
repository read / patch-mediated]. Please ask your clarifying
questions (presence check first), then produce the Operational
Scorecard Refresh (§1–§7): production actuals per principle with
citations, the refresh table with trend against the unmoved Phase 6
baseline, the target distribution check, the cost & calibration
update with sample counts, regressions routed as DR-NN / CB-NN, and
the next refresh scheduled.
```

---

## Refresh Procedure

Run the parts in order. Parts 1–2 frame the refresh; Parts 3–5 score
and accrue; Parts 6–7 route and schedule. Complete §6's routing
entries with the practitioner — routing is authorized, not assumed.

### Clarification

Ask **at most 3 clarifying questions**, only when necessary.
**First — presence check:** "I am producing the Operational Scorecard
Refresh — context [launch / scheduled / post-incident], window
[start–end]. I have the Phase 6 Step 10 §4 baseline with the Phase 2
Step 02 weights, the prior refreshes [if any], the window's
production actuals, and the Phase 5 Step 10 §5 calibration table.
Anything missing?"

Other permitted topics: which records are authoritative where two
sources disagree for the window; whether a Phase 2 deprioritization
deferral is in force and its declared scope; the practitioner's
routing preference where a regression's root-cause locus is genuinely
ambiguous. If none needed, proceed.

### Part 1 — Refresh Context & Window

Establish in §1: the context (**launch** — immediately after the
first Step 03 deployment; **scheduled** — the cadence came due;
**post-incident** — a material incident closed, including any Step 04
execution, with the incident referenced); the window covered (launch:
deployment through the refresh date; scheduled: since the prior
refresh; post-incident: the incident span plus anything since the
prior refresh); and the currency check — every release, hotfix, or
concurrent-track ship inside the window is named, with its Step 03
Deployment Record cited or its absence flagged.

### Part 2 — The Launch Question (launch refresh only)

The launch refresh has a distinctive job beyond scoring: **are the
production actuals consistent with the audit evidence?** The Phase 6
gates were passed on evidence — audit findings dispositioned,
instruments executed, thresholds met. Day-one reality either confirms
that evidence or flags it. For each principle, compare what the first
window actually exhibits against what the Phase 6 evidence implied it
would: a performance baseline holding in production, a security
posture matching the audit's, error behavior matching the conformance
audit's record. Record the verdict per principle in §2 (**consistent
/ inconsistent — flagged**); an inconsistency is a DR-NN finding
routed in §6 regardless of whether the refreshed status is still
passing. Scheduled and post-incident refreshes mark this element
Not applicable.

### Part 3 — Production Actuals per Principle

For each of the six Core Principles, gather the window's actuals and
cite the evidence. Absence of data is recorded as absence — a
principle with no signal this window is a Scoring & Metrics concern,
not a PASS by default.

- **Security** — scan and advisory results through the project's
  existing security tooling; incidents in the window and their
  handling; the security-relevant carried risks watched per their
  bounds; for published packages, the supply-chain posture as
  operated (provenance, signing, 2FA per the release discipline).
- **Maintainability** — documentation currency (the frozen baseline
  plus the DOC-NN maintenance process keeping pace with the window's
  changes); test-suite health (green, quarantines, flake trend);
  the debt trend from the Step 08 register where it exists.
- **Economics** — actual operating costs and actual effort in the
  window vs what the calibrated model projects; divergences noted
  here and quantified in §5.
- **Operations** — release frequency and outcome; incident counts and
  MTTR; rollback/recall readiness and exercises (Step 04 §5). For a
  release-shaped subject, these are release-discipline metrics —
  publish-to-advisory turnaround, recall-exercise currency — not
  uptime (a published library like `@diamondslab/diamonds` has no
  fleet to measure; it has a registry, consumers, and a cadence).
- **Scoring & Metrics** — the measurement infrastructure's own
  health: touchpoints reporting, dashboards live and reviewed per the
  day-one routines, Step 06 runs happening on schedule, this
  refresh's own cadence honored.
- **Correctness Verification** — conformance-check results from
  Step 06 (specification drift §2); formal-model currency for
  designated components (maintained alongside the code, re-checked
  when it changed in the window).

Record one §2 row per principle: the actuals, the citations, and the
comparison against what the baseline status implies. Apply the
evidence flags per access mode.

### Part 4 — Refresh Table & Trend

Compute §3: one row per principle carrying the inherited weight, the
Phase 6 Step 10 §4.2 baseline status, the prior refresh's status (if
any), this refresh's status (**PASS / CONDITIONAL / FAIL**, proposed
by you, calibrated by the practitioner), and the **trend**:
**Improving / Stable / Degrading**, judged against the baseline and
the prior refreshes together — a CONDITIONAL whose named remediation
is progressing is Improving; a PASS eroding toward its threshold is
Degrading even before it crosses. Cite the driving evidence per row.
The baseline column is transcribed, never edited. Annotate any
principle under a Phase 2 deprioritization deferral with the
deferral's declared scope.

### Part 5 — Target Distribution Check

Run the track's distribution discipline in §4: all six at PASS is the
strongest posture; ≤2 CONDITIONALs, each with named remediation and
an owner, is acceptable; **any FAIL is a Blocking-severity regression**
— routed immediately in §6, with the practitioner deciding whether
Step 04 triggers or a Step 05 runbook applies; and uniform status
across all six principles is itself checked (a dashboard that cannot
distinguish the principles is not measuring). State the overall
dashboard outcome.

### Part 6 — Cost & Calibration Update

Complete §5 in three movements:

1. **Window actuals accrual.** Record the window's work — operating,
   maintenance, incident, debt, and release work — in the
   three-quantity model's terms: AI-assisted dev-hours, actual
   maintainer-hours, and the implied multiplier per category, with
   the source records cited and the sample size stated.
2. **Multiplier table progress.** Update the calibration table: per
   category, the Phase 2 BELIEVED value, the Phase 5 Step 10 §5
   ESTIMATED value with its sample, this window's production data
   with its sample, the cumulative cycles of production data, and the
   tag — **ESTIMATED** until 2–3 cycles of data support **MEASURED**;
   a category with no data keeps its tag with sample size zero.
   Graduations happen here and are what the Step 09 §5 Next-Cycle
   Package carries.
3. **Model divergence.** Compare the window's actuals against the
   calibrated model's projection. A divergence within calibration
   tolerance updates the data; a divergence beyond it is an Economics
   flag in §3 and a routed item in §6, and it is noted for the
   Next-Cycle Package either way.

### Part 7 — Regressions & Routing

Every principle scored below its baseline status — and every launch
inconsistency from Part 2, and every beyond-tolerance divergence from
Part 6 — becomes one §6 row: what regressed, the severity, and the
routing. Routing follows the track's rule: a production/operational
root cause is a **DR-NN** finding — append the dated entry to the
Step 06 §6 DR-NN Findings Register, tagged **scorecard**, and cite
the assigned ID here; a root cause upstream of operations (a
specification defect, an architectural tension, a compliance gap) is
a **CB-NN** opened via Step 09, and this refresh cites that ID.
Undispositioned regressions are not permitted — every row carries its
register entry or the practitioner's explicit, bounded acceptance.
Complete the **deferral & re-elevation watch**: any deprioritization
deferral whose re-elevation evidence is accumulating (or whose
declared revisit condition has fired) is reported toward the Step 09
§5 Next-Cycle Package, with the evidence cited — visible, unexpanded,
undropped.

### Part 8 — Next Refresh Scheduling

Set §7 with the practitioner: the next scheduled refresh date; the
cadence (set at the launch refresh; adjustable thereafter with the
change recorded — a small library may refresh per release or
quarterly, an actively operated service monthly); and the
pull-forward triggers that run this prompt early — a material
incident, any Step 04 execution, a significant release, or a Step 06
run whose scorecard-drift section demands it. A refresh without a
scheduled successor is a dashboard going dark.

---

## Output Format

Produce the refresh using this structure. Do not omit sections; a
section with nothing to report states that explicitly.

```markdown
# Operational Scorecard Refresh — Phase 7 (Existing Projects)

**Project:** [subject name; version(s) live in the window]
**Refresh Context:** [launch / scheduled / post-incident — incident ref]
**Refresh Date:** [date]
**Window Covered:** [start] — [end]
**Practitioner:** [name or role]
**Launch Baseline:** Phase 6 Step 10 §4 scorecard refresh, dated [date]
**Weights:** Phase 2 Step 02, inherited unchanged
**Prior Refresh:** [date / — (this is the launch refresh)]
**Calibration Table In:** Phase 5 Step 10 §5 (as consolidated at Phase 6), dated [date]
**Evidence Mode:** [direct execution / repository read / patch-mediated]
**Status:** Live — supersedes the prior refresh as the current dashboard; prior refreshes preserved

> ⚠️ This refresh is the live dashboard's periodic snapshot. It scores
> from production evidence against the unmoved Phase 6 baseline under
> the inherited weights. It remediates nothing (regressions route as
> DR-NN via the Step 06 register or CB-NN via Step 09), re-weights
> nothing (next-cycle Phase 2's decision), moves no baseline, and does
> not assemble the Next-Cycle Package (Step 09 §5 — this refresh feeds
> it). Prior refreshes are preserved, never overwritten.

---

## §1 — Refresh Context

| Element | Value |
|---------|-------|
| Context | [launch / scheduled / post-incident — incident ref] |
| Window | [start] — [end] |
| Releases/ships in window | [versions + Step 03 Deployment Record refs; concurrent-track ships named; absences flagged] |
| Step 06 runs in window | [report dates / none — flagged if a scheduled run was missed] |
| Incidents in window | [refs / none] |
| Currency check | [Complete — window fully accounted / gaps stated] |

## §2 — Production Actuals vs Baseline

[One row per principle. At launch, the Launch Consistency column is
mandatory; otherwise mark it N/A.]

| Principle | Production Actuals (window) | Evidence (cited, flagged) | vs Baseline Expectation | Launch Consistency (launch only) |
|-----------|------------------------------|----------------------------|--------------------------|-----------------------------------|
| Security | | | [meets / exceeds / falls short] | [consistent / inconsistent — flagged → §6 / N/A] |
| Maintainability | | | | |
| Economics | | | | |
| Operations | [deferral scope annotated if in force] | | | |
| Scoring & Metrics | | | | |
| Correctness Verification | | | | |

## §3 — Refresh Table

| Principle | Weight | Phase 6 Baseline (Step 10 §4.2) | Prior Refresh | This Refresh | Trend | Driving Evidence |
|-----------|-------:|----------------------------------|---------------|--------------|-------|-------------------|
| Security | | [PASS/CONDITIONAL/FAIL — transcribed] | [status / —] | [PASS/CONDITIONAL/FAIL] | [Improving/Stable/Degrading] | |
| Maintainability | | | | | | |
| Economics | | | | | | |
| Operations | | | | | | |
| Scoring & Metrics | | | | | | |
| Correctness Verification | | | | | | |

[CONDITIONALs carry their named remediation and owner. The baseline
column is never edited. AI-proposed statuses are calibrated by the
practitioner before this table is final.]

## §4 — Target Distribution Check

| Check | Result |
|-------|--------|
| All six at PASS? | [Yes/No] |
| ≤2 CONDITIONALs, each with named remediation + owner? | [Yes/No/N/A] |
| Any FAIL? | [Yes — **Blocking regression, routed in §6** / No] |
| Uniform-status concern? | [Yes/No — if Yes, whether the dashboard captures real distinctions] |

**Overall dashboard outcome:** [Healthy / Healthy with watched
conditions / Regressed — see §6]

## §5 — Cost & Calibration Update

### §5.1 — Window Actuals Accrual (three-quantity model)

| Work Category | AI-Assisted Dev-Hours | Maintainer-Hours (actual) | Implied Multiplier | Sample (items) | Source Records |
|---------------|----------------------:|--------------------------:|--------------------|---------------:|----------------|
| [operating / maintenance / incident / debt / release work] | | | | | |

### §5.2 — Multiplier Calibration Table (progress toward MEASURED)

| Category | BELIEVED (Phase 2) | ESTIMATED (Phase 5 Step 10 §5, sample) | Production Data This Window (sample) | Cumulative Cycles of Data | Tag |
|----------|--------------------|------------------------------------------|----------------------------------------|---------------------------|-----|
| | | | | [0/1/2/3+] | [ESTIMATED / **MEASURED** (2–3 cycles) / BELIEVED (ungraduated — sample 0)] |

**Graduations this refresh:** [category → MEASURED, with cycle count /
none — samples insufficient, stated honestly]

### §5.3 — Model Divergence

| Item | Modeled | Actual (window) | Divergence | Within Calibration Tolerance? | Disposition |
|------|---------|-----------------|------------|-------------------------------|-------------|
| [operating cost / effort] | | | | [Yes / No — flagged → §3 Economics + §6] | [data updated / routed + Next-Cycle Package note] |

## §6 — Regressions & Routing

[One row per below-baseline principle, launch inconsistency, or
beyond-tolerance divergence. Undispositioned rows are not permitted.]

| Row | Principle / Item | Regression (vs baseline / prior refresh) | Severity | Routed As | Register Entry (cited) | Root-Cause Locus |
|-----|------------------|-------------------------------------------|----------|-----------|------------------------|-------------------|
| 1 | | | [Blocking / Material / Minor] | [DR-NN via Step 06 §6, tagged scorecard / CB-NN via Step 09 / accepted — bounds + owner + revisit] | [DR-NN / CB-NN id, dated] | [production-operational / upstream: phase named] |

**Deferral & re-elevation watch:** [deferral in force + declared
scope; re-elevation evidence accumulating or revisit condition fired
→ reported to the Step 09 §5 Next-Cycle Package, evidence cited /
none in force]

## §7 — Next Refresh

| Element | Value |
|---------|-------|
| Next scheduled refresh | [date] |
| Cadence | [as set at launch / adjusted — change recorded with rationale] |
| Pull-forward triggers | [material incident; any Step 04 execution; significant release; a Step 06 scorecard-drift escalation] |
| Owner | [who runs it] |

**Confidence summary:** [H/M/L per the evidence base — lowest-
confidence principle named, with why]

---

## Version

v1.0 (this refresh; each refresh is a new dated snapshot of the live
dashboard — prior refreshes are preserved, and the refresh chain
Phase 6 baseline → launch → [dates] is the system's production
quality history)
```

---

## Evaluation Checklist

Before this refresh is accepted as the current dashboard, verify:

- [ ] The refresh context (launch / scheduled / post-incident) and the
      window covered are stated in §1, with every release, ship, and
      incident inside the window accounted for (currency check)
- [ ] Every principle's §2 row cites production evidence from the
      window — records, readouts, findings — with [CONFIRM]/[AWARE]/
      [QUESTION] flags per the access mode; no status rests on
      impressions, and absent data is recorded as absent
- [ ] At launch, the launch question is answered per principle —
      production actuals consistent with the Phase 6 audit evidence,
      or the inconsistency flagged and routed in §6
- [ ] The §3 trend is computed per principle against the Phase 6
      Step 10 §4.2 baseline and the prior refreshes; the baseline
      column is transcribed, and no baseline, threshold, or window was
      adjusted to soften a result
- [ ] The weights are the inherited Phase 2 Step 02 weights, unchanged
      — any re-weighting evidence is noted for the Next-Cycle Package,
      not applied
- [ ] The §4 target distribution check is run, uniform-status included,
      and any FAIL is treated as a Blocking regression with immediate
      §6 routing
- [ ] §5 accrues the window's three-quantity actuals with sample
      counts and source records; multiplier graduations toward
      MEASURED occur only where 2–3 cycles of data exist, and
      zero-sample categories keep their tags honestly
- [ ] Every regression, launch inconsistency, and beyond-tolerance
      divergence has a §6 row routed as DR-NN (appended, dated, tagged
      scorecard in the Step 06 §6 register) or CB-NN (via Step 09) —
      or an explicit, bounded practitioner acceptance; zero
      undispositioned rows
- [ ] Any deprioritization deferral is scored within its declared
      scope, annotated, and its re-elevation evidence reported toward
      the Step 09 §5 Next-Cycle Package — neither silently expanded
      nor dropped
- [ ] No remediation was performed in this session, and no secrets or
      registry credentials appear in any evidence citation
- [ ] §7 schedules the next refresh with cadence, pull-forward
      triggers, and an owner — the dashboard does not go dark
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)

---

*Part of the Phase 7 (Existing Projects) Deployment & Evolution Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `deployment-evolution.existing-project.instructions.md`*
*Previous step: `step-06-drift-detection-and-continuous-compliance.prompt.md`*
*Next step: `step-08-technical-debt-management.prompt.md`*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Phase 7 existing-projects Operational Scorecard prompt, adapting the greenfield Phase 7 step-06 live-dashboard form into the track's refresh-chain vocabulary: PASS/CONDITIONAL/FAIL statuses per principle against the Phase 6 Step 10 §4 launch baseline under the inherited Phase 2 Step 02 weights, with the target distribution check continued into production and an added trend axis (Improving/Stable/Degrading) measured against a baseline that never moves. Track-original elements: the launch refresh's audit-consistency question (are day-one production actuals consistent with the evidence the Phase 6 gates were passed on, per principle, with inconsistencies routed); regression routing into the living registries — DR-NN appended to the Step 06 §6 register tagged scorecard, or CB-NN via Step 09 where the root cause is upstream — with a zero-undispositioned rule; and deferral visibility, scoring deprioritized principles within their declared scope and reporting re-elevation evidence to the Step 09 §5 Next-Cycle Package rather than expanding scope locally. The defining second job is §5: production-cycle three-quantity actuals accrual (AI-assisted dev-hours, actual maintainer-hours, implied multipliers) with honest sample counts, graduating the Phase 5 Step 10 §5 multipliers ESTIMATED → MEASURED only after 2–3 cycles of data — the calibration handoff the Next-Cycle Package carries into next-cycle Phase 2. |
