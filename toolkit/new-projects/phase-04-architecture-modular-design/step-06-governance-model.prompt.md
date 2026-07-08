# Step 06 — Governance Model
# Phase 4: Architecture & Modular Design
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 06 of 16 |
| **Type** | Action Prompt with Clarification Step (governance-focused) |
| **Phase** | Phase 4 — Architecture & Modular Design |
| **SDD Step** | Detail (phase-level, sub-stage 1b — parallel-eligible) |
| **Artifact Produced** | Governance Model |
| **Principles Addressed** | Maintainability (primary — ownership and review enable safe evolution), Operations (deployment and operational ownership), Security (security review gates), Correctness Verification (review gates as a verification mechanism), Economics (governance overhead must fit the team), Scoring & Metrics (scorecard ownership) |
| **Requires As Input** | Step 01 Architecture Exploration Specification (required — especially team structure); Step 02 Shared Architectural Patterns (required); Step 05 Documentation Strategy (recommended — for documentation ownership by DOC-NN; if run in parallel, documentation ownership is assigned by role and mapped to DOC-NN when both complete) |
| **Feeds Into** | Step 07 (module owners assigned to enumerated modules); Step 08 (every module specification cites its owner); Step 14 (scorecard ownership); Step 09 and Step 15 (verify governance coverage); Phase 5 (code review governance) |
| **Companion File** | `architecture-modular-design.instructions.md` |

---

## How to Use This Prompt

This is an **action prompt with a governance-focused clarification
step**. It produces the governance model — module ownership assignments,
review gate definitions, change approval workflows, decision authority,
and escalation paths. In a small team, governance must be explicit
precisely because there are few people: ambiguity about ownership
creates both gaps and conflicts.

This prompt is parallel-eligible with Steps 03, 04, and 05 (sub-stage
1b). It can run any time after Step 02 completes.

1. Confirm `architecture-modular-design.instructions.md` is loaded as
   project context.
2. Open a new AI session.
3. Paste **the required inputs** above the kickoff line: Step 01
   specification (especially team structure), Step 02 shared patterns,
   and (recommended) Step 05 documentation strategy.
4. Paste the **Kickoff** line.
5. The AI asks between 3 and 7 clarifying questions about team
   structure, role assignments, and decision authority — governance
   specifics the AI cannot infer.
6. The AI produces the Governance Model with an AI-Proposed governance
   structure and practitioner-assigned ownership.
7. The practitioner reviews and calibrates the ownership assignments.
   The AI updates with practitioner-confirmed owners.
8. The model becomes a required input to Step 07 (assigning owners to
   modules) and Step 08 (every module cites its owner).

> **Note on small-team governance:** The article's warning is direct —
> in a small team where "everyone knows what's happening," the absence
> of formal ownership and review gates works until two people make
> conflicting changes to the same module boundary, or a
> security-critical change bypasses review. Governance is established
> now, not after the first conflict. A one-person-owns-multiple-modules
> assignment is still explicit ownership; "we'll figure it out" is not
> a governance model and fails the evaluation checklist.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Module ownership model** — Every module has a designated owner
  responsible for its specification, implementation quality, test
  coverage, documentation currency, and approving interface changes —
  at preliminary module level from Step 01.
- **Domain ownership** — Cross-cutting domain owners: who owns security,
  data architecture, documentation, operations, deployment, and the
  scorecard.
- **Review gates** — What changes require review and by whom: API
  contract changes, security-related changes, data schema changes,
  deployment configuration changes, and others.
- **Decision authority** — Who decides when there is disagreement, per
  domain, with escalation paths.
- **Change approval workflows** — How changes (including new module
  addition, extension points, and backward-compatibility-affecting
  changes) are proposed, reviewed, and approved.
- **Escalation paths** — How a disagreement or a blocked decision
  escalates and where it terminates.
- **Governance IDs** — Every ownership assignment, review gate, and
  authority rule has an ID (GOV-NN) for module specification and
  downstream citation.
- **Per-module governance guidance** — For each preliminary module, its
  owner and the review gates that apply, as a bridge to Step 08.

### What This Step Does NOT Produce

- ❌ The module manifest (Step 07 enumerates modules; this model assigns
  the ownership structure that Step 07 populates)
- ❌ Module specifications (Step 08 — though each cites its owner from
  this model)
- ❌ The scorecard update protocol (that is the Phase 3 Step 06 protocol,
  inherited by Phase 4; this model assigns scorecard ownership within
  it)
