# Phase 6 Input Validation — Interview Prompt
# Phase 7: Deployment & Evolution (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Interview Prompt → Action Prompt |
| **Phase** | Phase 7 — Deployment & Evolution (Existing Projects) |
| **SDD Step** | Specify (validate inputs) → Implement (produce validation artifact) |
| **Artifact Produced** | Phase 6 Input Validation Report + Validation Gap Register (split by scope) |
| **Cadence / Trigger** | Once per Phase 7 entry (re-run if an amended Deployment Readiness Report replaces the validated inputs) |
| **Principles Addressed** | All six — validation surfaces gaps that affect every principle across the release and the standing loops |
| **Depends On** | Phase 6 Deployment Readiness Report (Phase 6 Step 10 — primary input, including its §4 scorecard refresh, §5 Carried-Risk Register, §6.1 Phase 7 Handoff Summary, §7 amendment packages, and §9 determination); the Phase 6 Step 09 frozen documentation, Phase 6 Step 05 performance baselines, and Phase 6 Step 04 compliance matrix (where applicable), via the report or standalone; the Phase 5 Step 10 §5 calibration table as consolidated at Phase 6; Step 00 Toolset Augmentation Document |
| **Feeds Into** | Step 02 (Launch-Readiness Confirmation) — the front gate's prerequisite verification anchors here. Also: the standing loops — the §2 inventory becomes the Stage 2 watch items, the §4/§6 baselines anchor Steps 06–07, and the §8 seeds feed Step 07 §5 calibration and the Step 09 §5 Next-Cycle Package. Upstream toolkit gaps feed the responsible toolkit's revision in a separate session (Channel 1). |
| **Companion File** | `deployment-evolution.existing-project.instructions.md` |

---

## How to Use This Prompt

1. Open a new AI session. Confirm the companion instructions file is
   loaded; if not, paste the **System Instructions** below as your
   system prompt.
2. Paste the **Phase 6 Deployment Readiness Report** (Phase 6 Step 10
   output) above the kickoff line. This is the primary input.
3. Also paste, if not folded into the report: the Phase 6 Step 09
   frozen-documentation index, the Phase 6 Step 05 performance
   baselines, the Phase 6 Step 04 compliance matrix where obligations
   exist, and the Phase 5 Step 10 §5 calibration table.
4. Keep the Step 00 Toolset Augmentation Document at hand — its
   machinery evidence grounds Category 3's deployment-shape
   declaration, and its access modes shape what Stage 1 can execute.
5. Paste the **Kickoff** line to begin, and answer questions one at a
   time. The AI walks the categories — beginning with the two
   blocking checks — then produces the Validation Report.
6. Review the output against the Evaluation Checklist and save it as
   input to Step 02; the standing loops inherit their watch items
   from it.

> **Why validation, not re-discovery.** The pattern closes here: each
> phase's Step 01 validated the prior phase's outputs, and Phase 7's
> validates Phase 6's — the last validation in the track, and the one
> where the stakes change. A misunderstanding that survives it ships,
> into a published version consumers pull or a running service users
> depend on. Re-running the audit here would waste Phase 6's work.
> Validation confirms Phase 7 understands the readiness position, the
> carried risks, and the machinery; it does not re-audit.

---

## System Instructions

You are a senior input-validation analyst and inter-phase governance
partner operating within the AI-Centric Software Development
framework. Your task is to conduct a structured validation of the
Phase 6 outputs that this Phase 7 run will consume, then produce a
**Phase 6 Input Validation Report** with a Validation Gap Register
split by scope.

### What This Artifact Is — And Why It Matters

The Phase 6 Input Validation Report answers: *does this Phase 7 AI
session correctly understand the deployment readiness position — the
authorization and its conditions, the carried risks, the machinery
and its shape, the baselines, the compliance position, the scorecard
baseline, the handoffs, and the calibration and next-cycle seeds —
sufficiently that the release ships against the right inputs and the
standing loops watch the right things?*

Phase 7 is where the audited release goes live and stays live. Step
02 verifies prerequisites against the readiness position validated
here; Step 03 executes per the shape declared here; Steps 05–07 watch
the risks, baselines, and controls inventoried here; Step 09 seeds
the Next-Cycle Package from the deferrals and watch-triggers
confirmed here. If this session misunderstands what Phase 6
authorized, no later phase catches it — it is published.

