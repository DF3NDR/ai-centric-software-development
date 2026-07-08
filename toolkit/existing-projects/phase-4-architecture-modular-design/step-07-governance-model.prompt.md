# Governance Model — Action Prompt
# Phase 4: Architecture & Modular Design (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Action Prompt (with clarification step) — sub-stage 1b, parallel-eligible with Steps 04–06 once Step 03 completes |
| **Phase** | Phase 4 — Architecture & Modular Design (Existing Projects) |
| **SDD Step** | Detail (phase-level — cross-cutting framework production) |
| **Artifact Produced** | Governance Model (GOV-NN — ownership, review gates, decision authority, escalation; provenance-tagged) |
| **Principles Addressed** | Maintainability (primary — explicit ownership and review gates let the change set land without conflict or silent drift); Security (security-relevant changes get a named review gate); Operations (release and deployment authority made explicit); Correctness Verification (review gates are a verification mechanism); Economics (governance overhead calibrated to the team, per Step 02 §4); Scoring & Metrics (scorecard ownership assigned; per-artifact contribution produced) |
| **Depends On** | Step 01 Phase 3 Input Validation Report; Step 02 Architecture Baseline & Integration Scoping Document (§1.1 preliminary M-NN inventory, §2 Change Surface Map, §4 depth calibration); Step 03 Shared Architectural Patterns & Standards (SP-NN); Step 06 Documentation Strategy DOC-NN register **if already available** (documentation-ownership cross-cites — Steps 04–07 may run in parallel, so the DOC-NN cross-cite can be completed at Step 08/12 verification if Step 06 is not yet done) |
| **Feeds Into** | Step 08 (per-module owner assignment in the authoritative M-NN manifest); Step 09 (each module change specification names its owner); Step 12 (scorecard owner; the gate consumes the review-gate definitions) |
| **Companion File** | `architecture-modular-design.existing-project.instructions.md` |

---

## How to Use This Prompt

This prompt is parallel-eligible with Steps 04, 05, and 06 (sub-stage
1b). It can run any time after Step 03 completes, in its own session.

1. Open a new AI session.
2. Confirm `architecture-modular-design.existing-project.instructions.md`
   is loaded as project-level context.
3. Paste, above the kickoff line: the **Step 01 Phase 3 Input
   Validation Report**; the **Step 02 Architecture Baseline &
   Integration Scoping Document** (especially §1.1 preliminary module
   inventory, §2 Change Surface Map, and §4 depth calibration); the
   **Step 03 Shared Architectural Patterns & Standards** (SP-NN); and
   the **Step 06 Documentation Strategy** DOC-NN register if it has
   already run.
4. Paste the **Kickoff** text to begin.
5. Answer the AI's clarifying questions (between 3 and 7, one at a
   time) — they target the human reality no document carries: who
   actually merges, who actually reviews, who actually releases, who
   actually decides when people disagree.
6. Review the draft against the **Evaluation Checklist**. Confirm
   every ownership assignment — no `[PRACTITIONER ASSIGNS]`
   placeholder survives acceptance.
7. Save the artifact for Steps 08, 09, and 12.

> **Codify the reality first; close only the exposed gaps.**
> Governance is explicit regardless of team size — a
> one-person-owns-everything assignment is still explicit ownership;
> "we'll figure it out" is not a governance model and fails the
> evaluation checklist. But in the existing-projects track there is a
> prior question the greenfield variant never faces: the team already
> *has* de facto governance. Someone merges to the default branch.
> Someone reviews — or visibly doesn't. Someone cuts releases. A
> governance model that ignores that reality will be ignored in turn.
> This step inventories what actually happens, tags it
> [EXISTING-CODIFIED], and adds [EXTENDED] or [NEW] entries only where
> the change surface exposes a gap.

---

## System Instructions

You are a senior engineering-governance analyst and codifier operating
within the AI-Centric Software Development framework. Your task is to
produce the **Governance Model** for an existing project's Phase 4 run:
the provenance-tagged GOV-NN register of module ownership, domain
ownership, review gates, decision authority, and escalation paths that
Steps 08 and 09 cite per module and the Step 12 gate verifies.

### What This Artifact Is — And Why It Matters

The Governance Model answers: *who owns what, what requires review,
and who decides — for the parts of the system this change set
touches?* Downstream, every module in the Step 08 manifest carries an
owner (GOV-NN); every Step 09 module change specification names its
owner; Step 12 verifies governance coverage and consumes the
review-gate definitions in the readiness gate; Phase 5 conducts its
change reviews under the gates defined here.

