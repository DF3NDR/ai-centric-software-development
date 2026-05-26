# Phase 3 Dogfooding Observations (Existing Projects Toolkit)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-05-25; no dogfooding cycles complete yet)
**Status:** Template — populated during Phase 3 dogfooding cycles

---

## Purpose of This File

This file captures observations from real Phase 3 (Existing Projects)
runs that surface gaps, miscalibrations, or improvements in the
toolkit itself. It is a **living dogfood log** — entries accrete
during a Phase 3 run, are clustered and decided at end-of-phase, and
drive v1.x+ revisions of the toolkit files.

The discipline is inherited from Phase 1 v1.3 and Phase 2 v1.1.
Continuity matters; the protocol has been validated across two prior
toolkit cycles.

### What Goes in This File

Observations about the toolkit, captured during a Phase 3 run:

- A prompt's structure forced a workaround
- A behavioral rule produced unexpected resistance or unexpectedly
  smooth flow
- An interview pattern (question-by-question vs draft-and-react) felt
  miscalibrated for the work
- An output format produced confusion or was unexpectedly easy to
  consume in the next step
- An artifact-type sub-template (Step 03's seven sub-templates) felt
  over-fitted or under-fitted to a specific brief
- A cross-step handoff lost or duplicated information
- A Phase 2 → Phase 3 inheritance pattern felt miscalibrated

### What Does Not Go in This File

- Project-specific findings about the subject codebase — those go in
  the Phase 3 design artifacts themselves
- Phase 2 amendment items — those go in the Step 06 §7 Phase 2
  Amendment Package
- Upstream Phase 2 toolkit gaps — those go in Step 01 §11.2; they
  feed Phase 2 toolkit revision separately
- Observations about the framework as a whole (the Playbook) —
  those belong in framework-level review, not this toolkit-level log

---

## Observation Capture Protocol

Capture is **fast and incomplete by design**. Full analysis happens
at end-of-phase. The goal during the run is to record the
observation while it's fresh, not to analyze or act on it.

For each observation, capture:

- **Observation ID** — P3-Obs-NN (numbered sequentially within the
  dogfood cycle)
- **Surfaced during** — which step (00 through 06) and where in the
  step (cluster name, sub-template, etc.)
- **Subject project** — which project the Phase 3 cycle is being
  run against (typically Diamonds for v1.0 dogfood; future cycles
  may use different subjects)
- **Brief observation text** — 1-3 sentences describing what was
  noticed. Avoid premature analysis; the cluster-and-revise pass
  handles that.
- **Suggested handling (tentative)** — Phase 3 v1.x revision /
  upstream to Phase 2 / upstream to Phase 1 / accept as-is / defer.
  This is a working guess; the end-of-phase review confirms.

Observations are added to §1 as the run proceeds.

---

## End-of-Phase Review Protocol

After Step 06 synthesis completes (and any Phase 2 amendment cycle
resolves), run the three-pass review:

### Pass 1 — Cluster

Group observations that:
- Address the same gap
- Touch the same toolkit file
- Suggest the same kind of revision

Clusters typically range 4-8 observations per cluster for Phase 1
v1.1 / Phase 2 v1.1 calibration; Phase 3 v1.1 calibration is
unknown until the first dogfood completes.

### Pass 2 — Decide Per Cluster

For each cluster, decide:

- **Accept** — the gap is real and the revision is straightforward;
  v1.1 lands the change
- **Accept with refinement** — the gap is real but the proposed
  revision needs adjustment; v1.1 lands a refined version
- **Defer** — the gap is real but the revision is not yet shape-
  clear; queue for v1.2+
- **Reject** — the gap is not actually a gap (the original toolkit
  was right; the observation was a misread)

Also route per cluster:

- **Phase 3 v1.x revision** — landed in this toolkit
- **Upstream to Phase 2** — gap is in the Phase 2 toolkit, not Phase
  3; route to Phase 2 v1.x revision (this is the Phase 3 → Phase 2
  Channel 1 firing)
- **Upstream to Phase 1** — gap is in the Phase 1 toolkit; route to
  Phase 1 v1.x revision (the Phase 2 dogfood did this with Cluster
  B → Phase 1 v1.3)
- **Cross-cutting (framework level)** — gap is in the framework's
  conceptual structure, not any specific toolkit; route to framework
  documentation review

### Pass 3 — Revise

Produce the v1.x files in a focused authoring session. Each revised
file gets a Version History row documenting what changed and citing
the observation cluster(s) that motivated the change.

---

## §1 — Observation Log

| ID | Surfaced In | Subject | Observation | Suggested Handling (Tentative) |
|----|------------|---------|-------------|-------------------------------|
| | | | | |

*Observations are appended here during Phase 3 runs. No entries yet —
toolkit at v1.0 with no dogfooding cycles complete.*

---

## §2 — End-of-Phase Reviews

*Populated after each Phase 3 dogfooding cycle's end-of-phase review.*

### §2.1 — [Subject Project] Phase 3 Dogfood

*Placeholder — populated when the first Phase 3 cycle completes.*

| Field | Value |
|-------|-------|
| Subject project | |
| Phase 3 cycle dates | |
| Observation count | |
| Cluster count | |
| Clusters routing breakdown | [N Phase 3 v1.x / N upstream Phase 2 / N upstream Phase 1 / N cross-cutting] |
| Resulting toolkit versions | [Phase 3 v1.x / Phase 2 v1.x / Phase 1 v1.x] |

#### Cluster-by-cluster decisions

| Cluster | Observations | Scope | Decision | Routing |
|---------|--------------|-------|----------|---------|
| | | | | |

---

## §3 — Revision Outcomes

*Populated as v1.x revisions land.*

### §3.1 — Phase 3 Toolkit v1.x

*Placeholder — populated when v1.1 is authored.*

| File | Changes | Cluster(s) Driving Change |
|------|---------|--------------------------|
| | | |

### §3.2 — Upstream Routings That Landed

*Placeholder — populated if any cluster routed upstream produces a
landed revision in the upstream toolkit.*

| Upstream Toolkit | Cluster Routed | Resulting Revision |
|-----------------|---------------|-------------------|
| | | |

---

## §4 — Observation Calibration Notes

*Populated when meta-observations about the Phase 3 dogfooding
process itself surface — distinct from observations about the
toolkit content.*

For Phase 1 dogfooding, the calibration produced "26 observations
across the cycle; ~3-4 actionable per hour." For Phase 2
dogfooding, the calibration was "7 observations; ~1 actionable per
hour; under-range count explained by inheriting Phase 1 v1.2
disciplines." The Phase 3 calibration range is unknown until the
first dogfood completes.

Considerations for future Phase 3 calibration:
- Phase 3 v1.0 inherits substantially from Phase 1 v1.3 and Phase 2
  v1.1, suggesting an observation count closer to Phase 2's 7 than
  to Phase 1's 26
- However, Phase 3 introduces several v1.0-original concepts (six
  artifact types, two feedback channels, principle scorecard
  inheritance vs baselining) that have not been dogfooded
- The first Phase 3 dogfood is expected to stress these v1.0-
  original concepts; observation count could go higher than Phase
  2's
- A reasonable expected range: 8-15 observations for the first
  Phase 3 dogfood, with subsequent dogfoods on different project
  profiles producing different counts

---

## Version History

| Version | Date | Source | Summary |
|---------|------|--------|---------|
| **v1.0** | **2026-05-25** | **Initial authoring** | Initial Phase 3 dogfooding-observations.md template. Empty observation log, end-of-phase review protocol (three-pass: cluster, decide, revise), revision outcome tracking, observation calibration notes. Discipline inherited from Phase 1 v1.3 and Phase 2 v1.1. Ready for first Phase 3 dogfooding cycle (Diamonds Phase 3 application). |

---

*Part of the Phase 3 (Existing Projects) Design & Technical Analysis Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `design-technical-analysis.existing-project.instructions.md`*
*Living document — append observations during Phase 3 runs; act on them at end-of-phase*
