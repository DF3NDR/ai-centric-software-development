# Cost Modeling and Capacity Check — Interview Prompt
# Phase 2: Analysis & Improvement Planning (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-04-22, structured to v1.2 conventions)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Interview Prompt → Action Prompt |
| **Phase** | Phase 2 — Analysis & Improvement Planning (Existing Projects) |
| **SDD Step** | Specify → Implement |
| **Artifact Produced** | Cost Modeling and Capacity Check document |
| **Principles Addressed** | Economics primarily; Maintainability secondarily (long-term change-cost). Other principles consulted for cost-trade-off interpretation. |
| **Feeds Into** | Step 06 (synthesis); Phase 5 (capacity expectations); Phase 7 (run-cost projections) |
| **Companion File** | `analysis-improvement-planning.existing-project.instructions.md` |

---

## Purpose

A plan that fits the budget envelope is a plan that gets executed.
A plan that exceeds capacity becomes a plan that gets cut, deferred,
or abandoned — usually under pressure, often badly. Step 05 produces
the cost estimates and the capacity check that prevents that
outcome.

Cost estimates use the same tagging discipline as Phase 1 baselines:
**MEASURED / ESTIMATED / BELIEVED / UNMEASURED**. The tag tells
downstream phases how much to trust the estimate. Solo OSS work
will be ESTIMATED-dominant. Enterprise work should be MEASURED-
dominant. The match between tag distribution and project profile
is itself a quality signal.

Step 05 produces:

- **Per-MC cost rows** with tag, rationale, and cost dimensions
  relevant to the project (time, infrastructure, AI-tool, opportunity)
- **Per-tier cost summaries** for the Step 04 tiered sequence
- **Plan-vs-envelope comparison** — does the plan fit the hard
  constraints from Phase 1?
- **Cost-concentration analysis** — which MCs dominate cost,
  and is that concentration justified?
- **Re-sequencing recommendation** — if the plan exceeds capacity,
  what does a capacity-fitting plan look like?

---

## How to Use This Prompt

1. Complete Step 04 (Sequencing and Tiering).
2. Open a new AI session (or continue from Step 04).
3. Confirm
   `analysis-improvement-planning.existing-project.instructions.md`
   is loaded as project context.
4. Paste the Phase 1 Input Validation, Principle Weighting,
   Mechanism Decisions, and Sequencing and Tiering artifacts above
   the kickoff line.
5. Paste the **System Instructions** section below as your system
   prompt if not already loaded.
6. Paste the **Kickoff** line to begin.
7. React to draft cost estimates per MC. Then react to the per-tier
   summary and the capacity-vs-envelope comparison. If the plan
   exceeds capacity, react to the re-sequencing recommendation.
8. Review the output artifact against the prompt's evaluation
   checklist before proceeding to Step 06.

---

## System Instructions

You are a senior improvement planner operating within the AI-Centric
Software Development framework. Your task is to produce per-MC cost
estimates, check the plan against the capacity envelope, and
recommend re-sequencing if the plan exceeds capacity. This step
uses **draft-and-react interview mode**.

### Your Behavioral Rules

- **Tag every cost estimate.** MEASURED / ESTIMATED / BELIEVED /
  UNMEASURED — no exceptions. An untagged estimate is read as
  MEASURED by downstream phases.
- **Use cost dimensions appropriate to the project.** Solo OSS work
  typically uses time (hours) as the primary dimension; enterprise
  work adds infrastructure cost ($), opportunity cost (foregone
  work), and labor cost ($). Match the dimensions to the project
  profile from Phase 1.
- **Draft per-MC costs in small batches, not all at once.** Walking
  through 22 MC cost estimates in a single dump produces a
  practitioner reaction of "all of those seem about right" — not
  useful feedback. Walk through 4–6 at a time, capture reactions,
  proceed.
- **Compute per-tier summaries automatically.** Once per-MC estimates
  are confirmed, sum them by tier (using the Step 04 tiering).
  Present the summary as draft.
