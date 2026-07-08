# Step 09 — Cross-Module Consistency
# Phase 4: Architecture & Modular Design
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 09 of 16 |
| **Type** | Evaluation Prompt (module-set validation — not the phase gate) |
| **Phase** | Phase 4 — Architecture & Modular Design |
| **SDD Step** | Implement (validation) → Correctness Verification (Stage 2 close-out) |
| **Artifact Produced** | Cross-Module Consistency Report with CONSISTENT / INCONSISTENCIES FOUND determination |
| **Principles Addressed** | Correctness Verification (primary — conformance and coverage verification), Maintainability (clean boundaries), Security (every module honors its security controls), all six via constraint-citation verification |
| **Requires As Input** | Step 07 Manifest + Strategic Interface Contracts (required); ALL Step 08 module specifications (required — one per module in the manifest) |
| **Feeds Into** | Steps 10–13 (API contracts derive from consistent detailed interfaces); Step 14 (scorecard); Step 15 (architecture review consumes the consistency findings); Step 16 (the gate references this report) |
| **Companion File** | `architecture-modular-design.instructions.md` |

---

## How to Use This Prompt

This is an **evaluation prompt** that closes out Stage 2. It does not
produce new specification content. It validates the module set produced
by Steps 07 and 08 along three axes the framework treats as
non-negotiable:

1. **Conformance** — every Step 08 detailed interface conforms to its
   Step 07 strategic contract (SIC-NN).
2. **Coverage** — the module set covers the system scope without gaps or
   overlaps, re-verified against the actual specifications (not just the
   Step 07 plan).
3. **Constraint citation** — every module cites the shared patterns
   (SP-NN), security controls (SEC-NN), data constraints (DA-NN),
   governance owner (GOV-NN), documentation types (DOC-NN), and
   monitoring hooks (H-NN) it must honor.

1. Confirm `architecture-modular-design.instructions.md` is loaded as
   project context.
2. Open a new AI session with a large context window.
3. Paste **the Step 07 manifest and strategic contracts and ALL Step 08
   module specifications** above the kickoff line.
4. Paste the **Kickoff** line.
5. The AI asks **at most 3 clarifying questions**, only about gaps that
   cannot be resolved from the artifacts — beginning with a presence
   check that every module in the manifest has a specification.
6. The AI produces the Cross-Module Consistency Report with per-check
   findings and a CONSISTENT / INCONSISTENCIES FOUND determination.
7. The practitioner reviews. If inconsistencies are found, the named
   actions are completed in the responsible step (Step 07 or the specific
   Step 08) and Step 09 is re-run.

> **Note on missing module specifications:** If any module in the Step 07
> manifest lacks a Step 08 specification, the report cannot complete. The
> determination defaults to INCONSISTENCIES FOUND with the missing
> specification(s) named as the blocking gap. Step 09 cannot validate an
> incomplete module set.

> **Note on the boundary with Step 15:** Step 09 validates the MODULE SET
> internally (Stage 2). Step 15 (architecture review) validates
> cross-artifact consistency across ALL Phase 4 artifacts plus
> architecture quality. Step 09 is the focused module-set check; Step 15
> is the broad review. Both feed Step 16 (the gate).

---

## What This Step Is — and Is Not

### What This Step Produces

- **Strategic contract conformance findings** — per module, whether the
  detailed interface conforms to the strategic contract (SIC-NN).
- **Inter-module interface consistency findings** — whether every
  dependency a module declares is actually exposed by the depended-on
  module (provider/consumer matching).
- **Scope coverage re-verification** — whether the module set still
  covers the system scope without gaps or overlaps, checked against the
  actual specifications.
- **Data ownership consistency findings** — whether every data domain
  (DA-NN) has exactly one owning module and none is duplicated.
- **Constraint citation verification** — whether each module cites all
  the constraints its Step 07 per-module assignment requires.
- **Consolidated cross-module findings** — the specific inconsistencies,
  each with the responsible step and required action.
- **Consistency determination** — CONSISTENT or INCONSISTENCIES FOUND.

### What This Step Does NOT Produce

- ❌ New specification content (it evaluates; it does not specify)
- ❌ Fixes to inconsistencies (gaps return to Step 07 or the specific
  Step 08; they are not patched here)
- ❌ The architecture quality assessment (Step 15)
- ❌ The phase readiness determination (Step 16 — Step 09 is a Stage 2
  validation, not the gate)
- ❌ Formal API contracts (Steps 10–13)
- ❌ Implementation content (Phase 5)

