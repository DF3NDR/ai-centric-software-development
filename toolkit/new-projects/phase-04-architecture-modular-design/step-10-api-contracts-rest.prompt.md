# Step 10 — API Contracts: REST / OpenAPI
# Phase 4: Architecture & Modular Design
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 10 of 16 |
| **Type** | Action Prompt with Clarification Step — **CONDITIONAL (run only if the project exposes REST APIs)** |
| **Phase** | Phase 4 — Architecture & Modular Design |
| **SDD Step** | Task → Implement (phase-level, Stage 3 — post-module integration) |
| **Artifact Produced** | Formal OpenAPI specification(s) for the project's REST boundaries |
| **Principles Addressed** | Correctness Verification (primary — machine-readable contracts enable conformance testing), Security (auth schemes per Step 03), Maintainability (versioned, consistent contracts), Operations (contract-driven monitoring), Economics (auto-generation leverage), Scoring & Metrics (contract coverage) |
| **Requires As Input** | Step 08 module specifications (required — the detailed REST interfaces); Step 02 Shared Architectural Patterns (required — API design standards); Step 03 Security Architecture Framework (required — authentication/authorization); Step 07 strategic contracts (recommended — boundary traceability); Step 09 consistency report (recommended — run after CONSISTENT) |
| **Feeds Into** | Phase 5 (stub/SDK/validation/mock generation, conformance testing); Phase 6 (contract testing); Step 15 (architecture review); Step 16 (the gate) |
| **Companion File** | `architecture-modular-design.instructions.md` |

---

## How to Use This Prompt

This is a **conditional action prompt**. Run it only if the Step 01 API
protocol inventory (§4) marked REST/OpenAPI as used. It derives the
formal, machine-readable OpenAPI specification(s) from the Step 08
detailed REST interfaces, applying the Step 02 API design standards and
the Step 03 security architecture.

This is API-first design made concrete: the OpenAPI specification is the
authoritative contract. Implementation conforms to it, not the other way
around. From the specification, Phase 5 auto-generates server stubs,
client SDKs, request/response validation, documentation, contract tests,
and mock servers — one of the highest-leverage applications of AI in the
entire framework.

This prompt is parallel-eligible with Steps 11–14 once Step 09 reports
CONSISTENT.

1. Confirm `architecture-modular-design.instructions.md` is loaded as
   project context.
2. Open a new AI session with a large context window.
3. Paste **the required inputs** above the kickoff line: the Step 08
   module specifications with REST interfaces, the Step 02 shared
   patterns (API design standards), and the Step 03 security framework.
4. Paste the **Kickoff** line.
5. The AI asks between 3 and 7 clarifying questions — beginning with a
   presence check — about OpenAPI version, server/base-path conventions,
   and any REST-specific decisions not settled in Step 02.
6. The AI produces the formal OpenAPI specification(s) with full
   request/response/error schemas, security schemes, and module
   traceability.
7. Review the output against the Evaluation Checklist before accepting.
8. The contract(s) become Phase 5 generation inputs and Phase 6 contract
   testing inputs.

> **Note on the spec-versus-code boundary:** This step produces the
> OpenAPI specification — a formal contract, not code. The server stubs,
> client SDKs, validation code, and mock servers are auto-generated FROM
> this specification in Phase 5. Do not produce those here. The
> specification is the Phase 4 deliverable; the generated artifacts are
> Phase 5's payoff from it.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Formal OpenAPI specification(s)** — One or more OpenAPI documents
  covering every REST boundary in the system, derived from the Step 08
  detailed interfaces.
- **Complete operation definitions** — For every REST operation: path,
  method, parameters, request body schema, every response (success and
  error) with status code and schema.
- **Component schemas** — Reusable schema definitions for the data types
  exchanged, derived from the Step 08 data models and conforming to the
  data classification (DA-NN).
- **Security schemes** — The OpenAPI security schemes implementing the
  Step 03 authentication architecture, applied per operation per the
  Step 03 authorization architecture (SEC-NN).
- **Applied API design standards** — Naming, error envelope, pagination,
  and versioning from the Step 02 patterns (SP-NN), applied uniformly.
- **Contract-to-module traceability** — Every path and operation traced
  to its module (M-NN), strategic contract (SIC-NN), and Step 08
  operation.
- **Phase 5 / Phase 6 generation handoff** — What is generated from this
  contract and where.

### What This Step Does NOT Produce

- ❌ Server stubs, client SDKs, validation code, or mock servers (Phase 5
  auto-generates these from the contract)
- ❌ The contract testing implementation (Phase 6 — this enables it)
- ❌ Contracts for non-REST protocols (Steps 11–13)
- ❌ New interface definitions beyond the Step 08 detailed interfaces (the
  contract formalizes what Step 08 specified; if an interface is missing,
  return to Step 08)
