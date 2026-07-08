# Step 04 — Data Architecture Framework
# Phase 4: Architecture & Modular Design
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 04 of 16 |
| **Type** | Action Prompt with Clarification Step |
| **Phase** | Phase 4 — Architecture & Modular Design |
| **SDD Step** | Detail (phase-level, sub-stage 1b — parallel-eligible) |
| **Artifact Produced** | Data Architecture Framework |
| **Principles Addressed** | Correctness Verification (integrity constraints, consistency strategy), Security (data classification, encryption coordination), Maintainability (schema evolution, migration), Operations (data lifecycle, storage operations), Economics (storage cost implications), Scoring & Metrics (data scoring inputs) |
| **Requires As Input** | Step 01 Architecture Exploration Specification (required); Step 02 Shared Architectural Patterns (required — data-implicated patterns); Phase 3 data architecture ADR (required); Phase 3 Compliance Design Constraints (recommended — data handling, residency); Phase 3 Observability Hooks Handoff (recommended — data operation hooks) |
| **Feeds Into** | Step 03 (encryption-at-rest coordinates with data classification); Step 07 (data ownership informs module boundaries); Step 08 (every module's data models section conforms to this framework); Steps 10–13 (API contracts reference data types); Step 09 and Step 15 (verify data conformance); Step 14 (data scorecard inputs) |
| **Companion File** | `architecture-modular-design.instructions.md` |

---

## How to Use This Prompt

This is an **action prompt with a clarification step**. It produces the
detailed, component-level data architecture — elaborating the Phase 3
data architecture ADR and the Step 02 data-implicated patterns into a
concrete data classification scheme, data ownership model, storage
architecture, component-level data flows, consistency and transaction
strategy, integrity constraints, and migration strategy.

This prompt is parallel-eligible with Steps 03, 05, and 06 (sub-stage
1b). It can run any time after Step 02 completes.

1. Confirm `architecture-modular-design.instructions.md` is loaded as
   project context.
2. Open a new AI session with a large context window.
3. Paste **the required inputs** above the kickoff line: Step 01
   specification, Step 02 shared patterns, Phase 3 data architecture
   ADR, and (recommended) Phase 3 Compliance Design Constraints and
   Observability Hooks Handoff.
4. Paste the **Kickoff** line.
5. The AI asks between 3 and 7 clarifying questions — beginning with a
   presence check on the required inputs — about data classification
   tiers, transaction requirements, and project-specific data context.
6. The AI produces the Data Architecture Framework with a data
   classification scheme, constraint IDs for module specification
   citation, and per-module data guidance.
7. Review the output against the Evaluation Checklist before accepting.
8. The framework becomes a required input to every module
   specification's data models section (Step 08) and a coordination
   reference for Step 03 (encryption at rest).

> **Note on the framework-versus-module boundary:** This framework
> establishes the cross-cutting data architecture — classification,
> ownership rules, storage architecture, consistency strategy,
> integrity constraint patterns, migration strategy, and shared data
> structures. The detailed per-module data schemas are produced in
> Step 08's data models section, conforming to this framework. If
> content drifts toward a specific module's full schema, that belongs
> in Step 08 — establish the constraint here that the module schema
> will conform to.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Data classification scheme** — The classification tiers (e.g.,
  public, internal, confidential, regulated) and the handling rules
  per tier, with each tier assigned an ID for citation.
- **Data ownership model** — Which module owns which data domain, the
  data-ownership rule (modules own their data; cross-module data access
  is through interfaces, not shared tables), at preliminary module
  level from Step 01.
- **Storage architecture** — Elaborating the Phase 3 storage model
  commitment: which logical stores exist, what each holds at the
  architecture level, and the access pattern for each.
- **Component-level data flows** — How data moves between conceptual
  components: what flows where, in what direction, synchronously or
  asynchronously, with what transformation.
- **Consistency and transaction strategy** — The consistency model
  (strong, eventual, causal) per data domain, transaction boundaries,
  and how cross-module consistency is maintained.
- **Data integrity constraints** — The integrity rules that apply
  across the system: referential integrity, validation constraints,
  invariants, uniqueness rules — as constraint patterns module schemas
  apply.
- **Migration and schema-versioning strategy** — How schemas evolve,
  how migrations are sequenced, and how backward compatibility is
  maintained (coordinating with the Step 02 versioning patterns).
- **Data lifecycle** — Retention, archival, and deletion at strategic
  level, coordinating with the Phase 3 compliance constraints.
- **Constraint IDs** — Every constraint, classification tier, and rule
  has an ID (DA-NN) for module specification citation.
- **Per-module data guidance** — For each preliminary module, the data
  domains it owns and the constraints its data models must apply.

### What This Step Does NOT Produce

- ❌ Module specifications (Step 08 — though each module's data models
  section conforms to this framework and cites its constraints)
- ❌ The complete per-module physical schema (Step 08 produces the
  detailed module data models within this framework's constraints)
- ❌ Formal API contracts (Steps 10–13 — though they reference the
  data types this framework classifies)
- ❌ The security architecture (Step 03 — though encryption-at-rest
  decisions coordinate with the classification scheme here)
- ❌ Actual DDL, migration scripts, ORM code, or seed data (Phase 5)
- ❌ Modifications to the Phase 3 data architecture ADR (if the storage
  model is insufficient, surface the gap for Step 16 amendment — do
  not silently change it)

If the data architecture cannot satisfy a compliance constraint or a
performance requirement without changing the Phase 3 storage model,
surface that as a finding for Step 16, not as a silent re-commitment.

---

## System Instructions

You are a **senior data architect** within the AI-Centric Software
Development framework, with deep knowledge of data modeling, consistency
models, transaction design, and schema evolution. You produce the
detailed, component-level data architecture that every module
specification applies.

### Your Role

You take the Phase 3 data architecture ADR, the Step 02 data-implicated
patterns, and the Phase 3 compliance constraints bearing on data. You
produce the detailed data architecture: classification scheme,
ownership model, storage architecture, component-level data flows,
consistency and transaction strategy, integrity constraints, and
migration strategy. You assign every constraint an ID so module
specifications cite it.

You enforce data ownership — each module owns its data, and other
modules access that data through interfaces, not by reaching into shared
tables. You make consistency explicit — every data domain has a named
consistency model, not an implicit assumption. You connect classification
to handling, so the security framework's encryption decisions have a
classification to act on.

### Behavioral Rules

**Classify data before anything else.**
The data classification scheme is the spine of the framework. Every
data domain maps to a classification tier, and each tier carries
handling rules (encryption requirement, access restrictions, retention,
residency). The security framework (Step 03) consumes this
classification to make encryption-at-rest decisions. A data architecture
without classification leaves the security framework guessing.

**Assign every constraint an ID.**
Each classification tier, ownership rule, consistency rule, integrity
constraint, and migration rule gets a unique ID (DA-NN). Module
specifications cite these IDs in their data models sections. The
cross-module consistency prompt (Step 09) and the architecture review
(Step 15) verify that each module's data model applies the constraints.
A constraint without an ID cannot be cited or verified.

**Modules own their data.**
The data-ownership rule is foundational: each data domain has exactly
one owning module, and other modules access it through that module's
interface — not by direct table access or shared mutable state. Specify
the ownership boundaries at the preliminary module level from Step 01.
Step 07 enumeration formalizes the module set; Step 09 verifies that no
two modules claim ownership of the same data domain and no data domain
is unowned.

**Make consistency explicit per domain.**
Every data domain has a named consistency model (strong, eventual,
causal, read-your-writes). Where modules share a consistency boundary,
specify how cross-module consistency is maintained (sagas, outbox,
two-phase patterns at the strategic level — not the implementation).
An unnamed consistency model is a correctness defect waiting to surface
in Phase 5.

**Specify integrity constraints as patterns modules apply.**
Referential integrity, validation rules, invariants, and uniqueness
constraints are specified as constraint patterns (DA-NN) that module
data models apply to their specific entities. The framework establishes
the pattern; the module specification applies it to concrete fields.

**Coordinate encryption with the security framework.**
The classification scheme states which tiers require encryption at rest.
Step 03's encryption strategy consumes this. Cite the coordination
explicitly: "Tier [confidential] (DA-NN) requires encryption at rest,
satisfied by SEC-NN." Do not produce the encryption mechanism here —
that is Step 03's role; produce the classification that drives it.

**Specify schemas at the architecture level, not the implementation
level.**
Shared and cross-cutting data structures (reference data, common value
types, shared envelopes) may be specified here as logical schemas —
entities, fields, types, constraints, relationships. Do not produce
physical DDL, indexes tuned for a specific engine, or ORM mappings —
those are Phase 5. The detailed per-module schemas are Step 08.

**Migration strategy honors the versioning patterns.**
The Step 02 versioning patterns (schema migration approach, deprecation
policy) constrain how schemas evolve. Elaborate them into the migration
strategy: how migrations are sequenced, how backward compatibility is
held during a migration window, and how a migration is rolled back.
Cite the Step 02 pattern (SP-NN) each migration rule elaborates.

**Honor compliance constraints bearing on data.**
The Phase 3 Compliance Design Constraints specify data handling,
residency, retention, and deletion requirements. Each compliance
constraint bearing on data maps to a framework rule (DA-NN). Cite the
compliance constraint each rule satisfies.

**Surface data needs that require Phase 3 or Phase 2 amendment.**
If a data requirement cannot be met without changing the Phase 3 storage
model commitment or a Phase 2 cost commitment (e.g., the classification
scheme implies a storage cost the envelope does not allow), surface it
as a finding for Step 16. Do not silently re-commit the storage model.

**Do not produce implementation.**
The framework specifies classification, ownership, flows, consistency,
constraints, and migration strategy — not DDL, migration scripts, or
ORM code. If content drifts toward implementation, redirect to Phase 5.

---

## Clarification Step

Read all inputs thoroughly. Note the Phase 3 storage model commitment,
the Step 02 data-implicated patterns, the compliance constraints bearing
on data, and the data framework depth scoped in Step 01 §5. Then ask
between **3 and 7 clarifying questions**, never more.

**The first question is a presence check:** "I have the following
required inputs: [list what is present]. The following appear missing:
[list]. Can you provide the missing inputs, or confirm I should proceed
noting the gap?"

Permitted clarification topics:

1. **Data classification tiers.** If the project handles regulated or
   sensitive data and the compliance constraints imply classification
   tiers but do not enumerate them, ask the practitioner to confirm the
   tier scheme. This is often the most consequential data decision.

2. **Consistency requirements per domain.** If the Phase 3 storage
   model is compatible with multiple consistency models, ask which data
   domains require strong consistency and which tolerate eventual
   consistency.

3. **Transaction boundary expectations.** If the project has operations
   that span data domains (and therefore potentially modules), ask how
   the practitioner expects cross-domain transactions to be handled.

4. **Existing data infrastructure.** If the organization has existing
   data stores, schemas, or data governance the architecture must
   integrate with, ask.

5. **Retention and residency specifics.** If the compliance constraints
   imply retention or residency requirements but leave the specifics
   open, ask before specifying the data lifecycle rules.

Do not ask the practitioner to produce module data models — those are
Step 08. Do not ask for formal API data contracts — those are Steps
10–13.

Ask questions one at a time. After clarifications, produce the full
framework in a single response.

---

## Kickoff

> Paste the Step 01 specification, Step 02 shared patterns, Phase 3 data
> architecture ADR, Phase 3 Compliance Design Constraints, and Phase 3
> Observability Hooks Handoff above this line, then paste this line to
> trigger the prompt.

```
The required inputs are pasted above. Please read all inputs thoroughly
— with particular attention to the Phase 3 data architecture ADR and
any compliance constraints bearing on data — then ask your clarifying
questions one at a time, beginning with the presence check, before
producing the Data Architecture Framework.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.

```markdown
# Data Architecture Framework
# Phase 4 Step 04 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Artifact Date:** [date]
**Produced By:** [AI model and version]
**Practitioner:** [name or role]
**Version:** v1.0
**Based On:**
- Step 01 Architecture Exploration Specification dated [date]
- Step 02 Shared Architectural Patterns dated [date] (data-implicated patterns)
- Phase 3 Data Architecture ADR (ADR-[NNNN]) dated [date]
- Phase 3 Compliance Design Constraints dated [date] (data handling)
- Phase 3 Observability Hooks Handoff dated [date] (data operation hooks)

**Data Framework Depth (from Step 01 §5):** [Deep / Standard / Light]
**Artifact Status:** [Draft / Reviewed / Approved]

> **Downstream Role:** Every module specification's data models section
> (Step 08) conforms to this framework and cites its constraints
> (DA-NN). The security framework (Step 03) consumes the classification
> scheme to make encryption-at-rest decisions. The cross-module
> consistency prompt (Step 09) and the architecture review (Step 15)
> verify each module's data model applies the constraints.

---

## 1. Executive Summary

[5–7 sentences covering: the storage model committed in Phase 3 the
framework elaborates, the classification scheme, the data ownership
approach, the consistency strategy across domains, the migration
strategy, any data needs requiring Phase 3/Phase 2 amendment, and the
compliance constraints the framework satisfies. End with one line
stating that module data models conform to and cite these constraints.]

---

## 2. Inputs Carried Forward

### 2.1 Phase 3 Data Architecture Commitment

| Element | Commitment | Source |
|---------|-----------|--------|
| Storage model | | Phase 3 ADR-[NNNN] |
| Primary data store(s) | | Phase 3 ADR-[NNNN] |
| Consistency commitment | | Phase 3 ADR-[NNNN] or [resolved in clarification] |
| Data residency commitment | | Phase 3 ADR-[NNNN] / Compliance constraints |

### 2.2 Step 02 Data-Implicated Patterns Elaborated Here

| Pattern ID | Pattern | What This Framework Adds |
|-----------|---------|--------------------------|
| SP-NN | [E.g., Data access / repository pattern] | [Detailed data architecture] |
| SP-NN | [E.g., Transaction boundaries] | |

### 2.3 Compliance Constraints Bearing on Data

| Constraint ID | Constraint | Source |
|--------------|-----------|--------|
| [From Phase 3 Step 08] | [E.g., PHI encrypted at rest] | Phase 3 Compliance Design Constraints |

---

## 3. Constraint Reference Conventions

| Convention | Value |
|-----------|-------|
| Constraint ID format | DA-NN |
| Citation in module specs | "Conforms to DA-NN" |
| Conformance verification | Step 09 (cross-module consistency), Step 15 (architecture review) |
| Coordination with security | Classification tiers (DA-NN) drive encryption controls (SEC-NN) |

---

## 4. Data Classification Scheme

The classification tiers and the handling rules per tier. The security
framework (Step 03) consumes this to make encryption decisions.

| Tier ID | Classification Tier | Definition | Encryption at Rest | Access Restriction | Retention Direction | Residency |
|---------|--------------------|-----------|--------------------|--------------------|--------------------|-----------|
| DA-01 | [E.g., Regulated] | [What data falls here] | [Required / Not required] | [Who may access] | [Strategic direction] | [Region constraint] |
| DA-02 | [E.g., Confidential] | | | | | |
| DA-03 | [E.g., Internal] | | | | | |
| DA-04 | [E.g., Public] | | | | | |

### Classification Notes
[How the classification maps to the compliance constraints. Which tiers
the security framework must encrypt. How classification is assigned to
new data as the system evolves.]

---

## 5. Data Ownership Model

Which module owns which data domain. Module boundaries here are
preliminary (from Step 01); Step 07 formalizes them, Step 09 verifies
no overlaps or gaps.

| Constraint ID | Data Domain | Owning Module (preliminary) | Classification Tier | Access By Other Modules |
|--------------|------------|----------------------------|--------------------|-----------------------|
| DA-NN | [E.g., User identity] | [Preliminary module] | DA-NN | [Through which interface — never direct] |

### Ownership Rule

| Constraint ID | Rule | Rationale |
|--------------|------|-----------|
| DA-NN | Each data domain has exactly one owning module | [Independent evolution, clear responsibility] |
| DA-NN | Cross-module data access is through interfaces, not shared tables | [Decoupling, contract enforcement] |

---

## 6. Storage Architecture

Elaborating the Phase 3 storage model. Which logical stores exist and
what each holds at the architecture level.

| Constraint ID | Logical Store | Holds | Classification Tier(s) | Access Pattern | Consistency Model |
|--------------|--------------|-------|------------------------|----------------|-------------------|
| DA-NN | [E.g., Primary relational store] | [What data domains] | DA-NN | [Read-heavy / write-heavy / mixed] | [Strong / eventual] |

### Storage Notes
[How the storage architecture honors the Phase 3 storage model
commitment. Where the storage architecture has cost implications
relevant to the Phase 2 envelope.]

---

## 7. Component-Level Data Flows

How data moves between conceptual components. Component level, not
module level — Step 07 refines to module specificity.

| Flow ID | From | To | Data | Direction | Sync/Async | Transformation |
|---------|------|----|----- |-----------|------------|----------------|
| DA-NN | [Component] | [Component] | [What data] | [One-way / bidirectional] | [Synchronous / asynchronous / event] | [Any transformation] |

### Data Flow Notes
[How the flows align with the Step 02 inter-module communication
patterns. Which flows cross trust boundaries (coordinate with Step 03).]

---

## 8. Consistency and Transaction Strategy

### 8.1 Consistency Model Per Domain

| Constraint ID | Data Domain | Consistency Model | Rationale |
|--------------|------------|-------------------|-----------|
| DA-NN | [Domain] | [Strong / eventual / causal / read-your-writes] | [Why this model fits] |

### 8.2 Transaction Boundaries

| Constraint ID | Transaction Scope | Spans Modules? | Strategy | Rationale |
|--------------|-------------------|----------------|----------|-----------|
| DA-NN | [Operation requiring atomicity] | [Yes / No] | [Local transaction / saga / outbox — strategic] | |

### 8.3 Cross-Module Consistency

[How consistency is maintained when an operation spans modules. The
strategic pattern (saga, outbox, eventual reconciliation) — not the
implementation. How failures mid-transaction are handled at the
architecture level.]

---

## 9. Data Integrity Constraints

Integrity rules specified as patterns module data models apply to their
concrete entities.

| Constraint ID | Integrity Rule | Type | Applies To | Module Spec Applies It By |
|--------------|----------------|------|-----------|---------------------------|
| DA-NN | [E.g., Referential integrity across owned entities] | [Referential / validation / invariant / uniqueness] | [Which data domains] | [Citing DA-NN in the data models section] |

### Integrity Notes
[How integrity constraints enable the correctness verification the
framework emphasizes — data integrity constraints enable automated
correctness checking. How constraints relate to the validation patterns
in Step 02.]

---

## 10. Migration and Schema-Versioning Strategy

Elaborating the Step 02 versioning patterns into a data migration
strategy.

| Constraint ID | Migration Rule | Elaborates Pattern | Rationale |
|--------------|----------------|--------------------|-----------|
| DA-NN | [E.g., Expand-contract migration sequence] | SP-NN | [Zero-downtime evolution] |
| DA-NN | [E.g., Backward compatibility window] | SP-NN | |
| DA-NN | [E.g., Migration rollback approach] | SP-NN | |

### Migration Notes
[How the migration strategy supports the extensibility the article
emphasizes. The actual migration scripts are Phase 5 — this establishes
the strategy they implement.]

---

## 11. Data Lifecycle

Retention, archival, and deletion at strategic level, coordinating with
the Phase 3 compliance constraints.

| Constraint ID | Data Domain | Retention Direction | Archival Approach | Deletion Approach | Satisfies Compliance |
|--------------|------------|--------------------|--------------------|-------------------|----------------------|
| DA-NN | [Domain] | [E.g., minimum 1 year] | [Strategic] | [Hard delete / soft delete / anonymize] | [Constraint ID] |

### Lifecycle Notes
[How the lifecycle satisfies compliance retention and deletion
requirements. Actual retention policy enforcement is Phase 5/Phase 7 —
this establishes the strategic direction.]

---

## 12. Coordination With Security Framework

The explicit handoff to Step 03. Where the data classification drives a
security control.

| Classification Tier (DA-NN) | Security Requirement | Step 03 Control That Satisfies It |
|----------------------------|----------------------|-----------------------------------|
| DA-NN | [E.g., Encryption at rest] | [SEC-NN — to be cited by Step 03] |

[If Step 03 has already run, cite the actual SEC-NN. If Step 03 runs in
parallel, this table states the requirement Step 03 must satisfy.]

---

## 13. Per-Module Data Guidance

For each preliminary module, the data domains it owns and the
constraints its data models must apply. The structural bridge to Step 08
data models sections.

| Module (preliminary) | Owned Data Domains | Constraints Module Spec Must Apply | Classification Tier(s) |
|----------------------|--------------------|------------------------------------|------------------------|
| [Preliminary module from Step 01] | [Domains] | DA-NN, DA-NN | DA-NN |

---

## 14. Constraint Index

The complete index of all constraints for downstream citation.

| Constraint ID | Category | Constraint Name | Satisfies Compliance | Coordinates With |
|--------------|----------|-----------------|----------------------|------------------|
| DA-01 | [Classification] | | [Constraint ID] | SEC-NN |
| [... all constraints ...] | | | | |

---

## 15. Cross-Artifact Consistency Check

| Check | Status | Notes |
|-------|--------|-------|
| Storage architecture aligns with Phase 3 data architecture ADR | [Yes / No] | |
| Every data-implicated Step 02 pattern is elaborated | | |
| Every data domain has exactly one owning module | | |
| Every data domain has a named consistency model | | |
| Classification tiers drive encryption requirements for Step 03 | | |
| Every compliance constraint bearing on data maps to a rule | | |
| Integrity constraints are specified as citable patterns | | |
| Migration strategy elaborates the Step 02 versioning patterns | | |
| Every constraint has a unique ID | | |
| Per-module data guidance is provided for Step 08 | | |
| Data needs requiring amendment are surfaced for Step 16 | | |
| No module data models, formal contracts, or implementation present | | |

---

## 16. Confidence Summary

| Section | Confidence | Basis |
|---------|-----------|-------|
| Classification scheme | [H/M/L] | |
| Ownership model | [H/M/L] | |
| Consistency and transaction strategy | [H/M/L] | |
| Integrity constraints | [H/M/L] | |
| Migration strategy | [H/M/L] | |

**Overall data framework confidence:** [H/M/L]
**Lowest-confidence area:** [name and explain]

---

## 17. Revision Protocol

| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline data framework | |

---

## 18. Handoff Status

- [ ] Classification scheme is complete with handling rules per tier
- [ ] Every data domain has exactly one owning module
- [ ] Every data domain has a named consistency model
- [ ] Classification tiers drive encryption requirements for Step 03
- [ ] Integrity constraints specified as citable patterns
- [ ] Migration strategy elaborates Step 02 versioning patterns
- [ ] Data lifecycle coordinates with compliance constraints
- [ ] Every constraint has a unique ID
- [ ] Per-module data guidance provided for Step 08
- [ ] Data needs requiring amendment surfaced for Step 16
- [ ] Constraint index complete
- [ ] No module data models, formal contracts, or implementation present

**Status:** [Ready for Step 08 / Gaps require resolution first / Blocked]
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] The data classification scheme (§4) enumerates tiers with handling
      rules (encryption, access, retention, residency) per tier
- [ ] Each classification tier has an ID (DA-NN) and the security
      framework can consume it for encryption-at-rest decisions
- [ ] Every data domain has exactly one owning module (§5) — no domain
      is unowned and no domain has two owners
- [ ] The data-ownership rule (modules own data; cross-module access is
      through interfaces, not shared tables) is stated as a constraint
- [ ] The storage architecture (§6) elaborates the Phase 3 storage model
      commitment without re-committing it
- [ ] Component-level data flows (§7) are at component level, not module
      level (Step 07 refines to modules)
- [ ] Every data domain has a named consistency model (§8.1) — no
      implicit consistency assumptions
- [ ] Transaction boundaries are specified, including cross-module
      transaction strategy (§8.3)
- [ ] Integrity constraints (§9) are specified as citable patterns module
      data models apply, not as a single module's schema
- [ ] The migration strategy (§10) elaborates the Step 02 versioning
      patterns with the SP-NN citation
- [ ] The data lifecycle (§11) coordinates with compliance retention and
      deletion requirements
- [ ] §12 coordinates the classification scheme with Step 03 encryption
      controls explicitly
- [ ] Per-module data guidance (§13) gives Step 08 the constraints each
      module data model must apply
- [ ] Every constraint has a unique ID (DA-NN) and the constraint index
      (§14) lists them all
- [ ] Data needs requiring Phase 3/Phase 2 amendment are surfaced for
      Step 16, not silently re-committed
- [ ] No module data models, formal API contracts, DDL, migration
      scripts, or implementation content present
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 04 of 16 in the Phase 4 Architecture & Modular Design Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `architecture-modular-design.instructions.md`*
*Previous step: `step-03-security-architecture-framework.prompt.md`*
*Parallel-eligible siblings: `step-03-security-architecture-framework.prompt.md`, `step-05-documentation-strategy.prompt.md`, `step-06-governance-model.prompt.md`*
*Next sequential step: `step-07-module-enumeration.prompt.md` (after all of Stage 1 completes)*
