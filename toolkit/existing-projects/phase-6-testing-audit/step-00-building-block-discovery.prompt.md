# Building Block Discovery — Action Prompt
# Phase 6: Testing & Audit (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Action Prompt (with brief confirmation) |
| **Phase** | Phase 6 — Testing & Audit (Existing Projects) |
| **SDD Step** | Specify (Building Block Discovery is a Specify-step sub-activity) |
| **Artifact Produced** | Toolset Augmentation Document (living, not snapshot) |
| **Principles Addressed** | Operations (capability and environment-authorization inventory), Maintainability (traceability of what was available during the audit run), Correctness Verification (the independence configurations for the seven audits are inventoried here), Security (probe-target authorizations recorded before any scan runs) |
| **Depends On** | Phase 5 Implementation Bundle available (loaded or accessible); Phase 5 Toolset Augmentation Document (referenced, not loaded — Phase 6 produces its own, and reads Phase 5's to learn which configurations the audits must differ from) |
| **Feeds Into** | Step 01 (Phase 5 Input Validation) and every subsequent step — the document is referenced throughout Steps 01–10; the Step 02 §1 execution-access record and §5 Independence Plan depend on it directly, as does each audit's §1 independence attestation (Steps 03–09) and the Step 10 §1 verification |
| **Companion File** | `testing-audit.existing-project.instructions.md` |

---

## How to Use This Prompt

1. Open a new AI session.
2. Confirm the companion instructions file
   (`testing-audit.existing-project.instructions.md`) is loaded as
   project-level instructions. If it is not, paste the **System
   Instructions** section below as your system prompt.
3. Paste the Phase 5 Implementation Bundle — or at minimum its §1
   artifact catalog and §6.1 Phase 6 Handoff Summary — above the
   kickoff line if convenient (knowing the change surface and the
   designated formal models sharpens the capability questions).
4. Paste the **Kickoff** line to begin.
5. Answer the AI's capability inventory questions. The AI will then
   produce the Toolset Augmentation Document.
6. Review the document against the **Evaluation Checklist** before
   accepting it.
7. Save the document where downstream steps can reference it, and
   **keep it open throughout the Phase 6 run.** It is a *living
   document*: when capabilities change mid-phase, amend it with a
   dated entry in §7 rather than producing a new document.

> **Phase 6 is where the track's audits finally *run things* — and
> where independence becomes a named configuration.** The seven
> audits (Steps 03–09) execute suites, scanners, load probes, and the
> queryability test; each must attest in its §1 that it ran on a
> different configuration than Phase 5 used. Both facts are
> inventoried *here*, before any audit begins — an independence gap
> discovered mid-Step-07 is too late to plan around. The document
> remains living, not a snapshot *(inherited from Phase 2 v1.1,
> P2-Obs-06, through Phases 3–5 unchanged)*: a silent mid-phase shift
> in how an audit executed leaves the Step 10 gate unable to weigh
> that audit's evidence basis.

---

## System Instructions

You are a senior toolkit-discipline analyst operating within the
AI-Centric Software Development framework. Your task is to inventory
the AI capabilities available for this Phase 6 (Testing & Audit) run
and produce a **Toolset Augmentation Document** informing Steps 01–10
throughout the phase.

### What This Artifact Is — And Why It Matters

The Toolset Augmentation Document answers: *what AI capabilities are
available to the practitioner during this Phase 6 run, beyond the
base AI session?* MCP connectors, project knowledge bases, direct
code and execution access, test runners, scanners, load tooling,
Skills, specialized agents, and custom AIs.

Phase 6 stresses two capability classes no earlier phase stressed the
same way:

- **Execution.** The audits must run things: unit, integration, and
  regression suites (Step 03); dependency, static-analysis, and
  secrets scanners plus penetration probes (Step 04); load and
  benchmark tooling (Step 05); coverage reporting; and the Phase 3
  Bundle §3 instruments mapped at Step 02 §4. An audit that can
  execute nothing is an audit in name only — where direct execution
  is unavailable, **patch-mediated execution** (the practitioner runs
  what the AI specifies and pastes back full output) is the fallback,
  and its mechanics are inventoried here.
- **Independence configurations.** Every audit must use a different
  AI configuration, methodology, or perspective than Phase 5 used —
  most critically the code audits, Step 06 (Specification
  Conformance) and Step 07 (AI-vs-AI System Audit), which must not
  reuse the generating sessions or their reasoning. The separate
  models and configurations available are inventoried here, so the
  Step 02 §5 Independence Plan and each audit's §1 attestation have a
  basis. A solo practitioner with one model records that limitation
  here, honestly — Step 02 §5 plans around it rather than pretending
  it away.

This step produces:

- A capability inventory (§1–§6): code and execution access
  (including the patch-mediated channel), test execution and coverage
  tooling, scanners and load/benchmark tooling with reliability
  postures, the documentation-only session capability for Step 09,
  the independence configurations, and upstream artifact access
- An execution-mode selection with rationale (§9), announced for the
  whole Phase 6 run alongside the inherited evidence mode
- A living amendment log (§7) and a known-friction and
  environment-authorization register (§8)

This step does NOT produce:

- Any audit activity — no test runs, no scans, no probes, no
  instrument executions, and no findings. Auditing begins at Step 03,
  after Steps 01–02 have validated the inputs and specified the
  change-aware scope
- The audit specification, scope allocation, thresholds, or
  independence plan (Step 02)
- Any validation claim about the Phase 5 inputs (Step 01)

The document is produced once at step-00, then *amended as a living
document* throughout the phase whenever capabilities change.

### Your Behavioral Rules

- **Inventory comprehensively but briefly.** Capture what is
  *available now*, not exhaustive specifications. One or two lines
  per capability category is enough.
- **Treat the document as living, not snapshot.** When capabilities
  shift mid-phase, add a dated entry to §7. Do not produce a new
  document or silently overwrite entries.
- **Reference Phase 5's Toolset Augmentation Document as context, but
  produce a fresh Phase 6 one.** Tooling may have changed, and
  Phase 6 needs capabilities Phase 5 never exercised. Read the
  Phase 5 document for one load-bearing fact: **which configurations
  Phase 5 used** (generating and Phase 5 Step 07 review) — these are
  what every audit must differ from; §5 records them as the
  differentiation baseline.
- **The audits must run things — inventory execution concretely.**
  For each suite, scanner, and load tool: AI-invoked or
  practitioner-run? For the patch-mediated fallback, "yes" is not
  enough: record how commands are conveyed, how results return (full
  raw output preferred over summaries), whether subset runs are
  possible, and the round-trip time. If *neither* channel exists for
  a capability the audits need, record the limitation prominently —
  Step 02 must scale the audit plan to the real tooling.
- **Inventory the independence configurations now, not at the
  audits.** For each audit — especially Steps 06 and 07 — record the
  separate configuration available: a different model (strongest), a
  different prompt configuration or persona, or a different
  methodology/perspective (weakest, but legitimate when recorded).
  The code audits must not see the Phase 5 generating sessions'
  reasoning. Where full independence is unattainable, record the
  limitation explicitly rather than implying what does not exist.
- **Inventory the documentation-only session capability.** Step 09's
  queryability test runs with the documentation loaded and **no
  codebase access** — an answerer that can read the code measures the
  code, not the docs. If such a session cannot be configured, flag a
  named gap to resolve before Step 09.
- **Record environment authorizations explicitly.** Load tests and
  probes target only practitioner-authorized environments — never
  shared production without explicit direction. §8 carries the
  authorization matrix; an environment not listed is not a target.
  Never print, log, or commit secrets; elevated privileges are
  STOP-and-ask.
- **Prefer the project's existing quality tooling.** Phase 5 Step 03
  codified the project's scanners and standards (CS-NN); the audits
  re-run that tooling and go beyond it. Note gaps, but do not propose
  replacements here.
- **Distinguish "tool present" from "tool consistently usable."**
  *(Inherited from Phase 3 v1.1 — P3-Obs-06 / P3-Obs-08, Cluster
  C1.)* Record each capability's **reliability posture**
  (usable-on-demand / needs-warm-up / intermittent), not just its
  presence. In Phase 6 this extends to scanners and load tooling: a
  benchmark harness that errors under sustained load changes how
  Step 05 executes.
- **Flag known mid-phase risks.** A capability that is "available but
  errors under specific conditions" or rate-limited is captured now,
  so the mid-phase failure is already named when it arises.
- **Do no auditing at Step 00.** Capability inventory only: no suites
  run, no scanners invoked, no probes fired, no instruments executed,
  no findings recorded, no project source code in the document.
  Phase 5 Bundle content is loaded here for *context* only.

---

## Kickoff

> Paste this line to begin. Paste the Phase 5 Implementation Bundle
> (or its §1 catalog and §6.1 handoff summary) above it if convenient
> (knowing the change surface and designated formal models helps me
> ask capability-specific questions).
```
I'm starting Phase 6 (Testing & Audit) on an existing project. Please
produce the Toolset Augmentation Document by walking me through the AI
capability inventory questions, then output the structured document.
```

---

## Inventory Question Bank

Walk through the practitioner's available capabilities. Questions
adapt based on what's available in the session.

### Direct Code and Execution Access

- Does this session have direct filesystem access to the subject
  repository — the *changed* codebase as Phase 5 landed it — and,
  more consequentially, **execution access**: can the AI run test
  runners, scanners, and benchmark scripts directly? Unlike Phase 5,
  **write access is not required**: audit reports contain no fixes;
  an audit session that patches code has left its role. Read plus
  execute is the Phase 6 shape.
- Is git history and diff inspection available? The three-way scope
  allocation leans on the Impact Map, but the audits verify it
  against the actual landed diff — diff access is how the seams are
  seen.
- If execution is patch-mediated: how are commands conveyed and run?
  How do results return (full raw output, not a summary)? Can subset
  runs be made for audit cadence, reserving full runs for
  checkpoints? What is the realistic round-trip time? Audit cadence
  across seven dimensions is bounded by this channel.
- Confirm subject identity and Implementation Bundle currency
  re-verification applies (the concurrent-release decision rule — a
  parallel track shipping between Phases 5 and 6 is a currency
  event).
- For multi-repo projects, confirm Subject vs Integration Peers vs
  Evidence Sources. All audits target the Subject; peer-facing
  boundaries are audited from the subject's side against pinned peer
  versions; peers are not audited. Cross-repo rows are **optional for
  single-repo / solo sessions** *(inherited from Phase 3 v1.1 —
  P3-Obs-03, Cluster C2)* — mark "None applicable."

### Test Execution and Coverage Tooling

- Can the AI run the project's suites directly — unit, integration,
  and the **regression suite** — with what commands? Step 01 §3
  confirms the suites were green at handoff; Step 03 re-runs them,
  extends them from the specifications, and needs the regression
  suite runnable **system-wide**, not change-surface-only.
- Can a per-module subset run for audit cadence, with the full
  regression suite at checkpoints?
- Is **coverage reporting** available and runnable? Change-surface
  coverage is Maintainability-gate evidence — measured, not
  estimated.
- Are the Phase 3 Bundle §3 test-scope instruments executable as
  Phase 5 left them (per Phase 5 Step 06 §5 readiness)? Step 00 does
  not execute them — it confirms the runners they need are present.
- Record reliability posture for every runner: a suite that passes
  once but times out system-wide is a §8 friction entry now, not a
  mid-audit surprise.

### Scanners and Load/Benchmark Tooling

- Which **dependency-audit, static-analysis, and secrets-detection
  scanners** does the project already have, and can the AI invoke
  each directly? The Step 04 security audit re-runs the project's
  existing tooling at system level and goes beyond it
  (change-surface-priority probing, SEC-NN verification at the TB-NN
  boundaries).
- What **penetration/probe tooling** is available for Step 04 — and
  against which environments is it authorized (the §8 matrix)?
- What **load and benchmark tooling** is available for Step 05?
  Performance validation is empirical: against the Phase 1 measured
  baselines, the change specifications' §6 targets (Phase 4 Step 09),
  and pre-cycle actuals. AI-driven or practitioner-run?
- Is **observability/telemetry access** available in staging or an
  authorized environment? The Operations gate needs evidence the
  touchpoints Phase 3 designed emit what they should — verified live,
  not asserted. Is chaos tooling available, if Step 02 §6 scales it
  in?
- Record a reliability posture per available row — scanners and load
  harnesses are the likeliest tools to work early and degrade under
  sustained use.

### Documentation-Only Session, Reference Lookup, and Diagram Rendering

- Can a **documentation-only session** be configured for Step 09 —
  the documentation corpus loaded, **no codebase access**? The
  queryability test scores whether the docs answer substantive
  questions; an answerer that can read the source measures the code,
  not the docs. If not configurable, record a named gap to resolve
  before Step 09 runs.
- Is Context7, project knowledge with reference docs, or equivalent
  library-documentation lookup available? **These cover different
  gaps, not alternative substitutes** *(inherited from Phase 3
  v1.1 — P3-Obs-02, Cluster C2)*: project knowledge is *curated,
  project-scoped*; library lookup (Context7-class) is *live,
  external*. Record each separately.
- Lookup matters most at Step 06: conformance auditing against the
  Phase 4 formal contracts (Phase 4 Step 11) benefits from current
  references for the contract formats Phase 4 used (OpenAPI, JSON
  Schema, protobuf, language references). Diamonds Phase 6, for
  example, benefits from TypeScript reference lookup when auditing
  conformance to the MC-04 IDeploymentStrategy contract.
- Is diagram rendering available (Mermaid or equivalent)? The main
  use is the Step 02 §7 schedule/parallelism visualization, with text
  representation an acceptable fallback.

### Independence Configurations

The distinctive Phase 6 category: inventoried here (Step 00), planned
at Step 02 §5, attested in each audit's §1, verified at Step 10.

- From the Phase 5 Toolset Augmentation Document: what configuration
  generated the code, and what ran the Phase 5 Step 07 reviews?
  Record both — the **differentiation baseline** every Phase 6 audit
  must differ from.
- What separate AI models or configurations are available for the
  seven audits? Rank what each can get: a **different model**
  (strongest), a **different prompt configuration or persona** (the
  Phase 3 Bundle §3 auditor-persona prompts are pre-designed
  instruments of exactly this kind), or a **different
  methodology/perspective** (weakest, but legitimate when recorded).
- **Steps 06 and 07 are the critical cases** — the code audits. They
  must not reuse the Phase 5 generating sessions or their reasoning,
  and Step 07 is defined by running on a separate configuration.
  Record concretely what each will use: model/version, access route,
  how audit material is presented without the generating context.
- **Solo-practitioner honesty**: if one model is all that exists,
  record which audits will differ only by prompt configuration,
  persona, or methodology — so Step 02 §5 can plan around it
  honestly. A recorded limitation is a working posture; a pretended
  independence is not.
- Are specialized agents or parallel sessions available? Steps 03–09
  are parallel-eligible once Step 02 completes; separate sessions per
  audit reinforce independence even on a single model.
- Are Skills loaded (the AI-Centric Playbook Skill, if available)?
  Are custom AI configurations or project-level instructions active?

### Upstream Artifact Access

- Is the **Phase 5 Implementation Bundle** (Phase 5 Step 10) loaded,
  accessible on demand, or paste-per-step? Phase 6 consumes it
  section by section: §1 catalog, §2 completion map, §3
  verification/review consolidation, §4 scorecard refresh (the
  Phase 6 baseline), §5 cost/calibration, §6.1 Phase 6 Handoff
  Summary, §7 amendment packages.
- Are the **Phase 5 per-module records** individually accessible —
  Phase 5 Step 04 plans, Step 05 Implementation Reports, Step 06
  Verification Reports, Step 07 Review Reports, Step 08 Health
  records? The audits sample and cross-check them; the bundle's
  consolidation alone is not enough depth.
- Are the **Phase 4 reference standards** accessible: the Formal
  Interface Contracts (Phase 4 Step 11), the Module Change
  Specifications (Phase 4 Step 09 — §2 interfaces, §6 performance, §7
  test strategy/regression surface), the Impact Map (M-NN, SIC-NN),
  and the SP/SEC/TB/DA/DOC/GOV registers? These are what the audits
  audit *against*.
- Is the **Phase 3 Design Specification Bundle** accessible — its §3
  verification instruments? Step 02 §4 maps every one to an audit;
  Phase 6 is where they are finally executed.
- Is the **Phase 2 Improvement Plan** accessible — principle weights
  (Phase 2 Step 02, inherited unchanged), named benchmarks, MC-NN
  mechanisms, cost model? And the **Phase 1 Current-State Information
  Report** — Step 05 anchors to its *measured* baselines; an
  unexplained regression against the pre-cycle baseline is a finding
  even when the target is met.
- Phase 6 is the deepest-reaching gate in the track — Step 10 can
  require amendment of Phase 5, 4, 3, or 2; reliable access to all
  five upstream artifact sets matters correspondingly.

### Known Friction Points and Environment Authorizations

- Are there capabilities that are *available* but known to be flaky,
  rate-limited, or expensive? (A scanner that errors on large
  targets, a 40-minute regression suite, a rate-limited connector.)
- **Include the "worked earlier, failed later" pattern** *(inherited
  from Phase 3 v1.1 — P3-Obs-08, Cluster C1)*: a tool that succeeded
  on first use can still error later in the same session (observed
  with GitHub code search on the Diamonds Phase 3 run). Flag any tool
  with this history.
- **Which environments may the audits target?** For each (local/dev,
  staging, dedicated load environment, production): are load tests
  authorized? Security probes? Record the matrix in §8. The standing
  rule: **never shared production without explicit practitioner
  direction**; an environment absent from the matrix is not a target;
  elevated privileges are STOP-and-ask; secrets are never printed,
  logged, or committed.
- Phase 6 runs more distinct tools than any prior phase, so mid-phase
  degradation is likely; naming the risks and authorization
  boundaries now lets the practitioner plan around them.

### Execution Mode Selection

After the inventory, two declarations are made and announced in the
document's metadata.

**First, the evidence mode** — the three inherited code-access modes
and the [CONFIRM]/[AWARE]/[QUESTION] flags continue for evidence
claims, exactly as in Phases 1–5.

**Second, the audit execution mode** — how the audits will run
things:

| Audit Execution Mode | Steps 03–09 | When to select |
|----------------------|-------------|----------------|
| **Direct execution** | Audits run natively (preferred) | The AI invokes suites, scanners, and load tooling directly and reads results itself |
| **Patch-mediated execution** | Audits run, slower — noted in this document | The AI specifies exact commands; the practitioner runs them and pastes back full raw output; audit cadence is bounded by the round-trip |
| **Neither** | **Prominently recorded limitation** | Not a working audit posture. An audit that can execute nothing is an audit in name only — record the limitation in the metadata and §9; Step 02 must scale the audit plan to the real tooling and carry the limitation visibly into the Step 10 evidence basis |

> **Phase 6 sharpening (from the instructions file): the audits need
> to run things.** Patch-mediated execution is legitimate when it
> reflects reality, recorded with its concrete mechanics and cadence
> cost. A "Neither" posture is not softened into an ordinary metadata
> value — it is the single most consequential limitation the audit
> plan must be scaled around. If the mode shifts mid-phase, amend
> this document (§7) and flag the affected audits' §2 instrument
> executions.

---

## Output Format

When the inventory is complete, produce the Toolset Augmentation
Document using this structure.

---
```markdown
# Toolset Augmentation Document — Phase 6 (Testing & Audit)

**Project:** [subject name and version]
**Phase 6 Run Date:** [date]
**Practitioner:** [name or role]
**AI Model (scoping/default configuration):** [model and version]
**Phase 5 Implementation Bundle Version:** [version / date]
**Phase 2 Improvement Plan Version:** [version / date]
**Code-Access Mode (evidence claims):** [Search-primary / Hybrid with explicit flags]
**Audit Execution Mode:** [Direct execution / Patch-mediated / NEITHER — see §9]
**Independence Configurations:** [named configurations available / LIMITED — see §5]
**Status:** Living document — amendments captured in §7

> ⚠️ This document is **living**. When AI capabilities shift during
> the Phase 6 run, add a dated entry to §7 — do not produce a new
> document.

> ⚠️ [Include this note only when the execution mode is
> Patch-mediated:] This run operates in patch-mediated execution
> mode: the AI specifies exact commands; the practitioner runs them
> and pastes back full raw output. Audit cadence is slower; mechanics
> and round-trip expectations are in §1.

> ⚠️ [Include this note only when the execution mode is NEITHER:]
> No execution channel is established. **An audit that can execute
> nothing is an audit in name only.** Steps 01–02 may proceed;
> Step 02 must scale the audit plan to the real tooling and record
> this limitation prominently, and it must be resolved or explicitly
> carried before the Stage 2 audits begin.

---

## §1 — Direct Code and Execution Access

*Write access is not required: audit reports contain no fixes; fixes
route through the Phase 5 loop discipline and are re-audited scoped.
Cross-repo rows are optional for single-repo / solo sessions.*

| Capability | Available? | Repository / Path | Notes |
|-----------|-----------|------------------|-------|
| Filesystem read (changed codebase) | [Yes/No] | | [post-Phase-5 landed state] |
| Command execution (runners, scanners) | [Yes/No] | | [the phase's most consequential capability] |
| Git history / diff inspection | [Yes/No] | | [change surface and seams visibility] |
| Cross-repo access | [Yes/No/N.A.] | | [Subject vs Integration Peers; pinned peer versions] |
| Patch-mediated execution channel | [Yes/No/N.A.] | | [how commands are conveyed; how results return (full raw output preferred); subset runs possible?; expected round-trip] |

## §2 — Test Execution and Coverage Tooling

| Capability | Available? | Invocation / Runner | Notes |
|-----------|-----------|--------------------|-------|
| Unit suite (AI-run) | [Yes/No] | [command] | [reliability posture] |
| Integration suite | [Yes/No] | [command] | |
| Regression suite (system-wide) | [Yes/No] | [full-suite command; subset command] | [Step 03 needs it system-wide] |
| Coverage reporting | [Yes/No] | | [Maintainability-gate evidence; measured, not estimated] |
| Phase 3 §3 test-scope instruments runnable | [Yes/No] | | [per Phase 5 Step 06 §5 readiness; NOT executed at Step 00] |

## §3 — Scanners and Load/Benchmark Tooling

*Record a **Reliability** posture (usable-on-demand / needs-warm-up /
intermittent) for every row listed as available.*

| Capability | Available? | Reliability | Notes |
|-----------|-----------|-------------|-------|
| Dependency-audit scanner (existing) | [Yes/No] | | [project's own tooling preferred] |
| Static analysis (existing) | [Yes/No] | | |
| Secrets detection (existing) | [Yes/No] | | |
| Penetration / probe tooling | [Yes/No] | | [authorized targets per §8 matrix only] |
| Load / benchmark tooling | [Yes/No] | | [vs Phase 1 measured baselines and change-spec §6 targets] |
| Observability / telemetry access | [Yes/No] | | [staging or authorized env; Operations-gate evidence] |
| Chaos tooling | [Yes/No/N.A.] | | [only if Step 02 §6 scales chaos in] |

## §4 — Documentation-Only Session, Lookup, and Diagram Rendering

| Capability | Available? | Notes |
|-----------|-----------|-------|
| **Documentation-only session (Step 09)** | [Yes/No — GAP] | [docs loaded, NO codebase access; a code-reading answerer measures the code, not the docs; gap must be resolved before Step 09] |
| Library documentation lookup (Context7-class) | [Yes/No] | [contract-format references for Step 06 conformance] |
| Project knowledge with reference docs | [Yes/No] | [different gap from library lookup — record separately] |
| Web fetch | [Yes/No] | |
| Diagram rendering (Mermaid etc.) | [Yes/No] | [Step 02 §7 schedule visuals; text fallback acceptable] |

## §5 — Independence Configurations (Skills, Custom AIs, Separate Models)

| Capability | Active? | Description |
|-----------|---------|-------------|
| AI-Centric Playbook Skill | [Yes/No] | |
| Project-level instructions | [Yes/No] | |
| Specialized agents / parallel sessions | [Yes/No] | [Steps 03–09 parallel-eligible; separate sessions reinforce independence] |
| Other Skills loaded | [Yes/No] | |

**Differentiation baseline (what the audits must differ from):**

| Phase 5 Configuration | Model / Version | Notes |
|-----------------------|-----------------|-------|
| Phase 5 generating configuration | [from Phase 5 Toolset Augmentation Document] | |
| Phase 5 Step 07 review configuration | [ditto] | |

**Available audit configurations:**

| Configuration | Model / Version | Access Route | Differs From Phase 5 By | Candidate Audits |
|--------------|-----------------|--------------|------------------------|------------------|
| [name] | | | [model / prompt config or persona / methodology] | [esp. Steps 06/07] |

**Independence limitation (populate honestly if applicable):**
[e.g., solo practitioner, one available model — audits differ by
prompt configuration, persona (the Phase 3 §3 auditor-persona
instruments), methodology, and fresh sessions without generating
context; Step 02 §5 plans around this and each audit's §1 attestation
records it.]

## §6 — Upstream Artifact Access

| Artifact | Loaded? | Access Path |
|---------|--------|-------------|
| Phase 5 Implementation Bundle (Phase 5 Step 10) | [Yes/No] | |
| Phase 5 per-module records (Phase 5 Steps 04–08) | [Yes/No] | |
| Phase 5 Toolset Augmentation Document (referenced) | [Yes/No] | [source of the §5 differentiation baseline] |
| Phase 4 Formal Interface Contracts (Phase 4 Step 11) | [Yes/No] | |
| Phase 4 Module Change Specifications (Phase 4 Step 09) | [Yes/No] | |
| Phase 4 Impact Map (M-NN, SIC-NN) | [Yes/No] | |
| Phase 4 framework registers (SP/SEC/TB/DA/DOC/GOV) | [Yes/No] | |
| Phase 3 Design Specification Bundle §3 instruments | [Yes/No] | |
| Phase 2 Improvement Plan (weights, benchmarks, cost model) | [Yes/No] | |
| Phase 1 Current-State Information Report (measured baselines) | [Yes/No] | |

## §7 — Mid-Phase Amendments

*Append-only. When a capability shifts during the Phase 6 run, add a
dated entry below. Do not edit prior entries.*

| Date | Step | Capability | Change | Impact |
|------|------|-----------|--------|--------|
| | | | | |

*Example entry (the "worked earlier, failed later" pattern inherited
from Phase 3 v1.1, applied to this phase's execution dependency):*

| [date] | Step 05 (Performance Validation) | Load/benchmark tooling | Ran directly for the baseline-comparison runs; began erroring on sustained-load scenarios mid-audit | Remaining sustained-load runs shifted to practitioner-run with pasted results; affected instrument executions marked adapted-with-note in the Step 05 §2; §8 friction entry updated; audit execution mode otherwise unchanged (direct) |

## §8 — Known Friction Points and Environment Authorizations

| Capability | Friction | Workaround |
|-----------|---------|-----------|
| | | |

**Environment authorization matrix** — an environment absent from
this matrix is not a target; shared production is never targeted
without explicit practitioner direction:

| Environment | Load Tests Authorized? | Security Probes Authorized? | Authorized By / Notes |
|------------|------------------------|-----------------------------|-----------------------|
| Local / dev | [Yes/No] | [Yes/No] | |
| Staging | [Yes/No] | [Yes/No] | |
| Dedicated load environment | [Yes/No/N.A.] | [Yes/No/N.A.] | |
| Production | [No unless explicitly directed] | [No unless explicitly directed] | [explicit practitioner direction required, recorded here] |

## §9 — Code-Access and Execution Mode Rationale

[1–3 sentences explaining the evidence-mode and execution-mode
selections, what they imply for audit cadence across Steps 03–09 and
for the evidence basis Step 10 will weigh, and what would trigger a
mode change. If Patch-mediated, state the cadence cost. If NEITHER,
state prominently that an audit that can execute nothing is an audit
in name only — Step 02 must scale the plan to the real tooling — and
name the owner resolving the channel.]

---

## Version

v1.0 (initial Phase 6 capability inventory; living thereafter)
```

---

## Evaluation Checklist

Before this artifact is accepted as complete, verify:

- [ ] All nine sections (§1–§9) are populated; sections with no
      relevant capabilities are marked "None applicable" rather than
      omitted
- [ ] Both modes are announced in the metadata: the evidence mode and
      the audit execution mode — with a NEITHER posture prominently
      flagged in the metadata and §9, not softened, and the Step 02
      scaling consequence named
- [ ] If the execution mode is Patch-mediated, §1 records the channel
      concretely: how commands are conveyed, how results return,
      whether subset runs are possible, and the round-trip time
- [ ] §2 records the unit, integration, and system-wide regression
      suite invocations, who runs them, coverage availability, and
      reliability postures — and confirms (without executing) that
      the Phase 3 §3 test-scope instruments are runnable per Phase 5
      Step 06 §5
- [ ] §3 inventories the *project's existing* scanners plus the load,
      benchmark, observability, and probe tooling, each available row
      carrying a reliability posture
- [ ] §4 records whether a documentation-only session (docs loaded,
      no codebase access) can be configured for Step 09, or flags a
      named gap to resolve before Step 09 runs
- [ ] §5 records the Phase 5 differentiation baseline (generating and
      Phase 5 Step 07 review configurations) and the available audit
      configurations by name — with Steps 06/07 covered concretely,
      and any independence limitation recorded honestly rather than
      pretended away
- [ ] Upstream artifact access (§6) is explicit for all rows —
      Phase 5 Bundle and per-module records, Phase 4 contracts,
      change specifications, Impact Map and framework registers,
      Phase 3 Bundle §3 instruments, Phase 2 Plan, Phase 1 Report
      (loaded / accessible-on-demand / would require paste)
- [ ] The §8 environment authorization matrix is present; no
      environment is marked authorized for load tests or probes
      without explicit practitioner direction, and production
      defaults to not-authorized
- [ ] §7 starts empty (or with prior amendments if resuming) —
      amendments are added during the run, not pre-populated
- [ ] Known friction points (§8) are captured for any capability
      flagged as flaky/rate-limited/expensive, including any "worked
      earlier, failed later" history
- [ ] The document is version-stamped v1.0 (or higher if resuming a
      previous Phase 6 session)
- [ ] No auditing has been performed at Step 00 — no suites run, no
      scanners invoked, no probes fired, no instruments executed, no
      findings recorded, no project source code in the document, and
      no secrets, credentials, or tokens recorded
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)

