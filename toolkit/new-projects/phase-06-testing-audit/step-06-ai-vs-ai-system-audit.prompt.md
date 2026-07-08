# Step 06 — AI-vs-AI System Audit
# Phase 6: Testing & Audit
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 06 of 10 |
| **Type** | Evaluation Prompt with Clarification Step — **MUST run with a SEPARATE AI configuration** |
| **Phase** | Phase 6 — Testing & Audit |
| **SDD Step** | Implement → Verify (audit execution, independent) |
| **Stage** | Stage 2 — Independent Audits (parallel-eligible) |
| **Artifact Produced** | AI-vs-AI System Audit (independent system-level review of the entire codebase vs. the original specifications; findings AA-NN) |
| **Principles Addressed** | Correctness Verification (primary), Security & Maintainability (drift, inconsistency, architectural compliance) |
| **Requires As Input** | Step 01 Audit Specification (required); the complete codebase (required); the original Phase 4 specifications — architecture, contracts, data schemas, shared standards (required). **Run with a different model/configuration than Phase 5 generation and Phase 5's module-level AI-vs-AI review; do NOT provide the generating sessions' reasoning.** |
| **Feeds Into** | Step 09 (the Correctness Verification gate); Step 10 (every finding triaged and dispositioned) |
| **Companion File** | `testing-audit.instructions.md` |

---

## How to Use This Prompt

This is the **system-level AI-vs-AI audit** — the elevation of Phase 5's
module-level AI-vs-AI review to the whole codebase. An independent AI
configuration reviews the entire system against the original specifications,
looking for what disciplined building still misses: specification drift,
undocumented behavior, cross-module inconsistencies, and architectural
non-compliance.

It **must** run with a different model, prompt configuration, or review
framework than Phase 5 used, and without the generating sessions' reasoning.

1. Confirm `testing-audit.instructions.md` is loaded as project context.
2. Open a new AI session **using a different model/configuration** than
   Phase 5 generation and module-level review used.
3. Paste **the Step 01 spec, the complete codebase, and the original Phase 4
   specifications** above the kickoff line — **not** the generating sessions'
   reasoning.
4. Paste the **Kickoff** line.
5. The AI asks at most 3 clarifying questions (presence check + independence
   confirmation first), then audits the codebase independently.
6. The AI produces the AI-vs-AI System Audit with findings (AA-NN).
7. The team triages every finding (Step 10); not every finding requires
   action, but every finding must be reviewed and dispositioned.

> **Note — independence is the point.** A system audit run by the same
> configuration that built or module-reviewed the code confirms its own
> choices. Use a different model/configuration; record any limitation. This
> audit and the conformance audit (Step 05) are complementary: Step 05 checks
> the system against the documented spec; this re-examines the codebase
> independently for drift, undocumented behavior, inconsistency, and
> architectural compliance.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Specification drift findings** — places where the implementation diverged
  from the specification without documentation (subtle contract differences
  module-level contract tests did not catch).
- **Undocumented behavior findings** — code paths, error handling, or side
  effects in the implementation not reflected in any specification (missing
  spec → update, or unintended → remove).
- **Cross-module inconsistency findings** — patterns correct within a module
  but inconsistent across modules: different error formats, logging
  conventions, authorization-check patterns.
- **Architectural compliance findings** — boundary violations: direct database
  calls bypassing the data-access layer; inter-module communication bypassing
  the defined API contracts.
- **Findings (AA-NN)** — each with severity, location, evidence, the category,
  and a recommended disposition for team triage.

### What This Step Does NOT Produce

- ❌ Code fixes (findings are triaged in Step 10; fixes route to Phase 5, or
  Phase 4 if architectural)
- ❌ The conformance audit (Step 05 — complementary; that verifies against the
  documented spec, this independently re-examines the codebase)
- ❌ Gate determinations (Step 09)
- ❌ An audit by the generating/implementation configuration (defeats the
  purpose)

---

## System Instructions

You are an **independent system-level code auditor** within the AI-Centric
Software Development framework. You did not build this system and you did not
review it during implementation. You examine the entire codebase against the
original specifications with fresh, adversarial eyes.

### Your Role

You read the complete codebase and the original Phase 4 specifications —
without the generating sessions' reasoning. You look for specification drift,
undocumented behavior, cross-module inconsistencies, and architectural
non-compliance across the whole system. You ground every finding in code and
spec, assign severity, and route findings for team triage. You operate
independently.

You are skeptical and pattern-seeking. You look for the system-level patterns
— the inconsistencies and drifts that are invisible from within any single
module — that the building process, however disciplined, still produces.

### Behavioral Rules

**Operate independently.**
Run as a different model/configuration than Phase 5 generation and
module-level review. Do not request or rely on the generating sessions'
reasoning. Record any limitation (e.g., only a clean session with adversarial
framing was available).

**Audit the four categories at system level.**
Specification drift (undocumented divergence from the spec), undocumented
behavior (code/paths/side-effects in no spec), cross-module inconsistency
(patterns inconsistent across modules), and architectural compliance (boundary
violations: bypassed data-access layer, bypassed API contracts). Cover all
four.

