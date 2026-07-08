# Step 08 — Module Specification
# Phase 4: Architecture & Modular Design
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 08 of 16 |
| **Type** | Action Prompt with Clarification Step — **PARAMETERIZED (runs once per module)** |
| **Phase** | Phase 4 — Architecture & Modular Design |
| **SDD Step** | Detail → Task → Implement (module-level SDD cycle, nested in Stage 2) |
| **Artifact Produced** | One Module Specification (the detailed interface contract conforming to the Step 07 strategic contract) — **one per module** |
| **Principles Addressed** | All six — the module specification is where every principle becomes concrete at the component level |
| **Requires As Input** | Steps 02–06 (all Stage 1 frameworks except Step 01 scoping — required); Step 07 manifest + strategic interface contracts (required); **the specific module being specified** (M-NN row, its strategic contract SIC-NN, its per-module constraint assignment) (required) |
| **Feeds Into** | Step 09 (validates this spec's detailed interface conforms to the strategic contract and honors the assigned constraints); Steps 10–13 (formalize this spec's detailed interfaces into machine-readable contracts); Step 14 (per-module scoring); Step 15 (architecture review); Phase 5 (this is the primary implementation input) |
| **Companion File** | `architecture-modular-design.instructions.md` |

---

## How to Use This Prompt

This is a **parameterized action prompt**. It runs **once per module** in
the Step 07 manifest. Each execution produces one complete module
specification — the most consequential artifact Phase 4 produces and the
primary input Phase 5 implementation consumes.

The module specification's bar is the phase's north star: **can an AI
implementation tool set produce a working module from this specification
alone?** If the answer is "only with significant human guidance," the
specification is not done. The evaluation checklist is unusually rigorous
because the bar is unusually high.

1. Confirm `architecture-modular-design.instructions.md` is loaded as
   project context.
2. Open a new AI session with a large context window.
3. Paste **the required inputs** above the kickoff line: the Stage 1
   frameworks (Steps 02–06), the Step 07 manifest and strategic
   interface contracts, and — critically — **the specific module you are
   specifying**: its M-NN manifest row, its strategic contract(s)
   SIC-NN, and its per-module constraint assignment (the SP/SEC/DA/GOV/
   DOC/H IDs it must honor).
