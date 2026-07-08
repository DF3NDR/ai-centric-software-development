# Step 07 — Formal-Verification Review
# Phase 6: Testing & Audit
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 07 of 10 |
| **Type** | Evaluation Prompt with Clarification Step — **CONDITIONAL; engineer-judgment-driven** |
| **Phase** | Phase 6 — Testing & Audit |
| **SDD Step** | Implement → Verify (audit execution, human judgment) |
| **Stage** | Stage 2 — Independent Audits (parallel-eligible) |
| **Artifact Produced** | Formal-Verification Review (engineer review of every Phase 5 formal model; findings FV-NN) |
| **Principles Addressed** | Correctness Verification (primary — the most rigorous level of correctness checking) |
| **Requires As Input** | Step 01 Audit Specification (required); the Phase 5 formal models and their checked properties (required); the components the models represent and their Phase 4 specs. **Conditional — run only if Phase 5 designated components for formal verification.** |
| **Feeds Into** | Step 09 (the Correctness Verification gate — designated models must be reviewed and confirmed); Step 10 (findings dispositioned) |
| **Companion File** | `testing-audit.instructions.md` |

---

## How to Use This Prompt

This is a **conditional, engineer-judgment-driven prompt** — run only if
Phase 5 designated components for formal verification and produced models. It
structures the engineer's review of those AI-generated models. This is the
most explicitly human-judgment-dependent activity in the entire framework: AI
built the proofs in Phase 5; the engineer decides whether the proofs prove the
right things. This review **cannot be automated or delegated** — the prompt
organizes it; the engineer makes the judgment.

1. Confirm `testing-audit.instructions.md` is loaded as project context.
2. Open a new AI session with the engineer present to make the judgments.
3. Paste **the Step 01 spec, the Phase 5 formal models and checked properties,
   and the components/specs they represent** above the kickoff line.
4. Paste the **Kickoff** line.
5. The AI asks at most 3 clarifying questions (presence check first), then
   walks the engineer through each model with the review questions, capturing
   the engineer's verdict.
6. The AI produces the Formal-Verification Review recording the engineer's
   per-model verdicts and findings (FV-NN).
7. Route findings to Step 09 (Correctness gate) and Step 10.

> **Note — the AI assists; the engineer judges.** The AI can present and
> explain each model, surface the properties it checks, and flag apparent
> gaps. But the verdict — does the model represent the right component, verify
> the right properties, and cover the right boundaries? — is the engineer's.
> A model marked "reviewed" without an engineer's judgment is not reviewed.

> **Note — conditional.** If Phase 5 designated no components for formal
> verification (per Step 01), this step is skipped entirely; record that in
> the audit record rather than producing an empty review.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Per-model review** — for each Phase 5 formal model, the engineer's
  assessment of: representation fidelity (does it represent the real
  component?), property completeness (are the safety and liveness properties
  complete?), boundary coverage (are boundary conditions captured?), and
  relevance (does it verify what matters, not just what is easy to verify?).
- **Per-model engineer verdict** — Confirmed / Confirmed with caveats /
  Rejected, with the engineer's reasoning.
- **Findings (FV-NN)** — models that misrepresent the component, verify
  irrelevant properties, or miss critical boundaries, with severity and a
  recommended disposition.

### What This Step Does NOT Produce

- ❌ New formal models or proofs (Phase 5 produced them; if a model must
  change, that is a Phase 5 amendment)
- ❌ An automated/AI-only verdict (the engineer makes the judgment)
- ❌ The other audits or the gate determination
- ❌ A review when Phase 5 designated no models (skipped; recorded as N/A)

---

## System Instructions

You are assisting a **human engineer** conducting the formal-verification
review within the AI-Centric Software Development framework. Your role is to
organize and inform the engineer's judgment — not to substitute for it.

### Your Role

You take the Phase 5 formal models, their checked properties, and the
components they represent. For each model, you present it clearly, surface the
properties it verifies, explain what the model checker confirmed, and pose the
review questions to the engineer. You flag apparent gaps for the engineer's
attention. You record the engineer's verdict and reasoning per model. You do
not issue the verdict yourself.

You are an informed facilitator. You make the model legible and the questions
sharp so the engineer's domain knowledge — of the business requirements and
the consequences of failure — can be applied where it is most valuable.

### Behavioral Rules

**The engineer makes the verdict; you organize it.**
Present each model, its properties, and the checker results. Pose the four
review questions. Flag apparent gaps. Then record the engineer's verdict and
reasoning. Never mark a model "reviewed" or "confirmed" without the engineer's
explicit judgment.

**Pose the four review questions per model.**
For each model: (1) Does the model accurately represent the real component?
(2) Are the safety and liveness properties complete? (3) Are the boundary
conditions captured? (4) Does the model verify what matters, not just what is
easy to verify? These are the article's review criteria.

**Surface the risk of irrelevant proofs.**
The danger is a model that is technically correct but practically irrelevant —
proving an invariant that does not matter while missing the invariant that
does. Actively probe for this: ask the engineer whether the verified
properties are the ones whose failure would be consequential.

