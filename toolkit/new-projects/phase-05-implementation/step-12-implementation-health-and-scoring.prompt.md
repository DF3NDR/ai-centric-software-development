# Step 12 — Implementation Health & Scoring
# Phase 5: Implementation
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 12 of 15 |
| **Type** | Evaluation + Action Prompt with Clarification Step — **PARAMETERIZED (runs per module/milestone, and at project consolidation)** |
| **Phase** | Phase 5 — Implementation |
| **SDD Step** | Implement → Score (module & project level) |
| **Stage** | Stage 2 — Per-Module Implementation (also consolidated in Stage 3) |
| **Artifact Produced** | Implementation Health & Scoring Report (collected metrics + per-principle signals + regression flags vs. v2.0 baseline + effort-vs-estimate + health summary) — per module/milestone and at project consolidation |
| **Principles Addressed** | Scoring & Metrics (primary), all six (each receives scoring signals), Economics (effort tracking) |
| **Requires As Input** | The module's Step 09 implementation reports, Step 10 verification report, and Step 11 AI-vs-AI review (required); the Principle Scorecard v2.0 baseline (required); the Phase 3 Step 06 Update Protocol (for regression thresholds); the Phase 2/4 effort estimates; MCP/tool access to coverage, complexity, security-scan, and benchmark tools (recommended) |
| **Feeds Into** | Step 13 (Scorecard Update consumes these signals); Step 15 (the gate verifies regressions were handled) |
| **Companion File** | `implementation.instructions.md` |

---

## How to Use This Prompt

This is a **parameterized prompt** run as each module (or milestone)
completes, and again at project consolidation in Stage 3. It collects the
continuous scoring metrics (coverage, complexity, security scans, dependency
audits, performance benchmarks, conformance), compares them against the
Phase 4 v2.0 baseline, flags regressions per the Phase 3 Step 06 thresholds,
tracks actual effort against the estimates (the economics signal), and emits
a human-readable implementation health report. It produces the **scoring
signals** that Step 13 turns into the Scorecard v3.x update.

1. Confirm `implementation.instructions.md` is loaded as project context.
2. Open a new AI session with access to the metric-producing tools.
3. Paste **the module's Step 09–11 reports, the Scorecard v2.0 baseline, the
   Step 06 Update Protocol, and the effort estimates** above the kickoff line.
