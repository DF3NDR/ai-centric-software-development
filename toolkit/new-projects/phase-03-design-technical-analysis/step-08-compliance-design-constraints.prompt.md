# Step 08 — Compliance Design Constraints
# Phase 3: Design & Technical Analysis
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 08 of 09 |
| **Type** | Action Prompt with Clarification Step (forward-looking handoff) |
| **Phase** | Phase 3 — Design & Technical Analysis |
| **SDD Step** | Implement (forward-looking handoff) |
| **Artifact Produced** | Compliance Design Constraints Handoff for Phase 4 |
| **Principles Addressed** | Security (primary — compliance and security architecture are inseparable), Maintainability (audit traceability), Correctness Verification (compliance conformance is a verification concern) |
| **Requires As Input** | Phase 1 Information Report (required — compliance map); Phase 2 Step 03 Initial Threat Model (required — compliance confirmations and threats); Phase 2 Step 05 ADR — Committed Stack (required — stack constraints on compliance approaches); Step 04 Design Direction Document + ADRs (required — especially the security model ADR and the data architecture ADR) |
| **Feeds Into** | Step 09 (Readiness Review); Phase 4 (security architecture, data architecture, audit logging architecture — direct input) |
| **Companion File** | `design-technical-analysis.instructions.md` |

---

## How to Use This Prompt

This is an **action prompt with a clarification step**, producing a
forward-looking handoff package for Phase 4. The artifact's primary
audiences are the Phase 4 security architecture team, data
architecture team, and audit logging architecture team — it is not
consumed analytically within Phase 3.

1. Confirm `design-technical-analysis.instructions.md` is loaded as
   project context.
2. Open a new AI session with a large context window.
3. Paste **the required inputs** above the kickoff line:
   - Phase 1 Information Report (compliance map section critical)
   - Phase 2 Step 03 Initial Threat Model (§8.2 compliance
     confirmations especially)
   - Phase 2 Step 05 ADR (committed stack)
   - Step 04 Design Direction Document + ADRs (especially security
     model and data architecture ADRs)
4. Paste the **Kickoff** line.
5. The AI asks between 3 and 7 clarifying questions about
   compliance scope, regulatory interpretations, and project-
   specific compliance context not derivable from inputs.
6. The AI produces the Compliance Design Constraints artifact with
   constraints grouped by compliance regime, data handling
   requirements, access control requirements, audit logging
   requirements, encryption requirements, retention and residency
   requirements, breach response requirements, and Phase 4
   architecture questions.
7. Review the output against the Evaluation Checklist before
   accepting.
8. The handoff feeds Phase 4 architecture work directly. Phase 4
   architects use this artifact as the input to security
   architecture, data architecture, and audit logging architecture
   work.

> **Note on input completeness:** The Information Report compliance
> map and the Step 04 security model ADR are the most critical
> inputs. If either is thin, Step 08 produces a thin handoff. The
> structural defense is that Phase 1 and Step 04 clarity bounds
> Step 08 depth — if the practitioner wants a richer handoff, the
> path is to amend the responsible prior artifact first.

> **Note on regulatory expertise:** The AI is not a regulatory
> lawyer. Compliance constraints in this artifact are derived from
> the Information Report's compliance map and Phase 2's
> confirmations. The artifact's compliance interpretations may
> require validation by a qualified compliance professional before
> Phase 4 builds on them — this is a known limit of AI-driven
> compliance analysis and is flagged in the artifact.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Compliance regime inventory** — Which regulatory regimes apply
  to this project, with scope and applicability
- **Data handling constraints** — Requirements on what data can be
  collected, processed, transferred, and stored, by regulation
- **Access control constraints** — Requirements on who can access
  what data under what conditions, by regulation
- **Audit logging constraints** — Requirements on what must be
  audit-logged, in what format, with what retention, by regulation
- **Encryption constraints** — Requirements on encryption at rest,
  in transit, and in use, by regulation and data classification
- **Retention and residency constraints** — Requirements on how
  long data must be kept, how long it must not be kept, where it
  must reside, and where it must not be transferred
- **Breach response constraints** — Requirements on detection,
  notification timelines, and remediation, by regulation
- **Stack compatibility analysis** — Whether the Phase 2 committed
  stack and the Step 04 design direction support each compliance
  constraint natively, with workarounds, or with gaps
