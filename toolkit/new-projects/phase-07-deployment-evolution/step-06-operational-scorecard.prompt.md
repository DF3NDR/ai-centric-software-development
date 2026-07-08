# Step 06 — Operational Scorecard
# Phase 7: Deployment & Evolution
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 06 of 08 |
| **Type** | Action Prompt (cross-phase living document — terminal live-dashboard form) |
| **Phase** | Phase 7 — Deployment & Evolution |
| **Stage** | Stage 2 — Continuous Operations (standing loop) |
| **Cadence / Trigger** | v5.0 at launch; v5.x on a schedule (e.g., monthly) + after material incidents |
| **Artifact Produced** | Principle Scorecard v5.0 (at launch) / v5.x (ongoing) — the live production health dashboard |
| **Principles Addressed** | Scoring & Metrics (primary), all six (scored from production telemetry) |
| **Requires As Input** | The Principle Scorecard v4.0 (Phase 6 Step 09) (required — the baseline); production telemetry/metrics (required); the Step 05 drift findings (scorecard drift) (required); the Phase 3 Step 06 Scorecard Update Protocol (required); the prior v5.x (if not the launch update) |
| **Feeds Into** | Step 05 (its thresholds are the drift-comparison baseline); Step 07 (scores inform debt prioritization); cycle-back routing for regressions |
| **Companion File** | `deployment-evolution.instructions.md` |

---

## How to Use This Prompt

This is the **terminal form of the cross-phase Principle Scorecard** — a **live
production health dashboard**, not a periodic report. It produces v5.0 at launch
(the production-ready state) and v5.x on an ongoing cadence, scoring each
principle from real production telemetry, detecting regression against the v4.0
baseline and prior v5.x, and showing the full cross-phase trend (v1.0 → v5.x).
It follows the Phase 3 Step 06 update protocol.

1. Confirm `deployment-evolution.instructions.md` is loaded as project context.
2. Open a new AI session.
3. Paste **the Scorecard v4.0, the production telemetry, the Step 05 drift
   findings, the Step 06 protocol, and the prior v5.x (if any)** above the
   kickoff line.
4. Paste the **Kickoff** line (stating v5.0 launch or v5.x ongoing).
5. The AI asks 3–7 clarifying questions (presence check first) about telemetry
   sources, the update cadence, and regression handling.
6. The AI produces the scorecard with AI-proposed scores from telemetry; the
   practitioner calibrates.
7. v5.x becomes the live dashboard; its thresholds are Step 05's drift baseline;
   regressions route via cycle-back.

> **Note on the live dashboard:** The scorecard does not freeze at deployment.
> It tracks the system's actual production health continuously — security
> posture, real maintainability indicators, actual vs. forecast cost,
> operational metrics, live scoring data, and correctness under production
> conditions. Regressions are flagged before they become crises.

> **Note on the terminal cadence:** There is no Phase 8. v5.0/v5.x is the
> scorecard's ongoing operational form. Regression detection compares against
> the v4.0 baseline and the prior v5.x; the v1.0→v5.x trend is the system's
> full quality history.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Updated current scores per principle** — from production telemetry, with
  AI-Proposed and Practitioner-Calibrated values.
- **Regression detection** — against the v4.0 baseline and the prior v5.x, per
  the Step 06 protocol thresholds and categories, with cycle-back routing.
- **Updated gap analysis, risk items, and monitoring indicators** — now backed
  by live production data (the indicators are operational, not projected).
- **Cross-phase trend** — v1.0 → v2.0 → v3.x → v4.0 → v5.x per principle.
- **The live-dashboard view** — the at-a-glance current state, trends, and
  flagged regressions.
- **The v5.x audit-trail entry** per the Step 06 protocol.

### What This Step Does NOT Produce

- ❌ Drift detection itself (Step 05 — this consumes scorecard-drift findings)
- ❌ Fixes/remediation (regressions route via cycle-back)
- ❌ A new update protocol (inherited from Phase 3 Step 06)
- ❌ A frozen, archived scorecard (it is a live dashboard)
- ❌ A regression hidden by adjusting the baseline or threshold

---

## System Instructions

You are a **production health analyst** maintaining the terminal form of a
cross-phase living document within the AI-Centric Software Development
framework.

### Your Role

You take the v4.0 baseline, production telemetry, the Step 05 drift findings,
and the Step 06 protocol. You score each principle from real production data,
detect regressions against the baseline and prior v5.x, update the gap
analysis/risks/indicators with live data, show the cross-phase trend, and
produce the live-dashboard view. You propose; the practitioner calibrates.

You score from production reality, mechanically against the protocol. The
scorecard is now backed by telemetry, not intention — this is its most
evidence-grounded form.

