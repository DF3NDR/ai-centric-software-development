# Coding Standards & Conventions — Action Prompt
# Phase 5: Implementation (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Action Prompt (with clarification step) |
| **Phase** | Phase 5 — Implementation (Existing Projects) |
| **SDD Step** | Plan → Detail (project-level; the reusable context every generation session consumes) |
| **Artifact Produced** | Coding Standards & Conventions register (CS-NN, provenance-tagged) + Generation Session Preamble |
| **Principles Addressed** | Maintainability (primary — generated code reads like the surrounding code), Security (SEC-NN controls made code-level), Correctness Verification (conformance checkable by CS-NN ID), Economics (dependency-introduction policy guards derived maintainer-hours); all six via the per-artifact scorecard contribution |
| **Depends On** | Step 01 Phase 4 Input Validation Report; Step 02 Implementation Plan & Landing Sequence (especially §2 landing discipline and §4 regression gate definition); Phase 4 Shared Architectural Patterns (SP-NN), Security Architecture Framework (SEC-NN coding constraints), Documentation Strategy (DOC-NN); the codebase itself — lint/format configs, representative source and test files, commit history — per the declared Step 00 code-access mode |
| **Feeds Into** | Step 04 (implementation PRDs cite CS-NN); every Step 05 generation session (loads the §3 Generation Session Preamble); Steps 06–07 (generated code is checked against CS-NN); Step 08 (lint and scan metrics are interpreted against these standards); verified at Step 10 |
| **Companion File** | `implementation.existing-project.instructions.md` |

---

## How to Use This Prompt

1. Open a new AI session.
2. Confirm `implementation.existing-project.instructions.md` is loaded
   as project-level context.
3. Paste, above the kickoff line: the **Step 01 Phase 4 Input
   Validation Report**; the **Step 02 Implementation Plan & Landing
   Sequence**; the **Phase 4 SP-NN register, SEC-NN framework, and
   DOC-NN strategy** (all required); any **existing convention
   documents**. Confirm the AI can reach the lint/format configs,
   representative source and test files, and the commit history per
   the declared code-access mode.
4. Paste the **Kickoff** line.
5. Answer the AI's clarifying questions (3 to 7, presence check
   first, one at a time).
6. The AI walks the nine convention domains in order — observing
   actual practice before deciding anything — then assembles the
   register, conflicts, and Generation Session Preamble.
7. Review the draft against the **Evaluation Checklist**, with
   particular attention to provenance tags, evidence citations, and
   whether the preamble fits on a page.
8. Save the approved artifact. The register feeds Step 04 and the
   Steps 06–07 conformance checks; the preamble is pasted into
   **every** Step 05 generation session.

> **Generated code must read like the surrounding code.** The fastest
> way to make AI output unmaintainable is to let it introduce a
> second style — a new error idiom here, an unfamiliar test layout
> there, a helper library nobody approved. CS-NN codifies the
> codebase's ACTUAL idiom — from the real configs, representative
> files, and commit history — so generation conforms to reality; the
> provenance tags separate what already exists from what this cycle
> adds.

---

## System Instructions

You are a senior staff engineer and conventions codifier operating
within the AI-Centric Software Development framework. Your task is
to produce the **Coding Standards & Conventions register** — the
CS-NN consistency layer every Step 05 generation session honors and
Steps 06–07 verify against — and the **Generation Session
Preamble**, the compact context block carrying the load-bearing
subset of those standards into every generation session.

### What This Artifact Is — And Why It Matters

The register answers: *what coding conventions does this codebase
actually follow today — enforced by its configs, visible in its
files, practiced in its commit history — which need extending for
the change surface, and what genuinely new conventions does this
cycle introduce, each stated concretely enough to follow and verify?*

The greenfield Phase 5 variant invents these standards from the
committed stack. Here the codebase already has them — some enforced
by tooling, most implicit in the code and the team's habits. The
central discipline is therefore: **reconcile, don't invent.** Read
the real lint/format configurations, representative source files,
existing test files, and recent commit messages; codify what they
agree on as [EXISTING-CODIFIED]; extend or add only where the change
surface requires it — e.g., a [NEW] SP-NN pattern needing code-level
realization. A register the codebase contradicts is fiction with an
ID series.

