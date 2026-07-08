# Step 07 — Implementation PRD
# Phase 5: Implementation
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 07 of 15 |
| **Type** | Action Prompt with Clarification Step — **PARAMETERIZED (runs once per epic)** |
| **Phase** | Phase 5 — Implementation |
| **SDD Step** | Detail (module level) |
| **Stage** | Stage 2 — Per-Module Implementation |
| **Artifact Produced** | Implementation PRD (the bridge from the epic's spec to its task list) — one per epic |
| **Principles Addressed** | All six — the PRD carries the per-epic principle requirements into implementation |
| **Requires As Input** | Step 06 Epic Overview (required); the Phase 4 module-spec section and API contract the epic realizes (required); Step 02 Coding Standards (CS-NN, required); the framework IDs the epic cited (SEC/DA/H) |
| **Feeds Into** | Step 08 (Task List Generation expands this PRD into tasks) |
| **Companion File** | `implementation.instructions.md` |

---

## How to Use This Prompt

This is a **parameterized prompt** run **once per epic**. It is the article's
"Detail — Produce Implementation PRDs": it bridges the gap between the
architectural specification (what the module should do) and the task list
(what AI should build). The Implementation PRD specifies, for the epic, the
functions/components to implement with their input/output types, the
invariants that must hold, the error-handling strategy per failure mode, the
logging and metrics to emit, the test properties to verify, any formal
verification targets, and the Core-Principle requirements.

1. Confirm `implementation.instructions.md` is loaded as project context.
2. Open a new AI session with a large context window.
3. Paste **the Step 06 epic overview, the Phase 4 module-spec section + API
   contract the epic realizes, and the Step 02 coding standards** above the
   kickoff line.
4. Paste the **Kickoff** line, naming the epic.
5. The AI asks 3–7 clarifying questions (presence check first) about failure
   modes, invariants, and verification targets.
6. The AI produces the Implementation PRD.
7. Review against the Evaluation Checklist, then proceed to Step 08.

> **Note on why this step is non-skippable:** The article's first pitfall is
> "generating without specifying tasks." The Detail (this step) and Task
> (Step 08) steps are what make generation a disciplined loop rather than a
> negotiation. Skipping the PRD produces vague tasks and vague code.

> **Note:** Planning only — the PRD specifies what to build; it generates no
> code.

---

## What This Step Is — and Is Not

### What This Step Produces

- **The components to implement** — the specific functions/methods/classes,
  with input/output types derived from the module spec and API contract.
- **Invariants** — the properties that must always hold (e.g., "account
  balance must never be negative after a transaction").
- **Error-handling strategy** — the handling for each failure mode the spec
  enumerates.
- **Logging & metrics** — what each operation emits (the H-NN hooks).
- **Test properties** — the properties to verify (for property-based
  testing), the required test types, and the coverage target.
- **Formal verification targets** — which components in this epic, if any, are
  designated for formal verification (conditional).
- **Security & conformance requirements** — input validation and authz
  (SEC-NN), and the conformance targets (API contract, data schema DA-NN).
- **Core-Principle requirements** — the per-epic obligations (security checks
  on every input, coverage above threshold, performance within budget).
- **Non-goals, risk/rollback, validation/success metrics, open questions.**

### What This Step Does NOT Produce

- ❌ Any code (Step 09 generates code from the task list this PRD feeds)
- ❌ The task list (Step 08)
- ❌ Re-specification of the module's interfaces or data model (those are the
  Phase 4 spec; this details how to implement them — if the spec is wrong,
  that is a Step 15 amendment, surfaced via Step 03)
- ❌ A PRD for another epic (run once per epic)

If the PRD cannot be written because the epic's spec content is ambiguous,
that ambiguity should have been caught in Step 03 — return to Step 03 and
disposition it, do not invent the missing detail.

---

## System Instructions

You are a **senior implementation engineer** within the AI-Centric Software
Development framework, producing the implementation PRD that turns an epic's
specification into a buildable, verifiable detail document.

### Your Role

You take the epic overview, the Phase 4 spec content it realizes, the API
contract, and the coding standards. You specify the components to implement
with their I/O types, the invariants, the error handling per failure mode,
the logging/metrics, the test properties, any formal verification targets,
and the principle requirements. You derive every detail from the
specification — you do not invent behavior.

You are precise. The PRD's precision directly determines the task list's
precision, which directly determines the generated code's quality. Vague PRD,
vague code.

### Behavioral Rules

**Derive components and I/O types from the spec and contract.**
The functions/components to implement, and their input/output types, come from
the Phase 4 module spec and the API contract — not from imagination. Cite the
spec interface and contract operation each component implements.

**Specify invariants explicitly.**
State the properties that must always hold. Invariants drive both the
implementation and the property-based tests. "Balance must never be negative
after a transaction" is an invariant; it becomes a test property in Step 08.

**Specify error handling per failure mode.**
For each failure mode the spec enumerates, specify the handling (the error
returned, whether retryable, the side effects), conforming to the SP-NN/CS-NN
error conventions. The happy path alone is an incomplete PRD.

**Specify logging and metrics.**
State what each operation logs and what metrics it emits, mapped to the H-NN
monitoring hooks — so observability is built with the feature, not after.

**Specify test properties and the coverage target.**
Derive the properties to verify (for property-based testing) from the
invariants and the spec. State the required test types and the coverage
target (from Step 03's confirmed targets). Tests verify the spec, not the
implementation.

**Designate formal verification targets (conditional).**
If the Phase 4 spec or Step 03 designated any component in this epic for
formal verification (critical paths: financial calc, auth logic, state
machines, concurrency), name it and the safety/liveness properties to prove.
If none, state "No formal-verification targets in this epic."

**Carry the principle requirements.**
State the Core-Principle obligations: security checks on every input
(SEC-NN), coverage above threshold, performance within budget, conformance to
the contract/schema. These become task acceptance criteria in Step 08.

**Detail, do not re-specify or implement.**
The PRD details how to build the spec; it does not change the spec and it
generates no code. Spec ambiguity routes back to Step 03; structural problems
to Step 15.

---

## Clarification Step

Read the epic overview, the Phase 4 spec content, the API contract, and the
coding standards. Then ask **3–7 clarifying questions**, never more.

**First question — presence check + epic confirmation:** "I am producing the
Implementation PRD for epic [M-NN-MS\<m\>-E\<e\> — title]. I have the epic
overview, the Phase 4 spec content and contract it realizes, and the coding
standards. Anything missing?"

Permitted topics: failure modes not fully enumerated in the spec; invariants
the practitioner wants asserted; formal-verification applicability;
performance-budget specifics; test-property priorities.

Ask one at a time. Then produce the PRD in a single response.

---

## Kickoff

> Paste the Step 06 epic overview, the Phase 4 module-spec section + API
> contract the epic realizes, and the Step 02 coding standards above this
> line, then paste this line to trigger the prompt.

```
I am producing the Implementation PRD for epic [M-NN-MS<m>-E<e> — title]. The
epic overview, the Phase 4 spec content and contract, and the coding
standards are pasted above. Please ask your clarifying questions one at a
time, beginning with the presence check, before producing the Implementation
PRD.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.

```markdown
# Implementation PRD — [Title] (M-NN-MS\<m\>-E\<e\>)
# Phase 5 Step 07 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Epic:** [M-NN-MS\<m\>-E\<e\> — title]
**Implementation Section:** [data models / business logic / API / auth / integration / tests / monitoring / IaC]
**Maps To:** Epic overview [link]; Phase 4 module-spec section [reference]; API contract [reference]
**Owner:** [GOV-NN]
**Status:** [Draft / Reviewed]
**Artifact Date:** [date]

---

## 1. Overview & Objective
[What this epic implements and the goal, in one or two sentences.]

## 2. Components to Implement
| Component (function/method/class) | Implements (spec interface / contract op) | Input Type | Output Type | Notes |
|-----------------------------------|-------------------------------------------|------------|-------------|-------|
| [name] | [SIC-NN op / API op / spec interface] | [type] | [type] | |

## 3. Invariants
| Invariant ID | Invariant (must always hold) | Applies To |
|--------------|------------------------------|------------|
| INV-1 | [e.g., balance never negative after a transaction] | [component] |

## 4. Error-Handling Strategy (per failure mode)
| Failure Mode | Handling | Error (CS-NN/SP-NN envelope) | Retryable? | Side Effects |
|--------------|----------|------------------------------|-----------|--------------|
| [from spec] | | | | |

## 5. Logging & Metrics to Emit
| Operation | Logs | Metrics | Monitoring Hook (H-NN) |
|-----------|------|---------|------------------------|
| [op] | | | H-NN |

## 6. Test Properties & Coverage
| Property (for property-based testing) | Derived From (invariant/spec) |
|---------------------------------------|-------------------------------|
| [e.g., output length equals input length] | INV-N / spec |

| Field | Value |
|-------|-------|
| Required test types | [unit / integration / property / contract] |
| Coverage target | [% — from Step 03] |

## 7. Formal Verification Targets (conditional)
[If designated: the component(s), the safety properties, the liveness
properties to prove. If none: "No formal-verification targets in this epic."]

| Component | Safety Properties | Liveness Properties |
|-----------|-------------------|---------------------|

## 8. Security & Compliance Requirements
| Requirement | Control (SEC-NN) | Convention (CS-NN) |
|-------------|------------------|--------------------|
| [input validation, authz enforcement, secrets handling] | SEC-NN | CS-NN |

Any step needing elevated privileges or touching sensitive resources is
called out as requiring **explicit human approval** — never routed around.

## 9. Conformance Targets
| Conformance Check | Reference |
|-------------------|-----------|
| API contract conformance | [contract] |
| Data schema conformance | DA-NN |
| Interface conformance | SIC-NN |

## 10. Core-Principle Requirements
| Principle | Requirement |
|-----------|-------------|
| Security | [SEC-NN checks on every input] |
| Maintainability | [coverage ≥ target; documentation generated] |
| Economics | [effort budget] |
| Operations | [H-NN hooks emitted; health check] |
| Scoring & Metrics | [metrics collected] |
| Correctness Verification | [conformance green; properties hold; formal targets if any] |

## 11. Non-Goals (Out of Scope)
[What this epic deliberately will not do.]

## 12. Risk, Rollback & Recovery
[What can go wrong; the rollback path; whether a backup/snapshot is required
before risky steps.]

## 13. Validation / Success Metrics
[How success is verified: tests green, conformance green, coverage ≥ target,
performance within budget, security scans clean.]

## 14. Open Questions
[Anything unresolved — but spec ambiguities route back to Step 03, not here.]

## 15. Cross-Artifact Consistency Check
| Check | Status | Notes |
|-------|--------|-------|
| Components & I/O types derived from spec/contract | [Yes/No] | |
| Invariants stated; error handling per failure mode | | |
| Logging/metrics mapped to H-NN | | |
| Test properties derived from invariants/spec | | |
| Formal-verification targets stated (or none) | | |
| Security/conformance/principle requirements carried | | |
| No code; no re-specification of the spec | | |

## 16. Confidence Summary
**Overall confidence:** [H/M/L] — **Lowest-confidence area:** [name]

## 17. Revision Protocol
| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline implementation PRD | |
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] Every component to implement has input/output types derived from the
      Phase 4 spec and API contract (cited), not invented
- [ ] Invariants that must always hold are stated explicitly
- [ ] Error handling is specified for every failure mode the spec enumerates
      — not just the happy path — using the CS-NN/SP-NN error conventions
- [ ] Logging and metrics are specified per operation and mapped to the H-NN
      monitoring hooks
- [ ] Test properties are derived from the invariants/spec, with the required
      test types and the coverage target from Step 03
- [ ] Formal-verification targets are designated (with safety/liveness
      properties) or explicitly stated as none
- [ ] Security requirements cite SEC-NN and CS-NN; privileged/sensitive steps
      are flagged for human approval
- [ ] Conformance targets (API contract, data schema DA-NN, interface SIC-NN)
      are stated
- [ ] The Core-Principle requirements are carried as concrete obligations
- [ ] No code is produced; the Phase 4 spec is not re-specified (ambiguity
      routes to Step 03, structural problems to Step 15)
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 07 of 15 in the Phase 5 Implementation Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `implementation.instructions.md`*
*Previous step: `step-06-epic-breakout.prompt.md`*
*Next step: `step-08-task-list-generation.prompt.md` (run per epic)*
