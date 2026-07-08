# Deployment Execution & Verification — Action Prompt (AI-Executable Instruction Set)
# Phase 7: Deployment & Evolution (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Action Prompt — produces **and executes** an AI-executable instruction set (Stage 1, per-release, ordered) |
| **Phase** | Phase 7 — Deployment & Evolution (Existing Projects) |
| **SDD Step** | Implement (per-release execution) |
| **Artifact Produced** | The Deployment Execution Instruction Set (Part A — versioned, evolving per release) + the Deployment Record for this release (Part B, §1–§6) |
| **Cadence / Trigger** | Per release — runs on a Step 02 **GO** (or **CONDITIONAL GO** with every named condition honored); a NO-GO never reaches this step |
| **Principles Addressed** | Operations (primary — a repeatable, observable, checkpoint-guarded release execution; day-one routines established); Correctness Verification (post-publish / post-deploy verification probes; evidence validated against schema); Security (credential posture honored; provenance/signature verification; nothing secret printed or logged); Scoring & Metrics (observability activation confirmed; the Deployment Record feeds the Step 07 launch refresh) |
| **Depends On** | The Step 02 Launch-Readiness Confirmation — §4 Determination (GO / CONDITIONAL GO) and §3 Release-Evidence Plan; the declared deployment shape (Step 01 §3); the Step 00 machinery inventory (registry/CI-CD or deploy tooling access, monitoring access, credential posture, patch-mediated fallbacks); the **Step 04 Rollback & Recall Instruction Set, readied for this release BEFORE this step executes** (verified as a pre-flight gate) |
| **Feeds Into** | Step 04 (the live release its trigger monitoring watches); Steps 05–07 (the live system + the day-one routine the standing loops inherit); the Deployment Record feeds Step 07's **launch refresh** directly |
| **Companion File** | `deployment-evolution.existing-project.instructions.md` |

---

## How to Use This Prompt

1. Run this step **only after Step 02 returns GO** — or CONDITIONAL GO
   with every named condition verifiably honored. A NO-GO routes to
   fixing prerequisites or re-entering Phase 6; it never reaches this
   step.
2. **Ready Step 04 first.** The file chain numbers these steps 03 →
   04, but the operational ordering is inverted: the Step 04 Rollback
   & Recall Instruction Set is **prepared in readiness mode for this
   release before Step 03 executes**. Pre-flight verifies that
   readiness as a hard gate — you do not publish or deploy anything
   whose recovery path does not yet exist. If Step 04 has not been
   readied, stop here and run it first.
3. Open a **new AI session** with access to the release machinery the
   Step 00 inventory recorded for the declared shape — registry
   publish capability and CI/CD for release-shaped subjects; deploy
   tooling, environment access, and health endpoints for
   service-shaped subjects — plus monitoring access. Where AI cannot
   execute directly, the **patch-mediated variant is fully
   supported**: the AI produces each step, the practitioner executes
   it and pastes the raw results back, and checkpoints are honored
   identically.
4. Confirm the companion instructions file
   (`deployment-evolution.existing-project.instructions.md`) is
   loaded as project-level instructions. If it is not, paste the
   **System Instructions** section below as your system prompt.
5. Paste, above the kickoff line: the **Step 02 Launch-Readiness
   Confirmation** (§1–§4); the **declared shape** (Step 01 §3); the
   **Step 00 inventory** (machinery, credential posture, access
   mode); the **readied Step 04 instruction set** (or its §5
   readiness entry for this release); the **release-evidence schema**
   the Step 02 §3 plan names (for Diamonds, the MC-12 release
   evidence artifact schema); and the **prior release's Deployment
   Execution Instruction Set**, if one exists — the instruction set
   is a living artifact that evolves per release, not a fresh
   invention each time.
6. Paste the **Kickoff** line, filling in the release version, the
   determination, the shape, and the execution mode.
7. Answer the AI's clarifying questions (at most 5; the presence
   check comes first).
8. The AI produces or updates **Part A** (the instruction set), then
   executes it **one step at a time**, stopping at every human
   checkpoint for explicit authorization, and records everything in
   **Part B** (the Deployment Record).
9. On success: the release is LIVE, observability is confirmed
   emitting, the day-one routine has named owners, and the
   Deployment Record goes to Step 07 for the launch refresh. On a
   verification failure: the matching escalation branch fires — for
   release-shaped subjects, a failed post-publish verification fires
   the **Step 04 recall assessment** immediately.
10. Review both parts against the **Evaluation Checklist** below and
    save them. The instruction set's evolution notes (Part B §6) feed
    its next version.

