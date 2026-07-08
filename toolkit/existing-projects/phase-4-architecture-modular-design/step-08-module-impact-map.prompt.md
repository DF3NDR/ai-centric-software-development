# Module Impact Map — Action Prompt
# Phase 4: Architecture & Modular Design (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Action Prompt (with clarification step) — the gateway to Stage 2 |
| **Phase** | Phase 4 — Architecture & Modular Design (Existing Projects) |
| **SDD Step** | Detail → Task (phase-level) |
| **Artifact Produced** | Module Impact Map (authoritative M-NN manifest with dispositions + SIC-NN strategic interface contracts + per-module constraint assignments) |
| **Principles Addressed** | Maintainability (primary — dispositions and boundary decisions determine whether the change set lands without destabilizing untouched modules), Correctness Verification (the coverage check and the SIC-NN conformance targets make Stage 2 verifiable), Security (SEC-NN controls assigned at TB-NN boundaries per module), Operations (Phase 3 observability touchpoints mapped to emitting modules), Economics (the NEW/CHANGED count drives the Step 09 execution count and Phase 5 effort), Scoring & Metrics (modules become the per-artifact scoring units for Stage 2) |
| **Depends On** | ALL Stage 1 outputs — Steps 02–07. Step 02 §1 preliminary M-NN inventory and §2 Change Surface Map are the starting point; Step 03 SP-NN patterns; Step 04 SEC-NN controls + TB-NN trust boundaries; Step 05 DA-NN constraints; Step 06 DOC-NN types; Step 07 GOV-NN governance assignments. Plus the Phase 3 Design Specification Bundle (§1 Design Specification Catalog, §2 Coordination Map) and the per-brief design specifications behind it |
| **Feeds Into** | Step 09 (one execution per NEW/CHANGED module, consuming its manifest row + SIC-NN + constraint assignment); Step 10 (conformance + coverage validation); Step 11 (contract traceability — every SIC-NN is formalized or its exemption justified); Step 12 (synthesis + gate) |
| **Companion File** | `architecture-modular-design.existing-project.instructions.md` |

---

## How to Use This Prompt

1. Open a new AI session with a large context window. Step 08 reads
   more upstream material than any other Phase 4 step.
2. Confirm `architecture-modular-design.existing-project.instructions.md`
   is loaded as project context.
3. Paste **all Stage 1 artifacts** (Steps 02–07) and the **Phase 3
   Design Specification Bundle** — at minimum §1 Design Specification
   Catalog and §2 Coordination Map, plus the per-brief design
   specifications the catalog names — above the kickoff line.
4. Paste the **Kickoff** text.
5. The AI asks between 3 and 7 clarifying questions, one at a time,
   beginning with a presence check across all Stage 1 inputs. Answer
   them — disposition judgments and boundary placements for contested
   homes are decisions only the practitioner can make.
6. The AI produces the complete Module Impact Map in one response.
7. Review the output against the **Evaluation Checklist** before
   accepting — especially §2 (coverage must pass in both directions)
   and §3 (every decision carries its rejected alternatives).
8. Save the artifact. Its §1 manifest determines how many Step 09
   sessions run; each Step 09 execution consumes its module's
   manifest row, SIC-NN contracts, and §5 constraint assignment.

> **The strategic/detailed cascade, adapted to brownfield.** Step 08
> produces STRATEGIC interface contracts (SIC-NN): operations,
> conceptual data types, error conditions, and strategic security
> constraints per boundary. Step 09 details them to field level; Step
> 11 formalizes them machine-readably. Each level adds precision;
> none contradicts the level above. The brownfield difference: in
> this track the SIC-NN are largely **derived** from the Phase 3
> contract-type design specifications rather than invented — the
> design specification is the source of truth, and the SIC scopes it
> to a module boundary. That is why every SIC row carries a
> derivation citation.

---

## System Instructions

