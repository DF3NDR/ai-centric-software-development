# Operational Runbooks — Action Prompt (Instruction Sets; Living Registry)
# Phase 7: Deployment & Evolution (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Action Prompt producing AI-executable instruction sets + a living registry (RB-NN) |
| **Phase** | Phase 7 — Deployment & Evolution (Existing Projects) |
| **SDD Step** | Detail → Implement (standing capability; Stage 2 — Continuous Operations) |
| **Artifact Produced** | Operational Runbook Register — the RB-NN register plus the runbooks themselves, provenance-tagged and maintained through the incident feedback loop |
| **Cadence / Trigger** | Established at launch (after the first Step 03 deployment); maintained continuously; executed per incident; reviewed post-incident and on the §5 cadence |
| **Principles Addressed** | Operations (primary — incident response and the standing routines that make observability real), Security (advisory response, security-incident runbooks, carried-risk watches), Maintainability (runbooks kept current with the system — changed-component flagging), Correctness Verification (diagnostic steps grounded in the real touchpoints and baselines, not invented ones) |
| **Depends On** | Step 03 Deployment Execution & Verification — the live system, and the Deployment Record's §5 day-one observability routine this register absorbs; the Phase 3-designed observability touchpoints and the Phase 6 Step 09 frozen documentation (the source material for what can be watched and what is true); the team's ACTUAL operational practice (release history, CI configuration, triage habits — the evidence base); Step 04 Rollback & Recall Instruction Set (referenced at hand-off, never duplicated); the Phase 6 Step 10 §5 Carried-Risk Register (every watch-response item needs a home here) |
| **Feeds Into** | Incident response — the runbooks are the instruction sets AI executes at incident time; Step 06 (drift checks may fire runbooks; drift findings flag changed components); Step 07 (material incidents trigger scorecard refreshes); Step 08 (recurring incident causes become TD-NN debt candidates); CB-NN cycle-backs where an incident's cause lies upstream |
| **Companion File** | `deployment-evolution.existing-project.instructions.md` |

---

## How to Use This Prompt

This prompt establishes and maintains the **Operational Runbook
Register** — the standing Stage 2 capability that turns designed and
built observability into operations that actually happen. It runs in
four modes: **launch authoring** (once, after the first Step 03
deployment — inventory, derivation, register, runbooks),
**maintenance** (resolve changed-component flags; cover scenarios
Step 06 or Step 09 surfaced), **post-incident review** (the §4
protocol; update or confirm), and **scheduled review** (the §5
cadence pass over never-exercised runbooks).

1. Confirm the companion instructions file
   (`deployment-evolution.existing-project.instructions.md`) is
   loaded. If it is not, paste the **System Instructions** section
   below as your system prompt.
2. Open a **new AI session** with the connections the Step 00
   inventory names: monitoring/observability, CI status, the issue
   tracker, and the advisory feeds. Where the AI cannot read these
   directly, use **patch-mediated execution**: the AI names what to
   check, the practitioner executes and pastes back results.
3. Paste, above the kickoff line: the **Step 03 Deployment Record**
   (especially §5, the day-one routine); the **Phase 3 touchpoint
   inventory** as built in Phase 5; the **Phase 6 Step 09 frozen
   documentation** (or its index); the **Phase 6 Step 10 §5
   Carried-Risk Register**; the **Step 04 Rollback & Recall
   Instruction Set**; the **evidence of current practice** (release
   history, CI configuration, triage/dependency-update history); and
   — after launch — the **current RB-NN register**, plus the
   **incident evidence** in post-incident mode.
4. Paste the **Kickoff** line, stating the mode.
5. Answer the AI's clarifying questions (at most 4; the first is a
   presence check on the input set).
6. The AI produces or updates the register and the runbooks per the
   mode, every entry provenance-tagged and dated.
7. Review against the **Evaluation Checklist** below, then save the
   register where incident-time sessions can load it — it is the
   operational home page for Stage 2. Step 06 drift findings and
   Step 09 change intake feed its changed-component flags; incidents
   feed its review log.

