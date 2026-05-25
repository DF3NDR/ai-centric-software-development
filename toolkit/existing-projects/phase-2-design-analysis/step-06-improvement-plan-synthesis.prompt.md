# Improvement Plan Synthesis — Action Prompt
# Phase 2: Analysis & Improvement Planning (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.1 (revised 2026-05-22 from Diamonds Phase 2 dogfooding run)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Action Prompt + Evaluation Prompt (capstone) |
| **Phase** | Phase 2 — Analysis & Improvement Planning (Existing Projects) |
| **SDD Step** | Implement → Correctness Verification |
| **Artifact Produced** | Improvement Plan + Self-Evaluation Scorecard (the Phase 2 → Phase 3+ handoff) |
| **Principles Addressed** | All six (applied with Step 02 weights) |
| **Feeds Into** | Phase 3 (Design), Phase 4 (Architecture), Phase 5 (Implementation), Phase 6 (Testing), Phase 7 (Deployment) |
| **Companion File** | `analysis-improvement-planning.existing-project.instructions.md` |

---

## Purpose

The Improvement Plan is the primary handoff artifact from Phase 2
to every subsequent phase. Phase 3 design briefs come from here.
Phase 5 task-list seeds come from here. Phase 6 verification methods
come from here (via Step 03 mechanism choices). Phase 7
run-cost projections build on the Step 05 cost modeling.

Step 06 is **synthesis-only**. The five prior Phase 2 artifacts
(Phase 1 Input Validation, Principle Weighting, Mechanism Decisions,
Sequencing and Tiering, Cost Modeling and Capacity Check) contain
everything the Plan needs. Step 06 consolidates, cross-references,
produces the executive summary, and runs the self-evaluation
scorecard.

**If Step 06 is producing net-new decisions, net-new mechanism
choices, net-new sequencing, or net-new cost estimates, something
was missed in Steps 01–05. Pause Step 06 and fix the upstream gap.**

---

## How to Use This Prompt

1. Complete Steps 01 through 05.
2. Open a new AI session with a large context window.
3. Confirm
   `analysis-improvement-planning.existing-project.instructions.md`
   is loaded as project context.
4. Paste all five completed Phase 2 artifacts plus the Phase 1
   Information Report for cross-reference.
5. Paste the **System Instructions** section below as your system
   prompt if not already loaded.
6. Paste the **Kickoff** line to begin.
7. The AI synthesizes in a single pass — this is an action prompt,
   not an interview. Review the produced Improvement Plan and
   self-evaluation scorecard.
8. If the scorecard returns a CONDITIONAL or FAIL gate, cycle back
   to the relevant Phase 2 step and re-run Step 06.

---

## System Instructions

You are a senior improvement planner operating within the AI-Centric
Software Development framework. Your task is to synthesize the five
prior Phase 2 artifacts into the Improvement Plan, and immediately
conduct the built-in self-evaluation against the Step 02
weighted Core Principles.

### Your Behavioral Rules

- **Synthesize, do not generate net-new content.** Step 06's job
  is to consolidate, cross-reference, and produce the executive
  framing. Every mechanism choice in the Plan must trace to Step 03.
  Every sequencing decision must trace to Step 04. Every cost row
  must trace to Step 05. If you find yourself producing a new
  mechanism, a new sequence, or a new cost — stop and surface that
  the upstream artifact has a gap.
- **Produce the Plan in the specified output format.** Downstream
  phases consume this Plan as AI input context; consistent
  structure matters.
- **Produce an executive summary that names the defining mechanism.**
  Phase 1's Step 06 surfaced "the gap between what the system
  claims and what the system can prove" as the defining mechanism
  for Diamonds. Phase 2's executive summary names the Plan's own
  defining synthesis — typically arising from the Step 04
  worst-case narrative or the cost-concentration analysis or a
  cross-artifact pattern.
- **Apply scorecard rigor discipline.** CONDITIONAL is preferred
  over PASS-with-caveats. A CONDITIONAL with explicit rationale
  surfaces a decision point for the next phase; a buried caveat
  in a PASS is easier to miss. Aim for **4–5 PASS + 1–2
  CONDITIONAL** on a well-executed Phase 2. Uniformly-PASS
  scorecards usually indicate insufficient self-evaluation rigor.
- **FAIL is reserved for genuinely blocking gaps.** Where a
  principle rates CONDITIONAL, state the specific Phase 3
  decision the next phase must make to resolve it — never just
  "some caveats exist."
- **Produce Phase 3 design briefs.** Mechanism choices that
  involve breaking changes, new architectural patterns, or
  significant API design need Phase 3 design work. The Plan
  surfaces them as design briefs — one per MC requiring design.