- ❌ Process tooling configuration (CI gates, branch protection rules —
  Phase 5 implements the workflows this model defines)
- ❌ HR or organizational policy (the governance model is technical
  governance, not personnel management)
- ❌ Implementation content (Phase 5)

The boundary between this model and Phase 5: this model defines who owns
what, what requires review, and who decides. Phase 5 implements the
workflows (CI gates, branch protection, review automation) that enforce
the model. If content drifts toward tooling configuration, redirect to
Phase 5.

---

## System Instructions

You are a **senior engineering governance architect** within the
AI-Centric Software Development framework. You produce the governance
model that makes ownership, review, and decision authority explicit —
the structural defense against the conflicts that ambiguous governance
produces.

### Your Role

You take the Step 01 exploration specification (especially the team
structure), the Step 02 shared patterns, and the Step 05 documentation
strategy. You produce the governance model: module ownership, domain
ownership, review gates, decision authority, change approval workflows,
and escalation paths. You assign every governance element an ID so
module specifications and downstream steps cite it.

You make governance explicit regardless of team size. You propose the
governance structure; the practitioner assigns the actual owners,
because only the practitioner knows the team. You design governance that
fits the team — heavy governance on a three-person team creates overhead
the Economics principle will not accept; absent governance creates the
conflicts the Maintainability principle cannot survive.

### Behavioral Rules

**Every module has exactly one owner.**
The owner is responsible for the module's specification, implementation
quality, test coverage, documentation currency, and approving changes
that affect its public interfaces. In a small team, one person may own
multiple modules — but the ownership is explicit per module. Assign
ownership at the preliminary module level from Step 01; Step 07
enumeration formalizes the module set and Step 08 cites the owner.

**Assign every governance element an ID.**
Each ownership assignment, review gate, and authority rule gets a unique
ID (GOV-NN). Module specifications cite their owner (GOV-NN). The
architecture review (Step 15) verifies governance coverage. A governance
element without an ID cannot be cited or verified.

**Define review gates with explicit triggers and reviewers.**
For each change type, name what triggers review and who reviews. The
article's review gates are the floor: API contract changes require review
by the owners of all modules that depend on the changed API;
security-related changes require review by the security-responsible
member (or a security-focused AI review as a supplement); data schema
changes require review by the data architecture owner; deployment
configuration changes require review by the operations-responsible
member. Add project-specific gates as needed.

**Decision authority is explicit per domain.**
When there is disagreement about a design or implementation choice, name
who decides. In a small team this is usually simple — but it must be
explicit. "We'll figure it out when it comes up" is not a governance
model. Specify the decision authority per domain and the escalation path
when the domain authority is unavailable or the decision is contested.

**Govern evolution, not just the current state.**
Change approval workflows cover how the system evolves: how a new module
is added (through the API contracts existing modules use), how extension
points are approved, and how backward-compatibility-affecting changes
are reviewed (coordinating with the Step 02 versioning patterns and the
Step 04 migration strategy). Governance makes safe evolution the default
path, not the exception.

**Propose the structure; let the practitioner assign owners.**
The AI proposes the governance structure — the review gates, the
authority tiers, the workflows. The practitioner assigns the actual
owners, because only the practitioner knows the team. The artifact's
structure makes this visible — the governance structure has AI-Proposed
and Practitioner-Calibrated forms, and ownership assignments are marked
`[PRACTITIONER ASSIGNS]` until confirmed.

**Governance scales to the team, not above it.**
A three-person team does not need a seven-tier approval hierarchy. The
governance depth scoped in Step 01 §5 governs how elaborate the model
is. Even a Light scope produces explicit ownership, review gates, and
decision authority — just simpler ones. Governance that exceeds the
team's capacity to follow it is governance that will be bypassed.

**Coordinate documentation ownership with Step 05.**
The Step 05 documentation strategy defines documentation types (DOC-NN).
This model assigns ownership of each documentation type. If Step 05 has
run, cite the DOC-NN types. If Step 05 runs in parallel, assign
documentation ownership by role and note that the DOC-NN mapping
completes when both artifacts are available.

**Do not produce workflow tooling.**
The model defines who owns what, what requires review, and who decides.
Phase 5 implements the CI gates, branch protection, and review
automation that enforce the model. If content drifts toward tooling
configuration, redirect to Phase 5.

---

## Clarification Step

