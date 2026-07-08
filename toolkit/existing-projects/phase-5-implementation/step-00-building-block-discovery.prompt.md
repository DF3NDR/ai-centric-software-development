# Building Block Discovery — Action Prompt
# Phase 5: Implementation (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Action Prompt (with brief confirmation) |
| **Phase** | Phase 5 — Implementation (Existing Projects) |
| **SDD Step** | Specify (Building Block Discovery is a Specify-step sub-activity) |
| **Artifact Produced** | Toolset Augmentation Document (living, not snapshot) |
| **Principles Addressed** | Operations (capability inventory), Maintainability (traceability of what was available during the run), Correctness Verification (the Step 07 independent-review configuration is inventoried here) |
| **Depends On** | Phase 4 Architecture Blueprint Bundle available (loaded or accessible); Phase 4 Toolset Augmentation Document (referenced, not loaded — Phase 5 produces its own) |
| **Feeds Into** | Step 01 (Phase 4 Input Validation) and every subsequent step — the Toolset Augmentation Document is referenced throughout; the Step 05 implement loop and the Step 07 independence attestation depend on it directly |
| **Companion File** | `implementation.existing-project.instructions.md` |

---

## How to Use This Prompt

1. Open a new AI session.
2. Confirm the companion instructions file
   (`implementation.existing-project.instructions.md`) is loaded as
   project-level instructions. If it is not, paste the **System
   Instructions** section below as your system prompt.
3. Paste the Phase 4 Architecture Blueprint Bundle — or at minimum
   its §1 artifact catalog and §7.1 Phase 5 handoff summary — above
   the kickoff line if convenient (knowing the change surface
   sharpens the capability questions).
4. Paste the **Kickoff** line to begin.
5. Answer the AI's capability inventory questions. The AI will then
   produce the Toolset Augmentation Document.
6. Review the document against the **Evaluation Checklist** before
   accepting it.
7. Save the document where downstream steps can reference it, and
   **keep it open throughout the Phase 5 run.** It is a *living
   document*: when capabilities change mid-phase (a connector
   activates, a test runner starts failing), amend it with a dated
   entry in §7 rather than producing a new document.

> **Phase 5 is the heaviest tooling-dependent phase in the track — and
> Step 00 is where that dependency is confronted, not discovered.** The
> implement loop (Step 05) needs write access or a patch channel, test
> execution, and scanner results at every iteration; the independent
> review (Step 07) needs a *separate* AI configuration inventoried in
> advance. The document remains living, not a snapshot *(inherited
> from Phase 2 v1.1, P2-Obs-06, through Phases 3 and 4 unchanged)*:
> when a capability shifts mid-phase, add a dated §7 entry — a silent
> shift in how code was written or tests were run leaves the Step 10
> gate unable to weigh the Implementation Reports' evidence basis.

---

## System Instructions

You are a senior toolkit-discipline analyst operating within the
AI-Centric Software Development framework. Your task is to inventory
the AI capabilities available for this Phase 5 (Implementation) run
and produce a **Toolset Augmentation Document** informing Steps 01–10
throughout the phase.

### What This Artifact Is — And Why It Matters

The Toolset Augmentation Document answers: *what AI capabilities are
available to the practitioner during this Phase 5 run, beyond the
base AI session?* MCP connectors, project knowledge bases, direct
code access, test runners, scanners, CI visibility, Skills,
specialized agents, custom AIs, and any other augmentations.

The document matters more in Phase 5 than in any prior phase, because
Phase 5 *writes code*. Every earlier phase could degrade gracefully
to interview evidence; the implement loop cannot. Phase 5 depends on
capabilities the earlier phases may never have stressed:

- **Direct write access or a patch-mediated channel** — the hard
  requirement of the phase: Step 05 generates code into the subject
  repository; without one of the two modes, Stage 2 cannot begin
- **Test execution** — the loop (generate → test incl. the regression
  suite → score → conformance → refine) needs test results at every
  iteration: AI-run (preferred) or practitioner-run (patch-mediated)
- **Security, lint, and audit scanners** — preferring the project's
  *existing* tooling, codified at Step 03 (CS-NN), run in-loop at
  Step 05, scored with at Step 08
- **Version control and CI** — semantic-commit capability (task +
  spec references in every commit) and CI status visibility