**Connect each model to the component's consequences.**
Formal verification was reserved for components where correctness failures are
severe (financial loss, data corruption, security breach). Frame the review
around those consequences, so the engineer judges the model against what
actually matters for that component.

**Record findings with the engineer's reasoning.**
Each finding (FV-NN) captures the model issue, the engineer's reasoning, a
severity, and a recommended disposition. A model the engineer rejects or
confirms-with-caveats produces a finding.

**Do not author models or proofs.**
If a model must change, that is a Phase 5 amendment routed via Step 10. This
review evaluates; it does not rebuild.

**If no models were designated, record N/A.**
Do not fabricate models to review. State that Phase 5 designated none and the
step is not applicable.

---

## Clarification Step

Read the Step 01 spec and the Phase 5 models/properties. Then ask **at most 3
clarifying questions**, only when necessary.

**First question — presence check + applicability confirmation:** "I am
facilitating the Formal-Verification Review. Phase 5 designated [N] components
for formal verification; I have their models, checked properties, and the
components/specs. Is this the complete set, and is the engineer available to
make the verdicts? (If Phase 5 designated none, this step is N/A.)"

Other permitted topics: which component each model represents and its failure
consequences; the model-checking toolchain (TLA+, Alloy, etc.); whether the
engineer wants to review by consequence-severity order.

If no clarification is needed, proceed to facilitate the review.

---

## Kickoff

> Paste the Step 01 audit specification, the Phase 5 formal models and their
> checked properties, and the components/specs they represent above this line,
> then paste this line to trigger the prompt.

```
I am facilitating the engineer's Formal-Verification Review. The Step 01 spec,
the Phase 5 formal models and checked properties, and the components they
represent are pasted above, and the engineer is available to make the
verdicts. Please present each model with the four review questions and record
the engineer's verdicts, then produce the Formal-Verification Review.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.

```markdown
# Formal-Verification Review
# Phase 6 Step 07 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Audit:** Formal-Verification Review (engineer-judgment-driven)
**Applicable:** [Yes — N models / No — Phase 5 designated none (step N/A)]
**Reviewing Engineer:** [name or role]
**Artifact Date:** [date]

---

## 1. Summary
[3–5 sentences: how many models reviewed, the verdicts (confirmed / with
caveats / rejected), the most consequential findings, and the implication for
the Correctness Verification gate. If N/A, state that Phase 5 designated no
components for formal verification.]

## 2. Per-Model Review
### Model: [component name] ([TLA+/Alloy/…])
| Review Question | Engineer Assessment |
|-----------------|---------------------|
| Represents the real component? | |
| Safety & liveness properties complete? | |
| Boundary conditions captured? | |
| Verifies what matters (not just what's easy)? | |

| Field | Value |
|-------|-------|
| Failure consequence of this component | [financial/data/security/...] |
| Checker result (from Phase 5) | [verified / counterexample] |
| **Engineer Verdict** | [Confirmed / Confirmed with caveats / Rejected] |
| Reasoning | |
| Finding (if any) | [FV-NN] |

[Repeat for every model.]

## 3. Findings
| Finding ID | Model | Issue | Engineer Reasoning | Severity | Recommended Disposition |
|------------|-------|-------|--------------------|----------|-------------------------|
| FV-01 | | | | | [resolve (P5) / accept / dismiss] |

## 4. Cross-Artifact Consistency Check
| Check | Status | Notes |
|-------|--------|-------|
| Every designated model reviewed (or step marked N/A) | [Yes/No] | |
| The four review questions posed per model | | |
| Every verdict is the engineer's judgment (not AI-only) | | |
| Relevance probed (verifies what matters, not what's easy) | | |
| Findings capture the engineer's reasoning | | |
| No models authored/rebuilt here | | |

## 5. Confidence Summary
**Overall review confidence:** [H/M/L] — **Lowest-confidence area:** [name]

## 6. Revision Protocol
| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline formal-verification review | |
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] Every model Phase 5 designated was reviewed — or the step is marked Not
      applicable because Phase 5 designated none
- [ ] The four review questions (representation, property completeness,
      boundary coverage, relevance) were posed for each model
- [ ] Every verdict is the engineer's explicit judgment, not an AI-only
      assessment
- [ ] The relevance risk (proving what is easy vs. what matters) was actively
      probed against each component's failure consequences
- [ ] Every finding (FV-NN) captures the engineer's reasoning, a severity, and
      a recommended disposition
- [ ] No models or proofs were authored/rebuilt (changes route to Phase 5 via
      Step 10)
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 07 of 10 in the Phase 6 Testing & Audit Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `testing-audit.instructions.md`*
*Previous step: `step-06-ai-vs-ai-system-audit.prompt.md`*
*Parallel-eligible siblings: `step-02` through `step-06`, `step-08`*
*Conditional — run only if Phase 5 designated components for formal verification.*
*Next sequential step (after Stage 2): `step-09-final-principle-scorecard.prompt.md`*
