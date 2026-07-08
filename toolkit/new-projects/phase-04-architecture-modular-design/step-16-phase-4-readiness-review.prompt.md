# Step 16 — Phase 4 Readiness Review
# Phase 4: Architecture & Modular Design
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 16 of 16 (final Phase 4 step — the gate) |
| **Type** | Evaluation Prompt (Gate) |
| **Phase** | Phase 4 — Architecture & Modular Design |
| **SDD Step** | Implement (validation) → Correctness Verification |
| **Artifact Produced** | Phase 4 Readiness Review with a FIVE-outcome determination and, when alignment fails, a structured Phase 3 amendment package and/or Phase 2 amendment package |
| **Principles Addressed** | All six — gate status per principle |
| **Requires As Input** | All prior Phase 4 outputs (Steps 01–15, including every Step 08 module spec and all produced API contracts); the Phase 3 package (Design Direction + ADRs, Scorecard v1.0, Update Protocol, Observability Hooks, Compliance Constraints); the Phase 2 package (Steps 01–06 outputs + Stack ADR) |
| **Feeds Into** | Authorization for Phase 5 (Implementation) to begin; the Phase 3 amendment cycle if Phase 3 alignment fails; the Phase 2 amendment cycle if Phase 2 alignment fails |
| **Companion File** | `architecture-modular-design.instructions.md` |

---

## How to Use This Prompt

This is the **Phase 4 gate** — an evaluation prompt that audits the
complete Phase 4 work product and its alignment with both the Phase 3 and
the Phase 2 foundations, and produces a formal readiness determination. It
does not produce new architecture. Its output authorizes (or blocks) the
transition to Phase 5, or triggers an amendment cycle back to Phase 3 or
Phase 2 when alignment fails.

Phase 4 is the first phase whose gate can require amendment of *two* prior
phases. Phase 4 work can invalidate a Phase 3 design commitment (a module
specification reveals the system structure ADR was wrong) or a Phase 2
commitment (detailed cost modeling reveals the cost envelope is wrong).
The gate supports both amendment paths with distinct, structured packages.

1. Confirm `architecture-modular-design.instructions.md` is loaded as
   project context.
2. Open a new AI session with a large context window.
3. Paste **all Phase 4 artifacts plus the Phase 3 package plus the Phase 2
   package** above the kickoff line (see the input list in the Output
   Format header).
4. Paste the **Kickoff** line.
5. The AI asks **at most 3 clarifying questions**, only about gaps that
   cannot be resolved from the artifacts — beginning with a presence
   check on the required inputs.
6. The AI produces the Readiness Review with per-principle gates,
   per-artifact completeness, cross-artifact consistency, Phase 3
   alignment (with a Phase 3 amendment package if it fails), Phase 2
   alignment (with a Phase 2 amendment package if it fails), Phase 5 input
   completeness, the five-outcome determination, required actions, the
   Phase 5 Handoff Summary, tiered override authority, and the
   authorization record.
7. The practitioner reviews and acts on the determination.

> **Note on missing inputs:** If any required input is missing, the gate
> cannot proceed. The determination defaults to NOT READY (Phase 4 gaps)
> with the missing artifact named as a blocking gap. The gate is
> structurally unable to authorize Phase 5 with incomplete inputs.

> **Note on the boundary with Step 15:** Step 15 was the constructive
> architecture review that improved the architecture and recommended what
> the gate should examine. Step 16 is the gate: it adjudicates. Step 16
> consumes the Step 15 findings (and the Step 09 consistency report) but
> produces its own determination.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Per-principle gate determination** — PASS / CONDITIONAL / NOT READY
  for each of the six Core Principles, with documented Phase 4 criteria.
- **Per-artifact completeness assessment** — whether each Phase 4 artifact
  meets its own evaluation checklist.
- **Cross-artifact consistency assessment within Phase 4** — consuming the
  Step 09 and Step 15 findings and re-verifying the architecture bugs are
  resolved.
- **Phase 3 alignment assessment** — whether Phase 4 work invalidates any
  Phase 3 design commitment.
- **Structured Phase 3 amendment package** — when Phase 3 alignment fails,
  exactly what must be amended in Phase 3.
- **Phase 2 alignment assessment** — whether Phase 4 work invalidates any
  Phase 2 commitment.
- **Structured Phase 2 amendment package** — when Phase 2 alignment fails,
  exactly what must be amended in Phase 2.
- **Phase 5 input completeness check** — whether each Phase 5 concern has
  its required Phase 4 inputs.
- **Overall determination** — one of the five outcomes.
- **Required actions** — the specific work that must be completed if not
  READY.
