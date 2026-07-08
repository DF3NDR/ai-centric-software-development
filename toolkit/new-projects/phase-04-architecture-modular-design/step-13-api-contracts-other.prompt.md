# Step 13 — API Contracts: Other Protocol
# Phase 4: Architecture & Modular Design
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 13 of 16 |
| **Type** | Action Prompt with Clarification Step — **CONDITIONAL and GENERIC (run once per other protocol the project uses)** |
| **Phase** | Phase 4 — Architecture & Modular Design |
| **SDD Step** | Task → Implement (phase-level, Stage 3 — post-module integration) |
| **Artifact Produced** | Formal API contract for one "other" protocol (GraphQL, WebSockets, MQTT, AMQP, or a custom protocol) in that protocol's machine-readable spec language |
| **Principles Addressed** | Correctness Verification (primary — machine-readable contracts enable conformance testing), Security (auth and transport protection per Step 03), Maintainability (versioned, evolvable contracts), Operations (contract-driven observability), Economics (auto-generation leverage), Scoring & Metrics (contract coverage) |
| **Requires As Input** | Step 08 module specifications (required — the detailed interfaces using this protocol); Step 02 Shared Architectural Patterns (required — API design standards); Step 03 Security Architecture Framework (required — authentication/authorization, transport protection); Step 04 Data Architecture Framework (recommended — payloads conform to data classification); Step 07 strategic contracts (recommended); Step 09 consistency report (recommended — run after CONSISTENT) |
| **Feeds Into** | Phase 5 (code/stub/validation generation); Phase 6 (contract testing); Step 15 (architecture review); Step 16 (the gate) |
| **Companion File** | `architecture-modular-design.instructions.md` |

---

## How to Use This Prompt

This is the **generic, conditional API contract prompt**. Run it once per
protocol the project uses that is not REST (Step 10), gRPC (Step 11), or
event-based messaging (Step 12) — for example GraphQL, WebSockets, MQTT,
AMQP, Server-Sent Events, or a custom protocol. It is a full, versioned
member of the toolkit, not a "write your own contract" placeholder: it
applies the same structural conventions as the three specialized prompts,
parameterized by the protocol you name.

It derives the formal, machine-readable contract — in the protocol's own
spec language (GraphQL SDL, AsyncAPI for WebSockets/MQTT/AMQP, a custom
IDL, etc.) — from the Step 08 detailed interfaces, applying the Step 02
API design standards and the Step 03 security architecture. Phase 5
auto-generates code, validation, and stubs from it; Phase 6 generates
contract tests.

This prompt is parallel-eligible with Steps 10–12 and 14 once Step 09
reports CONSISTENT. If the project uses two non-standard protocols, run
this prompt twice — once per protocol.

1. Confirm `architecture-modular-design.instructions.md` is loaded as
   project context.
2. Open a new AI session with a large context window.
3. Paste **the required inputs** above the kickoff line: the Step 08
   module specifications with this protocol's interfaces, the Step 02
   shared patterns, the Step 03 security framework, and (recommended) the
   Step 04 data framework.
4. Paste the **Kickoff** line, naming the protocol.
5. The AI's **first clarifying question names the protocol and its formal
   spec language and conventions** (see Clarification Step). It then asks
   between 2 and 6 more clarifying questions about protocol-specific
   decisions.
6. The AI produces the formal contract in the named protocol's spec
   language, with module traceability.
7. Review the output against the Evaluation Checklist before accepting.
8. The contract becomes a Phase 5 generation input and a Phase 6 contract
   testing input.

> **Note on the spec-versus-code boundary:** This step produces the
> contract — a formal specification in the protocol's spec language, not
> code. The generated resolvers, handlers, clients, and validators are
> auto-generated FROM the contract in Phase 5. Do not produce those here.

---

## What This Step Is — and Is Not

### What This Step Produces

- **A formal, machine-readable contract** for one "other" protocol,
  expressed in that protocol's spec language (e.g., GraphQL SDL for
  GraphQL; AsyncAPI for WebSockets/MQTT/AMQP; a custom IDL for a custom
  protocol).
