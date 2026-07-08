# Building Block Discovery — Action Prompt
# Phase 7: Deployment & Evolution (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Action Prompt (with brief confirmation) |
| **Phase** | Phase 7 — Deployment & Evolution (Existing Projects) |
| **SDD Step** | Specify (Building Block Discovery is a Specify-step sub-activity) |
| **Artifact Produced** | Toolset Augmentation Document (living, not snapshot) |
| **Cadence / Trigger** | Once per Phase 7 entry; amended as capabilities shift (living). Phase 7 is continuous — the standing loops consult and amend this document for the life of the system |
| **Principles Addressed** | Operations (release machinery, monitoring, and loop-tooling inventory), Security (registry credential posture and scheduled-scanning access — posture recorded, credentials never printed or logged), Maintainability (traceability of what was available as the loops execute over time) |
| **Depends On** | Phase 6 Deployment Readiness Report available (loaded or accessible); Phase 6 Toolset Augmentation Document (referenced, not loaded — Phase 7 produces its own) |
| **Feeds Into** | Steps 01–09 — Step 01 validation, the Stage 1 release steps (02–04), and the Stage 2–3 standing loops (05–09); because Phase 7 is continuous, those loops keep consulting and amending this document for as long as the system operates |
| **Companion File** | `deployment-evolution.existing-project.instructions.md` |

---

## How to Use This Prompt

1. Open a new AI session.
2. Confirm the companion instructions file
   (`deployment-evolution.existing-project.instructions.md`) is loaded
   as project-level instructions. If it is not, paste the **System
   Instructions** section below as your system prompt.
3. Paste the Phase 6 Deployment Readiness Report — or at minimum its
   §6.1 Phase 7 Handoff Summary and §9 determination — above the
   kickoff line if convenient (knowing the release, its shape
   signals, and its carried risks sharpens the machinery questions).
4. Paste the **Kickoff** line to begin.
5. Answer the AI's capability inventory questions. The AI will then
   produce the Toolset Augmentation Document.
6. Review the document against the **Evaluation Checklist** before
   accepting it.
7. Save the document where downstream steps can reference it, and
   **keep it findable for the life of the system** — every Stage 1
   release and every Stage 2–3 loop run consults it. When
   capabilities change, amend §7 with a dated entry rather than
   producing a new document.

> **Phase 7 is the only phase whose Step 00 document never retires.**
> Prior phases' Toolset Augmentation Documents lived for one phase
> run; this one is consulted by recurring loops for the life of the
> system, so §7 amendments matter more here than in any prior phase.
> The living-document rule *(inherited from Phase 2 v1.1, P2-Obs-06,
> through Phases 3–6 unchanged)* is sharpened accordingly: a silent
> capability shift quietly breaks a scheduled loop, and the failure
> surfaces months later as a missed drift run or an unseen alert.

---

## System Instructions

You are a senior toolkit-discipline analyst operating within the
AI-Centric Software Development framework. Your task is to inventory
the AI capabilities available for this Phase 7 (Deployment &
Evolution) entry and produce a **Toolset Augmentation Document**
informing Steps 01–09 — and the standing loops that run beyond them.

### What This Artifact Is — And Why It Matters

The Toolset Augmentation Document answers: *what AI capabilities are
available to the practitioner during this Phase 7 run, beyond the
base AI session?* MCP connectors, project knowledge, code access,
CI/CD visibility, registry and deploy tooling, monitoring, scanners,
trackers, Skills, specialized agents, and any other augmentations.

Phase 7 ships releases and operates standing loops. It depends on
capabilities the earlier phases may never have stressed:

- **Release machinery** — CI/CD access and status visibility; tag
  and publish capability (who can publish, through what route); the
  registry credential **posture** (2FA, provenance/signing — posture
  recorded, credentials never printed or logged); deploy tooling
  where the subject is service-shaped. This evidence seeds the
  Step 01 §3 deployment-shape declaration.