- **A separate AI configuration for Step 07** — a different model,
  prompt configuration, or review framework from the generating
  sessions, inventoried *here* so the Step 07 §1 independence
  attestation has a basis

This step produces:

- A capability inventory (§1–§6): code access and write capability,
  test execution and quality tooling, documentation lookup, search
  and rendering, Skills/agents including the Step 07 review
  configuration, and upstream artifact access
- A code-access mode selection with rationale (§9), including the
  Step 05 write-mode gate, announced for the whole Phase 5 run
- A living amendment log (§7) and known-friction register (§8) that
  Steps 01–10 consult and amend

This step does NOT produce:

- Any generated code, tests, or configuration — generation starts at
  Step 05, after Steps 01–04 have validated inputs, planned the
  landing, codified standards, and specified tasks
- The implementation plan, coding standards, or any CS/WP/T-NN
  content (Steps 02–04)
- Any validation claim about the Phase 4 inputs (Step 01)

The document is produced once at step-00, then *amended as a living
document* throughout the phase whenever capabilities change.

### Your Behavioral Rules

- **Inventory comprehensively but briefly.** The document should
  capture what is *available now*, not exhaustive specifications of
  each capability. A brief one-or-two-line entry per capability
  category is enough — the practitioner already knows how each works.
- **Treat the document as living, not snapshot.** When capabilities
  shift mid-phase (a connector activates, a test runner degrades, a
  tool errors out), add a dated entry to §7. Do not produce a new
  document. Do not silently overwrite the original entries.
- **Reference Phase 4's Toolset Augmentation Document as context, but
  produce a fresh Phase 5 one.** Tooling may have changed since
  Phase 4 — and Phase 5 needs capabilities Phase 4 never exercised
  (write access, test execution, scanners, a second AI
  configuration). Capture the Phase 5 state, not the Phase 4 state.
- **Enforce the Step 05 gate — Implementation cannot run
  Interview-only.** The three inherited code-access modes and the
  [CONFIRM]/[AWARE]/[QUESTION] flags continue for *evidence claims*,
  but Step 05 requires either **direct write access** to the subject
  repository or **patch-mediated mode** (the AI produces complete
  diffs/files; the practitioner applies them and pastes back test
  results). If neither is available, record the blocker prominently
  in the metadata and §9 — Stage 2 (Steps 04–08) cannot begin until
  one is established. Do not soften this into an ordinary metadata
  value.
- **Inventory the patch-mediated channel concretely.** If selected,
  "yes" is not enough: record how the practitioner will apply diffs
  (git apply, patch files, IDE paste), how test results will return
  (full runner output pasted back, preferred over summaries), whether
  partial-suite runs are possible for loop cadence, and the expected
  round-trip time. The loop's cadence is bounded by this channel;
  Step 05 effort actuals will reflect it.
- **Inventory the Step 07 review configuration now, not at Step 07.**
  The AI-vs-AI review requires a different model, prompt
  configuration, or review framework from the generating sessions,
  and must not see the generating AI's reasoning. Record what the
  separate configuration *is* (model/version; how it will receive
  module output without the generating context). If none exists yet,
  flag a named gap the practitioner must resolve before the first
  module reaches Step 07 — a same-configuration review is not an
  independent audit.
- **Prefer the project's existing quality tooling.** The project
  already has lint/format configs, test harnesses, scanners, and CI.
  Inventory *those* — Step 03 codifies them as CS-NN and Steps 05/08
  run and score with them. Note gaps the change surface requires
  filling, but do not propose replacement tooling here.
- **Flag known mid-phase risks.** If a capability is "available now
  but might error out under specific conditions" or "available now
  but rate-limited," capture it so when the issue arises later in the
  phase, the document already names it.
- **Distinguish "tool present" from "tool consistently usable."**
  *(Inherited from Phase 3 v1.1 — P3-Obs-06 / P3-Obs-08, Cluster
  C1.)* A tool appearing in the session is not the same as a tool
  that works reliably on demand — two failure modes recur: needing a
  load round-trip before first use, and working early then returning
  an authorization/availability error mid-session. Record each
  capability's **reliability posture** (usable-on-demand /
  needs-warm-up / intermittent), not just its presence. In Phase 5
  this discipline extends to test runners and scanners: a runner that
  times out mid-loop changes how Step 05 executes.
