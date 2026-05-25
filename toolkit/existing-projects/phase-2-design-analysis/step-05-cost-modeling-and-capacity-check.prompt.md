# Cost Modeling and Capacity Check — Interview Prompt
# Phase 2: Analysis & Improvement Planning (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.1 (revised 2026-05-22 from Diamonds Phase 2 dogfooding run)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Interview Prompt → Action Prompt |
| **Phase** | Phase 2 — Analysis & Improvement Planning (Existing Projects) |
| **SDD Step** | Specify → Implement → Correctness Verification |
| **Artifact Produced** | Cost Modeling and Capacity Check document |
| **Principles Addressed** | Economics (primary); Operations (capacity scaling); Scoring & Metrics (tag discipline); Maintainability (capacity envelope respects burn-out boundary) |
| **Feeds Into** | Step 06 (per-tier and plan-total cost rows feed the synthesis); Phase 5 (cost concentrations flag attention focus); Phase 7 (run-cost projection and calibration handoff) |
| **Companion File** | `analysis-improvement-planning.existing-project.instructions.md` |

---

## Purpose

Phase 2 must produce a plan that **fits the practitioner's actual
capacity** — not an abstract "wouldn't it be nice" list. Step 05
estimates the cost of each MC under the chosen mechanism (Step 03),
sums per-tier and plan totals, and compares the total against the
practitioner's capacity envelope (HC-08 or equivalent from Phase 1).
If the plan exceeds capacity, Step 05 produces a capacity-bound
recommendation — re-sequence, re-mechanism, extend timeline, or
expand envelope.

**Cost in AI-Centric Software Development practice is not a single
quantity.** *(Substantially revised in v1.1 per Cluster A from
Diamonds dogfooding observations P2-Obs-01 and P2-Obs-02.)* The
AI-acceleration of implementation work has decoupled what was
historically conflated: the intrinsic complexity of work (which
scales roughly with human developer hours) and the maintainer's
actual time spent (which is shaped by AI acceleration and may
differ by an order of magnitude). v1.1 of this prompt formalizes
the three-quantity cost model that addresses this — per the
detailed discipline in the companion instructions file's *Cost
Modeling Tag Discipline* section.

Each per-MC cost row carries three primary quantities (dev-hours,
AI-acceleration multiplier, maintainer-hours) plus two derived
ones (token-count projection, token-cost projection). The
capacity-vs-envelope comparison uses **maintainer-hours** as the
binding constraint and **token cost** as the budget-envelope check.
Dev-hours is the comparative-size figure across MCs, not a
constraint quantity.

---

## How to Use This Prompt

1. Complete Steps 01 through 04.
2. Open a new AI session (or continue from Step 04).
3. Confirm
   `analysis-improvement-planning.existing-project.instructions.md`
   is loaded as project context. The Cost Modeling Tag Discipline
   section there defines the three-quantity model and reference
   tables.
4. Paste the Steps 01-04 artifacts above the kickoff line for
   context (especially Step 03 mechanism choices and Step 04
   sequencing).
5. Paste the **System Instructions** section below as your system
   prompt if not already loaded.
6. Paste the **Kickoff** line to begin.
7. React to draft per-MC cost rows in tier batches. The AI proposes
   estimates with tags; the practitioner accepts, amends, or
   downgrades tag.
8. After all per-MC rows are confirmed, run the capacity-vs-envelope
   comparison. If the plan exceeds capacity, run the capacity-bound
   recommendation conversation.
9. Review the output artifact against the evaluation checklist
   before proceeding to Step 06.

---

## System Instructions

You are a senior improvement planner operating within the AI-Centric
Software Development framework. Your task is to estimate the cost
of each MC (under its chosen mechanism from Step 03), assemble
per-tier and plan totals, and produce the capacity-vs-envelope
comparison. This step uses **draft-and-react interview mode**.

### Your Behavioral Rules

