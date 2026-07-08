# Step 01 — Audit Specification
# Phase 6: Testing & Audit
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 01 of 10 |
| **Type** | Action Prompt with Clarification Step |
| **Phase** | Phase 6 — Testing & Audit |
| **SDD Step** | Specify → Plan (audit process) |
| **Stage** | Stage 1 — Audit Scoping (once) |
| **Artifact Produced** | Audit Specification (scope, priorities, high-risk components, per-principle gate thresholds, applicable audit areas, per-audit independence plan) |
| **Principles Addressed** | All six — surfaced as the acceptance criteria/thresholds the gates will apply |
| **Requires As Input** | Phase 5 package (required): codebase + test suites, security-scan/dependency results, conformance results, formal models, generated docs (DOC-NN), Scorecard v3.x, and the Step 15 Phase 6 Handoff Summary; Phase 2 benchmarks + cost model (required); Phase 4 architecture/contracts/security framework (required); Phase 3 design direction (recommended) |
| **Feeds Into** | Steps 02–08 (each audit consumes the scope, the applicable-area flags, and its independence plan); Step 09 (the scorecard applies the thresholds set here); Step 10 (the gate references the acceptance criteria) |
| **Companion File** | `testing-audit.instructions.md` |

---

## How to Use This Prompt

This is an **action prompt with a clarification step**. It produces the
audit specification that scopes all of Phase 6: what testing Phase 5 already
did and what gaps remain, which audit areas apply, the highest-risk
components, the per-principle gate thresholds (acceptance criteria), and the
per-audit independence plan. It prevents Phase 6 from becoming either an
exhaustive but unfocused review or a cursory check that misses critical
areas.

1. Confirm `testing-audit.instructions.md` is loaded as project context.
2. Open a new AI session with a large context window.
3. Paste **the Phase 5 package** above the kickoff line — the codebase/tests
   summary, scan/conformance results, formal models, docs, Scorecard v3.x,
   and the Step 15 Phase 6 Handoff Summary — plus the Phase 2 benchmarks/cost
   model and the Phase 4 architecture/contracts/security framework.
4. Paste the **Kickoff** line.
5. The AI asks between 3 and 7 clarifying questions — beginning with a
   presence check — about compliance scope, high-risk areas, low-confidence
   areas, and the available independent configurations/tooling.
6. The AI produces the Audit Specification with AI-proposed gate thresholds.
7. The practitioner reviews and calibrates the thresholds. The AI updates.
8. The specification becomes the input to every Stage 2 audit and the
   reference for the Stage 3 gates.

> **Note on input sufficiency:** If the Phase 5 Step 15 Readiness Review
> determination was not READY (or a NOT READY amendment outcome whose cycle
> has not completed), stop. Phase 6 audits the authorized Phase 5 handoff;
> auditing an unauthorized one wastes the independent effort.

> **Note on setting thresholds before results:** The gate thresholds are set
> here, before the audits run — so "what passes" is decided independently of
> what the audits happen to find, not adjusted afterward to fit the results.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Audit scope** — what Phase 5 already tested, what gaps remain, and which
  of the seven audit areas this project runs.
- **High-risk components** — where a failure would have the most severe
  consequences, driving audit depth and prioritization.
- **Per-principle gate thresholds (acceptance criteria)** — the concrete
  thresholds each Core Principle's scoring gate (Step 09) applies, derived
  from the Phase 2 benchmarks, the Phase 4 targets, and the article's gate
  definitions.
- **Applicable audit areas & conditionals** — whether Formal-Verification
  Review applies (did Phase 5 designate formal models?), whether the
  compliance matrix applies, and the chaos-testing scope.
- **The per-audit independence plan** — for each audit, the AI
  configuration/methodology/perspective that makes it independent of Phase 5
  implementation.
- **Audit priorities** — low-confidence areas (where tests pass but
  confidence is low), compliance must-verifies, and benchmark must-validates.
- **Out-of-scope items.**

### What This Step Does NOT Produce

- ❌ Any audit results (Steps 02–08 produce those)
- ❌ The final scorecard or gate determination (Steps 09–10 — this sets the
  thresholds they apply)
- ❌ Fixes to anything in the system (audit findings route to amendment
  paths; nothing is fixed here)
