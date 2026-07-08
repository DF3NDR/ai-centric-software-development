# Phase 6: Testing & Audit — Tool Set
## AI-Centric Software Development Playbook

---

## Overview

This directory contains the complete tool set for **Phase 6: Testing & Audit**
of the AI-Centric Software Development Playbook. Phase 6 applies an
**independent eye** to the complete, implemented system from Phase 5 — extended
testing, security audit, performance validation, specification conformance, a
system-level AI-vs-AI audit, formal-verification review, and documentation
audit — and produces the **deployment readiness determination**, the most
consequential checkpoint in the entire framework.

Phase 5 built the system optimistically — building, progressing, solving
problems, with every module passing its tests. Phase 6 asks a different
question: *is that enough?* Implementation-time testing was conducted by the
same team, with the same tool sets, within the same assumptions that produced
the code. Phase 6 steps outside that frame. It is **skeptical by design**: it
looks for what was missed, what was assumed, and what broke quietly. And it is
where the Core Principles stop being continuous signals and become **pass/fail
gates** with real authority to block deployment.

The primary outputs are the **Comprehensive Test Results**, the **Security
Audit Report**, the **Performance Validation Report**, the **Documentation
Audit** (including the queryability test and documentation freeze), the **Final
Principle Scorecard (v4.0)** with per-principle Pass/Conditional/Fail gates,
and the **Deployment Readiness Report** that authorizes or blocks deployment.

---

## Framework Context

This tool set is part of the [AI-Centric Software Development
Playbook](../../../README.md), a practitioner's framework for small teams
(1–5 people) that use AI tools to deliver what large organizations once
required.

### Phase 6 Differs From Phases 3–5 in Character

| Dimension | Phase 3 | Phase 4 | Phase 5 | Phase 6 |
|-----------|---------|---------|---------|---------|
| Primary work | Locking direction | Specifying the blueprint | Generating verified code | **Independently auditing the complete system** |
| AI role | Design analyst | Architecture specifier | Implementation generator + verifier | **Independent auditor** |
| Number of prompts | 9 | 16 | 15 | **10** |
| Orientation | Analytical | Specifying | Optimistic (building) | **Skeptical (verifying)** |
| Granularity | System | Per-module | Per-module | **System-level** |
| Principle role | Living scorecard | Architectural scores | Continuous signal | **Pass/Conditional/Fail gates** |
| Cross-phase living artifact | Scorecard v1.0 | Scorecard v2.0 | Scorecard v3.x | **Scorecard v4.0 (final pre-deployment)** |
| Backward effects | Phase 2 | Phase 3 + 2 | Phase 4 + 3 + 2 | **Phase 5 + 4 + 3 + 2** |
| Gate outcomes | 4 | 5 | 6 | **7** |

Four things make Phase 6 distinct:

**It is skeptical, not optimistic.** Its job is to find what the building
phases missed — separating verifying from building so verification has its own
space, rigor, and authority.

**The principles become pass/fail gates.** A principle below its target is not
a signal to monitor — it is a finding that must be resolved or explicitly
accepted before deployment. A Fail blocks.

**Independence is the source of value.** Same prompts and AI configuration find
the same things and miss the same things. Every audit uses a different
configuration, methodology, or perspective than Phase 5 used.

**It can amend any prior building phase.** A deployment-blocking finding
typically routes to Phase 5, but its root cause may be in Phase 4, Phase 3, or
Phase 2. The gate supports all four amendment paths.

### The Six Core Principles in Phase 6

| Principle | Phase 6 Evidence (and gate) |
|-----------|------------------------------|
| **Security** | Penetration testing, vulnerability scan, compliance matrix, security-architecture review. Typically the strictest gate — high+ findings block. |
| **Maintainability** | Test coverage, documentation queryability score, code-quality metrics. |
| **Economics** | Cost-model validation; actual development effort reconciled against estimates. |
| **Operations** | Monitoring functionality, deployment automation, rollback testing. |
| **Scoring & Metrics** | Completeness and currency of automated metrics. |
| **Correctness Verification** | End-to-end conformance, formal-verification review, AI-vs-AI system audit. |

### The SDD Cycle in Phase 6

Phase 6 applies the SDD cycle to the audit process: **Specify** the audit scope
(Step 01) → **Plan/Detail/Task** the audit dimensions (within each Stage 2
audit) → **Implement** by executing the audits → score and gate (Stage 3). The
audit specification prevents Phase 6 from becoming either an exhaustive but
unfocused review or a cursory check that misses critical areas.