- **Produce a Phase 5 task-list seed.** Mechanism choices already
  contain acceptance criteria seeds (from Step 03 verification
  methods). The Plan consolidates these into a task-list seed
  ordered by Step 04 sequencing, with Step 05 cost tags. Phase 5
  refines into formal tasks; Phase 5 does not restart from zero.
- **Preserve worst-case mechanism narrative from Step 04.** Phase 2's
  worst-case narrative (and its named common mechanism) is the
  Plan's structural-fragility signal. The Plan must carry it
  forward, not bury it.
- **Apply the Version & Identity Re-Verification discipline.**
  Confirm the subject is at the version captured in Step 01 — if
  the subject has released between Phase 2 steps, note any drift
  the Plan must accommodate.
- **If Step 05 uses BELIEVED multipliers, Section 10 must surface
  a Phase 7 calibration handoff.** *(New in v1.1 per Diamonds
  dogfooding observation P2-Obs-04, Cluster C.)* The three-quantity
  cost model uses AI-acceleration multipliers and tokens-per-dev-hour
  ratios that are BELIEVED at v1.0 of any project (no historical
  data). Phase 7 operational tracking is the mechanism that
  graduates these from BELIEVED to ESTIMATED and eventually to
  MEASURED. Whenever Step 05's cost rows include BELIEVED-tagged
  multiplier or ratio inputs, the Improvement Plan's Section 10
  (Gaps and Forward Handoffs) must include an explicit Phase 7
  calibration-handoff row naming: (a) what should be tracked during
  Phase 5 execution, (b) what calibration data the tracking produces,
  (c) how the data feeds the next cycle's Phase 2 cost modeling.
  Without this handoff, the BELIEVED multipliers stay BELIEVED
  forever and the cost model never improves.

### Synthesis Categories

The Improvement Plan consolidates into these sections:

1. **Executive Summary** — one paragraph framing the Plan's
   defining mechanism
2. **The Plan** — tiered sequence with per-MC entries
3. **Cost Summary** — per-tier totals with tag distribution
4. **Principle-Weighted Scorecard** — resolves Phase 1's CONDITIONAL
   on Scoring & Metrics
5. **Minimum-Viable-Completion Floor and Stretch Scope** — from
   Step 04
6. **Phase 3 Design Briefs** — one per MC requiring design work
7. **Phase 5 Task-List Seed** — ordered tasks with acceptance
   criteria seeds
8. **Worst-Case Plan-Failure Narrative** — preserved from Step 04
9. **Self-Evaluation Scorecard** — the Phase 2 → Phase 3 phase gate
10. **Gaps and Forward Handoffs** — explicit enumeration **including
    Phase 7 calibration handoff when applicable** *(v1.1 addition)*
11. **Source & Evidence Register** — which Phase 2 artifacts
    informed what

---

## Kickoff

> Paste this line to begin. All five Phase 2 artifacts and the
> Phase 1 Information Report should be loaded as context.
```
Please run Phase 2 synthesis. Consolidate the five Phase 2
artifacts into the Improvement Plan, then run the self-evaluation
scorecard. Apply scorecard rigor — CONDITIONAL preferred over
PASS-with-caveats. Apply synthesis-only discipline — no net-new
decisions. If Step 05 used BELIEVED multipliers, include Phase 7
calibration handoff in Section 10.
```

---

## Output Format

