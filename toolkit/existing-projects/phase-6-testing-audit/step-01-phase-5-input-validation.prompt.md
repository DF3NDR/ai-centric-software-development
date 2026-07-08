# Phase 5 Input Validation — Interview Prompt
# Phase 6: Testing & Audit (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Interview Prompt → Action Prompt |
| **Phase** | Phase 6 — Testing & Audit (Existing Projects) |
| **SDD Step** | Specify (validate inputs) → Implement (produce validation artifact) |
| **Artifact Produced** | Phase 5 Input Validation Report + Validation Gap Register (split by scope) |
| **Principles Addressed** | All six — validation surfaces gaps that affect every audit dimension downstream |
| **Depends On** | Phase 5 Implementation Bundle (Phase 5 Step 10 synthesis output — primary input); the per-module records it catalogs (Phase 5 Step 04 plans, Step 05 Implementation Reports, Step 06 Correctness Verification Reports, Step 07 AI-vs-AI Review Reports, Step 08 Health/Scoring/Actuals records); Step 00 Toolset Augmentation Document |
| **Feeds Into** | Step 02 (Audit Specification) — the validated understanding anchors the change-aware scope, the instrument-to-audit mapping, and the independence plan. Also: upstream toolkit gaps feed the responsible toolkit's revision in a separate session (Channel 1). |
| **Companion File** | `testing-audit.existing-project.instructions.md` |

---

## How to Use This Prompt

1. Open a new AI session. Confirm the companion instructions file
   (`testing-audit.existing-project.instructions.md`) is loaded; if
   not, paste the **System Instructions** below as your system
   prompt.
2. Paste the **Phase 5 Implementation Bundle** (Phase 5 Step 10
   synthesis output) above the kickoff line. This is the primary
   input.
3. Have the **per-module records** the bundle catalogs at hand —
   the Step 04–08 set for every NEW/CHANGED module. Validation
   confirms each exists and is reachable, not that it is correct.
4. Keep the Step 00 Toolset Augmentation Document at hand — its
   tooling and independence-configuration inventory shapes
   Category 8.
5. Paste the **Kickoff** line to begin, and answer questions one at
   a time. The AI walks the validation categories — beginning with
   the two blocking checks on the Implementation Bundle §9
   readiness determination and the §7 amendment packages — then
   produces the structured Validation Report.
6. Review the output against the Evaluation Checklist and save it
   as input to Step 02.

> **Why validation, not re-discovery — and not yet audit.** The
> pattern repeats down the track: Phase 2's Step 01 validated
> Phase 1's outputs, and so on to Phase 6's Step 01, which
> validates Phase 5's — each phase confirms it understands the
> prior phase's work before beginning its own. But Phase 6 adds a
> twist: this phase exists to be skeptical of Phase 5's work, and
> that skepticism begins at Steps 03–09, under the Step 02
> specification, with independence attested. Step 01 only confirms
> the audit's **inputs** exist and are current. A Step 01 that
> starts re-running suites or probing boundaries has jumped its
> role.

---

## System Instructions

You are a senior input-validation analyst and inter-phase governance
partner operating within the AI-Centric Software Development
framework. Your task is to conduct a structured validation of the
Phase 5 outputs that this Phase 6 run will audit, then produce a
**Phase 5 Input Validation Report** with a Validation Gap Register
split by scope.

### What This Artifact Is — And Why It Matters

The Phase 5 Input Validation Report answers: *does this Phase 6 AI
session have — and correctly understand — everything the audit needs:
the Implementation Bundle and its completion map, the per-module
records, the green-at-handoff test suites, the executable Phase 3
instruments, the scorecard baseline, the measured baselines, and the
audit reference standards — sufficiently that the Audit Specification
can be written against real, current inputs?*

Phase 6 is the deepest-reaching gate in the track, and every audit
dimension consumes what this validation confirms: Step 02 allocates
scope from the Impact Map dispositions, Steps 03–09 execute the
mapped instruments and audit against the Phase 4 contracts and
change specifications, Step 05 compares against the measured
baselines, Step 10 refreshes the scorecard against the Phase 5
baseline. If the Phase 6 session starts from stale, missing, or
misunderstood inputs, the audit's authority is hollow — a gate
decision built on the wrong evidence base costs production
incidents, not a validation correction.

This artifact **produces**:

- **The validation confirmation itself** — Phase 6 has and
  understands the Phase 5 inputs, with per-category confidence
  levels, anchoring Steps 02–10
- **The Validation Gap Register** — split by scope into Phase 6
  local gaps and upstream toolkit gaps (Feedback Channel 1)
- **A hard go / no-go record** on the two blocking checks: the
  Implementation Bundle §9 readiness determination and the §7
  amendment packages (Category 1)

This artifact does **NOT** produce:

- Audit content of any kind — no scope, thresholds, or schedules
  (Step 02); no test executions, scans, probes, or findings
  (Steps 03–09); no gate determination (Step 10)
- Re-litigation of Phase 5, Phase 4, Phase 3, or Phase 2 decisions
  — all are authoritative inputs for this cycle; whether the *work*
  holds up is what the audits will test, and Step 01 neither
  re-litigates nor pre-judges that
- Amendment packages — when audit evidence (not validation)
  invalidates an upstream commitment, Step 10 produces the
  Phase 5 / Phase 4 / Phase 3 / Phase 2 Amendment Package
  (Channels 2–5)

### The Two-Scope Split — Phase 6 Feedback Channel 1

*Inherited pattern from Phase 2 v1.1 through Phase 5 v1.0 Step 01,
which implemented the same channel upstream.*

Every validation gap is classified by scope. The classification
determines the routing.

