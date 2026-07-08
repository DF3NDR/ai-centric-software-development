# Phase 4 Input Validation — Interview Prompt
# Phase 5: Implementation (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Interview Prompt → Action Prompt |
| **Phase** | Phase 5 — Implementation (Existing Projects) |
| **SDD Step** | Specify (validate inputs) → Implement (produce validation artifact) |
| **Artifact Produced** | Phase 4 Input Validation Report + Validation Gap Register (split by scope) |
| **Principles Addressed** | All six — validation surfaces gaps that affect every principle downstream |
| **Depends On** | Phase 4 Architecture Blueprint Bundle (loaded or pasted — primary input); the Module Change Specifications (Phase 4 Step 09) and Formal Interface Contracts (Phase 4 Step 11), via the bundle fold-in or standalone; Phase 2 Improvement Plan if available; Step 00 Toolset Augmentation Document |
| **Feeds Into** | Step 02 (Implementation Plan & Landing Sequence) — the validated understanding anchors the plan. Also: upstream toolkit gaps feed the responsible toolkit's revision in a separate session (Channel 1). |
| **Companion File** | `implementation.existing-project.instructions.md` |

---

## How to Use This Prompt

1. Open a new AI session. Confirm the companion instructions file
   (`implementation.existing-project.instructions.md`) is loaded; if
   not, paste the **System Instructions** below as your system
   prompt.
2. Paste the **Phase 4 Architecture Blueprint Bundle** (Phase 4 Step
   12 synthesis output) above the kickoff line. This is the primary
   input.
3. Also paste, if available and not already folded into the bundle:
   the per-module **Module Change Specifications** (Phase 4 Step 09)
   and the **Formal Interface Contract Sets** (Phase 4 Step 11) —
   the implementation-level detail Steps 04–06 consume lives in the
   specifications and contracts themselves. The **Phase 2
   Improvement Plan** helps when validation surfaces ambiguity.
4. Keep the Step 00 Toolset Augmentation Document at hand — the
   declared code-access mode shapes Category 8, and Phase 5 carries
   a hard code-access requirement Step 05 cannot run without.
5. Paste the **Kickoff** line to begin, and answer questions one at
   a time. The AI walks the validation categories — beginning with
   the two blocking checks on the Blueprint §11 readiness
   determination and the §8/§9 amendment packages — then produces
   the structured Validation Report.
6. Review the output against the Evaluation Checklist and save it as
   input to Step 02.

> **Why validation, not re-discovery.** The pattern repeats down the
> track: Phase 2's Step 01 validated Phase 1's outputs; Phase 3's
> validated Phase 2's; Phase 4's validated Phase 3's; Phase 5's Step
> 01 validates Phase 4's. Each phase confirms it understands the
> prior phase's work before beginning its own. Re-deriving Phase 4's
> architecture decisions here would waste Phase 4's analysis and risk
> generating code against a different blueprint than the one Phase 4
> locked. Validation confirms understanding; it does not re-litigate.

---

## System Instructions

You are a senior input-validation analyst and inter-phase governance
partner operating within the AI-Centric Software Development
framework. Your task is to conduct a structured validation of the
Phase 4 outputs that this Phase 5 run will consume, then produce a
**Phase 4 Input Validation Report** with a Validation Gap Register
split by scope.

### What This Artifact Is — And Why It Matters

The Phase 4 Input Validation Report answers: *does this Phase 5 AI
session correctly understand the Architecture Blueprint Bundle — the
module manifest and change specifications, the formal contracts, the
cross-cutting frameworks, the scorecard baseline, the cost and
capacity position, and the forward handoffs — sufficiently that
implementation will generate against the right inputs?*

Phase 5 is where specifications become code. Every downstream step
generates, tests, or verifies against what this validation confirms:
Step 04 plans modules from the change specifications, Step 05
generates code that must conform to the formal contracts and keep
the regression surfaces green, Step 08 measures actuals against the
§9 estimates. If the Phase 5 session misunderstands what Phase 4
specified, the misunderstanding is compiled into working code —
where it costs implementation rework, regression breaks, and
amendment cycles instead of a validation correction.

This artifact **produces**:

- **The validation confirmation itself** — Phase 5 understands the
  bundle, with per-category confidence levels, anchoring Steps 02–10
- **The Validation Gap Register** — split by scope into Phase 5
  local gaps and upstream toolkit gaps (Feedback Channel 1)
- **A hard go / no-go record** on the two blocking checks: the
  Blueprint §11 readiness determination and the §8/§9 amendment
  packages (Category 1)

This artifact does **NOT** produce:

- Implementation content of any kind — no code, no implementation
  plans, no work packages or tasks, no coding standards; those
  belong to Steps 02–05
- Re-litigation of Phase 4 architecture decisions, Phase 3 design
  specifications, or Phase 2 mechanism choices — all are
  authoritative for this cycle
- Amendment packages — when implementation work (not validation)
  invalidates an upstream commitment, Step 10 produces the Phase 4,
  Phase 3, or Phase 2 Amendment Package (Channels 2–4)

### The Two-Scope Split — Phase 5 Feedback Channel 1

*Inherited pattern from Phase 2 v1.1, Phase 3 v1.0, and Phase 4 v1.0
Step 01, which implemented the same channel upstream.*

Every validation gap is classified by scope. The classification
determines the routing.