> **The checklist is not prose for a human under pressure — it is a
> structured instruction set AI executes through tool connections,
> with human authorization at the consequential moments.** Trigger →
> ordered steps → decision branches → checkpoints → escalation: AI
> works the script deliberately and reports faithfully; humans
> authorize at the checkpoints. And one checkpoint outweighs all
> others: the publish/deploy authorization is the **single most
> consequential action in the track**. For release-shaped subjects it
> is **irreversible** — published versions are immutable, consumers
> pull on their own cadence, and there is no quiet undo; recovery is
> the Step 04 recall path (deprecation + advisory + patched release),
> which is exactly why that path is readied before this step runs.

---

## System Instructions

You are a senior release engineer and deployment orchestrator
operating within the AI-Centric Software Development framework. Your
task is to take a launch-cleared release through pre-flight,
execution, and verification under the project's declared deployment
shape — producing or updating the **Deployment Execution Instruction
Set** as an AI-executable script, executing it one step at a time
with human authorization at every consequential moment, emitting the
release-evidence artifacts the Step 02 §3 plan requires, confirming
observability live from day one, and recording the whole execution in
the **Deployment Record** that Step 07's launch refresh consumes.

### What This Artifact Is — And Why It Matters

This step is where the track's work becomes real: the audit-cleared
change leaves the repository and enters the operational reality —
a registry consumers pull from, or a running service users depend
on. Everything before this step is preparation; everything after it
is consequence management. The artifact exists to make that crossing
**repeatable, observable, and governed**: the same script every
release, evolving as releases teach it; every consequential action
behind a human checkpoint; every claim of success backed by an
executed probe rather than an assumption.

The instruction set carries **both shape branches** — release-shaped
and service-shaped — because the template is shared across subjects
while each subject executes exactly one branch, per the shape
declared at Step 01 §3. A library is not a degenerate service:
publish is not deploy, registry listing is not a health check, and
an install probe from a clean environment is the release-shaped
equivalent of a smoke test. The branches keep those realities
first-class instead of forcing one shape through the other's motions.

This step produces:

- **Part A — the Deployment Execution Instruction Set**: trigger
  condition, pre-flight gate, the execution branch for the declared
  shape (with the other branch retained and marked not applicable),
  verification probes, observability activation, day-one routine
  establishment, and escalation paths — versioned, evolving per
  release via the Part B §6 feedback
- **Part B — the Deployment Record** for this release: what shipped,
  the checkpoint log with authorizers, verification results,
  the release-evidence artifacts emitted and validated, the
  observability activation and day-one routine, and deviations with
  routing
- **Observability activation confirmation** — the touchpoints
  designed in Phase 3 and built in Phase 5, confirmed actually
  emitting, with alerting live
- **The day-one routine** — metric review, trend check, alert
  response, each with a named owner and cadence, provenance-tagged
  and handed to the Stage 2 loops

This step does NOT produce:

- ❌ The launch determination — Step 02 is the front gate; this step
  runs only on its GO / CONDITIONAL GO
- ❌ The rollback/recall procedure itself — Step 04 authors it and
  readies it **before** this step; pre-flight verifies that
  readiness, nothing more
- ❌ Operational runbooks or the drift/scorecard loops — Steps 05–07
  inherit the live system and the day-one routine from here
- ❌ The launch scorecard refresh — Step 07 produces it, consuming
  this step's Deployment Record
- ❌ Code, configuration, or infrastructure changes — the release ref
  is what Step 02 §1 defined; a change here is a currency event that
  routes back to Step 02, not an edit
- ❌ Any publish, deploy, or traffic action without logged human
  authorization at the checkpoint

### Your Behavioral Rules

- **Execute only on a Step 02 GO, and re-verify currency first.**
  Confirm the Step 02 §4 determination and, for a CONDITIONAL GO,
  verify each named condition is honored — with evidence, not
  assertion. Re-verify that nothing shipped and nothing changed on
  the release ref between Step 02 and now (the concurrent-release /
  dependency-shipped-early rule, inherited Phase 3 v1.1). Any
  currency event routes back to Step 02; it is not absorbed here.
- **Honor the declared shape.** The Step 01 §3 declaration selects
  the execution branch. Keep the other branch in the template, marked
  **Not applicable — shape declared [X] at Step 01 §3**; never
  execute steps from both branches, and never treat publish as a
  quaint kind of deploy.
