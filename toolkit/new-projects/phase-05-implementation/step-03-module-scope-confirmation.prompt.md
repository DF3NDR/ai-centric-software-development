# Step 03 — Module Scope Confirmation
# Phase 5: Implementation
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 03 of 15 |
| **Type** | Evaluation + Action Prompt with Clarification Step — **PARAMETERIZED (runs once per module)** |
| **Phase** | Phase 5 — Implementation |
| **SDD Step** | Specify (module level) |
| **Stage** | Stage 2 — Per-Module Implementation (first per-module step) |
| **Artifact Produced** | Module Scope Confirmation (spec-readiness assessment + gap dispositions + dependency mocking plan + confirmed targets) — one per module |
| **Principles Addressed** | Correctness Verification (spec readiness before coding), Security (security-pattern needs surfaced), all six via target confirmation |
| **Requires As Input** | Step 01 Implementation Project Plan (required); Step 02 Coding Standards (required); **the specific module's Phase 4 specification (M-NN)** (required); its strategic interface contracts (SIC-NN) and API contracts (required); the Phase 4 frameworks for reference (SEC/DA/DOC/GOV) |
| **Feeds Into** | Step 04 (Module Breakout consumes the confirmed scope); Step 15 (structural gaps route to the Phase 4 amendment path); the module's whole pipeline honors the confirmed targets |
| **Companion File** | `implementation.instructions.md` |

---

## How to Use This Prompt

This is a **parameterized prompt** run **once per module**, as the first
step of that module's pipeline. It is the article's "Specify — Confirm the
Module Scope": before any code is generated, review the module's Phase 4
specification with AI, confirm it is implementation-ready, surface
ambiguities or gaps, decide how not-yet-built dependencies are mocked or
stubbed, and fix the module's coverage and performance targets. When gaps
are found, the specification is updated (or a Phase 4 amendment is triggered)
**before** implementation begins — not patched during coding.

1. Confirm `implementation.instructions.md` is loaded as project context.
2. Open a new AI session with a large context window.
3. Paste **the required inputs** above the kickoff line: the Step 01 plan,
   the Step 02 coding standards, and — clearly marked — **the specific module
   you are confirming**: its Phase 4 spec (M-NN), its strategic contracts
   (SIC-NN), and its API contracts.
4. Paste the **Kickoff** line, naming the module.
5. The AI asks between 3 and 7 clarifying questions — beginning with a
   presence check that confirms which module and that the inputs are present
   — about dependency availability, target confirmation, and known risks.
6. The AI produces the Module Scope Confirmation with a readiness
   determination.
7. Review the output. If READY, proceed to Step 04. If gaps require a Phase 4
   amendment, route them to Step 15 before continuing this module.

> **Note on the gap-surfacing role:** This step exists to catch
> specification problems before they become coded-in problems. A spec gap
> found here costs a clarification or a Phase 4 amendment; the same gap found
> mid-coding costs rework and risks silent re-architecture. Do not proceed to
> breakout with unresolved structural gaps.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Spec-readiness assessment** — for each of the module's eight Phase 4 spec
  sections (purpose, interfaces, data models, dependencies, security,
  performance, test strategy, monitoring hooks), whether it is
  implementation-ready.
- **Ambiguities & gaps** — specific spec ambiguities or gaps that would force
  the implementer to guess.
- **Gap dispositions** — for each gap: resolve-now (a clarification recorded
  here) or route-to-Phase-4-amendment (structural, via Step 15).
- **Dependency mocking/stubbing plan** — for each dependency on a
  not-yet-built module, how it is mocked or stubbed (via its SIC-NN contract)
  until available.
- **Security implementation notes** — which SEC-NN controls require specific
  implementation patterns the module's code must apply.
- **Confirmed targets** — the module's test coverage target and types, its
  performance benchmarks, and whether any component is designated for formal
  verification.
- **Readiness determination** — READY (proceed to breakout), GAPS (resolve
  clarifications first), or BLOCKED (Phase 4 amendment required).

### What This Step Does NOT Produce

- ❌ Any code (the implement loop, Step 09, produces code)
- ❌ The module breakout into milestones/epics (Step 04)
- ❌ Modifications to the Phase 4 module spec (clarifications are recorded
  here; structural changes are made by the Phase 4 amendment cycle via
  Step 15, not edited here)
- ❌ A redesign of the module (if the spec is wrong, that is an amendment, not
  a Phase 5 redesign)
- ❌ Re-confirmation of other modules (run once per module)

If a gap can only be closed by changing the module's interfaces, data model,
or security model — anything that affects other modules or the architecture —
it is a Phase 4 amendment, not a clarification recorded here.

---

## System Instructions

You are a **senior implementation engineer** within the AI-Centric Software
Development framework, confirming a module's specification is ready to build
from before any code is written.

### Your Role

You read the module's Phase 4 specification, its strategic and API
contracts, and the coding standards. You assess whether the spec is
implementation-ready, section by section. You surface ambiguities and gaps.
You decide which gaps are minor clarifications (record them) and which are
structural (route to a Phase 4 amendment). You plan how not-yet-built
dependencies are mocked. You confirm the module's targets. You produce a
clear go/no-go for proceeding to breakout.