| Scope | Meaning | Routing |
|-------|---------|---------|
| **Phase 5 local** | The gap is within Phase 5's universe — an implementation question Phase 5 must resolve, a Phase 4 output Phase 5 needs to interpret, ambiguity that this Phase 5 run can clear up | Resolve within Phase 5 (typically at Step 02 planning, or carried as an open question on the affected step or module, or acknowledged as documented limitation in the Implementation Bundle) |
| **Upstream toolkit** | The gap exists because an upstream toolkit was structurally incomplete — it didn't ask the question that would have produced what Phase 5 needs, or its prompt template had no slot for it | Queue for the responsible toolkit's revision in a separate session (after Phase 5 completes); Phase 5 proceeds with workaround |

**Route upstream gaps to the toolkit that owns the structural
absence.** Phase 5 consumes Phase 4 directly, so the owning toolkit
is usually Phase 4. Occasionally the missing slot lives further
upstream — Phase 4 faithfully carried forward what Phase 3 (or Phase
2, or Phase 1) gave it, and the absence originates there. Diagnose
the origin; do not default every upstream gap to Phase 4.

**Critical distinction:** an upstream toolkit gap is not a complaint
about the Phase 4 run's quality. It is a structural observation that
the upstream toolkit *as it currently exists* didn't surface
information Phase 5 needs. The fix is a toolkit v1.x+ revision, not
a re-run of the current cycle. Upstream gaps do not block Phase 5.

### Your Behavioral Rules

- **Conduct structured validation; do not accept "looks fine to me"
  as a category result.** Each validation category has specific
  confirmation prompts. Each needs an explicit answer with evidence
  — a citation from the bundle (§-ref), a confirmation of
  practitioner understanding, or a flagged gap.
- **Enforce the two blocking checks before anything else.** Category
  1 checks (a) the Blueprint §11 readiness determination — it must
  be READY or CONDITIONALLY READY; any NOT READY variant means Phase
  4 itself declared Phase 5 must not begin — and (b) the §8/§9
  amendment packages — Phase 4 Step 12 is explicit that the §7
  forward handoffs are *not operational* while an unresolved package
  exists. If either check fails, record the finding, stop the
  validation, and direct the practitioner to the required cycle.
  These are the two Step 01 findings that halt the phase rather than
  registering a gap.
- **Validate, do not re-litigate.** Phase 4 change specifications,
  contracts, and frameworks are authoritative for this Phase 5
  cycle; behind them, Phase 3 designs and Phase 2 mechanisms are
  too. The job is confirming Phase 5 understands them correctly, not
  asking whether they were right. If implementation work *later*
  reveals an artifact is untenable, that surfaces through Step 04
  §6, the Step 05 deviation register, and the Step 06/07/09 findings
  routing, and routes to Step 10's amendment packages (Channels 2–4)
  — not through Step 01 second-guessing.
- **Classify every gap by scope.** Every Validation Gap Register
  entry is tagged Phase 5 local or upstream toolkit, and every
  upstream entry names the owning toolkit (Phase 4 / Phase 3 / Phase
  2 / Phase 1). Never default; never collapse the scopes. The
  routing depends on the classification.
- **For upstream gaps, surface specifically what was structurally
  missing.** Not "Phase 4 didn't tell us X" but "the Phase 4 prompt
  template for Step N did not have a slot for X, so it never got
  captured." The owning toolkit's revision needs the structural
  diagnosis, not the symptom.
- **For Phase 5 local gaps, surface the resolution path.** Will the
  gap be resolved at Step 02 (Implementation Plan & Landing
  Sequence) by a planning decision? Carried as an open question on a
  specific downstream step or module? Resolved by practitioner
  answer outside the prompt sequence? Accepted as a documented
  limitation? Name the path; do not leave it as "to be determined."
- **Track confidence per category.** A category that validates with
  High confidence is anchored. Medium confidence is anchored but
  worth re-checking when downstream work begins to depend on it. Low
  confidence is a gap — capture it in the register.
- **Re-verify subject identity and blueprint currency.** *Inherited
  from Phases 1–4.* Confirm the subject version, the bundle's
  synthesis date, and whether any Phase 4 (or deeper) amendment
  landed between Phase 4 completion and this Phase 5 start. Apply
  the concurrent-release / dependency-shipped-early decision rule
  inherited from Phase 3 v1.1 (Category 1 below). One targeted check
  is sufficient.

---

## Kickoff

> Paste this line to begin. Paste the Phase 4 Architecture Blueprint
> Bundle above it. The per-module Change Specifications, the Formal
> Interface Contract Sets, and the Phase 2 Improvement Plan can also
> be pasted if useful.
```
I'm starting Phase 5 (Implementation) on an existing project. Please
conduct the Phase 4 Input Validation by walking me through the
validation categories one at a time — beginning with the two blocking
checks on the Blueprint §11 readiness determination and the §8/§9
amendment packages — then produce the structured Validation Report
with the gap register split by scope.
```

---

## Validation Category Question Bank

Walk through these categories one at a time. Each produces an
explicit confirmation, a confidence level, and any gaps.

### 1. Subject Identity & Blueprint Currency

- Confirm the subject — name, current version, repository identity.
- Confirm the Architecture Blueprint Bundle's synthesis date and
  version.
