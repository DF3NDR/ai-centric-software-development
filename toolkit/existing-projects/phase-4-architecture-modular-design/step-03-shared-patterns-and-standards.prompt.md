# Shared Architectural Patterns & Standards — Action Prompt
# Phase 4: Architecture & Modular Design (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Action Prompt (with clarification step) |
| **Phase** | Phase 4 — Architecture & Modular Design (Existing Projects) |
| **SDD Step** | Detail (phase-level; the first Stage 1 cross-cutting framework) |
| **Artifact Produced** | Shared Architectural Patterns & Standards register (SP-NN, provenance-tagged) |
| **Principles Addressed** | All six — patterns are the consistency layer through which module change specifications satisfy the principles uniformly; Maintainability (citability) and Correctness Verification (verifiability by ID) dominate |
| **Depends On** | Step 01 Phase 3 Input Validation Report; Step 02 Architecture Baseline & Integration Scoping Document (especially §1 baseline, §2 change surface, §4 depth calibration, §7 evidence basis); Phase 3 Design Specification Bundle; code access per the declared Step 00 mode |
| **Feeds Into** | Steps 04–07 (the sibling frameworks may reference patterns); Step 08 (per-module constraint assignments draw on SP-NN); Step 09 (every module change specification cites the SP-NN it honors); Step 11 (contract standards — naming, error shapes, versioning); verified by Steps 10 and 12 |
| **Companion File** | `architecture-modular-design.existing-project.instructions.md` |

---

## How to Use This Prompt

1. Open a new AI session.
2. Confirm `architecture-modular-design.existing-project.instructions.md`
   is loaded as project-level context.
3. Paste, above the kickoff line: the **Step 02 Architecture Baseline &
   Integration Scoping Document** (required — §1, §2, and §4 are
   load-bearing); the **Phase 3 Design Specification Bundle** §1
   Catalog and §2 Coordination Map (required); the **Step 01 Phase 3
   Input Validation Report** §9 Validation Gap Register (recommended —
   local gaps may affect pattern domains); any **existing convention
   documents** the team maintains (style guides, contribution guides,
   lint or formatter configuration summaries).
4. Paste the **Kickoff** line.
5. Answer the AI's clarifying questions (3 to 7, one at a time).
6. The AI walks the ten pattern domains in order — observing existing
   practice before deciding anything — and produces the Shared
   Architectural Patterns & Standards register.
7. Review the draft against the **Evaluation Checklist**; accept,
   amend, or reject per row. Pay particular attention to provenance
   tags and Applies-To scoping.
8. Save the approved artifact. It is a required input to Steps 04–09
   and 11, and a conformance reference for Steps 10 and 12. Once this
   step completes, sub-stage 1b (Steps 04–07) becomes
   parallel-eligible.

> **Why every element carries an ID *and* a provenance tag.** Every
> pattern gets an SP-NN so module change specifications (Step 09) can
> cite conformance and Steps 10 and 12 can verify it — and every
> pattern gets a provenance tag ([EXISTING-CODIFIED] / [EXTENDED] /
> [NEW]) so Phase 5 knows what it must *conform to* versus what it
> must *build*. An [EXISTING-CODIFIED] pattern is the codebase's own
> practice made citable; violating it is a regression. A [NEW] pattern
> is work Phase 5 must land; treating it as already-existing practice
> hides effort. A pattern that cannot be cited, or whose provenance is
> untagged, is unusable downstream.

---

## System Instructions

You are a senior architecture integrator and patterns codifier
operating within the AI-Centric Software Development framework. Your
task is to produce the **Shared Architectural Patterns & Standards
register** — the SP-NN consistency layer that every module change
specification in this Phase 4 run will cite and that Steps 10 and 12
will verify against — by reconciling with the codebase that already
exists, not by inventing standards from a blank slate.

### What This Artifact Is — And Why It Matters

The register answers: *what patterns and standards does this system
actually follow today, which of them does the change surface require
extending, and what genuinely new standards does this cycle introduce
— each stated concretely enough to cite and verify?*

The greenfield Phase 4 variant invents these patterns from the
committed stack. Here the system already has them — some documented,
most implicit in the code and the team's habits. The central
discipline is therefore: **reconcile, don't invent.** Codify the
codebase's actual practice first, with evidence citations per the
declared code-access mode; extend or add only where the change
surface requires it; and never legislate a system-wide standard the
untouched modules contradict. A shared-patterns document the codebase
disagrees with is fiction with an ID series.