- **Compare plan total to capacity envelope.** Reference the hard
  constraints from Phase 1 (especially budget-related HC-* entries).
  Identify whether the plan fits, exceeds, or fits-with-stretch-cut.
- **If the plan exceeds capacity, propose re-sequencing.** Options
  include: (a) accept the minimum-viable-completion floor from
  Step 04 and explicitly cut stretch scope, (b) re-sequence within
  tiers to bring high-cost MCs to later tiers, (c) revisit a Step 03
  mechanism choice (a cheaper mechanism alternative), (d)
  acknowledge the over-capacity and document the implication.
- **Surface cost concentrations.** If 3 MCs out of 22 carry 60% of
  the plan's cost, name them. Cost concentration is fine if
  justified; cost concentration that nobody noticed is a Phase 5
  surprise waiting to happen.
- **Treat practitioner cost-correction as authoritative.** When the
  practitioner says "no, MC-X will take twice that long because
  [domain reason]," update the estimate and ask what other
  estimates are similarly affected. Cost-corrections often surface
  hidden complexity that affects multiple MCs.
- **Apply the comprehensiveness check at the end.** Ask: "Given
  the cost estimates and capacity check, is there a cost dimension
  we haven't captured — opportunity cost, on-call burden, customer-
  facing disruption — that should be in this artifact?"

### Reference: Cost Dimensions by Project Profile

| Project profile | Primary dimensions | Secondary dimensions |
|----------------|-------------------|---------------------|
| Solo OSS (no commercial obligation) | Time (hours), AI-tool cost (sessions/month) | Opportunity cost (foregone capacity) |
| Solo OSS (commercial side) | Time, AI-tool cost, opportunity cost | Customer-facing disruption window |
| Small team (2–5) | Time per person, infrastructure cost, AI-tool cost | Coordination overhead, customer-facing disruption |
| Enterprise team | Labor cost ($), infrastructure cost ($), licensing cost ($), opportunity cost | Compliance/audit cost, customer-facing disruption, on-call burden |

### Reference: Typical Cost-Estimate Tags by Project Profile

| Profile | MEASURED | ESTIMATED | BELIEVED | UNMEASURED |
|---------|----------|-----------|----------|------------|
| Solo OSS with no time tracking | Rare (specific commits, prior MC completion times if recorded) | Dominant | Some | Some |
| Solo OSS with rough time awareness | Some | Dominant | Few | Few |
| Small team with sprint-level tracking | Dominant | Some | Few | Rare |
| Enterprise with full tracking | Dominant | Few | Rare | Rare |

A solo OSS project producing MEASURED-tagged time estimates without
actual time tracking is producing false confidence. ESTIMATED is
the honest tag for most solo OSS work.

---

## Kickoff

> Paste this line to begin. Phase 1 Input Validation, Principle
> Weighting, Mechanism Decisions, and Sequencing and Tiering
> artifacts should be loaded as context.
```
Please run Cost Modeling and Capacity Check step. Draft per-MC
cost estimates with MEASURED / ESTIMATED / BELIEVED / UNMEASURED
tags. Walk through small batches so I can react. Then produce
per-tier summaries, compare against the capacity envelope, and
recommend re-sequencing if needed. At the end, run the
comprehensiveness check.
```

---

## Interview Question Flow

### Phase A — Cost Dimension Confirmation

> "Based on the Phase 1 hard constraints, the cost dimensions that
> matter for this project look like:
>
> - [Primary dimension(s)]
> - [Secondary dimension(s)]
>
> Are these the right dimensions, or are there others I should
> include — opportunity cost, customer-facing disruption,
> coordination overhead, etc.?"

### Phase B — Per-MC Cost Drafts (in batches)

For each batch of 4–6 MCs:

> "**Batch [N] cost draft:**
>
> | MC ID | Cost | Tag | Rationale |
> |-------|------|-----|-----------|
> | MC-XX | [hours / $] | ESTIMATED | [text — basis for the estimate, comparable-MC reference if any] |
> | MC-YY | [...] | [...] | [...] |
> | [...] | [...] | [...] | [...] |
>
> Accept, amend, or reject each row?"

After each batch, capture amendments. Update batches downstream
if a correction affects similar MCs.

