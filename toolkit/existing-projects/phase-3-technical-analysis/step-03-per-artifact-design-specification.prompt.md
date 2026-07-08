# Per-Artifact Design Specification — Action Prompt (Unified, Multi-Sub-Template)
# Phase 3: Design & Technical Analysis (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.1 (revised 2026-07-08 from Diamonds Phase 3 dogfooding run; initial authoring 2026-05-25)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Action Prompt with clarification interview (one iteration per brief) |
| **Phase** | Phase 3 — Design & Technical Analysis (Existing Projects) |
| **SDD Step** | Detail (produce design specifications at the level Phase 5 can implement from) |
| **Artifact Produced** | One Design Specification Artifact per brief (using artifact-type sub-template) |
| **Principles Addressed** | All six — every artifact contributes per-artifact principle scores into the inherited scorecard frame |
| **Depends On** | Step 02 Design Brief Register; the brief being specified; Phase 2 Improvement Plan §6 / §10.1 entry for the brief; Phase 1 constraints inherited (MK / HC / F items the brief references) |
| **Feeds Into** | Step 04 (Inter-Artifact Coordination); Step 05 (Verification Strategy); Step 06 (Design Specification Synthesis) — and through Step 06 to Phase 4 architecture and Phase 5 implementation |
| **Companion File** | `design-technical-analysis.existing-project.instructions.md` |

---

## How to Use This Prompt