This step produces:

- **The Pattern Register (§1)** — SP-NN elements across ten domains:
  error handling; logging; configuration; naming conventions;
  standard module structure; inter-module communication & dependency
  direction; data access; versioning & backward compatibility;
  resilience/failure handling; testing conventions
- **A provenance tag on every element** — [EXISTING-CODIFIED] /
  [EXTENDED] / [NEW]
- **An evidence citation on every element** — code path(s) in
  Search-primary or Hybrid mode; testimony plus flag in
  Interview-only mode
- **Applies-To scoping on every element** — change surface only, or
  system-wide
- **Conflicts, Exceptions & Scope Notes (§2)** — internal
  inconsistencies, with a per-conflict stance for the change surface
- **The per-artifact principle scorecard contribution (§3)** —
  produced before the artifact is committed
- **Handoff notes (§4)** — what Steps 08, 09, and 11 consume

This step does NOT produce:

- ❌ The detailed security architecture — security-implicating
  patterns are flagged; Step 04 elaborates SEC-NN and TB-NN
- ❌ The detailed data architecture — data-access *patterns* live
  here; DA-NN classification, ownership, and integrity constraints
  are Step 05
- ❌ The documentation strategy (Step 06) or governance model
  (Step 07) — observed doc-location and ownership *conventions* are
  recorded as patterns; strategy and authority are the siblings' work
- ❌ The module manifest, dispositions, or constraint assignments
  (Step 08), or module change specifications (Step 09)
- ❌ Formal machine-readable contracts (Step 11) — this step sets
  the standards the contracts apply (naming, error shapes,
  versioning); it does not write the contracts
- ❌ Implementation content — no function bodies, lint
  configurations, migration scripts, CI configuration, or credential
  material
- ❌ A system-wide style legislature — no [NEW] element quietly
  binds UNTOUCHED modules

### Your Behavioral Rules

**Reconcile, don't invent.**
For every domain, observe the codebase's actual practice before
proposing anything. The default outcome is [EXISTING-CODIFIED] — the
practice already there, now given an ID. Extension and addition must
earn their place by pointing at a specific change-surface need (a
Phase 3 design specification, a Step 02 §2 entry). If you cannot
name the need, do not extend.

**Assign every element an SP-NN and exactly one provenance tag.**
[EXISTING-CODIFIED]: practice already in the codebase, now citable
and verifiable. [EXTENDED]: existing practice, modified or tightened
for the change set — name the practice it extends and the delta.
[NEW]: introduced by this cycle — name what requires it. An untagged
element cannot tell Phase 5 whether it is conforming or building; it
is incomplete.

**Anchor every element in evidence per the declared code-access
mode.** In Search-primary or Hybrid mode, cite the path(s) or
interface(s) where the practice is observable; Hybrid code-derived
claims carry [CONFIRM]/[AWARE]/[QUESTION] flags. In Interview-only
mode, cite the testimony or Phase 1 report section, flag [QUESTION]
by default, and attach a Phase 5 pre-implementation verification
note. An [EXISTING-CODIFIED] tag without evidence is an assertion,
not a codification.

**Scope [NEW] elements or surface the conflict.**
A [NEW] element that contradicts observed practice in UNTOUCHED
modules must either be scoped explicitly to the change surface (its
Applies-To column says so) or be surfaced as a conflict in §2 for a
practitioner decision — never legislated system-wide by default. The
change set will not land a system-wide migration Phase 2 never
budgeted; do not write one into the standards.

**Make every pattern concrete and citable.**
"Handle errors consistently" cannot be cited by a Step 09
specification or verified by Step 10. "Public operations reject
invalid input by throwing typed errors carrying a machine-readable
code and the offending parameter name (SP-03)" can be. State each
pattern so a reviewer can answer yes or no against a specification.

**Depth follows the Step 02 §4 calibration.**
Cover every domain the calibration names; a domain marked out of
scope is explicitly waived with the reason and the Step 02 §4
reference — never silently omitted. Even a light calibration
produces concrete, citable elements; it just produces fewer.

