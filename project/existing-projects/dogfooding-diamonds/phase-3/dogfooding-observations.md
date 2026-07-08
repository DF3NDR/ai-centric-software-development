# Phase 3 Dogfooding Observations — Diamonds Phase 3 (populated instance)

> Populated instance of the toolkit `dogfooding-observations.md` template for the `@diamondslab/diamonds` Phase 3 dogfood.
> **Date:** 2026-07-07 · **Total observations:** 14 (P3-Obs-01..14) — within the toolkit's 8–15 first-dogfood prediction.
> §1 authored in M4-E1; §2 three-pass review in M4-E2 (Pass-2 dispositions pending OP-10 → see status inline).

---

## §1 — Observation Log

| ID | Description | Handling recommendation | Source |
|----|-------------|------------------------|--------|
| **P3-Obs-01** | AI-Centric Playbook Skill reference should be added to the Phase 3 toolkit instructions/README — a practitioner picking up the toolkit won't know the skill exists. | Phase 3 v1.1 | Session 1 (Step 00) |
| **P3-Obs-02** | Step 00 §2 wording could clarify that "project knowledge with reference docs" and "library documentation lookup" cover different gaps, not substitutes. | Phase 3 v1.1 (minor) | Session 1 (Step 00) |
| **P3-Obs-03** | Step 00 §3 cross-repo-search three-row template invites filling cells that don't apply for a solo-practitioner session. | Phase 3 v1.1 (low) | Session 1 (Step 00) |
| **P3-Obs-04** | Phase 2 Step 03 §2 detail missing for MC-21 (multi-mechanism MC in §1.1 with no §2 entry). **VG-P3-U-01.** | **Upstream Phase 2 v1.2** | Session 1 (Step 01) |
| **P3-Obs-05** | NTI mentions in primary briefs lack explicit cycle-vs-future-cycle clarification. **VG-P3-U-02.** | **Upstream Phase 2 v1.2** | Session 1 (Step 01) |
| **P3-Obs-06** | `Github:search_code` expected per Step 00 §3 was not pre-loaded; needed a `tool_search` round-trip. | Phase 3 v1.1 (minor) | Session 1 |
| **P3-Obs-07** | Step 03 Contract sub-template A.4 doesn't ask *conformance-suite purpose/lifecycle role* before harness location; reframing during MC-04 substantively shaped decisions. | Phase 3 v1.1 | Session 1 (Step 03) |
| **P3-Obs-08** | `Github:search_code` returned "No approval received" mid-session despite working earlier — Step 00 §3 capability claim over-confident. | Phase 3 v1.1 | Session 1 |
| **P3-Obs-09** | MC-21 Session-1 artifact §2.4 mis-cites the coordinated cohort ("Plan §5.2 / MC-04+MC-21+MC-22+MC-13") — should be **Plan §2.2** and include **MC-05**. | **Phase 2 v1.2** (Step 03 checklist: verify cohort citations) + artifact erratum | M0 / Step 04 |
| **P3-Obs-10** | Currency check caught a Phase-2-scheduled dependency (MC-11 publish workflow) that **shipped early** via a parallel productization track — handled cleanly as a grounding update, but the toolkit has no explicit "dependency shipped early via parallel track" currency-event guidance. | Phase 3 v1.1 (Step 01 / §7) | M0-E1/E2 |
| **P3-Obs-11** | Two productization tracks share one subject at different cadences (df3ndr releases vs AICSDP design cycle); the toolkit has no handshake for "another release shipped mid-design-cycle." | Phase 3 v1.1 (§7) | M0-E2 |
| **P3-Obs-12** | Several Plan §10.3 watch-triggers are *process/methodology* triggers with no runtime code touchpoint; sub-template E.5 assumes touchpoint-backable triggers. | Phase 3 v1.1 (E.5 taxonomy) | M1-E2 |
| **P3-Obs-13** | The four-spoke flow is described in three artifacts (MC-12 §2.4, MC-07 verify-a-release, Verification I-4); the toolkit could prompt Step 03 to declare a single source of truth for artifacts referenced by 3+ briefs. | Phase 3 v1.1 (Step 03/04) | M2-E1 (Step 04) |
| **P3-Obs-14** | A well-specified F.2 (shape + worked examples) made Step 05 refinement near-mechanical — a **positive** signal that the OP-6 "shape + worked examples" choice paid off. | Phase 3 v1.1 (calibration note; no change needed) | M2-E2 (Step 05) |

