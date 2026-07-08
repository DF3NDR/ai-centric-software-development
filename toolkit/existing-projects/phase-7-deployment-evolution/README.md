# Phase 7 — Deployment & Evolution Tool Set (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Purpose

This tool set supports **Phase 7: Deployment & Evolution** when applied
to an **existing codebase** that has completed Phases 1–6 of the
existing-projects track.

Phase 7's job here is **shipping the audit-cleared release into the
operational reality that already exists — and keeping the loop
turning**: the per-release deployment sequence (front go/no-go,
execution, rollback/recall readiness), the standing operational loops
(runbooks, drift detection, the live scorecard), and the evolution loops
(technical debt, change orchestration) that ultimately assemble the
**Next-Cycle Package** re-entering the track's own Phase 1/2 toolkits.

This is the existing-projects variant of Phase 7. The greenfield variant
(`toolkit/new-projects/phase-07-deployment-evolution/`) takes a
brand-new system live for the first time. This variant ships a release
into a project that already ships — with **release-shaped deployment**
(publish, tag, changelog, release-evidence artifact, consumer
advisories; recall = deprecation + advisory + patched release) as
first-class alongside service-shaped deployment, operations reconciled
with the team's actual practice, and evolution channeled into the next
improvement cycle.

> **Companion Skill.** `skills/ai-centric-playbook/` — load per the
> skill's own guidance; the instructions file explains when.

---

## When to Use This Tool Set

Use this tool set when:

- The subject has completed Phase 6 with a Deployment Readiness Report
  whose determination is READY or CONDITIONALLY READY (amendment
  packages resolved)
- The release machinery (pipeline, registry access, or deploy tooling)
  is available per the Step 00 inventory
- The team is ready to ship, operate, and evolve under the same rigor
  that built the change

Do *not* use this tool set when:

- The project is greenfield — use the greenfield Phase 7 toolkit
- Phase 6 returned NOT READY in any variant — resolve it first
- The intent is a one-off publish with no operational follow-through —
  the standing loops are the phase, not an optional extra

---

## Tool Set Files

| File | Type | Purpose |
|------|------|---------|
| `deployment-evolution.existing-project.instructions.md` | Load-once context | Three shifts; the cadence-and-trigger model; Channel 1 + cycle-backs (no terminal gate); living registries (RB/DR/TD/CB-NN); instruction-set output discipline; safety gates; behavioral rules; pitfalls. |
| `step-00-building-block-discovery.prompt.md` | Action (living document) | Release machinery, monitoring access, registry credential posture, scanner scheduling, patch-mediated fallbacks — and the deployment-shape evidence. |
| `step-01-phase-6-input-validation.prompt.md` | Interview → Action | Validates the Deployment Readiness Report; hard blocking checks on the Phase 6 gate; carried-risk inventory; two-scope Validation Gap Register (Channel 1). |
| `step-02-launch-readiness-confirmation.prompt.md` | Evaluation (the front gate; per release) | Release definition + prerequisite verification + release-evidence plan → GO / CONDITIONAL GO / NO-GO. |
| `step-03-deployment-execution-and-verification.prompt.md` | Action (AI-executable instruction set; per release) | The deployment checklist — release-shaped and service-shaped branches, human checkpoints, evidence-artifact emission, day-one observability activation — plus the Deployment Record. |
| `step-04-rollback-and-recall-procedure.prompt.md` | Action (AI-executable instruction set; readied per release) | Defined triggers, the service rollback path AND the release recall path (deprecation + advisory + patched release, registry realities), verification, exercise cadence. |
| `step-05-operational-runbooks.prompt.md` | Action (instruction sets; living registry) | RB-NN runbooks — existing practice codified with provenance tags, extended for the cycle's new surface; the post-incident feedback loop. |
| `step-06-drift-detection-and-continuous-compliance.prompt.md` | Evaluation (recurring) | DR-NN findings across specification / scorecard / compliance drift (compliance conditional); scheduled conformance checks vs the Phase 4 contracts; carried-risk timeline watch; routing. |
| `step-07-operational-scorecard.prompt.md` | Action + Evaluation (recurring) | The launch refresh vs the Phase 6 baseline, then ongoing refreshes on cadence + per material incident — the live dashboard; cost-model calibration continues toward MEASURED. |
| `step-08-technical-debt-management.prompt.md` | Action + Evaluation (living registry) | TD-NN inventory (every SDD bypass captured), three-quantity characterization, principle-weighted prioritization, SDD-cycle resolution routing. |
| `step-09-evolution-and-next-cycle-orchestration.prompt.md` | Action (routing + assembly) | Change intake and impact assessment; CB-NN cycle-back routing (abbreviated vs full re-entry); and the **Next-Cycle Package** assembling re-elevations, calibrated multipliers, watch-trigger outcomes, and accumulated candidates for the next improvement cycle. |
| `dogfooding-observations.md` | Living log | P7-Obs-NN capture for end-of-phase review (in a continuous phase: reviewed at cycle boundaries). |

---

## Recommended Sequence

