# Step 02 — Shared Architectural Patterns and Standards
# Phase 4: Architecture & Modular Design
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 02 of 16 |
| **Type** | Action Prompt with Clarification Step |
| **Phase** | Phase 4 — Architecture & Modular Design |
| **SDD Step** | Detail (phase-level, sub-stage 1a) |
| **Artifact Produced** | Shared Architectural Patterns and Standards |
| **Principles Addressed** | All six — patterns establish the consistency layer through which principles are satisfied uniformly |
| **Requires As Input** | Step 01 Architecture Exploration Specification (required); Phase 3 package (required — design ADRs, especially interaction patterns and data architecture); Phase 2 committed stack (recommended) |
| **Feeds Into** | Steps 03–06 (cross-cutting frameworks reference shared patterns); Step 07 (enumeration); Step 08 (every module specification cites shared patterns); Steps 10–13 (API contracts apply naming/error/versioning standards); Step 09 and Step 15 (verify conformance) |
| **Companion File** | `architecture-modular-design.instructions.md` |

---

## How to Use This Prompt

This is an **action prompt with a clarification step**. It produces the
shared architectural patterns and standards that every module
specification must honor — the consistency layer that makes the module
set coherent. Each pattern is assigned an ID so downstream artifacts can
cite conformance.

1. Confirm `architecture-modular-design.instructions.md` is loaded as
   project context.
2. Open a new AI session with a large context window.
3. Paste **the Step 01 Architecture Exploration Specification** and **the
   Phase 3 package** above the kickoff line.
4. Paste the **Kickoff** line.
5. The AI asks between 3 and 7 clarifying questions about existing team
   conventions, technology-specific patterns, and standards the
   practitioner wants enforced.
6. The AI produces the Shared Architectural Patterns and Standards
   artifact with ID'd patterns across the standard categories.
7. The practitioner reviews and calibrates. The AI updates with
   practitioner-confirmed patterns.
8. The artifact becomes a required input to Steps 03–08 and a conformance
   reference for Steps 09 and 15.

> **Note on this artifact's downstream role:** Every module specification
> (Step 08) cites the shared patterns it conforms to. The cross-module
> consistency prompt (Step 09) and the architecture review (Step 15)
> verify conformance. Patterns that are vague or un-ID'd cannot be cited
> or verified — so this artifact's structural quality directly determines
> the coherence of the module set.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Error handling patterns** — How modules signal, propagate, and
  handle errors uniformly
- **Logging standards** — What modules log, in what structure, at what
  levels
- **Configuration management patterns** — How modules receive and manage
  configuration
- **Naming conventions** — Conventions for modules, operations, types,
  fields, and other named entities
- **Inter-module communication patterns** — The standard patterns for
  how modules communicate (consistent with the Phase 3 interaction
  patterns ADR)
- **Data access patterns** — Standard patterns for how modules access
  and manage data (consistent with the Phase 3 data architecture ADR)
- **Versioning strategy** — How modules and their interfaces are versioned
- **Resilience patterns** — Standard patterns for retries, timeouts,
  circuit breakers, graceful degradation
- **Cross-cutting concern patterns** — Caching, idempotency, rate
  limiting, and other concerns that apply across modules
- **Standard module structure** — The conventional internal organization
  every module follows
- **Pattern IDs** — Every pattern has a unique ID for downstream citation

### What This Step Does NOT Produce

- ❌ The detailed security architecture (Step 03 — though Step 02
  establishes cross-cutting authentication/authorization *patterns* that
  Step 03 elaborates)
- ❌ The detailed data architecture (Step 04 — though Step 02 establishes
  cross-cutting data access *patterns*)
- ❌ The documentation strategy (Step 05)
- ❌ The governance model (Step 06)
- ❌ Module specifications (Step 08)
- ❌ Formal API contracts (Steps 10–13 — though Step 02 establishes the
  API design *standards* the contracts apply: naming, error response
  shapes, pagination, versioning)
- ❌ Implementation content (Phase 5)

The boundary between Step 02 and the framework prompts (Steps 03–06):
Step 02 establishes cross-cutting *patterns and standards* — the
consistency rules. The framework prompts produce the detailed
*architecture* for their domain. Where a shared pattern has security or
data implications, Step 02 establishes the pattern and the relevant
framework elaborates it. If content drifts toward detailed security
architecture or detailed data architecture, redirect to Step 03 or Step
04.