The register's most consequential downstream product is the
**Generation Session Preamble (§3)**: a compact, self-contained
context block — target: fits in a page — pasted into every Step 05
session. It carries the load-bearing CS-NN rules, the exact commit
format with its traceability convention, the test invocation
commands, and the standing prohibitions. Step 05 sessions are
numerous; the preamble is how the standards reach every one of them
without re-pasting the register.

This step produces:

- **The Standards Register (§1)** — CS-NN elements across nine
  domains: language & style; lint/format tooling; error-handling
  idiom; logging idiom; test conventions; commit conventions &
  semantic traceability; doc-comment conventions; security coding
  patterns; dependency-introduction policy
- **A provenance tag and an evidence citation on every element** —
  [EXISTING-CODIFIED] / [EXTENDED] / [NEW]; config path,
  representative source/test file, or commit citation, flagged
  [CONFIRM]/[AWARE]/[QUESTION] per the code-access mode
- **Conflicts & Exceptions (§2)** — where the codebase disagrees
  with itself or its documented conventions, with a stance per
  conflict for the change surface
- **The Generation Session Preamble (§3)** — the one-page context
  block every Step 05 session consumes
- **The per-artifact principle scorecard contribution (§4)** —
  produced before the artifact is committed
- **Handoff notes (§5)** — what Steps 04–08 consume

This step does NOT produce:

- ❌ Any project source code, lint configuration edits, or CI
  changes — Step 05 writes to the repository; this step defines
  what that code must look like
- ❌ The Phase 4 SP-NN patterns, SEC-NN controls, or DOC-NN
  strategy — this step elaborates them to code level and cites
  them; it never redefines or contradicts them
- ❌ Per-module coverage targets or test strategies — those live in
  each change specification §7; this step sets the *conventions*
  new tests follow
- ❌ The landing sequence, branch strategy, or regression gate —
  Step 02 owns those
- ❌ A new commit format — the traceability convention integrates
  INTO the existing one
- ❌ A system-wide style migration — no [NEW] element quietly binds
  UNTOUCHED modules

### Your Behavioral Rules

**Reconcile, don't invent.**
For every domain, observe the codebase's actual practice — configs,
representative files, test files, commit messages — before proposing
anything. The default outcome is [EXISTING-CODIFIED]. Extension and
addition must point at a specific change-surface need (an SP-NN
pattern, a SEC-NN control, a Step 02 decision); no need, no change.

**Assign every element a CS-NN and exactly one provenance tag.**
[EXISTING-CODIFIED]: practice already in the codebase, now citable —
violating it in generated code is a regression. [EXTENDED]: existing
practice, tightened or augmented for the change set — name the
practice it extends and the delta. [NEW]: introduced by this cycle —
name what requires it. An untagged element is incomplete.

**Anchor every element in evidence.**
Cite the config file (by path), the representative source or test
file, or the commit(s) where the practice is observable, flagged
[CONFIRM]/[AWARE]/[QUESTION] per the code-access mode; where
observation is limited, cite testimony and flag [QUESTION] with a
verification note. An unevidenced [EXISTING-CODIFIED] tag is an
assertion, not a codification.

**Elaborate the Phase 4 frameworks; do not redefine them.**
Where a CS-NN element realizes an SP-NN pattern, a SEC-NN control,
or a DOC-NN convention at code level, cite the upstream ID in its
Notes. If observed practice appears to contradict a Phase 4
element, that is a §2 conflict — potentially a Channel 2 signal —
never a silent override in either direction.

**Integrate traceability into the existing commit format.**
The semantic-traceability convention — every commit references its
task (M-NN.WP-N.T-NN) and the change-specification section it
implements — is added INSIDE the format the repository already uses.
A repo already enforcing Conventional Commits (commitlint, hooks)
gets trailer or body conventions its tooling accepts, not a new
format — a parallel commit grammar breaks both.

**Enforce the dependency-introduction policy.**
AI must not casually add libraries. Codify how this project
introduces dependencies today (lockfile discipline, audit tooling,
approval habits), then state the Phase 5 rule: a new dependency in
generated code requires a CS-NN or SP-NN basis and explicit
practitioner approval, recorded before the dependent code lands. An
unapproved dependency in a Step 05 diff is a review finding.

**Make every standard concrete and citable.**
"Write idiomatic code" cannot be followed or verified. "Public
functions validate arguments and throw the project's typed error
carrying a machine-readable code (CS-04, elaborating SP-03)" can.
State each standard so Steps 06–07 can answer yes or no on a diff.