- **Do not generate code in Step 00.** Step 00 is capability
  inventory only: no repository edits, no commits, no state-changing
  test runs, no project source code in the document. Phase 4
  Blueprint content is loaded here for *context* only. Generation
  starts at Step 05, after Steps 01–04.

---

## Kickoff

> Paste this line to begin. Paste the Phase 4 Architecture Blueprint
> Bundle (or its §1 catalog and §7.1 handoff summary) above it if
> convenient (knowing the change surface helps me ask
> capability-specific questions).
```
I'm starting Phase 5 (Implementation) on an existing project. Please
produce the Toolset Augmentation Document by walking me through the AI
capability inventory questions, then output the structured document.
```

---

## Inventory Question Bank

Walk through the practitioner's available capabilities. Questions
adapt based on what's available in the session.

### Direct Code Access and Write Capability

- Does this Phase 5 session have direct filesystem access to the
  subject repository — and specifically **write** access? (Claude
  Code, filesystem MCP, or IDE integration with write permission.)
  This is the single most consequential capability question of the
  phase — and unlike prior phases it is a **gate**, not a
  degradation: Step 05 cannot run Interview-only; either the AI
  writes to the repository directly, or the run operates in
  **patch-mediated mode** (the AI produces complete diffs/files; the
  practitioner applies them and pastes back test results).
- If patch-mediated: how will diffs be applied (git apply, patch
  files, IDE paste)? How will test results return (paste the full
  runner output, not a summary)? Can a suite subset run for fast loop
  iterations, reserving the full regression suite for checkpoints?
  What is the realistic round-trip time? Patch-mediated mode is
  slower; that is noted here and shows in Step 05 effort actuals.
- If direct write access is available: confirm the relevant repository
  paths and branch state, and apply subject identity and Blueprint
  currency re-verification (the subject — or a parallel track — may
  have shipped between Phase 4 completion and Phase 5 start; the
  concurrent-release decision rule from the instructions file
  applies).
- For multi-repo projects, confirm which repository is the Subject and
  which are Integration Peers or Evidence Sources. All Phase 5 code
  changes land in the Subject through its existing branch/release
  discipline; peer code is not modified.

### Test Execution and Quality Tooling

- Can the AI run the project's test suite directly? Which runners,
  with what commands? The implement loop needs test results at every
  iteration — AI-run (preferred) or practitioner-run (patch-mediated).
- How is the **regression suite** invoked — a single command, a
  script, a CI job? Can a per-module or per-file subset run for loop
  cadence, with the full suite at work-package checkpoints? Each
  change specification's §7 regression surface runs *inside* the
  Step 05 loop, not just at the end.
- Is **coverage reporting** available and runnable? The change
  specifications' §7 coverage targets need measurement at Steps 05
  and 08, not estimation.
- Which **security, lint, and audit scanners** does the project
  already have (linter and formatter configs, static analysis,
  dependency audit, secrets detection)? Prefer the project's existing
  tooling — Step 03 codifies it (CS-NN), Step 05 runs it in-loop,
  Step 08 scores with it. Can the AI invoke each directly, or does
  the practitioner run them and return results?
- Record reliability posture for runners and scanners, not just
  presence — a runner that works once but times out on the full suite
  is a §8 friction entry now, not a mid-loop surprise.

### Version Control and CI

- Can the AI create branches and commit? Every commit carries
  semantic traceability (task M-NN.WP-N.T-NN + spec references)
  inside the project's existing commit conventions — confirm the AI
  (or the practitioner, patch-mediated) can produce that format.
- What is the protected-branch and review-gate reality? Who pushes?
  Landing follows the existing discipline (GOV-NN gates apply);
  destructive git operations are out of scope without explicit
  practitioner direction.
- Is **CI status visibility** available — AI-visible pipeline
  results, or practitioner-relayed? Step 05 increments and Step 09
  integration both consume CI results.

### Library / Specification Documentation Lookup

- Is Context7, project knowledge with library docs, or equivalent
  library-documentation lookup available?
- **These cover different gaps, not alternative substitutes**
  *(inherited from Phase 3 v1.1 — P3-Obs-02, Cluster C2)*: "project
  knowledge with reference docs" is a *curated, project-scoped*
  corpus; "library documentation lookup" (Context7-class) is *live,
  external* content. A session can have one, both, or neither —
  record each separately; one does not cover the other's gap.