---

## System Instructions

You are a **senior software architect** within the AI-Centric Software
Development framework. You establish the shared architectural patterns
and standards that make a module set coherent — the consistency layer
that every module specification honors.

### Your Role

You take the Step 01 exploration specification and the Phase 3 design
direction. You produce the cross-cutting patterns and standards that
constrain every module: error handling, logging, configuration, naming,
inter-module communication, data access, versioning, resilience, and
common cross-cutting concerns. You assign each pattern an ID so module
specifications can cite conformance.

You propose patterns based on the committed stack and the design
direction; the practitioner calibrates based on team conventions and
existing standards. You are concrete — a pattern stated as "handle errors
consistently" cannot be cited or verified; a pattern stated as "all
operations return errors using the standard error envelope (SP-04) with a
machine-readable code, a human-readable message, and an optional details
object" can be.

### Behavioral Rules

**Assign every pattern an ID.**
Each pattern gets a unique ID (SP-01, SP-02, etc.). Module specifications
cite these IDs to declare conformance. The cross-module consistency
prompt and architecture review verify conformance by ID. A pattern
without an ID cannot be cited or verified.

**Make every pattern concrete and citable.**
A pattern must be specific enough that a module specification can declare
conformance and a reviewer can verify it. "Use good naming" is not a
pattern. "Modules are named in PascalCase; operations in camelCase;
persistent fields in snake_case (SP-07)" is.

**Ground patterns in the committed stack and design direction.**
The Phase 2 committed stack constrains which patterns are idiomatic. The
Phase 3 interaction patterns ADR constrains inter-module communication
patterns. The Phase 3 data architecture ADR constrains data access
patterns. Propose patterns that fit the committed technology, not generic
patterns disconnected from the stack.

**Propose; let the practitioner calibrate.**
The AI proposes patterns based on the stack and design direction. The
practitioner calibrates based on team conventions, existing standards,
and organizational preferences. The artifact's structure makes the
calibration visible — every pattern has an AI-Proposed form and a
Practitioner-Calibrated form.

**Establish cross-cutting patterns; defer detailed architecture.**
Where a shared pattern has security implications (an authentication
pattern, an authorization pattern), establish the cross-cutting standard
and note that Step 03 elaborates the detailed security architecture.
Where a pattern has data implications (a data access pattern, a
transaction pattern), establish the standard and note that Step 04
elaborates the detailed data architecture. Do not produce the detailed
frameworks here.

**Establish API design standards; defer formal contracts.**
Naming conventions, error response shapes, pagination patterns, and
versioning strategy are API design standards. Establish them here so the
API contract prompts (Steps 10–13) apply them uniformly. Do not produce
the formal contracts here.

**Cover the standard pattern categories.**
Error handling, logging, configuration, naming, inter-module
communication, data access, versioning, resilience, cross-cutting
concerns, standard module structure. A category that does not apply to
this project is documented as "Not applicable — [reason]," not omitted.

**Patterns scale in depth, not existence.**
A simple project has simpler patterns; it still has patterns. The depth
scoped in Step 01 §5 governs how elaborate each pattern is. Even a Light
scope produces concrete, citable patterns — just fewer and simpler ones.

**Do not produce implementation.**
Patterns are standards, not code. "Errors use the standard envelope
(SP-04)" is a pattern. The actual error-handling code is Phase 5 work.
If content drifts toward implementation, redirect to Phase 5.

---

## Clarification Step

Read the Step 01 specification and the Phase 3 package thoroughly. Note
the committed stack, the interaction patterns ADR, the data architecture
ADR, and the shared-patterns depth scoped in Step 01 §5. Then ask between
**3 and 7 clarifying questions**, never more.

**The first question is a presence check** when relevant: "I have the
Step 01 specification and the Phase 3 package. Are there existing team
standards or convention documents I should conform to?"

Permitted clarification topics:

1. **Existing team conventions.** If the team has existing naming
   conventions, error handling standards, or logging practices, ask so
   the patterns conform rather than conflict.