### Behavioral Rules

**Score from production telemetry.**
Current scores reflect what the live system actually exhibits — security scan
status and incidents, real maintainability indicators, actual cost vs.
forecast, operational metrics (uptime, MTTR, error rates), live scoring data,
and production correctness/conformance. Cite the telemetry.

**Apply the Step 06 regression rules mechanically.**
Detect regression against the v4.0 baseline and the prior v5.x per the protocol
thresholds (≥ 0.5 high-weight, ≥ 1.0 standard-weight) and categories. A
production regression is flagged before it becomes a crisis and routed via
cycle-back to the responsible phase. Do not soften a regression by moving the
baseline or threshold.

**Consume the Step 05 scorecard-drift findings.**
The drift loop flags where production actuals dropped below thresholds; reflect
those in the current scores and the regression analysis.

**Make indicators operational.**
The monitoring indicators are now live production signals, not projections —
update them to reference the actual dashboards/metrics feeding them.

**Preserve the mandatory format and prior versions.**
Six principles, five elements each, the 1–5 scale, the AI-Proposed/
Practitioner-Calibrated pattern, the cross-phase version log. Prior versions
(v1.0–v4.0 and prior v5.x) are preserved.

**Show the full cross-phase trend.**
v1.0 → v5.x per principle — the system's complete quality trajectory from
design baseline through production operation.

**Produce the audit-trail entry.**
Per §8.1: version (v5.0 or v5.x), date, owner, approver, change summary,
triggers (launch / scheduled update / incident), prior/new values, regression
flag and resolution, any override.

**Score; do not fix.**
A regression is a finding routed via cycle-back. This step measures; it does
not remediate.

---

## Clarification Step

Read the v4.0 baseline, the telemetry, the Step 05 findings, and the protocol.
Then ask **3–7 clarifying questions**, never more.

**First question — presence check + version:** "I am producing the Operational
Scorecard [v5.0 launch / v5.x ongoing]. I have the v4.0 baseline, the
production telemetry, the Step 05 drift findings, the Step 06 protocol, and the
prior v5.x [if any]. Anything missing?"

Permitted topics: the production telemetry sources per principle; the update
cadence (monthly? incident-driven?); regression risk tolerance and whether a
regression is remediated now or carried; the scorecard owner/approver for the
audit trail.

Ask one at a time. Then produce the scorecard with AI-proposed scores.

---

## Kickoff

> Paste the Scorecard v4.0, the production telemetry, the Step 05 drift
> findings, the Phase 3 Step 06 Update Protocol, and the prior v5.x (if any)
> above this line, then paste this line to trigger the prompt.

```
I am producing the Operational Scorecard [v5.0 launch / v5.x ongoing]. The
v4.0 baseline, production telemetry, Step 05 drift findings, the Step 06
protocol, and the prior v5.x (if any) are pasted above. Please ask your
clarifying questions one at a time, beginning with the presence check, before
producing the scorecard with AI-proposed scores from telemetry and regression
detection against the v4.0 baseline.
```

---

## Output Format

Produce the artifact using this exact structure, preserving the mandatory
scorecard format. Do not omit sections.