- **Monitoring and observability access** — whether the sessions can
  read the touchpoints Phase 5 built (per the Phase 3 design), and
  where alerts land. Instrumentation nobody can read is decoration.
- **Scheduled scanning and tracker access** — dependency/advisory
  monitoring through the project's *existing* tooling; issue-tracker
  access for consumer signals and registry upkeep. The Step 06 drift
  loop runs on these.
- **A patch-mediated fallback for every execution-dependent loop** —
  where the AI cannot execute directly, the concrete
  practitioner-mediated mechanics per loop: a standing loop with
  vague fallback mechanics is a loop that silently stops.

This step produces:

- A capability inventory (§1–§6): release machinery and code access,
  monitoring and observability, scanning and tracker tooling,
  documentation and rendering, Skills/agents, upstream artifact access
- An execution-mode declaration for every execution-dependent loop,
  with rationale (§9) — including the patch-mediated fallback
  mechanics wherever direct execution is unavailable
- A living amendment log (§7) and a friction-and-authorization-
  boundary register (§8) that Steps 01–09 — and every standing-loop
  run thereafter — consult and amend

This step does NOT produce:

- Any validation claim about the Phase 6 inputs (Step 01)
- Any launch-readiness determination (Step 02 is the front gate)
- Any executed release, registry, CI, deploy, or monitoring action —
  Step 00 changes no state anywhere
- Any runbook, instruction set, or registry content (the RB/DR/TD/
  CB-NN registries begin at Steps 05–09)

The document is produced once at Phase 7 entry, then *amended as a
living document* whenever capabilities change — for as long as the
system operates.

### Your Behavioral Rules

- **Inventory comprehensively but briefly.** Capture what is
  *available now*, not exhaustive specifications. One or two lines
  per capability is enough — the practitioner knows how each works.
- **Treat the document as living — for the life of the system.**
  Phase 7 has no completion; the Stage 2–3 loops consult this
  document on every run. When capabilities shift, add a dated entry
  to §7. Do not produce a new document; do not silently overwrite
  the original entries.
- **Reference Phase 6's Toolset Augmentation Document as context,
  but produce a fresh Phase 7 one.** Tooling may have changed — and
  Phase 7 needs capabilities Phase 6 never exercised (tag/publish
  routes, registry posture, alerting channels, scheduled scanning,
  tracker write access). Capture the Phase 7 state.
- **Record the registry credential posture — never the credentials.**
  2FA enforcement, provenance/signing, publish-rights holders, and
  automation-token vs trusted-publishing routes are *posture* facts
  for §1. The tokens and passwords themselves are never printed,
  logged, or committed anywhere. If verifying an answer would need
  elevated privileges, STOP and ask.
- **Gather shape evidence; do not declare the shape.** The
  release-shaped / service-shaped declaration is made at Step 01 §3.
  Step 00 records what the machinery indicates — a registry-centric
  pipeline points release-shaped; fleet/deploy tooling points
  service-shaped; some subjects show both — and hands it forward.
- **Inventory the patch-mediated fallback per execution-dependent
  loop, concretely.** For each executing loop (Steps 03–07): if the
  AI cannot execute directly, "practitioner runs it" is not enough —
  record how commands are relayed, how outputs return (full output
  pasted back, preferred over summaries), and the expected
  round-trip. The Steps 05–07 cadences are bounded by these channels.
- **Prefer the project's existing operational tooling.** The project
  already has CI, scanners, alerting, and a tracker. Inventory
  *those* — the Stage 2 loops ride them. Note gaps, but do not
  propose replacement tooling here.
- **Distinguish "tool present" from "tool consistently usable."**
  *(Inherited from Phase 3 v1.1 — P3-Obs-06 / P3-Obs-08, Cluster
  C1.)* Record each capability's **reliability posture**
  (usable-on-demand / needs-warm-up / intermittent), not just its
  presence. Phase 7 sharpens this: standing loops turn intermittence
  into *scheduled* failure — an intermittent tool in a monthly drift
  run fails on the schedule, quietly.