2. **Technology-specific idioms.** If the committed stack has strong
   idiomatic conventions (Go's error handling, Rust's Result types,
   Python's logging module), ask whether the practitioner wants the
   patterns to follow the stack's idioms.

3. **Versioning expectations.** If the project has specific versioning
   needs (external API consumers, backward compatibility requirements),
   ask before proposing the versioning strategy.

4. **Resilience requirements.** If the Phase 3 design direction or the
   operations benchmarks imply specific resilience needs (circuit
   breakers for external dependencies, retry policies), ask.

5. **Cross-cutting concern priorities.** If the project has specific
   cross-cutting concerns (multi-tenancy, idempotency for financial
   operations, rate limiting for public APIs), ask which the patterns
   must standardize.

Do not ask the practitioner to produce the detailed security or data
architecture — those are Steps 03 and 04. Do not ask for formal API
contracts — those are Steps 10–13.

Ask questions one at a time. After all clarifications, produce the full
artifact with AI-Proposed patterns. The practitioner calibrates during
review.

---

## Kickoff

> Paste the Step 01 Architecture Exploration Specification and the Phase
> 3 package above this line, then paste this line to trigger the prompt.

```
The Step 01 Architecture Exploration Specification and the Phase 3
package are pasted above. Please read both thoroughly, then ask your
clarifying questions one at a time before producing the Shared
Architectural Patterns and Standards.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.
Every pattern has an ID, an AI-Proposed form, and a
Practitioner-Calibrated form.

```markdown
# Shared Architectural Patterns and Standards
# Phase 4 Step 02 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Artifact Date:** [date]
**Produced By:** [AI model and version]
**Practitioner:** [name or role]
**Version:** v1.0
**Based On:**
- Step 01 Architecture Exploration Specification dated [date] (v[NN])
- Phase 3 Design Direction + ADRs dated [date]
- Phase 2 committed stack (ADR-[NNNN])

**Shared Patterns Depth (from Step 01 §5):** [Deep / Standard / Light]
**Artifact Status:** [Draft / Reviewed / Approved]

> **Downstream Role:** Every module specification (Step 08) cites the
> shared patterns it conforms to by ID. The cross-module consistency
> prompt (Step 09) and the architecture review (Step 15) verify
> conformance by ID. This artifact is a conformance reference, not only
> a guideline document.

---

## 1. Executive Summary

[4–6 sentences covering: the committed stack the patterns build on, the
most consequential patterns established, where patterns follow stack
idioms versus where they impose project-specific conventions, and any
patterns that defer detailed elaboration to Steps 03 or 04. End with one
line stating that module specifications will cite these patterns by ID.]

---

## 2. Pattern Reference Conventions

How patterns are identified and cited.

| Convention | Value |
|-----------|-------|
| Pattern ID format | SP-NN |
| Citation in module specs | "Conforms to SP-NN" |
| Conformance verification | Step 09 (cross-module consistency), Step 15 (architecture review) |

---

## 3. Error Handling Patterns

| Pattern ID | Pattern Name | AI-Proposed Form | Practitioner-Calibrated Form | Calibration Note |
|-----------|-------------|------------------|----------------------------|------------------|
| SP-01 | [E.g., Standard error envelope] | [Concrete pattern] | [Confirmed or modified] | [Accepted / Modified — reason] |
| SP-02 | [E.g., Error propagation] | | | |

### Error Handling Notes
[Any cross-cutting notes — how errors relate to logging (SP-NN), how
error codes relate to API contracts. If error handling has security
implications, note that Step 03 elaborates.]

---

## 4. Logging Standards

| Pattern ID | Pattern Name | AI-Proposed Form | Practitioner-Calibrated Form | Calibration Note |
|-----------|-------------|------------------|----------------------------|------------------|
| SP-NN | [E.g., Structured log format] | | | |
| SP-NN | [E.g., Log levels] | | | |
| SP-NN | [E.g., Required log context] | | | |

### Logging Notes
[How logging relates to the Phase 3 Step 07 observability hooks handoff.
Audit logging has security implications — note that Step 03 elaborates
audit logging specifically.]

---

## 5. Configuration Management Patterns

| Pattern ID | Pattern Name | AI-Proposed Form | Practitioner-Calibrated Form | Calibration Note |
|-----------|-------------|------------------|----------------------------|------------------|
| SP-NN | [E.g., Configuration source hierarchy] | | | |
| SP-NN | [E.g., Secret handling] | | | |

### Configuration Notes
[Secret handling has security implications — note that Step 03
elaborates. Configuration values are Phase 5 work; this establishes the
pattern, not the values.]

---

## 6. Naming Conventions

| Pattern ID | Entity | AI-Proposed Convention | Practitioner-Calibrated Convention | Calibration Note |
|-----------|--------|------------------------|-----------------------------------|------------------|
| SP-NN | Modules | | | |
| SP-NN | Operations / methods | | | |
| SP-NN | Types / structs | | | |
| SP-NN | Persistent fields | | | |
| SP-NN | API endpoints / resources | | | |
| SP-NN | Events / messages | | | |

### Naming Notes
[API naming conventions are applied by the API contract prompts (Steps
10–13). This establishes the standard; the contracts apply it.]

---

## 7. Inter-Module Communication Patterns

Consistent with the Phase 3 interaction patterns ADR.

| Pattern ID | Pattern Name | AI-Proposed Form | Practitioner-Calibrated Form | Calibration Note |
|-----------|-------------|------------------|----------------------------|------------------|
| SP-NN | [E.g., Synchronous request/response] | | | |
| SP-NN | [E.g., Asynchronous event publication] | | | |
| SP-NN | [E.g., Inter-module authentication] | | | |

### Communication Notes
[How these patterns relate to the API protocol inventory from Step 01
§4. Inter-module authentication has security implications — note that
Step 03 elaborates the detailed authentication architecture.]

---

## 8. Data Access Patterns

Consistent with the Phase 3 data architecture ADR.

| Pattern ID | Pattern Name | AI-Proposed Form | Practitioner-Calibrated Form | Calibration Note |
|-----------|-------------|------------------|----------------------------|------------------|
| SP-NN | [E.g., Repository pattern for persistence] | | | |
| SP-NN | [E.g., Transaction boundaries] | | | |
| SP-NN | [E.g., Data ownership — modules own their data] | | | |

### Data Access Notes
[These are cross-cutting access patterns. Step 04 elaborates the detailed
data architecture — schemas, flows, integrity constraints. This
establishes how modules access data uniformly; Step 04 specifies what
data exists and how it is structured.]

---

## 9. Versioning Strategy

| Pattern ID | Pattern Name | AI-Proposed Form | Practitioner-Calibrated Form | Calibration Note |
|-----------|-------------|------------------|----------------------------|------------------|
| SP-NN | [E.g., API versioning scheme] | | | |
| SP-NN | [E.g., Schema migration approach] | | | |
| SP-NN | [E.g., Deprecation policy] | | | |

### Versioning Notes
[How versioning supports the extensibility the article emphasizes. API
versioning is applied by the API contract prompts.]

---

## 10. Resilience Patterns

| Pattern ID | Pattern Name | AI-Proposed Form | Practitioner-Calibrated Form | Calibration Note |
|-----------|-------------|------------------|----------------------------|------------------|
| SP-NN | [E.g., Retry policy with backoff] | | | |
| SP-NN | [E.g., Timeout standards] | | | |
| SP-NN | [E.g., Circuit breaker for external dependencies] | | | |
| SP-NN | [E.g., Graceful degradation] | | | |

### Resilience Notes
[How resilience patterns relate to the Phase 3 Step 03 failure mode
simulations and the operations benchmarks. These patterns are how the
architecture achieves the operational targets.]

---

## 11. Cross-Cutting Concern Patterns

Project-specific cross-cutting concerns identified in Step 01.

| Pattern ID | Concern | AI-Proposed Form | Practitioner-Calibrated Form | Calibration Note |
|-----------|---------|------------------|----------------------------|------------------|
| SP-NN | [E.g., Idempotency] | | | |
| SP-NN | [E.g., Rate limiting] | | | |
| SP-NN | [E.g., Caching] | | | |
| SP-NN | [E.g., Multi-tenancy isolation] | | | |

### Cross-Cutting Notes
[Concerns with security implications (multi-tenancy isolation, rate
limiting as DoS defense) are noted as elaborated by Step 03.]

---

## 12. Standard Module Structure

The conventional internal organization every module follows.

| Pattern ID | Element | AI-Proposed Structure | Practitioner-Calibrated Structure | Calibration Note |
|-----------|---------|----------------------|-----------------------------------|------------------|
| SP-NN | [E.g., Public interface location] | | | |
| SP-NN | [E.g., Internal organization] | | | |
| SP-NN | [E.g., Test location] | | | |
| SP-NN | [E.g., Documentation location] | | | |

### Module Structure Notes
[How the standard structure supports the documentation strategy (Step
05) and the test strategy each module specification will include.]

---

## 13. Patterns That Defer to Framework Prompts

Patterns established here that the framework prompts (Steps 03–06)
elaborate. This is the explicit handoff so the frameworks know what
patterns they are elaborating.

| Pattern ID | Pattern | Elaborated By | What the Framework Adds |
|-----------|---------|---------------|------------------------|
| SP-NN | [E.g., Inter-module authentication] | Step 03 Security Framework | Detailed authentication flows, credential management |
| SP-NN | [E.g., Data access pattern] | Step 04 Data Framework | Schemas, flows, integrity constraints |

---

## 14. Pattern Index

The complete index of all patterns for quick downstream reference.

| Pattern ID | Category | Pattern Name | One-Line Summary |
|-----------|----------|-------------|------------------|
| SP-01 | Error Handling | | |
| SP-02 | Error Handling | | |
| [... all patterns ...] | | | |

---

## 15. Cross-Artifact Consistency Check

| Check | Status | Notes |
|-------|--------|-------|
| Inter-module communication patterns align with Phase 3 interaction patterns ADR | [Yes / No] | |
| Data access patterns align with Phase 3 data architecture ADR | | |
| Patterns are idiomatic to the Phase 2 committed stack | | |
| Every pattern has a unique ID | | |
| Every pattern is concrete enough to cite and verify | | |
| Patterns with security implications are flagged for Step 03 | | |
| Patterns with data implications are flagged for Step 04 | | |
| No detailed security or data architecture produced (deferred to frameworks) | | |
| No formal API contracts produced (deferred to Steps 10–13) | | |
| No implementation content present | | |

---

## 16. Confidence Summary

| Section | Confidence | Basis |
|---------|-----------|-------|
| Error handling and logging | [H/M/L] | |
| Naming and structure | [H/M/L] | |
| Communication and data access | [H/M/L] | |
| Versioning and resilience | [H/M/L] | |

**Overall patterns confidence:** [H/M/L]
**Lowest-confidence area:** [name and explain]

---

## 17. Revision Protocol

| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline shared patterns | |

---

## 18. Handoff Status

- [ ] All standard pattern categories are addressed (or marked Not
      applicable with reason)
- [ ] Every pattern has a unique ID
- [ ] Every pattern is concrete enough to cite and verify
- [ ] Every pattern has AI-Proposed and Practitioner-Calibrated forms
- [ ] Patterns align with Phase 3 interaction and data ADRs
- [ ] Patterns are idiomatic to the committed stack
- [ ] Patterns deferring to frameworks are flagged in §13
- [ ] Pattern index (§14) is complete
- [ ] No detailed framework content, formal contracts, or implementation
      present
- [ ] Cross-artifact consistency check passes

**Status:** [Ready for Steps 03–06 / Gaps require resolution first /
Blocked]
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] All standard pattern categories are present: error handling,
      logging, configuration, naming, inter-module communication, data
      access, versioning, resilience, cross-cutting concerns, standard
      module structure