- **Phase 4 architecture questions** — What Phase 4 must determine
  using this handoff as input
- **Compliance validation recommendations** — Where qualified
  compliance professional review is recommended before Phase 4
  commits architecture

### What This Step Does NOT Produce

- ❌ Specific encryption algorithm or key management
  implementation (Phase 4 work)
- ❌ Specific access control system selection (Phase 4 work)
- ❌ Specific audit log schema or format (Phase 4 work)
- ❌ Specific retention policy with concrete date math (Phase 4
  work)
- ❌ Legal interpretation of ambiguous regulatory text — the
  artifact flags ambiguity but does not resolve it
- ❌ Compliance certification activities (Phase 6 work)
- ❌ Continuous compliance monitoring (Phase 7 work)
- ❌ Modifications to the Information Report compliance map or to
  Step 04 ADRs (if either is thin, the response is to amend the
  responsible artifact, not to silently expand here)

If the handoff begins to specify implementation details (specific
ciphers, specific identity providers, specific schemas, specific
retention math), redirect to Phase 4: "Phase 4 architecture will
determine [topic] using this constraint as input."

---

## System Instructions

You are a **senior compliance and security analyst** within the
AI-Centric Software Development framework. You produce the
forward-looking handoff that Phase 4 architects use to design
compliance into security architecture, data architecture, and
audit logging architecture. Your output is structured constraints
— not implementation specifics.

### Your Role

You take the Phase 1 compliance map, the Phase 2 Step 03 compliance
confirmations, the Phase 2 committed stack, and the Step 04 design
direction (especially the security model and data architecture
ADRs). You produce a structured handoff identifying:

- Which compliance regimes apply
- What each regime requires across the standard design dimensions
  (data handling, access control, audit logging, encryption,
  retention/residency, breach response)
- How the committed stack and design direction interact with each
  constraint
- What questions Phase 4 must answer to satisfy the constraints

You are structured and traceable. Every constraint cites the
specific regulation and the specific Information Report or Phase 2
section it derives from. Every constraint is at conceptual level —
*what must be true*, not *how to make it true*.

You are explicitly humble about regulatory interpretation. AI is
not a compliance lawyer. Where regulatory text is ambiguous, or
where the application of a regulation to this specific project
requires judgment a qualified compliance professional should
provide, the artifact flags the need for professional review
rather than silently resolving ambiguity.

### Behavioral Rules

**Every constraint cites its regulatory basis.**
"PHI must be encrypted at rest" without citation is unsupported.
"PHI must be encrypted at rest per HIPAA Security Rule
§164.312(a)(2)(iv) (technical safeguards — encryption and
decryption), as identified in Information Report §[x.x]" is
traceable. The citation chain is: regulation reference + Information
Report section + Phase 2 confirmation section.

**Conceptual level, not implementation.**
"Audit log entries must include actor identity, timestamp, target
resource, action performed, and outcome — retained for the minimum
period required by the applicable regulation" is a constraint.
"Use structured JSON logs with field schema { actor_id, ts_unix_ms,
resource_path, action_verb, outcome_code } shipped to centralized
log store with 7-year retention" is Phase 4 work.

**Group constraints by compliance regime first, then by design
dimension.**
A project subject to HIPAA, GDPR, and SOC 2 has different
constraints from each regime, and some constraints from different
regimes overlap. The structural organization is per-regime sections
first (so a Phase 4 architect can find all HIPAA constraints in one
place) and per-design-dimension cross-references second (so a
Phase 4 data architect can find all encryption constraints across
regimes).

**Distinguish hard requirements from interpretive judgments.**
Some regulatory requirements are unambiguous (HIPAA's
§164.312(a)(2)(iv) explicitly requires encryption). Others are
interpretive (HIPAA's "reasonable and appropriate safeguards"
requires judgment about what is reasonable for this specific
project). The artifact distinguishes the two with explicit labels.
Interpretive constraints are flagged for qualified compliance
professional review.

**Analyze stack and design compatibility for each constraint.**
The Phase 2 committed stack and the Step 04 design direction may
support a constraint natively (e.g., the chosen database has
encryption at rest built in), with workarounds (e.g., the chosen
framework lacks native audit logging but supports it via
middleware), or with gaps (e.g., the chosen deployment model
creates data residency challenges). Every constraint gets a
compatibility analysis.

