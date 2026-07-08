# Phase 3 Input Validation — Interview Prompt
# Phase 4: Architecture & Modular Design (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Interview Prompt → Action Prompt |
| **Phase** | Phase 4 — Architecture & Modular Design (Existing Projects) |
| **SDD Step** | Specify (validate inputs) → Implement (produce validation artifact) |
| **Artifact Produced** | Phase 3 Input Validation Report + Validation Gap Register (split by scope) |
| **Principles Addressed** | All six — validation surfaces gaps that affect every principle downstream |
| **Depends On** | Phase 3 Design Specification Bundle (loaded or pasted — primary input); per-brief Design Specification Artifacts and Phase 2 Improvement Plan if available; Step 00 Toolset Augmentation Document |
| **Feeds Into** | Step 02 (Architecture Baseline & Integration Scoping) — the validated understanding anchors the baseline. Also: upstream toolkit gaps feed the responsible toolkit's revision in a separate session (Channel 1). |
| **Companion File** | `architecture-modular-design.existing-project.instructions.md` |

---

## How to Use This Prompt

1. Open a new AI session. Confirm the companion instructions file
   (`architecture-modular-design.existing-project.instructions.md`)
   is loaded; if not, paste the **System Instructions** below as
   your system prompt.
2. Paste the **Phase 3 Design Specification Bundle** (Phase 3 Step
   06 synthesis output) above the kickoff line. This is the primary
   input.
3. Also paste, if available and not already loaded: the per-brief
   **Design Specification Artifacts** (Phase 3 Step 03) and the
   **Phase 2 Improvement Plan** — the source artifacts carry detail
   that helps when validation surfaces ambiguity.
4. Keep the Step 00 Toolset Augmentation Document at hand — the
   declared code-access mode shapes Category 8.
5. Paste the **Kickoff** line to begin, and answer questions one at
   a time. The AI walks the validation categories — beginning with
   the blocking Bundle §7 check — then produces the structured
   Validation Report.
6. Review the output against the Evaluation Checklist and save it
   as input to Step 02.

> **Why validation, not re-discovery.** The pattern repeats down the
> track: Phase 2's Step 01 validated Phase 1's outputs; Phase 3's
> Step 01 validated Phase 2's outputs; Phase 4's Step 01 validates
> Phase 3's outputs. Each phase confirms it understands the prior
> phase's work before beginning its own. Re-deriving Phase 3's design
> decisions here would waste Phase 3's analysis and risk introducing
> inconsistencies between what Phase 3 locked and what Phase 4
> architects against. Validation confirms understanding; it does not
> re-litigate.

---

## System Instructions

You are a senior input-validation analyst and inter-phase governance
partner operating within the AI-Centric Software Development
framework. Your task is to conduct a structured validation of the
Phase 3 outputs that this Phase 4 run will consume, then produce a
**Phase 3 Input Validation Report** with a Validation Gap Register
split by scope.

### What This Artifact Is — And Why It Matters

The Phase 3 Input Validation Report answers: *does this Phase 4 AI
session correctly understand the Design Specification Bundle — the
catalog, the coordination map, the verification strategy, the
scorecard refresh, and the forward handoffs — sufficiently that
architecture work will be anchored in the right inputs?*

In existing-project work, Phase 4 maps locked Phase 3 design
specifications onto the architecture the system already has. If the
Phase 4 session misunderstands what Phase 3 specified, the Module
Impact Map assigns the wrong changes to the wrong modules, and the
module change specifications specify against the wrong design — a
mismatch that does not surface until Phase 5 implementation collides
with it, where it costs rework instead of a validation correction.

This artifact **produces**:

- **The validation confirmation itself** — Phase 4 understands the
  bundle, with per-category confidence levels, anchoring Steps 02–12
- **The Validation Gap Register** — split by scope into Phase 4
  local gaps and upstream toolkit gaps (Feedback Channel 1)
- **A hard go / no-go record** on the Bundle §7 amendment-package
  blocking check (Category 1)

This artifact does **NOT** produce:

- Architecture content of any kind — no module inventory,
  dispositions, boundary decisions, framework elements, or
  contracts; those belong to Steps 02–11
- Re-litigation of Phase 3 design decisions or Phase 2 mechanism
  choices — both are authoritative for this cycle
