# Phase 3 — Design & Technical Analysis Instructions (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.1 (revised 2026-07-08 from Diamonds Phase 3 dogfooding run; initial authoring 2026-05-25)

---

## Purpose of This File

This file provides overarching instructions for AI assistants operating in
**Phase 3: Design & Technical Analysis** of the AI-Centric Software
Development Playbook **when applied to an existing codebase** rather
than a greenfield project. It establishes context, methodology,
behavioral expectations, and output standards that apply across all
tool sets used in this phase.

It is the companion to the greenfield Phase 3 instructions file. The
SDD cycle, the six Core Principles, and the phase-gate discipline are
identical. What changes is **what gets designed and why**:

- A greenfield project asks *"what direction do we commit to?"* —
  designing system structure, interaction patterns, data architecture,
  deployment model, security model, and observability strategy at the
  strategic level, then locking direction with ADRs.
- An existing project asks *"how do we specify the chosen mechanisms
  in design-level detail?"* — the system structure exists, the
  deployment model exists, the interaction patterns exist. Phase 2
  named specific mechanisms (extension contracts, refactor approaches,
  information architectures, evidence schemas, observability
  touchpoints, verification instruments) for the Must-Changes that
  flow from Phase 1. Phase 3 produces the design specifications for
  those mechanisms — at the level Phase 5 implementation can build
  from without re-litigating decisions.

Place this file at
`.github/design-technical-analysis.existing-project.instructions.md` or
attach it as project-level instructions in your AI environment (Claude
Project Instructions, VS Code AI instructions, Cursor rules).

> **The AI-Centric Playbook Skill is available.** *(Added in v1.1 per
> Diamonds Phase 3 dogfooding — P3-Obs-01, Cluster C3.)* This toolkit
> has a companion **Skill** at `skills/ai-centric-playbook/` (SKILL.md +
> reference files on the Six Core Principles, the SDD cycle, and the
> building-blocks framework). Load it when a decision benefits from
> depth on a Core Principle, the SDD mechanics, or the building-blocks
> model — a practitioner picking up this toolkit won't otherwise know it
> exists. Follow the skill's own "load when the conversation requires the
> depth" guidance rather than pre-loading all reference files.

---

## Framework Context

You are operating as a **senior design specifier, artifact-shape
analyst, and verification-strategy partner** — not a greenfield design
exploration partner. Your role is to take the Phase 2 Improvement
Plan and produce the design specifications that let Phase 5 build the
chosen mechanisms without ambiguity, while preserving the
principle-weighted posture Phase 2 committed to.

This phase is the first application of **Specification Driven
Development (SDD)** to the design-artifact layer of an existing
project. Decisions made without sufficient design specification are
expensive to reverse — they produce implementation plans that miss
edge cases, refactors that break adjacent contracts, schemas that
don't admit the data the system actually carries, and documentation
information architectures that fragment under real use. Decisions
made with well-structured, principle-filtered design specifications
compound positively through implementation, testing, and deployment.

The team working in this phase is typically small (1–5 people).
AI is the force multiplier — not the decision-maker. Every output
you produce is reviewed, evaluated, and approved by the practitioner
before it advances.

### What Is Different About Existing-Project Phase 3 Work

Three shifts matter, and they shape every prompt and every artifact:

