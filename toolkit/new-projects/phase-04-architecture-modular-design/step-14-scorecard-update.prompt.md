# Step 14 — Scorecard Update
# Phase 4: Architecture & Modular Design
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 14 of 16 |
| **Type** | Action Prompt with Clarification Step (cross-phase living document update) |
| **Phase** | Phase 4 — Architecture & Modular Design |
| **SDD Step** | Implement (governance) → Scoring & Metrics |
| **Artifact Produced** | Principle Scorecard v2.0 (the Phase 3 baseline updated to reflect the detailed architecture) |
| **Principles Addressed** | Scoring & Metrics (primary), all six (each is re-scored against the architecture), Correctness Verification (regression detection) |
| **Requires As Input** | All Stage 1 outputs (Steps 01–06) and all Stage 2 outputs (Steps 07–09 + every Step 08 module spec) (required); Phase 3 Principle Scorecard v1.0 (required — the baseline); Phase 3 Step 06 Scorecard Update Protocol (required — the governing protocol); Step 10–13 API contracts (recommended, if produced) |
| **Feeds Into** | Step 15 (architecture review references the updated scorecard); Step 16 (the gate verifies v2.0 and regression handling); Phase 5 (inherits v2.0 and continues to v3.x per the Step 06 protocol) |
| **Companion File** | `architecture-modular-design.instructions.md` |

---

## How to Use This Prompt

This is an **action prompt that updates a cross-phase living document**.
It produces **Principle Scorecard v2.0** — the Phase 3 baseline (v1.0)
updated to reflect every Phase 4 architectural decision — following the
update protocol established in Phase 3 Step 06. The scorecard is the
framework's instrument for making design health visible and regression
detectable across phases; this is its first update.

1. Confirm `architecture-modular-design.instructions.md` is loaded as
   project context.
2. Open a new AI session with a large context window.
3. Paste **the required inputs** above the kickoff line: all Stage 1 and
   Stage 2 outputs, the Phase 3 Principle Scorecard v1.0, and the Phase 3
   Step 06 Scorecard Update Protocol. Include the Step 10–13 API
   contracts if produced.
4. Paste the **Kickoff** line.
5. The AI asks between 3 and 7 clarifying questions — beginning with a
   presence check — about score calibration anchors and risk tolerance
   for any regressions detected.
6. The AI produces Scorecard v2.0 with AI-Proposed current scores
   reflecting the architecture, regression detection against the v1.0
   baseline per the Step 06 rules, and updated gap analysis, risk items,
   and monitoring indicators.
7. The practitioner reviews and calibrates the scores. The AI updates
   with Practitioner-Calibrated values.
8. v2.0 becomes the input to Step 15 and Step 16; Phase 5 continues it to
   v3.x per the Step 06 protocol.

> **Note on format inheritance:** Per the Step 06 protocol §10, this
> update preserves the mandatory format conventions from the v1.0
> baseline — the six-principle structure, the five elements per principle
> (current, target, gap analysis, risk items, monitoring indicators), the
> 1–5 scale, the AI-Proposed/Practitioner-Calibrated pattern, and the
> cross-phase version log. This update adds Phase 4 content; it does not
> change the format.

> **Note on what this step does NOT do:** It does not establish the
> update protocol (that is the inherited Phase 3 Step 06 protocol). It
> does not produce Phase 5+ scorecard entries. It applies the existing
> protocol to produce exactly one update: v1.0 → v2.0.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Updated current scores per principle** — reflecting the Phase 4
  architecture, with AI-Proposed and Practitioner-Calibrated values.
- **Target reconciliation** — confirmation that targets still hold, or
  documented target changes (a substantive change per the Step 06
  protocol).
- **Regression detection against v1.0** — per the Step 06 thresholds and
  categories (Critical / Material / Minor), comparing v2.0 current scores
  to the v1.0 baseline.
- **Updated gap analysis per principle** — what the architecture closed
  and what remains for Phase 5 and beyond.
- **Updated risk items per principle** — risks the architecture
  introduced, resolved, or left open.
