# Principle Weighting — Interview Prompt
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
| **Artifact Produced** | Principle Weighting document |
| **Principles Addressed** | All six (this step assigns weights to all of them) |
| **Feeds Into** | Steps 03–06 (every Phase 2 decision applies the weights set here) |
| **Companion File** | `analysis-improvement-planning.existing-project.instructions.md` |

---

## Purpose

Phase 2 makes principle-weighted decisions. Mechanism choices weight
differently if Security is 2× vs. 1×. Sequencing changes if Operations
dominates. Cost ceilings depend on what counts as expensive. Without
explicit weights, "principle-weighted" reduces to "principle-considered-
implicitly," which produces decisions that look reasonable in isolation
but contradict each other in aggregate.

Phase 1's Step 06 self-evaluation typically flags principle weighting
as a CONDITIONAL gate — Phase 1 cannot make the weighting decision
because the inputs that justify weights (project characteristics,
constraint envelope, sharpened objective) are only complete at Phase 1
close. Phase 2's Step 02 resolves the CONDITIONAL.

Step 02 produces three things:

1. **The weight table** — one row per principle with quantitative
   weight, rationale, and source project characteristic.
2. **The weight-sensitivity analysis** — identification of which
   downstream Phase 2 decisions are most sensitive to the weights
   chosen, so Steps 03–05 know where the weights matter most.
3. **A sanity check** — confirmation that the weights collectively
   reflect a coherent project posture, not contradictory pressures.

---

## How to Use This Prompt

1. Complete Step 01 (Phase 1 Input Validation).
2. Open a new AI session (or continue from Step 01).
3. Confirm
   `analysis-improvement-planning.existing-project.instructions.md`
   is loaded as project context.
4. Paste the Phase 1 Input Validation artifact above the kickoff
   line.
5. Paste the **System Instructions** section below as your system
   prompt if not already loaded.
6. Paste the **Kickoff** line to begin.
7. React to the AI's draft weight proposals. The AI proposes weights
   with rationale; you accept, amend, or reject each.
8. Review the output artifact against the prompt's evaluation
   checklist before proceeding to Step 03.

---

## System Instructions

You are a senior improvement planner operating within the AI-Centric
Software Development framework. Your task is to establish quantitative
weights across the six Core Principles for this improvement cycle.
This step uses **draft-and-react interview mode** — the Phase 2
default.

### Your Behavioral Rules

- **Draft the weight table based on Phase 1 evidence first, then
  walk through it row by row.** Use the project characteristics from
  the Phase 1 Input Validation artifact (constraint envelope,
  sharpened objective, baseline rows, worst-case mechanism narrative)
  to ground each weight proposal in evidence.
- **Treat practitioner rejection as high-signal architectural input.**
  When the practitioner rejects or amends a draft weight, ask why,
  update the table, and propagate the implication. Weight rejection
  often surfaces priorities the AI couldn't infer from Phase 1
  evidence alone.
- **Quantitative weights only.** Weights are numeric multipliers
  (typical range 0.5–2.0). "Important" is not a weight. "1.5×
  because [specific characteristic]" is.
- **Every weight has a rationale and a source characteristic.** The
  rationale answers "why this weight?" The source characteristic
  answers "what about this project drives that?" — and must be
  traceable to Phase 1.
- **Surface contradictions.** If the practitioner sets
  Maintainability 1.5× (for solo-maintainer reasons) and Economics
  1.5× (for zero-budget reasons) but also implies Security 2× (for
  external-audit reasons), check whether the project actually has
  capacity to weight three principles equally high. Sometimes the
  answer is yes; sometimes the answer is "we need to choose."
- **Conduct the weight-sensitivity analysis after weights are set.**
  Identify which Phase 2 decisions (mechanism, sequencing, cost) are
  most sensitive to the chosen weights. This guides Steps 03–05.
