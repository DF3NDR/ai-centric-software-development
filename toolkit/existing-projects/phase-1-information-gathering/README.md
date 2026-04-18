# Phase 1: Information Gathering (Existing Projects) — Tool Set
## AI-Centric Software Development Playbook

---

## Overview

This directory contains the complete tool set for **Phase 1:
Information Gathering** of the AI-Centric Software Development
Playbook, **adapted for existing projects** rather than greenfield
work. It is the first phase of the improvement-cycle application of
the seven-phase framework.

Phase 1 for existing projects answers the questions every subsequent
improvement phase depends on: what the system actually is today
(stack, architecture, deployment), how it actually behaves in
production (reliability, performance, cost, change velocity), what
the improvement must preserve and what it must change, what risks
and technical debt bound the work, and which components should be
kept, upgraded, replaced, or retired. Done well, it gives the team
a shared, evidence-grounded picture of the current state and a
sharpened improvement objective before any remediation plan is
drafted. Done poorly — or skipped — the improvement plan collides
with undocumented reality somewhere in Phase 4 or Phase 5, where
correction costs weeks instead of hours.

The primary output of this phase is the **Current-State Information
Report** — a structured document synthesized from five research
artifacts, designed for both human decision-making and AI consumption
in every subsequent phase. It is the handoff artifact to Phase 2
(Analysis & Improvement Planning).

---

## Relationship to the Greenfield Tool Set

This tool set is the brownfield sibling of
`toolkit/phase-01-information-gathering-toolset/` (greenfield). The
SDD cycle, the six Core Principles, the phase-gate discipline, and
the synthesis-plus-scorecard pattern are identical. What changes is
**where the evidence comes from and what questions are asked**.

| Dimension | Greenfield | Existing Projects |
|-----------|-----------|-------------------|
| Primary evidence source | Outside world — ecosystems, markets, compliance regimes | Inside the team — codebase, deployment, telemetry, incidents |
| Core question | *"What should we choose?"* | *"What do we have, where are we, and what must change?"* |
| Tech artifact focus | Technology landscape (what exists in the ecosystem) | Current-state technology & architecture (what the system is built from) |
| Second artifact focus | Competitive & market scan (what others have built) | Operational & performance baseline (how the system actually behaves) |
| Requirements artifact | User needs, business goals, non-negotiables for a new build | Must-keep / must-change / nice-to-improve / incidental for an improvement |
| Risk artifact categories | Compliance, security, hard constraints, project/operational | ...plus **technical debt** as a first-class category |
| Components artifact disposition | Adopt / Adapt / Reference only / Do not use | Keep / Upgrade / Replace / Retire (for existing) + Adoption (for candidates) |
| Compliance treatment | Does this apply? | Does this apply *and* is it enforced end-to-end vs. merely claimed? |

Practitioners familiar with the greenfield tool set will find the
same muscle memory here — the same interview rhythm, the same file
naming convention, the same synthesis-plus-scorecard pattern. The
differences are deliberate: they reflect the fundamentally different
shape of evidence available for an existing system.

---

## Framework Context

This tool set is part of the
[AI-Centric Software Development Playbook](../../README.md),
a practitioner's framework for small teams (1–5 people) that use AI
tools to deliver what large organizations once required.

Three framework concepts are essential to understanding how this
tool set works.

### The Six Core Principles

Every artifact in this tool set is filtered through six principles
that travel with the project from Phase 1 through deployment. The
first four define *what you are optimizing for*. The last two
define *how you know you are getting it right*.

Applied to existing-project work, they ask:

| Principle | What It Asks in Phase 1 (Existing Projects) |
|-----------|---------------------------------------------|
| **Security** | What are the known vulnerabilities in the current dependency graph? What compliance regimes apply, and which are enforced end-to-end vs. claimed on paper? What is the historical incident pattern? |
| **Maintainability** | How accurate is the current documentation vs. the code? What is the measured test coverage? What technical debt has accumulated? How steep is the contributor ramp-up? |
| **Economics** | What does the system cost to run today (infrastructure, licensing, labor)? What does it cost to change (DORA metrics)? Where is vendor lock-in concentrated? |
| **Operations** | How is the system actually deployed today? What is observable, what is not? What are the known scaling limits and integration contracts? |
| **Scoring & Metrics** | What measured baselines exist for the dimensions the improvement is intended to move? Where are the measurement gaps? |
| **Correctness Verification** | Are claims about the current system verified against code / config / telemetry, or repeated from memory? Are documented-vs-observed divergences surfaced? Are discovery gaps explicit? |