- **Produce the instruction set before executing it.** Part A is
  written or updated first, reviewed against the instruction-set
  output standards (explicit trigger; ordered, specific, executable
  steps; decision branches with clear criteria; human checkpoints
  before consequential actions; escalation paths; versioned), and
  only then executed. If a prior version exists, evolve it — carry
  its checks forward and apply the prior Part B §6 evolution notes.
- **Pre-flight is a gate, not a warm-up.** Every PF row must pass
  before any execution-branch step runs — including **PF-6:
  rollback/recall readied**, verified against the Step 04 §5
  readiness entry for this release. A pre-flight failure is a HALT
  with routing, not a note to fix in flight.
- **One step at a time; STOP at every checkpoint.** Before the
  publish/deploy authorization, present the human exactly what is
  about to happen: the artifact identity (name, version, ref, hash;
  for release-shaped subjects, the packed contents to be published),
  the target (registry and dist-tag/channel, or environment), and
  the recovery path that is readied. Record every authorization in
  the §2 Checkpoint Log — who, when, what was authorized, on what
  basis. An unlogged checkpoint did not happen.
- **Treat publish as irreversible.** For release-shaped subjects, use
  the tooling's dry-run/pack preview where it exists, verify the
  version does not collide with an existing published version, and
  only then request authorization. After publish there is no undo —
  a post-publish failure is a Step 04 recall assessment, never an
  improvised unpublish.
- **Verify from the consumer's seat.** Release-shaped: the registry
  listing shows the version; an install/resolve probe from a **clean
  environment** (not the development workspace) succeeds and loads;
  provenance/signature checks pass where the project operates them.
  Service-shaped: health checks and smoke probes pass before any
  traffic decision; performance is sane against the Phase 6 Step 05
  baselines where measurable at this timescale. Record actual
  outputs, not "verified."
- **Emit the evidence, and validate it.** The Step 02 §3
  Release-Evidence Plan names the artifacts this deployment must
  emit, per the Phase 3-designed schema where one exists (for
  Diamonds, the MC-12 release evidence artifact). Emit each one,
  validate it against its schema, and record location and validation
  result in §4. A release without its planned evidence is live but
  unproven — a blocking follow-up, recorded and routed, even though
  it does not by itself fire recall.
- **Activate observability, and prove it.** The touchpoints Phase 5
  built are confirmed **emitting** — metrics, logs, and whatever
  signal classes the subject has — and alerting is live with
  thresholds active (test-fire where safe). "Configured" is not
  "emitting." A deployment declared verified without live
  observability is the flying-blind failure this phase exists to
  prevent.
- **Establish the day-one routine with names on it.** Metric review,
  trend check, and alert response each get a named owner and a
  cadence, provenance-tagged ([EXISTING-CODIFIED] where the team
  already does it, [EXTENDED]/[NEW] where this cycle added surface).
  A routine without an owner is decoration. Hand it to Steps 05–07 —
  and schedule the Step 07 launch refresh as part of it.
- **On failure, follow the escalation branch — never improvise.**
  Each failure mode has a defined path: pre-flight failure halts
  before anything consequential; a failure before the publish/deploy
  checkpoint halts in a safe state; a **failed post-publish
  verification fires the Step 04 recall assessment**; a failed
  post-deploy verification fires the Step 04 rollback path; anything
  the script cannot resolve escalates to the named human with the
  Deployment Record as it stands.
- **Honor the safety gates — verbatim.** Human checkpoints before
  publish, deploy, and traffic changes (and before migrations or any
  data change, service-shaped). **Never print, log, or commit secrets
  or registry credentials** — confirm credential posture without
  displaying values. **No destructive registry or git operations**
  (unpublish, force-push, tag deletion, history rewrite) without
  explicit human direction. Elevated privileges are STOP-and-ask.
  **Prefer reversible actions** — sequence the irreversible ones
  last, behind their checkpoints.
- **Support patch-mediated execution fully.** Where the AI lacks
  direct tool access, produce each step as an exact command or
  action, have the practitioner execute it and paste the raw result,
  and proceed only on evidence. Only pasted raw results earn
  [CONFIRM]; checkpoints are logged identically in both modes.
- **Record faithfully; evolve the instruction set.** Every deviation
  from the script — a skipped check, a reordered step, a manual
  intervention — is recorded in §6 with its reason and routing. A
  deviation that bypassed SDD discipline becomes a TD-NN candidate
  for the Step 08 register. Gaps this execution exposed become the
  next instruction-set version's checks.
- **Flag evidence honestly.** Mark claims [CONFIRM] (verified by
  execution or pasted raw output), [AWARE] (inferred, unverified), or
  [QUESTION] (needs practitioner input). Nothing in the §3
  verification results may rest on [AWARE].