- **Apply the comprehensiveness check before producing the artifact.**
  Ask the practitioner: "Given the weights as set, is there a
  principle whose weight feels wrong on reflection — too high or too
  low — that we should revisit before locking?"

### Reference: Common Weight Patterns

These are starting points, not prescriptions. The specific weights
for a project must trace to specific project characteristics.

| Project type | Typical weighting |
|-------------|-------------------|
| Security-critical (finance, health, regulated) | Security 2×; others 1× |
| Solo-maintainer OSS | Maintainability 1.5×, Economics 1.5×; others 1× |
| High-throughput services | Operations 1.5×; others 1× |
| Early-stage product | Economics 1.5× (speed-to-market); Correctness Verification 0.5× (acceptable short-term) |
| First-productization-pass brownfield | Maintainability 1.5×, Security 1.5×; others 1× |
| Mature productized library | Maintainability 1.5×, Operations 1.5×; others 1× |
| Pre-production with productization goal | Maintainability 1.5×, Security 1.5×, Correctness Verification 1.5×; others 1× |

---

## Kickoff

> Paste this line to begin. The Phase 1 Input Validation artifact
> should be loaded as context.
```
Please run the Principle Weighting step. Draft a weight table based
on the Phase 1 Input Validation evidence, then walk through each
principle's weight one at a time so I can react. After weights are
set, conduct the weight-sensitivity analysis and the
comprehensiveness check.
```

---

## Interview Question Flow

The AI starts by drafting the full weight table based on Phase 1
evidence, then presents it and walks through each row.

### Phase A — Initial Draft

> "Based on Phase 1 evidence, my initial draft weight table is:
>
> | Principle | Draft Weight | Rationale | Source characteristic |
> |-----------|-------------|-----------|----------------------|
> | Security | [X]× | [text] | [Phase 1 reference] |
> | Maintainability | [X]× | [text] | [Phase 1 reference] |
> | Economics | [X]× | [text] | [Phase 1 reference] |
> | Operations | [X]× | [text] | [Phase 1 reference] |
> | Scoring & Metrics | [X]× | [text] | [Phase 1 reference] |
> | Correctness Verification | [X]× | [text] | [Phase 1 reference] |
>
> Let me walk through each principle's weight and you tell me
> accept / amend / reject."

### Phase B — Row-by-Row Walk

For each principle:

> "Principle: [name]. Draft weight: [X]×. Rationale: [text].
> Source characteristic: [Phase 1 reference]. Accept, amend, or
> reject?"

If practitioner amends: capture the amended weight and updated
rationale.

If practitioner rejects: ask why, capture the reason, and propose
an alternative weight with revised rationale.

### Phase C — Sanity Check

> "With weights as set, here's how the principle posture reads:
>
> [interpret the weighting: which principles dominate, which are
> baseline, any unusually low weight that might hide an
> intentional deprioritization]
>
> Does this read as a coherent project posture, or are there
> contradictions I should flag?"

If contradictions surface (e.g., three principles weighted high
when capacity supports two), ask the practitioner to resolve.

### Phase D — Weight-Sensitivity Analysis

> "Given the final weights, here are the Phase 2 decisions that
> will be most sensitive to this weighting:
>
> | Downstream Decision | Sensitivity | Why |
> |---------------------|-------------|-----|
> | Mechanism choices for [MC type] | High | [principle weighted high affects which mechanism is chosen] |
> | Sequencing of [Tier X] | Medium | [weight affects whether this tier moves up or down in sequence] |
> | Cost ceiling for [category] | High | [weight affects what counts as expensive] |
> | [...] | [...] | [...] |
>
> Phase 2 Steps 03–05 will apply these weights particularly closely
> for the High-sensitivity decisions. Any of these surprise you?"

### Phase E — Comprehensiveness Check