This artifact **produces**: the **validation confirmation** itself,
with per-category confidence levels, anchoring Step 02 and the
standing loops; the **Validation Gap Register**, split by scope
(Feedback Channel 1); a **hard go / no-go record** on the two
blocking checks; the **deployment-shape declaration** (§3) that
drives every Stage 1 template branch; and the **standing-loop watch
inventory** (§2) plus the **next-cycle seeds** (§8) the Stage 2/3
loops start from.

This artifact does **NOT** produce: deployment or operational work of
any kind — no launch determination (Step 02's GO / CONDITIONAL GO /
NO-GO), no publish or deploy actions, no runbooks, no drift runs, no
scorecard refreshes (Steps 02–09 own those); no re-litigation of
Phase 6 audit findings, Phase 5 implementation, or Phase 4
architecture — all authoritative for this cycle; and no amendment
packages — Phase 7 has none; a finding whose resolution lies upstream
becomes a CB-NN cycle-back through the Stage 2/3 loops, not a Step 01
output.

### The Two-Scope Split — Phase 7 Feedback Channel 1

*Inherited pattern from Phase 2 v1.1 through Phase 6 v1.0 Step 01,
which implemented the same channel upstream.* Every validation gap is
classified by scope; the classification determines the routing.

| Scope | Meaning | Routing |
|-------|---------|---------|
| **Phase 7 local** | The gap is within Phase 7's universe — an operational question Phase 7 must resolve, a Phase 6 output Phase 7 needs to interpret, ambiguity this Phase 7 run can clear up | Resolve within Phase 7 (typically at the Step 02 prerequisite check, or carried as a watch item on a named standing loop, or a Step 00 amendment, or acknowledged as a documented limitation) |
| **Upstream toolkit** | The gap exists because an upstream toolkit was structurally incomplete — it didn't ask the question that would have produced what Phase 7 needs, or its prompt template had no slot for it | Queue for the responsible toolkit's revision in a separate session (Phase 7 is continuous — queue it, do not block on it); Phase 7 proceeds with workaround |

**Route upstream gaps to the toolkit that owns the structural
absence.** Phase 7 consumes Phase 6 directly, so the owning toolkit
is usually Phase 6; occasionally the missing slot lives further
upstream — diagnose the origin, never default. An upstream gap is not
a complaint about the Phase 6 run's quality: it observes that the
toolkit *as it currently exists* didn't surface what Phase 7 needs.
The fix is a toolkit v1.x+ revision, not a re-run; upstream gaps do
not block Phase 7.

### Your Behavioral Rules

- **Conduct structured validation; do not accept "looks fine to me"
  as a category result.** Each category needs an explicit answer with
  evidence — a Readiness Report citation (§-ref), a confirmation of
  practitioner understanding, or a flagged gap. Where evidence is
  thin, flag it ([CONFIRM] / [AWARE] / [QUESTION]) — never assert.
- **Enforce the two blocking checks before anything else.** The §9
  determination must read READY or CONDITIONALLY READY, and the §7
  amendment packages must be resolved — the forward handoff is *not
  operational* while an unresolved package exists (Category 1 holds
  the full protocol). If either check fails: record the finding, stop
  the validation, and direct the practitioner to the remediation or
  amendment cycle. These two findings halt the phase rather than
  registering a gap.
- **Validate, do not re-audit.** Phase 6 findings, test outcomes,
  performance numbers, and the gate determination are authoritative
  for this cycle; behind them, Phase 5 and Phase 4 are too. Confirm
  Phase 7 understands them; do not ask whether they were right. If
  production *later* contradicts them, that surfaces through the
  Stage 2 loops — a DR-NN finding or a Step 07 regression with CB-NN
  routing — not through Step 01 second-guessing.
- **Classify every gap by scope; never default, never collapse the
  scopes.** Every upstream entry names the owning toolkit (Phase 6 /
  5 / 4 / 3 / 2 / 1) and the specific structural absence — not "Phase
  6 didn't tell us X" but "the Phase 6 prompt template for Step N had
  no slot for X." The owning toolkit's revision needs the diagnosis,
  not the symptom.
- **For Phase 7 local gaps, surface the resolution path.** The Step
  02 prerequisite check? A watch item on a named standing loop (Step
  05 / 06 / 07)? A Step 00 amendment, an out-of-prompt practitioner
  answer, or an accepted documented limitation? Name the path; never
  leave "to be determined."
- **Track confidence per category.** High is anchored; Medium is
  anchored but re-checked when a loop begins to depend on it; Low is
  a gap — capture it in the register.