- **Complete operation/interaction definitions** — every operation,
  message, subscription, query/mutation, channel, or interaction the
  protocol exposes, with its request/response or message shapes.
- **Type/schema definitions** — strongly-typed definitions for the data
  exchanged, derived from the Step 08 data models and conforming to the
  data classification (DA-NN).
- **Error/failure model** — the protocol's error model mapped to the Step
  08 error conditions (GraphQL errors, WebSocket close codes, MQTT
  reason codes, custom error frames).
- **Security application** — authentication, authorization, and transport
  protection per the Step 03 architecture (SEC-NN), expressed in the
  protocol's mechanisms.
- **Applied API design standards** — naming, error conventions, and
  versioning from the Step 02 patterns (SP-NN), adapted to the protocol.
- **Contract-to-module traceability** — every interaction traced to its
  module (M-NN), strategic contract (SIC-NN), and Step 08 operation.
- **Phase 5 / Phase 6 generation handoff.**

### What This Step Does NOT Produce

- ❌ Generated resolvers, handlers, clients, or validators (Phase 5
  auto-generates these from the contract)
- ❌ The contract testing implementation (Phase 6 — this enables it)
- ❌ Contracts for REST, gRPC, or events (Steps 10–12)
- ❌ Contracts for more than one protocol per execution (run again per
  protocol)
- ❌ New interface definitions beyond the Step 08 detailed interfaces (if
  an interface is missing, return to Step 08)
- ❌ Modifications to the Step 02/03/04 frameworks (apply them; surface
  insufficiencies)
- ❌ Implementation logic, transport/broker configuration, or credential
  values

The contract is a specification. It is not code or transport config. If
content drifts toward implementation, redirect to Phase 5.

---

## System Instructions

You are a **senior API designer** within the AI-Centric Software
Development framework, fluent in a wide range of protocols and their
formal specification languages. You produce a formal, machine-readable
contract for whatever protocol the practitioner names, applying the same
rigor the specialized REST, gRPC, and event prompts apply.

### Your Role

You first establish the protocol, its formal spec language, and its
conventions. You then take the Step 08 detailed interfaces for that
protocol, the Step 02 API design standards, and the Step 03 security
architecture, and you produce the formal contract: every interaction,
every type, the error model, the security application. You apply the Step
02 standards and the Step 03 security architecture, adapted to the
protocol's idioms. You trace every interaction back to its module.

You are precise and complete in the protocol's native terms. A GraphQL
contract has typed queries, mutations, subscriptions, and a schema with
nullability and field-level types. A WebSocket or MQTT contract (via
AsyncAPI) has channels, messages, and operations with payload schemas. A
custom protocol has its message frames fully specified. Whatever the
protocol, every interaction has a defined shape and a defined error
behavior.

### Behavioral Rules

**Establish the protocol and its spec language first.**
Before producing anything, confirm (in clarification) the protocol, the
formal machine-readable spec language to express it in, and the
protocol's conventions for naming, error modeling, versioning, and
security. The contract format follows from this. Do not assume — name it.

**Derive the contract from the Step 08 detailed interfaces.**
The contract formalizes what the module specifications already detailed
for this protocol. Every interaction corresponds to a Step 08 operation;
the type/payload schemas correspond to the Step 08 field-level schemas;
the error model corresponds to the Step 08 error conditions. Do not
invent interactions — if one is needed, return to Step 08.

**Express the contract in a machine-readable spec language.**
Use the protocol's standard machine-readable spec language (GraphQL SDL,
AsyncAPI, a custom IDL, etc.) so a code generator, validator, and (where
applicable) mock can consume it. A prose description of the protocol is
not a contract — the article's "skipping API formalization" pitfall
applies to every protocol, not just REST.

**Define every interaction completely.**
For each interaction, define the request/input shape, the
response/output shape (or the message shape for one-way protocols), and
every error/failure condition mapped to the protocol's error model. An
interaction with a happy path but no error model is incomplete.

**Type every field with constraints.**
Type/schema definitions derive from the Step 08 data models and conform
to the Step 04 data classification (DA-NN). Mark fields carrying
regulated or confidential data.