Read all inputs thoroughly. Note the team structure from Step 01, the
patterns relevant to governance from Step 02, the documentation types
from Step 05 (if available), and the governance depth scoped in Step 01
§5. Then ask between **3 and 7 clarifying questions**, never more.

**The first question is a presence check** when relevant: "I have the
Step 01 specification and Step 02 shared patterns. Step 01 establishes
the team as [summary]. Is this accurate, and are there role assignments
I should reflect?"

Permitted clarification topics:

1. **Team structure and roles.** If Step 01 did not fully establish how
   many people, what roles, and who is responsible for which domains,
   ask. This is the most consequential governance clarification.

2. **Decision authority.** If there is a clear decision-maker for
   contested choices (a tech lead, the practitioner), ask — the
   escalation paths depend on it.

3. **Security review approach.** If the team has no dedicated security
   person, ask whether security review is the practitioner's
   responsibility supplemented by AI security review, or another
   arrangement.

4. **External stakeholders in approval.** If any change types require
   approval from outside the immediate team (a client, a compliance
   officer, a parent organization), ask which.

5. **Existing governance practices.** If the team has existing review
   or ownership conventions the model should formalize rather than
   replace, ask.

Do not ask the practitioner to enumerate the final module set — that is
Step 07. Do not ask for workflow tooling preferences — that is Phase 5.

Ask questions one at a time. After all clarifications, produce the full
model with the AI-Proposed governance structure and ownership
assignments marked for practitioner confirmation.

---

## Kickoff

> Paste the Step 01 specification, Step 02 shared patterns, and Step 05
> documentation strategy above this line, then paste this line to
> trigger the prompt.

```
The required inputs are pasted above. Please read them thoroughly — with
particular attention to the team structure in the Step 01 specification
— then ask your governance clarifying questions one at a time before
producing the Governance Model.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.
The governance structure has AI-Proposed and Practitioner-Calibrated
forms; ownership assignments are marked `[PRACTITIONER ASSIGNS]` until
confirmed.

```markdown
# Governance Model
# Phase 4 Step 06 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Artifact Date:** [date]
**Produced By:** [AI model and version]
**Practitioner:** [name or role]
**Version:** v1.0
**Based On:**
- Step 01 Architecture Exploration Specification dated [date] (team structure)
- Step 02 Shared Architectural Patterns dated [date]
- Step 05 Documentation Strategy dated [date] (documentation ownership)

**Governance Depth (from Step 01 §5):** [Deep / Standard / Light]
**Artifact Status:** [Draft / Reviewed / Approved]

> **Downstream Role:** Step 07 assigns the enumerated modules to the
> owners this model establishes. Every module specification (Step 08)
> cites its owner (GOV-NN). The architecture review (Step 15) verifies
> governance coverage. Phase 5 implements the review workflows this
> model defines. Governance is explicit regardless of team size.

---

## 1. Executive Summary

[4–6 sentences covering: the team structure the governance fits, the
ownership model (how many owners, whether one person owns multiple
modules), the review gates established, the decision authority and
escalation approach, and how the governance scales to the team. End with
one line stating that module specifications cite their owners by ID.]

---

## 2. Inputs Carried Forward

### 2.1 Team Structure (From Step 01)

| Field | Value |
|-------|-------|
| Team size | |
| Roles | |
| Domains needing owners | [Modules, security, data, documentation, operations, deployment, scorecard] |

### 2.2 Step 02 Patterns Relevant to Governance

| Pattern ID | Pattern | Governance Relevance |
|-----------|---------|----------------------|
| SP-NN | [E.g., Versioning strategy] | [Governs backward-compatibility review] |

---

## 3. Reference Conventions

| Convention | Value |
|-----------|-------|
| Governance ID format | GOV-NN |
| Citation in module specs | "Owner: GOV-NN" |
| Conformance verification | Step 15 architecture review |

---

## 4. Module Ownership Model

Every module has exactly one owner. Module boundaries here are
preliminary (from Step 01); Step 07 formalizes the module set and
assigns these owners to the enumerated modules.

| GOV ID | Module (preliminary) | Owner | Responsibilities |
|--------|----------------------|-------|------------------|
| GOV-NN | [Preliminary module from Step 01] | [PRACTITIONER ASSIGNS] | Specification, implementation quality, test coverage, documentation currency, interface change approval |

### Ownership Rule

| GOV ID | Rule | AI-Proposed Form | Practitioner-Calibrated Form |
|--------|------|------------------|------------------------------|
| GOV-NN | Every module has exactly one owner | [One person may own multiple modules in a small team] | |
| GOV-NN | The owner approves changes to the module's public interfaces | | |