| Scope | Meaning | Routing |
|-------|---------|---------|
| **Phase 6 local** | The gap is within Phase 6's universe — an audit-planning question Phase 6 must resolve, a Phase 5 output Phase 6 needs to interpret, an artifact the practitioner can supply, an instrument that cannot be executed as designed | Resolve within Phase 6 (typically at Step 02 — a scope decision, an instrument waiver-with-justification at §4, an independence-plan adjustment at §5 — or by practitioner-supplied artifact, or carried as a documented limitation in the affected audit's report and the Step 10 record) |
| **Upstream toolkit** | The gap exists because an upstream toolkit was structurally incomplete — it didn't ask the question that would have produced what Phase 6 needs, or its prompt template had no slot for it | Queue for the responsible toolkit's revision in a separate session (after Phase 6 completes); Phase 6 proceeds with workaround |

**Route upstream gaps to the toolkit that owns the structural
absence.** Phase 6 consumes Phase 5 directly, so the owning toolkit
is usually Phase 5. Occasionally the missing slot lives further
upstream — Phase 5 faithfully carried forward what Phase 4 (or
Phase 3, or Phase 2, or Phase 1) gave it, and the absence originates
there. Diagnose the origin; do not default every upstream gap to
Phase 5.

**Critical distinction:** an upstream toolkit gap is not a complaint
about the Phase 5 run's quality — and it is not an audit finding.
It is a structural observation that the upstream toolkit *as it
currently exists* didn't surface information Phase 6 needs. The fix
is a toolkit v1.x+ revision, not a re-run of the current cycle.
Upstream gaps do not block Phase 6.

### Your Behavioral Rules

- **Conduct structured validation; do not accept "looks fine to me"
  as a category result.** Each validation category has specific
  confirmation prompts. Each needs an explicit answer with evidence
  — a citation from the bundle (§-ref) or a per-module record, a
  confirmation of practitioner understanding, or a flagged gap.
- **Enforce the two blocking checks before anything else.** Category
  1 checks (a) the Implementation Bundle §9 readiness determination
  — READY or CONDITIONALLY READY only — and (b) the §7 amendment
  packages, which must be resolved. If either check fails, record
  the finding, stop the validation, and direct the practitioner to
  the required cycle. These are the two Step 01 findings that halt
  the phase rather than registering a gap.
- **Validate the inputs; do not begin auditing.** Step 01 confirms
  the audit's **inputs** exist and are current — records present,
  suites recorded green at handoff, instruments recorded executable,
  baselines reachable. It reads the recorded evidence (Bundle §3.3
  run references, Phase 5 Step 06 §5 readiness entries); it does not
  re-run suites, execute instruments, scan code, or score
  documentation. That work belongs to Steps 03–09, under the Step 02
  specification, with independence attested — an "audit" performed
  here would have no independence plan and would pre-empt the scope
  allocation. Equally: do not re-litigate upstream decisions. If
  audit work *later* shows an artifact is defective, that surfaces
  through the audits' findings and routes to Step 10's amendment
  packages (Channels 2–5) — not through Step 01 second-guessing.
- **Classify every gap by scope.** Every Validation Gap Register
  entry is tagged Phase 6 local or upstream toolkit, and every
  upstream entry names the owning toolkit (Phase 5 / Phase 4 /
  Phase 3 / Phase 2 / Phase 1). Never default; never collapse the
  scopes. The routing depends on the classification.
- **For upstream gaps, surface specifically what was structurally
  missing.** Not "Phase 5 didn't tell us X" but "the Phase 5 prompt
  template for Step N did not have a slot for X, so it never got
  captured." The owning toolkit's revision needs the structural
  diagnosis, not the symptom.
- **For Phase 6 local gaps, surface the resolution path.** Will the
  gap be resolved at Step 02 by a scope decision or an instrument
  waiver-with-justification? By the practitioner supplying the
  artifact? Carried as a [QUESTION] flag on a named audit step?
  Accepted as a documented limitation? Name the path; do not leave
  it as "to be determined."
- **Track confidence per category.** A category that validates with
  High confidence is anchored. Medium confidence is anchored but
  worth re-checking when an audit begins to depend on it. Low
  confidence is a gap — capture it in the register.
- **Re-verify subject identity and bundle currency.** *Inherited
  from Phases 1–5.* Confirm the subject version, the bundle's
  synthesis date, and whether any Phase 5 (or deeper) amendment
  landed between Phase 5 completion and this Phase 6 start. Apply
  the concurrent-release / dependency-shipped-early decision rule
  inherited from Phase 3 v1.1 (Category 1 below). One targeted
  check is sufficient.

---

## Kickoff

> Paste this line to begin. Paste the Phase 5 Implementation Bundle
> above it. The per-module records and the Step 00 Toolset
> Augmentation Document can also be pasted if useful.
```
I'm starting Phase 6 (Testing & Audit) on an existing project. Please
conduct the Phase 5 Input Validation by walking me through the
validation categories one at a time — beginning with the two blocking
checks on the Implementation Bundle §9 readiness determination and
the §7 amendment packages — then produce the structured Validation
Report with the gap register split by scope.
```

---

## Validation Category Question Bank

Walk through these categories one at a time. Each produces an
explicit confirmation, a confidence level, and any gaps.

### 1. Subject Identity & Implementation Bundle Currency

- Confirm the subject — name, current version, repository identity.
- Confirm the Implementation Bundle's synthesis date and version,
  and the upstream versions it carries (Blueprint, Phase 3 Bundle,
  Improvement Plan — Bundle header and §0).
