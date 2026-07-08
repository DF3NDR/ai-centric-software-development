# Phase 6 Dogfooding Observations (Existing Projects Toolkit)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08; no dogfooding cycles complete yet)
**Status:** Template — populated during Phase 6 dogfooding cycles

---

## Purpose of This File

This file captures observations from real Phase 6 (Existing Projects)
runs that surface gaps, miscalibrations, or improvements in the toolkit
itself. It is a **living dogfood log** — entries accrete during a Phase 6
run, are clustered and decided at end-of-phase, and drive v1.x+
revisions of the toolkit files.

The discipline is inherited from Phase 1 v1.3, Phase 2 v1.1, Phase 3
v1.1, and Phase 4 v1.0. Continuity matters; the protocol has been
validated across the prior toolkit cycles.

### What Goes in This File

Observations about the toolkit, captured during a Phase 6 run:

- A prompt's structure forced a workaround
- A behavioral rule produced unexpected resistance or unexpectedly
  smooth flow
- The change-aware three-way scope allocation (change surface /
  remainder / seams) felt over- or under-fitted in practice
- The instrument-to-audit mapping (Phase 3 Bundle §3 distribution)
  left an instrument without a natural home, or double-assigned one
- An independence-plan requirement was hard to satisfy or verify
  (especially solo-practitioner configurations)
- The queryability test or the measured-baseline comparison rules felt
  miscalibrated
- An output format produced confusion or was unexpectedly easy to
  consume in the next step
- A cross-step handoff (Step N → Step N+1) lost or duplicated
  information
- An upstream inheritance pattern (principle weights, Phase 4 baseline,
  estimates, cohorts, currency rules) felt miscalibrated

### What Does Not Go in This File

- Project-specific findings about the subject codebase — those go in the
  Phase 6 artifacts themselves
- Phase 5 / Phase 4 / Phase 3 / Phase 2 amendment items — those go in the Step 10
  §7 Amendment Packages
- Upstream toolkit gaps — those go in Step 01 §9.2; they feed the
  responsible toolkit's revision separately
- Observations about the framework as a whole (the Playbook) — those
  belong in framework-level review, not this toolkit-level log

---

## Observation Capture Protocol

Capture is **fast and incomplete by design**. Full analysis happens at
end-of-phase. The goal during the run is to record the observation while
it's fresh, not to analyze or act on it.

For each observation, capture:

- **Observation ID** — P6-Obs-NN (numbered sequentially within the
  dogfood cycle)
- **Surfaced during** — which step (00 through 10) and where in the step
  (section, loop iteration, module, work package, etc.)
- **Subject project** — which project the Phase 6 cycle is being run
  against
- **Brief observation text** — 1–3 sentences describing what was
  noticed. Avoid premature analysis; the cluster-and-revise pass handles
  that.
- **Suggested handling (tentative)** — Phase 6 v1.x revision / upstream
  to Phase 4 / upstream to Phase 3 / upstream to Phase 2 / upstream to
  Phase 1 / accept as-is / defer. This is a working guess; the
  end-of-phase review confirms.

Observations are added to §1 as the run proceeds.

---

## End-of-Phase Review Protocol

After Step 10 synthesis completes (and any amendment cycles resolve), run
the three-pass review:

### Pass 1 — Cluster

Group observations that:
- Address the same gap
- Touch the same toolkit file
- Suggest the same kind of revision

### Pass 2 — Decide Per Cluster

For each cluster, decide:

- **Accept** — the gap is real and the revision is straightforward;
  v1.1 lands the change
- **Accept with refinement** — the gap is real but the proposed revision
  needs adjustment; v1.1 lands a refined version
- **Defer** — the gap is real but the revision is not yet shape-clear;
  queue for v1.2+
- **Reject** — the gap is not actually a gap (the original toolkit was
  right; the observation was a misread)

Also route per cluster:

- **Phase 6 v1.x revision** — landed in this toolkit
- **Upstream to Phase 4 / Phase 3 / Phase 2 / Phase 1** — the gap is in
  an upstream toolkit; route to that toolkit's revision (Channel 1
  firing)
- **Cross-cutting (framework level)** — the gap is in the framework's
  conceptual structure; route to framework documentation review

### Pass 3 — Revise

Produce the v1.x files in a focused authoring session. Each revised file
gets a Version History row documenting what changed and citing the
observation cluster(s) that motivated the change.

---

## §1 — Observation Log

| ID | Surfaced In | Subject | Observation | Suggested Handling (Tentative) |
|----|------------|---------|-------------|-------------------------------|
| | | | | |

*Observations are appended here during Phase 6 runs. No entries yet —
toolkit at v1.0 with no dogfooding cycles complete.*

---

## §2 — End-of-Phase Reviews

*Populated after each Phase 6 dogfooding cycle's end-of-phase review.*

### §2.1 — [Subject Project] Phase 6 Dogfood

*Placeholder — populated when the first Phase 6 cycle completes.*

| Field | Value |
|-------|-------|
| Subject project | |
| Phase 6 cycle dates | |
| Observation count | |
| Cluster count | |
| Clusters routing breakdown | [N Phase 6 v1.x / N upstream Phase 5 / N upstream Phase 4 / N upstream Phase 3 / N upstream Phase 2 / N upstream Phase 1 / N cross-cutting] |
| Resulting toolkit versions | [Phase 6 v1.x / Phase 5 v1.x / Phase 4 v1.x / Phase 3 v1.x / Phase 2 v1.x / Phase 1 v1.x] |

#### Cluster-by-cluster decisions

| Cluster | Observations | Scope | Decision | Routing |
|---------|--------------|-------|----------|---------|
| | | | | |

---

## §3 — Revision Outcomes

*Populated as v1.x revisions land.*

### §3.1 — Phase 6 Toolkit v1.x

| File | Changes | Cluster(s) Driving Change |
|------|---------|--------------------------|
| | | |

### §3.2 — Upstream Routings That Landed

| Upstream Toolkit | Cluster Routed | Resulting Revision |
|-----------------|---------------|-------------------|
| | | |

---

## §4 — Observation Calibration Notes

*Populated when meta-observations about the Phase 6 dogfooding process
itself surface — distinct from observations about the toolkit content.*

Calibration history across the track: Phase 1's first dogfood produced
26 observations; Phase 2's produced 7; Phase 3's produced 14 across 8
clusters; Phase 4's and Phase 5's are pending. Phase 6 introduces
several v1.0-original disciplines that have not been dogfooded (the
three-way scope allocation, instrument distribution and execution
accounting, per-audit independence plans, the no-fixes-in-audit rule,
the measured-baseline comparison) — a reasonable expected range: 8–16
observations for the first Phase 6 dogfood. 

---

## Version History

| Version | Date | Source | Summary |
|---------|------|--------|---------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Phase 6 dogfooding-observations.md template. Empty observation log, end-of-phase three-pass review protocol (cluster, decide, revise), revision outcome tracking, observation calibration notes. Discipline inherited from Phase 1 v1.3 / Phase 2 v1.1 / Phase 3 v1.1 / Phase 4 v1.0. Ready for the first Phase 6 dogfooding cycle. |

---

*Part of the Phase 6 (Existing Projects) Implementation Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `testing-audit.existing-project.instructions.md`*
*Living document — append observations during Phase 6 runs; act on them at end-of-phase*