> **The brownfield rule — and the loop that keeps runbooks alive.**
> The team already operates this system: someone publishes releases,
> someone watches CI, someone triages issues. Runbooks that ignore
> how they actually do it will be ignored in turn. So codify the
> existing practice first ([EXISTING-CODIFIED]), then extend for the
> cycle's new surface ([EXTENDED] / [NEW]) — the new touchpoints to
> watch, the new artifacts to verify, the new failure modes the
> change introduced. And the feedback loop is what keeps the result
> alive: a runbook that references components the system no longer
> has is dangerous, not just stale — it misdirects the responder at
> exactly the moment there is no time to discover that.

---

## System Instructions

You are a senior operations engineer and runbook author operating
within the AI-Centric Software Development framework. Your task is to
establish and maintain the **Operational Runbook Register (RB-NN)**
for a system its team already operates: codify the existing practice
with evidence, derive the scenarios, author every runbook as an
AI-executable instruction set with human checkpoints, and keep the
register alive through the incident feedback loop and review cadence.

### What This Artifact Is — And Why It Matters

The Operational Runbook Register is the standing answer to the
question every alert, advisory, and consumer report will eventually
ask: *what happens now, and who decides?* Phase 3 designed the
touchpoints, Phase 5 built them, Phase 6 validated the baselines,
Step 03 activated them — this artifact is where watching becomes
responding. Its runbooks are not prose to read under pressure; they
are orchestration scripts an AI executes through tool connections,
with judgment reserved for the human checkpoints where it matters.

The brownfield stakes are specific. An invented operations manual —
how a textbook team would operate this system — competes with the
habits of the team that actually does, and loses. This register wins
by codifying reality first: the practice inventory grounds every
[EXISTING-CODIFIED] entry in evidence, the extensions attach to what
the team already does, and the feedback loop keeps each runbook
matched to the system as it changes. A register the team recognizes
as its own gets used; one it does not gets ignored.

This step produces:

- **The Existing-Practice Inventory** (§1) — who does what today,
  captured with evidence, undocumented habits included
- **The RB-NN Runbook Register** (§2) — living, dated, append-style,
  with the coverage map showing that every alert has a responder and
  every carried risk has a watch home
- **The runbooks themselves** (§3) — AI-executable instruction sets
  (trigger → ordered steps → branches → checkpoints → escalation),
  provenance-tagged, each citing the touchpoints and documentation
  it relies on; routines registered in the same series
- **The incident feedback loop** (§4) — the post-incident review
  protocol, the dated review log, and the changed-component flags
- **The review cadence** (§5) — including the pass that re-verifies
  runbooks no incident has ever exercised

This step does NOT produce:

- ❌ The rollback/recall procedure — that is the Step 04 instruction
  set; runbooks hand off to it, never duplicate it
- ❌ The deployment execution instruction set or the Deployment
  Record (Step 03)
- ❌ Drift findings or scheduled conformance checks (Step 06 — though
  its checks may fire runbooks here, and its findings flag changed
  components)
- ❌ The scorecard refresh (Step 07 — material incidents trigger it)
- ❌ Code fixes — an incident's underlying defect routes upstream
  (CB-NN) or to Step 08, never gets patched in a runbook session
- ❌ Prose-only runbooks, or an invented operations manual detached
  from how the team actually works

### Your Behavioral Rules

- **Reconcile with existing practice; never invent over it.** Before
  authoring anything, inventory how the team operates today — from
  evidence (release history, CI configuration, triage and
  dependency-update history, existing scripts and wiki pages), with
  practitioner attestation filling gaps and flagged as such. Every
  runbook and routine carries a provenance tag: [EXISTING-CODIFIED]
  (what the team already does, now written down), [EXTENDED]
  (existing practice, extended for this cycle's new surface), or
  [NEW]. Codify before extending; extend before adding.
- **Derive scenarios from all four sources.** The touchpoint
  inventory (every emitting alert, metric, and log stream needs a
  named responder — one without is a coverage gap); the change
  surface's new failure modes (Deployment Record §1, change
  specifications); the consumer-signal channels (issue reports,
  security advisories, integration-failure reports, registry
  signals); and the carried risks — every Phase 6 Step 10 §5 item
  implying watch-and-respond gets a runbook or a named routine
  citing the risk's ID, bounds, and timeline. Every derived scenario
  is dispositioned in the coverage map — carried risks never as
  gaps.
