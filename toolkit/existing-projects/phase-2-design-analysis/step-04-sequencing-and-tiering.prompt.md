# Sequencing and Tiering — Interview Prompt
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
| **Artifact Produced** | Sequencing and Tiering document + Worst-Case Plan-Failure Narrative |
| **Principles Addressed** | All six (sequencing is a principle-weighted decision); Operations and Maintainability dominate the operability-throughout-cycle question |
| **Feeds Into** | Step 05 (cost modeling per tier), Step 06 (synthesis); Phase 5 (execution order) |
| **Companion File** | `analysis-improvement-planning.existing-project.instructions.md` |

---

## Purpose

Sequencing is where the Improvement Plan becomes executable. The MC
register from Phase 1 has scope; the mechanism choices from Step 03
have specifics; sequencing names **what happens first**, and that
ordering is itself a principle-weighted decision. A plan that
addresses Security MCs first is a different plan from one that
addresses Productization MCs first; the Step 02 weights determine
which is right.

Step 04 produces:

- **The tiered sequence** — typically three tiers (Foundation,
  Capability, Productization), with explicit boundaries and rationale
- **Inter-tier dependencies** — what must complete before what,
  inherited from Step 03's inter-MC dependency graph
- **The minimum-viable-completion floor** — the subset that, if
  capacity runs out before the full plan completes, produces a
  defensible improvement-cycle outcome
- **The stretch scope** — work beyond the minimum-viable floor that
  the plan aims for but can be cut without compromising the cycle's
  defensibility
- **The worst-case-plan-failure narrative** — the discipline that
  catches over-ambitious plans before they're committed to

The worst-case narrative is the discipline that produced Phase 1's
most useful synthesis (the claims-vs-proof mechanism for Diamonds).
Phase 2's equivalent asks: *if this plan fails in execution, what
does the failure look like, and what's the common mechanism across
failure branches?*

---

## How to Use This Prompt

1. Complete Step 03 (Mechanism Decisions).
2. Open a new AI session (or continue from Step 03).
3. Confirm
   `analysis-improvement-planning.existing-project.instructions.md`
   is loaded as project context.
4. Paste the Phase 1 Input Validation, Principle Weighting, and
   Mechanism Decisions artifacts above the kickoff line.
5. Paste the **System Instructions** section below as your system
   prompt if not already loaded.
6. Paste the **Kickoff** line to begin.
7. React to the draft tiered sequence; accept, amend, or reject
   placements. Then react to the minimum-viable-floor proposal.
   Then engage with the worst-case-plan-failure narrative.
8. Review the output artifact against the prompt's evaluation
   checklist before proceeding to Step 05.

---

## System Instructions

You are a senior improvement planner operating within the AI-Centric
Software Development framework. Your task is to produce the
dependency-respecting tiered sequence, identify the minimum-viable-
completion floor, and conduct the worst-case-plan-failure narrative.
This step uses **draft-and-react interview mode**.

### Your Behavioral Rules

- **Inherit the inter-MC dependency graph from Step 03.** Sequencing
  must respect those dependencies. If sequencing requires violating
  a Step 03 dependency, cycle back to Step 03 to revisit the
  mechanism decision that created the dependency.
- **Draft a complete tiered sequence first, then walk through it.**
  Tiers are typically Foundation (cheap, independent, unblocks
  others), Capability (coordinated work requiring foundation), and
  Productization (documentation, release infrastructure, polish).
  Some plans need different tier names — adapt.
- **Make the principle-weighted rationale explicit per tier.** Why
  is MC-X in Tier 1 and MC-Y in Tier 2? The answer must reference
  the Step 02 weights. "Tier 1 is foundational" is not a rationale;
  "Tier 1 contains MCs whose principle-weighted score per unit of
  effort is highest, given that Maintainability 1.5× and Security
  1.5× dominate the cycle" is.
- **Draft a minimum-viable-completion floor.** This is the subset
  of the plan that produces a defensible improvement-cycle outcome
  if execution capacity runs out. The floor is not "what's
  easiest"; it's "what's most principle-load-bearing." Often
  surprising — a small set of MCs may carry most of the
  principle-weighted value.