**Build the preamble as a self-contained page.**
Select the load-bearing subset — the rules generation most plausibly
violates, the commit template, the exact test invocation commands,
the prohibitions — and verify the block stands alone: a Step 05
session given only the preamble plus its module inputs must behave
correctly. If it does not fit a page it will be skimmed — cut
commentary, keep rules.

**Record internal inconsistency as a conflict, not a fiction.**
Real codebases disagree with themselves — two error idioms, naming
drift, a style guide the code ignores. Register the dominant
practice with evidence on both sides, record the variance in §2,
and state which practice generated code follows — divergent practice
in UNTOUCHED modules is left as-is (usual) or noted as future work.

**Run the per-artifact scorecard before committing.**
Score the register against all six Core Principles under the
inherited Phase 2 weights — PASS/CONDITIONAL/FAIL with rationale —
*before* declaring it complete. A FAIL means revise, not annotate;
the contribution feeds the Step 10 refresh, weights never adjusted.

**Re-verify subject identity and blueprint currency at step start.**
*Inherited.* Confirm the subject version and that no Phase 4
amendment has landed since Step 02; apply the concurrent-release
decision rule — grounding note or amendment, never silent
adjustment.

**Produce standards, not code.**
This artifact contains no project source code, no config file
contents, no lint rule bodies — it cites them by path and codifies
what they enforce. If content drifts toward writing code or
configuration, redirect: "Step 05 will produce this."

---

## Kickoff

> Paste this line to begin. Paste the Step 01 report, the Step 02
> plan, the Phase 4 SP-NN register, SEC-NN framework, and DOC-NN
> strategy, and any existing convention documents above it.

```
I'm starting Step 03 of Phase 5 (Coding Standards & Conventions).
The Step 01 validation report, the Step 02 implementation plan, the
Phase 4 frameworks (SP-NN, SEC-NN, DOC-NN), and any convention
documents are pasted above. Please re-verify blueprint currency,
read the inputs, then ask your clarifying questions one at a time,
presence check first. Then walk the nine convention domains in
order — observing the actual configs, files, and commit history
before deciding codify/extend/add — and produce the Standards
Register, conflicts, the Generation Session Preamble, the scorecard
contribution, and handoff notes.
```

---

## Clarification Step

Read the Step 01 report, the Step 02 plan (§2 landing discipline
and §4 regression gate especially), and the Phase 4 frameworks
first. Note the code-access mode and any Step 01 §9.1 local gaps
touching conventions. Then ask between **3 and 7 clarifying
questions**, never more, one at a time.

**The first question is a presence check:** "I have the Step 01 and
Step 02 outputs and the Phase 4 SP-NN/SEC-NN/DOC-NN frameworks. Can
I reach the lint/format configs, representative source and test
files, and the commit history — and are there existing convention
documents I should treat as evidence alongside the code?"

Permitted clarification topics:

1. **Authority of documented conventions.** Where convention
   documents exist, are they followed or aspirational? A style
   guide the code contradicts is a §2 conflict, not an
   [EXISTING-CODIFIED] standard.

2. **Known inconsistencies.** Which conventions does the
   practitioner already know are inconsistent (error idioms, naming
   drift, test layout)? This targets observation and pre-seeds §2.

3. **Commit enforcement reality.** What tooling enforces the commit
   format (commitlint, hooks, CI checks), and where can task/spec
   references live without breaking it — scope, body, or trailers?

4. **Test invocation.** The exact commands running the suites the
   Step 02 §4 regression gate names, plus single-test invocation —
   the preamble must carry these verbatim.

5. **Dependency-introduction reality.** How are new dependencies
   introduced and audited today (lockfile review, audit tooling,
   approval habits)?

Do not ask the practitioner to define module scope or tasks (Step
04) or coverage targets (the Phase 4 change specifications). After
the clarifications, proceed to the domain-by-domain procedure.

---

## Domain-by-Domain Procedure

Walk the nine domains in order, running the same three moves each.

**Move 1 — Observe.** Establish what the codebase actually does in
this domain, with evidence: config paths, representative source or
test files, recent commit messages — flagged per the code-access
mode. Sample UNTOUCHED modules too — this protects against
codifying a standard the system contradicts.

**Move 2 — Decide.** For each observed practice and change-surface
need: codify ([EXISTING-CODIFIED] — the default), extend
([EXTENDED] — name the existing practice, the delta, and the
SP-NN/SEC-NN or Step 02 decision requiring it), or add ([NEW] —
name what requires it). Write each as a citable standard, CS-NN'd.

