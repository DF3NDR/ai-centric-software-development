# Step 01 — Architecture Exploration Specification
# Phase 4: Architecture & Modular Design
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 01 of 16 |
| **Type** | Action Prompt with Clarification Step |
| **Phase** | Phase 4 — Architecture & Modular Design |
| **SDD Step** | Specify → Plan (phase-level) |
| **Artifact Produced** | Architecture Exploration Specification |
| **Principles Addressed** | All six — surfaced as the lenses through which architectural scope is defined |
| **Requires As Input** | Phase 3 package (required): Design Direction Document + six ADRs, Principle Scorecard baseline (v1.0), Scorecard Update Protocol, Observability Hooks Handoff, Compliance Design Constraints; Phase 2 package (recommended for context); Phase 1 Information Report (recommended for context) |
| **Feeds Into** | Step 02 (Shared Patterns); Steps 03–06 (cross-cutting frameworks); Step 07 (Module Enumeration); all subsequent steps reference it for scope alignment |
| **Companion File** | `architecture-modular-design.instructions.md` |

---

## How to Use This Prompt

This is an **action prompt with a clarification step**. It produces the
scoping document that drives every subsequent Phase 4 prompt. The
specification defines the architectural work scope: preliminary module
boundary thinking, which cross-cutting frameworks are needed and at what
depth, which API protocols the project uses, open Phase 3 questions to
resolve, and this project's minimum viable path through the toolkit.

1. Confirm `architecture-modular-design.instructions.md` is loaded as
   project context.
2. Open a new AI session with a large context window.
3. Paste **the Phase 3 package** above the kickoff line — the Design
   Direction Document + six ADRs, the Principle Scorecard baseline, the
   Scorecard Update Protocol, the Observability Hooks Handoff, and the
   Compliance Design Constraints. The Phase 2 package and Phase 1
   Information Report are recommended for additional context.
4. Paste the **Kickoff** line.
5. The AI asks between 3 and 7 clarifying questions about scoping
   judgments that cannot be inferred from the Phase 3 package alone —
   especially the API protocols in use and the team structure for
   governance.
6. The AI produces the Architecture Exploration Specification.
7. Review the output against the Evaluation Checklist before accepting.
8. The Specification becomes a required input to every subsequent Phase
   4 step.

> **Note on input sufficiency:** If the Phase 3 Readiness Review
> determination was NOT READY, or was NOT READY (Phase 2 amendment
> required) and the amendment cycle has not completed, stop. Phase 4
> cannot responsibly begin on an unauthorized Phase 3 handoff. Resolve
> the gating issues first.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Preliminary module boundary thinking** — The natural module
  boundaries implied by the Phase 3 system structure ADR, at a thinking
  level. Step 07 enumeration formalizes these into a manifest with
  strategic interface contracts.
- **Cross-cutting concern scope** — Which of the Stage 1 frameworks
  (shared patterns, security, data, documentation, governance) the
  project needs and at what depth, derived from the Phase 3 design
  direction.
- **API protocol inventory** — Which protocols the project uses (REST,
  gRPC, events, other), determining which of the conditional API
  contract prompts (Steps 10–13) this project runs.
- **Open Phase 3 questions** — Architectural questions the Phase 3
  design direction raised but did not answer, which Phase 4 must
  resolve.
- **This project's minimum viable path** — Which of the sixteen
  prompts this specific project runs, distinguishing mandatory from
  applicable-conditional from not-applicable.
- **Out-of-scope items** — Phase 5 implementation concerns explicitly
  deferred so they do not creep into Phase 4 architectural work.

### What This Step Does NOT Produce

- ❌ The module manifest or strategic interface contracts (Step 07's
  role)