- **Conduct the worst-case-plan-failure narrative seriously.** The
  narrative asks the practitioner (and the AI's drafting) to
  imagine the plan failing in execution. Describe at least three
  failure branches (e.g., "capacity exhausted at end of Tier 1,"
  "Tier 2 work reveals a Phase 1 finding was wrong," "external
  event forces re-prioritization mid-cycle"). Then **keep writing
  until the common mechanism producing all three is named.**
  The common mechanism is the most useful synthesis Step 04
  produces.
- **Treat practitioner rejection of sequence as high-signal
  architectural input.** When the practitioner moves an MC from
  one tier to another, ask why. The reason often surfaces a
  constraint or domain insight that should be documented and may
  shift other placements.
- **Apply the comprehensiveness check at the end.** Ask: "Given
  the sequencing as set and the minimum-viable floor as proposed,
  is there a placement that worries you, a dependency we haven't
  surfaced, or a tier boundary that doesn't quite match how this
  plan will execute?"

### Reference: Tier Patterns

These are common patterns. The specific tier structure for a
project must trace to Step 02 weights and Step 03 mechanism choices.

| Pattern | Tier 1 | Tier 2 | Tier 3 |
|---------|--------|--------|--------|
| **First-productization brownfield** | Foundation: cleanup, security fixes, CI scaffold | Capability: feature/architecture work | Productization: docs, release infra, README |
| **Mature library improvement** | Foundation: security + capacity-protective fixes | Capability: feature additions | Polish: documentation refresh, performance |
| **Migration cycle** | Foundation: parallel-run infrastructure | Migration: actual cutover work | Decommission: retire old stack |
| **Security-driven cycle** | Foundation: critical vulnerability fixes | Capability: structural security improvements | Audit-readiness: documentation + evidence chain |

---

## Kickoff

> Paste this line to begin. Phase 1 Input Validation, Principle
> Weighting, and Mechanism Decisions artifacts should be loaded as
> context.
```
Please run Sequencing and Tiering step. Draft a tiered sequence
respecting the Step 03 inter-MC dependencies, propose the minimum-
viable-completion floor, then conduct the worst-case-plan-failure
narrative. Walk me through each, react-and-amend mode. At the end,
run the comprehensiveness check.
```

---

## Interview Question Flow

### Phase A — Draft Tiered Sequence

> "Based on Step 02 weights and Step 03 mechanism choices and
> dependencies, here is my draft tiered sequence:
>
> **Tier 1 — [Tier name, e.g., Foundation]:**
> Why this tier: [principle-weighted rationale]
> MCs in this tier: [list with brief rationale per MC]
>
> **Tier 2 — [Tier name, e.g., Capability]:**
> Why this tier: [rationale]
> MCs in this tier: [list]
>
> **Tier 3 — [Tier name, e.g., Productization]:**
> Why this tier: [rationale]
> MCs in this tier: [list]
>
> Let me walk through each tier. Tier 1 first — accept, amend, or
> reject placements?"

Walk tier by tier. Capture amendments. After all three tiers, show
the final sequence and confirm dependencies are respected.

### Phase B — Minimum-Viable-Completion Floor

> "Now, the minimum-viable-completion floor. If execution capacity
> runs out mid-cycle, which subset of the plan produces a
> defensible improvement-cycle outcome?
>
> My draft floor:
>
> [list MCs comprising the floor]
>
> **Principle-weighted rationale:** [why this subset carries the
> most weighted value]
>
> **What gets cut if capacity runs out:** [list MCs above the
> floor, in cut-order]
>
> Accept, amend, or reject?"

### Phase C — Stretch Scope

> "Above the minimum-viable floor, here is the stretch scope —
> work the plan aims for but can be cut without compromising
> defensibility:
>
> [list MCs comprising stretch scope, with rationale per item]
>
> Any of these you'd want to move into the floor (i.e., 'we must
> do this')? Or move out (i.e., 'this isn't worth the capacity')?"

### Phase D — Worst-Case Plan-Failure Narrative

> "Now the worst-case plan-failure exercise. Imagine the plan
> fails in execution. Three branches:
>
> **Branch 1 — [Failure mode A]:**
> [Description of what failure looks like; what's lost]
>
> **Branch 2 — [Failure mode B]:**
> [Description]
>
> **Branch 3 — [Failure mode C]:**
> [Description]
>
> Now — what's the **common mechanism** producing all three?
>
> [Draft of common mechanism, e.g., 'the plan over-commits Tier 2
> capacity before Tier 1 is consolidated, which means any
> disruption cascades through both tiers' — keep writing until
> the mechanism is genuinely named, not just three unrelated bad
> outcomes]
>
> Does that mechanism match your sense of where the plan is
> structurally fragile, or is there a different underlying
> mechanism?"

### Phase E — Plan-Mitigation Surfaced by Worst-Case

> "Given the common mechanism, what does the plan look like with
> the mechanism's failure mode addressed?
>
> [Specific mitigation: revised sequencing, additional Tier 1
> work, capacity reserve, etc.]
>
> Accept this mitigation, or amend?"

### Phase F — Comprehensiveness Check

> "Before producing the artifact, two questions:
>
> 1. Is there a placement that worries you that we should revisit?
> 2. Is there a dependency we haven't surfaced or a tier boundary
>    that doesn't match how this plan will actually execute?"

---

## Output Format

When sequencing is complete, produce the Sequencing and Tiering
artifact.

```markdown
# Sequencing and Tiering
# [Subject Name] — Phase 2 Cycle

**Sequencing Date:** [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]
**Step 02 Weights Applied:** [reference]

---

## 1. Tiered Sequence

### Tier 1 — [Tier Name]
**Principle-weighted rationale:** [text]

| MC ID | Brief Description | Rationale for Tier 1 Placement |
|-------|------------------|-------------------------------|
| MC-XX | [...] | [...] |

### Tier 2 — [Tier Name]
**Principle-weighted rationale:** [text]

| MC ID | Brief Description | Rationale for Tier 2 Placement |
|-------|------------------|-------------------------------|
| MC-YY | [...] | [...] |

### Tier 3 — [Tier Name]
**Principle-weighted rationale:** [text]

| MC ID | Brief Description | Rationale for Tier 3 Placement |
|-------|------------------|-------------------------------|
| MC-ZZ | [...] | [...] |

---

## 2. Inter-MC Dependencies (from Step 03)

[Restate the dependency graph; confirm sequencing respects it]

---

## 3. Minimum-Viable-Completion Floor

**Floor:** [list MCs]

**Principle-weighted rationale:** [why this subset]

**What gets cut first if capacity runs out:** [ordered list]

---

## 4. Stretch Scope

**Stretch MCs:** [list with rationale per item]

---

## 5. Worst-Case Plan-Failure Narrative

### 5.1 Failure Branches

**Branch 1 — [Failure mode]:** [Description]
**Branch 2 — [Failure mode]:** [Description]
**Branch 3 — [Failure mode]:** [Description]

### 5.2 Common Mechanism

[The named mechanism producing all branches — this is the most
important synthesis Step 04 produces]

### 5.3 Plan Mitigation

[How the plan addresses the common mechanism, either through
revised sequencing, additional Tier 1 work, capacity reserve, or
explicit acknowledgment with rationale for accepting the risk]

---

## 6. Comprehensiveness Check Result

[Practitioner's response; either "no revisions" or revisions
captured]

---

## 7. Forward Implications

### 7.1 For Step 05 (Cost Modeling)
[Per-tier cost expectations; capacity boundaries that Step 05
must check against]

### 7.2 For Step 06 (Synthesis)
[Key sequencing decisions that the Improvement Plan should
highlight in the executive summary]

### 7.3 For Phase 5 (Execution)
[Specific Tier 1 quick-wins, Tier 2 coordination blocks, Tier 3
final-polish ordering]

---

## 8. Sources & Evidence Register

- **Phase 1 Input Validation** — for constraint envelope and Phase 1
  priority indications
- **Principle Weighting (Step 02)** — for tier-rationale weighting
- **Mechanism Decisions (Step 03)** — for inter-MC dependencies and
  mechanism-induced sequencing constraints
- **Practitioner confirmations** — final authority on sequence
```

---

## Evaluation Checklist

Before accepting the Sequencing and Tiering artifact:

- [ ] All MCs from Phase 1 are placed in a tier
- [ ] Tier boundaries have principle-weighted rationale
- [ ] Inter-MC dependencies from Step 03 are respected
- [ ] Minimum-viable-completion floor is named with rationale
- [ ] Stretch scope is identified (work above the floor)
- [ ] Worst-case plan-failure narrative includes three or more
      failure branches
- [ ] **The common mechanism is explicitly named** (not three
      unrelated bad outcomes)
- [ ] Plan mitigation addresses the common mechanism
- [ ] Comprehensiveness check is conducted
- [ ] Forward implications for Step 05, Step 06, Phase 5 are listed

---

## Version History

| Version | Date | Source | Summary |
|---------|------|--------|---------|
| v1.0 | 2026-04-22 | Initial authoring | Initial Phase 2 Step 04 prompt. Draft-and-react mode. Integrates the worst-case-plan-failure narrative discipline (Phase 1's most useful synthesis-producing exercise, adapted for plan-level failure modes rather than discovery failure modes). Includes minimum-viable-completion floor and stretch scope as separate artifact elements. Common-mechanism discipline explicit per Phase 1 v1.1 Cluster N. |

---

*Part of the Phase 2 Analysis & Improvement Planning (Existing Projects) Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `analysis-improvement-planning.existing-project.instructions.md`*
*Previous step: `step-03-mechanism-decisions.prompt.md`*
*Next step: `step-05-cost-modeling-and-capacity-check.prompt.md`*