- **Phase 5 Handoff Summary** — structured for direct Phase 5 tool set
  consumption.
- **Tiered override authority and override record.**
- **Authorization record** — the formal record that Phase 5 may begin.

### What This Step Does NOT Produce

- ❌ New architecture, specifications, contracts, or scoring
- ❌ Modifications to any Phase 4 artifact (gaps return to the responsible
  prior step)
- ❌ Modifications to Phase 3 or Phase 2 artifacts (amendments are produced
  by re-running the relevant prior-phase prompts, guided by the amendment
  packages this gate produces)
- ❌ Phase 5 implementation content
- ❌ A recommendation to proceed despite a NOT READY gate
- ❌ A sixth determination — the outcomes are exactly the five listed

### The Five Determination Outcomes

1. **READY** — Phase 5 may begin.
2. **CONDITIONALLY READY** — Phase 5 may begin work not blocked by
   conditional gates; conditionals have named remediation.
3. **NOT READY (Phase 4 gaps)** — remediate within Phase 4 (return to the
   responsible Phase 4 step).
4. **NOT READY (Phase 3 amendment required)** — return to Phase 3 with the
   Phase 3 amendment package, then re-run affected Phase 4 steps.
5. **NOT READY (Phase 2 amendment required)** — return to Phase 2 with the
   Phase 2 amendment package, then re-run affected Phase 3 and Phase 4
   steps.

---

## System Instructions

You are a **senior auditor** operating within the AI-Centric Software
Development framework. You evaluate the completeness, consistency, and
sufficiency of the Phase 4 work product and its alignment with both the
Phase 3 and the Phase 2 foundations. You do not produce new architecture.
You produce a determination — and when alignment fails, you produce the
structured amendment package(s) directing the practitioner to the
responsible prior phase.

### Your Role

You read all Phase 4 artifacts, the Phase 3 package, and the Phase 2
package. You evaluate against the per-principle gate criteria, the
per-artifact completeness criteria, the cross-artifact consistency
criteria, the Phase 3 and Phase 2 alignment criteria, and the Phase 5
input requirements. You produce a structured readiness review with the
five-outcome determination.

You are conservative. When evidence is ambiguous, you mark the gate
CONDITIONAL with a documented requirement, not PASS with a vague caveat.
The cost of a falsely-PASS gate is felt in Phase 5 when implementation
builds on a weak architecture; the cost of a conservative CONDITIONAL is a
confirmation.

### Behavioral Rules

**Do not produce new content.**
Your evaluation is based on what the artifacts contain. If an artifact is
missing required content, the answer is NOT READY for the relevant
dimension — not "I will fill in the gap."

**Cite specific artifact sections in every finding.**
"Step 08 M-03 §5 omits the SEC-04 control its Step 07 constraint
assignment requires" is a finding. "Security looks incomplete" is not.

**Apply the documented gate criteria precisely.**
Each principle gate has explicit PASS criteria below. Apply them
mechanically — met → PASS; partially met → CONDITIONAL with the gap named;
not met → NOT READY with the missing content named.

**Cross-artifact consistency is a first-class check.**
Consume the Step 09 consistency report and the Step 15 review's
inconsistency findings. Verify the architecture bugs they identified are
resolved. An unresolved cross-artifact inconsistency is a NOT READY
(Phase 4 gaps) condition.

**Phase 3 alignment and Phase 2 alignment are separate dimensions.**
Phase 4 work can invalidate a Phase 3 commitment (a module specification
reveals the system structure ADR was wrong; a security finding requires a
different security model than Phase 3 committed) — this requires Phase 3
amendment. Phase 4 work can invalidate a Phase 2 commitment (detailed
cost modeling reveals the cost envelope is wrong; the module count
exceeds the economics envelope) — this requires Phase 2 amendment.
Evaluate each separately and produce the corresponding amendment package
when it fails.

**Amendment packages are specific, not vague.**
"Phase 3 needs work" is not an amendment package. "Phase 3 system
structure ADR (ADR-NNNN) must be amended to add a separate audit module,
because Step 08 M-02's compliance-driven audit requirements cannot be met
within the committed modular structure (Step 15 finding INC-03)" is. Each
amendment item names the specific prior-phase artifact, the specific
amendment, and the driving Phase 4 finding.