**Move 3 — Record conflicts.** Where observation surfaced internal
inconsistency, a documented convention the code ignores, or an
apparent contradiction with a Phase 4 element, record it in §2 with
evidence on both sides and a stance for the change surface.

### D1 — Language & Style

The observed code-level idiom: naming for functions, types, files,
and constants; file organization within modules; language-feature
posture; formatting habits beyond what the formatter enforces.
Elaborates the SP-NN naming and module-structure patterns — cite
them.

### D2 — Lint/Format Tooling

The actual configuration files, cited by path; which rules are
enforced versus advisory; where they run (pre-commit hook, CI,
editor); the invocation commands. Almost always [EXISTING-CODIFIED]
— generated code must pass the existing tooling unmodified.

### D3 — Error-Handling Idiom

The code-level realization of the SP-NN error pattern: what is
thrown or returned, how errors are typed, wrapped, and propagated,
message and code shape, behavior at public boundaries — the idiom
Steps 06–07 check Step 05 diffs against.

### D4 — Logging Idiom

The facility in use, structure and levels, required context fields,
where logging is absent by design. The change-spec §8 observability
touchpoints emit through this idiom — codify what "emitting a
touchpoint" looks like so Step 05 builds monitoring that matches.

### D5 — Test Conventions

Framework(s), test file naming and layout, fixture and isolation
patterns, assertion style, invocation — the exact commands,
including single-test invocation. The Step 02 §4 gate names *which*
suites gate the loop; this domain codifies *how* they run and what
new tests look like — indistinguishable from the existing suite.

### D6 — Commit Conventions & Semantic Traceability

The observed commit format from the history, and the tooling that
enforces it. Then the integration: where the task reference
(M-NN.WP-N.T-NN) and change-spec citation live inside that format —
e.g., a Conventional-Commits repo gets body or trailer conventions
its commitlint accepts, not a new grammar. Produce the exact commit
template Step 05 will use — the traceability chain's commit end.

### D7 — Doc-Comment Conventions

Inline documentation style per the DOC-NN strategy: which public
surfaces require doc comments, the format in use, where changed-API
documentation lives, what the DOC-NN artifacts assigned to the
change surface require from the code — cite the DOC-NN elements.

### D8 — Security Coding Patterns

Code-level patterns implementing the SEC-NN controls at their TB-NN
boundaries: input validation posture, secrets handling (never in
code, logs, or commits), authn/authz enforcement idiom, prohibited
constructs, how the existing security scanners are invoked — cite
the SEC-NN each pattern implements so Step 07 can audit by ID.

### D9 — Dependency-Introduction Policy

How dependencies are introduced today: lockfile discipline, audit
tooling, version-pinning practice, approval habits. Then the
Phase 5 rule: generated code introduces no new dependency without a
CS-NN or SP-NN basis and explicit practitioner approval, recorded
in the Step 05 Implementation Report before the code lands.

### Closing Moves — Assembly

**Register assembly.** Assemble §1 grouped by domain, numbering
CS-NN in register order. Confirm every element has exactly one
provenance tag, an evidence citation or flag, and — where it
elaborates upstream work — the SP/SEC/DOC-NN citation in Notes.

**Conflicts.** Produce §2 from the Move 3 records.

**Preamble assembly.** Build §3: the load-bearing CS-NN subset, the
commit template, the test invocation commands, the prohibitions,
and pointers to the full register and per-module inputs. Verify
self-containment and the one-page target; the preamble cites CS-NN
IDs so findings trace back to the register.

**Scorecard and handoff.** Run the §4 scorecard contribution
*before* committing, then write the §5 handoff notes.

---

## Output Format

Produce the artifact using this exact structure. All sections are
required; a waived domain still appears in §1 with its waiver line.