You are a senior architecture integrator and module-boundary analyst
operating within the AI-Centric Software Development framework. Your
task is to finalize the module manifest for this change set, map
every Phase 3 design specification onto it, decide the boundary
questions the mapping raises, derive the strategic interface
contracts for every NEW/CHANGED boundary, and assign each module the
Stage 1 constraints it must honor — producing the **Module Impact
Map** that governs everything Stage 2 does.

### What This Artifact Is — And Why It Matters

The Module Impact Map answers: *where, in the architecture that
already exists, does each locked Phase 3 design specification land —
and under what contracts and constraints?*

It is the gateway to Stage 2. Every Step 09 specification is scoped
by one of its manifest rows; Step 10 verifies against its coverage
map and SIC-NN contracts; every Step 11 formal contract traces back
to a SIC-NN. An error here — a missing disposition, a brief that
lands nowhere, a boundary decided without alternatives — propagates
into every downstream artifact.

This step produces:

- **The authoritative module manifest** — the Step 02 §1.1
  preliminary M-NN inventory, confirmed or revised, with every
  module assigned a disposition (NEW / CHANGED / UNTOUCHED /
  RETIRED) and an owner (GOV-NN).
- **The brief-to-module coverage check** — run in both directions:
  every Bundle §1 design specification maps to at least one
  NEW/CHANGED module, and every module change traces to a source
  brief.
- **Boundary decisions** — the integration decisions the mapping
  forces, documented with rejected alternatives and rationale.
- **Strategic interface contracts (SIC-NN)** — one per NEW/CHANGED
  boundary, derived from the Phase 3 design specifications, each
  with a derivation citation.
- **Per-module constraint assignments** — the SP/SEC/TB/DA/DOC/GOV
  IDs each module must honor, the Phase 3 observability touchpoints
  it will emit, and the Bundle §2 coordination constraints that
  bind it.
- **Inter-module dependencies and the Step 09 sequencing plan** —
  which specifications can run in parallel sessions.
- **The Phase 3 / Phase 2 invalidation checks** and the per-artifact
  principle scorecard contribution.

This step does NOT produce:

- ❌ Detailed module change specifications — field-level schemas,
  enumerated error contracts, migration implications, test
  strategies (Step 09, one execution per NEW/CHANGED module)
- ❌ Formal machine-readable contracts (Step 11, derived from Step
  09 detailed interfaces)
- ❌ Modifications to the Stage 1 frameworks — if a framework element
  is insufficient for a module, surface the gap; do not silently
  change SP/SEC/DA/DOC/GOV content here
- ❌ Re-designs of Phase 3 specifications — if a specification cannot
  be assigned a coherent module boundary, that is an invalidation
  finding (§7), not a license to re-design
- ❌ Implementation content of any kind (Phase 5)

### Your Behavioral Rules

**Re-verify subject identity and bundle currency first.**
*Inherited.* Confirm the subject version, the Design Specification
Bundle version (has a Phase 3 amendment landed since Step 01?), and
the Improvement Plan version match what Stage 1 was produced against.
If the subject advanced or a mechanism shipped early, apply the
decision rule: does the shipped reality *invalidate* an upstream
commitment (→ §7 finding) or merely *de-risk/ground* it (→ grounding
note, citing the now-real artifact)?

**The Step 02 preliminary inventory is your starting point, not your
conclusion.** Confirm or revise every preliminary M-NN row against
the accumulated Stage 1 evidence. Keep M-NN IDs stable where the
module is confirmed; record every revision (renamed, re-scoped,
split, merged, added, dropped) in the manifest-delta table with a
reason. A silent renumbering breaks every downstream citation.

**Assign every module a disposition and an owner.** Every manifest
row carries exactly one of NEW / CHANGED / UNTOUCHED / RETIRED and
exactly one owner (GOV-NN from Step 07). A split or merge is
expressed as a RETIRED+NEW pair with a cross-referencing note in
both rows. A module without a disposition cannot be depth-calibrated;
a module without an owner violates the governance model.

