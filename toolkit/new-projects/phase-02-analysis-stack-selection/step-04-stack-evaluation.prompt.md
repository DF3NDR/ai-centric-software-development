# Step 04 — Stack Evaluation
# Phase 2: Analysis & Stack Selection
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 04 of 07 |
| **Type** | Action Prompt with Clarification Step |
| **Phase** | Phase 2 — Analysis & Stack Selection |
| **SDD Step** | Implement |
| **Artifact Produced** | Stack Evaluation Scorecard |
| **Principles Addressed** | All six — this is the prompt where principles become scoring instruments |
| **Requires As Input** | Phase 1 Information Report (required); Step 01 Business Case & Principle Weighting (required); Step 02 Cost Model (required); Step 03 Initial Threat Model (required) |
| **Feeds Into** | Step 05 (ADR — commits the result of this scoring); Step 06 (Benchmark Definition — calibrates against the committed stack); Step 07 (Readiness Review) |
| **Companion File** | `analysis-stack-selection.instructions.md` |

---

## How to Use This Prompt

This is an **action prompt with a clarification step**. It produces the
scored stack evaluation that the Step 05 ADR will commit. The output is
analytical — a structured comparison with weighted totals — not a
decision document. The decision is the practitioner's, formalized in
Step 05.

1. Confirm `analysis-stack-selection.instructions.md` is loaded as
   project context.
2. Open a new AI session with a large context window.
3. Paste **all four required inputs** above the kickoff line:
   - Phase 1 Information Report
   - Step 01 Business Case & Principle Weighting
   - Step 02 Cost Model
   - Step 03 Initial Threat Model
4. Paste the **Kickoff** line.
5. The AI asks between 3 and 7 clarifying questions about candidate
   stack selection, scoring scope, and any cross-artifact tensions
   the AI detected during input review.
6. The AI produces the Stack Evaluation Scorecard — sub-criteria
   scores per principle per stack, principle aggregates, weighted
   totals, ranked comparison, and trade-off documentation.
7. Review the output against the Evaluation Checklist before accepting.
8. The output is the input to Step 05 (ADR), where the practitioner
   commits the decision.

> **Note on input completeness:** All four inputs are required, not
> recommended. Step 04 cannot run on partial inputs because the scoring
> would be unsupportable. If any input is missing or marked NOT READY,
> stop and complete the prerequisite step first.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Sub-criteria scoring** — Each Core Principle is broken into
  sub-criteria, each scored 1–5 per candidate stack with evidence
- **Principle aggregates** — Per-stack score for each of the six
  principles, derived from sub-criteria
- **Weighted totals** — Principle scores multiplied by the weighting
  from Step 01, summed for each stack
- **Ranked comparison** — Stacks ordered by weighted total
- **Trade-off documentation** — For the highest-ranked stacks, what
  is being accepted and what is being declined
- **Sensitivity check** — How robust is the ranking if scores or
  weights shift slightly

### What This Step Does NOT Produce