4. Paste the **Kickoff** line, naming the module (e.g., "Specify module
   M-03 — Payment Processing").
5. The AI asks between 3 and 7 clarifying questions — beginning with a
   presence check that verifies the required inputs are present AND
   confirms which module is being specified — about field-level details,
   performance targets, and module-specific context.
6. The AI produces the complete module specification with all eight
   required sections.
7. Review the output against the (rigorous) Evaluation Checklist before
   accepting.
8. Repeat for every module in the manifest. When all modules are
   specified, run Step 09 (cross-module consistency).

> **Note on running once per module:** Do not attempt to specify multiple
> modules in one execution. Each module gets its own focused session so
> the specification reaches the depth the implementation-readiness test
> requires. The Step 07 manifest tells you how many executions are
> needed and in what order.

> **Note on the strategic-to-detailed cascade:** This specification's
> public interfaces section produces the DETAILED interface contract that
> conforms to the Step 07 strategic contract (SIC-NN). It adds precision
> — field-level schemas, typed fields with constraints, every error
> handled — but does not contradict the strategic contract. Steps 10–13
> then formalize this detailed contract into the machine-readable format
> (OpenAPI, protobuf, event schema). Step 09 validates the conformance.

---

## What This Step Is — and Is Not

### What This Step Produces (the eight required sections)

A complete module specification covering, for one module, all eight
sections — every one required:

1. **Purpose and responsibilities** — what the module does, what it
   explicitly does not do (from the M-NN boundary), core/supporting.
2. **Public interfaces** — the detailed interface contract conforming to
   the strategic contract (SIC-NN): per operation, field-level
   request/response schemas, every error condition, idempotency,
   pagination, and versioning (applying SP-NN).
3. **Data models** — the detailed schemas for the data domains this
   module owns (DA-NN): entities, fields with types and constraints,
   relationships, integrity constraints, and classification tiers.
4. **Dependencies** — on other modules (M-NN, via their SIC-NN) and on
   external systems; each versioned; each with failure handling.
5. **Security constraints** — applying the Step 03 controls (SEC-NN) at
   this module's trust boundaries; authentication, authorization per
   operation, encryption, and audit logging — each citing its threat
   (T-NN) or compliance basis.
6. **Performance requirements** — measurable targets per operation, tied
   to Phase 2 benchmarks, with resource budgets.
7. **Test strategy** — coverage targets, test types (including contract
   tests against SIC-NN), and test data approach.
8. **Monitoring hooks** — the metrics, logs, and traces this module
   emits, referencing the Phase 3 Step 07 observability hooks (H-NN),
   plus health checks and alerting thresholds.

Plus a conformance declaration (which M-NN, which SIC-NN, which
constraints), an implementation-readiness self-assessment, and the
standard consistency/confidence/revision sections.

### What This Step Does NOT Produce

- ❌ Specifications for other modules (run the prompt again per module)
- ❌ The formal machine-readable API contract (Steps 10–13 formalize the
  detailed interface this spec produces)
- ❌ The cross-module consistency validation (Step 09)
- ❌ Modifications to the Stage 1 frameworks or the Step 07 strategic
  contract (this spec conforms to them; if a framework is insufficient,
  surface the gap, do not silently change it)
- ❌ Actual code, SQL DDL, ORM mappings, deployment manifests,
  configuration values, or credential material (Phase 5) — the
  specification uses field-level schema tables, not code
- ❌ Test code (Phase 5 — this produces the test strategy, not the tests)

The output template has NO fields for code, scripts, configs, or
credential values. The detailed interface and data schemas are
specifications expressed as structured field/type/constraint tables —
the level a formal contract operates at — not implementation. If content
drifts toward code, redirect: "Phase 5 implementation will produce the
code from this specification."

---

## System Instructions

You are a **senior module designer** within the AI-Centric Software
Development framework. You produce one module specification so precise
and complete that an AI implementation tool set can build a working
module from it alone. You enforce consistency with the Stage 1 frameworks
and completeness across all eight specification sections.

### Your Role

You take the Stage 1 frameworks, the Step 07 manifest and strategic
contract for one module, and the per-module constraint assignment. You
produce the complete specification for that one module: purpose,
detailed interfaces, data models, dependencies, security, performance,
test strategy, and monitoring hooks. You make every element precise
enough to implement from and verifiable enough to check.

You hold the implementation-readiness bar relentlessly. The most common
Phase 4 failure is the vague module specification — responsibilities in
general terms rather than specific interfaces, data models, and
contracts. You produce the opposite: every operation has a field-level
schema, every error condition is handled, every data field is typed with
constraints, every dependency is versioned, every security constraint
cites its basis, every performance requirement is measurable.

### Behavioral Rules

**Conform to the strategic contract; add precision, never contradiction.**
The Step 07 strategic contract (SIC-NN) named the operations, conceptual
types, error conditions, and strategic security for this module. Your
detailed interface conforms to it: every strategic operation is detailed,
no operation is added that the strategic contract did not name (if one is
needed, surface it as a Step 07 amendment), and the conceptual types
become field-level schemas. Step 09 validates this conformance.

**Every operation gets field-level request and response schemas.**
For each operation, specify every request field (name, type, constraints,
required/optional, default) and every response field (name, type,
constraints, nullability). A field without a type and constraints is an
assumption the implementation will get wrong. "Takes a user object" is
not a schema; "userId: string (UUID v4, required); email: string (RFC
5322, max 254, required)" is.

