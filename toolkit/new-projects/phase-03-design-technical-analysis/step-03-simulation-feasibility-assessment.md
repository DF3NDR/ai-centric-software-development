# Step 02 — Design Option Scoring
# Phase 3: Design & Technical Analysis
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 02 of 09 |
| **Type** | Action Prompt with Clarification Step |
| **Phase** | Phase 3 — Design & Technical Analysis |
| **SDD Step** | Detail → Implement |
| **Artifact Produced** | Design Option Scoring across all six dimensions |
| **Principles Addressed** | All six — applied as the evaluation lens for every option in every dimension |
| **Requires As Input** | Phase 2 package (required); Step 01 Design Exploration Specification (required) |
| **Feeds Into** | Step 03 (Simulation & Feasibility — consumes the scored options to determine which must be simulated); Step 04 (Design Direction Document + ADRs — consumes scoring evidence for the locked commitments); Step 09 (Readiness Review) |
| **Companion File** | `design-technical-analysis.instructions.md` |

---

## How to Use This Prompt

This is an **action prompt with a clarification step**. It produces
the structured scoring of every viable design option across all six
locked dimensions, using the evaluation criteria framework established
in Step 01. The output ranks options per dimension by weighted total
but does not commit any choice.

1. Confirm `design-technical-analysis.instructions.md` is loaded as
   project context.
2. Open a new AI session with a large context window.
3. Paste **the Phase 2 package** and **the Step 01 Design Exploration
   Specification** above the kickoff line.
4. Paste the **Kickoff** line.
5. The AI asks between 3 and 7 clarifying questions about evidence
   gaps, options that need clarification, or cross-dimension tensions
   detected during input review.
6. The AI produces the Design Option Scoring artifact — sub-criteria
   scores per option per dimension, principle aggregates, weighted
   totals using the Phase 2 weighting, ranked options per dimension,
   trade-off documentation, and sensitivity analysis.
7. Review the output against the Evaluation Checklist before accepting.
8. The output feeds Step 03 (which simulates the scored options) and
   Step 04 (which commits direction based on the integrated evidence
   from Steps 02 and 03).

> **Note on input completeness:** Both inputs are required, not
> recommended. Step 02 cannot run on partial inputs because scoring
> would be unsupportable. If the Specification is incomplete or marks
> any dimension as `[REQUIRES PRACTITIONER INPUT]`, stop and complete
> Step 01 first.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Sub-criteria scoring per option per dimension** — Each viable
  option from Step 01 is scored against the evaluation criteria
  framework defined in Step 01, with evidence citations
- **Principle aggregates** — Per-option principle scores derived from
  sub-criteria, for each of the six dimensions
- **Weighted totals** — Principle scores multiplied by the Phase 2
  weighting, summed for each option in each dimension
- **Ranked options per dimension** — Options ordered by weighted
  total within each dimension
- **Trade-off documentation** — For top-ranked options in each
  dimension, what is being accepted and what is being declined
- **Sensitivity check** — How robust each dimension's ranking is to
  small changes in scores or weights
- **Cross-dimension tensions** — Where high-ranked options in one
  dimension would conflict with high-ranked options in another

### What This Step Does NOT Produce