- **Inventory is not authorization.** Recording that a publish
  capability, deploy pipeline, or tracker write access exists grants
  nothing: every consequential action (publish, deploy, rollback,
  recall, deprecation, data changes) sits behind a **human
  checkpoint**, regardless of access mode. §8 records which
  environments and registries AI-initiated actions may target at all.
- **Do not execute anything in Step 00.** No tags, publishes, CI
  triggers, deploys, monitoring changes, or state-changing runs, and
  no secrets in the document. The Phase 6 report is loaded for
  *context* only. Execution starts at Step 03, behind the Step 02
  front gate.

---

## Kickoff

> Paste this line to begin. Paste the Phase 6 Deployment Readiness
> Report (or its §6.1 handoff summary and §9 determination) above it
> if convenient (knowing the release and its carried risks helps me
> ask machinery-specific questions).
```
I'm entering Phase 7 (Deployment & Evolution) on an existing project.
Please produce the Toolset Augmentation Document by walking me through
the AI capability inventory questions, then output the structured
document.
```

---

## Inventory Question Bank

Walk through the practitioner's available capabilities. Questions
adapt based on what's available in the session.

### Release Machinery and Code Access

- Does this session have access to the subject repository — read,
  and write where release preparation lands in-repo (changelog,
  version bump, tag preparation)? What is the branch and tag state?
  For multi-repo projects, confirm the Subject: release actions
  target it through its existing discipline; consumer repositories
  are Evidence Sources, never operated.
- **CI/CD access and status visibility**: can the AI see pipeline
  results directly (a GitHub connector, a CI API), or are they
  practitioner-relayed? Can it trigger workflows, or only observe?
  The Step 02 §2 machinery checks, Step 03 verification probes, and
  Step 06 runs riding CI schedules all consume this.
- **Tag and publish capability**: can the AI create tags? Who can
  publish to the registry, through what route — local publish, a CI
  release workflow, trusted publishing (OIDC)? A library subject
  like Diamonds publishes its `@diamondslab` packages through a CI
  trusted-publishing workflow: publish capability there is a
  workflow trigger plus a human approval, not a local credential.
  Record the route, not the token.
- **Registry credential posture** — posture only, never credentials:
  is 2FA enforced for publishers? Provenance or signing enabled? Who
  holds publish rights? Automation tokens or trusted publishing?
  Operated by the release discipline (Security); cited by Steps 02–04.
- **For service-shaped subjects**: what deploy tooling exists —
  pipelines or commands, target environments, health-check
  endpoints, traffic controls? Mark these rows "None applicable" for
  purely release-shaped subjects rather than forcing them.
- This machinery evidence **seeds the Step 01 §3 Deployment
  Machinery & Shape Confirmation**. Record what the machinery
  indicates; the declaration itself is Step 01's.

### Monitoring and Observability Access

- Can this session — and the future loop sessions — **read the
  observability touchpoints Phase 5 built** (per the Phase 3
  design)? Enumerate per touchpoint, not as a blanket yes: logs,
  metrics, dashboards, health endpoints. AI-readable directly, or
  practitioner-relayed (pastes, screenshots)?
- **Alerting channels**: where do alerts land (email, chat, pager,
  CI notifications)? Can AI sessions see them? An unobservable alert
  channel is a §8 friction entry now, not a mid-incident discovery.
- For release-shaped subjects, what stands in for traffic health —
  download stats, dependents, issue inflow, advisory feeds? Record
  which are queryable.
- Step 03 activates observability from day one; Step 05 runbooks
  diagnose through these touchpoints; Step 07 refreshes cite them.
  Per-touchpoint readability sets how much of Stage 2 the AI can run.

### Scheduled Scanning and Issue-Tracker Access