```markdown
# Improvement Plan
# [Subject Name] — Phase 2 Cycle

**Plan Date:** [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]
**Phase 1 Completion Date:** [date]
**Phase 2 Completion Date:** [today]
**Subject Version at Plan Date:** [version]

---

## Section 1: Executive Summary

### 1.1 The Cycle in One Paragraph

[Three-to-five sentence framing: what the subject is, what Phase 1
established, what the Plan proposes, what completing it produces.]

### 1.2 The Plan's Defining Mechanism

[One paragraph naming the synthesis that holds the Plan together —
typically arising from the Step 04 worst-case narrative or a
cross-artifact pattern. Examples: "The Plan front-loads
foundational cleanup because [reason], coordinates breaking
changes in a single block because [reason], and lands productization
last because [reason]."]

### 1.3 Principal Tensions Carried Forward

[Brief enumeration of principal tensions identified during Phase 1
that the Plan addresses or explicitly defers.]

### 1.4 Plan-vs-Capacity Fit

[Single-sentence assessment: "Plan fits the capacity envelope" /
"Plan fits with stretch scope cut" / "Plan exceeds capacity — see
Section 8."]

### 1.5 Principle-Weighted Posture

[Restate the Step 02 weights in one sentence: e.g., "This is a
first-productization-pass brownfield posture: Maintainability and
Security elevated 1.5×, others baseline."]

---

## Section 2: The Plan

### 2.1 Tier 1 — [Tier Name]

**Principle-weighted rationale:** [text from Step 04]

| MC ID | Chosen Mechanism | Cost (Tag) | Verification Method | Dependencies | Phase 3 Design Brief? |
|-------|-----------------|-----------|--------------------|--------------|----------------------|
| MC-XX | [text from Step 03] | [Step 05 value, tag] | [Step 03 verification method] | [Step 03 dependencies] | Yes / No |
| [...] | [...] | [...] | [...] | [...] | [...] |

### 2.2 Tier 2 — [Tier Name]
[Same structure]

### 2.3 Tier 3 — [Tier Name]
[Same structure]

---

## Section 3: Cost Summary

### 3.1 Per-Tier Totals

| Tier | Total | Tag Distribution | Cost-Concentration MCs |
|------|-------|------------------|------------------------|
| Tier 1 | [...] | [...] | [...] |
| Tier 2 | [...] | [...] | [...] |
| Tier 3 | [...] | [...] | [...] |
| **Plan Total** | [...] | [...] | [list across all tiers] |

### 3.2 Capacity-vs-Envelope Fit

[From Step 05; restate the assessment]

---

## Section 4: Principle-Weighted Scorecard

### 4.1 Phase 1 Scoring & Metrics CONDITIONAL — Resolved

Phase 1 Step 06 flagged Scoring & Metrics as CONDITIONAL because
principle weights were not yet assigned. This Plan resolves that
CONDITIONAL: weights are now assigned (Step 02), applied across
mechanism choices (Step 03), sequencing (Step 04), and cost
modeling (Step 05).

### 4.2 Principle Weights (Reference)

| Principle | Weight | Source |
|-----------|--------|--------|
| Security | [X]× | Step 02 §[X] |
| Maintainability | [X]× | Step 02 §[X] |
| Economics | [X]× | Step 02 §[X] |
| Operations | [X]× | Step 02 §[X] |
| Scoring & Metrics | [X]× | Step 02 §[X] |
| Correctness Verification | [X]× | Step 02 §[X] |

---

## Section 5: Minimum-Viable-Completion Floor and Stretch Scope

### 5.1 Minimum-Viable Floor

[From Step 04 §3]

**Floor MCs:** [list]
**Principle-weighted rationale:** [text]
**What gets cut first:** [ordered list above floor]

### 5.2 Stretch Scope

[From Step 04 §4]

---

## Section 6: Phase 3 Design Briefs

For each MC requiring design work, produce a brief:

### Brief for MC-XX

**MC:** [text]
**Chosen Mechanism (from Step 03):** [text]
**Design questions Phase 3 must resolve:**
- [question 1 — e.g., "What is the migration path for adopters
  currently on the prior API?"]
- [question 2 — e.g., "What does the extension contract look
  like for external implementers of the strategy?"]

**Constraints inherited from Phase 1:**
- [list — e.g., HC-* entries that affect design]

**Verification method (for Phase 6 forward awareness):**
[from Step 03]

---

[Repeat for each design-requiring MC]

---

## Section 7: Phase 5 Task-List Seed

Tasks ordered by Step 04 sequencing, with Step 05 cost tags and
Step 03 acceptance criteria seeds. Phase 5 refines into formal
tasks; this seeds the work.

### Tier 1 Task Seeds

| Task ID | Source MC | Description | Acceptance Criteria Seed | Cost (Tag) |
|---------|-----------|-------------|--------------------------|-----------|
| T1-001 | MC-XX | [text] | [from Step 03 verification method] | [Step 05 value, tag] |
| [...] | [...] | [...] | [...] | [...] |

### Tier 2 Task Seeds
[Same structure]

### Tier 3 Task Seeds
[Same structure]

---

## Section 8: Worst-Case Plan-Failure Narrative (Preserved)

### 8.1 Failure Branches (from Step 04)

[Restate three or more failure branches]

### 8.2 Common Mechanism (from Step 04)

[Restate the named common mechanism producing all branches]

### 8.3 Plan Mitigation (from Step 04)

[Restate how the Plan addresses the common mechanism]

### 8.4 Residual Risk

[If mitigation is partial: explicitly name the residual risk and
the Phase 7 watch-trigger that should escalate it]

---

## Section 9: Self-Evaluation Scorecard

Phase 2 deliverables rated against the six Core Principles using
Step 02 weights.

| Principle | Weight | Rating | Rationale |
|-----------|--------|--------|-----------|
| Security | [X]× | PASS / CONDITIONAL / FAIL | [text — if CONDITIONAL, name the specific Phase 3 decision required to resolve] |
| Maintainability | [X]× | [...] | [...] |
| Economics | [X]× | [...] | [...] |
| Operations | [X]× | [...] | [...] |
| Scoring & Metrics | [X]× | PASS | [Phase 1 CONDITIONAL resolved by this Plan] |
| Correctness Verification | [X]× | [...] | [...] |

**Overall Phase 2 self-assessment:** [N PASS + M CONDITIONAL + K FAIL]

**Phase 3 Readiness:** READY / READY WITH REMEDIATION (list
CONDITIONAL items with named Phase 3 actions) / CYCLE BACK (list
FAIL items and required Phase 2 amendment)

---

## Section 10: Gaps and Forward Handoffs

### 10.1 Decisions Deferred to Phase 3

| Decision | Phase 3 Step | Notes |
|----------|-------------|-------|
| [text] | [...] | [...] |

### 10.2 Decisions Deferred to Phase 5

| Decision | Phase 5 Step | Notes |
|----------|-------------|-------|
| [text] | [...] | [...] |

### 10.3 Items Acknowledged as Unresolved

[List with rationale for accepting; Phase 7 watch-triggers]

### 10.4 Phase 7 Calibration Handoff *(New in v1.1; required when Step 05 uses BELIEVED multipliers)*

*This subsection is required whenever Step 05's cost rows include
BELIEVED-tagged AI-acceleration multipliers or
tokens-per-dev-hour ratios. It names the operational tracking that
Phase 7 must establish so that future cycles graduate BELIEVED
inputs to MEASURED ones.*

**What Phase 7 should track during Phase 5 execution:**

| Quantity | Tracking Mechanism | Tag Status at Plan Date | Target Tag After Phase 5 |
|----------|-------------------|-------------------------|--------------------------|
| Actual dev-hours per MC (Senior baseline equivalent) | Time-tracking system or post-MC reflection log | UNMEASURED / ESTIMATED at v1.0 | MEASURED post-Phase 5 |
| Actual maintainer-hours per MC | Same tracking system | UNMEASURED / ESTIMATED | MEASURED |
| Implied AI-acceleration multiplier per MC and per category | Derived: dev-hours ÷ maintainer-hours | BELIEVED at v1.0 | ESTIMATED after first cycle; MEASURED after 2-3 cycles |
| Actual token usage per MC | API usage logs or session reports | UNMEASURED at v1.0 | MEASURED post-Phase 5 |
| Implied tokens-per-dev-hour ratio | Derived: tokens ÷ dev-hours | BELIEVED at v1.0 (default 6,000/hr) | ESTIMATED after first cycle |
| Actual API cost per MC | Billing data or token × pricing computation | UNMEASURED at v1.0 | MEASURED post-Phase 5 |

**How the calibration data feeds the next cycle's Phase 2 cost
modeling:**

- Per-category multipliers (mechanical cleanup 10×, doc authorship
  8×, config edit 5×, novel design 3×) are validated or revised
  against the actual ratios observed across Phase 5 work
- Tokens-per-dev-hour ratio is validated or revised per category
  (some work is more API-intensive than others)
- Future Phase 2 Step 05 cost rows can use the calibrated values
  with ESTIMATED tags instead of BELIEVED, increasing the trust
  downstream phases place in the cost projections

**Phase 7 toolkit forward implication:**

When the Phase 7 (Deployment & Evolution) toolkit is authored, it
should include the operational-tracking pattern for these
quantities as a first-class capability — not as an afterthought.
The data the practitioner collects during Phase 5 execution should
flow into Phase 7's tracking surface as standard practice. *(This
note may become a Phase 7 toolkit requirement once that toolkit is
authored.)*

---

## Section 11: Source & Evidence Register

- **Phase 1 Current-State Information Report** — primary upstream
  input
- **Phase 2 Step 01 (Phase 1 Input Validation)** — confirmed
  Phase 1 understanding
- **Phase 2 Step 02 (Principle Weighting)** — weights applied
  throughout
- **Phase 2 Step 03 (Mechanism Decisions)** — chosen mechanisms,
  alternatives, verification methods
- **Phase 2 Step 04 (Sequencing and Tiering)** — tiers, dependencies,
  minimum-viable floor, worst-case narrative
- **Phase 2 Step 05 (Cost Modeling and Capacity Check)** — per-MC
  costs with tags, capacity check, re-sequencing recommendation
- **Practitioner confirmations** — final authority throughout
```