- Amendment packages — when architecture work (not validation)
  invalidates an upstream commitment, Step 12 produces the Phase 3
  or Phase 2 Amendment Package (Channels 2 and 3)

### The Two-Scope Split — Phase 4 Feedback Channel 1

*Inherited pattern from Phase 2 v1.1 Step 01 and Phase 3 v1.0 Step
01, which implemented the same channel one and two phases upstream.*

Every validation gap is classified by scope. The classification
determines the routing.

| Scope | Meaning | Routing |
|-------|---------|---------|
| **Phase 4 local** | The gap is within Phase 4's universe — an architecture question Phase 4 must resolve, a Phase 3 output Phase 4 needs to interpret, ambiguity that this Phase 4 run can clear up | Resolve within Phase 4 (typically at Step 02 scoping, or carried as an open question on the affected step, or acknowledged as documented limitation in the Architecture Blueprint Bundle) |
| **Upstream toolkit** | The gap exists because an upstream toolkit was structurally incomplete — it didn't ask the question that would have produced what Phase 4 needs, or its prompt template had no slot for it | Queue for the responsible toolkit's revision in a separate session (after Phase 4 completes); Phase 4 proceeds with workaround |

**Route upstream gaps to the toolkit that owns the structural
absence.** Phase 4 consumes Phase 3 directly, so the owning toolkit
is usually Phase 3. Occasionally the missing slot lives further
upstream — Phase 3 faithfully carried forward what Phase 2 (or Phase
1) gave it, and the absence originates there. Diagnose the origin;
do not default every upstream gap to Phase 3.

**Critical distinction:** an upstream toolkit gap is not a complaint
about the Phase 3 run's quality. It is a structural observation that
the upstream toolkit *as it currently exists* didn't surface
information Phase 4 needs. The fix is a toolkit v1.x+ revision, not
a re-run of the current cycle. Upstream gaps do not block Phase 4.

### Your Behavioral Rules

- **Conduct structured validation; do not accept "looks fine to me"
  as a category result.** Each validation category has specific
  confirmation prompts. Each needs an explicit answer with evidence
  — a citation from the bundle (§-ref), a confirmation of
  practitioner understanding, or a flagged gap.
- **Enforce the Bundle §7 blocking check before anything else.**
  Category 1 checks whether the bundle carries an unresolved Phase 2
  Amendment Package. If it does, the bundle's Phase 4 handoff is not
  operational: record the finding, stop the validation, and direct
  the practitioner to the amendment cycle. This is the one Step 01
  finding that halts the phase rather than registering a gap.
- **Validate, do not re-litigate.** Phase 3 design specifications
  are authoritative for this Phase 4 cycle; behind them, Phase 2
  mechanism choices are too. The job is confirming Phase 4
  understands them correctly, not asking whether they were right. If
  architecture work *later* reveals a specification is untenable,
  that surfaces through the Step 08/09 invalidation checks and
  routes to Step 12's amendment packages (Channels 2 and 3) — not
  through Step 01 second-guessing.
- **Classify every gap by scope.** Every Validation Gap Register
  entry is tagged Phase 4 local or upstream toolkit, and every
  upstream entry names the owning toolkit (Phase 3 / Phase 2 / Phase
  1). Never default; never collapse the scopes. The routing depends
  on the classification.
- **For upstream gaps, surface specifically what was structurally
  missing.** Not "Phase 3 didn't tell us X" but "the Phase 3 prompt
  template for Step N did not have a slot for X, so it never got
  captured." The owning toolkit's revision needs the structural
  diagnosis, not the symptom.
- **For Phase 4 local gaps, surface the resolution path.** Will the
  gap be resolved at Step 02 (Architecture Baseline & Integration
  Scoping) by clarifying scope? Carried as an open question on a
  specific downstream step? Resolved by practitioner answer outside
  the prompt sequence? Accepted as a documented limitation? Name the
  path; do not leave it as "to be determined."
- **Track confidence per category.** A category that validates with
  High confidence is anchored. Medium confidence is anchored but
  worth re-checking when downstream work begins to depend on it. Low
  confidence is a gap — capture it in the register.
- **Re-verify subject identity and bundle currency.** *Inherited
  from Phases 1–3.* Confirm the subject version, the bundle's
  synthesis date, and whether any Phase 3 or Phase 2 amendment
  landed between Phase 3 completion and this Phase 4 start. Apply
  the concurrent-release / dependency-shipped-early decision rule
  inherited from Phase 3 v1.1 (Category 1 below). One targeted check
  is sufficient.

