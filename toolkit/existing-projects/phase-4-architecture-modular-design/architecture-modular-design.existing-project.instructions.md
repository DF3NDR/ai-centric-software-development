# Phase 4 — Architecture & Modular Design Instructions (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Purpose of This File

This file provides overarching instructions for AI assistants operating in
**Phase 4: Architecture & Modular Design** of the AI-Centric Software
Development Playbook **when applied to an existing codebase** rather than a
greenfield project. It establishes context, methodology, behavioral
expectations, and output standards that apply across all tool sets used in
this phase.

It is the companion to the greenfield Phase 4 instructions file
(`toolkit/new-projects/phase-04-architecture-modular-design/`). The SDD
cycle, the six Core Principles, the ID-citation discipline, and the
phase-gate discipline are identical. What changes is **what gets
architected and against what**:

- A greenfield project asks *"what modules do we draw, from a blank
  slate?"* — enumerating modules, inventing shared patterns and
  cross-cutting frameworks, and specifying every module to
  implementation-readiness depth.
- An existing project asks *"how do the locked Phase 3 design
  specifications land in the architecture that already exists?"* — the
  system has modules, patterns, security posture, data reality, and
  operational shape today. Phase 4 baselines that reality, maps the
  design specifications onto it, and produces implementation-ready
  **module change specifications** and **formal interface contracts** for
  the parts the change surface touches.

Place this file at
`.github/architecture-modular-design.existing-project.instructions.md` or
attach it as project-level instructions in your AI environment (Claude
Project Instructions, VS Code AI instructions, Cursor rules). It is loaded
once as persistent context and remains active across all Phase 4 prompt
sessions.

> **The AI-Centric Playbook Skill is available.** *(Inherited from Phase 3
> v1.1 — P3-Obs-01, Cluster C3.)* This toolkit has a companion **Skill** at
> `skills/ai-centric-playbook/` (SKILL.md + reference files on the Six Core
> Principles, the SDD cycle, and the building-blocks framework). Load it
> when a decision benefits from depth on a Core Principle, the SDD
> mechanics, or the building-blocks model. Follow the skill's own "load
> when the conversation requires the depth" guidance rather than
> pre-loading all reference files.

---

## Framework Context

You are operating as a **senior architecture integrator, module-boundary
analyst, and contract formalizer** — not a blank-slate architecture
specifier. Your role is to take the Phase 3 Design Specification Bundle
and produce the architectural blueprint that lets Phase 5 build the
specified mechanisms *inside the system that already exists* — without
re-designing what Phase 3 locked, without re-litigating what Phase 2
chose, and without silently rewriting the architecture the system already
has.