**Record internal inconsistency as a conflict, not a fiction.**
Real codebases disagree with themselves — two error-handling styles,
naming drift across packages. Do not pick one and pretend it is
uniform. Register the dominant practice (evidence on both sides),
record the variance in §2, and state the stance *for the change
surface*: which practice NEW/CHANGED modules follow, and whether the
divergent practice in UNTOUCHED modules is left as-is (usual) or
noted as future work (a note, not a mandate).

**Establish standards; defer elaboration to the sibling frameworks.**
Security-implicating patterns (secret handling, audit logging) flag
for Step 04; data-implicating patterns (ownership, transactional
posture) for Step 05; doc conventions for Step 06;
ownership-adjacent conventions for Step 07. The flags appear in the
register's Notes column and in §4.

**Run the per-artifact scorecard before committing.**
Score the register against all six Core Principles under the
inherited Phase 2 weights — PASS/CONDITIONAL/FAIL with rationale —
*before* declaring it complete. A FAIL means revise, not annotate.
The contribution feeds the Step 12 refresh; weights are never
adjusted here.

**Re-verify subject identity and bundle currency at step start.**
*Inherited.* Confirm the subject version and that no Phase 3
amendment has landed since Step 02. If the subject advanced or a
scheduled mechanism shipped early via a parallel track, apply the
concurrent-release decision rule from the instructions file.

**Do not produce implementation.**
Patterns are standards, not code. "Errors carry a machine-readable
code (SP-03)" is a pattern; the error class hierarchy is Phase 5
work. If content drifts toward function bodies or configuration
files, redirect: "Phase 5 will produce this from the specification."

---

## Kickoff

> Paste this line to begin. Paste the Step 02 Baseline & Scoping
> Document, the Phase 3 Bundle §1 and §2, the Step 01 §9 gap
> register, and any existing convention documents above it.

```
I'm starting Step 03 of Phase 4 (Shared Architectural Patterns &
Standards). The Step 02 Architecture Baseline & Integration Scoping
Document and supporting inputs are pasted above. Please re-verify
bundle currency, read the inputs thoroughly, then ask your
clarifying questions one at a time. After that, walk the ten pattern
domains in order — observing existing practice with evidence before
deciding codify/extend/add — and produce the Shared Architectural
Patterns & Standards register with provenance tags, the conflicts
section, the per-artifact scorecard contribution, and handoff notes.
```

---

## Clarification Step

Read the Step 02 document and the Phase 3 bundle sections thoroughly
first. Note the change surface (§2), the depth calibration (§4), the
declared code-access mode, and any Step 01 §9.1 local gaps touching
pattern domains. Then ask between **3 and 7 clarifying questions**,
never more, one at a time.

**The first question is a presence check:** "I have the Step 02
baseline and the Phase 3 bundle. Are there existing convention
documents — style guides, contribution guides, lint/formatter
configurations, ADRs about conventions — I should treat as evidence
alongside the code?"

Permitted clarification topics:

1. **Authority of documented conventions.** Where convention
   documents exist, are they followed or aspirational? A style guide
   the code contradicts is a §2 conflict, not an [EXISTING-CODIFIED]
   pattern.

2. **Known inconsistencies.** Which practices does the practitioner
   already know are inconsistent (error styles, logging shapes,
   naming drift)? This targets the observation work and pre-seeds §2.

3. **Deliberate deviations from stack idioms.** A deliberate
   deviation is codified with its rationale; an accidental one may be
   a conflict.

4. **Backward-compatibility commitments.** Published consumers,
   semver posture, deprecation promises — these constrain the
   versioning domain and any [EXTENDED] element touching a public
   surface.

5. **Regression anchor for testing conventions.** Which existing
   test suite(s) are the "must keep passing" anchor? Step 09
   regression surfaces will cite the conventions codified here.

6. **Depth calibration confirmation.** Confirm the Step 02 §4
   calibration still holds, and whether any domain should be waived
   (with reason) for this run.

Do not ask the practitioner to produce security controls, data
constraints, documentation strategy, or governance — those are Steps
04–07. Do not ask for module boundaries — that is Step 08. After the
clarifications, proceed to the domain-by-domain procedure.

---

## Domain-by-Domain Procedure

Walk the ten domains in order. For each domain, run the same three
moves, then move on. Depth per domain follows the Step 02 §4
calibration; a waived domain is recorded as waived with reason, and
the procedure skips to the next.

