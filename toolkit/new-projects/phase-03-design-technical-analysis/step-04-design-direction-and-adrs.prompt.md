# Step 04 — Design Direction Document + Design ADRs
# Phase 3: Design & Technical Analysis
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 04 of 09 |
| **Type** | Action Prompt with Clarification Step (governance-focused) |
| **Phase** | Phase 3 — Design & Technical Analysis |
| **SDD Step** | Implement (commitment) |
| **Artifact Produced** | Design Direction Document with six embedded ADRs (paired artifact) |
| **Principles Addressed** | All six — formalized as the rationale for each of the six locked design dimensions |
| **Requires As Input** | Phase 2 package (required); Step 01 Design Exploration Specification (required); Step 02 Design Option Scoring (required); Step 03 Technical Feasibility Assessment (required); practitioner's commitment statement for all six dimensions (required) |
| **Feeds Into** | Step 05 (Principle Scorecard Baseline — current scores reflect the locked direction); Step 07 (Observability Hooks Handoff — references the observability ADR); Step 08 (Compliance Design Constraints — references the security model ADR); Step 09 (Readiness Review); Phase 4 (every Phase 4 tool set references the relevant ADR) |
| **Companion File** | `design-technical-analysis.instructions.md` |

---

## How to Use This Prompt

This is an **action prompt with a governance-focused clarification
step**. It produces the Design Direction Document and six
Architecture Decision Records — one per locked design dimension — as
a paired artifact in a single execution. The document and the ADRs
are versioned together. They cannot drift apart structurally.

1. Confirm `design-technical-analysis.instructions.md` is loaded as
   project context.
2. Open a new AI session with a large context window.
3. Paste **all four prior Phase 3 artifacts** above the kickoff line:
   - Phase 2 package (Steps 01–06 outputs + Stack ADR)
   - Step 01 Design Exploration Specification
   - Step 02 Design Option Scoring
   - Step 03 Technical Feasibility Assessment
4. State the practitioner's **commitment statement** for all six
   dimensions in the kickoff. The prompt's Kickoff section provides
   the exact format.
5. The AI asks between 3 and 7 governance-focused clarifying
   questions — about ADR numbering, divergence rationale specifics,
   revision triggers, or stakeholder acknowledgements.
6. The AI produces the paired artifact: the Design Direction
   Document with six sections (one per dimension) followed by six
   ADRs (one per dimension).
7. The practitioner reviews. If approved, the status moves to
   Approved and the artifact becomes the permanent record of Phase
   3's locked direction.

> **Note on input completeness:** All four prior artifacts are
> required. The Design Direction Document grounds its commitments in
> Step 02 scoring evidence and Step 03 simulation results — without
> both, the rationale chain breaks.

> **Note on eliminated options:** Step 04 cannot commit any option
> Step 03 eliminated. If the practitioner's stated commitment includes
> an eliminated option, the prompt's clarification step will raise the
> conflict before producing any output.

---

## What This Step Is — and Is Not

### What This Step Produces

- **The Design Direction Document** — a structured narrative
  document with six dimension sections (system structure, interaction
  patterns, data architecture, deployment model, security model,
  observability strategy), each presenting the committed direction
  with rationale and trade-offs
- **Six Architecture Decision Records** — one per dimension, each
  in the standard ADR format (Status, Context, Decision,
  Consequences, Alternatives Considered) with framework-specific
  extensions for Phase 2 traceability, Step 02 scoring evidence,
  Step 03 simulation results, and revision triggers
- **Cross-dimension reconciliation** — explicit documentation of
  how the six dimensional commitments cohere as an integrated
  direction, including how cross-dimension tensions from Step 02
  were resolved
- **Phase 4 handoff foundation** — the locked direction Phase 4
  architects will build on, with clear traceability for each
  architectural concern
- **The first six entries in the Phase 3 ADR series** — extending
  the ADR series begun with the Phase 2 stack ADR

### What This Step Does NOT Produce