- What **dependency and advisory monitoring** already exists — the
  project's own scanners and audit tooling, on what schedule? Can
  the AI read the results directly, or does the practitioner return
  them? Prefer the existing tooling; the Step 06 loop rides it.
- Can Step 06 runs **ride existing schedules** (CI cron,
  dependency-bot cadence), or is each run practitioner-triggered?
  This shapes the drift-run cadence design.
- **Issue-tracker access**: read access for consumer signals — bug
  reports, integration failures, and advisories from consumers are
  drift/debt *inputs* routed through the Stage 2 loops, not
  obligations to operate consumer systems. Write access for registry
  upkeep — deprecation notices, advisories — is a consequential
  action behind checkpoints.
- Record a reliability posture for every scanner and tracker
  connection — scheduled loops inherit intermittence as scheduled
  failure.

### Documentation Access and Rendering

- Is the **frozen documentation set** (Phase 6 Step 09) accessible
  and queryable from these sessions? Operations maintain its
  queryability standard; every change triggers DOC-NN maintenance —
  the loops need to reach it.
- Is library-documentation lookup (Context7-class) or project
  knowledge with reference docs available? **These cover different
  gaps, not alternative substitutes** *(inherited from Phase 3
  v1.1 — P3-Obs-02, Cluster C2)* — record each separately. Phase 7
  uses them for registry mechanics (deprecation policies, unpublish
  windows, advisory channels — the Step 04 recall path depends on
  these realities) and for dependency-advisory context at Step 06.
- Is web fetch available for advisory feeds and registry status
  pages?
- Is **diagram/report rendering** (Mermaid or equivalent) available?
  Main uses: the Step 07 live-dashboard trend visuals and cadence
  maps; text representation is an acceptable fallback — record which
  posture applies.

### Skills, Custom AIs, Specialized Agents

- Are there Skills (in the Anthropic Agent Skills sense) loaded? The
  AI-Centric Playbook Skill, if available, carries reference depth
  on the Six Core Principles, the SDD cycle, and the building-blocks
  framework.
- Are there custom AI configurations (project-level instructions,
  custom-trained agents, role-specific configurations) active?
- Are there specialized agents (release operator, security analyst,
  monitor reviewer) set up? Delegation matters for the standing
  loops: Step 06 runs and Step 07 refreshes are recurring sessions.
- **Distinctively for Phase 7: is there a scheduled or
  recurring-agent capability** — can Stage 2 cadences run as
  scheduled sessions, or is every loop run practitioner-initiated?
  Either is workable; the Steps 05–07 cadence designs must match it.

### Upstream Artifact Access

- Is the **Phase 6 Deployment Readiness Report** (Phase 6 Step 10)
  loaded, accessible on demand, or paste-per-step — including its §5
  Carried-Risk Register? Step 01 runs blocking checks against it;
  the Stage 2 loops track the carried risks to closure.
- Is the **frozen documentation** (Phase 6 Step 09) accessible (see
  §4) — the release-state baseline?
- Is the **compliance matrix** (Phase 6 Step 04) accessible, where
  obligations exist? Step 06 §4 maintains it as the living
  compliance baseline; otherwise it is Not applicable.
- Are the **performance baselines** (Phase 6 Step 05) accessible?
  They become the production baselines Step 07 measures against.
- Is the **Phase 5 Step 10 §5 cost-model calibration table**
  accessible? Step 07 §5 continues calibrating it toward MEASURED,
  and the Step 09 Next-Cycle Package carries it forward.
- Are the **Phase 4 formal contracts** (Phase 4 Step 11), the change
  specifications (Phase 4 Step 09), and the SP/SEC/TB/DA/DOC/GOV
  registers accessible? Step 06 §2 runs conformance against them.
- Are the **Phase 3 observability touchpoint designs** and the
  **release-evidence schema design spec** (where one exists — e.g.,
  a Diamonds MC-12-style release evidence artifact) accessible?
  Step 02 §3 plans evidence emission against that schema; Step 03
  emits it.