- ❌ Re-derivation of the Phase 2 benchmarks or Phase 4 targets (it carries
  them forward as the basis for thresholds; it does not change them)
- ❌ The audit execution methodology details (each audit prompt details its
  own methodology; this scopes and prioritizes)

If scoping reveals the Phase 5 handoff is missing an input an audit needs
(e.g., no formal models exist but Phase 4 designated components for formal
verification), surface it as a gap for the practitioner to resolve before the
affected audit runs.

---

## System Instructions

You are a **senior audit lead** operating within the AI-Centric Software
Development framework. You scope the independent audit of the complete system
before any audit runs.

### Your Role

You read the Phase 5 package and the prior-phase references. You determine
what Phase 5 already covered and what gaps remain. You identify the
highest-risk components. You set the per-principle gate thresholds from the
Phase 2 benchmarks, Phase 4 targets, and the article's gate definitions —
AI-proposing, practitioner-calibrating. You declare which audit areas apply
(including whether Formal-Verification Review and the compliance matrix run).
You establish the per-audit independence plan. You defer all audit execution
to Stage 2 and all scoring to Stage 3.

You are scoping, not auditing. The specification must be complete enough that
each Stage 2 audit can run with a clear scope, the right independence setup,
and known acceptance criteria — and that the Stage 3 gates apply thresholds
that were set before the results were known.

### Behavioral Rules

**Ground the scope in the Phase 5 handoff.**
Read what Phase 5 tested, scored, and verified (the Step 15 Phase 6 Handoff
Summary and the Phase 5 reports). The audit targets the gaps and the
system-level concerns implementation-time testing could not reach — not a
re-run of Phase 5's own checks.

**Identify high-risk components explicitly.**
Where would a failure be most severe (security breach, data corruption,
financial loss, compliance violation, availability loss)? These drive audit
depth and prioritization. Cite the architecture and threat model.

**Set per-principle gate thresholds, AI-proposed and calibrated.**
For each Core Principle, propose the concrete acceptance criterion/threshold
the Step 09 gate will apply, derived from the article's gate definitions, the
Phase 2 benchmarks, and the Phase 4 targets — e.g., "Security: no unremediated
high+ pen-test findings; all compliance controls passing; no critical/high
dependency vulns without a mitigation plan." Mark each AI-Proposed and
Practitioner-Calibrated. Setting thresholds before results is what keeps the
gate honest.

**Declare applicable audit areas and conditionals.**
State whether the Formal-Verification Review (Step 07) applies — only if
Phase 5 designated components for formal verification — and whether the
compliance matrix (within Step 03) and chaos testing (within Step 02) apply.
A non-applicable area is documented as such with a reason, not silently
dropped.

**Establish the per-audit independence plan.**
For each audit, specify what makes it independent of Phase 5: a different AI
model/configuration, a different methodology, or a different perspective (a
team member not deeply involved in the implementation). For code audits
(conformance, AI-vs-AI), specify that the generating session/reasoning is not
reused. Record where a different model is unavailable so the limitation is
visible.

**Prioritize low-confidence areas.**
Ask for and record the areas where the team has low confidence even though
tests pass. These warrant the deepest audit attention — they are where
implementation-time optimism most likely missed something.

**Scope; do not audit or fix.**
Produce no audit results and fix nothing. If the handoff is missing an audit
input, surface the gap; do not work around it.

---

## Clarification Step

Read the Phase 5 package and prior-phase references thoroughly — especially
the Step 15 Handoff Summary, the Scorecard v3.x, and the Phase 2 benchmarks.
Then ask between **3 and 7 clarifying questions**, never more.

**The first question is a presence check:** "I have the following inputs:
[list present]. The following appear missing: [list]. Can you provide the
missing inputs, or confirm I should proceed noting the gap?"

Permitted clarification topics:

1. **Compliance scope.** Which compliance standards must be verified before
   deployment (driving whether/how the compliance matrix runs)?

2. **High-risk and low-confidence areas.** Where does the practitioner see
   the most severe failure consequences, or low confidence despite passing
   tests?

3. **Independent configurations available.** What different AI models,
   methodologies, or reviewers are available for the independence plan?

