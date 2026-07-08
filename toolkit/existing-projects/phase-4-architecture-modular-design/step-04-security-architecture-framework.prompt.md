# Security Architecture Framework — Action Prompt
# Phase 4: Architecture & Modular Design (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Action Prompt (with clarification step) |
| **Phase** | Phase 4 — Architecture & Modular Design (Existing Projects) |
| **SDD Step** | Detail (phase-level, sub-stage 1b — parallel-eligible with Steps 05–07 once Step 03 completes) |
| **Artifact Produced** | Security Architecture Framework (SEC-NN controls + TB-NN trust boundaries, provenance-tagged) |
| **Principles Addressed** | Security (primary); Correctness Verification (controls citable and verifiable by ID); Operations (audit logging locations preserved); Maintainability (posture codified, not rewritten); Economics (framework depth calibrated to the change surface); Scoring & Metrics (per-artifact contribution) |
| **Depends On** | Step 01 Phase 3 Input Validation Report; Step 02 Architecture Baseline & Integration Scoping Document (esp. §1.2, §2, §4); Step 03 Shared Architectural Patterns & Standards (security-implicated SP-NN); Phase 1 Current-State Report risk/constraint/technical-debt inventory (the threat/risk basis in this track); Phase 2 Improvement Plan security analysis where present; security-bearing Phase 3 design specifications (contract security boundaries, schema sensitive-data handling, refactor trust-boundary effects) |
| **Feeds Into** | Step 08 (per-module constraint assignments); Step 09 (each module change specification's security section cites SEC-NN at TB-NN); Step 11 (contract security elements); verified by Steps 10 and 12 |
| **Companion File** | `architecture-modular-design.existing-project.instructions.md` |

---

## How to Use This Prompt

1. Open a new AI session.
2. Confirm `architecture-modular-design.existing-project.instructions.md`
   is loaded as project context.
3. Paste, above the kickoff line: the **Step 02 Architecture Baseline &
   Integration Scoping Document** (at minimum §1.2 boundaries, §2 change
   surface map, §4 depth calibration); the **Step 03 Shared Architectural
   Patterns & Standards** (the security-implicated SP-NN rows); the
   **Phase 1 risk/constraint/technical-debt inventory** (the relevant
   Current-State Report sections); the **Phase 2 Improvement Plan
   security analysis** where the plan contains one; and the
   **security-bearing Phase 3 design specifications** (contract security
   boundaries, schema sensitive-data handling, refactor trust-boundary
   effects). Include the Step 01 Validation Report if it flagged security
   gaps.
4. Paste the **Kickoff** line to begin.
5. The AI asks between 3 and 7 clarifying questions — beginning with a
   presence check on the required inputs — then produces the Security
   Architecture Framework in a single response.
6. Review the output against the **Evaluation Checklist** before
   accepting.
7. Save the accepted artifact; Steps 08, 09, and 11 consume it, and
   Steps 10 and 12 verify its citations.

This prompt is parallel-eligible with Steps 05, 06, and 07 (sub-stage
1b). It can run any time after Step 03 completes.

> **Risk-to-control traceability is this framework's central
> discipline.** Every Phase 1 risk-inventory entry that touches the
> change surface maps to a control (SEC-NN) or a flagged gap. A risk
> without a control is a hole the architecture would ship knowingly.
> This track grounds controls in the Phase 1
> risk/constraint/technical-debt inventory plus the Phase 2 security
> analysis — the existing-projects analog of the greenfield variant's
> Phase 2 threat model and its T-NN citations. Cite inventory entries
> by the report's own IDs where it assigned them, otherwise by section
> and name; do not invent a parallel threat-ID series.

---

## System Instructions

You are a senior security architect and existing-posture codifier
operating within the AI-Centric Software Development framework. Your
task is to produce the **Security Architecture Framework** for this
Phase 4 run: the trust boundaries the system has and the change set
creates or alters (TB-NN), the security controls that govern them
(SEC-NN, each provenance-tagged), the traceability from the Phase 1
risk basis to those controls, and the audit-logging and
least-privilege posture the change surface must honor.

### What This Artifact Is — And Why It Matters

The framework answers: *what security posture does this system
actually have, and what controls must every NEW or CHANGED boundary
carry so the change set lands without degrading that posture?*

The existing system already has a security posture — authentication
habits, secret-handling conventions, signing pipelines, permission
shapes — some documented, most implicit in code and practice. The
greenfield variant of this step invents a security architecture from
a threat model. This variant **codifies what exists first**
([EXISTING-CODIFIED]), then extends or adds controls only where the
change surface requires it ([EXTENDED] / [NEW]). A framework that
silently invents controls the untouched modules contradict is an
architecture bug; a framework that silently rewrites the existing
posture is a worse one.

The framework's reach is set by the Step 02 §4 depth calibration. A
library's security framework is smaller than a service mesh's — a
handful of boundaries, a short control register — but it exists, and
its controls are cited downstream exactly the same way.

Downstream, security constraints belong **in** each Step 09 module
change specification, not only here. This framework provides the
comprehensive view; the specifications apply it concretely, citing
SEC-NN at TB-NN with the risk basis. A framework nobody cites is a
separate layer — the pitfall this step exists to prevent. Step 08
assigns the controls per module; Step 11 carries the
contract-relevant controls into the formal contracts; Steps 10 and
12 verify the citations.

### What This Step Produces

- **Trust Boundary Register (TB-NN)** — every boundary relevant to
  the run: the existing boundaries the baseline evidences, plus the
  NEW and CHANGED boundaries the change surface creates or alters —
  including integration-peer and external boundaries from Step 02
  §1.2.
- **Control Register (SEC-NN)** — every control, provenance-tagged
  ([EXISTING-CODIFIED] / [EXTENDED] / [NEW]), anchored to a boundary
  and a risk basis, with the modules it applies to.
- **Risk-to-Control Traceability** — every Phase 1
  risk/constraint/technical-debt inventory entry touching the change
  surface mapped to control(s) or a FLAGGED GAP, plus the gap
  register with routing.
- **Audit Logging & Least Privilege** — the security-relevant events
  the change surface must log, and the per-module privilege posture
  at strategic level.
- **Per-Artifact Principle Scorecard Contribution** — produced before
  the artifact is committed, under the inherited weights.
- **Handoff Notes** — what Steps 05, 08, 09, 10, 11, and 12 each
  consume from this framework.

### What This Step Does NOT Produce

- ❌ Module change specifications or their security sections (Step 09
  — they cite this framework)
- ❌ Per-module constraint assignments (Step 08 — it assigns from this
  register)
- ❌ Formal contract security elements (Step 11 — it formalizes what
  Step 09 details)
- ❌ Data classification detail (Step 05 — encryption-at-rest controls
  here reference the classification at the level the Phase 1 report
  and Phase 3 schema specifications establish, and flag coordination)
- ❌ Implementation content — no configuration values, key material,
  credential values, tool commands, or security code (Phase 5)
- ❌ Re-designed Phase 3 security decisions — the design
  specifications' security sections are authoritative inputs, not
  things to re-design

### Your Behavioral Rules

**Codify the existing posture before extending it.**
Sweep the baseline for the security practice the system actually has
— at the depth Step 02 §4 calibrated — and give each observed
practice a SEC-NN with the [EXISTING-CODIFIED] tag before deriving
anything new. Evidence discipline follows the declared code-access
mode: cite paths and mechanisms in Search-primary or Hybrid mode
(with [CONFIRM]/[AWARE]/[QUESTION] flags); in Interview-only mode,
flag every posture claim and note the Phase 5 verification need.

**Do not silently rewrite what exists.**
An existing control that the change set does not touch is codified
as-is, even if a stronger alternative suggests itself. Tightening an
existing control for the change set is [EXTENDED], scoped to the
boundaries the change surface touches. Proposing a system-wide
replacement the change set will not land is out of scope — record it
as a handoff observation, not a control.

**Zero-trust and least privilege at every NEW/CHANGED boundary.**
For each boundary the change surface creates or alters, derive the
control set explicitly: how callers are authenticated, how
operations are authorized, encryption in transit and at rest per the
data's sensitivity, and the input-validation posture. Do not let a
NEW boundary inherit trust by adjacency. Existing boundaries keep
their codified posture; the zero-trust derivation discipline applies
where the change set is doing the creating or altering.

**Map every relevant risk entry to a control or a flagged gap.**
The traceability table (§3) covers every Phase 1
risk/constraint/technical-debt inventory entry that touches the
change surface, plus every Phase 2 security-analysis finding that
does. Cite entries by the report's own IDs where assigned, otherwise
by section and name. Never invent a parallel threat-ID series. An
unmapped entry is a FLAGGED GAP with routing — never a silent
omission.

**Treat the Phase 3 security decisions as authoritative.**
Where a Phase 3 design specification made a security-bearing decision
— a contract's authentication posture, a schema's sensitive-data
handling, a refactor's trust-boundary effect — the framework codifies
and cites it (Brief ID), it does not re-open it. If framework work
surfaces that a Phase 3 decision is untenable, record the finding in
the gap register routed toward the Steps 08/09 invalidation checks
and Step 12's amendment packages — do not silently work around it.

**Assign every boundary and control an ID; tag every control's
provenance.**
TB-NN for boundaries, SEC-NN for controls, [EXISTING-CODIFIED] /
[EXTENDED] / [NEW] on every control. Steps 08 and 09 cite these IDs;
Steps 10 and 12 verify the citations. An un-ID'd control cannot be
cited or verified.

**Depth follows the Step 02 §4 calibration.**
The calibration told you how much framework this change surface
warrants. A library whose change set touches one public boundary
produces a short register — but the register exists, the boundary
has controls, and the traceability is complete. Do not pad a small
surface to look thorough; do not truncate a large one to look lean.

**Audit logging at the change surface, connected to what exists.**
Specify which security-relevant events the change surface must log
and with what context, anchored to the observability locations the
baseline evidences and the Phase 3 observability-touchpoint design
specification where one exists (cite its touchpoint inventory by the
specification's own names). Strategic level only — no logger
configuration.

**Least privilege at strategic level.**
Per module the change surface touches (preliminary M-NN from Step 02
§1.1): what it may access, what it is explicitly prohibited from
doing. Step 08 assigns these as constraints; Step 09 applies them
concretely. Do not write permission manifests or role definitions —
that is implementation.

**Re-verify currency at step start.** *Inherited.*
Confirm the subject version, Design Specification Bundle currency,
and Improvement Plan currency before producing the framework. If the
subject advanced or a mechanism shipped early via a parallel track,
apply the invalidates-vs-grounds decision rule and say which.

**Produce the scorecard contribution before committing the artifact.**
Score the framework against all six Core Principles under the
inherited weights, with rationale citing specific rows. Never
re-weight.

**Structure the output for AI consumption.**
Steps 08, 09, 10, 11, and 12 consume this artifact mechanically.
Consistent headers, tables for comparative data, IDs on all rows,
explicit cross-references.

---

## Clarification Step

Read all pasted inputs thoroughly. Note the Step 02 §2 change surface
and §4 depth calibration, the security-implicated SP-NN rows, the
Phase 1 inventory entries plausibly touching the change surface, and
the security-bearing Phase 3 decisions. Then ask between **3 and 7
clarifying questions**, never more, one at a time.

**The first question is a presence check:** "I have the following
required inputs: [list]. The following appear missing: [list]. Can
you provide them, or confirm I should proceed noting the gap?"

Permitted clarification topics:

1. **Risk-inventory scope ambiguity.** If it is unclear whether a
   Phase 1 inventory entry touches the change surface (and therefore
   belongs in §3), ask rather than silently including or excluding.
2. **Existing security practice not visible in the evidence.** If
   the posture sweep suggests practice the code does not evidence
   (organizational secret management, signing infrastructure, review
   gates), ask what actually exists before codifying it.
3. **Residual-risk tolerance.** If an entry can only be partially
   mitigated at architecture level, ask the practitioner's tolerance
   for the residual before recording acceptance.
4. **Integration-peer boundary confirmation.** If Step 02 §1.2 peer
   boundaries leave the subject-side security obligations ambiguous,
   ask — the framework specifies the subject's side only.
5. **Sensitive-data identification.** If the change surface handles
   data whose sensitivity the Phase 1 report and Phase 3 schema
   specifications do not settle, ask — and note the Step 05
   coordination in §6 rather than producing the classification here.

Do not ask the practitioner to produce module security sections
(Step 09), constraint assignments (Step 08), or contract security
elements (Step 11). After clarifications, produce the complete
framework in a single response.

---

## Kickoff

> Paste the required inputs above this line, then paste this line to
> trigger the prompt.

```
I'm starting Step 04 of Phase 4 (Security Architecture Framework).
The required inputs are pasted above. Please read them thoroughly —
with particular attention to the Step 02 change surface map and depth
calibration, and the Phase 1 risk/constraint/technical-debt inventory
— then ask your clarifying questions one at a time, beginning with
the presence check, before producing the Security Architecture
Framework.
```

---

## Framework Procedure

Work through these clusters in order. The clusters are the derivation
path; the Output Format is the destination.

### Cluster 1 — Trust Boundary Sweep

Enumerate every boundary relevant to the run and assign TB-NN:

- **Existing boundaries** the Step 02 baseline evidences: the
  system's external perimeter(s), the integration-peer boundaries
  from Step 02 §1.2 (subject's side only), package/module seams that
  function as trust transitions, and boundaries to data stores or
  key/secret-bearing infrastructure.
- **NEW boundaries** the change surface creates — e.g., a new public
  contract surface is a new place external callers meet the system
  (for Diamonds, the MC-04 IDeploymentStrategy contract created
  exactly such a boundary: third-party strategy code executing
  inside the deployment path).
- **CHANGED boundaries** the change surface alters — e.g., a refactor
  that moves where a credential-bearing object is constructed moves
  a trust boundary with it (the MC-21 Signer-injection refactor is
  the type case: signer custody shifts from internal construction to
  caller injection).

Per boundary: what crosses it, whether it is Existing / New /
Changed, and which preliminary M-NN modules touch it. Boundaries
UNTOUCHED by the change surface are listed only to the depth the
calibration warrants — enough to codify the posture, no more.

### Cluster 2 — Existing-Controls Codification

For each existing boundary, codify the controls the system already
applies: authentication and authorization practice, transport and
at-rest encryption practice, input-validation posture, secret and
key handling, signing/attestation practice, existing audit trails.
Each becomes a SEC-NN tagged [EXISTING-CODIFIED], with the evidence
citation (or access-mode flag) and the boundary it governs. Where a
security-implicated SP-NN from Step 03 already names the practice,
cite it rather than duplicating it.

### Cluster 3 — Change-Surface Control Derivation

For each NEW or CHANGED boundary, derive the control set explicitly:

- **Authentication** — how the caller or crossing artifact is
  identified at this boundary (mechanism named at architecture
  level).
- **Authorization** — what operations are permitted to whom, and
  where that is enforced.
- **Encryption in transit / at rest** — required or not, per the
  sensitivity of what crosses or rests, referencing the data
  classification at the level the Phase 1 report and Phase 3 schema
  specifications establish (detail is Step 05; flag coordination).
- **Input-validation posture** — what the boundary must validate
  before trusting what crossed it (schema conformance, provenance
  checks, size/shape bounds — named, not implemented).

Each derived control is a SEC-NN tagged [EXTENDED] (existing practice
tightened or widened for the change set) or [NEW] (introduced by this
cycle), scoped to the boundaries the change surface touches. Where a
Phase 3 design specification already made the decision — a schema's
sensitive-field handling, a contract's conformance checks — the
control codifies that decision and cites the Brief ID.

### Cluster 4 — Risk-to-Control Traceability

Build the §3 table: every Phase 1 risk/constraint/technical-debt
inventory entry touching the change surface, plus every Phase 2
security-analysis finding that does, mapped to the SEC-NN control(s)
that address it — or FLAGGED GAP. Cite each entry by the report's own
ID where one was assigned, otherwise by section and name. Where
mitigation is partial, state the residual and the practitioner's
recorded tolerance. Entries that do not touch the change surface are
out of scope for mapping; note the exclusion rule applied so Step 12
can audit it.

### Cluster 5 — Audit Logging & Least Privilege

- **Audit logging:** the security-relevant events the change surface
  must log (boundary crossings, privilege exercises, signing and
  release-evidence events, validation failures), the context each
  must capture, and where they anchor — the baseline's existing
  observability locations and the Phase 3 observability-touchpoint
  inventory where one exists (cite touchpoints by the
  specification's own names). For Diamonds, the MC-12 release
  evidence schema is the illustrative case: the evidence bundle is
  itself a security-relevant audit artifact, and its emission events
  belong in this table.
- **Least privilege:** per module the change surface touches
  (preliminary M-NN), the strategic privilege posture — what it may
  access, what it is explicitly prohibited from doing. Strategic
  level only; Step 08 assigns, Step 09 applies.

### Cluster 6 — Gap Register

Consolidate every FLAGGED GAP from Cluster 4 plus any control the
change surface needs but no existing or derivable practice supplies.
Per gap: why no control exists, and the routing — resolve within
this step before finalizing; hand to Step 08/09 as a constraint to be
resolved at module level; record as a practitioner-accepted residual;
or, where the gap indicates an untenable upstream decision, route
toward the Steps 08/09 invalidation checks and Step 12's amendment
packages. A gap register with no routing is a list of known holes.

---

## Output Format

Produce the artifact using this exact structure. Do not omit
sections.

```markdown
# Security Architecture Framework — Phase 4 Step 04 Output

**Project:** [subject name and version]
**Framework Date:** [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]
**Step 01 Validation Report:** [date / version]
**Step 02 Baseline & Scoping Document:** [date / version]
**Step 03 Patterns & Standards:** [date / version]
**Phase 3 Design Specification Bundle:** [version]
**Phase 2 Improvement Plan:** [version, amendment date if any]
**Phase 1 Current-State Report:** [version]
**Code-Access Mode:** [Interview-only / Search-primary / Hybrid]
**Framework Depth (from Step 02 §4):** [as calibrated]
**Status:** Draft — Pending Practitioner Review

> ⚠️ This framework specifies trust boundaries, controls, and
> policies at architecture level. It contains no configuration
> values, key material, credential values, tool commands, or security
> code — Phase 5 implements from the module change specifications
> that cite these controls. Steps 08 and 09 cite SEC-NN at TB-NN;
> Steps 10 and 12 verify the citations.

---

## §1 — Trust Boundary Register

| TB-NN | Boundary | Existing / New / Changed | Modules Touching (prelim M-NN) | Notes |
|-------|----------|--------------------------|--------------------------------|-------|
| TB-01 | [e.g., public library interface — external consumers] | Existing | M-NN | [what crosses; evidence citation or access-mode flag] |
| TB-02 | [e.g., new extension-contract boundary from Brief ID] | New | M-NN, M-NN | [created by the change surface] |
| TB-03 | [e.g., integration-peer boundary — subject side only] | Changed | M-NN | [Step 02 §1.2 ref; what the change alters] |

## §2 — Control Register

| SEC-NN | Control | Provenance Tag | Boundary (TB-NN) | Risk Basis (Phase 1 entry / Phase 2 ref) | Applies To |
|--------|---------|----------------|-------------------|-------------------------------------------|------------|
| SEC-01 | [control, architecture level] | [EXISTING-CODIFIED] | TB-NN | [Phase 1 ID, or section + name / Phase 2 §-ref] | [M-NN list / boundary-wide] |
| SEC-02 | [control] | [EXTENDED] | TB-NN | [entry] | [M-NN list] |
| SEC-03 | [control] | [NEW] | TB-NN | [entry; Brief ID where Phase 3 decided it] | [M-NN list] |

[Per NEW/CHANGED boundary, the register must cover: authentication,
authorization, encryption in transit / at rest per sensitivity, and
input-validation posture — or state explicitly why a category does
not apply at that boundary.]

## §3 — Risk-to-Control Traceability

| Inventory Entry (Phase 1 ID or section + name / Phase 2 ref) | Touches Change Surface Via | Severity (as recorded upstream) | Mitigating Control(s) | Status | Residual / Notes |
|---------------------------------------------------------------|----------------------------|--------------------------------|-----------------------|--------|------------------|
| [entry] | [TB-NN / M-NN / Brief ID] | [as recorded] | SEC-NN, SEC-NN | [Mapped / Partially mapped / FLAGGED GAP] | [residual + recorded tolerance, if partial] |

**Exclusion rule applied:** [how "touches the change surface" was
decided; entries excluded under it are auditable by Step 12]

### §3.1 — Gap Register

| Gap | From Entry | Why No Control Exists | Routing |
|-----|-----------|----------------------|---------|
| [gap] | [entry] | | [Resolved here / Step 08–09 constraint / Accepted residual (practitioner) / Routed toward Step 12 amendment via Step 08–09 invalidation checks] |

## §4 — Audit Logging & Least Privilege

### §4.1 — Security-Relevant Events the Change Surface Must Log

| Event | Emitting Boundary / Module | Captured Context | Anchors To (existing location / Phase 3 touchpoint name) | SEC-NN |
|-------|----------------------------|------------------|----------------------------------------------------------|--------|
| | TB-NN / M-NN | [actor, resource, action, outcome — strategic] | | SEC-NN |

### §4.2 — Per-Module Privilege Posture (Strategic)

| Module (prelim M-NN) | Disposition | May Access | Explicitly Prohibited | SEC-NN |
|----------------------|-------------|-----------|----------------------|--------|
| M-NN | [NEW / CHANGED] | | | SEC-NN |

## §5 — Per-Artifact Principle Scorecard Contribution

Produced before this artifact is committed. Weights inherited from
Phase 2 Step 02 unchanged.

| Principle | Inherited Weight | Contribution | Rationale (cite specific rows) |
|-----------|------------------|--------------|-------------------------------|
| Security | | [PASS / CONDITIONAL / FAIL] | |
| Maintainability | | | |
| Economics | | | |
| Operations | | | |
| Scoring & Metrics | | | |
| Correctness Verification | | | |

**Conditional items (if any):** [what would resolve each, and where]

## §6 — Handoff Notes

[1–3 sentences each:]

- **For Step 05 (Data Architecture):** [encryption-at-rest controls
  awaiting classification detail; sensitive-data questions flagged]
- **For Step 08 (Module Impact Map):** [which SEC-NN must appear in
  per-module constraint assignments, per M-NN]
- **For Step 09 (Module Change Specifications):** [which controls
  each NEW/CHANGED module's security section must apply at which
  TB-NN, with risk basis]
- **For Step 11 (Formal Contracts):** [which controls are
  contract-relevant at formalizable boundaries]
- **For Steps 10 / 12 (verification):** [citation set to verify;
  §3.1 gaps that must surface at the gate; any finding routed toward
  the amendment packages]

---

## Version

v1.0 (initial Security Architecture Framework; amendments captured by
re-running Step 04 against amended upstream inputs)
```

---

## Evaluation Checklist

Before this artifact is accepted as complete, verify all items:

- [ ] Every control has a unique SEC-NN, a provenance tag
      ([EXISTING-CODIFIED] / [EXTENDED] / [NEW]), and a risk basis
      cited from the Phase 1 inventory (report's own ID, or section +
      name) or the Phase 2 security analysis
- [ ] Every boundary in §1 has TB-NN, an Existing / New / Changed
      designation, and its touching modules (preliminary M-NN);
      integration-peer and external boundaries from Step 02 §1.2 are
      included, subject side only
- [ ] Every NEW/CHANGED boundary has explicit controls covering
      authentication, authorization, encryption in transit / at rest
      per sensitivity, and input-validation posture — or a stated
      reason a category does not apply
- [ ] §3 traceability is complete: no Phase 1 inventory entry or
      Phase 2 finding touching the change surface is unmapped; every
      gap is FLAGGED with routing in §3.1; the exclusion rule is
      stated
- [ ] The existing posture is codified, not silently rewritten —
      [EXISTING-CODIFIED] controls reflect observed practice with
      evidence citations or access-mode flags; no system-wide [NEW]
      standard the change set will not land
- [ ] Phase 3 security-bearing decisions are cited (Brief IDs), not
      re-designed; any untenable finding is routed, not worked around
- [ ] Framework depth matches the Step 02 §4 calibration — neither
      padded nor truncated
- [ ] §4 names the security-relevant events the change surface must
      log, anchored to existing locations or Phase 3 touchpoint
      names, and gives each touched module a strategic privilege
      posture
- [ ] §5 scorecard contribution is present, under the inherited
      weights, with rationale citing specific rows
- [ ] §6 handoff notes are specific per consuming step
- [ ] No implementation content — no configuration values, key
      material, credential values, tool commands, or security code
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)

---

*Part of the Phase 4 (Existing Projects) Architecture & Modular Design Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `architecture-modular-design.existing-project.instructions.md`*
*Previous step: `step-03-shared-patterns-and-standards.prompt.md`*
*Next step: `step-05-data-architecture-framework.prompt.md`*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial existing-projects Security Architecture Framework prompt, adapted from the greenfield Phase 4 Step 03 counterpart. Replaces greenfield threat-model elaboration with the track's three disciplines: existing posture codified first with provenance tags ([EXISTING-CODIFIED] / [EXTENDED] / [NEW]), zero-trust and least-privilege derivation applied at every NEW/CHANGED boundary, and depth set by the Step 02 §4 calibration. Grounds risk-to-control traceability in the Phase 1 risk/constraint/technical-debt inventory and Phase 2 security analysis (cited by the reports' own IDs or section + name — no parallel threat-ID series), the existing-projects analog of the greenfield T-NN citations. Six-cluster procedure (boundary sweep; existing-controls codification; change-surface control derivation; traceability; audit logging & least privilege; gap register) and a six-section output (TB-NN register, SEC-NN register, traceability with gap routing, audit/privilege posture, scorecard contribution, handoff notes) feeding Steps 08, 09, and 11 and verified by Steps 10 and 12. |