### The Three-Stage Structure

- **Stage 1 — Audit Scoping** (Step 01): the audit specification that scopes
  everything, sets the per-principle gate thresholds, and establishes the
  per-audit independence plan.
- **Stage 2 — Independent Audits** (Steps 02–08): seven independent,
  parallel-eligible audit dimensions, each carrying an Independence Requirement.
- **Stage 3 — Scoring & Gate** (Steps 09–10): the Final Scorecard v4.0 with
  per-principle gates, then the Deployment Readiness Review.

---

## Directory Contents

```
phase-06-testing-audit/
├── README.md                                          ← You are here
├── testing-audit.instructions.md                      ← Load as project context
│
│   ═══ STAGE 1 — AUDIT SCOPING (once) ═══
├── step-01-audit-specification.prompt.md               ← scope, high-risk areas, gate thresholds, independence plan
│
│   ═══ STAGE 2 — INDEPENDENT AUDITS (parallel-eligible; each independent) ═══
├── step-02-extended-testing.prompt.md                  ← system-level, edge, adversarial, chaos
├── step-03-security-audit.prompt.md                    ← pen test + vuln + compliance matrix + security-arch review
├── step-04-performance-validation.prompt.md            ← empirical load/latency/throughput/resource vs Phase 2 benchmarks
├── step-05-specification-conformance-audit.prompt.md   ← E2E system-vs-spec; deviation classification
├── step-06-ai-vs-ai-system-audit.prompt.md             ← separate config; drift, undocumented behavior, inconsistency, arch compliance
├── step-07-formal-verification-review.prompt.md        ← CONDITIONAL; engineer review of Phase 5 models
├── step-08-documentation-audit.prompt.md               ← queryability test (20 Qs, docs-only) + documentation freeze
│
│   ═══ STAGE 3 — SCORING & GATE (once) ═══
├── step-09-final-principle-scorecard.prompt.md         ← v4.0; each principle scored vs threshold → Pass/Conditional/Fail
└── step-10-deployment-readiness-review.prompt.md       ← THE GATE; 7 outcomes, 4 amendment paths; deployment readiness report
```

**10 step prompts + instructions + README = 12 files.** Phase 6 is
system-level, so its footprint is closer to Phase 3's than to the per-module
bulk of Phases 4–5.

---

## File Descriptions

### `testing-audit.instructions.md`
**Type:** Instructions file (load once as persistent project context)

The overarching context for Phase 6: the six-phase comparison, the SDD cycle
for the audit, the six principles as gates, the three-stage structure, the
dependency graph, the minimum viable path, the **independence discipline**, the
**finding-disposition discipline**, the behavioral guidelines, the output
standards, the common pitfalls, and the Phase 7 handoff.

### Stage 1

#### `step-01-audit-specification.prompt.md` — Action Prompt
Scopes all of Phase 6: Phase 5 coverage vs. remaining gaps, high-risk
components, the **per-principle gate thresholds** (AI-proposed/calibrated from
Phase 2/4 + the article, set *before* the audits run), the applicable audit
areas (incl. whether Formal-Verification Review and the compliance matrix
apply), and the **per-audit independence plan**.

### Stage 2 — Independent Audits (parallel-eligible)

#### `step-02-extended-testing.prompt.md`
System-level, edge-case, adversarial, and chaos testing **derived from the spec,
not the implementation** — finding what implementation-time tests missed.
Findings: **XT-NN**.

#### `step-03-security-audit.prompt.md`
Independent of Phase 5 scanning: penetration testing (OWASP/PTES),
system-level vulnerability assessment, the **compliance matrix** (conditional),
and an independent SEC-NN security-architecture review. The Security gate is
typically the strictest. Findings: **SA-NN**.

#### `step-04-performance-validation.prompt.md`
**Empirical** load testing (1x/5x/10x), latency (p50/p95/p99 per workflow),
throughput, resource consumption vs. the cost model, scaling, cold start/
recovery — vs. the Phase 2 benchmarks. Severe misses route to Phase 3/4/5.
Findings: **PV-NN**.

#### `step-05-specification-conformance-audit.prompt.md`
End-to-end system-vs-spec conformance across API sequences, data flow,
cross-cutting concerns, and observability. Every deviation classified
spec-wrong / impl-wrong / acceptable. Findings: **CF-NN**.

