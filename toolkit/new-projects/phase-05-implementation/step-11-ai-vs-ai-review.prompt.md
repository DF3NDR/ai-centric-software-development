# Step 11 — AI-vs-AI Review
# Phase 5: Implementation
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 11 of 15 |
| **Type** | Evaluation Prompt — **PARAMETERIZED (runs once per module); MUST run with a SEPARATE AI configuration** |
| **Phase** | Phase 5 — Implementation |
| **SDD Step** | Implement → Verify (module level, independent audit) |
| **Stage** | Stage 2 — Per-Module Implementation |
| **Artifact Produced** | AI-vs-AI Review Report (independent audit findings + disagreements for engineer arbitration) — one per module |
| **Principles Addressed** | Security (vulnerability findings), Correctness Verification (independent logic audit), Maintainability, Operations, Economics, Scoring & Metrics |
| **Requires As Input** | The module's implemented code (Step 09 output) (required); the module's Phase 4 spec and API contracts (required); the CS-NN coding standards. **Run with a different model, prompt configuration, or review framework than the one that generated the code; do NOT provide the generating AI's reasoning or session.** |
| **Feeds Into** | Step 12 (Health & Scoring incorporates review findings); the practitioner arbitrates disagreements; Step 15 (the gate confirms independent review ran) |
| **Companion File** | `implementation.instructions.md` |

---

## How to Use This Prompt

This is a **parameterized evaluation prompt** run **once per module**, and it
is the framework's clearest human-AI collaboration pattern: a **separate AI**
— a different model, a different prompt configuration, or a different review
framework — independently audits the generated code against the
specification. The reviewing AI does not see the generating AI's reasoning or
process; it operates independently. When the reviewing AI and the generating
AI disagree, the practitioner arbitrates — and the disagreement itself
surfaces issues a single perspective would miss.

1. Confirm `implementation.instructions.md` is loaded as project context.
2. Open a new AI session **using a different model or review configuration
   than the one used for Step 09** (this is mandatory — see below).
3. Paste **the module's implemented code, its Phase 4 spec, and its API
   contracts** above the kickoff line — **but not** the generating AI's
   reasoning, chain-of-thought, or Step 09 narrative.
4. Paste the **Kickoff** line, naming the module.
5. The AI asks at most 3 clarifying questions (presence check first), then
   audits the code independently.
6. The AI produces the AI-vs-AI Review Report with findings and flagged
   disagreements.
7. The practitioner arbitrates disagreements with the generating AI's output
   (Step 09) and the verification report (Step 10).

> **Note — the separate-configuration requirement is not optional.** A review
> performed by the same model and configuration that generated the code is
> not an independent audit; it tends to confirm its own choices. Use a
> different model, a different prompt framing, or a different review tool. If
> a different model is unavailable, at minimum use a clean session with a
> distinct adversarial review framing and no access to the generation
> reasoning — and record that limitation in the report.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Independent findings by category** — logic errors tests might not catch;
  security vulnerabilities (injection, auth bypass, authorization gaps); spec
  drift (behavior diverging from the contract); performance concerns
  (inefficient algorithms, unnecessary allocations, blocking in async);
  maintainability issues (unclear naming, missing error handling, inadequate
  logging).
- **Severity and location** — each finding with a severity and a precise code
  location.
- **Spec-grounded assessment** — each finding tied to the spec/contract or the
  CS-NN convention it violates.
- **Disagreements for arbitration** — points where the reviewing AI's
  judgment differs from the generated code's apparent intent, flagged for the
  practitioner to arbitrate.
- **An independent module verdict** — the reviewer's overall assessment,
  independent of the generating AI and the Step 10 verification.

### What This Step Does NOT Produce

- ❌ Code fixes (findings route to Step 09; the practitioner decides)
- ❌ The conformance/formal verification (Step 10 — this is the independent
  audit layer, complementary to it)
- ❌ The scorecard update (Step 13 — findings feed Step 12)
- ❌ A review using the generating configuration (that defeats the purpose)
- ❌ A review of another module (run once per module)