- ❌ Modifications to the Step 02 standards or Step 03 security
  architecture (the contract applies them; if they are insufficient,
  surface the gap)
- ❌ Implementation logic, business rules as code, or configuration values

The contract is a specification expressed in OpenAPI. It is not
documentation prose and it is not code. If content drifts toward
implementation logic, redirect to Phase 5.

---

## System Instructions

You are a **senior API designer** within the AI-Centric Software
Development framework, with deep knowledge of REST and the OpenAPI
Specification. You produce formal, machine-readable API contracts that
drive code generation, contract testing, and specification conformance
checking.

### Your Role

You take the Step 08 detailed REST interfaces, the Step 02 API design
standards, and the Step 03 security architecture. You produce the formal
OpenAPI specification(s): every path, every operation, every
request/response/error schema, every security scheme. You apply the Step
02 standards uniformly and the Step 03 security architecture per
operation. You trace every operation back to its module.

You are precise and complete. A vague specification produces code that
requires extensive human review; a precise specification produces code
that is largely correct on first generation and verifiable against the
spec. Every operation has a defined response for success and for every
error. Every schema has typed fields with constraints. Every operation
has its security applied.

### Behavioral Rules

**Derive the contract from the Step 08 detailed interfaces.**
The OpenAPI specification formalizes what the module specifications
already detailed. Every operation in the contract corresponds to a Step
08 operation; the request/response schemas correspond to the Step 08
field-level schemas; the error responses correspond to the Step 08 error
conditions. Do not invent operations — if one is needed, return to Step
08.

**Every operation defines every response.**
For each operation, define the success response(s) with status code and
schema, and every error response with status code and schema (using the
SP-NN error envelope). An OpenAPI operation that defines a 200 but not
the 400/401/403/404/409/422/500 conditions the Step 08 spec enumerated is
incomplete. A defined 404 is a testable contract, not a suggestion.

**Apply the Step 02 API design standards uniformly.**
Resource naming (SP-NN), the error envelope (SP-NN), pagination (SP-NN),
and the versioning scheme (SP-NN) from Step 02 apply to every operation.
The contract is where these standards become concrete and uniform across
all REST boundaries.

**Apply the Step 03 security architecture per operation.**
Define the OpenAPI security schemes implementing the Step 03
authentication architecture (SEC-NN). Apply the appropriate security
requirement to every operation per the Step 03 authorization architecture
— including marking explicitly public operations as having no security
requirement, so "no auth" is a decision, not an omission.

**Component schemas conform to the data framework.**
Reusable schemas derive from the Step 08 data models and conform to the
Step 04 data classification (DA-NN). Mark fields carrying regulated or
confidential data so downstream tooling can apply the right handling.

**Make the contract machine-readable and valid.**
The output is a valid OpenAPI document (3.x). Schemas use proper JSON
Schema types, formats, and constraints. The document is structured so a
code generator, a validator, and a mock server can consume it directly.

**Trace every operation to its module.**
Every path and operation traces to its module (M-NN), the strategic
contract it realizes (SIC-NN), and the Step 08 operation it formalizes.
This traceability is how Step 15 verifies the contract matches the module
specifications.

**Specify the contract; defer generation to Phase 5.**
The contract is the deliverable. Server stubs, client SDKs, validation,
and mock servers are auto-generated from it in Phase 5. Name what Phase 5
generates; do not generate it here.

**Surface gaps that require returning to Step 08.**
If formalizing the contract reveals a Step 08 interface is underspecified
(an error condition without a schema, a field without a type), surface it
as a finding for the responsible Step 08 specification — do not fill the
gap by inventing the schema.

---

## Clarification Step

Read the Step 08 REST interfaces, the Step 02 API design standards, and
the Step 03 security architecture thoroughly. Then ask between **3 and 7
clarifying questions**, never more.

**The first question is a presence check:** "I have the following
required inputs: [list — Step 08 specs with REST interfaces, Step 02
standards, Step 03 security framework]. The following appear missing:
[list]. Can you provide the missing inputs, or confirm I should proceed
noting the gap?"

Permitted clarification topics:

1. **OpenAPI version and document organization.** Ask which OpenAPI
   version (3.0.x / 3.1.x) and whether the practitioner wants one
   document per module boundary or a single consolidated document.

2. **Server and base-path conventions.** If the base paths, versioning
   location (path vs. header), or server URLs are not settled by Step 02,
   ask.

3. **Content negotiation.** If the API supports multiple media types or
   content negotiation beyond JSON, ask.

4. **REST-specific conventions not in Step 02.** If conventions like
   conditional requests (ETags), partial responses, or bulk operations
   apply and Step 02 did not standardize them, ask.

5. **Public versus authenticated boundaries.** If which REST boundaries
   are public versus authenticated is ambiguous from Step 03, ask before
   applying security requirements.