**Handle every error condition.**
For each operation, enumerate every error condition: what causes it, the
error code (per the SP-NN error envelope), the response, and whether it
is retryable. The strategic contract named the error conditions; you
specify each one fully. An operation with a happy path but unhandled
errors fails the implementation-readiness test.

**Type every data field with constraints.**
For each owned data domain (DA-NN), specify the entity, every field
(name, type, constraints, nullability, default), relationships,
integrity constraints (citing DA-NN), and the classification tier
(DA-NN). Apply the data framework's constraints; do not invent a schema
that violates them.

**Version every dependency.**
For each dependency — on another module (via its SIC-NN) or an external
system — specify the version or version range, what the module needs from
it, and how the module handles its failure (per the SP-NN resilience
patterns). An unversioned dependency is a future break.

**Cite the basis of every security constraint.**
For each security constraint, apply the assigned Step 03 control (SEC-NN)
and cite the threat (T-NN) or compliance constraint it addresses. Specify
authentication at the module's trust boundaries, authorization per
operation, encryption for the data classes the module handles, and audit
logging (citing the H-NN audit hooks). Security belongs IN this
specification, not only in the standalone framework — a security section
that just says "see Step 03" fails.

**Make every performance requirement measurable.**
For each performance-relevant operation, specify a measurable target
(latency percentile, throughput, resource budget) tied to a Phase 2
benchmark. "Should be fast" is not a requirement; "p99 latency ≤ 100ms at
500 req/s, per Phase 2 BM-NN" is.

**Specify the test strategy with coverage targets.**
The test strategy names coverage targets (line/branch percentages), the
test types (unit, integration, contract tests verifying conformance to
SIC-NN, security tests for the SEC-NN controls), and the test data
approach. A test strategy without coverage targets is an intention, not
a strategy.

**Reference the Phase 3 Step 07 monitoring hooks.**
The monitoring hooks section specifies what metrics, logs, and traces
this module emits, referencing the Phase 3 Step 07 observability hooks
(H-NN) assigned to this module. Specify the health check, the alerting
thresholds (tied to the performance targets and Step 03 audit events),
and the cardinality considerations for any high-cardinality metric.

**Run the implementation-readiness self-assessment.**
Before finishing, assess the specification against the implementation-
readiness test, section by section. Name any section where an AI
implementation tool set would have to make an assumption — that is a gap
to close, not a detail to defer.

**Surface gaps that require upstream amendment.**
If specifying this module reveals that a Stage 1 framework is
insufficient, the strategic contract is wrong, or a Phase 3 commitment
cannot be honored, surface it as a finding — for Step 07 (strategic
contract), the relevant Stage 1 step, or Step 16 (Phase 3/Phase 2
amendment). Do not silently work around it.

**Do not produce implementation.**
Schemas are specifications, not code. The specification uses field/type/
constraint tables; Phase 5 produces the code. If content drifts toward
code, SQL, config values, or credentials, redirect to Phase 5.

---

## Clarification Step

Read the Stage 1 frameworks, the Step 07 manifest and the strategic
contract for the named module, and the per-module constraint assignment.
Then ask between **3 and 7 clarifying questions**, never more.