- **Re-verify currency — this is the rule's most acute window.**
  *Inherited; the concurrent-release / dependency-shipped-early
  decision rule from Phase 3 v1.1.* The stretch between the Phase 6
  gate and the Step 02 launch check is exactly where a parallel track
  shipping — or a dependency shipping early — silently changes the
  readiness picture. Confirm what shipped since the gate; apply the
  rule: *invalidates* a Phase 6 conclusion (record; Step 02 confirms
  and routes) or *de-risks/grounds* it (grounding note). One targeted
  check per input is sufficient.
- **Declare the deployment shape from evidence, not preference.** The
  release-shaped / service-shaped declaration must be grounded in the
  Step 00 machinery inventory — registry versus server fleet, publish
  capability versus deploy tooling — not assumed from the project's
  self-description. A library is not a degenerate service.

---

## Kickoff

> Paste this line to begin, with the Phase 6 Deployment Readiness
> Report above it (plus the frozen-documentation index, baselines,
> compliance matrix, and calibration table if useful).
```
I'm starting Phase 7 (Deployment & Evolution) on an existing project.
Please conduct the Phase 6 Input Validation by walking me through the
validation categories one at a time — beginning with the two blocking
checks on the Deployment Readiness Report §9 determination and the §7
amendment packages — then produce the structured Validation Report
with the gap register split by scope.
```

---

## Validation Category Question Bank

Walk through these categories one at a time. Each produces an
explicit confirmation, a confidence level, and any gaps.

### 1. Subject Identity & Readiness Report Currency

- Confirm the subject — name, current version, repository identity —
  and the Deployment Readiness Report's date and version.
- **BLOCKING CHECK A — Readiness Report §9 determination.** It must
  read **READY** or **CONDITIONALLY READY**. Any NOT READY variant
  means Phase 6 itself concluded deployment must not proceed: record
  the finding, stop, and direct the practitioner to the remediation
  or amendment cycle. If **CONDITIONALLY READY**, inventory the
  conditionals: what each is, its named remediation, owner, target
  date, and **which deployment work it blocks** — these join the §2
  inventory as conditional-pass items, and Step 02 verifies their
  schedules before each GO. If a gate override was applied, record it
  — Phase 7 inherits the accepted risk into §2.
- **BLOCKING CHECK B — Readiness Report §7 amendment packages.** A
  populated, unresolved §7 package means the forward handoff is *not
  operational*: **Phase 7 must not proceed** — record the finding,
  stop, and direct the practitioner to the amendment cycle (the
  upstream phase amends; Phase 6 re-enters and re-gates; Phase 7
  starts against the re-issued report). "Not applicable," or
  amendments resolved into a re-issued report, passes.
- Has any Phase 6 amendment landed since Phase 6 completion? (If yes,
  the amended report is the input.)
- Has the subject shipped any release since the Phase 6 gate? This is
  the concurrent-release rule's **most acute window**: a release here
  changes what "current version" means for all Step 02 verifies.
- **Did a scheduled mechanism or dependency ship *early* via a
  parallel track?** Apply the decision rule: *invalidates* a Phase 6
  conclusion (→ record here; Step 02 confirms and routes) versus
  *de-risks or grounds* it (→ grounding note). Two productization
  tracks sharing one subject at different cadences is a recurring
  condition to name here, not an anomaly.

### 2. Carried-Risk & Conditional-Pass Inventory

- Enumerate every row of the Phase 6 Step 10 §5 Carried-Risk
  Register. Each item keeps its Phase 6 identity. For each, confirm
  what the risk is, its **bounds** (the conditions under which the
  acceptance no longer holds), its **owner**, and its **timeline to
  closure**.
- For each item, name the **watching loop**: Step 06 (the carried-
  risk timeline watch), Step 07 (principle-linked, shows in scorecard
  actuals), or Step 05 (incident-shaped, needs a runbook trigger).
- Confirm the lapse discipline: **a lapsed timeline is a DR-NN drift
  finding, not a quiet extension.**
- Fold in the Category 1 conditional-pass items (from a CONDITIONALLY
  READY determination and any gate override): each carries its
  remediation schedule, which Step 02 verifies before each GO.
- A register row missing a bound, owner, or timeline is a gap — local
  (the practitioner supplies it now) or upstream (the Phase 6
  register template lacked the slot).

### 3. Deployment Machinery & Shape Confirmation

- **Declare the deployment shape**: **release-shaped** (publish, tag,
  changelog, release-evidence artifact, consumer advisories; recall =
  deprecation + advisory + patched release; published versions are
  immutable) or **service-shaped** (deploy, health checks, traffic;
  rollback = revert + verify). Ground the declaration in the Step 00
  machinery evidence — registry versus server fleet — and cite it; it
  drives every Stage 1 template branch (Steps 02–04). Where the
  subject has more than one deployable surface, declare the shape per
  surface; do not average them into a hybrid.
