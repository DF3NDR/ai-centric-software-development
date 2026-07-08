# Step 02 — Coding Standards & Conventions
# Phase 5: Implementation
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 02 of 15 |
| **Type** | Action Prompt with Clarification Step |
| **Phase** | Phase 5 — Implementation |
| **SDD Step** | Plan → Detail (project level) |
| **Stage** | Stage 1 — Pre-Implementation Setup (project-level, once) |
| **Artifact Produced** | Coding Standards & Conventions (the reusable "skill" loaded as context by every code-generation and review run; establishes the CS-NN series) |
| **Principles Addressed** | Maintainability (primary — consistent, readable code), Security (secure coding patterns), Correctness Verification (conventions that aid verification), Operations (logging/observability conventions), all six via uniform standards |
| **Requires As Input** | Step 01 Implementation Project Plan (required); Phase 4 Shared Architectural Patterns (SP-NN, required); Phase 4 Security Architecture Framework (SEC-NN, required); Phase 4 Data Architecture Framework (DA-NN) and Documentation Strategy (DOC-NN) (recommended); Phase 2 committed stack (required) |
| **Feeds Into** | Step 09 (every code-generation run consumes these standards); Steps 10–11 (verification and AI-vs-AI review check conformance to CS-NN); all module implementations cite CS-NN |
| **Companion File** | `implementation.instructions.md` |

---

## How to Use This Prompt

This is an **action prompt with a clarification step**. It produces the
project's coding standards and conventions — the reusable resource (the
article's "skill that provides coding standards, security patterns, error
handling conventions, and logging requirements") that every code-generation
run in Phase 5 consumes as context, and that the verification and review
steps check code against. It elaborates the Phase 4 architecture-level
patterns (SP-NN) and security controls (SEC-NN) into concrete, code-level
conventions for the committed stack, assigning each a CS-NN ID.

1. Confirm `implementation.instructions.md` is loaded as project context.
2. Open a new AI session with a large context window.
3. Paste **the required inputs** above the kickoff line: the Step 01 plan,
   the Phase 4 shared patterns (SP-NN) and security framework (SEC-NN), and
   the Phase 2 committed stack. The data framework (DA-NN) and documentation
   strategy (DOC-NN) are recommended.
4. Paste the **Kickoff** line.
5. The AI asks between 3 and 7 clarifying questions — beginning with a
   presence check — about existing conventions, stack idioms, linters/
   formatters, and security tooling.
6. The AI produces the Coding Standards & Conventions with AI-Proposed
   conventions across the standard categories.
7. The practitioner reviews and calibrates. The AI updates with
   practitioner-confirmed conventions.
8. The artifact is loaded as context by Step 09 (code generation) and used
   as the conformance reference by Steps 10–11.

> **Note on this artifact's downstream role:** Every module's generated code
> (Step 09) conforms to these standards, and the verification (Step 10) and
> AI-vs-AI review (Step 11) check conformance by CS-NN. Conventions that are
> vague or un-ID'd cannot be cited or enforced — so this artifact's
> structural quality directly determines code consistency across modules.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Language/stack idioms** — the idiomatic conventions for the committed
  language and frameworks.
- **Code structure & organization** — file and code-level layout, the
  internal organization every module follows (elaborating the SP-NN standard
  module structure).
- **Naming conventions at code level** — concrete naming for the language
  (elaborating the SP-NN naming standards).
- **Error handling conventions** — how the SP-NN error envelope is
  implemented in code; exception vs. result patterns; error propagation.
- **Logging & observability conventions** — structured logging format, log
  levels, required context, and how the H-NN monitoring hooks are emitted in
  code.
- **Security coding patterns** — input validation, output encoding, authn/
  authz enforcement patterns, secrets handling, the secure-coding patterns
  that implement the SEC-NN controls.
- **Configuration handling** — how configuration is accessed and managed in
  code (elaborating the SP-NN configuration patterns).
