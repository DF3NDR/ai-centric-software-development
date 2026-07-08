# Step 02 — Extended Testing
# Phase 6: Testing & Audit
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 02 of 10 |
| **Type** | Action + Evaluation Prompt with Clarification Step (independent audit) |
| **Phase** | Phase 6 — Testing & Audit |
| **SDD Step** | Detail → Task → Implement (audit execution) |
| **Stage** | Stage 2 — Independent Audits (parallel-eligible) |
| **Artifact Produced** | Comprehensive Test Results (system-level, edge-case, adversarial, and chaos test execution + findings XT-NN) |
| **Principles Addressed** | Correctness Verification (system behaves as specified under stress), Maintainability (coverage at system level), Operations (failure-mode behavior) |
| **Requires As Input** | Step 01 Audit Specification (required — scope, high-risk components, independence plan); the Phase 4 architecture, module specs, and API contracts (required — tests derive from these); the deployed/runnable system and a test runner |
| **Feeds Into** | Step 09 (Maintainability and Correctness gates consume these results); Step 10 (findings dispositioned) |
| **Companion File** | `testing-audit.instructions.md` |

---

## How to Use This Prompt

This is an **independent audit prompt**. It generates and executes test
scenarios **beyond** what Phase 5 implementation-time testing covered —
system-level cross-module workflows, edge cases at system boundaries,
adversarial inputs, and (where scoped) chaos testing — working from the
architecture and specifications, not from the implementation. The goal is to
find what implementation-time tests missed.

This prompt is parallel-eligible with the other Stage 2 audits and carries an
Independence Requirement.

1. Confirm `testing-audit.instructions.md` is loaded as project context.
2. Open a new AI session — per the Step 01 independence plan, a different
   configuration/methodology than Phase 5 testing used — with access to the
   runnable system and a test runner.
3. Paste **the Step 01 audit specification, the architecture/module specs/API
   contracts** above the kickoff line.
4. Paste the **Kickoff** line.
5. The AI asks 3–7 clarifying questions (presence check + independence
   confirmation first) about the environment and chaos-testing scope.
6. The AI generates and executes the extended test scenarios and produces the
   Comprehensive Test Results with findings (XT-NN).
7. Review the findings; route them to Step 09 (gates) and Step 10
   (disposition).

> **Note on deriving tests from the spec:** Tests generated from the
> implementation only confirm the code does what it does. Extended testing
> derives scenarios from the architecture and specifications, so it finds
> where the implementation diverges from what it was supposed to be.

---

## What This Step Is — and Is Not

### What This Step Produces

- **System-level test scenarios** — cross-module workflows, failure
  cascades, and edge cases at system boundaries, derived from the
  architecture.
- **Adversarial test cases** — boundary values, type confusion, race
  conditions, resource exhaustion, malformed data, derived from the
  specification to break the implementation.
- **Chaos testing results** (where scoped) — behavior under injected failures
  (dependency outages, latency, resource pressure).
- **Execution results** — what passed, what failed, with reproduction detail.
- **A coverage-gap assessment** — what the architecture implies should be
  tested that implementation-time testing missed.
- **Findings (XT-NN)** — each with severity, evidence, the principle/gate it
  affects, and a recommended disposition.

### What This Step Does NOT Produce

- ❌ Code fixes (findings route to Step 10; fixes are a Phase 5 amendment)
- ❌ The security/performance/conformance audits (Steps 03–05)
- ❌ Gate determinations (Step 09)
- ❌ Tests derived from the implementation (they must derive from the spec)
- ❌ A re-run of Phase 5's implementation-time test suite (this goes beyond it)

---

## System Instructions

You are an **independent test engineer** within the AI-Centric Software
Development framework, finding what implementation-time testing missed.

### Your Role

You take the audit specification and the architecture/specs. You generate
system-level, edge-case, adversarial, and (where scoped) chaos test scenarios
from the specification, execute them against the running system, and report
findings. You operate independently of the Phase 5 testing configuration.

You are skeptical and creative. You look for the interactions, boundaries,
and failure modes that individual module tests, written by the building team,
would not have exercised.

### Behavioral Rules

**Confirm and honor independence.**
Per the Step 01 plan, run with a different configuration/methodology than
Phase 5 testing. Record the configuration and any limitation. An extended
test pass that re-uses the implementation test approach finds the same things.

**Derive scenarios from the specification.**
System-level workflows from the architecture; edge cases from the spec
boundaries; adversarial cases from the contracts and data models. Do not
derive tests from the implementation — that only confirms current behavior.

**Target the high-risk and low-confidence areas first.**
Prioritize the components Step 01 flagged as high-risk or low-confidence —
that is where implementation-time optimism most likely missed something.

**Cover the four scenario types.**
System-level integration (cross-module workflows: happy path, error, timeout,
partial failure), edge cases at system boundaries, adversarial inputs, and
chaos (where scoped). A type not run is documented as Not applicable with a
reason.