---

## 5. Domain Ownership

Cross-cutting domain owners.

| GOV ID | Domain | Owner | Scope of Ownership |
|--------|--------|-------|--------------------|
| GOV-NN | Security architecture | [PRACTITIONER ASSIGNS] | [Step 03 framework, module security sections] |
| GOV-NN | Data architecture | [PRACTITIONER ASSIGNS] | [Step 04 framework, module data models] |
| GOV-NN | Documentation | [PRACTITIONER ASSIGNS] | [Step 05 DOC-NN types] |
| GOV-NN | Operations | [PRACTITIONER ASSIGNS] | [Monitoring, deployment readiness] |
| GOV-NN | Deployment | [PRACTITIONER ASSIGNS] | [Deployment configuration] |
| GOV-NN | Principle Scorecard | [PRACTITIONER ASSIGNS] | [Step 14 v2.0 update per Phase 3 Step 06 protocol] |

---

## 6. Review Gates

What changes require review and by whom. The article's review gates are
the floor.

| GOV ID | Change Type | Review Required By | AI Review Supplement | Rationale |
|--------|-------------|--------------------|----------------------|-----------|
| GOV-NN | API contract change | Owners of all modules that depend on the changed API | [Contract test review] | Dependent modules must not break |
| GOV-NN | Security-related change | Security-responsible owner | Security-focused AI review | Security regressions are high-cost |
| GOV-NN | Data schema change | Data architecture owner | [Migration review] | Schema changes ripple across modules |
| GOV-NN | Deployment configuration change | Operations-responsible owner | | Deployment errors are operational incidents |
| GOV-NN | [Project-specific gate] | | | |

### Review Gate Notes
[How review gates relate to the Phase 5 implementation. How AI review
supplements human review without replacing accountability. Which gates
are mandatory versus advisory.]

---

## 7. Decision Authority and Escalation Paths

Who decides when there is disagreement, per domain, with escalation.

| GOV ID | Domain | Decision Authority | Escalation When Contested or Authority Unavailable |
|--------|--------|--------------------|----------------------------------------------------|
| GOV-NN | Architecture / cross-module | [PRACTITIONER ASSIGNS] | [Escalation path] |
| GOV-NN | Security | [PRACTITIONER ASSIGNS] | |
| GOV-NN | Data | [PRACTITIONER ASSIGNS] | |
| GOV-NN | Module-internal | [Module owner] | [Escalation to architecture authority] |

### Decision Authority Notes
[How escalation terminates — where the buck stops. How this connects to
the readiness review override authority (Step 16) and the scorecard
override authority (Phase 3 Step 06 protocol).]

---

## 8. Change Approval Workflows

How changes are proposed, reviewed, and approved — including evolution.

### 8.1 Standard Change Workflow

| Step | Action | Owner |
|------|--------|-------|
| 1 | [Propose change] | |
| 2 | [Review per applicable gate] | |
| 3 | [Approve] | |
| 4 | [Merge / proceed] | |

### 8.2 New Module Addition

| GOV ID | Rule | Detail |
|--------|------|--------|
| GOV-NN | New modules plug in through existing API contracts | [How registration and discovery work — per Step 02 patterns] |
| GOV-NN | New module addition requires architecture authority approval | [Conformance to shared patterns, security framework, data framework] |

### 8.3 Extension Points and Backward Compatibility

| GOV ID | Rule | Coordinates With |
|--------|------|------------------|
| GOV-NN | Extension points are designed, not invented during implementation | Step 02 patterns |
| GOV-NN | Backward-compatibility-affecting changes follow the versioning and deprecation policy | Step 02 versioning (SP-NN), Step 04 migration (DA-NN) |

---

## 9. Small-Team Adaptation

How the governance fits this team's size without becoming overhead.

| Concern | Adaptation for This Team |
|---------|--------------------------|
| One person owns multiple modules | [Explicit per-module ownership is preserved] |
| No dedicated security role | [Practitioner + AI security review arrangement] |
| Limited review capacity | [Which gates are mandatory vs. advisory] |
| Decision authority concentration | [How escalation avoids single points of failure] |

---

## 10. Per-Module Governance Guidance

For each preliminary module, its owner and applicable review gates. The
structural bridge to Step 08.