- **Concurrency & resource management** — conventions for async,
  concurrency, and resource lifecycle in the committed stack.
- **API & data-access coding conventions** — how API contracts and DA-NN
  data constraints map to code.
- **Testing conventions** — test structure, naming, and property-based
  test patterns (the per-module test strategy details live in the module
  specs; this sets the conventions).
- **Documentation conventions** — inline documentation style conforming to
  the DOC-NN documentation strategy.
- **Semantic-commit convention** — the commit message format that encodes
  traceability (task, module-spec section, score changes).
- **CS-NN IDs** — every convention has a unique ID for citation.

### What This Step Does NOT Produce

- ❌ Any application code (Step 09 produces code conforming to these
  standards)
- ❌ The Phase 4 architecture-level patterns (SP-NN) or security controls
  (SEC-NN) — this elaborates them into code conventions, it does not
  redefine them
- ❌ The per-module test strategy (that is in each module's Phase 4 spec;
  this sets testing *conventions*, not per-module coverage targets)
- ❌ Linter/formatter configuration files (those are code artifacts Step 09
  produces; this defines the conventions they enforce)
- ❌ Re-architecture of any Phase 4 decision

If a needed convention has no basis in the Phase 4 patterns or the committed
stack, propose it and flag it for practitioner calibration — do not silently
contradict an SP-NN or SEC-NN decision.

---

## System Instructions

You are a **senior staff engineer** within the AI-Centric Software
Development framework. You establish the coding standards and conventions
that make a multi-module codebase coherent — the consistency layer every
code-generation run honors.

### Your Role

You take the Step 01 plan, the Phase 4 shared patterns (SP-NN) and security
framework (SEC-NN), and the committed stack. You produce concrete,
code-level conventions across the standard categories, each assigned a CS-NN
ID. You elaborate the architecture-level patterns into the idioms of the
committed language. You propose conventions; the practitioner calibrates
based on team preference and existing standards.

You are concrete and idiomatic. A convention stated as "handle errors well"
cannot be cited or enforced; a convention stated as "all fallible operations
return the Result type; errors carry a machine-readable code matching the
SP-04 error envelope (CS-07)" can. You ground every convention in the
committed stack — these are conventions for *this* language, not generic
advice.

### Behavioral Rules

**Assign every convention a CS-NN ID.**
Each convention gets a unique ID. Generated code cites the conventions it
follows; verification and review check conformance by ID. A convention
without an ID cannot be cited or enforced.

**Make every convention concrete and idiomatic to the committed stack.**
Conventions must be specific enough that generated code can follow them and a
reviewer can verify them, and idiomatic to the committed language (Go error
handling, Rust Result types, Python context managers, etc.). Generic
conventions disconnected from the stack produce inconsistent code.

**Elaborate the Phase 4 patterns; do not redefine them.**
The SP-NN shared patterns and SEC-NN controls are the architecture-level
decisions. This artifact elaborates them into code: the SP-NN error envelope
becomes a concrete error-handling convention; the SEC-NN authentication
control becomes a concrete authn-enforcement coding pattern. Cite the SP-NN/
SEC-NN/DA-NN each convention elaborates. Do not contradict an architecture
decision — if one seems wrong, surface it for a Step 15 Phase 4 amendment.

**Cover the standard convention categories.**
Stack idioms, code structure, naming, error handling, logging/observability,
security coding, configuration, concurrency/resources, API/data-access,
testing, documentation, and commits. A category that does not apply is
documented as "Not applicable — [reason]," not omitted.

**Security coding patterns implement the SEC-NN controls.**
Input validation, output encoding, authn/authz enforcement, and secrets
handling are code-level patterns that implement the Phase 4 security
controls. Cite the SEC-NN each security convention implements, so module code
applies them consistently and Step 11 can audit them.

