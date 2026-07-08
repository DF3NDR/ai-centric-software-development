# Phase 3 Toolkit v1.1 — Revision Scope Brief

> ✅ **EXECUTED 2026-07-08** — all 7 clusters applied across 7 files (step-00, instructions, README, step-01, step-03, step-04, step-05), each bumped to v1.1 (header + footer + Version History). step-02/step-06/observations-template correctly untouched. Verified: version consistency + all clusters landed + code fences balanced. **Two scoping notes:** (a) C3 skill reference went to instructions + README (step-00 §5 already lists the Skill); (b) C8 calibration went to step-05 + the populated phase-3 instance — the *generic* dogfooding-observations template §4 was intentionally NOT edited (a Diamonds-specific finding doesn't belong in a generic template). Local (playbook repo uncommitted).


> **Target toolkit:** `toolkit/existing-projects/phase-3-technical-analysis/`
> **Surfaced by:** the Diamonds Phase 3 dogfood (this dir); end-of-phase three-pass review, OP-10 ratified 2026-07-07.
> **Scope depth:** scope brief (file → section → change → acceptance). **Authoring is a separate session** — this doc is its input, not the edit.
> **Source clusters:** C1, C2, C3, C4, C6, C7, C8 (see [dogfooding-observations.md](./dogfooding-observations.md) §2). Cluster C5 routes upstream to Phase 2 v1.2 (separate scope in `../phase-2/`).

---

## 0. Summary

Seven observation clusters route to a Phase 3 toolkit v1.1 revision. All dispositions are **Accept / Accept-with-refinement**. No behavioral rules change; these are precision, discoverability, completeness, and taxonomy refinements to existing prompts. Bump the phase-3 prompts' Toolset Version to **v1.1** with a "revised from Diamonds Phase 3 dogfooding run" note (mirroring how phase-2 step-03 already carries its v1.1 note).

## 1. Change table

| # | Cluster / Obs | File | Section | Change | Acceptance criterion |
|---|---------------|------|---------|--------|----------------------|
| 1 | C1 (Obs-06, 08) | `step-00-building-block-discovery.prompt.md` | §3 Cross-Repo Search + `### Known Friction Points or Risks` (line ~213) | Distinguish **"tool present"** from **"tool consistently usable"**; add a friction-point note that a listed tool (e.g. code-search) may need a load round-trip or fail mid-session. | The prompt explicitly asks the practitioner to record tool *reliability*, not just availability; §3 no longer implies presence = usability. |
| 2 | C2 (Obs-02) | `step-00-…prompt.md` | §2 Library and Specification Documentation Lookup (line ~268) | Clarify that "project knowledge with reference docs" and "library documentation lookup" cover **different gaps**, not substitutes. | §2 wording states the two are complementary; a reader can't mistake one for the other. |
| 3 | C2 (Obs-03) | `step-00-…prompt.md` | §3 Cross-Repo Search three-row template (line ~276) | Mark the three template rows **solo-practitioner-optional** (rows that don't apply need not be filled). | The template says solo sessions may leave inapplicable rows blank; no forced empty cells. |
| 4 | C3 (Obs-01) | `design-technical-analysis.existing-project.instructions.md` + `README.md` + `step-00` `### Skills, Custom AIs…` (line ~194) | instructions header / README intro / step-00 skills row | Add a reference to the **AI-Centric Playbook Skill** (`skills/ai-centric-playbook/`) so a practitioner knows it exists. | Both the instructions file and README name the skill with a one-line "load when depth is needed" pointer. |
| 5 | C4 (Obs-07) | `step-03-per-artifact-design-specification.prompt.md` | Sub-template A, **A.4 Conformance Scope** (line ~305) | Add a question asking the **conformance suite's purpose / lifecycle role** *before* harness location (self-conformance vs regression vs external conformance). Audit C/E/F sub-templates for the analogous **"purpose before mechanism"** question. | A.4 asks purpose first; a note flags the same pattern for other sub-templates. |
| 6 | C6 (Obs-10, 11) | `step-01-phase-2-input-validation.prompt.md` + `design-…instructions.md` §7 currency discipline | currency re-verification section | Add a **"concurrent-release / dependency-shipped-early" currency-event check**: when the subject advanced or a Phase-2-scheduled dependency shipped via a parallel track since the Plan, record it as a *grounding update* and test whether it invalidates any mechanism (Channel-2) vs merely de-risks it. | The §7 discipline names the parallel-track/early-ship event and gives the grounding-update-vs-amendment decision rule. |
| 7 | C7 (Obs-12) | `step-03-…prompt.md` | Sub-template E, **E.5 Watch-Trigger Integration** (line ~659) | Add a **code-observable vs process/methodology** taxonomy for watch-triggers; E.5 should mark which triggers a touchpoint can back and which are process-only. | E.5 template has a "type: code-observable | process" column; process triggers are legitimately markable as unbacked. |
| 8 | C7 (Obs-13) | `step-03-…prompt.md` §9 Cross-Brief References + `step-04-inter-artifact-coordination.prompt.md` §3 Shared Design Decisions | cross-brief / shared-artifact handling | Add a **single-source-of-truth declaration** for any artifact referenced by **3+ briefs** (one owning brief; others reference it). | Step 03 §9 / Step 04 §3 prompt for a single owner when an artifact appears in ≥3 briefs. |
| 9 | C8 (Obs-14) | `dogfooding-observations.md` template §4 Calibration + `step-05-verification-strategy.prompt.md` note | calibration note | Record the **positive** calibration: a well-specified F.2 (shape + worked examples) makes Step 05 near-mechanical — recommend the "shape + 2–3 worked examples" pattern for verification briefs. | A calibration note captures the finding; step-05 references the expected upstream shape. |

## 2. Sequencing

1. **step-00** edits (rows 1–3) — independent, do first.
2. **instructions + README + step-00 skills row** (row 4) — independent.
3. **step-03** edits (rows 5, 7, 8) — group the sub-template changes in one pass.
4. **step-01 / instructions §7** (row 6) — currency discipline.
5. **step-04 §3** (row 8 second half) + **step-05 note** (row 9) — coordination/verification touch-ups.
6. Version-stamp all edited phase-3 prompts to **v1.1** with the dogfood note; update each file's Version History.

## 3. Verification

- **Self-check:** re-run the phase-3 dogfood's friction points mentally against the revised prompts — each of Obs-01/02/03/06/07/08/10/11/12/13/14 should now be pre-empted by the prompt text.
- **Diff discipline:** every change is additive/clarifying (no behavioral-rule change); confirm no existing instruction is contradicted.
- **Cross-consistency:** the E.5 taxonomy (row 7) and the single-source rule (row 8) must not conflict with step-04's existing coordination sections.

## 4. Out of scope for this revision

- Cluster **C5** (VG-P3-U-01/02 + P3-Obs-09) → **Phase 2 toolkit v1.2** (see `../phase-2/REVISION-phase-2-v1.2-SCOPE.md`).
- Any change to the phase-3 *artifact outputs* already produced for Diamonds (those are committed to `DiamondsLab/diamonds`).