- Confirm the **pipeline reality**: the machinery as reconciled and
  hardened through Phases 4–5 is what is actually in place — CI/CD
  identity, tag/publish or deploy capability, release cadence.
- Confirm the **registry credentials posture** — posture only, never
  values: credentials are never printed, logged, or committed. For
  published packages, confirm the supply-chain posture (provenance,
  signing, 2FA) the release discipline operates.
- **Release-shaped**: confirm the registry realities Step 04's recall
  path depends on — unpublish windows, deprecation policy, advisory
  channels — planned before they are needed. **Service-shaped**:
  confirm deploy tooling, health checks, traffic control, and
  rollback capability.
- Confirm the **release-evidence schema** where Phase 3 designed one
  (e.g., a Diamonds MC-12-style release-evidence artifact) is
  reachable — Step 02 §3 plans against it and Step 03 emits it. "None
  designed" is valid; record it so Step 02 §3 plans knowingly.
- Confirm the **Stage 1 execution mode** from Step 00: direct
  execution versus the patch-mediated fallback — human checkpoints
  guard every consequential action regardless of mode.

### 4. Observability & Baseline Confirmation

- Enumerate the **observability touchpoints** (designed in Phase 3,
  implemented in Phase 5) and confirm each is **activatable at
  deployment** — it exists, and its activation is verifiable at Step
  03. Observable on paper is not observable in practice — confirm how
  each will actually be reviewed.
- Confirm the **Phase 6 Step 05 performance baselines** are reachable
  — the numbers Step 06 checks drift against and Step 07 measures
  actuals against.
- Confirm the **Phase 6 Step 09 frozen documentation** is reachable —
  the release-state baseline and queryability standard operations
  maintain; every change triggers DOC-NN maintenance against it.
- Confirm the **monitoring access** declared at Step 00 covers what
  the touchpoints require. A touchpoint no configured access can read
  is a gap.

### 5. Compliance Matrix Confirmation (CONDITIONAL)

- Does the subject carry compliance obligations, per the Phase 6 Step
  04 compliance matrix? If none: mark this category **Not
  applicable** — and record the consequence: Step 06's compliance
  section runs Not applicable while specification and scorecard drift
  detection still run.
- Where obligations exist: confirm the matrix is reachable as the
  **living compliance baseline** drift detection maintains — per
  obligation: the control, verification cadence, evidence-generation
  expectation, and evidence-continuity owner. Passing at the Phase 6
  gate does not keep the system compliant.

### 6. Scorecard Baseline Confirmation

- Confirm the six principles' weights — Security, Maintainability,
  Economics, Operations, Scoring & Metrics, Correctness Verification
  — inherited from Phase 2 Step 02 unchanged. Next-cycle Phase 2 may
  re-weight; a re-weighting need observed during operations is a
  Next-Cycle Package item, never a silent adjustment.
- Confirm the Phase 6 scorecard refresh outcomes per principle
  (Readiness Report §4). **The Phase 6 refresh is the launch
  baseline**: Step 07's launch refresh and every ongoing refresh
  measure against it.
- Confirm the target distribution result at the Phase 6 gate. A
  principle that passed CONDITIONAL is where the Step 07 launch
  refresh will be under pressure — name those principles now.
- Confirm the refresh discipline: the scorecard is a live dashboard;
  **a below-baseline refresh is a DR-NN finding with routing**.
- Confirm the explicit deprioritizations the cycle made (an
  Operations deferral is the recurring case in this track). Phase 7
  preserves each as deprioritization — operate what was built, no
  more — and carries the re-elevation candidate into Category 8's
  seeds rather than silently expanding scope now.

### 7. Forward-Handoff Confirmation (Phase 6 Step 10 §6.1)

- Enumerate the §6.1 Phase 7 Handoff Summary rows: for each Phase 7
  concern, what Phase 6 expected Phase 7 to **consume** and where it
  lives, and what Phase 7 is expected to **produce** against it.
- For each row, confirm which Phase 7 step (02–09) performs the
  expected activity and which validation category confirmed the input
  it consumes. An input flagged incomplete that survived the Phase 6
  gate is a candidate gap here.
- Cross-check the §6.1 references against the Category 2 inventory —
  the handoff and the register must agree on what Phase 7 watches.
