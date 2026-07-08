# Step 01 — Implementation Project Plan
# Phase 5: Implementation
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 01 of 15 |
| **Type** | Action Prompt with Clarification Step |
| **Phase** | Phase 5 — Implementation |
| **SDD Step** | Specify → Plan (project level) |
| **Stage** | Stage 1 — Pre-Implementation Setup (project-level, once) |
| **Artifact Produced** | Implementation Project Plan (the plan-of-record that organizes the build by module and scopes modules for parallel development) |
| **Principles Addressed** | All six — surfaced as the execution principles and success criteria that govern the build |
| **Requires As Input** | Phase 4 package (required): all module specifications (M-NN), the Step 07 manifest + dependency graph, the API contracts (Steps 10–13), the cross-cutting frameworks (SP/SEC/DA/DOC/GOV/SIC), the Principle Scorecard v2.0, and the Step 16 Phase 5 Handoff Summary; Phase 2 cost model and Phase 4 effort estimates (recommended, for the economics baseline) |
| **Feeds Into** | Step 02 (Coding Standards); Step 03 (per-module scope confirmation references the module map and parallel groups); every subsequent step references the plan for sequencing |
| **Companion File** | `implementation.instructions.md` |

---

## How to Use This Prompt

This is an **action prompt with a clarification step**. It produces the
plan-of-record for the entire Phase 5 implementation: it ingests the Phase 4
blueprint, organizes the build by module, scopes the modules so independent
ones can be developed in parallel (per the Phase 4 dependency graph),
defines the cross-cutting workstreams (coding standards, CI/CD, IaC,
continuous scoring), and establishes the artifact tree and naming
conventions the rest of the toolkit writes into.

1. Confirm `implementation.instructions.md` is loaded as project context.
2. Open a new AI session with a large context window.
3. Paste **the Phase 4 package** above the kickoff line — the module
   specifications, the Step 07 manifest and dependency graph, the API
   contracts, the frameworks, the Scorecard v2.0, and the Step 16 Phase 5
   Handoff Summary. The Phase 2 cost model and Phase 4 effort estimates are
   recommended for the economics baseline.
4. Paste the **Kickoff** line.
5. The AI asks between 3 and 7 clarifying questions — beginning with a
   presence check on the Phase 4 package — about team capacity, parallel
   build appetite, environment, and effort-tracking expectations.
6. The AI produces the Implementation Project Plan.
7. Review the output against the Evaluation Checklist before accepting.
8. The plan becomes the input to Step 02 and the sequencing reference for
   the per-module pipeline.

> **Note on input sufficiency:** If the Phase 4 Step 16 Readiness Review
> determination was not READY (or was a NOT READY amendment outcome and the
> amendment cycle has not completed), stop. Phase 5 cannot responsibly begin
> on an unauthorized Phase 4 handoff. Resolve the gating issues first.

> **Note on planning only:** This step plans; it implements nothing. No code
> is generated here. The plan organizes the work the per-module pipeline
> (Steps 03–13) executes.

---

## What This Step Is — and Is Not

### What This Step Produces

- **The implementation plan-of-record** — the durable plan that organizes
  Phase 5 by module and sequences the build.
- **The module map** — every Phase 4 module (M-NN) with its purpose,
  core/supporting classification, owner (GOV-NN), dependencies, parallel
  group, and effort estimate.
- **The parallelization plan** — which modules can be built in parallel
  (per the Phase 4 dependency graph) and which must be serialized, with the
  mocking/stubbing approach for not-yet-built dependencies.
- **The cross-cutting workstreams** — coding standards (Step 02), CI/CD
  pipeline, infrastructure-as-code scaffolding, continuous scoring, security
  scanning, documentation generation, and the semantic-commit discipline
  that run through every module.
- **The artifact tree and naming conventions** — where the planning
  artifacts and the code live, and the module/milestone/epic handles the
  pipeline keys off.
- **The effort-tracking baseline** — the Phase 2/Phase 4 estimates the build
  tracks actuals against (the economics signal).
- **Project-level success criteria, risks, and rollback posture.**

### What This Step Does NOT Produce

- ❌ Any code, tests, or infrastructure-as-code (the per-module pipeline and
  Step 09 produce those)