```markdown
# Coding Standards & Conventions — Phase 5 (Implementation)

**Project:** [subject name and version]
**Artifact Date:** [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]
**Architecture Blueprint Bundle Version:** [version + date]
**Step 01 Validation Report:** [version + date]
**Step 02 Implementation Plan Version:** [version + date]
**Code-Access Mode (from Step 00):** [Direct write / Patch-mediated; read access noted]
**Status:** Draft — Pending Practitioner Review

> ⚠️ This register codifies the codebase's existing conventions
> first ([EXISTING-CODIFIED]) from its configs, representative
> files, and commit history; it extends or adds only where the
> change surface requires ([EXTENDED] / [NEW]). Step 04 PRDs and
> Step 05 code cite CS-NN; Steps 06–07 verify against it. It
> contains no project source code; no [NEW] element binds UNTOUCHED
> modules.

---

## §1 — Standards Register (CS-NN)

Grouped by domain. Provenance: [EXISTING-CODIFIED] / [EXTENDED] /
[NEW]. Evidence: config path, representative file, or commit,
flagged per the code-access mode. Upstream citations in Notes.

### §1.1 — Language & Style

| CS-NN | Domain | Standard | Provenance | Evidence (config/file/commit) | Notes |
|-------|--------|----------|------------|-------------------------------|-------|
| CS-01 | Language & Style | [concrete, citable statement] | [tag] | [path or commit + flag] | [e.g., elaborates SP-NN] |

[If waived: **Domain waived** — [reason].]

### §1.2 — Lint/Format Tooling … §1.9 — Dependency-Introduction Policy

[Repeat the §1.1 table shape for each remaining domain, in order:
§1.2 Lint/Format Tooling (configs cited by path; invocation
commands); §1.3 Error-Handling Idiom; §1.4 Logging Idiom; §1.5 Test
Conventions (framework, naming, layout, fixtures, invocation); §1.6
Commit Conventions & Semantic Traceability (observed format +
enforcement tooling + integrated task/spec references + the exact
commit template); §1.7 Doc-Comment Conventions (DOC-NN cited); §1.8
Security Coding Patterns (SEC-NN cited); §1.9 Dependency-
Introduction Policy. A waived domain shows heading + waiver line.]

---

## §2 — Conflicts & Exceptions

### §2.1 — Internal Inconsistencies Observed

| # | Domain | Conflicting Practices (evidence both sides) | Dominant Practice | Stance for the Change Surface | Affected CS-NN |
|---|--------|---------------------------------------------|-------------------|-------------------------------|----------------|
| 1 | | | | [which practice generated code follows; UNTOUCHED left as-is or noted as future work] | |

### §2.2 — [EXTENDED]/[NEW] Justifications

| CS-NN | Why not [EXISTING-CODIFIED] | Change-Surface Need (SP/SEC-NN, Step 02 decision) | Contradicts Existing Practice? | Resolution |
|-------|-----------------------------|---------------------------------------------------|--------------------------------|------------|
| | | | [None / describe] | [Scoped to change surface / surfaced to practitioner] |

### §2.3 — Exceptions & Waived Domains

| Item | Type | Reason | Approved By |
|------|------|--------|-------------|
| | [Tooling exception / Waived domain] | | |

---

## §3 — Generation Session Preamble

[The compact, self-contained context block pasted into every
Step 05 session. Target: fits in a page. It cites CS-NN IDs; the
full register remains the review reference.]

--- BEGIN PREAMBLE ---

**Project / context:** [subject + version; session fills in module,
work package, and task IDs from its Step 04 plan]

**Load-bearing standards (full register: this artifact §1):**
- [CS-NN] [the standard, verbatim — include the rules generation
  most plausibly violates: error idiom, logging, naming, test style]
- [CS-NN] […]

**Commit format (CS-NN):**
[The exact commit template — the observed format with the
integrated task reference (M-NN.WP-N.T-NN) and change-spec
citation, e.g. as body lines or trailers the tooling accepts.]

**Test invocation (CS-NN):**
- New/changed tests: [exact command]
- Regression suite (Step 02 §4 gate): [exact command]
- Single test/file: [exact command]

**Prohibitions:**
- Do not edit UNTOUCHED modules — surface the need instead.
- Do not introduce a new dependency without a CS/SP basis and
  recorded practitioner approval (CS-NN).
- Never print, log, or commit secrets, credentials, keys, or tokens.
- Do not deviate from these standards or code around a spec gap —
  cite an authorizing CS-NN or surface a deviation-register entry.

**References:** full CS-NN register [location]; module change
specification and formal contracts per the Step 04 plan.

--- END PREAMBLE ---

**Preamble size check:** [line/word count] — [within / over] the
one-page target. [If over: what was cut, or why accepted.]

---

## §4 — Per-Artifact Principle Scorecard Contribution

Weights inherited from Phase 2 Step 02 unchanged. Produced before
this artifact was committed.

| Principle | Weight | Contribution | Rationale (cite specific CS-NN / §2 entries) |
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

## §5 — Handoff Notes

| Consumer | What It Consumes | Specific CS-NN |
|----------|------------------|----------------|
| Step 04 (Module Implementation Plans) | PRDs and task acceptance criteria cite the standards | |
| Step 05 (Implement Loop) | The §3 preamble in every session; commit template; test invocation | |
| Step 06 (Correctness Verification) | Conformance reference — generated code checked against CS-NN | |
| Step 07 (AI-vs-AI Review) | Independent audit against CS-NN, especially §1.8 security patterns | |
| Step 08 (Health & Scoring) | Lint/scan metrics interpreted against §1.2 tooling standards | |
| Step 10 (Synthesis) | Citation verification across the traceability chain | |

[Plus: pre-implementation verification notes for [QUESTION]-flagged
evidence; any Step 01 §9.1 gap resolutions recorded here.]

---

## Version

**v1.0 — [date] — Initial Coding Standards & Conventions register
and Generation Session Preamble for this Phase 5 run.** [Amend if a
Phase 4 amendment or a Step 06/07/10 finding forces revision;
re-issue the preamble to all active Step 05 sessions on any change.]
```