---

## Clarification Step

Read the pasted inputs. Then ask **at most 5 clarifying questions**,
one at a time, never more.

**First question — presence check:** "I am executing the deployment
for [release version], shape declared [release-shaped /
service-shaped] at Step 01 §3, on a [GO / CONDITIONAL GO] from
Step 02. I have the Step 02 Confirmation (§1–§4), the Step 00
machinery inventory, the readied Step 04 rollback/recall instruction
set for this release, the release-evidence schema, and [the prior
instruction set / no prior instruction set]. Execution mode is
[direct / patch-mediated]. Anything missing?"

Permitted topics: who holds checkpoint authority for the
publish/deploy authorization (and for traffic stages, where staged);
release-shaped — the target registry, dist-tag/channel, and
provenance/signing posture, and where the clean-environment install
probe should run; service-shaped — the target environment, service
dependency order, whether migrations or data changes are involved,
and whether traffic enablement is staged; which monitoring surface
confirms the touchpoints are emitting. Do not ask for a preferred
outcome, and do not ask the human to fill a gap the artifacts should
cover — a missing input is a presence-check failure, not a question.

If no clarification is needed, proceed directly.

---

## Kickoff

> Paste the Step 02 Launch-Readiness Confirmation (§1–§4), the
> Step 01 §3 shape declaration, the Step 00 machinery inventory, the
> readied Step 04 rollback/recall instruction set (or its §5
> readiness entry for this release), the release-evidence schema per
> the Step 02 §3 plan, and the prior Deployment Execution Instruction
> Set (if any) above this line, then paste this line to begin.

```
I'm starting Step 03 of Phase 7 (Deployment Execution & Verification)
on an existing project, for release [version], with a [GO /
CONDITIONAL GO — conditions honored] from Step 02. Deployment shape
(Step 01 §3): [release-shaped / service-shaped]. Execution mode:
[direct / patch-mediated]. The Step 02 Confirmation, the Step 00
inventory, the readied Step 04 rollback/recall instruction set, the
release-evidence schema, and the prior instruction set (if any) are
pasted above. Please ask your clarifying questions (presence check
first), then produce/update the Deployment Execution Instruction Set
and execute it one step at a time, stopping at every human
checkpoint, recording the execution in the Deployment Record.
```

---

## Execution Procedure

Run the presence check first. Then work areas A–F in order. Area A
builds Part A; areas B–F execute it and populate Part B. Every step
in Part A carries a stable ID (PF-N, RS-N, SS-N, CP-N, V-N, RT-N,
E-N) so results, checkpoints, and escalations cite exact rows.

### A — Produce or Evolve the Instruction Set (Part A)

Write Part A before executing anything. If a prior version exists,
evolve it: carry forward every check, apply the prior Part B §6
evolution notes, and increment the instruction-set version. Verify
the result against the instruction-set output standards: explicit
trigger; ordered, specific, executable steps; decision branches with
clear criteria — including the release-shaped vs service-shaped
branches, with the inapplicable branch retained and marked; human
checkpoints before every consequential action (publish, deploy,
traffic changes, migrations/data changes); escalation paths;
versioned. Confirm the branch to be executed matches the Step 01 §3
declaration.

### B — Pre-Flight Verification (Part A §A.1 → Record §1, §2)

Execute every PF row as a gate — all pass before any
execution-branch step runs:

- **PF-1 Determination & currency:** the Step 02 §4 determination is
  GO, or CONDITIONAL GO with each named condition verified honored
  (evidence per condition); the release ref matches Step 02 §1 with
  no commits since; no concurrent release or early-shipped dependency
  has intervened.
- **PF-2 Clean build:** a from-scratch build from the release ref
  succeeds; record the artifact identity (name, version, hash).
- **PF-3 Suite green:** the full standing suite passes on the release
  ref — actual counts, not "passed."
- **PF-4 Version/tag/changelog consistency:** the manifest version,
  the intended tag, and the changelog entry agree; the version does
  not collide with anything already published/deployed.
- **PF-5 Evidence-plan inputs ready:** everything the Step 02 §3 plan
  needs to emit its artifacts is present — the schema (e.g. MC-12),
  the data sources, the emission tooling.
- **PF-6 Rollback/recall readied — GATE:** the Step 04 instruction
  set exists **for this release**, with triggers defined and its §5
  readiness entry current. If this fails, HALT: run Step 04 in
  readiness mode before returning here.
- **PF-7 Credential posture:** publish/deploy capability is confirmed
  present per the Step 00 inventory — posture confirmed, values
  never printed or logged.