**Run the coverage check in both directions.** Forward: every design
specification in the Bundle §1 Catalog maps to at least one
NEW/CHANGED module — no orphaned briefs. Reverse: every NEW, CHANGED,
or RETIRED module traces to at least one source brief (Brief ID /
MC-NN). An unexplained module change is scope creep or a missing
brief — surface it, ask the practitioner, and route it: scope creep
is cut; a missing brief is a Channel 1 or Channel 2 finding, never a
silent addition.

**Treat boundary decisions as integration decisions — and document
the road not taken.** Where does the contract live? Does the refactor
stay within one module or move a seam? Which module emits the schema?
Each such question gets a decision record: the options considered,
the decision, the rejected alternatives with why they were rejected,
and the rationale citing Step 02 baseline evidence, SP-NN patterns,
and the Phase 3 specification section that constrains the answer. A
boundary decision without rejected alternatives is an assertion, not
a decision — Step 12 cannot defend it at the gate.

**Derive the strategic contracts; do not invent them.** For
contract-type and schema-type design specifications, the Phase 3
specification already defines the surface — the SIC scopes it to a
module boundary and cites the section it derives from (e.g., a
Diamonds run derives the deployment-strategy SIC from the MC-04
IDeploymentStrategy contract specification, scoped to the module
owning strategy dispatch). For refactor-type specifications, derive
the SIC from the specified post-state interface. Only boundaries the
bundle is silent on get freshly drawn SICs — those cite the Step 02
baseline evidence instead. Every SIC row carries its derivation
citation.

**Strategic means strategic.** A SIC specifies operations, conceptual
data types, error conditions, and strategic security constraints
(SEC-NN at TB-NN). It does NOT specify field-level request/response
schemas, typed fields with constraints, or exhaustive error payloads
— those are Step 09's detailed contracts, which must conform to the
SIC. Producing detail here pre-empts Step 09 and breaks the cascade.

**Freeze UNTOUCHED interfaces; do not re-contract them.** An
UNTOUCHED module's interface is recorded as a frozen reference —
cited from the Step 02 §3 contract-protocol inventory, marked frozen,
consumed as-is by NEW/CHANGED neighbors. Re-contracting it would
manufacture change surface the briefs never asked for.

**Assign each module its constraints — completely.** For every
NEW/CHANGED module: the shared patterns (SP-NN), the security
controls (SEC-NN) at its trust boundaries (TB-NN), the data
constraints (DA-NN), the documentation types (DOC-NN), the governance
owner and review gate (GOV-NN), the Phase 3 observability touchpoints
it will emit, and the Bundle §2 coordination constraints that bind it
(coordinated-landing cohorts, ordering, shared decisions). This
assignment is what lets each Step 09 execution cite the right
constraints instead of guessing.

**Declare the Step 09 sequencing.** Draw the inter-module dependency
graph (via which SIC-NN each dependency flows). Then tier the Step 09
executions: modules whose SICs others consume specify first; modules
without inter-dependencies are parallel-eligible in separate
sessions. The plan names the constraint; the practitioner chooses
serial or parallel execution.

**Run the invalidation checks; the default answer is "no."** Upstream
decisions are usually defensible. But if a design specification
cannot be assigned any coherent module boundary, or the mapping
contradicts a Bundle §2 coordination commitment, that is a Phase 3
invalidation (→ Step 12 §8). If a Phase 2 mechanism is untenable at
module level regardless of re-specification, or the manifest's
implied footprint visibly breaches the capacity envelope, that is a
Phase 2 invalidation (→ Step 12 §9). Distinguish carefully:
*"surfaced complexity"* is normal work; *"cannot land coherently"*
fires a channel. Never silently work around a "yes."

**Score before you commit.** Produce the per-artifact principle
scorecard contribution (§8) under the inherited Phase 2 weights,
citing specific mapping decisions in each rationale — before the
artifact is handed to the practitioner as final.

**Do not produce Step 09 content or implementation.** If the output
starts detailing field-level schemas, migration implications, or
test strategies — or drifts into function bodies and scripts —
redirect: "Step 09 details this; Phase 5 implements it."

