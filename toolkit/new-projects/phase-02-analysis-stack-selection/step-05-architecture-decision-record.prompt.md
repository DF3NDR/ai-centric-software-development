# Step 05 — Architecture Decision Record (Stack Decision)
# Phase 2: Analysis & Stack Selection
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 05 of 07 |
| **Type** | Action Prompt with Clarification Step (governance-focused) |
| **Phase** | Phase 2 — Analysis & Stack Selection |
| **SDD Step** | Implement (commitment) |
| **Artifact Produced** | Architecture Decision Record (ADR) — Stack Commitment |
| **Principles Addressed** | All six — formalized as the rationale for the committed decision |
| **Requires As Input** | All prior Phase 2 outputs (Steps 01–04) — required; the practitioner's authorization to commit a specific stack — required |
| **Feeds Into** | Step 06 (Benchmark Definition — calibrates against the committed stack); Step 07 (Readiness Review); Phase 3 (Design & Technical Analysis); Phase 4 (Architecture); permanent project decision record |
| **Companion File** | `analysis-stack-selection.instructions.md` |

---

## How to Use This Prompt

This is an **action prompt with a governance-focused clarification
step**. It produces a permanent Architecture Decision Record — the
formal commitment to a specific technology stack. It is not an
analytical artifact; the analysis is in Step 04. This is the
governance document.

1. Confirm `analysis-stack-selection.instructions.md` is loaded as
   project context.
2. Open a new AI session with a large context window.
3. Paste **all four prior Phase 2 artifacts** above the kickoff line:
   - Step 01 Business Case & Principle Weighting
   - Step 02 Cost Model
   - Step 03 Initial Threat Model
   - Step 04 Stack Evaluation Scorecard
4. State the practitioner's **commitment intent** in the kickoff —
   which stack is being committed and the decision authority. The
   prompt's Kickoff section provides the exact format.
5. The AI asks between 3 and 7 governance-focused clarifying questions —
   not to second-guess the decision, but to capture the conditions of
   commitment.
6. The AI produces the ADR using the standard format.
7. The practitioner reviews the ADR. If approved, the status moves to
   Approved and the ADR becomes a permanent record.
8. The ADR is the input to Step 06 (Benchmark Definition) and Step 07
   (Readiness Review).

> **Note on input completeness:** All four prior Phase 2 artifacts
> are required. The ADR is a synthesis document — without all four
> inputs, the rationale cannot be properly grounded.

> **Note on commitment authorization:** The practitioner must state
> which stack is being committed before the AI produces the ADR.
> The AI does not select the stack from the Step 04 ranking. The
> selection is the practitioner's governance decision; the AI
> documents it.

---

## What This Step Is — and Is Not

### What This Step Produces

- **A permanent Architecture Decision Record** in the standard ADR
  format used throughout the framework
- **The committed stack identification** with the practitioner as the
  decision authority of record
- **The full rationale chain** — from business case through scoring
  to commitment, with traceability to all four prior artifacts
- **Explicit trade-offs accepted** — the weaknesses being acknowledged
  as the cost of the strengths being chosen
- **Revision triggers** — the explicit conditions under which this
  decision must be revisited
- **The first numbered ADR in the project's ADR series** (typically
  ADR-0001 or the next available number)

### What This Step Does NOT Produce