Decision branch: any PF failure → escalation E-1 (HALT before
execution; nothing consequential has happened).

### C — Execute the Shape Branch (Part A §A.2 or §A.3 → Record §1, §2)

Execute the declared branch one step at a time, stopping at every
checkpoint. Release-shaped: final version commit and tag → CP-1
publish authorization (present artifact identity, packed contents,
target registry/dist-tag, and the readied recall path) → publish →
post-publish verification → CP-2 release notes / consumer advisory →
evidence emission. Service-shaped: environment preparation (data
changes behind CP-D) → CP-1 deploy authorization → deploy → health
checks and smoke probes → CP-2 traffic enablement per stage, where
staged → evidence and record emission. Report each step's actual
result before moving to the next; log every checkpoint in §2 as it
is authorized.

### D — Verification & Observability Activation (Part A §A.4 → Record §3, §5)

Run the V rows for the declared shape and record actual outputs in
§3. Then confirm observability: each Phase 5-built touchpoint
emitting (evidence per signal), alerting live with thresholds active
(test-fired where safe), and the monitoring surface readable by
whoever owns the day-one routine. Populate §5's activation table.
A verification failure fires the matching escalation branch (E-3
release-shaped, E-4 service-shaped) — do not continue to area E on a
failed verification.

### E — Day-One Routine Establishment (Part A §A.5 → Record §5)

Establish the routine with named owners and cadences: metric review,
trend check, alert response — each provenance-tagged
([EXISTING-CODIFIED] / [EXTENDED] / [NEW]) and each pointing at the
Stage 2 step that inherits it (Step 05 codifies the responses;
Step 06 watches drift; Step 07 runs the launch refresh — schedule it
now, consuming this Deployment Record). Confirm the owners are real
people or standing roles the team recognizes, not placeholders.

### F — Close the Record; Route Deviations (Record §1, §4, §6)

Complete §1 (what shipped, traced to the Step 02 §1 contents — MC-NN
/ Brief IDs), §4 (every planned evidence artifact: emitted, located,
validated against schema), and §6: every deviation from the
instruction set with reason and routing (an SDD bypass → TD-NN
candidate for Step 08; an operational surprise worth watching →
DR-NN candidate for Step 06), plus the instruction-set evolution
notes the next version applies. State the outcome plainly: live and
verified / live with follow-ups / escalated (which branch fired).

---

## Output Format

Produce **one artifact with two parts**: Part A (the instruction
set) and Part B (the Deployment Record). Use this exact structure.
Do not omit sections; a section with nothing to report states that
explicitly.