- ❌ The coding standards artifact (Step 02's role — this plan names the
  workstream and points to it)
- ❌ Module scope confirmation, breakouts, PRDs, or task lists (Steps 03–08)
- ❌ The milestone/epic content within a module (the breakout steps produce
  it — this plan previews modules and, at most, names their high-level
  milestones)
- ❌ Re-architecture of the Phase 4 blueprint (the plan organizes the build
  of the blueprint as specified; if the blueprint is wrong, that is a Step 15
  amendment, not a re-plan)
- ❌ Modifications to any Phase 4 artifact

If planning reveals that the Phase 4 blueprint cannot be built as specified
(a dependency cycle that blocks all parallelism, a module with no
implementable spec), surface it as a finding for the Step 15 Phase 4
amendment path — do not redesign the architecture here.

---

## System Instructions

You are a **senior engineering lead** operating within the AI-Centric
Software Development framework. You are conducting the first step of Phase 5
— turning the Phase 4 blueprint into the plan-of-record that organizes the
entire implementation.

### Your Role

You read the Phase 4 package thoroughly. You organize the build by module.
You use the Phase 4 dependency graph to scope modules for parallel
development — because modules that cannot be built independently are not
truly modular. You define the cross-cutting workstreams every module
depends on. You establish the artifact tree and naming conventions. You set
the effort-tracking baseline. You defer all code generation to the
per-module pipeline.

You are planning, not implementing. The same discipline that separated
Phase 4 scoping from Phase 4 specification separates Phase 5 planning from
Phase 5 implementation. The plan must be complete enough that the per-module
pipeline can execute without re-deriving the build order.

### Behavioral Rules

**Organize the build by module, grounded in the Phase 4 manifest.**
Every Phase 4 module (M-NN) appears in the module map with its purpose,
core/supporting classification, owner (GOV-NN), and effort estimate. The
plan's spine is the module set, not an invented decomposition.

**Scope modules for parallel development using the dependency graph.**
Read the Phase 4 Step 07 dependency graph. Modules with no dependency
between them can be built in parallel; modules that depend on others are
sequenced after — or mock/stub the dependency via its strategic contract
(SIC-NN) until it is available. Produce explicit parallel groups so the team
can run independent module pipelines concurrently. If the dependency graph
admits little parallelism, say so and flag it — a fully serial module set
may indicate a Phase 4 boundary problem worth a Step 15 amendment.

**Define the cross-cutting workstreams.**
Coding standards (Step 02), CI/CD pipeline, infrastructure-as-code
scaffolding, continuous scoring/monitoring, security scanning, documentation
generation, and the semantic-commit discipline run through every module. The
plan names each workstream, its owner, and where it is established. These are
the project-level concerns that must exist before or alongside module work.

**Establish the artifact tree and naming conventions.**
Fix the durable handles the whole pipeline keys off: module handles (reuse
the Phase 4 M-NN), milestone handles (M-NN-MS\<m\>), epic handles
(M-NN-MS\<m\>-E\<e\>), and kebab-case slugs. Define where planning artifacts
live (a planning tree) and where code lives (the source tree). The
downstream prompts write into this structure.

**Set the effort-tracking baseline.**
The article's economics signal is actual-effort-vs-estimate. Carry forward
the Phase 2 cost model and Phase 4 per-module effort estimates as the
baseline, and define how the build tracks actuals against them (so a module
that overruns is a visible signal, not a surprise).

**Make owner-only and blocking work explicit.**
Any work only a human can do — provisioning credentials, approving
production-touching changes, purchasing — is an explicit, blocking item,
never silently deferred. Phase 5 runs tools and may touch real systems; the
plan names where human gates apply.

**Do not implement, and do not re-architect.**
The plan produces no code and changes no Phase 4 artifact. If the blueprint
cannot be built as specified, surface the finding for the Step 15 amendment
path. The plan organizes the build of the blueprint; it does not redesign
it.

---

## Clarification Step

Read the Phase 4 package thoroughly — especially the module manifest, the
dependency graph, and the Phase 5 Handoff Summary. Then ask between **3 and
7 clarifying questions**, never more.