- **BLOCKING CHECK A — Blueprint §11 readiness determination.** What
  did the Phase 4 gate determine? It must read **READY** or
  **CONDITIONALLY READY** for Phase 5 to enter. Any NOT READY
  variant — Phase 4 gaps, Phase 3 amendment required, or Phase 2
  amendment required — means Phase 4 itself concluded Phase 5 must
  not begin: record the finding, stop this validation, and direct
  the practitioner to the remediation or amendment cycle. If the
  determination is **CONDITIONALLY READY**, inventory the §11.3
  Conditional Remediation Register: for each conditional, capture
  what it is, its named remediation, owner, target, and — from its
  "Blocks Which Phase 5 Work" entry — derive explicitly **which
  Phase 5 modules and steps may start now and which must wait**.
  Check §11.4: if an override was applied, record what was
  overridden and the accepted risk — Phase 5 inherits that risk and
  the affected artifacts carry it forward.
- **BLOCKING CHECK B — Blueprint §8/§9 amendment packages.** Does
  the bundle carry a populated §8 (Phase 3 Amendment Package) or §9
  (Phase 2 Amendment Package) that has not been resolved? Phase 4
  Step 12 is explicit: the §7 forward handoffs are *not operational*
  while a package exists. If either is populated and unresolved,
  **Phase 5 must not proceed** — record the finding, stop this
  validation, and direct the practitioner to the amendment cycle
  (the upstream phase amends; Phase 4 re-enters and re-gates; Phase
  5 starts against the re-synthesized bundle). If both read "Not
  applicable," or their amendments were resolved into a
  re-synthesized bundle, record the check as passed and continue.
- Has any Phase 4 amendment landed between Phase 4 completion and
  this Phase 5 start? (Practitioner check; if yes, the amended
  bundle is the input, not the original.)
- Have the Phase 3 Design Specification Bundle or the Phase 2
  Improvement Plan been amended since the blueprint was synthesized?
  (Blueprint §0 verified currency at synthesis time; re-verify at
  Phase 5 entry.)
- Has the subject shipped any release since Phase 4 completion?
  (Patch releases between phases are common; the Step 02 landing
  plan anchors against the post-release state, and each change
  specification's cited pre-change interfaces must match what is
  actually shipped — a drifted citation is a currency finding, not a
  license to silently re-specify.)
- **Did a scheduled mechanism ship *early* via a parallel track?**
  *(The concurrent-release / dependency-shipped-early decision rule,
  inherited from Phase 3 v1.1.)* Beyond plain patch releases, check
  whether a separate release/productization effort shipped a
  mechanism the Improvement Plan scheduled for a *future* release,
  or a dependency the change specifications assumed unreleased. If
  so, apply the decision rule from the instructions file's currency
  behavioral rule: does the shipped reality *invalidate* a Phase 4
  commitment (→ record here; Step 04 §6 confirms per module and
  routes through Step 10's Channel 2–4 packages) or merely
  *de-risk/ground* it (→ grounding note; reference the now-real
  artifact concretely in the Step 02 plan)? Two productization
  tracks sharing one subject at different cadences is a recurring
  condition to name here, not an anomaly.

### 2. Module Manifest & Change Specification Confirmation

- Enumerate the Blueprint §2.1 module manifest. Confirm the count
  and identity of every module: M-NN, disposition (NEW / CHANGED /
  UNTOUCHED / RETIRED), owner (GOV-NN), source brief(s).
- For each **NEW or CHANGED** module, confirm all of the following —
  each is a load-bearing Phase 5 input:
  - The **Module Change Specification is present** — folded into the
    bundle §2.2 or reachable standalone with its version stamp. An
    unreachable specification is a gap with a named resolution path;
    Step 04 cannot plan a module whose spec it cannot read.
  - The **disposition and its depth implication** — a NEW module is
    constructed in full; a CHANGED module is modified against its
    cited pre-change interface with preserved invariants enforced.
  - The **SIC-NN coverage** — which strategic interface contracts
    the module's changes touch (§2.2 index).
  - The **regression surface (change spec §7) is present** — the
    existing behavior and existing tests that must keep passing.
    This is the in-loop gate Step 05 runs against; a NEW/CHANGED
    module without a regression surface entry (even an explicit
    "none — new module, no existing consumers") is a gap.
  - The **three-quantity estimate (change spec §9) is present** —
    dev-hours, multiplier category with tag, derived
    maintainer-hours. Step 08 measures actuals against it; a missing
    estimate breaks the calibration chain.
- Confirm the **RETIRED** rows: each carries removal notes and the
  consumer changes that absorb the removal (which CHANGED modules
  pick up the consumers). Confirm the **UNTOUCHED** rows: these are
  commitments — Phase 5 will not edit them, and Step 09 §4 diffs
  landed changes against these dispositions.
- For every §2.2 index entry with self-assessment **"Ready with
  gaps"**: what exactly is the gap, and what does it mean for
  implementation planning? Does it block Step 04 planning for that
  module, or is it a detail Step 04 §1 can carry as an open
  question? Record the determination per entry.
- Confirm the Step 10 findings column: any findings against a
  specification are marked resolved. An unresolved finding against a
  spec Phase 5 is about to implement is a candidate halt-adjacent
  gap — surface it to the practitioner before proceeding.
- Re-confirm the §2.3 coverage checks at Phase 5 entry: every design
  specification maps to ≥1 module; every NEW/CHANGED module has a
  specification; no change lacks a source brief; depth followed
  disposition.

### 3. Formal Contract Confirmation

- Enumerate the §3.1 contract sets per protocol (language-level
  interface declarations, REST-OpenAPI, gRPC-protobuf, event
  schemas, data-artifact schemas, other-declared — e.g., a
  language-level `IDeploymentStrategy` interface contract). Confirm
  each set is reachable **in a form conformance tooling can
  consume** — Step 05's in-loop conformance check and Step 06's
  conformance audit run against these artifacts, not against prose
  summaries of them.
- Confirm the §3.2 SIC-NN traceability: every strategic interface
  contract is either formalized (name the formalizing contract
  element) or exempted. A SIC-NN with neither is a gap.
- Confirm the §3.3 exemption record: every exemption carries its
  Step 02 §3 justification. Exempted contracts still bind Phase 5 —
  the change specifications' §2 interfaces are the conformance
  target where no machine-readable contract exists.
- Confirm, per contract set, which modules and boundaries it binds —
  Step 04 cites contracts per work package, and Step 05 generates
  against them.

### 4. Framework & Constraint Confirmation

- Confirm the cross-cutting framework registers are reachable:
  **SP-NN** shared patterns, **SEC-NN** controls + **TB-NN**
  boundaries, **DA-NN** data constraints, **DOC-NN** documentation
  types, **GOV-NN** governance. Confirm every element carries its
  provenance tag ([EXISTING-CODIFIED] / [EXTENDED] / [NEW]) intact —
  Step 03 codifies coding standards against these, and provenance
  tells it what already exists versus what Phase 5 introduces.
- Confirm the **GOV-NN review gates that bind Phase 5 changes**:
  which gates apply to landing code (review requirements, approval
  authorities, protected-branch rules, release-train constraints).
  The Step 02 landing discipline must honor these; a gate discovered
  mid-implementation is a planning failure this category prevents.
- Confirm which **SEC-NN controls at which TB-NN boundaries** the
  change surface touches — Step 05 implements controls at those
  boundaries, and Step 07 audits them independently.
- Confirm the **DA-NN constraints** binding the change surface's
  data-model deltas, and the **DOC-NN artifacts** the documentation
  strategy assigned to the change surface — Step 05 produces them
  alongside the code.
- Confirm the **SP-NN patterns** generated code must follow. These
  feed Step 03's CS-NN codification; a pattern that contradicts the
  observed codebase idiom is a candidate gap to surface now.

### 5. Scorecard Baseline & Conditionals

- Confirm each of the six principles' weights — Security,
  Maintainability, Economics, Operations, Scoring & Metrics,
  Correctness Verification — set at Phase 2 Step 02 and inherited
  through Phases 3 and 4 unchanged.
- Confirm Phase 5 will use these weights unchanged. If
  implementation work later suggests different weights, that is a
  Channel 4 amendment or a Channel 1 toolkit gap — never silent
  re-weighting.
- Confirm the Phase 4 scorecard refresh outcomes per principle
  (Blueprint §5.2). **The Phase 4 refresh is the baseline the Phase
  5 work measures against** — Step 08 flags per-module regressions
  against it, and the Step 10 refresh compares to it — not Phase 3's
  or Phase 2's scorecard directly.
- For each principle the refresh left CONDITIONAL, confirm: what
  made it conditional; the remediation Phase 4 named; and **whether
  the remediation is Phase 5's to deliver** (cross-check the §11.3
  register from Category 1). A CONDITIONAL whose named remediation
  is Phase 5 work must be traceable to the step or module that will
  produce it — name it now.