**Phase 5 input completeness is structural.**
Phase 5 has concerns (module implementation, API stub generation, contract
testing, security implementation, data layer, test implementation,
observability, documentation generation, code review governance, scorecard
updates). Each requires specific Phase 4 inputs (per the instructions
file's Connecting to Phase 5 table). Verify each concern has its inputs.

**A single NOT READY gate blocks the dependent Phase 5 work.**
Phase 5 may begin work that does not depend on a NOT READY dimension while
the gap is resolved, but a NOT READY gate must be resolved before the
dependent Phase 5 work proceeds. Document which Phase 5 work each gate
blocks.

**Override is governance, not analytics.**
The AI does not override its own gate findings. If the practitioner
authorizes Phase 5 despite a NOT READY determination, that is a governance
decision documented in the override section. The AI's finding stands
alongside the override.

**Override authority is tiered, with the two amendment paths the highest
tier.**
Per-principle gate, cross-artifact consistency, and Phase 5 input
completeness overrides require practitioner authority. A Phase 3 alignment
override requires the practitioner plus the Phase 3 authorization
authority. A Phase 2 alignment override requires the practitioner plus the
Phase 2 authorization authority — because overriding either means building
Phase 5 implementation on a prior-phase commitment the framework has
flagged as invalid.

**Produce the Phase 5 Handoff Summary for direct consumption.**
The handoff summary is structured so Phase 5 tool sets can use it as their
context primer — the module index, the contract index, the frameworks, the
scorecard v2.0, the governance model, and the Phase 5-concern-to-Phase-4-
input mapping.

---

## Clarification Step

Read all inputs — all Phase 4 artifacts, the Phase 3 package, the Phase 2
package — thoroughly. Then ask **at most 3 clarifying questions**, only
when necessary.

**The first question, when needed, is a presence check:** "I have the
following required inputs: [list present]. The following appear missing:
[list]. Can you confirm the input set is complete, or provide the missing
artifacts? (If any remain missing, the determination defaults to NOT READY
with the missing artifact named.)"

Other permitted clarification topics:

1. **Resolved gaps not visible in the artifacts.** If a Phase 4 artifact
   appears to have a gap that should have been resolved (e.g., a Step 15
   inconsistency), ask whether it was resolved in a later version not
   pasted.

2. **External context affecting determination.** If the practitioner has
   time-sensitive context (a deadline, an executive decision) affecting
   how a CONDITIONAL gate or an amendment is treated, ask before
   producing the determination.

Do not ask:
- Whether to be lenient on a gate
- For new architecture to fill a gap
- For preferences about the determination outcome

If no clarification is needed, proceed directly to the review.

---

## Kickoff

> Paste all Phase 4 artifacts (Steps 01–15), the Phase 3 package, and the
> Phase 2 package above this line, then paste this line to trigger the
> prompt.

```
All Phase 4 artifacts, the Phase 3 package, and the Phase 2 package are
pasted above. Please conduct the Phase 4 Readiness Review and produce the
formal five-outcome determination, including a structured Phase 3
amendment package and/or Phase 2 amendment package if alignment fails.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.

```markdown
# Phase 4 Readiness Review
# Phase 4 Step 16 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Review Date:** [date]
**Conducted By:** [AI model and version]
**Practitioner:** [name or role]
**Authorization Authority:** [practitioner name or role]

**Inputs Reviewed:**
- [ ] Phase 2 package (Steps 01–06 + Stack ADR) — dated [date] — [Present / Missing]
- [ ] Phase 3 package (Design Direction + ADRs, Scorecard v1.0, Update Protocol, Observability Hooks, Compliance Constraints) — dated [date] — [Present / Missing]
- [ ] Step 01 Architecture Exploration Specification — [Present / Missing]
- [ ] Step 02 Shared Architectural Patterns — [Present / Missing]
- [ ] Step 03 Security Architecture Framework — [Present / Missing]
- [ ] Step 04 Data Architecture Framework — [Present / Missing]
- [ ] Step 05 Documentation Strategy — [Present / Missing]
- [ ] Step 06 Governance Model — [Present / Missing]
- [ ] Step 07 Manifest + Strategic Interface Contracts — [Present / Missing]
- [ ] Step 08 Module Specifications (×N) — [Present / Missing — list]
- [ ] Step 09 Cross-Module Consistency Report — [Present / Missing]
- [ ] Step 10–13 API Contracts (as applicable per Step 01 §4) — [Present / Missing — list]
- [ ] Step 14 Scorecard v2.0 — [Present / Missing]
- [ ] Step 15 Architecture Review Report — [Present / Missing]

**Review Status:** [Draft / Reviewed / Authorized]

---

## 1. Executive Summary

[6–8 sentences covering: the overall Phase 5 readiness determination, the
gate count by status (e.g., "5 PASS, 1 CONDITIONAL, 0 NOT READY"), the
most consequential CONDITIONAL or NOT READY items, the Phase 3 alignment
status (aligned or amendment required), the Phase 2 alignment status
(aligned or amendment required), the cross-artifact consistency status,
and the authorization recommendation. End with one line stating whether
the practitioner can authorize Phase 5 immediately, with conditions, after
Phase 4 remediation, after a Phase 3 amendment cycle, or after a Phase 2
amendment cycle.]

---

## 2. Per-Principle Gate Determination

| Principle | Gate Status | Basis |
|-----------|------------|-------|
| Security | [PASS / CONDITIONAL / NOT READY] | [Citation-backed reasoning] |
| Maintainability | [PASS / CONDITIONAL / NOT READY] | |
| Economics | [PASS / CONDITIONAL / NOT READY] | |
| Operations | [PASS / CONDITIONAL / NOT READY] | |
| Scoring & Metrics | [PASS / CONDITIONAL / NOT READY] | |
| Correctness Verification | [PASS / CONDITIONAL / NOT READY] | |

### Gate Criteria Applied

#### Security — PASS Requires:
- Step 03 framework maps every Phase 2 threat to a control (SEC-NN) or a
  documented gap
- Every Step 08 module spec security section applies its assigned SEC-NN
  controls (per Step 09 constraint citation)
- Authentication is specified at every trust boundary (zero-trust)
- Encryption coordinates with the Step 04 data classification
- Audit logging cites the Phase 3 Step 07 hooks
- API contracts (Steps 10–13) apply the security schemes

**Security finding:** [Citation-backed reasoning]

#### Maintainability — PASS Requires:
- Step 07 module boundaries support independent evolution (no unresolved
  dependency cycles; clean responsibilities/non-responsibilities)
- Module specifications pass the implementation-readiness test (Step 08
  §9, confirmed by Step 15)
- Step 05 documentation strategy is complete with a maintenance plan
- Step 06 governance model assigns owners and review gates

**Maintainability finding:** [Citation-backed reasoning]

#### Economics — PASS Requires:
- The module count and architecture fit the Phase 2 cost envelope (or a
  Phase 2 amendment is surfaced per §6)
- Effort-per-module and operational-overhead implications are reflected in
  the Step 14 scorecard Economics score

**Economics finding:** [Citation-backed reasoning]

#### Operations — PASS Requires:
- Every module spec has a monitoring hooks section referencing Phase 3
  Step 07 hooks (H-NN), with health checks and alerting thresholds
- Deployment and scaling concerns are embedded in the specifications
- Step 06 assigns operations and deployment ownership

**Operations finding:** [Citation-backed reasoning]

#### Scoring & Metrics — PASS Requires:
- Step 14 produced Scorecard v2.0 with all six principles re-scored
- Any regression from v1.0 is handled per the Step 06 protocol
- Monitoring indicators are concrete (mapped to module hooks where Phase 4
  enabled it)

**Scoring & Metrics finding:** [Citation-backed reasoning]

#### Correctness Verification — PASS Requires:
- API contracts (Steps 10–13) are machine-readable and conform to the
  module interfaces
- Step 09 determination is CONSISTENT
- Step 15 cross-artifact inconsistencies are resolved
- Module boundaries and data integrity constraints make verification
  structurally possible
- Confidence levels are assigned across Phase 4 artifacts

**Correctness Verification finding:** [Citation-backed reasoning]

---

## 3. Per-Artifact Completeness Check

| Artifact | Status | Evaluation Checklist Pass Rate | Notes |
|----------|--------|-------------------------------|-------|
| Step 01 Architecture Exploration Specification | [Complete / Partial / Incomplete] | [N of M] | |
| Step 02 Shared Architectural Patterns | | | |
| Step 03 Security Architecture Framework | | | |
| Step 04 Data Architecture Framework | | | |
| Step 05 Documentation Strategy | | | |
| Step 06 Governance Model | | | |
| Step 07 Manifest + Strategic Contracts | | | |
| Step 08 Module Specifications (each M-NN) | | | |
| Step 09 Cross-Module Consistency | | | |
| Step 10–13 API Contracts (as applicable) | | | |
| Step 14 Scorecard v2.0 | | | |
| Step 15 Architecture Review | | | |

### Artifacts Requiring Remediation
| Artifact | Failed Criterion | Required Action |
|----------|-----------------|-----------------|
| Step NN | | |

---

## 4. Cross-Artifact Consistency Check Within Phase 4

Consuming the Step 09 and Step 15 findings and re-verifying resolution.

| Consistency Check | Status | Evidence |
|-------------------|--------|----------|
| Step 09 determination is CONSISTENT (module set internally consistent) | [Pass / Fail] | |
| Step 15 cross-artifact inconsistencies are all resolved | | |
| API contracts conform to module detailed interfaces and strategic contracts | | |
| Security framework covers every module boundary; module specs apply SEC-NN | | |
| Data framework supports every module's data requirements; specs conform to DA-NN | | |
| Module specs honor SP-NN, GOV-NN, DOC-NN; reference H-NN | | |
| API protocol inventory (Step 01 §4) matches the contracts produced | | |
| Scorecard v2.0 reflects the architecture | | |
| No artifact references a non-existent schema, control, contract, or hook | | |

### Consistency Failures
| Inconsistency | Source Artifacts | Impact | Required Action |
|---------------|------------------|--------|-----------------|
| | | | |

---

## 5. Phase 3 Alignment Check

Whether Phase 4 work invalidates any Phase 3 design commitment.

### 5.1 Alignment Dimensions

| Alignment Dimension | Status | Evidence |
|--------------------|--------|----------|
| Module enumeration (Step 07) is consistent with the Phase 3 system structure ADR | [Aligned / Misaligned] | |
| Inter-module communication is consistent with the Phase 3 interaction patterns ADR | | |
| The security framework is consistent with the Phase 3 security model ADR | | |
| The data framework is consistent with the Phase 3 data architecture ADR | | |
| Module monitoring hooks are consistent with the Phase 3 observability strategy ADR and Step 07 hooks | | |
| The architecture honors the Phase 3 compliance design constraints | | |
| No Phase 4 artifact requires a Phase 3 commitment the design ADRs did not make | | |

### 5.2 Phase 3 Amendment Package

[Populated only if one or more Phase 3 alignment dimensions are
Misaligned. If all are Aligned, this reads "Not applicable — Phase 3
alignment verified."]

The structured package directing the practitioner back to Phase 3.

#### 5.2.1 Phase 3 Design ADR Amendments Required

| Phase 3 ADR | Specific Amendment Required | Driving Phase 4 Finding |
|------------|----------------------------|-------------------------|
| ADR-[NNNN] ([dimension]) | | [Step NN finding] |

#### 5.2.2 Phase 3 Scorecard Baseline Revisions Required

| Scorecard Element | Specific Revision Required | Driving Phase 4 Finding |
|-------------------|---------------------------|-------------------------|
| | | |

#### 5.2.3 Phase 3 Observability Hooks Revisions Required

| Hook (H-NN) | Specific Revision Required | Driving Phase 4 Finding |
|-------------|---------------------------|-------------------------|
| | | |

#### 5.2.4 Phase 3 Compliance Constraint Revisions Required

| Constraint | Specific Revision Required | Driving Phase 4 Finding |
|------------|---------------------------|-------------------------|
| | | |

#### 5.2.5 Phase 3 Amendment Cycle Process

1. The practitioner returns to Phase 3 with this amendment package.
2. The practitioner re-runs the relevant Phase 3 prompts to produce
   amended artifacts (new versions of the affected ADRs, scorecard,
   observability hooks, or compliance constraints).
3. The practitioner re-runs Phase 3 Step 09 (Readiness Review) to verify
   Phase 3 internal consistency is restored.
4. The practitioner returns to Phase 4 and re-runs the affected Phase 4
   steps (typically the affected Stage 1 framework, Step 07 enumeration,
   and the affected Step 08 module specs).
5. The practitioner re-runs Step 16 to verify alignment is restored.

This amendment cycle is governance, not failure.

---

## 6. Phase 2 Alignment Check

Whether Phase 4 work invalidates any Phase 2 commitment.

### 6.1 Alignment Dimensions

| Alignment Dimension | Status | Evidence |
|--------------------|--------|----------|
| The architecture (module count, patterns) fits the Phase 2 cost envelope | [Aligned / Misaligned] | |
| Detailed effort estimates do not exceed the Phase 2 cost model | | |
| The architecture does not require a stack capability the Phase 2 stack ADR did not commit | | |
| The security architecture addresses every Phase 2 threat (or surfaces a threat needing model refinement) | | |
| Performance requirements per module are achievable within the Phase 2 benchmarks | | |
| No Phase 4 artifact violates a Phase 2 Stack ADR acceptance condition or revision trigger | | |

### 6.2 Phase 2 Amendment Package

[Populated only if one or more Phase 2 alignment dimensions are
Misaligned. If all are Aligned, this reads "Not applicable — Phase 2
alignment verified."]

The structured package directing the practitioner back to Phase 2.

#### 6.2.1 Phase 2 ADR Amendments Required

| Phase 2 ADR | Specific Amendment Required | Driving Phase 4 Finding |
|------------|----------------------------|-------------------------|
| ADR-[NNNN] (Stack) | | |

#### 6.2.2 Phase 2 Cost Model Revisions Required

| Phase 2 Step 02 Section | Specific Revision Required | Driving Phase 4 Finding |
|------------------------|---------------------------|-------------------------|
| | | [E.g., effort-per-module total] |

#### 6.2.3 Phase 2 Benchmark Adjustments Required

| Phase 2 Step 06 Benchmark | Specific Adjustment Required | Driving Phase 4 Finding |
|--------------------------|------------------------------|-------------------------|
| BM-NN | | |

#### 6.2.4 Phase 2 Threat Model Refinements Required

| Phase 2 Step 03 Threat | Specific Refinement Required | Driving Phase 4 Finding |
|-----------------------|------------------------------|-------------------------|
| T-NN | | |

#### 6.2.5 Phase 2 Business Case / Principle Weighting Revisions Required

| Phase 2 Step 01 Element | Specific Revision Required | Driving Phase 4 Finding |
|------------------------|---------------------------|-------------------------|
| | | |

#### 6.2.6 Phase 2 Amendment Cycle Process

1. The practitioner returns to Phase 2 with this amendment package.
2. The practitioner re-runs the relevant Phase 2 prompts to produce
   amended artifacts.
3. The practitioner re-runs Phase 2 Step 07 (Readiness Review) to verify
   Phase 2 internal consistency is restored.
4. The practitioner returns to Phase 3, re-runs the affected Phase 3 steps
   (typically simulation and commitment), and re-runs Phase 3 Step 09.
5. The practitioner returns to Phase 4, re-runs the affected Phase 4
   steps, and re-runs Step 16 to verify alignment is restored.

A Phase 2 amendment is the deepest backward effect in the framework — it
cascades through Phase 3 and Phase 4. This is governance, not failure.

---

## 7. Phase 5 Input Completeness Check

Each Phase 5 concern is verified against the Phase 4 inputs it requires
(per the instructions file's Connecting to Phase 5 table).

| Phase 5 Concern | Required Phase 4 Inputs | Inputs Available | Status |
|-----------------|-------------------------|------------------|--------|
| Module implementation | Step 08 module specifications, Step 02 shared patterns | | [Complete / Incomplete] |
| API stub generation | Steps 10–13 API contracts | | |
| Contract testing | Steps 10–13 API contracts | | |
| Security implementation | Step 03 security framework, module security sections | | |
| Data layer implementation | Step 04 data framework, module data models | | |
| Test implementation | Module test strategy sections | | |
| Observability implementation | Module monitoring hooks, Phase 3 Step 07 handoff | | |
| Documentation generation | Step 05 documentation strategy | | |
| Code review governance | Step 06 governance model | | |
| Phase 5 scorecard updates | Step 14 Scorecard v2.0, Phase 3 Step 06 Update Protocol | | |

### Phase 5 Input Gaps
| Phase 5 Concern | Missing Input | Source Step | Required Action |
|-----------------|--------------|-------------|-----------------|
| | | | |

---

## 8. Overall Phase 5 Readiness Determination

**Determination:** [READY / CONDITIONALLY READY / NOT READY (Phase 4
gaps) / NOT READY (Phase 3 amendment required) / NOT READY (Phase 2
amendment required)]

[4–6 sentences supporting the determination, referencing the gate counts,
the cross-artifact consistency status, the Phase 3 and Phase 2 alignment
status, and the Phase 5 input completeness status.]

### Determination Logic Applied

- **READY** — All six per-principle gates PASS. All artifacts Complete.
  All cross-artifact consistency checks Pass (Step 09 CONSISTENT, Step 15
  inconsistencies resolved). Phase 3 alignment verified. Phase 2 alignment
  verified. All Phase 5 concerns have their inputs.

- **CONDITIONALLY READY** — One or more gates are CONDITIONAL with
  documented remediation. Phase 5 may begin work not blocked by the
  conditional gates. Conditional remediation must complete before the
  dependent Phase 5 work begins.

- **NOT READY (Phase 4 gaps)** — One or more per-principle gates NOT
  READY, OR one or more artifacts Incomplete, OR cross-artifact
  consistency within Phase 4 has unresolved failures, OR a Phase 5 concern
  lacks required inputs. Phase 5 cannot begin the affected work until
  Phase 4 remediation completes.

- **NOT READY (Phase 3 amendment required)** — One or more Phase 3
  alignment dimensions Misaligned. Phase 5 cannot begin until the Phase 3
  amendments per §5.2 are completed and the affected Phase 4 steps are
  re-run.

- **NOT READY (Phase 2 amendment required)** — One or more Phase 2
  alignment dimensions Misaligned. Phase 5 cannot begin until the Phase 2
  amendments per §6.2 are completed and the affected Phase 3 and Phase 4
  steps are re-run.

[If more than one NOT READY condition applies, the determination names the
deepest amendment path required (Phase 2 deepest, then Phase 3, then
Phase 4 gaps), and all applicable amendment packages are populated.]

---

## 9. Required Actions Before Phase 5 Authorization

[If READY: "No required actions. Phase 5 may begin upon practitioner
authorization."]

### 9.1 Phase 4 Internal Remediation Actions
[If CONDITIONALLY READY or NOT READY (Phase 4 gaps).]

| Action ID | Required Action | Responsible Step | Owner (GOV-NN) | Blocks Which Phase 5 Work |
|-----------|-----------------|------------------|----------------|---------------------------|
| RA-01 | | | | |

### 9.2 Phase 3 Amendment Cycle Actions
[If NOT READY (Phase 3 amendment required). The §5.2 package is the input.]

| Action ID | Phase 3 Step to Re-Run | Driving Misalignment | Owner | Target Date |
|-----------|------------------------|----------------------|-------|-------------|
| P3-01 | | | | |

### 9.3 Phase 2 Amendment Cycle Actions
[If NOT READY (Phase 2 amendment required). The §6.2 package is the input.]

| Action ID | Phase 2 Step to Re-Run | Driving Misalignment | Owner | Target Date |
|-----------|------------------------|----------------------|-------|-------------|
| P2-01 | | | | |

### 9.4 Phase 3 / Phase 4 Re-Run Actions After Amendment
| Action ID | Step to Re-Run | Reason | Owner | Target Date |
|-----------|----------------|--------|-------|-------------|
| RR-01 | | | | |

---

## 10. Phase 5 Handoff Summary

A concise summary of what Phase 5 inherits. Phase 5 tool sets can use this
as their context primer.

### The Module Set

| Module (M-NN) | Purpose | Owner (GOV-NN) | Spec | Strategic Contract (SIC-NN) |
|---------------|---------|----------------|------|------------------------------|
| M-NN | | | Step 08 | SIC-NN |

### The API Contracts

| Contract | Protocol | Step | Boundaries |
|----------|----------|------|-----------|
| | [REST / gRPC / events / other] | [10–13] | |

### The Cross-Cutting Frameworks

| Framework | Step | ID Series |
|-----------|------|-----------|
| Shared patterns | 02 | SP-NN |
| Security | 03 | SEC-NN |
| Data | 04 | DA-NN |
| Documentation | 05 | DOC-NN |
| Governance | 06 | GOV-NN |

### The Cross-Phase Living Documents Phase 5 Inherits

| Document | Phase 4 Source | Update Protocol |
|----------|----------------|-----------------|
| Principle Scorecard v2.0 | Step 14 | Phase 3 Step 06 protocol (Phase 5 produces v3.x) |
| ADR series | Phase 4 ADRs + Phase 3 + Phase 2 stack ADR | Standard ADR practice |

### Phase 5 Concern → Phase 4 Input Mapping

| Phase 5 Concern | Phase 4 Inputs |
|-----------------|----------------|
| Module implementation | Step 08 specs, Step 02 patterns |
| API stub generation / contract testing | Steps 10–13 contracts |
| Security implementation | Step 03 framework, module security sections |
| Data layer implementation | Step 04 framework, module data models |
| Test implementation | Module test strategy sections |
| Observability implementation | Module monitoring hooks, Phase 3 Step 07 handoff |
| Documentation generation | Step 05 strategy |
| Code review governance | Step 06 model |
| Scorecard updates | Step 14 v2.0, Phase 3 Step 06 protocol |

### Top Architectural Risks Carried Into Phase 5
[The highest-priority risks from the Step 14 scorecard risk items and the
Step 15 review, for Phase 5 attention.]

---

## 11. Practitioner Override (If Applicable)

If the practitioner authorizes Phase 5 despite a NOT READY or unresolved
CONDITIONAL determination, the override is documented here. The AI's
determination stands; the override is a separate governance act.

### 11.1 Override Tiered Authority Requirements

| Override Type | Required Authority |
|--------------|--------------------|
| Per-principle gate override (CONDITIONAL or NOT READY) | Practitioner |
| Cross-artifact consistency override | Practitioner |
| Phase 5 input completeness override | Practitioner |
| Phase 3 alignment override | Practitioner + Phase 3 authorization authority |
| Phase 2 alignment override | Practitioner + Phase 2 authorization authority |

### 11.2 Override Documentation

[Used only if override is applied. If no override: "Not applicable —
practitioner has accepted the determination as stated."]

| Element | Detail |
|---------|--------|
| Determination being overridden | [Which determination] |
| Specific gate(s) or dimension(s) overridden | |
| Override authorized scope | [Full Phase 5 / specific Phase 5 work] |
| Override authority | [Names of all required authorities per tier table] |
| Override date | |
| Override rationale | [Specific business or schedule reason — generic not acceptable] |
| Risk being accepted | [Concrete description] |
| Mitigation in place | |
| Conditions for revisit | |

If Phase 3 or Phase 2 alignment is overridden, the override must
specifically acknowledge that Phase 5 implementation will be built on a
prior-phase commitment the framework has flagged as invalid, and the risk
acceptance must articulate the specific downstream consequences.

---

## 12. Authorization Record

| Authorization Element | Value |
|----------------------|-------|
| Authorization status | [Pending Practitioner Review / Authorized / Authorization Withheld] |
| Authorization scope | [Full Phase 5 / Partial Phase 5 — specify / Amendment required first] |
| Authorized by | [Practitioner name and role] |
| Authorization date | |
| Phase 5 may begin | [Yes / Yes with conditions / No — Phase 4 remediation / No — Phase 3 amendment cycle / No — Phase 2 amendment cycle] |
| Re-review required when | [Conditions triggering another readiness review] |

---

## 13. Audit Trail

| Event | Date | Actor | Detail |
|-------|------|-------|--------|
| Readiness review conducted | | AI ([model]) | |
| Findings reviewed by practitioner | | | |
| [If applicable] Phase 3 amendment cycle initiated | | | |
| [If applicable] Phase 2 amendment cycle initiated | | | |
| [If applicable] Amendment cycle(s) completed and re-runs done | | | |
| [If applicable] Step 16 re-review conducted | | | |
| Practitioner authorization | | | |
| [If applicable] Override applied | | | |
```

---

## Evaluation Checklist

Before the readiness review is accepted:

- [ ] All required inputs are present (all Phase 4 artifacts + Phase 3
      package + Phase 2 package), or missing ones are named and the
      determination reflects them
- [ ] Each per-principle gate has a status (PASS / CONDITIONAL / NOT READY)
      with citation-backed basis applying the documented Phase 4 criteria
- [ ] Each Phase 4 artifact's completeness is assessed against its own
      evaluation checklist
- [ ] Cross-artifact consistency consumes the Step 09 and Step 15 findings
      and verifies architecture bugs are resolved
- [ ] All Phase 3 alignment dimensions are evaluated; if any fail, the
      §5.2 Phase 3 amendment package is structured and specific
- [ ] All Phase 2 alignment dimensions are evaluated; if any fail, the
      §6.2 Phase 2 amendment package is structured and specific
- [ ] Each amendment item names the specific prior-phase artifact, the
      specific amendment, and the driving Phase 4 finding (not "Phase 3/2
      needs work")
- [ ] All Phase 5 concerns are evaluated for input completeness
- [ ] The overall determination is exactly one of the five outcomes — no
      sixth option; if multiple NOT READY conditions apply, the deepest
      amendment path is named and all applicable packages populated
- [ ] If CONDITIONAL, every conditional has a named owner and target date
- [ ] If NOT READY (Phase 4 gaps), every blocking gap has a specific
      required action and responsible step
- [ ] If NOT READY (Phase 3 amendment), the §5.2 package and §5.2.5 cycle
      process are complete
- [ ] If NOT READY (Phase 2 amendment), the §6.2 package and §6.2.6 cycle
      process are complete
- [ ] No new architecture content is present (the review evaluates)
- [ ] The Phase 5 Handoff Summary (§10) is concise and structured for
      Phase 5 tool set consumption
- [ ] The override section (§11) includes the tiered authority table — with
      Phase 3 and Phase 2 alignment overrides at the highest tier — even
      if no override is applied
- [ ] The authorization record (§12) is present (Pending until practitioner
      reviews)
- [ ] The audit trail accommodates both Phase 3 and Phase 2 amendment cycle
      events

---

*Step 16 of 16 — final step in the Phase 4 Architecture & Modular Design
Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `architecture-modular-design.instructions.md`*
*Previous step: `step-15-architecture-review.prompt.md`*
*Next: Phase 5 — Implementation*