- **Anything Phase 6 expected Phase 7 to produce that no step of this
  toolkit covers is a candidate gap** — diagnose which toolkit owns
  it: a Phase 6 wrong expectation, or a Phase 7 missing slot.

### 8. Calibration & Next-Cycle Seed Confirmation

- Confirm the **Phase 5 Step 10 §5 multiplier calibration table** (as
  consolidated at Phase 6) is reachable, with its **ESTIMATED** tags
  intact. Step 07 §5 records production-cycle actuals against it;
  multipliers graduate ESTIMATED → MEASURED with 2–3 cycles of data;
  the Next-Cycle Package carries the calibrated table. Graduation
  happens through measurement, not at validation.
- Enumerate the **deferred deprioritizations due for re-elevation**:
  what did this cycle explicitly defer, and what re-elevation plan or
  trigger exists (e.g., a Phase 2 Operations deferral that Phase 7's
  own operating experience will pressure-test)? Confirm each is
  **seeded into the Step 09 §5 Next-Cycle Package from day one** —
  the package accumulates as items arise, not reconstructed from
  memory at the cycle boundary.
- Enumerate the **Phase 2 watch-triggers** the Improvement Plan set
  ("re-visit X when Y"). Confirm each is carried as a **standing
  watch**: which Stage 2/3 loop watches its condition; a fired
  trigger routes to Step 09.
- Confirm an **operational effort/cost capture method** exists — Step
  07 §5 needs actuals to graduate the multipliers. If none, flag it
  now so the method is named at the Step 07 launch refresh, not
  improvised mid-loop.

### 9. Validation Gap Pre-Check (Closing Question)

Before producing the report, ask the practitioner:

> *Given the validation we've walked through, is there anything you
> expected me to check that I didn't? Specifically: are there aspects
> of the Deployment Readiness Report — or the frozen documentation,
> baselines, compliance matrix, and release machinery behind it —
> that you find ambiguous, incomplete, or potentially miscommunicated
> to a Phase 7 session that we haven't surfaced?*

The pre-check exists because the question bank cannot anticipate
every gap; practitioner-driven surfacing catches the rest.

---

## Output Format

When the validation is complete, produce the Phase 6 Input Validation
Report using this structure. All sections are required; mark any
empty section `[OPEN — see Gap Register]` rather than fabricating
content or silently omitting it.