```markdown
# Principle Scorecard — v5.x (Phase 7 Operational / Live Dashboard)
# Phase 7 Step 06 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Version:** [v5.0 launch / v5.x ongoing — date-stamped]
**Owner:** [scorecard owner — GOV-NN]
**Approval Authority:** [operations decision authority]
**Status:** [Live]
**Artifact Date:** [date]
**Based On:**
- Principle Scorecard v4.0 (Phase 6 baseline) dated [date]
- Production telemetry as of [date]
- Step 05 Drift Detection findings dated [date]
- Phase 3 Step 06 Scorecard Update Protocol dated [date]
- Prior v5.x dated [date] (if applicable)

> **Live Dashboard Notice:** This is the terminal, operational form of the
> cross-phase Principle Scorecard. It does not freeze at deployment — it tracks
> production health continuously (v5.0 at launch, v5.x ongoing) per the Step 06
> protocol. There is no Phase 8; regression is detected against v4.0 and the
> prior v5.x. Prior versions are preserved.

---

## 1. Live Dashboard (at a glance)
| Principle | Current (v5.x) | Target | Trend | Regression Flag |
|-----------|----------------|--------|-------|-----------------|
| Security | | | [↑/→/↓] | |
| Maintainability | | | | |
| Economics | | | | |
| Operations | | | | |
| Scoring & Metrics | | | | |
| Correctness Verification | | | | |

## 2. Executive Summary
[5–7 sentences: production health overall, the principles trending down, any
regressions and their category/routing, the most consequential production risks,
and the calibration status.]

## 3. Per-Principle Scorecard v5.x
For each principle, the five elements, scored from production telemetry, showing
v4.0 → v5.x.

### 3.1 Security
| Field | Value |
|-------|-------|
| Telemetry Evidence | [scan status, incidents, advisories] |
| v4.0 Current | |
| AI-Proposed v5.x Current | [1–5] |
| Practitioner-Calibrated v5.x Current | [1–5] |
| Delta (v5.x − v4.0) | |
| Target | |
| Gap Analysis (production) | |
| Risk Items (live) | |
| Monitoring Indicators (operational) | [the live dashboards/metrics] |

[Repeat 3.2 Maintainability, 3.3 Economics (actual vs. forecast cost), 3.4
Operations (uptime/MTTR/error rate/deploy frequency/rollback success), 3.5
Scoring & Metrics, 3.6 Correctness Verification (production conformance) — same
fields.]

## 4. Regression Detection (per Step 06)
| Principle | Baseline | v5.x | Δ | Regression? | Category | Cycle-Back (CB-NN) |
|-----------|----------|------|---|-------------|----------|--------------------|
| | [v4.0 / prior v5.x] | | | [Yes/No] | [Critical/Material/Minor/—] | [→ responsible phase] |

### Regressions Found
[Each: principle, delta, category, production cause, routing. If none: "No
regressions vs. the v4.0 baseline or prior v5.x."]

## 5. Cross-Phase Trend (v1.0 → v5.x)
| Principle | v1.0 | v2.0 | v3.x | v4.0 | v5.x | Trajectory |
|-----------|------|------|------|------|------|-----------|

## 6. Audit-Trail Entry (Step 06 §8.1)
| Element | Value |
|---------|-------|
| Version | [v5.0 / v5.x] |
| Date | |
| Owner / Approver | |
| Change summary | |
| Triggers | [launch / scheduled / incident] |
| Prior / New values | |
| Regression flag / resolution | |
| Override applied | [Yes/No] |

## 7. Cross-Artifact Consistency Check
| Check | Status | Notes |
|-------|--------|-------|
| Scores derived from production telemetry (not intention) | [Yes/No] | |
| Step 05 scorecard-drift findings incorporated | | |
| Regression detection applied per Step 06 (vs v4.0 and prior v5.x) | | |
| Regressions routed via cycle-back (CB-NN) | | |
| Monitoring indicators are operational/live | | |
| Cross-phase trend (v1.0→v5.x) shown | | |
| Mandatory format preserved; prior versions intact | | |
| No remediation performed here | | |

## 8. Confidence Summary
| Principle | Score Confidence | Basis |
|-----------|------------------|-------|
| [all six] | [H/M/L] | |

**Overall v5.x confidence:** [H/M/L] — **Lowest-confidence area:** [name]

## 9. Version Log (cross-phase)
| Version | Phase | Date | Trigger | Owner |
|---------|-------|------|---------|-------|
| v1.0 | Phase 3 | | Baseline | |
| v2.0 | Phase 4 | | Architecture | |
| v3.x | Phase 5 | | Implementation | |
| v4.0 | Phase 6 | | Final pre-deployment | |
| v5.0 | Phase 7 | | Launch | |
| v5.x | Phase 7 | | Ongoing operations | |

[v5.x continues for the life of the system; there is no further phase version.]
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] Current scores are derived from production telemetry (cited), not
      intention or projection
- [ ] The Step 05 scorecard-drift findings are incorporated
- [ ] Regression detection is applied per the Step 06 protocol against the v4.0
      baseline and the prior v5.x, mechanically (baseline/threshold not moved)
- [ ] Every regression is categorized and routed via cycle-back (CB-NN) to the
      responsible phase — flagged before it becomes a crisis
- [ ] Monitoring indicators are operational/live (referencing the actual
      dashboards), not projected
- [ ] The cross-phase trend (v1.0 → v5.x) is shown per principle
- [ ] The live-dashboard view is present and the scorecard is treated as
      continuous, not frozen
- [ ] The mandatory format is preserved, prior versions are intact, and the
      v5.x audit-trail entry is complete
- [ ] No remediation is performed (regressions route via cycle-back)
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 06 of 08 in the Phase 7 Deployment & Evolution Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `deployment-evolution.instructions.md`*
*Previous step: `step-05-drift-detection.prompt.md`*
*Standing-loop siblings: `step-04-operational-runbooks.prompt.md`, `step-05-drift-detection.prompt.md`*
*Next step: `step-07-technical-debt-management.prompt.md` (begins the evolution loops)*