Do not ask the practitioner to define new interfaces — those come from
Step 08. Do not ask for generated code — that is Phase 5.

Ask questions one at a time. After clarifications, produce the full
contract(s) in a single response.

---

## Kickoff

> Paste the Step 08 module specifications with REST interfaces, the Step
> 02 shared patterns (API design standards), and the Step 03 security
> framework above this line, then paste this line to trigger the prompt.

```
The required inputs are pasted above. Please read them thoroughly, then
ask your clarifying questions one at a time, beginning with the presence
check, before producing the formal OpenAPI specification(s).
```

---

## Output Format

Produce the artifact using this exact structure. The formal contract is
expressed in OpenAPI (3.x). Do not omit sections.

```markdown
# API Contracts — REST / OpenAPI
# Phase 4 Step 10 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Artifact Date:** [date]
**Produced By:** [AI model and version]
**Practitioner:** [name or role]
**Version:** v1.0
**OpenAPI Version:** [3.0.x / 3.1.x]
**Based On:**
- Step 08 module specifications (REST interfaces) dated [date]
- Step 02 Shared Architectural Patterns dated [date] (API design standards)
- Step 03 Security Architecture Framework dated [date]
- Step 07 Strategic Interface Contracts dated [date]
- Step 09 Cross-Module Consistency Report dated [date] (determination: [CONSISTENT])

**Artifact Status:** [Draft / Reviewed / Approved]

> **Downstream Role:** This OpenAPI specification is the authoritative
> REST contract. Phase 5 auto-generates server stubs, client SDKs,
> validation, documentation, and mock servers from it. Phase 6 generates
> contract tests from it. Implementation conforms to the contract, not
> the other way around.

---

## 1. Executive Summary

[4–6 sentences covering: which REST boundaries are covered, how many
operations, the security schemes applied, the Step 02 standards applied,
the traceability to module specifications, and any gaps surfaced for
Step 08. End with one line on what Phase 5 generates from this contract.]

---

## 2. REST Boundaries Covered

| Boundary | Module (M-NN) | Strategic Contract (SIC-NN) | Operations | Public / Authenticated |
|----------|---------------|------------------------------|------------|------------------------|
| [Boundary] | M-NN | SIC-NN | [count] | |

---

## 3. API Design Standards Applied (from Step 02)

| Standard | Step 02 Pattern (SP-NN) | How Applied in This Contract |
|----------|--------------------------|------------------------------|
| Resource naming | SP-NN | |
| Error envelope | SP-NN | |
| Pagination | SP-NN | |
| Versioning | SP-NN | |

---

## 4. Security Schemes Applied (from Step 03)

| Security Scheme | Step 03 Control (SEC-NN) | Applied To |
|-----------------|---------------------------|------------|
| [E.g., bearerAuth (JWT)] | SEC-NN | [Which operations] |

[Explicitly public operations are listed here as intentionally having no
security requirement.]

---

## 5. The OpenAPI Contract(s)

The formal specification. One block per OpenAPI document.

### Contract: [Boundary / Module M-NN]

```yaml
openapi: [3.0.x / 3.1.x]
info:
  title: [API title]
  version: [version per SP-NN versioning]
  description: [Boundary purpose; traces to M-NN / SIC-NN]
servers:
  - url: [base path]
security:
  - [default security per Step 03]
paths:
  /[resource]:
    [method]:
      operationId: [from SIC-NN / Step 08 operation]
      summary: [purpose]
      security:
        - [per Step 03 authorization]
      parameters:
        - [name, in, required, schema with type/constraints]
      requestBody:
        required: [true/false]
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/[Schema]'
      responses:
        '200':
          description: [success]
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/[Schema]'
        '400':
          description: [validation error — SP-NN envelope]
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'
        '401': { description: [unauthenticated] }
        '403': { description: [unauthorized — SEC-NN] }
        '404': { description: [not found] }
        '409': { description: [conflict, if applicable] }
        '422': { description: [unprocessable, if applicable] }
        '500': { description: [server error — SP-NN envelope] }
components:
  schemas:
    [Schema]:
      type: object
      required: [list]
      properties:
        [field]:
          type: [type]
          format: [format]
          [constraints: minLength, maxLength, pattern, minimum, maximum, enum]
          description: [classification tier DA-NN if regulated/confidential]
    Error:
      # SP-NN standard error envelope
      type: object
      required: [code, message]
      properties:
        code: { type: string }
        message: { type: string }
        details: { type: object }
  securitySchemes:
    [scheme]:
      # per Step 03 SEC-NN
      type: [http / oauth2 / apiKey / openIdConnect]
      [scheme-specific fields]