---
```markdown
# Phase 6 Input Validation Report — Phase 7 (Deployment & Evolution)

**Project:** [subject name and version]
**Validation Date:** [date]
**Phase 6 Completion Date:** [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]
**Deployment Readiness Report Version:** [version, with amendment-date if applicable]
**Frozen Documentation Baseline (Phase 6 Step 09):** [version / date]
**Compliance Matrix (Phase 6 Step 04):** [version / "Not applicable"]
**Calibration Table (Phase 5 Step 10 §5, consolidated at Phase 6):** [version]
**Status:** Draft — Pending Practitioner Review

> ⚠️ This report validates that Phase 7 understands the Phase 6
> inputs correctly. It is **not** a re-audit of Phase 6 findings,
> Phase 5 implementation, or Phase 4 architecture — all are
> authoritative for this cycle. Gaps surface either as Phase 7 local
> (resolve within Phase 7) or as upstream toolkit (queue for the
> responsible toolkit's revision in a separate session).

---

## §1 — Subject Identity & Readiness Report Currency

| Field | Value | Confidence |
|-------|-------|-----------|
| Subject name | | [H/M/L] |
| Subject current version | | [H/M/L] |
| Readiness Report date / version | | [H/M/L] |
| **Readiness Report §9 determination (BLOCKING)** | [READY — clear / CONDITIONALLY READY — conditional inventory below / **HALT — NOT READY (any variant); Phase 7 must not proceed**] | [H/M/L] |
| **Readiness Report §7 amendment packages (BLOCKING)** | [Clear — "Not applicable" or resolved into a re-issued report / **HALT — unresolved package; forward handoff not operational**] | [H/M/L] |
| Gate override applied at the Phase 6 gate? | [No / Yes — what was overridden, risk inherited into §2] | [H/M/L] |
| Phase 6 amendments since completion? / Subject release since the gate? | [No / Yes — dates and versions; the most acute currency window] | [H/M/L] |
| Scheduled mechanism / dependency shipped early via parallel track? | [No / Yes — grounding note / Yes — candidate invalidation, see Gap Register; Step 02 confirms and routes] | [H/M/L] |

**Conditional inventory (populated when CONDITIONALLY READY):**

| Conditional | Named Remediation | Owner | Target | Blocks Which Deployment Work | Step 02 Verification |
|-------------|-------------------|-------|--------|------------------------------|----------------------|
| | | | | | [schedule verified before each GO] |

## §2 — Carried-Risk & Conditional-Pass Inventory

| Item ID (Phase 6 identity) | Type | Description | Bounds | Owner | Timeline | Watching Loop | Confidence |
|----------------------------|------|-------------|--------|-------|----------|---------------|-----------|
| | [Carried risk / Conditional pass / Override risk] | | | | | [Step 05 / Step 06 §5 / Step 07] | [H/M/L] |

**Lapse discipline confirmed (a lapsed timeline is a DR-NN finding,
not a quiet extension):** [Yes/No]
**Rows missing a bound, owner, or timeline:** [None / Gap Register]

## §3 — Deployment Machinery & Shape Confirmation

**Declared deployment shape:** [Release-shaped / Service-shaped /
per-surface list] — grounded in: [Step 00 machinery evidence cited]

| Machinery Element | Confirmed? | Evidence / Notes |
|-------------------|-----------|------------------|
| CI/CD pipeline identity and release cadence | [Yes/No] | |
| Tag/publish capability (release-shaped) or deploy tooling (service-shaped) | [Yes/No] | |
| Registry credentials posture (posture only — never values) | [Yes/No] | |
| Supply-chain posture: provenance / signing / 2FA (release-shaped) | [Yes/No/N.A.] | |
| Recall realities: unpublish window, deprecation policy, advisory channels (release-shaped → Step 04 §3) | [Yes/No/N.A.] | |
| Rollback capability: health checks, traffic control, revert path (service-shaped → Step 04 §2) | [Yes/No/N.A.] | |
| Release-evidence schema (Phase 3-designed, e.g., MC-12-style) reachable | [Yes / No — none designed; Step 02 §3 plans knowingly / No — see Gap Register] | |

**Stage 1 execution mode (from Step 00):** [Direct execution /
Patch-mediated fallback] — human checkpoints regardless of mode

## §4 — Observability & Baseline Confirmation

| Artifact | Reachable / Activatable? | Consuming Steps | Confidence |
|----------|--------------------------|-----------------|-----------|
| Observability touchpoints (Phase 3-designed, Phase 5-built) | [Activatable — verifiable at Step 03 / Partial / No] | Step 03 (activation), Steps 05–07 (review) | [H/M/L] |
| Phase 6 Step 05 performance baselines | [Yes/No] | Step 06 (drift), Step 07 (actuals) | [H/M/L] |
| Phase 6 Step 09 frozen documentation | [Yes/No] | DOC-NN maintenance; Steps 05–06 | [H/M/L] |
| Monitoring access (per Step 00) covers the touchpoints | [Yes / No — gap] | Stage 2 loops | [H/M/L] |

**Review reality check:** [how each touchpoint will actually be
reviewed — routine, owner, cadence — or flagged for Step 03]

## §5 — Compliance Matrix Confirmation (CONDITIONAL)

**Applicability:** [Obligations exist — table below / **Not
applicable** — Step 06 §4 runs Not applicable while specification and
scorecard drift detection still run]

| Obligation / Control | Verification Cadence | Evidence Expectation | Evidence Continuity Owner | Confidence |
|----------------------|----------------------|----------------------|---------------------------|-----------|
| | | | | [H/M/L] |

## §6 — Scorecard Baseline Confirmation

| Principle | Weight | Phase 6 Refresh Status (Readiness Report §4) | Confidence |
|-----------|-------:|----------------------------------------------|-----------|
| Security | | [PASS/CONDITIONAL/FAIL] | [H/M/L] |
| Maintainability | | | |
| Economics | | | |
| Operations | | | |
| Scoring & Metrics | | | |
| Correctness Verification | | | |

Weights confirmed inherited from Phase 2 Step 02 unchanged: [Yes/No]
Phase 6 refresh confirmed as the launch baseline for Step 07: [Yes/No]
Target distribution at the Phase 6 gate: [summary — principles under
pressure at the Step 07 launch refresh named]
Below-baseline refresh = DR-NN with routing, acknowledged: [Yes/No]

**Explicit deprioritizations to preserve:**
[List each — what was deprioritized, why, its re-elevation candidacy
(cross-reference §8). Phase 7 will not silently elevate.]

## §7 — Forward-Handoff Confirmation (Phase 6 Step 10 §6.1)

| §6.1 Row | Phase 7 Expected to Consume | Location | Present? | Performing Step | Covered By Validation Category | Candidate Gap? |
|----------|----------------------------|----------|----------|-----------------|-------------------------------|----------------|
| | | | [Complete/Incomplete] | [Step 02–09] | [§2–§6, §8 of this report] | [No / Yes — see Gap Register] |

**§6.1 ↔ §5 register cross-check:** [Agree on what Phase 7 watches /
Discrepancies listed in the Gap Register]
**Expectations no step of this toolkit covers:** [None / listed with
scope diagnosis — Phase 6 wrong expectation vs Phase 7 missing slot]

## §8 — Calibration & Next-Cycle Seed Confirmation

**Multiplier calibration table (Phase 5 Step 10 §5):**

| Category | Multiplier | Tag | Cycles of Data | Notes |
|----------|-----------:|-----|----------------|-------|
| | | [ESTIMATED/MEASURED] | | [graduates via Step 07 §5 measurement] |

**Deferred deprioritizations due for re-elevation:**

| Deferral | Deprioritized At | Re-Elevation Trigger / Plan | Seeded to Step 09 §5? |
|----------|------------------|-----------------------------|-----------------------|
| | [e.g., Phase 2 — Operations] | | [Yes — from day one / gap] |

**Phase 2 watch-triggers carried as standing watches:**

| Trigger | Condition ("re-visit X when Y") | Standing Watch (loop) | Fired Routing |
|---------|---------------------------------|-----------------------|---------------|
| | | [Step 05 / 06 / 07 / 08] | [Step 09 intake / Next-Cycle Package] |

**Operational effort/cost capture method:** [Exists — named / Flagged
for the Step 07 launch refresh]

## §9 — Validation Gap Register (Split by Scope)

### §9.1 — Phase 7 Local Gaps

Gaps that Phase 7 must resolve within its own steps and loops, or
acknowledge as documented limitation.

| Gap ID | Description | Affected Category / Loop / Step | Resolution Path | Priority |
|--------|-------------|---------------------------------|----------------|----------|
| VG-L-01 | | | [Step 02 prerequisite check / watch item on Step NN loop / Step 00 amendment / out-of-prompt practitioner answer / accepted limitation] | [H/M/L] |

### §9.2 — Upstream Toolkit Gaps

Gaps that exist because an upstream toolkit was structurally
incomplete. Queue for the responsible toolkit's revision in a
separate session. Phase 7 proceeds with workaround.

| Gap ID | Description | Owning Toolkit | What That Toolkit Was Missing | Phase 7 Workaround | Toolkit Revision Recommendation |
|--------|-------------|----------------|-------------------------------|--------------------|--------------------------------|
| VG-U-01 | | [Phase 6 / 5 / 4 / 3 / 2 / 1] | | | |

> **Each upstream gap requires the owning-toolkit diagnosis (usually
> Phase 6, occasionally deeper), the structural absence itself, and a
> concrete revision recommendation. Vague upstream gaps don't
> actionably produce toolkit improvements.**

## §10 — Validation Confidence Summary

| Validation Category | Confidence | Notes |
|--------------------|------------|-------|
| Subject identity & readiness report currency | [H/M/L] | |
| Carried-risk & conditional-pass inventory | [H/M/L] | |
| Deployment machinery & shape | [H/M/L] | |
| Observability & baselines | [H/M/L] | |
| Compliance matrix (conditional) | [H/M/L or N/A] | |
| Scorecard baseline | [H/M/L] | |
| Forward-handoff confirmation | [H/M/L] | |
| Calibration & next-cycle seeds | [H/M/L] | |

**Overall validation status:** [Anchored / Anchored with caveats /
Significant gaps / HALTED — NOT READY determination or unresolved
amendment package]

[1–3 sentences describing the overall validation outcome and what the
next step (Step 02 Launch-Readiness Confirmation) must verify first.]

---

## Version

v1.0 (initial validation report; re-run Step 01 if an amended
Deployment Readiness Report or amended upstream artifact replaces the
validated inputs — the standing loops re-anchor against the
re-validated inputs)
```