#### `step-06-ai-vs-ai-system-audit.prompt.md`
The system-level elevation of Phase 5's AI-vs-AI review — **separate
configuration**, no generating reasoning. Drift, undocumented behavior,
cross-module inconsistency, architectural compliance. Findings: **AA-NN**.

#### `step-07-formal-verification-review.prompt.md` — Conditional
The **engineer's** review of Phase 5's AI-generated formal models (the most
human-judgment-dependent activity). The prompt facilitates the article's four
review questions; the engineer judges. Conditional — skipped if Phase 5
designated no models. Findings: **FV-NN**.

#### `step-08-documentation-audit.prompt.md`
The **queryability test** — twenty substantive questions answered from
documentation only (no codebase), scored — plus completeness assessment and the
**documentation freeze**. Findings: **DG-NN**.

### Stage 3 — Scoring & Gate

#### `step-09-final-principle-scorecard.prompt.md`
**Final Scorecard v4.0**: each principle scored from cited audit evidence
against its Step 01 threshold, yielding the per-principle **Pass / Conditional /
Fail** gate. Every Conditional carries a complete plan; cross-phase trend
(v1.0 → v4.0).

#### `step-10-deployment-readiness-review.prompt.md` — The Gate
Aggregates the gates, verifies every finding is dispositioned and every audit
complete, checks the four alignment dimensions, and produces the **seven-outcome
deployment readiness determination** and the **deployment readiness report**.
No "deploy anyway" path except a documented, tiered override.

---

## The Minimum Viable Path

Ten prompts is the full toolkit. Phase 6 is the final assurance before
production, so almost everything is mandatory.

### Mandatory (every Phase 6 project)

| Step | Prompt |
|------|--------|
| 01 | Audit Specification |
| 02 | Extended Testing |
| 03 | Security Audit |
| 04 | Performance Validation |
| 05 | Specification Conformance Audit |
| 06 | AI-vs-AI System Audit |
| 08 | Documentation Audit |
| 09 | Final Principle Scorecard (v4.0) |
| 10 | Deployment Readiness Review |

### The One Conditional Prompt

| Step | Prompt | Run When |
|------|--------|----------|
| 07 | Formal-Verification Review | Only if Phase 5 designated components for formal verification. Skipped (marked N/A) otherwise. |

### Section-Level Scaling

What scales *within* prompts rather than being skipped: the **compliance
matrix** (Step 03) runs only if compliance requirements apply; **chaos testing**
(Step 02) scales with project risk; the **depth** of each audit scales with the
risk profile set in Step 01. No mandatory audit is skipped — skipping a
pre-deployment assurance is the "audit as formality" pitfall.

---

## How to Use This Tool Set

### Prerequisites

1. Confirm the [Phase 5 toolkit](../phase-05-implementation/README.md) is
   complete with a passing Step 15 Readiness Review (READY or CONDITIONALLY
   READY). Phase 6 audits the authorized Phase 5 handoff.
2. Load `testing-audit.instructions.md` as project-level instructions.
3. Have available the different AI configurations/methodologies the
   independence plan calls for.

### Execution Order — Three Stages, Independent Audits

```
Phase 5 Package (codebase + tests, scan/conformance results, formal models,
                 docs DOC-NN, Scorecard v3.x, Step 15 Phase 6 Handoff Summary)
   │  + Phase 4 architecture/contracts/security; Phase 3 design direction;
   │    Phase 2 benchmarks + cost model
   ▼
═══ STAGE 1: AUDIT SCOPING (once) ═══
Step 01: Audit Specification (scope, thresholds, independence plan)
   │
   ▼
═══ STAGE 2: INDEPENDENT AUDITS (parallel-eligible; each independent) ═══
   ├─ Step 02 Extended Testing
   ├─ Step 03 Security Audit
   ├─ Step 04 Performance Validation
   ├─ Step 05 Specification Conformance Audit
   ├─ Step 06 AI-vs-AI System Audit
   ├─ Step 07 Formal-Verification Review (conditional)
   └─ Step 08 Documentation Audit
   │
   ▼
═══ STAGE 3: SCORING & GATE (once) ═══
Step 09: Final Principle Scorecard v4.0 (Pass/Conditional/Fail gates)
   ▼
Step 10: Deployment Readiness Review (the gate)
   │
   ┌──────────┬──────────┬──────────┬──────────┬──────────┬──────────┐
   ▼          ▼          ▼          ▼          ▼          ▼          ▼
Phase 7    Phase 6    Phase 5    Phase 4    Phase 3    Phase 2   (CONDITIONALLY
Authorized Internal   Amendment  Amendment  Amendment  Amendment  READY — deploy
(READY)    Remediation                                            with conditions)
```