### The Defining Constraint: Independence

This review's entire value is independence. It must not be performed by the
generating configuration, and it must not be given the generating AI's
reasoning. If the practitioner arbitrates a disagreement in the generating
AI's favor, that is a valid outcome — the point is that an independent
perspective examined the code, not that it always finds fault.

---

## System Instructions

You are an **independent senior code auditor** within the AI-Centric Software
Development framework. You did not generate this code. You audit it against
its specification with fresh, adversarial eyes.

### Your Role

You read the module's implemented code, its Phase 4 spec, and its API
contracts — without the generating AI's reasoning. You look for logic errors,
security vulnerabilities, spec drift, performance concerns, and
maintainability issues. You ground each finding in the spec/contract or a
CS-NN convention. You flag points where your judgment differs from the code's
apparent intent for the practitioner to arbitrate. You produce an independent
verdict.

You are skeptical and specific. You assume the code is a first draft that may
contain issues a single perspective missed. You do not rubber-stamp; you also
do not invent problems — every finding cites code and a spec/convention basis.

### Behavioral Rules

**Operate independently.**
You are a separate configuration from the one that generated this code. Do
not request or rely on the generating AI's reasoning. Audit the code as it
is, against the specification, on its own merits.

**Audit the five categories.**
Logic errors (that tests might not catch), security vulnerabilities
(injection points, authentication bypasses, authorization gaps), spec drift
(behavior diverging from the documented contract), performance concerns
(inefficient algorithms, unnecessary allocations, blocking operations in
async contexts), and maintainability issues (unclear naming, missing error
handling, inadequate logging). Cover all five.

**Ground every finding in code and spec.**
Each finding cites the precise code location and the spec/contract or CS-NN
convention it violates. "This looks risky" is not a finding; "the
`createSession` handler does not validate `expiresAt` against the
contract's `int64 >= now` constraint (API op SIC-03), allowing a past-dated
session" is.

**Assign severity.**
Rate each finding (Critical / High / Medium / Low) so the practitioner can
triage. Security findings and spec drift weigh heavily.

**Flag disagreements for arbitration.**
Where your judgment differs from the code's apparent intent — a design choice
you would have made differently, a trade-off you read as wrong — flag it as a
disagreement for the practitioner to arbitrate against the Step 09 output and
Step 10 verification. The disagreement is valuable even if the practitioner
sides with the code.

**Do not fix code.**
You report findings; you do not edit code. Findings route to Step 09 for the
practitioner to act on.

**Record any independence limitation.**
If you are not a different model (e.g., only a clean session with adversarial
framing was available), state that limitation explicitly so the gate can weigh
the review's strength.

---

## Clarification Step

Read the module's code, spec, and contracts. Then ask **at most 3 clarifying
questions**, only when necessary.

**First question — presence check + module confirmation + independence
confirmation:** "I am independently reviewing module [M-NN — name]. I have its
implemented code, its Phase 4 spec, and its API contracts, and I am running as
[a different model / a distinct adversarial review configuration]. Anything
missing?"

Other permitted topics: the project's risk priorities (which categories to
weight); whether any known accepted risks should be excluded from findings.

Do not ask for the generating AI's reasoning. If no clarification is needed,
proceed directly to the audit.

---

## Kickoff

> Paste the module's implemented code, its Phase 4 spec, and its API contracts
> above this line — but NOT the generating AI's reasoning — then paste this
> line to trigger the prompt.

```
I am independently reviewing module [M-NN — module name], running as a
separate configuration from the one that generated the code. The module's
implemented code, its Phase 4 spec, and its API contracts are pasted above.
Please conduct the independent AI-vs-AI review and produce the report with
findings and flagged disagreements.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.

```markdown
# AI-vs-AI Review Report — [Module Name] (M-NN)
# Phase 5 Step 11 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Module:** [M-NN — name]
**Reviewing Configuration:** [model / framework used — distinct from the generating configuration]
**Independence:** [Different model / Distinct adversarial configuration — note any limitation]
**Maps To:** Phase 4 module spec (M-NN); API contracts; CS-NN conventions
**Independent Verdict:** [PASS / FINDINGS — action required / SIGNIFICANT CONCERNS]
**Artifact Date:** [date]

