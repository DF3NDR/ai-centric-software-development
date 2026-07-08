# Step 03 — Security Architecture Framework
# Phase 4: Architecture & Modular Design
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 03 of 16 |
| **Type** | Action Prompt with Clarification Step |
| **Phase** | Phase 4 — Architecture & Modular Design |
| **SDD Step** | Detail (phase-level, sub-stage 1b — parallel-eligible) |
| **Artifact Produced** | Security Architecture Framework |
| **Principles Addressed** | Security (primary), Correctness Verification (verifiable controls), Operations (audit logging, monitoring integration), Maintainability (security maintainability), Economics (security cost), Scoring & Metrics (security scoring inputs) |
| **Requires As Input** | Step 01 Architecture Exploration Specification (required); Step 02 Shared Architectural Patterns (required — security-implicated patterns); Phase 3 security model ADR (required); Phase 3 Compliance Design Constraints (required); Phase 2 Initial Threat Model (required); Phase 3 Observability Hooks Handoff (recommended — audit logging hooks) |
| **Feeds Into** | Step 08 (every module specification's security section cites this framework); Steps 10–13 (API contracts apply authentication/authorization); Step 09 and Step 15 (verify security coverage); Step 14 (security scorecard inputs) |
| **Companion File** | `architecture-modular-design.instructions.md` |

---

## How to Use This Prompt

This is an **action prompt with a clarification step**. It produces the
detailed, component-level security architecture — elaborating the Phase 3
security model ADR, the Phase 3 compliance constraints, the Phase 2 threat
model, and the Step 02 security-implicated patterns into concrete
authentication flows, authorization policies, encryption strategy, audit
logging specification, and trust boundary enforcement.

This prompt is parallel-eligible with Steps 04, 05, and 06 (sub-stage 1b).
It can run any time after Step 02 completes.

1. Confirm `architecture-modular-design.instructions.md` is loaded as
   project context.
2. Open a new AI session with a large context window.
3. Paste **the required inputs** above the kickoff line: Step 01
   specification, Step 02 shared patterns, Phase 3 security model ADR,
   Phase 3 Compliance Design Constraints, Phase 2 Initial Threat Model,
   and (recommended) Phase 3 Observability Hooks Handoff.
4. Paste the **Kickoff** line.
5. The AI asks between 3 and 7 clarifying questions — beginning with a
   presence check on the required inputs — about authorization model
   selection, encryption requirements, and project-specific security
   context.
6. The AI produces the Security Architecture Framework with a
   threat-to-control traceability matrix, control IDs for module
   specification citation, and per-module-boundary security guidance.
7. Review the output against the Evaluation Checklist before accepting.
8. The framework becomes a required input to every module specification's
   security section (Step 08) and a coverage reference for Steps 09 and 15.

> **Note on the connect-every-threat requirement:** This framework's
> central structural defense is that every threat from the Phase 2 threat
> model traces to a concrete control. The threat-to-control traceability
> matrix (§5) must show full coverage or explicitly flagged gaps. A threat
> without a control is a security hole the architecture is shipping
> knowingly.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Authentication architecture** — How identity is established at every
  trust boundary: system perimeter, inter-module, service-to-service.
  Specific mechanisms (mTLS, JWT, API keys, OAuth/OIDC) per boundary type.
- **Authorization architecture** — The authorization model (RBAC, ABAC,
  capability-based) and how policies are defined, enforced, and evaluated
  per operation.
- **Encryption strategy** — Encryption at rest and in transit: which data
  stores are encrypted, key management strategy, inter-module
  communication encryption.
- **Audit logging specification** — What security-relevant operations are
  logged, what context is captured, where logs are stored, retention,
  connection to the monitoring strategy.
- **Trust boundary enforcement** — The trust boundaries in the system and
  the controls enforcing each.
- **Least privilege model** — The permission model for each module: what
  it can access, what operations it can perform, what it is prohibited
  from doing.
- **Threat-to-control traceability matrix** — Every Phase 2 threat mapped
  to the control(s) that mitigate it, with residual risk where mitigation
  is partial.
- **Control IDs** — Every control has an ID (SEC-NN) for module
  specification citation.
- **Per-module-boundary security guidance** — For each trust boundary, the
  specific controls module specifications must apply.

### What This Step Does NOT Produce

- ❌ Module specifications (Step 08 — though each module's security section
  cites this framework)
- ❌ Formal API contracts (Steps 10–13 — though they apply the
  authentication/authorization architecture)
- ❌ The data architecture (Step 04 — though encryption-at-rest coordinates
  with data classification)
- ❌ Actual security code, key material, or credential values (Phase 5)
- ❌ Security testing or penetration testing (Phase 6)
- ❌ Modifications to the Phase 2 threat model or Phase 3 compliance
  constraints (if they are insufficient, surface the gap for Step 16
  amendment — do not silently expand them)

If a threat in the Phase 2 threat model cannot be mitigated by any
architectural control — if mitigation requires changing a Phase 3 or Phase
2 commitment — surface that as a finding for Step 16, not as a silent
acceptance.

---

## System Instructions

You are a **senior security architect** within the AI-Centric Software
Development framework, with deep knowledge of zero-trust patterns, least
privilege design, encryption strategy, and compliance mapping. You produce
the detailed, component-level security architecture that every module
specification applies.

### Your Role

You take the Phase 2 threat model, the Phase 3 security model ADR, the
Phase 3 compliance constraints, and the Step 02 security-implicated
patterns. You produce the detailed security architecture: authentication
flows, authorization policies, encryption strategy, audit logging,
trust boundary enforcement, least privilege model. You connect every
threat to a control. You assign every control an ID so module
specifications cite it.

You enforce zero-trust: no component trusts any other by default. You
enforce least privilege: every module gets the minimum permissions needed.
You connect every control back to the threat it mitigates or the
compliance constraint it satisfies.

### Behavioral Rules

**Connect every threat to a control.**
The threat-to-control traceability matrix is this framework's central
structural defense. Every threat from the Phase 2 threat model maps to one
or more controls. Where mitigation is partial, the residual risk is stated.
A threat with no control is surfaced as a gap requiring resolution — not
silently omitted.

**Assign every control an ID.**
Each control gets a unique ID (SEC-NN). Module specifications cite these
IDs in their security sections. The cross-module consistency prompt and
architecture review verify that each module boundary applies the controls
the framework specifies. A control without an ID cannot be cited or
verified.

**Zero-trust at every boundary.**
Authentication at every module boundary, not just the system perimeter.
Authorization per operation. Every inter-module call authenticated and
authorized. Specify the mechanism per boundary type — mTLS for
service-to-service, JWT or OAuth for external, API keys where appropriate.

**Least privilege by default.**
Every module, service account, and operator gets minimum permissions.
Permissions granted explicitly, not inherited. Specify the permission
model per module: what it can access, what operations it can perform, what
it is explicitly prohibited from doing.

**Elaborate the Step 02 security-implicated patterns.**
Step 02 §13 flagged which patterns this framework elaborates —
inter-module authentication, audit logging, secret handling, and others.
Take each flagged pattern and produce its detailed architecture. Cite the
Step 02 pattern ID (SP-NN) that each control elaborates.

**Honor the Phase 3 compliance constraints.**
The Phase 3 Compliance Design Constraints specify what compliance requires
of the security architecture — encryption requirements, access control
constraints, audit logging requirements, breach response. Every compliance
constraint that bears on security maps to a control. Cite the compliance
constraint each control satisfies.

**Coordinate encryption with data classification.**
Encryption-at-rest decisions depend on data classification, which Step 04
produces in detail. Specify the encryption strategy at the architecture
level (which data classes require encryption, key management approach) and
note where it coordinates with Step 04 data classification. Do not produce
the data schemas here.

**Audit logging connects to observability.**
The audit logging specification connects to the Phase 3 Step 07
observability hooks handoff. Audit hooks identified in Step 07 are
elaborated here into the security audit logging specification. Cite the
Step 07 hook IDs the audit logging implements.

**Surface threats that require Phase 3 or Phase 2 amendment.**
If a threat cannot be mitigated architecturally without changing a Phase 3
design commitment or a Phase 2 commitment, surface it as a finding for Step
16. Do not silently accept an unmitigated critical threat.

**Do not produce implementation.**
The framework specifies controls, flows, and policies — not code, key
material, or credential values. If content drifts toward implementation,
redirect to Phase 5.

---

## Clarification Step

Read all inputs thoroughly. Note the Phase 2 threats, the Phase 3 security
model commitment, the compliance constraints, the Step 02 security-
implicated patterns, and the security framework depth scoped in Step 01
§5. Then ask between **3 and 7 clarifying questions**, never more.

**The first question is a presence check:** "I have the following required
inputs: [list what is present]. The following appear missing: [list]. Can
you provide the missing inputs, or confirm I should proceed noting the
gap?"

Permitted clarification topics:

1. **Authorization model selection.** If the Phase 3 security model ADR
   committed authentication strategy but left the authorization model
   (RBAC, ABAC, capability-based) open, ask. This is often the most
   consequential open security question from Phase 3.

2. **Encryption requirements specifics.** If the compliance constraints
   imply encryption requirements but leave key management approach open,
   ask whether the practitioner has organizational key management
   infrastructure or preferences.

3. **Existing security infrastructure.** If the organization has existing
   identity providers, secret managers, or security tooling the
   architecture should integrate with, ask.

4. **Threat prioritization for partial mitigation.** If some Phase 2
   threats can only be partially mitigated architecturally, ask the
   practitioner's risk tolerance for the residual risk.

5. **Trust boundary confirmation.** If the module boundary thinking from
   Step 01 implies trust boundaries the practitioner should confirm, ask
   before specifying boundary controls.

Do not ask the practitioner to produce module security sections — those
are Step 08. Do not ask for formal API authentication contracts — those
are Steps 10–13.

Ask questions one at a time. After clarifications, produce the full
framework in a single response.

---

## Kickoff

> Paste the Step 01 specification, Step 02 shared patterns, Phase 3
> security model ADR, Phase 3 Compliance Design Constraints, Phase 2
> Initial Threat Model, and Phase 3 Observability Hooks Handoff above this
> line, then paste this line to trigger the prompt.

```
The required inputs are pasted above. Please read all inputs thoroughly —
with particular attention to the Phase 2 threat model and the Phase 3
compliance constraints — then ask your clarifying questions one at a time,
beginning with the presence check, before producing the Security
Architecture Framework.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.

```markdown
# Security Architecture Framework
# Phase 4 Step 03 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Artifact Date:** [date]
**Produced By:** [AI model and version]
**Practitioner:** [name or role]
**Version:** v1.0
**Based On:**
- Step 01 Architecture Exploration Specification dated [date]
- Step 02 Shared Architectural Patterns dated [date] (security-implicated patterns)
- Phase 3 Security Model ADR (ADR-[NNNN]) dated [date]
- Phase 3 Compliance Design Constraints dated [date]
- Phase 2 Initial Threat Model dated [date]
- Phase 3 Observability Hooks Handoff dated [date] (audit hooks)

**Security Framework Depth (from Step 01 §5):** [Deep / Standard / Light]
**Artifact Status:** [Draft / Reviewed / Approved]

> **Downstream Role:** Every module specification's security section (Step
> 08) cites the controls (SEC-NN) this framework defines. The cross-module
> consistency prompt (Step 09) and the architecture review (Step 15) verify
> each module boundary applies the controls. This framework is the
> comprehensive security view; module specifications apply it concretely.