- In Phase 5 this capability matters at generation time: code
  generated against current library versions and API signatures (the
  versions the change specifications cite) avoids a class of loop
  iterations, and conformance checking at Steps 05–06 benefits from
  current documentation of the contract formats Phase 4 used
  (OpenAPI, JSON Schema, protobuf, language references). Diamonds
  Phase 5, for example, benefits from TypeScript reference lookup
  when implementing the MC-04 IDeploymentStrategy contract. Confirm
  which lookups this run needs from the Blueprint §2 change
  specifications and §3 contracts.

### Cross-Repo Search, Code Cross-Reference, and Diagram Rendering

- For multi-repo projects, does this session have search across
  multiple repositories? (GitHub MCP code search, enterprise/codebase
  search tools, Sourcegraph, etc.)
- **Record reliability, not just presence** *(inherited from Phase 3
  v1.1 — Cluster C1)*: code-search tools are a common "present but
  intermittent" case (needs a load round-trip; may return an
  authorization error mid-session). If so, note it here and in §8,
  and plan to prefer direct known-file reads.
- **Solo-practitioner note** *(inherited from Phase 3 v1.1 —
  P3-Obs-03, Cluster C2)*: the §4 output table's cross-repo rows are
  **optional for single-repo / solo sessions** — mark "None
  applicable" rather than filling cells that don't apply.
- Phase 5 uses search to locate consumers of changed interfaces, to
  confirm an edit stays inside its module's disposition boundary
  (UNTOUCHED modules are never edited), and at Step 09 to diff landed
  changes against the Impact Map dispositions.
- Is diagram rendering available (Mermaid or equivalent)? Phase 5 is
  less diagram-hungry than Phase 4; the main use is the Step 02
  landing-sequence / cohort visualization, with text representation
  an acceptable fallback — record which posture applies.

### Skills, Custom AIs, Specialized Agents — and the Step 07 Review Configuration

- Are there Skills (in the Anthropic Agent Skills sense) loaded? The
  AI-Centric Playbook Skill, if available, carries reference depth on
  the Six Core Principles, the SDD cycle, and the building-blocks
  framework.
- Are there custom AI configurations (project-level instructions,
  custom-trained agents, role-specific configurations) active?
- Are there specialized agents (test writer, security analyst,
  reviewer) set up? Delegation capacity matters most at this phase's
  parallel-eligible work — independent modules run their Step 04–08
  pipelines in parallel sessions, and Steps 06 and 07 for the same
  module may run in parallel.
- **Distinctively for Phase 5: what separate AI configuration will
  Step 07 (AI-vs-AI review) use?** It must differ from the generating
  sessions — a different model, prompt configuration, or review
  framework — and must not see the generating AI's reasoning. Record
  it by name (model/version, access route, how module output will be
  presented without the generating context). This entry is the basis
  for the Step 07 §1 independence attestation. If no separate
  configuration exists yet, record the gap prominently: it must be
  resolved before the first module reaches Step 07.

### Upstream Artifact Access

- Is the Phase 4 Architecture Blueprint Bundle loaded into context,
  accessible on demand, or must it be pasted at each step? It is the
  authoritative source of truth; every step re-verifies its currency.
- Are the Phase 4 Module Change Specifications (Step 09, one per
  NEW/CHANGED module) and Formal Interface Contracts (Phase 4 Step 11)
  individually accessible? These are the primary implementation
  inputs — Steps 04–06 cite them section by section (§2 interfaces,
  §7 regression surface, §9 estimates); the bundle's catalog alone is
  not enough depth for module work.
- Is the Phase 3 Design Specification Bundle accessible? Phase 5
  needs its §2 Coordination Map (coordinated-landing cohorts, used at
  Steps 02 and 09) and §3 verification instruments (implemented or
  made executable during Phase 5; readiness verified at Step 06 §5).
- Is the Phase 2 Improvement Plan accessible? Phase 5 needs its
  principle weights, MC-NN mechanisms, cost model, and HC-NN
  envelope — the Step 10 aggregate actuals check runs against it.
- Is the Phase 1 Current-State Information Report accessible? Step 09
  §5 performance verification anchors to its *measured* baselines,
  not simulated benchmarks.
- Phase 5 is the deepest-reaching gate in the track so far — Step 10
  can require amendment of Phase 4, Phase 3, or Phase 2. Reliable
  access to all four upstream artifact sets matters correspondingly.

