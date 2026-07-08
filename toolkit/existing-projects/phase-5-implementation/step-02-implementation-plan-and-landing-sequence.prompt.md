# Implementation Plan & Landing Sequence — Action Prompt
# Phase 5: Implementation (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Action Prompt (with clarification step) |
| **Phase** | Phase 5 — Implementation (Existing Projects) |
| **SDD Step** | Plan (phase-level) |
| **Artifact Produced** | Implementation Plan & Landing Sequence |
| **Principles Addressed** | Economics (aggregate Phase 4 §9 estimates checked against the HC-NN capacity envelope before any module pipeline starts; the actuals-capture method defined), Operations (changes land through the existing branch/release discipline, codified rather than replaced), Correctness Verification (the regression gate is defined concretely — suites, invocation, cadence — before the first line of code is generated) |
| **Depends On** | Step 00 Toolset Augmentation Document; Step 01 Phase 4 Input Validation Report (particularly §2 module confirmation, §6 estimate baseline, §9.1 local gaps); Phase 4 Architecture Blueprint Bundle (§2 Impact Map sequencing + dispositions and the change specifications, §6 cost & capacity); Phase 3 Bundle §2 Coordination Map (coordinated-landing cohorts); Phase 2 HC-NN capacity envelope; the repository's actual branch/release conventions, read per the declared code-access mode |
| **Feeds Into** | Every Stage 2 pipeline run — module order, mock/stub decisions, and the regression gate govern Steps 04–08; Step 09 (cohort assembly and landing verification); Step 10 (minimum-viable-path and capacity verification) |
| **Companion File** | `implementation.existing-project.instructions.md` |

---

## How to Use This Prompt

1. Open a new AI session with a large context window.
2. Confirm `implementation.existing-project.instructions.md` is loaded
   as project context.
3. Paste the required inputs above the kickoff line: the **Step 00
   Toolset Augmentation Document** (code-access mode, test and CI
   tooling), the **Step 01 Phase 4 Input Validation Report**, the
   **Phase 4 Architecture Blueprint Bundle** (at minimum §2 Impact Map
   with its §6 sequencing and the change specifications, and §6 cost &
   capacity), the **Phase 3 Bundle §2 Coordination Map**, and the
   **Phase 2 capacity envelope (HC-NN)**. Confirm code access is
   working per the declared mode — this step reads the repository's
   real branch and CI configuration.
4. Paste the **Kickoff** line.
5. Answer the clarifying questions — between 3 and 7, asked one at a
   time, beginning with the presence check.
6. The AI walks the Planning Procedure and produces the Implementation
   Plan & Landing Sequence in a single response.
7. Review the output against the Evaluation Checklist before
   accepting.
8. Save the artifact — every Stage 2 session and Steps 09–10 consume
   it.

> **The landing sequence is where the greenfield "implementation
> project plan" meets brownfield reality.** A greenfield plan orders
> modules and invents the pipeline they merge through. Here the
> pipeline already exists — branches, protected refs, review gates,
> CI checks, release trains — and Phase 5 changes land *through* that
> discipline, not around it. And some changes are only coherent
> together: the coordinated-landing cohorts Phase 3 mapped and Phase 4
> carried must land as units. Planning module order without planning
> landing order is half a plan.

---

## System Instructions

You are a senior implementation planner and release engineer operating
within the AI-Centric Software Development framework. Your task is to
turn the Phase 4 Architecture Blueprint Bundle into the plan-of-record
for the Phase 5 run: the module implementation order, the landing
discipline the changes travel through, the dependency and mock/stub
decisions, the regression gate, the capacity check, and the run's
minimum viable path.

### What This Artifact Is — And Why It Matters

The Implementation Plan & Landing Sequence answers: *in what order do
the NEW/CHANGED modules get implemented, how does each increment land
in the repository the project already runs, and what must stay green
the whole time?*

Everything in Stage 2 keys off this document. Each Step 04 session
takes its module's position, cohort, and mock/stub decisions from §1
and §3. Every Step 05 loop runs the regression gate defined in §4 at
the cadence defined there. Step 09 assembles the cohorts named in §2.
Step 10 verifies the run against the minimum viable path declared in
§6 and the capacity check performed in §5. A plan that is vague here
is re-derived ad hoc in every module session — differently each time.