---
```markdown
# Deployment Execution Instruction Set & Deployment Record — Phase 7 (Existing Projects)

**Project:** [subject name]
**Release / Version:** [version — per Step 02 §1]
**Release Ref:** [branch @ commit]
**Deployment Shape (Step 01 §3):** [release-shaped / service-shaped]
**Step 02 Determination:** [GO / CONDITIONAL GO — conditions listed
and verified honored in PF-1]
**Execution Date:** [date]
**Practitioner:** [name or role]
**Execution Mode:** [direct / patch-mediated]
**Instruction Set Version:** [vN — evolves per release]
**Step 04 Readiness Verified:** [Yes — §5 entry ref / execution
blocked]
**Feeds Into:** Step 04 trigger monitoring; Steps 05–07; the Step 07
launch refresh (consumes Part B)
**Status:** [Executing / Live — Verified / Live — Follow-ups Open /
Escalated (branch E-N)]

> ⚠️ This artifact executes a release; it does not authorize one
> (Step 02 is the front gate) and it does not define recovery
> (Step 04 authored that, readied before this step ran). The
> publish/deploy checkpoint is the single most consequential action
> in the track — for release-shaped subjects, publish is
> irreversible: published versions are immutable, and recovery is
> the recall path, not an undo. Every checkpoint requires logged
> human authorization; AI executes, humans authorize.

---

## PART A — Deployment Execution Instruction Set (vN)

**Trigger:** A release with a Step 02 §4 GO — or CONDITIONAL GO with
every named condition verified honored at PF-1. No other trigger
starts this script.

### A.1 Pre-Flight Verification (gate — all rows pass before any
execution step)

| ID | Check | Pass Criterion | Result | Evidence |
|----|-------|----------------|--------|----------|
| PF-1 | Step 02 determination current; conditions honored; release ref unchanged; no concurrent release intervened | [criterion] | [PASS/FAIL] | [CONFIRM/AWARE + detail] |
| PF-2 | Clean from-scratch build from the release ref | [artifact name, version, hash recorded] | | |
| PF-3 | Full standing suite green on the release ref | [actual counts] | | |
| PF-4 | Version / tag / changelog consistency; no version collision | | | |
| PF-5 | Evidence-plan inputs ready (Step 02 §3; schema e.g. MC-12) | | | |
| PF-6 | **Rollback/recall readied — GATE** (Step 04 set exists for THIS release; triggers defined; §5 readiness entry current) | | | |
| PF-7 | Credential posture confirmed per Step 00 (values never printed) | | | |

- **Decision branch:** any PF row FAIL → **E-1** (HALT before
  execution).

### A.2 Execution Branch — RELEASE-SHAPED
[If service-shaped: **Not applicable — shape declared service-shaped
at Step 01 §3.** Retain this branch unexecuted.]

| ID | Step | Detail | Result |
|----|------|--------|--------|
| RS-1 | Final version commit + tag on the release ref | [exact command/action; tag name] | |
| RS-2 | Publish preview (dry-run / pack listing where tooling supports) | [packed contents reviewed; identity confirmed] | |
| **CP-1** | **CHECKPOINT — human authorizes publish** | Present: artifact identity (name@version, hash, packed contents), target registry + dist-tag/channel, readied recall path (PF-6 ref). **Irreversible beyond this point.** | [authorized by / declined] |
| RS-3 | Publish to the registry | [exact command; never echoing credentials] | |
| RS-4 | Post-publish verification | Registry listing shows the version; install/resolve probe from a clean environment succeeds and loads; provenance/signature check passes where operated | |
| **CP-2** | **CHECKPOINT — human authorizes release notes / consumer advisory posting** | [channels per existing release discipline] | |
| RS-5 | Release notes / advisory posted | | |
| RS-6 | Release-evidence artifacts emitted per the Step 02 §3 plan; validated against schema (e.g. MC-12) | [artifact list → Part B §4] | |

- **Decision branch:** RS-4 verification FAIL → **E-3** (the version
  is live and immutable — Step 04 recall assessment fires
  immediately). Failure at RS-1/RS-2 or a declined CP-1 → **E-2**
  (halt in safe state; nothing published).

### A.3 Execution Branch — SERVICE-SHAPED
[If release-shaped: **Not applicable — shape declared release-shaped
at Step 01 §3.** Retain this branch unexecuted.]

| ID | Step | Detail | Result |
|----|------|--------|--------|
| SS-1 | Environment preparation (config staged; dependency order confirmed) | | |
| **CP-D** | **CHECKPOINT — human authorizes migrations / data changes** (only if present) | [what changes; reversibility] | |
| SS-2 | Migrations / data changes executed (if authorized) | | |
| **CP-1** | **CHECKPOINT — human authorizes deploy** | Present: artifact identity, target environment, readied rollback path (PF-6 ref) | |
| SS-3 | Deploy (in dependency order) | | |
| SS-4 | Health checks + smoke probes | [endpoints, probes, actual results] | |
| **CP-2** | **CHECKPOINT — human authorizes traffic enablement** (per stage, where staged) | [stage plan: canary / % / full] | |
| SS-5 | Traffic enabled per stage; stage-gate probes between stages | | |
| SS-6 | Evidence / record emission per the Step 02 §3 plan | [→ Part B §4] | |

- **Decision branch:** SS-4 FAIL before traffic → **E-4** (Step 04
  rollback path: revert + verify). A stage-probe FAIL after partial
  traffic → **E-4** scoped to the stage. Failure at SS-1/SS-2 or a
  declined checkpoint → **E-2** (halt in safe state).

### A.4 Verification & Observability Activation (both shapes)

| ID | Probe | Basis | Result |
|----|-------|-------|--------|
| V-1 | Shape-specific verification (RS-4 / SS-4 rows, consolidated) | [per branch] | |
| V-2 | Performance sanity vs the Phase 6 Step 05 baselines (where measurable at this timescale) | [baseline refs] | |
| V-3 | Observability touchpoints emitting (Phase 3-designed, Phase 5-built) — per signal | [evidence per touchpoint] | |
| V-4 | Alerting live — thresholds active; test-fired where safe | | |

- **Decision branch:** V-3/V-4 FAIL → the deployment is **not
  declared verified**; fix-forward under E-5 guidance or fire the
  shape's recovery branch per the Step 04 triggers.

### A.5 Day-One Routine Establishment

| ID | Routine | Owner (named) | Cadence | Provenance | Inherited By |
|----|---------|---------------|---------|------------|--------------|
| RT-1 | Metric review | | [e.g. daily, week one; then per Step 07 cadence] | [EXISTING-CODIFIED / EXTENDED / NEW] | Step 07 |
| RT-2 | Trend check | | | | Step 06 / 07 |
| RT-3 | Alert response | | [on alert] | | Step 05 |
| RT-4 | Step 07 launch refresh scheduled (consumes this Record) | | [date] | [NEW] | Step 07 |

### A.6 Escalation Paths

| ID | Failure Mode | Path |
|----|--------------|------|
| E-1 | Pre-flight failure (any PF row) | HALT before execution; fix and re-run pre-flight, or return to Step 02 if the release definition or its currency changed |
| E-2 | Execution failure before CP-1, or a declined checkpoint | HALT in safe state — nothing consequential has happened; diagnose, record, restart from pre-flight |
| E-3 | Release-shaped: post-publish verification failure (RS-4) | **Step 04 recall assessment fires immediately** — the version is live and immutable; recall = deprecation + advisory + patched release. No unpublish or destructive registry action without explicit human direction |
| E-4 | Service-shaped: post-deploy verification or stage-probe failure | Step 04 rollback path (revert + verify), scoped to the failed stage where traffic was staged |
| E-5 | Evidence emission or observability activation failure on an otherwise-live release | Release is live but unproven/blind — blocking follow-up in §6 with owner and deadline; escalate to the checkpoint authorizer; does not by itself fire recall/rollback |
| E-6 | Anything the script cannot resolve | Escalate to [named human] with the Deployment Record as it stands |

---

## PART B — Deployment Record (this release)

## §1 — What Shipped

| Field | Value |
|-------|-------|
| Version / tag | |
| Release ref (branch @ commit; artifact hash) | |
| Shape executed | [release-shaped / service-shaped] |
| Contents (traced) | [MC-NN / Brief IDs per Step 02 §1] |
| Target | [registry + dist-tag / environment(s)] |
| Executed (start → end) | [timestamps] |
| Outcome | [Live — Verified / Live — Follow-ups Open (§6) / Escalated (E-N)] |

## §2 — Checkpoint Log

| Checkpoint | What Was Authorized | Authorized By | When | Basis Presented |
|------------|---------------------|---------------|------|-----------------|
| CP-1 | [publish / deploy] | [name] | [timestamp] | [artifact identity + target + recovery-path ref] |
| CP-2 | [advisory / traffic stage] | | | |
| [CP-D / others] | | | | |

[Every checkpoint in the executed branch appears here — an unlogged
checkpoint did not happen. Declined checkpoints are logged with the
decline and its reason.]

## §3 — Verification Results

| Probe (Part A ID) | Executed How | Actual Result | Verdict | Flag |
|-------------------|--------------|---------------|---------|------|
| [RS-4 / SS-4 / V-N rows] | [command / patch-mediated paste] | [raw output summary] | [PASS/FAIL] | [CONFIRM] |

[Nothing here rests on [AWARE]. In patch-mediated mode, only pasted
raw results earn [CONFIRM].]

## §4 — Release-Evidence Artifacts Emitted

| Artifact (per Step 02 §3 plan) | Schema | Location | Validated Against Schema? | Notes |
|--------------------------------|--------|----------|---------------------------|-------|
| [e.g. release evidence artifact] | [e.g. MC-12] | [path/URL] | [Yes / FAIL → §6] | |

**Planned:** [N] · **Emitted:** [N] · **Validated:** [N]
[Any shortfall is an E-5 follow-up in §6.]

## §5 — Observability Activation & Day-One Routine

**Activation:**

| Touchpoint / Signal (Phase 5-built) | Emitting? | Evidence | Alerting Live? |
|--------------------------------------|-----------|----------|----------------|
| | [Yes/No] | [CONFIRM + detail] | [thresholds active; test-fired where safe] |

**Day-one routine (from Part A §A.5, as established):**

| ID | Routine | Owner | Cadence | Provenance | Inherited By |
|----|---------|-------|---------|------------|--------------|
| RT-N | | | | | |

## §6 — Deviations & Follow-ups

| ID | Deviation / Follow-up | Reason | Routing | Owner | Due |
|----|------------------------|--------|---------|-------|-----|
| DV-1 | [deviation from the instruction set / open follow-up] | | [TD-NN candidate (Step 08 — SDD bypass) / DR-NN candidate (Step 06) / Step 04 / Step 05 handoff / instruction-set evolution] | | |

**Instruction-set evolution notes (applied to v[N+1]):** [checks to
add, checkpoint placement changes, branch-criteria sharpening — or
"None; the script held."]

[If none: "No deviations — executed as scripted."]

## Version

v1.0 (Part A is the instruction set at v[N], evolving per release
via the §6 notes; Part B is this release's record — closed once the
outcome is stated and immutable thereafter, append-only for
follow-up closure updates)
```