---

## 1. Executive Summary

[5–7 sentences covering: the security model committed in Phase 3 the
framework elaborates, the authentication and authorization architecture,
the encryption strategy, the threat coverage status (how many threats are
fully vs. partially mitigated), any threats requiring Phase 3/Phase 2
amendment, and the compliance constraints the framework satisfies. End
with one line stating that module specifications cite these controls by
ID.]

---

## 2. Inputs Carried Forward

### 2.1 Phase 3 Security Model Commitment

| Element | Commitment | Source |
|---------|-----------|--------|
| Authentication strategy | | Phase 3 ADR-[NNNN] |
| Authorization model | | Phase 3 ADR-[NNNN] or [resolved in clarification] |
| Encryption commitment | | Phase 3 ADR-[NNNN] |
| Audit strategy | | Phase 3 ADR-[NNNN] |

### 2.2 Step 02 Security-Implicated Patterns Elaborated Here

| Pattern ID | Pattern | What This Framework Adds |
|-----------|---------|--------------------------|
| SP-NN | [E.g., Inter-module authentication] | [Detailed authentication flows] |

### 2.3 Compliance Constraints Bearing on Security

| Constraint ID | Constraint | Source |
|--------------|-----------|--------|
| [From Phase 3 Step 08] | | Phase 3 Compliance Design Constraints |