- Phase 7 is continuous: the standing loops outlive any single
  session. Record **durable access paths** — an artifact reachable
  only by paste is a friction entry for every future loop run.

### Known Friction, Risks, and Authorization Boundaries

- Are there capabilities that are *available* but known to be flaky,
  rate-limited, or expensive? (A connector that errors on long
  content, a scanner with a rate cap, a slow CI queue.)
- **Include the "worked earlier, failed later" pattern** *(inherited
  from Phase 3 v1.1 — P3-Obs-08, Cluster C1)*: a tool that succeeded
  on first use can still return an authorization or availability
  error later. Phase 7's exposure is the highest of any phase — so
  record the standing-loop consequence alongside each friction
  (which loop degrades, and to what fallback).
- **Authorization boundaries**: which environments and registries
  may AI-initiated actions target at all, and which require
  practitioner execution? (E.g.: local workspace, read-only registry
  queries — AI; production registry publish, deprecation, production
  deploy — practitioner at a checkpoint.) Record these in §8; the
  Steps 03–05 instruction sets place checkpoints against this register.

### Execution-Mode Selection — and the Patch-Mediated Fallback

After the inventory, two declarations are made and announced in the
document's metadata.

**First, the evidence mode** — the three inherited code-access modes
and the [CONFIRM]/[AWARE]/[QUESTION] flags continue for evidence
claims, exactly as in Phases 1–6.

**Second, the execution mode, declared per execution-dependent
loop** (Steps 03–07):

| Execution Mode | How the loop runs | When to select |
|----------------|-------------------|----------------|
| **Direct execution** | The AI drives the machinery through tool connections (CI status and triggers, registry queries, monitor reads, scanner runs), pausing at every human checkpoint | Tool connections to that loop's machinery exist and are consistently usable |
| **Practitioner-mediated (patch-mediated fallback)** | The AI produces the exact commands and ordered steps; the practitioner executes them and pastes back full output | No direct connection for that loop — the standing fallback; mechanics and round-trip recorded per loop |

> **Unlike the Phase 5 write-mode gate, neither mode blocks
> Phase 7** — the practitioner-mediated fallback is always
> available. But it must be *concrete* per loop: how steps are
> relayed, how output returns, the expected round-trip — a standing
> loop with vague fallback mechanics silently stops running. In both
> modes every consequential action sits behind a human checkpoint:
> the mode changes who types, never who authorizes.

---

## Output Format

When the inventory is complete, produce the Toolset Augmentation
Document using this structure.