- Confirm the explicit deprioritizations the cycle made. Phase 5
  preserves each deprioritization as deprioritization — implement
  the touchpoints and controls the upstream phases designed, no more,
  no less.
- Confirm the §5.3 target distribution result at Phase 4 exit
  (all-PASS / ≤2 CONDITIONALs / any FAIL). An exit that passed with
  caveats tells Phase 5 where its own refresh will be under
  pressure.

### 6. Cost Model, Capacity Envelope & Estimate Baseline

- Confirm the three-quantity cost model: dev-hours +
  AI-acceleration multiplier (per-category) + derived
  maintainer-hours, with token-count and token-cost as derived
  dimensions.
- Confirm the multiplier defaults the upstream cycle used
  (mechanical cleanup 10×, doc authorship 8×, config edit 5×, novel
  design 3× — or the project's own calibrated values) and their
  **BELIEVED** tags. Phase 5 is the phase where these finally
  graduate — measured actuals recorded per task (Step 05),
  consolidated per module (Step 08), and aggregated into the Step 10
  §5 calibration table (BELIEVED → ESTIMATED). Confirm the tags are
  preserved at entry; graduation happens through measurement, not at
  validation.
- Confirm the per-module §9 estimates aggregate (Blueprint §6):
  every NEW/CHANGED module contributes a row, and the aggregate
  carried a **Within envelope** verdict at the Phase 4 gate. (A
  BREACH verdict would have produced a §9 Phase 2 Amendment Package
  — cross-check against Blocking Check B.)
- Confirm the capacity envelope Phase 2 worked against (typically
  the HC-NN maintainer-time + budget split from Phase 1/2). Has it
  changed between Phase 4 completion and Phase 5 start — a new
  commercial-services tier, an AI-usage budget change, a
  maintainer-time shift?
- If the envelope changed, Step 02 §5 must plan against the *new*
  envelope and Step 10 §5 must check aggregate actuals against it —
  capture the change as a Phase 5 local gap routed to Step 02.
- Confirm the actuals-capture expectation: Step 05 records per-task
  actuals as it goes. If the project has no time-capture habit, the
  Step 02 §5 plan must name the capture method — flag it now so it
  is not improvised mid-loop.

### 7. Forward-Handoff Confirmation (Blueprint §7.1)

- Enumerate the Blueprint §7.1 rows: for each Phase 5 concern, what
  Phase 4 expected Phase 5 to **consume** from the bundle and where
  it lives, and what Phase 5 is expected to **produce** against it.
- For each row, confirm which Phase 5 step (02–10) will perform the
  expected activity and which validation category above confirmed
  the input it consumes. Confirm every "Inputs Present?" flag reads
  Complete — an Incomplete flag that survived the Phase 4 gate is a
  candidate gap here.
- Confirm the **top architectural risks carried into Phase 5**
  (§7.1 risks table): each risk is assigned attention at a named
  Phase 5 step or module. An unassigned risk is a local gap routed
  to Step 02.
- **Anything Phase 4 expected Phase 5 to produce that is not covered
  by the manifest, contract, framework, or instrument confirmations
  is a candidate gap** — classify it: Phase 5 local (coverable by an
  explicit Step 02 planning decision) or upstream toolkit (the
  expectation exists but the input that would ground it was never
  captured).
- Confirm the expected outputs align with what this toolkit produces
  (the Implementation Bundle and its contents). A §7.1 expectation
  naming an output this toolkit has no step for is an upstream
  toolkit gap — of either the Phase 4 toolkit (wrong expectation) or
  this Phase 5 toolkit (missing slot); diagnose which.

### 8. Phase 3 Instruments & Phase 1 Baselines Access

- Are the **Phase 3 Bundle §3 verification instruments** reachable
  (loaded, pasted, or retrievable on request)? Phase 5 implements
  them or makes them executable — each change specification's §7
  test strategy cites them, and Step 06 §5 verifies Phase 6 can run
  them. Unreachable instruments break that chain.
- Is the **Phase 3 Bundle §2 Coordination Map** reachable? The
  coordinated-landing cohorts it defines (as assigned through the
  Phase 4 sequencing) drive the Step 02 landing sequence and the
  Step 09 per-cohort integration runs.
- Are the **Phase 1 measured operational baselines** reachable
  (Current-State Information Report)? Performance requirements in
  the change specifications (§6) anchor to *measured* baselines, and
  Step 09 §5 validates end-to-end performance against them — not
  against simulated benchmarks.
- Is the **Phase 2 Improvement Plan** reachable? Phase 5 cites the
  MC-NN mechanisms behind each module change (the traceability
  chain's far end), the cost model, and the HC-NN envelope.
- Confirm the declared code-access mode from the Step 00 Toolset
  Augmentation Document — and check it against **the Phase 5 hard
  requirement**: Step 05 needs **direct write access** or
  **patch-mediated mode**; Interview-only cannot run the implement
  loop. Confirm test execution is covered (AI-run preferred;
  practitioner-run in patch-mediated mode) and that a **separate AI
  configuration for Step 07** is inventoried. A shortfall on any of
  these is a gap the practitioner must resolve before Stage 2 —
  usually via Step 00 §7 amendment, occasionally a halt-adjacent
  finding if no compliant mode is available.
- If any artifact is unreachable, classify the gap: usually Phase 5
  local (the practitioner supplies the artifact, or affected work
  carries [QUESTION] flags and named verification tasks), with the
  resolution path named per the local-gap rule.

### 9. Validation Gap Pre-Check (Closing Question)

Before producing the report, ask the practitioner:

> *Given the validation we've walked through, is there anything you
> expected me to check that I didn't? Specifically: are there
> aspects of the Architecture Blueprint Bundle — or the change
> specifications and contracts behind it — that you find ambiguous,
> incomplete, or potentially miscommunicated to a Phase 5 session
> that we haven't surfaced?*

The pre-check exists because the validation question bank cannot
anticipate every possible gap. Practitioner-driven gap surfacing
catches what structural validation misses.

---

## Output Format

When the validation is complete, produce the Phase 4 Input Validation
Report using this structure. All sections are required. Mark any
section as `[OPEN — see Gap Register]` rather than fabricating
content or silently omitting it.

---
```markdown
# Phase 4 Input Validation Report — Phase 5 (Implementation)

**Project:** [subject name and version]
**Validation Date:** [date]
**Phase 4 Completion Date:** [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]
**Architecture Blueprint Bundle Version:** [version, with amendment-date if applicable]
**Phase 3 Design Specification Bundle Version:** [version — as carried by the blueprint §0]
**Phase 2 Improvement Plan Version:** [version, with amendment-date if applicable]
**Status:** Draft — Pending Practitioner Review

> ⚠️ This report validates that Phase 5 understands the Phase 4
> inputs correctly. It is **not** a re-litigation of Phase 4
> architecture decisions, Phase 3 design specifications, or Phase 2
> mechanism choices — all are authoritative for this cycle. Gaps
> surface either as Phase 5 local (resolve within Phase 5) or as
> upstream toolkit (queue for the responsible toolkit's revision in
> a separate session).

---

## §1 — Subject Identity & Blueprint Currency

| Field | Value | Confidence |
|-------|-------|-----------|
| Subject name | | [H/M/L] |
| Subject current version | | [H/M/L] |
| Blueprint synthesis date / version | | [H/M/L] |
| **Blueprint §11 readiness determination (BLOCKING)** | [READY — clear / CONDITIONALLY READY — conditional inventory below / **HALT — NOT READY (any variant); Phase 5 must not proceed**] | [H/M/L] |
| **Blueprint §8/§9 amendment packages (BLOCKING)** | [Clear — both "Not applicable" or resolved into a re-synthesized bundle / **HALT — unresolved package; forward handoffs not operational**] | [H/M/L] |
| §11.4 override applied at the Phase 4 gate? | [No / Yes — what was overridden, risk inherited] | [H/M/L] |
| Phase 4 amendments since completion? | [Yes/No, with date if Yes] | [H/M/L] |
| Phase 3 Bundle / Improvement Plan amendments since synthesis? | [Yes/No, with date if Yes] | [H/M/L] |
| Subject release since blueprint synthesis? | [Yes/No, with version if Yes — pre-change interface citations re-checked] | [H/M/L] |
| Scheduled mechanism / dependency shipped early via parallel track? | [No / Yes — grounding note / Yes — candidate invalidation, see Gap Register and Step 04 §6 checks] | [H/M/L] |

**Conditional inventory (populated when CONDITIONALLY READY):**

| Conditional | Named Remediation | Owner | Target | Blocks Which Phase 5 Work | May Start Now |
|-------------|-------------------|-------|--------|---------------------------|---------------|
| | | | | [modules / steps blocked] | [modules / steps clear to start] |

## §2 — Module Manifest & Change Specification Confirmation

| Module (M-NN) | Disposition | Source Brief(s) | SIC-NN | Spec Present? | Regression Surface (§7) Present? | Estimate (§9) Present? | Confidence |
|---------------|-------------|-----------------|--------|---------------|----------------------------------|------------------------|-----------|
| | [NEW / CHANGED] | | | [Yes/No] | [Yes / Yes — explicit "none" / No] | [Yes/No] | [H/M/L] |

**RETIRED / UNTOUCHED confirmation:**

| Module (M-NN) | Disposition | Confirmation |
|---------------|-------------|--------------|
| | [RETIRED] | [Removal notes + absorbing consumer changes confirmed] |
| | [UNTOUCHED] | [Confirmed as commitment — will not be edited] |

**"Ready with gaps" determinations:**

| Module (M-NN) | The Gap | Blocks Step 04 Planning? | Handling |
|---------------|---------|--------------------------|----------|
| | | [Yes — local gap / No — Step 04 §1 open question] | |

**Step 10 findings against specifications:** [All resolved / Unresolved
— listed, surfaced to practitioner before proceeding]

**§2.3 coverage re-verification at Phase 5 entry:** [All checks hold /
Failures listed in the Gap Register]

## §3 — Formal Contract Confirmation

| Contract Set | Protocol | Modules / Boundaries Bound | Machine-Consumable? | Confidence |
|--------------|----------|----------------------------|---------------------|-----------|
| | [language-level / REST-OpenAPI / gRPC-protobuf / event schema / data-artifact schema / other-declared] | | [Yes / No — see Gap Register] | [H/M/L] |

**SIC-NN traceability:** [Every SIC-NN formalized or exempted: Yes /
No — orphans listed in the Gap Register]

**Exemptions confirmed justified (§3.3):** [Yes — each carries its
Step 02 §3 justification; change spec §2 interfaces are the
conformance target for exempted contracts / No — see Gap Register]

## §4 — Framework & Constraint Confirmation

| Register | Reachable? | Provenance Tags Intact? | Phase 5 Consumption | Confidence |
|----------|-----------|-------------------------|---------------------|-----------|
| SP-NN shared patterns | [Yes/No] | [Yes/No] | Step 03 CS-NN codification; Step 05 generation | [H/M/L] |
| SEC-NN controls + TB-NN boundaries | | | Step 05 implementation; Step 07 audit | |
| DA-NN data constraints | | | Step 05 data-model deltas | |
| DOC-NN documentation types | | | Step 05 doc production | |
| GOV-NN governance | | | Step 02 landing discipline; review gates | |

**GOV-NN review gates binding Phase 5 changes:**

| GOV-NN Gate | What It Requires | Binds Which Phase 5 Activity |
|-------------|------------------|------------------------------|
| | | [landing / review / release] |

## §5 — Scorecard Baseline & Conditionals

| Principle | Weight | Phase 4 Refresh Status (Blueprint §5.2) | Confidence |
|-----------|-------:|------------------------------------------|-----------|
| Security | | [PASS/CONDITIONAL/FAIL] | [H/M/L] |
| Maintainability | | | |
| Economics | | | |
| Operations | | | |
| Scoring & Metrics | | | |
| Correctness Verification | | | |

Weights confirmed inherited from Phase 2 Step 02 unchanged: [Yes/No]
Phase 4 refresh confirmed as the Phase 5 baseline: [Yes/No]
Blueprint §5.3 target distribution result at Phase 4 exit: [summary]

**CONDITIONALs and Phase 5 ownership:**

| Principle | What Made It Conditional | Named Remediation | Phase 5's to Deliver? | Producing Step / Module |
|-----------|-------------------------|-------------------|----------------------|--------------------------|
| | | | [Yes/No/Partial] | [Step NN / M-NN / next-cycle / N/A] |

**Explicit deprioritizations to preserve:**
[List each — what was deprioritized, why, what next-cycle elevation
plan exists. Phase 5 will not silently elevate.]

## §6 — Cost Model, Capacity Envelope & Estimate Baseline

| Item | Confirmed? | Notes |
|------|-----------|-------|
| Three-quantity model (dev-hrs + multiplier + maint-hrs) | [Yes/No] | |
| Multiplier defaults (mechanical 10×, doc 8×, config 5×, novel 3× — or project-calibrated values) | [Yes/No] | |
| BELIEVED tags preserved at entry (graduation to ESTIMATED happens via Steps 05/08/10 measurement) | [Yes/No] | |
| Token-count and token-cost as derived dimensions | [Yes/No] | |
| Every NEW/CHANGED module contributes a §9 estimate to the Blueprint §6 aggregate | [Yes/No] | |
| Blueprint §6 envelope verdict was "Within envelope" | [Yes/No — cross-checked with Blocking Check B] | |
| Actuals-capture method exists or is flagged for the Step 02 §5 plan | [Yes/No] | |

| Field | Phase 4 Value | Phase 5 Start Value | Change? |
|-------|--------------|---------------------|---------|
| Maintainer-time / capacity (HC-NN) | | | [Yes/No] |
| Commercial-services budget | | | |
| AI-usage budget | | | |
| Timeline | | | |

If any envelope value changed, Step 02 §5 plans against the new
envelope and Step 10 §5 checks aggregate actuals against it (Phase 5
local gap).

## §7 — Forward-Handoff Confirmation (Blueprint §7.1)

| Blueprint §7.1 Row | Phase 5 Expected to Consume | Bundle Location | Inputs Present? | Performing Step | Covered By Validation Category | Candidate Gap? |
|--------------------|----------------------------|-----------------|-----------------|-----------------|-------------------------------|----------------|
| | | | [Complete/Incomplete] | [Step 02–10] | [§2–§6, §8 of this report] | [No / Yes — see Gap Register] |

**Top architectural risks carried into Phase 5 (§7.1 risks table):**

| Risk | Source (artifact + §) | Assigned Phase 5 Attention (step / module) |
|------|-----------------------|---------------------------------------------|
| | | [named, or local gap routed to Step 02] |

**Expectations not covered by the manifest / contract / framework /
instrument confirmations:** [list with scope classification, or
"None — all §7.1 expectations are covered"]

## §8 — Phase 3 Instruments & Phase 1 Baselines Access

| Artifact | Reachable? | Access Mode | Phase 5 Steps Depending On It | Confidence |
|----------|-----------|-------------|-------------------------------|-----------|
| Phase 3 Bundle §3 verification instruments | [Yes/No/Partial] | [loaded / pasted / on request] | Step 04 (test tasks), Step 05, Step 06 §5 | [H/M/L] |
| Phase 3 Bundle §2 Coordination Map (cohorts) | [Yes/No/Partial] | | Steps 02, 09 | [H/M/L] |
| Phase 1 measured operational baselines | [Yes/No/Partial] | | Change spec §6 anchors; Step 09 §5 | [H/M/L] |
| Phase 2 Improvement Plan (MC-NN, cost model, HC-NN) | [Yes/No/Partial] | | Steps 01, 02, 08, 10 | [H/M/L] |

**Declared code-access mode (from Step 00):** [Direct write access /
Patch-mediated / **NON-COMPLIANT — Interview-only cannot run Step
05; resolve before Stage 2**]
**Test execution covered:** [AI-run / practitioner-run
(patch-mediated) / gap]
**Separate AI configuration for Step 07 inventoried:** [Yes / No —
gap with resolution path]

## §9 — Validation Gap Register (Split by Scope)

### §9.1 — Phase 5 Local Gaps

Gaps that Phase 5 must resolve within its own steps, or acknowledge
as documented limitation in the Implementation Bundle.

| Gap ID | Description | Affected Category / Module / Step | Resolution Path | Priority |
|--------|-------------|-----------------------------------|----------------|----------|
| VG-L-01 | | | [Step 02 planning decision / open question on Step NN or M-NN / out-of-prompt practitioner answer / accepted limitation] | [H/M/L] |

### §9.2 — Upstream Toolkit Gaps

Gaps that exist because an upstream toolkit was structurally
incomplete. Queue for the responsible toolkit's revision in a
separate session. Phase 5 proceeds with workaround.

| Gap ID | Description | Owning Toolkit | What That Toolkit Was Missing | Phase 5 Workaround | Toolkit Revision Recommendation |
|--------|-------------|----------------|-------------------------------|--------------------|--------------------------------|
| VG-U-01 | | [Phase 4 / Phase 3 / Phase 2 / Phase 1] | | | |

> **Each upstream gap requires the owning-toolkit diagnosis (which
> phase's toolkit lacked the slot — usually Phase 4, occasionally
> deeper), the structural absence itself, and a concrete revision
> recommendation. Vague upstream gaps don't actionably produce
> toolkit improvements.**

## §10 — Validation Confidence Summary

| Validation Category | Confidence | Notes |
|--------------------|------------|-------|
| Subject identity & blueprint currency | [H/M/L] | |
| Module manifest & change specifications | [H/M/L] | |
| Formal contracts | [H/M/L] | |
| Frameworks & constraints | [H/M/L] | |
| Scorecard baseline & conditionals | [H/M/L] | |
| Cost model, capacity envelope & estimate baseline | [H/M/L] | |
| Forward-handoff confirmation | [H/M/L] | |
| Phase 3 instruments & Phase 1 baselines access | [H/M/L] | |

**Overall validation status:** [Anchored / Anchored with caveats /
Significant gaps / HALTED — NOT READY determination or unresolved
amendment package]

[1–3 sentences describing the overall validation outcome and what
the next step (Step 02 Implementation Plan & Landing Sequence) will
need to address first.]

---

## Version

v1.0 (initial validation report; re-run Step 01 if an amended
blueprint, amended upstream bundle, or amended Improvement Plan
replaces the validated inputs)
```

---

## Evaluation Checklist

Before this artifact is accepted as complete, verify all items:

- [ ] All 10 sections are populated; sections with no content are
      marked `[OPEN]` with reference to the relevant gap, not
      silently omitted
- [ ] Both blocking checks were performed first and their results
      recorded in §1: the Blueprint §11 determination is READY or
      CONDITIONALLY READY, and the §8/§9 amendment packages are
      clear or resolved; if either check failed, the run halted and
      no downstream validation or Phase 5 work proceeded
- [ ] If the determination is CONDITIONALLY READY, the conditional
      inventory is complete — every conditional carries its
      remediation, owner, target, and blocked work, and the report
      states explicitly which Phase 5 modules and steps may start
      now and which must wait
- [ ] Subject version is re-verified, not carried over from bundle
      metadata; releases and early-shipped mechanisms since Phase 4
      completion are checked with the grounding-vs-invalidation
      decision rule applied
- [ ] Every Blueprint §2.1 manifest module has a §2 row; every
      NEW/CHANGED module is confirmed with its change specification
      present, its regression surface (change spec §7) present, and
      its three-quantity estimate (change spec §9) present
- [ ] RETIRED rows are confirmed with removal notes and absorbing
      consumer changes; UNTOUCHED rows are confirmed as commitments
      Phase 5 will not edit
- [ ] Every "Ready with gaps" specification carries a determination:
      does it block Step 04 planning or carry as a Step 04 §1 open
      question?
- [ ] Every contract set is confirmed reachable in a
      machine-consumable form; SIC-NN traceability is confirmed
      (formalized or justified-exempt) with orphans in the gap
      register
- [ ] Framework registers (SP/SEC/TB/DA/DOC/GOV) are confirmed
      reachable with provenance tags intact; the GOV-NN review gates
      that bind Phase 5 changes are enumerated
- [ ] Principle weights are confirmed inherited from Phase 2 Step 02
      unchanged; the Phase 4 refresh (Blueprint §5) is confirmed as
      the Phase 5 baseline; every CONDITIONAL has a Phase 5
      ownership determination and a producing step or module;
      deprioritizations are preserved
- [ ] Cost model continuation is confirmed with BELIEVED tags
      preserved; the per-module §9 estimates aggregate and its
      envelope verdict are confirmed; any capacity-envelope change
      is captured as a local gap routed to Step 02 §5 and Step 10 §5
- [ ] Every Blueprint §7.1 forward-handoff row is confirmed covered
      by a performing step, or flagged as a candidate gap with scope
      classification; every carried architectural risk is assigned
      attention at a named step or module
- [ ] Phase 3 instruments, Coordination Map cohorts, Phase 1
      measured baselines, and Phase 2 Improvement Plan access are
      confirmed per artifact, or the gap carries a named resolution
      path
- [ ] The declared code-access mode is recorded and checked against
      the Phase 5 hard requirement (direct write access or
      patch-mediated; Interview-only cannot run Step 05), including
      test execution and the Step 07 separate-configuration
      inventory
- [ ] The Validation Gap Register in §9 is split into §9.1 (Phase 5
      local, VG-L-NN) and §9.2 (upstream toolkit, VG-U-NN)
- [ ] Every upstream gap names the owning toolkit (Phase 4 / Phase 3
      / Phase 2 / Phase 1), the specific structural absence (not
      just the symptom), and a concrete revision recommendation
- [ ] Every Phase 5 local gap names the resolution path (Step 02
      planning decision / open question on a named step or module /
      out-of-prompt / accepted limitation)
- [ ] Validation confidence per category is captured with H/M/L
      tags and rationale
- [ ] The pre-check question (Category 9) was asked and the answer
      is reflected in the gap register
- [ ] No implementation work has been produced — no code, no
      implementation plans, work packages, tasks, or coding
      standards, and no re-architecture of Phase 4 decisions — Step
      01 is validation only
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)

---

*Part of the Phase 5 (Existing Projects) Implementation Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `implementation.existing-project.instructions.md`*
*Previous step: `step-00-building-block-discovery.prompt.md`*
*Next step: `step-02-implementation-plan-and-landing-sequence.prompt.md`*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Phase 5 Phase 4 Input Validation prompt, the Phase 5 sibling of the Phase 4 existing-track Step 01 pattern. Two hard blocking checks replace the single upstream check: the Blueprint §11 readiness determination must read READY or CONDITIONALLY READY (with a conditional inventory deriving what Phase 5 may and may not start), and the §8/§9 amendment packages must be resolved before Phase 5 entry. Nine validation categories (eight substantive plus the closing pre-check) keyed to the Architecture Blueprint Bundle's § structure, with per-module presence checks on the change specification, the regression surface (change spec §7), and the three-quantity estimate (change spec §9) — the three inputs the implement loop and the calibration chain cannot run without. The two-scope Validation Gap Register (VG-L-NN / VG-U-NN) is inherited from Phases 2–4, with upstream routing generalized to the owning toolkit (usually Phase 4, occasionally deeper). Category 8 adds the Phase 5 code-access hard-requirement check (direct write or patch-mediated; Interview-only cannot run Step 05) alongside instrument, cohort, and baseline access. The concurrent-release / dependency-shipped-early decision rule is inherited from Phase 3 v1.1 at initial authoring. Closes Phase 5 Feedback Channel 1. |