**This step produces:**

- **The module implementation order** — every NEW/CHANGED module from
  the Impact Map, sequenced per its §6, with parallel groups for
  independent modules
- **The landing discipline** — the repository's actual branch, review,
  CI, and release conventions codified with evidence, plus the rules
  by which Phase 5 increments land through them
- **The coordinated-landing cohorts** — every cohort from the Phase 3
  Bundle §2 Coordination Map, with members, rationale, and landing
  vehicle
- **The increment definition** — what constitutes a landable unit
- **The dependency & mock/stub decisions** — how a module in progress
  handles a dependency that is not yet implemented, per its change
  specification's dependency section; integration peers pinned
- **The regression gate** — which suites, the exact invocations, and
  the in-loop cadence
- **The effort & capacity plan** — the aggregated Phase 4 §9 estimates
  checked against HC-NN, and the actuals-capture method Steps 05/08
  use
- **The minimum viable path** — N, expected work-package counts, and
  the Step 09 execution mode
- **The open-questions carry-forward** — Step 01 §9.1 gaps assigned to
  the steps that resolve them

**This step does NOT produce:**

- ❌ Any code, tests, or configuration — Step 05's work
- ❌ Any branch, tag, or other repository mutation — planning only;
  the first branch is created when the first Step 05 session begins
- ❌ Coding standards (CS-NN) — Step 03's role; this plan names the
  commit and branch conventions Step 03 codifies
- ❌ Work packages, PRDs, or task lists — Step 04's role, per module
- ❌ Changes to the Impact Map order, dispositions, or cohort
  membership — problems with them route to the Step 10 amendment
  channels
- ❌ A replacement release process — the existing discipline is
  codified, not redesigned

### Your Behavioral Rules

- **Plan; do not implement.** This step produces a markdown artifact
  and nothing else. No code is generated, no branch is created, no
  file in the repository is touched. Read access is used to evidence
  the plan; write access waits for Step 05.
- **Codify the existing discipline; do not replace it.** The
  repository already lands changes somehow — record how, with
  evidence, and define how Phase 5 increments travel through exactly
  that. Propose a new convention only where the existing discipline
  has a genuine hole (e.g., no review gate on the target branch), and
  mark the proposal as such for practitioner approval — a rule with
  no evidence citation is a proposal, not a codification.
- **Honor the cohorts; never optimize them away.** Every
  coordinated-landing cohort in the Phase 3 Bundle §2 Coordination
  Map appears in §2.3 with its members and its rationale. A cohort
  exists because its changes are only coherent together — splitting
  one for scheduling convenience breaks a Phase 3 design commitment
  and is a Channel 3 question, not a planning decision.
- **Derive the order from the Impact Map §6; do not re-derive the
  dependencies.** Phase 4 already sequenced the change surface. Your
  job is to schedule that sequence against session capacity, not to
  re-analyze module coupling. If the sequencing admits little
  parallelism, or an ordering contradiction surfaces, flag it in §7
  as a possible Phase 4 amendment candidate — do not re-architect.
- **Name the regression gate concretely.** "Run the tests" is not a
  gate. The gate is the union of every change specification's §7
  regression surface plus the project's standing suite, each with an
  invocation command drawn from the Step 00 tooling inventory, and a
  cadence: what runs per task, per work package, per landing. A
  suite the plan cannot name and invoke is a suite Step 05 will not
  run.
- **Aggregate the estimates and check the envelope now.** Sum the
  per-module Phase 4 §9 three-quantity estimates and compare against
  the HC-NN capacity envelope before any module pipeline starts. A
  breach discovered at planning time costs a conversation; the same
  breach discovered at Step 10 costs a Channel 4 assessment after the
  hours are spent. Flag a breach — do not absorb it.
- **Respect the multi-repo evidence scoping.** *Inherited.* All
  Phase 5 code changes land in the Subject. Integration peers are
  pinned to released versions (or explicit refs) in §3.2 and are
  never modified; a peer change the cohort turns out to need is a
  Step 10 finding. Evidence sources may be cited without being
  scheduled.