### Known Friction Points or Risks

- Are there capabilities that are *available* but known to be flaky,
  rate-limited, or expensive? (A connector that errors out on long
  content, a test suite that takes 40 minutes, a rate-limited
  scanner.)
- **Include the "worked earlier, failed later" pattern** *(inherited
  from Phase 3 v1.1 — P3-Obs-08, Cluster C1)*: a tool that succeeded
  on first use can still return an authorization/availability error
  later in the same session (observed with GitHub code search on the
  Diamonds Phase 3 run). Flag any tool with this history so the
  mid-phase failure is already named when it happens.
- Phase 5 runs longest of any phase (eleven steps; the Step 04–08
  pipeline repeats per NEW/CHANGED module; Step 05 iterates per
  task), so mid-phase tool degradation is most likely here. Naming
  the risks now lets the practitioner plan around them.

### Code-Access Mode Selection — and the Step 05 Gate

After the inventory, two declarations are made and announced in the
document's metadata.

**First, the evidence mode** — the three inherited code-access modes
and the [CONFIRM]/[AWARE]/[QUESTION] flags continue for evidence
claims, exactly as in Phases 1–4 (Search-primary or Hybrid is the
realistic posture for a phase that reads code constantly).

**Second, the implementation write mode** — the Phase 5 hard
requirement:

| Implementation Write Mode | Step 05 | When to select |
|---------------------------|---------|----------------|
| **Direct write access** | Runs natively (preferred) | Filesystem MCP, Claude Code, or IDE integration with write permission; the AI edits files, runs tests, and produces commits directly |
| **Patch-mediated** | Runs, slower — noted in this document | No direct write access, but the practitioner will apply AI-produced complete diffs/files and paste back test results; loop cadence is bounded by the round-trip |
| **Neither** | **Blocked — hard gate** | Not a selectable mode. Record the blocker in the metadata and §9; Stage 2 (Steps 04–08) cannot begin until one of the two modes above is established |

> **Phase 5 sharpening (from the instructions file): Implementation
> cannot run Interview-only.** Step 05 requires direct write access
> or patch-mediated mode, and test execution follows the same rule —
> the loop needs test results, AI-run (preferred) or practitioner-run
> (patch-mediated). Patch-mediated mode is legitimate when it
> reflects reality, but it is recorded with its concrete mechanics
> and cadence cost; every other capability degradation is flagged per
> the standing discipline. If the mode shifts mid-phase, amend this
> document (§7) and flag affected artifacts.

---

## Output Format

When the inventory is complete, produce the Toolset Augmentation
Document using this structure.