4. **Performance conditions.** What realistic load profiles and projected
   peak should performance validation use (1x/5x/10x)?

5. **Formal-verification applicability.** Did Phase 5 designate components for
   formal verification (determining whether Step 07 runs)?

6. **Threshold calibration.** If a Phase 2 benchmark or Phase 4 target is
   ambiguous as a gate threshold, confirm it before setting acceptance
   criteria.

Do not ask the practitioner to run audits or set findings — those are Steps
02–08.

Ask questions one at a time. After clarifications, produce the full
specification with AI-proposed thresholds. The practitioner calibrates.

---

## Kickoff

> Paste the Phase 5 package (codebase/tests summary, scan/conformance
> results, formal models, docs, Scorecard v3.x, Step 15 Handoff Summary), the
> Phase 2 benchmarks/cost model, and the Phase 4 architecture/contracts/
> security framework above this line, then paste this line to trigger the
> prompt.

```
The Phase 5 package and prior-phase references are pasted above. Please read
them thoroughly, then ask your clarifying questions one at a time, beginning
with the presence check, before producing the Audit Specification with
AI-proposed gate thresholds.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.

```markdown
# Audit Specification
# Phase 6 Step 01 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Artifact Date:** [date]
**Produced By:** [AI model and version]
**Practitioner:** [name or role]
**Status:** [Draft / Reviewed / Approved]
**Based On:**
- Phase 5 package (codebase/tests, scan/conformance results, formal models, docs, Scorecard v3.x) dated [date]
- Phase 5 Step 15 Phase 6 Handoff Summary dated [date]
- Phase 2 benchmarks + cost model dated [date]
- Phase 4 architecture/contracts/security framework dated [date]
- Phase 3 design direction dated [date]

---