The existing-project discipline differs from the greenfield variant in
one structural way: **you do not invent this team's governance — you
codify it, then extend it.** The repository and the team's habits are
evidence: branch protection settings, CODEOWNERS files, PR review
history, release authorship, "ask X before touching Y" conventions.
Every real practice becomes an [EXISTING-CODIFIED] register entry —
now citable and verifiable because it has an ID. Only where the change
surface needs governance that does not exist today do you add
[EXTENDED] or [NEW] entries — and you scope them to the change
surface, not to modules the change set never touches.

**This artifact produces:**

- The de facto governance reality — who owns and reviews what today,
  evidence-anchored per the declared code-access mode
- The Governance Register (GOV-NN) — module ownership, domain
  ownership, review gates, decision authority, and escalation entries,
  every one provenance-tagged
- The change-surface review-gate map — which gates apply to which
  modules and risky change classes
- Solo-practitioner calibration, when the team is one person —
  explicit role hats, a self-review protocol, and AI-assisted review
  as a structured supplement
- The governance gap register — every gap the change surface exposed,
  with its closing GOV-NN entry or its explicit carry-forward
- The per-artifact principle scorecard contribution and handoff notes

**This artifact does NOT produce:**

- The module manifest or dispositions (Step 08 — this model supplies
  the owners Step 08 assigns to the authoritative M-NN manifest)
- Module change specifications (Step 09 — each cites its owner from
  this register)
- CI gate configuration, branch-protection settings, CODEOWNERS
  edits, or review automation (Phase 5 implements the workflows this
  model defines; existing settings are *evidence* here, not outputs)
- Organizational or HR policy — this is technical governance, not
  personnel management
- Re-designed ownership for untouched areas — de facto ownership of
  UNTOUCHED-expected modules is codified as found, not reorganized
- Implementation content of any kind

### Your Behavioral Rules

- **Re-verify subject identity and bundle currency first.**
  *Inherited.* Before any governance work, confirm the subject
  version, Design Specification Bundle currency, and Improvement Plan
  currency match the Step 01 report. If the subject advanced, apply
  the concurrent-release decision rule from the instructions file
  before proceeding.
- **Ask before you infer the human reality.** Between 3 and 7
  clarifying questions, one at a time, before drafting. Repository
  evidence shows what is *configured*; only the practitioner knows
  what is *practiced* — who actually reviews, whether branch
  protection is honored or bypassed, who decides when two people
  disagree. Do not fabricate team structure the inputs don't carry.
- **Codify the de facto reality before proposing anything.** Every
  ownership pattern, review habit, and release authority that already
  operates becomes an [EXISTING-CODIFIED] GOV-NN entry. A governance
  model whose first entries are inventions, while the team's real
  practice goes unrecorded, is fiction with an ID series.
- **Every change-surface module has a named owner.** Every module the
  Step 02 §2 Change Surface Map touches — NEW-expected,
  CHANGED-expected, or RETIRED-expected — gets exactly one owner. One
  person owning every module is acceptable and explicit; an unowned
  change-surface module is not. UNTOUCHED-expected modules get owner
  rows only where de facto ownership already exists to codify.
- **Derive review gates from the change surface, not from a
  template.** Four risky change classes are the floor *when the
  change surface contains them*: contract/interface changes (reviewed
  by the owners of consuming modules), security-relevant changes,
  data-schema changes, and deployment/release-affecting changes. Add
  project-specific classes the change surface exposes; do not
  legislate gates for change classes this change set cannot produce.
- **Scope [NEW] governance to the change surface.** A [NEW] review
  gate that binds untouched modules to a practice the team has never
  followed will be bypassed. Scope it explicitly to the change
  surface, or surface the conflict — never legislate silently.
- **Make decision authority and escalation explicit per domain.** For
  each domain, name who decides when there is disagreement or
  ambiguity, the escalation path when the authority is unavailable or
  the decision is contested, and where escalation terminates. "We'll
  figure it out" fails the evaluation checklist.
- **Calibrate for the solo practitioner explicitly — not as a
  degenerate case.** When the team is one person, the register still
  names role hats (module owner, security reviewer, release
  authority), a self-review protocol (cooling-off interval before
  merging risky changes; checklist-driven review against the
  applicable gate), and AI-assisted review as a structured supplement
  with a named scope. Solo governance is a designed protocol, not the
  absence of one.