- **BLOCKING CHECK A — Implementation Bundle §9 readiness
  determination.** What did the Phase 5 gate determine (§9.2)? It
  must read **READY** or **CONDITIONALLY READY** for Phase 6 to
  enter. Any NOT READY variant means Phase 5 itself concluded the
  changes are not fit to hand to audit: record the finding, stop
  this validation, and direct the practitioner to the remediation
  or amendment cycle. If **CONDITIONALLY READY**, inventory the
  §9.3 Conditional Remediation Register: for each conditional,
  capture what it is, its named remediation, owner, target, and —
  from its "Blocks Which Phase 6 Work" entry — derive explicitly
  **which Phase 6 audits may start once Step 02 completes and
  which must wait**. Check §9.4: if an override was applied,
  record what was overridden and the accepted risk — Phase 6
  inherits it as carried context, and an overridden
  amendment-path determination means Phase 6 is auditing changes
  built on a commitment the framework flagged as invalid: name
  that prominently.
- **BLOCKING CHECK B — Implementation Bundle §7 amendment
  packages.** Does the bundle carry a populated §7.1 (Phase 4
  Amendment Package), §7.2 (Phase 3), or §7.3 (Phase 2) that has
  not been resolved? Phase 5 Step 10 is explicit: the §6 forward
  handoffs — including the §6.1 Phase 6 Handoff Summary — are *not
  operational* while a package exists. If any is unresolved,
  **Phase 6 must not proceed**: record the finding, stop this
  validation, and direct the practitioner to the amendment cycle
  (the upstream phase amends; Phase 5 re-enters and re-gates;
  Phase 6 starts against the re-synthesized bundle). If all read
  "Not applicable," or were resolved into a re-synthesized bundle,
  record the check as passed and continue.
- Has any Phase 5 amendment or scoped re-entry landed between
  Phase 5 completion and this Phase 6 start? (Practitioner check;
  if yes, the re-synthesized bundle is the input, not the
  original.)
- Have the Architecture Blueprint Bundle, Phase 3 Design
  Specification Bundle, or Phase 2 Improvement Plan been amended
  since the Implementation Bundle was synthesized? (Bundle §0
  verified currency at synthesis time; re-verify at Phase 6 entry.)
- Has the subject shipped any release since Phase 5 completion?
  If yes: do the bundle's landed refs still describe the shipped
  state? A release carrying the audited changes plus *other* work
  means the system under audit and the system about to deploy
  have diverged — a currency finding to resolve before Step 02
  pins the system-under-audit version.
- **Did a scheduled mechanism or assumed-unreleased dependency ship
  *early* via a parallel track?** *(The concurrent-release /
  dependency-shipped-early decision rule, inherited from Phase 3
  v1.1.)* If a separate release/productization effort shipped a
  mechanism the Improvement Plan scheduled for a future release,
  or a dependency the change specifications assumed unreleased,
  apply the decision rule from the instructions file's currency
  rule: does the shipped reality *invalidate* a commitment the
  audits would verify against (→ record here; the affected audits
  carry the note; candidate Channel 2–5 routing at Step 10) or
  merely *de-risk/ground* it (→ grounding note; Step 02 pins the
  now-real version in the system-under-audit definition)? Two
  productization tracks sharing one subject at different cadences
  is a recurring condition to name, not an anomaly.

### 2. Change Surface & Implementation Confirmation

- Confirm the Bundle §2 Change Surface Completion Map and its
  verdict: does §2.4 record **"Closes both ways"** — every
  NEW/CHANGED module planned, landed, verified, reviewed, and
  scored (§2.1); every Brief/MC landed or deferred with
  practitioner acceptance (§2.2); and no landed change without a
  change-spec basis? A completion map with unrouted gaps that
  nevertheless reached a READY determination is a contradiction —
  surface it to the practitioner before proceeding.
- For each **NEW or CHANGED** module (M-NN), confirm **all five
  per-module records exist and are reachable** — each is an audit
  input, not a formality: the **Step 04 Module Implementation
  Plan** (scope and work-package structure); the **Step 05
  Implementation Report** (landed refs, deviation register, the
  commit → task → spec chain the conformance and AI-vs-AI audits
  trace); the **Step 06 Correctness Verification Report** (its
  determination and §5 instrument-readiness entries feed
  Category 3); the **Step 07 AI-vs-AI Review Report** (its
  configuration note feeds the Step 02 §5 independence plan —
  Phase 6 must not reuse that configuration); and the **Step 08
  Health, Scoring & Effort Actuals record** (the per-module
  scoring the Step 10 refresh traces back to). A missing record is
  a gap with a named resolution path; auditing a module whose
  records cannot be read starts blind.
- Confirm the **RETIRED** rows (§2.3): removals verified with their
  consumers' changes. Confirm the **UNTOUCHED** rows: the Step 09
  §4 diff confirmed zero unexplained touches. These dispositions
  are Step 02's scoping instrument — the change surface, the
  untouched remainder, and the seams derive from them; a module
  whose disposition is uncertain cannot be allocated audit depth.
- Confirm the Bundle §3.2 open-findings inventory at handoff:
  every Phase 5 finding carries a status and routing, with no open
  Blocking findings (an open Blocking finding contradicts a READY
  determination). Accepted findings noted there are audit context
  — the audits re-examine accepted risks; they do not inherit the
  acceptance.

### 3. Test Suite & Verification Instrument Confirmation

- Confirm the suites were **green at handoff**, from the recorded
  evidence — do not re-run anything here: Bundle §3.3 shows the
  full regression suite green at the final landed state (run
  reference, pass/fail counts), every change-spec §7
  regression-surface test passing, and authorized breaks citing
  their specification basis; and every Phase 5 Step 09 cohort
  report carries an **INTEGRATED** determination (Bundle §3.1). An
  ISSUES FOUND that survived into a READY bundle is a
  contradiction — surface it.
- Confirm the suites (new + regression) are reachable and runnable
  by Phase 6 at the landed refs — Step 03 re-runs and extends
  them, and every audit's regression sweep depends on them — and
  how they run under the declared access mode (AI-run preferred;
  practitioner-run patch-mediated fallback).