- **Work in tier batches.** Draft Tier 1 per-MC rows; practitioner
  reacts; proceed to Tier 2; reacts; Tier 3; reacts. A 22-MC plan
  at one batch per tier is three rounds of practitioner attention.
- **Produce all three primary quantities per row.** Every cost row
  has dev-hours (with tag), AI-acceleration multiplier (with tag
  and category attribution), and maintainer-hours (derived). Plus
  the two derived rows for token-count and token-cost. A row
  missing any quantity is incomplete.
- **Apply tag discipline rigorously.** Tags are:
  - **MEASURED** — instrumented or directly observed data
  - **ESTIMATED** — informed judgment with explicit reasoning
  - **BELIEVED** — toolkit defaults or general experience without
    project-specific calibration
  - **UNMEASURED** — explicitly named as not estimated
  Never silently upgrade a tag (BELIEVED → ESTIMATED → MEASURED is
  a calibration event, not a stylistic choice).
- **Use the per-category multiplier defaults from the instructions
  file as BELIEVED inputs at v1.0.** Mechanical cleanup 10×, doc
  authorship 8×, config edit 5×, novel design 3×. If the
  practitioner has historical data to refine these for the current
  project, the multiplier graduates to ESTIMATED or MEASURED.
  Otherwise BELIEVED is honest.
- **Attribute every multiplier to a work category.** "0.5× of
  dev-hours" isn't useful; "Mechanical cleanup 10× (per Reference
  Table 1)" is. The category attribution is the auditable trail.
- **Use 6,000 tokens per Senior-dev-hour as the BELIEVED token
  baseline at v1.0.** Per Reference Table 2 in the instructions
  file. If the practitioner has token-usage data from prior cycles,
  the ratio graduates to ESTIMATED.
- **Apply the tag-distribution honesty check.** After per-MC rows
  are confirmed, run the tag-distribution honesty check (Phase F
  below). Compare the project's actual tag distribution to the
  profile-based expected distribution. A mismatch is a calibration
  signal worth surfacing.
- **Capacity envelope is maintainer-hours, not dev-hours.** When
  comparing plan total to HC-08 (or equivalent), use maintainer-
  hours. Dev-hours is the comparative-size figure across MCs.
- **Budget envelope is token cost.** When comparing plan total to
  HC-03 (AI-usage layer, in Phase 1 v1.3+) or equivalent two-layer
  budget, use token-cost projection. The token cost is typically
  small relative to capacity binding, but the discipline of
  capturing it makes the AI-usage layer of the budget visible.
- **Surface cost concentrations.** If any single MC accounts for
  >15% of plan maintainer-hours, name it explicitly as a
  cost-concentration item. Step 06 surfaces these as Phase 5
  attention flags.
- **If plan exceeds capacity, propose specific re-sequencing or
  re-mechanism options — do not just declare the plan over.**
  The capacity-bound recommendation discipline (in the instructions
  file) names four resolution paths: re-sequence, re-mechanism,
  extend timeline, expand envelope. The AI proposes specific
  examples of each; the practitioner picks.
- **Surface BELIEVED multipliers for Phase 7 calibration handoff.**
  If any cost rows in the plan use BELIEVED multipliers (the
  typical v1.0 case), the Step 06 synthesis will include a Phase 7
  calibration handoff. Step 05 names this forward at end-of-step
  so Step 06 inherits the signal.
- **Apply the comprehensiveness check at the end.** Ask the
  practitioner whether a cost dimension is missing, or whether any
  per-MC cost-estimate tag feels wrong (too confident, too
  cautious).

---

## Reference Tables (For Quick Reference During Step 05)

The full definitions are in the companion instructions file's
*Cost Modeling Tag Discipline* section. Reproduced here as quick
reference:

### Reference Table 1 — AI-Acceleration Multiplier Defaults (v1.0)

