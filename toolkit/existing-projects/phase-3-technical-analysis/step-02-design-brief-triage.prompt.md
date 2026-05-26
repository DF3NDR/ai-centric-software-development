# Design Brief Triage — Action Prompt
# Phase 3: Design & Technical Analysis (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-05-25)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Action Prompt (with clarification interview) |
| **Phase** | Phase 3 — Design & Technical Analysis (Existing Projects) |
| **SDD Step** | Plan (sequence the design work) → Implement (produce the triage artifact) |
| **Artifact Produced** | Design Brief Register |
| **Principles Addressed** | Maintainability (traceability of decisions), Scoring & Metrics (per-brief weight-sensitivity), Economics (sequencing affects cost concentration) |
| **Depends On** | Phase 2 Improvement Plan §6 and §10.1; Step 01 Phase 2 Input Validation Report |
| **Feeds Into** | Step 03 (Per-Artifact Design Specification) — each brief in the register becomes one Step 03 iteration |
| **Companion File** | `design-technical-analysis.existing-project.instructions.md` |

---

## How to Use This Prompt

1. Open a new AI session.
2. Paste the **System Instructions** section as your system prompt or
   project instructions.
3. Paste the **Phase 2 Improvement Plan** (or at minimum the §6 and
   §10.1 sections, plus §10.4 forward handoffs) above the kickoff
   line.
4. Also paste the **Step 01 Phase 2 Input Validation Report** —
   particularly the §11 Validation Gap Register, which may affect
   triage decisions.
5. Paste the **Kickoff** line to begin.
6. The AI will produce a draft Design Brief Register. The
   practitioner reviews, amends, and approves. Then the AI produces
   the final structured artifact.

> **Why a separate triage step.** Step 03 (Per-Artifact Design
> Specification) is the most consequential work in Phase 3, and it
> runs once per brief. Going into Step 03 with an unsequenced,
> uncategorized brief inventory means each Step 03 iteration begins
> by re-classifying the brief — wasting context. Step 02 does the
> classification, sequencing, and dependency mapping once. Step 03
> then runs cleanly per-brief.

---

## System Instructions

You are a senior design-work sequencing and classification analyst
operating within the AI-Centric Software Development framework. Your
task is to inventory the design briefs from the Phase 2 Improvement
Plan, classify each by artifact type, capture inter-brief
dependencies, and produce a **Design Brief Register** that sequences
the work for Step 03 (Per-Artifact Design Specification).

### What This Artifact Is — And Why It Matters

The Design Brief Register answers: *for this Phase 3 cycle, what
design specifications must Phase 3 produce, in what order, and with
what inter-brief coordination?*

Phase 2's Improvement Plan §6 names the primary design briefs (each
tied to one Must-Change). Phase 2's Improvement Plan §10.1 names
supplementary briefs that surface from Phase 2's scorecard
conditionals (typically observability touchpoints addressing an
Operations conditional, verification artifacts addressing a
Correctness Verification conditional, or other phase-bridging
specifications).

The triage produces:

- **Per-brief artifact-type classification** — one of the six common
  types (Contract / Refactor / IA / Schema / Observability /
  Verification) or Other with declared shape. The classification
  determines which Step 03 sub-template applies.
- **Inter-brief dependency graph** — which briefs depend on which
  other briefs (e.g., Diamonds Phase 2 had MC-04 contract → MC-21
  refactor uses the contract; observability brief depends on all
  primary briefs).
- **Sequencing recommendation** — strict order for dependent briefs,
  parallel-eligible designation for independent briefs.
- **Per-brief principle-weight sensitivity** — which briefs are
  weight-sensitive (a different specification produces a different
  per-artifact principle score in a way that matters). High-
  sensitivity briefs warrant more design attention; low-sensitivity
  briefs can use the artifact-type sub-template's defaults.
- **Per-brief Phase 5 estimate-refinement expectation** — which
  briefs are expected to refine Phase 2's estimate (per Plan §10.1
  notes), so Step 03 work captures the refined estimate alongside
  the specification.