- Confirm **every Phase 3 Bundle §3 verification instrument** —
  enumerated test scopes, conformance properties, proxy-reader
  question sets, auditor-persona prompts — has a Phase 5 Step 06
  §5 **Verification Instrument Readiness** entry recording it as
  executable by a later phase in a fresh session: implemented or
  staged, with location and run instructions. The instruments are
  the audit's floor; Phase 6 executes them at Steps 03–09 per the
  Step 02 §4 mapping.
- For any instrument whose readiness entry is missing, ambiguous,
  or **not executable**: register a candidate gap now. These
  candidates feed the Step 02 §4 mapping decision —
  execute-as-designed, adapt-with-note, or
  **waiver-with-justification** — and Step 10 §2 accounts for
  every one. Step 01 flags executability; it does not decide
  waivers.

### 4. Scan, Conformance & Formal-Model Confirmation

- Confirm the **Phase 5 scan results** are reachable — dependency
  audit, static analysis, secrets scanning (Bundle §6.1
  security-audit row). Step 04 uses them as the departure point it
  must independently exceed, not as evidence to rubber-stamp.
- Confirm the **conformance results** against the Phase 4 formal
  contracts are reachable (Phase 5 Step 06 §1 per module; Bundle
  §6.1 conformance row). Step 06 audits conformance independently;
  the Phase 5 results tell it where implementation believed itself
  conformant.
- Confirm the **formal models, checker outputs, and staged
  practitioner-review items** for designated components are
  reachable (Phase 5 Step 06 §4; Bundle §6.1 row).
- Confirm the **formal-verification designation statement** itself:
  did Phase 5 designate components? This decides whether **Step 08
  runs at all** — it is conditional, skipped entirely when no
  models were designated; Step 02 §6 consumes the outcome. A
  designated component whose model is unreachable is a gap; an
  undesignated codebase with no models is a clean skip, not a gap.

### 5. Scorecard Baseline & Conditionals

- Confirm each of the six principles' weights — Security,
  Maintainability, Economics, Operations, Scoring & Metrics,
  Correctness Verification — set at Phase 2 Step 02 and inherited
  through Phases 3–5 unchanged. Phase 6 uses them unchanged; the
  Step 10 refresh is the definitive pre-release scoring under the
  same weights.
- Confirm the Phase 5 scorecard refresh outcomes per principle
  (Bundle §4.2). **The Phase 5 refresh is the baseline the Phase 6
  audit measures against** — each audit's §6 Gate Input Summary
  and the Step 10 §4.2 refresh compare to it — not Phase 4's or
  earlier scorecards directly.
- Confirm the §4.3 target distribution result at Phase 5 exit
  (all-PASS / ≤2 CONDITIONALs / any FAIL / uniform-status
  concern). An exit that passed with caveats tells Phase 6 where
  its gates will be under pressure and where audit depth should
  concentrate.
- For each principle the Phase 5 refresh left CONDITIONAL, confirm
  what made it conditional, the remediation Phase 5 named, and
  **whether the conditional is Phase 6's to audit** — cross-check
  the §9.3 register from Category 1. A remediation due *before*
  Phase 6 must show delivery evidence; a closure the audit itself
  is expected to confirm must be traceable to the audit step that
  will produce that evidence — name it now.
- Confirm the explicit deprioritizations the cycle made. Phase 6
  audits each deferral *per its deferral* — neither silently
  expanded nor silently skipped — and does not re-elevate it
  mid-audit; re-elevation candidates route to next-cycle Phase 2.

### 6. Benchmarks & Measured Baselines Access

- Are the **Phase 1 measured operational baselines** reachable
  (Current-State Information Report)? Step 05 validates
  empirically against *measured* reality, not projections.
- Are the **change specifications' §6 performance targets**
  reachable for every NEW/CHANGED module? Set against the measured
  baselines, they are the per-module pass/fail anchors.
- Are the **pre-cycle actuals** reachable — the system's behavior
  before this cycle's changes, wherever recorded (Phase 1 report,
  production monitoring, prior benchmark runs)? The track's rule
  binds Step 05: **an unexplained regression against the pre-cycle
  baseline is a finding even when the stated target is met** — a
  rule that cannot run without the pre-cycle numbers. A missing
  anchor is a gap with a named resolution path, surfaced now
  rather than discovered mid-audit.
- Are the **Phase 2 benchmarks** reachable where the Improvement
  Plan named them (commitments attached to MC-NN mechanisms)?
  Severe misses are phase-traced, not patched at audit time.
- Are the **Phase 5 handoff measurements** reachable — the Step 09
  §5 numbers at the integrated state and the benchmark results the
  Bundle §6.1 performance row cites? These are the
  implementation-side numbers the independent validation will
  confirm or contradict.

### 7. Forward-Handoff Confirmation (Implementation Bundle §6.1)

- Enumerate the Bundle §6.1 Phase 6 Handoff Summary rows: for each
  Phase 6 concern, what Phase 5 expected Phase 6 to **consume**
  and where it lives (bundle § / repo ref), and confirm every
  "Inputs Present?" flag reads **Complete**. An Incomplete flag
  that survived the Phase 5 gate is a candidate gap here.
- For each row, confirm which Phase 6 audit step (03–09, or 10)
  will perform the expected activity and which validation
  category above confirmed the input it consumes.
- Confirm the **top risks carried into Phase 6** (§6.1 risks
  table): each risk is assigned attention at a named audit step.
  An unassigned risk is a local gap routed to Step 02, which
  allocates it scope and depth.
- **Anything Phase 5 expected Phase 6 to audit that is not covered
  by the suite, instrument, scan, baseline, or reference
  confirmations is a candidate gap** — classify it: Phase 6 local
  (coverable by an explicit Step 02 scope decision) or upstream
  toolkit (the expectation exists but the input that would ground
  it was never captured).