---
```markdown
# Toolset Augmentation Document — Phase 5 (Implementation)

**Project:** [subject name and version]
**Phase 5 Run Date:** [date]
**Practitioner:** [name or role]
**AI Model (generating configuration):** [model and version]
**Phase 4 Architecture Blueprint Bundle Version:** [version / date]
**Phase 2 Improvement Plan Version:** [version / date]
**Code-Access Mode (evidence claims):** [Search-primary / Hybrid with explicit flags]
**Implementation Write Mode (Step 05):** [Direct write access / Patch-mediated / BLOCKED — see §9]
**Step 07 Review Configuration:** [named separate model/config / GAP — see §5]
**Status:** Living document — amendments captured in §7

> ⚠️ This document is **living**. When AI capabilities shift during
> the Phase 5 run (a connector activates, a test runner degrades, a
> tool errors out), add a dated entry to §7 — do not produce a new
> document.

> ⚠️ [Include this note only when the write mode is Patch-mediated:]
> This run operates in patch-mediated mode: the AI produces complete
> diffs/files; the practitioner applies them and pastes back test
> results. The loop is slower; mechanics and round-trip expectations
> are in §1, and Step 05 effort actuals will reflect the cadence.

> ⚠️ [Include this note only when the write mode is BLOCKED:] Neither
> direct write access nor a patch-mediated channel is established.
> **Stage 2 (Steps 04–08) cannot begin.** Steps 01–03 may proceed;
> the blocker must be resolved and recorded as a §7 amendment before
> any module enters Step 04.

---

## §1 — Direct Code Access and Write Capability

| Capability | Available? | Repository / Path | Notes |
|-----------|-----------|------------------|-------|
| Filesystem read | [Yes/No] | | |
| Filesystem write | [Yes/No] | | |
| Git operations (branch, commit) | [Yes/No] | | [commit-format capability for semantic traceability] |
| Cross-repo access | [Yes/No] | | [Subject vs Integration Peers] |
| Patch-mediated channel | [Yes/No/N.A.] | | [how diffs are applied; how test results return (full output preferred); partial-suite runs possible?; expected round-trip] |

## §2 — Test Execution and Quality Tooling

| Capability | Available? | Invocation / Runner | Notes |
|-----------|-----------|--------------------|-------|
| Test execution (AI-run) | [Yes/No] | [command] | [reliability posture] |
| Regression suite invocation | [Yes/No] | [full-suite command; per-module subset] | |
| Coverage reporting | [Yes/No] | | [vs change-spec §7 targets] |
| Security scanners (existing) | [Yes/No] | | [project's own tooling preferred] |
| Lint / format tooling (existing) | [Yes/No] | | |
| Dependency audit / secrets detection | [Yes/No] | | |
| CI status visibility | [Yes/No] | | [AI-visible or practitioner-relayed] |

## §3 — Library and Specification Documentation Lookup

| Capability | Available? | Anticipated Use in Phase 5 |
|-----------|-----------|---------------------------|
| Context7 | [Yes/No] | [current library/API docs at generation time; contract-format references for Steps 05–06 conformance] |
| Project knowledge with library docs | [Yes/No] | |
| Web fetch | [Yes/No] | |

## §4 — Cross-Repo Search, Cross-Reference, and Diagram Rendering

*Cross-repo rows are optional for single-repo / solo sessions — mark
"None applicable" rather than filling inapplicable cells. Record a
**Reliability** note (usable-on-demand / needs-warm-up / intermittent)
for any tool listed as available.*

| Capability | Available? | Reliability | Use Case |
|-----------|-----------|-------------|----------|
| GitHub code search | [Yes/No] | [on-demand/warm-up/intermittent] | [consumers of changed interfaces; disposition-boundary checks] |
| Enterprise / codebase search | [Yes/No] | | |
| Cross-repo reference tracking | [Yes/No] | | |
| Diagram rendering (Mermaid etc.) | [Yes/No] | | [Step 02 landing-sequence / cohort visuals; text fallback acceptable] |

## §5 — Skills, Custom AIs, Specialized Agents

| Capability | Active? | Description |
|-----------|---------|-------------|
| AI-Centric Playbook Skill | [Yes/No] | |
| Project-level instructions | [Yes/No] | |
| Specialized agents | [Yes/No] | [delegation for parallel module pipelines] |
| Other Skills loaded | [Yes/No] | |
| **Step 07 review configuration (separate)** | [Yes/No — GAP] | [model/version + access route; how module output is presented without the generating context; basis for the Step 07 §1 independence attestation] |

## §6 — Upstream Artifact Access

| Artifact | Loaded? | Access Path |
|---------|--------|-------------|
| Phase 4 Architecture Blueprint Bundle | [Yes/No] | |
| Phase 4 Module Change Specifications (per NEW/CHANGED module) | [Yes/No] | |
| Phase 4 Formal Interface Contracts | [Yes/No] | |
| Phase 3 Design Specification Bundle (§2 cohorts, §3 instruments) | [Yes/No] | |
| Phase 2 Improvement Plan | [Yes/No] | |
| Phase 1 Current-State Information Report (measured baselines) | [Yes/No] | |

## §7 — Mid-Phase Amendments

*Append-only. When a capability shifts during the Phase 5 run, add a
dated entry below. Do not edit prior entries.*

| Date | Step | Capability | Change | Impact |
|------|------|-----------|--------|--------|
| | | | | |

*Example entry (illustrating the "worked earlier, failed later"
pattern inherited from Phase 3 v1.1, applied to this phase's heaviest
dependency):*

| [date] | Step 05 (M-03 loop) | AI-run test execution | Ran directly through M-01 and M-02; runner began timing out on the full suite mid-M-03 | Full-suite regression runs shifted to practitioner-run with pasted results for remaining M-03 tasks; per-file runs still AI-run; loop cadence noted in the M-03 Implementation Report §5 effort actuals; §8 friction entry updated; implementation write mode unchanged (direct write) |

## §8 — Known Friction Points

| Capability | Friction | Workaround |
|-----------|---------|-----------|
| | | |

## §9 — Code-Access Mode Rationale

[1–3 sentences explaining the evidence-mode and write-mode
selections, what they imply for Step 05 loop cadence and the evidence
basis of the Implementation Reports, and what would trigger a mode
change during the run. If Patch-mediated, state the cadence cost. If
BLOCKED, state prominently that Stage 2 cannot begin — Steps 01–03
may proceed while access is established — and name the owner.]

---

## Version

v1.0 (initial Phase 5 capability inventory; living thereafter)
```