### Parallelism

The seven audits (Steps 02–08) are parallel-eligible once Step 01 completes —
they are independent dimensions, and running them in separate sessions also
reinforces independence. Step 01 precedes all audits; Steps 09–10 follow all
applicable audits; Step 10 follows Step 09.

### Running Each Prompt

For each step: open a new AI session with `testing-audit.instructions.md`
loaded — for Stage 2, using the independent configuration the Step 01 plan
specifies; paste the required inputs (see the prompt's metadata table); answer
the clarifying questions (presence check + independence confirmation first);
review the output against the prompt's evaluation checklist. Step 08's
queryability test runs documentation-only; Step 06 requires a different model/
configuration; Step 07 requires the engineer present.

### Iterating

- **An audit surfaces findings** → recorded with IDs (XT/SA/PV/CF/AA/FV/DG),
  routed to Step 10 for disposition.
- **A conformance deviation** → classified spec-wrong (Phase 4) / impl-wrong
  (Phase 5) / acceptable.
- **A severe performance miss** → root-caused to Phase 3/4/5.
- **Step 09 yields a Fail** → Step 10 routes it to the responsible phase.
- **Step 10 returns a NOT READY variant** → run the corresponding amendment
  cycle (below), then re-audit and re-gate.

---

## The Four Amendment Cycles

Phase 6 is the deepest backward-reaching gate. Step 10 evaluates Phase 5,
Phase 4, Phase 3, and Phase 2 alignment as separate dimensions, producing a
distinct, structured amendment package for each Fail's root cause.

- **Phase 5 amendment** (the typical case) — a Fail rooted in an implementation
  defect. Fix in Phase 5, re-run the affected Phase 5 verification, re-audit
  the affected area, re-run Steps 09–10.
- **Phase 4 amendment** — a Fail rooted in architecture (structurally incapable
  of a benchmark; a conformance deviation rooted in the spec). Cascades through
  Phase 5.
- **Phase 3 amendment** — a Fail rooted in analysis/simulation/data (e.g., a
  severe performance miss from inaccurate Phase 3 simulation). Cascades through
  Phase 4/5.
- **Phase 2 amendment** (deepest) — a Fail rooted in the cost model/benchmarks.
  Cascades through Phase 3/4/5.

All four are governance, not failure — the structural defense against deploying
on a foundation the framework flagged as unfit.

---

## The Deployment Readiness Determination

The Step 10 gate is the most consequential checkpoint in the framework.

| Gate Dimension | What It Asks |
|---------------|--------------|
| Scoring-gate roll-up | Does each principle Pass / Conditional / Fail against its threshold? |
| Findings disposition | Is every audit finding triaged and dispositioned? |
| Per-audit completeness | Did every applicable audit run, independently, to its checklist? |
| Phase 5 / 4 / 3 / 2 alignment | Does any Fail's root cause lie in a prior building phase? |

### The Seven Outcomes

| Status | Meaning | Action |
|--------|---------|--------|
| **READY** | All gates Pass; findings dispositioned; audits complete; alignments verified | Deploy to Phase 7 |
| **CONDITIONALLY READY** | Conditional gates with complete plans; no Fails | Deploy with documented conditions (carried risks) |
| **NOT READY (Phase 6 gaps)** | Audit work incomplete / findings undispositioned | Complete Phase 6 |
| **NOT READY (Phase 5 amendment)** | A Fail rooted in implementation | Phase 5 amendment cycle, re-audit |
| **NOT READY (Phase 4 amendment)** | A Fail rooted in architecture | Phase 4 cycle (cascades) |
| **NOT READY (Phase 3 amendment)** | A Fail rooted in analysis/simulation | Phase 3 cycle (cascades) |
| **NOT READY (Phase 2 amendment)** | A Fail rooted in cost model/benchmarks | Phase 2 cycle (deepest cascade) |

---

## Independence and Finding Discipline

Two disciplines carry Phase 6.

### Independence

Every audit uses a different AI configuration, methodology, or perspective than
Phase 5 used; code audits (conformance, AI-vs-AI) do not reuse the generating
session. Each Stage 2 prompt carries an Independence Requirement and records
its configuration (or its limitation); Step 01 sets the plan; Steps 09–10
verify it was honored. This is the structural defense against "auditing with the
same assumptions."

### Finding Disposition

Each audit assigns domain-prefixed finding IDs so the gate can verify the
article's checkpoint — every finding dispositioned.

| Prefix | Audit |
|--------|-------|
| XT-NN | Extended Testing (02) |
| SA-NN | Security Audit (03) |
| PV-NN | Performance Validation (04) |
| CF-NN | Specification Conformance Audit (05) |
| AA-NN | AI-vs-AI System Audit (06) |
| FV-NN | Formal-Verification Review (07) |
| DG-NN | Documentation Audit (08) |

Findings are dispositioned (resolved / accepted / dismissed), not cited
forward — a distinct namespace from the Phase 4/5 constraint IDs the system is
**audited against** (SP/SEC/DA/DOC/GOV/SIC, H-NN, CS-NN, and the API contracts).

---

## Cross-Phase Living Documents

- **The Final Principle Scorecard (Step 09)** — v4.0, the definitive
  pre-deployment scoring with gate status. Phase 7 produces v5.0 at deployment
  and v5.x in operations, per the Phase 3 Step 06 protocol.
- **The Deployment Readiness Report (Step 10)** — the definitive deploy/block
  artifact and the primary Phase 7 input.
- **The Frozen Documentation (Step 08)** — the deployed-state baseline,
  maintained post-deployment via the Phase 4 documentation process.

---

## Common Pitfalls

**Treating audit as a formality.** *Defense:* the gates' real authority (a Fail
blocks) and the seven-outcome determination with no "deploy anyway" path short
of a documented override.