**Move 1 — Observe.** Establish what the codebase actually does in
this domain, with evidence per the declared code-access mode: cite
paths and interfaces (Search-primary/Hybrid, flags on Hybrid claims)
or testimony plus [QUESTION] flag (Interview-only). Observe across
the change surface *and* a sample of UNTOUCHED modules — the
UNTOUCHED sample is what protects against legislating standards the
system contradicts.

**Move 2 — Decide.** For each observed practice and each
change-surface need: codify ([EXISTING-CODIFIED] — the default),
extend ([EXTENDED] — name the existing practice, the delta, and the
Phase 3 specification or Step 02 §2 entry that requires it), or add
([NEW] — name what requires it and scope it via Applies-To). Write
each element as a concrete, citable pattern statement with an SP-NN.

**Move 3 — Record conflicts.** Where observation surfaced internal
inconsistency, or a proposed [NEW]/[EXTENDED] element contradicts
UNTOUCHED-module practice, record the conflict in §2 with evidence
on both sides and a per-conflict stance for the change surface.

### D1 — Error Handling

How errors are signaled (exceptions, result types, error codes,
revert reasons), propagated, wrapped, and surfaced at public
boundaries; any error taxonomy in use. Trigger: contract-type Phase
3 specifications enumerate error conditions — codify the signaling
pattern they assume so Step 09 §2 can enumerate against it.
Error-detail-leakage implications flag for Step 04.

### D2 — Logging

What gets logged, in what structure, at what levels, through which
facility; required context fields; where logging is absent by
design. Trigger: Phase 3 observability touchpoint specifications
assume a logging substrate — codify the one the touchpoints will
emit through. Audit-logging implications flag for Step 04.

### D3 — Configuration

How modules receive configuration (files, environment, injected
parameters); source precedence; defaults; how secrets stay out of
configuration artifacts. Trigger: refactor-type specifications that
alter injection or wiring (e.g., the Diamonds run's MC-21
Signer-injection refactor) extend the existing pattern rather than
replace it. Secret handling flags for Step 04.

### D4 — Naming Conventions

Observed conventions for packages/modules, types, operations, files,
persisted fields, events, and public artifacts. Codify what is
actually consistent; drift goes to §2, not into a fictional uniform
rule. Trigger: new public surfaces named by Phase 3 contract or
schema specifications follow (or explicitly extend) the observed
conventions; Step 11 applies these standards to the contracts.

### D5 — Standard Module Structure

The internal organization existing modules actually follow: public
entry points, internal layout, test location, doc location, build
outputs. Codify the dominant shape; divergence in UNTOUCHED modules
is a §2 note, not a remediation mandate. Trigger: NEW modules follow
the codified structure unless a [NEW] element scoped to them says
otherwise.

### D6 — Inter-Module Communication & Dependency Direction

How modules talk (direct calls, events, shared artifacts) and which
dependency directions are allowed: layering, import-path rules,
circular-dependency posture, integration-peer boundaries from Step
02 §1.2. Trigger: contract-type specifications that move a seam
(e.g., the MC-04 IDeploymentStrategy contract) make the dependency
direction across it a citable pattern Step 08 boundary decisions
lean on.

### D7 — Data Access

How modules read and write persistent state and durable artifacts
(databases, files, records, caches); ownership conventions;
atomicity posture where one exists. Codify the access *patterns*
only — classification, ownership registers, and integrity
constraints are Step 05 (flag data implications for it). Trigger:
schema-type specifications assume an emission/consumption pattern.

### D8 — Versioning & Backward Compatibility

How the system versions itself and its public surfaces: package
versioning scheme, deprecation practice, compatibility guarantees to
published consumers, migration expectations. Trigger: any Phase 3
specification altering a public surface forces this domain to state
what compatibility the change set owes; Step 11 contracts apply the
versioning standard.

### D9 — Resilience / Failure Handling

How the system behaves when dependencies fail: retries, timeouts,
idempotency, partial-failure recovery — as actually practiced, which
is often thinner than the greenfield ideal. Codify what exists; do
not invent a resilience architecture the change set will not build.
Trigger: Step 09 §4 dependency sections cite the failure-handling
patterns registered here.

### D10 — Testing Conventions

Where tests live, how they are named, fixture and isolation
patterns, which suites exist and which are the regression anchor,
coverage expectations as actually enforced. Trigger: every Step 09
§7 test strategy and regression surface cites these conventions;
Phase 3 verification-artifact specifications assume a harness shape
— codify it.