The principles are not evaluated at the end of Phase 1. They shape
what is discovered, how findings are evaluated, and what questions
are asked — from the first interview through the final synthesis.

### Specification Driven Development (SDD)

All work in this phase follows the SDD cycle — the same iterative,
specification-first methodology that drives every phase of the
framework. The cycle does not change; the tool sets that power it
do.
```
Specify → Plan → Detail → Task → Implement
```

| SDD Step | What Happens in Phase 1 (Existing Projects) | Output |
|----------|---------------------------------------------|--------|
| **Specify** | Interview the practitioner to define what must be discovered about the existing system and what the improvement objective is | Discovery Specification |
| **Plan** | Break the discovery into organized sections by domain of inquiry (code, architecture, operations, compliance, users, constraints) | Discovery Plan |
| **Detail** | Generate specific, evaluable discovery questions per section, grounded in what the codebase and artifacts can actually reveal | Discovery Requirements Document |
| **Task** | Convert questions into concrete, actionable discovery tasks — code scans, document reviews, telemetry pulls, operator interviews | Task list with acceptance criteria |
| **Implement** | Execute discovery, evaluate findings, synthesize into artifacts | Five research artifacts + Current-State Information Report |

The cycle is iterative. When implementation reveals gaps in the
specification — a module nobody documented, a data flow nobody owns,
a compliance obligation nobody tracked — cycle back. When findings
in one area raise new questions in another, add them to the task
list. The SDD cycle is not a one-way pipeline — it is a structured
loop.

### Tool Sets

A tool set is a curated combination of building blocks — prompts,
instructions, skills, MCP connections, and resources — assembled
for a specific purpose. This directory contains the Phase 1
(Existing Projects) tool set: the instructions file that provides
overarching context, and the individual prompt files that produce
each research artifact.

---

## The Three-Timeframes Discipline

Existing-project work has one discipline that does not exist in
greenfield: every claim about the system must be taggable as one
of three timeframes.

- **Observed** — verified against code, configuration, telemetry,
  or the running system
- **Documented Intent** — from ADRs, READMEs, design documents,
  architecture diagrams (may or may not match current state)
- **Desired Future** — the improvement goal (confined to the
  Requirements & Improvement Objective Sketch)

Collapsing these categories silently is the most expensive mistake
in existing-project work. If the team treats documented intent as
observed reality, the improvement plan fixes problems that don't
exist while leaving real problems alone. If the team treats current
behavior as a must-keep requirement, the improvement plan is
constrained by incidental behavior nobody actually needs. If the
team treats the improvement goal as current state, Phase 6 has no
before-picture against which to judge success.

Every artifact in this tool set, and the synthesis that combines
them, preserves this three-timeframes separation structurally.

---

## Directory Contents
```
phase-01-information-gathering-existing-project-toolset/
├── README.md                                                                   ← You are here
├── step-00-information-gathering.existing-project.instructions.md              ← Load this first
├── step-01-current-state-technology-architecture-assessment.prompt.md          ← Artifact 1
├── step-02-operational-performance-baseline.prompt.md                          ← Artifact 2
├── step-03-requirements-improvement-objective-sketch.prompt.md                 ← Artifact 3
├── step-04-risk-constraint-technical-debt-inventory.prompt.md                  ← Artifact 4
├── step-05-reusable-replaceable-components-catalog.prompt.md                   ← Artifact 5
└── step-06-current-state-information-report-synthesis.prompt.md                ← Final synthesis
```

---

## File Descriptions

### `step-00-information-gathering.existing-project.instructions.md`
**Type:** Instructions file (load as project or system context)

The overarching instructions for any AI assistant operating in
Phase 1 for an existing project. Contains the full framework
orientation — the SDD cycle, all six Core Principles applied to
existing-project work, the three-timeframes discipline, behavioral
guidelines, output standards, common pitfalls, and the connection
to Phase 2. Load this file as project-level instructions in your
AI environment before using any of the prompt files.