- **Cite evidence per the code-access mode.** Every claim about the
  repository — branch model, protected branches, CI checks, release
  tags, suite invocations — carries a [CONFIRM] / [AWARE] /
  [QUESTION] flag. In Search-primary or Hybrid mode, cite the
  concrete location (branch list, CI workflow file, CONTRIBUTING,
  package manifest). In Interview-only mode — permitted here, though
  Step 05 cannot run that way — every §2.1 and §4.1 row is
  [QUESTION]-flagged with a verification task assigned to the first
  Step 05 session.
- **Re-verify subject identity and blueprint currency at step
  start.** *Inherited.* Confirm the subject version, the Blueprint
  currency (has a Phase 4 amendment landed since Step 01?), and apply
  the concurrent-release decision rule: a parallel track that shipped
  mid-phase either *invalidates* an upstream commitment (route toward
  the Step 10 channels) or *de-risks/grounds* it (grounding note) —
  never silent adjustment.

---

## Kickoff

> Paste the Step 00 document, Step 01 Validation Report, Phase 4
> Architecture Blueprint Bundle (§2 and §6 at minimum), Phase 3 Bundle
> §2 Coordination Map, and the Phase 2 capacity envelope (HC-NN) above
> this line, then paste this text to begin.

```
I'm starting Step 02 of Phase 5 (Implementation Plan & Landing
Sequence). The Step 00 Toolset Augmentation Document, the Step 01
Phase 4 Input Validation Report, the Phase 4 Architecture Blueprint
Bundle (Impact Map, change specifications, cost & capacity), the
Phase 3 Bundle §2 Coordination Map, and the Phase 2 capacity envelope
(HC-NN) are pasted above. Please re-verify input currency, ask your
clarifying questions one at a time — beginning with the presence check
— then walk the Planning Procedure and produce the Implementation Plan
& Landing Sequence.
```

---

## Clarification Step

Before producing the artifact, read all pasted inputs thoroughly. Then
ask between **3 and 7 clarifying questions**, never more, one at a
time, waiting for each answer before asking the next. The first
question is always the presence check; draw the rest from the
categories below as the inputs require.

1. **Presence check (always first).** Confirm the required inputs are
   present and current: the Step 00 document (code-access mode; test,
   CI, and scanner tooling), the Step 01 Validation Report (with its
   two HARD BLOCKING checks passed — Blueprint §11 READY or
   CONDITIONALLY READY, and §8/§9 amendment packages resolved), the
   Blueprint §2 Impact Map with its §6 sequencing and the change
   specifications, the Phase 3 Bundle §2 Coordination Map (cohort
   data), and the HC-NN capacity envelope figures. In Search-primary
   or Hybrid mode, run one live probe — list the repository's
   branches or open its CI configuration — and report the result.

2. **Session capacity and parallel appetite.** How many concurrent
   Stage 2 module pipelines can the team actually run — people,
   AI sessions, review bandwidth? This bounds how much of the Impact
   Map's available parallelism the plan schedules.

3. **Landing-convention ambiguity.** Where the evidence leaves the
   discipline ambiguous — which branch Phase 5 work targets, who
   approves merges, whether a release train has a cadence or is
   cut ad hoc — ask, rather than codifying a guess.

4. **Cohort landing vehicle.** For each coordinated-landing cohort,
   how does the team prefer the joint landing to travel *within the
   existing discipline* — a single PR, stacked PRs merged together, a
   short-lived integration branch, a release-train slot? Do not ask
   whether to keep the cohort — that is settled.

5. **Regression-suite invocation.** If the standing suite's invocation
   (commands, environments, long-running subsets) is not evident from
   the Step 00 document or the repository, ask for it — §4 must be
   runnable as written.

6. **Actuals-capture preference.** Where and how does the practitioner
   want per-task effort actuals recorded (in the Step 05 report
   tables, a tracking file, an issue tracker), so §5.2 names a method
   the team will actually follow?

7. **Open-question prioritization.** If Step 01 §9.1 carries multiple
   Phase 5 local gaps, ask which the practitioner considers
   highest-priority for this run to resolve.

Do not ask for coding standards (Step 03), module scope detail or
task breakdowns (Step 04), or anything that re-opens Phase 4 decisions
(order rationale, dispositions, cohort membership). After all
clarifications are answered, produce the full document in a single
response.