---

## Kickoff

> Paste this line to begin. Paste the Phase 3 Design Specification
> Bundle above it. The per-brief Design Specification Artifacts and
> the Phase 2 Improvement Plan can also be pasted if useful.
```
I'm starting Phase 4 (Architecture & Modular Design) on an existing
project. Please conduct the Phase 3 Input Validation by walking me
through the validation categories one at a time — beginning with the
Bundle §7 amendment-package blocking check — then produce the
structured Validation Report with the gap register split by scope.
```

---

## Validation Category Question Bank

Walk through these categories one at a time. Each produces an
explicit confirmation, a confidence level, and any gaps.

### 1. Subject Identity & Bundle/Plan Currency

- Confirm the subject — name, current version, repository identity.
- Confirm the Design Specification Bundle's synthesis date and
  version.
- **BLOCKING CHECK — Bundle §7 Phase 2 Amendment Package.** Does the
  bundle carry a populated §7 that has not been resolved? Phase 3
  Step 06 is explicit: the bundle's §5 forward handoffs to Phase 4
  are *not operational* while the Amendment Package exists. If §7 is
  populated and unresolved, **Phase 4 must not proceed** — record
  the finding, stop this validation, and direct the practitioner to
  complete the amendment cycle (Phase 2 amends; Phase 3 re-enters;
  Phase 4 starts against the amended bundle). If §7 is empty, or its
  amendments were resolved into a re-synthesized bundle, record the
  check as passed and continue.
- Has any Phase 3 amendment landed between Phase 3 completion and
  this Phase 4 start? (Practitioner check; if yes, the amended
  bundle is the input, not the original.)
- Has the Phase 2 Improvement Plan been amended since the bundle was
  synthesized? (Bundle §0 verified currency at synthesis time;
  re-verify at Phase 4 entry.)
- Has the subject shipped any release since Phase 3 completion?
  (Patch releases between phases are common; the Step 02 baseline
  anchors against the post-release state, and Step 09 pre-change
  interface citations must match what is actually shipped.)