- Confirm the expected outputs align with what this toolkit
  produces (seven audit reports, the Deployment Readiness Report,
  the carried-risk register, the frozen documentation baseline).
  A §6.1 expectation naming an output this toolkit has no step for
  is an upstream toolkit gap — of either the Phase 5 toolkit
  (wrong expectation) or this Phase 6 toolkit (missing slot);
  diagnose which.

### 8. Framework & Contract Reference Access

The audits verify the changed system *against the specifications,
not the implementation* — this category confirms the reference
standards are reachable.

- Are the **Phase 4 Step 11 formal contract sets** reachable, in
  the machine-consumable form the conformance audit runs against
  (e.g., a language-level `IDeploymentStrategy` interface contract
  — the MC-04 conformance target)? Exempted contracts still bind:
  the change specifications' §2 interfaces are the conformance
  target where no machine-readable contract exists.
- Are the **module change specifications** (Phase 4 Step 09)
  reachable for every NEW/CHANGED module — in particular their §2
  interfaces (conformance targets), §6 performance targets
  (Category 6), and §7 test strategy / regression surface (the
  regression assurance's definition of "what must still pass")?
- Is the **Impact Map** reachable — M-NN dispositions and SIC-NN
  contracts? It is Step 02's scoping instrument: the three-way
  allocation (change surface / untouched remainder / seams)
  derives directly from it.
- Are the **cross-cutting framework registers** reachable —
  **SP-NN** patterns, **SEC-NN** controls + **TB-NN** boundaries
  (Step 04 verifies the controls at the boundaries), **DA-NN**
  data constraints, **DOC-NN** documentation types (Step 09's
  coverage standard), **GOV-NN** governance (release and approval
  constraints the readiness determination must honor)?
- Confirm the **audit execution capability** from the Step 00
  document: the declared code-access mode and tooling inventory
  (test runners, scanners, load/benchmark tools,
  documentation-only session capability), with per-audit coverage
  — AI-run preferred, patch-mediated (practitioner runs, pastes
  results) as the fallback. An audit that can execute nothing is
  an audit in name only; a tooling shortfall is a gap Step 02 must
  scale the audit plan around, with the limitation recorded
  prominently.
- Confirm the **independence configurations** are inventoried
  (Step 00): the separate AI models/configurations each audit will
  use, distinct from the Phase 5 generating and reviewing sessions
  — Step 07's especially. Step 02 §5 plans per-audit independence
  from this inventory; where full independence is unattainable,
  the limitation is recorded, never pretended away. A missing
  entry is a gap with a named resolution path (usually a Step 00
  §7 amendment).

### 9. Validation Gap Pre-Check (Closing Question)

Before producing the report, ask the practitioner:

> *Given the validation we've walked through, is there anything you
> expected me to check that I didn't? Specifically: are there
> aspects of the Implementation Bundle — or the per-module records,
> suites, instruments, and baselines behind it — that you find
> ambiguous, incomplete, or potentially miscommunicated to a
> Phase 6 session that we haven't surfaced?*

The pre-check exists because the validation question bank cannot
anticipate every possible gap. Practitioner-driven gap surfacing
catches what structural validation misses.

---

## Output Format

When the validation is complete, produce the Phase 5 Input Validation
Report using this structure. All sections are required. Mark any
section as `[OPEN — see Gap Register]` rather than fabricating
content or silently omitting it.

---
```markdown
# Phase 5 Input Validation Report — Phase 6 (Testing & Audit)

**Project:** [subject name and version]
**Validation Date:** [date]
**Phase 5 Completion Date:** [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]
**Implementation Bundle Version:** [version, with amendment-date if applicable]
**Architecture Blueprint Bundle Version:** [version — as carried by the bundle §0]
**Phase 3 Design Specification Bundle Version:** [version — as carried by the bundle §0]
**Phase 2 Improvement Plan Version:** [version — as carried by the bundle §0]
**Status:** Draft — Pending Practitioner Review

> ⚠️ This report validates that Phase 6 has — and correctly
> understands — the Phase 5 inputs the audit will consume. It is
> **not** the beginning of the audit itself (no suites re-run, no
> instruments executed, no findings raised), and it is not a
> re-litigation of Phase 5, Phase 4, Phase 3, or Phase 2 decisions
> — all are authoritative inputs for this cycle. Gaps surface
> either as Phase 6 local (resolve within Phase 6) or as upstream
> toolkit (queue for the responsible toolkit's revision in a
> separate session).

---

## §1 — Subject Identity & Implementation Bundle Currency

| Field | Value | Confidence |
|-------|-------|-----------|
| Subject name | | [H/M/L] |
| Subject current version | | [H/M/L] |
| Implementation Bundle synthesis date / version | | [H/M/L] |
| **Bundle §9 readiness determination (BLOCKING)** | [READY — clear / CONDITIONALLY READY — conditional inventory below / **HALT — NOT READY (any variant); Phase 6 must not proceed**] | [H/M/L] |
| **Bundle §7 amendment packages (BLOCKING)** | [Clear — §7.1/§7.2/§7.3 all "Not applicable" or resolved into a re-synthesized bundle / **HALT — unresolved package; forward handoffs not operational**] | [H/M/L] |
| §9.4 override applied at the Phase 5 gate? | [No / Yes — what was overridden, risk inherited; if an amendment-path determination was overridden, named prominently as carried context for every audit] | [H/M/L] |
| Phase 5 amendments / scoped re-entries since completion? | [Yes/No, with date if Yes — re-synthesized bundle is the input] | [H/M/L] |
| Blueprint / Phase 3 Bundle / Improvement Plan amendments since synthesis? | [Yes/No, with date if Yes] | [H/M/L] |
| Subject release since bundle synthesis? | [No / Yes — landed refs vs shipped state reconciled; divergence is a currency finding] | [H/M/L] |
| Scheduled mechanism / dependency shipped early via parallel track? | [No / Yes — grounding note; Step 02 pins the now-real version / Yes — candidate invalidation, see Gap Register] | [H/M/L] |

**Conditional inventory (populated when CONDITIONALLY READY):**

| Conditional | Named Remediation | Owner | Target | Blocks Which Phase 6 Work (§9.3) | Audits That May Start |
|-------------|-------------------|-------|--------|-----------------------------------|------------------------|
| | | | | [audit steps blocked] | [audit steps clear once Step 02 completes] |

## §2 — Change Surface & Implementation Confirmation

**Completion-map verdict (Bundle §2.4):** [Closes both ways /
Contradiction — gaps listed and surfaced to practitioner]

| Module (M-NN) | Disposition | Step 04 Plan | Step 05 Report | Step 06 Verification | Step 07 Review | Step 08 Health | Confidence |
|---------------|-------------|--------------|----------------|----------------------|----------------|----------------|-----------|
| | [NEW / CHANGED] | [Reachable / Gap] | [Reachable / Gap] | [Reachable / Gap] | [Reachable / Gap] | [Reachable / Gap] | [H/M/L] |

**RETIRED / UNTOUCHED confirmation (the remainder and the seams):**

| Module (M-NN) | Disposition | Confirmation |
|---------------|-------------|--------------|
| | [RETIRED] | [Removal + absorbing consumer changes verified per Bundle §2.3] |
| | [UNTOUCHED] | [Step 09 §4 diff confirmed zero unexplained touches] |

**Open findings at handoff (Bundle §3.2):** [No open Blocking
findings — accepted findings listed as audit context / Contradiction
— open Blocking finding under a READY determination, surfaced]

## §3 — Test Suite & Verification Instrument Confirmation

| Check | Recorded Evidence (not re-run) | Result | Confidence |
|-------|--------------------------------|--------|-----------|
| Full regression suite green at handoff (Bundle §3.3) | [run ref, pass/fail counts] | [Confirmed / Gap] | [H/M/L] |
| Every change-spec §7 regression-surface test passing | | [Confirmed / Gap] | [H/M/L] |
| Authorized breaks cite their specification basis | | [Confirmed / Gap] | [H/M/L] |
| Every Step 09 cohort determination INTEGRATED (Bundle §3.1) | [cohort list] | [Confirmed / Contradiction — surfaced] | [H/M/L] |
| Suites reachable and runnable by Phase 6 at the landed refs | [access mode: AI-run / patch-mediated] | [Confirmed / Gap] | [H/M/L] |

**Instrument executability (Phase 3 Bundle §3 × Phase 5 Step 06 §5):**

| Instrument (ID / name) | Type | Step 06 §5 Readiness Entry | Executable by Phase 6? | Candidate Step 02 §4 Waiver? |
|------------------------|------|----------------------------|------------------------|------------------------------|
| | [test scope / conformance property / proxy-reader question set / auditor-persona prompt] | [executable — location + run instructions / missing / ambiguous] | [Yes / No — gap registered] | [No / Yes — flagged for the Step 02 mapping decision] |

## §4 — Scan, Conformance & Formal-Model Confirmation

| Artifact Class | Reachable? | Location | Consuming Audit | Confidence |
|----------------|-----------|----------|-----------------|-----------|
| Phase 5 scan results (dependency / static / secrets) | [Yes/No] | | Step 04 (departure point, independently exceeded) | [H/M/L] |
| Conformance results vs Phase 4 contracts | [Yes/No] | | Step 06 | [H/M/L] |
| Formal models + checked properties + staged review items | [Yes / No / N/A — none designated] | | Step 08 | [H/M/L] |

**Formal-verification designation statement:** [Components designated
— listed; Step 08 RUNS / No components designated; Step 08 SKIPPED —
recorded for Step 02 §6. A designated component with an unreachable
model is a gap; an undesignated codebase is a clean skip.]

## §5 — Scorecard Baseline & Conditionals

| Principle | Weight | Phase 5 Refresh Status (Bundle §4.2) | Confidence |
|-----------|-------:|---------------------------------------|-----------|
| Security | | [PASS/CONDITIONAL/FAIL] | [H/M/L] |
| Maintainability | | | |
| Economics | | | |
| Operations | | | |
| Scoring & Metrics | | | |
| Correctness Verification | | | |

Weights confirmed inherited from Phase 2 Step 02 unchanged: [Yes/No]
Phase 5 refresh confirmed as the Phase 6 baseline: [Yes/No]
Bundle §4.3 target distribution result at Phase 5 exit: [summary —
pressure points noted for Step 02 depth allocation]

**CONDITIONALs and Phase 6 ownership:**

| Principle | What Made It Conditional | Named Remediation | Phase 6's to Audit? | Auditing Step / Evidence Expected |
|-----------|-------------------------|-------------------|---------------------|-----------------------------------|
| | | | [Yes — audit confirms closure / No — due before Phase 6, delivery evidence checked / next-cycle] | [Step NN / evidence ref / N/A] |

**Explicit deprioritizations to audit per their deferral:**
[List each — audited as neither silently expanded nor silently
skipped; re-elevation candidates route to next-cycle Phase 2.]

## §6 — Benchmarks & Measured Baselines Access

| Anchor | Reachable? | Location | Consuming Audit | Confidence |
|--------|-----------|----------|-----------------|-----------|
| Phase 1 measured operational baselines | [Yes/No/Partial] | | Step 05 | [H/M/L] |
| Change-spec §6 targets (every NEW/CHANGED module) | [Yes/No/Partial] | | Step 05 | [H/M/L] |
| Pre-cycle actuals (pre-change system behavior) | [Yes/No/Partial] | | Step 05 — the unexplained-regression rule cannot run without them | [H/M/L] |
| Phase 2 benchmarks (where the Improvement Plan named them) | [Yes/No/N/A] | | Step 05; severe misses phase-traced at Step 10 | [H/M/L] |
| Phase 5 handoff measurements (Step 09 §5; Bundle §6.1 bench refs) | [Yes/No/Partial] | | Step 05 (confirm or contradict) | [H/M/L] |

## §7 — Forward-Handoff Confirmation (Implementation Bundle §6.1)

| Bundle §6.1 Row | Phase 6 Expected to Consume | Location | Inputs Present? | Performing Audit (Step 03–10) | Covered By Validation Category | Candidate Gap? |
|------------------|----------------------------|----------|-----------------|-------------------------------|-------------------------------|----------------|
| | | | [Complete/Incomplete] | | [§2–§6, §8 of this report] | [No / Yes — see Gap Register] |

**Top risks carried into Phase 6 (§6.1 risks table):**

| Risk | Source (artifact + §) | Assigned Phase 6 Attention (audit step) |
|------|-----------------------|------------------------------------------|
| | | [named, or local gap routed to Step 02] |

**Expectations not covered by the suite / instrument / scan /
baseline / reference confirmations:** [list with scope
classification, or "None — all §6.1 expectations are covered"]

## §8 — Framework & Contract Reference Access

| Reference Standard | Reachable? | Machine-Consumable (where required)? | Consuming Audit | Confidence |
|--------------------|-----------|--------------------------------------|-----------------|-----------|
| Phase 4 Step 11 formal contract sets | [Yes/No] | [Yes / No — change-spec §2 interfaces are the target for exempted contracts] | Step 06 | [H/M/L] |
| Module change specifications (Phase 4 Step 09 — §2/§6/§7) | [Yes/No] | | Steps 03, 05, 06 | [H/M/L] |
| Impact Map (M-NN dispositions, SIC-NN) | [Yes/No] | | Step 02 scope allocation | [H/M/L] |
| SP-NN shared patterns | [Yes/No] | | Steps 06, 07 | [H/M/L] |
| SEC-NN controls + TB-NN boundaries | [Yes/No] | | Step 04 | [H/M/L] |
| DA-NN data constraints | [Yes/No] | | Steps 04, 06 | [H/M/L] |
| DOC-NN documentation types | [Yes/No] | | Step 09 | [H/M/L] |
| GOV-NN governance (release/approval constraints) | [Yes/No] | | Step 10 | [H/M/L] |

**Audit execution capability (from Step 00):**
[Code-access mode + tooling inventory per audit: test runners /
scanners / load tools / documentation-only session. Shortfalls
listed — Step 02 scales the plan around them with the limitation
recorded prominently.]
**Independence configurations inventoried (Step 00):** [Yes — per
audit, Step 07 separate configuration confirmed / Gaps listed with
resolution path (usually Step 00 §7 amendment); unattainable
independence recorded as limitation, never pretended]

## §9 — Validation Gap Register (Split by Scope)

### §9.1 — Phase 6 Local Gaps

Gaps that Phase 6 must resolve within its own steps, or acknowledge
as documented limitation in the affected audit report and Step 10.

| Gap ID | Description | Affected Category / Audit Step / Instrument | Resolution Path | Priority |
|--------|-------------|---------------------------------------------|----------------|----------|
| VG-L-01 | | | [Step 02 scope decision / Step 02 §4 waiver-with-justification / practitioner supplies artifact / [QUESTION] flag on Step NN / accepted limitation] | [H/M/L] |

### §9.2 — Upstream Toolkit Gaps

Gaps that exist because an upstream toolkit was structurally
incomplete. Queue for the responsible toolkit's revision in a
separate session. Phase 6 proceeds with workaround.

| Gap ID | Description | Owning Toolkit | What That Toolkit Was Missing | Phase 6 Workaround | Toolkit Revision Recommendation |
|--------|-------------|----------------|-------------------------------|--------------------|--------------------------------|
| VG-U-01 | | [Phase 5 / Phase 4 / Phase 3 / Phase 2 / Phase 1] | | | |

> **Each upstream gap requires the owning-toolkit diagnosis (which
> phase's toolkit lacked the slot — usually Phase 5, occasionally
> deeper), the structural absence itself, and a concrete revision
> recommendation. Vague upstream gaps don't actionably produce
> toolkit improvements.**

## §10 — Validation Confidence Summary

| Validation Category | Confidence | Notes |
|--------------------|------------|-------|
| Subject identity & bundle currency | [H/M/L] | |
| Change surface & implementation confirmation | [H/M/L] | |
| Test suites & verification instruments | [H/M/L] | |
| Scans, conformance & formal models | [H/M/L] | |
| Scorecard baseline & conditionals | [H/M/L] | |
| Benchmarks & measured baselines access | [H/M/L] | |
| Forward-handoff confirmation | [H/M/L] | |
| Framework & contract reference access | [H/M/L] | |

**Overall validation status:** [Anchored / Anchored with caveats /
Significant gaps / HALTED — NOT READY determination or unresolved
amendment package]

[1–3 sentences describing the overall validation outcome and what
the next step (Step 02 Audit Specification) will need to address
first — typically the instrument-waiver candidates, unassigned
carried risks, and any tooling or independence shortfalls.]

---

## Version

v1.0 (initial validation report; re-run Step 01 if a re-synthesized
Implementation Bundle, an amended upstream bundle, or a mid-audit
subject release replaces the validated inputs)
```

---

## Evaluation Checklist

Before this artifact is accepted as complete, verify all items:

- [ ] All 10 sections are populated; sections with no content are
      marked `[OPEN]` with reference to the relevant gap, not
      silently omitted
- [ ] Both blocking checks were performed first and recorded in §1:
      the Implementation Bundle §9 determination is READY or
      CONDITIONALLY READY, and the §7 amendment packages are clear
      or resolved; if either failed, the run halted and no
      downstream validation or Phase 6 work proceeded
- [ ] If CONDITIONALLY READY, the conditional inventory is complete
      — remediation, owner, target, and blocked work per
      conditional, stating which Phase 6 audits may start and which
      must wait; any §9.4 override is recorded with its inherited
      risk
- [ ] Subject version is re-verified, not carried over from bundle
      metadata; releases, re-entries, and early-shipped mechanisms
      since Phase 5 completion are checked with the
      grounding-vs-invalidation decision rule applied
- [ ] The §2.4 completion-map verdict is confirmed; every
      NEW/CHANGED module's five records (Step 04 plan, Step 05
      report, Step 06 verification, Step 07 review, Step 08 health)
      are confirmed reachable or the gap carries a named resolution
      path; RETIRED/UNTOUCHED dispositions are confirmed; the §3.2
      inventory shows no open Blocking finding contradicting READY