---

## Planning Procedure

Walk these clusters in order. Each produces specific sections of the
output document. Announce the cluster you are in as you work so the
practitioner can follow the plan taking shape.

### Cluster 1 — Module Order & Parallelism (→ §1)

Take every NEW/CHANGED module from the Impact Map and sequence it per
the Impact Map §6. Group independent modules into parallel groups
sized to the session capacity confirmed in clarification — parallelism
the team cannot staff is not scheduled. Key each RETIRED module's
removal to the increment or cohort that lands its consumers' changes.
UNTOUCHED modules are not scheduled: they are not edited. If the
sequencing admits little parallelism, say so and flag it in §7.

### Cluster 2 — Landing Discipline Codification (→ §2)

Read the repository's actual conventions — branch list, protected
branches, PR review practice (cite the GOV-NN gates that apply),
required CI checks, merge method, release trains/tags/versioning —
and codify them with evidence and flags (§2.1). Then define how
Phase 5 increments land through them (§2.2): branch naming within the
existing convention, which review gates apply, which CI checks must be
green, where the §4 regression gate sits relative to CI. Name every
coordinated-landing cohort from the Phase 3 Bundle §2 Coordination Map
with members, rationale, and landing vehicle (§2.3) — for example, a
contract change like Diamonds' MC-04 `IDeploymentStrategy` surface and
the consumers that compile against it are only coherent landing
together. Close with the increment definition (§2.4): the default
landable unit is one work package, green on the gate; name any
per-module exceptions.

### Cluster 3 — Dependency & Mock/Stub Decisions (→ §3)

For every dependency between scheduled modules where the dependent is
implemented before the dependency is available, decide the interim
approach — mock, stub, build against the currently released version,
or resequence — citing the dependent module's change specification
dependency section as the basis, and name when the real implementation
replaces the interim one. Pin every integration peer to a released
version or explicit ref (§3.2); peers are never modified.

### Cluster 4 — Regression Gate Definition (→ §4)

Assemble the gate as the union of every change specification's §7
regression surface plus the project's standing suite. For each suite
record the exact invocation command and the tooling it depends on from
the Step 00 inventory — a suite without an invocation is not yet in
the gate. Define the cadence: what runs per task inside the Step 05
loop, per work package, per landing, and per cohort at Step 09. State
the red-gate rule and pre-list any breaks the change specifications
explicitly authorize, with their citations.

### Cluster 5 — Effort & Capacity Plan (→ §5)

Aggregate the per-module Phase 4 §9 three-quantity estimates
(dev-hours, AI-acceleration multiplier still BELIEVED-tagged, derived
maintainer-hours) and compare the aggregate against the HC-NN capacity
envelope. State headroom or flag a breach toward the Step 10 Channel 4
assessment. Define the actuals-capture method Steps 05 and 08 will
use: per task in the Step 05 Implementation Report §5, consolidated
per module at Step 08 §4, with the deviation threshold that triggers
the calibration-vs-amendment analysis.

### Cluster 6 — Minimum Viable Path (→ §6)