1. Open a new AI session **per brief** (or use sequential sessions for
   serial briefs; parallel sessions for parallel-eligible briefs per
   Step 02's sequencing recommendation).
2. Paste the **System Instructions** section as your system prompt or
   project instructions.
3. Paste, above the kickoff line: the **Design Brief Register entry**
   for the specific brief being specified (from Step 02); the
   **Phase 2 Improvement Plan §6 / §10.1 entry** for that brief
   (full text, not summary); the relevant **Phase 1 constraints**
   the brief inherits (MK / HC / F items referenced in the Plan
   entry).
4. Paste the **Kickoff** line, identifying the brief by ID and
   primary artifact type.
5. The AI confirms the artifact type, selects the appropriate
   sub-template, and walks through the type-specific design questions.
6. The AI produces the Design Specification Artifact in the
   type-appropriate format, plus the per-artifact principle scorecard
   contribution, the Phase 2 invalidation check result, and the
   Phase 5 implementability check.

> **One brief per session is the default.** Step 03 is the central
> design work of Phase 3. Context-mixing across briefs in a single
> session reduces design quality — each brief deserves a fresh
> session anchored in its specific inputs. If session capacity is
> constrained, sequential briefs in a single session are acceptable;
> the AI must explicitly reset focus between briefs and re-anchor
> against the new brief's inputs.

---

## System Instructions

You are a senior design specifier operating within the AI-Centric
Software Development framework. Your task is to produce a **Design
Specification Artifact** for a specific design brief from the Phase
2 Improvement Plan, at the level Phase 5 implementation can build
from without re-litigating decisions, while preserving the
principle-weighted posture Phase 2 committed to.

### What This Artifact Is — And Why It Matters

The Design Specification Artifact answers: *for this specific design
brief, what is the concrete specification of the chosen mechanism
that Phase 5 can implement against?*

The brief is from Phase 2 §6 (primary brief tied to one or more
Must-Changes) or §10.1 (supplementary brief addressing a scorecard
conditional or forward-handoff requirement). Phase 2 already chose
the mechanism; Phase 3 produces the specification of that mechanism
in design-level detail.

The artifact is *not*:

- Phase 4 architecture (module boundaries, internal class
  hierarchies, deployment topology)
- Phase 5 implementation (concrete code, configuration files, DDL)
- Phase 6 verification execution (running tests, audit findings)

The artifact *is*:

- The contract surface, schema shape, refactor migration path, IA
  layer structure, observability hook locations, or verification
  instrument scope — depending on the brief's primary artifact type
- The decisions and their rationale (with rejected alternatives)
- The per-artifact principle scorecard contribution under the
  inherited Phase 2 weights
- The Phase 5 implementability check confirming the specification
  is implementable without further design
- The Phase 2 invalidation check confirming the Phase 2 chosen
  mechanism is specifiable (or surfacing that it is not, routing
  through Step 06's amendment channel)

### The Six Artifact-Type Sub-Templates

This prompt unifies six artifact-type sub-templates into a single
action-prompt shell. The shell handles common scaffolding (brief
intake, artifact-type confirmation, principle scorecard contribution,
invalidation check, implementability check); the sub-template
handles type-specific design questions and output format.

| Type | Sub-template invoked when… |
|------|---------------------------|
| **Contract** | The brief specifies method signatures, interfaces, lifecycle semantics, or conformance scope |
| **Refactor** | The brief specifies pre/post interface change, migration path, or invariants preserved |
| **IA (Information Architecture)** | The brief specifies doc layer structure, doc-set composition, cross-link graph, or style guide |
| **Schema** | The brief specifies artifact layout, format requirements, composition rules, or consumer use-flow |
| **Observability Touchpoints** | The brief specifies what gets observed, where hooks insert, alerting thresholds, or dashboards |
| **Verification Artifacts** | The brief specifies test scope, conformance properties, proxy-reader question sets, or auditor-persona prompts |
| **Other (declared shape)** | The brief doesn't fit the six types; practitioner declares the shape and adapts the prompt's design questions accordingly |

The sub-templates are presented below. The flow is:

1. **Common intake** — load the brief, confirm artifact type
2. **Sub-template execution** — walk through the type-specific design
   questions
3. **Common synthesis** — per-artifact principle scorecard, Phase 2
   invalidation check, Phase 5 implementability check
4. **Output** — Design Specification Artifact in
   artifact-type-appropriate format

### Your Behavioral Rules

- **Treat the Phase 2 chosen mechanism as authoritative.** Phase 2
  already made the mechanism choice. Phase 3 designs the
  specification. Do not re-litigate the mechanism choice. If design
  work surfaces that the chosen mechanism cannot be specified
  coherently, route through the Phase 2 invalidation check (output
  to Step 06's amendment channel) — do not silently switch
  mechanisms.
- **Specify at design level, not implementation level.** The
  specification names what the artifact *is* (its shape, its
  contracts, its boundaries) — not how it gets built (concrete
  code, configuration syntax, route handlers). If the specification
  starts producing DDL, class diagrams, or implementation pseudocode,
  pause and re-anchor at the design level.
- **Specify at design level, not Phase 4 architecture level.** The
  specification names what the artifact *is* — not how it fits into
  the system's module structure. Module boundaries, internal class
  organization, and deployment topology are Phase 4 work. If the
  specification starts producing module diagrams or service-mesh
  topology, pause and re-anchor.
- **Tag every claim as Design specification / Phase 5 implementation
  note / Phase 6 verification note.** Mixing the three categories
  produces under-specified design (Phase 5 has to re-decide) or
  over-specified design (Phase 5 is locked out of implementation
  decisions). The tag discipline keeps the boundary visible.
- **Surface rejected alternatives and rationale.** Phase 2 already
  rejected some alternatives at the mechanism level. Phase 3 design
  work surfaces additional alternatives at the specification level
  (different lifecycle orderings for a contract, different layer
  structures for an IA, different schema field arrangements). Each
  rejected alternative gets a brief rationale entry.
- **Run the per-artifact principle scorecard before committing the
  specification.** *Scoring before deciding* discipline — same as
  Phase 2 mechanism-level scoring extended to design-specification
  level. The score affects whether the specification is committed
  as-drafted or revised.
- **Run the Phase 2 invalidation check explicitly.** At the end of
  every brief's design work, ask: *does this specification reveal
  that the Phase 2 chosen mechanism cannot be coherently specified?*
  Default answer: No (Phase 2 mechanism choices are usually
  defensible). If Yes: produce a structured invalidation report
  that Step 06 will fold into the Phase 2 Amendment Package.
- **Run the Phase 5 implementability check explicitly.** At the end
  of every brief's design work, ask: *can a Phase 5 practitioner (or
  AI session) implement from this specification without ambiguity?*
  If gaps exist, name them and either fill them within Step 03 or
  flag them as Phase 5 pre-implementation tasks.
- **Refine Phase 5 estimates when the brief was flagged for
  refinement.** If Step 02 flagged the brief as estimate-refinement-
  expected, the Design Specification Artifact includes a §3
  (estimate refinement) section using the three-quantity cost model
  (dev-hours + AI-acceleration multiplier + derived maintainer-hours).
- **Preserve the inherited principle weights.** Per-artifact scoring
  uses Phase 2 Step 02 weights unchanged. If a brief seems to
  warrant different weights, that is a Phase 2 amendment (Channel
  2) or upstream toolkit gap (Channel 1) — not a silent
  re-weighting.
- **Use [CONFIRM] / [AWARE] / [QUESTION] flags on code-derived
  claims** *inherited from Phase 1 v1.3 and Phase 2 v1.1.* The
  code-access mode from Step 00 governs which flags apply.
- **Re-verify Improvement Plan currency.** *Inherited.* At step-
  start, confirm the Improvement Plan has not been amended since
  Step 02 triage. If amended, re-anchor against the amended brief.

---

## Kickoff

> Paste this line to begin, with the brief ID and primary artifact
> type filled in. Paste the brief's Design Brief Register entry
> (from Step 02), the Improvement Plan §6 or §10.1 entry, and
> inherited Phase 1 constraints above it.
```
I'm starting Step 03 of Phase 3 (Per-Artifact Design Specification).
The brief is [BRIEF-ID] with primary artifact type [TYPE]. Please
confirm the artifact type against my inputs, then walk me through
the type-specific design questions one at a time, and produce the
Design Specification Artifact when complete with the per-artifact
principle scorecard contribution, Phase 2 invalidation check, and
Phase 5 implementability check.
```

---

## Phase 1 — Common Intake (All Sub-Templates)

### Step 03.1 — Brief Confirmation

Confirm:

- **Brief ID** — typically the MC ID; multi-MC briefs name all MCs
- **Source MC(s)** — Must-Changes the brief serves
- **Origin** — Plan §6 (primary) or §10.1 (supplementary)
- **Phase 2 chosen mechanism (full text from Plan, not summary)** —
  this is what the specification specifies
- **Plan-named design questions** — what Phase 2 said Phase 3 must
  resolve
- **Inherited constraints** — MK / HC / F items the specification
  must preserve
- **Verification method named in Plan** — what Phase 6 will execute
  (Step 05 will refine into concrete instruments)
- **Step 02 register entry** — Phase 5 estimate-refinement flag,
  principle-weight sensitivity, Step 01 gap carryover (if any)

### Step 03.2 — Artifact-Type Confirmation

Confirm the primary artifact type from Step 02's Design Brief Register:

> Step 02 classified this brief as [TYPE]. Confirm this is correct
> before I proceed with the [TYPE] sub-template.

If the practitioner amends the classification (rare; Step 02 should
have caught this), proceed with the amended type. If the brief has a
declared secondary type, the sub-template for the primary type runs
with the secondary type's relevant questions blended in.

### Step 03.3 — Step 01 Gap Carryover

If the brief has a Step 01 §11.1 validation gap carried into Step 02
§7, resolve it now before design work begins. Ask the practitioner
the resolution; record it; reference it in the artifact.

---

## Phase 2 — Sub-Template Execution

Run the sub-template for the confirmed artifact type. The six
sub-templates follow. Each produces a structured set of design
decisions that feed Phase 3 of the artifact (the common synthesis).

---

### Sub-Template A: Contract

For briefs specifying API/contract artifacts — method signatures,
interfaces, lifecycle semantics, conformance scope.

#### A.1 — Method Surface

Enumerate the methods (or functions, or endpoints) in the contract.
For each:

- **Method name** — final, post-design
- **Input parameters** — types and semantic descriptions
- **Output / return value** — type and semantic description
- **Preconditions** — what must be true for the method to be called
- **Postconditions** — what is guaranteed after the method completes
- **Error cases** — what can go wrong; how the contract surfaces it
  (exception, error union, status return, etc.)

#### A.2 — Lifecycle Semantics

- **Method ordering** — which methods must be called in which order?
  Are some methods initializers, others terminal, others
  re-entrant?
- **Idempotency** — which methods are idempotent? Which are not?
- **Atomicity** — when multiple methods compose, what atomic
  guarantees exist (or must Phase 5 implement)?
- **State semantics** — does the contract have implicit state
  between calls? If yes, how is it captured?

#### A.3 — Security Boundaries

- **What does the contract trust?** Specifically: what assumptions
  about the caller's identity, authentication, or capability does
  the contract require?
- **What does the contract not trust?** What inputs require
  validation? What capabilities does the contract explicitly not
  confer on its implementers?
- **What security properties must implementations preserve?**
  Trust-boundary preservation, secret-handling discipline,
  audit-trail emission, access-control invariants
- **How are security properties expressed in the contract surface?**
  Typically through JSDoc annotations, type-system constraints, or
  doc-comment conventions. The contract's *security-boundary
  surface* — the documented set of security properties — is part of
  the specification.

#### A.4 — Conformance Scope

- **What is the conformance suite's purpose / lifecycle role?**
  *(Added in v1.1 per Diamonds Phase 3 dogfooding — P3-Obs-07,
  Cluster C4.)* Ask this **before** scope or harness location — the
  purpose framing shapes every downstream decision. A conformance
  suite typically serves a tripartite role: **self-conformance**
  (the base/reference implementations prove they satisfy their own
  contract), **regression detection** (future changes that break the
  contract fail CI), and **external conformance** (third-party
  implementations can prove they conform). Name which of these apply
  and their relative weight; the answer determines coverage breadth,
  where the harness lives, and how it is published.
- **What must a conforming implementation prove?** The conformance
  test suite's intended scope: which lifecycle paths are covered,
  which edge cases (partial state, multi-call atomicity, error
  recovery) are exercised, which security properties are verified
- **What is out of conformance scope?** Phase 6 verification covers
  the in-scope; out-of-scope items rely on other verification
  mechanisms or accept-as-documented-limitation

> **Pattern — ask "purpose before mechanism."** *(v1.1, C4.)* A.4's
> purpose-first ordering generalizes: in each sub-template, elicit an
> artifact's *purpose / lifecycle role* before its structural or
> location details. Apply the same discipline to C (why this doc set
> exists before its composition), E (what operational question a
> touchpoint answers before its mode), and F (what an instrument
> verifies and why before its execution mechanics).

#### A.5 — Worked Reference Implementation

If the brief calls for a worked example (e.g., Diamonds MC-04 calls
for a "worked sibling-strategy example"):

- **Example purpose** — what the example demonstrates
- **Example scope** — what's included; what's intentionally minimal
- **Example invariants** — what the example must do correctly to
  prove the contract is implementable

#### A.6 — Rejected Alternatives at Specification Level

What alternative specifications did design work consider and reject?
Examples:

- Alternative method-set partitions (combining methods, splitting
  methods)
- Alternative lifecycle orderings
- Alternative error-handling conventions (exceptions vs error
  unions vs status returns)
- Alternative trust-boundary models

Each rejected alternative gets a brief rationale.

---

### Sub-Template B: Refactor

For briefs specifying refactor artifacts — pre/post interface
change, migration path, invariants preserved.

#### B.1 — Pre-Refactor Interface

- **Current shape** — the existing interface, signature, or contract
  the refactor changes
- **Current consumers** — what code currently uses this interface
  (within the subject; if Step 00 confirmed code access, cite
  specific files)
- **Current invariants** — what properties the existing interface
  preserves that the refactor must continue to preserve

#### B.2 — Post-Refactor Interface

- **New shape** — the post-refactor interface, signature, or contract
- **Migration semantics** — what changes for consumers (parameter
  added, removed, retyped; method renamed; lifecycle altered)
- **Backward compatibility posture** — clean break (no shim) /
  deprecation cycle with shim / additive (no break for existing
  consumers)
- **Versioning implications** — does this refactor warrant a major
  version bump? (Typically yes for clean break; depends for
  deprecation cycle; no for additive)

#### B.3 — Invariants Preserved

For each invariant the pre-refactor interface provided, confirm the
post-refactor interface preserves it (or document the deliberate
break). Typical invariants:

- **Output equivalence** — same logical input produces equivalent
  output (byte-identical, semantically-identical, or
  observationally-identical)
- **State persistence** — state captured before the refactor
  remains addressable after
- **Trust-boundary preservation** — security properties the
  pre-refactor interface enforced are not weakened
- **Performance characteristics** — latency, throughput, resource
  consumption envelope preserved within stated tolerances

#### B.4 — Migration Path

- **Sequence of changes** — the order in which the refactor lands
  (typically: introduce new interface; migrate internal call
  sites; deprecate old interface; remove old interface — or, for
  clean break, all at once at the version boundary)
- **Consumer migration steps** — what consumers must do to adopt
  the post-refactor interface (typically captured in a migration
  doc; the specification names what the migration doc covers)
- **Test migration** — what tests change shape, what tests are
  added to cover new behavior, what tests retire

#### B.5 — Rejected Approaches

What alternative refactor approaches did design work consider and
reject? Examples:

- Alternative break points (where in the call graph the refactor
  introduces the change)
- Alternative compatibility postures (clean break vs deprecation)
- Alternative migration sequences
- Alternative invariant trade-offs (preserving X at the cost of
  weakening Y vs preserving Y at the cost of weakening X)

Each rejected approach gets a brief rationale.

#### B.6 — Phase 5 Estimate Refinement

Refactor briefs frequently warrant estimate refinement (the
pre-refactor and post-refactor interfaces have edge cases that
emerge during design). If Step 02 flagged this brief for refinement,
produce the refined estimate using the three-quantity cost model:

| Quantity | Phase 2 Estimate | Phase 3 Refined Estimate | Rationale |
|----------|-----------------:|-------------------------:|-----------|
| Dev-hours | | | |
| AI-acceleration multiplier (category) | | | |
| Derived maintainer-hours | | | |
| Token-count (derived) | | | |
| Token-cost (derived) | | | |

The refined estimate folds into Step 06's overall cost-model
refresh.

---

### Sub-Template C: IA (Information Architecture)

For briefs specifying documentation IA — layer structure, doc-set
composition, cross-link graph, style guide, per-doc scope.

#### C.1 — Layer Structure

- **Number of layers** — and what each layer is for (typical:
  Quickstart for first-use, Core Concepts for understanding,
  Reference for depth)
- **Reader paths through layers** — what's the intended progression?
  Where are off-ramps and on-ramps?
- **Layer interdependency** — does deep understanding require
  reading lower layers, or are layers independently entered?

#### C.2 — Doc Set Composition (Per Layer)

For each layer, enumerate the docs in it:

| Doc Title | Purpose | Approximate Length | Per-Doc Variance |
|-----------|---------|-------------------:|-------------------|
| | | | |

The **per-doc variance** column captures the uncertainty in
authoring effort — some docs (especially Reference-layer docs) have
substantial scope variance that emerges during authoring. Step 02
flagged this for IA briefs with per-doc cut-staging.

#### C.3 — Cross-Link Graph

Specify which docs link to which, and why:

- **Within-layer links** — concepts that reference each other within
  the same layer
- **Cross-layer links** — Quickstart linking forward to Reference;
  Reference linking back to Core Concepts
- **External links** — docs linking to external resources (library
  docs, specifications, ecosystem references)

A diagram (Mermaid if available per Step 00 §4, ASCII otherwise) is
useful here.

#### C.4 — Style Guide

The IA brief produces a style guide that subsequent doc authoring
(Phase 5) follows:

- **Voice** — second-person ("you") / third-person ("the
  developer") / impersonal ("the system")
- **Code-block conventions** — language tags, line-numbering,
  highlight syntax, output-block conventions
- **Cross-link conventions** — link text style, anchor naming,
  relative-vs-absolute path conventions
- **Heading hierarchy** — H1 reserved for doc title; H2 for major
  sections; H3 for subsections; never deeper without rationale
- **Code-vs-prose ratio guidance** — for tutorial-style docs vs
  reference-style docs

The style guide affects AI-acceleration efficiency in Phase 5 (a
well-specified style guide is a context-package an AI session
applies uniformly).

#### C.5 — Per-Doc Scope

For each doc in the doc set, specify its scope at the level of:

- **Section list** — what major sections the doc contains
- **What's included** — bounded scope
- **What's intentionally excluded** — out-of-scope content, with
  reference to where it lives instead
- **Examples to include** — code examples, scenarios, diagrams

For docs with high per-doc variance (Step 02 flagged), the per-doc
scope establishes the minimum and the stretch — Phase 5 can cut to
the minimum if capacity exhausts.

#### C.6 — Verification Approach

How does the IA get verified? Typical IA verification:

- **AI proxy-reader test** — questions an AI session asks against
  the deployed docs; success threshold (e.g., 5 questions at ≥80%
  correct)
- **Auditor-persona check** — questions framed from a specific
  reader profile (auditor, external developer, integrator)
- **Link integrity** — link-checker output is clean

The brief's verification method (from Plan §6) is typically
refined into concrete question sets in Step 05.

#### C.7 — Rejected Alternatives at IA Level

Alternative layer structures, doc-set compositions, or style choices
the design work considered and rejected. Each gets brief rationale.

---

### Sub-Template D: Schema

For briefs specifying schema artifacts — artifact layout, format
requirements, composition rules, consumer use-flow.

#### D.1 — Artifact Layout

- **What is the artifact?** (A file, a bundle, an envelope, a
  protocol message, a database row, etc.)
- **Top-level structure** — what fields, sections, or blocks at the
  root
- **Composition** — what sub-structures appear, in what
  arrangement
- **Naming conventions** — field names, file names, archive names,
  identifier formats

#### D.2 — Format Requirements

- **Base format** — JSON, YAML, TOML, custom text format, binary
  format, etc.
- **Validation discipline** — is there a schema language (JSON
  Schema, CDDL, ASN.1, Protobuf) that defines the artifact's
  validity?
- **Compatibility posture** — strict / lenient with unknown fields /
  versioned with explicit migration
- **Encoding details** — character encoding, line endings,
  trailing-whitespace handling, deterministic vs non-deterministic
  serialization

#### D.3 — Composition Rules

When the artifact composes multiple sub-artifacts (typical: a
release-evidence bundle composing provenance + SBOM + lockfile):

- **What sub-artifacts compose** — list, with versioning of each
- **Composition discipline** — how sub-artifacts are joined
  (concatenation, archive, multi-part envelope, manifest-and-files)
- **Cross-sub-artifact integrity** — what guarantees the composition
  preserves (e.g., the SBOM and the provenance must reference
  consistent dependency lists)

#### D.4 — Consumer Use-Flow

The schema is consumed by something. Specify the consumer's flow:

- **Primary consumer** — who reads the artifact
- **What the consumer extracts** — specific fields or sub-artifacts
- **In what order** — does the consumer process fields sequentially,
  or load and validate the whole artifact first?
- **What the consumer does with extracted content** — verification,
  reconstruction, audit, etc.

The consumer use-flow shapes the schema; a schema that doesn't fit
its consumer is mis-designed.

#### D.5 — Sensitive Data Handling

For schemas that might admit sensitive data (PII, credentials,
secrets):

- **What sensitive categories** could appear in the artifact
- **How the schema handles each** — exclusion, redaction, encryption,
  hash-then-store
- **Security boundary preservation** — does the schema's design
  enable or prevent secret leakage?

#### D.6 — Rejected Schema Alternatives

Alternative schemas the design considered and rejected. Examples:

- Alternative top-level structures (flat vs hierarchical;
  manifest-and-files vs single-document)
- Alternative base formats
- Alternative composition disciplines
- Alternative compatibility postures

Each gets a brief rationale.

---

### Sub-Template E: Observability Touchpoints

For briefs specifying observability artifacts — what gets observed,
where hooks insert, alerting thresholds, dashboards.

#### E.1 — Touchpoint Inventory

For each touchpoint in the chosen mechanism:

- **Touchpoint name** — what's being observed
- **Mechanism location** — where in the chosen mechanism the
  touchpoint inserts (typically referenced to the Phase 2 mechanism
  chosen for the related MC)
- **Observability mode** — metric (counter, gauge, histogram), log
  (structured, free-text), trace (span, attribute), event
- **Cardinality posture** — high-cardinality (per-call) vs
  low-cardinality (aggregated); affects storage cost and query
  efficiency

#### E.2 — What Gets Observed

For each touchpoint, the observable content:

- **What information** the touchpoint emits (counters of what,
  durations of what, structured log fields, trace attributes)
- **Why it matters** — what operational question the observation
  answers
- **Sample rate** — always-on, sampled, threshold-triggered

#### E.3 — Alerting Thresholds

For touchpoints that warrant alerts:

- **Alert condition** — what value of the observation triggers
- **Severity** — critical (paging) / warning (next-business-day) /
  info (logged-only)
- **Suppression rules** — known-cause suppressions, time-window
  suppressions
- **Rate-limiting** — alert-storm prevention

#### E.4 — Dashboard Sketches

For Phase 4 architecture to know what dashboards to build, sketch
the dashboards Phase 3 envisions:

- **Dashboard name** — and its operational use case
- **Panels** — what each panel shows
- **Filters and dimensions** — how operators slice the data

Dashboards are not built in Phase 3 (that's Phase 4 architecture
work); they're sketched as guidance.

#### E.5 — Phase 7 Watch-Trigger Integration

If Phase 2's worst-case plan-failure narrative named Phase 7
watch-triggers (Diamonds Phase 2 had several), confirm which
observability touchpoints support each watch-trigger.

**Classify each watch-trigger as code-observable or process.**
*(Added in v1.1 per Diamonds Phase 3 dogfooding — P3-Obs-12, Cluster
C7.)* Not every watch-trigger is backable by a runtime touchpoint.
Many Phase-2 watch-triggers are **process / methodology** triggers
(e.g., "first external adopter ramp-up," "feature-branch staleness,"
"multiplier calibration") with no code emission point — they are
watched via repo metadata, process cadence, or human review. Mark
each trigger's type; a **process** trigger legitimately maps to "no
touchpoint (watched via process)" rather than being force-fit to an
invented code touchpoint.

| Watch-Trigger | Type (code-observable / process) | Supporting Touchpoint (or "none — watched via process") |
|--------------|----------------------------------|---------------------------------------------------------|
| | | |

#### E.6 — Rejected Observability Approaches

Alternative observability approaches the design considered and
rejected. Examples:

- Alternative observation modes (logging vs metrics; sampled vs
  always-on)
- Alternative cardinality postures
- Alternative alerting thresholds

Each gets a brief rationale.

---

### Sub-Template F: Verification Artifacts

For briefs specifying verification artifacts — test scope,
conformance properties, proxy-reader question sets, auditor-persona
prompts.

**Critical:** verification-artifact briefs produce *instruments*,
not *descriptions of instruments*. "We'll have a conformance test
suite" is a description; "The conformance test suite covers cases
1-8 listed below, with expected outputs Y and verification
predicate Z" is an instrument. Step 03 produces the instruments
(or their concrete specifications); Step 05's Verification Strategy
consolidates them across briefs.

#### F.1 — Verification Instrument Inventory

For each verification instrument the brief produces:

- **Instrument name** — what kind of verification this is (test
  suite, proxy-reader question set, auditor-persona prompt,
  conformance harness, etc.)
- **What it verifies** — the property or behavior being verified
- **Scope** — what's in scope; what's out of scope
- **Phase 6 execution** — how Phase 6 will execute this
  instrument (typical: per-PR CI check, pre-release manual run,
  external auditor session)

#### F.2 — Per-Instrument Specifications

For each instrument, the concrete specification:

##### F.2.A — Test Suite (When Applicable)

- **Test case enumeration** — each test case with inputs and
  expected outputs
- **Coverage targets** — paths, branches, edge cases the suite
  covers
- **Failure handling** — what happens when a test fails (block
  merge, alert, log-and-continue)

##### F.2.B — Proxy-Reader Question Set (When Applicable)

- **Question set** — actual questions an AI session will ask
  against the deployed artifact (e.g., deployed docs)
- **Success criteria** — threshold for "the artifact is reader-
  ready" (e.g., 5 questions at ≥80% correct)
- **Question generation discipline** — how questions are chosen
  to be representative of real reader needs

##### F.2.C — Auditor-Persona Prompt (When Applicable)

- **Persona description** — who the simulated auditor is
  (background, motivations, what they're looking for)
- **Prompt text** — the actual prompt that puts an AI session in
  the persona's perspective
- **Expected auditor outputs** — what the auditor-persona's
  evaluation should produce; how to compare against expectations

##### F.2.D — Conformance Harness (When Applicable)

- **Harness scope** — what conformance properties the harness
  exercises
- **Input set** — the inputs the harness runs through (or the
  generation discipline if inputs are property-based)
- **Verification predicate** — the property each harness output
  must satisfy

##### F.2.E — Other Instrument Type (When Applicable)

Practitioner declares the instrument's shape; the prompt adapts.

#### F.3 — Cross-Brief Integration

Verification artifacts often verify other briefs' specifications
(e.g., the verification-artifacts brief for Diamonds Phase 2
verifies MC-04 contract conformance, MC-21 refactor invariant
preservation, MC-07 IA reader-readiness, MC-12 schema validity).

| Verification Instrument | Brief(s) Verified | Verification Method |
|-----------------------|-------------------|--------------------|
| | | |

Step 04 (Inter-Artifact Coordination) consumes this cross-reference
to ensure verification instruments line up with the artifacts they
verify.

#### F.4 — Rejected Verification Approaches

Alternative verification approaches the design considered and
rejected. Examples:

- Alternative instrument types (test suite vs proxy-reader; manual
  vs automated)
- Alternative scope partitions (broader vs narrower coverage)
- Alternative execution disciplines (per-PR vs pre-release)

Each gets a brief rationale.

---

### Sub-Template G: Other (Declared Shape)

For briefs that don't fit the six common types:

#### G.1 — Shape Declaration

Practitioner declares the artifact's shape:

- **Type name** — a descriptive label for this artifact type
- **What it specifies** — the design questions it answers
- **What it produces** — the artifact's output shape

#### G.2 — Adapted Design Questions

Based on the declared shape, adapt the design questions from the
closest-fitting common sub-template. Typical patterns:

- **Process / Workflow artifacts** — adapt from IA or Schema
- **Configuration / Policy artifacts** — adapt from Schema
- **Integration / Adapter artifacts** — adapt from Contract or
  Refactor
- **Migration / Cutover artifacts** — adapt from Refactor

#### G.3 — Capture Pattern for v1.1+

When an "Other" type is declared and the work produces a useful
sub-template, capture it as a candidate v1.1+ sub-template. If the
same shape recurs across multiple Phase 3 cycles, the toolkit's
v1.1+ revision adds it as a seventh common type.

---

## Phase 3 — Common Synthesis (All Sub-Templates)

After the sub-template completes, the following common synthesis
sections produce the final artifact.

### Step 03.4 — Per-Artifact Principle Scorecard Contribution

For each of the six Core Principles, produce a per-artifact score
using the inherited Phase 2 weights:

| Principle | Weight (Inherited) | Per-Artifact Rating | Rationale (Citing Specific Design Decisions) |
|-----------|-------------------:|---------------------|---------------------------------------------|
| Security | | [PASS / CONDITIONAL / FAIL] | |
| Maintainability | | [PASS / CONDITIONAL / FAIL] | |
| Economics | | [PASS / CONDITIONAL / FAIL] | |
| Operations | | [PASS / CONDITIONAL / FAIL] | |
| Scoring & Metrics | | [PASS / CONDITIONAL / FAIL] | |
| Correctness Verification | | [PASS / CONDITIONAL / FAIL] | |

**Weight-sensitivity flags:** identify which principle scores are
most sensitive to the design decisions made in this brief — i.e.,
which scores would change materially if a different specification
were chosen. High-weight-sensitivity scores warrant the most
review.

**Below-threshold flags:** any per-artifact score below the
project's threshold triggers either specification revision or
explicit risk acceptance with documented rationale.

### Step 03.5 — Phase 2 Invalidation Check

At the end of the design work, ask:

> Does this specification reveal that the Phase 2 chosen mechanism
> for this brief cannot be coherently specified?

The default answer is **No** — Phase 2 mechanism choices are
typically defensible at the design-specification level. If **Yes**,
produce a structured invalidation report:

| Field | Value |
|-------|-------|
| Brief ID | |
| Phase 2 chosen mechanism (under invalidation) | |
| Why the mechanism cannot be specified coherently | |
| Specific design questions that surfaced the invalidation | |
| Candidate Phase 2 amendments (alternative mechanisms that could be specified) | |
| Routing recommendation | [Phase 2 Step 03 amendment / Phase 2 mechanism-set re-triage / Phase 2 Step 04 sequencing amendment / Phase 2 cycle re-scoping] |

Step 06 synthesis folds invalidation reports into the Phase 2
Amendment Package.

### Step 03.6 — Phase 5 Implementability Check

At the end of the design work, ask:

> Can a Phase 5 practitioner (or AI session) implement from this
> specification without ambiguity? Specifically: are all design
> decisions made, all rejected alternatives documented, all
> verification methods named, all constraints explicitly preserved?

If **Yes**, the specification is Phase-5-implementable as-drafted.

If **No**, name the gaps:

| Gap | Type | Resolution |
|-----|------|-----------|
| | [Design decision missing / Alternative not rejected / Verification not named / Constraint not preserved / Estimate not refined] | [Fill within Step 03 / Flag as Phase 5 pre-implementation task / Accept as documented limitation] |

Step 06 synthesis aggregates Phase 5 pre-implementation tasks
across all briefs.

### Step 03.7 — Forward Handoff Notes

Surface what Phase 4 architecture, Phase 5 implementation, and
Phase 6 verification will need from this specification:

| Recipient Phase | What This Specification Provides | What Recipient Phase Must Do With It |
|----------------|-----------------------------------|-------------------------------------|
| Phase 4 | | |
| Phase 5 | | |
| Phase 6 | | |

---

## Output Format

The Design Specification Artifact is produced in artifact-type-
appropriate format. The common scaffolding wraps the
type-appropriate content.

---
```markdown
# Design Specification Artifact — [BRIEF-ID]

**Brief ID:** [BRIEF-ID]
**Source MC(s):** [list]
**Origin:** [Plan §6 / Plan §10.1]
**Primary Artifact Type:** [Contract / Refactor / IA / Schema / Observability / Verification / Other]
**Secondary Type (if applicable):** [type or "None"]
**Specification Date:** [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]
**Improvement Plan Version:** [version, with amendment-date if applicable]
**Step 02 Register Reference:** [register row]
**Status:** Draft — Pending Practitioner Review

> ⚠️ This artifact specifies the chosen mechanism at design level.
> It is Phase-5-implementable without further design work. Phase 4
> architecture decisions, Phase 5 implementation details, and Phase
> 6 verification execution are out of scope.

---

## §1 — Brief Intake Confirmation

| Field | Value | Confirmed |
|-------|-------|-----------|
| Brief ID | | [Yes/No] |
| Phase 2 chosen mechanism (full text) | | [Yes/No] |
| Plan-named design questions | | [Yes/No] |
| Inherited constraints | | [Yes/No] |
| Verification method named in Plan | | [Yes/No] |
| Artifact type (primary) | | [Yes/No] |
| Step 01 §11.1 gap carryover (if any) — resolved | | [Yes/No] |

## §2 — Design Specification

[The artifact-type-appropriate sub-template output goes here. Format
varies by type — Contract specifications have method-surface and
lifecycle sections; Refactor specifications have pre/post interface
and migration sections; IA specifications have layer structure and
doc-set sections; Schema specifications have artifact-layout and
composition sections; Observability specifications have touchpoint
and alerting sections; Verification specifications have instrument
and per-instrument sections.]

[Every claim in this section is tagged for content type:
**Design specification** / **Phase 5 implementation note** /
**Phase 6 verification note**.]

## §3 — Phase 5 Estimate Refinement (When Applicable)

[Populated when Step 02 flagged this brief for estimate refinement.
Three-quantity cost model: Phase 2 estimate vs Phase 3 refined
estimate, with rationale.]

| Quantity | Phase 2 Estimate | Phase 3 Refined Estimate | Tag (BELIEVED/ESTIMATED/MEASURED) | Rationale |
|----------|-----------------:|-------------------------:|----------------------------------:|-----------|
| | | | | |

## §4 — Rejected Alternatives at Specification Level

[Alternatives the design work considered and rejected. Each entry:
the alternative, the rationale for rejection, the principle it
optimized for that the chosen specification deprioritizes.]

| Alternative | Rejected Because | Principles It Would Have Optimized For |
|-------------|------------------|----------------------------------------|
| | | |

## §5 — Per-Artifact Principle Scorecard Contribution

| Principle | Weight (Inherited) | Per-Artifact Rating | Rationale |
|-----------|-------------------:|---------------------|-----------|
| Security | | [PASS/CONDITIONAL/FAIL] | |
| Maintainability | | [PASS/CONDITIONAL/FAIL] | |
| Economics | | [PASS/CONDITIONAL/FAIL] | |
| Operations | | [PASS/CONDITIONAL/FAIL] | |
| Scoring & Metrics | | [PASS/CONDITIONAL/FAIL] | |
| Correctness Verification | | [PASS/CONDITIONAL/FAIL] | |

**Weight-sensitivity flags:** [list of principles where the score
is most sensitive to design choices]

**Below-threshold flags (if any):** [list of principles scoring
below threshold, with revision-or-acceptance decision]

## §6 — Phase 2 Invalidation Check

| Field | Result |
|-------|--------|
| Does this specification reveal Phase 2 mechanism invalidation? | [Yes / No] |
| If Yes, invalidation report attached | [Reference §6.1 below or "Not applicable"] |

### §6.1 — Invalidation Report (Populated Only If §6 Result Is "Yes")

[Structured invalidation report; folds into Step 06 Phase 2 Amendment
Package.]

| Field | Value |
|-------|-------|
| Phase 2 chosen mechanism (under invalidation) | |
| Why the mechanism cannot be specified coherently | |
| Candidate Phase 2 amendments | |
| Routing recommendation | |

## §7 — Phase 5 Implementability Check

| Field | Result |
|-------|--------|
| Can Phase 5 implement from this specification without ambiguity? | [Yes / No / With pre-implementation tasks] |

### §7.1 — Implementability Gaps (If Any)

| Gap | Type | Resolution |
|-----|------|-----------|
| | | |

## §8 — Forward Handoff Notes

| Recipient Phase | What This Specification Provides | What Recipient Phase Must Do With It |
|----------------|-----------------------------------|-------------------------------------|
| Phase 4 | | |
| Phase 5 | | |
| Phase 6 | | |

## §9 — Cross-Brief References

[References to other briefs whose specifications this artifact
depends on, or which depend on this artifact. Step 04 consumes this
section.]

| Related Brief | Relationship | Reference |
|--------------|--------------|-----------|
| | [Depends on / Provides to / Cross-verifies] | |

**Declare a single source of truth for shared artifacts.** *(Added
in v1.1 per Diamonds Phase 3 dogfooding — P3-Obs-13, Cluster C7.)*
When an artifact is referenced by **three or more briefs** (e.g., an
auditor/verification flow described in a schema brief, an IA doc, and
a verification instrument), name **one owning brief** as its canonical
definition; the others reference that owner rather than restating it.
Restated-in-N-places artifacts drift. List any such 3+-brief artifact
here with its owner; Step 04 §3 (Shared Design Decisions) confirms
the single-owner assignment.

## §10 — Confidence and Code-Access Notes

| Field | Value |
|-------|-------|
| Code-access mode (from Step 00) | [Interview-only / Search-primary / Hybrid] |
| Code-derived claims flagged with | [CONFIRM] / [AWARE] / [QUESTION] as applicable |
| Overall specification confidence | [High / Medium / Low] |
| Specific low-confidence sections | |

---

## Version History

| Version | Date | Source | Summary |
|---------|------|--------|---------|
| v1.0 | [date] | Initial Step 03 production | Per-brief Design Specification produced via [type] sub-template |
```

---

## Evaluation Checklist (Per-Brief — One Checklist Per Step 03 Iteration)

Before this artifact is accepted as complete, verify all items:

- [ ] Brief intake confirmation in §1 is complete; the Phase 2 chosen
      mechanism is loaded with full text (not summary)
- [ ] Artifact type is confirmed against Step 02's classification
- [ ] Step 01 §11.1 gap carryover (if any) is resolved before design
      work began
- [ ] The artifact-type sub-template's questions are answered
      comprehensively; no sub-template section is silently omitted
- [ ] Every claim in §2 is tagged **Design specification** / **Phase
      5 implementation note** / **Phase 6 verification note**
- [ ] No content drifted into Phase 4 architecture territory
      (module boundaries, internal class hierarchies, deployment
      topology)
- [ ] No content drifted into Phase 5 implementation territory
      (concrete code, DDL, configuration syntax)
- [ ] §3 estimate refinement is present if Step 02 flagged the brief
      for it; uses the three-quantity cost model
- [ ] §4 rejected alternatives lists at least one alternative (most
      design work has rejected alternatives; "no alternatives
      considered" is suspicious and worth re-checking)
- [ ] §5 per-artifact principle scorecard contribution is complete
      for all six principles
- [ ] §5 weight-sensitivity flags identify which principle scores
      are most sensitive to the design decisions
- [ ] §5 below-threshold flags (if any) have explicit revision-or-
      acceptance decisions
- [ ] §6 Phase 2 invalidation check is run; if invalidation
      surfaced, §6.1 invalidation report is complete
- [ ] §7 Phase 5 implementability check is run; if gaps surfaced,
      §7.1 names them with resolution paths
- [ ] §8 forward handoff notes are populated for Phases 4, 5, and 6
- [ ] §9 cross-brief references identify related briefs (Step 04
      will consume this)
- [ ] §10 confidence and code-access notes are populated; low-
      confidence sections are named specifically
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)
- [ ] Version history row records the production date and
      sub-template used

---

*Part of the Phase 3 (Existing Projects) Design & Technical Analysis Tool Set — v1.1*
*AI-Centric Software Development Playbook*
*Companion file: `design-technical-analysis.existing-project.instructions.md`*
*Previous step: `step-02-design-brief-triage.prompt.md`*
*Next step: `step-04-inter-artifact-coordination.prompt.md`*

---

## Version History (Of This Prompt File)

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-05-25** | **Initial authoring** | Initial Phase 3 Per-Artifact Design Specification prompt. Unified action-prompt shell with six artifact-type sub-templates (Contract / Refactor / IA / Schema / Observability Touchpoints / Verification Artifacts) plus "Other" with declared shape. Common scaffolding: brief intake confirmation (§1), per-artifact principle scorecard contribution under inherited Phase 2 weights (§5), Phase 2 invalidation check with structured invalidation report (§6), Phase 5 implementability check (§7), forward handoff notes for Phases 4/5/6 (§8), cross-brief references for Step 04 consumption (§9). Phase 5 estimate refinement (§3) populated when Step 02 flagged the brief. Rejected alternatives at specification level (§4) — distinct from Phase 2's mechanism-level rejected alternatives. Per-brief iteration; default one brief per AI session. The three behavioral disciplines unique to Phase 3 (treat Phase 2 chosen mechanism as authoritative; specify at design level not implementation; preserve inherited principle weights) operationalized through the prompt structure. |
| **v1.1** | **2026-07-08** | **Diamonds Phase 3 dogfooding run (Clusters C4, C7)** | (C4, P3-Obs-07) A.4 Conformance Scope now asks the suite's **purpose / lifecycle role** (self-conformance / regression / external conformance) *before* scope or harness location, with a generalized "purpose before mechanism" pattern note for the C/E/F sub-templates. (C7, P3-Obs-12) E.5 adds a **code-observable vs process** watch-trigger classification so process triggers map to "no touchpoint (watched via process)" instead of an invented one. (C7, P3-Obs-13) §9 adds a **single-source-of-truth** rule for artifacts referenced by 3+ briefs (one owning brief; others reference it), confirmed in Step 04 §3. |