```
Phase 6 Deployment Readiness Report (READY / COND. READY) + Carried-Risk
Register + frozen docs + compliance matrix + performance baselines +
scorecard refresh + calibration table
        │
        ▼
   Step 00 Building Block Discovery ──→ machinery + monitoring inventory
   Step 01 Phase 6 Input Validation ──→ blocking checks; carried risks;
        │                               gap register (Channel 1)
        ▼
   ═══ STAGE 1: DEPLOYMENT (per release — ordered) ═══
   Step 02 Launch-Readiness ── NO-GO ──→ fix prerequisites / re-enter Phase 6
        │ (GO / CONDITIONAL GO)
        ▼
   Step 03 Deployment Execution & Verification
        │ (publish/deploy per shape; evidence emitted; observability live)
        ▼
   Step 04 Rollback & Recall (readied; fires on trigger)
        │
        ▼  the release is LIVE
   ═══ STAGE 2: CONTINUOUS OPERATIONS (standing loops) ═══
   ├─ Step 05 Runbooks        — continuous; per-incident; post-incident review
   ├─ Step 06 Drift & Compl.  — scheduled + per-change (DR-NN)
   └─ Step 07 Scorecard       — launch refresh; then cadence + per-incident
   ═══ STAGE 3: EVOLUTION (triggered) ═══
   ├─ Step 08 Technical Debt  — continuous capture; scheduled review (TD-NN)
   └─ Step 09 Evolution & Next-Cycle (CB-NN)
        │
        ├── single change ────────→ abbreviated/full SDD re-entry (Phases 1–6)
        ├── architectural tension ─→ Phase 3 + Phase 4
        ├── debt resolution ───────→ Phase 5 + Phase 6
        └── ACCUMULATION ──────────→ Next-Cycle Package → re-enter the
                                     Phase 1/2 toolkits (next improvement
                                     cycle — the track loops)
```

There is **no terminal gate**: the only gate is Step 02's front
GO/CONDITIONAL GO/NO-GO, and upstream findings route as CB-NN
cycle-backs rather than amendment packages.

---

## The Minimum Viable Path

All ten steps are standing capabilities. What varies is **cadence and
depth** — a small library runs lighter loops but runs them — plus one
section-level conditional: Step 06's compliance section runs only where
obligations exist (per the Phase 6 compliance matrix). Steps 02–04
repeat per release; Steps 05–09 run on their cadences and triggers for
the life of the system.

---

## MCP Server Recommendations

- **Release machinery access** — CI/CD status, tag/publish capability
  (with credential posture recorded, never printed), or deploy tooling
  per the declared shape.
- **Monitoring/observability access** — the Phase 5-built touchpoints
  are only useful if the Stage 2 loops can read them.
- **Scheduled scanning** — dependency/advisory monitoring through the
  project's existing security tooling.
- **Issue-tracker access** — consumer signals, incident capture, and
  TD/DR/CB registry upkeep benefit from direct tracker integration.
- **Patch-mediated fallback** — where AI cannot execute directly, the
  instruction sets still drive practitioner-executed steps with pasted
  results.

Capability shifts amend the Step 00 document (§7), inherited discipline
unchanged.

---

## Dogfooding & Calibration Guidance

Capture observations in `dogfooding-observations.md` (P7-Obs-NN):
release-shaped template fit (the first dogfood subject is a published
library — expect this to be the richest source), checkpoint placement in
the instruction sets, loop-cadence calibration, carried-risk tracking
friction, and Next-Cycle Package assembly. In a continuous phase, run
the three-pass review at **cycle boundaries** (when the Next-Cycle
Package hands off) rather than waiting for a phase end that never comes.

---

## Common Pitfalls

*Toolkit-run-specific; the instructions file has the comprehensive
list.*

**Publishing and walking away.** The standing loops ARE the phase. A
release with no drift detection, no scorecard cadence, and no debt
capture is the "observable on paper" failure in its brownfield form.

**Treating publish as deploy.** Published versions are immutable;
consumers pull on their own schedule; recall is deprecation + advisory +
patched release. Use the release-shaped branches.

**Skipping Step 02 because Phase 6 said READY.** The front gate exists
for what changed since the gate — the concurrent-release rule's home
ground.

**Executing consequential actions without checkpoints.** Publish,
deploy, rollback, recall, deprecation — every one sits behind a human
checkpoint in the instruction sets.

**Reconstructing the Next-Cycle Package from memory.** It accumulates as
items arise (Step 09 §-entries, CB-NN routing) — assembly at the cycle
boundary is consolidation, not archaeology.

---

## What's Available, What's Not

### Available in v1.0
All ten step prompts, instructions file, README, dogfooding template.

### Not Yet Available (Queued for v1.1+)
Worked examples (a Diamonds-derived release-shaped Deployment Record and
recall procedure); registry-specific recall playbooks (npm/PyPI/crates
deprecation realities); loop-cadence presets per project profile; the
next-cycle re-entry checklist for the Phase 1 toolkit (may land in the
Phase 1 toolkit instead — routing decided at first dogfood).

---

## Version History

| Version | Date | Source | Summary |
|---------|------|--------|---------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Phase 7 existing-projects toolkit. Thirteen files (instructions + 10 step prompts + README + dogfooding template). Cadence-and-trigger model with no terminal gate: front GO/CONDITIONAL GO/NO-GO at Step 02; Channel 1 + CB-NN cycle-backs replace amendment packages; the accumulation rule separates single-change re-entry from next-cycle-scale needs. v1.0-original disciplines: release-shaped deployment (publish/tag/evidence/advisory; recall = deprecation + advisory + patched release) first-class alongside service-shaped; provenance-tagged runbook reconciliation; carried-risk tracking to closure; the Next-Cycle Package re-entering the Phase 1/2 toolkits. Living registries RB/DR/TD/CB-NN; instruction-set output discipline with human checkpoints; cost-model calibration continued toward MEASURED. Inherits the track's step-00/step-01 scaffolding, scorecard refresh pattern, currency rules, safety gates, and dogfooding protocol. |

---

*Part of the Phase 7 (Existing Projects) Deployment & Evolution Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `deployment-evolution.existing-project.instructions.md`*