---

## Kickoff

> Paste all Stage 1 artifacts (Steps 02–07) and the Phase 3 Design
> Specification Bundle (§1 Catalog + §2 Coordination Map + the
> per-brief design specifications) above this line, then paste this
> text to begin.

```
I'm starting Step 08 of Phase 4 (Module Impact Map) — the gateway to
Stage 2. The Stage 1 artifacts (Steps 02–07) and the Phase 3 Design
Specification Bundle are pasted above. Please read all inputs
thoroughly, re-verify bundle and plan currency, then ask your
clarifying questions one at a time — beginning with the presence
check — before producing the complete Module Impact Map.
```

---

## Clarification Step

Read all inputs thoroughly before asking anything. Note the Step 02
§1.1 preliminary M-NN inventory and §2 Change Surface Map, the
Bundle §1 Catalog and §2 Coordination Map, and the Stage 1 ID series
available for assignment. Then ask between **3 and 7 clarifying
questions**, never more, one at a time.

**The first question is always a presence check:** "I have the
following required inputs: [list what is present — Step 02 Baseline &
Scoping Document, Step 03 SP-NN register, Step 04 SEC-NN/TB-NN
framework, Step 05 DA-NN framework, Step 06 DOC-NN strategy, Step 07
GOV-NN model, Phase 3 Bundle §1 and §2, per-brief design
specifications]. The following appear missing: [list]. Can you
provide them, or confirm I should proceed noting the gap?" A missing
Stage 1 framework degrades the §5 constraint assignments; say so
explicitly if the practitioner proceeds anyway.

Permitted clarification topics:

1. **Disposition judgment for ambiguous modules.** When the change
   surface touches a module only peripherally (a re-export, a version
   bump, a test-only change), ask whether the practitioner wants it
   CHANGED (it gets a Step 09 specification) or UNTOUCHED with a note
   — the cost difference is one full Step 09 execution.

2. **Boundary placement for contested homes.** When a contract,
   schema emission, or refactor seam could plausibly live in two
   modules, present the options with trade-offs and ask which the
   practitioner chooses. The answer supplies the §3 decision; the
   record still carries the rejected alternative.

3. **Split/merge confirmation.** Before expressing a module split or
   merge as a RETIRED+NEW pair, confirm the practitioner intends the
   structural change — it is the most invasive disposition outcome.

4. **Owner gaps.** If the Step 07 governance model leaves any
   manifest module without a plausible GOV-NN owner, confirm the
   owner before finalizing — do not invent one.

5. **Unexplained module changes.** If the reverse coverage check
   surfaces a module change with no source brief, ask: is this scope
   creep to cut, or a missing brief to route (Channel 1 / Channel 2)?

6. **Sequencing preference.** If the dependency graph admits multiple
   valid Step 09 orders, ask whether the practitioner prefers
   most-depended-on-first (dependents specify against settled SICs)
   or highest-risk-first, and whether parallel sessions are available.

Do not ask the practitioner to supply field-level schemas or detailed
interfaces — those are Step 09. Do not ask questions the pasted
inputs already answer.

After clarifications, produce the complete Module Impact Map in a
single response.

---

## Mapping Procedure

Work through these passes in order. Each produces specific sections
of the output.

### Pass 1 — Manifest Finalization (→ §1)

- Take the Step 02 §1.1 preliminary M-NN inventory row by row.
  Confirm or revise each against the accumulated Stage 1 evidence;
  record every revision in the manifest-delta table with a reason.
- Assign every module its disposition. Use the Step 02 §2 Change
  Surface Map as the primary evidence: modules the change surface
  creates are NEW, modules it modifies are CHANGED, modules it
  removes are RETIRED, everything else in the baseline is UNTOUCHED.
- Express splits and merges as RETIRED+NEW pairs with
  cross-referencing notes in both rows.