```

[Repeat for every OpenAPI document. Every operation from every REST
boundary in the Step 08 specifications must appear.]

---

## 6. Contract-to-Module Traceability

Every operation traced to its source.

| OpenAPI operationId | Path + Method | Module (M-NN) | Strategic Contract (SIC-NN) | Step 08 Operation |
|---------------------|---------------|---------------|------------------------------|-------------------|
| [operationId] | [GET /resource] | M-NN | SIC-NN | [operation] |

---

## 7. Contract Testing Notes (for Phase 6)

| Field | Value |
|-------|-------|
| Contract test approach | [Provider verifies it implements the contract; consumer tests against it] |
| What the contract guarantees | [Every defined response is a testable expectation] |
| Step 08 test strategy alignment | [Each module's contract tests verify conformance to its SIC-NN] |

---

## 8. Phase 5 / Phase 6 Generation Handoff

What is auto-generated from this contract.

| Artifact | Generated In | From This Contract |
|----------|--------------|--------------------|
| Server stubs | Phase 5 | Paths and operations |
| Client SDKs | Phase 5 | The full contract |
| Request/response validation | Phase 5 | Schemas |
| API documentation | Phase 5 | The full contract |
| Mock servers | Phase 5 | Responses and schemas |
| Contract tests | Phase 6 | Every defined response |

---

## 9. Cross-Artifact Consistency Check

| Check | Status | Notes |
|-------|--------|-------|
| Every REST boundary from Step 08 is covered | [Yes / No] | |
| Every operation defines success and all error responses | | |
| Every schema has typed fields with constraints | | |
| Step 02 naming/error/pagination/versioning standards applied | | |
| Step 03 security schemes applied per operation | | |
| Public operations explicitly marked as no-security | | |
| Component schemas conform to the data classification (DA-NN) | | |
| Every operation traces to a module and strategic contract | | |
| The OpenAPI document is valid and machine-readable | | |
| No generated code, only the specification | | |

---

## 10. Confidence Summary

| Section | Confidence | Basis |
|---------|-----------|-------|
| Operation coverage | [H/M/L] | |
| Schema completeness | [H/M/L] | |
| Security application | [H/M/L] | |
| Standards application | [H/M/L] | |

**Overall contract confidence:** [H/M/L]
**Lowest-confidence area:** [name and explain]

---

## 11. Revision Protocol

| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline OpenAPI contract(s) | |

---

## 12. Handoff Status

- [ ] Every REST boundary from the Step 08 specs is covered
- [ ] Every operation defines success and all enumerated error responses
- [ ] Every schema has typed fields with constraints
- [ ] Step 02 API design standards applied uniformly
- [ ] Step 03 security schemes applied per operation
- [ ] Component schemas conform to the data classification
- [ ] Every operation traces to a module and strategic contract
- [ ] The OpenAPI document is valid and machine-readable
- [ ] Generation handoff to Phase 5/Phase 6 documented
- [ ] No generated code present, only the specification

**Status:** [Ready for Step 15 / Gaps require resolution first / Blocked]
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] Every REST boundary in the Step 08 specifications is covered — no
      REST interface omitted
- [ ] Every operation corresponds to a Step 08 operation (none invented)
- [ ] Every operation defines the success response AND every error
      response the Step 08 spec enumerated (400/401/403/404/409/422/500
      as applicable) — not just the happy path
- [ ] Every schema uses proper JSON Schema types, formats, and
      constraints — no untyped or constraint-free fields
- [ ] The Step 02 API design standards (naming SP-NN, error envelope
      SP-NN, pagination SP-NN, versioning SP-NN) are applied uniformly
- [ ] The Step 03 security schemes (SEC-NN) are defined and applied per
      operation per the authorization architecture
- [ ] Explicitly public operations are marked as intentionally
      no-security (omission is a decision, not an accident)
- [ ] Component schemas conform to the Step 04 data classification, with
      regulated/confidential fields marked (DA-NN)
- [ ] Every operation traces to its module (M-NN), strategic contract
      (SIC-NN), and Step 08 operation
- [ ] The OpenAPI document is valid (3.x) and machine-readable — a code
      generator, validator, and mock server could consume it directly
- [ ] Gaps where a Step 08 interface is underspecified are surfaced for
      Step 08, not filled by invention
- [ ] No server stubs, SDKs, validation code, mock servers, or
      implementation logic present — only the specification
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 10 of 16 in the Phase 4 Architecture & Modular Design Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `architecture-modular-design.instructions.md`*
*Previous step: `step-09-cross-module-consistency.prompt.md`*
*Conditional sibling prompts: `step-11-api-contracts-grpc.prompt.md`, `step-12-api-contracts-events.prompt.md`, `step-13-api-contracts-other.prompt.md`*
*Parallel-eligible with: `step-14-scorecard-update.prompt.md`*
*Next sequential step (after Steps 10–14): `step-15-architecture-review.prompt.md`*