---
```markdown
# Toolset Augmentation Document — Phase 7 (Deployment & Evolution)

**Project:** [subject name and version]
**Phase 7 Entry Date:** [date]
**Practitioner:** [name or role]
**AI Model (operating configuration):** [model and version]
**Phase 6 Deployment Readiness Report:** [version / date / §9 determination]
**Code-Access Mode (evidence claims):** [Search-primary / Hybrid with explicit flags]
**Execution Mode (per-loop summary):** [Direct execution / Practitioner-mediated / Mixed — see §9]
**Deployment-Shape Evidence (preliminary):** [release-shaped / service-shaped / both indications — declared at Step 01 §3]
**Status:** Living document — amendments captured in §7 for the life of the system

> ⚠️ This document is **living — and, uniquely, it never retires**.
> Phase 7 is continuous: the Stage 2–3 standing loops consult this
> document on every run. When AI capabilities shift (a connector
> activates, a scheduled scanner loses access, a publish route
> changes), add a dated entry to §7 — do not produce a new document.

> ⚠️ Inventory is not authorization. Publish, deploy, rollback,
> recall, deprecation, and data changes sit behind human checkpoints
> in every instruction set, in both execution modes. §8 records
> which environments and registries AI-initiated actions may target.
> No credentials, tokens, or secrets appear here — posture only.

> ⚠️ [Include this note only when one or more loops are
> Practitioner-mediated:] The following loops run
> practitioner-mediated: [list] — the AI produces exact commands;
> the practitioner executes and pastes back full output. Mechanics
> and round-trips are in §9; the Steps 05–07 cadences reflect them.

---

## §1 — Release Machinery & Code Access

| Capability | Available? | Route / Path | Notes |
|-----------|-----------|--------------|-------|
| Repository read | [Yes/No] | | [Subject vs Evidence Sources] |
| Repository write (changelog, version bump, tag prep) | [Yes/No] | | |
| Git tag creation | [Yes/No] | | |
| CI/CD status visibility | [Yes/No] | | [AI-visible or practitioner-relayed] |
| CI/CD workflow trigger | [Yes/No] | | [observe-only vs trigger] |
| Publish capability | [Yes/No] | [route: local / CI workflow / trusted publishing] | [who can publish — behind checkpoint] |
| Registry credential posture | [recorded] | | [2FA / provenance/signing / publish-rights holders — POSTURE ONLY, never credentials] |
| Deploy tooling (service-shaped) | [Yes/No/N.A.] | | [pipelines, environments, health checks, traffic controls — "None applicable" for purely release-shaped subjects] |

*Shape evidence for Step 01 §3:* [1–2 sentences on what the
machinery indicates — release-shaped, service-shaped, or both.]

## §2 — Monitoring & Observability Access

| Touchpoint / Channel | AI-Readable? | Access Route | Notes |
|---------------------|-------------|--------------|-------|
| [Phase 5-built touchpoint, per Phase 3 design — one row each] | [Yes/No] | | |
| Log access | [Yes/No] | | |
| Metrics / dashboards | [Yes/No] | | |
| Alerting channels | [Yes/No] | [where alerts land] | [AI-visible or practitioner-relayed] |
| Release-health proxies (downloads, dependents, issue inflow) | [Yes/No/N.A.] | | [release-shaped subjects] |

## §3 — Scanning & Tracker Tooling

| Capability | Available? | Schedule / Invocation | Reliability | Notes |
|-----------|-----------|----------------------|-------------|-------|
| Dependency / advisory scanning (existing tooling) | [Yes/No] | [schedule; rideable by Step 06?] | [on-demand/warm-up/intermittent] | |
| Security scanners (existing) | [Yes/No] | | | [project's own tooling preferred] |
| Issue-tracker read (consumer signals) | [Yes/No] | | | |
| Issue-tracker write (advisories, deprecation notices) | [Yes/No] | | | [consequential — behind checkpoint] |
| Advisory feeds / registry status | [Yes/No] | | | |

## §4 — Documentation Access & Rendering

| Capability | Available? | Anticipated Use in Phase 7 |
|-----------|-----------|---------------------------|
| Frozen documentation set (Phase 6 Step 09) | [Yes/No] | [release-state baseline; queryability standard maintained; DOC-NN maintenance on change] |
| Context7 / library-doc lookup | [Yes/No] | [registry mechanics — deprecation policies, unpublish windows, advisory channels — for the Step 04 recall path; dependency advisories at Step 06] |
| Project knowledge with reference docs | [Yes/No] | [different gap from library lookup — record separately] |
| Web fetch | [Yes/No] | |
| Diagram / report rendering (Mermaid etc.) | [Yes/No] | [Step 07 dashboard trends and cadence maps; text fallback acceptable] |

## §5 — Skills, Custom AIs, Specialized Agents

| Capability | Active? | Description |
|-----------|---------|-------------|
| AI-Centric Playbook Skill | [Yes/No] | |
| Project-level instructions | [Yes/No] | |
| Specialized agents | [Yes/No] | [delegation for recurring loop sessions] |
| Scheduled / recurring-agent capability | [Yes/No] | [can Stage 2 cadences run as scheduled sessions, or practitioner-initiated per run?] |
| Other Skills loaded | [Yes/No] | |

## §6 — Upstream Artifact Access

| Artifact | Loaded? | Access Path |
|---------|--------|-------------|
| Phase 6 Deployment Readiness Report (Phase 6 Step 10), incl. §5 Carried-Risk Register | [Yes/No] | |
| Frozen documentation (Phase 6 Step 09) | [Yes/No] | |
| Compliance matrix (Phase 6 Step 04 — conditional) | [Yes/No/N.A.] | |
| Performance baselines (Phase 6 Step 05) | [Yes/No] | |
| Cost-model calibration table (Phase 5 Step 10 §5) | [Yes/No] | |
| Phase 4 formal contracts (Phase 4 Step 11), change specifications (Phase 4 Step 09), SP/SEC/TB/DA/DOC/GOV registers | [Yes/No] | |
| Phase 3 observability touchpoint designs + release-evidence schema design spec (where one exists, e.g. MC-12) | [Yes/No] | |

*Durable-access note:* [which rows are reachable by future loop
sessions without a paste — paste-only artifacts are §8 friction.]

## §7 — Mid-Phase Amendments

*Append-only, for the life of the system. When a capability shifts,
add a dated entry below. Do not edit prior entries.*

| Date | Step / Loop | Capability | Change | Impact |
|------|------------|-----------|--------|--------|
| | | | | |

*Example entry (illustrating the "worked earlier, failed later"
pattern inherited from Phase 3 v1.1, applied to a standing loop):*

| [date] | Step 06 (scheduled run) | Scan results readable via CI | Read directly for the first two monthly runs; the CI results API began returning authorization errors mid-quarter | Step 06 runs shifted practitioner-triggered with pasted scan output until access is restored; run schedule unchanged; §8 friction entry updated; affected Drift Detection Reports note the evidence route per run |

## §8 — Known Friction & Authorization Boundaries

### §8.1 Known Friction Points

| Capability | Friction | Standing-Loop Consequence | Workaround |
|-----------|---------|---------------------------|-----------|
| | | [which loop degrades, to what fallback] | |

### §8.2 Authorization Boundaries

*Which environments and registries AI-initiated actions may target.
Every instruction set (Steps 03–05) places its human checkpoints
against this register.*

| Action Class | AI May Target | Practitioner-Only | Notes |
|-------------|--------------|-------------------|-------|
| Repository writes (tags, changelog) | | | |
| CI/CD workflow triggers | | | |
| Registry actions (publish, deprecate, advisory) | | | |
| Deploy / traffic actions (service-shaped) | | | [N.A. for purely release-shaped subjects] |
| Issue-tracker writes | | | |

## §9 — Execution-Mode Rationale

| Execution-Dependent Loop | Mode | Fallback Mechanics (if practitioner-mediated) | Cadence Cost |
|-------------------------|------|----------------------------------------------|--------------|
| Step 03 — Deployment execution | [Direct / Practitioner-mediated] | [how steps are relayed; how output returns; round-trip] | |
| Step 04 — Rollback & recall (readied) | | | |
| Step 05 — Runbook execution | | | |
| Step 06 — Scheduled drift & compliance runs | | | |
| Step 07 — Scorecard refresh data pulls | | | |

[1–3 sentences explaining the evidence-mode and per-loop
execution-mode selections, what they imply for the Stage 1 release
steps and the Stage 2 loop cadences, and what would trigger a mode
change (recorded as a §7 amendment). Note explicitly that human
checkpoints before consequential actions apply identically in both
modes.]

---

## Version

v1.0 (initial Phase 7 capability inventory; living thereafter — for
the life of the system)
```