---

## Self-Evaluation Scorecard Discipline

After producing the Plan, run the Self-Evaluation Scorecard in
Section 9 with these checks:

For each principle:

- **PASS** — Sufficient for Phase 3 to proceed on this dimension.
- **CONDITIONAL** — Sufficient with documented caveats. Must name
  the specific Phase 3 decision required to resolve. A
  CONDITIONAL without a named resolution decision is a buried
  caveat masquerading as a gate status.
- **FAIL** — Insufficient. Phase 3 cannot responsibly proceed on
  this dimension. Cycle back to Phase 2 to fill the gap and
  re-run Step 06.

**Target distribution on a well-executed Phase 2:** 4–5 PASS + 1–2
CONDITIONAL. Uniformly-PASS suggests perfunctory self-evaluation.
Multiple FAILs suggest Phase 2 hasn't done its work.

**Common CONDITIONALs at Phase 2 completion:**
- *Operations CONDITIONAL* — Plan establishes mechanisms but
  Phase 3 must design specific observability touchpoints for
  the chosen mechanisms.
- *Correctness Verification CONDITIONAL* — Plan names verification
  methods per mechanism, but Phase 3 must produce specific
  verification artifacts (property-test definitions, contract
  specifications, audit procedures).
- *Security CONDITIONAL* — Plan addresses security MCs but a
  specific threat-modeling exercise belongs in Phase 3 (or
  Phase 4 for module-level threats).

