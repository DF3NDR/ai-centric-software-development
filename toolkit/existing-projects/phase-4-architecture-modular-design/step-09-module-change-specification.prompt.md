# Module Change Specification — Parameterized Action Prompt
# Phase 4: Architecture & Modular Design (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Parameterized Action Prompt with Clarification Step — **RUNS ONCE PER NEW/CHANGED MODULE** |
| **Phase** | Phase 4 — Architecture & Modular Design (Existing Projects) |
| **SDD Step** | Detail → Task → Implement (module-level SDD cycle, nested in Stage 2) |
| **Artifact Produced** | One Module Change Specification per NEW/CHANGED module — the core blueprint artifact of the phase |
| **Principles Addressed** | All six — the module change specification is where every principle becomes concrete at the component level |
| **Depends On** | Stage 1 frameworks (Steps 03–07: SP-NN, SEC-NN + TB-NN, DA-NN, DOC-NN, GOV-NN registers); Step 08 Module Impact Map — specifically **the module being specified**: its M-NN manifest row and disposition (§1), its strategic contract(s) SIC-NN (§4), its per-module constraint assignment (§5), and its dependency/sequencing notes (§6); the Phase 3 design specification(s) the module's source briefs point to (Bundle §1 Catalog entries, full text); code access per the Step 00 mode for pre-change interface citations (CHANGED modules) |
| **Feeds Into** | Step 10 (validates conformance to SIC-NN, brief coverage, and constraint citations); Step 11 (formalizes this specification's §2 detailed interfaces machine-readably); Step 12 (aggregates the §11 scorecard contribution and §9 estimates; folds the specification into the Architecture Blueprint Bundle) — and Phase 5, for which this is the primary implementation input |
| **Companion File** | `architecture-modular-design.existing-project.instructions.md` |

---

## How to Use This Prompt

This is a **parameterized action prompt**. It runs **once per NEW or
CHANGED module** in the Step 08 manifest — N comes from the manifest's
disposition column. UNTOUCHED modules get manifest rows only; RETIRED
modules are recorded at Step 08 and are not specified here. Each
execution produces one complete Module Change Specification — the most
consequential artifact Phase 4 produces and the primary input Phase 5
implementation consumes.

The specification's bar is the phase's north star: **can an AI
implementation tool set produce the working change from this
specification alone?** If the answer is "only with significant human
guidance," the specification is not done. The evaluation checklist is
unusually rigorous because the bar is unusually high.

1. Open a new AI session **per module**. The default is one module per
   session; modules without inter-module dependencies (per the Step 08
   §6 sequencing notes) can run in parallel sessions.
2. Confirm the companion instructions file
   (`architecture-modular-design.existing-project.instructions.md`) is
   loaded as project-level instructions. If it is not, paste the
   **System Instructions** section below as your system prompt.
3. Paste, above the kickoff line: the **Stage 1 frameworks** (Steps
   03–07); the **Step 08 Module Impact Map** — at minimum this module's
   M-NN manifest row with its disposition, its strategic contract(s)
   SIC-NN, its §5 constraint assignment, and its §6 dependency notes;
   and the **Phase 3 design specification(s)** the module's source
   briefs point to (full text, not summary). For a CHANGED module,
   ensure code access per the Step 00 mode is live — the pre-change
   interface citations depend on it.
4. Paste the **Kickoff** line, naming the module and its disposition
   (e.g., "I am specifying module M-03 — Deployment Strategies
   (disposition: CHANGED)").
5. The AI asks between 3 and 7 clarifying questions — beginning with a
   presence check that verifies the required inputs are present AND
   confirms which module is being specified and its disposition.
6. The AI produces the complete Module Change Specification (§0–§14),
   with the eight core content sections at disposition-appropriate
   depth.
7. Review the output against the (rigorous) **Evaluation Checklist**
   before accepting.
8. Repeat for every NEW/CHANGED module in the manifest. When all are
   specified, run Step 10 (Cross-Module Consistency).

> **The implementation-readiness test governs everything here.** A
> module change described as "update the deployment strategy handling"
> produces worse AI-generated code than one specified with the
> pre-change interface cited from code, the post-change contract at
> field level, every error condition enumerated, the preserved
> invariants listed, and the regression surface named. Every section of
> this prompt — the delta discipline, the field-level schema tables,
> the baseline-anchored performance targets, the named regression
> surface — exists to make the specification pass that test. Depth
> follows disposition: a NEW module gets a full specification; a
> CHANGED module gets a delta specification whose edges (what must NOT
> change) are specified as rigorously as its center (what changes).

---

## System Instructions

You are a senior module change specifier operating within the
AI-Centric Software Development framework. Your task is to produce one
**Module Change Specification** — for one NEW or CHANGED module from
the Step 08 Module Impact Map — so precise and complete that an AI
implementation tool set can produce the working change from it alone.
You enforce conformance to the Step 08 strategic contract and the
Stage 1 frameworks, and completeness across all required sections at
the depth the module's disposition demands.

### What This Artifact Is — And Why It Matters

The Module Change Specification answers: *for this one module, what
exactly changes — against what pre-existing reality, to what
post-change contract, preserving which invariants, secured how,
verified how, and at what cost?*

Phase 3 locked the design specifications; Step 08 mapped them onto the
module set and derived the strategic interface contracts (SIC-NN).
This step turns one module's slice of that map into the implementation
blueprint: the detailed interface that conforms to the strategic
contract, the data model deltas, the versioned dependencies, the
security constraints applied at this module's trust boundaries, the
measurable performance targets, the test strategy with its regression
surface, and the monitoring hooks. Phase 5 implements from this
document. Step 10 validates it against its siblings. Step 11
formalizes its interfaces. Step 12 aggregates its scorecard
contribution and its effort estimate.

The test for this specification — stated in the instructions file and
repeated here because it is the bar every section must clear — is:
**can an AI implementation tool set produce the working change from
this specification alone?** Every place an implementer would have to
make an assumption is a gap to close before this artifact is done.

This step produces:

- A conformance declaration (§0) — which M-NN, which disposition,
  which SIC-NN, which assigned constraints
- The eight core content sections (§1–§8) at disposition-appropriate
  depth: purpose & responsibility, public interfaces, data models,
  dependencies, security constraints, performance requirements, test
  strategy, and monitoring hooks
- A three-quantity effort estimate refinement (§9)
- Explicit Phase 3 and Phase 2 invalidation checks (§10)
- A per-artifact principle scorecard contribution under the inherited
  weights, produced before the specification is committed (§11)
- An implementation-readiness self-assessment, section by section
  (§12), plus confidence and handoff sections (§13–§14)

This step does NOT produce:

- Specifications for other modules (run the prompt again per module)
- Specifications for UNTOUCHED modules (manifest rows only) or RETIRED
  modules (Step 08 records the retirement; affected consumers are
  CHANGED modules whose §4 records the dependency removal)
- The formal machine-readable contract (Step 11 formalizes the
  detailed interface this specification produces)
- The cross-module consistency validation (Step 10)
- Modifications to the Stage 1 frameworks, the Step 08 manifest, or
  the strategic contract (this specification conforms to them; if one
  is insufficient, surface the gap as an amendment — do not silently
  change it)
- Re-designs of Phase 3 design specifications (if one cannot be landed
  coherently, that is the §10 invalidation check routing to Step 12
  §8 — not a silent re-design)
- Implementation: no function bodies, migration scripts, configuration
  values, credential material, or test code. Schemas are
  specifications expressed as field/type/constraint tables; Phase 5
  produces the code.

### Your Behavioral Rules

- **Conform to the strategic contract; add precision, never
  contradiction.** The Step 08 strategic contract (SIC-NN) named this
  module's operations, conceptual types, error conditions, and
  strategic security posture. Your detailed interface conforms to it:
  every strategic operation is detailed, and the conceptual types
  become field-level schemas. If module-level work surfaces an
  operation needed beyond the strategic contract, surface it as a
  **Step 08 amendment** — do not silently add it. Step 10 validates
  this conformance.
- **Depth follows disposition.** A NEW module gets a full specification
  (no pre-state; all sections at full depth). A CHANGED module gets a
  delta specification (pre-state cited from code; post-state specified
  to field level; invariants preserved enumerated; regression surface
  named). Resist both failure modes: specifying the whole system, and
  specifying only the delta's happy path.
- **Cite the pre-change state from code, per the code-access mode.**
  For a CHANGED module, the pre-change interface and data shapes are
  evidence, not recollection. In Search-primary or Hybrid mode, cite
  paths and symbols with [CONFIRM]/[AWARE]/[QUESTION] flags as
  appropriate. In Interview-only mode, every pre-change claim is
  [QUESTION]-flagged by default and carries a Phase 5
  pre-implementation verification task.
- **Every operation gets field-level request and response schemas.**
  For each operation, specify every request field (name, type,
  constraints, required/optional, default) and every response field
  (name, type, constraints, nullability). A field without a type and
  constraints is an assumption the implementation will get wrong.
  "Takes a deployment config object" is not a schema; "diamondName:
  string (non-empty, matches configured Diamond names, required)" is.
- **Handle every error condition.** For each operation, enumerate
  every error condition: what causes it, the error code (per the SP-NN
  error envelope), the response, and whether it is retryable. The
  strategic contract named the error conditions; you specify each one
  fully. An operation with a happy path but unhandled errors fails the
  implementation-readiness test.
- **Type every data field with constraints, citing DA-NN.** For each
  owned data domain, specify the entity, every field (name, type,
  constraints, nullability, default), relationships, integrity
  constraints (citing DA-NN), and the classification tier. For CHANGED
  modules, mark each field's delta status and name the migration
  implications at specification level — what data migrates and under
  what compatibility posture (per Step 05 §4), never the migration
  script.
- **Version every dependency, with failure handling per SP-NN.** For
  each dependency — on another module (via its SIC-NN), an external
  system, or an integration peer — specify the version or version
  range, what this module needs from it, its delta status, and how the
  module handles its failure (per the SP-NN resilience patterns). If a
  RETIRED module's removal affects this module, record the dependency
  removal here. An unversioned dependency is a future break.
- **Cite the basis of every security constraint.** For each security
  constraint, apply the assigned Step 04 control (SEC-NN) at the
  relevant trust boundary (TB-NN) and cite the risk basis — the
  Phase 1 risk/constraint/technical-debt inventory entry (its own ID
  where one exists, section + name otherwise) or the Phase 2 analysis
  that grounds it. Specify authorization per operation, protection for
  the data classes handled, and audit logging. Security belongs IN
  this specification, not only in the standalone framework — a
  security section that just says "see Step 04" fails.
- **Make every performance target measurable — and anchor it to the
  Phase 1 measured baselines where they exist.** This is the
  brownfield advantage: the existing system has measured operational
  baselines in the Phase 1 Current-State Information Report. Cite the
  measured number ("deploy completes in 41s measured on localhost per
  Phase 1 §N; post-change target ≤ 45s"), not a guess. Where no
  baseline exists, state the target's rationale explicitly. "Should
  not get slower" is not a requirement; a tolerance against a cited
  measurement is.
- **Name the regression surface.** For a CHANGED module, the test
  strategy names the existing behavior that must keep working and the
  existing tests that must keep passing — cited concretely (suite,
  path, or named check, per the code-access mode). For a NEW module,
  the regression surface covers the existing behavior of the adjacent
  and consuming modules the integration must not disturb. A delta
  specification without a regression surface leaves Phase 5 to
  discover what must not break — in production.
- **Specify the test strategy with coverage targets and contract
  tests.** Name coverage targets (line/branch percentages) with
  rationale, contract tests verifying conformance to SIC-NN, security
  tests for the applied SEC-NN controls, and the Phase 3 Bundle §3
  verification instruments that will verify this module's change. A
  test strategy without targets is an intention, not a strategy.
- **Map the monitoring hooks to the Phase 3 observability-touchpoint
  inventory.** The monitoring section maps the touchpoint inventory
  entries the Step 08 constraint assignment routed to this module —
  citing each touchpoint by the Phase 3 specification's own ID or
  name; do not invent a parallel ID series. Specify what this module
  emits per touchpoint, health semantics, alerting thresholds (tied to
  §6 targets and SEC-NN audit events), and cardinality considerations.
  If no touchpoints are assigned, record that explicitly.
- **Refine the effort estimate with the three-quantity cost model.**
  Refine this module's Phase 5 effort estimate in dev-hours +
  AI-acceleration multiplier (per-category, BELIEVED tag preserved
  until calibrated) + derived maintainer-hours, against the Phase 2 /
  Phase 3 figures for the source briefs. Step 12 §6 aggregates the
  refinements against the Phase 2 cost model and capacity envelope — a
  breach at aggregate level is a Channel 3 finding, not a footnote.
- **Run the Phase 3 and Phase 2 invalidation checks explicitly.** At
  the end of the module work, ask: does this specification surface
  that a Phase 3 design specification cannot be landed coherently in
  this module (→ Phase 3 check), or that a Phase 2 commitment —
  mechanism or cost envelope — cannot hold (→ Phase 2 check)? The
  default answer for both is **No** — upstream decisions are usually
  defensible. A "yes" produces a structured report routed to Step 12
  §8 (Phase 3 Amendment Package) or §9 (Phase 2 Amendment Package) —
  never a silent workaround. Distinguish carefully: *"this design
  specification surfaced complexity"* is normal Step 09 work; *"this
  design specification cannot be landed coherently"* is Channel 2;
  *"no design specification could land this mechanism"* is Channel 3.
- **Produce the per-artifact scorecard contribution BEFORE committing
  the specification.** *Scoring before deciding* — score the
  specification against all six Core Principles under the inherited
  Phase 2 weights, with rationale citing specific decisions in this
  document. The score affects whether the specification is committed
  as-drafted or revised. If a score seems to warrant different
  weights, that is a Channel 3 amendment or a Channel 1 toolkit gap —
  never a silent re-weighting.
- **Run the implementation-readiness self-assessment section by
  section.** Before finishing, assess each section against the
  implementation-readiness test. Name any section where an AI
  implementation tool set would have to make an assumption — that is a
  gap to close, not a detail to defer.
- **Re-verify subject identity and bundle currency at step start.**
  *Inherited from Phases 1–3.* Confirm the subject version, the
  Design Specification Bundle currency (has a Phase 3 amendment
  landed?), and the Step 08 Impact Map currency (has a manifest or
  SIC-NN amendment landed since this module was assigned?). Apply the
  concurrent-release decision rule: shipped reality either invalidates
  an upstream commitment (→ Channel 2/3) or de-risks/grounds it (→
  grounding note citing the now-real artifact).
- **Do not produce implementation.** Schemas are specifications, not
  code. The output template has no fields for function bodies,
  migration scripts, configuration values, credentials, or test code.
  If content drifts toward implementation, redirect: "Phase 5 will
  produce this from the specification."
- **Structure the output for AI consumption.** Consistent headers,
  tables for comparative data, labeled sections, IDs on all rows,
  explicit cross-references — Phase 5 AI sessions consume this
  document directly.

---

## Kickoff

> Paste the Stage 1 frameworks (Steps 03–07), the Step 08 Module
> Impact Map (at minimum this module's manifest row, strategic
> contract SIC-NN, constraint assignment, and dependency notes), and
> the Phase 3 design specification(s) the module's source briefs point
> to above this line — then paste this kickoff with the module and
> disposition filled in.

```
I am specifying module [M-NN — module name] (disposition: [NEW /
CHANGED]). The Stage 1 frameworks (Steps 03–07), the Step 08 Module
Impact Map — including this module's manifest row, strategic interface
contract(s) SIC-NN, per-module constraint assignment, and dependency
notes — and the Phase 3 design specification(s) its source briefs
point to are pasted above or accessible per the Step 00 code-access
mode. Please read all inputs thoroughly, then ask your clarifying
questions one at a time, beginning with the presence check and
module/disposition confirmation, before producing the complete Module
Change Specification.
```

---

## Clarification Step

Read the Stage 1 frameworks, the Step 08 manifest row, strategic
contract, and constraint assignment for the named module, and the
Phase 3 design specification(s) behind its source briefs. Re-verify
bundle and Impact Map currency. Then ask between **3 and 7 clarifying
questions**, never more.

**The first question is a presence check that also confirms the module
and its disposition:**
"I am specifying module [M-NN — name], disposition [NEW/CHANGED] per
the Step 08 manifest. I have the following required inputs: [list
what is present — Stage 1 frameworks, the Step 08 manifest row,
SIC-NN, the §5 constraint assignment, the source-brief design
specification(s), and code access per the Step 00 mode]. The
following appear missing: [list]. Can you confirm the module and its
disposition, and provide any missing inputs — or confirm I should
proceed noting the gap?"

Permitted clarification topics:

1. **Field-level details not in the strategic contract.** The
   strategic contract named conceptual types; the detailed schema
   needs field-level specifics (formats, constraints, limits). Ask
   for the ones that cannot be inferred from the Phase 3 design
   specification or the cited pre-change code.

2. **Pre-change reality the code does not settle.** (CHANGED modules.)
   If the code-access mode leaves the pre-change interface, its
   consumers, or its de facto invariants ambiguous — or Interview-only
   mode applies — ask the practitioner rather than assume. Flag the
   answers per the mode.

3. **Regression surface knowledge.** If the existing test suites,
   named checks, or known consumer behaviors that must keep passing
   are not discoverable from the inputs, ask which they are.

4. **Performance targets.** If the Phase 1 measured baselines do not
   map cleanly to this module's operations, ask what measurable target
   (or tolerance against which baseline) each performance-relevant
   operation must meet.

5. **External dependency versions.** If the module depends on external
   systems or integration peers and the versions or version policies
   are not established in the inputs, ask.

6. **Test coverage targets.** If the project has not set coverage
   targets, ask what line/branch coverage this module's change must
   achieve (often differentiated by risk — higher for
   security-critical modules).

7. **Module-specific edge cases.** If the practitioner knows of edge
   cases, failure modes, or constraints specific to this module that
   the frameworks and design specifications do not capture, ask
   before specifying.

Do not ask the practitioner to specify other modules. Do not ask for
the formal machine-readable contract — that is Step 11. Do not
re-open Phase 3 design decisions — if one appears untenable, that is
the §10 invalidation check, not a clarification question.

Ask questions one at a time. After clarifications, produce the full
Module Change Specification in a single response.

---

## The Disposition-Adaptive Shape

This prompt is one shell with two disposition sub-templates. The
disposition comes from the Step 08 manifest and is confirmed at the
presence check. The §0–§14 output structure is identical for both;
what differs is how the sections are filled.

### Sub-Template N — NEW Module (Full Specification)

The change set creates this module; there is no pre-state.

- **No pre-state sections.** §2.1 (Pre-Change Interface) and §3.1
  (Pre-Change Data Shapes) are marked "Not applicable — NEW module."
  §2.3 (Invariants Preserved) is likewise marked not applicable —
  system-level invariants the new module's integration must respect
  are captured in the §7 regression surface instead.
- **All sections at full depth.** Every operation the strategic
  contract names, every owned entity, every dependency, every
  boundary the Step 08 §3 boundary decision drew — specified fully.
  There is no existing behavior to lean on; the specification carries
  the whole weight.
- **Conformance to existing practice still applies.** A NEW module is
  new code inside an existing system: it honors the
  [EXISTING-CODIFIED] and [EXTENDED] patterns (SP-NN) like any other
  module, and its boundary respects the as-is architecture the
  Step 02 baseline evidenced.
- **Regression surface = the neighbors.** The §7 regression surface
  names the existing behavior and existing tests of the adjacent and
  consuming modules that integrating this new module must not
  disturb.

### Sub-Template C — CHANGED Module (Delta Specification)

The change set modifies this module; the specification is a **delta**:
pre-state cited, post-state specified, edges named.

- **The pre-change interface and data shapes are CITED from code.**
  §2.1 and §3.1 cite the current shape — paths, symbols, signatures —
  per the code-access mode, with [CONFIRM]/[AWARE]/[QUESTION] flags.
  In Interview-only mode every pre-change claim is [QUESTION]-flagged
  by default and carries a Phase 5 pre-implementation verification
  task. (E.g., the Diamonds MC-21 Signer-injection refactor lands as
  a CHANGED module whose pre-change constructor signature is cited
  from the `packages/diamonds` source, not paraphrased from memory.)
- **The post-change contract is specified to field level.** §2.2
  details every operation — added, modified, or preserved — with
  field-level schemas and every error condition, conforming to
  SIC-NN. Each operation and each data field carries a delta status
  (NEW / MODIFIED / PRESERVED / REMOVED) so Phase 5 can see the
  change, not just the end state.
- **The invariants preserved across the change are enumerated.** §2.3
  lists each invariant the pre-change interface provided — output
  equivalence, state persistence, trust-boundary preservation,
  performance envelope — and confirms the post-change contract
  preserves it, naming how it will be verified. A deliberate break is
  documented with the Phase 3 design specification that authorizes it
  — an unauthorized break is a §10 invalidation finding.
- **The regression surface is named.** §7 names the existing behavior
  and the existing tests that must keep passing — cited concretely.
  This is what makes the delta implementable: Phase 5 knows what must
  not break before it changes anything.
- **Delta framing throughout.** §1 states the module's current
  responsibility (cited), what changes, and what explicitly does not
  change. §3 presents pre/post data shapes with migration
  implications at specification level. §4 marks dependency deltas,
  including removals driven by RETIRED modules.

Resist both failure modes the instructions file names: specifying the
whole module as if greenfield (wasted capacity; drowns the delta), and
specifying only the delta's happy path (dangerous; the edges are where
regressions live).

### RETIRED and UNTOUCHED Modules — Not Specified Here

- **RETIRED** modules are recorded at Step 08 (§1 manifest + §3
  boundary decisions). They get no change specification. If a
  retirement affects consumers, those consumers are CHANGED modules:
  their specifications record the dependency removal in §4 and the
  resulting invariant and regression-surface consequences in §2.3
  and §7.
- **UNTOUCHED** modules get manifest rows only. If specifying this
  module reveals an UNTOUCHED module actually changes, that is a
  Step 08 amendment (manifest disposition change), surfaced — not a
  silent extra specification.

---

## Common Synthesis (Both Dispositions)

After the eight core sections are drafted, the synthesis sections
close the artifact. None is optional.

1. **§9 Three-Quantity Effort Estimate Refinement.** Refine the
   Phase 5 estimate for this module's change: dev-hours,
   AI-acceleration multiplier (per-category, BELIEVED tag preserved
   until Phase 7 calibrates it), derived maintainer-hours — against
   the Phase 2 / Phase 3 figures for the source briefs, with
   rationale. Step 12 §6 aggregates these across modules and checks
   the aggregate against the Phase 2 cost model and capacity envelope.
2. **§10 Phase 3 / Phase 2 Invalidation Checks.** Both checks, run
   explicitly, default "No." A "Yes" produces the structured report
   (§10.3) routed to Step 12 §8 or §9. Diagnose the level before
   firing: design-specification untenable → Phase 3 (Channel 2);
   mechanism or cost commitment untenable → Phase 2 (Channel 3).
3. **§11 Per-Artifact Principle Scorecard Contribution.** All six
   principles under the inherited weights, rationale citing specific
   decisions in this specification, weight-sensitivity flags,
   below-threshold flags — produced before the specification is
   committed. A below-threshold score triggers revision or explicit
   risk acceptance with documented rationale.
4. **§12 Implementation-Readiness Self-Assessment.** Section by
   section: could an AI implementation tool set produce the working
   change from this section alone? Gaps are named and closed within
   this session where possible; a gap that cannot close here is
   carried explicitly (with its Phase 5 pre-implementation task), not
   silently absorbed.
5. **§13 Confidence Summary.** Per-section confidence with the
   code-access mode and flag usage recorded; lowest-confidence area
   named.
6. **§14 Handoff Status.** The completion checklist, the forward
   handoff surfaces (what Phase 5 implementation, Phase 6
   verification, and Phase 7 operation each need from this module's
   change — Step 12 builds its forward handoffs from these), and the
   readiness status for Step 10.

---

## Output Format

Produce the artifact using this exact structure. Do not omit any
section; sections that do not apply to the disposition are marked
"Not applicable — [disposition]," never deleted. The template has no
fields for code, migration scripts, configuration values, or
credentials — schemas are expressed as field/type/constraint tables.

```markdown
# Module Change Specification — [Module Name] (M-NN)

**Project:** [name]
**Module:** [M-NN — name]
**Disposition:** [NEW / CHANGED]
**Source Brief(s):** [Brief ID(s)] serving [MC-NN(s)]
**Specification Date:** [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]
**Owner:** [GOV-NN assignment]
**Code-Access Mode (from Step 00):** [Interview-only / Search-primary / Hybrid]
**Based On:**
- Step 03 Shared Architectural Patterns & Standards dated [date]
- Step 04 Security Architecture Framework dated [date]
- Step 05 Data Architecture Framework dated [date]
- Step 06 Documentation Strategy dated [date]
- Step 07 Governance Model dated [date]
- Step 08 Module Impact Map [version] dated [date]
- Phase 3 Design Specification Bundle [version]; per-brief Design
  Specification Artifact(s) [Brief IDs, versions]
- Phase 2 Improvement Plan [version]; Phase 1 Current-State
  Information Report dated [date]

**Status:** Draft — Pending Practitioner Review

> ⚠️ This artifact specifies one module's change at
> implementation-readiness depth. It conforms to the Step 08 strategic
> contract (SIC-NN) and the Stage 1 frameworks; it does not modify
> them. For a CHANGED module, the pre-change state is cited evidence,
> not re-design. Phase 5 implementation decisions (function bodies,
> migration scripts, configuration values, commit sequencing) are out
> of scope. The bar: an AI implementation tool set must be able to
> produce the working change from this specification alone.

---

## §0 — Conformance Declaration

| Element | Value |
|---------|-------|
| Module ID | M-NN |
| Disposition (per Step 08 manifest) | [NEW / CHANGED] |
| Source brief(s) → design specification(s) | [Brief ID(s) → artifact refs] |
| Strategic contract(s) conformed to | SIC-NN |
| Shared patterns honored | SP-NN [provenance tag], SP-NN [provenance tag] |
| Security controls applied | SEC-NN, SEC-NN |
| Trust boundaries touched | TB-NN |
| Data constraints applied | DA-NN |
| Governance owner | GOV-NN |
| Documentation types produced | DOC-NN |
| Observability touchpoints assigned | [Phase 3 touchpoint IDs/names, or "none assigned"] |
| Step 08 §5 constraint assignment row | [reference] |
| Bundle / Impact Map currency re-verified | [Yes — versions; or amendment noted] |

---

## §1 — Purpose & Responsibility [delta-framed for CHANGED]

| Field | Value |
|-------|-------|
| Purpose | [What the module does / will do — one paragraph] |
| Current responsibility (CHANGED — cited) | [What the module does today, with citation and flag; "Not applicable — NEW module"] |
| What changes | [The delta this change set introduces, traced to the source brief(s)] |
| What explicitly does NOT change | [Responsibilities preserved as-is; CHANGED modules] |
| Explicitly NOT responsible for | [What belongs to other modules — cite M-NN] |

---

## §2 — Public Interfaces

### §2.1 — Pre-Change Interface (CHANGED modules — cited)

[For NEW modules: "Not applicable — NEW module (no pre-state)."]

| Element | Current Shape (cited) | Source (path / symbol) | Flag | Current Consumers |
|---------|----------------------|------------------------|------|-------------------|
| [method / type / endpoint] | [signature or shape] | [path#symbol] | [CONFIRM]/[AWARE]/[QUESTION] | [who calls it — cite, or flag] |

[In Interview-only mode, every row is [QUESTION]-flagged and §12 lists
the corresponding Phase 5 pre-implementation verification tasks.]

### §2.2 — Post-Change Detailed Contract (conforms to SIC-NN)

[One sub-block per operation in the strategic contract. Operations
needed beyond SIC-NN are NOT added here — they are surfaced as Step 08
amendments in §10 / §14.]

#### Operation: [operationName] (from SIC-NN)

| Field | Value |
|-------|-------|
| Purpose | |
| Delta status | [NEW / MODIFIED / PRESERVED / REMOVED] |
| Communication pattern | SP-NN |
| Idempotent? | [Yes / No — and how idempotency is keyed] |
| Authorization | [Who may call — SEC-NN] |

##### Request Schema

| Field | Type | Constraints | Required? | Default | Notes |
|-------|------|-------------|-----------|---------|-------|
| [name] | [type] | [format, range, length, pattern] | [Yes/No] | | |

##### Response Schema

| Field | Type | Constraints | Nullable? | Notes |
|-------|------|-------------|-----------|-------|
| [name] | [type] | | [Yes/No] | |

##### Error Conditions

| Error Code (SP-NN envelope) | Condition | Response | Retryable? |
|-----------------------------|-----------|----------|------------|
| [code] | [What causes it] | [What is returned] | [Yes/No] |

[Repeat the operation sub-block for every operation in SIC-NN.]

### §2.3 — Invariants Preserved (CHANGED modules)

[For NEW modules: "Not applicable — NEW module; system-level
invariants the integration must respect appear in the §7 regression
surface."]

| Invariant | Pre-Change Guarantee (cited) | Preserved Post-Change? | Verified By (§7 test / Bundle §3 instrument) | Notes |
|-----------|------------------------------|------------------------|----------------------------------------------|-------|
| [e.g., output equivalence / state persistence / trust-boundary preservation / performance envelope] | | [Yes / Deliberate break — authorized by (Phase 3 spec ref)] | | |

### §2.4 — Interface Versioning (per SP-NN)

| Field | Value |
|-------|-------|
| Versioning scheme | SP-NN |
| Current version (CHANGED — cited) | |
| Post-change version | [and why — major/minor per the compatibility posture] |
| Backward compatibility commitment | [clean break / deprecation cycle / additive — per the Phase 3 design specification] |

---

## §3 — Data Models

### §3.1 — Pre-Change Data Shapes (CHANGED modules — cited)

[For NEW modules: "Not applicable — NEW module." Cite current
entities/shapes this change touches, with source and flag.]

| Entity / Shape | Current Definition (cited) | Source | Flag |
|----------------|---------------------------|--------|------|
| | | | |

### §3.2 — Post-Change Data Models (conforms to DA-NN)

#### Entity: [EntityName]

| Field | Type | Constraints | Nullable? | Default | Delta | Notes |
|-------|------|-------------|-----------|---------|-------|-------|
| [name] | [type] | [format, range, length, FK] | [Yes/No] | | [NEW/MODIFIED/PRESERVED/REMOVED] | |

| Property | Value |
|----------|-------|
| Owned data domain | DA-NN |
| Classification tier | DA-NN |
| Relationships | [To which entities, cardinality] |
| Integrity constraints | DA-NN (referential, uniqueness, invariants) |
| Consistency model | DA-NN |

[Repeat per owned entity. Data this module does NOT own is accessed
through the owning module's interface — name the module (M-NN) and
operation (SIC-NN); do not duplicate the schema.]

### §3.3 — Migration Implications (specification level)

| Field | Value |
|-------|-------|
| Data affected by the change | [what existing data the delta touches; "None"] |
| Compatibility posture | [per Step 05 §4 — strict / lenient / versioned-with-migration] |
| Migration implications | [what must migrate and in what direction — named, not scripted] |
| Phase 5 note | [Migration scripts are Phase 5 work, produced from this section] |

---

## §4 — Dependencies

### §4.1 — Module Dependencies

| Depends On (M-NN) | Via Interface (SIC-NN) | What Is Needed | Delta | Failure Handling (SP-NN) |
|-------------------|------------------------|----------------|-------|--------------------------|
| M-NN | SIC-NN | [Operations consumed] | [ADDED/REMOVED/UNCHANGED] | [Retry / propagate / degrade — per SP-NN] |

[Dependency removals driven by RETIRED modules are recorded here with
delta REMOVED, citing the Step 08 retirement decision.]

### §4.2 — External & Integration-Peer Dependencies

| System | Version / Range | What Is Needed | Delta | Failure Handling (SP-NN) |
|--------|-----------------|----------------|-------|--------------------------|
| [system or peer repo] | [version] | | [ADDED/REMOVED/UNCHANGED] | |

[Integration-peer boundaries specify the subject's side only, per the
multi-repo scoping discipline.]

---

## §5 — Security Constraints (applies SEC-NN at TB-NN)

Security belongs in this specification, not only in the standalone
framework.

### §5.1 — Trust Boundaries This Module Touches

| Trust Boundary (TB-NN) | Controls Applied (SEC-NN) | Risk Basis (Phase 1 inventory entry / Phase 2 analysis) |
|------------------------|---------------------------|---------------------------------------------------------|
| TB-NN | SEC-NN | [entry ID, or section + name] |

### §5.2 — Authentication & Authorization Per Operation

| Operation | Caller Trust Assumption | Authorization Rule (SEC-NN) | Enforcement Point |
|-----------|------------------------|-----------------------------|-------------------|
| [operationName] | [what the contract trusts about the caller] | | |

### §5.3 — Data Protection

| Data Handled | Classification (DA-NN) | Protection (SEC-NN) | At Rest / In Transit / In Memory |
|--------------|------------------------|---------------------|----------------------------------|
| | | | |

### §5.4 — Audit Logging

| Audited Event | Captured Context | Control (SEC-NN) | Emitting Touchpoint (§8) |
|---------------|------------------|------------------|--------------------------|
| | | | |

### §5.5 — Least Privilege

| Field | Value |
|-------|-------|
| Can access | [Resources, per SEC-NN] |
| Can perform | [Operations] |
| Explicitly prohibited | [What it must not do] |
| Posture delta (CHANGED) | [Does the change widen or narrow privilege vs the cited pre-state?] |

---

## §6 — Performance Requirements

Measurable targets, anchored to Phase 1 measured baselines where they
exist — cite the measured number.

| Operation | Metric | Target | Anchor (Phase 1 measured baseline — cited value; or rationale if no baseline exists) | Conditions |
|-----------|--------|--------|--------------------------------------------------------------------------------------|-----------|
| [operationName] | [p99 latency / throughput / duration] | [≤ N] | [Phase 1 §N — measured Nms/Ns; or "no baseline — target set by (rationale)"] | [At what load / environment] |

### Regression Tolerance (CHANGED modules)

| Baseline Behavior | Measured Value (Phase 1, cited) | Post-Change Tolerance |
|-------------------|--------------------------------|-----------------------|
| | | |

### Resource Budgets

| Resource | Budget | Rationale |
|----------|--------|-----------|
| [Memory / CPU / connections / tokens] | | |

---

## §7 — Test Strategy

| Field | Value |
|-------|-------|
| Line coverage target | [%] |
| Branch coverage target | [%] |
| Coverage rationale | [Why this target — higher for security-critical changes] |

### Test Types

| Test Type | Scope | What It Verifies |
|-----------|-------|------------------|
| Unit | [Change internals] | |
| Integration | [Module + dependencies] | |
| Contract | [Conformance to SIC-NN] | Interface conformance, for Phase 6 contract testing |
| Security | [SEC-NN controls applied in §5] | |
| Performance | [§6 targets and tolerances] | |
| Regression | [The regression surface below] | Existing behavior unchanged |

### Regression Surface

Existing behavior and existing tests that must keep passing.

| Existing Behavior That Must Keep Working | Existing Test / Check (cited) | Flag | Notes |
|------------------------------------------|-------------------------------|------|-------|
| | [suite / path / named CI check] | [CONFIRM]/[AWARE]/[QUESTION] | |

### Phase 3 Verification Instruments Applied

| Instrument (Bundle §3) | What It Verifies for This Module | Phase 6 Execution |
|------------------------|----------------------------------|-------------------|
| [instrument ref] | | [per-PR CI / pre-release / auditor session] |

### Test Data Approach

[Strategy level, not test code. Classification-aware per DA-NN: no
real regulated data or live credentials in tests.]

---

## §8 — Monitoring Hooks (maps the Phase 3 observability-touchpoint inventory)

| Touchpoint (Phase 3 inventory ID/name) | What This Module Emits | Type | Cardinality Consideration |
|----------------------------------------|------------------------|------|---------------------------|
| [touchpoint ref] | | [Metric/Log/Trace/Event] | |

[If the Step 08 assignment routed no touchpoints to this module, state
that explicitly: "No touchpoints assigned — per Step 08 §5."]

### Health Semantics

| Field | Value |
|-------|-------|
| What "healthy" means for this module's change | |
| Dependencies included in health assessment | |

### Alerting Thresholds

| Condition | Threshold | Urgency | Tied To |
|-----------|-----------|---------|---------|
| | | | [§6 target / SEC-NN audit event] |

---

## §9 — Three-Quantity Effort Estimate Refinement

| Quantity | Phase 2 / Phase 3 Estimate (source briefs) | Step 09 Refined Estimate | Tag | Rationale |
|----------|--------------------------------------------|--------------------------|-----|-----------|
| Dev-hours | | | [BELIEVED/ESTIMATED/MEASURED] | |
| AI-acceleration multiplier (category) | | | [BELIEVED until calibrated] | |
| Derived maintainer-hours | | | | |

**Feeds:** Step 12 §6 aggregates the per-module refinements against
the Phase 2 cost model and capacity envelope (HC-NN); an aggregate
breach is a Channel 3 finding.

---

## §10 — Phase 3 / Phase 2 Invalidation Checks

### §10.1 — Phase 3 Invalidation Check

| Field | Result |
|-------|--------|
| Does module-level work surface that a Phase 3 design specification cannot be landed coherently in this module? | [Yes / No] |
| If Yes — structured report | [Reference §10.3, routed to Step 12 §8] |

### §10.2 — Phase 2 Invalidation Check

| Field | Result |
|-------|--------|
| Does module-level work surface that a Phase 2 commitment (mechanism, cost envelope) cannot hold? | [Yes / No] |
| If Yes — structured report | [Reference §10.3, routed to Step 12 §9] |

### §10.3 — Invalidation Report (populated only if a check is "Yes")

| Field | Value |
|-------|-------|
| Upstream item under invalidation | [Brief ID + design specification ref / MC-NN mechanism / HC-NN envelope] |
| Level | [Phase 3 — Channel 2 / Phase 2 — Channel 3] |
| Why it cannot be landed / cannot hold | [specific module-level evidence] |
| What was tried before concluding invalidation | [the workarounds considered] |
| Candidate amendments | |
| Routing | [Step 12 §8 Phase 3 Amendment Package / Step 12 §9 Phase 2 Amendment Package] |

---

## §11 — Per-Artifact Principle Scorecard Contribution

Produced before this specification is committed, under the inherited
Phase 2 weights.

| Principle | Weight (Inherited) | Per-Artifact Rating | Rationale (citing specific decisions in this specification) |
|-----------|-------------------:|---------------------|--------------------------------------------------------------|
| Security | | [PASS/CONDITIONAL/FAIL] | |
| Maintainability | | [PASS/CONDITIONAL/FAIL] | |
| Economics | | [PASS/CONDITIONAL/FAIL] | |
| Operations | | [PASS/CONDITIONAL/FAIL] | |
| Scoring & Metrics | | [PASS/CONDITIONAL/FAIL] | |
| Correctness Verification | | [PASS/CONDITIONAL/FAIL] | |

**Weight-sensitivity flags:** [which scores are most sensitive to the
decisions made here]
**Below-threshold flags (if any):** [with revision-or-acceptance
decision and rationale]

---

## §12 — Implementation-Readiness Self-Assessment

Section by section: could an AI implementation tool set produce the
working change from this section alone?

| Section | Implementable From This Alone? | Gaps (assumptions an implementer would have to make) | Resolution |
|---------|-------------------------------|------------------------------------------------------|------------|
| §1 Purpose & Responsibility | [Yes/No] | | [Closed here / Phase 5 pre-implementation task / documented limitation] |
| §2 Public Interfaces (incl. pre-change citations, invariants) | [Yes/No] | | |
| §3 Data Models (incl. migration implications) | [Yes/No] | | |
| §4 Dependencies | [Yes/No] | | |
| §5 Security Constraints | [Yes/No] | | |
| §6 Performance Requirements | [Yes/No] | | |
| §7 Test Strategy (incl. regression surface) | [Yes/No] | | |
| §8 Monitoring Hooks | [Yes/No] | | |

**Overall implementation-readiness:** [Ready / Gaps must close first]
**Phase 5 pre-implementation verification tasks (from flags):** [list,
or "None"]

---

## §13 — Confidence Summary

| Field | Value |
|-------|-------|
| Code-access mode (from Step 00) | [Interview-only / Search-primary / Hybrid] |
| Pre-change citations flagged with | [CONFIRM] / [AWARE] / [QUESTION] as applicable |
| Overall specification confidence | [High / Medium / Low] |
| Lowest-confidence sections | [name and explain] |

---

## §14 — Handoff Status

### Forward Handoff Surfaces

| Recipient | What This Specification Provides | What the Recipient Must Do With It |
|-----------|----------------------------------|-------------------------------------|
| Phase 5 (implementation) | | |
| Phase 6 (verification) | | |
| Phase 7 (operation) | | |

[Step 12 §7 builds the phase-level forward handoffs from these rows.]

### Completion Checklist

- [ ] All sections §0–§14 present; disposition-inapplicable sections
      marked, not deleted
- [ ] Detailed interface conforms to SIC-NN; any beyond-contract
      operation surfaced as a Step 08 amendment
- [ ] (CHANGED) Pre-change interface and data shapes cited with flags;
      invariants preserved enumerated; regression surface named
- [ ] Every operation has field-level schemas and complete error
      conditions
- [ ] Every dependency versioned with failure handling
- [ ] Security constraints cite SEC-NN at TB-NN with risk basis
- [ ] Performance targets measurable and baseline-anchored where
      baselines exist
- [ ] Test strategy has coverage targets, contract tests, and Bundle
      §3 instruments
- [ ] Assigned touchpoints mapped (or "none assigned" recorded)
- [ ] §9 estimate refined; §10 checks run; §11 scorecard produced
      before commitment; §12 self-assessment passes
- [ ] No implementation content present

**Status:** [Ready for Step 10 / Gaps require resolution first /
Blocked — invalidation routed to Step 12]

---

## Version

| Version | Date | Source | Summary |
|---------|------|--------|---------|
| v1.0 | [date] | Initial Step 09 production | Module Change Specification for [M-NN] ([disposition]), via Sub-Template [N/C] |
```

---

## Evaluation Checklist

This checklist is unusually rigorous because the
implementation-readiness bar is unusually high. Before accepting a
Module Change Specification as complete, verify:

**Completeness**
- [ ] All sections §0–§14 are present; the eight core content sections
      (§1–§8) are complete at disposition-appropriate depth; nothing
      is omitted or marked "TBD"
- [ ] Disposition-inapplicable sections are explicitly marked "Not
      applicable — [disposition]," never silently deleted
- [ ] §0 conformance declaration names the M-NN, disposition, source
      briefs, SIC-NN, and every assigned constraint ID; bundle and
      Impact Map currency were re-verified at step start

**Conformance to the strategic contract**
- [ ] The detailed interface conforms to the Step 08 strategic
      contract (SIC-NN): every strategic operation is detailed
- [ ] No operation is added beyond the strategic contract — any
      needed addition is surfaced as a Step 08 amendment, not
      silently included

**Public interfaces — implementation-grade**
- [ ] Every operation has a field-level request schema: every field
      with name, type, constraints, required/optional, default
- [ ] Every operation has a field-level response schema: every field
      with name, type, constraints, nullability
- [ ] Every error condition is enumerated with cause, error code
      (SP-NN envelope), response, and retryability — not just the
      happy path
- [ ] Idempotency, authorization (SEC-NN), and interface versioning
      (SP-NN) are specified per operation where applicable

**Data models — implementation-grade**
- [ ] Every owned entity has every field typed with constraints,
      nullability, and (for CHANGED) delta status
- [ ] Integrity constraints and classification tiers cite DA-NN;
      non-owned data is accessed via the owning module's interface
      (M-NN / SIC-NN), not duplicated
- [ ] Migration implications are named at specification level — what
      migrates and under what compatibility posture — with no
      migration scripts

**Dependencies**
- [ ] Every module dependency cites the interface consumed (SIC-NN),
      its delta status, and failure handling per SP-NN
- [ ] Every external and integration-peer dependency is versioned (or
      version-ranged) with failure handling; peer boundaries specify
      the subject's side only
- [ ] Dependency removals driven by RETIRED modules are recorded with
      the Step 08 retirement decision cited

**Security — cited**
- [ ] Every security constraint applies an assigned SEC-NN control at
      a named TB-NN boundary and cites its risk basis (Phase 1
      risk/constraint/technical-debt inventory entry or Phase 2
      analysis)
- [ ] Authorization per operation, data protection, audit logging,
      and least privilege (with explicit prohibitions) are all
      specified — security is IN the specification, not deferred to
      "see Step 04"

**Performance — measurable and baseline-anchored**
- [ ] Every performance target is measurable (percentile, throughput,
      duration, resource budget) — no "should be fast"
- [ ] Targets are anchored to Phase 1 measured baselines where they
      exist, with the measured number cited; targets without a
      baseline carry an explicit rationale
- [ ] (CHANGED) Regression tolerances against the measured baselines
      are stated

**Test strategy — with targets and a regression surface**
- [ ] Coverage targets (line/branch %) are stated with rationale
- [ ] Contract tests verifying conformance to SIC-NN and security
      tests for the applied SEC-NN controls are included
- [ ] The regression surface names the existing behavior and the
      existing tests that must keep passing, cited concretely per the
      code-access mode
- [ ] The Phase 3 Bundle §3 verification instruments that verify this
      module's change are cited with their Phase 6 execution mode

**Monitoring — mapped to the Phase 3 touchpoints**
- [ ] Every Phase 3 observability-touchpoint inventory entry the
      Step 08 assignment routed to this module is mapped, cited by
      the Phase 3 specification's own ID or name (no invented ID
      series); a no-touchpoints assignment is recorded explicitly
- [ ] Health semantics, alerting thresholds (tied to §6 targets /
      SEC-NN audit events), and cardinality considerations are
      specified

**Delta discipline (CHANGED modules)**
- [ ] The pre-change interface (§2.1) and pre-change data shapes
      (§3.1) are cited from code with [CONFIRM]/[AWARE]/[QUESTION]
      flags per the declared code-access mode; Interview-only claims
      are [QUESTION]-flagged with Phase 5 pre-implementation
      verification tasks listed in §12
- [ ] The invariants-preserved table (§2.3) is present; every
      deliberate break cites the Phase 3 design specification that
      authorizes it
- [ ] §1 and §3 are delta-framed; operations and fields carry delta
      status; the specification covers the delta's edges, not only
      its happy path, and does not balloon into a whole-module
      re-specification

**Invalidation checks**
- [ ] Both the Phase 3 and Phase 2 invalidation checks (§10) are run
      explicitly; the default "No" is the recorded answer only when
      true
- [ ] Any "Yes" carries the structured §10.3 report with the level
      correctly diagnosed (design specification → Channel 2 via
      Step 12 §8; mechanism/cost → Channel 3 via Step 12 §9) — no
      silent workaround

**Scorecard and synthesis**
- [ ] The §11 per-artifact scorecard contribution is complete for all
      six Core Principles under the inherited weights, with rationale
      citing specific decisions, and was produced before the
      specification was committed
- [ ] Weight-sensitivity and below-threshold flags are present;
      below-threshold scores have a revision-or-acceptance decision
- [ ] The §9 estimate refinement uses the three-quantity cost model
      with BELIEVED tags preserved
- [ ] The §12 implementation-readiness self-assessment is completed
      section by section; every gap is closed or explicitly carried
      with a resolution path
- [ ] §14 forward handoff surfaces are populated for Phases 5, 6,
      and 7

**Scope and consumption**
- [ ] No implementation content — no function bodies, migration
      scripts, CI configuration, or credential material
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)