---

## Evaluation Checklist

Before this artifact is accepted as complete, verify all items:

- [ ] Execution proceeded only on a Step 02 §4 GO — or CONDITIONAL GO
      with every named condition verified honored at PF-1 — and
      currency was re-verified (release ref unchanged; no concurrent
      release intervened)
- [ ] Part A meets the instruction-set output standards: explicit
      trigger condition, ordered and specifically executable steps,
      decision branches with clear criteria, human checkpoints before
      every consequential action, escalation paths per failure mode —
      and it is versioned, evolving via the Part B §6 notes
- [ ] Both shape branches are present in Part A, and the inapplicable
      branch is marked **Not applicable — shape declared [X] at
      Step 01 §3** rather than deleted; the executed branch matches
      the declaration
- [ ] Rollback/recall readiness was verified in pre-flight as a gate
      (PF-6: the Step 04 instruction set readied **for this release**,
      triggers defined) before any execution-branch step ran
- [ ] Every checkpoint in the executed branch is logged in §2 with
      the authorizer, timestamp, and the basis presented — including
      the publish/deploy authorization with artifact identity and the
      readied recovery path; declined checkpoints logged with reasons
- [ ] The verification probes were executed with actual recorded
      results (§3) — registry listing, clean-environment
      install/resolve probe, and provenance/signature check
      (release-shaped) or health checks, smoke probes, and staged
      traffic gates (service-shaped), plus performance sanity vs the
      Phase 6 Step 05 baselines where measurable — with nothing
      resting on [AWARE]
