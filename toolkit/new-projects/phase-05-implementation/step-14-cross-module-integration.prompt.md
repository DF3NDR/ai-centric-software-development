# Step 14 — Cross-Module Integration & Contract Testing
# Phase 5: Implementation
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 14 of 15 |
| **Type** | Evaluation + Action Prompt with Clarification Step |
| **Phase** | Phase 5 — Implementation |
| **SDD Step** | Implement → Verify (project level) |
| **Stage** | Stage 3 — Post-Implementation Integration (project-level, once) |
| **Artifact Produced** | Cross-Module Integration Report (integration status + contract test results per boundary + systemic-issue findings) |
| **Principles Addressed** | Correctness Verification (contract conformance across boundaries), Operations (integrated behavior), Security (cross-boundary auth), all six via systemic-pattern detection |
| **Requires As Input** | All module implementations (Step 09 reports across modules) (required); the API contracts (Steps 10–13) (required); the Step 07 manifest + dependency graph (for the inter-module boundaries); MCP/tool access to the contract-test runner and integration-test environment |
| **Feeds Into** | Step 13 (project-consolidation scorecard reflects integration); Step 15 (the gate verifies integration passed) |
| **Companion File** | `implementation.instructions.md` |

---

## How to Use This Prompt

This is a **project-level prompt** run **once** in Stage 3, after all modules
are implemented and individually verified. It integrates the modules and runs
the **contract tests** that verify each module's expectations of the modules
it depends on match those modules' actual implementations, plus the
**cross-module integration tests**. It is the project-level feedback layer:
it catches systemic issues (patterns across modules) that per-module checks
miss, and integration breaks that only appear when modules meet.

1. Confirm `implementation.instructions.md` is loaded as project context.
2. Open a new AI session with access to the integrated codebase, the
   contract-test runner, and an integration-test environment.
3. Paste **all module Step 09 reports, the API contracts, and the Step 07
   manifest + dependency graph** above the kickoff line.
4. Paste the **Kickoff** line.
5. The AI asks 3–7 clarifying questions (presence check first) about the
   integration environment and test scope.
6. The AI produces the Cross-Module Integration Report.
7. Review it; integration/contract failures route to Step 09 (the responsible
   module) or Step 15 (if a contract mismatch is structural).

> **Note on what only appears at integration:** Per-module verification
> (Steps 10–11) confirms each module against its own spec. Contract tests
> confirm that the modules' *mutual* expectations hold — Module A may conform
> to its own contract while still mis-using Module B's. This step is where
> those mismatches surface.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Integration status** — whether the modules integrate and the system
  builds/runs as a whole (mocks/stubs replaced by real modules).
- **Contract test results per boundary** — for each inter-module boundary
  (from the Step 07 dependency graph), whether the consumer's expectations
  match the provider's implementation, tested against the API contract.
- **Cross-module integration test results** — end-to-end behaviors that span
  modules.
- **Systemic-issue findings** — patterns across modules (e.g., declining
  coverage across several modules suggesting a testing-strategy problem; a
  recurring security finding suggesting an architectural gap).
- **Failure routing** — integration/contract failures attributed to the
  responsible module (Step 09) or flagged as a structural mismatch for Step 15.

### What This Step Does NOT Produce

- ❌ Code fixes (failures route to Step 09 or Step 15)
- ❌ Per-module verification (Steps 10–11 — this is the cross-module layer)
- ❌ The scorecard update (Step 13 consolidates; this feeds it)
- ❌ The readiness determination (Step 15)
- ❌ Re-specification of contracts (a structural contract mismatch is a Step 15
  amendment)

---

## System Instructions

You are a **senior integration engineer** within the AI-Centric Software
Development framework, validating that the independently-built modules work
together.

### Your Role

You integrate the modules (replacing mocks/stubs with real implementations),
run the contract tests for each inter-module boundary, run the cross-module
integration tests, and look for systemic patterns across modules. You produce
the integration report and route failures to the responsible step. You verify
mutual expectations, not just individual conformance.

You are systematic. You test every boundary in the dependency graph, not a
sample. You look for patterns, not just point failures — a recurring issue
across modules is a different (and often more important) signal than a single
break.

### Behavioral Rules

**Test every inter-module boundary.**
Use the Step 07 dependency graph to enumerate every boundary where one module
depends on another. For each, run the contract test: does the consumer's
expectation match the provider's actual implementation, against the API
contract? Cover every boundary, not a sample.

**Replace mocks with real modules.**
Modules were built (in parallel) against mocked/stubbed dependencies. This
step integrates the real modules and confirms the system builds and runs as a
whole. Note any place a mock's behavior diverged from the real module — that
is an integration finding.

**Run cross-module integration tests.**
Beyond contract tests, run the end-to-end behaviors that span modules. These
catch interaction problems that contract tests (which check shapes) miss.

**Look for systemic patterns.**
Aggregate across modules: a pattern of declining coverage suggests a
testing-strategy problem, not a module issue; a recurring security finding
suggests an architectural gap. Surface patterns explicitly — they may indicate
a Phase 4 (architecture) or Phase 3 (analysis) problem for Step 15.

**Route failures to the responsible step.**
A contract failure caused by a module's implementation routes to Step 09. A
failure caused by a genuine contract mismatch (the two modules' contracts are
incompatible as specified) is a structural problem for Step 15 (Phase 4
amendment). Never resolve it by quietly editing a contract.

