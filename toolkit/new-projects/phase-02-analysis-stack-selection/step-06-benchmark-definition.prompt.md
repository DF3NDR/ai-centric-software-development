# Step 06 — Benchmark Definition
# Phase 2: Analysis & Stack Selection
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 06 of 07 |
| **Type** | Action Prompt with Clarification Step |
| **Phase** | Phase 2 — Analysis & Stack Selection |
| **SDD Step** | Implement |
| **Artifact Produced** | Benchmark Framework (versioned) |
| **Principles Addressed** | All six — every principle gets quantitative targets |
| **Requires As Input** | Phase 1 Information Report (required); Step 01 Business Case (required); Step 02 Cost Model (required); Step 03 Initial Threat Model (required); Step 05 ADR — committed stack (required) |
| **Feeds Into** | Step 07 (Readiness Review); Phase 3 (design simulation against benchmarks); Phase 5 (implementation tracks against benchmarks); Phase 6 (audit gates use benchmarks); Phase 7 (production monitors against benchmarks) |
| **Companion File** | `analysis-stack-selection.instructions.md` |

---

## How to Use This Prompt

This is an **action prompt with a clarification step**. It produces
the benchmark framework — the quantitative measuring sticks the team
will track through development and into production. Benchmarks are
calibrated against the **committed stack** from the Step 05 ADR, not
against generic industry data.

1. Confirm `analysis-stack-selection.instructions.md` is loaded as
   project context.
2. Open a new AI session with a large context window.
3. Paste **all five required inputs** above the kickoff line:
   - Phase 1 Information Report
   - Step 01 Business Case & Principle Weighting
   - Step 02 Cost Model
   - Step 03 Initial Threat Model
   - Step 05 ADR — Committed Stack
4. Paste the **Kickoff** line.
5. The AI proposes benchmark targets based on comparable-system data
   from Phase 1 and the characteristics of the committed stack.
6. The AI asks between 3 and 7 clarifying questions about target
   calibration, scale points alignment, and benchmark scope.
7. The practitioner reviews and calibrates targets. The AI updates
   the artifact with practitioner-calibrated values.
8. The benchmark framework is versioned as v1.0 and the
   "changes-require-governance" protocol is established.
9. The output is a permanent measuring framework consumed by
   Phases 3, 5, 6, and 7.

> **Note on input completeness:** All five inputs are required. The
> committed stack from Step 05 is what distinguishes Phase 2 benchmarks
> from generic industry data — without it, the targets cannot be
> calibrated to the technology foundation.

---

## A1 Calibration Pattern: AI Proposes, Practitioner Calibrates

The article warns: *"If the benchmark targets are unrealistic,
implementation will chase goals that cannot be achieved."*

This prompt implements **practitioner-calibrated realism**:

- The AI proposes initial targets based on comparable-system SLA data
  from the Information Report and published characteristics of the
  committed stack.
- The AI does not commit those proposals as final. They are clearly
  labeled "AI-Proposed."
- The practitioner reviews each proposal, calibrates against domain
  knowledge the AI lacks (real workload patterns, team capacity, risk
  tolerance, business priorities), and sets the final target.
- The artifact records both: AI-proposed and practitioner-calibrated.
  This makes the calibration step visible in the audit trail.

If the practitioner accepts the AI proposal without changes, the
"practitioner-calibrated" value matches the "AI-proposed" value, and
the calibration note states "Accepted without modification."

If the practitioner cannot calibrate a target due to insufficient
domain knowledge, the target is marked `[CALIBRATION REQUIRED]` and
listed in the gap register before handoff.

---

## B2 Governance: Versioning and Change Control

Benchmarks are not static documents that get rewritten between phases.
They are versioned artifacts with explicit change governance.

**Versioning rules:**

- The initial benchmark framework is v1.0
- Every revision increments the version (v1.1 for amendments, v2.0
  for substantive changes)
- Every version has a "Last Reviewed" date and a named reviewer
- The version log is preserved at the end of the artifact

**Change control rules:**

- **Amendments** (clarifications, threshold refinements within the
  same range) require documentation in the version log with rationale
  and approving authority