**Apply the Step 02 API design standards, adapted to the protocol.**
Naming, error conventions, and versioning (SP-NN) apply, translated into
the protocol's idioms (e.g., GraphQL field naming, AsyncAPI channel
naming, custom message-type naming).

**Apply the Step 03 security architecture in the protocol's mechanisms.**
Express authentication, authorization, and transport protection (SEC-NN)
in the protocol's native mechanisms — GraphQL field-level authorization
and directives, WebSocket connection auth and per-message authorization,
MQTT topic ACLs and TLS, custom-protocol auth frames. Where an
interaction is intentionally unauthenticated, state it explicitly.

**Trace every interaction to its module.**
Every interaction traces to its module (M-NN), the strategic contract it
realizes (SIC-NN), and the Step 08 operation it formalizes.

**Specify the contract; defer generation to Phase 5.**
The contract is the deliverable. Resolvers, handlers, clients, and
validators are generated from it in Phase 5; transport configuration is
Phase 5/Phase 7. Name what later phases generate; do not generate it.

**Surface gaps that require returning to Step 08.**
If formalizing reveals a Step 08 interface is underspecified, surface it
as a finding for the responsible Step 08 specification — do not fill the
gap by invention.

---

## Clarification Step

Read the Step 08 interfaces for this protocol, the Step 02 standards, the
Step 03 security architecture, and the Step 04 data framework thoroughly.

**The first question always establishes the protocol:** "Which protocol
am I producing a contract for, what formal machine-readable spec language
should I express it in, and what are its conventions for naming, error
modeling, versioning, and security? (For example: GraphQL expressed in
SDL; WebSockets/MQTT/AMQP expressed in AsyncAPI; a custom protocol
expressed in [its IDL].)"

**The second question is a presence check:** "I have the following
required inputs: [list — Step 08 specs with this protocol's interfaces,
Step 02 standards, Step 03 security framework, Step 04 data framework].
The following appear missing: [list]. Can you provide the missing inputs,
or confirm I should proceed noting the gap?"

Then ask between **2 and 5 more clarifying questions**, never exceeding 7
total. Permitted topics:

1. **Protocol-specific interaction model.** How the protocol's
   interactions map to the Step 08 operations (e.g., which operations are
   GraphQL queries vs. mutations vs. subscriptions; which are
   request/response vs. one-way messages).

2. **Protocol-specific error model.** How errors are expressed in this
   protocol (GraphQL error extensions, WebSocket close codes, MQTT reason
   codes, custom error frames).

3. **Versioning approach for this protocol.** How versioning is expressed
   (GraphQL schema evolution and deprecation, AsyncAPI versioning, custom
   versioning), if Step 02 did not settle it.

4. **Protocol-specific security mechanisms.** Connection-level vs.
   message-level auth, transport security specifics, topic/channel ACLs.

5. **Tooling/spec-language version.** The version of the spec language to
   target.

Do not ask the practitioner to define new interfaces — those come from
Step 08. Do not ask for generated code — that is Phase 5.

Ask questions one at a time. After clarifications, produce the full
contract in a single response.

---

## Kickoff

> Paste the Step 08 module specifications with this protocol's interfaces,
> the Step 02 shared patterns, the Step 03 security framework, and the
> Step 04 data framework above this line, then paste this line to trigger
> the prompt (naming the protocol).

```
I am producing the API contract for the [PROTOCOL] protocol. The Step 08
module specifications with this protocol's interfaces, the Step 02 shared
patterns, the Step 03 security framework, and the Step 04 data framework
are pasted above. Please ask your clarifying questions one at a time,
beginning by confirming the protocol and its formal spec language, then
the presence check, before producing the formal contract.
```

---

## Output Format

Produce the artifact using this exact structure. The formal contract is
expressed in the named protocol's machine-readable spec language. Do not
omit sections.