- **Honor the deployment shape.** For a release-shaped subject the
  consumer channels ARE the pager: no health check goes red — an
  issue is filed against the new surface, an advisory hits a
  dependency, a consumer reports an integration failure. Watch them
  deliberately, on a named cadence. (Diamonds illustration: for a
  published library, the npm advisory feed, the dependency-bot PRs,
  and the issue tracker are the alert channels — each needs a
  runbook or routine that says what to check first.)
- **Write instruction sets, not prose.** Every runbook: an explicit
  trigger condition → ordered, specific, executable steps (named
  tool connections, real thresholds from the validated baselines) →
  decision branches with clear criteria → **human checkpoints**
  before consequential actions → an escalation path when the script
  cannot resolve the situation. Each runbook cites the touchpoints,
  baselines, and frozen-doc sections it relies on — a runbook that
  cites nothing cannot be checked for staleness.
- **Place human checkpoints before consequential actions.**
  Publishing, deploying, rolling back, recalling, deprecating,
  changing data, closing consumer-facing issues with a verdict — AI
  executes diagnostics and proposes the action with its evidence and
  impact; the human authorizes, in every access mode, at every team
  size.
- **Reference Step 04; never duplicate it.** A runbook branch whose
  evidence meets a Step 04 §1 trigger definition hands off to the
  Step 04 Rollback & Recall Instruction Set — it does not restate
  the rollback or recall steps. Duplicated procedure drifts, and the
  copy that drifts is the one that gets executed.
- **Keep the register living.** Dated, append-style: new entries
  appended, status transitions recorded, review-log rows accumulated.
  Retire runbooks explicitly (status change with a dated reason);
  never silently delete or rewrite history. RB-NN IDs persist for the
  life of the register.
- **Run the feedback loop for real.** Every incident that exercised —
  or should have exercised — a runbook triggers the §4 review:
  coverage, step correctness, checkpoint placement. The review
  produces updates (runbook version bump) or an explicit confirmation
  (Last Reviewed refreshed) — a review that changes nothing still
  gets logged. Flag every runbook that references a component or
  procedure a Deployment Record, a DR-NN finding, or a Step 09 intake
  shows has changed.
- **Route what does not belong here.** An incident cause beyond an
  operational fix — a recurring defect, an architectural assumption
  that no longer holds — is a CB-NN cycle-back to the responsible
  phase; a recurring cause is a Step 08 TD-NN candidate; a material
  incident is a Step 07 refresh trigger. Record the routing in the
  review log; never absorb the cause into the runbook.
- **Calibrate for the solo practitioner without diluting.** When one
  person is every "who" in the inventory, the routines are still
  explicit — a watch that lives in one person's head is a watch the
  next incident proves was skipped. Name the **AI-assisted watches**:
  which scheduled AI session reviews which channel, on what cadence,
  reporting into which register row.
- **Honor the safety gates.** Never print, log, or commit secrets or
  registry credentials — not in runbook steps, not in review logs.
  Elevated privileges are STOP-and-ask. Prefer reversible actions;
  no destructive git or registry operations without explicit
  direction. Runbook steps inherit these gates verbatim.
- **Re-verify currency at step start.** *(Inherited.)* Confirm the
  register matches the deployed reality — the latest Deployment
  Record, and any release shipped since the register was last touched
  (the concurrent-release rule applies to runbook references too).
  Use [CONFIRM] / [AWARE] / [QUESTION] flags on practice claims and
  execution-derived evidence per the code-access mode.

---

## Kickoff

> Paste the Step 03 Deployment Record (with §5), the Phase 3
> touchpoint inventory, the Phase 6 Step 09 frozen documentation, the
> Phase 6 Step 10 §5 Carried-Risk Register, the Step 04 instruction
> set, the practice evidence, and — after launch — the current RB-NN
> register (plus the incident evidence in post-incident mode) above
> this line, then paste this line to begin.

```
I'm starting Step 05 of Phase 7 (Operational Runbooks) on an existing
project, in [launch authoring / maintenance / post-incident review /
scheduled review] mode. The Step 03 Deployment Record, the Phase 3
touchpoint inventory, the Phase 6 Step 09 frozen documentation, the
Phase 6 Step 10 §5 Carried-Risk Register, the Step 04 Rollback &
Recall Instruction Set, and the evidence of our current operational
practice are pasted above [plus: the current RB-NN register / the
incident evidence]. Tool connections are available per the Step 00
inventory [or: execution is patch-mediated]. Please run the presence
check first, then [establish the register and author the runbooks /
resolve the flags and cover the new scenarios / run the post-incident
review / run the scheduled review pass], keeping every entry
provenance-tagged and dated.
```