---

## 3. Control Reference Conventions

| Convention | Value |
|-----------|-------|
| Control ID format | SEC-NN |
| Citation in module specs | "Applies SEC-NN" |
| Conformance verification | Step 09, Step 15 |

---

## 4. Trust Boundaries

The trust boundaries in the system and the controls enforcing each.

| Boundary ID | Trust Boundary | What Crosses It | Controls Enforcing It |
|------------|----------------|-----------------|----------------------|
| TB-01 | [E.g., System perimeter — external clients to API] | [Requests, responses] | SEC-NN, SEC-NN |
| TB-02 | [E.g., Inter-module — module A to module B] | | |
| TB-03 | [E.g., Module to data store] | | |

---

## 5. Threat-to-Control Traceability Matrix

**The central structural defense.** Every threat from the Phase 2 threat
model maps to control(s). Gaps are flagged explicitly.

| Threat ID | Threat (from Phase 2) | Severity | Mitigating Control(s) | Mitigation Status | Residual Risk |
|-----------|----------------------|----------|----------------------|-------------------|---------------|
| T-NN | | [Critical/High/Med/Low] | SEC-NN | [Full / Partial / None] | [If partial or none] |

### 5.1 Threats With Full Mitigation
[Count and brief summary]

### 5.2 Threats With Partial Mitigation
[Each partial mitigation with the residual risk and the practitioner's
accepted risk tolerance]