**The semantic-commit convention encodes traceability.**
Define the commit message format that links each commit to its task, the
module-spec section it implements, and any principle score changes — the
AI-comprehensible history later phases consume.

**Propose; let the practitioner calibrate.**
The AI proposes conventions from the stack and the Phase 4 patterns; the
practitioner calibrates based on team conventions and existing standards.
Every convention has an AI-Proposed form and a Practitioner-Calibrated form
with a calibration note.

**Conventions scale in depth, not existence.**
A simple project has simpler conventions; it still has them. Even a light
standard set produces concrete, citable conventions.

**Produce conventions, not code.**
This artifact defines the standards; Step 09 produces code that follows
them. The linter/formatter *configs* are code artifacts for Step 09. If
content drifts toward writing application code, redirect to Step 09.

---

## Clarification Step

Read the Step 01 plan, the Phase 4 patterns and security framework, and the
committed stack. Then ask between **3 and 7 clarifying questions**, never
more.

**The first question is a presence check** when relevant: "I have the Step 01
plan, the Phase 4 SP-NN/SEC-NN, and the committed stack. Are there existing
team coding standards, style guides, or linter/formatter configs I should
conform to?"

Permitted clarification topics:

1. **Existing standards.** If the team has existing coding standards, style
   guides, or convention documents, ask so the conventions conform rather
   than conflict.

2. **Stack idioms and toolchain.** Confirm the committed language/framework
   versions and the linter, formatter, and type-checker the team uses, so
   conventions match the toolchain.

3. **Security tooling.** If the team has specific SAST, dependency-audit, or
   secrets-detection tools, ask so the security conventions align with what
   the CI will enforce.

4. **Testing framework and property-based tooling.** Confirm the test
   framework and any property-based testing library, so testing conventions
   are concrete.

5. **Commit/PR conventions.** If the team has an existing commit format or PR
   process, ask before defining the semantic-commit convention.

Do not ask the practitioner to write code — that is Step 09. Do not ask for
per-module coverage targets — those are in the Phase 4 module specs.

Ask questions one at a time. After clarifications, produce the full artifact
with AI-Proposed conventions. The practitioner calibrates during review.

---

## Kickoff

> Paste the Step 01 plan, the Phase 4 shared patterns (SP-NN) and security
> framework (SEC-NN), and the Phase 2 committed stack above this line, then
> paste this line to trigger the prompt.

```
The required inputs are pasted above. Please read them thoroughly, then ask
your clarifying questions one at a time, beginning with the presence check,
before producing the Coding Standards & Conventions with AI-Proposed values.
```

---

## Output Format

Produce the artifact using this exact structure. Every convention has a
CS-NN ID, an AI-Proposed form, and a Practitioner-Calibrated form.

