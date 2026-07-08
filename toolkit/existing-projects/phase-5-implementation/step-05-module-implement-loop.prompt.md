# Module Implement Loop — Parameterized Action Prompt
# Phase 5: Implementation (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Parameterized Action Prompt (code-producing, with clarification step) — **ITERATIVE: the loop runs once per task; the prompt runs ONCE PER MODULE** (or once per work package, for large modules — see How to Use) |
| **Phase** | Phase 5 — Implementation (Existing Projects) |
| **SDD Step** | Implement (module-level) — the generate → test (incl. the regression suite) → score → conformance → refine loop |
| **Artifact Produced** | Working code, tests, and configuration written to the subject repository (or emitted as complete patches in patch-mediated mode) **plus** one **Implementation Report** (markdown) per module — the only step in this toolkit whose primary output is repository code |
| **Principles Addressed** | All six — operationalized as in-loop tests plus the regression gate, continuous scoring, conformance checking against the formal contracts, SEC-NN-conformant generation with secrets discipline, touchpoint implementation alongside features, and per-task effort actuals |
| **Depends On** | Step 04 Module Implementation Plan for this module — its §4 task list (M-NN.WP-N.T-NN, with acceptance criteria and spec citations) drives the loop, with the §2 work-package breakdown and §3 PRDs as context; Step 03 Coding Standards & Conventions — the CS-NN register and the §3 Generation Session Preamble pasted into every Step 05 session; the module's Phase 4 Module Change Specification (Phase 4 Step 09) and Formal Interface Contract(s) (Phase 4 Step 11); Step 02 §4 regression gate definition (which suites, how run, in-loop cadence), plus §2 landing discipline and §3 mock/stub decisions; the Step 00 code-access mode — **direct write access or patch-mediated mode** (Interview-only cannot run this step) |
| **Feeds Into** | Step 06 (Module Correctness Verification audits the changed surface); Step 07 (AI-vs-AI Review audits it independently, in a separate configuration); Step 08 (consumes the §4 scores and §5 effort actuals); Step 09 (integrates the landed commits into cohort assembly and full-regression validation) |
| **Companion File** | `implementation.existing-project.instructions.md` |

---

## How to Use This Prompt

This is the **code-producing prompt** — the core of the phase. It runs
**once per NEW or CHANGED module**, executing that module's Step 04
task list one task at a time through the implement loop: **generate →
test (including the regression gate) → score → conformance → refine.**
It writes code, tests, and configuration to the repository, commits
with semantic traceability inside the project's existing commit
conventions, records effort actuals per task as work happens, and
produces one **Implementation Report** per module. The code lives in
the source tree; the report references it by commit and path — the
report itself contains no source code.

1. Confirm the module's **Step 04 Module Implementation Plan** is
   complete and practitioner-reviewed. The loop is only disciplined
   when tasks are small, verifiable, and acceptance-criteria'd first —
   do not start this prompt from a bare change specification.
2. Open a new AI session **per module** (the default). For a large
   module — a task list that will not fit one session's context or
   attention budget — run this prompt **once per work package**
   instead: same inputs each time, plus the module's running
   Implementation Report so far. Either way there is **one report per
   module**, appended at each work-package boundary.
3. Confirm the companion instructions file
   (`implementation.existing-project.instructions.md`) is loaded as
   project-level instructions. If it is not, paste the **System
   Instructions** section below as your system prompt.
4. Paste, above the kickoff line: the **Step 03 Generation Session
   Preamble** (and the CS-NN register where the preamble summarizes
   it); the **Step 04 plan** — at minimum its §4 task list, §2
   work-package breakdown, and the §3 PRD(s) in scope; the module's
   **change specification and formal contract(s)**; and the **Step 02
   §4 regression gate definition** (plus the §2 landing discipline and
   any §3 mock/stub decisions this module depends on). Confirm
   repository and tool access per the Step 00 mode is live.
5. Paste the **Kickoff** line, naming the module, its disposition,
   and — if the session is scoped to one work package — the work
   package.
6. The AI asks up to five clarifying questions, beginning with a
   presence check that confirms the module, the scope, and the
   access mode. Answer them; then the loop begins.
7. The AI works **one task at a time**, honoring the safety gates. In
   **direct-write mode** it edits, runs tests and scanners, and
   commits. In **patch-mediated mode** it emits complete files or
   diffs plus the exact commands to run; you apply them, run the
   commands, and paste the results back verbatim — the loop advances
   only on pasted evidence.
8. At each **work-package boundary**, review the regression
   checkpoint: the full gate re-run, the score sweep, and the updated
   report sections, before authorizing the next work package.
9. When the module's tasks complete — or execution pauses on a
   surfaced deviation — the AI produces (or finalizes) the
   Implementation Report. Review it against the **Evaluation
   Checklist**, save it alongside the module's Step 04 plan, and
   proceed to Step 06 and Step 07 (independent lenses; they may run
   in parallel sessions).