- **Updated monitoring indicators per principle** — indicators that
  Phase 4 made concrete (e.g., now mapped to module monitoring hooks
  H-NN).
- **Cross-principle dashboard** — weighted current and target scores,
  v1.0 vs. v2.0.
- **Architectural decisions driving score changes** — traceability from
  each score change to the Phase 4 artifact that drove it.
- **Audit trail entry** — the full v2.0 audit trail entry per the Step 06
  protocol §8.

### What This Step Does NOT Produce

- ❌ The update protocol (inherited from Phase 3 Step 06)
- ❌ Phase 5, 6, or 7 scorecard entries (those phases produce their own
  per the protocol)
- ❌ Modifications to Phase 4 architecture artifacts (the scorecard
  reflects them; it does not change them)
- ❌ The readiness determination (Step 16 — the scorecard is an input)
- ❌ A guarantee that any principle reaches its target (the scorecard
  measures; later phases close gaps)
- ❌ Implementation content (Phase 5)

If the architecture produced a regression that cannot be remediated
within Phase 4, the scorecard documents it per the protocol — it does not
hide it by adjusting the target. Target changes are substantive changes
requiring documentation and approval per the Step 06 protocol.

---

## System Instructions

You are a **senior systems analyst** updating a cross-phase living
document within the AI-Centric Software Development framework. You produce
Scorecard v2.0 — the architecture's effect on each Core Principle's
health, measured against the Phase 3 baseline and governed by the Step 06
protocol.

### Your Role

You take all the Phase 4 architecture artifacts, the v1.0 baseline
scorecard, and the Step 06 update protocol. You re-score each principle
against the architecture as it now stands. You detect regressions against
the baseline per the protocol's rules. You update the gap analysis, risk
items, and monitoring indicators. You document which architectural
decision drove each score change. You produce the audit trail entry.

You score the architecture as it is, not as it is intended to become. You
apply the protocol's regression rules mechanically — a regression is what
the thresholds say it is, not a matter of judgment. You propose; the
practitioner calibrates.

### Behavioral Rules

**Score the architecture, not the intentions.**
The current scores reflect what the Phase 4 architecture actually
delivers — the module specifications, the frameworks, the contracts — not
what the team hopes the implementation will achieve. AI tends to score
intentions; score the artifacts in hand.

**Apply the Step 06 regression rules mechanically.**
A regression is a current-score decline from v1.0 meeting the protocol's
thresholds: ≥ 0.5 for a high-weight principle (weight ≥ 20), ≥ 1.0 for a
standard-weight principle. Categorize each regression (Critical /
Material / Minor) per the protocol §5.2 and apply its escalation path. Do
not soften a regression by adjusting the baseline — the baseline is fixed.

**Preserve the mandatory format (protocol §10.1).**
Six principles, five elements each (current, target, gap analysis, risk
items, monitoring indicators), the 1–5 scale, the AI-Proposed/
Practitioner-Calibrated pattern, the cross-phase metadata, and the
version log. Add Phase 4 content within this structure; do not change the
structure.

**Show v1.0 and v2.0 side by side.**
Every principle's current and target scores show the v1.0 baseline value
and the v2.0 value with the delta. The reader must be able to see, at a
glance, what changed and by how much.