- [ ] Suite status at handoff is confirmed from recorded evidence
      (Bundle §3.3 references and counts; every Step 09 cohort
      INTEGRATED), and the suites are confirmed runnable by Phase 6
      under the declared access mode — nothing was re-run at
      Step 01
- [ ] Every Phase 3 Bundle §3 instrument's executability is
      confirmed against its Phase 5 Step 06 §5 readiness entry, or
      flagged as a candidate gap feeding the Step 02 §4
      waiver-with-justification decision
- [ ] Scan results, conformance results, and formal models are
      confirmed reachable, and the formal-verification designation
      statement is recorded — deciding explicitly whether Step 08
      runs or is skipped
- [ ] Principle weights are confirmed inherited from Phase 2
      Step 02 unchanged; the Phase 5 refresh (Bundle §4) is
      confirmed as the Phase 6 baseline; every CONDITIONAL has a
      Phase 6 ownership determination with its auditing step or
      delivery evidence; deprioritizations are audited per their
      deferral
- [ ] All five measured-baseline anchors are confirmed reachable —
      Phase 1 baselines, change-spec §6 targets, pre-cycle actuals,
      named Phase 2 benchmarks, Phase 5 handoff measurements — or
      the gap carries a named resolution path
- [ ] Every Bundle §6.1 forward-handoff row is confirmed covered by
      a performing audit step, or flagged as a candidate gap with
      scope classification; every carried risk is assigned
      attention at a named audit step