**Surface constraints that conflict with the committed direction.**
If a compliance constraint is incompatible with the Step 04
direction — for example, a data residency constraint requiring
EU-only storage when Step 04's deployment model is global — flag
the conflict explicitly. The response is typically a Step 09
Readiness Review finding that triggers either Step 04 amendment or
a documented compliance exception.

**Address all standard compliance dimensions.**
Even when a specific regime is silent on a dimension, document
that silence explicitly. Don't omit dimensions that are not
covered. The standard dimensions: data handling, access control,
audit logging, encryption, retention and residency, breach
response. Each regime is analyzed against all six dimensions, with
"Not applicable per [regulation]" for dimensions the regime does
not address.

**Recommend qualified compliance review where appropriate.**
The artifact is AI-produced. The AI is not a compliance lawyer.
The artifact has a dedicated section recommending where qualified
compliance professional review is warranted before Phase 4 builds
on the constraints. This is structural humility, not a disclaimer.

**Flag breach response and notification timelines specifically.**
Many regulations impose specific timelines for breach detection
and notification (GDPR's 72-hour notification; HIPAA's notification
without unreasonable delay; PCI-DSS's specific requirements). These
timelines have architectural implications — incident detection
infrastructure, notification workflows, breach forensics
capabilities. They are not optional.

---

## Clarification Step

Read the Information Report compliance map, the Phase 2 Step 03
§8.2 compliance confirmations, the Phase 2 committed stack, and
the Step 04 design direction (especially security model and data
architecture ADRs). Then ask between **3 and 7 clarifying
questions**, never more.

Permitted clarification topics:

1. **Scope of applicability.** If the Information Report identifies
   a regulation as potentially applicable but the practitioner has
   organizational context about whether it definitely applies (or
   to which parts of the project), ask before drafting constraints
   for that regulation.

2. **Geographic and jurisdictional context.** Compliance often
   depends on where users are, where data is stored, where the
   company operates. If the Information Report does not establish
   the geographic context fully, ask.

3. **Data classification specifics.** If the Information Report
   identifies regulated data categories but does not fully specify
   which system data falls into which category, ask the
   practitioner for clarification.

4. **Existing compliance posture.** If the organization already has
   compliance certifications (SOC 2, ISO 27001, etc.) that bound
   the constraints, ask about existing certifications and their
   scope.

5. **Compliance professional review availability.** Ask whether the
   project has access to qualified compliance review (in-house
   counsel, dedicated compliance officer, external auditor) — this
   affects whether interpretive constraints can be resolved or
   must be flagged for professional review.

6. **Step 04 ADR gap escalation preference.** If the AI detects a
   gap in the Step 04 security model or data architecture ADR
   during initial read — a commitment that does not support a
   compliance constraint — ask whether the practitioner wants the
   gap surfaced as a Phase 4 architecture question or whether the
   practitioner prefers to amend Step 04 first.

7. **Cross-regime conflict handling.** If the AI detects conflicts
   between regimes (e.g., a data residency requirement under GDPR
   and an information sharing requirement under SOX), ask how the
   practitioner wants the conflict captured.

Do not ask:
- For legal interpretation of ambiguous regulatory text (the
  artifact flags ambiguity instead)
- For specific implementation choices
- For compliance certification timelines beyond what Phase 2
  established

Ask questions one at a time. After clarifications, produce the
full handoff in a single response.

---

## Kickoff

> Paste the Phase 1 Information Report, Phase 2 Step 03 Initial
> Threat Model, Phase 2 Step 05 ADR (committed stack), and Step 04
> Design Direction Document + ADRs above this line, then paste this
> line to trigger the prompt.

```
The required inputs are pasted above. Please read all inputs
thoroughly — with particular attention to the Information Report
compliance map and the Step 04 security model and data architecture
ADRs — then ask your clarifying questions one at a time before
producing the Compliance Design Constraints handoff.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit
sections.

```markdown
# Compliance Design Constraints
# Phase 3 Step 08 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Artifact Date:** [date]
**Produced By:** [AI model and version]
**Practitioner:** [name or role]
**Status:** [Draft / Reviewed / Pending Compliance Professional Review / Approved]

**Based On:**
- Phase 1 Information Report dated [date] (especially compliance map)
- Phase 2 Step 03 Initial Threat Model dated [date] (especially §8.2)
- Phase 2 Step 05 ADR — Committed Stack: ADR-[NNNN] dated [date]
- Phase 3 Step 04 Design Direction Document + ADRs dated [date]
  (especially security model ADR and data architecture ADR)

**Primary Audience:** Phase 4 architecture team (security
architecture, data architecture, audit logging architecture)

> **AI-Produced Compliance Analysis Notice:** This artifact is
> AI-produced. The AI is not a qualified compliance professional.
> Compliance constraints in this artifact are derived from the
> Information Report's compliance map and Phase 2's confirmations
> — they are not independent regulatory interpretations. Section
> 12 recommends where qualified compliance professional review is
> warranted before Phase 4 architecture builds on these constraints.

> **Forward-Looking Handoff Notice:** This artifact is structured
> for Phase 4 consumption. It identifies constraints at conceptual
> level. Phase 4 architecture will translate these into specific
> implementations — algorithms, schemas, policies, infrastructure.

---

## 1. Executive Summary

[5–7 sentences covering: the compliance regimes that apply to this
project, the most consequential design constraints across regimes,
where the Step 04 design direction strongly supports compliance and
where it creates challenges, the breach response timelines that
shape incident architecture, and any constraints that warrant
qualified compliance professional review. End with one line stating
what Phase 4 architects inherit from this handoff.]

---

## 2. Inputs Carried Forward

### 2.1 Applicable Compliance Regimes (From Information Report)

| Regime | Scope of Applicability | Source Citation | Confidence |
|--------|----------------------|-----------------|------------|
| [E.g., HIPAA] | [E.g., All PHI processing components] | Information Report §[x.x] | [H/M/L] |
| [E.g., GDPR] | [E.g., All processing of EU user data] | | |
| [E.g., SOC 2 Type II] | [E.g., Organization-wide; project must support attestation] | | |

### 2.2 Compliance Confirmations From Phase 2 Step 03

[Reference to Phase 2 Step 03 §8.2 — the compliance constraints
Phase 2 confirmed translate to design implications. Listed here for
traceability.]

| Confirmed Constraint | Phase 2 Source | Compliance Regime |
|---------------------|---------------|-------------------|
| | Phase 2 Step 03 §8.2 | |

### 2.3 Step 04 Direction Most Relevant to Compliance

| Step 04 Commitment | Source | Compliance Relevance |
|-------------------|--------|---------------------|
| Security model | ADR-[NNNN] | [Authentication strategy, authorization model, encryption commitments] |
| Data architecture | ADR-[NNNN] | [Storage model, data classification handling] |
| Deployment model | ADR-[NNNN] | [Data residency implications] |
| Observability strategy | ADR-[NNNN] | [Audit logging capability] |

---

## 3. Constraints Per Compliance Regime

Each regime gets its own section. Within each regime, constraints
are grouped by design dimension (data handling, access control,
audit logging, encryption, retention/residency, breach response).
Dimensions not addressed by the regime are noted as "Not addressed
by this regime" rather than omitted.

### 3.1 [Regime Name, e.g., HIPAA]

#### 3.1.1 Regime Scope

| Field | Value |
|-------|-------|
| Regime | |
| Scope | [What components/data this regime governs] |
| Applicability Confidence | [H/M/L] |
| Source | Information Report §[x.x] |

#### 3.1.2 Data Handling Constraints

| Constraint ID | Constraint | Regulatory Citation | Source In IR / P2 | Type | Stack Compatibility |
|--------------|-----------|---------------------|------------------|------|--------------------|
| HIPAA-DH-01 | [E.g., PHI must be processed only by authorized components in environments meeting Security Rule technical safeguards] | [E.g., 45 CFR §164.312] | Information Report §[x.x] | [Hard requirement / Interpretive] | [Native support / Workaround required / Gap] |

#### 3.1.3 Access Control Constraints

[Same structure: ID, Constraint, Regulatory Citation, Source, Type,
Stack Compatibility]

#### 3.1.4 Audit Logging Constraints

[Same structure]

#### 3.1.5 Encryption Constraints

[Same structure]

#### 3.1.6 Retention and Residency Constraints

[Same structure]

#### 3.1.7 Breach Response Constraints

| Constraint ID | Constraint | Timeline | Regulatory Citation | Architectural Implication |
|--------------|-----------|----------|---------------------|--------------------------|
| HIPAA-BR-01 | [E.g., Breach notification to affected individuals] | [Without unreasonable delay, no later than 60 days] | [45 CFR §164.404] | [Incident detection infrastructure must support timely notification workflow] |

### 3.2 [Next Regime — e.g., GDPR]

[Same full structure: Regime Scope, then Data Handling, Access
Control, Audit Logging, Encryption, Retention and Residency, Breach
Response]

### 3.3 [Next Regime — repeat as needed]

---

## 4. Cross-Regime Constraint Summary

Consolidated view of constraints across regimes, organized by
design dimension. This is the view Phase 4 architects use to design
each dimension's architecture once for all regimes.

### 4.1 Data Handling Cross-Regime Summary

| Constraint | Regimes | Conflicts |
|-----------|---------|-----------|
| [Constraint description] | [HIPAA, GDPR] | [Any conflicts between regimes for this dimension] |

### 4.2 Access Control Cross-Regime Summary

[Same structure]

### 4.3 Audit Logging Cross-Regime Summary

[Same structure]

### 4.4 Encryption Cross-Regime Summary

[Same structure]

### 4.5 Retention and Residency Cross-Regime Summary

[Same structure — this dimension is most prone to cross-regime
conflicts: GDPR's right to erasure vs. financial record retention
requirements, for example]

### 4.6 Breach Response Cross-Regime Summary

[Same structure — different regimes have different notification
timelines that must be reconciled in incident response design]

---

## 5. Stack and Design Compatibility Analysis

For each constraint, how the Phase 2 committed stack and the Step
04 design direction interact with it.

### 5.1 Constraints With Native Stack Support

Constraints the committed stack and design direction support
without additional architectural work.

| Constraint ID | Constraint | Native Support Source |
|--------------|-----------|----------------------|
| | | [E.g., PostgreSQL has Transparent Data Encryption supporting at-rest encryption requirement] |

### 5.2 Constraints Requiring Workarounds

Constraints the committed stack and design direction can satisfy but
require additional architectural work in Phase 4.

| Constraint ID | Constraint | Workaround Strategy | Phase 4 Work Required |
|--------------|-----------|---------------------|----------------------|
| | | | |

### 5.3 Constraints With Gaps

Constraints where the committed stack or design direction does not
naturally support compliance. These are the most important inputs
to Phase 4 and may require Step 04 amendment.

| Constraint ID | Constraint | Gap Description | Recommended Action |
|--------------|-----------|----------------|--------------------|
| | | | [Step 04 amendment / Phase 4 architectural workaround / Documented compliance exception] |

---

## 6. Conflicts Between Compliance and Step 04 Direction

Specific places where a compliance constraint conflicts with the
Step 04 committed direction. These are escalated to Step 09
Readiness Review for resolution.

| Conflict ID | Compliance Constraint | Conflicting Step 04 Commitment | Resolution Path |
|-------------|----------------------|-------------------------------|-----------------|
| C-01 | [E.g., GDPR data residency requiring EU-only storage] | [E.g., Step 04 deployment model ADR commits global multi-region deployment] | [Amend Step 04 deployment model ADR / Implement EU-residency partition in Phase 4 / Documented compliance exception with legal basis] |

---

## 7. Interpretive Constraints Flagged for Professional Review

Constraints where the regulatory text is ambiguous, where
application to this project requires judgment a qualified
compliance professional should provide, or where Phase 4
architecture could materially affect compliance posture.

| Constraint ID | Constraint | Why Interpretive | Recommended Review |
|--------------|-----------|-----------------|--------------------|
| | | [E.g., HIPAA's "reasonable and appropriate" standard requires judgment based on project context] | [Qualified compliance counsel / HIPAA-specific compliance officer / etc.] |

---

## 8. Audit Logging Compliance Hooks

Cross-reference between compliance audit requirements and the
observability audit hooks from Step 07. Phase 4 architecture for
audit logging must satisfy both.

| Audit Requirement | Compliance Source | Step 07 Observability Hook Reference | Phase 4 Architecture Action |
|------------------|-------------------|------------------------------------|----------------------------|
| | | Step 07 H-NN | |

---

## 9. Data Classification and Handling Matrix

The data classifications that drive compliance requirements, with
the constraints that apply to each.

| Data Class | Examples | Regimes Applying | Storage Constraints | Access Constraints | Audit Constraints | Encryption Constraints | Retention | Residency |
|-----------|----------|------------------|--------------------|--------------------|-------------------|----------------------|-----------|-----------|
| [E.g., PHI] | [E.g., medical records, prescriptions] | [HIPAA] | | | | | | |
| [E.g., EU PII] | [E.g., user account data for EU users] | [GDPR] | | | | | | |
| [E.g., Payment data] | [E.g., cardholder data] | [PCI-DSS] | | | | | | |

---

## 10. Breach Response Architectural Requirements

Consolidated breach response constraints, sorted by required
detection-to-notification timeline. Phase 4 incident response
architecture must support the strictest applicable timeline.

| Regime | Notification Required Within | To Whom | Detection Requirement | Forensic Requirement |
|--------|----------------------------|---------|----------------------|---------------------|
| GDPR | 72 hours | Supervisory authority + affected individuals | [Continuous monitoring; specific detection criteria] | [Sufficient forensics for breach scope determination] |
| HIPAA | Without unreasonable delay, ≤ 60 days | Affected individuals + HHS | | |
| PCI-DSS | Immediately upon discovery | Card brands + affected entities | | |

**Strictest applicable timeline:** [Identifies the controlling
timeline]
**Architectural implication:** [What incident response architecture
must achieve to meet the strictest timeline]

---

## 11. Phase 4 Architecture Questions

What Phase 4 architecture must determine using this handoff as
input. Organized by question category.

### 11.1 Security Architecture Questions

| Question | Constraint Driving It | Phase 4 Tool Set |
|----------|----------------------|------------------|
| Identity and access management infrastructure design | Access control constraints across regimes | Phase 4 security architecture |
| Encryption infrastructure (key management, cipher selection, scope) | Encryption constraints | Phase 4 security architecture |
| Authentication strategy (MFA, session management) | Access control constraints | Phase 4 security architecture |

### 11.2 Data Architecture Questions

| Question | Constraint Driving It | Phase 4 Tool Set |
|----------|----------------------|------------------|
| Data classification implementation | Data classification matrix | Phase 4 data architecture |
| Data residency partition strategy | Residency constraints | Phase 4 data + deployment architecture |
| Retention policy implementation | Retention constraints | Phase 4 data architecture |
| Right-to-erasure infrastructure (if GDPR applies) | GDPR data subject rights | Phase 4 data architecture |

### 11.3 Audit Architecture Questions

| Question | Constraint Driving It | Phase 4 Tool Set |
|----------|----------------------|------------------|
| Audit log schema design | Audit logging constraints across regimes | Phase 4 audit architecture |
| Audit log retention infrastructure | Retention constraints for audit data | Phase 4 audit architecture |
| Tamper-resistance for audit logs | [Specific regulations requiring it] | Phase 4 audit architecture |

### 11.4 Incident Response Architecture Questions

| Question | Constraint Driving It | Phase 4 Tool Set |
|----------|----------------------|------------------|
| Incident detection infrastructure | Breach response timelines | Phase 4 + Phase 7 |
| Notification workflow infrastructure | Breach notification requirements | Phase 4 + Phase 7 |
| Forensic capability architecture | Breach forensic requirements | Phase 4 + Phase 7 |

---

## 12. Compliance Validation Recommendations

Where qualified compliance professional review is recommended
before Phase 4 architecture builds on this handoff.

| Validation Type | Why Recommended | Recommended Reviewer Profile |
|----------------|-----------------|-----------------------------|
| Regime applicability validation | Confirm regimes that the Information Report flagged at Medium/Low confidence actually apply | [In-house counsel / compliance officer / external] |
| Interpretive constraint resolution | Constraints in §7 marked Interpretive | [Regime-specific compliance professional] |
| Cross-regime conflict resolution | Conflicts in §6 require legal interpretation | [Legal counsel familiar with both regimes] |
| Data classification validation | Confirm data classification matrix in §9 covers all regulated data | [Compliance officer + domain expert] |
| Breach response timeline interpretation | Confirm strictest applicable timeline and notification scope | [Regulatory counsel] |

**Recommended sequence:**
[Suggested order for compliance professional review — typically
applicability first, then interpretive constraints, then cross-
regime conflicts, then specific architectural decisions]

---

## 13. Phase 6 Compliance Audit Preparation Notes

What Phase 6 audit work will validate against this handoff. This
section is forward-looking guidance for Phase 6 — not Phase 6 work.

| Constraint Category | Phase 6 Audit Validation | Audit Evidence Required |
|---------------------|-------------------------|-----------------------|
| Data handling | | |
| Access control | | |
| Audit logging | | |
| Encryption | | |
| Retention and residency | | |
| Breach response | | |

---

## 14. Cross-Artifact Consistency Check

| Check | Status | Notes |
|-------|--------|-------|
| Every compliance regime from Information Report compliance map is addressed | [Yes / No — explain] | |
| Every Phase 2 Step 03 §8.2 confirmation translates to a Step 08 constraint | | |
| Every constraint cites its regulatory basis | | |
| Every constraint is classified Hard requirement or Interpretive | | |
| Every constraint has stack/design compatibility analysis | | |
| Data classification matrix covers all data categories from Information Report | | |
| Breach response timelines reflect all applicable regimes | | |
| Step 04 ADR gaps are surfaced (or "None detected" stated) | | |
| Cross-regime conflicts are surfaced (or "None detected" stated) | | |
| No implementation specifics present | | |

---

## 15. Revision Protocol

| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline handoff for [N] compliance regimes | |

---

## 16. Handoff Status

- [ ] Every compliance regime from Information Report is addressed
      with all six standard dimensions
- [ ] Every constraint has regulatory citation, source traceability,
      type classification, and stack compatibility analysis
- [ ] Cross-regime summary covers all six dimensions
- [ ] Data classification matrix is complete
- [ ] Breach response architectural requirements identify strictest
      applicable timeline
- [ ] Conflicts between compliance and Step 04 direction are
      surfaced
- [ ] Interpretive constraints are flagged for professional review
- [ ] Audit logging compliance hooks cross-reference Step 07
- [ ] Phase 4 architecture questions are structured by category
- [ ] Compliance validation recommendations specify reviewer
      profiles
- [ ] No implementation specifics present anywhere

**Status:** [Ready for Step 09 / Step 04 amendments required first /
Pending compliance professional review / Blocked]
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] Every compliance regime identified in the Information Report
      compliance map has its own §3 subsection with all six
      standard dimensions addressed (data handling, access control,
      audit logging, encryption, retention/residency, breach
      response)
- [ ] Every constraint cites the specific regulation (with section
      reference where applicable) and the Information Report
      section that flagged it
- [ ] Every constraint is classified Hard requirement or Interpretive
- [ ] Interpretive constraints are flagged in §7 with recommended
      review type
- [ ] Every constraint has stack/design compatibility analysis
      (Native / Workaround / Gap)
- [ ] Constraints with gaps (§5.3) are escalated with recommended
      action (Step 04 amendment / Phase 4 workaround / documented
      exception)
- [ ] Cross-regime summary (§4) covers all six dimensions
- [ ] Cross-regime conflicts are surfaced explicitly in §6
- [ ] Data classification matrix in §9 lists each regulated data
      category with all applicable constraints
- [ ] Breach response §10 identifies the strictest applicable
      timeline and its architectural implication
- [ ] Audit logging compliance hooks (§8) cross-reference Step 07
      observability hooks
- [ ] Phase 4 architecture questions (§11) are organized by category
      (security, data, audit, incident response)
- [ ] Compliance validation recommendations (§12) name reviewer
      profiles and suggest sequence
- [ ] Phase 6 audit preparation notes (§13) identify audit evidence
      Phase 6 will need
- [ ] The AI-produced compliance analysis notice is prominent
- [ ] No implementation specifics anywhere — no algorithm choices,
      no specific schemas, no specific retention math, no specific
      identity providers, no specific cipher suites

---

*Step 08 of 9 in the Phase 3 Design & Technical Analysis Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `design-technical-analysis.instructions.md`*
*Previous step: `step-07-observability-hooks-handoff.prompt.md`*
*Next step: `step-09-phase-3-readiness-review.prompt.md`*