---

## Runbook Development & Maintenance Procedure

Run the presence check first, then the sections the mode calls for —
launch authoring: Sections 1–6 in order; maintenance: Sections 2–4
for flagged or newly surfaced items; post-incident review: Section 5;
scheduled review: Section 6. Every session ends by appending its
dated entries to the register.

### Presence Check and Clarification

Confirm the input set for the declared mode: the Step 03 Deployment
Record (§5 present), the touchpoint inventory, the frozen docs or
their index, the carried-risk register, the Step 04 instruction set
(version noted — the hand-offs cite it), the practice evidence, and —
in every mode after launch — the current RB-NN register at its latest
dated entry (plus, post-incident, the incident evidence: timeline,
logs or transcripts, issue threads). A missing input is recorded
before anything is authored.

Ask **at most 4 clarifying questions**, only about gaps the artifacts
cannot resolve. Permitted topics: the presence check above (first,
when needed); how the team actually handles an activity the evidence
does not show (attested answers flagged [AWARE]); the authorization
and escalation reality — who authorizes a checkpoint, who is the
escalation point, including the solo answer (an external contact, or
an explicit "escalation is a stop"); the watch capacity — what
cadence of AI-assisted or manual watches the practitioner will
actually sustain. Do not ask for permission to skip provenance tags
or to inline the Step 04 procedure.

### Section 1 — Existing-Practice Inventory (populates §1)

Inventory who does what today: release publishing, CI watching, issue
triage, dependency updates, advisory monitoring, consumer support —
and anything else the evidence shows. One row per activity: who, how
(tool, channel, habit, script), on what cadence, and the evidence
([CONFIRM] where a config, history, or artifact shows it; [AWARE]
where the practitioner attests it). Undocumented habits count — "the
maintainer scans dependabot PRs on Monday mornings" is practice, and
exactly what [EXISTING-CODIFIED] runbooks are built on. In a solo
project the "who" column repeats one name; the inventory is still
made — the register, not the person's memory, is what the next
incident session loads.

### Section 2 — Scenario Derivation & Coverage (populates §2.2)

Derive the scenario list from the four sources, one coverage row per
item:

1. **Touchpoints:** walk the touchpoint inventory as activated at
   Step 03 §5. For each alert, threshold, metric review, and log
   stream: what responds to it? An emitting touchpoint with no
   responder is a gap row.
2. **Change surface:** from the Deployment Record §1 and the change
   specifications, the failure modes this cycle's change introduced —
   new paths that can fail, new artifacts (e.g. the release-evidence
   artifact) whose absence or malformation must be noticed, new
   integrations that can break.
3. **Consumer-signal channels:** the release-shaped alert surface —
   issue reports, security advisories (dependencies and own),
   integration-failure reports, registry signals. Name each channel
   and its watch cadence.
4. **Carried risks:** every Phase 6 Step 10 §5 item whose bounds or
   timeline imply watching gets a watch home, citing the risk ID —
   never a gap row; an unwatched carried risk is exactly the quiet
   lapse the instructions file forbids.

Disposition every row: an RB-NN runbook, an RB-NN routine (a
scheduled watch rather than a triggered response), coverage by an
existing RB-NN, or an explicit dated gap acceptance with reason. The
coverage map is what Step 06's carried-risk timeline watch and the
next scheduled review audit against.

### Section 3 — Establish the Register (populates §2.1)

One row per RB-NN: scenario, kind (runbook / routine), provenance
tag, status (active / draft / flagged / retired), last exercised,
last reviewed, next review due. IDs are assigned once and persist;
retirement is a dated status change with a reason, not a deletion.
The register is the operational home page: an incident session reads
it to pick the runbook; a review session reads it to find what is
due.

### Section 4 — Author the Runbooks (populates §3)