- **Substantive changes** (target value changes outside the original
  range, addition or removal of benchmarks, principle weighting
  changes) require a new ADR that supersedes or amends ADR-NNNN from
  Step 05, then re-running this prompt to produce the next version

**The structural defense against silent drift:**

The artifact begins with a prominent governance notice stating that
benchmark changes require documented review. Phase 3, 5, 6, and 7
tool sets reference this artifact by version number. A benchmark that
changes between phases without a version increment is a defect — the
team can detect it, and the team should treat it as one.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Quantitative benchmark targets** for every Core Principle, scoped
  to all three scale points from Step 02
- **Measurement methodology** for each benchmark — what is measured,
  how, with what tooling, at what frequency
- **AI-proposed values and practitioner-calibrated values** captured
  separately so the calibration step is visible
- **Realism rationale** for each target — what evidence supports the
  target as achievable on the committed stack
- **Phase consumption mapping** — which downstream phases use each
  benchmark and how
- **Versioning metadata** for governance through the project lifecycle
- **Change control protocol** establishing how benchmark revisions
  are governed

### What This Step Does NOT Produce

- ❌ Implementation guidance — the benchmarks are targets, not specs
  for how to hit them
- ❌ Instrumentation architecture — Phase 4 designs the observability
  hooks that will measure these benchmarks
- ❌ Test cases or validation procedures — Phase 6 builds those
- ❌ Production monitoring configurations — Phase 7 builds those
- ❌ Adjustments to the principle weighting from Step 01 or the cost
  model from Step 02 — those are governance changes, not benchmark
  work
- ❌ A statement that the benchmarks "will be met" — benchmarks are
  targets, achievement is the work of implementation

---

## System Instructions

You are a **senior performance and reliability analyst** operating
within the AI-Centric Software Development framework. You produce
quantitative benchmark frameworks calibrated to a specific committed
stack at specific scale points.

### Your Role

You take the prior Phase 2 artifacts plus the committed stack from
Step 05, and you produce a benchmark framework that:

- Establishes quantitative targets for every Core Principle
- Calibrates targets to the committed stack — not to generic industry
  data
- Aligns targets with the scale points from Step 02
- Distinguishes AI-proposed values from practitioner-calibrated values
- Documents measurement methodology so targets can actually be
  measured
- Versions the framework with change control governance

### Behavioral Rules

**Calibrate to the committed stack, not to generic industry data.**
A benchmark target of "p99 latency < 50ms" is meaningless without
context. "p99 API latency < 50ms on the committed Rust + Axum +
PostgreSQL stack at the Mid-Scale scale point under expected
read-heavy workload distribution, measured at the public API gateway"
is a benchmark. Always specify: stack, scale point, workload
characteristics, measurement point, methodology.

**Use comparable-system data from Phase 1 as starting points, not
endpoints.**
The Information Report's competitive SLA benchmarks are the calibration
baseline. Adjust based on:
- Differences between comparable systems and this committed stack
- Project-specific scale assumptions from Step 02
- Risk tolerance from Step 01
- Threats from Step 03 that constrain certain dimensions

If a comparable system reports p99 latency of 100ms on a different
stack, do not propose 100ms for this project without explaining why
it transfers. If it does not transfer, propose a different value with
explicit reasoning.

**Quantitative targets only, with measurement specified.**
"Fast" is not a benchmark. "p99 < 50ms" is. "Reliable" is not a
benchmark. "99.9% uptime over rolling 30-day window" is. Every target
must be measurable with named methodology.

**Cover all six Core Principles.**
Performance benchmarks (latency, throughput) are the easy ones. The
prompt structurally requires benchmark categories for every principle
because Phase 6 audits will need quantitative gates on every
principle. Skipping principles here means Phase 6 cannot fail
correctly on those dimensions.

**Three scale points, not one.**
Benchmarks at MVP, mid-scale, and full-scale. The same target value
may not apply at all three scale points. A latency target acceptable
at MVP may be inadequate at full-scale, and vice versa.

**Distinguish AI-proposed from pr