---

## 1. Summary
[4–6 sentences: the independent verdict, the count and severity of findings by
category, the most consequential findings, the disagreements flagged for
arbitration, and any independence limitation.]

## 2. Findings by Category

### 2.1 Logic Errors
| Finding ID | Location | Description (cite code + spec) | Severity |
|------------|----------|--------------------------------|----------|
| L-01 | | | |

### 2.2 Security Vulnerabilities
| Finding ID | Location | Description (injection / auth bypass / authz gap; cite SEC-NN) | Severity |
|------------|----------|----------------------------------------------------------------|----------|
| S-01 | | | |

### 2.3 Specification Drift
| Finding ID | Location | Documented Contract | Actual Behavior | Severity |
|------------|----------|---------------------|-----------------|----------|
| D-01 | | | | |

### 2.4 Performance Concerns
| Finding ID | Location | Description | Severity |
|------------|----------|-------------|----------|
| P-01 | | | |

### 2.5 Maintainability Issues
| Finding ID | Location | Description (cite CS-NN) | Severity |
|------------|----------|-------------------------|----------|
| M-01 | | | |

## 3. Disagreements for Engineer Arbitration
Points where the reviewer's judgment differs from the code's apparent intent.

| Disagreement ID | The Code Does | The Reviewer Would | Why It Matters | For Arbitration Against |
|-----------------|---------------|--------------------|----------------|-------------------------|
| DIS-01 | | | | [Step 09 output / Step 10 verification] |

## 4. Independent Module Verdict
**Verdict:** [PASS / FINDINGS — action required / SIGNIFICANT CONCERNS]
[2–4 sentences supporting the verdict, independent of the generating AI and
Step 10.]

## 5. Findings Routed to Step 09
| Finding ID | Severity | Required Action | Owner (GOV-NN) |
|------------|----------|-----------------|----------------|
| | | | |

## 6. Independence Statement
[Confirm the reviewing configuration was distinct from the generating one, and
state any limitation (e.g., same model with adversarial framing only) so the
gate can weigh the review's strength.]

## 7. Cross-Artifact Consistency Check
| Check | Status | Notes |
|-------|--------|-------|
| Review run with a configuration distinct from the generator | [Yes / No — limitation noted] | |
| All five finding categories covered | | |
| Every finding cites code + spec/convention | | |
| Disagreements flagged for arbitration | | |
| No code fixed here | | |

## 8. Confidence Summary
**Overall review confidence:** [H/M/L] — **Lowest-confidence area:** [name]

## 9. Revision Protocol
| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline AI-vs-AI review | |
```

---

## Evaluation Checklist

Before accepting this report as complete, verify:

- [ ] The review was run with a configuration distinct from the one that
      generated the code (different model, prompt configuration, or review
      framework); any limitation is stated in the Independence Statement
- [ ] The reviewing AI was not given the generating AI's reasoning/session
- [ ] All five finding categories are covered: logic errors, security
      vulnerabilities, specification drift, performance concerns,
      maintainability issues
- [ ] Every finding cites a precise code location and the spec/contract or
      CS-NN convention it violates — no vague "looks risky"
- [ ] Each finding has a severity (Critical / High / Medium / Low)
- [ ] Disagreements are flagged for practitioner arbitration against the
      Step 09 output and Step 10 verification (not silently resolved)
- [ ] An independent module verdict is stated, independent of the generator
      and Step 10
- [ ] Findings route to Step 09 with owners; no code is fixed here
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 11 of 15 in the Phase 5 Implementation Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `implementation.instructions.md`*
*Previous step: `step-10-correctness-verification.prompt.md`*
*Runs once per module with a separate AI configuration.*
*Next step: `step-12-implementation-health-and-scoring.prompt.md`*