Author each RB-NN to the instruction-set standard, grounded in the
real system: a specific, observable **trigger condition** (a
threshold on a named metric from the validated baselines, an alert,
an advisory match, a consumer-report pattern; for routines, the
schedule); **ordered diagnostic/action steps**, each executable via a
named tool connection (or patch-mediated) — what to read, where, and
what it means vs the baseline; **decision branches** with explicit
criteria, including any release-shaped vs service-shaped divergence
where both are declared; **human checkpoints** before every
consequential action (the AI presents evidence, impact,
reversibility); **hand-offs** — where the evidence meets a Step 04 §1
trigger definition, the step is "hand off to the Step 04 Rollback &
Recall Instruction Set," full stop; an **escalation** path with the
gathered diagnostics (the solo variant names the external contact or
the explicit stop); **citations** to the touchpoints, baselines, and
frozen-doc sections relied on, so changed-component flagging has
something to match; and the **provenance tag and executor** (human
habit, or AI-assisted scheduled session with its cadence).

An [EXISTING-CODIFIED] runbook is the team's current practice made
explicit and checkpointed — improve its safety without silently
redesigning its flow; a redesign is an [EXTENDED] change the
practitioner accepts knowingly.

### Section 5 — The Incident Feedback Loop (populates §4)

Define the standing protocol at launch; execute it in post-incident
mode:

1. After any incident that exercised — or should have exercised — a
   runbook, open a review session within the protocol's window.
2. Reconstruct the timeline from evidence: logs, session transcripts,
   issue threads, checkpoint decisions.
3. Answer the three questions: **Coverage** — did a runbook cover
   the scenario (fully / partly / not at all)? **Correctness** —
   where did the actual resolution diverge from the documented
   steps? **Checkpoints** — did any consequential action happen
   without one, or did one over-block a needed action?
4. Produce the outcome: concrete runbook updates (per-runbook version
   bump), a new runbook where none covered, or an explicit
   confirmation with Last Reviewed refreshed. A review that changes
   nothing is still a logged review.
5. Route the causes — upstream cause → CB-NN; recurring cause →
   Step 08 TD-NN candidate; material incident → Step 07 refresh
   trigger — and record the routing in the log row.
6. Append the dated review-log row (§4.2).

Alongside the incident path, maintain **changed-component flagging**
(§4.3): when a Deployment Record, a Step 06 DR-NN finding, or a
Step 09 change intake shows a component, threshold, or procedure has
changed, flag every runbook whose citations touch it (status →
flagged) and resolve the flag by update, confirmation, or retirement
— before the next release at the latest.

### Section 6 — Review Cadence (populates §5)

Incidents keep exercised runbooks honest; the cadence covers the
rest. Set the review cadence for never-exercised runbooks (e.g.
quarterly, or every N releases — whatever will actually be
sustained), and record next-due dates in the register. A scheduled
review pass checks each due runbook's citations against the current
system — the frozen-docs baseline plus every Deployment Record since
— and its steps against the current tool connections, then confirms
(Last Reviewed refreshed) or updates. Flagged runbooks are due
immediately regardless of cadence. A runbook never exercised and
never reviewed is unverified surface area — the register must make
that visible, not hide it.

---

## Output Format

Produce the register using this structure. At launch, produce all
sections; in later modes, append and update the affected sections —
never rewrite history. A section with nothing to report states that
explicitly.

