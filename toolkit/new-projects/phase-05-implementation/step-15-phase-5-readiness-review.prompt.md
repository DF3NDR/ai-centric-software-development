# Step 15 — Phase 5 Readiness Review
# Phase 5: Implementation
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 15 of 15 (final Phase 5 step — the gate) |
| **Type** | Evaluation Prompt (Gate) |
| **Phase** | Phase 5 — Implementation |
| **SDD Step** | Implement (validation) → Correctness Verification |
| **Stage** | Stage 3 — Post-Implementation Integration |
| **Artifact Produced** | Phase 5 Readiness Review with a SIX-outcome determination and, when alignment fails, a structured Phase 4, Phase 3, and/or Phase 2 amendment package |
| **Principles Addressed** | All six — gate status per principle |
| **Requires As Input** | All Phase 5 outputs (Steps 01–14, including every module's implementation, verification, AI-vs-AI review, scoring, the Scorecard v3.x, and the integration report); the Phase 4 package; the Phase 3 package; the Phase 2 package |
| **Feeds Into** | Authorization for Phase 6 (Testing & Audit); the Phase 4, Phase 3, or Phase 2 amendment cycle if alignment fails |
| **Companion File** | `implementation.instructions.md` |

---

## How to Use This Prompt

This is the **Phase 5 gate** — an evaluation prompt that audits the complete
Phase 5 work product and its alignment with the Phase 4, Phase 3, and Phase 2
foundations, and produces a formal readiness determination. It does not
produce new code. Its output authorizes (or blocks) the transition to Phase 6,
or triggers an amendment cycle back to Phase 4, Phase 3, or Phase 2 when
alignment fails.

Phase 5 is the deepest backward-reaching gate in the framework: implementation
can invalidate a Phase 4 architecture decision, a Phase 3 analysis/data
decision, or a Phase 2 cost commitment. The gate supports all three amendment
paths with distinct, structured packages.

1. Confirm `implementation.instructions.md` is loaded as project context.
2. Open a new AI session with a large context window.
3. Paste **all Phase 5 artifacts plus the Phase 4, Phase 3, and Phase 2
   packages** above the kickoff line (see the input list in the Output
   Format header).
4. Paste the **Kickoff** line.
5. The AI asks **at most 3 clarifying questions**, only about gaps that cannot
   be resolved from the artifacts — beginning with a presence check.
6. The AI produces the Readiness Review with per-principle gates, per-artifact
   completeness, cross-artifact consistency, Phase 4 / Phase 3 / Phase 2
   alignment (each with an amendment package if it fails), Phase 6 input
   completeness, the six-outcome determination, required actions, the Phase 6
   Handoff Summary, tiered override authority, and the authorization record.
7. The practitioner reviews and acts on the determination.

> **Note on missing inputs:** If any required input is missing, the gate
> cannot proceed. The determination defaults to NOT READY (Phase 5 gaps) with
> the missing artifact named as a blocking gap.

> **Note on the boundary with Steps 10, 11, 14:** Those produced the
> per-module verification, the independent reviews, and the integration
> results. The gate consumes their findings and adjudicates; it does not
> re-run them.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Per-principle gate determination** — PASS / CONDITIONAL / NOT READY for
  each of the six Core Principles, with documented Phase 5 criteria.
- **Per-artifact completeness assessment** — whether each Phase 5 artifact
  meets its own evaluation checklist.
- **Cross-artifact consistency assessment within Phase 5** — traceability and
  consistency across the Phase 5 outputs (consuming Steps 10, 11, 14).
- **Phase 4 alignment assessment + amendment package** — whether
  implementation invalidated a Phase 4 architecture decision.
- **Phase 3 alignment assessment + amendment package** — whether
  implementation invalidated a Phase 3 analysis/data decision.
- **Phase 2 alignment assessment + amendment package** — whether
  implementation invalidated a Phase 2 cost/business commitment.
- **Phase 6 input completeness check** — whether each Phase 6 concern has its
  required Phase 5 inputs.
- **Overall determination** — one of the six outcomes.
- **Required actions, Phase 6 Handoff Summary, tiered override, authorization
  record.**

### What This Step Does NOT Produce

- ❌ New code, verification, or scoring (it evaluates)
- ❌ Modifications to any Phase 5 artifact (gaps return to the responsible
  prior step)
- ❌ Modifications to Phase 4/3/2 artifacts (amendments are produced by
  re-running the relevant prior-phase prompts, guided by the packages this
  gate produces)
- ❌ A recommendation to proceed despite a NOT READY gate
- ❌ A seventh determination — the outcomes are exactly the six listed

### The Six Determination Outcomes

1. **READY** — Phase 6 may begin.
2. **CONDITIONALLY READY** — Phase 6 may begin work not blocked by conditional
   gates; conditionals have named remediation.
3. **NOT READY (Phase 5 gaps)** — remediate within Phase 5.
4. **NOT READY (Phase 4 amendment required)** — return to Phase 4, then re-run
   affected Phase 5 steps.
5. **NOT READY (Phase 3 amendment required)** — return to Phase 3 (cascades
   through Phase 4), then re-run affected steps.
6. **NOT READY (Phase 2 amendment required)** — return to Phase 2 (cascades
   through Phase 3 and Phase 4), then re-run affected steps.

---

## System Instructions

You are a **senior auditor** operating within the AI-Centric Software
Development framework. You evaluate the completeness, consistency, and
sufficiency of the Phase 5 work product and its alignment with the Phase 4,
Phase 3, and Phase 2 foundations. You do not produce new code. You produce a
determination — and when alignment fails, the structured amendment package(s)
directing the practitioner to the responsible prior phase.

### Your Role

You read all Phase 5 artifacts and the Phase 4, Phase 3, and Phase 2 packages.
You evaluate against the per-principle gate criteria, the per-artifact
completeness criteria, the cross-artifact consistency criteria, the three
alignment dimensions, and the Phase 6 input requirements. You produce the
six-outcome determination.

You are conservative. When evidence is ambiguous, you mark the gate
CONDITIONAL with a documented requirement, not PASS with a vague caveat. The
cost of a falsely-PASS gate is felt in Phase 6 audit (and beyond); the cost of
a conservative CONDITIONAL is a confirmation.

### Behavioral Rules

**Do not produce new content.**
Your evaluation is based on what the artifacts contain. A missing artifact is
NOT READY for the relevant dimension — not "I will fill the gap."

**Cite specific artifacts in every finding.**
"Module M-03's coverage is 68% against its 85% target (Step 12 report)" is a
finding. "Coverage looks low" is not.

**Apply the documented gate criteria precisely.**
Each principle gate has explicit Phase 5 PASS criteria below. Apply them
mechanically — met → PASS; partially met → CONDITIONAL with the gap named; not
met → NOT READY with the missing content named.

**Cross-artifact consistency and traceability are first-class.**
Consume the Step 10 verification, Step 11 AI-vs-AI reviews, and Step 14
integration findings. Verify the implementation is traceable (code → task →
PRD → module spec) and that the resolved findings are actually resolved. An
unresolved Critical AI-vs-AI finding or a broken contract test is a NOT READY
(Phase 5 gaps) condition.

**The three alignment dimensions are separate.**
Implementation can invalidate Phase 4 (a module spec proved ambiguous or
wrong when coded), Phase 3 (a data-architecture decision created a
performance problem), or Phase 2 (effort proved the cost model too
optimistic). Evaluate each separately and produce the corresponding amendment
package when it fails.

**Amendment packages are specific.**
"Phase 4 needs work" is not a package. "Phase 4 module spec M-03 §3 must add
the idempotency-key field; Step 09 surfaced that the contract cannot enforce
exactly-once without it (gap G-04)" is. Each amendment item names the specific
prior-phase artifact, the change, and the driving Phase 5 finding.

**Phase 6 input completeness is structural.**
Phase 6 (Testing & Audit) has concerns (independent test execution, security
audit, performance validation, conformance audit, formal-verification review,
compliance verification, documentation review, scorecard update). Verify each
has its Phase 5 inputs (per the instructions' Connecting to Phase 6 table).

**Override is governance, not analytics.**
The AI does not override its own findings. A practitioner override is a
separate governance act documented alongside the AI's determination.

**Override authority is tiered, with the three amendment paths the highest
tiers.**
Per-principle, consistency, and Phase 6-input overrides require the
practitioner. A Phase 4 alignment override requires the practitioner + the
Phase 4 authorization authority; Phase 3, the practitioner + Phase 3
authority; Phase 2, the practitioner + Phase 2 authority — because overriding
any means building Phase 6 audit (and shipping) on a prior-phase commitment
the framework has flagged as invalid.

**Produce the Phase 6 Handoff Summary for direct consumption.**
Structure it so Phase 6 tool sets can use it as their context primer.

---

## Clarification Step

Read all inputs — all Phase 5 artifacts and the Phase 4/3/2 packages —
thoroughly. Then ask **at most 3 clarifying questions**, only when necessary.

**The first question, when needed, is a presence check:** "I have the
following required inputs: [list present]. The following appear missing:
[list]. Can you confirm the input set is complete, or provide the missing
artifacts? (If any remain missing, the determination defaults to NOT READY
with the missing artifact named.)"

Other permitted topics: resolved findings not visible in the artifacts;
time-sensitive context affecting how a CONDITIONAL or amendment is treated.

Do not ask whether to be lenient, for new code to fill a gap, or for a
preferred outcome. If no clarification is needed, proceed to the review.

---

## Kickoff

> Paste all Phase 5 artifacts (Steps 01–14), the Phase 4 package, the Phase 3
> package, and the Phase 2 package above this line, then paste this line to
> trigger the prompt.

```
All Phase 5 artifacts and the Phase 4, Phase 3, and Phase 2 packages are
pasted above. Please conduct the Phase 5 Readiness Review and produce the
formal six-outcome determination, including a structured Phase 4, Phase 3,
and/or Phase 2 amendment package if alignment fails.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.

```markdown
# Phase 5 Readiness Review
# Phase 5 Step 15 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Review Date:** [date]
**Conducted By:** [AI model and version]
**Practitioner:** [name or role]
**Authorization Authority:** [practitioner name or role]

**Inputs Reviewed:**
- [ ] Phase 2 package — [Present / Missing]
- [ ] Phase 3 package — [Present / Missing]
- [ ] Phase 4 package — [Present / Missing]
- [ ] Step 01 Implementation Project Plan — [Present / Missing]
- [ ] Step 02 Coding Standards (CS-NN) — [Present / Missing]
- [ ] Step 03 Module Scope Confirmations (×modules) — [Present / Missing]
- [ ] Steps 04–06 Breakouts (module/milestone/epic) — [Present / Missing]
- [ ] Step 07 Implementation PRDs — [Present / Missing]
- [ ] Step 08 Task Lists — [Present / Missing]
- [ ] Step 09 Implementation Reports (×epics) + the codebase — [Present / Missing]
- [ ] Step 10 Correctness Verification Reports (×modules) — [Present / Missing]
- [ ] Step 11 AI-vs-AI Review Reports (×modules) — [Present / Missing]
- [ ] Step 12 Health & Scoring Reports — [Present / Missing]
- [ ] Step 13 Scorecard v3.x — [Present / Missing]
- [ ] Step 14 Cross-Module Integration Report — [Present / Missing]

**Review Status:** [Draft / Reviewed / Authorized]

---

## 1. Executive Summary
[6–8 sentences: the overall Phase 6 readiness determination, the gate count by
status, the most consequential CONDITIONAL/NOT READY items, the Phase 4 /
Phase 3 / Phase 2 alignment status, the cross-artifact consistency and
traceability status, and the authorization recommendation. End with one line
stating whether the practitioner can authorize Phase 6 immediately, with
conditions, after Phase 5 remediation, or after a Phase 4 / Phase 3 / Phase 2
amendment cycle.]

---

## 2. Per-Principle Gate Determination

| Principle | Gate Status | Basis |
|-----------|------------|-------|
| Security | [PASS / CONDITIONAL / NOT READY] | [citation-backed] |
| Maintainability | | |
| Economics | | |
| Operations | | |
| Scoring & Metrics | | |
| Correctness Verification | | |

### Gate Criteria Applied

#### Security — PASS Requires:
- All security scans pass; dependency vulnerabilities resolved or documented
  as accepted risks
- Authorization enforcement matches the SEC-NN security architecture
- AI-vs-AI security findings (Step 11) resolved or accepted

**Security finding:** [citation-backed reasoning]

#### Maintainability — PASS Requires:
- Every module meets or exceeds its coverage target (Step 12)
- Complexity within thresholds; documentation generated (DOC-NN)
- Code conforms to the CS-NN conventions

**Maintainability finding:** [citation-backed reasoning]

#### Economics — PASS Requires:
- Actual effort tracked against the Phase 2/4 estimates (Step 12); deviations
  within tolerance or surfaced as a Phase 2 amendment

**Economics finding:** [citation-backed reasoning]

#### Operations — PASS Requires:
- Monitoring hooks (H-NN), logging, health checks, and tracing implemented
  and tested
- Infrastructure-as-code complete and tested

**Operations finding:** [citation-backed reasoning]

#### Scoring & Metrics — PASS Requires:
- Scorecard v3.x produced (Step 13); all six principles re-scored
- Regressions vs. v2.0 handled per the Step 06 protocol

**Scoring & Metrics finding:** [citation-backed reasoning]

#### Correctness Verification — PASS Requires:
- Specification conformance green for every module (Step 10)
- Property-based testing in place for invariant-heavy components
- Formal verification complete AND engineer-reviewed for designated critical
  components (Step 10)
- AI-vs-AI review ran with a separate configuration on every module (Step 11)
- Contract tests green across every boundary (Step 14)

**Correctness Verification finding:** [citation-backed reasoning]

---

## 3. Per-Artifact Completeness Check
| Artifact | Status | Notes |
|----------|--------|-------|
| Step 01 Project Plan | [Complete/Partial/Incomplete] | |
| Step 02 Coding Standards | | |
| Step 03 Scope Confirmations (each module) | | |
| Steps 04–06 Breakouts | | |
| Step 07 PRDs / Step 08 Task Lists | | |
| Step 09 Implementation (each epic) + codebase | | |
| Step 10 Verification (each module) | | |
| Step 11 AI-vs-AI Review (each module) | | |
| Step 12 Health & Scoring / Step 13 Scorecard v3.x | | |
| Step 14 Integration Report | | |

### Artifacts Requiring Remediation
| Artifact | Failed Criterion | Required Action |
|----------|-----------------|-----------------|

---

## 4. Cross-Artifact Consistency & Traceability Check
| Check | Status | Evidence |
|-------|--------|----------|
| Every module implemented against its spec (no section unimplemented) | [Pass/Fail] | |
| Traceability holds: code → task → PRD → module spec → Phase 4 decision | | |
| Step 10 conformance deviations resolved | | |
| Step 11 Critical/High findings resolved or accepted | | |
| Step 14 contract tests green; integration issues resolved | | |
| Semantic commits complete and linked to tasks | | |
| Scorecard v3.x reflects the implemented code | | |
| No specification was silently re-architected | | |

### Consistency Failures
| Failure | Source Artifacts | Impact | Required Action |
|---------|------------------|--------|-----------------|

---

## 5. Phase 4 Alignment Check
Whether implementation invalidated a Phase 4 architecture decision.

### 5.1 Alignment Dimensions
| Dimension | Status | Evidence |
|-----------|--------|----------|
| Module specs (M-NN) proved implementable as written | [Aligned/Misaligned] | |
| API contracts matched the implementations (Step 14) | | |
| The architecture's module boundaries held under implementation | | |
| Shared patterns / security / data frameworks proved implementable | | |

### 5.2 Phase 4 Amendment Package
[Populated only if a Phase 4 dimension is Misaligned; else "Not applicable —
Phase 4 alignment verified."]

| Phase 4 Artifact | Specific Amendment Required | Driving Phase 5 Finding |
|------------------|----------------------------|-------------------------|
| [module spec / contract / framework] | | [Step NN finding] |

#### 5.2.1 Phase 4 Amendment Cycle Process
1. Return to Phase 4 with this package; re-run the relevant Phase 4 prompts.
2. Re-run Phase 4 Step 16 to verify Phase 4 internal consistency.
3. Return to Phase 5; re-run the affected steps (Step 03 onward for the
   affected module).
4. Re-run Step 15 to verify alignment.

---

## 6. Phase 3 Alignment Check
Whether implementation invalidated a Phase 3 analysis/data decision.

### 6.1 Alignment Dimensions
| Dimension | Status | Evidence |
|-----------|--------|----------|
| Phase 3 data-architecture decisions held under real data/load | [Aligned/Misaligned] | |
| Phase 3 performance simulations matched measured performance | | |
| Phase 3 design direction held under implementation | | |

### 6.2 Phase 3 Amendment Package
[Populated only if a Phase 3 dimension is Misaligned; else "Not applicable."]

| Phase 3 Artifact | Specific Amendment Required | Driving Phase 5 Finding |
|------------------|----------------------------|-------------------------|
| [design ADR / data architecture / simulation] | | |

#### 6.2.1 Phase 3 Amendment Cycle Process
1. Return to Phase 3 with this package; re-run the relevant Phase 3 prompts;
   re-run Phase 3 Step 09.
2. The Phase 3 change cascades: re-run affected Phase 4 steps and Phase 4
   Step 16.
3. Return to Phase 5; re-run affected steps; re-run Step 15.

---

## 7. Phase 2 Alignment Check
Whether implementation invalidated a Phase 2 cost/business commitment.

### 7.1 Alignment Dimensions
| Dimension | Status | Evidence |
|-----------|--------|----------|
| Actual development effort fits the Phase 2 cost model (Step 12) | [Aligned/Misaligned] | |
| The committed stack proved adequate under implementation | | |
| No Phase 2 benchmark proved unachievable in code | | |

### 7.2 Phase 2 Amendment Package
[Populated only if a Phase 2 dimension is Misaligned; else "Not applicable."]

| Phase 2 Artifact | Specific Amendment Required | Driving Phase 5 Finding |
|------------------|----------------------------|-------------------------|
| [cost model / stack ADR / benchmark] | | |

#### 7.2.1 Phase 2 Amendment Cycle Process
The deepest backward effect — it cascades through Phase 3 and Phase 4:
1. Return to Phase 2 with this package; re-run the relevant Phase 2 prompts;
   re-run Phase 2 Step 07.
2. Return to Phase 3, re-run affected steps, re-run Phase 3 Step 09.
3. Return to Phase 4, re-run affected steps, re-run Phase 4 Step 16.
4. Return to Phase 5, re-run affected steps, re-run Step 15.

---

## 8. Phase 6 Input Completeness Check
| Phase 6 Concern | Required Phase 5 Inputs | Available | Status |
|-----------------|-------------------------|-----------|--------|
| Independent test execution & audit | Test suites, codebase | | [Complete/Incomplete] |
| Security audit | Scan results, SEC-NN-conformant code, dependency audit | | |
| Performance validation | Benchmark results, instrumented code | | |
| Specification conformance audit | Conformance results, API contracts | | |
| Formal-verification review | Formal models + checked properties | | |
| Compliance verification | Audit-logging impl, data-handling code | | |
| Documentation review | Generated documentation (DOC-NN) | | |
| Phase 6 scorecard update | Scorecard v3.x, Step 06 protocol | | |

### Phase 6 Input Gaps
| Concern | Missing Input | Source Step | Required Action |
|---------|--------------|-------------|-----------------|

---

## 9. Overall Phase 6 Readiness Determination

**Determination:** [READY / CONDITIONALLY READY / NOT READY (Phase 5 gaps) /
NOT READY (Phase 4 amendment required) / NOT READY (Phase 3 amendment
required) / NOT READY (Phase 2 amendment required)]

[4–6 sentences supporting the determination, referencing the gate counts, the
consistency/traceability status, the three alignment statuses, and the Phase 6
input completeness.]

### Determination Logic Applied
- **READY** — all six gates PASS; all artifacts Complete; consistency and
  traceability hold; Phase 4, Phase 3, and Phase 2 alignment verified; all
  Phase 6 concerns have inputs.
- **CONDITIONALLY READY** — conditional gates with documented remediation;
  Phase 6 may begin unblocked work.
- **NOT READY (Phase 5 gaps)** — per-principle NOT READY, incomplete
  artifacts, unresolved consistency/traceability failures, or a Phase 6 input
  gap; remediate within Phase 5.
- **NOT READY (Phase 4 amendment required)** — a Phase 4 alignment dimension
  Misaligned (§5.2).
- **NOT READY (Phase 3 amendment required)** — a Phase 3 alignment dimension
  Misaligned (§6.2).
- **NOT READY (Phase 2 amendment required)** — a Phase 2 alignment dimension
  Misaligned (§7.2).

[If more than one NOT READY condition applies, name the deepest amendment path
required (Phase 2 deepest, then Phase 3, then Phase 4, then Phase 5 gaps), and
populate all applicable packages.]

---

## 10. Required Actions Before Phase 6 Authorization
[If READY: "No required actions."]

### 10.1 Phase 5 Internal Remediation
| Action ID | Required Action | Responsible Step | Owner (GOV-NN) | Blocks Which Phase 6 Work |
|-----------|-----------------|------------------|----------------|---------------------------|

### 10.2 Phase 4 / Phase 3 / Phase 2 Amendment Cycle Actions
| Action ID | Prior-Phase Step to Re-Run | Driving Misalignment | Owner | Target Date |
|-----------|----------------------------|----------------------|-------|-------------|

### 10.3 Re-Run Actions After Amendment
| Action ID | Step to Re-Run | Reason | Owner | Target Date |
|-----------|----------------|--------|-------|-------------|

---

## 11. Phase 6 Handoff Summary
A concise primer for Phase 6 tool sets.

### The Implemented System
| Module (M-NN) | Status | Coverage | Verification | AI-vs-AI | Owner |
|---------------|--------|----------|--------------|----------|-------|
| M-NN | [complete] | [%] | [verified] | [reviewed] | GOV-NN |

### Test Suites & Verification Assets
| Asset | Location |
|-------|----------|
| Test suites (unit/integration/property/contract) | |
| Formal models + checked properties | |
| Conformance check results | |

### Cross-Phase Living Documents Phase 6 Inherits
| Document | Phase 5 Source | Update Protocol |
|----------|----------------|-----------------|
| Principle Scorecard v3.x | Step 13 | Phase 3 Step 06 protocol (Phase 6 produces v4.0) |
| Codebase + semantic commit history | Step 09 | — |
| ADR series | Phase 5 + prior ADRs | Standard ADR practice |

### Phase 6 Concern → Phase 5 Input Mapping
| Phase 6 Concern | Phase 5 Inputs |
|-----------------|----------------|
| Independent testing | Test suites, codebase |
| Security audit | Scan results, SEC-NN code, dependency audit |
| Performance validation | Benchmark results, instrumented code |
| Conformance audit | Conformance results, API contracts |
| Formal-verification review | Formal models + properties |
| Compliance verification | Audit-logging impl, data-handling code |
| Documentation review | Generated docs (DOC-NN) |
| Scorecard update | Scorecard v3.x, Step 06 protocol |

### Top Risks Carried Into Phase 6
[From the Step 13 scorecard risks, Step 11 accepted findings, and Step 14
systemic findings.]

---

## 12. Practitioner Override (If Applicable)

### 12.1 Override Tiered Authority Requirements
| Override Type | Required Authority |
|--------------|--------------------|
| Per-principle gate override | Practitioner |
| Cross-artifact consistency / traceability override | Practitioner |
| Phase 6 input completeness override | Practitioner |
| Phase 4 alignment override | Practitioner + Phase 4 authorization authority |
| Phase 3 alignment override | Practitioner + Phase 3 authorization authority |
| Phase 2 alignment override | Practitioner + Phase 2 authorization authority |

### 12.2 Override Documentation
[Used only if an override is applied; else "Not applicable — practitioner has
accepted the determination as stated."]

| Element | Detail |
|---------|--------|
| Determination being overridden | |
| Specific gate(s)/dimension(s) overridden | |
| Override authorized scope | [Full Phase 6 / specific work] |
| Override authority | [all required authorities per the tier table] |
| Override date | |
| Override rationale | [specific business/schedule reason — generic not acceptable] |
| Risk being accepted | [concrete] |
| Mitigation in place | |
| Conditions for revisit | |

If a Phase 4/3/2 alignment override is applied, it must acknowledge that
Phase 6 audit (and shipping) will be built on a prior-phase commitment the
framework has flagged as invalid, and articulate the specific downstream
consequences.

---

## 13. Authorization Record
| Element | Value |
|---------|-------|
| Authorization status | [Pending Practitioner Review / Authorized / Withheld] |
| Authorization scope | [Full Phase 6 / Partial — specify / Amendment required first] |
| Authorized by | [name and role] |
| Authorization date | |
| Phase 6 may begin | [Yes / Yes with conditions / No — Phase 5 remediation / No — Phase 4 amendment / No — Phase 3 amendment / No — Phase 2 amendment] |
| Re-review required when | |

---

## 14. Audit Trail
| Event | Date | Actor | Detail |
|-------|------|-------|--------|
| Readiness review conducted | | AI ([model]) | |
| Findings reviewed by practitioner | | | |
| [If applicable] Phase 4/3/2 amendment cycle initiated | | | |
| [If applicable] Amendment cycle(s) completed and re-runs done | | | |
| [If applicable] Step 15 re-review conducted | | | |
| Practitioner authorization | | | |
| [If applicable] Override applied | | | |
```

---

## Evaluation Checklist

Before the readiness review is accepted:

- [ ] All required inputs are present (all Phase 5 artifacts + Phase 4 + Phase
      3 + Phase 2 packages), or missing ones are named and reflected in the
      determination
- [ ] Each per-principle gate has a status with citation-backed basis applying
      the documented Phase 5 criteria
- [ ] Each Phase 5 artifact's completeness is assessed
- [ ] Cross-artifact consistency AND traceability (code → task → PRD → spec)
      are verified, consuming the Step 10/11/14 findings
- [ ] All three alignment dimensions (Phase 4, Phase 3, Phase 2) are
      evaluated; each failure produces a specific amendment package naming the
      artifact, the change, and the driving Phase 5 finding
- [ ] All Phase 6 concerns are evaluated for input completeness
- [ ] The overall determination is exactly one of the six outcomes — no
      seventh; if multiple NOT READY conditions apply, the deepest amendment
      path is named and all applicable packages populated
- [ ] If CONDITIONAL, every conditional has a named owner and target date
- [ ] If NOT READY (any variant), every blocking gap/amendment has a specific
      required action and the cycle process is documented
- [ ] No new code/verification/scoring is produced (the review evaluates)
- [ ] The Phase 6 Handoff Summary is concise and structured for Phase 6
      consumption
- [ ] The override section includes the tiered authority table — with the
      three amendment-path overrides at the highest tiers — even if no override
      is applied
- [ ] The authorization record is present (Pending until practitioner reviews)
- [ ] The audit trail accommodates the Phase 4 / Phase 3 / Phase 2 amendment
      cycle events

---

*Step 15 of 15 — final step in the Phase 5 Implementation Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `implementation.instructions.md`*
*Previous step: `step-14-cross-module-integration.prompt.md`*
*Next: Phase 6 — Testing & Audit*