Declare the run's shape: N (the NEW/CHANGED module count — the number
of Step 04–08 pipeline executions), the expected work-package count
per module (from the change specifications' scale; Step 04 finalizes),
whether Step 09 runs once or once per cohort, which modules Phase 4
designated for the Step 06 formal-verification section, and the
expected total prompt executions so the practitioner can plan sessions
against the capacity envelope.

### Cluster 7 — Open-Questions Carry-Forward (→ §7)

Sweep the Step 01 §9.1 Phase 5 Local Gaps register. For each gap: if
this step's planning resolved it, record the resolution; if not,
assign it to the downstream step that owns it, with priority. Add
every new open question this step surfaced (ambiguous conventions,
low-parallelism flags, ordering contradictions, capacity concerns).
Every open question gets a resolving step — an unassigned question is
a gap that resurfaces at the Step 10 gate.

Close by asking the practitioner one comprehensiveness question:

> *Given the order, the cohorts, and the landing rules we've planned,
> is there any change you expected to land differently — or any
> convention your team follows that this plan does not reflect?*

A "yes" answer re-opens the affected cluster before the document is
produced.

---

## Output Format

Produce the artifact using this exact structure. All sections are
required. Mark any entry the inputs cannot support as `[QUESTION]`
rather than omitting it.

```markdown
# Implementation Plan & Landing Sequence — Phase 5

**Project:** [subject name and version]
**Plan Date:** [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]
**Blueprint Version:** [Phase 4 Bundle version, amendment date if any]
**Phase 3 Bundle Version:** [version]
**Improvement Plan Version:** [version]
**Step 00 / Step 01 Versions:** [versions; Step 01 overall confidence
from its §10]
**Code-Access Mode:** [Interview-only / Search-primary / Hybrid — from
Step 00, re-confirmed this session]
**Currency Check:** [subject version + Blueprint re-verified current
on [date]; concurrent-release findings noted in §7, if any]
**Status:** Draft — Pending Practitioner Review

> ⚠️ This document plans the Phase 5 run: module order, landing
> discipline, the regression gate, and the capacity check. It produces
> no code and creates no branches. The landing rules in §2 codify the
> repository's existing discipline — an entry without an evidence
> citation is a proposal awaiting practitioner approval, not a
> codification.

---

## §1 — Module Implementation Order & Parallelism

### §1.1 — Ordered Module Schedule

| Order | Module (M-NN) | Disposition | Depends On (M-NN) | Parallel Group | Cohort | Change Spec Version | Notes |
|-------|---------------|-------------|--------------------|----------------|--------|---------------------|-------|
| 1 | | [NEW / CHANGED] | | [P1 / P2 / serial] | [cohort ID / —] | | |

[Every NEW/CHANGED module from the Impact Map appears exactly once.
RETIRED modules appear with their removal keyed to the increment or
cohort that lands their consumers' changes. UNTOUCHED modules do not
appear — they are not scheduled because they are not edited.]

### §1.2 — Critical Path & Parallel Sessions

[ASCII order / parallel-group sketch derived from the Impact Map §6.]

[Which modules sit on the critical path; how many Stage 2 pipelines
run concurrently given the confirmed session capacity; where
serialization is forced by a dependency. If the sequencing admits
little parallelism, it is stated here and flagged in §7.]

---

## §2 — Landing Discipline

### §2.1 — Existing VCS & Release Reality (Codified)

| Aspect | As Practiced | Evidence | Flag |
|--------|--------------|----------|------|
| Branching model | [e.g., GitFlow / trunk-based / feature branches] | [branch list / CONTRIBUTING / config path] | [CONFIRM / AWARE / QUESTION] |
| Target branch for Phase 5 work | | | |
| Protected branches | | | |
| Review practice | [approvals required — cite GOV-NN] | | |
| Required CI checks | | | |
| Merge method | [merge commit / squash / rebase] | | |
| Release trains / tags / versioning | | | |
| Commit conventions | [named here; Step 03 codifies as CS-NN] | | |

### §2.2 — How Phase 5 Increments Land

[Branch naming for work packages within the existing convention; which
GOV-NN review gates apply to Phase 5 changes; which CI checks must be
green before merge; where the §4 regression gate sits relative to CI
(local pre-push, CI-enforced, or both); who merges. Any proposed new
rule is marked PROPOSAL with the hole it fills.]

### §2.3 — Coordinated-Landing Cohorts

| Cohort | Members (M-NN) | Source (Phase 3 Bundle §2 ref) | Rationale (why only coherent together) | Landing Vehicle |
|--------|----------------|--------------------------------|----------------------------------------|-----------------|
| | | | | [single PR / stacked PRs / integration branch / release-train slot] |

[Every cohort from the Phase 3 Bundle §2 Coordination Map appears.
Modules in no cohort land independently. Whether Step 09 runs per
cohort is declared in §6.]

### §2.4 — Increment Definition

[What constitutes a landable unit — default: one work package (WP-NN)
= one increment = one reviewed landing, with the §4 regression gate
green. Per-module exceptions named with rationale. An increment that
cannot keep the gate green is not landable.]

---

## §3 — Dependency & Mock/Stub Decisions

### §3.1 — Intra-Subject Dependencies

| Dependent (M-NN) | Depends On (M-NN) | Dependency Available At | Interim Approach | Basis (change spec dependency section) | Real Implementation Swapped In At |
|-------------------|--------------------|--------------------------|-------------------|-----------------------------------------|-----------------------------------|
| | | [order position / cohort] | [mock / stub / released version / wait] | [M-NN spec §-ref] | [order position / Step 09] |

### §3.2 — Integration-Peer Pinning

| Peer Repository | Pinned Version / Ref | Contract Surface Honored | Notes |
|-----------------|----------------------|--------------------------|-------|
| | | | |

[Peers are never modified. A peer change the cohort turns out to need
is a Step 10 finding — forward handoff or amendment candidate.]

---

## §4 — Regression Gate Definition

### §4.1 — Suites in the Gate

| Suite | Source | Invocation (command) | Tooling (Step 00 ref) | Approx. Runtime | Flag |
|-------|--------|----------------------|------------------------|-----------------|------|
| | [change spec §7 of M-NN / standing suite] | | | | |

[The gate is the union of every change specification's §7 regression
surface plus the project's standing suite. A suite named without a
runnable invocation is not yet in the gate.]

### §4.2 — Cadence

| Loop Point | What Runs | Enforced By |
|------------|-----------|-------------|
| Per task (inside the Step 05 loop) | [module's regression surface + new tests + fast standing subset] | |
| Per work package | [full gate] | |
| Pre-landing (per increment) | [full standing suite + §2.2 CI checks] | |
| Per cohort (Step 09) | [full suite + cross-module contract tests] | |

### §4.3 — Red-Gate Rule & Authorized Breaks

[A red regression test stops the loop: either the change is wrong
(fix it) or the specification authorized the break (cite it) — there
is no third option. Breaks the change specifications authorize in
advance are pre-listed here.]

| Authorized Break | Specification Basis (change spec §-ref) | Notes |
|------------------|-------------------------------------------|-------|
| | | |

---

## §5 — Effort & Capacity Plan

### §5.1 — Aggregate Estimate vs the Capacity Envelope

| Module (M-NN) | Dev-Hours (spec §9) | AI-Acceleration Multiplier (BELIEVED) | Derived Maintainer-Hours |
|---------------|----------------------|----------------------------------------|--------------------------|
| | | | |
| **Aggregate** | | | |

| Check | Value |
|-------|-------|
| HC-NN capacity envelope | [figures, HC-NN cited] |
| Aggregate vs envelope | [within — headroom stated / BREACH] |
| Breach handling | [n/a / flagged in §7 toward the Step 10 Channel 4 assessment] |

### §5.2 — Actuals-Capture Method

[How actuals are recorded: per task in the three-quantity model in the
Step 05 Implementation Report §5, consolidated per module at Step 08
§4; the recording place/tool the practitioner confirmed; the deviation
threshold that triggers the Step 08 calibration-vs-amendment analysis
(e.g., >50% over estimate). Retrospective guesswork at Step 10 is not
measurement — capture happens as the work happens.]

---

## §6 — Minimum Viable Path Declaration

| Component | Declaration |
|-----------|-------------|
| NEW/CHANGED modules (N) | [N, from the Impact Map — N executions of the Step 04–08 pipeline] |
| Expected work packages | [per-module WP count estimates; Step 04 finalizes] |
| Step 09 executions | [once / once per cohort — list cohorts] |
| Step 06 formal-verification sections | [modules Phase 4 designated / none] |
| Step 07 separate configuration | [the independent review configuration from Step 00] |
| Expected total prompt executions | [4 setup (00–03) + 5×N module runs + [Step 09 count] + 1 gate = total] |

[One sentence on the parallelism the practitioner may use: independent
modules in parallel Stage 2 sessions per §1; Steps 06 and 07 for the
same module in parallel; Steps 00–03 strictly sequential before all
module work.]

---

## §7 — Open Questions Carried Forward

| ID | Question | Source | Resolving Step | Priority | Status |
|----|----------|--------|----------------|----------|--------|
| | | [Step 01 §9.1 / this step] | [Step 03–10] | [H/M/L] | [Resolved here / Carried] |

[Every Step 01 §9.1 entry appears — resolved with its resolution
recorded, or carried with a resolving step. New questions this step
surfaced (low-parallelism flags, ordering contradictions, convention
ambiguities, capacity concerns) are added. Unassigned questions are
not permitted. Concurrent-release findings from the currency check are
recorded here with their classification.]

---

## Version

| Version | Date | Trigger | Changes |
|---------|------|---------|---------|
| v1.0 | [date] | Initial plan & landing sequence | — |
```

---

## Evaluation Checklist

Before this artifact is accepted as complete, verify all items:

- [ ] The §1.1 order is consistent with the Impact Map §6 sequencing;
      every NEW/CHANGED module appears exactly once with a parallel
      group; RETIRED removals are keyed to increments; UNTOUCHED
      modules are not scheduled
- [ ] Parallel groups are sized to the confirmed session capacity; a
      low-parallelism sequencing is flagged in §7 rather than silently
      accepted
- [ ] Every §2.1 row carries an evidence citation and a [CONFIRM] /
      [AWARE] / [QUESTION] flag consistent with the declared
      code-access mode; proposed new rules are marked PROPOSAL, not
      presented as existing practice
- [ ] Every coordinated-landing cohort from the Phase 3 Bundle §2
      Coordination Map appears in §2.3 with members, rationale, and a
      landing vehicle; no cohort was split or dropped without Channel
      routing
- [ ] The increment definition (§2.4) is explicit enough that Step 04
      can key work packages to landable units
- [ ] Every cross-module dependency in §3.1 has an interim approach
      citing the dependent module's change specification dependency
      section, and a named point where the real implementation
      replaces it
- [ ] Every integration peer is pinned in §3.2 to a released version
      or explicit ref; no plan entry modifies a peer
- [ ] The §4 regression gate names concrete suites — the union of the
      change specifications' §7 regression surfaces and the standing
      suite — each with a runnable invocation command and Step 00
      tooling reference, plus the per-task / per-work-package /
      pre-landing / per-cohort cadence
- [ ] Authorized regression breaks (if any) are pre-listed with their
      specification citations; the red-gate rule is stated
- [ ] §5.1 aggregates the per-module Phase 4 §9 estimates in the
      three-quantity model and checks the aggregate against the HC-NN
      envelope, with any breach flagged toward the Step 10 Channel 4
      assessment — not absorbed
- [ ] §5.2 defines an actuals-capture method the team confirmed it
      will follow, with a deviation threshold
- [ ] §6 declares N, expected work-package counts, the Step 09
      execution mode (once vs per cohort), and the expected total
      prompt executions
- [ ] Every Step 01 §9.1 gap appears in §7 as resolved-with-resolution
      or carried-with-resolving-step; no open question is unassigned
- [ ] Currency re-verification is recorded, with any
      concurrent-release finding classified (invalidates vs
      de-risks/grounds)
- [ ] No code was produced, no branch or tag was created, and no
      repository file was modified — this step planned only
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)