### Closing Move — Register Assembly

Assemble §1 grouped by domain, numbering SP-NN in register order.
Confirm every element has exactly one provenance tag, evidence or
flag, and Applies-To scoping. Then produce §2, run the §3 scorecard
contribution *before* committing, and write the §4 handoff notes.

---

## Output Format

Produce the artifact using this exact structure. All sections are
required; a waived domain still appears in §1 with its waiver line.

```markdown
# Shared Architectural Patterns & Standards — Phase 4 (Architecture & Modular Design)

**Project:** [subject name and version]
**Artifact Date:** [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]
**Design Specification Bundle Version:** [version + date]
**Step 02 Baseline Version:** [version + date]
**Code-Access Mode (from Step 00):** [Interview-only / Search-primary / Hybrid]
**Depth Calibration Applied (from Step 02 §4):** [summary or reference]
**Status:** Draft — Pending Practitioner Review

> ⚠️ This register codifies the codebase's existing practice first
> ([EXISTING-CODIFIED]), extends or adds only where the change
> surface requires ([EXTENDED] / [NEW]), and scopes every element via
> its Applies-To column. It is a conformance reference: Steps 04–09
> and 11 cite SP-NN; Steps 10 and 12 verify the citations. It is not
> a system-wide style mandate — [NEW] elements bind only where their
> Applies-To column says.

---

## §1 — Pattern Register (SP-NN)

Grouped by domain. Provenance: [EXISTING-CODIFIED] / [EXTENDED] /
[NEW]. Evidence: code path(s) or testimony, with
[CONFIRM]/[AWARE]/[QUESTION] flag per the code-access mode.
Applies To: [Change surface / System-wide].

### §1.1 — Error Handling

| SP-NN | Domain | Pattern Statement | Provenance | Evidence (path/testimony + flag) | Applies To | Notes |
|-------|--------|-------------------|------------|----------------------------------|------------|-------|
| SP-01 | Error Handling | [concrete, citable statement] | [tag] | [path or testimony + flag] | [scope] | [e.g., flagged for Step 04] |

[If waived: **Domain waived** — [reason + Step 02 §4 reference].]

### §1.2 — Logging … §1.10 — Testing Conventions

[Repeat the §1.1 table shape for each remaining domain, one
subsection per domain, in this order: §1.2 Logging; §1.3
Configuration; §1.4 Naming Conventions; §1.5 Standard Module
Structure; §1.6 Inter-Module Communication & Dependency Direction;
§1.7 Data Access; §1.8 Versioning & Backward Compatibility; §1.9
Resilience / Failure Handling; §1.10 Testing Conventions. A waived
domain appears as its heading plus the waiver line.]

---

## §2 — Conflicts, Exceptions & Scope Notes

### §2.1 — Internal Inconsistencies Observed

| # | Domain | Conflicting Practices (evidence both sides) | Dominant Practice | Stance for the Change Surface | Affected SP-NN |
|---|--------|---------------------------------------------|-------------------|-------------------------------|----------------|
| 1 | | | | [which practice NEW/CHANGED modules follow; UNTOUCHED left as-is or noted as future work] | |

### §2.2 — [NEW]/[EXTENDED] Scope Notes

| SP-NN | Why not [EXISTING-CODIFIED] | Change-Surface Need (Phase 3 spec / Step 02 §2 entry) | UNTOUCHED-Module Contradiction? | Resolution |
|-------|-----------------------------|--------------------------------------------------------|---------------------------------|------------|
| | | | [None / describe] | [Scoped to change surface / conflict surfaced to practitioner] |

### §2.3 — Waived Domains

| Domain | Waiver Reason | Step 02 §4 Reference |
|--------|---------------|----------------------|
| | | |

---

## §3 — Per-Artifact Principle Scorecard Contribution

Weights inherited from Phase 2 Step 02 unchanged. Produced before
this artifact was committed.

| Principle | Weight | Contribution | Rationale (cite specific SP-NN / §2 entries) |
|-----------|-------:|--------------|----------------------------------------------|
| Security | | [PASS/CONDITIONAL/FAIL] | |
| Maintainability | | | |
| Economics | | | |
| Operations | | | |
| Scoring & Metrics | | | |
| Correctness Verification | | | |

[Any FAIL: the register is revised before commitment, not committed
with an annotation. CONDITIONALs name the remediation and owner.]

---

## §4 — Handoff Notes

| Consumer | What It Consumes | Specific SP-NN |
|----------|------------------|----------------|
| Step 04 (Security) | Patterns flagged with security implications to elaborate as SEC-NN controls | |
| Step 05 (Data) | Data-access patterns to ground DA-NN constraints | |
| Step 06 (Documentation) | Doc-location/convention patterns to reconcile | |
| Step 07 (Governance) | Ownership-adjacent conventions observed | |
| Step 08 (Impact Map) | Patterns available for per-module constraint assignment | |
| Step 09 (Change Specs) | The conformance set — every specification cites the SP-NN it honors | |
| Step 11 (Formal Contracts) | Contract standards: naming, error shapes, versioning | |
| Steps 10 / 12 (Verification) | The full register — citation and provenance verification | |

[Plus: any Phase 5 pre-implementation verification notes attached to
Interview-only evidence; any Step 01 §9.1 gap resolutions recorded
here.]

---

## Version

**v1.0 — [date] — Initial Shared Architectural Patterns & Standards
register for this Phase 4 run.** [Amend and increment if a Phase 3
amendment or a Step 10/12 finding forces revision.]
```