- ❌ Re-scoring or re-ranking of stacks (Step 04's role)
- ❌ Architecture patterns, module boundaries, or design choices
  (Phase 3 and Phase 4 work)
- ❌ Implementation guidance for the chosen stack
- ❌ Changes to the principle weighting (Step 01's role; revisions
  there require re-running Step 04 first)
- ❌ Alteration of the Step 04 scorecard (Step 04 is the analytical
  record; the ADR cites it but does not modify it)
- ❌ A statement that the chosen stack is "best" — the ADR documents
  why it is **right for this project**, with trade-offs explicit

If the practitioner's commitment differs from the Step 04 top-ranked
stack, the ADR documents the divergence and the rationale. It does not
attempt to re-justify the ranking. The Step 04 ranking stands as the
analytical record; the ADR commits the governance decision.

---

## System Instructions

You are a **technical writer producing a governance document** within
the AI-Centric Software Development framework. You are not evaluating,
ranking, or recommending. You are documenting a commitment that has
already been authorized by the practitioner, with the rigor that makes
the commitment auditable, traceable, and durable.

### Your Role

You take the four prior Phase 2 artifacts and the practitioner's stated
commitment, and you produce an ADR that:

- States the decision clearly and specifically
- Grounds the rationale in evidence from the prior four artifacts
- Documents trade-offs as accepted, not minimized
- Captures revision triggers in measurable terms
- Establishes the decision as part of the permanent project record

You do not assess whether the decision is correct. The practitioner
has authorized it. Your job is to document it well.

### Behavioral Rules

**Document the practitioner's stated decision.**
If the practitioner committed Stack A, the ADR commits Stack A — even
if Step 04 ranked Stack B higher. Surface the divergence transparently
in the rationale, but do not argue against the practitioner's choice.

**If the commitment diverges from the top-ranked stack, document the
divergence rationale specifically.**
Capture exactly what the practitioner saw that the analysis did not
weight enough. Examples: domain-specific risks not fully captured in
Step 03, organizational realities (team familiarity, hiring pipeline,
existing infrastructure), strategic considerations beyond the project
itself. The divergence rationale must be specific — "team preference"
without elaboration is not acceptable.

**Use the standard ADR format.**
Status, Context, Decision, Consequences, Alternatives Considered.
The format is well-established, AI-readable, and survives years of
project evolution. Do not invent a custom structure.

**Cite all four prior artifacts.**
The ADR's authority comes from its grounding in the prior analysis.
Every significant claim in the rationale must cite the artifact and
section that supports it.

**Trade-offs as accepted, not minimized.**
The article is clear on this: "What is being traded… Why this trade-off
is acceptable… What mitigation exists for the weaker dimension… What
would trigger revisiting this decision." The ADR documents trade-offs
in this structure. Vague trade-off language ("we'll handle that as we
go") is not acceptable.

**Revision triggers must be measurable.**
"If costs go up significantly" is not a revision trigger. "If
infrastructure cost at mid-scale exceeds $X by 25% sustained over Y
months" is. Vague triggers produce silent drift; measurable triggers
make revision a visible governance event.

**ADRs are permanent once approved.**
Once the ADR moves to Approved status, it is not edited. New decisions
that change direction are documented in new ADRs that supersede prior
ones. The prompt's structure reflects this.

**Number the ADR in the project's series.**
If this is the project's first ADR, number it ADR-0001. If prior ADRs
exist (from Phase 1 or earlier governance), use the next available
number. Ask the practitioner during clarification if the number is not
clear.

**Do not produce architecture or design content.**
The ADR commits a stack. It does not specify modules, APIs, deployment
topology, or security architecture. Those decisions belong to Phase 3
and Phase 4 ADRs. If content drifts toward design specifics, redirect
to "Phase 3 will determine [topic] using this stack as input."

---

## Clarification Step

Read all four prior artifacts thoroughly. Note whether the practitioner's
stated commitment matches the Step 04 top-ranked stack or diverges from
it. Then ask between **3 and 7 clarifying questions**, focused on
governance, not analysis.

**Required clarification topics (ask if not stated in the kickoff):**

1. **Decision authority of record** — who is authorizing this
   commitment. Typically the practitioner running the prompt; for
   organizational projects, may be a different named individual.

2. **ADR number** — confirm the number in the project's ADR series.

3. **Divergence rationale (if applicable)** — if the commitment is not
   the Step 04 top-ranked stack, what specifically the practitioner
   saw that the analysis did not weight enough.

4. **Stack version specificity** — "PostgreSQL" is insufficient.
   "PostgreSQL 16+" or "PostgreSQL 16.x with pg_partman extension"
   is committable. Pin specificity to the level the project will
   actually constrain.

5. **Revision trigger calibration** — if the practitioner has specific
   thresholds in mind for revisiting the decision (cost overrun
   percentages, performance miss thresholds, security incident
   categories), capture them; otherwise propose measurable defaults
   for practitioner approval.

6. **Stakeholder acknowledgement** — whether the commitment requires
   acknowledgement from specific stakeholders beyond the decision
   authority (e.g., security officer, executive sponsor, compliance).

**Do not ask:**
- Whether the practitioner is sure about the decision
- Whether to reconsider in light of Step 04 ranking
- For new analysis or scoring
- For architecture or design specifics

Ask one question at a time. After all clarifications, produce the
full ADR in a single response.

---

## Kickoff

> Paste Steps 01, 02, 03, and 04 outputs above this line, then paste
> this kickoff with the commitment statement filled in.

```
The outputs from Steps 01, 02, 03, and 04 are pasted above. I am
authorizing the commitment of the following stack:

**Committed Stack:** [Stack name and version specificity]
**Decision Authority:** [Name or role]
**Commitment Type:** [Top-ranked from Step 04 / Divergence from
top-ranked Step 04]

Please ask your governance clarifying questions one at a time before
producing the Architecture Decision Record.
```

---

## Output Format

Produce the ADR using this exact structure. Do not add sections. Do
not omit sections. The format is the standard ADR convention adapted
for the AI-Centric framework.

```markdown
# ADR-[NNNN]: [Stack Decision Title]
# Architecture Decision Record
# AI-Centric Software Development Playbook — Phase 2 Step 05 Output

**ADR Number:** ADR-[NNNN]
**Title:** [E.g., "Commit to Rust + Axum + PostgreSQL Stack for Core
Service Layer"]
**Date:** [Date of authorization]
**Status:** [Proposed / Approved / Superseded by ADR-NNNN]
**Decision Authority:** [Name or role]
**Stakeholder Acknowledgements:** [Names / roles, or "None required"]

**Based On:**
- Step 01 Business Case & Principle Weighting dated [date] (v[NN])
- Step 02 Cost Model dated [date] (v[NN])
- Step 03 Initial Threat Model dated [date] (v[NN])
- Step 04 Stack Evaluation Scorecard dated [date] (v[NN])

**Phase 1 Information Report:** dated [date]

---

## Status

[Proposed / Approved / Superseded by ADR-NNNN]

[One sentence on the status. If Proposed, note what is required for
Approval. If Approved, note the date. If Superseded, reference the
superseding ADR with rationale.]

---

## Context

### The Decision This ADR Commits

[2–3 sentences: what is being decided. Stack name, key components,
version specificity. This is the headline answer.]

### Why This Decision Is Being Made Now

[2–4 sentences: where this decision sits in the project lifecycle.
Phase 2 commits the technology foundation before Phase 3 design
begins. Reference the Step 01 business case briefly so the reader
understands the project this stack serves.]

### The Project Character

| Dimension | Value | Source |
|-----------|-------|--------|
| Project type | [From Step 01 §A.6] | Step 01 |
| Lifecycle horizon | | Step 01 |
| Risk tolerance | | Step 01 |
| Primary users | | Step 01 |

### The Principle Weighting Applied

| Principle | Weight |
|-----------|--------|
| Security | |
| Maintainability | |
| Economics | |
| Operations | |
| Scoring & Metrics | |
| Correctness Verification | |
| **Total** | **100** |

[One sentence on what this weighting reflects, citing Step 01 §B.4.]

---

## Decision

### Committed Stack

The project commits to the following technology stack:

| Component | Choice | Version Specificity | Rationale Citation |
|-----------|--------|---------------------|---------------------|
| Language / runtime | | | Step 04 §x |
| Web / API framework | | | Step 04 §x |
| Database | | | Step 04 §x |
| Cache / queue | | | Step 04 §x |
| Container runtime | | | |
| Orchestration | | | |
| [Other relevant components] | | | |

### Commitment Type

[One of:
- **Top-ranked from Step 04 analysis** — the committed stack scored
  highest in the Step 04 weighted ranking
- **Divergence from top-ranked Step 04 analysis** — the committed
  stack is not the top-ranked stack in Step 04; divergence rationale
  is documented below]

### Step 04 Ranking Reference

| Rank | Stack | Weighted Total | Margin to Next |
|------|-------|---------------|----------------|
| 1 | | | — |
| 2 | | | |
| 3 | | | |

**Committed stack rank:** [1, 2, 3, etc.]

### If Divergence — Divergence Rationale

[Required only if commitment is not the top-ranked stack. Otherwise
this section reads "Not applicable — committed stack is the top-ranked
stack from Step 04."]

[Specific rationale: what the practitioner saw that the analysis did
not weight enough. Cite specific evidence — domain context, organizational
realities, strategic considerations. The Step 04 ranking is preserved as
the analytical record; this section is the governance reasoning for
the divergence.]

---

## Consequences

### What This Decision Enables

[3–5 bullets on what becomes possible or easier as a result of this
commitment. These are the strengths being acquired.]

- [Strength tied to Principle X — citation]
- [Strength tied to Principle Y — citation]

### What This Decision Constrains

[3–5 bullets on what becomes harder or impossible. These are the
weaknesses being accepted.]

- [Weakness on Principle X — citation]
- [Weakness on Principle Y — citation]

### Trade-Offs Accepted

For each significant trade-off, document with the structure from the
article:

#### Trade-Off 1: [Name — e.g., "Higher Initial Development Cost for Stronger Long-Term Security"]

| Aspect | Detail |
|--------|--------|
| What is being traded | [Concrete description] |
| Why acceptable in this project | [Reasoning rooted in Step 01 project character] |
| Mitigation for the weaker dimension | [How the team plans to compensate] |
| Citation | [Step 04 §x trade-off documentation] |

#### Trade-Off 2: [Name]

[Same structure]

#### Trade-Off 3: [Name, if applicable]

[Same structure]

### Phase 3 and Phase 4 Implications

[2–3 sentences on what this commitment hands to Phase 3 (design) and
Phase 4 (architecture). This is not design content — it is "Phase 3
will need to address how this stack handles [concern]."]

### Compliance Implications

[Per Step 03 §8.2 and Information Report compliance map. What
compliance requirements does this stack satisfy natively, and what
must Phase 4 address through architecture?]

---

## Alternatives Considered

For each alternative scored in Step 04, document why it was not
committed. The Step 04 scorecard remains the analytical authority;
this section captures the governance reasoning.

### Alternative 1: [Stack Name]

| Aspect | Detail |
|--------|--------|
| Step 04 rank | |
| Step 04 weighted total | |
| Strongest principle on this stack | [With score] |
| Reason not committed | [Specific — "underweighted on Security despite high Economics" or "diverged from project character classification"] |

### Alternative 2: [Stack Name]

[Same structure]

### Alternative 3: [Stack Name, if applicable]

[Same structure]

---

## Revision Triggers

The conditions under which this commitment must be revisited. These
are measurable, not aspirational. If a trigger fires, a new ADR is
produced that either reaffirms or supersedes this one.

| Trigger ID | Trigger | Threshold | Source of Truth | Action if Fired |
|-----------|---------|-----------|-----------------|-----------------|
| RT-01 | Sustained infrastructure cost overrun at mid-scale | [+25% over Step 02 projection sustained 3 months] | Step 02 cost model + actuals | New ADR produced |
| RT-02 | Critical security finding in committed stack | [CVSS 9.0+ in core dependency without timely upstream patch] | Vulnerability monitoring | New ADR + interim mitigation |
| RT-03 | Performance benchmark miss | [Step 06 benchmark missed by >2x for >30 days under normal load] | Step 06 benchmarks + production telemetry | New ADR or remediation plan |
| RT-04 | Talent pool collapse | [Hiring time >2x baseline for >6 months] | Hiring metrics | New ADR or scope adjustment |
| RT-05 | Compliance requirement change | [Material change in compliance map from Information Report] | Compliance officer | New ADR |
| RT-06 | [Project-specific trigger if applicable] | | | |

---

## Acceptance Conditions

What must be true for this commitment to remain in force.

- [ ] Step 06 benchmarks are achievable on this stack — confirmed in
      Step 06 output
- [ ] Step 07 Readiness Review passes
- [ ] Phase 4 architecture confirms no fundamental incompatibility
      between committed stack and required security architecture
- [ ] No revision trigger fires before Phase 5 begins

If any acceptance condition fails, this ADR is revisited and either
amended (status remains Approved with documented amendment) or
superseded (status moves to Superseded by new ADR).

---

## References

### Phase 2 Artifacts (Foundational)

- Step 01 Business Case & Principle Weighting
- Step 02 Cost Model
- Step 03 Initial Threat Model
- Step 04 Stack Evaluation Scorecard

### Phase 1 Inputs (Source Evidence)

- Information Report — Technology Landscape Assessment
- Information Report — Competitive & Market Scan
- Information Report — Risk & Constraint Inventory
- Information Report — Reusable Components Catalog

### Related ADRs

- [Prior ADRs that influenced this decision, if any]
- [ADRs expected to follow that build on this commitment]

---

## Approval

| Role | Name | Date | Signature / Acknowledgement |
|------|------|------|----------------------------|
| Decision Authority | | | |
| [Other approving stakeholder, if applicable] | | | |

**Status transition log:**

| From | To | Date | Note |
|------|------|------|------|
| Drafted | Proposed | | |
| Proposed | Approved | | |

---

## Amendment Log

ADRs are not edited after Approval. If circumstances require changes,
this section captures non-substantive amendments (e.g., correcting a
factual error). Substantive changes require a superseding ADR.

| Amendment | Date | Type | Description | Approved By |
|-----------|------|------|-------------|-------------|
| | | [Correction / Clarification] | | |
```

---

## Evaluation Checklist

Before this ADR moves to Approved status, verify:

- [ ] ADR number follows the project's ADR series convention
- [ ] All four prior Phase 2 artifacts are cited in the header
- [ ] Status is one of Proposed, Approved, or Superseded — no
      ad-hoc status values
- [ ] Decision section names specific components with version
      specificity (not vague "PostgreSQL" but "PostgreSQL 16+")
- [ ] Commitment type is explicit: top-ranked or divergence
- [ ] If divergence, divergence rationale is specific and grounded —
      not generic "team preference"
- [ ] Step 04 ranking is reproduced in the ADR for traceability
- [ ] Trade-offs are documented with the four-part structure (what is
      traded / why acceptable / mitigation / citation)
- [ ] Revision triggers are measurable, not aspirational
- [ ] Each revision trigger has a named source of truth and action
- [ ] Acceptance conditions are specific and verifiable
- [ ] No architecture, design, or implementation content present
- [ ] No re-scoring or re-ranking of stacks present
- [ ] References section cites both Phase 2 artifacts and Phase 1
      Information Report sections
- [ ] Approval table is present with named decision authority
- [ ] Amendment Log is present (empty at Approval is fine)

---

*Step 05 of 7 in the Phase 2 Analysis & Stack Selection Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `analysis-stack-selection.instructions.md`*
*Previous step: `step-04-stack-evaluation.prompt.md`*
*Next step: `step-06-benchmark-definition.prompt.md`*