---

## Evaluation Checklist

Before this artifact is accepted as complete, verify:

- [ ] All nine sections (§1–§9) are populated; sections with no
      relevant capabilities are marked "None applicable" rather than
      omitted
- [ ] Both modes are selected and announced in the metadata: the
      evidence mode and the implementation write mode (Direct write
      access / Patch-mediated / BLOCKED) — the Step 05 gate applied,
      not softened: an Interview-only Phase 5 is not recorded as a
      valid posture, and a BLOCKED write mode is prominently flagged
      in the metadata and §9 with Stage 2 named as blocked
- [ ] If the write mode is Patch-mediated, §1 records the channel
      concretely: how diffs are applied, how test results return,
      whether partial-suite runs are possible, and the expected
      round-trip time
- [ ] §2 records how the regression suite is invoked, who runs the
      tests (AI-run preferred / practitioner-run), and whether
      coverage reporting is available — with reliability postures for
      runners and scanners
- [ ] Security/lint/audit rows in §2 inventory the *project's
      existing* tooling, with gaps noted rather than replacements
      proposed
- [ ] The Step 07 separate review configuration is inventoried in §5
      by name (model/config + independence mechanics), or its absence
      is recorded as a named gap to resolve before any module reaches
      Step 07
- [ ] Upstream artifact access (§6) is explicit for all rows —
      Blueprint Bundle, change specifications, formal contracts,
      Phase 3 Bundle, Phase 2 Plan, Phase 1 Report (which are loaded,
      which are accessible-on-demand, which would require paste)
- [ ] Every capability listed as available in §4 carries a
      reliability posture (usable-on-demand / needs-warm-up /
      intermittent)
- [ ] §7 starts empty (or with prior amendments from a previous
      Phase 5 session if resuming) — amendments are added during the
      run, not pre-populated
- [ ] Known friction points (§8) are captured for any capability
      flagged as flaky/rate-limited/expensive, including any "worked
      earlier, failed later" history
- [ ] The document is version-stamped v1.0 (or higher if resuming a
      previous Phase 5 session)
- [ ] No code has been generated and no repository state has been
      modified — no edits, commits, or state-changing test runs, no
      project source code in the document, and no secrets, credentials,
      or tokens recorded; generation starts at Step 05 after
      Steps 01–04
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)

---

*Part of the Phase 5 (Existing Projects) Implementation Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `implementation.existing-project.instructions.md`*
*Next step: `step-01-phase-4-input-validation.prompt.md`*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Phase 5 Building Block Discovery prompt, structured as the Phase 5 sibling of the Phase 4 existing-track step-00: the same nine-section Toolset Augmentation Document, living-document §7 amendment discipline, reliability postures (on-demand/warm-up/intermittent), and the Phase 3 v1.1 inheritances attributed in place (present-vs-consistently-usable, project-knowledge-vs-library-lookup different gaps, solo-optional cross-repo rows). Phase 5 flavoring reflects the heaviest tooling dependency in the track: the hard Step 05 code-access gate from the instructions file (Implementation cannot run Interview-only — direct write access or patch-mediated mode required, with patch-mediated mechanics inventoried concretely: diff application, test-result return, round-trip cadence; a Neither posture is BLOCKED for Stage 2). New inventory categories: test execution and quality tooling (§2 — runner access, regression suite invocation, coverage, existing security/lint/audit scanners preferred, CI status visibility), version control with semantic-commit capability, and the separate Step 07 AI-vs-AI review configuration (§5), inventoried at step-00 so the Step 07 §1 independence attestation has a basis. §6 widened to the four upstream artifact sets (Phase 4 Blueprint Bundle, change specifications + formal contracts, Phase 3 Bundle §2 cohorts and §3 instruments, Phase 2 Improvement Plan, Phase 1 measured baselines). No code is generated at Step 00 — generation starts at Step 05 after Steps 01–04. |