- ❌ A committed design direction (that is Step 04's role)
- ❌ Simulation results (Step 03's role)
- ❌ Adjusted principle weights (weights are set in Phase 2 Step 01
  and may not be modified here)
- ❌ Changes to the evaluation criteria framework (criteria are set
  in Step 01 and may not be adjusted during scoring)
- ❌ New viable options not listed in Step 01 (if scoring reveals a
  missing option, the response is to return to Step 01 and amend the
  Specification)
- ❌ A "recommendation" — the ranked options are evidence inputs to
  Step 04, not recommendations

If scoring reveals the evaluation criteria from Step 01 are wrong,
the correct response is to stop, return to Step 01, document the
revision, and re-run Step 02 with updated criteria. Silently
adjusting criteria during scoring is the same anti-pattern as
adjusting weights during scoring — it undermines the entire
analytical framework.

---

## System Instructions

You are a **senior design analyst** operating within the AI-Centric
Software Development framework. You produce structured,
evidence-backed scoring of design options across the six locked
dimensions, using the evaluation criteria framework established in
Step 01 and the principle weighting committed in Phase 2 Step 01.

### Your Role

You take the Design Exploration Specification from Step 01 and the
Phase 2 package. You score every viable option in every dimension
against the dimension-specific sub-criteria. You apply the principle
weighting exactly as set in Phase 2. You rank options within each
dimension by weighted total. You document trade-offs for top-ranked
options. You test ranking robustness. You surface cross-dimension
tensions.

You are not committing a design direction. You produce the scored
evidence base. Step 03 will simulate. Step 04 will commit.

### Behavioral Rules

**Do not adjust the principle weighting.**
The weighting is an input from Phase 2 Step 01. It is not a parameter
to optimize. If scoring reveals the weighting was wrong, surface that
observation explicitly — but do not silently change weights to produce
a different ranking. The integrity of the scoring framework depends
on this constraint.

**Do not adjust the evaluation criteria from Step 01.**
The criteria framework was committed in Step 01 before scoring
began. Adjusting it during scoring is the rationalization failure
mode the framework's articles warn against. If a criterion turns out
to be poorly specified, stop scoring and return to Step 01.

**Score with evidence, not impression.**
Every score must cite specific evidence: the Information Report, a
Phase 2 artifact, a Step 01 Specification section, or a clearly
labeled assumption. Scores without evidence citations are not
acceptable. If evidence is insufficient to support a confident
score, mark the score Medium or Low confidence and flag it for
practitioner review.

**Use sub-criteria, not bare principle scores.**
Each principle per dimension decomposes into the sub-criteria defined
in Step 01. The principle score is the unweighted average of its
sub-criteria. This makes scoring auditable.

**Use the documented 1–5 scale.**
The same scale used in Phase 2 Step 04 applies here. A score of 3
means "adequate," not "I am unsure." Uncertain scores are marked
Low confidence rather than defaulting to the middle.

**Score every viable option in every dimension.**
Step 01 named viable options per dimension. Score them all. Do not
silently drop options the AI judges unlikely to win — the scoring
matrix must reflect every option the practitioner authorized for
evaluation. If an option is genuinely non-viable, the response is
to return to Step 01 and document its elimination.

**Apply analytical depth per the Step 01 risk ranking.**
The Step 01 Specification ranked dimensions by risk. Higher-risk
dimensions warrant deeper scoring rigor — more sub-criteria
attention, more evidence citation, more confidence calibration.
Lower-risk dimensions can be scored more lightly. The risk ranking
is the AI's guide to where to invest analytical effort.

**Document trade-offs explicitly for top-ranked options.**
For the top one or two options in each dimension, document what is
being accepted and what is being declined. No option scores highest
on every principle. The trade-offs must be visible.

**Test ranking robustness.**
Run sensitivity analysis. If a dimension's top option's lead
disappears when one score shifts by a single point, the ranking is
fragile and Step 04 should be aware. If the lead is robust to small
perturbations, that is also valuable information.

**Surface cross-dimension tensions.**
The most important content this prompt produces beyond per-dimension
scoring is the identification of tensions between dimensions. If the
top-ranked system structure option implies an interaction pattern
that scores poorly in that dimension's ranking, that tension is
critical input to Step 04. Document such tensions explicitly.

**Flag cross-artifact inconsistencies.**
If scoring reveals an inconsistency between Step 01 and the Phase 2
package — for example, an evaluation criterion that contradicts a
Phase 2 commitment — surface it. Do not paper over it.

---

## Clarification Step

Read both inputs thoroughly. Note the viable options per dimension,
the evaluation criteria framework, the simulation requirements, and
the cross-dimension risk ranking from Step 01. Then ask between **3
and 7 clarifying questions**, never more.

Permitted clarification topics:

1. **Evidence gaps for specific options.** If the Phase 2 package
   does not provide sufficient evidence to score a specific option
   on a specific sub-criterion confidently, ask whether the
   practitioner has additional context to supply or whether the
   score should be marked Low confidence with the gap documented.

2. **Cross-dimension tensions detected during input review.** If
   you detect a tension between dimensions during the initial read
   (e.g., the Step 01 viable options for data architecture include
   one that would conflict with viable options for system
   structure), surface the tension and ask how the practitioner
   wants it handled — score independently and let Step 04 reconcile,
   or note the tension in advance.

3. **Sub-criteria specificity questions.** If a sub-criterion from
   Step 01 is ambiguous when applied to a specific option, ask the
   practitioner to clarify the intended interpretation before
   scoring.

4. **Option-specific evidence the practitioner can supply.** If the
   practitioner has domain knowledge about a specific option (prior
   team experience, organizational considerations, vendor
   relationships) that scoring should reflect, ask before producing
   scores.

5. **Risk ranking validation.** If the Step 01 risk ranking suggests
   one dimension warrants substantially more depth than the AI's
   initial read suggests, or vice versa, ask before allocating
   analytical effort.

Do not ask the practitioner to score anything — that is the AI's
job. Do not ask the practitioner to adjust weights — those are
fixed by Phase 2. Do not ask the practitioner to adjust criteria —
those are fixed by Step 01. Do not ask which option the practitioner
prefers — Step 04 makes that determination based on integrated
evidence.

Ask questions one at a time. After all clarifications, produce the
full scoring artifact in a single response.

---

## Kickoff

> Paste the Phase 2 package and the Step 01 Design Exploration
> Specification above this line, then paste this line to trigger
> the prompt.

```
The Phase 2 package and Step 01 Design Exploration Specification
are pasted above. Please read all inputs thoroughly, then ask your
clarifying questions one at a time before producing the Design
Option Scoring artifact.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit
sections. Do not add a "recommendation" section.

```markdown
# Design Option Scoring
# Phase 3 Step 02 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Artifact Date:** [date]
**Produced By:** [AI model and version]
**Practitioner:** [name or role]
**Based On:**
- Phase 2 package (Steps 01–06 outputs + Stack ADR) dated [date]
- Step 01 Design Exploration Specification dated [date] (v[NN])

**Dimensions Scored:** 6 (system structure, interaction patterns,
data architecture, deployment model, security model, observability
strategy)
**Total Options Scored:** [N]
**Artifact Status:** [Draft / Reviewed / Approved]

> **Scope Boundary:** This artifact ranks options within each
> dimension by weighted total. It does not commit any design
> direction. The committed direction is produced in Step 04 based on
> the integrated evidence from this artifact and Step 03 simulation
> results.

---

## 1. Executive Summary

[6–8 sentences covering: the dimensions scored, the principle
weighting applied (carried forward from Phase 2 Step 01), the
top-ranked option per dimension by weighted total, dimensions where
the ranking is decisive versus where it is narrow, the most
significant cross-dimension tensions detected, and any sub-criteria
where evidence gaps required Low-confidence scoring. End with a
one-line statement that Step 04 will commit direction based on this
scoring plus Step 03 simulation results.]

---

## 2. Inputs Carried Forward

### 2.1 Principle Weighting (From Phase 2 Step 01)

| Principle | Weight | Source |
|-----------|--------|--------|
| Security | | Phase 2 Step 01 §B.3 |
| Maintainability | | |
| Economics | | |
| Operations | | |
| Scoring & Metrics | | |
| Correctness Verification | | |
| **Total** | **100** | |

### 2.2 Evaluation Criteria Framework (From Step 01)

[Confirmation that the criteria framework from Step 01 §3 is the
basis for scoring. No modifications are permitted in this artifact.
If modifications are needed, Step 01 must be re-run.]

### 2.3 Risk-Ranked Dimensions (From Step 01 §4)

| Rank | Dimension | Risk Level | Analytical Depth Applied |
|------|-----------|-----------|--------------------------|
| 1 | | | [Deep / Standard / Light] |
| 2 | | | |
| 3 | | | |
| 4 | | | |
| 5 | | | |
| 6 | | | |

---

## 3. Scoring Scale

All scores use the 1–5 scale.

| Score | Label | Definition |
|-------|-------|------------|
| 5 | Excellent | Strongly supports the sub-criterion. Leading evidence; sets the bar. |
| 4 | Strong | Solid support. Above baseline; minor gaps if any. |
| 3 | Adequate | Acceptable support. Meets baseline; no notable strengths or weaknesses. |
| 2 | Weak | Below baseline. Notable gaps requiring active mitigation. |
| 1 | Poor | Fundamentally inadequate. Significant remediation required. |

**Scoring discipline:** A score of 3 means "adequate," not "I am
unsure." If evidence is insufficient to assign a confident score,
the score is marked with Low confidence and flagged for practitioner
review — not defaulted to 3.

---

## 4. Per-Dimension Scoring

For each dimension, score every viable option from Step 01 against
the sub-criteria defined in Step 01, then aggregate to principle
scores, then compute weighted totals.

### 4.1 System Structure

#### Options Scored

[List of options from Step 01 §3.1, e.g., SS-1, SS-2, SS-3]

#### Sub-Criteria Scoring

For each option, score each sub-criterion 1–5 with evidence.

##### Option SS-1: [Option Name]

| Principle | Sub-Criterion | Score | Confidence | Evidence |
|-----------|--------------|-------|-----------|----------|
| Security | [Sub-criterion from Step 01] | | [H/M/L] | [Citation] |
| Security | [Sub-criterion from Step 01] | | | |
| Security | [Sub-criterion from Step 01] | | | |
| **Security average** | | | | |
| Maintainability | [Sub-criterion from Step 01] | | | |
| [continue all sub-criteria for all six principles] | | | | |

##### Option SS-2: [Option Name]

[Same structure as SS-1]

##### Option SS-3: [Option Name]

[Same structure as SS-1]

#### Principle Score Summary (System Structure)

| Principle | SS-1 | SS-2 | SS-3 |
|-----------|------|------|------|
| Security | | | |
| Maintainability | | | |
| Economics | | | |
| Operations | | | |
| Scoring & Metrics | | | |
| Correctness Verification | | | |

#### Weighted Total Calculation (System Structure)

##### SS-1 Weighted Total

| Principle | Score (1–5) | Weight | Weighted Contribution |
|-----------|-------------|--------|----------------------|
| Security | | | |
| Maintainability | | | |
| Economics | | | |
| Operations | | | |
| Scoring & Metrics | | | |
| Correctness Verification | | | |
| **Weighted Total** | | **100** | **[Sum]** |

##### SS-2 Weighted Total

[Same structure]

##### SS-3 Weighted Total

[Same structure]

#### Ranked Comparison (System Structure)

| Rank | Option | Weighted Total | Margin to Next |
|------|--------|---------------|----------------|
| 1 | | | — |
| 2 | | | |
| 3 | | | |

**Ranking Margin Assessment:**
[One sentence per pair: decisive (>0.5), narrow (0.2–0.5), or
essentially tied (<0.2).]

#### Trade-Off Documentation (Top Options, System Structure)

##### Top-Ranked: [Option Name]

| Aspect | Detail |
|--------|--------|
| Strongest principle | [Principle name with score] |
| Weakest principle | [Principle name with score] |
| What is being accepted | |
| What is being declined | |
| Mitigation for weakest principle | |
| What would trigger reconsidering | |

##### Second-Ranked: [Option Name]

[Same structure if applicable]

### 4.2 Interaction Patterns

[Same full structure as 4.1 — Options Scored, Sub-Criteria Scoring
per option, Principle Score Summary, Weighted Total Calculation per
option, Ranked Comparison with Margin Assessment, Trade-Off
Documentation for top options]

### 4.3 Data Architecture

[Same full structure as 4.1]

### 4.4 Deployment Model

[Same full structure as 4.1]

### 4.5 Security Model

[Same full structure as 4.1]

### 4.6 Observability Strategy

[Same full structure as 4.1]

---

## 5. Consolidated Ranking Summary

The top-ranked option per dimension, with the weighted total and
ranking margin. This is the consolidated view Step 03 and Step 04
will reference.

| Dimension | Top-Ranked Option | Weighted Total | Margin to Next | Margin Assessment |
|-----------|------------------|---------------|----------------|-------------------|
| System Structure | | | | [Decisive / Narrow / Tied] |
| Interaction Patterns | | | | |
| Data Architecture | | | | |
| Deployment Model | | | | |
| Security Model | | | | |
| Observability Strategy | | | | |

---

## 6. Cross-Dimension Tension Register

The most consequential content in this artifact beyond per-dimension
scoring. Tensions between top-ranked options across dimensions are
critical input to Step 04.

| Tension ID | Dimension A — Top Option | Dimension B — Top Option | Conflict Description | Implication for Step 04 |
|-----------|-------------------------|-------------------------|---------------------|------------------------|
| CDT-01 | [E.g., Data Architecture: Event Sourcing] | [E.g., Interaction Patterns: Synchronous REST] | [Event sourcing favors event-driven interaction; synchronous REST creates impedance mismatch] | [Step 04 must reconcile — either commit to event-driven and accept Interaction Patterns trade-off, or commit to synchronous and accept Data Architecture trade-off] |
| CDT-02 | | | | |

### Tensions Requiring Simulation Validation

[Tensions that Step 03 simulation should specifically test. For
example, a system structure choice that creates network latency
that may breach a performance benchmark — Step 03 should simulate
the latency under the proposed choice.]

| Tension ID | Simulation Step 03 Should Run | Reference |
|-----------|------------------------------|-----------|
| CDT-NN | [Simulation scenario] | Phase 2 Step 06 BM-NN |

---

## 7. Sensitivity Analysis

How robust the rankings are to small changes. Critical input to Step
04 — a fragile ranking warrants more deliberation.

### 7.1 Score Sensitivity (Per Dimension)

For each dimension's top-ranked option, identify the sub-criterion
score that most influences the weighted total. Show how the ranking
changes if that score shifts by ±1.

| Dimension | Top Option | Most Influential Sub-Criterion | Current Score | At -1 | At +1 | Rank Changes? |
|-----------|-----------|------------------------------|---------------|-------|-------|---------------|
| System Structure | | | | | | [Yes / No] |
| [...all six dimensions] | | | | | | |

### 7.2 Weight Sensitivity

Show how the rankings shift if any single principle weight changes
by ±5 points.

| Principle | Weight Direction | Effect on Top-Ranked Options |
|-----------|------------------|------------------------------|
| Security | -5 | [Which dimensions' rankings change, if any] |
| Security | +5 | |
| [...all six principles] | | |

### 7.3 Robustness Summary

[2–3 sentences: which dimensions have robust rankings, which have
fragile rankings. Fragile rankings warrant more attention from Step
03 simulation and more deliberation in Step 04.]

---

## 8. Evidence Gap Register

Sub-criteria where evidence was insufficient for confident scoring.
These are priorities for practitioner validation before Step 04 or
for additional simulation in Step 03.

| Gap ID | Dimension | Option | Sub-Criterion | Confidence | Evidence Gap | Resolution Path |
|--------|-----------|--------|---------------|-----------|--------------|-----------------|
| EG-01 | | | | Low | | [Step 03 simulation / Practitioner clarification / Document as known risk] |

---

## 9. Confidence Summary

| Section | Confidence | Basis |
|---------|-----------|-------|
| Sub-criteria scoring | [H/M/L] | |
| Principle aggregation | [H/M/L] | |
| Weighted rankings | [H/M/L] | |
| Cross-dimension tension identification | [H/M/L] | |
| Sensitivity analysis | [H/M/L] | |

**Overall scoring confidence:** [H/M/L]
**Lowest-confidence area:** [name and explain]

---

## 10. Cross-Artifact Consistency Check

| Check | Status | Notes |
|-------|--------|-------|
| Principle weights match Phase 2 Step 01 exactly | [Yes / No — explain] | |
| Evaluation criteria match Step 01 Specification §3 | | |
| Every option from Step 01 viable options is scored | | |
| No new options added that were not in Step 01 | | |
| Sub-criteria scoring evidence is traceable | | |
| Weighting was not adjusted during scoring | | |
| Criteria were not adjusted during scoring | | |
| Cross-dimension tensions reference both dimensions explicitly | | |

---

## 11. Revision Protocol

| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline scoring of [N] options across 6 dimensions | |

---

## 12. Handoff Status

- [ ] All six dimensions scored with all viable options from Step 01
- [ ] Every sub-criterion has a score and an evidence citation
- [ ] Confidence levels assigned where evidence is thin
- [ ] Weighted totals use the exact Phase 2 weighting
- [ ] Trade-offs documented for top-ranked options per dimension
- [ ] Sensitivity analysis demonstrates ranking robustness or
      fragility per dimension
- [ ] Cross-dimension tensions surfaced explicitly
- [ ] No "recommendation" or "committed direction" content present
- [ ] Cross-artifact consistency check passes

**Status:** [Ready for Step 03 / Gaps require resolution first / Blocked]
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] Principle weights match Phase 2 Step 01 exactly — no
      adjustments
- [ ] Evaluation criteria match Step 01 Specification §3 exactly —
      no adjustments during scoring
- [ ] Every viable option from Step 01 is scored — no silent drops
- [ ] No new options added that did not appear in Step 01
- [ ] Every sub-criterion has a score and an evidence citation
- [ ] No score is "3 because I am unsure" — uncertain scores are
      Low confidence with the gap explained
- [ ] Sub-criteria sets are consistent with Step 01 for each
      dimension (no stack has different sub-criteria)
- [ ] Principle averages are unweighted averages of sub-criteria,
      verifiable arithmetically
- [ ] Weighted totals use Phase 2 weights, verifiable arithmetically
- [ ] Every dimension has its own ranked comparison with margin
      assessment
- [ ] Trade-offs documented for top-ranked options per dimension —
      gained, given up, mitigation, revision trigger
- [ ] Cross-dimension tension register is populated — top-ranked
      options across dimensions are checked for conflicts
- [ ] Tensions requiring simulation validation are flagged for
      Step 03
- [ ] Sensitivity analysis covers both score and weight perturbations
      per dimension
- [ ] Evidence gap register identifies sub-criteria with Low
      confidence and their resolution path
- [ ] No section uses "recommendation" or "commitment" language —
      the rankings are evidence, not decisions
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 02 of 9 in the Phase 3 Design & Technical Analysis Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `design-technical-analysis.instructions.md`*
*Previous step: `step-01-design-exploration-specification.prompt.md`*
*Next step: `step-03-simulation-feasibility.prompt.md`*