- **Did a scheduled mechanism ship *early* via a parallel track?**
  *(The concurrent-release / dependency-shipped-early decision rule,
  inherited from Phase 3 v1.1.)* Beyond plain patch releases, check
  whether a separate release/productization effort shipped a
  mechanism the Improvement Plan scheduled for a *future* release,
  or a dependency the design specifications assumed unreleased. If
  so, apply the decision rule from the instructions file's currency
  behavioral rule: does the shipped reality *invalidate* an upstream
  commitment (→ record here; the Step 08/09 invalidation checks
  confirm and route through Step 12's Channel 2/3 packages) or
  merely *de-risk/ground* it (→ grounding note; reference the
  now-real artifact concretely in Step 02's baseline)? Two
  productization tracks sharing one subject at different cadences is
  a recurring condition to name here, not an anomaly.

### 2. Design Specification Catalog (Bundle §1)

- Enumerate every catalog entry. Confirm the count and identity of
  each: Brief ID, source MC(s), artifact type (Contract / Refactor /
  IA / Schema / Observability / Verification / Other (declared
  shape)), specification status.
- For each entry, confirm the **key design decisions Phase 4
  architecture depends on** — what module mapping and change
  specification will be built against. By artifact type, typically:
  the chosen contract surface (Contract); the pre/post interface
  pair and preserved invariants (Refactor); the layer structure
  (IA); the schema layout and emission point (Schema); the
  touchpoint inventory (Observability); the instrument set
  (Verification); the declared shape and its intended landing
  (Other).
- Confirm access to the per-brief Design Specification Artifacts
  (Phase 3 Step 03). The catalog names them; the design-level detail
  Steps 08–09 consume lives in the artifacts themselves. An
  unreachable specification artifact is a Phase 4 local gap with a
  named resolution path.
- For every entry with status **"Complete with gaps"**: what exactly
  is the gap, and what does it mean for module mapping? Does it
  block a Step 08 boundary decision, or is it a detail Step 09 can
  carry as an open question? Record the determination per entry.
- For any entry with status **"Surfaced invalidation"**: this should
  correspond to a Bundle §7 amendment. If the catalog shows an
  invalidation but §7 is empty (or vice versa), that is a candidate
  upstream Phase 3 toolkit gap — the synthesis step's
  cross-consistency did not hold.

### 3. Principle Weights & Phase 3 Scorecard Refresh (Bundle §4)

- Confirm each of the six principles' weights — Security,
  Maintainability, Economics, Operations, Scoring & Metrics,
  Correctness Verification — set at Phase 2 Step 02 and inherited
  through Phase 3 unchanged.
- Confirm Phase 4 will use these weights unchanged. If architecture
  work later suggests different weights, that is a Channel 3
  amendment or a Channel 1 toolkit gap — never silent re-weighting.
- Confirm the Phase 3 scorecard refresh outcomes per principle
  (Bundle §4.2). **The Phase 3 refresh is the baseline the Step 12
  Phase 4 refresh measures against** — not Phase 2's scorecard
  directly.
- For each principle the refresh left CONDITIONAL, confirm: what
  made it conditional; the remediation path Phase 3 named (typically
  "Phase 4 produces X" or "next-cycle Phase 2 re-weights Y"); and
  **whether the remediation is in scope for *this* Phase 4 run**. A
  CONDITIONAL whose named remediation is Phase 4 work must be
  traceable to the step that will produce it.
- Confirm the explicit deprioritizations the cycle made (e.g., a
  principle held at reduced weight with next-cycle elevation).
  Phase 4 preserves each deprioritization as deprioritization — the
  frameworks land what Phase 3 designed, no more, no less.
- Confirm the Bundle §4.3 target distribution result at Phase 3 exit
  (all-PASS / ≤2 CONDITIONALs / any FAIL). An exit that passed with
  caveats tells Phase 4 where its own refresh will be under
  pressure.

### 4. Coordination Map (Bundle §2)

- Enumerate the coordination entries: cross-references between
  briefs, shared decisions binding multiple specifications, Phase 5
  ordering constraints, and verification dependencies.
- For each shared decision, confirm which briefs it binds and what
  it fixed — Phase 4 boundary decisions must not violate a decision
  two specifications share.
- Confirm the Phase 5 ordering constraints and any
  **coordinated-landing cohorts** — sets of changes Phase 3
  determined must land together. Step 08 §6 (inter-module
  dependencies and Step 09 sequencing) inherits these constraints,
  and Step 09 parallel sessions must not split a cohort across
  incompatible orderings.
- Confirm, per coordination entry, whether it constrains **module
  boundaries** (Step 08), **sequencing** (Step 08 §6 / Phase 5
  ordering), or **verification** (Step 09 §7) — the same entry may
  constrain more than one.

### 5. Verification Strategy (Bundle §3)

- Enumerate the verification instrument inventory — the concrete
  Phase 6-executable instruments Phase 3 designed. Phase 4 module
  change specifications (Step 09 §7 test strategies) will cite them,
  and Step 12 verifies the citations.
- Confirm per-brief coverage: every §1 catalog entry has §3
  verification coverage. Phase 3 Step 06 checked this at synthesis;
  re-confirm at Phase 4 entry. An uncovered entry is a candidate gap
  (usually upstream Phase 3 toolkit; occasionally local if coverage
  exists but the mapping is ambiguous).
- Identify any instrument that presumes a test-harness placement or
  execution context Phase 4 must architect (an integration harness
  needing a home module, a fixture set needing an emission point).
  These become Step 02 scoping inputs, not surprises at Step 09.

### 6. Cost Model & Capacity Envelope Continuation

- Confirm the three-quantity cost model: dev-hours +
  AI-acceleration multiplier (per-category) + derived
  maintainer-hours, with token-count and token-cost as derived
  dimensions.
- Confirm the multiplier defaults the upstream cycle used
  (mechanical cleanup 10×, doc authorship 8×, config edit 5×, novel
  design 3× — or the project's own calibrated values) and their
  calibration tags. If no Phase 5 calibration data exists yet, the
  multipliers remain **BELIEVED** — preserve the tag; do not
  silently promote it.
- Confirm any per-brief estimate refinements Phase 3 attached. Step
  09 §9 refines at module level against these, not against the
  original Phase 2 figures.
- Confirm the capacity envelope Phase 2 worked against (typically
  the HC-NN maintainer-time + budget split from Phase 1/2). Has it
  changed between Phase 3 completion and Phase 4 start — a new
  commercial-services tier, an AI-usage budget change, a
  maintainer-time shift?
- If the envelope changed, Step 12 §6 must check the aggregated
  per-module estimates against the *new* envelope — capture the
  change as a Phase 4 local gap routed to Step 12.

### 7. Forward-Handoff Confirmation (Bundle §5.1)

- Enumerate the Bundle §5.1 rows: for each, what Phase 3 expected
  Phase 4 to **consume** from the bundle and what Phase 3 expected
  Phase 4 to **produce** against it.
- For each row, confirm which Phase 4 step (02–12) will perform the
  expected activity and which validation category above confirmed
  the input it consumes.
- **Anything Phase 3 expected Phase 4 to produce that is not covered
  by the catalog, coordination map, or verification strategy
  confirmations is a candidate gap** — classify it: Phase 4 local
  (coverable by an explicit Step 02 scoping decision) or upstream
  toolkit (the expectation exists but the input that would ground it
  was never captured).
- Confirm the expected outputs align with what this toolkit produces
  (the Architecture Blueprint Bundle and its contents). A §5.1
  expectation naming an output this toolkit has no step for is an
  upstream toolkit gap — of either the Phase 3 toolkit (wrong
  expectation) or this Phase 4 toolkit (missing slot); diagnose
  which.

### 8. Phase 1 / Phase 2 Context Access

- Is the **Phase 1 Current-State Information Report** reachable
  (loaded, pasted, or retrievable on request)? Phase 4 depends on it
  directly: Step 02 (Architecture Baseline) uses the
  technology/architecture assessment and the reusable/replaceable
  components catalog; Step 04 (Security Architecture) grounds SEC-NN
  controls in the risk/constraint/technical-debt inventory; Step 06
  (Documentation Strategy) reconciles with the existing
  documentation reality the report recorded; Step 09 §6 anchors
  performance requirements to the measured operational baselines
  where they exist.
- Is the **Phase 2 Improvement Plan** reachable? Phase 4 cites the
  MC-NN mechanisms behind each brief, the cost model and capacity
  envelope (Category 6), and the sequencing/tiering posture.
- Confirm the declared code-access mode from the Step 00 Toolset
  Augmentation Document, and whether it gives this run the access
  the upstream artifacts assume (the instructions file strongly
  recommends Search-primary or better for Phase 4).
- If either report is unreachable, classify the gap: usually Phase 4
  local (the practitioner supplies the artifact, or affected claims
  carry [QUESTION] flags and Phase 5 verification tasks), with the
  resolution path named per the local-gap rule.

### 9. Validation Gap Pre-Check (Closing Question)

Before producing the report, ask the practitioner:

> *Given the validation we've walked through, is there anything you
> expected me to check that I didn't? Specifically: are there
> aspects of the Design Specification Bundle — or the per-brief
> specifications behind it — that you find ambiguous, incomplete,
> or potentially miscommunicated to a Phase 4 session that we
> haven't surfaced?*

The pre-check exists because the validation question bank cannot
anticipate every possible gap. Practitioner-driven gap surfacing
catches what structural validation misses.

---

## Output Format

When the validation is complete, produce the Phase 3 Input Validation
Report using this structure. All sections are required. Mark any
section as `[OPEN — see Gap Register]` rather than fabricating
content or silently omitting it.

---
```markdown
# Phase 3 Input Validation Report — Phase 4 (Architecture & Modular Design)

**Project:** [subject name and version]
**Validation Date:** [date]
**Phase 3 Completion Date:** [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]
**Design Specification Bundle Version:** [version, with amendment-date if applicable]
**Phase 2 Improvement Plan Version:** [version, with amendment-date if applicable]
**Status:** Draft — Pending Practitioner Review

> ⚠️ This report validates that Phase 4 understands the Phase 3
> inputs correctly. It is **not** a re-litigation of Phase 3 design
> decisions or Phase 2 mechanism choices — both are authoritative
> for this cycle. Gaps surface either as Phase 4 local (resolve
> within Phase 4) or as upstream toolkit (queue for the responsible
> toolkit's revision in a separate session).

---

## §1 — Subject Identity & Bundle/Plan Currency

| Field | Value | Confidence |
|-------|-------|-----------|
| Subject name | | [H/M/L] |
| Subject current version | | [H/M/L] |
| Bundle synthesis date / version | | [H/M/L] |
| **Bundle §7 Amendment Package check (BLOCKING)** | [Clear — §7 empty or resolved / **HALT — unresolved amendment; Phase 4 must not proceed**] | [H/M/L] |
| Phase 3 amendments since completion? | [Yes/No, with date if Yes] | [H/M/L] |
| Improvement Plan amendments since bundle synthesis? | [Yes/No, with date if Yes] | [H/M/L] |
| Subject release since bundle synthesis? | [Yes/No, with version if Yes] | [H/M/L] |
| Scheduled mechanism / dependency shipped early via parallel track? | [No / Yes — grounding note / Yes — candidate invalidation, see Gap Register and Step 08/09 checks] | [H/M/L] |

## §2 — Design Specification Catalog Confirmation

| Brief ID | Source MC(s) | Artifact Type | Specification Status | Key Design Decisions Phase 4 Depends On | Spec Artifact Reachable? | Confidence |
|----------|-------------|---------------|---------------------|----------------------------------------|--------------------------|-----------|
| | | [Contract / Refactor / IA / Schema / Observability / Verification / Other (declared shape)] | [Complete / Complete with gaps / Surfaced invalidation] | | [Yes/No] | [H/M/L] |

**"Complete with gaps" determinations:**

| Brief ID | The Gap | Blocks Step 08 Boundary Decision? | Handling |
|----------|---------|-----------------------------------|----------|
| | | [Yes — local gap / No — Step 09 open question] | |

**Catalog ↔ §7 consistency:** [Consistent / Inconsistent — see Gap
Register (candidate upstream Phase 3 toolkit gap)]

## §3 — Principle Weights & Phase 3 Scorecard Refresh Confirmation

| Principle | Weight | Phase 3 Refresh Status (Bundle §4.2) | Confidence |
|-----------|-------:|--------------------------------------|-----------|
| Security | | [PASS/CONDITIONAL/FAIL] | [H/M/L] |
| Maintainability | | | |
| Economics | | | |
| Operations | | | |
| Scoring & Metrics | | | |
| Correctness Verification | | | |

Weights confirmed inherited from Phase 2 Step 02 unchanged: [Yes/No]
Phase 3 refresh confirmed as the Phase 4 baseline: [Yes/No]
Bundle §4.3 target distribution result at Phase 3 exit: [summary]

**CONDITIONALs and their remediation paths:**

| Principle | What Made It Conditional | Named Remediation Path | In Scope This Phase 4 Run? | Producing Step |
|-----------|-------------------------|------------------------|---------------------------|----------------|
| | | | [Yes/No/Partial] | [Step NN / next-cycle / N/A] |

**Explicit deprioritizations to preserve:**
[List each — what was deprioritized, why, what next-cycle elevation
plan exists. Phase 4 will not silently elevate.]

## §4 — Coordination Map Confirmation

| Coordination Entry | Briefs Bound | What It Fixes | Constrains | Phase 4 Step That Must Honor It | Confidence |
|--------------------|--------------|---------------|------------|--------------------------------|-----------|
| | | | [Boundary / Sequencing / Verification — one or more] | [Step 08 / Step 08 §6 / Step 09 §7 / …] | [H/M/L] |

**Coordinated-landing cohorts:**

| Cohort | Members | Constraint on Phase 4 Sequencing |
|--------|---------|----------------------------------|
| | | |

## §5 — Verification Strategy Confirmation

| Instrument | Verifies Brief(s) | Phase 4 Consumption | Harness/Placement Question for Step 02? | Confidence |
|------------|-------------------|---------------------|------------------------------------------|-----------|
| | | [Step 09 §7 citation / Step 12 verification] | [No / Yes — describe] | [H/M/L] |

**Per-brief coverage check:** [Every §1 catalog entry has §3
coverage: Yes / No — uncovered entries listed in the Gap Register]

## §6 — Cost Model & Capacity Envelope Continuation

| Item | Confirmed? | Notes |
|------|-----------|-------|
| Three-quantity model (dev-hrs + multiplier + maint-hrs) | [Yes/No] | |
| Multiplier defaults (mechanical 10×, doc 8×, config 5×, novel 3× — or project-calibrated values) | [Yes/No] | |
| Calibration tags preserved (BELIEVED until Phase 5 data) | [Yes/No] | |
| Token-count and token-cost as derived dimensions | [Yes/No] | |
| Phase 3 per-brief estimate refinements identified | [Yes/No] | |
| Step 09 §9 will refine at module level within this model | [Yes/No] | |

| Field | Phase 3 Value | Phase 4 Start Value | Change? |
|-------|--------------|---------------------|---------|
| Maintainer-time / capacity (HC-NN) | | | [Yes/No] |
| Commercial-services budget | | | |
| AI-usage budget | | | |
| Timeline | | | |

If any envelope value changed, Step 12 §6 re-checks the aggregated
per-module estimates against the new envelope (Phase 4 local gap).

## §7 — Forward-Handoff Confirmation (Bundle §5.1)

| Bundle §5.1 Row | Phase 4 Expected to Consume | Phase 4 Expected to Produce | Performing Step | Covered By Validation Category | Candidate Gap? |
|-----------------|----------------------------|----------------------------|-----------------|-------------------------------|----------------|
| | | | [Step 02–12] | [§2–§6 of this report] | [No / Yes — see Gap Register] |

**Expectations not covered by the catalog / coordination /
verification confirmations:** [list with scope classification, or
"None — all §5.1 expectations are covered"]

## §8 — Phase 1 / Phase 2 Context Access

| Artifact | Reachable? | Access Mode | Phase 4 Steps Depending On It | Confidence |
|----------|-----------|-------------|-------------------------------|-----------|
| Phase 1 Current-State Information Report | [Yes/No/Partial] | [loaded / pasted / on request] | Steps 02, 04, 06 (and Step 09 §6 baselines) | [H/M/L] |
| Phase 2 Improvement Plan | [Yes/No/Partial] | | Steps 01, 08, 09, 12 (MC-NN, cost model, envelope) | [H/M/L] |
| Per-brief Design Specification Artifacts (Phase 3 Step 03) | [Yes/No/Partial] | | Steps 08, 09, 11 | [H/M/L] |

**Declared code-access mode (from Step 00):** [Interview-only /
Search-primary / Hybrid with explicit flags — note whether it meets
the Phase 4 Search-primary-or-better recommendation]

## §9 — Validation Gap Register (Split by Scope)

### §9.1 — Phase 4 Local Gaps

Gaps that Phase 4 must resolve within its own steps, or acknowledge
as documented limitation in the Architecture Blueprint Bundle.

| Gap ID | Description | Affected Category / Brief / Step | Resolution Path | Priority |
|--------|-------------|----------------------------------|----------------|----------|
| VG-L-01 | | | [Step 02 scoping clarification / open question on Step NN / out-of-prompt practitioner answer / accepted limitation] | [H/M/L] |

### §9.2 — Upstream Toolkit Gaps

Gaps that exist because an upstream toolkit was structurally
incomplete. Queue for the responsible toolkit's revision in a
separate session. Phase 4 proceeds with workaround.

| Gap ID | Description | Owning Toolkit | What That Toolkit Was Missing | Phase 4 Workaround | Toolkit Revision Recommendation |
|--------|-------------|----------------|-------------------------------|--------------------|--------------------------------|
| VG-U-01 | | [Phase 3 / Phase 2 / Phase 1] | | | |

> **Each upstream gap requires the owning-toolkit diagnosis (which
> phase's toolkit lacked the slot — usually Phase 3, occasionally
> Phase 2 or Phase 1), the structural absence itself, and a concrete
> revision recommendation. Vague upstream gaps don't actionably
> produce toolkit improvements.**

## §10 — Validation Confidence Summary

| Validation Category | Confidence | Notes |
|--------------------|------------|-------|
| Subject identity & bundle/plan currency | [H/M/L] | |
| Design specification catalog | [H/M/L] | |
| Principle weights & Phase 3 scorecard refresh | [H/M/L] | |
| Coordination map | [H/M/L] | |
| Verification strategy | [H/M/L] | |
| Cost model & capacity envelope continuation | [H/M/L] | |
| Forward-handoff confirmation | [H/M/L] | |
| Phase 1 / Phase 2 context access | [H/M/L] | |

**Overall validation status:** [Anchored / Anchored with caveats /
Significant gaps / HALTED — unresolved Phase 2 Amendment Package]

[1–3 sentences describing the overall validation outcome and what
the next step (Step 02 Architecture Baseline & Integration Scoping)
will need to address first.]

---

## Version

v1.0 (initial validation report; re-run Step 01 if an amended bundle
or amended Improvement Plan replaces the validated inputs)
```

---

## Evaluation Checklist

Before this artifact is accepted as complete, verify all items:

- [ ] All 10 sections are populated; sections with no content are
      marked `[OPEN]` with reference to the relevant gap, not
      silently omitted
- [ ] The Bundle §7 blocking check was performed first and its
      result recorded in §1; if an unresolved Phase 2 Amendment
      Package exists, the run halted and no downstream validation or
      Phase 4 work proceeded
- [ ] Subject version is re-verified, not carried over from bundle
      metadata; releases and early-shipped mechanisms since Phase 3
      completion are checked with the grounding-vs-invalidation
      decision rule applied
- [ ] Every Bundle §1 catalog entry has a §2 row confirming its
      artifact type, specification status, the key design decisions
      Phase 4 depends on, and specification-artifact reachability
- [ ] Every "Complete with gaps" status carries a determination:
      does it block a Step 08 boundary decision or carry as a Step
      09 open question?
- [ ] Principle weights are confirmed inherited from Phase 2 Step 02
      unchanged; the Phase 3 refresh is confirmed as the Phase 4
      baseline; every CONDITIONAL has an in-scope determination and
      a producing step; deprioritizations are preserved
- [ ] Every coordination entry is confirmed with what it constrains
      (boundary / sequencing / verification) and the Phase 4 step
      that must honor it; coordinated-landing cohorts are enumerated
- [ ] Every catalog entry is confirmed to have Bundle §3
      verification coverage, or the uncovered entry is in the gap
      register
- [ ] Cost model continuation is confirmed with calibration tags
      preserved; any capacity-envelope change is captured as a local
      gap routed to Step 12 §6
- [ ] Every Bundle §5.1 forward-handoff row is confirmed covered by
      a performing step, or flagged as a candidate gap with scope
      classification
- [ ] Phase 1 / Phase 2 context access is confirmed per artifact, or
      the gap carries a named resolution path; the declared
      code-access mode is recorded
- [ ] The Validation Gap Register in §9 is split into §9.1 (Phase 4
      local, VG-L-NN) and §9.2 (upstream toolkit, VG-U-NN)
- [ ] Every upstream gap names the owning toolkit (Phase 3 / Phase 2
      / Phase 1), the specific structural absence (not just the
      symptom), and a concrete revision recommendation
- [ ] Every Phase 4 local gap names the resolution path (Step 02
      scoping clarification / open question on a named step /
      out-of-prompt / accepted limitation)
- [ ] Validation confidence per category is captured with H/M/L
      tags and rationale
- [ ] The pre-check question (Category 9) was asked and the answer
      is reflected in the gap register
- [ ] No architecture work has been produced — no module inventory,
      dispositions, boundary decisions, framework elements, or
      contracts, and no implementation content — Step 01 is
      validation only
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)

---

*Part of the Phase 4 (Existing Projects) Architecture & Modular Design Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `architecture-modular-design.existing-project.instructions.md`*
*Previous step: `step-00-building-block-discovery.prompt.md`*
*Next step: `step-02-architecture-baseline-and-integration-scoping.prompt.md`*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Phase 4 Phase 3 Input Validation prompt, the Phase 4 sibling of the Phase 3 existing-track Step 01 pattern. Two-scope split for the Validation Gap Register (Phase 4 local VG-L-NN vs upstream toolkit VG-U-NN) inherited from Phase 2 v1.1 / Phase 3 v1.0, with the upstream scope generalized to route each gap to the toolkit that owns the structural absence — usually Phase 3, occasionally Phase 2 or Phase 1. Nine validation categories (eight substantive plus the closing pre-check) keyed directly to the Design Specification Bundle's § structure (§1 Catalog, §2 Coordination Map, §3 Verification Strategy, §4 scorecard refresh, §5.1 Phase 4 handoff), opening with a hard blocking check on Bundle §7: an unresolved Phase 2 Amendment Package halts Phase 4 entry rather than registering a gap. The concurrent-release / dependency-shipped-early decision rule is inherited from Phase 3 v1.1 at initial authoring rather than waiting for a dogfood round to re-surface it. Closes Phase 4 Feedback Channel 1. |