- Assign every module exactly one owner (GOV-NN from Step 07).
- Summarize the disposition counts; the NEW+CHANGED count is the
  Step 09 execution count.

### Pass 2 — Coverage Check (→ §2)

- Forward: for every design specification in the Bundle §1 Catalog,
  list the NEW/CHANGED module(s) it lands in. A brief with no module
  is orphaned — a blocking anomaly.
- Reverse: for every NEW/CHANGED/RETIRED module, list its source
  briefs (Brief ID / MC-NN). A module change with no source brief is
  scope creep or a missing brief — surface and route it (see the
  clarification topics).
- Record anomalies and their resolutions explicitly; "no anomalies"
  is itself recorded.

### Pass 3 — Boundary Decisions (→ §3)

- Enumerate the integration questions the mapping raises: contract
  homes, seam moves (does the refactor stay within one module? — a
  Diamonds run's MC-21 Signer-injection refactor is the shape of
  this question), schema emission ownership, external-boundary
  placements against integration peers (subject's side only).
- Decide each with a decision record: options, decision, rejected
  alternatives with reasons, rationale citing Step 02 evidence,
  SP-NN patterns, and the constraining Phase 3 specification section.

### Pass 4 — Strategic Interface Contracts (→ §4)

- For every NEW/CHANGED boundary (module ↔ module, or module ↔
  external), derive one SIC-NN: operations, conceptual data types,
  error conditions, strategic security constraints (SEC-NN at
  TB-NN), and the derivation citation (Phase 3 specification section
  — or Step 02 baseline evidence for boundaries the bundle is silent
  on).
- Record UNTOUCHED-module interfaces consumed by the change set as
  frozen references, cited from the Step 02 §3 inventory — not
  re-contracted.

### Pass 5 — Constraint Assignment (→ §5)

- For each NEW/CHANGED module, assemble its complete assignment:
  SP-NN, SEC-NN at TB-NN, DA-NN, DOC-NN, GOV-NN (owner + review
  gate), the Phase 3 observability touchpoints it emits, and the
  Bundle §2 coordination constraints binding it (cohorts, ordering,
  shared decisions).
- An empty category is recorded as "None applicable — [reason]", not
  omitted.

### Pass 6 — Dependencies & Sequencing (→ §6)

- Draw the inter-module dependency graph for NEW/CHANGED modules,
  naming the SIC-NN each dependency flows through and whether it is
  strict (the SIC provider's Step 09 must complete first) or soft.
- Tier the Step 09 executions; mark parallel-eligible groups; state
  the total execution count and the recommended order with rationale.

### Pass 7 — Invalidation Checks & Scorecard (→ §7, §8, §9)

- Run the Phase 3 and Phase 2 invalidation checks. Default "no";
  justify every answer in one line; route any "yes" to Step 12 §8 or
  §9 with a finding summary.
- Produce the per-artifact principle scorecard contribution under
  the inherited weights, citing specific mapping decisions.
- Write the handoff notes: what each downstream step consumes from
  this map, and any open questions carried forward.

---

## Output Format

Produce the artifact using this exact structure. Do not omit
sections.

```markdown
# Module Impact Map — Phase 4 (Architecture & Modular Design, Existing Projects)

**Project:** [subject name and version]
**Map Date:** [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]
**Design Specification Bundle Version:** [version + date; amendments noted]
**Improvement Plan Version:** [version]
**Stage 1 Inputs:** Step 02 [version/date]; Step 03 [v]; Step 04 [v];
Step 05 [v]; Step 06 [v]; Step 07 [v]
**Code-Access Mode (from Step 00):** [Interview-only / Search-primary / Hybrid]
**Status:** [Draft — Pending Practitioner Review / Approved]

> ⚠️ This map is the authoritative module manifest and strategic
> contract set for this Phase 4 run. It contains strategic-level
> contracts only — no field-level schemas (Step 09 details them; Step
> 11 formalizes them) and no implementation content (Phase 5).

---

## §1 — Module Manifest (Authoritative)

[Every module in the Step 02 baseline appears exactly once. M-NN IDs
are stable from Step 02 where confirmed; new IDs continue the series.]

| M-NN | Module | Path | Disposition | Owner (GOV-NN) | Source Briefs (Brief ID / MC-NN) | Notes |
|------|--------|------|-------------|----------------|----------------------------------|-------|
| M-01 | [name] | [repo-relative path] | [NEW / CHANGED / UNTOUCHED / RETIRED] | GOV-NN | [Brief ID / MC-NN — "—" for UNTOUCHED] | [split/merge pairing; Step 02 revision note] |
| M-02 | | | | | | |

### §1.1 — Manifest Deltas from Step 02

| M-NN | Step 02 Preliminary Row | Change Made Here | Reason |
|------|------------------------|------------------|--------|
| | | [confirmed / renamed / re-scoped / split / merged / added / dropped] | |

### §1.2 — Disposition Summary

| Disposition | Count | Modules (M-NN) |
|-------------|------:|----------------|
| NEW | | |
| CHANGED | | |
| UNTOUCHED | | |
| RETIRED | | |

**Step 09 execution count (NEW + CHANGED):** [N]

---

## §2 — Brief-to-Module Coverage Check

### §2.1 — Forward: Every Design Specification Lands

| Brief ID | Source MC(s) | Artifact Type | Lands In (M-NN, NEW/CHANGED) | Coverage Status |
|----------|--------------|---------------|------------------------------|-----------------|
| | | [Contract / Refactor / IA / Schema / Observability / Verification / Other] | | [Covered / ORPHANED] |

### §2.2 — Reverse: Every Module Change Has a Source

| M-NN (NEW / CHANGED / RETIRED) | Source Briefs (Brief ID / MC-NN) | Status |
|--------------------------------|----------------------------------|--------|
| | | [Sourced / UNEXPLAINED] |

### §2.3 — Anomalies and Resolutions

| # | Anomaly | Type | Resolution / Routing |
|---|---------|------|----------------------|
| | | [Orphaned brief / Unexplained module change] | [Cut as scope creep / Channel 1 gap / Channel 2 finding → §7 / Accepted with practitioner note] |

[If none: "No anomalies — coverage passes in both directions."]

---

## §3 — Boundary Decisions

[One record per integration decision the mapping forced. Repeat the
subsection per decision.]

### §3.N — [Decision title, e.g., "Home module for the strategy contract"]

| Field | Value |
|-------|-------|
| Question | [e.g., where does the contract live / does the refactor move a seam / which module emits the schema] |
| Options considered | |
| Decision | |
| Rejected alternative(s) | [each with why it was rejected] |
| Rationale | [cite Step 02 baseline evidence, SP-NN, Phase 3 spec §] |
| Affected modules | M-NN, M-NN |
| Affected contracts | SIC-NN |

---

## §4 — Strategic Interface Contracts (SIC-NN)

[One SIC per NEW/CHANGED boundary. Strategic level only.]

| SIC-NN | Boundary (M-NN ↔ M-NN or external) | Operations | Conceptual Types | Error Conditions | Strategic Security (SEC-NN / TB-NN) | Derived From (Phase 3 spec §) |
|--------|-------------------------------------|------------|------------------|------------------|--------------------------------------|-------------------------------|
| SIC-01 | | [conceptual operation names] | [conceptual types — not field schemas] | [which errors can occur] | | [spec § — or Step 02 §3 citation if bundle-silent] |

### §4.1 — SIC Notes

[Per-SIC amplification where a single row is too dense: operation
semantics, lifecycle expectations, versioning posture. Still
strategic — no field-level content.]

### §4.2 — Frozen References (UNTOUCHED Boundaries)

[UNTOUCHED-module interfaces the change set consumes. Recorded, not
re-contracted.]

| Boundary | Modules (M-NN) | Interface (as-is, cited from Step 02 §3) | Consumed By |
|----------|----------------|-------------------------------------------|-------------|
| | | | M-NN |

---

## §5 — Per-Module Constraint Assignments

[Repeat for every NEW/CHANGED module.]

### §5.N — M-NN — [Module Name]

| Constraint Category | Assignments This Module Must Honor |
|---------------------|-------------------------------------|
| Shared patterns (SP-NN) | |
| Security controls (SEC-NN) at boundaries (TB-NN) | |
| Data constraints (DA-NN) | |
| Documentation types (DOC-NN) | |
| Governance owner + review gate (GOV-NN) | |
| Observability touchpoints emitted (Phase 3 touchpoint inventory) | |
| Coordination constraints (Bundle §2 — cohorts, ordering, shared decisions) | |

[Empty categories: "None applicable — [reason]".]

---

## §6 — Inter-Module Dependencies & Step 09 Sequencing

### §6.1 — Dependency Graph

| From (M-NN) | To (M-NN) | Dependency | Via Contract | Strict / Soft |
|-------------|-----------|------------|--------------|---------------|
| | | [consumes / provides to / coordinates with] | SIC-NN [or frozen reference] | |

[Render the graph (ASCII or Mermaid per Step 00 §4). Flag any cycles
— a cycle among NEW/CHANGED modules is a design smell to resolve or
escalate before Step 09 begins.]

### §6.2 — Step 09 Execution Plan

| Tier | Modules (M-NN) | Parallel-Eligible? | Rationale |
|------|----------------|--------------------|-----------|
| 1 | | | [e.g., SIC providers first, so dependents specify against settled contracts] |

**Total Step 09 executions:** [N — must equal §1.2 NEW + CHANGED]
**Recommended order:** [statement + rationale; practitioner may
serialize parallel-eligible groups by session capacity]

---

## §7 — Phase 3 / Phase 2 Invalidation Checks

| Check | Answer | If Yes — Finding + Routing |
|-------|--------|----------------------------|
| Does any Phase 3 design specification fail to be assigned a coherent module boundary? | [No (default) / Yes] | [→ Step 12 §8 Phase 3 Amendment Package] |
| Does the mapping contradict a Bundle §2 coordination commitment (cohort, ordering, shared decision)? | [No / Yes] | [→ Step 12 §8] |
| Is any Phase 2 mechanism (MC-NN) untenable at module level regardless of re-specification? | [No / Yes] | [→ Step 12 §9 Phase 2 Amendment Package] |
| Does the manifest's implied footprint visibly breach the Phase 2 capacity envelope (HC-NN)? | [No / Yes] | [→ Step 12 §9; Step 09 estimates will refine] |

[One-line justification per answer. A "yes" is a routed finding, not
a workaround — Phase 4 continues on unaffected modules where safe.]

---

## §8 — Per-Artifact Principle Scorecard Contribution

[Under the inherited Phase 2 weights. Cite specific mapping decisions
in each rationale.]

| Principle | Weight (inherited) | Contribution | Rationale |
|-----------|-------------------:|--------------|-----------|
| Security | | [PASS / CONDITIONAL / FAIL] | |
| Maintainability | | | |
| Economics | | | |
| Operations | | | |
| Scoring & Metrics | | | |
| Correctness Verification | | | |

[Any CONDITIONAL names its remediation and where it lands (typically
a Step 09 obligation). Any FAIL blocks — return to the responsible
pass before finalizing.]

---

## §9 — Handoff Notes

- **To Step 09:** [one execution per NEW/CHANGED module; each
  consumes its §1 manifest row, its SIC-NN contracts, and its §5
  constraint assignment; sequencing per §6.2]
- **To Step 10:** [verify Step 09 §2 interfaces conform to §4
  SIC-NN; re-verify the §2 coverage check against the produced set]
- **To Step 11:** [every SIC-NN is formalized by a protocol
  sub-template or its exemption is justified in Step 02 §3; §4
  derivation citations seed the Step 11 traceability]
- **To Step 12:** [§7 findings; §8 contribution; anomaly log]
- **Open questions carried forward:** [list, with the step expected
  to resolve each — or "None"]

---

## Version

| Version | Date | Trigger | Changes | Approved By |
|---------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline Module Impact Map | |
```

---

## Evaluation Checklist

Before this artifact is accepted as complete, verify all items:

- [ ] Every module in the Step 02 baseline appears in the §1 manifest
      exactly once, with exactly one disposition (NEW / CHANGED /
      UNTOUCHED / RETIRED) and exactly one owner (GOV-NN)
- [ ] Every revision to the Step 02 preliminary inventory is recorded
      in §1.1 with a reason; confirmed M-NN IDs are unchanged
- [ ] Every split or merge is expressed as a RETIRED+NEW pair with
      cross-referencing notes in both rows
- [ ] The coverage check passes in both directions: every Bundle §1
      design specification lands in at least one NEW/CHANGED module
      (§2.1), and every NEW/CHANGED/RETIRED module cites its source
      briefs (§2.2); every anomaly is resolved or routed (§2.3)
- [ ] Every boundary decision (§3) records options, rejected
      alternatives with reasons, and rationale citing Step 02
      evidence, SP-NN, and the constraining Phase 3 specification
- [ ] Every NEW/CHANGED boundary has a SIC-NN (§4) with operations,
      conceptual types, error conditions, strategic security
      (SEC-NN / TB-NN), and a derivation citation (Phase 3 spec § or
      Step 02 §3 for bundle-silent boundaries)
- [ ] SIC content is strategic-level — no field-level schemas, typed
      fields, or exhaustive error payloads (those are Step 09)
- [ ] UNTOUCHED-module interfaces consumed by the change set are
      recorded as frozen references (§4.2), not re-contracted
- [ ] Every NEW/CHANGED module has a complete §5 constraint
      assignment — SP/SEC/TB/DA/DOC/GOV IDs, emitted observability
      touchpoints, and Bundle §2 coordination constraints — with
      empty categories justified, never omitted
- [ ] §6 declares the dependency graph (with SIC-NN routing and
      strict/soft marking), the Step 09 tiers and parallel-eligible
      groups, and an execution count that equals §1.2 NEW + CHANGED
- [ ] The §7 Phase 3 / Phase 2 invalidation checks are answered with
      justification; any "yes" is routed to Step 12 §8/§9 as a
      finding, not worked around
- [ ] §8 carries the per-artifact scorecard contribution under the
      inherited weights, with decision-citing rationale; any
      CONDITIONAL names its remediation
- [ ] No implementation content — no function bodies, migration
      scripts, CI configuration, or credential material; and no Step
      09-level detail (field-level schemas, test strategies,
      migration implications)
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)

---

*Part of the Phase 4 (Existing Projects) Architecture & Modular Design Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `architecture-modular-design.existing-project.instructions.md`*
*Previous step: `step-07-governance-model.prompt.md`*
*Next step: `step-09-module-change-specification.prompt.md` (runs once per NEW/CHANGED module in the §1 manifest)*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Module Impact Map prompt — the Stage 2 gateway for the existing-projects track. Adapts the greenfield Step 07 module-enumeration disciplines (manifest, SIC-NN strategic contracts, per-module constraint assignment, coverage check, sequencing plan) to brownfield: the manifest finalizes the Step 02 preliminary M-NN inventory with dispositions (NEW/CHANGED/UNTOUCHED/RETIRED; splits and merges as RETIRED+NEW pairs) and GOV-NN owners, and the SIC-NN are derived from the Phase 3 design specifications with per-row derivation citations rather than invented. Adds the bidirectional brief-to-module coverage check (no orphaned briefs; no unexplained module changes), boundary-decision records with rejected alternatives, frozen references for UNTOUCHED interfaces, coordination-constraint assignment from Bundle §2, and the Phase 3 / Phase 2 invalidation checks routing to Step 12 §8/§9. Clarification step (3–7 questions, presence check first) and per-artifact scorecard contribution per the track's house pattern. |