**Auditing with the same assumptions.** *Defense:* the per-prompt Independence
Requirement, the Step 01 plan, and the gate's verification.

**Skipping the formal-verification review.** *Defense:* Step 07's structured
engineer review and the Correctness gate's requirement that designated models
are reviewed.

**Documentation audit as checkbox.** *Defense:* Step 08's scored,
documentation-only queryability test.

**Conditional passes without timelines.** *Defense:* every Conditional records
shortfall, remediation, timeline, owner, and acceptance — or it is a Fail.

**Leaving findings undispositioned.** *Defense:* the finding-disposition
discipline and the Step 10 verification.

**Treating a severe benchmark miss as a Phase 6 problem.** *Defense:* the
amendment paths route severe misses to Phase 3/4/5 via root-cause analysis.

---

## Connecting to Phase 7

Phase 6 hands off the deployment readiness determination to Phase 7 (Deployment
& Evolution), which takes the system live and shifts the framework from building
to sustaining.

| Phase 7 Concern | Phase 6 Input |
|-----------------|---------------|
| Deployment authorization | The deployment readiness report (Step 10) |
| Production monitoring activation | Operations gate evidence (Step 04 / monitoring) |
| Operational runbooks | The frozen, queryable documentation (Step 08) |
| Carried-risk management | Conditional passes + known risks (Steps 09–10) |
| Compliance evidence | The compliance matrix (Step 03) |
| Performance baselines | The performance validation report (Step 04) |
| Phase 7 scorecard updates | Scorecard v4.0, the Phase 3 Step 06 protocol |

When all gates pass — or conditionally pass with documented plans — deployment
proceeds. Phase 7 is where the operational practices designed throughout the
process begin running, and where the SDD cycle continues driving the system's
evolution.

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | [date] | Initial release — instructions file plus ten prompts |

---

## Related Resources

- [AI-Centric Software Development Playbook — Full Series](../../../README.md)
- [Part 1 — Core Principles](../../../docs/part-01-core-principles.md)
- [Part 2 — Building Your Toolkit](../../../docs/part-02-building-your-toolkit.md)
- [Part 8 — Phase 6: Testing & Audit](../../../docs/part-08-testing-audit.md)
- [Phase 1 Tool Set](../phase-01-information-gathering-toolset/README.md)
- [Phase 2 Tool Set](../phase-02-analysis-stack-selection/README.md)
- [Phase 3 Tool Set](../phase-03-design-technical-analysis/README.md)
- [Phase 4 Tool Set](../phase-04-architecture-modular-design/README.md)
- [Phase 5 Tool Set](../phase-05-implementation/README.md)
- [Part 9 — Phase 7: Deployment & Evolution](../../../docs/part-09-deployment-evolution.md) *(the next phase)*

---

*Part of the AI-Centric Software Development Playbook*
*This tool set is a living artifact — it will be refined as the methodology
matures and use in practice reveals improvements.*