- [ ] The audit reference standards (Phase 4 Step 11 contracts,
      change specifications, Impact Map, SP/SEC/TB/DA/DOC/GOV
      registers) are confirmed reachable — contracts
      machine-consumable where the conformance audit requires it
- [ ] Audit execution capability and independence configurations
      are confirmed from Step 00 — per-audit tooling coverage, the
      Step 07 separate configuration, and any shortfall recorded as
      a gap Step 02 must scale around
- [ ] The Validation Gap Register in §9 is split into §9.1 (Phase 6
      local, VG-L-NN) and §9.2 (upstream toolkit, VG-U-NN)
- [ ] Every upstream gap names the owning toolkit (Phase 5 /
      Phase 4 / Phase 3 / Phase 2 / Phase 1), the specific
      structural absence (not just the symptom), and a concrete
      revision recommendation
- [ ] Every Phase 6 local gap names the resolution path (Step 02
      scope decision / Step 02 §4 waiver / practitioner-supplied
      artifact / [QUESTION] flag on a named audit step / accepted
      limitation)
- [ ] Validation confidence per category is captured with H/M/L
      tags and rationale, and the pre-check question (Category 9)
      was asked with its answer reflected in the gap register
- [ ] No audit work has been performed — no suites re-run, no
      instruments executed, no scans launched, no findings raised,
      no scope or thresholds set, and no re-litigation of upstream
      decisions — Step 01 is validation only
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)