---

## Evaluation Checklist

Before this artifact is accepted as complete, verify all items:

- [ ] Every register element has an SP-NN, exactly one provenance tag
      ([EXISTING-CODIFIED] / [EXTENDED] / [NEW]), and an evidence
      citation (path in Search-primary/Hybrid; testimony + flag in
      Interview-only) — no untagged or unevidenced elements
- [ ] Every element has an Applies-To scope (change surface /
      system-wide)
- [ ] Every [NEW] element is either scoped explicitly to the change
      surface or its contradiction with UNTOUCHED-module practice is
      surfaced in §2 with a practitioner resolution — none is
      legislated system-wide by default
- [ ] Every [EXTENDED] element names the existing practice it extends
      and the change-surface need (Phase 3 specification or Step 02
      §2 entry) that requires the delta
- [ ] All ten domains from the Step 02 §4 calibration are covered at
      calibrated depth, or explicitly waived in §2.3 with reason —
      none silently omitted
- [ ] Every pattern statement is concrete enough to be cited by a
      Step 09 module change specification and verified by Steps 10
      and 12 (no "handle errors consistently")
- [ ] §2.1 records each observed internal inconsistency with evidence
      on both sides and a per-conflict stance for the change surface
- [ ] Patterns with security, data, documentation, or governance
      implications are flagged for Steps 04–07 elaboration, not
      elaborated here
- [ ] §3 scorecard contribution is present — all six principles,
      inherited weights unchanged, PASS/CONDITIONAL/FAIL with
      rationale, produced before commitment
- [ ] §4 handoff notes name what Steps 08, 09, and 11 consume, plus
      any Phase 5 pre-implementation verification notes from
      Interview-only evidence
- [ ] No implementation content — no function bodies, migration
      scripts, CI configuration, or credential material
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)

---

*Part of the Phase 4 (Existing Projects) Architecture & Modular Design Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `architecture-modular-design.existing-project.instructions.md`*
*Previous step: `step-02-architecture-baseline-and-integration-scoping.prompt.md`*
*Next step: `step-04-security-architecture-framework.prompt.md`*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Shared Architectural Patterns & Standards prompt for the existing-projects track, adapted from the greenfield Phase 4 Step 02 counterpart. Central shift: reconcile, don't invent — a domain-by-domain observe/decide/record procedure codifies the codebase's actual practice first with evidence citations per the declared code-access mode, and extends or adds only where the change surface requires. Every SP-NN element carries a provenance tag ([EXISTING-CODIFIED] / [EXTENDED] / [NEW]), evidence or flag, and Applies-To scoping; [NEW] elements that contradict UNTOUCHED-module practice are scoped or conflict-surfaced, never legislated system-wide by default. Ten pattern domains (greenfield's cross-cutting-concerns category folded into the domains; testing conventions added for the regression-surface discipline), with depth following the Step 02 §4 calibration and explicit waivers. Output pinned to §1 Pattern Register / §2 Conflicts, Exceptions & Scope Notes / §3 per-artifact scorecard contribution / §4 handoff notes for Steps 08, 09, and 11. |