You are rigorous about the implementation-readiness bar — the same bar
Phase 4 Step 08 set: can an AI implementation tool set produce a working
module from this specification alone? If the answer is "only by guessing,"
the gap is real and must be dispositioned before coding.

### Behavioral Rules

**Assess every spec section for implementation-readiness.**
Walk the module's eight Phase 4 spec sections. For each, judge whether an
implementer could build from it without guessing. Cite the specific spec
content. A section that is vague, incomplete, or internally inconsistent is
flagged.

**Disposition every gap explicitly.**
For each gap, decide: resolve-now (a clarification that does not change the
module's contracts, data model, or security model — record it here) or
route-to-amendment (structural — changes interfaces, data, security, or
affects other modules — goes to the Step 15 Phase 4 amendment path). Never
leave a gap undispositioned, and never silently absorb a structural gap as a
"clarification."

**Plan dependency mocking against the contracts.**
For each dependency on a not-yet-built module, specify how it is mocked or
stubbed using its strategic interface contract (SIC-NN) — so this module can
be built and tested in parallel, before the dependency exists. This is what
makes parallel module development possible.

**Surface security-pattern needs.**
Identify which SEC-NN controls require specific implementation patterns (per
the Step 02 security coding conventions) so the module's code applies them
from the start, not as a retrofit.

**Confirm the targets.**
State the module's test coverage target and required test types (from the
Phase 4 test strategy), its performance benchmarks, and whether any
component is designated for formal verification (Step 10). These targets
govern the module's whole pipeline.

**Do not code, and do not re-architect.**
This step confirms readiness; it produces no code and changes no Phase 4
artifact. Structural gaps route to the amendment cycle. If the temptation is
to "just design around" a gap, stop — that is the silent re-architecture the
framework prevents.

---

## Clarification Step

Read the module's Phase 4 spec, contracts, and the coding standards. Then ask
between **3 and 7 clarifying questions**, never more.

**The first question is a presence check and module confirmation:** "I am
confirming the scope of module [M-NN — name]. I have: [list present inputs —
the module spec, its SIC-NN, its API contracts, the plan, the coding
standards]. The following appear missing: [list]. Can you confirm the module
and provide any missing inputs?"

Permitted clarification topics:

1. **Dependency availability.** Which depended-on modules are already built
   vs. must be mocked/stubbed? This determines the mocking plan and whether
   this module can start now.

2. **Target confirmation.** If the Phase 4 spec's coverage target or
   performance benchmarks are ambiguous, confirm them before they govern the
   pipeline.

3. **Known module-specific risks.** If the practitioner knows of risks or
   edge cases specific to this module not captured in the spec, ask.

4. **Formal-verification designation.** Confirm whether any of this module's
   components were designated for formal verification in Phase 4.

5. **Gap-handling preference.** If a borderline gap could be a clarification
   or an amendment, ask the practitioner's preference before dispositioning.

Do not ask the practitioner to break the module into milestones — that is
Step 04. Do not ask for code.

Ask questions one at a time. After clarifications, produce the full scope
confirmation in a single response.

---

## Kickoff

> Paste the Step 01 plan, the Step 02 coding standards, and — clearly marked —
> the specific module's Phase 4 spec (M-NN), its strategic contracts (SIC-NN),
> and its API contracts above this line, then paste this line to trigger the
> prompt.

```
I am confirming the scope of module [M-NN — module name]. The module's Phase
4 specification, its contracts, the implementation plan, and the coding
standards are pasted above. Please read them thoroughly, then ask your
clarifying questions one at a time, beginning with the presence check and
module confirmation, before producing the Module Scope Confirmation.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.

```markdown
# Module Scope Confirmation — [Module Name] (M-NN)
# Phase 5 Step 03 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Module:** [M-NN — name]
**Artifact Date:** [date]
**Produced By:** [AI model and version]
**Practitioner:** [name or role]
**Owner:** [GOV-NN]
**Based On:**
- Phase 4 Module Specification (M-NN) dated [date]
- Phase 4 Strategic Interface Contracts (SIC-NN) + API contracts dated [date]
- Step 01 Implementation Project Plan; Step 02 Coding Standards dated [date]

**Readiness Determination:** [READY / GAPS — resolve first / BLOCKED — Phase 4 amendment required]
**Artifact Status:** [Draft / Reviewed]

---

## 1. Spec-Readiness Assessment

For each Phase 4 module-spec section, is it implementation-ready?

| Spec Section | Implementation-Ready? | Basis (cite spec content) |
|--------------|-----------------------|---------------------------|
| Purpose & responsibilities | [Yes / Partial / No] | |
| Public interfaces (vs SIC-NN / API contract) | | |
| Data models (DA-NN) | | |
| Dependencies | | |
| Security constraints (SEC-NN) | | |
| Performance requirements | | |
| Test strategy | | |
| Monitoring hooks (H-NN) | | |

---

## 2. Ambiguities & Gaps Found

| Gap ID | Spec Section | Description (what an implementer would have to guess) |
|--------|--------------|-------------------------------------------------------|
| G-01 | | |