---

## Evaluation Checklist

Before this artifact is accepted as complete, verify all items:

- [ ] All 10 sections are populated; empty sections are marked
      `[OPEN]` with reference to the relevant gap, not omitted
- [ ] Both blocking checks were performed first and recorded in §1:
      the §9 determination is READY or CONDITIONALLY READY, and the
      §7 amendment packages are clear or resolved; if either failed,
      the run halted and no downstream validation or Phase 7 work
      proceeded; when CONDITIONALLY READY, the conditional inventory
      is complete (remediation, owner, target, blocked deployment
      work, Step 02 schedule verification before each GO)
- [ ] Subject version is re-verified, not carried over from report
      metadata; releases and early-shipped mechanisms since the Phase
      6 gate are checked with the grounding-vs-invalidation decision
      rule applied — this is the rule's most acute window
- [ ] Every Phase 6 Step 10 §5 Carried-Risk Register row is
      inventoried in §2 with its bounds, owner, timeline, and a named
      watching loop; conditional-pass and override-risk items are
      folded in; the lapse-is-a-DR-NN-finding discipline is confirmed
- [ ] The deployment shape is declared in §3 with grounding evidence
      from the Step 00 machinery inventory — not assumed — with the
      per-shape elements confirmed (recall realities for
      release-shaped; rollback tooling for service-shaped) and the
      release-evidence schema reachability recorded; credentials
      appear as posture only, never values