*Use in: Claude Project Instructions, VS Code AI instructions,
Cursor rules, or equivalent.*

---

### `step-01-current-state-technology-architecture-assessment.prompt.md`
**Type:** Interview Prompt → Action Prompt | **SDD Step:** Specify → Implement

Conducts a structured conversational interview to gather what is
needed, then produces the Current-State Technology & Architecture
Assessment. Covers languages, runtimes, frameworks, data stores,
managed services, application architecture, deployment topology,
security posture as implemented, observability state, testing
state, and documentation state — grounded in the codebase and
deployment, not in stated intent.

**Key design decision:** The codebase is the authoritative source
of truth. When documentation, memory, and code conflict, the code
wins as a description of current behavior. Divergences between
documented intent and observed reality are surfaced as first-class
findings, not silently reconciled. Every significant claim carries
an evidence-basis tag (Code / Config / Telemetry / Doc /
Practitioner / Inferred) alongside its confidence level.

**Key output elements:** Stack inventory by category (with version
numbers, not just names), application architecture tables with
deployable units and communication patterns, deployment topology,
security posture as-implemented, observability and testing state,
documentation state with currency assessment, documented-vs-observed
divergences register, tribal-knowledge zones with bus-factor
analysis, principal tensions identified, confidence-rated findings.

---

### `step-02-operational-performance-baseline.prompt.md`
**Type:** Interview Prompt → Action Prompt | **SDD Step:** Specify → Implement

Conducts a structured interview to capture how the system actually
behaves in production, then produces the Operational & Performance
Baseline. Covers reliability and availability, performance, change
cost (DORA-style metrics), run cost, incident history, observability
state, and known operator pain points. This is the artifact that
replaces greenfield competitive scanning with brownfield
self-measurement.

**Key design decision:** Measurement over belief. Every number is
tagged **Measured** (from telemetry/dashboards/billing), **Estimated**
(from spot checks or samples), **Believed** (practitioner impression),
or **UNMEASURED** (no data available). Unmeasured dimensions are
recorded as explicit rows with the UNMEASURED marker — they are
findings, not omissions. This baseline is the **before-picture**
against which every improvement will be judged in Phase 6;
qualitative-only claims have no place here.

**Key output elements:** Reliability and performance baselines with
SLO/actual separation, DORA change-cost metrics (deployment
frequency, lead time, change failure rate, MTTR), run-cost breakdown,
incident history with severity distribution and recurring classes,
observability coverage assessment, operator pain points, measurement
gaps consolidated for Phase 2's observability-investment decisions.

---

### `step-03-requirements-improvement-objective-sketch.prompt.md`
**Type:** Interview Prompt → Action Prompt | **SDD Step:** Specify → Implement

Conducts a structured interview to distinguish three questions that
must never be conflated, then produces the Requirements & Improvement
Objective Sketch. The three questions: *what must the system continue
to do*, *what must it do differently*, and *what is incidental current
behavior that Phase 2 is free to change*. This is **not** the final
requirements document — that comes in Phase 3 through the SDD Detail
step.