---

## Evaluation Checklist

Before accepting the Improvement Plan:

- [ ] Executive summary names the Plan's defining mechanism
- [ ] Every MC in the Plan has a chosen mechanism (from Step 03)
- [ ] Every MC has a cost row with tag (from Step 05)
- [ ] Every MC has a verification method (from Step 03)
- [ ] Per-tier and plan-total cost summaries match Step 05
- [ ] Plan-vs-capacity assessment is restated from Step 05
- [ ] Phase 1 Scoring & Metrics CONDITIONAL is explicitly resolved
- [ ] Step 02 weights are restated for forward reference
- [ ] Minimum-viable floor and stretch scope are stated explicitly
- [ ] Phase 3 design briefs produced for every design-requiring MC
- [ ] Phase 5 task-list seed organized by Step 04 tier sequence
- [ ] Worst-case narrative and common mechanism are preserved from
      Step 04 (not regenerated)
- [ ] Self-evaluation scorecard produces gate status per principle
- [ ] Each CONDITIONAL rating names the specific Phase 3 decision
      required to resolve
- [ ] No net-new decisions, mechanisms, sequencing, or costs were
      introduced during synthesis
- [ ] **Phase 7 calibration handoff section (§10.4) is present
      whenever Step 05 used BELIEVED multipliers** *(new in v1.1)*
- [ ] Sources and dates are recorded

---

## Version History

| Version | Date | Source | Summary |
|---------|------|--------|---------|
| v1.0 | 2026-04-22 | Initial authoring | Initial Phase 2 Step 06 prompt (capstone). Synthesis-only discipline applied throughout — no net-new decisions during synthesis. Scorecard rigor discipline: CONDITIONAL preferred over PASS-with-caveats, target 4–5 PASS + 1–2 CONDITIONAL, each CONDITIONAL must name the specific Phase 3 decision required to resolve. Phase 3 design briefs and Phase 5 task-list seed are direct outputs (not afterthoughts) to make the Phase 2 → Phase 3 / Phase 5 handoff explicit. |
| **v1.1** | **2026-05-22** | **Diamonds Phase 2 dogfooding run (P2-Obs-04, Cluster C)** | Added Phase 7 calibration handoff requirement when Step 05 uses BELIEVED multipliers. New §10.4 in Output Format with structured table for tracking dev-hours, maintainer-hours, AI-acceleration multipliers, token usage, and API cost per MC during Phase 5 execution. New behavioral rule directing AI to include §10.4 when applicable. Evaluation Checklist item added. Forward-looking note about Phase 7 toolkit capturing this pattern as first-class capability. |

---

*Final artifact of the Phase 2 Analysis & Improvement Planning (Existing Projects) Tool Set — v1.1*
*AI-Centric Software Development Playbook*
*Companion file: `analysis-improvement-planning.existing-project.instructions.md`*
*Previous step: `step-05-cost-modeling-and-capacity-check.prompt.md`*
*Handoff to: Phase 3 (Design & Technical Analysis), Phase 4 (Architecture & Modular Design), Phase 5 (Implementation), Phase 6 (Testing & Audit), Phase 7 (Deployment & Evolution)*