---

*Part of the Phase 6 (Existing Projects) Testing & Audit Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `testing-audit.existing-project.instructions.md`*
*Previous step: `step-00-building-block-discovery.prompt.md`*
*Next step: `step-02-audit-specification.prompt.md`*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Phase 6 Phase 5 Input Validation prompt, the Phase 6 sibling of the track's Step 01 pattern. Two hard blocking checks inherited from the Phase 5 sibling and re-keyed to the Implementation Bundle: the §9 readiness determination must read READY or CONDITIONALLY READY (with a §9.3-derived conditional inventory stating which audits may start and which must wait, and §9.4 overrides named as inherited risk), and the §7 amendment packages must be resolved before Phase 6 entry. Nine validation categories (eight substantive plus the closing pre-check) keyed to the Implementation Bundle's § structure, with per-module presence checks on the five Step 04–08 records, suite-green-at-handoff confirmation from recorded evidence only, and per-instrument executability checks against Phase 5 Step 06 §5 whose failures feed the Step 02 §4 waiver decision. The phase-distinctive rule — validate the inputs, do not begin auditing — separates Step 01 from the independence-attested audit work of Steps 03–09. Category 6 secures the five measured-baseline anchors the unexplained-regression rule depends on; Category 8 adds the audit-execution and independence-configuration checks from Step 00. The two-scope Validation Gap Register (VG-L-NN / VG-U-NN) is inherited from Phases 2–5, with upstream routing to the owning toolkit (usually Phase 5, occasionally deeper). The concurrent-release / dependency-shipped-early decision rule is inherited from Phase 3 v1.1 at initial authoring. Closes Phase 6 Feedback Channel 1. |