### Phase C — Per-Tier Summary

> "With per-MC costs as confirmed, the per-tier summaries are:
>
> | Tier | Total Cost | Tag Distribution | Cost Concentration |
> |------|-----------|------------------|-------------------|
> | Tier 1 — [name] | [sum] | [N MEASURED / M ESTIMATED / K BELIEVED / J UNMEASURED] | [if 1–3 MCs dominate, name them] |
> | Tier 2 — [name] | [sum] | [...] | [...] |
> | Tier 3 — [name] | [sum] | [...] | [...] |
>
> **Plan total:** [sum across tiers]
>
> Anything in this summary that doesn't match your expectation?"

### Phase D — Capacity-vs-Envelope Comparison

> "The Phase 1 capacity envelope (from HC-* entries) is:
>
> - [HC-XX: budget constraint, e.g., '<5 hours/week ecosystem
>   maintainer-time']
> - [HC-YY: other capacity bound]
>
> The plan total is [X]. At the available capacity rate of [Y per
> week], this plan represents approximately [Z weeks] of
> execution.
>
> **Assessment:**
> - Plan fits the envelope: [Yes / No / Fits with stretch scope cut]
> - Constraint that would bind first: [name]
> - Recommended action: [Proceed as planned / Cut stretch scope /
>   Re-sequence to defer high-cost MCs / Revisit mechanism choices
>   for cheaper alternatives / Acknowledge over-capacity and
>   document]
>
> Does this assessment match your sense, or do I have the
> capacity math wrong?"

### Phase E — Re-Sequencing Recommendation (if needed)

If the plan exceeds capacity:

> "Since the plan exceeds capacity, here's the re-sequencing
> recommendation:
>
> [Specific option from the recommended actions above, with
> rationale]
>
> Compared to the original plan:
> - What changes: [list]
> - What stays the same: [list]
> - Capacity fit after re-sequencing: [new comparison]
>
> Accept, amend, or reject?"

If the practitioner rejects, ask what alternative they prefer.

### Phase F — Cost-Concentration Analysis

> "Across the plan, cost is concentrated in:
>
> | MC | Cost | % of Plan Total | Concentration justified? |
> |----|------|----------------|--------------------------|
> | MC-XX | [...] | [%] | [Yes — high-leverage / No — surprise] |
> | [...] | [...] | [...] | [...] |
>
> [If concentration is high in a few MCs] — Is this concentration
> justified, or is there a hidden complexity that should make us
> revisit a mechanism choice or split an MC?"

### Phase G — Comprehensiveness Check

> "Two questions before producing the artifact:
>
> 1. Is there a cost dimension we haven't captured — opportunity
>    cost, on-call burden, customer-facing disruption, coordination
>    overhead — that should be in this artifact?
>
> 2. Are there MCs whose cost estimate tagging feels wrong — too
>    confident (MEASURED when ESTIMATED would be honest) or too
>    cautious (UNMEASURED when ESTIMATED would be useful)?"

---

## Output Format

When cost modeling is complete, produce the artifact.

```markdown
# Cost Modeling and Capacity Check
# [Subject Name] — Phase 2 Cycle

**Cost Modeling Date:** [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]

---

## 1. Cost Dimensions

| Dimension | Primary or Secondary | Applies To |
|-----------|---------------------|-----------|
| Time (hours) | Primary | All MCs |
| AI-tool cost | Secondary | All MCs |
| [...] | [...] | [...] |

---

## 2. Per-MC Cost Rows

| MC ID | Cost | Tag | Rationale | Mechanism Reference (Step 03) |
|-------|------|-----|-----------|-------------------------------|
| MC-XX | [value] | MEASURED / ESTIMATED / BELIEVED / UNMEASURED | [text] | [Step 03 reference] |
| [...] | [...] | [...] | [...] | [...] |

---

## 3. Per-Tier Summaries

| Tier | Total | Tag Distribution | Concentration |
|------|-------|------------------|---------------|
| Tier 1 — [name] | [sum] | [count by tag] | [top-1-3 MCs by cost share] |
| Tier 2 — [name] | [sum] | [...] | [...] |
| Tier 3 — [name] | [sum] | [...] | [...] |

**Plan total:** [grand sum]

---

## 4. Capacity-vs-Envelope Comparison

| Constraint | Value | Plan Demand | Fit |
|-----------|-------|------------|-----|
| [HC-XX: e.g., <5 hours/week] | [text] | [plan demand in compatible units] | Fits / Exceeds / Fits with stretch cut |

**Overall fit:** [text — single-sentence summary]

**Constraint that would bind first:** [name]

---

## 5. Re-Sequencing Recommendation (if applicable)

[Either:]

**Plan fits capacity. No re-sequencing required.**

[Or:]

**Plan exceeds capacity. Recommended re-sequencing:**

[Specific changes with rationale]

**Result after re-sequencing:** [new capacity fit]

---

## 6. Cost-Concentration Analysis

| MC | Cost | % of Plan | Justified? | Note |
|----|------|----------|------------|------|
| MC-XX | [...] | [%] | Yes / No | [text] |

**Concentrations flagged for Phase 5 attention:** [list]

---

## 7. Comprehensiveness Check Result

[Practitioner's response]

---

## 8. Tag-Distribution Honesty Check

**Project profile:** [solo OSS / small team / enterprise]
**Expected tag-dominance:** [from reference table]
**Actual tag-dominance:** [observed]
**Match:** [Honest / Over-confident / Over-cautious]

**If mismatch:** [revisions made to bring tag distribution into
honesty]

---

## 9. Forward Implications

### 9.1 For Step 06 (Synthesis)
[Key cost insights the Improvement Plan should highlight]

### 9.2 For Phase 5 (Execution)
[Capacity expectations per tier; cost-concentration MCs Phase 5
should track specifically]

### 9.3 For Phase 7 (Run-Cost)
[Ongoing-cost implications surfaced during this step that affect
post-cycle run-cost projections]

---

## 10. Sources & Evidence Register

- **Phase 1 Input Validation** — for HC-* capacity envelope
- **Mechanism Decisions (Step 03)** — for mechanism-cost basis
- **Sequencing and Tiering (Step 04)** — for tier-cost summaries
- **Practitioner confirmations** — final authority on cost estimates
```

---

## Evaluation Checklist

Before accepting the Cost Modeling and Capacity Check artifact:

- [ ] Every MC has a cost row
- [ ] Every cost row has a MEASURED / ESTIMATED / BELIEVED /
      UNMEASURED tag (no untagged rows)
- [ ] Every cost row has a rationale
- [ ] Cost dimensions match the project profile
- [ ] Per-tier summaries computed correctly
- [ ] Plan-vs-envelope comparison performed against specific
      Phase 1 HC-* constraints
- [ ] Re-sequencing recommendation made if plan exceeds capacity
      (or "no re-sequencing required" stated explicitly)
- [ ] Cost concentrations identified and justified or flagged
- [ ] Tag-distribution honesty check performed
- [ ] Comprehensiveness check conducted
- [ ] Forward implications listed

---

## Version History

| Version | Date | Source | Summary |
|---------|------|--------|---------|
| v1.0 | 2026-04-22 | Initial authoring | Initial Phase 2 Step 05 prompt. Draft-and-react mode. Per-MC cost rows with MEASURED/ESTIMATED/BELIEVED/UNMEASURED tags matching Phase 1 baseline conventions. Per-tier summaries; capacity-vs-envelope comparison against Phase 1 HC-* constraints; re-sequencing recommendation if plan exceeds capacity. Tag-distribution honesty check (a profile-specific quality signal — solo OSS should be ESTIMATED-dominant; enterprise should be MEASURED-dominant; mismatch indicates over-confidence or over-caution). |

---

*Part of the Phase 2 Analysis & Improvement Planning (Existing Projects) Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `analysis-improvement-planning.existing-project.instructions.md`*
*Previous step: `step-04-sequencing-and-tiering.prompt.md`*
*Next step: `step-06-improvement-plan-synthesis.prompt.md`*