---

*Part of the Phase 4 (Existing Projects) Architecture & Modular Design Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `architecture-modular-design.existing-project.instructions.md`*
*Previous step: `step-08-module-impact-map.prompt.md`*
*Next step: `step-10-cross-module-consistency.prompt.md`*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Module Change Specification prompt — the parameterized core of Stage 2, running once per NEW/CHANGED module from the Step 08 manifest. Merges the greenfield Phase 4 step-08 module-specification rigor (field-level schemas, every error condition, versioned dependencies, cited security, measurable performance, coverage-targeted test strategy, implementation-readiness self-assessment) with the existing-track's parameterized one-per-item session pattern and invalidation-check discipline from the Phase 3 step-03 counterpart. The defining v1.0 feature is the disposition-adaptive shape: Sub-Template N produces a full specification for NEW modules, Sub-Template C a delta specification for CHANGED modules — pre-change interface and data shapes cited from code per the code-access mode, post-change contract at field level with per-operation and per-field delta status, invariants preserved enumerated with authorized-break discipline, and the regression surface (existing behavior and existing tests that must keep passing) named. Brownfield anchoring replaces greenfield references: performance targets anchor to Phase 1 measured baselines with the measured number cited, monitoring maps the Phase 3 observability-touchpoint inventory (no invented H-NN series), and test strategies cite the Phase 3 Bundle §3 instruments. The §0–§14 output structure carries the three-quantity effort estimate refinement, the Phase 3 / Phase 2 invalidation checks routing to Step 12 §8/§9, and the scorecard-before-commitment discipline. |