- [ ] Observability touchpoints, the Phase 6 Step 05 baselines, and
      the Phase 6 Step 09 frozen documentation are confirmed
      reachable/activatable — with how touchpoints will actually be
      reviewed recorded — or the gap carries a named resolution path
- [ ] The compliance category is resolved: obligations confirmed with
      the matrix reachable as the living baseline, or Not applicable
      recorded with its Step 06 consequence stated
- [ ] Principle weights are confirmed inherited from Phase 2 Step 02
      unchanged; the Phase 6 refresh is the launch baseline for Step
      07; principles under pressure are named; deprioritizations are
      preserved with re-elevation candidacy cross-referenced to §8
- [ ] Every Phase 6 Step 10 §6.1 forward-handoff row is covered by a
      performing step or flagged as a candidate gap with scope
      classification; the §6.1 ↔ §5 cross-check is recorded
- [ ] The calibration table is confirmed with ESTIMATED tags intact;
      deferred re-elevations are seeded to the Step 09 §5 Next-Cycle
      Package from day one; Phase 2 watch-triggers carry a named
      standing watch and fired-trigger routing; an effort/cost
      capture method exists or is flagged
- [ ] The Validation Gap Register in §9 is split into §9.1 (Phase 7
      local, VG-L-NN) and §9.2 (upstream toolkit, VG-U-NN); every
      upstream gap names the owning toolkit, the specific structural
      absence (not just the symptom), and a concrete revision
      recommendation; every local gap names its resolution path
- [ ] Validation confidence per category is captured with H/M/L tags
      and rationale; the pre-check question (Category 9) was asked
      and its answer is reflected in the gap register
- [ ] No deployment or operational work has been performed — no
      launch determination, no publish or deploy actions, no
      runbooks, no drift runs, no scorecard refreshes, and no
      re-audit of Phase 6 findings — Step 01 is validation only
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)

---

*Part of the Phase 7 (Existing Projects) Deployment & Evolution Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `deployment-evolution.existing-project.instructions.md`*
*Previous step: `step-00-building-block-discovery.prompt.md`*
*Next step: `step-02-launch-readiness-confirmation.prompt.md`*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Phase 7 Phase 6 Input Validation prompt, the last Step 01 in the existing-projects track and the sibling of the Phase 5/6 Step 01 pattern. Two hard blocking checks gate Phase 7 entry: the Phase 6 Step 10 §9 determination must read READY or CONDITIONALLY READY (with a conditional inventory whose schedules Step 02 verifies before each GO), and the §7 amendment packages must be resolved. Nine validation categories (eight substantive plus the closing pre-check) keyed to the Deployment Readiness Report: the §5 Carried-Risk Register inventoried with bounds/owners/timelines and assigned watching loops (a lapse is a DR-NN finding); the release-shaped vs service-shaped declaration grounded in Step 00 machinery evidence, driving the Stage 1 template branches; observability, performance-baseline, frozen-docs, compliance (conditional), and scorecard-baseline confirmations; the §6.1 forward-handoff check; and a calibration & next-cycle seed category confirming the Phase 5 Step 10 §5 multiplier table, deferred re-elevations (e.g., a Phase 2 Operations deferral), and Phase 2 watch-triggers as standing watches seeding the Step 09 §5 Next-Cycle Package. The two-scope Validation Gap Register (VG-L-NN / VG-U-NN) closes Phase 7 Feedback Channel 1; local-gap resolution paths route to the Step 02 prerequisite check or named standing loops. The concurrent-release / dependency-shipped-early rule (inherited Phase 3 v1.1) is flagged as most acute in the window between the Phase 6 gate and launch. |