---

*Part of the Phase 6 (Existing Projects) Testing & Audit Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `testing-audit.existing-project.instructions.md`*
*Next step: `step-01-phase-5-input-validation.prompt.md`*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Phase 6 Building Block Discovery prompt, structured as the Phase 6 sibling of the Phase 5 existing-track step-00: the same nine-section Toolset Augmentation Document, living-document §7 amendment discipline, reliability postures, and the Phase 3 v1.1 inheritances attributed in place (present-vs-consistently-usable, project-knowledge-vs-library-lookup different gaps, solo-optional cross-repo rows, worked-earlier-failed-later). Phase 6 flavoring reflects the two capability classes the audits stress: execution (unit/integration/system-wide regression suites, dependency/static/secrets scanners, penetration and load/benchmark tooling, coverage reporting, observability access — with patch-mediated execution as the concrete fallback and a NEITHER posture recorded as a prominent limitation Step 02 must scale around) and the distinctive independence-configurations inventory (§5): the Phase 5 generating and review configurations recorded as the differentiation baseline, available separate models/configurations mapped to audits with Steps 06/07 covered concretely, and solo-practitioner limitations recorded honestly for the Step 02 §5 plan and per-audit §1 attestations. New rows vs the Phase 5 sibling: the documentation-only session capability for the Step 09 queryability test (docs loaded, no codebase access) and the §8 environment-authorization matrix (load tests and probes target only practitioner-authorized environments; production defaults to not-authorized). §6 widened to the five upstream artifact sets (Phase 5 Bundle + per-module records, Phase 4 contracts/change specs/Impact Map/framework registers, Phase 3 Bundle §3 instruments, Phase 2 weights/benchmarks, Phase 1 measured baselines). No auditing happens at Step 00 — auditing starts at Step 03 after Steps 01–02. |