**Key behavioral constraint:** The AI is explicitly prohibited from
two existing-project temptations. First, treating current behavior
as requirement (which would freeze incidental behavior in place as a
constraint). Second, jumping straight to a proposed fix ("rewrite
in Rust," "move to Kubernetes") rather than sharpening the outcome
("reduce change-failure-rate from 22% to under 10% within two
release cycles"). The improvement objective must be stated as a
measurable outcome referencing the Operational & Performance
Baseline.

**Key output elements:** Must-Keep register (what improvement must
preserve), Must-Change register (outcomes the improvement must
achieve, each linked to a baseline), Nice-to-Improve backlog
(consciously deferred), Incidental current behaviors (Phase 2 is
free to change), sharpened improvement objective with measurable
targets and time horizon, non-negotiable constraints on the
improvement itself, conflicts between must-keeps and must-changes
surfaced explicitly.

---

### `step-04-risk-constraint-technical-debt-inventory.prompt.md`
**Type:** Interview Prompt → Action Prompt | **SDD Step:** Specify → Implement

Conducts a structured interview across five distinct risk and
constraint categories, then produces the Risk, Constraint &
Technical Debt Inventory. The five categories — compliance
constraints, security risks, hard constraints, project/operational
risks, and **technical debt** — are kept explicitly separate because
they require different treatment in downstream phases.

**Key design decision (new in existing-project work):** Technical
debt is a first-class category with its own register and
principle-weighted ranking. The greenfield artifact has four
categories because a greenfield project has no debt yet — it has
only candidate technologies whose long-term risk is being evaluated.
An existing-project team has already made decisions, shipped code,
and deferred work. That accumulated deferral is first-class subject
matter here, with its own evaluation and its own place in the
priority register.

**Key design decision (brownfield-specific compliance dimension):**
Compliance constraints carry a second dimension that greenfield does
not have — *claimed vs. enforced end-to-end*. A system can claim SOC 2
or HIPAA posture while the actual authentication flow bypasses the
claim in one code path, or the audit log gap creates a
documentation-only control. Surfacing this distinction in Phase 1
is orders of magnitude cheaper than surfacing it in a certification
audit.

**Key output elements:** Compliance register with claimed-vs-enforced
columns, threat actor profile grounded in incident history, live
data-exposure and attack-surface inventories, third-party and supply-
chain risk register, hard-constraint register for the improvement
itself (budget, timeline, change windows, disruption tolerance),
project/operational risks specific to the improvement cycle,
technical-debt register ranked by principle-weighted impact, priority
register consolidating all five categories, worst-case security
scenario, cross-phase handoff notes.

---

### `step-05-reusable-replaceable-components-catalog.prompt.md`
**Type:** Interview Prompt → Action Prompt | **SDD Step:** Specify → Implement

Conducts a structured interview across four component categories,
then produces the Reusable & Replaceable Components Catalog. Covers
internal existing assets, open-source libraries, managed API
services and platforms, and standard patterns and reference
architectures — each currently present in the system.

**Key design decision:** Every component already in the system gets
exactly one of four dispositions — **Keep**, **Upgrade**, **Replace**,
or **Retire**. A component listed without a disposition is an
incomplete catalog entry. New-adoption candidates proposed as
replacements get their own evaluation including fitness for purpose,
integration complexity, migration cost, and exit strategy — because
swapping a managed service with lock-in for a different managed
service with different lock-in is a common failure mode of
improvement work.

**Key design decision:** Every managed service under Replace or
Retire disposition requires an exit-cost estimation. This is where
the team will actually pay the exit cost it hoped it would never
need — enforcing the estimation at planning time, when the team
still has leverage, is cheaper than discovering it mid-migration.

**Key output elements:** Keep / Upgrade / Replace / Retire registers
with per-component rationale and migration-cost estimation, adoption
evaluations for candidate replacements, license and compliance
register with current-vs-original license comparison, dependency
risk summary, cross-references from catalog dispositions to technical
debt items from Step 04, aggregate migration-scope estimate for
Phase 2 cost modeling, catalog index.

---

### `step-06-current-state-information-report-synthesis.prompt.md`
**Type:** Action Prompt + Evaluation Prompt | **SDD Step:** Implement → Correctness Verification

**This is the only file in this directory that is not an interview
prompt.** It is an action prompt — the practitioner pastes all five
completed artifacts into the session and the AI synthesizes them
into the Current-State Information Report, then immediately conducts
a built-in self-evaluation.

The Current-State Information Report is the primary handoff artifact
from Phase 1 to Phase 2 for existing-project work. When Phase 2 tool
sets activate, the report becomes their primary input context. The
AI in Phase 2 does not start from zero — it starts from the
structured current-state findings here.

**Key synthesis disciplines enforced:**
- **Three-timeframes preservation** — every claim in the synthesis
  carries its Observed / Documented Intent / Desired Future tag from
  its source artifact
- **Baseline-to-objective linkage** — every must-change outcome
  links to a measured baseline row, so Phase 6 has a before-picture
  against which to judge success
- **Debt-to-disposition linkage** — every technical debt item with
  a material Phase 2 implication links to a specific Keep / Upgrade
  / Replace / Retire disposition
- **Documented-vs-observed divergences** are surfaced in their own
  section, not silently reconciled
- **Evidence-basis distribution** is surfaced — a report whose
  significant claims are 80% Practitioner/Memory and 15% verified
  against code is honest about the quality of its current-state
  picture

**Key output elements:** Executive summary, project & improvement
context with sharpened improvement objective and must-keep/must-
change summaries, current stack & architecture with
disposition/debt/compliance cross-references, operational & performance
baseline as Phase 6 before-picture, divergences register, compliance
map with claimed-vs-enforced dimension, consolidated risk & debt
register, component dispositions & migration scope, principal
tensions for Phase 2 navigation, Phase 2 readiness inputs including
baseline handoff for Phase 6, gap register, source/confidence/
evidence register with three-timeframes distribution, self-evaluation
scorecard.

---

## How to Use This Tool Set

### Prerequisites

Before opening any prompt file, load
`step-00-information-gathering.existing-project.instructions.md` as
project-level instructions in your AI environment. This gives every
AI session the framework context, behavioral guidelines, output
standards, and the three-timeframes discipline it needs without
requiring the practitioner to re-establish context in each session.

**For teams running this toolset alongside the greenfield toolset
on a related project:** load only one instructions file per AI
session. The two sets of behavioral rules are compatible but the
prompt style is different — the greenfield AI scans outward; the
existing-project AI inspects inward. Mixing them in one session
produces muddled output.

### Optional But Highly Recommended: AI Access to the Codebase

Several of these prompts produce much higher-quality output when
the AI can inspect the codebase directly — through Claude Code,
Cursor, an IDE AI session connected to the repository, or an MCP
server with read access. Where direct code access is available, the
AI can verify claims ("auth is handled by middleware X in file Y
line Z") rather than recording them as practitioner testimony.

Where direct access is not available, the toolset still works —
claims are recorded with appropriate confidence tags and surfaced as
verification candidates. But the scorecard's Correctness Verification
gate is easier to pass with direct code access, because the
evidence-basis distribution will skew toward Code/Config/Telemetry
rather than Practitioner/Memory.

### Recommended Sequence

The five research artifacts are designed to build on each other.
Unlike greenfield — where the order is recommended but flexible —
the existing-project sequence has harder ordering dependencies
because each artifact grounds the next in discovered evidence:
```
1. step-01-current-state-technology-architecture-assessment.prompt.md
   ↓ (what the system is)
2. step-02-operational-performance-baseline.prompt.md
   ↓ (how it behaves, what it costs)
3. step-03-requirements-improvement-objective-sketch.prompt.md
   ↓ (must-keep / must-change / improvement objective)
4. step-04-risk-constraint-technical-debt-inventory.prompt.md
   ↓ (risks, constraints, technical debt bounding the change)
5. step-05-reusable-replaceable-components-catalog.prompt.md
   ↓ (keep / upgrade / replace / retire dispositions)
6. step-06-current-state-information-report-synthesis.prompt.md
   ↓ (synthesis of all five → Current-State Information Report)
```

The improvement objective in Step 03 depends on measured baselines
from Step 02. The dispositions in Step 05 depend on the debt
register from Step 04. Running the sequence out of order is
possible but produces weaker cross-artifact linkages.

**Running each prompt:**
1. Open a new AI session
2. Confirm `step-00-information-gathering.existing-project.instructions.md`
   is loaded as project context
3. Paste completed prior artifacts above the kickoff line for
   additional context — and any available raw evidence (dependency
   manifests, dashboard screenshots, recent postmortems, audit
   reports, compliance matrices). The AI will prefer concrete
   evidence over stated impressions whenever both are present.
4. Paste the **System Instructions** section from the prompt file
   as your system prompt (if not already loaded via the instructions
   file)
5. Paste the **Kickoff** line to begin
6. Answer questions one at a time — the AI interviews you
   conversationally
7. Review the output artifact against the prompt's evaluation
   checklist before accepting it as complete

**Running the synthesis:**
1. Open a new AI session with a large context window
2. Paste all five completed artifacts in recommended sequence order
3. Paste the synthesis kickoff line
4. Review both the Current-State Information Report and the
   self-evaluation scorecard

### Iterating

The SDD cycle is iterative. If the synthesis self-evaluation returns
a CONDITIONAL or FAIL gate on any principle, cycle back to the
relevant artifact prompt, fill the gap, and re-run synthesis. This
is expected behavior, not a failure — the gate system exists to
catch gaps before they become Phase 2 problems.

Existing-project work has a particular iteration pattern: discovery
often reveals that a claim from an earlier artifact was based on
memory rather than evidence. When this happens, cycle back and
re-verify rather than carrying the claim forward. Low-confidence
claims that accumulate through the synthesis produce a report that
*looks* complete but is largely hypothesis.

---

## The Self-Evaluation Scorecard

The synthesis prompt's built-in self-evaluation is the phase gate
that determines whether Phase 1 is complete. It is not optional and
it is not a formality. It is the mechanism that makes the
Current-State Information Report trustworthy as a Phase 2 input.

The scorecard evaluates the report against all six Core Principles
and produces a gate status for each:

| Gate Status | Meaning | Phase 2 Action |
|-------------|---------|---------------|
| **PASS** | Sufficient for Phase 2 to proceed on this dimension | Proceed |
| **CONDITIONAL** | Sufficient with documented caveats; specific gaps must be addressed within Phase 2 before relevant decisions are made | Proceed with documented remediation plan |
| **FAIL** | Insufficient; Phase 2 cannot responsibly proceed on this dimension | Cycle back to Phase 1 |

### What Each Gate Evaluates (Existing-Project Variant)

**Security — PASS requires:**
Current compliance posture documented with evidence (not claims),
live threat surface enumerated from the actual deployment topology,
known vulnerabilities in the current dependency graph inventoried,
historical security incidents summarized with root causes and
remediation status, claimed-vs-enforced compliance divergences
surfaced. If this gate fails, Phase 2 will plan security improvements
against threats it hasn't actually identified.

**Maintainability — PASS requires:**
Documentation accuracy assessed (not just existence), test coverage
profile measured with current numbers, known technical debt
inventoried with code-level grounding, contributor ramp-up friction
documented, documentation-vs-code divergences surfaced. If this gate
fails, Phase 2's improvement scope will miss the work that actually
makes the system sustainable.

**Economics — PASS requires:**
Current run-cost measured (infrastructure, licensing, third-party,
operational labor), change-cost indicators captured (DORA-style:
deployment frequency, lead time, change failure rate, MTTR),
realistic improvement-budget envelope defined, migration and exit
costs estimated for components under Replace or Retire disposition.
If this gate fails, Phase 2 cost modeling will project improvements
against unmeasured baselines and produce unreliable ROI estimates.

**Operations — PASS requires:**
Current deployment topology documented, observability state
assessed (what is logged, monitored, alerted — and what is not),
incident history summarized with recurring classes identified,
known scaling limits documented, integration inventory complete.
If this gate fails, Phase 2 cannot plan operational improvements
because the current operational surface is unclear.

**Scoring & Metrics — PASS requires:**
Baseline measurements captured for every dimension the improvement
is intended to move — before improvement begins. Every must-change
outcome links to a measured baseline row. Qualitative claims ("the
system is slow," "deploys are painful") are replaced with
measurements or explicitly tagged as UNMEASURED. If this gate fails,
improvement success will be asserted rather than demonstrated, and
regressions introduced during improvement will be invisible.

**Correctness Verification — PASS requires:**
Every significant claim is tagged Observed / Documented Intent /
Desired Future, every claim carries a source and a confidence level,
divergences between documented intent and observed behavior are
surfaced rather than reconciled, conflicts between source artifacts
are documented, discovery gaps are explicitly registered, and the
evidence-basis distribution shows a credible share of Code/Config/
Telemetry-verified claims relative to memory-only claims. If this
gate fails, Phase 2 will be planning improvements against a
current-state picture that may not reflect reality.

### Gate Logic

A single FAIL gate does not block all of Phase 2 — it blocks Phase 2
on that specific dimension. The team must cycle back to the
relevant Phase 1 artifact prompt, fill the gap, and re-run synthesis
before Phase 2 makes decisions in that area.

CONDITIONAL gates allow Phase 2 to proceed with documented caveats.
Each conditional pass must have a named remediation action, a
responsible owner, and a target date. Conditional passes that
accumulate without remediation degrade into silent failures over
time.

The gate system's value is in its honesty. A Current-State
Information Report that passes all six gates with documented
confidence is worth more to Phase 2 than a report that appears
comprehensive but contains low-confidence claims passed off as
established findings. In existing-project work, this discipline
has an additional benefit: a report that overstates current-state
confidence produces an improvement plan that fails on contact with
reality, which is the most expensive failure mode this tool set
exists to prevent.

---

## Artifact Dependency Map
```
step-01-current-state-technology-architecture-assessment
        │ (what the system is)
        │
        ├──────────────────────────────────────┐
        │                                      │
step-02-operational-performance-baseline        │
        │ (how it behaves)                     │
        │                                      │
        └──────────────┬───────────────────────┘
                       │
                       ▼
step-03-requirements-improvement-objective-sketch
        │ (must-keep / must-change / objective)
        │
        ▼
step-04-risk-constraint-technical-debt-inventory
        │ (risks, constraints, debt)
        │
        ▼
step-05-reusable-replaceable-components-catalog
        │ (keep / upgrade / replace / retire)
        │
        ▼
step-06-current-state-information-report-synthesis
        │ (consumes all five artifacts)
        │
        ▼
Current-State Information Report
[Phase 1 → Phase 2 handoff]
```

Cross-artifact connections that the synthesis must surface:

- **Baselines → Improvement objectives** (Op & Perf Baseline §4
  → Requirements & Improvement Objective Sketch must-changes):
  every must-change outcome has a measured baseline that Phase 6
  will use as the before-picture
- **Compliance claims → Current implementation**
  (Risk/Constraint/Technical Debt compliance register → Technology
  & Architecture Assessment authentication/authorization rows): a
  compliance claim dependent on a component under Replace
  disposition is a Phase 2 sequencing dependency
- **Incident history → Technical debt → Component dispositions**
  (Op & Perf Baseline incidents → Risk/Constraint/Technical Debt
  register → Components Catalog): recurring incident classes are
  traced to the debt items and component dispositions that will
  address them
- **Hard constraints → Improvement scope**
  (Risk/Constraint/Technical Debt hard constraints → Requirements
  & Improvement Objective Sketch): budget, timeline, change windows,
  and disruption tolerance bound the improvement plan
- **Documented-vs-observed divergences → Phase 2 decisions**
  (Technology & Architecture Assessment divergences register):
  every divergence requires Phase 2 to decide — correct the docs,
  correct the implementation, or accept the gap
- **Migration & retirement scope → Phase 2 cost model**
  (Components Catalog → Phase 2 cost modeling): the improvement
  cost model rolls up component-by-component migration estimates

---

## Common Pitfalls

**Trusting documentation over code.**
Documentation represents what someone intended to be true at some
point in the past. Code represents what is running now. When they
disagree, the code wins as a description of current behavior. The
disagreement itself is a finding — document it; don't resolve it
silently.

**Trusting memory over evidence.**
Practitioners often describe systems from confident memory. Memory
is a useful starting point for hypotheses, not a substitute for
verification. "We already do X" is a hypothesis until confirmed in
the code or the running system. In existing-project work, this
discipline is structural: the evidence-basis distribution in the
synthesis scorecard surfaces when a report relies too heavily on
memory.

**Collapsing the three timeframes.**
Mixing observed current behavior, documented intent, and desired
future state produces improvement plans that fix symptoms rather
than causes. Keep them distinct in every artifact and preserve the
distinction through synthesis.

**Treating current behavior as requirement.**
Not every current behavior is a must-keep. Many are incidental —
the system does them today because nobody had reason to change
them, not because anyone needs them. Classifying incidental
behavior as must-keep freezes the system in place and eliminates
improvement options that would have been fine.

**Treating every pain point as a must-change.**
A catalog of every team frustration, promoted to the must-change
register, produces an improvement scope that Phase 2 cannot
sequence. The improvement objective must be sharpened to a
focused set of outcomes with measurable targets.

**Skipping the baseline capture.**
If Phase 1 does not measure the dimensions the improvement is
meant to move, the improvement's success will be asserted rather
than demonstrated, and regressions introduced during improvement
will be invisible. Baselines are not optional for existing-project
work — they are the evidence against which improvement is judged
in Phase 6.

**Letting the improvement objective stay vague.**
"Modernize the stack," "fix the tech debt," and "improve
performance" are starting points, not objectives. A vague objective
produces a vague Phase 2 and an unfocused Phase 3. Sharpen the
objective to a measurable outcome with a time horizon before
Phase 1 is declared complete.

**Classifying differences as defects prematurely.**
Not every oddity in the codebase is technical debt. Some reflect
constraints the team has forgotten, compliance decisions, or
integrations with systems the practitioner no longer routinely
thinks about. Before labeling a component as Replace or Retire,
ask whether the oddity is intentional. Frame findings neutrally
and let the practitioner classify.

**Proposing solutions in this phase.**
The temptation is strong in existing-project work — the problems
are visible and the fixes seem obvious. Resist. Phase 1 discovers
and structures the current state; Phase 2 decides what to change
and how. Surfacing a candidate improvement area is in scope.
Prescribing a solution is not.

**Conflating compliance constraints with security risks.**
Compliance constraints are non-negotiable external obligations —
they are satisfied or the project faces regulatory consequence.
Security risks are threats to analyze and mitigate. Conflating
them produces an inventory where neither gets the treatment it
deserves. In existing-project work, this pitfall has a second
face: conflating a *claimed* compliance posture with an *enforced*
one. Surface the claimed-vs-enforced distinction explicitly.

**Dropping the technical debt category into project risks.**
Technical debt is its own category because it requires its own
treatment. Debt items are ranked by principle-weighted impact;
project risks are ranked by likelihood-times-impact on the
improvement cycle. Mixing them produces a priority register where
debt and risk items drown each other out.

**Producing a report that serves humans but not AI.**
Narrative prose buried in unstructured sections is insufficient
for downstream AI consumption. Structure, label, and format every
output for machine parseability alongside human readability. If
a Phase 2 AI tool set cannot load the Current-State Information
Report as context and produce useful analysis from it, the report
structure needs work.

**Accepting a synthesis without reviewing the scorecard.**
The self-evaluation scorecard is the phase gate. A CONDITIONAL or
FAIL gate that is ignored or deprioritized does not go away — it
surfaces as a problem in Phase 2 when it is significantly more
expensive to address. In existing-project work, it surfaces as a
plan that collides with reality in Phase 5, which is the most
expensive failure mode.

---

## Connecting to Phase 2

The Current-State Information Report is the direct input to every
Phase 2 (Analysis & Improvement Planning) tool set. When Phase 2
activates, the report becomes a resource in every tool set — Phase
2 does not re-discover the system, it analyzes, evaluates, and
decides using the current-state evidence gathered here.

Phase 2 tool sets draw directly from specific sections of the
Current-State Information Report:

| Phase 2 Tool Set | Draws From |
|-----------------|-----------|
| Improvement Scope & Sequencing | §2 improvement objective, §7 priority register, §8 migration scope, §9 tensions |
| Improvement Cost Modeling | §4 baseline costs, §8 migration scope, §7 debt register, §2 budget constraint |
| Updated Compliance Architecture | §5 divergences, §6 compliance map with claimed-vs-enforced dimension |
| Updated Threat Modeling | §3 current stack, §6 compliance gaps, §7 security risks |
| Improvement Benchmark Definition | §2 must-change targets, §4 baseline values, §10 baseline handoff |
| Component Adoption Confirmation | §8 Replace candidates, §6 compliance coverage |

The quality of Phase 1 directly determines the quality of Phase 2.
A shallow Current-State Information Report produces shallow
improvement planning. A principle-filtered, well-verified,
AI-parseable report with baseline-to-objective linkage, debt-to-
disposition linkage, and surfaced divergences gives Phase 2 a
strong foundation for weighted evaluation, improvement sequencing,
and cost modeling.

The baseline handoff (§10) serves an additional purpose: it
travels forward all the way to Phase 6, where improvement success
is verified against the before-picture captured here. An
improvement that claims to reduce change-failure-rate from 22% to
10% is only verifiable in Phase 6 if the 22% baseline was
captured in Phase 1.

---

*Part of the AI-Centric Software Development Playbook — Phase 1: Information Gathering (Existing Projects)*
*Framework reference: article-03-information-gathering.md*
*Companion (greenfield): `toolkit/phase-01-information-gathering-toolset/`*
*Handoff to: Phase 2 (Analysis & Improvement Planning) tool sets*