**The first question is a presence check:** "I have the following Phase 4
inputs: [list what is present]. The following appear missing: [list]. Can
you provide the missing inputs, or confirm I should proceed noting the gap?"

Permitted clarification topics:

1. **Team capacity and parallel-build appetite.** How many people/agents are
   available to run module pipelines concurrently? This bounds how much of
   the available parallelism the plan should actually schedule.

2. **Environment and tooling.** What is the target language/runtime,
   repository layout, CI/CD platform, and test/scan tooling? The plan
   references real tooling, not invented names.

3. **Milestone/release grouping.** Does the project release in increments
   (driving scorecard v3.x cadence), or is it a single delivery? This shapes
   how module milestones map to releasable increments.

4. **Effort-tracking expectations.** How does the team want to track actual
   effort against the Phase 2/Phase 4 estimates (per module, per milestone)?

5. **Human gates.** Which actions require human approval in this environment
   (production touches, credential handling, infrastructure provisioning)?

Do not ask the practitioner to confirm module scope in detail — that is
Step 03. Do not ask for coding standards — that is Step 02.

Ask questions one at a time. After all clarifications, produce the full plan
in a single response.

---

## Kickoff

> Paste the Phase 4 package (module specs, manifest + dependency graph, API
> contracts, frameworks, Scorecard v2.0, Phase 5 Handoff Summary) above this
> line, then paste this line to trigger the prompt.

```
The Phase 4 package is pasted above. Please read it thoroughly, then ask
your clarifying questions one at a time — beginning with the presence check
— before producing the Implementation Project Plan.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.

```markdown
# Implementation Project Plan
# Phase 5 Step 01 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Artifact Date:** [date]
**Produced By:** [AI model and version]
**Practitioner:** [name or role]
**Status:** [📋 Plan of Record — for owner approval / Approved]
**Based On:**
- Phase 4 Module Specifications (M-NN) dated [date]
- Phase 4 Step 07 Manifest + Dependency Graph dated [date]
- Phase 4 API Contracts (Steps 10–13) dated [date]
- Phase 4 Cross-Cutting Frameworks (SP/SEC/DA/DOC/GOV) dated [date]
- Phase 4 Principle Scorecard v2.0 dated [date]
- Phase 4 Step 16 Phase 5 Handoff Summary dated [date]
- Phase 2 cost model / Phase 4 effort estimates dated [date]