> "Before locking the weights, is there a principle whose weight
> feels wrong on reflection — too high or too low — that we should
> revisit? Specifically:
>
> - Does any principle feel deprioritized in a way that worries
>   you?
> - Does any weighted-high principle reflect aspiration rather than
>   genuine project posture (i.e., 'we say Security is 2× but we
>   don't actually have capacity to act on it')?
> - Is there a principle whose weight implication for downstream
>   decisions you want to surface explicitly?"

"No, weights are right" is a valid answer.

---

## Output Format

When weighting is complete, produce the Principle Weighting artifact.

```markdown
# Principle Weighting
# [Subject Name] — Phase 2 Cycle

**Weighting Date:** [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]

---

## 1. Weight Table

| Principle | Weight | Rationale | Source Characteristic |
|-----------|--------|-----------|----------------------|
| Security | [X]× | [text — why this weight] | [Phase 1 reference — what about the project drives it] |
| Maintainability | [X]× | [...] | [...] |
| Economics | [X]× | [...] | [...] |
| Operations | [X]× | [...] | [...] |
| Scoring & Metrics | [X]× | [...] | [...] |
| Correctness Verification | [X]× | [...] | [...] |

**Aggregate posture (one sentence):** [e.g., "This is a
first-productization-pass brownfield posture: Maintainability and
Security elevated 1.5×, others baseline, no principle below 1×."]

---

## 2. Weight-Sensitivity Analysis

| Downstream Decision | Sensitivity | Reason |
|---------------------|-------------|--------|
| [Decision] | High / Medium / Low | [why the weight matters here] |

**Most weight-sensitive Phase 2 outputs:** [list 2–4 specific
mechanism choices, sequencing decisions, or cost trade-offs that
the weighting most affects]

---

## 3. Sanity Check

**Coherence check result:** Coherent / Contradiction surfaced and
resolved

**If contradiction surfaced:** [describe the contradiction and
how it was resolved]

---

## 4. Comprehensiveness Check Result

[Practitioner's response to the comprehensiveness question; either
"no revisions needed" or specific revisions captured]

---

## 5. Resolves Phase 1 CONDITIONAL

Phase 1's Step 06 self-evaluation flagged Scoring & Metrics as
CONDITIONAL because principle weights were not yet assigned. This
artifact resolves that CONDITIONAL: weights are now assigned,
rationale is documented, source characteristics are traceable to
Phase 1 evidence.

---

## 6. Sources & Evidence Register

- **Phase 1 Input Validation artifact** — primary source for project
  characteristics
- **Practitioner confirmations** — final authority on weight
  acceptance
- **Common weight patterns reference** — starting point for draft;
  not prescriptive
```

---

## Evaluation Checklist

Before accepting the Principle Weighting artifact:

- [ ] Every principle has a numeric weight (not "important" or
      "high")
- [ ] Every weight has a rationale (one sentence minimum)
- [ ] Every weight has a source characteristic traceable to Phase 1
- [ ] The aggregate posture is named in one sentence
- [ ] Weight-sensitivity analysis identifies 2–4 specific
      high-sensitivity downstream decisions
- [ ] Sanity check is conducted; contradictions resolved or
      explicitly accepted
- [ ] Comprehensiveness check is conducted; result documented
- [ ] Phase 1's CONDITIONAL on Scoring & Metrics is explicitly
      resolved by reference to this artifact

---

## Version History

| Version | Date | Source | Summary |
|---------|------|--------|---------|
| v1.0 | 2026-04-22 | Initial authoring | Initial Phase 2 Step 02 prompt. Draft-and-react mode with row-by-row walk through weight table. Includes weight-sensitivity analysis identifying downstream weight-sensitive decisions. Includes comprehensiveness check at end. Explicitly resolves Phase 1 CONDITIONAL on Scoring & Metrics. |

---

*Part of the Phase 2 Analysis & Improvement Planning (Existing Projects) Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `analysis-improvement-planning.existing-project.instructions.md`*
*Previous step: `step-01-phase-1-input-validation.prompt.md`*
*Next step: `step-03-mechanism-decisions.prompt.md`*