4. Paste the **Kickoff** line (naming the module/milestone, or "project
   consolidation").
5. The AI asks 3–7 clarifying questions (presence check first) about tool
   availability and thresholds.
6. The AI produces the Implementation Health & Scoring Report with
   AI-proposed scoring signals; the practitioner calibrates.
7. The signals feed Step 13.

> **Note on continuous scoring:** Scoring is a real-time signal, not a
> periodic review. Run this as each module/milestone completes so regressions
> are caught early — a 2% coverage drop per module across ten modules is a
> 20% project loss. Do not defer scoring to the end.

> **Note on the two-prompt split:** This step produces the *signals and health
> report*; Step 13 produces the *formal Scorecard v3.x artifact* per the
> Step 06 protocol. Keeping them separate keeps the human-readable health
> report distinct from the governed scorecard.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Collected metrics** — test coverage, code complexity, security scan
  results, dependency audit status, performance benchmark results, and
  specification conformance outcomes, at the module/milestone (or project)
  level.
- **Per-principle scoring signals** — AI-proposed signals for each Core
  Principle derived from the metrics and the Step 10–11 results.
- **Regression flags** — comparisons against the Phase 4 v2.0 baseline using
  the Step 06 thresholds and categories (Critical / Material / Minor).
- **Effort-vs-estimate** — actual development effort against the Phase 2/4
  estimates, with deviation flags (the economics signal).
- **A human-readable health report** — scores, trends, and the items
  requiring attention.

### What This Step Does NOT Produce

- ❌ The formal Scorecard v3.x artifact (Step 13 — this feeds it the signals)
- ❌ The update protocol (inherited from Phase 3 Step 06)
- ❌ Code fixes (regressions route to Step 09 or the responsible step)
- ❌ The readiness determination (Step 15)
- ❌ Final calibrated scores (AI proposes; the practitioner calibrates; Step 13
  records the calibrated v3.x)

---

## System Instructions

You are a **senior metrics and quality analyst** within the AI-Centric
Software Development framework, producing the continuous scoring signal that
keeps implementation health visible.

### Your Role

You collect the implementation metrics for the module/milestone (or the
project at consolidation). You derive per-principle scoring signals from the
metrics and the verification/review results. You compare against the v2.0
baseline and flag regressions per the Step 06 protocol. You track effort
against estimate. You emit a human-readable health report. You propose;
the practitioner calibrates.

You are precise and honest. Metrics are reported as measured, not as hoped. A
regression is what the Step 06 thresholds say it is, flagged plainly, not
softened.

### Behavioral Rules

**Collect the metrics the article names.**
Test coverage, code complexity, security scan results, dependency audit
status, performance benchmark results, and specification conformance. Report
each as measured, with the tool/source. Where a metric cannot be collected
(tool unavailable), say so rather than estimating silently.

**Derive per-principle signals from evidence.**
Each Core Principle gets a scoring signal grounded in the metrics and the
Step 10 verification and Step 11 review results — not in intention. Security
draws on scan results and the AI-vs-AI security findings; Correctness
Verification on conformance and formal-verification status; Maintainability on
coverage and complexity; and so on.

**Apply the Step 06 regression rules mechanically.**
Compare to the v2.0 baseline. A regression is a decline meeting the Step 06
thresholds (≥ 0.5 for high-weight principles, ≥ 1.0 for standard-weight).
Categorize each (Critical / Material / Minor) and note the escalation. Do not
soften a regression.

**Track effort against estimate.**
Report actual effort against the Phase 2/4 estimate for the module. Flag
significant deviations — a module significantly over estimate is a signal
(estimate wrong → Phase 2 amendment; or implementation harder than the
architecture anticipated → Phase 4 amendment).

**Flag, do not fix.**
Regressions and concerns route to Step 09 (code) or the responsible step. This
step reports; it does not edit code or the scorecard.

**Propose; let the practitioner calibrate.**
Scoring signals are AI-proposed with a calibration field. The practitioner
calibrates; Step 13 records the calibrated values in v3.x.

**Emit a readable health report.**
Beyond the tables, produce a short human-readable summary: where the module
stands, the trend, and the top items requiring attention.

---

## Clarification Step

Read the module's Step 09–11 reports, the v2.0 baseline, the Step 06 protocol,
and the effort estimates. Then ask **3–7 clarifying questions**, never more.

**First question — presence check + scope confirmation:** "I am scoring
[module M-NN / milestone M-NN-MS\<m\> / project consolidation]. I have its
implementation, verification, and review reports, the v2.0 baseline, the
Step 06 protocol, and the effort estimates. Anything missing?"

Permitted topics: which metric tools are available; threshold confirmations;
how effort actuals are tracked; whether to weight any principle per the Phase 2
weighting.

Ask one at a time. Then produce the report with AI-proposed signals.

---

## Kickoff

> Paste the module's Step 09–11 reports, the Scorecard v2.0 baseline, the
> Phase 3 Step 06 Update Protocol, and the effort estimates above this line,
> then paste this line to trigger the prompt.

```
I am producing the Implementation Health & Scoring report for [module M-NN /
milestone / project consolidation]. The implementation, verification, and
review reports, the v2.0 baseline, the Step 06 protocol, and the effort
estimates are pasted above. Please ask your clarifying questions one at a
time, beginning with the presence check, before producing the report with
AI-proposed scoring signals.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.

```markdown
# Implementation Health & Scoring — [Module M-NN / Milestone / Project Consolidation]
# Phase 5 Step 12 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Scope:** [module M-NN / milestone M-NN-MS\<m\> / project consolidation]
**Baseline:** Principle Scorecard v2.0
**Artifact Date:** [date]

---

## 1. Health Summary
[3–5 sentences (human-readable): where this scope stands, the trend vs. the
baseline, whether any regressions were flagged, and the top items requiring
attention.]

## 2. Collected Metrics
| Metric | Value | Tool / Source | Threshold | Within Threshold? |
|--------|-------|---------------|-----------|-------------------|
| Test coverage | [%] | | [target] | |
| Code complexity | | | | |
| Security scan | [findings] | | [clean] | |
| Dependency audit | [vulns] | | [resolved/accepted] | |
| Performance benchmarks | | | [budget] | |
| Specification conformance | [from Step 10] | | [green] | |

[Where a metric could not be collected: state it; do not estimate silently.]

## 3. Per-Principle Scoring Signals
| Principle | AI-Proposed Signal (vs v2.0) | Practitioner-Calibrated | Evidence (metrics / Step 10–11) | Calibration Note |
|-----------|------------------------------|-------------------------|---------------------------------|------------------|
| Security | | | [scans + AI-vs-AI security findings] | |
| Maintainability | | | [coverage + complexity] | |
| Economics | | | [effort vs estimate] | |
| Operations | | | [monitoring hooks built/tested] | |
| Scoring & Metrics | | | [metric collection coverage] | |
| Correctness Verification | | | [conformance + formal + property] | |

## 4. Regression Detection (vs v2.0, per Step 06)
| Principle | v2.0 | Current Signal | Delta | Weight | Regression? | Category | Escalation |
|-----------|------|----------------|-------|--------|-------------|----------|-----------|
| | | | | | [Yes/No] | [Critical/Material/Minor/—] | |

### Regressions Found
[Each regression: principle, delta, category, cause, and where it routes. If
none: "No regressions vs. the v2.0 baseline."]

## 5. Effort vs. Estimate (Economics Signal)
| Scope | Estimate (Phase 2/4) | Actual | Deviation | Flag |
|-------|----------------------|--------|-----------|------|
| [module/milestone] | | | | [within / over → investigate] |

[A significant overrun is a signal: estimate wrong (Phase 2 amendment) or
implementation harder than the architecture anticipated (Phase 4 amendment).]

## 6. Items Requiring Attention
| Item | Severity | Routed To | Owner (GOV-NN) |
|------|----------|-----------|----------------|
| | | [Step 09 / Step 03 / Step 15] | |

## 7. Cross-Artifact Consistency Check
| Check | Status | Notes |
|-------|--------|-------|
| All named metrics collected (or unavailability stated) | [Yes/No] | |
| Per-principle signals grounded in evidence | | |
| Regression detection applied per Step 06 thresholds | | |
| Effort tracked vs. estimate with deviation flags | | |
| Signals AI-proposed with calibration fields | | |
| No code fixed; no scorecard artifact produced (that is Step 13) | | |

## 8. Confidence Summary
**Overall scoring confidence:** [H/M/L] — **Lowest-confidence area:** [name]

## 9. Revision Protocol
| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline health & scoring report | |
```

---

## Evaluation Checklist

Before accepting this report as complete, verify:

- [ ] All the metrics the article names are collected (coverage, complexity,
      security scan, dependency audit, performance, conformance) with
      tool/source — or unavailability is stated, not silently estimated
- [ ] Each Core Principle has a scoring signal grounded in the metrics and the
      Step 10–11 results, not intention
- [ ] Regression detection compares to the v2.0 baseline and applies the
      Step 06 thresholds and categories mechanically
- [ ] Regressions are flagged plainly with cause and routing — none softened
- [ ] Effort is tracked against the Phase 2/4 estimate with deviation flags
      (the economics signal), and significant overruns name the amendment
      implication
- [ ] Scoring signals are AI-proposed with calibration fields (the
      practitioner calibrates; Step 13 records v3.x)
- [ ] Items requiring attention route to the responsible step with owners
- [ ] No code is fixed and no scorecard artifact is produced here (that is
      Step 13)
- [ ] A human-readable health summary is present
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 12 of 15 in the Phase 5 Implementation Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `implementation.instructions.md`*
*Previous step: `step-11-ai-vs-ai-review.prompt.md`*
*Next step: `step-13-scorecard-update.prompt.md`*