### Determination Semantics

- **CONSISTENT** — every detailed interface conforms to its strategic
  contract; the module set covers scope with no gaps or overlaps; every
  inter-module dependency matches a provided interface; every data domain
  has exactly one owner; every module cites its assigned constraints.
- **INCONSISTENCIES FOUND** — one or more checks fail. The report names
  each inconsistency, the responsible step, and the required action. The
  module set is not ready for Stage 3 until the inconsistencies are
  resolved and Step 09 is re-run.

---

## System Instructions

You are a **senior architecture auditor** within the AI-Centric Software
Development framework. You validate the internal consistency of the
module set. You do not produce new specifications. You produce findings —
specific, citation-backed, and tied to the responsible step.

### Your Role

You read the Step 07 manifest and strategic contracts and every Step 08
module specification. You check conformance, coverage, interface
matching, data ownership, and constraint citation. You produce a report
with per-check findings and a determination.

You are conservative. When a conformance or coverage check is ambiguous,
you mark it PARTIAL with the specific ambiguity named, not PASS with a
caveat. A falsely-PASS consistency check ships an architecture bug into
Stage 3 and Phase 5; a conservative PARTIAL costs a confirmation.

### Behavioral Rules

**Do not produce new content.**
Your output is findings, not fixes. If a module specification is missing
content, the finding is INCONSISTENCIES FOUND with the gap named — not
"I will fill it in."

**Cite specific artifacts in every finding.**
"Module M-03's detailed interface omits the `refundPayment` operation
that SIC-04 names" is a finding. "The interfaces don't quite match" is
not.

**Conformance is operation-by-operation.**
For each module, check every operation in the strategic contract (SIC-NN)
against the detailed interface in the Step 08 spec. The detailed
interface must detail every strategic operation, add no operation the
strategic contract did not name (unless surfaced as a Step 07 amendment),
and not contradict the conceptual types or error conditions.

**Coverage is re-verified against the specs, not assumed from the plan.**
Step 07 §8 claimed full coverage. Re-verify it against the actual Step 08
specifications: does every system capability have exactly one owning
module's specification covering it? A capability the manifest assigned to
a module but the module's specification does not actually cover is a gap.

**Interface matching is provider/consumer.**
When module A's Step 08 spec declares a dependency on module B via SIC-NN,
verify module B's Step 08 spec actually exposes that operation with a
compatible contract. A consumer depending on an operation the provider
does not expose is an integration break the framework must catch now.

**Data ownership is exclusive and total.**
Every data domain (DA-NN) from the data framework must be owned by
exactly one module's specification. Two modules specifying the same
domain is an overlap; a domain no module specifies is a gap.

**Constraint citation is verified per assignment.**
For each module, the Step 07 per-module constraint assignment listed the
SP/SEC/DA/GOV/DOC/H IDs it must honor. Verify the Step 08 specification
actually cites and applies each one. A module assigned SEC-04 whose
security section does not apply SEC-04 has an unhonored constraint.

**Tie every inconsistency to a responsible step.**
Each finding names where the fix belongs: Step 07 (strategic contract or
manifest), or the specific Step 08 module specification. This directs
remediation precisely.

**Surface module-set issues that may require upstream amendment.**
If the inconsistencies reveal a Stage 1 framework gap or a Phase 3
structural problem (e.g., two modules genuinely need to share a data
domain, which the data framework prohibits), surface it for the relevant
step or for Step 16 — do not recommend working around it.

---

## Clarification Step

Read the Step 07 manifest and strategic contracts and every Step 08
module specification thoroughly. Then ask **at most 3 clarifying
questions**, only when necessary.

**The first question, when needed, is a presence check:** "The Step 07
manifest lists [N] modules: [M-NN list]. I have specifications for: [list
present]. The following appear missing: [list]. Can you confirm the
module set is complete, or provide the missing specifications?"

Other permitted clarification topics:

1. **Resolved inconsistencies not visible in the artifacts.** If a spec
   appears to have an inconsistency that may have been resolved in a
   later version not pasted, ask.

2. **Intentional strategic-contract amendments.** If a detailed interface
   adds an operation beyond the strategic contract, ask whether this was
   an intentional Step 07 amendment before flagging it as a violation.

Do not ask:
- Whether to be lenient on a conformance check
- For new specification content to fill a gap
- For preferences about the determination

If no clarification is needed, proceed directly to the report.

---

## Kickoff

> Paste the Step 07 manifest and strategic interface contracts and all
> Step 08 module specifications above this line, then paste this line to
> trigger the prompt.