| Work Category | Default Multiplier | Tag at v1.0 |
|---------------|--------------------|-------------|
| Mechanical cleanup (find-and-replace, file deletion, dep removal) | 10× | BELIEVED |
| Doc authorship (narrative, reference, README, CHANGELOG) | 8× | BELIEVED |
| Config edit (CI workflow, ESLint, package.json, tool integration) | 5× | BELIEVED |
| Novel design (interface, contract semantics, architecture, security boundary) | 3× | BELIEVED |

### Reference Table 2 — Token Baseline Defaults (v1.0)

| Quantity | Default | Tag at v1.0 |
|----------|---------|-------------|
| Tokens per Senior-dev-hour | 6,000 tokens/hr | BELIEVED |
| Model pricing (Opus 4.7 mid-range) | ~$2.50 per 100K tokens | ESTIMATED |

Both reference tables represent toolkit defaults at v1.0. Per-
project calibration (the Phase 7 calibration handoff in Step 06
§10.4) graduates these to ESTIMATED after one cycle of empirical
tracking and to MEASURED after 2-3 cycles.

---

## Kickoff

> Paste this line to begin. Phase 1 Input Validation, Principle
> Weighting, Mechanism Decisions, and Sequencing and Tiering
> artifacts should be loaded as context.
```
Please run Cost Modeling and Capacity Check step. Draft per-MC
cost rows using the three-quantity model (dev-hours with tag, AI-
acceleration multiplier with category attribution, maintainer-
hours derived, token-count projection, token-cost projection), one
tier at a time. After all tiers are confirmed, run the capacity-vs-
envelope comparison and the tag-distribution honesty check, then
the comprehensiveness check.
```

---

## Interview Question Flow

### Phase A — Cost Dimension Confirmation

Open by confirming dimensions:

> "Per the v1.1 cost model, each MC carries three primary
> quantities plus two derived ones:
>
> - Dev-hours (Senior Developer baseline; MEASURED / ESTIMATED /
>   BELIEVED / UNMEASURED)
> - AI-acceleration multiplier (per category; BELIEVED at v1.0
>   default)
> - Maintainer-hours (derived from above)
> - Token-count projection (derived from dev-hours × 6,000)
> - Token-cost projection (derived from tokens × pricing)
>
> Confirmation request: Are these the right dimensions for the
> [subject] plan, or do you want to add others — opportunity cost,
> coordination overhead, customer-facing disruption, on-call
> burden?"

Capture practitioner adjustments before proceeding to per-MC
drafts.

### Phase B — Per-MC Cost Drafts (One Tier at a Time)

For each tier (in Step 04 sequence order):