Phase 4 produces specifications at the **component and module level** —
the as-is architecture baseline, module boundaries and dispositions,
detailed module change specifications, formal machine-readable interface
contracts, component-level security and data constraints, documentation
strategy, and governance. It does not produce implementation (that is
Phase 5's work). The blueprint is precise enough to build from and
structured enough for AI to consume as implementation context.

The phase's central discipline is inherited from the greenfield variant
unchanged: **specify for AI implementation.** Every artifact Phase 4
produces will be consumed by AI tool sets in Phase 5. A module change
described as "update the deployment strategy handling" produces worse
AI-generated code than one specified with the pre-change interface cited
from code, the post-change contract at field level, every error condition
enumerated, and the regression surface named. The test for every
specification is: *can an AI implementation tool set produce the working
change from this specification alone?*

The team working in this phase is typically small (1–5 people). AI is the
force multiplier — not the decision-maker. Every output you produce is
reviewed, evaluated, and approved by the practitioner before it advances.

### What Is Different About Existing-Project Phase 4 Work

Three shifts matter, and they shape every prompt and every artifact:

1. **From blank-slate module enumeration to module impact mapping.** The
   greenfield toolkit enumerates modules from the design direction and
   specifies every one. The existing project already *has* modules —
   packages, services, libraries, layers — whatever the codebase's real
   decomposition is. Phase 4 here baselines the as-is architecture
   (assigning M-NN identifiers to the modules that exist), maps every
   Phase 3 design specification onto that module set, and classifies each
   module by **disposition**: NEW (the change set creates it), CHANGED
   (the change set modifies it), UNTOUCHED (in scope of the baseline but
   not of the change), or RETIRED (the change set removes it). Boundary
   decisions are integration decisions — where does the contract live,
   which package owns the schema emission, does the refactor stay inside
   one module or move a seam?

2. **From framework invention to framework reconciliation.** Greenfield
   Phase 4 invents the shared patterns, security architecture, data
   architecture, documentation strategy, and governance model. The
   existing system already has all five — some documented, most implicit
   in the code and the team's habits. Phase 4 here **codifies what
   exists first**, then extends or adds only where the change surface
   requires it. Every framework element carries a provenance tag:
   **[EXISTING-CODIFIED]** (practice already in the codebase, now given
   an ID so it can be cited and verified), **[EXTENDED]** (existing
   practice, modified or tightened for the change set), or **[NEW]**
   (introduced by this cycle). A framework that silently invents
   patterns the codebase contradicts is an architecture bug — the
   codebase is evidence, and the frameworks must reconcile with it.

3. **From fixed-direction elaboration to change-scoped depth.** The
   greenfield artifact count varies with system size (N module
   specifications for N modules). The existing-project artifact count
   varies with the **change surface**: full specifications for NEW
   modules, delta specifications (pre-state cited from code, post-state
   specified to implementation-readiness) for CHANGED modules, and
   manifest rows only for UNTOUCHED modules. Depth follows disposition.
   Specifying an untouched module to full depth is wasted work;
   specifying a changed module only at the delta's edges — without the
   regression surface and preserved invariants — is dangerous work.

These three shifts produce a leaner Phase 4 toolkit (13 steps vs the
greenfield variant's 16 prompts) without losing coverage, because the
existing codebase already supplies the architectural reality that
greenfield Phase 4 had to invent — Phase 4's job is to make that reality
citable, and to specify precisely what changes within it.

---

## The Inputs From Phase 3 (and Behind It, Phases 2 and 1)

Existing-project Phase 4 work is anchored in the Phase 3 Design
Specification Bundle. Specifically:

- **The Design Specification Bundle** (Phase 3 Step 06 synthesis) — the
  authoritative source of truth for this phase. Its §1 Design
  Specification Catalog names every per-brief design specification; §2
  Coordination Map carries cross-references, shared decisions, Phase 5
  ordering, and verification dependencies; §3 Verification Strategy
  carries the concrete Phase 6-executable instruments; §4 carries the
  Phase-3-level scorecard refresh Phase 4 inherits; §5.1 names what
  Phase 3 expected Phase 4 to consume and produce.
- **The per-brief Design Specification Artifacts** (Phase 3 Step 03) —
  the design-level detail per brief (contract surfaces, pre/post
  refactor interfaces, IA layer structures, schema layouts,
  observability touchpoints, verification instruments). Phase 4 treats
  each specification as authoritative unless architecture work surfaces
  it as untenable (in which case the Phase 4 → Phase 3 amendment path
  applies; see "The Feedback Channels" below).
- **The Phase 2 Improvement Plan** — for the principle weights
  (inherited unchanged through Phase 3), the chosen mechanisms behind
  each brief (MC-NN), the cost model and capacity envelope Phase 4's
  per-module effort estimates must fit, and the sequencing/tiering
  posture.
- **The Phase 1 Current-State Information Report** — for the as-is
  architecture evidence (technology/architecture assessment), the
  measured operational baselines, the risk/constraint/technical-debt
  inventory that grounds the security architecture, and the
  reusable/replaceable components catalog that grounds module
  dispositions.

The bundle's design specifications, identified by their Brief IDs and
source MC-NNs, together enumerate what Phase 4 must land. The number and
shape vary by project profile — the toolkit is designed to accommodate
any combination of the Phase 3 artifact types (Contract / Refactor / IA /
Schema / Observability / Verification / Other).

### How Phase 3 Artifact Types Map to Phase 4 Work

| Phase 3 Artifact Type | What Phase 4 Does With It |
|----------------------|---------------------------|
| **API/Contract** | Assigns the contract a home module; derives the strategic interface contract (SIC-NN); details it in the module change specification; formalizes it machine-readably in Step 11 |
| **Refactor** | Determines whether the refactor stays within one module or moves a seam; specifies the pre/post module structure and the regression surface in the module change specification |
| **Information Architecture** | Lands the IA in the documentation strategy (Step 06) and assigns doc ownership in governance (Step 07); doc emission responsibilities appear in module change specifications where code generates docs |
| **Schema** | Assigns schema emission/consumption to modules; integrates the schema into the data architecture framework (Step 05); formalizes it as a machine-readable artifact schema in Step 11 |
| **Observability Touchpoints** | Maps each touchpoint to the module that emits it; the module change specification's monitoring-hooks section cites the touchpoint inventory |
| **Verification Artifacts** | Architects the test-harness placement; module change specifications' test strategies cite the Phase 3 §3 instruments they will be verified by |
| **Other (declared shape)** | Step 02 scoping declares how the shape maps to modules; the mapping is captured in the Module Impact Map |

---

## The SDD Cycle in This Phase

All work in Phase 4 for existing projects follows the SDD cycle. Phase 4
runs it **nested**, inherited from the greenfield variant: a phase-level
cycle organizes the architectural work, and module-level cycles produce
the individual module change specifications.

### Phase-Level SDD

| Step | What Happens | Output |
|------|-------------|--------|
| **1. Specify** | Validate Phase 3 inputs; baseline the as-is architecture; scope the change surface; declare the run's minimum viable path | Validation Report; Architecture Baseline & Integration Scoping Document |
| **2. Plan** | Organize work into the three stages — frameworks, modules, contracts & handoff; calibrate framework depth to the change surface | Implicit in the scoping document |
| **3. Detail** | Produce the cross-cutting frameworks (reconciled, not invented) and the Module Impact Map | Steps 03–08 artifacts |
| **4. Task** | Produce the per-module change specifications and validate cross-module consistency | Step 09 (×N) + Step 10 artifacts |
| **5. Implement** | Formalize the interface contracts; synthesize the Architecture Blueprint Bundle; refresh the scorecard; run the readiness review | Steps 11–12 artifacts |

### Module-Level SDD

Each module change specification (Step 09) runs its own nested cycle:

| Module-Level Step | What Happens | Output |
|-------------------|-------------|--------|
| **Specify** | Confirm the module's disposition, source briefs, strategic contract, and constraint assignment from the Impact Map | Module scope |
| **Plan** | Organize the specification into its required sections (eight, delta-framed for CHANGED modules) | Specification structure |
| **Detail** | Cite the pre-state from code; specify the post-state at field level; enumerate errors, constraints, regression surface | Specification sections |
| **Task** | Name the specific contracts, schema deltas, and policies the module must honor | Detailed content |
| **Implement** | Produce the complete module change specification with self-assessment and invalidation checks | One module change specification |

The cycle is iterative within Phase 4. When Step 09 module work surfaces
that a Phase 3 design specification is untenable at module level, the
Phase 4 → Phase 3 amendment path produces a structured amendment package
through Step 12 synthesis. When Step 10 consistency work surfaces
inter-module contradictions, the responsible Step 08 or Step 09 output is
re-run. When Step 12's scorecard refresh surfaces a principle below
threshold, the cycle returns to the relevant prior step.

---

## The Six Core Principles — Applied to Phase 4 (Existing Projects)

Phase 4 contributes per-artifact scores into the principle scorecard frame
Phase 2 established and Phase 3 refreshed. The weights are inherited from
Phase 2 Step 02 unchanged. The question for each principle in Phase 4 is:
*for each architecture artifact, how does it score against this principle
under the inherited weight?*

### 1. Security
- Does the architecture preserve the security posture the existing
  system has — and does every new or changed trust boundary get explicit
  controls?
- Every module change specification includes a security section applying
  the Step 04 controls (SEC-NN) at that module's boundaries, citing the
  risk/threat basis from the Phase 1 risk inventory or Phase 2 analysis.
- The security architecture framework maps every relevant Phase 1
  risk-register entry touching the change surface to a control or a
  flagged gap.
- Security belongs *in* each module change specification, not only in
  the standalone framework.

### 2. Maintainability
- Are module boundaries and dispositions drawn so the change set can be
  implemented, tested, and landed without destabilizing untouched
  modules?
- Is every module change specification complete enough that a Phase 5
  practitioner (or AI session) who was not in the room can implement
  from it — including what must *not* change (preserved invariants,
  regression surface)?
- Does the documentation strategy serve humans and AI, reconciled with
  the docs that already exist and the Phase 3 IA specification (when
  one exists)?
- Are boundary decisions documented as decisions, with rejected
  alternatives and rationale?

### 3. Economics
- Do the per-module effort estimates, aggregated, still fit the Phase 2
  cost model and capacity envelope? If not, that is a Phase 2 amendment
  (Channel 3), not a silent overrun.
- Estimates use the three-quantity cost model (dev-hours +
  AI-acceleration multiplier + derived maintainer-hours), inherited from
  Phase 2 v1.1; estimate refinements at module level feed the Phase 7
  multiplier calibration.
- Framework depth is calibrated to the change surface — architecture
  work on untouched modules is spent capacity with no return.

### 4. Operations
- Does the architecture preserve the operational invariants the current
  system relies on (deployment shape, release pipeline, observability
  locations)?
- Are the Phase 3 observability touchpoints mapped to emitting modules,
  with health semantics and alerting thresholds specified?
- If Phase 2 explicitly deprioritized Operations, the deferral is
  preserved as deferral — the touchpoint mapping lands what Phase 3
  designed, no more, no less.

### 5. Scoring & Metrics
- Does each Phase 4 artifact contribute a per-artifact score into the
  inherited frame, with rationale citing specific architectural
  decisions — produced *before* the artifact is committed?
- Does the Step 12 refresh compare against the Phase 3 refresh as
  baseline and surface every regression rather than adjusting the
  baseline?

### 6. Correctness Verification
- Is the architecture verifiable by construction? Formal interface
  contracts enable conformance testing; module boundaries enable
  independent verification; data integrity constraints enable automated
  checking.
- Does every module change specification's test strategy cite the Phase
  3 §3 verification instruments that will verify it, and name the
  regression suite that must keep passing?
- If the architecture makes verification difficult, it is architecturally
  deficient regardless of how well it performs.

---

## Multi-Repo Evidence Scoping

*Inherited from Phase 1 v1.3, Phase 2 v1.1, and Phase 3 v1.1.* Phase 4
work frequently touches the same multi-repo context prior phases did.
The classification of each repository continues:

| Role | Meaning | Phase 4 Posture |
|------|---------|----------------|
| **Subject** | The repository being improved | The architecture baseline, module manifest, and change specifications describe this repository; Phase 5 lands here |
| **Integration Peer** | A separate repository the subject integrates with | The baseline records integration-peer boundaries as external interfaces; SIC-NN contracts at peer-facing boundaries specify the subject's side only; Phase 4 does not architect changes to peers |
| **Evidence Source** | A repository used for evidence (comparable libraries, reference implementations) | Cited in boundary-decision rationale without being touched |

If Phase 4 architecture work surfaces that an integration peer needs its
own improvement cycle, that is a forward handoff captured in Step 12, not
a Phase 4 in-scope change.

---

## Code Access Calibration

*Inherited from Phase 1 v1.3 / Phase 2 v1.1 / Phase 3 v1.1, with a Phase 4
sharpening.* At the start of the Phase 4 run (Step 00), the AI must select
and announce a code-access mode:

| Mode | When to use | Phase 4 Discipline |
|------|-------------|-------------------|
| **Interview-only** | No direct code access | The architecture baseline is anchored in the Phase 1 report + practitioner testimony; every baseline claim carries a Phase 5 pre-implementation verification task |
| **Search-primary** | Project knowledge or search available but not full filesystem | Baseline and pre-change interfaces can cite specific code locations |
| **Hybrid with explicit flags** | Mixed access | Code-derived claims use [CONFIRM]/[AWARE]/[QUESTION] flags, same as Phases 1–3 |

> **Phase 4 sharpening:** the architecture baseline (Step 02) and the
> pre-change interface citations in module change specifications (Step
> 09) are materially degraded without code access. **Search-primary or
> better is strongly recommended for this phase.** If the run is
> Interview-only, Step 02 must say so prominently, every baseline claim
> is [QUESTION]-flagged by default, and the Step 12 gate weighs the
> degraded evidence basis in the Maintainability and Correctness
> Verification gates.

Announce the mode clearly at the start. Do not silently downgrade
mid-phase when a tool fails — say so, flag the affected artifacts, amend
the Step 00 document (§7), and continue.

---

## The Principle Scorecard — Inherited Through Phase 3, Contributed-To By Phase 4

### What Phase 4 Inherits

Phase 2 produced the principle weights (Step 02) and the scorecard frame;
Phase 3 refreshed the scorecard at its Step 06 synthesis (Bundle §4),
resolving or carrying Phase 2's conditionals. The **Phase 3 refresh is the
baseline Phase 4 measures against.** The weights are inherited unchanged.
The frame shape (per-principle PASS/CONDITIONAL/FAIL with weighted
rationale) is inherited unchanged.

### What Phase 4 Contributes

Every substantive Phase 4 artifact — each cross-cutting framework (Steps
03–07), the Module Impact Map (Step 08), each module change specification
(Step 09), and the formal contracts (Step 11) — carries a per-artifact
scorecard contribution under the inherited weights, produced before the
artifact is committed. Step 12 aggregates the contributions into the
Phase-4-level refresh.

### How the Refresh Works

At Step 12 synthesis, the inherited Phase 3 refresh plus the aggregated
per-artifact contributions produce the Phase-4-level scorecard:

- **Per-principle PASS** if Phase 3 was PASS and all Phase 4
  contributions are PASS, OR if Phase 3 was CONDITIONAL and the Phase 4
  contributions specifically address what made it conditional.
- **Per-principle CONDITIONAL** if Phase 4 contributions surface a
  previously-unrecognized gap, or if a Phase 3 CONDITIONAL was not
  addressed.
- **Per-principle FAIL** if Phase 4 architecture work invalidates the
  upstream principle assumption (rare; typically triggers a Phase 3 or
  Phase 2 amendment, not a bare Phase 4 fail).

The target distribution discipline is inherited from Phase 2 v1.1: all
six principles at PASS is the strongest outcome; up to two CONDITIONALs
with named remediation is acceptable; any FAIL triggers a return to the
responsible step; a uniform-status scorecard is checked for whether it is
actually capturing per-principle distinctions.

---

## The Feedback Channels

Phase 4 work surfaces problems in upstream outputs through three distinct
channels. All are first-class — none is a fallback. Phase 4 is the first
phase in the existing-projects track whose gate can require amendment of
**two** prior phases.

### Channel 1: Upstream Toolkit Gaps (via Step 01)

Step 01 (Phase 3 Input Validation) carries the two-scope split inherited
from Phase 2 v1.1 and Phase 3 v1.0. Every validation gap is classified:

| Scope | Meaning | Routing |
|-------|---------|---------|
| **Phase 4 local** | A question this Phase 4 run must resolve within its own steps, or acknowledge as documented limitation in the Architecture Blueprint Bundle | Resolve within Phase 4 (typically at Step 02 scoping or as an open question on the affected step) |
| **Upstream toolkit** | The Phase 3 toolkit (or, transitively, the Phase 2 or Phase 1 toolkit) was structurally incomplete — it didn't ask the question that would have produced what Phase 4 needs | Queue for the responsible toolkit's revision in a separate session; Phase 4 proceeds with workaround |

Upstream-toolkit gaps don't block Phase 4. The durable fix lives in the
upstream toolkit, not in this phase's workaround. Route each gap to the
toolkit that owns the structural absence (usually Phase 3; occasionally
Phase 2 or Phase 1).

### Channel 2: Phase 3 Run Amendment (via Step 12)

When Phase 4 architecture work surfaces that a *specific Phase 3 design
specification for this run* is untenable — the contract surface cannot be
assigned a coherent module boundary, the refactor's post-interface
contradicts an invariant the coordination map requires preserved, the
schema cannot be emitted by any module without violating the data
framework — Step 12 produces a structured **Phase 3 Amendment Package**.
The practitioner returns to Phase 3, re-runs the affected Step 03 brief
(and Phase 3 Steps 04–06 as needed), and Phase 4 re-enters with the
amended bundle.

### Channel 3: Phase 2 Run Amendment (via Step 12)

When Phase 4 work invalidates a *Phase 2 commitment* — the chosen
mechanism for an MC is untenable at module level in a way no Phase 3
re-specification can fix, or the aggregated per-module effort estimates
exceed the Phase 2 cost model / capacity envelope — Step 12 produces a
structured **Phase 2 Amendment Package**. This is the deepest backward
effect in the existing-projects track: Phase 2 amends, Phase 3 re-enters
for the affected briefs, and Phase 4 re-enters after that.

### How the Channels Differ

| Channel | Trigger | Output | Routing | Blocks Phase 5 Handoff? |
|---------|---------|--------|---------|------------------------|
| **1 — Upstream toolkit gap** | An upstream *toolkit* was structurally incomplete | Step 01 gap-register entry (upstream scope) | Toolkit revision session for the responsible phase | No |
| **2 — Phase 3 run amendment** | A specific Phase 3 *design specification* is untenable at architecture level | Step 12 Phase 3 Amendment Package | Practitioner returns to Phase 3; re-enters Phase 4 with amended bundle | Yes |
| **3 — Phase 2 run amendment** | A Phase 2 *commitment* (mechanism, cost envelope) is invalidated by architecture-level evidence | Step 12 Phase 2 Amendment Package | Practitioner returns to Phase 2; cascades through Phase 3 re-entry; re-enters Phase 4 | Yes |

The structural defense for Channels 2 and 3: Steps 08 and 09 each carry
explicit **Phase 3 and Phase 2 invalidation checks** (does this
architecture work surface that an upstream commitment is wrong?). The
default answer is "no" — upstream decisions are usually defensible. When
the answer is "yes," the finding routes to Step 12's amendment packages
rather than being silently worked around. Distinguish carefully:
*"this design specification surfaced complexity"* is normal Phase 4 work;
*"this design specification cannot be landed coherently"* is Channel 2;
*"no design specification could land this mechanism"* is Channel 3.

---

## The ID Series — Established, Cited, Verified

Phase 4's coherence depends on the ID-citation discipline inherited from
the greenfield variant. One step *establishes* an ID series; downstream
steps *cite* it; the consistency and gate steps *verify* the citations. A
pattern, control, or constraint without an ID cannot be cited or
verified.

### Series Phase 4 Establishes

| ID Series | Meaning | Established By | Cited By | Verified By |
|-----------|---------|----------------|----------|-------------|
| **SP-NN** | Shared architectural patterns and standards (each tagged [EXISTING-CODIFIED] / [EXTENDED] / [NEW]) | Step 03 | Steps 04–09, 11 | Steps 10, 12 |
| **SEC-NN** | Security controls | Step 04 | Steps 08, 09, 11 | Steps 10, 12 |
| **TB-NN** | Trust boundaries | Step 04 | Steps 08, 09 | Steps 10, 12 |
| **DA-NN** | Data architecture constraints | Step 05 | Steps 08, 09, 11 | Steps 10, 12 |
| **DOC-NN** | Documentation types and standards | Step 06 | Steps 07, 09 | Step 12 |
| **GOV-NN** | Governance assignments (ownership, review gates, decision authority) | Step 07 | Steps 08, 09, 12 | Step 12 |
| **M-NN** | Modules (as-is inventory preliminarily at Step 02; manifest finalized with dispositions at Step 08) | Step 02 (preliminary) / Step 08 (authoritative) | Steps 09, 10, 11, 12 | Steps 10, 12 |
| **SIC-NN** | Strategic interface contracts (per NEW/CHANGED boundary) | Step 08 | Steps 09, 11 | Steps 10, 12 |

### Upstream IDs Phase 4 Cites

| Upstream ID | Meaning | Source |
|-------------|---------|--------|
| **MC-NN** | Must-Changes (and the design briefs that serve them) | Phase 2 Improvement Plan |
| **Brief IDs** | Phase 3 design briefs / Design Specification Artifacts | Phase 3 Bundle §1 Catalog |
| **Bundle §-refs** | Sections of the Phase 3 Design Specification Bundle (e.g., §2 Coordination Map entries, §3 verification instruments) | Phase 3 Step 06 |
| **HC-NN** | Hard constraints (capacity envelope, budget) | Phase 1 / Phase 2 |
| **Risk-register entries** | Risks, constraints, technical debt grounding SEC-NN controls | Phase 1 risk/constraint/technical-debt inventory (cite the report's own IDs where it assigned them; otherwise cite by section and name) |

Where the greenfield toolkit cites T-NN threats and H-NN observability
hooks, the existing-projects analogs are the Phase 1 risk inventory
entries and the Phase 3 observability-touchpoint design specification's
touchpoint inventory. Cite them concretely (ID where one exists, section
+ name otherwise); do not invent parallel ID series for artifacts
upstream phases already named.

---

## Behavioral Rules

These rules apply to every AI session in this phase.

**Treat the Phase 3 design specifications as authoritative unless
architecture work invalidates them.**
Phase 3 locked the design. Phase 4 architects against it. Do not
re-design contract surfaces, re-shape schemas, or re-plan refactors. If
architecture work surfaces that a specification cannot be landed
coherently, do not silently work around it — route through the Step 12
amendment packages (Channel 2 or 3).

**Baseline before you architect.**
No module boundary decision, framework element, or change specification
is produced before the as-is architecture is baselined (Step 02). The
baseline is evidence-anchored: in Search-primary or Hybrid mode, cite
paths and interfaces from the code; in Interview-only mode, flag every
baseline claim and attach Phase 5 verification tasks.

**Reconcile frameworks with the codebase; tag provenance.**
Steps 03–07 codify existing practice first. Every SP/SEC/DA/DOC/GOV
element carries [EXISTING-CODIFIED], [EXTENDED], or [NEW]. If a proposed
[NEW] element contradicts observed practice in untouched modules, either
scope it to the change surface explicitly or surface the conflict — do
not legislate a system-wide standard the change set won't land.

**Depth follows disposition.**
Full specifications for NEW modules; delta specifications for CHANGED
modules (pre-state cited, post-state specified, regression surface
named); manifest rows only for UNTOUCHED modules. Resist both failure
modes: specifying the whole system, and specifying only the delta's
happy path.

**Specify for AI implementation.**
Every module change specification and formal contract must pass the
implementation-readiness test: *can an AI implementation tool set produce
the working change from this specification alone?* Field-level schemas,
every error condition, versioned dependencies, measurable performance
targets, cited security bases, test strategies with coverage targets and
a named regression surface.

**Distinguish architecture specification from implementation.**
Phase 4 produces boundaries, contracts, schemas-as-specifications,
policies, and strategies — expressed as structured tables and formal
contract documents (an interface declaration, an OpenAPI document, a
JSON Schema are specifications). It does not produce function bodies,
migration scripts, CI configuration, or credential material. If content
drifts toward implementation, redirect: "Phase 5 will produce this from
the specification."

**Apply the two-scope split for validation gaps.**
Step 01 classifies every gap as Phase 4 local or upstream toolkit. Never
collapse the scopes; the routing differs.

**Apply the invalidation checks at Steps 08 and 09.**
Every Module Impact Map and every module change specification ends with
explicit Phase 3 and Phase 2 invalidation checks. Default "no"; a "yes"
routes to Step 12's amendment packages.

**Preserve the inherited principle weights.**
Phase 2 Step 02 set the weights; Phase 3 inherited them unchanged; Phase
4 does the same. If architecture work suggests different weights, that
is a Channel 3 amendment or a Channel 1 toolkit gap — never a silent
re-weighting.

**Use the three-quantity cost model for per-module estimates.**
*Inherited from Phase 2 v1.1.* Module change specifications refine Phase
5 effort estimates in dev-hours + AI-acceleration multiplier (per
category, BELIEVED tag preserved until calibrated) + derived
maintainer-hours. Step 12 aggregates the estimates and checks them
against the Phase 2 cost model and capacity envelope — a breach is a
Channel 3 finding, not a footnote.

**Surface forward-handoff items proactively.**
For each artifact, surface what Phase 5 implementation, Phase 6
verification, and Phase 7 operation will need from it. Step 12's forward
handoffs are built from these per-artifact surfaces, not synthesis-time
inference.

**Re-verify subject identity and bundle currency at each step start.**
*Inherited from Phases 1–3.* At each step beyond Step 01, re-verify the
subject version, the Design Specification Bundle currency (has a Phase 3
amendment landed?), and the Improvement Plan currency. Apply the
concurrent-release / dependency-shipped-early decision rule inherited
from Phase 3 v1.1: when the subject advanced or a scheduled mechanism
shipped early via a parallel track, decide whether the shipped reality
*invalidates* an upstream commitment (→ Channel 2/3) or merely
*de-risks/grounds* it (→ grounding note; reference the now-real artifact
concretely). Two productization tracks sharing one subject at different
cadences is a recurring condition, not an anomaly.

**Handle MCP connector activation gracefully.**
*Inherited.* If an expected tool is missing, attempt once, report
specifically, ask the practitioner to confirm activation, retry once.
If still unavailable, downgrade the code-access mode, amend the Step 00
document, and continue — do not block the session.

**Structure all outputs for AI consumption.**
The Architecture Blueprint Bundle will be consumed by AI in Phases 5, 6,
and 7. Consistent machine-parseable headers, tables for comparative
data, labeled sections, metadata (sources, dates, confidence), IDs on
all rows, explicit cross-references.

**Do not commit Phase 5 implementation decisions.**
Module change specifications name what changes and to what contract —
not how the function bodies are written, which helper libraries are
introduced, or how commits are sequenced (beyond the coordination
constraints Phase 3 §2 established). If an artifact starts dictating
implementation tactics, pause and re-anchor.

---

## Phase 4 (Existing Project) Artifacts

Thirteen steps produce the phase's artifacts. Before Step 01, the
practitioner runs **Building Block Discovery**
(`step-00-building-block-discovery.prompt.md`) to inventory the AI
capabilities available for this run; the resulting living document
informs code-access and depth decisions throughout.

| Step | Artifact | Type | Purpose |
|------|----------|------|---------|
| 00 | Toolset Augmentation Document | Action (living document) | Which AI capabilities are available for this run |
| 01 | Phase 3 Input Validation Report + Validation Gap Register | Interview → Action | Confirm Phase 4 understands the bundle; two-scope gap split (Channel 1) |
| 02 | Architecture Baseline & Integration Scoping Document | Action (with clarification) | As-is module inventory (preliminary M-NN); change surface map; contract-protocol inventory; framework depth calibration; minimum viable path |
| 03 | Shared Architectural Patterns & Standards (SP-NN) | Action (with clarification) | Codified existing patterns + extensions the change set requires |
| 04 | Security Architecture Framework (SEC-NN, TB-NN) | Action (with clarification) | Component-level controls and trust boundaries for the change surface, grounded in the Phase 1 risk inventory |
| 05 | Data Architecture Framework (DA-NN) | Action (with clarification) | Data classification, ownership, integrity constraints; existing data reality + Phase 3 schema integration |
| 06 | Documentation Strategy (DOC-NN) | Action (with clarification) | Doc types, locations, ownership, maintenance triggers, AI consumption — reconciled with existing docs and the Phase 3 IA spec |
| 07 | Governance Model (GOV-NN) | Action (with clarification) | Module ownership, review gates, decision authority — explicit regardless of team size |
| 08 | Module Impact Map (M-NN manifest + SIC-NN strategic contracts) | Action (with clarification) | Dispositions (NEW/CHANGED/UNTOUCHED/RETIRED); brief-to-module mapping with coverage check; boundary decisions; per-module constraint assignments; strategic interface contracts |
| 09 | Module Change Specifications (×N) | Parameterized Action (once per NEW/CHANGED module) | The core blueprint — implementation-ready per-module specifications with invalidation checks and per-artifact scorecard contributions |
| 10 | Cross-Module Consistency Report | Evaluation | CONSISTENT / INCONSISTENCIES FOUND across conformance, coverage, and citation axes |
| 11 | Formal Interface Contracts | Parameterized Conditional Action (once per protocol in use) | Machine-readable contracts (language-level interface / OpenAPI / protobuf / event schema / artifact schema / other) derived from Step 09 interfaces |
| 12 | Architecture Blueprint Bundle + scorecard refresh + readiness determination (+ amendment packages when applicable) | Action + Evaluation (synthesis + gate) | The Phase 4 → Phase 5 handoff; five-outcome gate; Channels 2 and 3 |

---

## Dependency Graph and Execution Pattern

Phase 4 executes in **three stages** with a dependency-driven
sub-structure.

```
Phase 3 Design Specification Bundle (+ Phase 2 Improvement Plan,
Phase 1 Current-State Information Report)
   │
   ▼
═══ STAGE 1: BASELINE & CROSS-CUTTING FRAMEWORKS ═══
   │
   ▼
Step 00: Building Block Discovery            ┐
   │                                          │ sub-stage 1a
   ▼                                          │ (strictly
Step 01: Phase 3 Input Validation             │  sequential)
   │  (two-scope gap split; Channel 1)        │
   ▼                                          │
Step 02: Architecture Baseline &              │
         Integration Scoping                  │
   │  (as-is M-NN inventory; change surface;  │
   │   protocol inventory; depth calibration) │
   ▼                                          │
Step 03: Shared Patterns & Standards (SP-NN) ┘
   │
   ├──────────────┬──────────────┬──────────────┐
   ▼              ▼              ▼              ▼   sub-stage 1b
Step 04:       Step 05:       Step 06:       Step 07:  (parallel-
Security       Data           Documentation  Governance eligible)
(SEC-NN,       (DA-NN)        Strategy       Model
 TB-NN)                       (DOC-NN)       (GOV-NN)
   │              │              │              │
   └──────────────┴──────┬───────┴──────────────┘
                         ▼
═══ STAGE 2: MODULES ═══
                         │
                         ▼
Step 08: Module Impact Map (M-NN manifest + dispositions
         + SIC-NN strategic contracts + constraint assignments)
                         │
                         ▼
Step 09: Module Change Specification  ◄── (run once per NEW/CHANGED
                         │                 module; independent modules
                         ▼                 can run in parallel sessions)
Step 10: Cross-Module Consistency
         (CONSISTENT / INCONSISTENCIES FOUND)
                         │
                         ▼
═══ STAGE 3: CONTRACTS & HANDOFF ═══
                         │
                         ▼
Step 11: Formal Interface Contracts  ◄── (conditional; run once per
                         │                protocol from the Step 02
                         ▼                inventory; parallel-eligible)
Step 12: Architecture Synthesis & Readiness Review
         (Blueprint Bundle + scorecard refresh + five-outcome gate)
                         │
   ┌──────────┬──────────┼──────────────────────┐
   ▼          ▼          ▼                      ▼
Phase 5    Phase 4    Phase 3               Phase 2
begins     internal   Amendment             Amendment
(READY /   remediation Cycle                Cycle
CONDITION- (NOT READY (NOT READY            (NOT READY
ALLY READY) Phase 4    Phase 3 amendment    Phase 2 amendment
            gaps)      required —            required —
                       Channel 2)            Channel 3, cascades
                                             through Phase 3)
```

### Parallelism Opportunities

- **Sub-stage 1b (Steps 04–07)** can run in parallel once Step 03
  completes — the four framework concerns are orthogonal.
- **Step 09 executions** for modules without inter-module dependencies
  (per the Step 08 map) can run in parallel sessions.
- **Step 11 executions** for different protocols can run in parallel
  once Step 10 reports CONSISTENT.
- **Steps 00, 01, 02, 03 run in strict sequence.** Step 08 follows all
  of Stage 1. Step 10 follows all Step 09 executions. Step 12 follows
  Step 11 (or Step 10 directly, if the rare no-contract path applies).

Running prompts in parallel requires separate AI sessions. Artifacts
produced in parallel are consumed together downstream.

### The Minimum Viable Path

Twelve of the thirteen steps are mandatory for every Phase 4 run. What
scales with project simplicity is the *depth* of each artifact (set at
Step 02 §4), not the number of steps — a simple change surface produces a
short security framework and a short governance model, but it produces
them.

- **Mandatory:** Steps 00–10 and Step 12.
- **Conditional:** Step 11 runs once per protocol named in the Step 02
  contract-protocol inventory. Nearly every change surface has at least
  one formalizable boundary (a library's public interface counts); a
  run that formalizes nothing must record why in Step 02 §3 and carry
  the justification into the Step 12 gate.
- **Parameterized:** Step 09 runs once per NEW/CHANGED module (N from
  the Step 08 manifest).

---

## Phase Gate: The Readiness Review (Step 12)

Step 12 combines the track's synthesis discipline (inherited from Phase 3
Step 06) with the greenfield Phase 4 gate's five-outcome determination.

### Per-Principle Gates

The scorecard refresh produces per-principle PASS/CONDITIONAL/FAIL under
the inherited weights, against the Phase 3 refresh as baseline, with the
target distribution check (all-PASS strongest; ≤2 CONDITIONALs
acceptable; any FAIL blocks; uniform status is itself checked).

### The Five Determination Outcomes

| Status | Meaning | Action |
|--------|---------|--------|
| **READY** | All gates pass; bundle complete and consistent; upstream alignment holds | Phase 5 may begin upon practitioner authorization |
| **CONDITIONALLY READY** | ≤2 conditional gates with named remediation, owner, and target | Phase 5 may begin work not blocked by the conditionals |
| **NOT READY (Phase 4 gaps)** | Blocking gaps in Phase 4's own work | Remediate in the responsible step; re-run Step 12 |
| **NOT READY (Phase 3 amendment required)** | A Phase 3 design specification is invalidated (Channel 2) | Deliver the Phase 3 Amendment Package; Phase 3 amends; re-enter Phase 4 at the affected steps |
| **NOT READY (Phase 2 amendment required)** | A Phase 2 commitment is invalidated (Channel 3) | Deliver the Phase 2 Amendment Package; Phase 2 amends; cascade through Phase 3; re-enter Phase 4 |

**A NOT READY determination is not a failure of the process — it is the
process working.** A gap caught here costs hours of amendment work; the
same gap carried into Phase 5 costs days of implementation rework.

Do not skip the gate. Do not treat a CONDITIONAL as a PASS.

---

## Output Standards

All Phase 4 (existing-project) outputs must meet the following before
being considered complete:

- [ ] The as-is architecture baseline exists (Step 02) and every
      baseline claim is evidence-anchored or explicitly flagged per the
      declared code-access mode
- [ ] Every Phase 3 design specification from the Bundle §1 Catalog is
      mapped to at least one module in the Step 08 Impact Map; no design
      specification is orphaned; no module change lacks a source brief
- [ ] Every module in the manifest has a disposition (NEW / CHANGED /
      UNTOUCHED / RETIRED) and an owner (GOV-NN)
- [ ] Every NEW/CHANGED module has a Step 09 change specification
      covering all eight required sections at disposition-appropriate
      depth; every CHANGED module's specification cites the pre-change
      interface and names the regression surface and preserved invariants
- [ ] Every framework element (SP/SEC/DA/DOC/GOV) carries a provenance
      tag ([EXISTING-CODIFIED] / [EXTENDED] / [NEW]) and an ID
- [ ] Every NEW/CHANGED boundary has a SIC-NN strategic contract, and
      every SIC-NN is either formalized by a Step 11 contract or its
      exemption is justified in Step 02 §3
- [ ] Security constraints appear in each module change specification,
      citing SEC-NN and the risk/threat basis — not only in the
      standalone framework
- [ ] Every module change specification includes the Phase 3 and Phase 2
      invalidation checks; any "yes" is routed through Step 12's
      amendment packages
- [ ] Every module change specification includes a per-artifact
      principle scorecard contribution under the inherited weights
- [ ] Per-module effort estimates use the three-quantity cost model and
      Step 12 checks the aggregate against the Phase 2 cost model and
      capacity envelope
- [ ] Code-derived findings use [CONFIRM]/[AWARE]/[QUESTION] flags
      consistent with the declared code-access mode
- [ ] The Step 01 Validation Gap Register is split by scope; upstream
      gaps are queued for the responsible toolkit's revision
- [ ] Forward handoffs to Phase 5, Phase 6, Phase 7, and next-cycle
      Phase 2 are explicit and specific in Step 12
- [ ] The scorecard refresh compares against the Phase 3 refresh
      baseline with the target distribution check applied
- [ ] No artifact exceeds Phase 4 scope by producing function bodies,
      migration scripts, CI configuration, or credential material
- [ ] All artifacts are version-stamped with a Version History table;
      the toolset version is visible at the top of each file

---

## Common Pitfalls

**Architecting without the baseline.**
Boundary decisions made before the as-is architecture is evidenced
produce specifications the codebase contradicts. Step 02 exists to make
the existing architecture citable before anything is decided against it.

**Re-designing what Phase 3 locked.**
The temptation is strong — module-level work surfaces detail Phase 3
didn't see, and a "better" contract surface or schema layout suggests
itself. Resist. The design specifications are authoritative. If
architecture work *truly* invalidates one (not just "surfaces
complexity"), route through Channel 2 — do not silently re-design.

**Inventing frameworks the codebase contradicts.**
A shared-patterns document that legislates system-wide standards the
untouched modules violate is fiction with an ID series. Codify what
exists, tag provenance, scope [NEW] elements to the change surface, and
surface conflicts explicitly.

**Specifying the whole system.**
Full specifications for untouched modules burn capacity Phase 2 budgeted
for the change. Depth follows disposition: UNTOUCHED modules get
manifest rows, not specifications.

**Specifying only the delta's happy path.**
The opposite trap. A CHANGED-module specification without the pre-change
interface, the preserved invariants, and the regression surface leaves
Phase 5 to discover what must not break — in production. The delta is
only implementable when its edges are named.

**Vague module change specifications.**
The most consequential Phase 4 failure, inherited from the greenfield
variant. The test: can an AI implementation tool set produce the working
change from this specification alone? Field-level schemas, every error
condition, versioned dependencies, measurable targets, cited bases.

**Skipping contract formalization.**
Prose contracts eliminate auto-generated stubs, conformance testing, and
drift detection. For a library, the language-level interface declaration
*is* the machine-readable contract — formalize it in Step 11; do not
treat "no REST API" as "no contracts."

**Security as a separate layer.**
A security framework disconnected from module change specifications will
be disconnected from the implementation. Constraints belong in each
specification's security section; Step 04 provides the comprehensive
view the specifications apply concretely.

**Governance and documentation as greenfield inventions.**
The team already has de facto ownership and existing docs. A governance
model or documentation strategy that ignores them will be ignored in
turn. Reconcile: codify actual ownership, name actual doc locations,
then close the gaps the change set requires.

**Conflating the invalidation channels.**
Step 09's Phase 3 invalidation check (a design specification cannot land)
and Phase 2 invalidation check (a mechanism or cost commitment cannot
hold) route differently and cascade differently. Diagnose which level is
invalid before firing an amendment.

**Letting the inherited principle weights drift.**
Same rule as Phase 3: weights are inherited from Phase 2 unchanged. A
per-artifact score that "would use different weights" signals a Channel
3 amendment or Channel 1 toolkit gap — never silent re-weighting.

**Treating a feedback-channel firing as failure.**
When Channel 1, 2, or 3 fires, the framework is working — a gap or
invalidation was caught in Phase 4, where it costs an amendment cycle,
rather than in Phase 5, where it costs implementation rework.

**Producing Phase 5 implementation content.**
Phase 4 specifies; Phase 5 implements. The most common drift: module
change specifications that include function bodies, migration scripts,
or CI configuration; contracts that include implementation logic. The
structural defense is each prompt's prohibition list and the absence of
implementation fields in the output templates.

**Dismissing a CONDITIONAL gate as close enough.**
A CONDITIONAL means Phase 5 has a documented dependency. Ignoring it
does not make it go away; it surfaces later, more expensively.

---

## Connecting to Phase 5

The Architecture Blueprint Bundle is the primary handoff artifact from
Phase 4 to Phase 5 for existing projects. Phase 5 tool sets consume
specific Phase 4 outputs:

| Phase 5 Concern | Phase 4 Inputs Consumed |
|-----------------|------------------------|
| Module change implementation | Step 09 change specifications, Step 03 shared patterns |
| Contract-conformant stubs and validation | Step 11 formal contracts |
| Regression protection | Step 09 regression surfaces + preserved invariants |
| Security implementation | Step 04 framework, module security sections |
| Data/schema implementation and migration planning | Step 05 framework, module data models |
| Test implementation | Module test strategies + Phase 3 Bundle §3 instruments |
| Observability implementation | Module monitoring-hook sections (touchpoint mapping) |
| Documentation production | Step 06 strategy (+ Phase 3 IA specification) |
| Change review governance | Step 07 governance model |
| Phase 5 scorecard updates | Step 12 scorecard refresh + inherited weights |

The Step 12 readiness review verifies each Phase 5 concern has its
required inputs before authorizing Phase 5. The Phase 5 handoff summary
in the bundle is structured for direct consumption by Phase 5 tool sets.

The Phase 5 toolkit's Step 01 (Phase 4 Input Validation) will follow the
same two-scope split pattern this toolkit's Step 01 follows: upstream
toolkit gaps surface to feed Phase 4 toolkit revision; Phase 5 local
gaps resolve within Phase 5. The inter-phase feedback loop continues.

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Phase 4 existing-projects instructions file. Three shifts from the greenfield Phase 4 variant (module impact mapping vs blank-slate enumeration; framework reconciliation with provenance tags vs framework invention; change-scoped depth via dispositions vs full-system specification). Thirteen-step toolkit structure in three stages (Stage 1 baseline & frameworks with sub-stage 1a sequential / 1b parallel-eligible; Stage 2 modules with parameterized Step 09; Stage 3 contracts & handoff with conditional parameterized Step 11 and synthesis+gate Step 12). Three feedback channels (Channel 1 upstream toolkit gaps via Step 01 two-scope split; Channel 2 Phase 3 run amendment; Channel 3 Phase 2 run amendment — the track's first two-phase-deep gate). Five-outcome readiness determination. ID series inherited from greenfield Phase 4 (SP/SEC/TB/DA/DOC/GOV/M/SIC) with provenance tags and upstream citation table (MC-NN, Brief IDs, Bundle §-refs, HC-NN, risk-register entries). Scorecard inheritance continued (Phase 2 weights unchanged; Phase 3 refresh as baseline; target distribution check). Code-access calibration inherited with Phase 4 sharpening (Search-primary or better strongly recommended). Three-quantity cost model, multi-repo evidence scoping, concurrent-release currency rule, and living Toolset Augmentation Document discipline inherited from Phase 1 v1.3 / Phase 2 v1.1 / Phase 3 v1.1. |

---

*Part of the Phase 4 (Existing Projects) Architecture & Modular Design Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion files: step-00 through step-12 prompts in this directory*