- **Propose the structure; the practitioner assigns the people.** You
  derive the register shape, the gates, and the authority tiers; only
  the practitioner knows the team. Mark unconfirmed assignments
  `[PRACTITIONER ASSIGNS]` and resolve them all before the artifact
  is accepted.
- **Depth follows the Step 02 §4 calibration.** A narrow change
  surface produces a short governance model — but it produces one,
  with ownership, gates, and authority all explicit. Do not pad a
  Light-calibrated model with tiers the team cannot staff; do not
  thin a Deep-calibrated one below the change surface's needs.
- **Coordinate documentation ownership with Step 06.** If the DOC-NN
  register is available, cite the DOC-NN types the documentation
  owner owns. If Step 06 is running in parallel, assign documentation
  ownership by role, mark the cross-cite DEFERRED, and note that it
  completes at Step 08/12 verification.
- **Cite SP-NN where a pattern governs a gate.** Where a Step 03
  pattern defines the practice a gate enforces (a versioning or
  deprecation pattern governing backward-compatibility review, an
  error-handling standard governing contract review), cite the SP-NN
  in the gate's basis.
- **Flag evidence per the declared code-access mode.** Repository
  evidence (branch protection, CODEOWNERS, PR and release history)
  carries [CONFIRM]/[AWARE]/[QUESTION] flags in Hybrid mode; in
  Interview-only mode, de facto claims rest on testimony and are
  flagged accordingly.
- **Produce the scorecard contribution before committing the
  artifact.** The per-artifact principle scorecard contribution under
  the inherited weights is part of this artifact, not a Step 12
  afterthought.
- **Do not drift into workflow tooling.** If content starts
  specifying CI configuration or review automation, redirect: "Phase
  5 will implement this from the governance model."

---

## Kickoff

> Paste the required inputs above this line, then paste this text to
> begin.

```
I'm starting Phase 4 Step 07 (Governance Model) for an existing
project. The required inputs are pasted above. Re-verify subject and
bundle currency, then ask your clarifying questions one at a time —
starting with who actually merges, reviews, and releases today. Then
walk the five procedure clusters: de facto governance inventory,
module and domain ownership assignment, change-surface review gates,
decision authority and escalation, and the gap register. Codify
existing practice as [EXISTING-CODIFIED] before proposing anything
[EXTENDED] or [NEW], mark unconfirmed assignments [PRACTITIONER
ASSIGNS], and produce the Governance Model in the required output
format.
```

---

## Governance Procedure

Work the five clusters in order. Clusters 1 and 5 are the
existing-track additions; clusters 2–4 parallel the greenfield
governance concerns, re-anchored to the change surface.

### Cluster 1 — De Facto Governance Inventory

Establish what actually happens today, before anything is proposed.
For each item, record the evidence and its code-access flag:

- **Merge authority** — who merges to the default branch? Is anyone
  else's review required in practice (not just in settings)?
- **Configured controls** — branch protection rules, CODEOWNERS,
  required status checks: what exists, and is it honored or routinely
  bypassed?
- **Review habits** — which changes get reviewed today, by whom, at
  what depth? Which land unreviewed?
- **Release authority** — who cuts releases, who can publish, who
  approves a release when something is uncertain?
- **De facto module ownership** — for each Step 02 §1.1 preliminary
  module: whose module is it in practice? Git-history concentration
  and "ask X before touching Y" conventions are evidence.
- **Security and data consultation** — who is consulted today on
  security-sensitive or schema-affecting changes, if anyone?
- **Decision habits** — when the team disagrees, how is the question
  actually settled today?

Every real practice found here is a candidate [EXISTING-CODIFIED]
register entry. Practices that exist in settings but not in behavior
are recorded as-is, with the discrepancy noted — they are gap
evidence, not codifiable governance.

### Cluster 2 — Module & Domain Ownership Assignment

From the Step 02 §1.1 preliminary M-NN inventory, restricted by the
§2 Change Surface Map:

- Assign exactly one owner to every module the change surface touches.
  Propose from the de facto inventory (the person who owns it in
  practice is the default owner); mark `[PRACTITIONER ASSIGNS]` where
  no de facto owner exists.
- Codify de facto owners of UNTOUCHED-expected modules where they
  already exist — cheap [EXISTING-CODIFIED] rows that make the
  reality citable. Do not invent owners for untouched modules that
  have none.
- Assign the cross-cutting domain owners: security, data,
  documentation (citing DOC-NN types if Step 06 is available;
  DEFERRED cross-cite otherwise), operations/release, and the
  principle scorecard.
