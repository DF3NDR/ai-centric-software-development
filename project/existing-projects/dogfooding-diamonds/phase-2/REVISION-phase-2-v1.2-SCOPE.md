# Phase 2 Toolkit v1.2 — Revision Scope Brief

> ✅ **EXECUTED 2026-07-08** — all three changes applied to `step-03-mechanism-decisions.prompt.md` (now v1.2); verification replay confirms the three Diamonds gaps are pre-empted. Local (playbook repo uncommitted) — commit/push to `DF3NDR/ai-centric-software-development` when ready.


> **Target toolkit:** `toolkit/existing-projects/phase-2-design-analysis/`
> **Surfaced by:** the Diamonds **Phase 3** dogfood (upstream Channel-1 routing) — the phase-3 run found gaps in the phase-2 *toolkit*, which queue here for a phase-2 revision. Ratified OP-10 2026-07-07.
> **Scope depth:** scope brief (file → section → change → acceptance). **Authoring is a separate session.**
> **Source cluster:** C5 — VG-P3-U-01, VG-P3-U-02, P3-Obs-09 (see `../phase-3/dogfooding-observations.md` §2).

---

## 0. Summary

The phase-3 dogfood surfaced three gaps in the phase-2 toolkit. `step-03-mechanism-decisions.prompt.md` is already **v1.1** (revised from the *Phase 2* dogfood); this routing bumps it to **v1.2**. All three are completeness/consistency checks — no mechanism-decision behavior changes.

## 1. Change table

| # | Obs / gap | File | Section | Change | Acceptance criterion |
|---|-----------|------|---------|--------|----------------------|
| 1 | **VG-P3-U-01** (P3-Obs-04) — a multi-mechanism MC listed in §1.1 had **no §2 detail entry** (MC-21) | `step-03-mechanism-decisions.prompt.md` | `### Phase D — Comprehensiveness Check` (line ~233) + Output Format §1.1↔§2 (lines ~266/274) | Add a **completeness check**: every MC in **§1.1 "MCs requiring mechanism decision"** must have a corresponding **§2 detail entry**; Phase D fails if any §1.1 MC lacks a §2 block. | Phase D explicitly cross-checks §1.1 against §2; the Output Format notes the 1:1 requirement. A future Step 03 cannot leave a multi-mechanism MC without §2 detail. |
| 2 | **VG-P3-U-02** (P3-Obs-05) — NTI mentions lacked **cycle-vs-future-cycle** tagging | `step-03-mechanism-decisions.prompt.md` | `### Phase B — Per-MC Mechanism Drafts` (line ~195) | For each **NTI** in an MC's constraint chain, ask whether it is **this-cycle** or **future-cycle** work; record the tag in the §2 detail. | Phase B prompts a per-NTI cycle tag; §2 entries carry `[this-cycle|future-cycle]` for each NTI. |
| 3 | **P3-Obs-09** — the coordinated-cohort citation drifted downstream (wrong section §5.2 vs §2.2; membership dropped MC-05) | `step-03-mechanism-decisions.prompt.md` | `## 3. Inter-MC Dependency Graph` / cohort definition (line ~307) | Require the **Coordinated / Breaking-Change cohort** to be stated **once, canonically** (section anchor + full membership) and cross-checked in Phase C; add a note that downstream (Phase 3) briefs must cite *that* anchor. | The cohort has a single canonical statement with a stable anchor; Phase C verifies membership completeness. Reduces the chance a Phase 3 brief mis-cites it. |

## 2. Sequencing

All three edits are in one file (`step-03-mechanism-decisions.prompt.md`) — do them in a single pass:
1. Add the §1.1↔§2 completeness check to Phase D + Output Format (row 1).
2. Add the per-NTI cycle-tagging to Phase B + §2 template (row 2).
3. Canonicalize the cohort statement in §3 + Phase C cross-check (row 3).
4. Bump Toolset Version to **v1.2** with a "revised from Diamonds Phase 3 dogfooding run" note; update Version History.

## 3. Verification

- **Self-check:** replay the Diamonds Phase 2 §1.1/§2/cohort against the revised prompt — MC-21's missing §2 entry and the §5.2-vs-§2.2 cohort drift would both be caught by the new checks.
- **No-regression:** the v1.1 batch-sizing and mechanism-decision flow are unchanged; the additions are validation gates only.
- **Downstream link:** confirm the canonical cohort anchor (row 3) is the one a future Phase 3 Step 04 would cite.

## 4. Out of scope for this revision

- The seven **Phase 3 v1.1** clusters (see `../phase-3/REVISION-phase-3-v1.1-SCOPE.md`).
- Re-running the Diamonds Phase 2 cycle — this only revises the *toolkit* for future subjects; it does not amend the Diamonds Phase 2 Improvement Plan (that Plan stayed current through the Phase 3 dogfood; Channel 2 never fired).