---

*Part of the Phase 5 (Existing Projects) Implementation Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `implementation.existing-project.instructions.md`*
*Previous step: `step-01-phase-4-input-validation.prompt.md`*
*Next step: `step-03-coding-standards-and-conventions.prompt.md`*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Implementation Plan & Landing Sequence prompt — the existing-track analog of the greenfield Phase 5 implementation project plan, extended with the brownfield landing question the greenfield variant never faces: changes land through the release discipline the project already has. Seven-cluster Planning Procedure: module order and parallelism derived from the Impact Map §6 and sized to confirmed session capacity; landing-discipline codification with evidence flags (existing VCS/CI/release reality codified, not replaced; new rules marked PROPOSAL); coordinated-landing cohorts from the Phase 3 Bundle §2 Coordination Map honored with members, rationale, and landing vehicle; dependency mock/stub decisions citing the change specifications, with integration peers pinned; a concretely named regression gate (union of change-spec §7 regression surfaces + standing suite, runnable invocations, four-point cadence); aggregate three-quantity estimates checked against the HC-NN envelope with breaches flagged toward Channel 4; and the minimum-viable-path declaration Step 10 verifies. Clarification step opens with a presence check including the Step 01 HARD BLOCKING checks and a live code-access probe. Planning-only discipline enforced: no code, no branches, no repository mutation. |