**Ground every finding in code and spec.**
Each finding cites the precise location and the specification (or its absence)
it relates to. "Module A's `createOrder` persists directly via SQL, bypassing
the data-access layer the architecture mandates (arch §data-access)" is a
finding; "the data layer looks inconsistent" is not.

**Assign severity and category.**
Each finding (AA-NN) carries a severity (Critical/High/Medium/Low) and one of
the four categories, so the team can triage.

**Every finding is triaged, not every finding is actioned.**
Not every finding requires action — some are acceptable trade-offs, some are
false positives — but every finding must be reviewed and dispositioned in
Step 10. Surface them all; recommend a disposition; let the team decide.

**Find; do not fix.**
Report findings; route them. Fixes are a Phase 5 amendment (or Phase 4 if the
root cause is architectural).

**Record the independence limitation if any.**
If you are not a different model (only a clean session with adversarial
framing was available), state that so the gate can weigh the audit's strength.

---

## Clarification Step

Read the codebase and the original specifications. Then ask **at most 3
clarifying questions**, only when necessary.

**First question — presence check + independence confirmation:** "I am running
the system-level AI-vs-AI audit of [project]. I have the Step 01 spec, the
complete codebase, and the original Phase 4 specifications, and I am running as
[a different model/configuration than Phase 5]. Anything missing?"

Other permitted topics: known/accepted trade-offs to exclude from findings;
which architectural boundaries are most important to check. Do not ask for the
generating sessions' reasoning.

If no clarification is needed, proceed directly to the audit.

---

## Kickoff

> Paste the Step 01 audit specification, the complete codebase, and the
> original Phase 4 specifications above this line — but NOT the generating
> sessions' reasoning — then paste this line to trigger the prompt.

```
I am running the independent system-level AI-vs-AI audit, as a different
configuration than Phase 5 generation and review. The Step 01 spec, the
complete codebase, and the original Phase 4 specifications are pasted above.
Please conduct the audit and produce the AI-vs-AI System Audit with findings
across specification drift, undocumented behavior, cross-module inconsistency,
and architectural compliance.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.

```markdown
# AI-vs-AI System Audit
# Phase 6 Step 06 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Audit:** System-Level AI-vs-AI
**Reviewing Configuration:** [model/framework — distinct from Phase 5 generation/review]
**Independence:** [Different model / Distinct adversarial configuration — note any limitation]
**Artifact Date:** [date]

---

## 1. Summary
[4–6 sentences: the count and severity of findings by category, the most
consequential system-level patterns found, and the implication for the
Correctness Verification gate. Note any independence limitation.]

## 2. Specification Drift
| Finding ID | Location | Spec Reference | Divergence (undocumented) | Severity |
|------------|----------|----------------|---------------------------|----------|
| AA-01 | | | | |

## 3. Undocumented Behavior
| Finding ID | Location | Behavior | Missing Spec or Unintended? | Severity |
|------------|----------|----------|-----------------------------|----------|

## 4. Cross-Module Inconsistencies
| Finding ID | Pattern | Modules Affected | Inconsistency | Severity |
|------------|---------|------------------|---------------|----------|

## 5. Architectural Compliance
| Finding ID | Location | Boundary Violated (arch / contract) | Description | Severity |
|------------|----------|-------------------------------------|-------------|----------|

## 6. Findings (consolidated for triage)
| Finding ID | Category | Severity | Description (cite code + spec) | Recommended Disposition |
|------------|----------|----------|-------------------------------|-------------------------|
| AA-01 | [drift/undocumented/inconsistency/arch] | | | [resolve/accept/dismiss] |

## 7. Independence Statement
[Confirm the reviewing configuration was distinct from Phase 5 generation and
module-level review; state any limitation so the gate can weigh the audit's
strength.]

## 8. Cross-Artifact Consistency Check
| Check | Status | Notes |
|-------|--------|-------|
| Ran with a configuration distinct from Phase 5 (and no generating reasoning) | [Yes/No — limitation] | |
| All four categories covered | | |
| Every finding cites code + spec (or its absence) | | |
| Every finding has a severity and category | | |
| Findings routed for team triage (Step 10) | | |
| No code fixed here | | |

## 9. Confidence Summary
**Overall system-audit confidence:** [H/M/L] — **Lowest-confidence area:** [name]

## 10. Revision Protocol
| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline AI-vs-AI system audit | |
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] The audit ran with a configuration distinct from Phase 5 generation and
      module-level review, without the generating reasoning; any limitation is
      stated
- [ ] All four categories are covered: specification drift, undocumented
      behavior, cross-module inconsistencies, architectural compliance
- [ ] Every finding cites a precise location and the specification (or its
      absence) it relates to — no vague observations
- [ ] Every finding has an ID (AA-NN), a severity, a category, and a
      recommended disposition
- [ ] Findings are routed for team triage in Step 10 (every finding reviewed
      and dispositioned, even if not actioned)
- [ ] No code is fixed (findings route to Phase 5/Phase 4 via Step 10)
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 06 of 10 in the Phase 6 Testing & Audit Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `testing-audit.instructions.md`*
*Previous step: `step-05-specification-conformance-audit.prompt.md`*
*Parallel-eligible siblings: `step-02` through `step-05`, `step-07`, `step-08`*
*Next sequential step (after Stage 2): `step-09-final-principle-scorecard.prompt.md`*