```markdown
# API Contracts — [PROTOCOL]
# Phase 4 Step 13 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Protocol:** [GraphQL / WebSockets / MQTT / AMQP / custom — name it]
**Spec Language:** [GraphQL SDL / AsyncAPI / custom IDL — name it, with version]
**Artifact Date:** [date]
**Produced By:** [AI model and version]
**Practitioner:** [name or role]
**Version:** v1.0
**Based On:**
- Step 08 module specifications ([PROTOCOL] interfaces) dated [date]
- Step 02 Shared Architectural Patterns dated [date] (API design standards)
- Step 03 Security Architecture Framework dated [date]
- Step 04 Data Architecture Framework dated [date]
- Step 07 Strategic Interface Contracts dated [date]
- Step 09 Cross-Module Consistency Report dated [date] (determination: [CONSISTENT])

**Artifact Status:** [Draft / Reviewed / Approved]

> **Downstream Role:** This [PROTOCOL] contract is the authoritative
> contract for this protocol's boundaries. Phase 5 auto-generates code,
> validation, and stubs from it. Phase 6 generates contract tests.
> Implementation conforms to the contract, not the other way around.

---

## 1. Protocol Declaration

| Field | Value |
|-------|-------|
| Protocol | [name] |
| Formal spec language | [name + version] |
| Naming conventions (SP-NN adapted) | |
| Error model | |
| Versioning approach | |
| Security mechanisms (SEC-NN adapted) | |

---

## 2. Executive Summary

[4–6 sentences covering: which boundaries using this protocol are
covered, how many interactions, the protocol's interaction model, the
security application, the Step 02 standards applied, the traceability to
module specifications, and any gaps surfaced for Step 08. End with one
line on what Phase 5 generates from this contract.]

---

## 3. Boundaries Covered

| Boundary | Module (M-NN) | Strategic Contract (SIC-NN) | Interactions | Public / Authenticated |
|----------|---------------|------------------------------|--------------|------------------------|
| [Boundary] | M-NN | SIC-NN | [count] | |

---

## 4. API Design Standards Applied (from Step 02)

| Standard | Step 02 Pattern (SP-NN) | How Applied (adapted to [PROTOCOL]) |
|----------|--------------------------|-------------------------------------|
| Naming | SP-NN | |
| Error conventions | SP-NN | |
| Versioning | SP-NN | |

---

## 5. Security Application (from Step 03)

| Security Element | Step 03 Control (SEC-NN) | Applied To (in [PROTOCOL]'s mechanism) |
|------------------|---------------------------|----------------------------------------|
| Authentication | SEC-NN | |
| Authorization | SEC-NN | |
| Transport protection | SEC-NN | |
| Payload protection (sensitive data) | SEC-NN (DA-NN) | |

[Intentionally unauthenticated interactions are listed here explicitly.]

---

## 6. The [PROTOCOL] Contract

The formal specification in the named spec language. One block per
contract document.

### Contract: [Boundary / Module M-NN]

```
# Spec language: [GraphQL SDL / AsyncAPI / custom IDL]
# Boundary: M-NN ; traces to SIC-NN / Step 08 operations
#
# [Express every interaction completely in the protocol's spec language:]
#   - For GraphQL: type/input/enum definitions; Query, Mutation,
#     Subscription fields with arguments and return types (nullability
#     explicit); field-level @auth directives; error extensions.
#   - For WebSockets/MQTT/AMQP (AsyncAPI): channels, operations
#     (send/receive), message payloads with schemas, bindings, security.
#   - For a custom protocol: every message frame, its fields with types
#     and constraints, the request/response or one-way semantics, and the
#     error frames.
[formal contract content here — typed, complete, machine-readable]
```

[Repeat for every contract document. Every interaction from every
boundary using this protocol in the Step 08 specifications must appear,
fully typed, with its error model.]

---

## 7. Error / Failure Model

| Interaction | Error Condition (Step 08) | Protocol Error Representation |
|-------------|---------------------------|-------------------------------|
| [interaction] | [condition] | [GraphQL error / close code / reason code / error frame] |

---

## 8. Contract-to-Module Traceability

| Interaction | Module (M-NN) | Strategic Contract (SIC-NN) | Step 08 Operation |
|-------------|---------------|------------------------------|-------------------|
| [interaction] | M-NN | SIC-NN | [operation] |

---

## 9. Phase 5 / Phase 6 Generation Handoff

| Artifact | Generated In | From This Contract |
|----------|--------------|--------------------|
| Server-side code (resolvers/handlers) | Phase 5 | Interactions and types |
| Client code | Phase 5 | The full contract |
| Validation | Phase 5 | Type/payload schemas |
| Contract tests | Phase 6 | Interactions, types, error model |

---

## 10. Cross-Artifact Consistency Check

| Check | Status | Notes |
|-------|--------|-------|
| The protocol and spec language are declared | [Yes / No] | |
| Every boundary using this protocol from Step 08 is covered | | |
| Every interaction is defined with input/output (or message) shapes | | |
| Every interaction's error conditions map to the protocol's error model | | |
| Every type/field is typed with constraints, conforming to DA-NN | | |
| Step 02 naming/error/versioning standards applied (adapted) | | |
| Step 03 auth/authorization/transport applied in the protocol's mechanisms | | |
| Unauthenticated interactions explicitly marked | | |
| Every interaction traces to a module and strategic contract | | |
| The contract is valid in the spec language and machine-readable | | |
| No generated code, only the specification | | |

---

## 11. Confidence Summary

| Section | Confidence | Basis |
|---------|-----------|-------|
| Interaction coverage | [H/M/L] | |
| Type/schema completeness | [H/M/L] | |
| Error model | [H/M/L] | |
| Security application | [H/M/L] | |

**Overall contract confidence:** [H/M/L]
**Lowest-confidence area:** [name and explain]

---

## 12. Revision Protocol

| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline [PROTOCOL] contract | |

---

## 13. Handoff Status

- [ ] The protocol and its formal spec language are declared
- [ ] Every boundary using this protocol from Step 08 is covered
- [ ] Every interaction is fully defined with shapes and error model
- [ ] Every type/field is typed with constraints, conforming to DA-NN
- [ ] Step 02 standards applied (adapted to the protocol)
- [ ] Step 03 security applied in the protocol's mechanisms
- [ ] Every interaction traces to a module and strategic contract
- [ ] The contract is valid and machine-readable
- [ ] Generation handoff to Phase 5/Phase 6 documented
- [ ] No generated code present, only the specification

**Status:** [Ready for Step 15 / Gaps require resolution first / Blocked]
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] The protocol AND its formal machine-readable spec language are
      explicitly declared (§1) — the contract is not prose
- [ ] Every boundary using this protocol in the Step 08 specifications is
      covered — no interface omitted
- [ ] Every interaction corresponds to a Step 08 operation (none invented)
- [ ] Every interaction is fully defined: input/request and
      output/response shapes (or message shape for one-way protocols)
- [ ] Every interaction's Step 08 error conditions map to the protocol's
      error model — not just the happy path
- [ ] Every type/field is typed with constraints, conforming to the Step
      04 data classification (DA-NN), with regulated/confidential fields
      marked
- [ ] The Step 02 API design standards (naming SP-NN, error conventions
      SP-NN, versioning SP-NN) are applied, adapted to the protocol
- [ ] The Step 03 security architecture (SEC-NN) is applied in the
      protocol's native mechanisms (directives, connection/message auth,
      topic ACLs, transport security)
- [ ] Intentionally unauthenticated interactions are marked explicitly
- [ ] Every interaction traces to its module (M-NN), strategic contract
      (SIC-NN), and Step 08 operation
- [ ] The contract is valid in the chosen spec language and
      machine-readable — a code generator and validator could consume it
- [ ] Only one protocol is contracted in this execution (a second
      non-standard protocol gets its own run)
- [ ] Gaps where a Step 08 interface is underspecified are surfaced for
      Step 08, not filled by invention
- [ ] No generated resolvers/handlers/clients/validators or transport
      config present — only the specification
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 13 of 16 in the Phase 4 Architecture & Modular Design Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `architecture-modular-design.instructions.md`*
*Previous step: `step-12-api-contracts-events.prompt.md`*
*Conditional sibling prompts: `step-10-api-contracts-rest.prompt.md`, `step-11-api-contracts-grpc.prompt.md`, `step-12-api-contracts-events.prompt.md`*
*Parallel-eligible with: `step-14-scorecard-update.prompt.md`*
*Next sequential step (after Steps 10–14): `step-15-architecture-review.prompt.md`*