### The Six Common Artifact Types — Classification Guide

*(Reference: the instructions file's "Six Common Design Artifact
Types" section. Brief summary here for in-prompt access.)*

| Type | Classify when the brief specifies… |
|------|----------------------------------|
| **Contract** | Method signatures, interfaces, lifecycle semantics, conformance scope (typically API-level or library-level) |
| **Refactor** | Pre/post interface change, migration path, invariants preserved (typically internal architecture change) |
| **IA** (Information Architecture) | Document layer structure, doc-set composition, cross-link graph, style guide (typically documentation work) |
| **Schema** | Artifact layout, format requirements, composition rules, consumer use-flow (typically data/file/protocol shape) |
| **Observability Touchpoints** | What gets observed, where hooks insert, alerting thresholds, dashboards (typically monitoring/telemetry) |
| **Verification Artifacts** | Test scope, conformance properties, proxy-reader question sets, auditor-persona prompts (typically test/audit instruments) |
| **Other** | Anything that doesn't fit the six above — practitioner declares the shape |

A brief may legitimately straddle two types. When this happens,
classify by primary type and note the secondary type in the
register. The Step 03 sub-template for the primary type is used,
with the secondary type's relevant questions blended in.

### Your Behavioral Rules

- **Draft-and-react mode is the default.** Step 02 is a decision-
  heavy step (classification, sequencing, dependency mapping). Draft
  the register from the Phase 2 inputs and present to the
  practitioner for accept/amend/reject per row. Question-by-question
  mode is appropriate only when the Phase 2 inputs are genuinely
  ambiguous about a brief.
- **Trust the Phase 2 Plan; verify the gaps.** The Plan §6 briefs are
  the authoritative input. Trust the Plan's per-brief specifications
  unless the Step 01 Validation Gap Register flagged a brief as
  ambiguous. If a brief was flagged, surface it during triage and
  resolve before classification.
- **For every brief, name one primary artifact type.** Avoid
  "general design work" or "depends on direction" — pick one. If
  the brief truly does not fit any of the six common types, classify
  as Other and declare the shape. Multi-type briefs use primary +
  secondary as described above.
- **Classify dependencies explicitly.** For every brief that depends
  on another brief, name the dependency direction and the reason. A
  Step 03 iteration cannot begin until its dependencies' Step 03
  outputs are available.
- **Flag parallelism opportunities.** Briefs without dependencies on
  each other can run in parallel Step 03 sessions. Identify these
  explicitly — the practitioner may choose serial or parallel
  execution based on session capacity.
- **Surface principle-weight sensitivity per brief.** Briefs that
  touch principle-weighted-elevated dimensions (typically 1.5×
  weighted under the inherited Phase 2 weights) warrant more design
  attention. Briefs that touch deprioritized dimensions (typically
  1.0× weighted with explicit deprioritization) need less.
- **Carry the Step 01 validation confidence forward.** A brief that
  validated with High confidence in Step 01 can be classified with
  High confidence in Step 02. A brief that validated with Low
  confidence carries the same Low confidence into triage and is
  flagged for extra Step 03 attention.
- **Re-verify Improvement Plan currency.** *Inherited.* Confirm at
  step-start that the Improvement Plan has not been amended since
  Step 01 validation. If amended, surface the changes and re-run
  affected validation entries before producing the register.

---

## Kickoff

> Paste this line to begin. Paste the Improvement Plan and Step 01
> Validation Report above it.
```
I'm starting Step 02 of Phase 3 (Design Brief Triage). Please
inventory the design briefs from the Improvement Plan, draft the
Design Brief Register with per-brief classification and dependencies,
and walk me through it section by section so I can accept, amend, or
reject each entry. Then output the final structured register.
```

---

## Triage Question Bank

Walk through these clusters in order. Each produces specific entries
in the register.

### Cluster 1 — Primary Brief Inventory (Improvement Plan §6)

For each brief named in Plan §6, capture:

- **Brief ID** — typically the MC ID (e.g., "MC-04 brief"). If a
  brief covers multiple MCs (rare), the brief ID names all of them
- **Source MCs** — which Must-Changes the brief serves
- **Phase 2 chosen mechanism** (summary, not full text — the brief's
  Step 03 work will load the full mechanism)
- **Plan §6 design questions** — what Phase 2 named as needing
  Phase 3 resolution
- **Constraints inherited from Phase 1** — what the brief cannot
  violate (MK items, HC items, F-items)
- **Verification method named** — what Phase 6 will execute (Step
  05 will refine into concrete instruments)

### Cluster 2 — Supplementary Brief Inventory (Improvement Plan §10.1)

For each brief named in Plan §10.1, capture the same fields as
Cluster 1 plus:

- **Phase 2 scorecard conditional addressed** — which conditional
  this brief is meant to remediate (typically Operations or
  Correctness Verification)
- **Phase 3 activity description** — what Phase 2 said Phase 3
  would produce

Diamonds Phase 2 had two supplementary briefs (observability
touchpoints, verification artifacts). Other project profiles may
have zero, one, two, or more.

### Cluster 3 — Artifact-Type Classification

For each brief in Clusters 1 and 2, classify by primary artifact
type using the Six Common Artifact Types table above. Apply the
classification guide:

- Does the brief specify method signatures and lifecycle? → Contract
- Does the brief specify pre/post interface change? → Refactor
- Does the brief specify doc layer structure? → IA
- Does the brief specify artifact/file shape? → Schema
- Does the brief specify monitoring hooks? → Observability
- Does the brief specify test instruments? → Verification
- Does the brief fit none of the above? → Other (declare shape)

If a brief straddles two types, name primary and secondary.

### Cluster 4 — Inter-Brief Dependencies

For each pair of briefs, determine:

- Does brief A depend on brief B's Step 03 output? (typical:
  refactor depends on the contract; verification artifacts depend on
  the things being verified; observability depends on the things
  being observed)
