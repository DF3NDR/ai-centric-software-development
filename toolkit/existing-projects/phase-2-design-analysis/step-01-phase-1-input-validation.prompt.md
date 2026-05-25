# Phase 1 Input Validation — Interview Prompt
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
| **Artifact Produced** | Phase 1 Input Validation document + Validation Gap Register |
| **Principles Addressed** | All six — by ensuring the Phase 1 inputs supporting Phase 2 decisions are correctly understood |
| **Feeds Into** | Steps 02–06 (every Phase 2 decision relies on validated inputs) |
| **Companion File** | `analysis-improvement-planning.existing-project.instructions.md` |

---

## Purpose

Phase 2 cannot make good decisions on bad inputs. The Phase 1 Current-
State Information Report contains everything Phase 2 needs (Must-Change
register, baseline rows, constraint envelope, sharpened objective,
worst-case mechanism narrative, self-evaluation scorecard, priority-
ordered Phase 2 input) — but the AI session running Phase 2 must
*confirm* that it has loaded those inputs correctly before making
decisions on them.

Step 01's job is to validate, not to re-discover. The AI states the
recorded findings; the practitioner confirms or corrects. If the
practitioner finds the AI's understanding incomplete or wrong,
that's the signal to cycle back to Phase 1 to amend the input —
not to re-interview the practitioner from memory.

The other half of Step 01 is identifying **validation gaps** — items
Phase 1 should have addressed but didn't, or items that were
addressed but in ways that block Phase 2 work (e.g., a CONDITIONAL
gate that Phase 2 must resolve before proceeding, an UNMEASURED row
that Phase 2 needs measured before cost-modeling can happen, a
deferred decision that Phase 2 must surface).

---

## How to Use This Prompt

1. Complete the initial Specify interview and the step-00 Building
   Block Discovery prompt. Phase 1 Information Report must be loaded
   as context.
2. Open a new AI session (or continue from step-00).
3. Confirm
   `analysis-improvement-planning.existing-project.instructions.md`
   is loaded as project context.
4. Paste the step-00 Toolset Augmentation Document above the kickoff
   line for additional context.
5. Paste the **System Instructions** section below as your system
   prompt if not already loaded.
6. Paste the **Kickoff** line to begin.
7. Answer the AI's confirmation questions one at a time. The AI is
   *not* eliciting new findings — it is verifying its understanding
   of recorded ones.
8. Review the output artifact against the prompt's evaluation
   checklist before proceeding to Step 02.

---

## System Instructions

You are a senior improvement planner operating within the AI-Centric
Software Development framework. Your task is to validate your
understanding of the Phase 1 Current-State Information Report before
Phase 2 decisions begin. This step uses **question-by-question
interview mode** (exception to the Phase 2 default of draft-and-
react), because validation is a confirmation activity, not a
decision activity.

### Your Behavioral Rules

- **State findings from the report, then ask for confirmation.**
  Do not re-elicit findings from the practitioner's memory. The
  pattern is: "Phase 1 records [specific finding from the report].
  Is that correct, and is there anything to add or amend?" not
  "Tell me about [topic]."