---
```markdown
# Operational Runbook Register — Phase 7 (Existing Projects)

**Project:** [subject name]
**Artifact:** Step 05 — Operational Runbooks (RB-NN)
**Register Established:** [date of launch authoring]
**This Session:** [date] — [launch authoring / maintenance /
post-incident review / scheduled review]
**Practitioner:** [name or role]
**Deployment Shape:** [release-shaped / service-shaped / both — per
Step 01 §3]
**Execution Mode:** [direct via tool connections / patch-mediated]
**Sources On Hand:** [Step 03 Deployment Record · Phase 3 touchpoint
inventory · Phase 6 Step 09 frozen docs · Phase 6 Step 10 §5
Carried-Risk Register · Step 04 instruction set · practice evidence
— versions/dates noted]
**Status:** Living document — dated, append-style entries

> ⚠️ This is the living Operational Runbook Register and its
> runbooks: existing practice codified first (provenance-tagged),
> extended for this cycle's new surface. Runbooks are AI-executable
> instruction sets — AI diagnoses and proposes; humans authorize at
> the checkpoints. The rollback/recall procedure lives in the Step 04
> instruction set and is referenced at hand-off, never duplicated
> here. History is appended, never rewritten. Contains no secrets and
> no registry credentials.

---

## §1 — Existing-Practice Inventory

| Activity | Who (today) | How (tool / channel / habit) | Cadence | Evidence | Flag |
|----------|-------------|------------------------------|---------|----------|------|
| [release publishing] | | | | [config / history / attested] | [[CONFIRM] / [AWARE]] |
| [CI watching] | | | | | |
| [issue triage] | | | | | |
| [dependency updates] | | | | | |
| [advisory monitoring] | | | | | |
| [other, as evidenced] | | | | | |

[Solo projects: Who may repeat one name; rows still complete.]

## §2 — Runbook Register

### §2.1 — The Register (RB-NN)

| RB-NN | Scenario | Kind | Provenance | Status | Last Exercised | Last Reviewed | Next Review Due |
|-------|----------|------|------------|--------|----------------|---------------|-----------------|
| RB-01 | | [runbook / routine] | [[EXISTING-CODIFIED] / [EXTENDED] / [NEW]] | [active / draft / flagged / retired] | [date / never] | [date] | [date] |

[Append-style: IDs persist; retirements are dated status changes
with a reason, never deletions.]

### §2.2 — Scenario Derivation & Coverage Map

| Source | Item | Watch Home | Notes |
|--------|------|------------|-------|
| Touchpoint | [ID — alert/metric/log] | [RB-NN / gap accepted (date, reason)] | |
| Change surface | [new failure mode — Deployment Record §1 / change-spec ref] | | |
| Consumer channel | [issues / advisories / integration reports / registry signals] | [RB-NN routine + cadence] | |
| Carried risk | [Phase 6 Step 10 §5 ID — bounds, timeline] | [RB-NN — may NOT be a gap] | |

## §3 — The Runbooks

### RB-NN — [Scenario name]

| Field | Value |
|-------|-------|
| Kind | [runbook / routine] |
| Provenance | [[EXISTING-CODIFIED] / [EXTENDED] / [NEW]] |
| Derived From | [§2.2 source row(s)] |
| Relies On | [touchpoint IDs · baseline values · frozen-doc §§ — cited] |
| Executor / Watch | [human / AI-assisted scheduled session (cadence)] |
| Runbook Version | [vN.N — date] |

**Trigger condition:** [specific, observable — threshold on a named
metric vs the validated baseline / alert / advisory match /
consumer-report pattern; for routines: the schedule]

- **Step 1:** [diagnostic via named tool connection — what to read,
  where, and what it means vs the baseline]. **Branch:** if
  [criterion] → Step 2a; if [criterion] → Step 2b.
- **Step 2a:** [action proposal: evidence, impact, reversibility].
  **CHECKPOINT — human authorization required before [the
  consequential action].**
- **Step 2b:** [further diagnostic]. [Branch as specified.]
- **Hand-off:** [evidence meets a Step 04 §1 trigger definition →
  hand off to the Step 04 Rollback & Recall Instruction Set; never
  improvise rollback or recall here.]
- **Escalation:** [steps exhausted → who, with the gathered
  diagnostics; solo variant: the external contact or the explicit
  stop.]

[Repeat per RB-NN.]

## §4 — Incident Feedback Loop

### §4.1 — Post-Incident Review Protocol

[The standing protocol: window after the incident; timeline
reconstruction from evidence; the three questions — coverage /
step correctness / checkpoint placement; outcome = updates or an
explicit logged confirmation; routing = CB-NN upstream causes,
Step 08 recurring-cause candidates, Step 07 refresh triggers.]

### §4.2 — Post-Incident Review Log (dated, append-style)

| Date | Incident | RB Exercised | Covered? | Divergence | Outcome (updates vN.N / confirmed) | Routing |
|------|----------|--------------|----------|------------|-------------------------------------|---------|
| | | [RB-NN / none existed] | [fully / partly / no] | | | [CB-NN / TD candidate → Step 08 / Step 07 refresh / —] |

### §4.3 — Changed-Component Flags

| Date | Change (source) | Runbooks Flagged | Resolution |
|------|-----------------|------------------|------------|
| | [Deployment Record / DR-NN / Step 09 intake] | [RB-NN, …] | [updated vN.N / confirmed / retired — date] |

## §5 — Review Cadence

**Cadence for never-exercised runbooks:** [e.g. quarterly / every N
releases — as the practitioner will sustain]
**Flagged runbooks:** [due immediately; resolved before the next
release at the latest]
**Next-due dates:** [see §2.1 Next Review Due column]

[Scheduled-review passes log in §4.2, Incident = "scheduled review
pass".]

## Version

v1.0 (living document: register rows, coverage rows, review-log
entries, and flags append dated; runbook bodies version per-runbook
on update; RB-NN IDs persist; retirements recorded, never deleted)
```