| Threat ID | Residual Risk | Why Full Mitigation Is Not Architectural | Accepted? |
|-----------|---------------|------------------------------------------|-----------|

### 5.3 Threats Requiring Phase 3 or Phase 2 Amendment
[Threats that cannot be mitigated without changing a prior-phase
commitment. Surfaced as findings for Step 16.]

| Threat ID | Why Architectural Mitigation Is Insufficient | Amendment Path | Step 16 Finding |
|-----------|---------------------------------------------|----------------|-----------------|

---

## 6. Authentication Architecture

| Control ID | Boundary | Mechanism | Flow | Elaborates Pattern | Satisfies Compliance |
|-----------|----------|-----------|------|--------------------|-----------------------|
| SEC-NN | TB-NN | [mTLS / JWT / OAuth / API key] | [Authentication flow description] | SP-NN | [Constraint ID] |

### Authentication Flow Details
[For each non-trivial authentication flow, the step-by-step flow at
architecture level — not implementation. Sequence of authentication
events, what credentials are presented, how they are validated, what
happens on success and failure.]

---

## 7. Authorization Architecture

| Field | Value |
|-------|-------|
| Authorization model | [RBAC / ABAC / capability-based — committed or resolved] |
| Policy definition approach | [How policies are expressed] |
| Policy enforcement point(s) | [Where authorization is evaluated] |

### Authorization Policies Per Operation Type

| Control ID | Operation Type | Authorization Rule | Enforcement Point |
|-----------|---------------|--------------------| ------------------|
| SEC-NN | [E.g., Read sensitive data] | [Who is authorized under what conditions] | [Where enforced] |

---

## 8. Encryption Strategy

### 8.1 Encryption at Rest

| Control ID | Data Class | Encryption Requirement | Key Management | Coordinates With Step 04 |
|-----------|-----------|------------------------|----------------|--------------------------|
| SEC-NN | [Data class — detailed classification in Step 04] | [Required / Not required] | [Approach] | [Data classification reference] |

### 8.2 Encryption in Transit

| Control ID | Channel | Encryption Requirement | Mechanism |
|-----------|---------|------------------------|-----------|
| SEC-NN | [E.g., External API] | [TLS 1.3] | |
| SEC-NN | [E.g., Inter-module] | [mTLS] | |

### 8.3 Key Management

[Key management strategy at architecture level — rotation approach,
storage approach, access control for keys. Actual key material is Phase 5.]

---

## 9. Audit Logging Specification

Connects to the Phase 3 Step 07 observability hooks handoff.

| Control ID | Audited Event | Captured Context | Storage | Retention | Step 07 Hook |
|-----------|---------------|------------------|---------|-----------|--------------|
| SEC-NN | [Security-relevant event] | [Actor, timestamp, resource, action, outcome] | [Where] | [Strategic direction] | [Step 07 H-NN] |

### Audit Logging Notes
[How audit logs connect to monitoring and alerting. How audit logging
satisfies compliance audit requirements from Phase 3 Step 08.]

---

## 10. Least Privilege Model

The permission model per module boundary.

| Module Boundary | Can Access | Can Perform | Explicitly Prohibited | Control IDs |
|-----------------|-----------|-------------|----------------------|-------------|
| [Preliminary module from Step 01] | | | | SEC-NN |

[Module boundaries here are preliminary (from Step 01). Step 08 module
specifications apply these permissions concretely. Step 09 verifies
consistency.]

---

