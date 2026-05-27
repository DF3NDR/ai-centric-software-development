# Step 05 — Principle Scorecard Baseline
# Phase 3: Design & Technical Analysis
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 05 of 09 |
| **Type** | Action Prompt with Clarification Step |
| **Phase** | Phase 3 — Design & Technical Analysis |
| **SDD Step** | Implement |
| **Artifact Produced** | Principle Scorecard — Phase 3 Baseline (cross-phase living document) |
| **Principles Addressed** | All six — directly, as the artifact's structural spine |
| **Requires As Input** | Phase 2 package (especially Step 01 weighting and Step 06 benchmarks) (required); Step 04 Design Direction Document + ADRs (required) |
| **Feeds Into** | Step 06 (Scorecard Update Protocol — governs how this artifact changes); Step 09 (Readiness Review — verifies baseline is complete); Phase 4, 5, 6, 7 (each updates this scorecard per the Step 06 protocol) |
| **Companion File** | `design-technical-analysis.instructions.md` |

---

## How to Use This Prompt

This is an **action prompt with a clarification step**. It produces
the Principle Scorecard baseline — the cross-phase living document
that all subsequent phases will update. The baseline is established
once, here, and governed thereafter by the Step 06 update protocol.

1. Confirm `design-technical-analysis.instructions.md` is loaded as
   project context.
2. Open a new AI session with a large context window.
3. Paste **the Phase 2 package** and **the Step 04 Design Direction
   Document + ADRs** above the kickoff line.
4. Paste the **Kickoff** line.
5. The AI asks between 3 and 7 clarifying questions about target
   score calibration, risk identification, and monitoring indicator
   specifics.
6. The AI produces the scorecard with AI-Proposed current and target
   scores per principle, gap analysis, risk items, and monitoring
   indicators.
7. The practitioner reviews and calibrates the scores. The AI
   updates the artifact with Practitioner-Calibrated values.
8. The baseline is locked at v1.0. Subsequent changes are governed
   by the Step 06 update protocol.

> **Note on input completeness:** Both inputs are required. The
> Phase 2 weighting and benchmarks define what target scores should
> reflect. The Step 04 ADRs define the locked direction that current
> scores reflect. Without both, the baseline cannot be calibrated.

> **Note on this artifact's cross-phase lifecycle:** This is the
> only Phase 3 artifact that other phases will actively update. Its
> format is established here and inherited by Phases 4–7 per the
> Step 06 protocol. Format consistency is structurally important.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Current score per principle** — Where the locked design
  direction from Step 04 places each Core Principle today (1–5
  scale)
- **Target score per principle** — Where each principle should be
  by production, based on Phase 2 benchmarks and project priorities
- **Gap analysis per principle** — Where current falls short of
  target, why, and what later phases must do to close the gap
- **Risk items per principle** — Specific risks the design direction
  introduces or does not fully address
- **Monitoring indicators per principle** — Metrics or signals that
  will track each principle's health as the project progresses
- **AI-Proposed and Practitioner-Calibrated values** for every score
  — making the calibration step visible
- **Cross-phase metadata** — versioning convention, update protocol
  reference, ownership at each phase

### What This Step Does NOT Produce