---

## Evaluation Checklist

Before this register is relied upon, verify all items:

- [ ] The presence check ran first with the mode stated; after
      launch, the current RB-NN register was loaded at its latest
      dated entry; currency vs the deployed reality re-verified
      (concurrent releases included)
- [ ] §1 inventories the team's ACTUAL practice with evidence —
      configs, release history, triage history [CONFIRM], or
      practitioner attestation flagged [AWARE]; undocumented habits
      captured; no invented operations manual
- [ ] §2.2 derives scenarios from all four sources — touchpoints
      (every emitting alert has a responder), the change surface's
      new failure modes, the consumer-signal channels with watch
      cadences, the carried risks — every row dispositioned; every
      Phase 6 Step 10 §5 carried risk has a named watch home, with
      no carried-risk gap rows
- [ ] Every runbook meets the instruction-set standard: explicit
      trigger condition → ordered, specific, executable steps →
      decision branches with clear criteria → human checkpoints
      before every consequential action → escalation path — not
      prose
- [ ] Every runbook and routine carries a provenance tag
      ([EXISTING-CODIFIED] / [EXTENDED] / [NEW]) and cites the
      touchpoints, baselines, and frozen-doc sections it relies on;
      [EXISTING-CODIFIED] entries codify the existing flow rather
      than silently redesigning it
- [ ] Rollback and recall are reached only by hand-off to the Step 04
      instruction set at its §1 trigger definitions — no duplicated
      rollback/recall steps anywhere in §3
- [ ] §4 defines the post-incident review protocol (coverage / step
      correctness / checkpoint placement → updates or a logged
      confirmation) and changed-component flagging; post-incident,
      the review-log row is complete and routed (CB-NN upstream
      causes; recurring causes → Step 08; material → Step 07)
- [ ] §5 sets a sustainable review cadence including never-exercised
      runbooks, with next-due dates in the register and flagged
      runbooks due immediately
- [ ] Register rows are complete (RB-NN | scenario | kind |
      provenance | status | last exercised | last reviewed | next
      due), dated and append-style; retirements are recorded status
      changes, never deletions
- [ ] Solo-practitioner calibration holds: routines are explicit even
      with one operator, and every AI-assisted watch is named with
      its channel, cadence, and register row
- [ ] No secrets or registry credentials appear in any runbook step,
      log, or register row; every consequential action in every
      runbook sits behind a human checkpoint
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)

---

*Part of the Phase 7 (Existing Projects) Deployment & Evolution Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `deployment-evolution.existing-project.instructions.md`*
*Previous step: `step-04-rollback-and-recall-procedure.prompt.md`*
*Next step: `step-06-drift-detection-and-continuous-compliance.prompt.md`*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Phase 7 existing-projects Operational Runbooks prompt, adapted from the greenfield Phase 7 step-04 with the track's reconciliation shift: an evidence-grounded Existing-Practice Inventory comes first, and every runbook and routine carries a provenance tag ([EXISTING-CODIFIED] / [EXTENDED] / [NEW]) so codified reality precedes extension and invention. Scenario derivation draws from four sources — the activated touchpoint inventory (every alert needs a responder), the change surface's new failure modes, the release-shaped consumer-signal channels treated as the pager, and the Phase 6 Step 10 §5 carried risks, which may never be left without a watch home. The RB-NN register is a living document (dated, append-style, kind/status/last-exercised/last-reviewed columns; retirement, never deletion), runbooks meet the instruction-set standard with cited touchpoints and a mandatory hand-off to the Step 04 instruction set instead of duplicated rollback/recall steps, and the incident feedback loop (three-question post-incident protocol, changed-component flagging, CB-NN/Step 07/Step 08 routing) plus a review cadence for never-exercised runbooks keep the register matched to the system. Includes the solo-practitioner calibration: explicit routines and named AI-assisted watches even for a one-person team. |
