# Phase 6 — Testing & Audit Tool Set (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Purpose

This tool set supports **Phase 6: Testing & Audit** when applied to an
**existing codebase** that has completed Phases 1–5 of the
existing-projects track.

Phase 6's job here is **independent, change-aware audit of the changed
system**: executing the verification instruments the track designed in
Phase 3 and made executable in Phase 5, running seven independent audit
dimensions with configurations separate from the ones that built the
changes, comparing against measured baselines rather than projections,
and producing the definitive pre-release scorecard and the deployment
readiness determination. The gates have real authority — a FAIL blocks
release.

This is the existing-projects variant of Phase 6. The greenfield variant
(`toolkit/new-projects/phase-06-testing-audit/`) audits a brand-new
system uniformly. This variant is **change-aware**: deepest scrutiny on
the change surface, regression assurance for the untouched remainder,
blast-radius analysis at the seams — while executing the pre-designed
Phase 3 instruments as the floor and independent auditing as the
ceiling.

> **Companion Skill.** `skills/ai-centric-playbook/` — load per the
> skill's own guidance; the instructions file explains when.

---

## When to Use This Tool Set

Use this tool set when:

- The subject is an existing codebase that has completed Phase 5 with an
  Implementation Bundle whose Step 10 determination is READY or
  CONDITIONALLY READY (amendment packages resolved)
- The changed system is runnable/testable (or patch-mediated execution is
  arranged), and audit tooling is available
- The team is ready to subject the changes to independent scrutiny with
  gates that can block release

Do *not* use this tool set when:

- The project is greenfield — use the greenfield Phase 6 toolkit
- Phase 5 is incomplete or its gate returned NOT READY — resolve first
- The intent is to use audit as a formality — the seven-outcome gate has
  no undocumented "deploy anyway" path

---

## Tool Set Files

| File | Type | Purpose |
|------|------|---------|
| `testing-audit.existing-project.instructions.md` | Load-once context | Three shifts; independence + finding-disposition disciplines; instrument execution; five channels; seven-outcome gate; behavioral rules; dependency graph; output standards. |
| `step-00-building-block-discovery.prompt.md` | Action (living document) | Audit tooling inventory — test runners, scanners, load tools — and the **independence configurations** each audit will use. |
| `step-01-phase-5-input-validation.prompt.md` | Interview → Action | Validates the Implementation Bundle; hard blocking checks on the Phase 5 gate; two-scope Validation Gap Register (Channel 1). |
| `step-02-audit-specification.prompt.md` | Action (with clarification) | The change-aware scope (change surface / remainder / seams), per-principle thresholds, the instrument-to-audit mapping (Phase 3 Bundle §3), the per-audit independence plan, conditional sections, and the audit schedule. |
| `step-03-extended-and-regression-testing.prompt.md` | Evaluation (audit; XT-NN) | Spec-derived edge/adversarial/property testing beyond Phase 5's suites + full-system regression assurance; chaos scaled per Step 02. |
| `step-04-security-audit.prompt.md` | Evaluation (audit; SA-NN) | Change-surface-priority penetration testing and scanning; SEC-NN verification at TB-NN boundaries; compliance matrix (conditional section). |
| `step-05-performance-validation.prompt.md` | Evaluation (audit; PV-NN) | Empirical validation vs Phase 1 measured baselines + change-spec §6 targets; unexplained pre-cycle regressions are findings; severe misses phase-traced. |
| `step-06-specification-conformance-audit.prompt.md` | Evaluation (audit; CF-NN) | End-to-end conformance vs the Phase 4 formal contracts and change specifications; every deviation classified (spec wrong / impl wrong / acceptable). |
| `step-07-ai-vs-ai-system-audit.prompt.md` | Evaluation (audit; AA-NN; **separate AI configuration**) | System-level independent audit — cross-module interactions and the blast-radius lens; independence attested. |
| `step-08-formal-verification-review.prompt.md` | Evaluation (structured human judgment; FV-NN; **conditional**) | Practitioner review of Phase 5's formal models — fidelity, property adequacy, boundary conditions. Runs only if Phase 5 designated models. |
| `step-09-documentation-audit.prompt.md` | Evaluation (audit; DG-NN) | The scored queryability test + stale-doc checks (docs describing the pre-change system) + coverage vs DOC-NN; freezes the documentation as the release baseline. |
| `step-10-audit-synthesis-and-deployment-readiness-review.prompt.md` | Action + Evaluation (synthesis + the gate) | Instrument consolidation, disposition verification, the definitive scorecard refresh, the Carried-Risk Register, the seven-outcome determination, and the four amendment packages (§7.1–§7.4). |
| `dogfooding-observations.md` | Living log | P6-Obs-NN capture for end-of-phase review. |

---

## Recommended Sequence