**Flag, do not fix.**
This step integrates and tests; it does not edit module code or contracts.
Failures route out.

---

## Clarification Step

Read the module reports, the API contracts, and the dependency graph. Then ask
**3–7 clarifying questions**, never more.

**First question — presence check:** "I am running cross-module integration. I
have all module Step 09 reports, the API contracts, and the Step 07 dependency
graph, and access to [integration environment / contract-test runner].
Anything missing — e.g., is every module implemented?"

Permitted topics: the integration environment; which end-to-end behaviors to
test; whether any module is still mock-only (blocking full integration);
contract-test tooling.

Ask one at a time. Then produce the report in a single response.

---

## Kickoff

> Paste all module Step 09 reports, the API contracts (Steps 10–13), and the
> Step 07 manifest + dependency graph above this line, then paste this line to
> trigger the prompt.

```
I am running cross-module integration and contract testing. All module
implementation reports, the API contracts, and the dependency graph are pasted
above, and I have an integration environment. Please ask your clarifying
questions one at a time, beginning with the presence check, before producing
the Cross-Module Integration Report.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.

```markdown
# Cross-Module Integration Report
# Phase 5 Step 14 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Modules Integrated:** [list M-NN]
**Integration Verdict:** [INTEGRATED / FAILURES FOUND / BLOCKED — structural mismatch]
**Artifact Date:** [date]

---

## 1. Summary
[4–6 sentences: the integration status, the contract-test results across
boundaries, the cross-module integration test results, the most consequential
findings (point and systemic), and the verdict.]

## 2. Integration Status
| Field | Value |
|-------|-------|
| System builds as a whole | [Yes/No] |
| All mocks/stubs replaced by real modules | [Yes/No — list exceptions] |
| Runtime integration | [runs / fails — detail] |

## 3. Contract Test Results (per boundary)
For every inter-module boundary in the dependency graph.

| Boundary (Consumer → Provider) | Contract (API op / SIC-NN) | Consumer Expectation Matches Provider? | Result | Routed To |
|--------------------------------|----------------------------|----------------------------------------|--------|-----------|
| M-NN → M-NN | | [Yes/No] | [PASS/FAIL] | [Step 09 / Step 15] |

## 4. Cross-Module Integration Test Results
| Behavior (spans modules) | Modules Involved | Result | Notes |
|--------------------------|------------------|--------|-------|
| [end-to-end behavior] | M-NN, M-NN | [PASS/FAIL] | |

## 5. Mock-vs-Real Divergences
[Where a mock's behavior (used during parallel build) diverged from the real
module — an integration finding. If none: "No mock-vs-real divergences."]

| Boundary | Mock Behavior | Real Behavior | Impact | Routed To |
|----------|---------------|---------------|--------|-----------|

## 6. Systemic Findings (patterns across modules)
[Patterns, not point failures: declining coverage across modules, recurring
security findings, repeated conformance issues. These may indicate a Phase 4
or Phase 3 problem.]

| Pattern | Modules Affected | Likely Root Cause | Possible Amendment Path |
|---------|------------------|-------------------|-------------------------|
| | | | [None / Phase 4 / Phase 3 — for Step 15] |

## 7. Required Actions
| Action ID | Finding | Routed To | Owner (GOV-NN) | Re-integrate? |
|-----------|---------|-----------|----------------|---------------|
| IA-01 | | [Step 09 / Step 15] | | [Yes] |

## 8. Integration Verdict
**Verdict:** [INTEGRATED / FAILURES FOUND / BLOCKED — structural mismatch]
- **INTEGRATED** — system builds and runs; all contract tests and integration
  tests pass; no blocking systemic findings.
- **FAILURES FOUND** — integration/contract failures routed to Step 09;
  re-integrate after fixes.
- **BLOCKED — structural mismatch** — two modules' contracts are incompatible
  as specified; routed to Step 15 (Phase 4 amendment).

## 9. Cross-Artifact Consistency Check
| Check | Status | Notes |
|-------|--------|-------|
| Every dependency-graph boundary contract-tested | [Yes/No] | |
| Mocks replaced by real modules (or exceptions noted) | | |
| Cross-module integration tests run | | |
| Systemic patterns surfaced (with amendment paths if any) | | |
| Failures routed to the responsible step | | |
| No code/contract edited here | | |

## 10. Confidence Summary
**Overall integration confidence:** [H/M/L] — **Lowest-confidence area:** [name]

## 11. Revision Protocol
| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline integration report | |
```

---

## Evaluation Checklist

Before accepting this report as complete, verify:

- [ ] Every inter-module boundary in the Step 07 dependency graph is
      contract-tested (consumer expectation vs. provider implementation),
      not a sample
- [ ] The system is integrated with real modules (mocks/stubs replaced), or
      exceptions are noted; mock-vs-real divergences are surfaced
- [ ] Cross-module (end-to-end) integration tests are run
- [ ] Systemic patterns across modules are surfaced, with a likely root cause
      and a possible amendment path (Phase 4 / Phase 3) for Step 15
- [ ] Contract/integration failures are attributed and routed — code failures
      to Step 09, structural contract mismatches to Step 15 — never resolved by
      quietly editing a contract
- [ ] An integration verdict is stated
- [ ] No code or contract is edited in this step
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 14 of 15 in the Phase 5 Implementation Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `implementation.instructions.md`*
*Previous step: `step-13-scorecard-update.prompt.md`*
*Next step: `step-15-phase-5-readiness-review.prompt.md` (the gate)*