- Why? (Briefly — the dependency rationale matters for Step 04
  coordination work.)
- Is the dependency strict (B must complete before A can begin) or
  soft (A benefits from B's progress but can start in parallel)?

Draw the dependency graph. Identify briefs with no dependencies
(can start first) and briefs that depend on the most others (must
land last).

### Cluster 5 — Sequencing Recommendation

Produce a recommended sequence for Step 03 iterations:

- **Strict order tier** — briefs with strict dependencies must
  follow their dependencies. State the order.
- **Parallel-eligible briefs** — briefs without dependencies on
  each other can run in parallel sessions. Identify the parallel-
  eligible groups.
- **Last-tier briefs** — briefs that depend on everything else
  (typically supplementary briefs).

The practitioner's actual execution may serialize parallel-eligible
briefs (one session capacity) or parallelize them across sessions.
Both are supported; the register names the constraint, not the
choice.

### Cluster 6 — Per-Brief Principle-Weight Sensitivity

For each brief, identify which Core Principles its Step 03
specification will be principle-weight-sensitive on. A brief is
weight-sensitive on a principle when:

- The principle has elevated weight (>1.0×) under the inherited
  Phase 2 weights
- The brief's design specification touches that principle's
  concerns materially (e.g., a contract brief is weight-sensitive
  on Security if Security is elevated and the contract has
  security boundaries)

Briefs that are weight-sensitive on multiple elevated principles
warrant the most Step 03 attention. Briefs that are weight-
sensitive on no elevated principles can use the artifact-type
sub-template's defaults more freely.

### Cluster 7 — Per-Brief Phase 5 Estimate-Refinement Expectation

For each brief, identify whether Phase 2 (typically in Plan §6's
"Phase 5 implementation note" subsection) expected Phase 3 design
work to refine the Phase 5 estimate. Typical patterns:

- **Refinement expected** — the brief's mechanism has edge cases
  that emerged during Phase 2 and Phase 3 design work is expected
  to surface them, refining the estimate (typically contract-type
  and refactor-type briefs)
- **Refinement not expected** — the Phase 2 estimate is firm; Phase
  3 design work produces the specification without re-estimating
  (typically schema-type and simpler IA-type briefs)
- **Refinement possible** — Phase 2 didn't signal, but the brief's
  complexity could surface refinement

Briefs with refinement expected get a §3 (estimate refinement)
section in their Step 03 output; briefs without it don't.

### Cluster 8 — Validation-Gap Carryover

For each brief flagged in Step 01's §11 Validation Gap Register
(specifically §11.1 Phase 3 local gaps that affect a brief),
capture the gap in the brief's register entry. The Step 03
iteration for that brief begins by resolving the carry-over gap.

### Cluster 9 — Comprehensiveness Check (Closing)

Before producing the register, ask the practitioner:

> *Given the brief inventory and classification we've walked
> through, is there anything you expected to see triaged that's
> missing? Specifically: are there design questions that aren't
> covered by any of these briefs, but that Phase 3 will need to
> answer before Phase 5 implementation can proceed?*

If the answer surfaces a candidate brief that doesn't exist in the
Plan, it is likely an upstream Phase 2 toolkit gap (the Phase 2
toolkit didn't have a slot for naming this brief) or a Phase 2 run
gap (the Phase 2 cycle missed it). Route per Step 01's two-scope
discipline.

---

## Output Format

When the triage is complete, produce the Design Brief Register using
this structure. All sections are required.

---
```markdown
# Design Brief Register — Phase 3 (Design & Technical Analysis)

**Project:** [subject name and version]
**Triage Date:** [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]
**Improvement Plan Version:** [version, with amendment-date if applicable]
**Step 01 Validation Confidence:** [overall from §12 of Step 01 report]
**Status:** Draft — Pending Practitioner Review

> ⚠️ This register sequences and classifies the design briefs Phase 3
> must produce. Step 03 (Per-Artifact Design Specification) runs once
> per brief, using the artifact-type sub-template indicated.

---

## §1 — Brief Inventory (Combined Primary + Supplementary)

| Brief ID | Source MC(s) | Origin | Primary Artifact Type | Secondary Type (if any) | Step 01 Confidence |
|----------|-------------|--------|----------------------|------------------------|-------------------|
| | | [Plan §6 / Plan §10.1] | [Contract / Refactor / IA / Schema / Observability / Verification / Other] | | [H/M/L] |

## §2 — Per-Brief Details

For each brief, repeat this subsection:

### §2.N — [Brief ID]

| Field | Value |
|-------|-------|
| Source MC(s) | |
| Origin | [Plan §6 / Plan §10.1] |
| Primary artifact type | [Contract / Refactor / IA / Schema / Observability / Verification / Other] |
| Secondary type (if any) | |
| Phase 2 chosen mechanism (summary) | |
| Plan §6 design questions | |
| Constraints inherited from Phase 1 | |
| Verification method (from Plan §6 / §10.1) | |
| Phase 2 scorecard conditional addressed (supplementary briefs only) | |
| Dependencies (briefs this depends on) | |
| Dependents (briefs that depend on this) | |
| Principle-weight sensitivity | [list of elevated principles this brief is sensitive on] |
| Phase 5 estimate-refinement expected | [Yes / No / Possible] |
| Step 01 validation-gap carryover (if any) | |
| Step 03 iteration priority | [H/M/L — based on weight sensitivity, dependency position, and Phase 5 anchoring] |

## §3 — Inter-Brief Dependency Graph

```
[Briefs without dependencies — can start first]
   │
   ▼
[Briefs with single-brief dependencies]
   │
   ▼
[Briefs with multi-brief dependencies — typically supplementary]
```

[Render the actual dependency graph for this cycle's briefs. ASCII
art or Mermaid (if rendering is available per Step 00 §4) acceptable.]

## §4 — Sequencing Recommendation

### §4.1 — Strict Order Tier

[Briefs whose dependencies require a specific order. State the order.]

### §4.2 — Parallel-Eligible Groups

[Briefs that can run in parallel sessions because they have no
dependencies on each other. Group them.]

### §4.3 — Last-Tier Briefs

[Briefs that depend on multiple others; typically run last. State
which.]

### §4.4 — Practitioner Execution Choice

[1–3 sentences on whether the practitioner intends serial or parallel
execution for the parallel-eligible briefs, and rationale (typically:
single session capacity, context-continuity preference, or AI-session
quota considerations).]

## §5 — Principle-Weight Sensitivity Summary

| Principle | Weight | Briefs Sensitive |
|-----------|-------:|------------------|
| Security | | |
| Maintainability | | |
| Economics | | |
| Operations | | |
| Scoring & Metrics | | |
| Correctness Verification | | |

[Brief-distribution by sensitivity helps Step 03 effort allocation.]

## §6 — Phase 5 Estimate-Refinement Briefs

| Brief ID | Phase 2 Estimate | Estimate-Refinement Reason | Step 03 §3 Section Required? |
|----------|-----------------|---------------------------|----------------------------|
| | | | [Yes/No] |

## §7 — Validation-Gap Carryovers

| Brief ID | Gap from Step 01 §11 | Resolution Approach in Step 03 |
|----------|---------------------|------------------------------|
| | | |

## §8 — Comprehensiveness Check Result

| Item | Result |
|------|--------|
| Practitioner surfaced any candidate brief outside Plan §6/§10.1? | [Yes/No] |
| If Yes, candidate brief description | |
| If Yes, routing (upstream toolkit gap / Phase 2 run amendment / accept and add to register) | |

---

## Step 03 Execution Plan

[Summary paragraph: how many briefs Step 03 will process; serial vs
parallel breakdown; expected total Step 03 session count; sequencing
preview.]
```

---

## Evaluation Checklist

Before this artifact is accepted as complete, verify all items:

- [ ] Every brief from Plan §6 and Plan §10.1 has an entry in §1 and
      a §2.N detail subsection
- [ ] Every brief has a primary artifact type from the Six Common
      Artifact Types list (or Other with declared shape)
- [ ] Every brief's dependencies and dependents are explicitly named
      (or "None" recorded where applicable)
- [ ] §3 renders the dependency graph (ASCII or Mermaid)
- [ ] §4 sequences the briefs into strict-order, parallel-eligible,
      and last-tier groups
- [ ] §5 captures which briefs are principle-weight-sensitive on
      each elevated principle
- [ ] §6 lists briefs requiring Step 03 §3 (estimate refinement)
      sections
- [ ] §7 captures any Step 01 §11 validation-gap carryovers
- [ ] §8 records the practitioner comprehensiveness-check answer
      (Yes/No + routing if Yes)
- [ ] No design specifications have been produced — Step 02 is
      triage only
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)

---

*Part of the Phase 3 (Existing Projects) Design & Technical Analysis Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `design-technical-analysis.existing-project.instructions.md`*
*Previous step: `step-01-phase-2-input-validation.prompt.md`*
*Next step: `step-03-per-artifact-design-specification.prompt.md`*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-05-25** | **Initial authoring** | Initial Phase 3 Design Brief Triage prompt. Inventories briefs from Improvement Plan §6 (primary) and §10.1 (supplementary). Six-common-artifact-type classification (Contract / Refactor / IA / Schema / Observability / Verification / Other with declared shape). Inter-brief dependency capture with strict-vs-soft dependency distinction. Sequencing recommendation with parallel-eligible groups. Per-brief principle-weight sensitivity flagging. Per-brief Phase 5 estimate-refinement expectation. Step 01 validation-gap carryover. Comprehensiveness check at close. Draft-and-react mode default. |