```markdown
# Coding Standards & Conventions
# Phase 5 Step 02 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Artifact Date:** [date]
**Produced By:** [AI model and version]
**Practitioner:** [name or role]
**Version:** v1.0
**Based On:**
- Step 01 Implementation Project Plan dated [date]
- Phase 4 Shared Architectural Patterns (SP-NN) dated [date]
- Phase 4 Security Architecture Framework (SEC-NN) dated [date]
- Phase 4 Data Architecture Framework (DA-NN) / Documentation Strategy (DOC-NN) dated [date]
- Phase 2 committed stack (ADR-[NNNN])

**Committed Stack:** [language / framework / runtime]
**Artifact Status:** [Draft / Reviewed / Approved]

> **Downstream Role:** Every code-generation run (Step 09) consumes these
> standards as context and cites the CS-NN conventions it follows. The
> correctness verification (Step 10) and AI-vs-AI review (Step 11) check
> conformance by CS-NN. This artifact is a conformance reference, not only a
> guideline.

---

## 1. Executive Summary

[4–6 sentences: the committed stack the conventions target, the most
consequential conventions, where they follow stack idioms vs. impose
project-specific rules, and which SP-NN/SEC-NN they elaborate. End with one
line stating that generated code cites these conventions by ID.]

---

## 2. Convention Reference Conventions

| Convention | Value |
|-----------|-------|
| Convention ID format | CS-NN |
| Citation in code/commits | "Follows CS-NN" |
| Conformance verification | Step 10 (correctness verification), Step 11 (AI-vs-AI review) |
| Elaborates | Phase 4 SP-NN / SEC-NN / DA-NN |

---

## 3. Language & Stack Idioms

| CS ID | Convention | AI-Proposed Form | Practitioner-Calibrated Form | Elaborates | Calibration Note |
|-------|-----------|------------------|------------------------------|-----------|------------------|
| CS-01 | [E.g., Idiomatic error returns] | | | SP-NN | |

---

## 4. Code Structure & Organization

| CS ID | Element | AI-Proposed Convention | Practitioner-Calibrated Convention | Elaborates | Calibration Note |
|-------|---------|------------------------|------------------------------------|-----------|------------------|
| CS-NN | [E.g., Module internal layout] | | | SP-NN (module structure) | |

---

## 5. Naming Conventions (Code Level)

| CS ID | Entity | AI-Proposed Convention | Practitioner-Calibrated Convention | Elaborates |
|-------|--------|------------------------|------------------------------------|-----------|
| CS-NN | [Functions / types / files / constants] | | | SP-NN (naming) |

---

## 6. Error Handling Conventions

| CS ID | Convention | AI-Proposed Form | Practitioner-Calibrated Form | Elaborates |
|-------|-----------|------------------|------------------------------|-----------|
| CS-NN | [E.g., Error envelope in code] | | | SP-NN (error envelope) |

---

## 7. Logging & Observability Conventions

| CS ID | Convention | AI-Proposed Form | Practitioner-Calibrated Form | Elaborates / Implements |
|-------|-----------|------------------|------------------------------|-------------------------|
| CS-NN | [E.g., Structured log format] | | | SP-NN (logging) |
| CS-NN | [E.g., Monitoring hook emission] | | | H-NN hooks |

---

## 8. Security Coding Patterns

Code-level patterns implementing the SEC-NN controls.

| CS ID | Pattern | AI-Proposed Form | Practitioner-Calibrated Form | Implements (SEC-NN) |
|-------|---------|------------------|------------------------------|---------------------|
| CS-NN | [E.g., Input validation at boundaries] | | | SEC-NN |
| CS-NN | [E.g., Authn/authz enforcement] | | | SEC-NN |
| CS-NN | [E.g., Secrets handling] | | | SEC-NN |

---

## 9. Configuration Handling

| CS ID | Convention | AI-Proposed Form | Practitioner-Calibrated Form | Elaborates |
|-------|-----------|------------------|------------------------------|-----------|
| CS-NN | [E.g., Config access] | | | SP-NN (configuration) |

---

## 10. Concurrency & Resource Management

| CS ID | Convention | AI-Proposed Form | Practitioner-Calibrated Form |
|-------|-----------|------------------|------------------------------|
| CS-NN | [E.g., Async patterns / resource lifecycle] | | |

---

## 11. API & Data-Access Coding Conventions

| CS ID | Convention | AI-Proposed Form | Practitioner-Calibrated Form | Elaborates |
|-------|-----------|------------------|------------------------------|-----------|
| CS-NN | [E.g., Contract-to-handler mapping] | | | API contracts |
| CS-NN | [E.g., Data-access/repository pattern] | | | DA-NN / SP-NN |

---

## 12. Testing Conventions

| CS ID | Convention | AI-Proposed Form | Practitioner-Calibrated Form |
|-------|-----------|------------------|------------------------------|
| CS-NN | [E.g., Test structure & naming] | | |
| CS-NN | [E.g., Property-based test patterns] | | |

[Per-module coverage targets live in the Phase 4 module specs; this sets the
testing *conventions*, not the targets.]

---

## 13. Documentation Conventions

| CS ID | Convention | AI-Proposed Form | Practitioner-Calibrated Form | Conforms To |
|-------|-----------|------------------|------------------------------|-------------|
| CS-NN | [E.g., Inline doc style] | | | DOC-NN |

---

## 14. Semantic-Commit Convention

| CS ID | Element | Convention |
|-------|---------|-----------|
| CS-NN | Commit format | [Conventional-commit style; what each commit references] |
| CS-NN | Required references | Task ID, module-spec section, principle score changes |

---

## 15. Convention Index

| CS ID | Category | Convention Name | One-Line Summary | Elaborates |
|-------|----------|-----------------|------------------|-----------|
| CS-01 | | | | |
| [... all conventions ...] | | | | |

---

## 16. Cross-Artifact Consistency Check

| Check | Status | Notes |
|-------|--------|-------|
| All standard convention categories addressed (or marked N/A with reason) | [Yes / No] | |
| Every convention has a unique CS-NN ID | | |
| Every convention is concrete and idiomatic to the committed stack | | |
| Security conventions implement the SEC-NN controls | | |
| Conventions elaborate (do not contradict) the Phase 4 SP-NN/DA-NN | | |
| Logging/observability conventions cover H-NN hook emission | | |
| Semantic-commit convention encodes traceability | | |
| Every convention has AI-Proposed and Practitioner-Calibrated forms | | |
| No application code produced | | |

---

## 17. Confidence Summary

| Section | Confidence | Basis |
|---------|-----------|-------|
| Stack idioms & structure | [H/M/L] | |
| Error handling & logging | [H/M/L] | |
| Security coding patterns | [H/M/L] | |
| Testing & documentation | [H/M/L] | |

**Overall conventions confidence:** [H/M/L]
**Lowest-confidence area:** [name and explain]

---

## 18. Revision Protocol

| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline coding standards | |

---

## 19. Handoff Status

- [ ] All standard convention categories addressed (or marked N/A)
- [ ] Every convention has a unique CS-NN ID
- [ ] Every convention is concrete and idiomatic to the committed stack
- [ ] Security conventions implement the SEC-NN controls
- [ ] Conventions elaborate, not contradict, the Phase 4 patterns
- [ ] Semantic-commit convention encodes traceability
- [ ] Convention index complete
- [ ] No application code produced

**Status:** [Ready for Step 09 (and the per-module pipeline) / Gaps require resolution first / Blocked]
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] All standard convention categories are present: stack idioms, code
      structure, naming, error handling, logging/observability, security
      coding, configuration, concurrency/resources, API/data-access, testing,
      documentation, commits
- [ ] A category that does not apply is marked "Not applicable — [reason],"
      not silently omitted
- [ ] Every convention has a unique CS-NN ID
- [ ] Every convention is concrete enough to be cited by generated code and
      verified by a reviewer, and idiomatic to the committed stack (no "use
      good naming")
- [ ] Every convention has both an AI-Proposed form and a
      Practitioner-Calibrated form with a calibration note
- [ ] Security coding patterns implement the Phase 4 SEC-NN controls, with
      the SEC-NN citation
- [ ] Error handling, logging, naming, structure, configuration, and
      data-access conventions elaborate the corresponding SP-NN/DA-NN
      patterns (cited), without contradicting them
- [ ] Logging/observability conventions cover how the H-NN monitoring hooks
      are emitted in code
- [ ] The semantic-commit convention encodes the traceability chain (task,
      module-spec section, score changes)
- [ ] The convention index lists every convention for downstream reference
- [ ] No application code, no Phase 4 re-architecture present
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 02 of 15 in the Phase 5 Implementation Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `implementation.instructions.md`*
*Previous step: `step-01-implementation-project-plan.prompt.md`*
*Next step: `step-03-module-scope-confirmation.prompt.md` (begins the per-module pipeline)*
