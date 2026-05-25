# Phase 2 Dogfooding Observations
# AI-Centric Software Development Playbook — Phase 2 (Existing Projects) Toolkit
# Source: Diamonds Phase 2 Dogfooding Run, 2026-05-22

**Subject:** `@diamondslab/diamonds` v1.3.2
**Toolkit version under test:** Phase 2 v1.0 (initial authoring 2026-04-22)
**Reviewing AI:** Claude Opus 4.7
**Practitioner:** Solo maintainer (DiamondsLab)
**Phase 1 cycle reference:** Completed 2026-04-20; report 5 PASS + 1 CONDITIONAL

---

## About This File

This file captures observations made during the Phase 2 (Existing Projects)
dogfooding run on `@diamondslab/diamonds`. Following the Phase 1 dogfooding
protocol (Option B): observations are captured as they surface during the
run but are not acted upon until end-of-phase review. The end-of-Phase-2
review (recorded in §End-of-Phase-2 Review below) clusters observations
and drives the v1.1 toolkit revision.

**Calibration target for Phase 2 v1.0:** 15-25 observations per complete
Phase 2 run.

**Actual count from Diamonds run:** 7 observations. Under-range — explained
in §End-of-Phase-2 Review by Phase 2 v1.0 inheriting Phase 1 v1.2's mature
disciplines. Future runs on different project profiles may surface
additional observations.

---

## Individual Observations

### Observation 1 (P2-Obs-01) — Cost framing assumes pre-AI man-hour-to-maintainer-time equivalence

- **Source step:** Initial Specify interview, Q2b
- **Nature:** Bug / structural gap in the Phase 2 toolkit
- **Evidence:** The toolkit's Step 05 cost-modeling discipline used time
  (hours) as the primary cost dimension for solo OSS work and assumed
  the time figure represented *maintainer-time spent*. The practitioner
  correctly identified that this conflates two distinct quantities in the
  age of AI-accelerated development: **the work's intrinsic complexity**
  (which can be estimated as developer-hours, roughly stable across humans)
  and **the maintainer's actual time spent** (which is shaped by AI
  acceleration and may differ from developer-hours by an order of
  magnitude). A naive 22-MC plan at "100+ hours of work, 2 hours per week
  of maintainer-time, equals one year" is correct arithmetic on the wrong
  quantity — the 100+ hours figure isn't what the maintainer will actually
  spend if AI acceleration is real.
- **Proposed toolset change:** v1.1 cost-model revision should introduce a
  two-dimension model: intrinsic work complexity (dev-hours, Senior
  Developer baseline, without AI assistance) and maintainer-time-with-AI-
  acceleration (maintainer-hours), with an explicit per-category AI-
  acceleration multiplier between them. The capacity envelope (HC-08)
  bounds maintainer-hours, not dev-hours. Each quantity carries its own
  MEASURED/ESTIMATED/BELIEVED/UNMEASURED tag.
- **Priority:** High — affects how Phase 2 plans capacity for every
  AI-accelerated project, and the Playbook's central thesis is precisely
  that AI acceleration is real.
- **Status:** Open
- **Cluster assignment:** Cluster A (Three-Quantity Cost Model)
- **Cross-reference:** Pairs with P2-Obs-02 (token-cost dimension); the two
  observations together drive the three-quantity model.

---

### Observation 2 (P2-Obs-02) — Token-cost dimension as a measurable cost layer

- **Source step:** Initial Specify interview, Q2b follow-up
- **Nature:** Enhancement (extends P2-Obs-01)
- **Evidence:** The practitioner observed that developer-hours can be
  roughly equated to AI token usage (cited heuristic: 1 Senior developer
  hour ≈ 6,000 AI tokens). This makes the dev-hours figure not just a
  comparative-size indicator but a **directly measurable cost predictor**
  in dollar terms. The token estimate enables an actual API-cost projection
  per MC and per tier — and the cost can then be evaluated against whatever
  cost framework matters (purely-OSS-budget, billable-time, AI-API-budget).