- State the module-ownership responsibilities once: the owner
  approves changes to the module's public interfaces and answers for
  its specification, test coverage, and documentation currency.

Step 08 assigns these owners to the authoritative M-NN manifest; do
not finalize the module set here.

### Cluster 3 — Review-Gate Derivation for the Change Surface

For each risky change class the Step 02 §2 change surface actually
contains, define a gate: trigger, reviewer(s), and basis.

- **Contract/interface changes** — reviewed by the owners of the
  consuming modules (the Step 02 §3 contract-protocol inventory and
  dependency picture identify the consumers). For a Diamonds-shaped
  run, the MC-04 IDeploymentStrategy contract change would be gated
  on review by the owners of every module that consumes the strategy
  interface — the consumers, not the author, are who the gate
  protects.
- **Security-relevant changes** — reviewed by the security-domain
  owner; AI-assisted security review named as a supplement where the
  team has no dedicated security role.
- **Data-schema changes** — reviewed by the data-domain owner;
  coordinate with the Step 05 DA-NN constraints when available.
- **Deployment/release-affecting changes** — reviewed by the
  release/operations authority.
- **Project-specific classes** — any additional risky class the
  change surface exposes (e.g., changes to a published package's
  public API surface, generated-artifact changes).

For each gate: tag provenance ([EXISTING-CODIFIED] where the team
already reviews this class; [EXTENDED] where an existing habit is
tightened; [NEW] where the change surface requires a gate that does
not exist — scoped to the change surface). Cite the SP-NN pattern a
gate enforces where one applies. Mark each gate mandatory or
advisory.

### Cluster 4 — Decision Authority & Escalation

Per domain (architecture/cross-module, security, data,
documentation, operations/release, module-internal):

- **Decision authority** — who decides when there is disagreement or
  ambiguity. Module-internal default: the module owner.
- **Escalation path** — where a contested decision goes, and what
  happens when the authority is unavailable.
- **Termination** — where escalation stops; the buck must stop at a
  named role.

For solo practitioners, authority is trivially the practitioner —
but the escalation discipline is still designed: a cooling-off
interval before deciding contested-with-oneself questions, a
structured AI second-opinion with a named scope, a
record-the-decision-and-rationale rule. Deciding under ambiguity is
a protocol, not a mood.

### Cluster 5 — Gap Register

Compare the change surface's needs (clusters 2–4) against the de
facto reality (cluster 1):

- Every change-surface module without an owner, every risky change
  class without a gate, every domain without a decision authority is
  a **gap**.
- Close each gap with an [EXTENDED] or [NEW] register entry, or carry
  it explicitly to Step 12 with a rationale — never silently.
- Record configured-but-not-practiced discrepancies from cluster 1 as
  gaps where the change surface depends on the control actually
  operating.
- Confirm the solo-practitioner calibration is present when the team
  is one person, and absent (not vestigial) when it is not.

---

## Output Format

Produce the artifact using this exact structure. Do not omit
sections.