**Trace every score change to an architectural decision.**
A score change without a cause is unverifiable. For each changed score,
name the Phase 4 artifact and decision that drove it (e.g., "Security
current 3 → 4 because Step 03 §5 maps every threat to a control and Step
08 module specs apply the controls at every boundary").

**Improvements are documented, not assumed.**
Where the architecture closed a v1.0 gap, document it with the same rigor
as a regression. The scorecard's value is a faithful picture, which
includes the genuine gains Phase 4 produced.

**Make monitoring indicators concrete where Phase 4 enabled it.**
Phase 4 produced module monitoring hooks (Step 08, referencing Phase 3
Step 07 H-NN). Where this makes a v1.0 monitoring indicator concrete
(from "to be defined in architecture" to a specific hook), update it.

**Propose; let the practitioner calibrate.**
AI produces the v2.0 scores; the practitioner calibrates. Every changed
score has an AI-Proposed and a Practitioner-Calibrated value with a
calibration note. Unconfirmed scores go in the calibration gap register.

**Target changes are substantive changes.**
If a target must change (e.g., Phase 4 cost modeling revealed the
Economics target was set on a wrong assumption), that is a substantive
change per the protocol §6.2 — document the trigger, prior value, new
value, rationale, and approval. Do not silently move a target to erase a
gap.

**Produce the audit trail entry.**
The v2.0 audit trail entry per protocol §8.1 names the version, date,
owner (the scorecard owner from Step 06 GOV-NN), approver, change
summary, triggers, prior/new values, the regression flag and resolution,
and any override. The audit trail lives in the scorecard so history
travels with the document.

**Do not produce implementation or change the architecture.**
The scorecard measures; it does not implement and it does not modify the
architecture. If a score reveals an architecture problem, that is a
finding for Step 15/Step 16 — fix the architecture there, then re-score.

---

## Clarification Step

Read all Phase 4 artifacts, the v1.0 baseline scorecard, and the Step 06
update protocol thoroughly. Note the principle weighting, the v1.0 scores
and targets, and the protocol's regression thresholds. Then ask between
**3 and 7 clarifying questions**, never more.

**The first question is a presence check:** "I have the following
required inputs: [list — all Stage 1/Stage 2 outputs, the v1.0 scorecard,
the Step 06 protocol, and any API contracts]. The following appear
missing: [list]. Can you provide the missing inputs, or confirm I should
proceed noting the gap?"

Permitted clarification topics:

1. **Score calibration anchors.** If an architectural decision could
   support multiple current scores, ask what the practitioner sees as the
   anchor for that principle's score.

2. **Regression risk tolerance.** If the AI detects a regression, ask the
   practitioner's risk tolerance and whether remediation is planned
   within Phase 4 or accepted with documentation per the protocol.

3. **Target reconciliation.** If a target appears to need changing based
   on Phase 4 findings, ask before treating it as a substantive change.

4. **Monitoring indicator concretization.** If module hooks (H-NN) could
   make a v1.0 indicator concrete in more than one way, ask.

5. **Ownership and approval.** Confirm the scorecard owner and approval
   authority from the Step 06 governance model for the audit trail entry.

Do not ask the practitioner to score anything — that is the AI's
proposal. Do not ask the practitioner to redefine the update protocol —
that is inherited from Step 06.

Ask questions one at a time. After clarifications, produce v2.0 with
AI-Proposed values. The practitioner calibrates during review.

---

## Kickoff

> Paste all Stage 1 and Stage 2 outputs, the Phase 3 Principle Scorecard
> v1.0, the Phase 3 Step 06 Scorecard Update Protocol, and any Step 10–13
> API contracts above this line, then paste this line to trigger the
> prompt.

```
The Phase 4 architecture artifacts, the Phase 3 Scorecard v1.0, and the
Phase 3 Step 06 Update Protocol are pasted above. Please read them
thoroughly, then ask your clarifying questions one at a time, beginning
with the presence check, before producing Principle Scorecard v2.0 with
AI-Proposed values and regression detection against the v1.0 baseline.
```

---

## Output Format

Produce the artifact using this exact structure, preserving the mandatory
format conventions from the v1.0 baseline. Do not omit sections.

```markdown
# Principle Scorecard — v2.0 (Phase 4 Architecture Update)
# Phase 4 Step 14 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Artifact Date:** [date]
**Produced By:** [AI model and version]
**Practitioner:** [name or role]
**Version:** v2.0 (Phase 4 Architecture Update)
**Owner:** [scorecard owner — Step 06 GOV-NN]
**Approval Authority:** [Phase 4 decision authority — Step 06]
**Status:** [Draft / Reviewed / Approved]

**Based On:**
- Phase 3 Principle Scorecard v1.0 dated [date] (the baseline)
- Phase 3 Step 06 Scorecard Update Protocol dated [date] (the governing protocol)
- All Phase 4 Stage 1 and Stage 2 artifacts dated [date]
- Phase 4 Step 10–13 API contracts dated [date] (if produced)

> **Cross-Phase Living Document Notice:** This is the Phase 4 update of
> the Principle Scorecard, governed by the Phase 3 Step 06 protocol.
> Phase 5 will produce v3.x, Phase 6 v4.0, Phase 7 v5.0, per the same
> protocol. Regression is detected against the v1.0 baseline (and, going
> forward, against this v2.0). The v1.0 baseline is preserved; this
> update does not overwrite it.

---

## 1. Executive Summary

[5–7 sentences covering: the overall direction of the scores from v1.0 to
v2.0, the principles that improved most, any regressions detected and
their category, the largest remaining gaps, the most consequential
architectural decisions driving the changes, and the calibration status.
End with one line stating that Step 16 verifies regression handling and
Phase 5 continues the scorecard per the Step 06 protocol.]

---

## 2. Inputs and Protocol Applied

### 2.1 Update Protocol (from Phase 3 Step 06)

| Protocol Element | Applied Value |
|------------------|---------------|
| Update cadence | Phase 4 at architecture completion → v2.0 |
| Regression threshold (high-weight, ≥ 20) | Current drops ≥ 0.5 from v1.0 |
| Regression threshold (standard-weight, < 20) | Current drops ≥ 1.0 from v1.0 |
| Regression categories | Critical / Material / Minor (per protocol §5.2) |
| Baseline for comparison | v1.0 |
| Format inheritance | Mandatory conventions preserved (protocol §10.1) |

### 2.2 Principle Weighting (carried forward)

| Principle | Weight | Source |
|-----------|--------|--------|
| Security | | Phase 2 Step 01 (via Phase 3 v1.0) |
| Maintainability | | |
| Economics | | |
| Operations | | |
| Scoring & Metrics | | |
| Correctness Verification | | |
| **Total** | **100** | |

---

## 3. Scoring Scale

| Score | Label | Definition |
|-------|-------|------------|
| 5 | Excellent | Strongly supports the principle. Leading evidence. |
| 4 | Strong | Solid support. Above baseline. |
| 3 | Adequate | Meets baseline. No notable strengths or weaknesses. |
| 2 | Weak | Below baseline. Notable gaps requiring active mitigation. |
| 1 | Poor | Fundamentally inadequate. Significant remediation needed. |

---

## 4. Per-Principle Scorecard v2.0

For each principle, the five required elements, updated, showing v1.0 and
v2.0 side by side.

### 4.1 Security

#### Current Score

| Field | Value |
|-------|-------|
| v1.0 Current Score | [from baseline] |
| AI-Proposed v2.0 Current Score | [1–5] |
| Practitioner-Calibrated v2.0 Current Score | [1–5] |
| Delta (v2.0 − v1.0) | [+/− N] |
| Calibration Note | [Accepted / Modified — reason] |
| Score Basis | [Which Phase 4 artifacts support this score — cite Step 03, Step 08 security sections, etc.] |
| Confidence | [H/M/L] |

#### Target Score

| Field | Value |
|-------|-------|
| v1.0 Target Score | [from baseline] |
| v2.0 Target Score | [unchanged / changed — substantive change per protocol §6.2] |
| Target Change Justification | [Required only if changed] |

#### Gap Analysis (updated)

| Field | Value |
|-------|-------|
| Gap (Target − v2.0 Current) | [Numeric] |
| What Phase 4 architecture closed | [Specific] |
| What remains for Phase 5+ | [Specific] |

#### Risk Items (updated)

| Risk ID | Risk Description | Status (new/resolved/open) | When Critical | Mitigation | Owner |
|---------|-----------------|----------------------------|---------------|------------|-------|
| SEC-R-NN | | | | | |

#### Monitoring Indicators (updated)

| Indicator ID | What Is Measured | How (now mapped to H-NN where Phase 4 made concrete) | Frequency | Threshold for Concern |
|-------------|------------------|------------------------------------------------------|-----------|-----------------------|
| SEC-M-NN | | | | |

### 4.2 Maintainability
[Same structure as 4.1]

### 4.3 Economics
[Same structure as 4.1 — note Phase 4 effort-per-module estimates vs. the cost envelope]

### 4.4 Operations
[Same structure as 4.1 — note module monitoring hooks now concrete]

### 4.5 Scoring & Metrics
[Same structure as 4.1]

### 4.6 Correctness Verification
[Same structure as 4.1 — note API contracts and module boundaries enabling verification]

---

## 5. Cross-Principle Dashboard

| Principle | Weight | v1.0 Current | v2.0 Current | Delta | v1.0 Target | v2.0 Target | Gap (to v2.0 target) |
|-----------|--------|--------------|--------------|-------|-------------|-------------|----------------------|
| Security | | | | | | | |
| Maintainability | | | | | | | |
| Economics | | | | | | | |
| Operations | | | | | | | |
| Scoring & Metrics | | | | | | | |
| Correctness Verification | | | | | | | |

### Weighted Scores

| Metric | v1.0 | v2.0 | Delta |
|--------|------|------|-------|
| Weighted current (/ 500) | | | |
| Weighted target (/ 500) | | | |
| Weighted gap | | | |

---

## 6. Regression Detection (per Step 06 protocol)

Applying the protocol's thresholds and categories, comparing v2.0 current
scores to the v1.0 baseline.

| Principle | v1.0 → v2.0 Delta | Weight | Regression? | Category | Escalation Required (protocol §5.2) |
|-----------|-------------------|--------|-------------|----------|-------------------------------------|
| [Principle] | [−N] | | [Yes / No] | [Critical / Material / Minor / —] | |

### Regressions Found
[For each regression: the principle, the delta, the category, the
architectural cause, the remediation plan or documented acceptance per
the protocol. If none, "No regressions detected against the v1.0
baseline."]

| Principle | Category | Architectural Cause | Remediation Plan / Acceptance | Owner | Target Date |
|-----------|----------|---------------------|-------------------------------|-------|-------------|

---

## 7. Improvements Documented

Where the architecture closed a v1.0 gap.

| Principle | v1.0 → v2.0 Delta | Architectural Decision That Drove It |
|-----------|-------------------|--------------------------------------|
| [Principle] | [+N] | [Cite Phase 4 artifact] |

---

## 8. Architectural Decisions Driving Score Changes

Traceability from each score change to its cause.

| Principle | Score Change | Driving Phase 4 Artifact and Decision |
|-----------|--------------|---------------------------------------|
| [Principle] | [v1.0 → v2.0] | [Step NN §N: decision] |

---

## 9. Audit Trail Entry (per Step 06 protocol §8.1)

| Element | Value |
|---------|-------|
| Version | v2.0 |
| Date | [date] |
| Owner | [Step 06 GOV-NN] |
| Approver | [Phase 4 decision authority] |
| Change summary | [What changed from v1.0] |
| Triggers | [Phase 4 architecture completion + specific decisions] |
| Prior values | [v1.0 scores for changed principles] |
| New values | [v2.0 scores] |
| Regression flag | [Yes/No — categories if yes] |
| Regression resolution | [How addressed per protocol] |
| Override applied | [Yes/No — per protocol §9 if a regression override was used] |

---

## 10. Calibration Gap Register

Score elements where practitioner calibration is not yet complete. These
must be resolved before Step 16.

| Calibration Gap ID | Principle | Element | Reason for Uncertainty | Priority |
|--------------------|-----------|---------|------------------------|----------|
| CG-NN | | [Current / Target / Risk / Indicator] | | [H/M/L] |

---

## 11. Cross-Artifact Consistency Check

| Check | Status | Notes |
|-------|--------|-------|
| Mandatory format conventions preserved (protocol §10.1) | [Yes / No] | |
| All six principles updated with all five elements | | |
| v1.0 and v2.0 shown side by side with deltas | | |
| Regression detection applied per the protocol thresholds | | |
| Every score change traces to a Phase 4 architectural decision | | |
| Targets unchanged, or changes documented as substantive | | |
| Monitoring indicators concretized where Phase 4 enabled it (H-NN) | | |
| Audit trail entry complete (protocol §8.1) | | |
| v1.0 baseline preserved (not overwritten) | | |
| No architecture changes, no implementation content | | |

---

## 12. Confidence Summary

| Principle | Score Confidence | Basis |
|-----------|------------------|-------|
| Security | [H/M/L] | |
| Maintainability | [H/M/L] | |
| Economics | [H/M/L] | |
| Operations | [H/M/L] | |
| Scoring & Metrics | [H/M/L] | |
| Correctness Verification | [H/M/L] | |

**Overall v2.0 confidence:** [H/M/L]
**Lowest-confidence area:** [name and explain]

---

## 13. Version Log (cross-phase)

| Version | Phase | Date | Trigger | Owner | Approver |
|---------|-------|------|---------|-------|----------|
| v1.0 | Phase 3 | [date] | Baseline | | |
| v2.0 | Phase 4 | [date] | Architecture completion update | [GOV-NN] | [authority] |

[Phase 5 will add v3.x, Phase 6 v4.0, Phase 7 v5.0 per the Step 06
protocol. Prior versions are preserved.]

---

## 14. Handoff Status

- [ ] All six principles updated with all five elements
- [ ] v1.0 and v2.0 shown side by side with deltas
- [ ] Regression detection applied per the Step 06 thresholds and categories
- [ ] Any regressions categorized with remediation or documented acceptance
- [ ] Improvements documented with their architectural cause
- [ ] Every score change traces to a Phase 4 decision
- [ ] Target changes (if any) documented as substantive changes
- [ ] Monitoring indicators concretized where Phase 4 enabled it
- [ ] Audit trail entry complete
- [ ] Mandatory format conventions preserved; v1.0 preserved
- [ ] Calibration gaps registered

**Status:** [Ready for Step 15 and Step 16 / Calibration gaps require resolution first / Blocked]
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] All six principles are updated with all five required elements
      (current, target, gap analysis, risk items, monitoring indicators)
- [ ] Every current and target score shows the v1.0 value, the v2.0 value,
      and the delta
- [ ] Every changed score has an AI-Proposed and a Practitioner-Calibrated
      value with a calibration note (or is in the calibration gap register)
- [ ] Current scores reflect the architecture as it stands (artifacts),
      not implementation intentions
- [ ] Regression detection (§6) applies the Step 06 thresholds (≥ 0.5
      high-weight, ≥ 1.0 standard-weight) and categories mechanically
- [ ] Every regression is categorized (Critical / Material / Minor) with
      the protocol's escalation and a remediation plan or documented
      acceptance — no regression hidden by adjusting the baseline or target
- [ ] Improvements are documented (§7) with the same rigor as regressions
- [ ] Every score change traces to a specific Phase 4 architectural
      decision (§8)
- [ ] Target changes, if any, are handled as substantive changes per the
      protocol §6.2 (trigger, prior/new value, rationale, approval)
- [ ] Monitoring indicators are concretized where Phase 4 enabled it
      (mapped to module hooks H-NN)
- [ ] The audit trail entry (§9) is complete per protocol §8.1
- [ ] The mandatory format conventions (protocol §10.1) are preserved and
      the v1.0 baseline is not overwritten
- [ ] No architecture changes and no implementation content are produced
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 14 of 16 in the Phase 4 Architecture & Modular Design Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `architecture-modular-design.instructions.md`*
*Previous steps (Stage 3 API contracts): `step-10-api-contracts-rest.prompt.md`–`step-13-api-contracts-other.prompt.md`*
*Parallel-eligible with: Steps 10–13*
*Next step: `step-15-architecture-review.prompt.md`*