- **Proposed toolset change:** v1.1 cost-model revision should include
  AI-token-usage as a derived dimension (dev-hours × tokens-per-dev-hour
  ratio). The ratio is itself a tagged input (BELIEVED at v1.0, ESTIMATED
  after one or two cycles, MEASURED once metered). Dollar projection
  derived from token-count × model-pricing-per-token, also tagged.
- **Priority:** High — pairs with P2-Obs-01 to produce a Phase 2 cost model
  that is meaningfully grounded in observable quantities rather than
  abstract "hours."
- **Status:** Open
- **Cluster assignment:** Cluster A (Three-Quantity Cost Model)
- **Cross-reference:** P2-Obs-01 (cost framing); P2-Obs-04 (Phase 7
  empirical validation of these ratios)

---

### Observation 3 (P2-Obs-03) — "Zero-cost budget" framing is incompatible with AI-Centric Software Development reality

- **Source step:** Initial Specify interview Q2b follow-up; surfaced
  during Phase 2 but originates in Phase 1
- **Nature:** Bug — affects Phase 1 toolkit; Phase 2 inherits the bad input
- **Evidence:** Phase 1 HC-03 captured "zero budget" as a hard constraint
  for Diamonds, with HC-04 as its corollary ("no commercial-tier services").
  The practitioner observed that this framing is inconsistent with
  AI-Centric Software Development practice: every AI-assisted cycle has a
  non-zero token cost. Diamonds Phase 5 execution at ~200+ dev-hours
  equivalent of work, at ~6,000 tokens/dev-hour, at Opus 4.7 pricing, will
  incur real API costs in the tens-of-dollars range — small but not zero.
  The "zero budget" constraint is honest about commercial-service
  exclusion ($0 to SaaS vendors) but misleading about total cost ($0
  ignores AI API costs which are now structural to the practice).
  - Phase 1 Must-Keep MK-07 ("Zero-budget / OSS-only operation") inherits
    the same simplification; HC-04 ("no commercial-tier services") is
    related but distinct.
- **Where the bug actually is:** Phase 1 v1.2 toolkit. Specifically the
  constraint-capture mechanics in
  `step-04-risk-constraint-technical-debt-inventory.prompt.md`, and the
  framing prompts in the instructions file that ask about "budget"
  without distinguishing between commercial-service budget and AI-usage
  budget.