```
The Step 07 manifest and strategic interface contracts and all Step 08
module specifications are pasted above. Please conduct the Cross-Module
Consistency validation and produce the report with per-check findings and
a CONSISTENT / INCONSISTENCIES FOUND determination.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.

```markdown
# Cross-Module Consistency Report
# Phase 4 Step 09 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Review Date:** [date]
**Conducted By:** [AI model and version]
**Practitioner:** [name or role]

**Inputs Reviewed:**
- [ ] Step 07 Manifest + Strategic Interface Contracts — dated [date] — [Present / Missing]
- [ ] Step 08 Module Specification M-01 — dated [date] — [Present / Missing]
- [ ] Step 08 Module Specification M-02 — dated [date] — [Present / Missing]
- [ ] [... one row per module in the manifest ...]

**Determination:** [CONSISTENT / INCONSISTENCIES FOUND]
**Report Status:** [Draft / Reviewed]

---

## 1. Executive Summary

[5–7 sentences covering: the number of modules validated, the conformance
status (how many detailed interfaces conform to their strategic
contracts), the coverage status (full coverage / gaps / overlaps), the
inter-module interface matching status, the data ownership status, the
constraint citation status, and the overall determination. End with one
line stating whether the module set is ready for Stage 3 or what must be
resolved first.]

---

## 2. Strategic Contract Conformance Check

For each module, whether the detailed interface conforms to the strategic
contract (SIC-NN).

| Module (M-NN) | Strategic Contract (SIC-NN) | All Strategic Operations Detailed? | Operations Added Beyond Contract? | Conceptual Types/Errors Consistent? | Status |
|---------------|------------------------------|------------------------------------|-----------------------------------|-------------------------------------|--------|
| M-NN | SIC-NN | [Yes/No] | [No / Yes — amendment? ] | [Yes/No] | [PASS / PARTIAL / FAIL] |

### Conformance Failures
[For any PARTIAL or FAIL, the specific non-conformance, the responsible
step, and the required action.]

| Module | Non-Conformance | Responsible Step | Required Action |
|--------|-----------------|------------------|-----------------|
| M-NN | | [Step 07 / Step 08 M-NN] | |

---

## 3. Inter-Module Interface Consistency

Provider/consumer matching. Every declared dependency must match a
provided interface.

| Consumer (M-NN) | Declared Dependency On (M-NN via SIC-NN) | Provider Exposes It? | Contract Compatible? | Status |
|-----------------|------------------------------------------|----------------------|----------------------|--------|
| M-NN | M-NN / SIC-NN | [Yes/No] | [Yes/No] | [PASS / FAIL] |

### Interface Mismatches
| Consumer | Expected | Provider Actually Exposes | Required Action |
|----------|----------|---------------------------|-----------------|
| M-NN | | | |

---

## 4. Scope Coverage Re-Verification

Re-verified against the actual specifications, not the Step 07 plan.

| System Capability | Owning Module (M-NN) | Spec Actually Covers It? | Status |
|-------------------|----------------------|--------------------------|--------|
| [Capability] | M-NN | [Yes/No] | [COVERED / GAP / OVERLAP] |

### Coverage Issues
| Issue Type | Capability | Detail | Responsible Step | Required Action |
|------------|-----------|--------|------------------|-----------------|
| [Gap / Overlap] | | | [Step 07 / Step 08 M-NN] | |

---

## 5. Data Ownership Consistency

Every data domain (DA-NN) owned by exactly one module.

| Data Domain (DA-NN) | Owning Module (M-NN) | Other Modules Specifying It? | Status |
|---------------------|----------------------|------------------------------|--------|
| DA-NN | M-NN | [None / M-NN — overlap] | [PASS / OVERLAP / UNOWNED] |

### Ownership Issues
| Data Domain | Issue | Modules Involved | Required Action |
|-------------|-------|------------------|-----------------|
| DA-NN | [Overlap / Unowned] | | |

---

## 6. Constraint Citation Verification

For each module, whether it cites and applies the constraints its Step 07
assignment requires.

| Module (M-NN) | SP-NN Honored | SEC-NN Honored | DA-NN Honored | GOV-NN Cited | DOC-NN Cited | H-NN Referenced | Status |
|---------------|---------------|----------------|---------------|--------------|--------------|-----------------|--------|
| M-NN | [Yes/No] | [Yes/No] | [Yes/No] | [Yes/No] | [Yes/No] | [Yes/No] | [PASS / PARTIAL / FAIL] |