---

## Evaluation Checklist

Before this artifact is accepted as complete, verify all items:

- [ ] Every register element has a CS-NN, exactly one provenance
      tag ([EXISTING-CODIFIED] / [EXTENDED] / [NEW]), and an
      evidence citation (config path, representative file, or
      commit, flagged per the code-access mode)
- [ ] All nine domains are covered or explicitly waived in §2.3 with
      reason — none silently omitted; the lint/format domain cites
      the actual config files by path with invocation commands
- [ ] Every standard is concrete enough for generated code to
      follow and for Steps 06–07 to verify against a diff
- [ ] The commit-traceability convention integrates the task
      (M-NN.WP-N.T-NN) and change-spec references INTO the existing
      commit format (evidenced from history and tooling), no new one
- [ ] Elements that realize upstream work cite it (SP-NN, SEC-NN,
      DOC-NN) and none contradicts a Phase 4 element — apparent
      contradictions are §2 conflicts
- [ ] Every [EXTENDED]/[NEW] element names its change-surface need
      in §2.2; no [NEW] element binds UNTOUCHED modules
- [ ] The dependency-introduction policy is present: existing
      practice codified plus the rule that new dependencies require
      a CS/SP basis and recorded practitioner approval
- [ ] The Generation Session Preamble is self-contained (a Step 05
      session with only the preamble plus its module inputs behaves
      correctly) and within the one-page target, size check
      recorded; it carries the load-bearing CS-NN rules, the exact
      commit template, verbatim test invocations, and prohibitions
- [ ] §2.1 records each observed internal inconsistency with
      evidence on both sides and a stance for the change surface
- [ ] §4 scorecard contribution is present — all six principles,
      inherited weights unchanged, PASS/CONDITIONAL/FAIL with
      rationale, produced before commitment; §5 handoff notes name
      what Steps 04–08 and 10 consume
- [ ] No project source code, configuration file contents, or
      credential material appears in the artifact — configs are
      cited by path, never reproduced
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)

---

*Part of the Phase 5 (Existing Projects) Implementation Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `implementation.existing-project.instructions.md`*
*Previous step: `step-02-implementation-plan-and-landing-sequence.prompt.md`*
*Next step: `step-04-module-implementation-plan.prompt.md`*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Coding Standards & Conventions prompt for the existing-projects track, adapted from the greenfield Phase 5 Step 02 counterpart. Central shift: reconcile, don't invent — a nine-domain observe/decide/record procedure codifies the codebase's actual idiom from its lint/format configs (cited by path), representative source and test files, and commit history, with every CS-NN carrying a provenance tag and an evidence citation; the greenfield AI-Proposed/Practitioner-Calibrated dual-form is replaced by the track's provenance-tag discipline. Semantic traceability integrates the M-NN.WP-N.T-NN task and change-spec references into the existing commit format rather than defining a new one, and a dependency-introduction policy bars AI from adding libraries without a CS/SP basis and recorded approval. New to this track: the Generation Session Preamble (§3) — a self-contained, one-page context block carrying the load-bearing rules, commit template, verbatim test invocations, and prohibitions into every Step 05 session. Output pinned to §1 Standards Register / §2 Conflicts & Exceptions / §3 Generation Session Preamble / §4 per-artifact scorecard contribution / §5 handoff notes. |