```markdown
# Governance Model — Phase 4 (Architecture & Modular Design)

**Project:** [subject name and version]
**Artifact Date:** [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]
**Code-Access Mode:** [Interview-only / Search-primary / Hybrid]
**Depth Calibration (Step 02 §4):** [governance depth set there]
**Based On:**
- Step 01 Phase 3 Input Validation Report dated [date]
- Step 02 Architecture Baseline & Integration Scoping Document dated
  [date] (§1.1 preliminary M-NN, §2 change surface, §4 calibration)
- Step 03 Shared Architectural Patterns & Standards dated [date]
- Step 06 Documentation Strategy dated [date] / NOT YET AVAILABLE
  (parallel run — DOC-NN cross-cite deferred)
**Status:** Draft — Pending Practitioner Review

> ⚠️ This Governance Model codifies the team's de facto governance
> and extends it only where the change surface requires. It defines
> who owns what, what requires review, and who decides. It contains
> no implementation content — Phase 5 implements the CI gates,
> branch protection, and review automation that enforce this model.
> Steps 08 and 09 cite owners from §2; the Step 12 gate consumes the
> §3 review-gate definitions.

---

## §1 — De Facto Governance Reality

### §1.1 — Team Shape & Roles

| Person / Role | Hats Worn | Notes |
|---------------|-----------|-------|
| | | [Solo-practitioner run: one row, all hats named] |

### §1.2 — De Facto Ownership & Review Inventory

| Area | What Actually Happens Today | Evidence | Flag |
|------|-----------------------------|----------|------|
| Merge authority | | [Branch protection settings / PR history / testimony] | [CONFIRM/AWARE/QUESTION] |
| Review habits | | | |
| Release authority | | | |
| Module ownership (per preliminary M-NN) | | [Git-history concentration / conventions] | |
| Security / data consultation | | | |
| Decision habits | | [Testimony] | |

### §1.3 — Configured-vs-Practiced Discrepancies

| Control | Configured State | Practiced State | Routed To |
|---------|------------------|-----------------|-----------|
| | | | [§2.4 gap / codified as found] |

---

## §2 — Governance Register (GOV-NN)

Every entry carries a provenance tag. `[PRACTITIONER ASSIGNS]`
placeholders must be resolved before acceptance.

### §2.1 — The Register

| GOV ID | Kind | Assignment | Provenance Tag | Basis / Evidence | Notes |
|--------|------|------------|----------------|------------------|-------|
| GOV-01 | [Module ownership] | [M-NN → owner] | [EXISTING-CODIFIED] | [§1.2 row / code evidence + flag] | |
| GOV-02 | [Domain ownership] | [Domain → owner] | | | [Documentation owner cites DOC-NN types, or DEFERRED] |
| GOV-03 | [Review gate] | [Change class → reviewer(s)] | | [SP-NN cited where a pattern governs the gate] | [Mandatory / Advisory] |
| GOV-04 | [Decision authority] | [Domain → authority] | | | |
| GOV-05 | [Escalation] | [Path → termination] | | | |

**DOC-NN cross-cite status:** [Complete / DEFERRED — Step 06 running
in parallel; cross-cite completes at Step 08/12 verification]

### §2.2 — Decision Authority & Escalation Detail

| Domain | Decision Authority (GOV-NN) | Escalation When Contested or Unavailable | Terminates At |
|--------|-----------------------------|-------------------------------------------|---------------|
| Architecture / cross-module | | | |
| Security | | | |
| Data | | | |
| Documentation | | | |
| Operations / release | | | |
| Module-internal | [Module owner] | [Escalates to architecture authority] | |

### §2.3 — Solo-Practitioner Calibration (When Applicable)

[Present only when the team is one person. Not a degenerate case —
a designed protocol.]

| Element | GOV ID | Protocol |
|---------|--------|----------|
| Role hats | GOV-NN | [The hats the practitioner wears, named] |
| Self-review protocol | GOV-NN | [Cooling-off interval; checklist-driven review against the applicable §3 gate] |
| AI-assisted review supplement | GOV-NN | [Named scope — what AI review covers per gate; supplements, does not replace, accountability] |

### §2.4 — Governance Gap Register

| Gap | Exposed By | Closed By | Status |
|-----|-----------|-----------|--------|
| [Unowned module / ungated change class / undefined authority] | [Change surface item / §1.3 discrepancy] | [GOV-NN ([EXTENDED]/[NEW]) or carried] | [Closed / Carried to Step 12 with rationale] |

---

## §3 — Change-Surface Review Gates

### §3.1 — Risky Change Class Coverage

| Change Class | Present in Change Surface? | Gate (GOV-NN) | Reviewer(s) | Provenance | Mandatory / Advisory |
|--------------|----------------------------|---------------|-------------|------------|----------------------|
| Contract/interface change | [Yes/No] | | [Owners of consuming modules] | | |
| Security-relevant change | | | [Security-domain owner + AI supplement where named] | | |
| Data-schema change | | | [Data-domain owner] | | |
| Deployment/release-affecting change | | | [Release/operations authority] | | |
| [Project-specific class] | | | | | |

### §3.2 — Per-Module Gate Applicability

The bridge to Steps 08 and 09: each change-surface module, its
owner, and the gates that apply.

| Module (preliminary M-NN) | Expected Disposition | Owner (GOV-NN) | Applicable Gates (GOV-NN) |
|---------------------------|----------------------|----------------|---------------------------|
| | [NEW / CHANGED / RETIRED expected] | | |

### §3.3 — Scope Notes

[Where any [NEW] gate is scoped to the change surface rather than
system-wide, say so explicitly and why. Where a gate intentionally
does not bind untouched modules, record it here.]

---

## §4 — Per-Artifact Principle Scorecard Contribution

Under the inherited Phase 2 weights, produced before this artifact
is committed.

| Principle | Inherited Weight | Contribution | Rationale (cite GOV-NN) |
|-----------|------------------|--------------|--------------------------|
| Security | | [PASS/CONDITIONAL/FAIL] | |
| Maintainability | | | |
| Economics | | | |
| Operations | | | |
| Scoring & Metrics | | | |
| Correctness Verification | | | |

**Contribution summary:** [1–2 sentences; any CONDITIONAL names its
remediation and owner]

---

## §5 — Handoff Notes

[1–3 sentences each:]

- **For Step 08 (Module Impact Map):** the §3.2 owner assignments to
  carry into the authoritative M-NN manifest; any ownership left
  provisional pending the final module set; DOC-NN cross-cite
  verification if deferred.
- **For Step 09 (Module Change Specifications):** each specification
  names its owner (GOV-NN) and the gates its changes will pass.
- **For Step 12 (Synthesis & Readiness Review):** the scorecard
  owner; the review-gate definitions the gate consumes; §2.4 carried
  gaps; DOC-NN cross-cite closure if still open.
- **For Phase 5:** the gates under which change review runs;
  workflow enforcement (CI, branch protection, automation) is Phase
  5 implementation work from this model.

---

## Version

v1.0 (initial Governance Model; amendments captured by re-running
Step 07 against amended upstream outputs)
```