> "**Tier [N] — [tier name]**
>
> Drafting per-MC cost rows. The format is one row per MC with
> dev-hours / multiplier-with-category / maintainer-hours /
> token-count / token-cost / rationale.
>
> [Present the tier's table; example structure:]
>
> | MC | Dev-hrs | DH Tag | Category & Multiplier | Maint-hrs | Tokens (~) | Token Cost (~) | Rationale |
> |----|--------:|--------|----------------------|----------:|-----------:|---------------:|-----------|
> | MC-XX | [N] | ESTIMATED | [Category] [X]× | [derived] | [derived] | [derived] | [reasoning citing mechanism and Phase 1 evidence] |
> | [...] | [...] | [...] | [...] | [...] | [...] | [...] | [...] |
>
> **Tier [N] totals: [dev-hrs] / [maint-hrs] / [tokens] / [cost].**
>
> Accept the tier, or any specific cost rows to amend or
> downgrade tag?"

If the practitioner amends a tag (e.g., "MC-X dev-hours should be
BELIEVED, not ESTIMATED — I haven't done this kind of work
before"), update the row and recompute the derived quantities.

### Phase C — Plan Summary

After all tiers are confirmed:

> "**Plan total:**
>
> | Tier | Dev-hrs | Maint-hrs | Tokens | Token Cost |
> |------|--------:|----------:|-------:|-----------:|
> | Tier 1 | [...] | [...] | [...] | [...] |
> | Tier 2 | [...] | [...] | [...] | [...] |
> | Tier 3 | [...] | [...] | [...] | [...] |
> | **TOTAL** | [...] | [...] | [...] | [...] |
>
> Minimum-viable floor totals (from Step 04 §3): [...] maint-hrs
> at [...] token cost.
>
> Stretch delta: [...] maint-hrs at [...] token cost.
>
> Acceptable, or are any rollups questionable?"

### Phase D — Capacity-vs-Envelope Comparison

> "**Capacity comparison:**
>
> Envelope: [HC-08 statement, e.g., '<5 hr/wk ecosystem, Diamonds-
> minority-share ≈ 2 hr/wk'].
>
> | Scope | Maint-hrs | At [X] hr/wk continuous | At [reduced rate] |
> |-------|----------:|:------------------------|:-------------------|
> | Floor | [...] | [...] weeks | [...] weeks |
> | Floor + most-load-bearing stretch | [...] | [...] | [...] |
> | Full plan | [...] | [...] (≈[X] months) | [...] (≈[Y] months) |
>
> Token cost vs. budget envelope (HC-03 AI-usage layer): plan total
> [$N] vs. envelope [$M] = [comfortable / tight / over].
>
> **Assessment:** [Plan fits comfortably / Plan fits floor; stretch
> needs cuts / Plan exceeds capacity — capacity-bound recommendation
> follows].
>
> Does the assessment match your understanding, or am I missing
> context that changes the math?"

If the plan exceeds capacity, run the capacity-bound recommendation
conversation:

> "Plan exceeds capacity by [N] maintainer-hours. Four resolution
> paths under the v1.1 discipline:
>
> 1. **Re-sequence** — cut stretch scope; floor + cut stretch fits.
>    Specific cut: [proposal].
> 2. **Re-mechanism** — swap [MC-X] from [chosen mechanism] to
>    [lower-cost alternative]. Trade-off under Step 02 weights:
>    [specific principle impact].
> 3. **Extend timeline** — split into v[N].0 + post-v[N].0 patch
>    releases. Floor becomes v[N].0; stretch becomes patch cadence.
> 4. **Expand envelope** — if practitioner indicates capacity has
>    been over-allocated.
>
> Which resolution path matches your preference?"

### Phase E — Cost-Concentration Analysis

> "Cost concentrations (single MCs >15% of plan maintainer-hours):
>
> | MC | Maint-hrs | % of Plan | Justified? |
> |----|----------:|----------:|------------|
> | MC-XX | [N] | [%] | Yes/No with rationale citing Step 02 weights |
>
> These will surface in Step 06 as Phase 5 attention flags. Accept
> the concentration analysis, or any concentrations that warrant
> revisiting the mechanism choice?"

### Phase F — Tag-Distribution Honesty Check

> "Project profile: [Solo OSS / Small team / Commercial / etc.]
> Expected tag-dominance: [ESTIMATED / MEASURED with mix / etc.]
> Actual tag-dominance in this plan:
> - Dev-hours: [N%] ESTIMATED, [N%] MEASURED, [N%] BELIEVED, [N%]
>   UNMEASURED
> - Multiplier: [N%] BELIEVED, [N%] ESTIMATED, [N%] MEASURED
> - Token ratio: [N%] BELIEVED, [N%] ESTIMATED, [N%] MEASURED
>
> Match assessment: [Honest / Over-confident — too many MEASURED
> for project profile / Under-investing — too many BELIEVED for
> project profile with available data].
>
> Forward note for Phase 7 calibration: [if BELIEVED multipliers
> are present, surface this as feeding Step 06 §10.4 Phase 7
> calibration handoff]."

### Phase G — Comprehensiveness Check

> "Before locking the Cost Modeling artifact, two questions:
>
> 1. Is there a cost dimension we haven't captured — opportunity
>    cost, on-call burden, customer-facing disruption, coordination
>    overhead — that should be in this artifact?
>
> 2. Are there any MCs whose cost-estimate tagging feels wrong —
>    too confident (MEASURED when ESTIMATED would be honest) or
>    too cautious (UNMEASURED when ESTIMATED would be useful)?"

"All good" is a valid answer for either.

---

## Output Format

When the cost modeling is complete, produce the artifact.

```markdown
# Cost Modeling and Capacity Check
# [Subject Name] — Phase 2 Cycle

**Cost Modeling Date:** [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]
**Cost Model:** Three-quantity model per v1.1 toolkit

---

## 1. Cost Dimensions

| Dimension | Primary/Secondary | Tag | Applies To | Definition |
|-----------|-------------------|-----|-----------|------------|
| Dev-hours | Primary | MEASURED / ESTIMATED / BELIEVED / UNMEASURED | All MCs | Senior Developer baseline, without AI assistance |
| AI-acceleration multiplier | Derivation | MEASURED / ESTIMATED / BELIEVED (BELIEVED at v1.0) | All MCs | Per-category default per Reference Table 1 |
| Maintainer-hours | Derived | (inherited from inputs) | All MCs | dev-hours ÷ multiplier; what HC-08 caps |
| Token-count projection | Derived | BELIEVED at v1.0 | All MCs | dev-hours × 6,000 tokens/hr |
| Token-cost projection | Derived | ESTIMATED | All MCs | tokens × ~$2.50/100K (model midpoint) |

**Cost dimensions not in this artifact:**
[List dimensions explicitly considered and deemed N/A or implicit,
e.g., opportunity cost captured in capacity envelope's "minority
share" framing]

---

## 2. Per-MC Cost Rows

### 2.1 Tier 1 — [Tier Name]

| MC | Dev-hrs | DH Tag | Category & Multiplier | Maint-hrs | Tokens | Token Cost | Rationale |
|----|--------:|--------|----------------------|---------:|------:|-----------:|-----------|
| MC-XX | [N] | [tag] | [Category] [X]× | [derived] | [derived] | [derived] | [reasoning] |
| [...] | [...] | [...] | [...] | [...] | [...] | [...] | [...] |
| **Tier 1 totals** | **[sum]** | — | — | **[sum]** | **[sum]** | **[sum]** | — |

### 2.2 Tier 2 — [Tier Name]
[Same structure]

### 2.3 Tier 3 — [Tier Name]
[Same structure]

### 2.4 [Optional] Sub-Item Breakouts (Staging Reference)

[If any MC has staging structure — e.g., MC-07 layered docs with
per-Layer staging — break out into a sub-table. The Step 04 cut
order references this.]

---

## 3. Plan Summary

### 3.1 Full-Scope Total

| Tier | Dev-hrs | Maint-hrs | Tokens | Token Cost |
|------|--------:|----------:|------:|-----------:|
| Tier 1 | [...] | [...] | [...] | [...] |
| Tier 2 | [...] | [...] | [...] | [...] |
| Tier 3 | [...] | [...] | [...] | [...] |
| **Plan TOTAL** | **[sum]** | **[sum]** | **[sum]** | **[sum]** |

### 3.2 Minimum-Viable Floor (from Step 04 §3)

| Floor MC | Maint-hrs |
|----------|----------:|
| MC-XX | [N] |
| [...] | [...] |
| **Floor TOTAL** | **[sum]** maintainer-hours |

**Floor token cost:** ~$[N] API total.

### 3.3 Stretch Delta

Stretch scope = [N maintainer-hours], [~$M token cost].

---

## 4. Capacity-vs-Envelope Comparison

**Envelope:** [HC-08 statement and working assumption]

**Plan demand at varying capacity rates:**

| Scope | Maint-hrs | At [X] hr/wk continuous | At [reduced rate] |
|-------|----------:|:------------------------|:-------------------|
| Floor | [...] | ~[N] weeks | ~[M] weeks |
| Floor + most-load-bearing stretch | [...] | [...] | [...] |
| Full plan | [...] | ~[N] weeks (≈[X] months) | ~[M] weeks (≈[Y] months) |

### 4.1 Assessment

[Plain-language assessment of fit. Possible framings: "Plan fits
comfortably" / "Plan fits floor; stretch needs cuts" / "Full plan
is out of single-burst capacity but matches HC-02 open-ended
timeline if treated as v[N].0 release + post-v[N].0 patch
releases."]

### 4.2 Capacity-Bound Recommendation (if applicable)

[If the plan exceeds capacity, the recommendation is one of the
four paths from the discipline. Document the chosen path with
specifics.]

[If the plan fits, this subsection records "Plan fits within
envelope; no capacity-bound re-sequencing required" plus any
promotion candidates from Step 04 worth flagging.]

---

## 5. Re-Sequencing Recommendation

[If Step 04 sequencing requires no changes given the cost model,
state so explicitly. If specific re-sequencing is recommended,
detail the change and why.]

**Promotion candidates from Step 04:**
[List any MCs the cost-vs-capacity math suggests could promote from
stretch to floor at small marginal cost.]

---

## 6. Cost-Concentration Analysis

| MC | Maint-hrs | % of Plan | Justified? |
|----|----------:|----------:|------------|
| MC-XX | [N] | [%] | Yes/No with Step 02 weighted rationale and Step 04 mitigation |
| [...] | [...] | [...] | [...] |
| **Top concentrations** | **[sum]** | **[%]** | **[summary justification]** |

**Phase 5 attention flags:**
- [list MCs requiring specific Phase 5 attention based on
  concentration analysis]

---

## 7. Tag-Distribution Honesty Check

**Project profile:** [profile description]
**Expected tag-dominance:** [from instructions file profile table]

**Actual tag-dominance in this plan:**
- Dev-hours: [breakdown]
- AI-acceleration multipliers: [breakdown]
- Token-count: [breakdown]
- Token-cost: [breakdown]

**Match assessment:** [Honest / Over-confident / Under-investing]

**Forward note for Phase 7 calibration:**
[If BELIEVED multipliers are present in the plan, name the
calibration that Phase 5 execution should produce and that Step 06
§10.4 will surface as the Phase 7 calibration handoff.]

---

## 8. Comprehensiveness Check Result

[Practitioner's response to comprehensiveness questions; either
"all good" or specific adjustments captured]

---

## 9. Forward Implications

### 9.1 For Step 06 (Synthesis)

[Key cost insights to surface in the Improvement Plan executive
summary; cost-concentration MCs requiring Phase 5 attention; any
promotion candidates; capacity-vs-envelope framing for v[N].0
release strategy]

### 9.2 For Phase 5 (Execution)

[Per-tier capacity expectations; attention flags; estimate
uncertainty notes (e.g., wider-uncertainty MCs that should
re-estimate post Phase 3 design brief)]

### 9.3 For Phase 7 (Run-Cost & Empirical Calibration)

[Forward-handoff items for Phase 7: token baseline empirical
validation, ongoing AI-usage cost tracking, BELIEVED → ESTIMATED →
MEASURED graduation, watch-triggers]

---

## 10. Sources & Evidence Register

- **Phase 1 Input Validation (Step 01)** — for HC-08 capacity envelope
  and HC-03 budget framing
- **Principle Weighting (Step 02)** — weights informing cost-concentration
  justification and re-mechanism recommendations
- **Mechanism Decisions (Step 03)** — per-MC mechanism-cost basis
- **Sequencing and Tiering (Step 04)** — tier composition, floor/stretch
  composition, staging mitigation flags
- **Cost Modeling Tag Discipline** in companion instructions file —
  three-quantity model definition, reference tables, capacity-bound
  recommendation discipline
- **Practitioner confirmations** — final authority on per-MC rows,
  capacity assessment, comprehensiveness check
```

---

## Evaluation Checklist

Before accepting the Cost Modeling and Capacity Check artifact:

- [ ] Every multi-mechanism MC and every single-mechanism MC has a
      cost row in §2 (no MCs missing from cost modeling)
- [ ] **Every cost row has all three primary quantities** — dev-hours
      with tag, AI-acceleration multiplier with category attribution
      and tag, maintainer-hours (derived) *(v1.1)*
- [ ] **Every cost row has token-count and token-cost projections
      (derived)** *(v1.1)*
- [ ] **Multiplier category attribution cites Reference Table 1
      explicitly** (Mechanical cleanup / Doc authorship / Config
      edit / Novel design) *(v1.1)*
- [ ] **Token ratio is 6,000 tokens/Senior-dev-hour default unless
      project-specific calibration data exists** *(v1.1)*
- [ ] Tags are never silently upgraded; tag changes are calibration
      events with rationale
- [ ] Per-tier and plan-total rows sum the primary and derived
      quantities consistently
- [ ] Floor and stretch maintainer-hour totals are stated explicitly
- [ ] Capacity-vs-envelope comparison uses maintainer-hours (not
      dev-hours) as the binding constraint
- [ ] Budget-envelope comparison uses token-cost (not dev-hours) as
      the AI-usage layer check
- [ ] If plan exceeds capacity, specific capacity-bound
      recommendation is produced (re-sequence / re-mechanism /
      extend / expand)
- [ ] Cost-concentration analysis surfaces MCs >15% of plan with
      Step 02 weighted justification
- [ ] Tag-distribution honesty check is conducted; project profile
      and expected vs. actual distributions compared
- [ ] **BELIEVED multipliers (if present) are surfaced forward to
      Step 06 §10.4 Phase 7 calibration handoff** *(v1.1)*
- [ ] Comprehensiveness check is conducted; result documented
- [ ] Forward implications for Step 06, Phase 5, Phase 7 are listed

---

## Version History

| Version | Date | Source | Summary |
|---------|------|--------|---------|
| v1.0 | 2026-04-22 | Initial authoring | Initial Phase 2 Step 05 prompt. Draft-and-react mode in tier batches. Per-MC cost rows with single-dimension time cost. Capacity-vs-envelope comparison. Capacity-bound recommendation if over. Tag-distribution honesty check with project-profile expected distributions. Cost-concentration analysis. Comprehensiveness check. |
| **v1.1** | **2026-05-22** | **Diamonds Phase 2 dogfooding run (P2-Obs-01 and P2-Obs-02, Cluster A)** | **Substantial revision.** Cost model expanded from single-dimension to three-quantity model: dev-hours (Senior baseline, with tag), AI-acceleration multiplier (per-category attribution, BELIEVED at v1.0), maintainer-hours (derived), token-count projection (derived), token-cost projection (derived). Per-MC cost row format expanded to 8-column layout. Two Reference Tables added for quick in-step access (per-category multiplier defaults: mechanical cleanup 10×, doc authorship 8×, config edit 5×, novel design 3×; token baseline: 6,000 tokens/Senior-dev-hour, Opus 4.7 ~$2.50/100K). Behavioral rules updated for three-quantity discipline. Output Format §2 row schema updated; §3 plan summary expanded; §7 tag-distribution honesty check updated. Evaluation Checklist substantially expanded (six new v1.1-specific items). BELIEVED-multiplier surfacing requirement added so Step 06 §10.4 Phase 7 calibration handoff inherits the signal. |

---

*Part of the Phase 2 Analysis & Improvement Planning (Existing Projects) Tool Set — v1.1*
*AI-Centric Software Development Playbook*
*Companion file: `analysis-improvement-planning.existing-project.instructions.md`*
*Previous step: `step-04-sequencing-and-tiering.prompt.md`*
*Next step: `step-06-improvement-plan-synthesis.prompt.md`*