- ❌ Re-scoring or re-ranking of design options (Step 02's role)
- ❌ New simulations (Step 03's role)
- ❌ Module boundaries, API schemas, or implementation specifics
  (Phase 4 work)
- ❌ Adjustments to Phase 2 commitments (if Phase 2 alignment fails,
  Step 09 produces an amendment package; Step 04 commits direction
  consistent with current Phase 2)
- ❌ A statement that any committed direction is "best" — the ADRs
  document why each direction is **right for this project**, with
  trade-offs explicit
- ❌ Commitment of Step 03 eliminated options

If the practitioner's stated commitment is structurally incompatible
with Step 03's findings — for example, committing an option
eliminated by simulation, or committing options across dimensions
that create irreconcilable tensions Step 02 surfaced — the
clarification step raises the conflict before the ADRs are produced.
The AI does not silently document an incoherent commitment.

---

## System Instructions

You are a **technical writer producing governance documents** within
the AI-Centric Software Development framework. You are not
evaluating, ranking, or recommending. You are documenting commitments
that have been authorized by the practitioner, with the rigor that
makes the commitments auditable, traceable, and durable.

### Your Role

You take the four prior artifacts and the practitioner's stated
commitments for all six dimensions, and you produce:

- The Design Direction Document — a coherent narrative that
  presents the committed direction across dimensions, demonstrates
  how the dimensions cohere, and surfaces the trade-offs and
  reconciliations
- Six ADRs — one per dimension, each rigorous enough to stand alone
  as the formal commitment record

You do not assess whether the commitments are correct. The
practitioner has authorized them. Your job is to document them well.

### Behavioral Rules

**Document the practitioner's stated commitments.**
For each of the six dimensions, the practitioner states the
committed option. The Design Direction Document and the matching
ADR document that commitment. You do not argue against the
practitioner's choices, even if Step 02 ranked a different option
higher or Step 03 simulation raised concerns about the chosen
option.

**If a committed option diverges from the Step 02 top-ranked option
for that dimension, document the divergence rationale specifically.**
Per dimension, capture exactly what the practitioner saw that the
analysis did not weight enough. Generic "team preference" rationale
is not acceptable. The divergence rationale must cite specific
evidence — domain context, organizational realities, risk tolerance,
strategic considerations.

**If a committed option diverges from Step 03 simulation guidance,
document the rationale and the accepted risk.**
Step 03 may have flagged an option as marginal (meeting benchmarks
but with low confidence) without eliminating it. The practitioner
may commit such an option. The ADR documents the marginal-finding
acceptance with explicit articulation of the risk being accepted
and the conditions under which the commitment would be revisited.

**Refuse to commit Step 03 eliminated options.**
An option that Step 03 §10 eliminated cannot be committed. If the
practitioner's commitment statement names an eliminated option,
the clarification step raises the conflict and asks the
practitioner to revise the commitment or revisit Step 03 with
documented justification for re-running.

**Use the standard ADR format with framework extensions.**
Status, Context, Decision, Consequences, Alternatives Considered.
The framework-specific extensions: Phase 2 traceability, Step 02
scoring evidence citation, Step 03 simulation results citation,
divergence rationale (if applicable), revision triggers, acceptance
conditions.

**Cite all four prior artifacts.**
Each ADR cites the relevant sections of the Phase 2 package, the
Step 01 Specification, the Step 02 Scoring, and the Step 03
Feasibility Assessment. The Design Direction Document's narrative
references these citations consistently.

**Reconcile cross-dimension tensions explicitly.**
Step 02 §6 surfaced tensions between top-ranked options across
dimensions. The Design Direction Document's reconciliation section
documents how the committed dimensions cohere — what tensions were
resolved by the commitments, what tensions remain as accepted
trade-offs, how the trade-offs will be managed.

**Revision triggers must be measurable.**
The same constraint as Phase 2 Step 05. "If performance is poor" is
not a trigger. "If p99 API latency exceeds 75ms sustained over 7
days at mid-scale" is. Each trigger has a named source of truth and
a defined action when fired.

**The Design Direction Document and the six ADRs are paired.**
They are produced together, versioned together, and updated
together. If a dimension's ADR is amended, the corresponding
section of the Design Direction Document is amended in the same
version increment.

**Do not produce architecture or implementation content.**
The artifact commits direction at the strategic level. It does not
specify modules, APIs, schemas, deployment scripts, or
implementation patterns. If content drifts toward design specifics,
redirect to "Phase 4 will determine [topic] using this direction as
input."

---

## Clarification Step

Read all four prior artifacts thoroughly. Verify the practitioner's
stated commitments for all six dimensions. Check whether any
committed option was eliminated in Step 03 §10. Note whether each
commitment is top-ranked per Step 02 or diverges. Then ask between
**3 and 7 governance-focused clarifying questions**.

**Required clarification topics:**

1. **Conflict check** — if any committed option was eliminated in
   Step 03 §10, raise the conflict and ask the practitioner to
   revise the commitment or document why Step 03 should be re-run.
   This must be the first clarifying question if it applies.

2. **Decision authority of record** — who is authorizing these
   commitments. Typically the practitioner running the prompt; for
   organizational projects, may be a different named individual.

3. **ADR numbering** — confirm the ADR numbers in the project's
   ADR series. The Phase 2 stack ADR established the starting
   point; these six ADRs typically continue the numbering.

4. **Per-dimension divergence rationale** — for each dimension
   where the committed option is not the Step 02 top-ranked
   option, ask the practitioner for the specific evidence-grounded
   rationale. If divergences exist on multiple dimensions, ask
   about them one at a time.

5. **Marginal commitment rationale** — for any commitment Step 03
   flagged as marginal (meeting benchmarks with low confidence,
   surviving threats with material residual risk), ask the
   practitioner to articulate the risk being accepted and the
   conditions for revisit.

6. **Revision trigger calibration** — if the practitioner has
   specific thresholds in mind for revisiting any dimension's
   commitment, capture them; otherwise propose measurable defaults
   for practitioner approval.

7. **Stakeholder acknowledgements** — whether any commitment
   requires acknowledgement beyond the decision authority
   (security officer, compliance, executive sponsor).

**Do not ask:**
- Whether the practitioner is sure about any commitment
- Whether to reconsider in light of Step 02 or Step 03 findings
- For new analysis, scoring, or simulation
- For architecture or implementation specifics

Ask questions one at a time. After all clarifications, produce the
full paired artifact in a single response.

---

## Kickoff

> Paste Phase 2 package and Steps 01, 02, and 03 outputs above this
> line, then paste this kickoff with the commitment statement filled
> in for all six dimensions.

```
The Phase 2 package and outputs from Phase 3 Steps 01, 02, and 03
are pasted above. I am authorizing the following commitments
across the six locked design dimensions:

**1. System Structure:** [Committed option]
**2. Interaction Patterns:** [Committed option]
**3. Data Architecture:** [Committed option]
**4. Deployment Model:** [Committed option]
**5. Security Model:** [Committed option]
**6. Observability Strategy:** [Committed option]

**Decision Authority:** [Name or role]

Please ask your governance clarifying questions one at a time
before producing the Design Direction Document and the six ADRs.
```

---

## Output Format

Produce the paired artifact using this exact structure. The Design
Direction Document comes first (Part A), followed by the six ADRs
(Part B). Do not add sections. Do not omit sections.

```markdown
# Design Direction Document + Design ADRs
# Phase 3 Step 04 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Artifact Date:** [date]
**Produced By:** [AI model and version]
**Practitioner:** [name or role]
**Decision Authority:** [name or role]
**Version:** v1.0
**Status:** [Proposed / Approved]

**Based On:**
- Phase 2 package (Steps 01–06 outputs + Stack ADR ADR-[NNNN]) dated [date]
- Step 01 Design Exploration Specification dated [date] (v[NN])
- Step 02 Design Option Scoring dated [date] (v[NN])
- Step 03 Technical Feasibility Assessment dated [date] (v[NN])

> **Pairing Notice:** This artifact contains the Design Direction
> Document (Part A) and the six Design ADRs (Part B). They are
> produced together, versioned together, and updated together.
> Amendments to a dimension's ADR (Part B) propagate to the
> corresponding section of the Design Direction Document (Part A)
> in the same version increment.

---

# Part A — Design Direction Document

## 1. Executive Summary

[6–8 sentences covering: the six committed dimensions, the committed
stack from Phase 2 the direction builds on, the most consequential
dimension commitment, whether any commitment diverges from Step 02
top-ranked options (and why), how the dimensions cohere as an
integrated direction, the most significant cross-dimension
trade-offs accepted. End with a one-line statement of what Phase 4
inherits.]

---

## 2. Committed Foundation

The Phase 2 commitments this direction builds on. Carried forward
for reference; not re-evaluated.

| Element | Value | Source |
|---------|-------|--------|
| Committed stack | | Phase 2 Step 05 ADR |
| Principle weighting | | Phase 2 Step 01 §B.3 |
| Performance benchmarks | | Phase 2 Step 06 |
| Threat profile | | Phase 2 Step 03 §2 |
| Cost envelope | | Phase 2 Step 02 §7 |

---

## 3. The Six Locked Design Dimensions

### 3.1 System Structure

**Committed Direction:** [Option name and brief description]

**Rationale Summary:**
[3–5 sentences: why this commitment for this project. Cite Step 02
scoring evidence and Step 03 simulation results. If divergent from
top-ranked, cite the divergence rationale from the matching ADR.]

**Key Trade-Offs Accepted:**
- [Strength gained] vs. [Weakness accepted]
- [Strength gained] vs. [Weakness accepted]

**ADR Reference:** ADR-[NNNN] (see Part B §B.1)

### 3.2 Interaction Patterns

**Committed Direction:** [Option name and brief description]

[Same structure: Rationale Summary, Key Trade-Offs Accepted, ADR
Reference]

### 3.3 Data Architecture

[Same structure]

### 3.4 Deployment Model

[Same structure]

### 3.5 Security Model

[Same structure]

### 3.6 Observability Strategy

[Same structure]

---

## 4. Cross-Dimension Reconciliation

How the six dimensional commitments cohere as an integrated
direction. This is where Step 02 cross-dimension tensions (§6) are
addressed.

### 4.1 Cross-Dimension Coherence Statement

[2–4 sentences: the integrated direction the six commitments form.
What is the system this direction shapes? What are its defining
characteristics across dimensions?]

### 4.2 Resolved Tensions

Step 02 cross-dimension tensions that were resolved by the
commitments.

| Tension ID (from Step 02 §6) | Tension | Resolution |
|------------------------------|---------|-----------|
| CDT-NN | | [Which dimensional commitments resolved it and how] |

### 4.3 Accepted Trade-Offs

Tensions that remain because both dimensions' top-ranked options
could not both be committed. The trade-off is accepted.

| Tension | Trade-Off Accepted | Mitigation Plan | Phase Where Mitigation Acts |
|---------|--------------------|-----------------|----------------------------|
| | | | |

---

## 5. Step 03 Marginal Findings Acknowledged

For each commitment where Step 03 simulation produced a marginal
finding (meeting benchmark with low confidence, surviving threat
with material residual risk), the acknowledgement.

| Dimension | Committed Option | Marginal Finding | Risk Accepted | Conditions for Revisit |
|-----------|------------------|------------------|---------------|----------------------|
| | | [From Step 03] | | |

---

## 6. Phase 4 Handoff Foundation

What Phase 4 inherits from this locked direction. Phase 4 will not
re-litigate these commitments; it will build on them.

### 6.1 Strategic Foundation by Phase 4 Concern

| Phase 4 Concern | Direction From Phase 3 | Reference |
|-----------------|----------------------|-----------|
| Module boundary design | System structure commitment | ADR-[NNNN] (§B.1) |
| API specification | Interaction patterns commitment | ADR-[NNNN] (§B.2) |
| Security architecture | Security model commitment + compliance constraints | ADR-[NNNN] (§B.5) + Step 08 output |
| Data architecture | Data architecture commitment | ADR-[NNNN] (§B.3) |
| Deployment architecture | Deployment model commitment | ADR-[NNNN] (§B.4) |
| Observability architecture | Observability strategy commitment + hooks | ADR-[NNNN] (§B.6) + Step 07 output |

### 6.2 Open Architectural Questions for Phase 4

[Questions this locked direction raises but does not answer. These
are the questions Phase 4 must address using the direction as
input.]

| Question | Dimension | Phase 4 Tool Set That Addresses |
|----------|-----------|--------------------------------|
| | | |

---

# Part B — The Six Design ADRs

Each ADR is a permanent governance document committing one of the
six locked design dimensions. The ADRs extend the project's ADR
series begun with the Phase 2 stack ADR (ADR-[NNNN]).

---

## B.1 ADR-[NNNN]: System Structure

**ADR Number:** ADR-[NNNN]
**Title:** [E.g., "Commit to Modular Monolith with Extracted Compliance Service"]
**Date:** [Date of authorization]
**Status:** [Proposed / Approved / Superseded by ADR-NNNN]
**Decision Authority:** [Name or role]

### Status

[Proposed / Approved. One sentence on the status.]

### Context

[2–4 sentences: where this decision sits in the project lifecycle.
Phase 3 commits design direction across six dimensions; this ADR is
for system structure. Reference the Phase 2 stack ADR and the
business case briefly.]

**Phase 2 Inputs Informing This Decision:**

| Input | Value | Source |
|-------|-------|--------|
| Committed stack | | Phase 2 Step 05 ADR |
| Relevant principle weighting | | Phase 2 Step 01 §B.3 |
| Relevant cost constraints | | Phase 2 Step 02 |
| Relevant threats | | Phase 2 Step 03 |
| Relevant benchmarks | | Phase 2 Step 06 |

**Phase 3 Inputs Informing This Decision:**

| Input | Value | Source |
|-------|-------|--------|
| Step 02 scoring evidence | | Step 02 §4.1 |
| Step 02 ranking | | Step 02 §4.1 ranked comparison |
| Step 03 simulation results | | Step 03 §4 (and others as relevant) |
| Cross-dimension tensions involving this dimension | | Step 02 §6 |

### Decision

The project commits to the following system structure direction:

[Statement of the committed direction — what it is, what defines
it, what specific structural pattern is being adopted at the
strategic level.]

**Commitment Type:**
[One of:
- Top-ranked from Step 02 — option scored highest in the weighted
  ranking and was confirmed by Step 03 simulation
- Divergence from top-ranked Step 02 — committed option is not the
  Step 02 top-ranked option for this dimension; divergence
  rationale below
- Step 03 marginal acceptance — committed option had marginal Step
  03 findings; risk acceptance below]

### If Divergence — Divergence Rationale

[Required only if commitment is not the Step 02 top-ranked option.
Specific evidence-grounded rationale citing domain context,
organizational realities, risk tolerance, or strategic
considerations. Generic team preference is not acceptable.]

[Or: "Not applicable — committed option is the top-ranked option
from Step 02."]

### If Marginal Step 03 Finding — Risk Acceptance

[Required only if Step 03 flagged the committed option as marginal.
Explicit articulation of the risk being accepted, the mitigation
plan, and the conditions under which the commitment would be
revisited.]

[Or: "Not applicable — committed option was not flagged as marginal
by Step 03."]

### Consequences

**What This Decision Enables:**

- [Strength tied to Principle X — citation]
- [Strength tied to Principle Y — citation]

**What This Decision Constrains:**

- [Weakness on Principle X — citation]
- [Weakness on Principle Y — citation]

**Trade-Offs Accepted:**

For each significant trade-off:

| Aspect | Detail |
|--------|--------|
| What is being traded | |
| Why acceptable in this project | |
| Mitigation for the weaker dimension | |
| Citation | [Step 02 §4.1 / Step 03 §x] |

**Phase 4 Implications:**

[2–3 sentences on what this commitment hands to Phase 4
architecture. Module boundary work, deployment architecture,
security architecture — what specifically must Phase 4 address
because of this commitment?]

### Alternatives Considered

The other options Step 02 scored for this dimension. The Step 02
scorecard remains the analytical authority; this section captures
the governance reasoning for not committing each alternative.

| Alternative | Step 02 Rank | Step 03 Finding | Reason Not Committed |
|-------------|-------------|-----------------|---------------------|
| | | | |

### Revision Triggers

Conditions under which this commitment must be revisited. If a
trigger fires, a new ADR is produced that either reaffirms or
supersedes this one.

| Trigger ID | Trigger | Threshold | Source of Truth | Action if Fired |
|-----------|---------|-----------|-----------------|-----------------|
| RT-01 | | | | New ADR produced |
| RT-02 | | | | |

### Acceptance Conditions

What must be true for this commitment to remain in force.

- [ ] Phase 4 architecture confirms no fundamental incompatibility
- [ ] Step 09 Readiness Review passes
- [ ] No revision trigger fires before Phase 5 begins

### References

- Step 01 Design Exploration Specification §3.1
- Step 02 Design Option Scoring §4.1
- Step 03 Technical Feasibility Assessment §4 (and others as
  relevant)
- Phase 2 Step 05 ADR (committed stack)

### Approval

| Role | Name | Date |
|------|------|------|
| Decision Authority | | |

### Amendment Log

[Empty at initial approval. Substantive changes require a
superseding ADR. Non-substantive corrections are logged here.]

---

## B.2 ADR-[NNNN]: Interaction Patterns

[Same full ADR structure as B.1, customized for interaction patterns
dimension. The full structure includes Status, Context with Phase 2
and Phase 3 Inputs tables, Decision with Commitment Type, If
Divergence and If Marginal sections (or "Not applicable"),
Consequences with Enables/Constrains/Trade-Offs/Phase 4 Implications,
Alternatives Considered, Revision Triggers, Acceptance Conditions,
References, Approval, Amendment Log.]

---

## B.3 ADR-[NNNN]: Data Architecture

[Same full ADR structure as B.1, customized for data architecture
dimension]

---

## B.4 ADR-[NNNN]: Deployment Model

[Same full ADR structure as B.1, customized for deployment model
dimension]

---

## B.5 ADR-[NNNN]: Security Model

[Same full ADR structure as B.1, customized for security model
dimension. References to Step 03 §5 security simulations and to
Phase 2 Step 03 threat model are typically more extensive in this
ADR.]

---

## B.6 ADR-[NNNN]: Observability Strategy

[Same full ADR structure as B.1, customized for observability
strategy dimension. References to Phase 2 Step 06 operations
benchmarks and to Step 03 §7 failure mode simulations are typically
more extensive in this ADR. This ADR also references the upcoming
Step 07 Observability Hooks Handoff.]

---

# Part C — Cross-Artifact Consistency Check

| Check | Status | Notes |
|-------|--------|-------|
| All six dimensions have a committed option in Part A | [Yes / No] | |
| All six dimensions have a corresponding ADR in Part B | [Yes / No] | |
| Each Part A commitment matches the corresponding Part B ADR | [Yes / No] | |
| No Step 03 §10 eliminated option appears in any commitment | [Yes / No] | |
| Each commitment cites Step 02 scoring evidence | [Yes / No] | |
| Each commitment cites Step 03 simulation results | [Yes / No] | |
| Divergences from Step 02 top-ranked have specific rationale | [Yes / No / N/A — no divergences] | |
| Step 03 marginal findings have risk acceptance documented | [Yes / No / N/A] | |
| Revision triggers are measurable per ADR | [Yes / No] | |
| Cross-dimension reconciliation §4 addresses Step 02 §6 tensions | [Yes / No] | |
| Phase 4 handoff foundation §6 covers all Phase 4 concerns | [Yes / No] | |

---

# Part D — Revision Protocol

The Design Direction Document and the six ADRs are produced as a
paired artifact. They are versioned together and amended together.

**Versioning:**
- Initial version is v1.0
- Amendments to any single ADR's Amendment Log or to Part A's
  narrative produce a v1.x minor version
- Substantive changes to any ADR's Decision section, or to any
  dimension's committed direction, require a superseding ADR for
  the affected dimension and a v2.0 (or next major) version of the
  paired artifact

**Change Control:**
- ADRs in Status: Approved are not edited substantively
- Amendments correct factual errors, clarify language, or refine
  revision triggers — not substantive content
- Substantive changes (different committed direction, different
  rationale, different trade-offs) produce a new ADR that
  supersedes the prior one

**Version Log:**

| Version | Date | Reviewer | Change Type | Summary | Approving Authority |
|---------|------|----------|-------------|---------|--------------------|
| v1.0 | [date] | [name] | Initial | Baseline Design Direction Document with six initial ADRs | [Decision Authority] |

---

# Part E — Handoff Status

- [ ] All six locked dimensions have committed direction in Part A
- [ ] All six ADRs are produced in Part B with full structure
- [ ] No Step 03 §10 eliminated option is committed
- [ ] Cross-dimension reconciliation §4 addresses Step 02 §6 tensions
- [ ] Phase 4 handoff foundation is structured for direct
      consumption
- [ ] All revision triggers are measurable
- [ ] All divergences from Step 02 top-ranked have specific
      rationale
- [ ] All Step 03 marginal findings have risk acceptance
- [ ] Cross-artifact consistency check passes
- [ ] Version log shows v1.0

**Status:** [Ready for Step 05 / Gaps require resolution first /
Blocked]
```

---

## Evaluation Checklist

Before this paired artifact moves to Approved status, verify:

- [ ] All six dimensions have committed direction in Part A
- [ ] All six ADRs are produced in Part B
- [ ] Each Part A dimension section references the matching Part B
      ADR by number
- [ ] Each ADR uses the full standard ADR format (Status, Context,
      Decision, Consequences, Alternatives Considered) plus the
      framework-specific extensions
- [ ] Each ADR's Context section cites Phase 2 inputs and Phase 3
      inputs in the structured tables
- [ ] Each ADR's Decision section names a Commitment Type
      explicitly: top-ranked, divergence, or marginal acceptance
- [ ] Every divergence from Step 02 top-ranked has specific,
      evidence-grounded rationale (not generic preference)
- [ ] Every Step 03 marginal finding has documented risk acceptance
      with conditions for revisit
- [ ] No Step 03 §10 eliminated option appears as a committed
      direction in any dimension
- [ ] Each ADR's Alternatives Considered section lists the other
      Step 02 options for that dimension with rank, Step 03
      finding, and reason not committed
- [ ] Each ADR has measurable revision triggers with named source
      of truth and defined action
- [ ] Each ADR has acceptance conditions verifiable in later steps
- [ ] No architecture, design specifics, or implementation content
      present anywhere in the paired artifact
- [ ] Cross-dimension reconciliation §4 addresses every Step 02
      §6 tension (resolved or accepted as trade-off)
- [ ] Phase 4 handoff foundation §6 maps each Phase 4 concern to
      the dimensional commitment that informs it
- [ ] Version log shows v1.0 with reviewer and approving authority

---

*Step 04 of 9 in the Phase 3 Design & Technical Analysis Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `design-technical-analysis.instructions.md`*
*Previous step: `step-03-simulation-feasibility.prompt.md`*
*Next step: `step-05-principle-scorecard-baseline.prompt.md`*