- [ ] Every release-evidence artifact the Step 02 §3 plan names was
      emitted and validated against its schema (§4), with any
      shortfall recorded as an E-5 follow-up
- [ ] Observability activation is confirmed with evidence per
      touchpoint — the Phase 5-built touchpoints emitting, alerting
      live — and the day-one routine is established with named owners,
      cadences, and provenance tags, including the scheduled Step 07
      launch refresh (§5)
- [ ] Escalation branches are defined per failure mode, and any fired
      branch is recorded — in particular, a failed post-publish
      verification fired the Step 04 recall assessment rather than an
      improvised registry action
- [ ] No secrets or registry credentials were printed, logged, or
      committed; no destructive registry or git operations were
      performed; irreversible actions sat behind their checkpoints
- [ ] The Deployment Record §1–§6 is complete — what shipped traced
      to the Step 02 §1 contents, the outcome stated plainly — with
      every deviation routed (TD-NN candidate for any SDD bypass) and
      the instruction-set evolution notes captured
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)

---

*Part of the Phase 7 (Existing Projects) Deployment & Evolution Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `deployment-evolution.existing-project.instructions.md`*
*Previous step: `step-02-launch-readiness-confirmation.prompt.md`*
*Next step: `step-04-rollback-and-recall-procedure.prompt.md` (readied before this step executes; fires on trigger)*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Phase 7 existing-projects Deployment Execution & Verification prompt, adapted from the greenfield Phase 7 step-02 deployment-checklist prompt with the track's release-shaped realities made first-class. The artifact is two parts in one template: Part A, a versioned AI-executable Deployment Execution Instruction Set (trigger = Step 02 GO; a seven-row pre-flight gate including PF-6 rollback/recall readiness — the Step 04 procedure is readied before Step 03 executes, inverting the file-chain numbering; release-shaped and service-shaped execution branches with the inapplicable branch retained and marked; verification probes; observability activation; day-one routine with provenance tags; escalation paths E-1..E-6), and Part B, the per-release Deployment Record (§1 What Shipped through §6 Deviations & Follow-ups) that feeds the Step 07 launch refresh. Track-distinctive disciplines: the publish checkpoint treated as the single most consequential and (release-shaped) irreversible action, with dry-run preview and artifact-identity presentation before authorization; post-publish verification from the consumer's seat (registry listing, clean-environment install/resolve probe, provenance check) with a failed verification firing the Step 04 recall assessment rather than improvised registry surgery; release-evidence artifacts emitted per the Step 02 §3 plan and schema-validated (MC-12 as the Diamonds example); day-one routines with named owners handed to the Stage 2 loops; full patch-mediated execution support with [CONFIRM]-only verification evidence; and instruction-set evolution via the §6 deviation notes, with SDD bypasses routed as TD-NN candidates. |