- **Proposed toolset change:** Phase 1 v1.3 should split the "budget"
  constraint capture into at least two questions: (a) commercial-service
  / SaaS-tier budget (which can legitimately be $0 for OSS), and (b)
  AI-usage budget (which is structurally non-zero for any AI-Centric
  work — could be $5/month, $50/month, $500/month, or "we'll figure out
  as we go," but should be made explicit). The instructions file should
  reframe budget as "two-layer budget: commercial tools layer and
  AI-usage layer." MK-07 framing in step-03 should similarly accommodate
  the two-layer distinction.
- **Priority:** High — affects every project using the Phase 1
  existing-projects toolkit going forward, and is structurally important
  to the Playbook's central thesis.
- **Status:** Open — will feed Phase 1 v1.3 revision rather than Phase 2
  v1.1 (since the gap is in Phase 1)
- **Cluster assignment:** Cluster B (Phase 1 Budget Framing Gap)
- **Cross-reference:** P2-Obs-01 (cost framing) and P2-Obs-02 (token-cost
  dimension); P2-Obs-03 is the Phase-1-side gap that makes P2-Obs-01/02
  necessary in Phase 2

---

### Observation 4 (P2-Obs-04) — Token-baseline empirical validation as Phase 7 operational tracking

- **Source step:** Initial Specify interview Q3 follow-up
- **Nature:** Enhancement / forward handoff
- **Evidence:** Phase 2 v1.0 introduces tokens-per-dev-hour and
  AI-acceleration-multiplier as BELIEVED inputs at v1.0 because no
  historical data exists. As Phase 5 execution proceeds, the practitioner
  accumulates actual dev-hours-vs-maintainer-hours data and actual
  token-usage data, which would let the multipliers move from BELIEVED to
  MEASURED. Phase 7 (Deployment & Evolution) should include an
  operational-tracking element for these quantities, both for project
  tracking and for refining future cycles' Phase 2 cost models. Diamonds'
  first Phase 5 execution can serve as the first empirical-validation
  cycle for the broader Playbook.
- **Proposed toolset change:** Phase 2 Step 06 should include a forward-
  handoff item to Phase 7 naming this specifically. Phase 7 toolkit (when
  authored) should include a token/maintainer-hour empirical-tracking
  pattern. Phase 2 v1.1 may also add a "Calibration data source"
  annotation in Step 05 so multiplier improvements over multiple cycles
  are traceable.
- **Priority:** Medium for Phase 2 toolkit, High for Phase 7 toolkit
  (which doesn't exist yet)
- **Status:** Open — will feed Phase 2 v1.1 minor enhancement plus
  Phase 7 toolkit authoring when that begins
- **Cluster assignment:** Cluster C (Phase 7 Empirical Calibration)
- **Cross-reference:** P2-Obs-01, P2-Obs-02

---

### Observation 5 (P2-Obs-05) — Step 01 validation reveals the Phase 2 → Phase 1 feedback channel

- **Source step:** Step 01
- **Nature:** Pattern (positive — toolkit discipline working, and
  structural)
- **Evidence:** Step 01 produced 5 validation gaps (VG-01 through VG-05),
  of which 3 (VG-02, VG-03, VG-04) were gaps in the *Phase 1 toolkit*
  surfaced by Phase 2 work. These three gaps would not have been visible
  without running Phase 2 — Phase 1's self-evaluation rated itself
  5 PASS + 1 CONDITIONAL, but Phase 2's cost-modeling requirements
  revealed that Phase 1's constraint-capture mechanics were incomplete in
  three specific ways. The validation-gap register is functioning as a
  structural feedback channel from later phases to earlier toolkit
  revisions, not just as a one-time check before Phase 2 proceeds.
- **Proposed toolset change:** Two related changes. (a) Phase 2 step-01
  artifact template should explicitly split the Validation Gap Register
  into "Phase 2 local gaps" (must resolve in Phase 2) and "Upstream
  toolkit gaps" (Phase-N-1 toolkit improvements surfaced during Phase N
  work). The current template treats both uniformly; today's run produced
  both kinds. (b) The toolkit README should describe the inter-phase
  feedback channel as an explicit feature: "Phase N validation may
  surface gaps in Phase N-1 toolkit; those gaps feed N-1 toolkit
  revision, not Phase N delay." The pattern generalizes to all
  Phase-N-input-validation steps in future toolkits.
- **Priority:** Medium — improves the toolkit's self-improvement loop,
  which is exactly the Playbook's dogfooding-driven-improvement thesis.
- **Status:** Open
- **Cluster assignment:** Cluster D (Phase 2 → Phase 1 Feedback Channel)

---

### Observation 6 (P2-Obs-06) — Mid-phase capability availability shift

- **Source step:** Step 03 (mid-step)
- **Nature:** Pattern (positive — capability gained mid-phase)
- **Evidence:** Step 00 Building Block Discovery recorded Context7 as
  unavailable for this session (tool call refused at the time). GitHub
  MCP tools and Context7 became available mid-Step-03. This shift
  improved AI ability to answer library-currency questions for MC-01
  (lodash replacement candidates) and MC-08 (doc-site tool selection)
  without falling back to training-data-with-caveat. The Toolset
  Augmentation Document produced in step-00 was treated as a snapshot
  but should have been treated as living.
- **Proposed toolset change:** The step-00 prompt and the instructions
  file should both note that capability availability can shift mid-phase.
  The Toolset Augmentation Document should be treated as living, not
  snapshot — when capabilities change, the document gets a brief
  amendment rather than being stale. Specifically:
  - In step-00 prompt System Instructions: "If a capability becomes
    available mid-phase, update the Toolset Augmentation Document with
    an amendment row and note which steps benefit. If a capability
    becomes unavailable mid-phase, downgrade affected step modes and
    note the downgrade explicitly."
  - In instructions file Behavioral Rules: "MCP connector activation
    can shift mid-phase; treat the augmentation document as living."
- **Priority:** Low — covers a relatively rare situation but the capture
  costs nothing.
- **Status:** Open
- **Cluster assignment:** Cluster E (Mid-Phase Capability Shift)

---

### Observation 7 (P2-Obs-07) — Step 03 batch sizing held up well at 4/3/1

- **Source step:** Step 03 (meta-observation)
- **Nature:** Pattern (positive — toolset discipline working)
- **Evidence:** The Step 03 prompt advised drafting 4–6 MCs per batch.
  The Diamonds run split the 8 multi-mechanism MCs into batches of 4
  (high-weight-sensitive: MC-01, MC-04, MC-08, MC-11) / 3 (mid-
  sensitivity: MC-07, MC-12, MC-21) / 1 (cleanup: MC-19). The 4-MC first
  batch was the maximum useful before practitioner-attention fatigue
  would have set in; the 3-MC batch felt slightly under-sized but worked
  because the three MCs shared cross-references that benefited from
  being read together; the 1-MC final batch was right-sized because
  MC-19 was independent and could be evaluated alone. Practitioner
  accepted all batches without amendment — no signal that the batching
  strategy itself was wrong.
- **Proposed toolset change:** Add to step-03.prompt.md a clarifying note
  on batch sizing in System Instructions: "Default batch size 4 MCs.
  Reduce to 2-3 when MCs share cross-references that benefit from being
  read together. Reduce to 1 for independent cleanup-type MCs. Maximum 6
  only when MCs are truly independent and the practitioner has signaled
  high attention bandwidth." This codifies the pattern improvised during
  the Diamonds run.
- **Priority:** Low — practitioners can figure this out, but capturing it
  as guidance helps future runs.
- **Status:** Open
- **Cluster assignment:** Cluster F (Step 03 Batch Sizing)

---

## Summary Statistics

**By priority:**
- High: 3 (P2-Obs-01, P2-Obs-02, P2-Obs-03)
- Medium: 2 (P2-Obs-04, P2-Obs-05)
- Low: 2 (P2-Obs-06, P2-Obs-07)

**By source step:**
- Initial Specify interview: 4 (P2-Obs-01, 02, 03, 04)
- Step 01: 1 (P2-Obs-05)
- Step 03: 2 (P2-Obs-06, 07)
- Other steps: 0

**By nature:**
- Bug / structural gap in Phase 2 toolkit: 1 (P2-Obs-01)
- Bug in Phase 1 toolkit (surfaced through Phase 2): 1 (P2-Obs-03)
- Enhancement: 2 (P2-Obs-02, P2-Obs-04)
- Pattern (positive): 3 (P2-Obs-05, P2-Obs-06, P2-Obs-07)

**By status at Phase 2 close:** all 7 Open. None acted on during
dogfooding per Option B protocol. End-of-Phase-2 review (below) converts
Open → Acted based on v1.1 toolset revision decisions.

**By status after v1.1 toolset revision (deferred to fresh session):**
TBD when v1.1 lands. Cluster A drives substantial revisions to instructions
file and step-05; Clusters C, D, E, F drive minor revisions across multiple
files. Cluster B routes to Phase 1 v1.3 separately.

---

## End-of-Phase-2 Review

Conducted 2026-05-22 immediately after Step 06 completion. Three-pass
structure matching Phase 1's end-of-Phase-1 review.

### Pass 1 — Cluster

7 observations clustered into 6 clusters by what file/concept the
proposed change touches:

| Cluster | Observations | Scope | Affects |
|---------|--------------|-------|---------|
| A — Three-Quantity Cost Model | P2-Obs-01, P2-Obs-02 | Phase 2 v1.1 substantial | Instructions file + step-05 prompt |
| B — Phase 1 Budget Framing Gap | P2-Obs-03 | **Phase 1 v1.3** (not Phase 2 v1.1) | Phase 1 step-04 + instructions |
| C — Phase 7 Empirical Calibration | P2-Obs-04 | Phase 2 v1.1 minor + Phase 7 future | Phase 2 step-06 forward-handoff note |
| D — Phase 2 → Phase 1 Feedback Channel | P2-Obs-05 | Phase 2 v1.1 moderate | step-01 prompt + README |
| E — Mid-Phase Capability Shift | P2-Obs-06 | Phase 2 v1.1 minor | step-00 prompt + instructions |
| F — Step 03 Batch Sizing | P2-Obs-07 | Phase 2 v1.1 trivial | step-03 prompt |

Six clusters from 7 observations. The 7-to-6 ratio reflects the tight
coupling of P2-Obs-01 + P2-Obs-02 (the cost model is one fix, not two).

### Pass 2 — Per-Cluster Decision

| Cluster | Decision | Notes |
|---------|----------|-------|
| A — Three-Quantity Cost Model | **Accept** | Validated through full Diamonds run; smooth per-MC drafting; honest tag-distribution check; cost-concentration analysis worked. In-line amendment was the right call; formalization is straightforward. |
| B — Phase 1 Budget Framing Gap | **Accept** (Phase 1 v1.3, not Phase 2 v1.1) | Correctly a Phase 1 toolkit gap; Phase 2 already captures the amendment in Step 01 VG register. Phase 1 v1.3 lands the structural fix. |
| C — Phase 7 Empirical Calibration | **Accept with refinement** | Phase 7 toolkit doesn't exist yet; change is forward-looking. Refinement: change is *additive* in step-06 prompt, not structural rework. |
| D — Phase 2 → Phase 1 Feedback Channel | **Accept** | Structural insight worth formalizing. Future runs will likely show similar shapes; artifact template should make feedback explicit rather than implicit. |
| E — Mid-Phase Capability Shift | **Accept** | Low-effort change with real value for any run where capability changes mid-phase. |
| F — Step 03 Batch Sizing | **Accept** | Trivial codification of a pattern that worked. |

**Decision summary:**
- 5 of 6 clusters accepted for Phase 2 v1.1
- 1 cluster (B) accepted but routed to Phase 1 v1.3
- 1 cluster (C) accepted with refinement (additive scope, not structural)
- 0 clusters deferred or rejected

**Accept-with-refinement rate:** 1 of 6 (Cluster C). Healthy ratio —
same shape as Phase 1's review where 1 of 19 was accepted-with-
refinement. A higher rate would suggest accepting under-developed
observations; a lower rate (straight-accept on all) would suggest
insufficient scrutiny.

### Pass 3 — Revise Plan for v1.1

Phase 2 toolkit v1.1 lands as a moderate revision affecting **7 of the
9 files**. Phase 1 toolkit v1.3 is queued separately (2 files).

**Files changing in Phase 2 v1.1:**

| File | Cluster(s) | Change Scope |
|------|-----------|--------------|
| `README.md` | A, D | Version table v1.1; reference three-quantity cost model in Step 05 description; note Step 01 surfaces upstream-toolkit gaps; Version History row |
| `analysis-improvement-planning.existing-project.instructions.md` | A, E | Cost Modeling Tag Discipline section substantial revision (three-quantity model definition + reference tables); Behavioral Rules add mid-phase capability-shift handling; Version History row |
| `step-00-building-block-discovery.prompt.md` | E | System Instructions add "Toolset Augmentation Document is living, not snapshot"; Output Format adds optional "Mid-Phase Amendments" subsection; Version History row |
| `step-01-phase-1-input-validation.prompt.md` | D | Output Format Section 8 splits VG Register into 8.1 (Phase 2 local) and 8.2 (Upstream toolkit gaps); Evaluation Checklist updated; Behavioral Rules add "classify each VG by scope"; Version History row |
| `step-03-mechanism-decisions.prompt.md` | F | System Instructions batch-sizing guidance refinement; Version History row |
| `step-05-cost-modeling-and-capacity-check.prompt.md` | A | Substantial revision: System Instructions for three-quantity model output; Reference tables with per-category multiplier defaults + token baselines; per-MC cost row format updated; Output Format cost row table format updated; tag-distribution honesty check updated; Evaluation Checklist updated; Version History row |
| `step-06-improvement-plan-synthesis.prompt.md` | C | Output Format Section 10 adds explicit Phase 7 calibration-handoff row when Step 05 uses BELIEVED multipliers; Behavioral Rules updated; Version History row |

**Files unchanged in Phase 2 v1.1:**
- `step-02-principle-weighting.prompt.md` — no observation affected
- `step-04-sequencing-and-tiering.prompt.md` — no observation affected

**Total Phase 2 v1.1 changes:** 7 files affected, 2 files unchanged.
Compared to Phase 1 v1.1 (which changed every file plus added one), this
is a more contained revision — consistent with the lower observation
count and the inheritance of Phase 1 v1.2 disciplines.

### Phase 1 v1.3 Queue (Forwarded; Not Acted in This Session)

Cluster B drives Phase 1 v1.3 in a separate session:

| File | Change |
|------|--------|
| `step-04-risk-constraint-technical-debt-inventory.prompt.md` | Hard Constraint capture adds two-layer-budget framing (commercial-tools layer + AI-usage layer); MK-07 framing in step-03 may also benefit |
| `information-gathering.existing-project.instructions.md` | Budget framing discipline notes two-layer budget capture |

This is a small revision (2 files); doing it in a fresh session preserves
the focused-attention pattern that produced Phase 1 v1.1 and Phase 2 v1.1
work. Phase 1 v1.3 can ride along with Phase 2 v1.1 authoring in the same
fresh session.

---

## Comparison to Phase 1 Dogfooding Review

| Dimension | Phase 1 Review | Phase 2 Review |
|-----------|---------------|----------------|
| Observation count | 26 | 7 |
| Clusters produced | 19 | 6 |
| Accept rate | 19/19 (one with refinement) | 6/6 (one with refinement, one routed to Phase 1 v1.3) |
| Files affected by revision | 8 + 1 new file | 7 (1 file routed to Phase 1 v1.3) |
| Calibration range | Expected 20-30, actual 26 (in range) | Expected 15-25, actual 7 (under-range) |
| Toolkit-shape signal | First-pass authoring; many structural improvements surfaced | v1.0 inherited v1.2 disciplines; structural shape worked; refinements concentrated in cost model (substantive) and several minor areas |

The under-range observation count for Phase 2 is **structurally explained**
by the v1.0 toolkit inheriting Phase 1 v1.2's mature disciplines. This is
a positive signal — the toolkit-building practice produced a working v1.0
from the start. Future Phase 2 dogfooding runs on different project
profiles (regulated-industry, multi-engineer team, mature-productized
library, etc.) may surface additional observations; the v1.1 revisions
land what is known now.

---

## Sources & Evidence Register

- **Phase 2 Step 01 artifact** (Phase 1 Input Validation, completed
  2026-05-22) — sources for P2-Obs-05
- **Phase 2 Step 03 artifact** (Mechanism Decisions, completed
  2026-05-22) — sources for P2-Obs-06, P2-Obs-07
- **Phase 2 Step 05 artifact** (Cost Modeling, completed 2026-05-22) —
  primary site of three-quantity cost model in-line amendment driven by
  P2-Obs-01, P2-Obs-02
- **Phase 2 Step 06 artifact** (Improvement Plan, completed 2026-05-22)
  — captures Phase 7 forward handoff (P2-Obs-04) as Section 10.3
  watch-trigger
- **Phase 1 Step 01-06 artifacts** (completed 2026-04-20) — referenced by
  P2-Obs-03 as origin of "zero-cost budget" framing gap
- **Phase 1 dogfooding-observations.md** — 26 observations, all Acted at
  v1.1; structural model for this Phase 2 dogfooding-observations file
- **Practitioner confirmations 2026-05-22** — final authority on all
  observation captures, cluster decisions, and v1.1 / v1.3 revision plans

---

*Phase 2 Dogfooding Observations — v1.0 of this record*
*Source: AI-Centric Software Development Playbook — Phase 2 (Existing Projects) Toolkit Dogfooding Run*
*Diamonds project, 2026-05-22*