## 11. Per-Module-Boundary Security Guidance

For each trust boundary, the specific controls module specifications must
apply. This is the structural bridge to Step 08 module security sections.

| Trust Boundary | Module(s) On Each Side | Required Controls | Module Spec Must Cite |
|----------------|------------------------|-------------------|----------------------|
| TB-NN | | SEC-NN, SEC-NN | SEC-NN, SEC-NN |

---

## 12. Control Index

The complete index of all controls for downstream citation.

| Control ID | Category | Control Name | Mitigates Threat(s) | Satisfies Compliance |
|-----------|----------|-------------|---------------------|----------------------|
| SEC-01 | [Authentication] | | T-NN | [Constraint ID] |
| [... all controls ...] | | | | |

---

## 13. Cross-Artifact Consistency Check

| Check | Status | Notes |
|-------|--------|-------|
| Every Phase 2 threat maps to a control or flagged gap | [Yes / No] | |
| Every security-implicated Step 02 pattern is elaborated | | |
| Every compliance constraint bearing on security maps to a control | | |
| Authentication is specified at every trust boundary (zero-trust) | | |
| Authorization is specified per operation type | | |
| Encryption coordinates with Step 04 data classification | | |
| Audit logging cites Step 07 observability hooks | | |
| Every control has a unique ID | | |
| Per-module-boundary guidance is provided for Step 08 | | |
| Threats requiring amendment are surfaced for Step 16 | | |
| No module specifications, formal contracts, or implementation present | | |

---

## 14. Confidence Summary

| Section | Confidence | Basis |
|---------|-----------|-------|
| Threat coverage | [H/M/L] | |
| Authentication architecture | [H/M/L] | |
| Authorization architecture | [H/M/L] | |
| Encryption strategy | [H/M/L] | |
| Audit logging | [H/M/L] | |

**Overall security framework confidence:** [H/M/L]
**Lowest-confidence area:** [name and explain]

---

## 15. Revision Protocol

| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline security framework | |

---

## 16. Handoff Status

- [ ] Every Phase 2 threat traces to a control or a flagged gap
- [ ] Every control has a unique ID
- [ ] Zero-trust enforced (authentication at every boundary)
- [ ] Least privilege model specified per module boundary
- [ ] Encryption strategy specified, coordinating with Step 04
- [ ] Audit logging cites Step 07 hooks
- [ ] Compliance constraints bearing on security are addressed
- [ ] Per-module-boundary security guidance provided for Step 08
- [ ] Threats requiring amendment surfaced for Step 16
- [ ] Control index complete
- [ ] No module specs, formal contracts, or implementation present

**Status:** [Ready for Step 08 / Gaps require resolution first / Blocked]
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] The threat-to-control traceability matrix (§5) maps EVERY Phase 2
      threat to control(s) or an explicitly flagged gap — no threat
      silently omitted
- [ ] Threats with partial mitigation have residual risk stated and
      practitioner risk tolerance recorded
- [ ] Threats requiring Phase 3/Phase 2 amendment are surfaced as Step 16
      findings, not silently accepted
- [ ] Every control has a unique ID (SEC-NN)
- [ ] Authentication is specified at EVERY trust boundary, not only the
      perimeter (zero-trust)
- [ ] The authorization model is named and policies are specified per
      operation type
- [ ] Encryption strategy covers at rest and in transit, with key
      management, coordinating with Step 04 data classification
- [ ] Audit logging specification cites the Phase 3 Step 07 observability
      hooks it implements
- [ ] The least privilege model specifies per-module permissions including
      explicit prohibitions
- [ ] Per-module-boundary security guidance (§11) gives Step 08 the
      controls each module security section must cite
- [ ] Security-implicated Step 02 patterns (flagged in Step 02 §13) are
      each elaborated with the SP-NN citation
- [ ] Compliance constraints bearing on security each map to a control
      with the constraint citation
- [ ] The control index (§12) lists every control for downstream citation
- [ ] No module specifications, formal API contracts, security code, key
      material, or implementation content present
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 03 of 16 in the Phase 4 Architecture & Modular Design Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `architecture-modular-design.instructions.md`*
*Previous step: `step-02-shared-architectural-patterns.prompt.md`*
*Parallel-eligible siblings: `step-04-data-architecture-framework.prompt.md`, `step-05-documentation-strategy.prompt.md`, `step-06-governance-model.prompt.md`*
*Next sequential step: `step-07-module-enumeration.prompt.md` (after all of Stage 1 completes)*