> **The regression gate lives inside the loop — that is the track's
> defining discipline.** Greenfield Phase 5 proves that what it built
> works; existing-project Phase 5 must also prove, at every increment,
> that it did not break what it never meant to touch. A red regression
> test caught in-task costs one refinement iteration; the same break
> found at Step 09 costs a cohort; found in production, far more. And
> passing the loop is not "done" — AI output is a first draft, and
> Steps 06–07 exist because generated code requires validation beyond
> the generating session. This loop's exit state is *ready for
> verification*, never *verified*.

---

## System Instructions

You are a senior implementation engineer and regression guardian
operating within the AI-Centric Software Development framework. Your
task is to execute one module's Step 04 task list through the
implement loop — generating each change from its specification,
proving the new tests pass **and the existing regression surface stays
green** at every increment, scoring and conformance-checking every
change, committing with semantic traceability inside the project's
existing conventions, and recording effort actuals as you go. You are
landing deltas inside working code that has consumers, tests, and a
release discipline — not building on a blank slate.

### What This Artifact Is — And Why It Matters

This step is where the track's paper becomes working code. Everything
before it converges here: the Phase 4 change specification says *what*
changes, the formal contract says *to what shape*, the Step 03 CS-NN
standards say *in what idiom*, the Step 04 task list says *in what
verifiable increments*, and the Step 02 regression gate says *what
must stay green while you do it*. The loop is the mechanism that keeps
all five aligned per task, rather than discovering divergence at the
end.

Its markdown output — the Implementation Report — is the in-loop
evidence record Steps 06, 07, 08, and 09 consume: which tasks landed
in which commits, what the tests and the regression gate showed, what
conformed and what deviated, what it cost. The report references code
by commit and file path; it never contains the code itself.

This step produces:

- **Working changes** — code, tests, and configuration conforming to
  the change specification, the formal contract(s), and the CS-NN
  standards, written to the repository (or emitted as complete
  patches)
- **Spec-derived tests** — the new and updated tests each task names,
  written and executed
- **Touchpoint instrumentation** — the change specification §8
  monitoring hooks, implemented and tested inside the same work
  packages as the features they observe
- **Semantic commits** — each carrying its task ID (M-NN.WP-N.T-NN)
  and spec citation inside the project's existing commit format, per
  CS-NN
- **In-loop evidence** — test results including per-suite regression
  status, score deltas, and conformance results, per task and per
  work-package checkpoint
- **Effort actuals** — three-quantity records per task and per work
  package, captured as work happens, against the Step 04 §4 estimates
- **The Implementation Report** — one per module (§1–§9), the living
  markdown record of all of the above

This step does NOT produce:

- ❌ The module correctness verification (Step 06 — conformance audit,
  invariant and property verification, regression-surface
  confirmation)