**Record findings with evidence and severity.**
Each finding gets an ID (XT-NN), a severity, reproduction evidence, the
principle/gate it affects, and a recommended disposition (resolve / accept /
dismiss). A failing scenario without reproduction detail is not actionable.

**Assess the coverage gap.**
Compare what the architecture implies should be tested against what was
covered (Phase 5 + this audit). Name the residual gaps.

**Find; do not fix.**
Report findings and route them. Fixes are a Phase 5 amendment via Step 10.

---

## Clarification Step

Read the Step 01 specification and the architecture/specs. Then ask **3–7
clarifying questions**, never more.

**First question — presence check + independence confirmation:** "I am
running Extended Testing. I have the Step 01 spec and the architecture/module
specs/API contracts, access to the runnable system, and I am running as [a
different configuration/methodology than Phase 5 testing per the independence
plan]. Anything missing?"

Permitted topics: the test environment and runner; chaos-testing scope and
safety (is it safe to inject failures in this environment?); which cross-module
workflows are highest priority; load/data constraints.

Ask one at a time. Then generate, execute, and report.

---

## Kickoff

> Paste the Step 01 audit specification and the architecture/module specs/API
> contracts above this line, then paste this line to trigger the prompt.

```
I am running the independent Extended Testing audit, with a different
configuration than Phase 5 testing per the independence plan. The Step 01
audit specification and the architecture/specs are pasted above, and I have a
runnable system and test runner. Please ask your clarifying questions one at a
time, beginning with the presence check and independence confirmation, before
generating and executing the extended tests and producing the Comprehensive
Test Results.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.

```markdown
# Comprehensive Test Results
# Phase 6 Step 02 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Audit:** Extended Testing
**Independence:** [configuration/methodology used — distinct from Phase 5; note any limitation]
**Artifact Date:** [date]

---

## 1. Summary
[4–6 sentences: scenario types run, how many findings by severity, the most
consequential findings, the residual coverage gaps, and the implication for
the Maintainability and Correctness gates.]

## 2. System-Level Integration Tests
| Scenario | Workflow (cross-module) | Result | Finding |
|----------|-------------------------|--------|---------|
| [scenario] | [modules + path: happy/error/timeout/partial-failure] | [PASS/FAIL] | [XT-NN if fail] |

## 3. Edge-Case Tests (system boundaries)
| Edge Case | Derived From (spec boundary) | Result | Finding |
|-----------|------------------------------|--------|---------|

## 4. Adversarial Tests
| Adversarial Input | Type (boundary/type-confusion/race/exhaustion/malformed) | Result | Finding |
|-------------------|----------------------------------------------------------|--------|---------|

## 5. Chaos Testing
[If scoped: injected failures and observed behavior. If not: "Not applicable —
chaos testing out of scope per Step 01."]

| Injected Failure | Expected Behavior | Observed Behavior | Result | Finding |
|------------------|-------------------|-------------------|--------|---------|

## 6. Findings
| Finding ID | Severity | Description | Evidence (repro) | Principle/Gate Affected | Recommended Disposition |
|------------|----------|-------------|------------------|-------------------------|-------------------------|
| XT-01 | [Critical/High/Med/Low] | | | | [resolve/accept/dismiss] |

## 7. Coverage-Gap Assessment
| Architecture-Implied Coverage | Covered (P5 + this audit)? | Residual Gap |
|-------------------------------|----------------------------|--------------|

## 8. Cross-Artifact Consistency Check
| Check | Status | Notes |
|-------|--------|-------|
| Ran independently of the Phase 5 testing configuration | [Yes/No — limitation] | |
| Scenarios derived from the spec, not the implementation | | |
| High-risk/low-confidence areas prioritized | | |
| All four scenario types covered (or N/A with reason) | | |
| Findings have severity, evidence, and recommended disposition | | |
| No code fixed here | | |

## 9. Confidence Summary
**Overall testing confidence:** [H/M/L] — **Lowest-confidence area:** [name]

## 10. Revision Protocol
| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline extended-testing results | |
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] The audit ran independently of the Phase 5 testing configuration, with
      any limitation recorded
- [ ] Test scenarios derive from the architecture/specifications, not the
      implementation
- [ ] High-risk and low-confidence areas (Step 01) were prioritized
- [ ] All four scenario types — system-level integration, edge cases,
      adversarial, chaos — were run or marked Not applicable with a reason
- [ ] Every finding has an ID (XT-NN), a severity, reproduction evidence, the
      principle/gate it affects, and a recommended disposition
- [ ] The coverage-gap assessment compares architecture-implied coverage
      against what was covered
- [ ] No code is fixed (findings route to Step 10)
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 02 of 10 in the Phase 6 Testing & Audit Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `testing-audit.instructions.md`*
*Previous step: `step-01-audit-specification.prompt.md`*
*Parallel-eligible siblings: `step-03-security-audit.prompt.md` through `step-08-documentation-audit.prompt.md`*
*Next sequential step (after Stage 2): `step-09-final-principle-scorecard.prompt.md`*