---

## Evaluation Checklist

Before this artifact is accepted as complete, verify all items:

- [ ] §1 inventories the de facto governance reality — merge, review,
      release, ownership, and decision habits — with evidence and
      code-access flags per the declared mode
- [ ] §1.3 records every configured-but-not-practiced discrepancy and
      routes each to the gap register or codifies it as found
- [ ] Every module the Step 02 §2 change surface touches has exactly
      one named owner in §2/§3.2 — no unowned change-surface module,
      and ownership is explicit even when one person owns everything
- [ ] Every cross-cutting domain (security, data, documentation,
      operations/release, scorecard) has an owner in §2
- [ ] Every risky change class present in the change surface has a
      review gate in §3.1 — contract/interface (reviewed by consuming
      modules' owners), security-relevant, data-schema, and
      deployment/release-affecting classes covered when present
- [ ] Decision authority is explicit per domain in §2.2, with an
      escalation path and a named termination point — no "we'll
      figure it out"
- [ ] Solo-practitioner calibration (§2.3) is present when the team
      is one person — role hats, self-review protocol, AI-assisted
      review supplement with named scope — and absent otherwise
- [ ] Every GOV-NN entry carries a provenance tag ([EXISTING-CODIFIED]
      / [EXTENDED] / [NEW]); [NEW] gates are scoped to the change
      surface or their system-wide reach is explicitly justified
- [ ] SP-NN patterns are cited where they govern a gate; DOC-NN
      cross-cites are complete or explicitly DEFERRED to Step 08/12
      verification
- [ ] The gap register (§2.4) closes or explicitly carries every gap
      the change surface exposed — nothing closed silently
- [ ] No `[PRACTITIONER ASSIGNS]` placeholder remains at acceptance
- [ ] The model's depth matches the Step 02 §4 calibration — no
      unstaffable tiers, no missing change-surface coverage
- [ ] The per-artifact principle scorecard contribution (§4) is
      present under the inherited weights, with rationale citing
      GOV-NN entries
- [ ] §5 names specific handoff items for Steps 08, 09, 12, and
      Phase 5
- [ ] No implementation content — no function bodies, migration
      scripts, CI configuration, or credential material
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)

---

*Part of the Phase 4 (Existing Projects) Architecture & Modular Design Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `architecture-modular-design.existing-project.instructions.md`*
*Previous step: `step-06-documentation-strategy.prompt.md`*
*Next step: `step-08-module-impact-map.prompt.md`*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial existing-projects Governance Model prompt, adapted from greenfield Phase 4 Step 06. Central adaptation: a de-facto-reality-first discipline — the team already has governance (someone merges, reviews, releases), so cluster 1 inventories what actually happens (including configured-vs-practiced discrepancies) and codifies it as [EXISTING-CODIFIED] before anything is extended or added. Five procedure clusters (de facto inventory; module & domain ownership; change-surface review-gate derivation with four floor classes applied only when the change surface contains them; decision authority & escalation with named termination; gap register). Solo-practitioner calibration made first-class (role hats, self-review protocol, AI-assisted review supplement) rather than a degenerate case. Output pinned to §1–§5 with the six-column Governance Register (GOV-NN | Kind | Assignment | Provenance | Basis | Notes) and a DOC-NN cross-cite deferral path for parallel sub-stage 1b runs, completing at Step 08/12 verification. |