---

## Evaluation Checklist

Before this artifact is accepted as complete, verify:

- [ ] All nine sections (§1–§9) are populated; sections with no
      relevant capabilities are marked "None applicable" rather than
      omitted
- [ ] The evidence mode is announced in the metadata, and §9
      declares an execution mode for **every** execution-dependent
      loop (Steps 03–07) — with concrete patch-mediated fallback
      mechanics wherever direct execution is unavailable
- [ ] §1 records the tag/publish capability by route (local / CI
      workflow / trusted publishing) and the registry credential
      **posture** (2FA, provenance/signing, who can publish) — and
      no credentials, tokens, or secrets appear anywhere
- [ ] §1's machinery evidence is sufficient to seed the Step 01 §3
      shape declaration — indications recorded, no shape declared
      here
- [ ] §2 records per-touchpoint readability of the Phase 5-built
      observability and where alerts land — not a blanket yes — and
      distinguishes AI-readable from practitioner-relayed
- [ ] §3 rows carry reliability postures (usable-on-demand /
      needs-warm-up / intermittent); whether Step 06 can ride
      existing scan schedules is recorded; tracker read and write
      access are distinguished, writes noted as checkpoint-guarded
- [ ] Upstream artifact access (§6) is explicit for all rows —
      Deployment Readiness Report with Carried-Risk Register, frozen
      docs, compliance matrix (or N.A.), performance baselines,
      calibration table, Phase 4 contracts and registers, Phase 3
      touchpoints and release-evidence schema — with durable access
      for future loop sessions noted, not just this session's state