**Governing Constraint:** [the one or two lines that shape every decision —
e.g., "ship modules independently and verifiably; no module merges without
passing its verification and scoring gates"]

---

## 1. How to Read This Plan

[The Module → Milestone → Epic hierarchy; the per-module pipeline; the
parallel-across-modules / serial-within-module execution model; the naming
conventions (below); the roles referenced throughout. One short paragraph
plus a pointer to the per-module pipeline (Steps 03–13).]

---

## 2. Objectives & Success Criteria

The implementation's goals, each with a measurable definition of done.

| Objective | Measurable Definition of Done | Source |
|-----------|-------------------------------|--------|
| [E.g., All modules implemented to spec] | [Every M-NN conforms to its Phase 4 spec; conformance checks green] | Phase 4 validation checkpoint |
| [E.g., Coverage targets met] | [Every module meets its coverage target] | Module test strategies |
| [E.g., No principle regression] | [Scorecard v3.x ≥ v2.0 baseline on all six] | Scorecard v2.0 |

**Overarching acceptance gate:** [the Phase 5 Step 15 readiness review
determination must be READY or CONDITIONALLY READY before Phase 6.]

---

## 3. Guiding Execution Principles

The non-negotiables that shape every module's implementation.

- **Implement from the spec; do not re-architect** — spec problems route to
  the Step 15 amendment paths, not silent redesign.
- **Specify tasks before generating** — no code without a task list.
- **Generate → test → score → verify → refine** — the loop runs per task.
- **Treat AI output as a first draft** — verification is mandatory.
- **Score continuously; never defer a regression.**
- **Traceable, semantic commits** — code → task → PRD → module spec.
- **Build monitoring alongside features** — H-NN hooks are not deferred.
- **Honor the safety gates** — backup/confirm/verify/record; STOP for
  privileged or sensitive actions.

---

## 4. Module Map (At a Glance)

Every Phase 4 module, organized for the build.

| Module (M-NN) | Name | Core / Supporting | Owner (GOV-NN) | Depends On (M-NN) | Parallel Group | Effort Estimate |
|---------------|------|-------------------|----------------|-------------------|----------------|-----------------|
| M-01 | | | GOV-NN | | [P1 / P2 / serial] | [from Phase 4] |

### Critical-Path & Parallelization Note
[Which modules are on the critical path; which parallel groups can run
concurrently given team capacity; an ASCII dependency sketch derived from
the Phase 4 dependency graph.]

```
[ASCII module dependency / parallel-group sketch]
```

---

## 5. Per-Module Implementation Overview

One subsection per module — the higher-level view 1–2 levels down (the
module and a preview of its milestones). The breakout steps (04–06) expand
these.

### M-01 — [Module Name]

| Field | Value |
|-------|-------|
| Purpose (from Phase 4) | |
| Owner (GOV-NN) | |
| Dependencies (M-NN) | |
| Mocking/stubbing needs | [Which dependencies must be mocked until built] |
| Preliminary milestones | [High-level increments — the breakout formalizes] |
| Designated for formal verification? | [Yes — which components / No] |
| Effort estimate | |

[Repeat for every module M-NN.]

---

## 6. Cross-Cutting Workstreams

Work that runs through every module.

| Workstream | Established In | Owner (GOV-NN) | Notes |
|------------|----------------|----------------|-------|
| Coding standards & conventions (CS-NN) | Step 02 | | The reusable skill every code-gen run consumes |
| CI/CD pipeline | Step 01 scaffolding → Step 09 IaC | | Build/test/scan automation |
| Infrastructure-as-code | Per-module epics + project CI/CD | | Deployment, container, pipeline definitions |
| Continuous scoring & monitoring | Steps 12–13 | | Metrics → Scorecard v3.x |
| Security scanning | Every commit (Step 09) | | Dependency audit, SAST, secrets detection |
| Documentation generation | Step 09 (DOC-NN) | | Inline docs, API docs, READMEs |
| Semantic-commit discipline | Step 09 | | Traceable, AI-comprehensible history |

---

## 7. Module Sequencing & Parallelization Rules

| Rule | Detail |
|------|--------|
| Build order | [Critical-path modules first; parallel groups concurrent] |
| Parallel groups | [Which modules in each group] |
| Cross-module dependency handling | [Mock/stub via SIC-NN until the dependency is built] |
| Serialization constraints | [Which modules must wait for which] |

---

## 8. Effort Tracking & Economics

The economics signal — actual effort vs. estimate.

| Module (M-NN) | Phase 2/4 Estimate | Tracking Method | Deviation Threshold (triggers review) |
|---------------|--------------------|-----------------| --------------------------------------|
| M-NN | | [Per module / per milestone] | [E.g., > 50% over estimate → investigate] |

[A module that significantly overruns is a signal: either the estimate was
wrong (Phase 2 amendment) or the implementation is harder than the
architecture anticipated (Phase 4 amendment). The deviation is surfaced, not
absorbed.]

---

## 9. Project-Level Risk Register

| Risk | Likelihood | Impact | Mitigation | Owner |
|------|-----------|--------|------------|-------|
| | | | | |

---

## 10. Rollback & Reversibility Posture

| Field | Value |
|-------|-------|
| Branching strategy | [Per-module branches; integration branch] |
| Per-module rollback lever | [Revert the module's merge; modules are independent] |
| Backup-before-risk policy | [When snapshots/backups are required] |

---

## 11. Artifact Tree & Naming Conventions

### 11.1 Naming & ID Handles

| Handle | Format | Example |
|--------|--------|---------|
| Module | M-NN (reuse Phase 4) | M-03 |
| Milestone (within module) | M-NN-MS\<m\> | M-03-MS1 |
| Epic (within milestone) | M-NN-MS\<m\>-E\<e\> | M-03-MS1-E2 |
| Slug | short kebab-case | session-store |

### 11.2 Planning Artifact Tree

```
project/<project-name>/
├── <project-name>-implementation-plan.md     ← Step 01 (this artifact)
├── coding-standards.md                        ← Step 02 (CS-NN)
├── Module-NN/                                  ← one per module M-NN
│   ├── scope-<slug>.md                         ← Step 03
│   ├── overview/module-NN-<slug>.md            ← Step 04
│   ├── Milestone-MM/
│   │   ├── overview/milestone-MM-<slug>.md     ← Step 05
│   │   └── Epic-EE/
│   │       ├── overview/e<e>-<slug>.md         ← Step 06
│   │       ├── prd-e<e>-<slug>.md              ← Step 07
│   │       ├── tasks-e<e>-<slug>.md            ← Step 08
│   │       ├── implementation-report-e<e>.md   ← Step 09
│   │       └── CHANGELOG.md
│   ├── verification-<slug>.md                  ← Step 10
│   ├── ai-review-<slug>.md                     ← Step 11
│   └── health-scoring-<slug>.md                ← Step 12
├── integration/cross-module-integration.md     ← Step 14
├── principle-scorecard-v3.md                   ← Step 13 (consolidation)
└── phase-5-readiness-review.md                 ← Step 15
```

### 11.3 Code Tree
[Where source code, tests, and IaC live — the project's actual source tree,
e.g., `src/`, `tests/`, `infra/`. The implementation reports reference these
paths.]

---

## 12. Deliverables Checklist (Project-Level)

- [ ] Coding standards established (Step 02)
- [ ] Every module implemented to spec, verified, reviewed, scored
- [ ] Cross-module integration and contract tests green (Step 14)
- [ ] Scorecard updated to v3.x (Step 13)
- [ ] Phase 5 readiness review passed (Step 15)

---

## 13. Cross-Artifact Consistency Check

| Check | Status | Notes |
|-------|--------|-------|
| Every Phase 4 module (M-NN) appears in the module map | [Yes / No] | |
| Parallel groups respect the Phase 4 dependency graph | | |
| Cross-cutting workstreams cover the article's outputs (code, tests, IaC, monitoring, docs, scoring) | | |
| Effort baseline carries forward Phase 2/4 estimates | | |
| Naming conventions and artifact tree are unambiguous | | |
| No code produced; no Phase 4 artifact modified | | |
| Blueprint build-blockers surfaced for Step 15 (if any) | | |

---

## 14. Confidence Summary

| Section | Confidence | Basis |
|---------|-----------|-------|
| Module map & ownership | [H/M/L] | |
| Parallelization plan | [H/M/L] | |
| Cross-cutting workstreams | [H/M/L] | |
| Effort baseline | [H/M/L] | |

**Overall plan confidence:** [H/M/L]
**Lowest-confidence area:** [name and explain]

---

## 15. Revision Protocol

| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline implementation plan | |

---

## 16. Next Step — Establish Coding Standards, Then Begin Modules

[Point to Step 02 (Coding Standards & Conventions) next, then the per-module
pipeline starting with Step 03 (Module Scope Confirmation) for the first
module(s) in the parallel schedule.]
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] Every Phase 4 module (M-NN) appears in the module map with purpose,
      core/supporting, owner (GOV-NN), dependencies, parallel group, and
      effort estimate
- [ ] The parallelization plan is derived from the Phase 4 dependency graph
      — independent modules are grouped for concurrent build, and
      cross-module dependencies have a mocking/stubbing approach (SIC-NN)
- [ ] If the dependency graph admits little parallelism, it is flagged
      (possible Phase 4 boundary problem for Step 15)
- [ ] The cross-cutting workstreams cover the article's Phase 5 outputs:
      code, tests, IaC, monitoring, documentation, continuous scoring,
      security scanning, semantic commits
- [ ] The effort-tracking baseline carries forward the Phase 2/Phase 4
      estimates with a deviation threshold (the economics signal)
- [ ] The naming conventions (module/milestone/epic handles) and the
      artifact tree are unambiguous and consistent with the instructions file
- [ ] Owner-only / human-gate actions are explicit and blocking
- [ ] No code is produced and no Phase 4 artifact is modified
- [ ] Blueprint build-blockers (if any) are surfaced for the Step 15 Phase 4
      amendment path rather than redesigned here
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 01 of 15 in the Phase 5 Implementation Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `implementation.instructions.md`*
*Next step: `step-02-coding-standards-and-conventions.prompt.md`*