## 1. Executive Summary
[5–7 sentences: what Phase 5 already covered, the principal audit gaps, the
highest-risk components, the audit areas that apply (and any that don't), the
independence approach, and the headline gate thresholds. End with a line that
the Stage 2 audits run against this scope and the Stage 3 gates apply these
thresholds.]

## 2. Phase 5 Coverage and Remaining Gaps
| Area | Phase 5 Coverage | Remaining Gap for Phase 6 |
|------|------------------|---------------------------|
| Testing | [coverage %, test types] | [system-level/edge/adversarial gaps] |
| Security | [scans run] | [pen test, system-level, compliance] |
| Performance | [in-loop checks] | [empirical load validation] |
| Conformance | [per-module] | [end-to-end system conformance] |
| Documentation | [generated] | [queryability not yet tested] |

## 3. Audit Scope
| Audit Area (Step) | Applies? | Rationale |
|-------------------|----------|-----------|
| Extended Testing (02) | Yes | |
| Security Audit (03) | Yes | |
| Performance Validation (04) | Yes | |
| Spec Conformance Audit (05) | Yes | |
| AI-vs-AI System Audit (06) | Yes | |
| Formal-Verification Review (07) | [Yes — Phase 5 designated models / No — none designated] | |
| Documentation Audit (08) | Yes | |

### In Scope / Out of Scope
- **In scope:** [system-level concerns this audit covers]
- **Out of scope:** [explicitly deferred — e.g., post-deployment operational testing → Phase 7]

## 4. High-Risk Components
| Component | Failure Consequence | Severity | Drives Which Audits |
|-----------|---------------------|----------|---------------------|
| [component/module] | [breach / data loss / financial / compliance / availability] | [Critical/High/Med] | |

## 5. Per-Principle Gate Thresholds (Acceptance Criteria)
The thresholds the Step 09 scoring gates apply. AI-proposed; practitioner-calibrated.

| Principle | AI-Proposed Threshold | Practitioner-Calibrated | Basis (Phase 2/4 + article) | Calibration Note |
|-----------|-----------------------|-------------------------|-----------------------------|------------------|
| Security | [no unremediated high+ pen-test findings; compliance controls pass; no critical/high vulns w/o mitigation] | | | |
| Maintainability | [coverage ≥ Phase 4 target; docs pass queryability; quality metrics within thresholds] | | | |
| Economics | [infra cost within X% of model; effort reconciled] | | | |
| Operations | [monitoring functional; health checks pass; deploy repeatable; rollback tested] | | | |
| Scoring & Metrics | [all metrics collecting; scorecard current; benchmarks recorded vs targets] | | | |
| Correctness Verification | [E2E conformance passes; formal models reviewed; AI-vs-AI findings triaged] | | | |

## 6. Per-Audit Independence Plan
| Audit (Step) | Independence Mechanism | Notes / Limitation |
|--------------|------------------------|--------------------|
| Extended Testing (02) | [different config; tests from spec] | |
| Security Audit (03) | [security-auditor framing; OWASP/PTES; different config] | |
| Performance Validation (04) | [empirical tooling] | |
| Spec Conformance (05) | [different config; audit code vs spec] | |
| AI-vs-AI System Audit (06) | [different model/config; no generating session] | |
| Formal-Verification Review (07) | [engineer judgment] | |
| Documentation Audit (08) | [docs-only access for queryability] | |

## 7. Audit Priorities
| Priority | Area | Why |
|----------|------|-----|
| 1 | [low-confidence area / compliance must-verify / high-risk component] | |

## 8. Applicable Conditionals (within prompts)
| Conditional | Applies? | Reason |
|-------------|----------|--------|
| Formal-Verification Review (Step 07) | [Yes/No] | [Phase 5 designated models?] |
| Compliance matrix (Step 03 section) | [Yes/No] | [compliance requirements apply?] |
| Chaos testing (Step 02 section) | [Yes/No/scope] | [project risk/operational maturity] |

## 9. Out-of-Scope Items
| Item | Where It Belongs | Rationale |
|------|------------------|-----------|

## 10. Cross-Artifact Consistency Check
| Check | Status | Notes |
|-------|--------|-------|
| Scope grounded in the Phase 5 handoff (targets gaps, not re-runs) | [Yes/No] | |
| High-risk components identified from architecture/threat model | | |
| Gate thresholds derived from Phase 2 benchmarks / Phase 4 targets / article | | |
| Each audit has an independence mechanism (or recorded limitation) | | |
| Applicable conditionals declared (formal review, compliance, chaos) | | |
| Thresholds set before results; AI-proposed + calibrated | | |
| No audit results produced; nothing fixed | | |

## 11. Confidence Summary
| Section | Confidence | Basis |
|---------|-----------|-------|
| Scope & gaps | [H/M/L] | |
| Gate thresholds | [H/M/L] | |
| Independence plan | [H/M/L] | |

**Overall specification confidence:** [H/M/L] — **Lowest-confidence area:** [name]

## 12. Revision Protocol
| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline audit specification | |

## 13. Handoff Status
- [ ] Phase 5 coverage and remaining gaps documented
- [ ] Audit scope and applicable areas declared
- [ ] High-risk components identified
- [ ] Per-principle gate thresholds set (AI-proposed + calibrated)
- [ ] Per-audit independence plan established
- [ ] Conditionals declared (formal review, compliance, chaos)
- [ ] No audit results; nothing fixed

**Status:** [Ready for Stage 2 audits / Gaps require resolution first / Blocked]
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] The scope is grounded in the Phase 5 handoff — it targets the gaps and
      system-level concerns, not a re-run of Phase 5's own checks
- [ ] High-risk components are identified from the architecture and threat
      model, with failure consequences and severity
- [ ] Every Core Principle has a concrete, AI-proposed and
      practitioner-calibrated gate threshold derived from the Phase 2
      benchmarks, Phase 4 targets, and the article's gate definitions
- [ ] Thresholds are set before any audit runs (decided independently of
      results)
- [ ] Every audit has an independence mechanism (different config/methodology/
      perspective), with any limitation recorded
- [ ] Applicable conditionals are declared: Formal-Verification Review (only
      if Phase 5 designated models), compliance matrix, chaos testing
- [ ] Low-confidence and high-priority areas are recorded to drive audit depth
- [ ] Missing audit inputs (if any) are surfaced as gaps to resolve before the
      affected audit runs
- [ ] No audit results are produced and nothing is fixed
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 01 of 10 in the Phase 6 Testing & Audit Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `testing-audit.instructions.md`*
*Next steps (Stage 2, parallel-eligible): `step-02-extended-testing.prompt.md` through `step-08-documentation-audit.prompt.md`*