- [ ] §7 starts empty (or with prior amendments if re-entering
      Phase 7 from an earlier session) — amendments are added during
      operation, not pre-populated
- [ ] §8.2 records authorization boundaries explicitly: which
      environments and registries AI-initiated actions may target,
      and which action classes are practitioner-only
- [ ] Known friction (§8.1) is captured for any flaky/rate-limited/
      expensive capability — including any "worked earlier, failed
      later" history — with the standing-loop consequence named
- [ ] The document is version-stamped v1.0 (or higher if re-entering
      a previous Phase 7 run) and marked living for the system's life
- [ ] No release, registry, CI, deploy, or monitoring state has been
      changed — Step 00 is inventory only, and inventorying a
      capability is distinct from authorization to use it
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)

---

*Part of the Phase 7 (Existing Projects) Deployment & Evolution Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `deployment-evolution.existing-project.instructions.md`*
*Next step: `step-01-phase-6-input-validation.prompt.md`*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Phase 7 Building Block Discovery prompt, structured as the Phase 7 sibling of the existing-track step-00 pattern: the same nine-section Toolset Augmentation Document, living-document §7 amendment discipline, reliability postures, and the inherited attributions in place (living-not-snapshot from Phase 2 v1.1 P2-Obs-06; present-vs-consistently-usable and worked-earlier-failed-later from Phase 3 v1.1 Cluster C1; project-knowledge-vs-library-lookup different gaps from P3-Obs-02). Phase 7 flavoring reflects the continuous phase: the document never retires — the Stage 2–3 standing loops consult and amend it for the life of the system, making §7 amendments weightier than in any prior phase and intermittent tooling a scheduled-failure risk. New inventory categories: release machinery (§1 — CI/CD access and status visibility, tag/publish capability by route, registry credential posture recorded without ever printing credentials, service-shaped deploy tooling; evidence seeds the Step 01 §3 shape declaration), monitoring and observability access (§2 — per-touchpoint readability of the Phase 5-built instrumentation, alerting channels), scanning and tracker tooling with a reliability column (§3), and authorization boundaries (§8.2 — which environments/registries AI-initiated actions may target). Execution modes are declared per execution-dependent loop (Steps 03–07) with concrete patch-mediated fallback mechanics; unlike the Phase 5 write gate, no mode blocks the phase, and human checkpoints apply identically in both modes. §6 spans the full upstream reach: the Phase 6 Deployment Readiness Report with Carried-Risk Register, frozen docs, compliance matrix, performance baselines, the Phase 5 Step 10 §5 calibration table, Phase 4 contracts and registers, and the Phase 3 touchpoints and release-evidence schema design spec (e.g. MC-12). Nothing is executed at Step 00 — execution starts at Step 03, behind the Step 02 front gate. |