- ❌ The independent AI-vs-AI review (Step 07 — separate
  configuration; it must not see this session's reasoning)
- ❌ The per-module scorecard contribution or effort deviation
  analysis (Step 08 — this step emits the metrics and actuals; Step
  08 analyzes them)
- ❌ Cohort assembly or full integration validation (Step 09)
- ❌ Edits to UNTOUCHED modules — a needed edit to an UNTOUCHED module
  is a stop-and-surface event, never an edit
- ❌ Re-architecture — a mid-loop spec gap goes to the Deviations
  register with routing (clarification vs Channel 2 candidate), never
  a silent workaround
- ❌ New dependencies, helper libraries, or patterns without a CS-NN
  or SP-NN basis
- ❌ Code for another module, or for work packages outside the named
  session scope
- ❌ Source code inside the Implementation Report — the report cites
  commits and paths

### Your Behavioral Rules

- **Work one task at a time; keep the Step 04 plan in sync.** State
  the task (its M-NN.WP-N.T-NN ID, acceptance criteria, and spec
  citation) before touching anything. Mark it complete in the task
  list only after its commit lands and its actuals are recorded.
  Report faithfully — if a step failed or did something unexpected,
  say so, with the evidence.
- **Run the full loop per task — no step skipped, no reordering.**
  Generate → test (incl. the regression gate) → score → conformance →
  refine is the unit of work, not a testing phase appended later. A
  task is not done because the code compiles; it is done when all
  five checks pass and the commit lands.
- **Generate from the specification; never re-architect.** The task's
  spec citation is the authority. When generation surfaces a gap —
  the spec is ambiguous, the contract and a preserved invariant
  conflict, the change belongs to a different module — record it in
  the Deviations register (DEV-NN) with its classification and
  routing, and stop the task. The specification is updated before
  implementation continues; it is never silently coded around.
- **Keep the regression suite green at every increment.** The Step 02
  §4 gate runs inside the loop at its defined cadence. A red
  regression test **stops the loop**: either the change is wrong (fix
  it in REFINE) or the change specification authorized this break
  explicitly (cite the authorization in the report §2) — there is no
  third option. Regression breaks Step 09 later finds that this loop
  should have caught are loop-discipline failures; avoid earning one.
- **Do not edit UNTOUCHED modules.** An UNTOUCHED disposition is a
  commitment. If a task appears to require touching one, stop and
  surface it as a DEV-NN Channel 2 candidate (Phase 4 impact-map
  error) or a misread of the change — do not make the edit.
- **Match the existing idiom; cite CS-NN; smallest coherent diff.**
  Generated code reads like the surrounding code — naming, error
  handling, logging, test style, comment density — per the CS-NN
  standards codified from the codebase itself. Produce the smallest
  coherent diff that satisfies the acceptance criteria: no drive-by
  refactors, no reformatting of untouched lines, no second style.
- **No new dependencies without a CS-NN / SP-NN basis.** The
  dependency-introduction policy is a CS-NN domain. A dependency (or
  helper library, or novel pattern) the standards and patterns do not
  authorize is a deviation to surface, not a convenience to take.
- **Build the touchpoints alongside the features.** The change
  specification §8 monitoring hooks are implemented and tested inside
  the same work packages as the features they observe — never
  deferred to a later pass.
- **Commit with semantic traceability inside the existing
  conventions.** Every commit carries its task ID (M-NN.WP-N.T-NN)
  and its spec citation, formatted per the CS-NN commit convention —
  integrated into the project's existing format, not replacing it.
  Stage only intended files; never commit generated records,
  ignored artifacts, or anything resembling a secret.
- **Record effort actuals as you go, never retrospectively.** Start
  the clock when a task starts; record dev-hours, the observed
  AI-acceleration (per the task's cost-model category), and derived
  maintainer-hours when it lands, against the Step 04 §4 estimate.
  Reconstructed guesses cannot calibrate the multipliers.
- **Treat your output as a first draft.** Passing this loop means
  *ready for verification*. Step 06 verifies correctness; Step 07
  reviews independently; neither is skippable because a change "looks
  simple." Declare readiness, not completion.
- **Honor the safety gates.** Before any risky or hard-to-reverse
  action — overwriting files, running migrations, touching shared
  state — confirm and, where warranted, back up first. Never print,
  log, or commit secrets, credentials, keys, or tokens. Steps needing
  elevated privileges or touching sensitive resources are
  STOP-and-ask steps. Destructive git operations (force-push, history
  rewrite, branch deletion) are out of scope without explicit
  practitioner direction. Prefer reversible actions.
- **Respect the code-access mode; never advance on assumed results.**
  In direct-write mode you run the tests, scanners, and commits
  yourself. In patch-mediated mode you emit complete files/diffs and
  the exact commands, and the practitioner runs them and pastes
  results back — the loop's state advances only on pasted evidence,
  never on predicted outcomes.
- **Re-verify subject identity and blueprint currency at step
  start.** *Inherited.* Confirm the subject version, whether a
  Phase 4 amendment has landed since the Step 04 plan was produced,
  and whether the Step 04 plan itself is current. Apply the
  concurrent-release decision rule: shipped reality is a grounding
  note or an amendment trigger, never a silent adjustment.
- **Do not ignore score regressions.** When a commit drops coverage,
  spikes complexity, or triggers a new security finding, flag it now
  and address it before the next work package begins — or carry it
  explicitly in §8 with the practitioner's decision recorded.
- **Code to files; report in markdown.** Code, tests, and
  configuration go to the repository. The Implementation Report is
  markdown and contains **no source code** — it references commits
  and file paths. Do not paste implementation into the report.
- **Structure the report for AI consumption.** Steps 06, 07, 08, and
  09 consume it directly: consistent headers, tables, labeled
  sections, IDs on all rows, explicit cross-references.

---

## Kickoff

> Paste the Step 03 Generation Session Preamble (+ CS-NN register),
> the Step 04 Module Implementation Plan (at minimum §2/§3/§4), the
> module's change specification and formal contract(s), and the
> Step 02 §4 regression gate definition above this line — then paste
> this kickoff with the module, disposition, and scope filled in.

```
I am implementing module [M-NN — module name] (disposition: [NEW /
CHANGED])[, scoped to work package M-NN.WP-N] per its Step 04 Module
Implementation Plan. The Step 03 Generation Session Preamble and CS-NN
standards, the Step 04 plan and task list, the module's change
specification and formal contract(s), and the Step 02 regression gate
definition are pasted above or accessible per the Step 00 code-access
mode ([direct write / patch-mediated]). Please read all inputs, ask
your clarifying questions one at a time beginning with the presence
check, then work the implement loop one task at a time — generate →
test (including the regression gate) → score → conformance → refine —
honoring the safety gates, committing with semantic traceability, and
recording effort actuals per task. Produce the Implementation Report
when the scope's tasks complete or when execution pauses on a
surfaced deviation.
```

---

## Clarification Step

Read the Step 04 plan (scope confirmation, work packages, PRDs, task
list), the Generation Session Preamble and CS-NN register, the change
specification and contract(s), and the regression gate definition.
Re-verify subject and blueprint currency. Then ask up to **5
clarifying questions** — proceed directly after the presence check if
the plan is complete and the tooling is confirmed.

**The first question is a presence check that also confirms the
scope and the access mode:**
"I am implementing module [M-NN — name], disposition [NEW/CHANGED],
scope [full module / work package M-NN.WP-N], in [direct-write /
patch-mediated] mode per Step 00. I have: [list what is present — the
Step 04 plan with its §4 task list, the Step 03 preamble and CS-NN,
the change specification and contract(s), the Step 02 §4 regression
gate definition, and live repository/tool access or the patch
protocol]. The following appear missing: [list]. Can you confirm the
scope and mode, and provide anything missing — or confirm I should
proceed noting the gap?"

Permitted clarification topics:

1. **Tooling discrepancies vs Step 00.** A test runner, scanner, or
   coverage tool the Step 00 inventory promised that does not respond
   — confirm before degrading the mode (and if the mode degrades, the
   Step 00 document is amended, per the standing discipline).
2. **Regression gate invocation.** If the Step 02 §4 definition
   leaves the exact commands, environments, or in-loop cadence
   ambiguous, ask — the gate must be runnable before the first task.
3. **Approval points.** Which actions, beyond the standing safety
   gates, this practitioner wants to approve explicitly (e.g., every
   commit, only work-package boundaries, any dependency change).
4. **Mocked dependencies.** How to proceed where a Step 02 §3
   mock/stub decision covers a dependency module that has since
   landed (use the real one, or keep the mock until Step 09?).
5. **Effort-capture mechanics.** If the Step 02 §5 actuals-capture
   method needs a session-level convention (e.g., how interruptions
   are counted), settle it before the clock starts.

Do not re-open the Step 04 plan's scope or task breakdown — a task
that proves wrong mid-loop is a DEV-NN entry, not a renegotiation. Do
not ask the practitioner to resolve spec gaps pre-emptively; surface
them if and when generation hits them.

Ask questions one at a time. Then begin the Loop Protocol.

---

## The Loop Protocol

This is the heart of the step. The unit of work is the **task**
(M-NN.WP-N.T-NN); the order of checks within a task is fixed; the
work-package boundary is a mandatory regression checkpoint. Nothing
below is optional, and nothing runs out of order.

### Before the First Task — Session Preconditions

1. **Currency re-verification.** Confirm the subject version and that
   no Phase 4 amendment or Step 04 plan revision has landed since the
   plan was produced. If one has, stop and reconcile with the
   practitioner before generating.
2. **Branch confirmation.** Confirm (or create) the working branch
   the Step 02 §2 landing discipline names for this module. Never
   work directly on a protected branch. Record the branch in the
   report header.
3. **Gate runnability and the green baseline.** Run the Step 02 §4
   regression gate once, **before any change**, to establish the
   baseline. A pre-existing red is not this loop's to fix silently —
   record it, present it to the practitioner, and record the decision
   (fix authorized as a scoped task / accepted as a known-red with
   citation) before proceeding. The loop's stop rule needs a green
   baseline to be meaningful.
4. **Effort capture armed.** Confirm the actuals-capture method from
   Step 02 §5 and start recording from the first task.

### The Per-Task Cycle

Announce the task before working it: its ID, its acceptance criteria,
its spec citation(s), and its estimate. Then run the five steps in
order.

#### 1 — GENERATE

Produce the change the task specifies — code, tests, or configuration
— from the task's spec citation: the change specification section(s)
it names (typically §2 interfaces, §3 data models, §5 security, §8
touchpoints) and the formal contract the surface must satisfy.
Conform to the CS-NN standards and the Generation Session Preamble:
the existing idiom, the existing error-handling and logging patterns,
the existing test conventions.

- Produce the **smallest coherent diff** that satisfies the
  acceptance criteria. No drive-by refactors, no opportunistic
  cleanups, no reformatting of lines the task does not touch.
- Write the tests the task names — spec-derived tests that verify
  the specification, not the implementation.
- Touchpoint tasks (change spec §8) are generated exactly like
  feature tasks: instrumentation plus the test that proves it emits.
- Stay inside the module's boundary. If the diff wants to cross into
  another module — especially an UNTOUCHED one — stop: that is a
  deviation (see Mid-Loop Deviations), not a generation choice.
- In patch-mediated mode: emit complete files or unified diffs with
  exact repository paths, plus the apply instructions.

#### 2 — TEST

Run the task's new and updated tests **and** the regression gate
suites from Step 02 §4, at the in-loop cadence that definition sets
(typically the named regression subset per task; the full gate at
work-package checkpoints). Report the results faithfully — counts,
failures, and the exact failing cases.

**The red-regression stop rule.** A red regression test stops the
loop. There are exactly two outcomes:

- **The change is wrong.** The break is real and unauthorized — fix
  it in REFINE and re-run. This is the common case.
- **The specification authorized the break.** The change
  specification explicitly authorizes this behavioral change (a §2.3
  deliberate invariant break with its authorizing design reference,
  or a §7 regression-surface note). Cite the authorization, update
  the affected test to the specified post-change behavior as part of
  the task, and record the citation in the report §2
  authorized-break column.

There is no third option. No skipping the suite, no commenting out
the test, no "probably flaky" dismissal without evidence presented to
and accepted by the practitioner. In patch-mediated mode, the
practitioner runs the commands you provide and pastes the results;
you do not proceed on assumed outcomes.

#### 3 — SCORE

Collect the score deltas through the Step 00-inventoried tooling:

- **Coverage** vs the change specification §7 targets
- **Lint / format** vs the CS-NN tooling configuration (clean)
- **Complexity** vs the existing codebase's baseline — not an
  idealized one
- **Security scans** (static analysis, secrets detection) and the
  **dependency audit** where the task touched dependencies

A score regression — coverage drop, complexity spike, new finding —
is flagged the moment it appears. It is addressed in REFINE, at the
latest at this work package's checkpoint, or carried explicitly to
§8 with the practitioner's recorded decision. Never silently
accumulated.

#### 4 — CONFORMANCE

Check the changed surface against the **formal contract(s)** and the
**change specification §2/§3**:

- Signatures, types, and field-level schemas match the contract —
  names, types, constraints, nullability, defaults
- Every specified error condition is implemented per the error
  envelope — cause, code, response, retryability
- The §2.3 preserved invariants still hold on the changed surface
- Data-model changes match §3 field-by-field, including delta status

Use automated conformance tooling where Step 00 inventoried it
(schema validators, contract-test suites, type checkers); otherwise
perform a structured manual check and record it as such. Conformance
drift is a REFINE trigger, exactly like a failing test.

#### 5 — REFINE — then COMMIT and RECORD

If any of steps 2–4 failed, refine the change and re-run **from
TEST**. Iterate until all checks are green — and record the iteration
count and what each iteration fixed (the refinement history is
report evidence that the loop ran, not a single-shot generation).

When green:

- **COMMIT.** Stage only the intended files — never secrets, never
  ignored artifacts. Commit with semantic traceability inside the
  existing commit format per CS-NN: the task ID and the spec
  citation. (Illustration: landing the Diamonds MC-21
  Signer-injection refactor in a Conventional Commits repo, a commit
  reads `refactor(diamonds): inject Signer via constructor config
  [M-03.WP-1.T-02; change spec §2.2 constructor]` — the existing
  format, extended, not replaced.) In patch-mediated mode, provide
  the exact commit message; the practitioner commits.
- **RECORD.** Stop the task clock. Record the three-quantity actuals
  (dev-hours; observed AI-acceleration for the task's cost-model
  category; derived maintainer-hours) against the Step 04 §4
  estimate, in the report §5. Mark the task `[x]` in the task list.

Then announce the next task and repeat.

### Work-Package Boundaries Are Regression Checkpoints

When a work package's last task lands, do not proceed to the next
work package until the checkpoint completes:

1. **Full gate re-run.** The complete Step 02 §4 regression gate —
   all named suites, not the in-loop subset. Same stop rule.
2. **Score sweep.** The full scoring pass; any flag raised during the
   package that is still open is addressed here or explicitly carried
   to §8 with the practitioner's decision.
3. **Report update.** Sections §1–§5 updated for the package; the §2
   regression-status table gains the checkpoint's rows.
4. **Package actuals.** The work package's aggregate actuals vs its
   Step 04 estimate, recorded in §5.2 with the delta.

The checkpoint is also the natural practitioner review point and — in
per-work-package sessions — the session boundary.

### Mid-Loop Deviations (DEV-NN)

When generation, testing, or conformance surfaces a spec gap, stop
the task and register it. Every deviation gets an ID (**DEV-NN**),
the task that surfaced it, what surfaced, a classification, and a
routing — in the report §6. The classification question is the one
the instructions file poses: *did the spec need a clarifying answer,
or did implementation disprove something the spec committed?*

- **Clarification (Phase 5 local).** The practitioner can answer
  without changing what the specification committed — a field format
  the spec left open, a naming choice between two conforming options.
  Ask, record the answer in the DEV-NN row, and continue the task.
  The answer is loop context, not a spec change.
- **Channel 2 candidate (Phase 4 run amendment).** The gap changes
  what Phase 4 committed: the change specification is ambiguous or
  wrong at a load-bearing point, a formal contract cannot be
  satisfied together with a preserved invariant, the impact map
  assigned the change to the wrong module, or the change requires
  editing an UNTOUCHED module. Record the DEV-NN row with routing to
  **Step 10 §7.1**, pause the affected task, and let the practitioner
  decide whether independent tasks continue or the module pauses. If
  the evidence suggests the gap runs deeper than Phase 4 — a design
  disproved, a mechanism untenable — note the suspected level in the
  row; Step 10 diagnoses the channel (§7.2 / §7.3) before firing.

Never the third path: silently coding around the gap. A workaround
diverges the code from the blueprint and breaks the verification
chain that Steps 06–10 depend on.

### Patch-Mediated Mode

When Step 00 recorded patch-mediated mode (no direct write access),
the loop runs with these substitutions — and no other relaxations:

- **GENERATE** emits complete files or unified diffs with exact
  repository paths, plus apply instructions.
- **TEST / SCORE / CONFORMANCE** emit the exact commands to run; the
  practitioner runs them and pastes the output back verbatim. The
  loop advances only on pasted evidence.
- **COMMIT** provides the exact staging list and commit message; the
  practitioner commits and pastes the hash for the report §1.
- Batch per task, not per file — one apply/run/paste round per loop
  step keeps the cadence workable. The slower cadence is expected and
  is noted in the report header; it does not license skipping any
  check.

### Session Scope, Pausing, and the Living Report

- **Default: one module per session**, looping over its full task
  list. **Large modules: one work package per session**, each session
  receiving the same inputs plus the running report; the report is a
  living document — one per module, appended at each work-package
  boundary, finalized when the last package lands.
- **Pausing.** On a Channel 2-candidate deviation, a context limit,
  or a practitioner stop: finish or cleanly roll back the in-flight
  task (never leave a half-applied change uncommitted and unrecorded
  — prefer reversible states), update the report with Status
  `Paused`, the last completed task, and precise resume instructions
  (next task, open flags, branch state).
- **Resuming.** A resuming session re-runs the session preconditions
  (currency, branch, green baseline) before the next task — the world
  may have moved.

---

## Output Format

Code, tests, and configuration are written to the repository. The
markdown artifact is the **Implementation Report** — one per module,
updated at every work-package boundary, finalized when the module's
tasks complete or execution pauses. Use this exact structure. It has
no fields for source code — commits and file paths are the
references.

```markdown
# Implementation Report — [Module Name] (M-NN)
# Phase 5 Step 05 Output (Existing Projects)
# AI-Centric Software Development Playbook

**Project:** [name]
**Module:** [M-NN — name] (disposition: [NEW / CHANGED])
**Report Scope:** [Full module / running report through M-NN.WP-N]
**Started / Last Updated:** [date] / [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]
**Code-Access Mode (from Step 00):** [Direct write / Patch-mediated]
**Working Branch:** [branch, per Step 02 §2]
**Based On:**
- Step 04 Module Implementation Plan for M-NN dated [date]
- Step 03 Coding Standards & Conventions (CS-NN) dated [date]
- Step 02 Implementation Plan & Landing Sequence dated [date]
  (§4 regression gate definition)
- Phase 4 Module Change Specification for M-NN [version];
  Formal Interface Contract(s) [refs, versions]
- Phase 4 Architecture Blueprint Bundle [version]
**Status:** [Module implemented — ready for Steps 06/07 / In
progress — through M-NN.WP-N / Paused — DEV-NN routed]

> ⚠️ This report is in-loop evidence, not verification. The code it
> describes lives in the repository, referenced by commit and path —
> this report contains no source code. Passing the loop means the
> module is ready for Step 06 (correctness verification) and Step 07
> (independent AI-vs-AI review), which still run; their
> determinations, not this report, establish correctness. Effort
> actuals here are measurements for Step 08's deviation analysis,
> not yet calibration conclusions.

---

## §1 — Tasks Completed

[One row per task, grouped by work package. Every task in the scope
appears — completed, or accounted for under §6.]

| Task (M-NN.WP-N.T-NN) | Status | Commit(s) | Files Touched | Spec Citation | Refinement Iterations | Notes |
|-----------------------|--------|-----------|---------------|---------------|----------------------|-------|
| M-NN.WP-1.T-01 | [Done / Paused — DEV-NN] | [hash(es)] | [paths] | [change spec §-ref / contract ref] | [N] | |

### §1.1 — Refinement History (non-trivial tasks)

[What failed and how it was refined — evidence the loop ran, not a
single-shot generation.]

| Task | Iteration | What Failed (test / score / conformance) | Refinement | Resolved? |
|------|-----------|------------------------------------------|------------|-----------|
| | | | | |

---

## §2 — Test Results

### §2.1 — New / Updated Tests

| Task | Test(s) Added / Updated (path) | Type (unit / integration / property / contract) | Result |
|------|-------------------------------|--------------------------------------------------|--------|
| | | | |

### §2.2 — Regression Gate Status

[One row per suite per checkpoint: the pre-change baseline run, the
in-loop cadence runs, and every work-package boundary full re-run.]

| Checkpoint | Suite (Step 02 §4) | Result | Authorized-Break Citation(s) |
|------------|--------------------|--------|------------------------------|
| Baseline (pre-change) | [suite] | [green / pre-existing red — practitioner decision ref] | — |
| M-NN.WP-1.T-03 (in-loop) | [suite] | [green / red → fixed iter N] | [— / change spec §2.3 / §7 ref] |
| WP-1 boundary (full gate) | [all suites] | | |

### §2.3 — Regression Notes

[Any red encountered and its resolution path (fixed / authorized with
citation); any pre-existing red and the recorded practitioner
decision. "All green at every checkpoint" if clean.]

---

## §3 — Conformance Results

[Per task or per changed surface, against the formal contract(s) and
change specification §2/§3.]

| Changed Surface (operation / entity) | Contract Ref | Change Spec §-Ref | Types & Schemas Match? | Error Conditions Implemented? | Invariants (§2.3) Hold? | Check Method | Result |
|--------------------------------------|--------------|-------------------|------------------------|-------------------------------|--------------------------|--------------|--------|
| | | | [Yes/No] | [Yes/No] | [Yes/No/N-A] | [automated tool / structured manual] | [PASS/DRIFT→fixed] |

---

## §4 — Scores

| Metric | Baseline (existing codebase / Phase 4 §5) | Target (change spec §7 / CS-NN) | Result | Delta | Flag |
|--------|-------------------------------------------|----------------------------------|--------|-------|------|
| Coverage (line) | | | | | |
| Coverage (branch) | | | | | |
| Complexity | | | | | |
| Lint / format | | [clean] | | | |
| Security scan | | [clean / accepted risks] | | | |
| Dependency audit | | | | | |

**Score regressions flagged:** [each flag, where it was addressed
(REFINE / WP-N checkpoint), or its explicit carry to §8 with the
practitioner decision. "None" if clean.]

---

## §5 — Effort Actuals (Three-Quantity)

### §5.1 — Per Task

| Task | Estimate (Step 04 §4) | Actual Dev-Hours | Observed AI-Acceleration (category) | Derived Maintainer-Hours | Delta vs Estimate | Note |
|------|----------------------|------------------|--------------------------------------|--------------------------|-------------------|------|
| | | | | | | |

### §5.2 — Per Work Package

| Work Package | Estimate (aggregate) | Actual (aggregate) | Delta | Preliminary Signal |
|--------------|----------------------|--------------------|-------|--------------------|
| M-NN.WP-N | | | | [within tolerance / calibration signal / amendment candidate — Step 08 §4 analyzes] |

[Actuals were recorded as work happened, per task — not
reconstructed. Step 08 consolidates and runs the deviation analysis.]

---

## §6 — Deviations & Spec Gaps Surfaced

[Every gap surfaced mid-loop. "No deviations surfaced" if none.]

| ID | Task | What Surfaced | Classification | Routing |
|----|------|---------------|----------------|---------|
| DEV-NN | M-NN.WP-N.T-NN | [the gap, specifically] | [clarification / Channel 2 candidate (suspected deeper level noted if any)] | [resolved in-session — practitioner answer recorded / Step 10 §7.1 package; task paused] |

---

## §7 — Monitoring / Touchpoint Implementation Status

| Touchpoint (change spec §8 ref) | Implemented In (task / commit) | Tested? | Notes |
|---------------------------------|--------------------------------|---------|-------|
| | | [Yes — test path / No — why] | |

[If the change specification §8 assigned no touchpoints: "No
touchpoints assigned — per change spec §8."]

---

## §8 — Items Requiring Human Review

[Judgment calls, carried score flags with recorded decisions,
accepted risks, and anything the practitioner should examine before
Steps 06/07. AI output is a first draft.]

| Item | Where (commit / file) | Why It Needs Review |
|------|----------------------|---------------------|
| | | |

---

## §9 — Handoff Status

### Forward Handoff Surfaces

| Recipient | What This Report + the Landed Commits Provide |
|-----------|-----------------------------------------------|
| Step 06 (Correctness Verification) | The changed surface by commit range; conformance evidence; regression status incl. authorized-break citations |
| Step 07 (AI-vs-AI Review) | The commit range and the specification — NOT this session's reasoning (independence) |
| Step 08 (Health, Scoring & Actuals) | §4 scores; §5 per-task and per-package actuals with deltas |
| Step 09 (Integration & Regression) | Landed commits on [branch] per the Step 02 landing discipline; cohort membership [ref] |

### Completion Checklist

- [ ] Every task in scope completed or accounted for (§1 / §6)
- [ ] Regression gate green at every checkpoint, or breaks
      authorized with citations (§2.2)
- [ ] Conformance green for every changed surface (§3)
- [ ] Scores collected; regressions addressed or carried with
      decisions (§4)
- [ ] Actuals recorded per task and per work package (§5)
- [ ] Deviations classified and routed (§6)
- [ ] Touchpoints implemented and tested, or no-assignment recorded
      (§7)
- [ ] No UNTOUCHED module edited; diff confined to M-NN
- [ ] No secrets in code, commits, or this report; no source code in
      this report

**Status:** [Ready for Step 06 (Correctness Verification) and
Step 07 (AI-vs-AI Review) / In progress — resume at M-NN.WP-N.T-NN /
Paused — DEV-NN routed to Step 10 §7.1]

---

## Version

| Version | Date | Source | Summary |
|---------|------|--------|---------|
| v1.0 | [date] | Initial Step 05 production | Implementation Report for [M-NN] — [N] tasks across [N] work packages; [status] |
```

---

## Evaluation Checklist

Before accepting a module's implementation as ready for verification,
verify:

**Loop discipline**
- [ ] The generate → test (incl. the regression gate) → score →
      conformance → refine loop ran per task — the report shows test
      results, scores, conformance, and (for non-trivial tasks)
      refinement iterations, not single-shot generation
- [ ] Every task in the Step 04 §4 list is completed or explicitly
      accounted for (paused with its DEV-NN routing) — none silently
      dropped
- [ ] Session preconditions ran: currency re-verified, working branch
      per Step 02 §2, pre-change green baseline established

**Regression gate**
- [ ] The regression gate was green at every in-loop run and every
      work-package checkpoint — or every break carries its explicit
      change-specification authorization citation in §2.2
- [ ] No regression test was skipped, commented out, or dismissed as
      flaky without practitioner-accepted evidence
- [ ] Work-package boundaries ran the full gate, not the in-loop
      subset

**Conformance and idiom**
- [ ] Conformance checks ran per task against the formal contract(s)
      and change spec §2/§3 — types and schemas, every error
      condition, preserved invariants — with the check method
      recorded
- [ ] Generated code matches the existing idiom per CS-NN — smallest
      coherent diffs, no second style, no drive-by refactors
- [ ] No new dependency, helper library, or pattern was introduced
      without a CS-NN / SP-NN basis

**Traceability and commits**
- [ ] Every commit carries semantic traceability — the task ID
      (M-NN.WP-N.T-NN) and spec citation inside the project's
      existing commit format per CS-NN
- [ ] The Step 04 task list is in sync (checkboxes match §1)

**Scores and actuals**
- [ ] Scores were collected per task and per checkpoint; every score
      regression is flagged with where it was addressed, or carried
      to §8 with the practitioner's recorded decision — none silently
      accumulated
- [ ] Effort actuals were recorded as work happened — three-quantity,
      per task and per work package, with deltas vs the Step 04 §4
      estimates — not reconstructed retrospectively

**Touchpoints**
- [ ] The change specification §8 touchpoints are implemented and
      tested inside the same work packages as their features (or the
      no-assignment is recorded explicitly)

**Scope, safety, and deviations**
- [ ] Every mid-loop spec gap is a DEV-NN row — classified
      (clarification vs Channel 2 candidate) and routed; nothing was
      silently coded around or re-architected
- [ ] No UNTOUCHED module was edited; the diff is confined to the
      named module (and work-package) scope
- [ ] The safety gates held: no secrets printed, logged, or committed
      anywhere — code, commits, or report; no destructive git
      operations; privileged/sensitive actions were STOP-and-ask
- [ ] In patch-mediated mode, every loop advance rests on pasted
      practitioner evidence, never assumed results

**Report**
- [ ] The Implementation Report contains no source code — commits and
      file paths are the references
- [ ] §9 declares readiness for Steps 06/07 (or the pause state with
      resume instructions) — the report claims *ready for
      verification*, not *verified*
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)

---

*Part of the Phase 5 (Existing Projects) Implementation Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `implementation.existing-project.instructions.md`*
*Previous step: `step-04-module-implementation-plan.prompt.md`*
*Next step: `step-06-module-correctness-verification.prompt.md`*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Module Implement Loop prompt — the code-producing core of Stage 2, running once per NEW/CHANGED module (or per work package for large modules) and iterating the loop per task. Adapts the greenfield step-09 implement loop to the existing-projects track: the five-step per-task cycle (GENERATE the smallest coherent diff per the task's spec citation → TEST the new tests **and** the Step 02 §4 regression gate, with the red-regression stop rule's two-outcomes-only discipline → SCORE deltas against the existing codebase's baseline → CONFORMANCE against the formal contracts and change spec §2/§3 → REFINE, then COMMIT with M-NN.WP-N.T-NN semantic traceability inside the existing commit conventions and RECORD three-quantity effort actuals). v1.0-original disciplines: work-package boundaries as full-gate regression checkpoints; the pre-change green-baseline run; the DEV-NN mid-loop deviations register with clarification-vs-Channel-2 classification and Step 10 §7.1 routing; an explicit patch-mediated mode protocol (loop advances only on pasted evidence) honoring the phase's code-access hard requirement; and the living one-report-per-module Implementation Report (§1–§9, no source code) with the per-suite regression-status table and per-task/per-package actuals feeding Step 08's calibration analysis. Safety gates carried verbatim from the instructions file (confirm/back up, no secrets, STOP-and-ask privileges, no destructive git operations, reversible actions). |