## §2 — End-of-Phase Review — Diamonds Phase 3 Dogfood

### Pass 1 — Cluster

| Cluster | Observations | Gap type / target |
|---------|--------------|-------------------|
| **C1 — Tooling-claim precision** | 06, 08 | Step 00 §3 should distinguish "tool present" vs "tool consistently usable" |
| **C2 — Step 00 wording / solo-fit** | 02, 03 | Step 00 §2 wording + §3 solo-practitioner template rows |
| **C3 — Skill discoverability** | 01 | Toolkit instructions/README should reference the Playbook Skill |
| **C4 — Sub-template question completeness** | 07 | Step 03 Contract A.4 (purpose before harness); analogous checks in other sub-templates |
| **C5 — Upstream Phase 2 toolkit gaps** | 04, 05, 09 | Phase 2 Step 03 §2 completeness + NTI cycle-tagging + cohort-citation check (VG-P3-U-01/02 + Obs-09) |
| **C6 — Concurrent-release / parallel-track currency** | 10, 11 | Step 01 / §7 currency discipline lacks "dependency/release shipped mid-cycle" event |
| **C7 — Cross-artifact taxonomy & single-source** | 12, 13 | E.5 watch-trigger taxonomy (code vs process); Step 03/04 single-source-of-truth declaration |
| **C8 — Positive calibration** | 14 | Confirms shape+worked-examples for verification briefs; calibration note |

### Pass 2 — Decide Per Cluster  *(✅ RATIFIED by Owner 2026-07-07 — OP-10, all 8 as drafted)*

| Cluster | Disposition (draft) | Route |
|---------|--------------------|-------|
| C1 Tooling-claim precision | **Accept** | Phase 3 v1.1 |
| C2 Step 00 wording / solo-fit | **Accept-with-refinement** (bundle the wording + template edits) | Phase 3 v1.1 |
| C3 Skill discoverability | **Accept** | Phase 3 v1.1 |
| C4 Sub-template question completeness | **Accept** | Phase 3 v1.1 |
| C5 Upstream Phase 2 gaps | **Accept** | **Upstream Phase 2 v1.2** |
| C6 Concurrent-release currency | **Accept** (new §7 currency-event guidance) | Phase 3 v1.1 |
| C7 Cross-artifact taxonomy & single-source | **Accept-with-refinement** | Phase 3 v1.1 |
| C8 Positive calibration | **Accept** (calibration note; no prompt change) | Phase 3 v1.1 |

### Pass 3 — Revise *(SCOPED ONLY — not authored; separate session)*

What the **Phase 3 v1.1** revision would change (per accepted cluster):
- C1/C2/C3: Step 00 — distinguish tool-present vs usable; clarify §2 wording; make §3 rows solo-optional; add a Skill-reference pointer.
- C4: Step 03 — add a "conformance-suite purpose/lifecycle role" question to Contract A.4; audit other sub-templates for the analogous "purpose before mechanism" question.
- C6: Step 01/§7 — add a "concurrent-release / dependency-shipped-early" currency-event check.
- C7: E.5 — add a code-observable-vs-process watch-trigger taxonomy; Step 03/04 — a single-source-of-truth declaration for artifacts referenced by 3+ briefs.
- C8: add a calibration note that shape+worked-examples makes Step 05 near-mechanical.

What the **Phase 2 v1.2** revision would change:
- VG-P3-U-01 (Obs-04): Step 03 Evaluation Checklist — every multi-mechanism MC in §1.1 must have a §2 detail entry.
- VG-P3-U-02 (Obs-05): Step 03 — per-NTI, ask this-cycle vs future-cycle.
- Obs-09: Step 03 — verify coordinated-cohort citations (section number + membership).

## §3 — Revision Outcomes

*(empty — the Phase 3 v1.1 and Phase 2 v1.2 revisions are separate, out-of-scope sessions; this dogfood produces their input queue only. See the queue in the M4-E2 review record.)*

## Version History

| Version | Date | Change |
|---------|------|--------|
| v1.0 | 2026-07-07 | §1 populated (14 observations); §2 three-pass review drafted (Pass-2 pending OP-10). |