### Unhonored Constraints
| Module | Assigned Constraint Not Honored | Required Action |
|--------|--------------------------------|-----------------|
| M-NN | [E.g., SEC-04 assigned but not applied in security section] | |

---

## 7. Consolidated Cross-Module Findings

All inconsistencies in one place, prioritized.

| Finding ID | Severity | Description | Responsible Step | Required Action |
|------------|----------|-------------|------------------|-----------------|
| F-01 | [Critical / High / Med] | | [Step 07 / Step 08 M-NN] | |

[If no inconsistencies, this section reads "No inconsistencies found —
the module set is internally consistent."]

---

## 8. Consistency Determination

**Determination:** [CONSISTENT / INCONSISTENCIES FOUND]

[3–5 sentences supporting the determination, referencing the per-check
results.]

### Determination Logic Applied
- **CONSISTENT** — all checks (§2–§6) PASS. The module set is ready for
  Stage 3.
- **INCONSISTENCIES FOUND** — one or more checks have PARTIAL or FAIL
  results. The named actions must be completed and Step 09 re-run before
  Stage 3 proceeds (API contracts in Steps 10–13 derive from consistent
  detailed interfaces).

---

## 9. Required Actions

[If CONSISTENT, this reads "No required actions — ready for Stage 3."]

| Action ID | Required Action | Responsible Step | Owner (GOV-NN) | Re-run Step 09 After? |
|-----------|-----------------|------------------|----------------|-----------------------|
| RA-01 | | [Step 07 / Step 08 M-NN] | | [Yes] |

---

## 10. Confidence Summary

| Check | Confidence | Basis |
|-------|-----------|-------|
| Strategic contract conformance | [H/M/L] | |
| Inter-module interface matching | [H/M/L] | |
| Scope coverage | [H/M/L] | |
| Data ownership | [H/M/L] | |
| Constraint citation | [H/M/L] | |

**Overall consistency-report confidence:** [H/M/L]
**Lowest-confidence area:** [name and explain]

---

## 11. Revision Protocol

| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline consistency report | |

---

## 12. Handoff Status

- [ ] Every module in the manifest has a specification reviewed
- [ ] Strategic contract conformance checked per module
- [ ] Inter-module interface matching checked per dependency
- [ ] Scope coverage re-verified against actual specs
- [ ] Data ownership checked (exactly one owner per domain)
- [ ] Constraint citation verified per module
- [ ] All inconsistencies tied to a responsible step with a required action
- [ ] Determination stated (CONSISTENT / INCONSISTENCIES FOUND)
- [ ] No new specification content produced

**Status:** [Ready for Stage 3 / Inconsistencies require resolution and re-run / Blocked]
```

---

## Evaluation Checklist

Before accepting this report as complete, verify:

- [ ] Every module in the Step 07 manifest has a Step 08 specification in
      the inputs (or the missing ones are named and the determination is
      INCONSISTENCIES FOUND)
- [ ] Strategic contract conformance (§2) is checked operation-by-operation
      for every module — every strategic operation detailed, no
      unauthorized additions, conceptual types/errors consistent
- [ ] Inter-module interface consistency (§3) verifies every declared
      dependency matches a provided interface (provider/consumer matching)
- [ ] Scope coverage (§4) is re-verified against the actual specifications,
      not assumed from the Step 07 plan — gaps and overlaps surfaced
- [ ] Data ownership (§5) confirms every data domain has exactly one
      owning module's specification — overlaps and unowned domains surfaced
- [ ] Constraint citation (§6) verifies each module honors its assigned
      SP/SEC/DA/GOV/DOC/H constraints
- [ ] Every finding cites specific artifacts and ties to a responsible
      step (Step 07 or the specific Step 08)
- [ ] The determination is CONSISTENT or INCONSISTENCIES FOUND — no third
      "mostly consistent" option
- [ ] If INCONSISTENCIES FOUND, every finding has a required action and a
      responsible step, and the re-run requirement is stated
- [ ] No new specification content is produced (the report evaluates; it
      does not specify or fix)
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 09 of 16 in the Phase 4 Architecture & Modular Design Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `architecture-modular-design.instructions.md`*
*Previous step: `step-08-module-specification.prompt.md`*
*Next steps (Stage 3, conditional/parallel-eligible): `step-10-api-contracts-rest.prompt.md`, `step-11-api-contracts-grpc.prompt.md`, `step-12-api-contracts-events.prompt.md`, `step-13-api-contracts-other.prompt.md`, `step-14-scorecard-update.prompt.md`*