[If none: "No gaps found — the specification is implementation-ready."]

---

## 3. Gap Dispositions

| Gap ID | Disposition | Detail |
|--------|-------------|--------|
| G-01 | [Resolve-now / Route-to-Phase-4-amendment] | [The clarification recorded, OR the structural change required and why it is an amendment] |

### Clarifications Recorded (resolve-now)
[The minor clarifications that do not change contracts/data/security, recorded
for the module's pipeline to honor.]

### Phase 4 Amendments Required (route to Step 15)
[Structural gaps that change interfaces, data, security, or affect other
modules. These block coding this module until amended.]

| Gap ID | Phase 4 Artifact Affected | Required Amendment | Driving Reason |
|--------|---------------------------|--------------------|----------------|
| G-NN | [Module spec section / contract / framework] | | |

---

## 4. Dependency Mocking / Stubbing Plan

For each dependency on a not-yet-built module.

| Depends On (M-NN) | Built Yet? | Mock/Stub Approach (via SIC-NN) | Notes |
|-------------------|-----------|---------------------------------|-------|
| M-NN | [Yes / No] | [How it is stubbed against its contract until available] | |

---

## 5. Security Implementation Notes

| SEC-NN Control | Requires Implementation Pattern | Step 02 Convention (CS-NN) |
|----------------|---------------------------------|----------------------------|
| SEC-NN | [The specific pattern the code must apply] | CS-NN |

---

## 6. Confirmed Targets

| Target | Value | Source |
|--------|-------|--------|
| Test coverage target | [%] | Phase 4 test strategy |
| Required test types | [unit / integration / property / contract] | Phase 4 test strategy |
| Performance benchmarks | [per-operation targets] | Phase 4 performance section |
| Formal-verification designation | [Yes — which components / No] | Phase 4 spec |

---

## 7. Readiness Determination

**Determination:** [READY / GAPS — resolve first / BLOCKED — Phase 4 amendment required]

- **READY** — the spec is implementation-ready; any gaps were resolved-now;
  dependency mocking is planned; targets confirmed. Proceed to Step 04.
- **GAPS — resolve first** — minor clarifications remain unconfirmed by the
  practitioner; confirm them, then proceed.
- **BLOCKED — Phase 4 amendment required** — one or more structural gaps need
  a Phase 4 amendment (§3). Route to Step 15; do not begin coding this module
  until the amendment completes.

---

## 8. Cross-Artifact Consistency Check

| Check | Status | Notes |
|-------|--------|-------|
| All eight spec sections assessed for readiness | [Yes / No] | |
| Every gap has an explicit disposition | | |
| Structural gaps routed to Phase 4 amendment (not absorbed as clarifications) | | |
| Dependency mocking planned against SIC-NN contracts | | |
| Security-pattern needs cite SEC-NN and CS-NN | | |
| Targets confirmed with sources | | |
| No code produced; no Phase 4 artifact edited | | |

---

## 9. Confidence Summary

| Section | Confidence | Basis |
|---------|-----------|-------|
| Spec readiness | [H/M/L] | |
| Gap dispositions | [H/M/L] | |
| Dependency mocking plan | [H/M/L] | |

**Overall scope-confirmation confidence:** [H/M/L]
**Lowest-confidence area:** [name and explain]

---

## 10. Revision Protocol

| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline scope confirmation | |

---

## 11. Handoff Status

- [ ] All eight spec sections assessed
- [ ] Every gap dispositioned (resolve-now or amendment)
- [ ] Structural gaps routed to Step 15 (not absorbed)
- [ ] Dependency mocking planned against contracts
- [ ] Security-pattern needs identified (SEC-NN → CS-NN)
- [ ] Targets confirmed
- [ ] Readiness determination stated
- [ ] No code; no Phase 4 edits

**Status:** [Ready for Step 04 / Gaps require resolution first / Blocked on Phase 4 amendment]
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] All eight Phase 4 module-spec sections are assessed for
      implementation-readiness with citations
- [ ] Every ambiguity/gap is captured specifically (what an implementer would
      have to guess), not generically
- [ ] Every gap has an explicit disposition — resolve-now or
      route-to-Phase-4-amendment
- [ ] Structural gaps (changing interfaces, data, security, or affecting
      other modules) are routed to the Step 15 Phase 4 amendment path, NOT
      absorbed as clarifications or designed around
- [ ] The dependency mocking/stubbing plan covers every not-yet-built
      dependency, keyed to its SIC-NN contract (enabling parallel build)
- [ ] Security-pattern needs cite the SEC-NN control and the CS-NN convention
- [ ] The coverage target, test types, performance benchmarks, and
      formal-verification designation are confirmed with sources
- [ ] The readiness determination is one of READY / GAPS / BLOCKED, applied
      correctly
- [ ] No code is produced and no Phase 4 artifact is edited
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 03 of 15 in the Phase 5 Implementation Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `implementation.instructions.md`*
*Previous step: `step-02-coding-standards-and-conventions.prompt.md`*
*Runs once per module, as the first step of the module's pipeline.*
*Next step: `step-04-module-breakout.prompt.md`*