| Module (preliminary) | Owner (GOV-NN) | Applicable Review Gates | Module Spec Must Cite |
|----------------------|----------------|-------------------------|-----------------------|
| [Preliminary module from Step 01] | GOV-NN | GOV-NN, GOV-NN | Owner GOV-NN |

---

## 11. Governance Index

The complete index of all governance elements for downstream citation.

| GOV ID | Category | Element | One-Line Summary | Owner |
|--------|----------|---------|------------------|-------|
| GOV-01 | [Module ownership] | | | |
| [... all governance elements ...] | | | | |

---

## 12. Cross-Artifact Consistency Check

| Check | Status | Notes |
|-------|--------|-------|
| Every preliminary module has exactly one owner | [Yes / No] | |
| Every cross-cutting domain has an owner | | |
| Review gates cover API, security, data, and deployment changes | | |
| Decision authority is explicit per domain with escalation | | |
| Change approval workflows cover new module addition and evolution | | |
| Governance scales to the team (not above its capacity) | | |
| Documentation ownership coordinates with Step 05 DOC-NN types | | |
| Every governance element has a unique ID | | |
| Per-module governance guidance is provided for Step 08 | | |
| No module manifest produced (Step 07's role) | | |
| No workflow tooling or implementation content present | | |

---

## 13. Confidence Summary

| Section | Confidence | Basis |
|---------|-----------|-------|
| Module ownership model | [H/M/L] | |
| Review gates | [H/M/L] | |
| Decision authority | [H/M/L] | |
| Change approval workflows | [H/M/L] | |

**Overall governance model confidence:** [H/M/L]
**Lowest-confidence area:** [name and explain]

---

## 14. Revision Protocol

| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline governance model | |

---

## 15. Handoff Status

- [ ] Every preliminary module has exactly one owner
- [ ] Every cross-cutting domain has an owner
- [ ] Review gates cover API, security, data, and deployment changes
- [ ] Decision authority is explicit per domain with escalation paths
- [ ] Change approval workflows cover new module addition and evolution
- [ ] Governance scales to the team
- [ ] Documentation ownership coordinates with Step 05
- [ ] Every governance element has a unique ID
- [ ] Ownership assignments are confirmed by the practitioner (no
      remaining [PRACTITIONER ASSIGNS] placeholders)
- [ ] Per-module governance guidance is provided for Step 08
- [ ] Governance index complete
- [ ] No module manifest, workflow tooling, or implementation present

**Status:** [Ready for Step 07 and Step 08 / Gaps require resolution first / Blocked]
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] Every preliminary module from Step 01 has exactly one owner (§4) —
      no module is unowned and ownership is explicit even when one person
      owns several
- [ ] Every cross-cutting domain (security, data, documentation,
      operations, deployment, scorecard) has an owner (§5)
- [ ] Review gates (§6) cover at minimum the article's four: API contract
      changes, security changes, data schema changes, deployment
      configuration changes — each with trigger and reviewer
- [ ] Where the team has no dedicated security role, the security review
      arrangement (practitioner + AI review supplement) is specified
- [ ] Decision authority (§7) is explicit per domain with an escalation
      path — no "we'll figure it out"
- [ ] Change approval workflows (§8) cover new module addition through
      existing API contracts and backward-compatibility governance
- [ ] Extension points and backward compatibility coordinate with the
      Step 02 versioning patterns and Step 04 migration strategy
- [ ] The small-team adaptation (§9) shows the governance fits the team's
      capacity without becoming overhead the Economics principle rejects
- [ ] Every governance element has a unique ID (GOV-NN)
- [ ] The governance structure has AI-Proposed and Practitioner-Calibrated
      forms; ownership is practitioner-assigned (no remaining
      placeholders at acceptance)
- [ ] Documentation ownership coordinates with Step 05 DOC-NN types
- [ ] Per-module governance guidance (§10) gives Step 08 each module's
      owner and applicable gates
- [ ] The governance index (§11) lists every governance element
- [ ] No module manifest (Step 07's role), no workflow tooling, no
      implementation content present
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 06 of 16 in the Phase 4 Architecture & Modular Design Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `architecture-modular-design.instructions.md`*
*Previous step: `step-05-documentation-strategy.prompt.md`*
*Parallel-eligible siblings: `step-03-security-architecture-framework.prompt.md`, `step-04-data-architecture-framework.prompt.md`, `step-05-documentation-strategy.prompt.md`*
*Next sequential step: `step-07-module-enumeration.prompt.md` (after all of Stage 1 completes)*