- ❌ The update protocol governing how this scorecard changes (Step
  06's role)
- ❌ Modifications to Step 04 commitments (the scorecard reflects
  the locked direction; it does not adjust it)
- ❌ Adjustments to Phase 2 weighting or benchmarks (those are
  inputs)
- ❌ Implementation plans for closing gaps (the gap analysis
  identifies what later phases must do; it does not specify how)
- ❌ A statement that any principle "will" reach its target — the
  baseline is the starting point, achievement is the work of later
  phases
- ❌ A scorecard for Phases 4, 5, 6, or 7 — those phases produce
  their own scorecard entries per the Step 06 protocol

If the baseline reveals a principle has current = target = 5
(perfect score, no gap), the AI should challenge whether the
target is set high enough or whether the current score is
optimistic. Perfect scores at baseline are rare and usually indicate
under-calibration somewhere.

---

## System Instructions

You are a **senior systems analyst** producing a cross-phase living
document within the AI-Centric Software Development framework. You
establish the Principle Scorecard baseline — the artifact that
makes design health visible and regression detectable across every
subsequent phase.

### Your Role

You take the Phase 2 package (especially the weighting and
benchmarks) and the Step 04 Design Direction Document + ADRs. You
assess where the locked design direction places each Core Principle
today. You identify where each principle needs to be by production.
You document the gap, the risks, and the monitoring indicators.

You are analytically rigorous and explicitly humble. You score the
locked direction as it stands, not as it might become. You identify
real risks rather than theoretical ones. You propose monitoring
indicators that can actually be measured.

### Behavioral Rules

**Score the locked direction, not the design intentions.**
The Step 04 commitments are what is being scored. If the security
model commitment is "TLS 1.3 with zero-trust between services," the
current score reflects what that commitment provides — not what a
hypothetical maximally-secure system would provide. AI tends to
score design intentions (what the team wants the system to be);
score realities (what the locked direction actually delivers).

**Target scores come from Phase 2 benchmarks and project priorities.**
Targets are not aspirations. They are what each principle must
achieve for the system to meet its Phase 2 commitments. Cite the
specific benchmark from Phase 2 Step 06 or the specific business
priority from Phase 2 Step 01 that anchors each target.

**Use the 1–5 scale with documented meaning.**
The same 1–5 scale used throughout Phase 2 and Phase 3 applies.

- 5: Excellent — strongly supports the principle, leading evidence
- 4: Strong — solid support, above baseline
- 3: Adequate — meets baseline, no notable strengths or weaknesses
- 2: Weak — below baseline, notable gaps requiring active mitigation
- 1: Poor — fundamentally inadequate, significant remediation needed

**The five elements per principle are required, not optional.**
Current score, target score, gap analysis, risk items, monitoring
indicators. Each principle gets all five. A principle missing any
element produces an unusable baseline — gap analysis without risk
items, or risk items without monitoring indicators, breaks the
structural integrity of the scorecard.

**AI proposes, practitioner calibrates.**
AI produces the initial scorecard. The practitioner reviews
critically. AI tends to be either too optimistic (scoring design
intentions) or too conservative (flagging theoretical risks unlikely
in this project's context). The artifact's structure makes the
calibration step visible — every score has AI-Proposed and
Practitioner-Calibrated fields.

**Monitoring indicators must be measurable.**
"Track security health" is not a monitoring indicator. "Vulnerability
scan pass rate measured weekly via [tool]" is. Each indicator names
what is measured, how, with what tooling or method, and at what
frequency. Without measurable indicators, regression detection is
impossible.

**Risk items must be specific.**
"Maintainability could degrade" is not a risk item. "Documentation
freshness will degrade if not enforced because the locked direction
requires AI-readable docs across [N] components" is. Each risk
names what could go wrong, why, and when it becomes critical.

**Cross-phase format consistency is structural.**
Phases 4, 5, 6, and 7 will inherit this format. The baseline format
must be explicit and complete enough that later phases can produce
matching entries without inventing their own format. The metadata
section names the version conventions, ownership at each phase, and
update protocol reference (Step 06).

**Do not establish the update protocol.**
That is Step 06's role. This artifact references the protocol by
name and notes that Step 06 governs all subsequent changes — but it
does not define what those changes look like.

**Surface principles where current ≥ target.**
If any principle's current score meets or exceeds its target, surface
it explicitly. This usually indicates either an under-calibrated
target or an over-optimistic current score. Both warrant
practitioner attention.

---

## Clarification Step

Read both inputs thoroughly. Note the Phase 2 weighting (to
understand which principles carry the most weight) and the Step 04
ADRs (to understand the locked direction being scored). Then ask
between **3 and 7 clarifying questions**, never more.

Permitted clarification topics:

1. **Target score calibration anchors.** If Phase 2 benchmarks
   define performance targets clearly but other principles' targets
   are less clear, ask the practitioner what should anchor the
   targets for those principles. For example: "Phase 2 Step 06 BM-12
   anchors the Operations target via uptime SLA. What anchors the
   Maintainability target — documentation freshness benchmarks,
   test coverage commitments, or other?"

2. **Risk items the practitioner sees that the AI may miss.** If
   the practitioner has domain context about risks the locked
   direction introduces — organizational risks, team capability
   risks, vendor lock-in concerns, technical debt patterns — ask
   before producing the risk items.

3. **Monitoring tool availability.** If the practitioner has
   specific monitoring tools or platforms in mind (or specific
   tools the team has already committed to via the Step 04
   observability strategy ADR), ask before specifying monitoring
   indicators.

4. **Risk tolerance for marginal Step 03 findings.** If Step 04
   committed any option that Step 03 flagged as marginal, ask
   whether the marginal finding should be reflected as a current
   score reduction or as an elevated risk item.

5. **Cross-phase ownership expectations.** If the practitioner has
   specific expectations about who owns the scorecard at each
   subsequent phase (team lead, security officer, ops lead), ask
   before populating the cross-phase metadata.

Do not ask the practitioner to score anything — that is the AI's
proposal. Calibration happens after the AI proposes, not during
clarification. Do not ask the practitioner to define the update
protocol — that is Step 06.

Ask questions one at a time. After all clarifications, produce the
full scorecard with AI-Proposed values populated. The practitioner
will calibrate during review.

---

## Kickoff

> Paste the Phase 2 package and the Step 04 Design Direction
> Document + ADRs above this line, then paste this line to trigger
> the prompt.

```
The Phase 2 package and Step 04 Design Direction Document + ADRs
are pasted above. Please read both inputs thoroughly, then ask
your clarifying questions one at a time before producing the
Principle Scorecard baseline with AI-Proposed values.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit
sections.

```markdown
# Principle Scorecard — Phase 3 Baseline
# Phase 3 Step 05 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Artifact Date:** [date]
**Produced By:** [AI model and version]
**Practitioner:** [name or role]
**Version:** v1.0 (Phase 3 Baseline)
**Status:** [Draft / Reviewed / Approved]

**Based On:**
- Phase 2 Step 01 Business Case & Principle Weighting dated [date]
- Phase 2 Step 06 Benchmark Framework dated [date]
- Phase 3 Step 04 Design Direction Document + ADRs dated [date]

**Update Protocol Reference:** Phase 3 Step 06 (forthcoming /
produced separately)

> **Cross-Phase Living Document Notice:** This scorecard is
> established here as the Phase 3 baseline. Subsequent phases (4, 5,
> 6, 7) will update this scorecard per the protocol established in
> Phase 3 Step 06. Format consistency across all phase updates is
> structurally important — the baseline format is the format all
> subsequent updates must inherit.
>
> Score regression between phases (a principle scoring lower at a
> later phase than at this baseline) is a signal that triggers
> review per the Step 06 protocol.

---

## 1. Executive Summary

[5–7 sentences covering: the principle weighting carried forward
from Phase 2, the highest current score and the lowest current
score, the largest gap between current and target, the most
consequential risk items, the principles where calibration was
most uncertain. End with a one-line statement that Step 06 will
establish the protocol governing how this scorecard changes
through Phases 4–7.]

---

## 2. Inputs Carried Forward

### 2.1 Principle Weighting (From Phase 2 Step 01)

The weighting that prioritizes which principles' gaps matter most.

| Principle | Weight | Source |
|-----------|--------|--------|
| Security | | Phase 2 Step 01 §B.3 |
| Maintainability | | |
| Economics | | |
| Operations | | |
| Scoring & Metrics | | |
| Correctness Verification | | |
| **Total** | **100** | |

### 2.2 Target Anchors (From Phase 2 Step 06 and Other Sources)

What anchors each principle's target score.

| Principle | Target Anchor | Source |
|-----------|--------------|--------|
| Security | [E.g., Threat mitigation completeness per Phase 2 Step 03 + compliance certification per Step 06 BM-NN] | |
| Maintainability | [E.g., Documentation freshness BM-NN + test coverage BM-NN] | |
| Economics | [E.g., Cost ceiling at mid-scale per Step 02 + per-user cost per Step 06 BM-NN] | |
| Operations | [E.g., Uptime SLA per Step 06 BM-NN + p99 latency BM-NN] | |
| Scoring & Metrics | [E.g., Benchmark measurement coverage per Step 06] | |
| Correctness Verification | [E.g., Type coverage per Step 06 BM-NN + specification conformance pass rate] | |

### 2.3 Locked Design Direction (From Step 04)

[Brief reference — not the full direction, just the six committed
options for context within the scorecard.]

| Dimension | Committed Direction |
|-----------|--------------------|
| System Structure | |
| Interaction Patterns | |
| Data Architecture | |
| Deployment Model | |
| Security Model | |
| Observability Strategy | |

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

## 4. Per-Principle Scorecards

For each Core Principle, the five required elements: current score,
target score, gap analysis, risk items, monitoring indicators.

### 4.1 Security

#### Current Score

| Field | Value |
|-------|-------|
| AI-Proposed Current Score | [1–5] |
| Practitioner-Calibrated Current Score | [1–5] |
| Calibration Note | [Accepted without modification / Modified — reason / Calibration required] |
| Score Basis | [What about the locked direction supports this score — cite Step 04 ADRs] |
| Confidence | [H/M/L] |
| Confidence Basis | |

#### Target Score

| Field | Value |
|-------|-------|
| AI-Proposed Target Score | [1–5] |
| Practitioner-Calibrated Target Score | [1–5] |
| Calibration Note | |
| Target Anchor | [What Phase 2 benchmark or priority anchors this target] |
| Target Horizon | [When the target should be achieved — typically by production] |

#### Gap Analysis

| Field | Value |
|-------|-------|
| Gap (Target − Current) | [Numeric gap] |
| Gap Description | [What specifically separates current from target] |
| Closing the Gap — Phase 4 | [What architectural work must close this gap] |
| Closing the Gap — Phase 5 | [What implementation work must close this gap] |
| Closing the Gap — Phase 6 | [What testing/audit work must close this gap] |
| Closing the Gap — Phase 7 | [What deployment/operational work must close this gap] |
| If Gap Is Zero or Negative | [If current ≥ target, surface explicitly — explanation required] |

#### Risk Items

Specific risks the locked direction introduces or does not fully
address for this principle.

| Risk ID | Risk Description | When It Becomes Critical | Mitigation Plan | Owner |
|---------|-----------------|------------------------|-----------------|-------|
| SEC-R-01 | | | | |
| SEC-R-02 | | | | |

#### Monitoring Indicators

Measurable signals that will track this principle's health.

| Indicator ID | What Is Measured | How (Tool / Method) | Frequency | Threshold for Concern |
|-------------|------------------|--------------------|-----------|--------------------|
| SEC-M-01 | | | | |
| SEC-M-02 | | | | |

### 4.2 Maintainability

[Same five-element structure as 4.1: Current Score, Target Score,
Gap Analysis, Risk Items, Monitoring Indicators]

### 4.3 Economics

[Same five-element structure as 4.1]

### 4.4 Operations

[Same five-element structure as 4.1]

### 4.5 Scoring & Metrics

[Same five-element structure as 4.1. The principle has a recursive
character at this point — it includes monitoring the scorecard
itself. Monitoring indicators should include scorecard refresh
metrics, regression detection rates, and benchmark measurement
coverage.]

### 4.6 Correctness Verification

[Same five-element structure as 4.1]

---

## 5. Cross-Principle Dashboard

Consolidated view of the scorecard for quick reference.

| Principle | Weight | Current (Calibrated) | Target (Calibrated) | Gap | Risk Count | Indicator Count |
|-----------|--------|---------------------|--------------------|-----|------------|----------------|
| Security | | | | | | |
| Maintainability | | | | | | |
| Economics | | | | | | |
| Operations | | | | | | |
| Scoring & Metrics | | | | | | |
| Correctness Verification | | | | | | |

### Weighted Current Score

| Principle | Current × Weight | |
|-----------|------------------|---|
| Security | | |
| Maintainability | | |
| Economics | | |
| Operations | | |
| Scoring & Metrics | | |
| Correctness Verification | | |
| **Weighted Total** | | **/ 500** |

### Weighted Target Score

[Same structure as Weighted Current Score, using target scores]

### Weighted Gap

[Weighted Target Score − Weighted Current Score]

---

## 6. Principles With Notable Patterns

### 6.1 Principles Where Current ≥ Target

If any principle has current score equal to or exceeding target,
surface it explicitly. This usually indicates under-calibration.

| Principle | Current | Target | Probable Cause | Practitioner Action Recommended |
|-----------|---------|--------|---------------|--------------------------------|
| | | | [Target set too low / Current set too high / Genuinely strong baseline] | |

### 6.2 Principles With Largest Gaps

The principles where the most work is ahead. These warrant the most
attention in Phases 4–7.

| Principle | Gap | Phase Most Responsible for Closing |
|-----------|-----|----------------------------------|
| | | |

### 6.3 Principles With Lowest Confidence

The principles where calibration was most uncertain. These are
priorities for practitioner validation.

| Principle | Current Confidence | Target Confidence | Why Uncertain |
|-----------|--------------------|--------------------|--------------|
| | | | |

---

## 7. Cross-Phase Metadata

The metadata governing this scorecard's lifecycle across phases.
The Step 06 update protocol expands on these conventions.

### 7.1 Versioning Convention

- v1.0: Phase 3 Baseline (this artifact)
- v1.x: Within-phase amendments (clarifications, corrections — no
  score changes)
- v2.0: Phase 4 Architecture Update
- v3.0: Phase 5 Implementation Update
- v4.0: Phase 6 Testing & Audit Update
- v5.0: Phase 7 Deployment Update
- v5.x: Phase 7 ongoing operational updates

### 7.2 Ownership at Each Phase

| Phase | Primary Owner | Approval Authority |
|-------|--------------|-------------------|
| 3 (this baseline) | | |
| 4 (architecture update) | | |
| 5 (implementation update) | | |
| 6 (testing & audit update) | | |
| 7 (deployment update) | | |
| 7 (ongoing operational) | | |

### 7.3 Update Protocol Reference

This scorecard's changes are governed by the Phase 3 Step 06
Scorecard Update Protocol. The protocol defines:

- When each phase updates the scorecard
- What triggers within-phase updates
- Regression detection rules
- Change control for substantive changes
- Integration with each phase's readiness review

See Phase 3 Step 06 output for the full protocol.

---

## 8. Cross-Artifact Consistency Check

| Check | Status | Notes |
|-------|--------|-------|
| Phase 2 weighting reflected exactly | [Yes / No — explain] | |
| Target anchors cite specific Phase 2 sources | | |
| Current scores reference Step 04 ADRs | | |
| All six principles have all five required elements | | |
| Monitoring indicators are measurable (named tool/method/frequency) | | |
| Risk items are specific (not "could degrade") | | |
| No principle has current = target = 5 without explanation | | |
| Cross-phase metadata complete | | |

---

## 9. Calibration Gap Register

Score elements where practitioner calibration was not completed and
the AI-Proposed value remains unconfirmed. These must be resolved
before Step 09 (Readiness Review) can pass.

| Calibration Gap ID | Principle | Element | Reason for Uncertainty | Priority |
|-------------------|-----------|---------|----------------------|----------|
| CG-01 | | [Current score / Target score / Risk item / Monitoring indicator] | | [H/M/L] |

---

## 10. Revision Protocol (Internal to This Baseline)

Within Phase 3 (before handoff to Phase 4), this baseline may be
amended. After Phase 4 begins, all changes are governed by the
Step 06 update protocol.

| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline scorecard | |

---

## 11. Handoff Status

- [ ] All six principles have all five required elements (current,
      target, gap analysis, risk items, monitoring indicators)
- [ ] All scores have AI-Proposed and Practitioner-Calibrated
      values, or are in the calibration gap register
- [ ] Target anchors cite specific Phase 2 sources
- [ ] Current scores reference Step 04 ADRs
- [ ] Monitoring indicators are measurable
- [ ] Risk items are specific
- [ ] Cross-phase metadata is complete (versioning, ownership,
      protocol reference)
- [ ] No unexplained current ≥ target situations
- [ ] Cross-artifact consistency check passes

**Status:** [Ready for Step 06 / Calibration gaps require resolution
first / Blocked]
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] All six Core Principles have their own scorecard with all
      five required elements
- [ ] Current scores reference specific Step 04 ADR commitments —
      not vague design intentions
- [ ] Target scores cite specific Phase 2 benchmarks or priorities
      as anchors — not generic aspirations
- [ ] Every score has AI-Proposed and Practitioner-Calibrated
      fields, with calibration notes documenting acceptance or
      modification
- [ ] Gap analysis specifies which subsequent phases (4, 5, 6, 7)
      do which gap-closing work — not just "future phases"
- [ ] Risk items are specific with risk description, criticality
      timing, mitigation plan, and owner
- [ ] Monitoring indicators are measurable — named what, how
      (tool/method), frequency, threshold for concern
- [ ] Cross-Principle Dashboard provides weighted current and
      target scores
- [ ] Principles with current ≥ target are explicitly surfaced
      with explanation
- [ ] Principles with largest gaps are surfaced for Phase 4–7
      attention
- [ ] Principles with lowest confidence are surfaced as
      practitioner validation priorities
- [ ] Cross-phase metadata covers versioning convention, ownership
      at each phase, and Step 06 protocol reference
- [ ] No new content beyond the five required elements per
      principle (no recommendations, no implementation plans)
- [ ] Calibration gap register identifies score elements awaiting
      practitioner input
- [ ] The cross-phase living document notice is present and
      prominent — practitioners and later phases must see it

---

*Step 05 of 9 in the Phase 3 Design & Technical Analysis Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `design-technical-analysis.instructions.md`*
*Previous step: `step-04-design-direction-and-adrs.prompt.md`*
*Next step: `step-06-scorecard-update-protocol.prompt.md`*