```
Phase 5 Implementation Bundle (gate READY/COND. READY) + per-module records
+ Phase 3 Bundle §3 instruments + Phase 4 contracts/frameworks/Impact Map
+ Phase 1 measured baselines + Phase 2 weights
        │
        ▼
   ═══ STAGE 1: AUDIT SCOPING (sequential) ═══
   Step 00 Building Block Discovery ──→ tooling + independence inventory
   Step 01 Phase 5 Input Validation ──→ gap register (two-scope; Channel 1)
   Step 02 Audit Specification ───────→ scope, thresholds, instrument map,
        │                                independence plan, conditionals
        ▼
   ═══ STAGE 2: INDEPENDENT AUDITS (parallel-eligible) ═══
   ┌────────┬────────┬────────┬────────┬────────┬─────────┬────────┐
   │Step 03 │Step 04 │Step 05 │Step 06 │Step 07 │Step 08* │Step 09 │
   │Extended│Security│Perf.   │Conform-│AI-vs-AI│Formal   │Documen-│
   │& Regr. │Audit   │Valid.  │ance    │System  │Verif.   │tation  │
   │Testing │        │        │Audit   │Audit   │Review   │Audit   │
   │(XT)    │(SA)    │(PV)    │(CF)    │(AA)    │(FV)*    │(DG)    │
   └────┬───┴────┬───┴────┬───┴────┬───┴────┬───┴────┬────┴───┬────┘
        └────────┴────────┴───┬────┴────────┴────────┴────────┘
                              ▼            (*conditional)
   ═══ STAGE 3: SYNTHESIS & GATE ═══
   Step 10 Audit Synthesis & Deployment Readiness Review
        │  (scorecard refresh; carried-risk register; 7 outcomes)
   ┌────┴────┬───────────┬──────────┬──────────┬──────────┬──────────┐
   ▼         ▼           ▼          ▼          ▼          ▼          ▼
 READY   CONDITION-  NOT READY  Phase 5    Phase 4    Phase 3    Phase 2
 → Phase ALLY READY  (Phase 6   amendment  amendment  amendment  amendment
 7       (deploy w/  gaps) →    (Ch. 2)    (Ch. 3)    (Ch. 4)    (Ch. 5)
         conditions) remediate
```

Fixes for findings are implemented through the **Phase 5 loop
discipline** (scoped re-entry) and re-audited scoped — never patched
inside an audit session.

---

## The Minimum Viable Path

Ten of eleven steps are mandatory. **Step 08** runs only if Phase 5
designated components for formal verification. Section-level scaling
(set at Step 02 §6): the compliance-matrix section of Step 04 runs only
where obligations exist; chaos testing in Step 03 scales with
operational risk; audit depth scales with the change surface's risk
profile. No mandatory audit is skipped.

---

## MCP Server Recommendations

- **Test execution + coverage** — Step 03's suites and every audit's
  probes; the regression assurance depends on running the real suites.
- **Security scanners** (dependency, static analysis, secrets) — prefer
  the project's existing tooling; Step 04 goes beyond it independently.
- **Load/benchmark tooling** — Step 05 is empirical or it is not
  performance validation.
- **Separate AI configurations** — Steps 06/07 (and ideally every audit)
  need configurations distinct from the Phase 5 generating sessions;
  inventoried at Step 00, planned at Step 02 §5.
- **Documentation-only session capability** — Step 09's queryability
  test runs with no codebase access.

Capability shifts mid-phase amend the Step 00 document (§7), inherited
discipline unchanged.

---

## Dogfooding & Calibration Guidance

Capture observations in `dogfooding-observations.md` (P6-Obs-NN):
instrument-to-audit mapping fit, the three-way scope allocation in
practice, independence-plan practicality for a solo practitioner,
queryability-test calibration, and cross-step handoffs. Fast, incomplete
capture; three-pass end-of-phase review (cluster → decide → revise),
inherited from Phase 1 v1.3 / Phase 2 v1.1 / Phase 3 v1.1.

The first Phase 6 dogfood is expected to stress the v1.0-original
concepts: the instrument-distribution model, the change-aware scoping,
and the measured-baseline comparison rules.

---

## Common Pitfalls

*Toolkit-run-specific; the instructions file has the comprehensive
list.*

**Skipping Step 02 and "just auditing."** Without the scope allocation,
thresholds, and independence plan, the audits drift into either
change-only tunnel vision or unfocused re-verification.

**Executing instruments and calling it done.** The instruments verify
what Phase 3 knew to design. The independent audit work beyond them is
where Phase 6 earns its keep.

**One session, all audits.** Separate sessions per audit reinforce
independence and keep evidence bases distinct.

**Letting a finding idle.** Every XT/SA/PV/CF/AA/FV/DG finding is
dispositioned — resolved, accepted (into the Carried-Risk Register), or
dismissed with justification. Step 10 verifies zero idle findings.

**Fixing during the audit.** Route fixes through Phase 5's loop
discipline and re-audit scoped. An auditing session that patches code
has left its role.

---

## What's Available, What's Not

### Available in v1.0
All eleven step prompts, instructions file, README, dogfooding template.

### Not Yet Available (Queued for v1.1+)
Worked examples (a Diamonds-derived Audit Specification and one audit
report); per-stack security-audit methodology variants; a
solo-practitioner independence-plan pattern library (expected to be the
first dogfood's richest observation source).

---

## Version History

| Version | Date | Source | Summary |
|---------|------|--------|---------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Phase 6 existing-projects toolkit. Fourteen files (instructions + 11 step prompts + README + dogfooding template). Three-stage structure (scoping / seven parallel independent audits / synthesis+gate). v1.0-original disciplines: change-aware three-way scope allocation; Phase 3 instrument-to-audit distribution with execution accounting; measured-baseline comparison (pre-cycle regression = finding); no-fixes-in-audit with scoped fix-and-re-audit. Five feedback channels; seven-outcome gate with the Carried-Risk Register; finding prefixes XT/SA/PV/CF/AA/FV/DG-NN. Independence inventory → plan → attestation → verification chain. Inherits the track's step-00/step-01 scaffolding, scorecard refresh pattern, currency rules, and dogfooding protocol. |

---

*Part of the Phase 6 (Existing Projects) Testing & Audit Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `testing-audit.existing-project.instructions.md`*