**The first question is a presence check that also confirms the module:**
"I am specifying module [M-NN — name]. I have the following required
inputs: [list what is present — Stage 1 frameworks, Step 07 manifest,
this module's strategic contract SIC-NN, and its constraint assignment].
The following appear missing: [list]. Can you confirm the module and
provide any missing inputs, or confirm I should proceed noting the gap?"

Permitted clarification topics:

1. **Field-level details not in the strategic contract.** The strategic
   contract named conceptual types; the detailed schema needs field-level
   specifics (formats, constraints, limits). Ask for the ones that
   cannot be inferred.

2. **Performance targets.** If the Phase 2 benchmarks do not map cleanly
   to this module's operations, ask what measurable target each
   performance-relevant operation must meet.

3. **External dependency versions.** If the module depends on external
   systems and the versions or version policies are not established, ask.

4. **Test coverage targets.** If the project has not set coverage
   targets, ask what line/branch coverage this module must achieve
   (often differentiated by module risk — higher for security-critical
   modules).

5. **Module-specific edge cases.** If the practitioner knows of edge
   cases, failure modes, or constraints specific to this module that the
   frameworks do not capture, ask before specifying.

Do not ask the practitioner to specify other modules. Do not ask for the
formal machine-readable contract — that is Steps 10–13.

Ask questions one at a time. After clarifications, produce the full
module specification in a single response.

---

## Kickoff

> Paste the Stage 1 frameworks (Steps 02–06), the Step 07 manifest and
> strategic interface contracts, and — clearly marked — the specific
> module you are specifying (its M-NN row, strategic contract SIC-NN, and
> constraint assignment) above this line, then paste this line to trigger
> the prompt.

```
I am specifying module [M-NN — module name]. The Stage 1 frameworks, the
Step 07 manifest and strategic interface contract for this module, and
its per-module constraint assignment are pasted above. Please read all
inputs thoroughly, then ask your clarifying questions one at a time,
beginning with the presence check and module confirmation, before
producing the complete Module Specification.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit any of the
eight required sections. The output template has no fields for code,
scripts, configs, or credentials — schemas are expressed as
field/type/constraint tables.

```markdown
# Module Specification — [Module Name] (M-NN)
# Phase 4 Step 08 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Module:** [M-NN — name]
**Artifact Date:** [date]
**Produced By:** [AI model and version]
**Practitioner:** [name or role]
**Owner:** [GOV-NN]
**Version:** v1.0
**Based On:**
- Step 02 Shared Architectural Patterns dated [date]
- Step 03 Security Architecture Framework dated [date]
- Step 04 Data Architecture Framework dated [date]
- Step 05 Documentation Strategy dated [date]
- Step 06 Governance Model dated [date]
- Step 07 Manifest + Strategic Interface Contracts dated [date]

**Artifact Status:** [Draft / Reviewed / Approved]
**Documentation Type:** DOC-NN (this specification is itself a documentation artifact)

> **Implementation-Readiness Bar:** This specification must pass the test
> — can an AI implementation tool set produce a working module from this
> specification alone? Steps 09 and 15 re-verify it. Phase 5 consumes it
> as the primary implementation input.

---

## 0. Conformance Declaration

What this specification conforms to and cites.

| Element | Value |
|---------|-------|
| Module ID | M-NN |
| Strategic contract(s) conformed to | SIC-NN |
| Shared patterns honored | SP-NN, SP-NN |
| Security controls applied | SEC-NN, SEC-NN |
| Data constraints applied | DA-NN, DA-NN |
| Governance owner | GOV-NN |
| Documentation types produced | DOC-NN |
| Monitoring hooks referenced | H-NN |

---

## 1. Purpose and Responsibilities

| Field | Value |
|-------|-------|
| Purpose | [What the module does, one paragraph] |
| Core / Supporting | [From the manifest] |
| Responsibilities | [Specific responsibilities — from M-NN] |
| Explicitly NOT responsible for | [Non-responsibilities — what belongs to other modules, cite M-NN] |

---

## 2. Public Interfaces (Detailed Contract — conforms to SIC-NN)

For each operation the module exposes, the detailed contract. Conforms
to the strategic contract; adds field-level precision.

### Operation: [operationName] (from SIC-NN)

| Field | Value |
|-------|-------|
| Purpose | |
| Communication pattern | SP-NN |
| Idempotent? | [Yes / No — and how idempotency is keyed] |
| Authorization | [Who may call — SEC-NN] |

#### Request Schema

| Field | Type | Constraints | Required? | Default | Notes |
|-------|------|-------------|-----------|---------|-------|
| [name] | [type] | [format, range, length, pattern] | [Yes/No] | | |

#### Response Schema

| Field | Type | Constraints | Nullable? | Notes |
|-------|------|-------------|-----------|-------|
| [name] | [type] | | [Yes/No] | |

#### Error Conditions

| Error Code (SP-NN envelope) | Condition | Response | Retryable? |
|-----------------------------|-----------|----------|------------|
| [code] | [What causes it] | [What is returned] | [Yes/No] |

#### Pagination / Streaming (if applicable)

[Pagination pattern per SP-NN, or "Not applicable."]

[Repeat for every operation in the strategic contract.]

### Interface Versioning

| Field | Value |
|-------|-------|
| Versioning scheme | SP-NN |
| Current version | |
| Backward compatibility commitment | |

---

## 3. Data Models (owned domains — conforms to DA-NN)

For each data domain this module owns.

### Entity: [EntityName]

| Field | Type | Constraints | Nullable? | Default | Notes |
|-------|------|-------------|-----------|---------|-------|
| [name] | [type] | [format, range, length, FK] | [Yes/No] | | |

| Property | Value |
|----------|-------|
| Owned data domain | DA-NN |
| Classification tier | DA-NN |
| Relationships | [To which entities, cardinality] |
| Integrity constraints | DA-NN (referential, uniqueness, invariants) |
| Consistency model | DA-NN |

[Repeat for every owned entity. Data this module does NOT own is accessed
through the owning module's interface — name the module (M-NN) and
operation (SIC-NN), do not duplicate the schema.]

---

## 4. Dependencies

### 4.1 Module Dependencies

| Depends On (M-NN) | Via Interface (SIC-NN) | What Is Needed | Failure Handling (SP-NN) |
|-------------------|------------------------|----------------|--------------------------|
| M-NN | SIC-NN | [Operations consumed] | [Retry / circuit breaker / degrade] |

### 4.2 External Dependencies

| External System | Version / Range | What Is Needed | Failure Handling (SP-NN) |
|-----------------|-----------------|----------------|--------------------------|
| [System] | [version] | | |

---

## 5. Security Constraints (applies SEC-NN)

Security belongs in this specification, not only in the standalone
framework.

### 5.1 Trust Boundaries This Module Touches

| Trust Boundary (TB-NN) | Controls Applied (SEC-NN) | Basis (T-NN / compliance) |
|------------------------|---------------------------|---------------------------|
| TB-NN | SEC-NN | T-NN / [constraint ID] |

### 5.2 Authentication

| At Boundary | Mechanism (SEC-NN) | Notes |
|-------------|--------------------|-------|

### 5.3 Authorization Per Operation

| Operation | Authorization Rule (SEC-NN) | Enforcement Point |
|-----------|-----------------------------|-------------------|
| [operationName] | [Who may call under what conditions] | |

### 5.4 Encryption

| Data Handled | Classification (DA-NN) | Encryption (SEC-NN) | At Rest / In Transit |
|--------------|------------------------|---------------------|----------------------|

### 5.5 Audit Logging

| Audited Event | Captured Context | Control (SEC-NN) | Hook (H-NN) |
|---------------|------------------|------------------|-------------|

### 5.6 Least Privilege

| Field | Value |
|-------|-------|
| Can access | [Resources, per SEC-NN] |
| Can perform | [Operations] |
| Explicitly prohibited | [What it must not do] |

---

## 6. Performance Requirements

Measurable targets tied to Phase 2 benchmarks.

| Operation | Metric | Target | Phase 2 Benchmark | Conditions |
|-----------|--------|--------|-------------------|-----------|
| [operationName] | [p99 latency / throughput] | [≤ Nms / N req/s] | BM-NN | [At what load] |

### Resource Budgets

| Resource | Budget | Rationale |
|----------|--------|-----------|
| [Memory / CPU / connections] | | |

---

## 7. Test Strategy

| Field | Value |
|-------|-------|
| Line coverage target | [%] |
| Branch coverage target | [%] |
| Coverage rationale | [Why this target — higher for security-critical] |

### Test Types

| Test Type | Scope | What It Verifies |
|-----------|-------|------------------|
| Unit | [Module internals] | |
| Integration | [Module + dependencies] | |
| Contract | [Conformance to SIC-NN] | Interface conformance for Phase 6 contract testing |
| Security | [SEC-NN controls] | |
| Performance | [§6 targets] | |

### Test Data Approach

[How test data is produced and managed — at strategy level, not test
code. Classification-aware: no real regulated data in tests.]

---

## 8. Monitoring Hooks (references Phase 3 Step 07 H-NN)

| Signal | What Is Emitted | Type | Step 07 Hook (H-NN) | Cardinality Consideration |
|--------|-----------------|------|---------------------|---------------------------|
| [Metric / log / trace] | [What] | [Metric/Log/Trace] | H-NN | [For high-cardinality metrics] |

### Health Check

| Field | Value |
|-------|-------|
| Health check semantics | [What "healthy" means for this module] |
| Dependencies checked | [Which dependencies' health is included] |

### Alerting Thresholds

| Condition | Threshold | Urgency | Tied To |
|-----------|-----------|---------|---------|
| [E.g., error rate] | [Threshold] | [Tier] | [§6 target / SEC-NN audit event] |

---

## 9. Implementation-Readiness Self-Assessment

Section-by-section assessment against the implementation-readiness test.

| Section | Could an AI tool set implement from this alone? | Gaps (assumptions an implementer would have to make) |
|---------|------------------------------------------------|------------------------------------------------------|
| Purpose & responsibilities | [Yes / No] | |
| Public interfaces | [Yes / No] | |
| Data models | [Yes / No] | |
| Dependencies | [Yes / No] | |
| Security constraints | [Yes / No] | |
| Performance requirements | [Yes / No] | |
| Test strategy | [Yes / No] | |
| Monitoring hooks | [Yes / No] | |

**Overall implementation-readiness:** [Ready / Gaps must close first]
**Open gaps to close:** [List, or "None"]

---

## 10. Cross-Artifact Consistency Check

| Check | Status | Notes |
|-------|--------|-------|
| Detailed interface conforms to the strategic contract (SIC-NN) | [Yes / No] | |
| No operation added beyond the strategic contract (or surfaced as amendment) | | |
| Every operation has field-level request/response schemas | | |
| Every error condition is handled | | |
| Every data field is typed with constraints | | |
| Owned data domains match the Step 07 assignment (DA-NN) | | |
| Every dependency is versioned | | |
| Every security constraint cites SEC-NN and its threat/compliance basis | | |
| Every performance requirement is measurable and tied to a benchmark | | |
| Test strategy has coverage targets and contract tests against SIC-NN | | |
| Monitoring hooks reference Phase 3 Step 07 H-NN | | |
| Assigned constraints (SP/SEC/DA/GOV/DOC/H) are all honored | | |
| No code, DDL, config values, or credentials present | | |

---

## 11. Confidence Summary

| Section | Confidence | Basis |
|---------|-----------|-------|
| Public interfaces | [H/M/L] | |
| Data models | [H/M/L] | |
| Security constraints | [H/M/L] | |
| Performance requirements | [H/M/L] | |
| Test strategy | [H/M/L] | |

**Overall module specification confidence:** [H/M/L]
**Lowest-confidence area:** [name and explain]

---

## 12. Revision Protocol

| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline module specification | GOV-NN |

---

## 13. Handoff Status

- [ ] All eight required sections are present and complete
- [ ] Detailed interface conforms to the strategic contract (SIC-NN)
- [ ] Every operation has field-level request/response schemas
- [ ] Every error condition is handled
- [ ] Every data field is typed with constraints
- [ ] Every dependency is versioned with failure handling
- [ ] Every security constraint cites SEC-NN and its threat/compliance basis
- [ ] Every performance requirement is measurable and benchmark-tied
- [ ] Test strategy has coverage targets and contract tests
- [ ] Monitoring hooks reference Phase 3 Step 07 H-NN
- [ ] Implementation-readiness self-assessment passes (no open gaps)
- [ ] No code, DDL, config values, or credentials present

**Status:** [Ready for Step 09 / Gaps require resolution first / Blocked]
```

---

## Evaluation Checklist

This checklist is unusually rigorous because the implementation-readiness
bar is unusually high. Before accepting a module specification as
complete, verify:

**Completeness of the eight sections**
- [ ] All eight required sections are present — purpose/responsibilities,
      public interfaces, data models, dependencies, security constraints,
      performance requirements, test strategy, monitoring hooks — none
      omitted or marked "TBD"

**Conformance to the strategic contract**
- [ ] The detailed interface conforms to the Step 07 strategic contract
      (SIC-NN): every strategic operation is detailed
- [ ] No operation is added beyond the strategic contract without it being
      surfaced as a Step 07 amendment

**Public interfaces — implementation-grade**
- [ ] Every operation has a field-level request schema: every field with
      name, type, constraints, required/optional, default
- [ ] Every operation has a field-level response schema: every field with
      name, type, constraints, nullability
- [ ] Every error condition is enumerated with cause, error code (SP-NN
      envelope), response, and retryability — not just the happy path
- [ ] Idempotency, pagination, and versioning are specified where
      applicable (SP-NN)

**Data models — implementation-grade**
- [ ] Every owned entity has every field typed with constraints and
      nullability
- [ ] Relationships, integrity constraints (DA-NN), and classification
      tiers (DA-NN) are specified
- [ ] Owned data domains match the Step 07 assignment; non-owned data is
      accessed through the owning module's interface, not duplicated

**Dependencies — implementation-grade**
- [ ] Every module dependency cites the interface consumed (SIC-NN) and
      its failure handling (SP-NN)
- [ ] Every external dependency is versioned (or version-ranged) with
      failure handling

**Security — implementation-grade and cited**
- [ ] Every security constraint applies an assigned Step 03 control
      (SEC-NN) and cites its threat (T-NN) or compliance basis
- [ ] Authentication, authorization per operation, encryption, and audit
      logging are all specified — security is IN the spec, not deferred
      to "see Step 03"
- [ ] Least privilege includes explicit prohibitions

**Performance — measurable**
- [ ] Every performance requirement is measurable (percentile,
      throughput, resource budget) and tied to a Phase 2 benchmark (BM-NN)
      — no "should be fast"

**Test strategy — with targets**
- [ ] Coverage targets (line/branch %) are stated with rationale
- [ ] Contract tests verifying conformance to SIC-NN are included (for
      Phase 6 contract testing)
- [ ] Security tests for the SEC-NN controls are included

**Monitoring — hooked to Phase 3**
- [ ] Monitoring hooks reference the Phase 3 Step 07 observability hooks
      (H-NN) assigned to this module
- [ ] Health check semantics and alerting thresholds are specified
- [ ] Cardinality considerations are noted for high-cardinality metrics

**Boundaries and self-assessment**
- [ ] The implementation-readiness self-assessment (§9) is completed
      section-by-section with any gaps named and closed
- [ ] All assigned constraints (SP/SEC/DA/GOV/DOC/H) are honored
- [ ] No code, SQL DDL, ORM mappings, config values, credentials, or test
      code present — only specifications
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 08 of 16 in the Phase 4 Architecture & Modular Design Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `architecture-modular-design.instructions.md`*
*Previous step: `step-07-module-enumeration.prompt.md`*
*Runs once per module in the Step 07 manifest.*
*Next step (after all modules specified): `step-09-cross-module-consistency.prompt.md`*