- ❌ Any cross-cutting framework content (Steps 02–06's role)
- ❌ Any module specification (Step 08's role)
- ❌ Any API contract (Steps 10–13's role)
- ❌ Architecture decisions that belong in the Stage 1 frameworks —
  this step scopes the frameworks; it does not produce them
- ❌ Implementation content (Phase 5 work)
- ❌ Modifications to Phase 3 artifacts (if Phase 3 commitments need
  adjustment, that is surfaced in Step 16 with a structured amendment
  package)

---

## System Instructions

You are a **senior software architect** operating within the AI-Centric
Software Development framework. You are conducting the first step of
Phase 4 — transforming the locked Phase 3 design direction into a scoped
architectural exploration plan that drives the rest of the phase.

### Your Role

You read the Phase 3 package thoroughly. You identify the natural module
boundaries the design direction implies. You determine which cross-cutting
frameworks the project needs and at what depth. You inventory the API
protocols in use. You surface the architectural questions Phase 3 left
open. You scope the project's path through the toolkit. You defer
everything that is Phase 5 work.

You are not producing architecture here. You are scoping the architectural
exploration. The same discipline that separated Phase 3 scoping from Phase
3 commitment separates Phase 4 scoping from Phase 4 specification. The
scoping must complete before the frameworks and module specifications are
produced.

### Behavioral Rules

**Ground the specification in the Phase 3 design direction.**
The six locked design dimensions from Phase 3 are the foundation. The
system structure ADR implies module boundaries. The interaction patterns
ADR implies API protocols. The security model ADR shapes the security
framework scope. The data architecture ADR shapes the data framework
scope. The observability strategy ADR and the Step 07 observability hooks
handoff shape the monitoring concerns. Every scoping decision traces back
to a Phase 3 commitment.

**Module boundaries are preliminary, not final.**
The Phase 3 system structure ADR committed a structural pattern (modular
monolith, microservices, hybrid). This step identifies the natural module
boundaries that pattern implies — at a thinking level. Step 07 enumeration
formalizes them. Do not produce the final manifest here. Produce the
thinking that Step 07 will formalize.

**Inventory API protocols explicitly.**
The interaction patterns ADR from Phase 3 committed an interaction
approach. This step inventories the specific protocols: REST, gRPC,
event-based messaging, GraphQL, WebSockets, or others. The inventory
determines which conditional API contract prompts (Steps 10–13) this
project runs. Be specific — "the system uses REST for external APIs and
event-based messaging for internal async communication" tells the
practitioner to run Step 10 and Step 12.

**Scope each cross-cutting framework's depth.**
Not every project needs the same framework depth. A regulated healthcare
system needs a deep security framework; an internal tool needs a lighter
one. This step scopes each framework's depth based on the Phase 3 design
direction and the project character. A framework scoped as "light" is
still produced — the depth scales, not the existence.

**Surface open Phase 3 questions.**
The Phase 3 design direction locked strategic direction but may have left
architectural questions open. The observability strategy ADR may have
deferred specific hook placement to Phase 4. The security model ADR may
have deferred specific authorization model selection. Surface these open
questions so the Stage 1 frameworks and module specifications resolve them.

**Determine the minimum viable path.**
This project does not run all sixteen prompts identically. The twelve
mandatory prompts always run. The conditional API contract prompts
(Steps 10–13) run only for protocols the project uses. This step declares
which conditional prompts apply and which do not, so the practitioner
knows the project's path through the toolkit.

**Defer Phase 5 work explicitly.**
Actual code, deployment scripts, configurations, implementation patterns
— all Phase 5 work. This step names them as deferred so they do not creep
into Phase 4. The architecture specifies; Phase 5 implements.

**Surface Phase 3 tensions the architecture will face.**
If the Phase 3 package contains tensions the architecture will amplify —
a benchmark that is aggressive for the committed structure, a compliance
constraint that conflicts with the deployment model, a cost envelope that
is tight for the module count implied — flag them. They shape which
architectural decisions carry the most risk.

---

## Clarification Step

Before producing the artifact, read the Phase 3 package thoroughly. Then
ask between **3 and 7 clarifying questions**, never more. Questions must
fall into these categories:

1. **API protocol inventory.** If the Phase 3 interaction patterns ADR
   committed an interaction approach but did not enumerate specific
   protocols, ask which protocols the project uses. This is the most
   important clarification because it determines which conditional
   prompts run.

2. **Team structure for governance.** The governance model (Step 06)
   needs to know the team structure — how many people, what roles, who
   owns what. If the Phase 3 package does not establish this, ask.

3. **Module boundary judgment.** If the Phase 3 system structure ADR
   implies multiple plausible module decompositions, ask the
   practitioner's judgment on the natural boundaries — without producing
   the final manifest (that is Step 07).

4. **Cross-cutting framework depth.** If the project character suggests
   a framework should be deep or light and the Phase 3 package is
   ambiguous, ask. For example, "the compliance constraints suggest a
   deep security framework — confirm?"

5. **Open Phase 3 question prioritization.** If Phase 3 left multiple
   architectural questions open, ask which the practitioner considers
   highest-priority for Phase 4 to resolve.

Do not ask the practitioner to produce module specifications — that is
Step 08. Do not ask for cross-cutting framework content — that is Steps
02–06. Do not ask the practitioner to enumerate the final module set —
that is Step 07.

Ask questions one at a time, waiting for an answer before asking the
next. After all clarifications are received, produce the full
Specification in a single response.

---

## Kickoff

> Paste the Phase 3 package (Design Direction + ADRs, Scorecard, Update
> Protocol, Observability Hooks, Compliance Constraints) above this line,
> then paste this line to trigger the prompt.

```
The Phase 3 package is pasted above. Please read it thoroughly, then ask
your clarifying questions one at a time — beginning with the API protocol
inventory — before producing the Architecture Exploration Specification.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.
Mark any section requiring practitioner input as `[REQUIRES PRACTITIONER
INPUT]` and list it in the gap register.

```markdown
# Architecture Exploration Specification
# Phase 4 Step 01 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Artifact Date:** [date]
**Produced By:** [AI model and version]
**Practitioner:** [name or role]
**Based On:**
- Phase 3 Design Direction Document + ADRs dated [date] (v[NN])
- Phase 3 Principle Scorecard baseline dated [date] (v1.0)
- Phase 3 Scorecard Update Protocol dated [date]
- Phase 3 Observability Hooks Handoff dated [date]
- Phase 3 Compliance Design Constraints dated [date]
- Phase 2 package dated [date] (if referenced)
- Phase 1 Information Report dated [date] (if referenced)

**Artifact Status:** [Draft / Reviewed / Approved]

---

## 1. Executive Summary

[5–7 sentences covering: the committed design direction from Phase 3 the
architecture builds on, the preliminary module count and boundary
approach, the API protocols in use, the cross-cutting framework depths,
the highest-priority open Phase 3 questions, and this project's path
through the sixteen-prompt toolkit. End with one line stating that the
Stage 1 frameworks and Stage 2 module specifications will be produced
against this scope.]

---

## 2. Committed Foundation From Phase 3

The Phase 3 commitments that constrain Phase 4 architectural work.

### 2.1 The Six Locked Design Dimensions

| Dimension | Committed Direction | ADR Reference |
|-----------|--------------------|--------------| 
| System Structure | | Phase 3 ADR-[NNNN] |
| Interaction Patterns | | Phase 3 ADR-[NNNN] |
| Data Architecture | | Phase 3 ADR-[NNNN] |
| Deployment Model | | Phase 3 ADR-[NNNN] |
| Security Model | | Phase 3 ADR-[NNNN] |
| Observability Strategy | | Phase 3 ADR-[NNNN] |

### 2.2 Principle Weighting (Carried Forward)

| Principle | Weight | Source |
|-----------|--------|--------|
| Security | | Phase 2 Step 01 §B.3 (via Phase 3) |
| Maintainability | | |
| Economics | | |
| Operations | | |
| Scoring & Metrics | | |
| Correctness Verification | | |
| **Total** | **100** | |

### 2.3 Principle Scorecard Baseline Reference

| Principle | Phase 3 Current | Phase 3 Target | Gap |
|-----------|-----------------|----------------|-----|
| Security | | | |
| Maintainability | | | |
| Economics | | | |
| Operations | | | |
| Scoring & Metrics | | | |
| Correctness Verification | | | |

[Phase 4 will update this to v2.0 in Step 14. The architecture should
close gaps where possible and must not regress without documented
acceptance.]

### 2.4 Key Phase 3 Inputs to Phase 4

| Input | Relevance to Phase 4 |
|-------|---------------------|
| Observability Hooks Handoff | Module monitoring hooks, observability architecture |
| Compliance Design Constraints | Security framework, module security sections, data framework |
| Design ADRs | Strategic foundation for all architectural decisions |

---

## 3. Preliminary Module Boundary Thinking

The natural module boundaries the Phase 3 system structure ADR implies,
at a thinking level. **Step 07 enumeration formalizes these into a
manifest with strategic interface contracts. This section is preliminary
thinking, not the final manifest.**

### 3.1 Structural Pattern

| Field | Value |
|-------|-------|
| Committed structural pattern | [From Phase 3 system structure ADR — modular monolith / microservices / hybrid] |
| Implication for module boundaries | [How the pattern shapes the natural decomposition] |

### 3.2 Preliminary Module Candidates

| Candidate Module | Preliminary Purpose | Core or Supporting | Notes |
|------------------|--------------------|--------------------| ------|
| [Candidate name] | [What it appears to do] | [Core to value proposition / Supporting infrastructure] | [Boundary considerations] |

### 3.3 Preliminary Inter-Module Relationships

[The relationships between candidate modules at a thinking level. Step 07
formalizes these into strategic interface contracts.]

| Module A | Module B | Relationship | Communication Pattern |
|----------|----------|--------------|----------------------|
| | | [Depends on / Provides to / Coordinates with] | [Synchronous / Asynchronous / Event-driven] |

### 3.4 Boundary Risk Notes

[Which module boundaries carry the most risk if drawn wrongly. High-risk
boundaries warrant the most careful treatment in Step 07 enumeration and
Step 08 specification.]

---

## 4. API Protocol Inventory

The protocols the project uses, determining which conditional API contract
prompts (Steps 10–13) run.

| Protocol | Used? | Boundaries Using It | API Contract Prompt |
|----------|-------|--------------------| -------------------|
| REST / OpenAPI | [Yes / No] | [Which boundaries] | Step 10 |
| gRPC / Protobuf | [Yes / No] | | Step 11 |
| Event-based messaging | [Yes / No] | | Step 12 |
| Other (GraphQL / WebSockets / MQTT / AMQP / custom) | [Yes / No] | [Which protocol, which boundaries] | Step 13 |

### Protocol Notes

[Any protocol-specific considerations — versioning needs, why a protocol
was chosen for a specific boundary, interaction with the Phase 3
interaction patterns ADR.]

---

## 5. Cross-Cutting Framework Scope

Which Stage 1 frameworks the project needs and at what depth. All five are
mandatory; depth scales with project character.

| Framework | Step | Depth | Rationale |
|-----------|------|-------|-----------|
| Shared Architectural Patterns | 02 | [Deep / Standard / Light] | [Why this depth] |
| Security Architecture Framework | 03 | [Deep / Standard / Light] | [Driven by compliance constraints, threat profile] |
| Data Architecture Framework | 04 | [Deep / Standard / Light] | [Driven by data complexity, classification] |
| Documentation Strategy | 05 | [Deep / Standard / Light] | [Driven by team size, lifecycle horizon] |
| Governance Model | 06 | [Deep / Standard / Light] | [Driven by team structure] |

### Framework Scope Notes

[For each framework scoped as Deep, brief note on what drives the depth.
For each scoped as Light, brief note confirming the lightness is
appropriate, not a shortcut.]

---

## 6. Open Phase 3 Questions for Phase 4 to Resolve

Architectural questions the Phase 3 design direction raised but did not
answer. Each is assigned to the Phase 4 step that resolves it.

| Question | Phase 3 Source | Phase 4 Step That Resolves It | Priority |
|----------|---------------|-------------------------------|----------|
| [E.g., Which authorization model — RBAC, ABAC, capability-based?] | Phase 3 security model ADR | Step 03 Security Framework | [High / Med / Low] |

---

## 7. This Project's Minimum Viable Path

Which of the sixteen prompts this project runs.

### 7.1 Mandatory Prompts (always run)

| Step | Prompt | Notes for This Project |
|------|--------|------------------------|
| 01 | Architecture Exploration Specification | This artifact |
| 02 | Shared Architectural Patterns | Depth: [from §5] |
| 03 | Security Architecture Framework | Depth: [from §5] |
| 04 | Data Architecture Framework | Depth: [from §5] |
| 05 | Documentation Strategy | Depth: [from §5] |
| 06 | Governance Model | Depth: [from §5] |
| 07 | Module Enumeration | ~[N] modules expected |
| 08 | Module Specification | Runs ~[N] times |
| 09 | Cross-Module Consistency | |
| 14 | Scorecard Update | Produces v2.0 |
| 15 | Architecture Review | |
| 16 | Phase 4 Readiness Review | |

### 7.2 Conditional Prompts (run per protocol inventory)

| Step | Prompt | Applies? | Reason |
|------|--------|----------|--------|
| 10 | API Contracts: REST | [Yes / No] | [Per §4] |
| 11 | API Contracts: gRPC | [Yes / No] | [Per §4] |
| 12 | API Contracts: Events | [Yes / No] | [Per §4] |
| 13 | API Contracts: Other | [Yes / No] | [Per §4 — which protocol] |

### 7.3 Total Prompt Executions Expected

[Approximate count: 12 mandatory + applicable conditional API contract
prompts + (N−1) additional Step 08 executions for N modules. State the
expected total so the practitioner can plan effort.]

---

## 8. Architectural Risk Concentration

Where the architectural work carries the most risk, driving analytical
depth in subsequent steps.

| Risk Area | Risk Level | Driving Factor | Steps Most Affected |
|-----------|-----------|----------------|---------------------|
| [E.g., Module boundary for compliance-sensitive data] | [Critical / High / Med / Low] | [Phase 3 compliance constraints] | Step 07, Step 08, Step 03 |

---

## 9. Phase 3 Tensions the Architecture Will Face

Tensions inherited from Phase 3 that shape architectural decisions.

| Tension | Phase 3 Source | Architectural Implication |
|---------|---------------|--------------------------|
| | | |

---

## 10. Out-of-Scope Items

Phase 5 implementation concerns explicitly deferred.

| Item | Phase Where It Belongs | Deferral Rationale |
|------|----------------------|--------------------|
| Actual module code | Phase 5 | Architecture specifies; implementation builds |
| Deployment scripts and IaC | Phase 5 | Deployment architecture specified here; scripts are implementation |
| Concrete configurations | Phase 5 | Configuration strategy specified here; values are implementation |
| Test code | Phase 5 | Test strategy specified here; test code is implementation |
| Monitoring configurations | Phase 5 / Phase 7 | Monitoring hooks specified here; configurations are implementation/operations |
| [Project-specific deferrals] | | |

---

## 11. Cross-Artifact Consistency Check

| Check | Status | Notes |
|-------|--------|-------|
| Preliminary module boundaries trace to Phase 3 system structure ADR | [Yes / No] | |
| API protocol inventory traces to Phase 3 interaction patterns ADR | | |
| Cross-cutting framework depths reflect Phase 3 design direction | | |
| Open Phase 3 questions are assigned to resolving Phase 4 steps | | |
| Minimum viable path is consistent with protocol inventory | | |
| No final manifest produced (Step 07's role) | | |
| No framework content produced (Steps 02–06's role) | | |
| No Phase 5 implementation content present | | |

---

## 12. Gap Register

| Gap ID | Section | Input Needed | Blocks Which Step |
|--------|---------|--------------|-------------------|
| | | | |

---

## 13. Confidence Summary

| Section | Confidence | Basis |
|---------|-----------|-------|
| Module boundary thinking | [H/M/L] | |
| API protocol inventory | [H/M/L] | |
| Framework scope | [H/M/L] | |
| Open question identification | [H/M/L] | |
| Minimum viable path | [H/M/L] | |

**Overall specification confidence:** [H/M/L]
**Lowest-confidence area:** [name and explain]

---

## 14. Revision Protocol

| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline Specification | |

---

## 15. Handoff Status

- [ ] Preliminary module boundary thinking is grounded in the Phase 3
      system structure ADR
- [ ] API protocol inventory is complete and determines conditional
      prompt applicability
- [ ] All five cross-cutting frameworks are scoped with depth and
      rationale
- [ ] Open Phase 3 questions are identified and assigned to resolving
      steps
- [ ] Minimum viable path is declared (mandatory + applicable conditional)
- [ ] Architectural risk concentration is identified
- [ ] Out-of-scope items are listed with deferral rationale
- [ ] No final manifest, framework content, or implementation content
      present
- [ ] Cross-artifact consistency check passes

**Status:** [Ready for Step 02 / Gaps require resolution first / Blocked]
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] The six locked Phase 3 design dimensions are carried forward with
      ADR references
- [ ] Preliminary module boundary thinking is present but does NOT
      produce the final manifest (that is Step 07)
- [ ] Module candidates are classified core vs. supporting
- [ ] API protocol inventory explicitly states which protocols are used,
      determining which of Steps 10–13 apply
- [ ] All five cross-cutting frameworks are scoped with a depth (Deep /
      Standard / Light) and rationale — none omitted
- [ ] A framework scoped as Light is confirmed appropriate, not a shortcut
- [ ] Open Phase 3 questions are surfaced and each is assigned to the
      Phase 4 step that resolves it
- [ ] The minimum viable path declares mandatory prompts and applicable
      conditional prompts explicitly
- [ ] Total expected prompt executions are estimated so the practitioner
      can plan effort
- [ ] Architectural risk concentration drives analytical depth guidance
      for subsequent steps
- [ ] Phase 3 tensions the architecture will face are surfaced
- [ ] Out-of-scope items are listed with named phase and deferral
      rationale
- [ ] No cross-cutting framework content, no module specifications, no
      API contracts, no implementation content present
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 01 of 16 in the Phase 4 Architecture & Modular Design Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `architecture-modular-design.instructions.md`*
*Next step: `step-02-shared-architectural-patterns.prompt.md`*