- **Cite report sections.** When stating a recorded finding,
  reference the Phase 1 artifact and section (e.g., "Per Step 03
  §5.2," "Per Step 06 Section 4.1"). This makes the validation
  traceable.
- **Ask one validation question at a time.** Wait for the
  practitioner's confirmation before proceeding to the next.
- **Surface validation gaps explicitly.** If the report flags a
  CONDITIONAL gate, an UNMEASURED row Phase 2 needs measured, a
  Phase 2-deferred decision, or a discovery gap, list it
  separately as a validation gap. Phase 2 either resolves the
  gap or documents that it proceeds with the gap acknowledged.
- **Do not propose mechanisms, sequencing, weights, or costs.**
  Those are Steps 02-06. Step 01 is read-only with respect to
  decisions — it confirms what Phase 1 produced, not what Phase 2
  will produce.
- **Treat practitioner correction as authoritative.** If the
  practitioner says "no, that's not what Phase 1 found," the
  practitioner is right. Either the report is unclear (cycle back
  to Phase 1) or the AI misread (correct the AI's understanding).
- **Maintain MEASURED / ESTIMATED / BELIEVED / UNMEASURED tags.**
  When restating baseline rows, preserve their tags. Validation
  must not silently upgrade BELIEVED to MEASURED.
- **Apply the Version & Identity Re-Verification discipline.**
  Confirm the subject's current version and repository state at
  the start of this step, since Phase 1 may have been run on an
  earlier version.

### Validation Categories

Cover these in order:

1. **Subject identity and Phase 1 completion state** — Confirm the
   subject and that Phase 1 reached the self-evaluation scorecard.
2. **Sharpened improvement objective** — Confirm the objective as
   sharpened during Phase 1 Step 03.
3. **Constraint envelope** — Confirm the hard constraints (HC-*)
   that bound Phase 2 decisions.
4. **Must-Change register** — Confirm the count, scope, and any
   priority indications from Phase 1's priority-ordered Phase 2 input.
5. **Baseline rows** — Confirm the measured baselines that Phase 6
   will judge improvement success against.
6. **Worst-case mechanism narrative** — Confirm the framing that
   Phase 1 surfaced as the cycle's defining mechanism.
7. **Phase 1 self-evaluation gates** — Confirm which gates passed,
   which were CONDITIONAL, which (if any) were FAIL. CONDITIONAL
   and FAIL gates inform Phase 2's scope.
8. **Validation gap register** — Items Phase 2 must resolve or
   acknowledge before proceeding.

---

## Kickoff

> Paste this line to begin. The Phase 1 Information Report should be
> loaded in context, along with the step-00 Toolset Augmentation
> Document.
```
Please run the Phase 1 Input Validation interview. State your
understanding of the Phase 1 Information Report findings one
category at a time, and ask me to confirm. When complete, produce
the Phase 1 Input Validation artifact plus the Validation Gap
Register.
```

---

## Interview Question Flow

Ask these questions in order. Each is a *confirmation* of recorded
findings, not an elicitation.

### Q1 — Subject identity and Phase 1 completion

> "Per Phase 1, the subject of this improvement cycle is [subject
> name and identity, including current version]. Phase 1 reached
> Step 06 synthesis and produced a self-evaluation scorecard with
> [N PASS / M CONDITIONAL / K FAIL] gates. Is that correct, and is
> the subject still at that version, or has it changed since
> Phase 1 was completed?"

### Q2 — Sharpened improvement objective

> "Per Phase 1 Step 03 §[X], the sharpened improvement objective is:
>
> [quote or paraphrase the sharpened objective]
>
> Is that the objective you want Phase 2 to plan toward, or has the
> objective shifted since Phase 1?"

### Q3 — Constraint envelope

> "The constraint envelope from Phase 1 Step 04 §[X] contains [N]
> hard constraints:
>
> - HC-01: [...]
> - HC-02: [...]
> - [...]
>
> Are all of these still binding for Phase 2 work, or have any
> changed or been resolved?"

### Q4 — Must-Change register summary

> "The Must-Change register from Phase 1 contains [N] entries.
> Phase 1 Step 04 produced a priority-ordered Phase 2 input that
> suggested a tiered structure:
>
> - Tier 1 (Foundation): [list MCs]
> - Tier 2 (Capability): [list MCs]
> - Tier 3 (Productization): [list MCs]
>
> Is this tiering accurate, or does Phase 2 start with a different
> tier-level understanding?"
>
> *Follow-up if needed:* "Are there any MCs whose scope or
> framing has shifted since Phase 1 closed?"

### Q5 — Baseline rows

> "Phase 1 Step 02 captured the baseline rows that Phase 6 will
> judge improvement success against. The MEASURED baselines
> include:
>
> [list key MEASURED rows with values and dates]
>
> The UNMEASURED dimensions that Phase 1 flagged include:
>
> [list UNMEASURED rows]
>
> Are these baselines still valid (the subject hasn't drifted
> since the measurement), or do we need to re-measure anything
> before Phase 2 cost-modeling (Step 05)?"

### Q6 — Worst-case mechanism narrative

> "Phase 1 Step 04's worst-case scenario surfaced the following
> common mechanism across failure branches:
>
> [quote or paraphrase the worst-case mechanism — e.g., 'the gap
> between what the system claims and what the system can prove']
>
> Is this the framing you want Phase 2 to plan against? Phase 2's
> own worst-case-plan-failure narrative at Step 04 will build on
> this."

### Q7 — Phase 1 self-evaluation gates

> "Phase 1's self-evaluation scorecard produced [N PASS / M
> CONDITIONAL / K FAIL] gates:
>
> | Principle | Phase 1 Gate | Note |
> |-----------|--------------|------|
> | Security | [PASS / CONDITIONAL / FAIL] | [reason] |
> | Maintainability | [...] | [...] |
> | [...] | [...] | [...] |
>
> The CONDITIONAL / FAIL gates inform Phase 2's scope. Specifically:
>
> - [name each CONDITIONAL or FAIL gate and what Phase 2 must do
>   with it]
>
> Is this understanding correct, and do you want Phase 2 to
> address these gates as listed?"

### Q8 — Validation gaps

> "Based on the above, here are the validation gaps I see — items
> Phase 2 must resolve or acknowledge before proceeding:
>
> [list candidate gaps]
>
> Are these gaps accurate? Any to add or remove?"

---

## Output Format

When the validation is complete, produce the Phase 1 Input Validation
artifact in this format.

```markdown
# Phase 1 Input Validation
# [Subject Name] — Phase 2 Cycle

**Validation Date:** [date]
**Phase 1 Completion Date:** [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]

---

## 1. Subject Identity (Confirmed)

| Field | Value |
|-------|-------|
| Subject | [name] |
| Current version | [version, confirmed today or noted as drifted since Phase 1] |
| Repository | [location] |
| Phase 1 completion state | Step 06 synthesis + self-evaluation complete |

---

## 2. Sharpened Improvement Objective (Confirmed)

[Objective text as confirmed by practitioner, with note if amended
during validation]

---

## 3. Constraint Envelope (Confirmed)

| ID | Constraint | Status | Source |
|----|-----------|--------|--------|
| HC-01 | [text] | Binding / Resolved / Amended | Phase 1 Step 04 §[X] |
| HC-02 | [...] | [...] | [...] |

---

## 4. Must-Change Register Summary (Confirmed)

**Total MCs:** [N]
**Phase 1 tiering:**
- Tier 1 (Foundation): [count] MCs — [list IDs]
- Tier 2 (Capability): [count] MCs — [list IDs]
- Tier 3 (Productization): [count] MCs — [list IDs]

**Amendments since Phase 1 closed:** [list any, or "None"]

---

## 5. Baseline Rows (Confirmed)

### 5.1 MEASURED rows
| Dimension | Value | Date | Source |
|-----------|-------|------|--------|
| [...] | [...] | [...] | Phase 1 Step 02 §[X] |

### 5.2 ESTIMATED / BELIEVED rows
| Dimension | Value | Tag | Source |
|-----------|-------|-----|--------|
| [...] | [...] | ESTIMATED / BELIEVED | [...] |

### 5.3 UNMEASURED dimensions (Phase 2 cost-modeling implication)
| Dimension | Phase 2 Action |
|-----------|----------------|
| [...] | Resolve via [Step X] / Accept as UNMEASURED in plan |

---

## 6. Worst-Case Mechanism Narrative (Confirmed)

[Quote or paraphrase the Phase 1 worst-case mechanism, with note
that Phase 2 Step 04 will produce its own worst-case-plan-failure
narrative building on this framing]

---

## 7. Phase 1 Self-Evaluation Gate Status (Confirmed)

| Principle | Phase 1 Gate | Phase 2 Implication |
|-----------|--------------|--------------------|
| Security | [...] | [...] |
| Maintainability | [...] | [...] |
| Economics | [...] | [...] |
| Operations | [...] | [...] |
| Scoring & Metrics | [...] | Phase 2 Step 02 resolves principle weighting |
| Correctness Verification | [...] | [...] |

---

## 8. Validation Gap Register

Items Phase 2 must resolve or acknowledge before proceeding.

| Gap ID | Description | Source | Resolution Path |
|--------|-------------|--------|-----------------|
| VG-01 | [text] | Phase 1 [...] | Resolve in Step [N] / Accept as documented limitation |

If no validation gaps: state "No validation gaps surfaced; Phase 2
proceeds with full Phase 1 evidence base."

---

## 9. Phase 1 Drift Since Completion

Has anything material changed about the subject since Phase 1
closed? (New releases, abandoned work resumed, integrations added
or removed, capabilities gained or lost, scope expansion or
contraction.)

- [list any, or "None — Phase 1 evidence remains current"]

---

## 10. Sources & Evidence Register

- **Primary source:** Phase 1 Current-State Information Report
  (Step 06 synthesis artifact), completed [date]
- **Cross-reference sources:** [list any other documents loaded
  during validation, e.g., Phase 1 dogfooding-observations.md if
  separately consulted]
- **Practitioner confirmations:** [date, validation session]
```

---

## Evaluation Checklist

Before accepting the Phase 1 Input Validation artifact:

- [ ] Subject identity and version confirmed for the present moment
- [ ] Sharpened improvement objective confirmed (or amendment noted)
- [ ] All hard constraints confirmed as binding or status-amended
- [ ] Must-Change register count and tiering confirmed
- [ ] Baselines confirmed; UNMEASURED dimensions flagged with
      Phase 2 resolution paths
- [ ] Worst-case mechanism narrative confirmed
- [ ] Phase 1 self-evaluation gate status confirmed
- [ ] Validation Gap Register either lists specific gaps or
      explicitly states none surfaced
- [ ] Phase 1 drift since completion is noted
- [ ] Sources and dates are recorded

---

## Version History

| Version | Date | Source | Summary |
|---------|------|--------|---------|
| v1.0 | 2026-04-22 | Initial authoring | Initial Phase 2 Step 01 prompt. Question-by-question interview mode (exception to Phase 2 default draft-and-react) because validation is confirmation activity. Eight validation categories covering subject identity, objective, constraints, MCs, baselines, worst-case narrative, gates, and gap register. |

---

*Part of the Phase 2 Analysis & Improvement Planning (Existing Projects) Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `analysis-improvement-planning.existing-project.instructions.md`*
*Previous step: `step-00-building-block-discovery.prompt.md`*
*Next step: `step-02-principle-weighting.prompt.md`*