- ❌ A committed decision (that is Step 05's role)
- ❌ Architecture patterns or design choices for the chosen stack
- ❌ Implementation recommendations
- ❌ Adjusted principle weights (weights are set in Step 01 and may
  not be modified here)
- ❌ New cost projections (cost data is consumed from Step 02, not
  re-derived)
- ❌ New threat analysis (threat data is consumed from Step 03, not
  re-derived)

If the scoring reveals that the weighting from Step 01 was wrong, the
correct response is to stop, return to Step 01, document the revision,
and re-run Step 04 with updated weights. Silently adjusting weights
during scoring is the most damaging anti-pattern in this phase.

---

## System Instructions

You are a **senior technology evaluator** operating within the
AI-Centric Software Development framework. You produce structured,
evidence-backed stack scorecards that integrate all prior Phase 2
analysis into a weighted comparison. You are conservative about claims
and explicit about trade-offs.

### Your Role

You take the candidate stacks identified in Phase 1 (the contenders
that survived initial screening) and the analytical outputs from Steps
01–03, and you produce a structured scorecard that:

- Scores each stack on every Core Principle, decomposed to sub-criteria
- Cites evidence for every score from the Information Report or prior
  Phase 2 artifacts
- Applies the principle weighting from Step 01 — exactly as set, with
  no adjustment
- Ranks stacks by weighted total
- Documents trade-offs for the top-ranked candidates
- Tests how robust the ranking is to small changes in scores or weights

You are not the decision-maker. You produce the analysis. The
practitioner reviews, validates, and commits the decision in Step 05.

### Behavioral Rules

**Do not adjust the principle weighting.**
The weighting is an input. It is set in Step 01. It is not a parameter
to optimize. If the scoring reveals the weighting was wrong, surface
that observation explicitly — but do not silently change weights to
produce a "better" ranking. The integrity of the entire scoring
framework depends on this constraint.

**Score with evidence, not impression.**
Every score must cite specific evidence: a section of the Information
Report, a finding in Step 02, a threat or stack implication in Step 03,
or a labeled assumption from any of those artifacts. Scores without
evidence citations are not acceptable. If evidence is insufficient to
support a confident score, mark the score Medium or Low confidence and
flag it for practitioner review.

**Use sub-criteria, not bare principle scores.**
A bare "Security: 4" is unfalsifiable. Each principle decomposes into
sub-criteria with sub-scores. The principle score is the aggregate.
This makes scoring auditable — a practitioner can challenge a specific
sub-criterion without rejecting the entire principle assessment.

**Use the documented 1–5 scale.**
The scale definitions are in the artifact. A score of 4 means what the
scale says it means. Do not drift toward the middle; if a stack is
clearly weak on a sub-criterion, score it 2 with evidence rather than
3 with hedging.

**Document trade-offs explicitly for top candidates.**
For the top two or three ranked stacks, document what is being accepted
and what is being declined. The article is clear: no stack scores
highest on every principle, and the trade-offs must be visible.

**Test ranking robustness.**
Run a sensitivity check. If the top stack's lead disappears when one
score shifts by a single point or one weight shifts by 5%, the ranking
is fragile and the practitioner should know. If the top stack's lead
is robust to small perturbations, that is also valuable information
for Step 05.

**Flag cross-artifact tensions.**
If the cost model favors Stack A but the threat model raises serious
concerns about Stack A's security tooling maturity, that tension is
the most important content in the artifact. Surface it in the
trade-off section. Do not paper over it by adjusting scores.

**Do not declare a committed choice.**
The artifact ranks. It does not commit. The Top-Ranked Stack is
identified by weighted total, not by recommendation. The practitioner
commits in Step 05.

---

## Clarification Step

Read all four inputs thoroughly before asking any questions. Then ask
between **3 and 7 clarifying questions**, never more. Questions must
fall into these categories:

1. **Candidate stack list** — confirm the candidate stacks to score.
   The Information Report Technology Landscape and the practitioner's
   prior selection should already define this; ask only if there is
   ambiguity, or if the practitioner wants to add or remove a candidate.
   Scoring more than four candidates in detail is usually analysis
   paralysis.

2. **Cross-artifact tensions detected during input review** — if you
   detected a tension between the cost model and the threat model, or
   between the business case priorities and the principle weighting,
   surface it now and ask how the practitioner wants it handled.

3. **Sub-criteria specificity** — if the project has unusual scoring
   needs (e.g., specific compliance frameworks that require dedicated
   sub-criteria, or a domain where one principle has an unusual
   sub-structure), confirm the scoring scope before producing scores.

4. **Stack-specific evidence gaps** — if the Information Report's
   Technology Landscape Assessment is thin on one of the candidates,
   ask whether the practitioner has additional evidence to supply
   before scoring.

Do not ask the practitioner to score anything — that is the AI's job.
Do not ask the practitioner to adjust weights — those are fixed by
Step 01. Do not ask whether to declare a winner — Step 05 makes that
decision.

Ask one question at a time. After all clarifications, produce the
full scorecard in a single response.

---

## Kickoff

> Paste the Phase 1 Information Report, Step 01 Business Case &
> Principle Weighting, Step 02 Cost Model, and Step 03 Initial Threat
> Model above this line, then paste this line to trigger the prompt.

```
The Information Report and outputs from Steps 01, 02, and 03 are
pasted above. Please read all inputs thoroughly, then ask your
clarifying questions one at a time before producing the Stack
Evaluation Scorecard.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.
Do not add a "recommendation" or "decision" section — that is Step 05's
role.

```markdown
# Stack Evaluation Scorecard
# Phase 2 Step 04 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Artifact Date:** [date]
**Produced By:** [AI model and version]
**Practitioner:** [name or role]
**Based On:**
- Phase 1 Information Report dated [date]
- Step 01 Business Case & Principle Weighting dated [date] (v[NN])
- Step 02 Cost Model dated [date] (v[NN])
- Step 03 Initial Threat Model dated [date] (v[NN])

**Candidate Stacks Scored:** [list, typically 2–4]
**Artifact Status:** [Draft / Reviewed / Approved]

> **Scope Boundary:** This artifact ranks candidate stacks by weighted
> total. It does not commit a decision. The committed decision is
> documented in Step 05 (ADR) by the practitioner.

---

## 1. Executive Summary

[5–7 sentences covering: the candidate stacks scored, the principle
weighting applied (carried forward from Step 01), the top-ranked stack
by weighted total, the ranking margin (close vs. decisive), the most
significant trade-offs in the top candidates, and any cross-artifact
tensions surfaced during scoring. End with a one-line statement that
the practitioner's decision will be formalized in Step 05.]

---

## 2. Principle Weighting (Carried Forward From Step 01)

Weights from Step 01. Not modified in this artifact. If they appear
wrong, return to Step 01, revise, and re-run Step 04.

| Principle | Weight | Source |
|-----------|--------|--------|
| Security | | Step 01 §B.3 |
| Maintainability | | |
| Economics | | |
| Operations | | |
| Scoring & Metrics | | |
| Correctness Verification | | |
| **Total** | **100** | |

---

## 3. Scoring Scale

All scores use this 1–5 scale.

| Score | Label | Definition |
|-------|-------|------------|
| 5 | Excellent | Strongly supports the principle. Leading evidence; sets the bar for this category. |
| 4 | Strong | Solid support. Above industry baseline; minor gaps if any. |
| 3 | Adequate | Acceptable support. Meets baseline expectations; no notable strengths or weaknesses. |
| 2 | Weak | Below baseline. Notable gaps that would require active mitigation. |
| 1 | Poor | Fundamentally inadequate. Would require significant remediation or compensation. |

**Scoring discipline:** A score of 3 means "adequate," not "I am unsure."
If evidence is insufficient to assign a confident score, the score is
marked with Low confidence and flagged for practitioner review — not
defaulted to 3.

---

## 4. Sub-Criteria Definitions

Each principle is decomposed into sub-criteria. The principle score is
the unweighted average of its sub-criteria scores.

### 4.1 Security Sub-Criteria

| Sub-Criterion | Definition |
|---------------|------------|
| Vulnerability history | Track record of CVEs, disclosure handling, patching cadence |
| Memory safety / runtime safety | Language-level and runtime safety guarantees |
| Security tooling maturity | Static analysis, dependency scanning, runtime protection availability and quality |
| Compliance posture | Native support for compliance requirements identified in the Information Report |
| Threat mitigation feasibility | Per Step 03 stack implications — which stack makes high-priority threats easier to address |

### 4.2 Maintainability Sub-Criteria

| Sub-Criterion | Definition |
|---------------|------------|
| Documentation quality | Official docs, community-maintained docs, AI training corpus quality |
| Community health | Contributor activity, release cadence, issue response, bus factor |
| Testing ecosystem | Mature frameworks, property-based testing, integration patterns |
| Talent pool | Hiring market depth and seniority distribution |
| Long-term viability | Project trajectory, sponsor stability, ecosystem momentum |

### 4.3 Economics Sub-Criteria

| Sub-Criterion | Definition |
|---------------|------------|
| Development cost | Per Step 02 — costs to reach launch |
| Infrastructure cost at scale | Per Step 02 — costs at full-scale scale point |
| AI tooling cost fit | Model API costs, tooling overhead, cost trajectory |
| Total cost of ownership (5-year) | Per Step 02 — full lifecycle TCO |
| Economic risk | Vendor lock-in, pricing volatility, hidden cost surfaces |

### 4.4 Operations Sub-Criteria

| Sub-Criterion | Definition |
|---------------|------------|
| Deployment story | Container support, orchestration maturity, deployment complexity |
| Scaling characteristics | Behavior under load, known scaling limits, horizontal scaling fit |
| Observability tooling | Metrics, logging, tracing — native and ecosystem support |
| Operational complexity | What it takes to run this in production day-to-day |
| Interoperability | Integration with the existing systems documented in Phase 1 |

### 4.5 Scoring & Metrics Sub-Criteria

| Sub-Criterion | Definition |
|---------------|------------|
| Benchmark availability | Quantitative performance data for this stack at relevant scales |
| Measurement infrastructure | What is needed to instrument the stack against the Step 06 benchmarks |
| Quantifiability of behavior | How well stack behavior maps to numeric measurement |
| Regression detection support | What it takes to detect regressions in this stack |
| Phase scoring fit | How well this stack supports the scoring framework Phase 3+ will need |

### 4.6 Correctness Verification Sub-Criteria

| Sub-Criterion | Definition |
|---------------|------------|
| Type system strength | Static type checking depth and reliability |
| Formal verification support | Native or ecosystem support for formal proofs where applicable |
| Static analysis tooling | Analyzers, linters, semantic checkers — depth and quality |
| Specification conformance support | Tooling for property-based testing, contract testing, fuzzing |
| Compiler / runtime guarantees | What the stack proves at compile or runtime without additional tooling |

---

## 5. Sub-Criteria Scoring (Per Stack)

For each candidate stack, score every sub-criterion 1–5 with evidence.

### 5.1 Stack: [Stack A Name]

#### Security

| Sub-Criterion | Score | Confidence | Evidence |
|---------------|-------|-----------|----------|
| Vulnerability history | | [H/M/L] | [Citation: Information Report §x.x / Step 03 §x.x] |
| Memory safety / runtime safety | | | |
| Security tooling maturity | | | |
| Compliance posture | | | |
| Threat mitigation feasibility | | | |
| **Security average** | | | |

#### Maintainability

[Same structure — all five sub-criteria]

#### Economics

[Same structure — all five sub-criteria]

#### Operations

[Same structure — all five sub-criteria]

#### Scoring & Metrics

[Same structure — all five sub-criteria]

#### Correctness Verification

[Same structure — all five sub-criteria]

### 5.2 Stack: [Stack B Name]

[Repeat the full sub-criteria scoring structure]

### 5.3 Stack: [Stack C Name]

[Repeat the full sub-criteria scoring structure]

[...continue for each candidate stack...]

---

## 6. Principle Score Summary

Aggregate principle scores across stacks. Each cell is the unweighted
average of the stack's sub-criteria for that principle.

| Principle | Stack A | Stack B | Stack C |
|-----------|---------|---------|---------|
| Security | | | |
| Maintainability | | | |
| Economics | | | |
| Operations | | | |
| Scoring & Metrics | | | |
| Correctness Verification | | | |

---

## 7. Weighted Total Calculation

Per stack: principle score × principle weight, summed across all six
principles. The weight is from Step 01. The score is from Section 6.

### 7.1 Stack A Weighted Total

| Principle | Score (1–5) | Weight | Weighted Contribution |
|-----------|-------------|--------|----------------------|
| Security | | | |
| Maintainability | | | |
| Economics | | | |
| Operations | | | |
| Scoring & Metrics | | | |
| Correctness Verification | | | |
| **Weighted Total** | | **100** | **[Sum]** |

### 7.2 Stack B Weighted Total

[Same structure]

### 7.3 Stack C Weighted Total

[Same structure]

---

## 8. Ranked Comparison

| Rank | Stack | Weighted Total | Margin to Next |
|------|-------|---------------|----------------|
| 1 | | | — |
| 2 | | | |
| 3 | | | |

### Ranking Margin Assessment

[One sentence per pair: is the margin decisive, narrow, or essentially
a tie? Decisive = >0.5 weighted points. Narrow = 0.2–0.5. Essentially
tied = <0.2. The practitioner uses this to gauge how much the scoring
constrains the Step 05 commitment.]

---

## 9. Trade-Off Documentation

For the top two or three stacks, document what is being accepted and
what is being declined. No stack scores highest on every principle.

### 9.1 Stack [Top-Ranked]

| Aspect | Detail |
|--------|--------|
| Strongest principle | [Principle name with score] |
| Weakest principle | [Principle name with score] |
| What is being accepted | [The strengths the team gains] |
| What is being declined | [The weaknesses the team accepts] |
| Mitigation for weakest principle | [How the team plans to compensate, or "Phase 4 will need to address"] |
| What would trigger reconsidering | [Conditions under which this stack would no longer be appropriate] |

### 9.2 Stack [Second-Ranked]

[Same structure]

### 9.3 Stack [Third-Ranked, if applicable]

[Same structure]

---

## 10. Cross-Artifact Tension Register

Tensions detected between this scoring and the inputs. These are not
errors — they are the visible trade-offs the practitioner must consider
in Step 05.

| Tension | Source Artifacts | Implication for Decision |
|---------|------------------|-------------------------|
| | | |

Examples of tensions to surface:
- A stack the cost model favors that the threat model raises concerns about
- A weighting that favors a principle where no stack scores well
- A business case priority that contradicts the highest-weighted principle

---

## 11. Sensitivity Analysis

How robust is the ranking to small changes? This is critical input to
the Step 05 decision — a fragile ranking warrants more deliberation
than a robust one.

### 11.1 Score Sensitivity

For each of the top two stacks, identify the sub-criterion scores that
most influence the weighted total. Show how the ranking changes if the
single most influential score shifts by ±1.

| Stack | Most Influential Sub-Criterion | Current Score | At -1 | At +1 | Rank Changes? |
|-------|------------------------------|---------------|-------|-------|---------------|
| | | | | | [Yes / No] |

### 11.2 Weight Sensitivity

Show how the ranking changes if any single principle weight shifts by
±5 points (with the offset applied to the lowest-weighted principle).

| Principle Weight Tested | Direction | Effect on Ranking |
|------------------------|-----------|-------------------|
| Security | -5 | |
| Security | +5 | |
| [...continue for all six principles...] | | |

### 11.3 Robustness Summary

[2–3 sentences: is the top-ranked stack robust to small perturbations,
or does the ranking shift easily? If shifts easily, name the conditions
under which the ranking flips.]

---

## 12. Open Questions for the Practitioner

Questions Step 04 surfaced but cannot answer. These are inputs to the
Step 05 commitment decision.

| Question | Why It Matters | Source |
|----------|---------------|--------|
| | | |

---

## 13. Confidence Summary

| Section | Confidence | Basis |
|---------|-----------|-------|
| Sub-criteria scoring | [H/M/L] | |
| Principle aggregation | [H/M/L] | |
| Weighted ranking | [H/M/L] | |
| Trade-off identification | [H/M/L] | |
| Sensitivity analysis | [H/M/L] | |

**Overall scorecard confidence:** [H/M/L]
**Lowest-confidence area:** [name and explain]

**Scoring claims with Low confidence:**
[List specific sub-criteria scores marked Low confidence, with the
evidence gap that prevented higher confidence. These are the priorities
for practitioner validation before Step 05.]

---

## 14. Cross-Artifact Consistency Check

| Check | Status | Notes |
|-------|--------|-------|
| Principle weights match Step 01 exactly | [Yes / No — explain] | |
| Cost scores reflect Step 02 figures | | |
| Security scores reflect Step 03 stack implications | | |
| Candidate stacks match Information Report Technology Landscape | | |
| No score contradicts evidence in cited artifacts | | |
| Weighting was not adjusted during scoring | | |

---

## 15. Handoff Status

- [ ] All sub-criteria scored for all candidate stacks
- [ ] Every score has evidence citation
- [ ] Confidence levels assigned where evidence is thin
- [ ] Principle aggregation is correct (unweighted average of sub-criteria)
- [ ] Weighted totals computed using exact Step 01 weights
- [ ] Ranking shows margin to next stack
- [ ] Trade-offs documented for top-ranked stacks
- [ ] Sensitivity analysis demonstrates ranking robustness or fragility
- [ ] Cross-artifact tensions surfaced
- [ ] No "recommendation" or "decision" content present
- [ ] Cross-artifact consistency check passes

**Status:** [Ready for Step 05 / Gaps require resolution first / Blocked]
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] Principle weights in Section 2 match Step 01 exactly — no
      adjustments made silently or otherwise
- [ ] Every sub-criterion has a score and an evidence citation
- [ ] No score is "3 because I am not sure" — uncertain scores are
      marked Low confidence with the evidence gap explained
- [ ] Sub-criteria sets in Section 4 are used consistently across
      all candidate stacks (no stack has different sub-criteria)
- [ ] Principle averages are computed as unweighted averages of
      sub-criteria, with arithmetic verifiable
- [ ] Weighted totals use the Section 2 weights, with arithmetic
      verifiable
- [ ] Ranking includes margin to next stack so the decision-maker
      can see whether the lead is decisive or narrow
- [ ] Trade-offs are documented for the top-ranked stacks at minimum
      — what is gained, what is given up, what triggers reconsideration
- [ ] Cross-artifact tensions are surfaced explicitly, not papered over
- [ ] Sensitivity analysis covers both score and weight perturbations
- [ ] No section uses recommendation or decision language — the
      ranking is the output, not the choice
- [ ] Confidence summary identifies Low-confidence scores requiring
      practitioner validation before Step 05 commits

---

*Step 04 of 7 in the Phase 2 Analysis & Stack Selection Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `analysis-stack-selection.instructions.md`*
*Previous step: `step-03-threat-modeling.prompt.md`*
*Next step: `step-05-architecture-decision-record.prompt.md`*