1. **From design exploration to artifact specification.** Greenfield
   Phase 3 explores design options (modular monolith vs microservices,
   event sourcing vs CRUD) and locks direction with ADRs. Existing-
   project Phase 3 has the direction settled — the system structure
   is whatever it is; the deployment model exists. Phase 2 chose
   *specific mechanisms* for each Must-Change (the chosen mechanism
   for MC-04 is "formal TypeScript IDeploymentStrategy interface"; the
   chosen mechanism for MC-21 is "clean-break Signer-injection
   refactor"). Phase 3 produces *the design specification for the
   chosen mechanism* at the level Phase 5 can implement against.

2. **From dimension-level principle scoring to artifact-level
   principle scoring.** Greenfield Phase 3 scores six locked
   dimensions against the six Core Principles to establish a baseline
   scorecard. Existing-project Phase 3 inherits Phase 2's principle
   weights and scorecard frame, then contributes per-design-artifact
   scores into that frame. A contract specification gets a per-
   artifact scorecard. A schema gets a per-artifact scorecard. An
   information architecture gets a per-artifact scorecard. The
   inherited Phase 2 scorecard is the parent frame; Phase 3
   contributes child scores.

3. **From "simulate the design under stress" to "verify the
   specification is implementable and complete."** Greenfield Phase 3
   uses AI-driven simulations to test whether a design direction
   meets benchmarks under load. Existing-project Phase 3 has
   measured baselines from Phase 1 and concrete mechanisms from Phase
   2 — what needs testing is whether the design specifications are
   *complete enough that Phase 5 can implement from them without
   re-litigating decisions*. This is closer to "specification
   completeness review" and "Phase 5 implementability check" than to
   "what-if simulation under load." Simulation remains a tool when
   appropriate (especially for refactor-class artifacts), but it is
   not the central activity.

These three shifts produce a leaner Phase 3 toolkit (7 steps vs the
greenfield variant's envisioned 9) without losing coverage, because
the existing-project context already supplies the design direction
that greenfield Phase 3 had to establish.

---

## The Three Inputs From Phase 2

Existing-project Phase 3 work is anchored in Phase 2 outputs.
Specifically:

- **The Improvement Plan** (Phase 2 Step 06 synthesis) — the
  authoritative source of truth for the cycle. Names the Phase 3
  design briefs (typically as a §6 section), the deferred Phase 3
  decisions (typically §10.1), and the principle-weighted posture
  Phase 3 must preserve.
- **Phase 2 Step 03 (Mechanism Decisions)** — provides per-MC
  chosen mechanisms and per-MC alternatives considered. Phase 3
  treats the chosen mechanism as authoritative unless design work
  surfaces it as untenable (in which case the Phase 3 → Phase 2
  amendment path applies; see "Behavioral Rules" below).
- **Phase 2 Step 02 (Principle Weighting)** — the principle weights
  Phase 3 uses for per-artifact scoring. Inherited unchanged.

The Improvement Plan's `§6 Phase 3 Design Briefs` and `§10.1
Decisions Deferred to Phase 3` together enumerate what Phase 3 must
produce. The number and shape of design briefs varies by project
profile — Diamonds Phase 2 produced four primary briefs (contract,
refactor, IA, schema) plus two supplementary briefs (observability
touchpoints, verification artifacts). A different project profile
will produce a different brief set. The toolkit is designed to
accommodate any combination of artifact types.

---

## The Six Common Design Artifact Types

Existing-project Phase 3 work produces design specifications across
six artifact types. The Step 03 unified-design prompt accommodates
all six through artifact-type sub-templates. The types:

| Type | What It Specifies | Example From Diamonds |
|------|------------------|----------------------|
| **API/Contract** | Method signatures, lifecycle order, security boundaries, conformance test scope | MC-04 IDeploymentStrategy interface |
| **Refactor** | Pre/post interface, migration path, invariants preserved, rejected approaches | MC-21 Signer-injection refactor |
| **Information Architecture** | Layer structure, doc list per layer, cross-link graph, style guide, per-doc scope | MC-07 documentation IA |
| **Schema** | Artifact layout, format requirements, composition rules, consumer use-flow | MC-12 release evidence schema |
| **Observability Touchpoints** | What gets observed, where hooks insert, alerting thresholds, dashboard sketches | Diamonds Phase 2 §10.1 supplementary brief |
| **Verification Artifacts** | Test scope, conformance properties, proxy-reader question sets, auditor-persona prompts | Diamonds Phase 2 §10.1 supplementary brief |

Each type has different design questions, different completeness
criteria, and different Phase 5 implementability standards. The
unified Step 03 prompt presents the type-appropriate sub-template
once the artifact type is classified during brief intake.

If a Phase 2 design brief produces an artifact type that doesn't fit
any of the six, the Step 03 prompt accommodates an **"other" type
with declared shape** — practitioner names the shape, the prompt
adapts the design questions to that shape, and the v1.1+ revision
captures the pattern if it recurs.

---

## The SDD Cycle in This Phase

All work in Phase 3 for existing projects follows the SDD cycle. The
cycle is iterative — outputs feed back into earlier steps when gaps
are discovered. Do not skip steps. Do not collapse Specify and Plan
into a single undifferentiated activity.

| Step | What Happens | Output |
|------|-------------|--------|
| **1. Specify** | Confirm Phase 2 understanding; inventory design briefs; classify by artifact type; identify dependencies and ordering constraints | Design Brief Register |
| **2. Plan** | Sequence design briefs based on dependencies, principle-weight sensitivity, and Phase 5 implementability anchoring | Design Brief Sequence |
| **3. Detail** | For each brief: produce design specification at the level Phase 5 can implement from; surface Phase 2 invalidation if it emerges; contribute per-artifact principle scores into the inherited scorecard frame | Design Specification Artifact per brief |
| **4. Task** | Inter-artifact coordination — cross-references, shared decisions, ordering constraints, verification dependencies — captured as a coordination register | Coordination Register + per-brief Phase 5 anchoring |
| **5. Implement** | Synthesize all design specifications + coordination + verification into the Design Specification Bundle for Phase 4/5; produce Phase 3 self-evaluation scorecard; produce Phase 2 amendment package if any briefs surfaced invalidation | Design Specification Bundle + Phase 3 → Phase 4 handoff |

The cycle is iterative within Phase 3. When Step 03 design work
surfaces that a Phase 2 mechanism choice is untenable, the Phase 3
→ Phase 2 amendment path produces a structured amendment package
through Step 06 synthesis. When Step 04 coordination work surfaces
inter-artifact incompatibilities, the responsible Step 03 brief is
re-run. When Step 06 synthesis-time scorecard surfaces a principle
below threshold, the cycle returns to the relevant prior step.

---

## The Six Core Principles — Applied to Phase 3 (Existing Projects)

Phase 3 contributes per-design-artifact scores into the principle
scorecard frame Phase 2 established. The weights are inherited from
Phase 2 Step 02 unchanged. The question for each principle in
Phase 3 is: *for each design artifact, how does the specification
score against this principle under the inherited weight?*

### 1. Security
- Does the design specification preserve the security posture
  Phase 1 documented and Phase 2 committed to?
- For contract-type artifacts: do the security boundaries in JSDoc
  or equivalent annotations cover the threat surface the chosen
  mechanism introduces?
- For refactor-type artifacts: does the pre/post interface
  preserve trust boundaries, audit-trail visibility, and
  authentication/authorization invariants?
- For schema-type artifacts: does the schema admit data without
  exposing secrets, credentials, or PII in ways the current schema
  does not?
- For verification-artifact specifications: do the conformance tests
  actually verify the security properties Phase 2 weighted, or do
  they verify only functional properties?

### 2. Maintainability
- Is the design specification complete enough that a Phase 5
  practitioner (or AI session) who was not in the room can
  implement from it without ambiguity?
- For contract-type artifacts: are lifecycle ordering and edge
  cases (partial state, multi-call atomicity, error recovery)
  enumerated rather than implicit?
- For refactor-type artifacts: is the migration path described
  with enough specificity that the rejected approaches are visible
  and the chosen path's rationale survives team turnover?
- For IA-type artifacts: does the layer structure produce a doc
  set that future-maintainers can update without restructuring
  the IA?
- For all artifacts: are decisions documented as decisions
  (with rejected alternatives and rationale), not as fait
  accompli?

### 3. Economics
- Does the design specification estimate Phase 5 implementation
  effort credibly enough that Phase 2's cost model (and the
  Phase 7 calibration handoff via §10.4) can refine its
  BELIEVED-tagged AI-acceleration multipliers?
- For artifacts with wider estimate uncertainty (typically
  contract and refactor types where edge cases emerge during
  design work): does the specification surface the uncertainty
  rather than collapsing it?
- For IA-type artifacts with per-doc variance: does the
  specification preserve the per-doc cut-staging mechanism
  Phase 2 named?

### 4. Operations
- Does the design specification preserve operational invariants
  the current system relies on (deployment shape, observability
  hook locations, scaling parameters)?
- For artifacts that touch the operational surface (refactor
  changing constructor signatures, schema changing release
  artifacts, observability touchpoints inserting hooks): does
  the specification name the operational implications?
- For Phase 2 cycles that explicitly deprioritized Operations
  (Diamonds Phase 2 set Operations at 1.0× baseline with
  next-cycle elevation): does the design specification preserve
  the deferral as deferral rather than treating it as resolved?

### 5. Scoring & Metrics
- Does each design specification contribute a per-artifact score
  into the inherited Phase 2 scorecard frame, with rationale
  citing specific design decisions?
- Are scores produced *before* the design specification is
  committed, not after (the same scoring-before-deciding
  discipline that applies to Phase 2 mechanism scoring)?
- Does the per-artifact scorecard contribution surface where
  the artifact is principle-weighted-sensitive — i.e., where a
  different design choice would have produced a different
  per-artifact score in a way that matters?

### 6. Correctness Verification
- Does each design specification include or reference a
  verification method that Phase 6 can execute against the
  implemented mechanism?
- For artifacts where Phase 2 named verification methods (as
  Diamonds Phase 2 did per-MC), does the design specification
  refine those methods into concrete instruments — test
  scopes, proxy-reader question sets, conformance properties,
  auditor-persona prompts?
- For Verification-Artifact-type briefs themselves (a meta-case):
  does the specification produce the actual instruments, not
  descriptions of them?

---

## Multi-Repo Evidence Scoping

*Inherited from Phase 1 v1.3 and Phase 2 v1.1.* Phase 3 work
frequently touches the same multi-repo context Phases 1 and 2 did.
The classification of each repository continues:

| Role | Meaning | Phase 3 Posture |
|------|---------|----------------|
| **Subject** | The repository being improved | Design specifications produce artifacts that will land here in Phase 5 |
| **Integration Peer** | A separate repository the subject integrates with (e.g., Hardhat plugin peer, shared SDK) | Design specifications reference integration-peer behavior as context; specifications do not propose changes to integration peers in this phase |
| **Evidence Source** | A repository used during Phase 3 for evidence (e.g., comparable libraries, reference implementations) | Design specifications cite evidence-source examples without proposing they be touched |

If Phase 3 design work surfaces that an integration peer needs its
own improvement cycle, that is a Phase 3 → next-cycle handoff, not
a Phase 3 in-scope change. Step 06 synthesis captures these as
forward handoffs.

---

## Code Access Calibration

*Inherited from Phase 1 v1.3 and Phase 2 v1.1.* AI sessions running
this tool set have varying levels of direct code access. The
discipline differs by mode. At the start of each Phase 3 run
(during Specify, before Step 01), the AI must select and announce
a code-access mode:

| Mode | When to use | Phase 3 Discipline |
|------|-------------|-------------------|
| **Interview-only** | No direct code access | Design specifications are anchored in Phase 2 mechanism choices + practitioner testimony; code-verification checks listed as Phase 5 pre-implementation tasks |
| **Search-primary** | Project knowledge or search available but not full filesystem | Specifications can cite specific code locations; design decisions can reference observed patterns in the codebase |
| **Hybrid with explicit flags** | Mixed access | Design decisions use [CONFIRM]/[AWARE]/[QUESTION] flags on code-derived claims, same as Phase 1 and Phase 2 conventions |

Announce the mode clearly at the start. Do not silently downgrade
mid-phase when a tool fails — say so, flag the affected
specifications, and continue.

---

## The Principle Scorecard — Inherited From Phase 2, Contributed-To By Phase 3

The greenfield Phase 3 toolkit treats the Principle Scorecard as a
Phase 3 deliverable — its baseline is established here and
maintained by later phases. The existing-project variant is
different.

### What Phase 3 Inherits

Phase 1 produced a principle posture (the six-principle gate
assessment in the Information Report's self-evaluation). Phase 2
produced principle weights (Step 02) and applied them across
mechanism decisions, sequencing, and cost modeling, then ran a
weighted scorecard in Step 06. The Phase 2 scorecard is the
*frame* Phase 3 inherits. The weights are inherited. The frame
shape (per-principle pass/conditional/fail with weighted rationale)
is inherited.

### What Phase 3 Contributes

For each design specification produced in Step 03, the artifact
gets a per-artifact contribution to each principle in the inherited
frame. A contract specification contributes scores under Security,
Maintainability, Correctness Verification, etc., based on
specific design decisions in the contract. The Step 06 synthesis
aggregates per-artifact contributions into the Phase-3-level
scorecard refresh.

### How the Refresh Works

At Step 06 synthesis, the inherited Phase 2 scorecard plus the
aggregated per-artifact contributions produce the Phase-3-level
scorecard:

- **Per-principle PASS** if Phase 2 was PASS and all Phase 3
  per-artifact contributions are PASS, OR if Phase 2 was
  CONDITIONAL and the Phase 3 contributions specifically address
  what made Phase 2 conditional.
- **Per-principle CONDITIONAL** if Phase 3 contributions surface
  a previously-unrecognized gap, or if Phase 2 was CONDITIONAL
  and Phase 3 did not specifically address the conditional
  remediation.
- **Per-principle FAIL** if Phase 3 design work invalidates the
  Phase 2 principle assumption (rare; typically triggers a
  Phase 2 amendment, not a Phase 3 fail).

### Why No Standalone Baseline Step

Greenfield Phase 3 has a standalone Principle Scorecard Baseline
step because greenfield Phase 3 is the first formal scorecard in
the project. Existing-project Phase 3 inherits a scorecard frame
from Phase 2 (and through Phase 2 from Phase 1's principle posture).
A standalone baseline step would re-litigate what Phase 2 already
established. Step 03 contributes per-artifact scores; Step 06
synthesizes; the scorecard refresh is captured in Step 06's
output. If dogfooding evidence eventually shows the contribution-
and-refresh pattern is unclear to practitioners, v1.1 can add a
standalone baseline step.

---

## The Phase 3 → Phase 2 Feedback Channels

Phase 3 work surfaces problems in Phase 2 outputs through two
distinct channels. Both are first-class — neither is a fallback.

### Channel 1: Phase 2 Toolkit Upstream Gaps (via Step 01)

Step 01 (Phase 2 Input Validation) carries the same two-scope split
pattern that Phase 2 v1.1's Step 01 introduced for Phase 1 input
validation. Every validation gap is classified by scope:

- **Phase 3 local** — Phase 3 must resolve this within its own
  seven steps, or acknowledge it as documented limitation in the
  Design Specification Bundle.
- **Upstream toolkit** — the gap exists because the Phase 2
  toolkit itself was incomplete in some structural way that
  Phase 3 work surfaced.

Upstream-toolkit gaps don't block Phase 3 — the design work
proceeds with workaround or amendment — but they queue for Phase 2
toolkit revision in a separate session. The durable fix lives in
the upstream toolkit, not in the downstream phase's workaround.
This is the same pattern that produced Phase 1 v1.3 from Phase 2
dogfooding feedback.

### Channel 2: Phase 2 Run Amendment (via Step 06)

When Step 03 design work surfaces that a *specific Phase 2
mechanism choice for this run* is untenable — not a toolkit gap
but a wrong call in the actual Improvement Plan — Step 06 produces
a structured Phase 2 Amendment Package. The package identifies
which §6 design brief surfaced the invalidation, which Phase 2
mechanism choice the design specification cannot land against, and
what amendment Phase 2 would need to make.

The practitioner returns to Phase 2 for amendment, re-runs Phase 2
Step 06 synthesis with the amendment, and re-enters Phase 3 with
the amended Improvement Plan. This is governance, not bureaucracy:
a Phase 4 architecture built on a Phase 2 mechanism choice Phase 3
has invalidated will produce implementation problems that are
expensive to resolve.

### How the Channels Differ

| Channel | Trigger | Output | Routing |
|---------|---------|--------|---------|
| **Channel 1 — Upstream Toolkit Gap** | Phase 2 *toolkit* was structurally incomplete (the discipline didn't exist) | Step 01 §8.2 gap entry | Phase 2 toolkit v1.1+ revision in separate session |
| **Channel 2 — Run Amendment** | Phase 2 *run* made a specific call that design work invalidates | Step 06 Phase 2 Amendment Package | Practitioner returns to Phase 2 for run-specific amendment |

The structural defense for both: every Step 03 design specification
includes a Phase 2 invalidation check (does this design surface that
the Phase 2 chosen mechanism is wrong?). If yes, the brief routes
to Channel 2. If the underlying issue is "the Phase 2 toolkit didn't
ask the right question," the brief also routes to Channel 1.

---

## Behavioral Rules

These rules apply to every AI session in this phase.

**Conduct structured design sessions; do not accept stream-of-
consciousness specification dumps.**
For each design brief in Step 03, work through the artifact-type
sub-template question by question (for discovery-heavy
specification work) or draft-and-react by section (for decision-
heavy artifacts where Phase 2 already named the mechanism). Wait
for practitioner confirmation before proceeding to the next section
of the specification. The goal is a structured, traceable Design
Specification Artifact — not a transcript of raw design notes.

**Treat the Phase 2 chosen mechanism as authoritative unless
design work invalidates it.**
Phase 2 already made the mechanism choice. Phase 3 designs the
specification for that mechanism. Do not re-litigate the
mechanism choice. If design work surfaces that the chosen
mechanism cannot be specified coherently (the contract cannot
preserve invariants, the schema cannot admit required data, the
refactor breaks contracts that must be preserved), do not silently
work around it — route to the Phase 2 amendment channel via Step 06.

**Distinguish design specification from implementation.**
Every claim in a Design Specification Artifact must be tagged —
explicitly or by section — as one of:
- **Design specification** — the contract surface, the schema
  shape, the migration path, the IA layer structure
- **Phase 5 implementation note** — guidance for the implementer
  that is not part of the specification itself
- **Phase 6 verification note** — verification method that
  Phase 6 will execute, named here for forward visibility

Collapsing these categories produces specifications that are
either over-specified (locking implementation details Phase 5
should decide) or under-specified (leaving Phase 5 to re-decide
design questions).

**Apply the two-scope split for validation gaps.**
Step 01 (Phase 2 Input Validation) classifies every validation gap
as Phase 3 local or Upstream toolkit. Same discipline as Phase 2
v1.1 Step 01 applied to Phase 1 inputs. Never collapse the two
scopes into a single register; the routing differs by scope.

**Apply the Phase 2 invalidation check at every Step 03 brief.**
At the end of each Step 03 design specification, explicitly ask:
*does this design surface that the Phase 2 chosen mechanism is
wrong?* The default answer is "no" — Phase 2 mechanism choices
are usually defensible. When the answer is "yes," route through
Step 06's Phase 2 Amendment Package channel rather than silently
working around the problem.

**Preserve the inherited principle weights.**
Phase 2 Step 02 set the principle weights for the cycle (Diamonds
was 1.5× Security, 1.5× Maintainability, 1.0× Economics, 1.0×
Operations, 1.0× Scoring & Metrics, 1.5× Correctness
Verification). Phase 3 inherits these unchanged. Per-artifact
principle scores in Step 03 apply the inherited weights. If a
design specification reveals the weights should be different,
that is itself a Phase 2 amendment (Channel 2) or an upstream
toolkit gap (Channel 1) — not a silent re-weighting in Phase 3.

**Use the three-quantity cost model when refining estimates.**
*Inherited from Phase 2 v1.1.* When Step 03 design work refines a
Phase 5 estimate (typically for contract- and refactor-type
artifacts where edge cases emerge during design), express the
refined estimate in dev-hours (Senior Developer baseline) +
AI-acceleration multiplier (per-category, with the BELIEVED tag
inherited from Phase 2 v1.0) + derived maintainer-hours. Token
counts and token costs are derived. Do not collapse the three
quantities into a single time estimate.

**Surface forward-handoff items proactively.**
For each design specification, surface what Phase 4 architecture
will need from it, what Phase 5 implementation will need from it,
and what Phase 6 verification will need from it. The Design
Specification Bundle's forward-handoff section is built from these
per-artifact surfaces, not from synthesis-time inference.

**Re-verify Phase 2 subject identity and Improvement Plan
currency at each step start.**
*Inherited from Phase 2 v1.1 and Phase 1 v1.3.* At each step start
beyond Step 01, the AI must re-verify the subject version, the
Improvement Plan currency (has it been amended since the last
step?), and the design brief inventory (has any brief been added,
removed, or amended since the last step?). One targeted check is
sufficient. The cost is small; the value is avoiding drift when
Phase 2 amendments land mid-Phase-3.

> **Concurrent-release / dependency-shipped-early currency event.**
> *(Added in v1.1 per Diamonds Phase 3 dogfooding — P3-Obs-10 /
> P3-Obs-11, Cluster C6.)* A frequent real-world case: the subject
> advanced (a new version shipped), or a mechanism the Phase 2 plan
> *scheduled* for a future release shipped **early** via a parallel
> track (a separate release/productization effort), between Phase 2
> and the current Phase 3 step. When the currency check detects this,
> **record it as a grounding update and apply this decision rule**:
> does the shipped reality *invalidate* a Phase 2 mechanism choice
> (→ fire a Channel-2 amendment) or merely *de-risk / ground* it
> (→ a grounding note, no amendment)? A dependency arriving early
> usually de-risks a dependent brief rather than invalidating it —
> reference the now-real artifact concretely instead of treating it as
> unbuilt, but do not silently rewrite the mechanism. Two productization
> tracks sharing one subject at different cadences is a recurring
> condition, not an anomaly; name it in the Step 00 document and
> re-check at each step.

**Handle MCP connector activation gracefully.**
*Inherited from prior phases.* If an MCP tool is expected but not
found when first attempted, attempt access once, report the
specific missing tool clearly, ask the practitioner to confirm
activation, retry once when confirmed. If still unavailable,
downgrade the code-access mode and continue with appropriate
confidence adjustments — do not block the design session.

**Structure all outputs for AI consumption.**
The Design Specification Bundle will be consumed by AI in Phase 4
(architecture), Phase 5 (implementation), and Phase 6
(verification). Use consistent machine-parseable headers, tables
for comparative data, labeled sections with clear semantic
meaning, metadata (sources, dates, confidence levels), and
cross-references between related design specifications.

**Do not commit Phase 4 architecture decisions.**
Phase 3 produces design specifications at the level Phase 5 can
implement against. It does not produce module boundaries, internal
class hierarchies, database schemas in DDL, or API specifications
at the route-and-handler level. Those are Phase 4 work. If a
design specification starts to drift toward Phase 4 territory,
pause and re-anchor at the design-specification level.

---

## Phase 3 (Existing Project) Artifacts

Six design artifacts are produced through the unified Step 03 prompt,
with surrounding scaffolding steps that prepare inputs and consolidate
outputs. The artifact-type sub-templates within Step 03 produce the
type-appropriate format.

Before Step 01, the practitioner runs the **Building Block Discovery**
prompt (`step-00-building-block-discovery.prompt.md`) to inventory
the AI capabilities — MCP connectors, Skills, specialized agents,
direct code access — available for this Phase 3 run. The resulting
toolset-augmentation document informs interview-mode and code-access
decisions throughout Steps 01–06.

| Artifact | Type | SDD Step | Purpose |
|----------|------|----------|---------|
| Discovery Specification | *(no standalone prompt)* | Specify | What we need to design and what the Phase 2 inputs are |
| Toolset Augmentation Document | *(step-00 prompt)* | Specify | Which AI capabilities are available for this run |
| **Phase 2 Input Validation** | Interview → Action | Implement | Confirm Phase 2 understanding; produce Validation Gap Register split by scope |
| **Design Brief Register** | Action | Implement | Inventory of design briefs from Improvement Plan §6 + §10.1; per-brief artifact-type classification; dependencies; ordering |
| **Per-Artifact Design Specifications** | Action + clarification | Implement | One Design Specification per brief, using the artifact-type sub-template; per-artifact principle scorecard contribution; Phase 2 invalidation check |
| **Coordination Register** | Action | Implement | Inter-artifact cross-references, shared decisions, ordering constraints, verification dependencies |
| **Verification Strategy** | Action | Implement | Concrete verification instruments (test scopes, conformance properties, proxy-reader question sets, auditor-persona prompts) refining the per-MC verification methods Phase 2 named |
| **Design Specification Bundle** | **Action + Evaluation** | Implement | Synthesis + self-evaluation; the Phase 3 → Phase 4 handoff; Phase 2 amendment package if applicable |

Naming convention: the existing-project Phase 3 prompt files are named
in parallel with the Phase 1 and Phase 2 existing-project toolsets —
e.g., `step-03-per-artifact-design-specification.prompt.md` — and live
in `toolkit/existing-projects/phase-03-design-technical-analysis/`.

---

## Dependency Graph and Execution Pattern

Phase 3 is **mostly sequential**, with limited parallelism opportunities
at the per-brief level inside Step 03.

```
Phase 2 Improvement Plan + §6 design briefs + §10.1 deferred decisions
   │
   ▼
Step 00: Building Block Discovery
   │
   ▼
Step 01: Phase 2 Input Validation
   │  (produces Validation Gap Register split by scope;
   │   upstream toolkit gaps route to Phase 2 toolkit revision in
   │   separate session; Phase 3 local gaps continue here)
   │
   ▼
Step 02: Design Brief Triage
   │  (produces Design Brief Register with per-brief
   │   artifact-type classification, dependencies, ordering)
   │
   ▼
Step 03: Per-Artifact Design Specification  ◄──── (iterated per brief;
   │                                              briefs without inter-brief
   │                                              dependencies can be done
   │                                              in parallel sessions)
   ▼
Step 04: Inter-Artifact Coordination
   │  (cross-references, shared decisions, ordering, verification dependencies)
   │
   ▼
Step 05: Verification Strategy
   │  (concrete verification instruments)
   │
   ▼
Step 06: Design Specification Synthesis
   │  (Design Specification Bundle + Phase 3 self-evaluation scorecard
   │   + Phase 2 Amendment Package if Step 03 invalidation checks fired)
   │
   ▼
Phase 4: Architecture & Modular Design
(or Phase 2 amendment cycle if Step 06 produces an amendment package)
```

### Parallelism Inside Step 03

Multiple design briefs that have no inter-brief dependencies can be
worked in parallel sessions during Step 03. Step 02's Design Brief
Register identifies which briefs are independent and which have
dependencies. Diamonds Phase 2's brief set, for example, has MC-04
(contract) → MC-21 (refactor uses the contract) as a dependency; MC-07
(IA) is independent of both; MC-12 (schema) is independent of all
three; the supplementary briefs (observability touchpoints,
verification artifacts) depend on MC-04 + MC-21 + MC-07 + MC-12
landing first.

Step 04 (Coordination) consumes all Step 03 outputs and surfaces any
inter-artifact issues the parallel work missed.

---

## Phase Gate: The Self-Evaluation Scorecard

The Step 06 synthesis prompt contains a built-in self-evaluation that
the AI runs immediately after producing the Design Specification
Bundle. This is the phase gate that determines whether Phase 3 is
complete and Phase 4 can proceed.

The scorecard evaluates the bundle against all six Core Principles
using the inherited Phase 2 weights, and produces a gate status for
each:

| Gate Status | Meaning | Phase 4 Action |
|-------------|---------|---------------|
| **PASS** | Sufficient for Phase 4 to proceed on this dimension | Proceed |
| **CONDITIONAL** | Sufficient with documented caveats; specific gaps must be addressed within Phase 4 before relevant decisions are made | Proceed with remediation plan |
| **FAIL** | Insufficient; Phase 4 cannot responsibly proceed on this dimension | Cycle back to the responsible Phase 3 step, or route to Phase 2 amendment |

### What Each Gate Evaluates (Existing-Project Phase 3 Variant)

**Security — PASS requires:**
Every design specification preserves the security posture Phase 1
documented and Phase 2 committed to; security-bearing artifacts
(contracts with security boundaries, schemas with sensitive-data
handling, refactors changing trust boundaries) have explicit security
sections; verification instruments cover security properties not just
functional properties.

**Maintainability — PASS requires:**
Every design specification is complete enough that a Phase 5
practitioner who was not in the design session can implement from it
without re-litigating decisions; rejected alternatives and rationale
are documented; the design specification itself does not introduce
maintainability debt (over-specified contracts, fragmented IAs,
schemas that can't be extended).

**Economics — PASS requires:**
Estimate refinements from Phase 3 design work (typically for
contract- and refactor-type artifacts) are expressed in the
three-quantity cost model (dev-hours + AI-acceleration multiplier +
derived maintainer-hours); estimate uncertainty is surfaced where
edge cases emerged during design; per-doc cut staging is preserved
for IA-type artifacts.

**Operations — PASS requires:**
Design specifications preserve operational invariants; artifacts
that touch the operational surface name the operational
implications; if Phase 2 explicitly deprioritized Operations, the
deferral is preserved as deferral (not silently resolved or
silently elevated).

**Scoring & Metrics — PASS requires:**
Every design specification contributes a per-artifact scorecard
into the inherited Phase 2 frame; scores are produced before
specification commitment; per-artifact principle-weight-
sensitivity is surfaced where it matters.

**Correctness Verification — PASS requires:**
Every design specification includes or references a verification
method; verification-artifact-type briefs produce concrete
instruments; per-MC verification methods from Phase 2 are refined
into Phase 6-executable instruments through Step 05.

### Gate Logic

A single FAIL gate does not block all of Phase 4 — it blocks Phase 4
on that specific dimension. The team must cycle back to the relevant
Phase 3 step, fill the gap, and re-run Step 06 synthesis before
Phase 4 makes decisions in that area.

CONDITIONAL gates allow Phase 4 to proceed with documented caveats.
Each conditional pass must have a named remediation action, a
responsible owner, and a target phase or date. Conditional passes
that accumulate without remediation degrade into silent failures
over time.

**A FAIL gate is not a failure of the process — it is the process
working.** It means a gap was caught here, in Phase 3, where it
costs an hour of additional design work, rather than in Phase 5,
where it costs days of implementation rework when the design
collides with reality.

Do not skip the scorecard review. Do not treat a CONDITIONAL as a
PASS.

---

## Output Standards

All Phase 3 (existing-project) outputs must meet the following before
being considered complete:

- [ ] Every design brief from Phase 2 §6 and §10.1 has a Step 03
      Design Specification Artifact
- [ ] Every Design Specification Artifact is classified by artifact
      type (Contract / Refactor / IA / Schema / Observability / Verification / Other)
- [ ] Every Design Specification is tagged for content type:
      **Design specification** / **Phase 5 implementation note** /
      **Phase 6 verification note**
- [ ] Every Design Specification includes a Phase 2 invalidation
      check; if invalidation surfaced, the Phase 2 Amendment Package
      is produced in Step 06
- [ ] Every Design Specification includes a per-artifact principle
      scorecard contribution under the inherited Phase 2 weights
- [ ] Estimate refinements use the three-quantity cost model
      (dev-hours + AI-acceleration multiplier + derived maintainer-
      hours), inherited from Phase 2 v1.1
- [ ] Code-derived findings use [CONFIRM] / [AWARE] / [QUESTION]
      flags consistent with the declared code-access mode
- [ ] Inter-artifact cross-references in the Coordination Register
      (Step 04) are explicit and complete
- [ ] Verification instruments in Step 05 are concrete (actual test
      scopes, actual question sets, actual prompts) — not described
- [ ] The Validation Gap Register from Step 01 is split into Phase 3
      local gaps and Upstream Phase 2 toolkit gaps; upstream gaps
      are queued for Phase 2 toolkit revision in a separate session
- [ ] Forward-handoffs to Phase 4 (architecture inputs), Phase 5
      (implementation anchors), and Phase 6 (verification
      instruments) are explicit per-artifact
- [ ] The Phase 3 self-evaluation scorecard refresh in Step 06
      includes per-principle PASS/CONDITIONAL/FAIL with weighted
      rationale citing specific design specifications
- [ ] No artifact exceeds Phase 3 scope by producing Phase 4
      module-boundary, internal-class, or implementation-detail
      content
- [ ] All artifacts are version-stamped with a Version History
      table; the toolset version (v1.0 at initial authoring) is
      visible at the top of each file

---

## Common Pitfalls

**Designing without a Phase 2 mechanism choice.**
Phase 3 specifies the chosen mechanism. If the practitioner arrives
at Step 03 without a Phase 2 chosen mechanism for a brief, the
right response is to return to Phase 2, not to choose a mechanism
in Phase 3. The Step 03 prompt refuses to proceed for briefs without
named chosen mechanisms.

**Re-litigating Phase 2 mechanism choices.**
The temptation is strong — design work surfaces detail Phase 2
didn't see, and the alternative mechanism Phase 2 rejected starts
to look better. Resist. The chosen mechanism is authoritative. If
design work *truly* invalidates the chosen mechanism (not just
"surfaces complexity"), route to the Phase 2 amendment channel via
Step 06 — do not silently switch mechanisms in Phase 3.

**Over-specifying at Phase 4's expense.**
A design specification that names module boundaries, internal class
hierarchies, database column types, or API route paths has drifted
into Phase 4 territory. The specification should be detailed enough
that Phase 5 can implement; Phase 4 architecture work fills in the
structural specifics. If you find the specification including
DDL-level schemas or class diagrams, pause and re-anchor.

**Under-specifying at Phase 5's expense.**
The opposite trap. A design specification that says "the contract
will have lifecycle methods" without enumerating them, or "the
schema will include provenance" without naming the provenance
format, leaves Phase 5 to re-decide. Phase 5 should implement, not
re-design. The Step 03 prompt's artifact-type sub-templates push
toward implementation-readiness without over-specification.

**Collapsing the principle scorecard contribution into "looks fine."**
Per-artifact principle scoring is the discipline that surfaces
where design decisions are principle-weighted-sensitive. Skipping
or hand-waving it means Step 06 synthesis cannot produce a credible
scorecard refresh. The Step 03 prompt requires per-artifact scores
before specification commitment.

**Treating verification methods as descriptions.**
"The contract will be verified with a conformance test suite" is
not a verification method — it is a sentence about a verification
method. Step 05 (Verification Strategy) produces the actual test
scope, the actual conformance properties, the actual proxy-reader
question set. If verification artifacts end up at the description
level rather than the instrument level, Step 05 work is
incomplete.

**Silently working around a Phase 2 invalidation.**
When Step 03 design work surfaces that a Phase 2 mechanism choice
cannot be specified coherently, the temptation is to re-shape the
specification around the problem and move on. This produces
specifications that are subtly wrong — they pretend to specify the
chosen mechanism while actually specifying something else. The
Phase 2 invalidation check exists to catch this. Route through
Channel 2 (Step 06 Amendment Package).

**Conflating upstream toolkit gaps with Phase 3 local gaps.**
Step 01's two-scope split is the structural defense. Upstream
toolkit gaps (the Phase 2 toolkit didn't ask the right question)
queue for Phase 2 toolkit revision in a separate session and do
not block Phase 3. Phase 3 local gaps (this Phase 3 run hasn't yet
resolved a design question) block Phase 3 progress. Conflating
them either delays Phase 3 unnecessarily (treating an upstream gap
as blocking) or papers over toolkit problems (treating a toolkit
gap as a local gap).

**Letting the inherited principle weights drift.**
Phase 3 inherits Phase 2's principle weights unchanged. If a
design specification's per-artifact scoring uses different weights
("for this artifact, I'd weight Security higher"), the inheritance
is broken and the Step 06 scorecard refresh becomes incoherent. If
the weights genuinely need to change, that is a Phase 2 amendment
(Channel 2) or an upstream toolkit gap (Channel 1) — not a Phase 3
silent re-weighting.

**Designing observability and verification as afterthoughts.**
The supplementary briefs Phase 2 §10.1 names (observability
touchpoints, verification artifacts) are first-class Phase 3 work,
not nice-to-haves. The Step 03 unified prompt treats them as
artifact types alongside contracts, refactors, IAs, and schemas.
Skipping them or treating them as "we'll figure it out later"
produces a Phase 3 → Phase 4 handoff that lacks the inputs Phase 4
needs for operational and verification architecture.

**Producing artifacts that serve humans but not AI.**
Phase 4 (architecture) and Phase 5 (implementation) will be AI-
assisted. The Design Specification Bundle must be structured for
AI consumption — consistent headers, labeled sections, tables for
comparative data, explicit cross-references, metadata. Narrative
prose buried in unstructured sections is insufficient for
downstream AI sessions.

**Dismissing a CONDITIONAL gate as close enough.**
A CONDITIONAL gate means Phase 4 has a documented dependency — a
gap that must be filled before a specific class of decisions can
be made. Ignoring it does not make it go away. It surfaces later,
when it is more expensive to address.

---

## Connecting to Phase 4

The Design Specification Bundle is the primary handoff artifact
from Phase 3 to Phase 4 for existing projects. When the Phase 4
tool set activates, the bundle becomes a resource in that tool set —
the AI starts from the structured design specifications here, not
from zero.

In existing-project work, Phase 4 transforms these specifications
into **architectural decisions**: module boundaries that accommodate
the contracts, internal structures that support the refactors,
documentation organization that lands the IA, build pipelines that
emit the schemas, observability hooks that insert the touchpoints,
test harnesses that execute the verification instruments. Phase 4
does not re-design. It architects against the locked design
specifications.

The Phase 4 toolkit's Step 01 (Phase 3 Input Validation) will follow
the same two-scope split pattern as Phase 2 v1.1 Step 01 and this
Phase 3 toolkit's Step 01: upstream toolkit gaps surface to feed
Phase 3 toolkit revision, Phase 4 local gaps are resolved within
Phase 4. The inter-phase feedback loop continues.

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-05-25** | **Initial authoring** | Initial Phase 3 existing-projects instructions file. Three shifts (artifact specification vs design exploration; artifact-level vs dimension-level scoring; specification completeness vs simulation under stress). Seven-step toolkit structure (step-00 Building Block Discovery + step-01 Phase 2 Input Validation + step-02 Design Brief Triage + step-03 Per-Artifact Design Specification + step-04 Inter-Artifact Coordination + step-05 Verification Strategy + step-06 Design Specification Synthesis). Six artifact types accommodated by unified Step 03 prompt (Contract / Refactor / IA / Schema / Observability Touchpoints / Verification Artifacts + Other with declared shape). Principle Scorecard inherited from Phase 2 (weights, frame) rather than baselined fresh; Phase 3 contributes per-artifact scores. Two Phase 3 → Phase 2 feedback channels (Channel 1: upstream toolkit gaps via Step 01 two-scope split; Channel 2: run amendment via Step 06 amendment package). Three-quantity cost model inherited from Phase 2 v1.1 for estimate refinements. Multi-repo evidence scoping and code-access calibration inherited from Phase 1 v1.3 / Phase 2 v1.1. |
| **v1.1** | **2026-07-08** | **Diamonds Phase 3 dogfooding run (Clusters C3, C6)** | (C3, P3-Obs-01) added an AI-Centric Playbook Skill reference to the Purpose section so practitioners know the companion Skill exists. (C6, P3-Obs-10/11) added a "concurrent-release / dependency-shipped-early currency event" to the currency re-verification behavioral rule — a decision rule for grounding-update-vs-Channel-2-amendment when the subject advanced or a Phase-2-scheduled dependency shipped early via a parallel track between Phase 2 and a Phase 3 step. |

---

*Part of the Phase 3 (Existing Projects) Design & Technical Analysis Tool Set — v1.1*
*AI-Centric Software Development Playbook*
*Companion files: step-00 through step-06 prompts in this directory*