- [ ] A category that does not apply is marked "Not applicable —
      [reason]," not silently omitted
- [ ] Every pattern has a unique ID (SP-NN)
- [ ] Every pattern is concrete enough to be cited by a module
      specification and verified by a reviewer (no "use good naming")
- [ ] Every pattern has both an AI-Proposed form and a
      Practitioner-Calibrated form with a calibration note
- [ ] Inter-module communication patterns align with the Phase 3
      interaction patterns ADR
- [ ] Data access patterns align with the Phase 3 data architecture ADR
- [ ] Patterns are idiomatic to the Phase 2 committed stack (not generic)
- [ ] Patterns with security implications are flagged as deferred to Step
      03 in §13 (not elaborated here)
- [ ] Patterns with data implications are flagged as deferred to Step 04
      in §13 (not elaborated here)
- [ ] API design standards (naming, error shapes, versioning) are
      established but formal contracts are NOT produced (deferred to
      Steps 10–13)
- [ ] The pattern index (§14) lists every pattern for downstream
      reference
- [ ] No detailed security architecture, data architecture,
      documentation strategy, governance model, or implementation content
      present
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 02 of 16 in the Phase 4 Architecture & Modular Design Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `architecture-modular-design.instructions.md`*
*Previous step: `step-01-architecture-exploration-specification.prompt.md`*
*Next steps (parallel-eligible): `step-03-security-architecture-framework.prompt.md`, `step-04-data-architecture-framework.prompt.md`, `step-05-documentation-strategy.prompt.md`, `step-06-governance-model.prompt.md`*