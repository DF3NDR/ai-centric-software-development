# Phase 1 Information Gathering Tool Set — Existing Projects

**AI-Centric Software Development Playbook**

**Toolset Version:** v1.1 (revised 2026-04-20 from Diamonds dogfooding run)

---

## What This Tool Set Is For

This directory contains the **existing-project variant** of the Phase 1
Information Gathering Tool Set. It is used when the practitioner is
improving a system that already exists — rather than choosing
technologies for a greenfield build.

The greenfield variant lives at
`toolkit/phase-01-information-gathering-toolset/` and asks
*"what should we choose?"*. This variant asks
*"what do we have, where are we, and what must change?"* —
evidence comes largely from inside the team (the codebase, its
deployment history, its documentation, its incidents, its users,
its operators) rather than from outside.

The SDD cycle, the six Core Principles, the phase-gate discipline,
and the Information Report format are identical across variants.
What changes is where the evidence comes from and what questions
are asked.

---

## The Six Core Principles in This Phase

Every artifact in this phase is evaluated against all six principles.
Every claim that enters the Information Report must be traceable to
at least one principle. Gaps that leave a principle unaddressed are
flagged explicitly — never silently omitted.

| Principle | What This Phase Asks About An Existing System |
|-----------|-----------------------------------------------|
| **Security** | Current threat model, enforced vs. claimed compliance, known vulnerabilities in the current dependency graph, secrets and trust-boundary posture, incident history |
| **Maintainability** | Documentation accuracy vs. code, test coverage and quality, known and latent technical debt, contributor ramp-up friction |
| **Economics** | Current run-cost (infra, licensing, operational labor), change-cost (deployment frequency, lead time, change failure rate, MTTR), realistic improvement-budget envelope |
| **Operations** | Deployment topology and automation, observability posture, incident history, integration inventory, scaling limits |
| **Scoring & Metrics** | Measured baselines for every dimension the improvement is intended to move — captured *before* improvement begins, so improvement can be measured rather than asserted |
| **Correctness Verification** | Divergences between documented intent and observed behavior, source and date for every significant claim, confidence levels assigned, discovery gaps explicitly registered |

The principles are not evaluated at the end of the phase. They shape
what is discovered, how findings are evaluated, and what questions are
asked — from the first interview through the final synthesis.

---

## Specification Driven Development (SDD)

All work in this phase follows the SDD cycle — the same iterative,
specification-first methodology that drives every phase of the
framework. The cycle does not change; the tool sets that power it do.
```
Specify → Plan → Detail → Task → Implement
```

| SDD Step | What Happens in This Phase | Output |
|----------|---------------------------|--------|
| **Specify** | Interview the practitioner to define what needs to be discovered and sharpen the improvement objective | Discovery Specification |
| **Plan** | Break the discovery into organized sections by domain of inquiry | Discovery Plan |
| **Detail** | Generate specific, evaluable discovery questions per section | Discovery Requirements Document |
| **Task** | Convert questions into concrete, actionable discovery tasks | Task list with acceptance criteria |
| **Implement** | Execute discovery, evaluate findings, synthesize into artifacts | Five discovery artifacts + Current-State Information Report |

The cycle is iterative. When implementation reveals gaps in the
specification, cycle back. When findings in one area raise new
questions in another, add them to the task list. The SDD cycle is not
a one-way pipeline — it is a structured loop.

---

## Tool Sets and Building Blocks

A tool set is a curated combination of building blocks — prompts,
instructions, skills, MCP connections, and resources — assembled for
a specific purpose. This directory contains the Phase 1
(Existing Projects) tool set: the instructions file that provides
overarching context, the Building Block Discovery prompt that surveys
what AI capabilities are available for the run, and the individual
prompt files that produce each discovery artifact.

---

## Directory Contents

```
phase-01-information-gathering-existing-project-toolset/
├── README.md                                                          ← You are here
├── step-00-information-gathering.existing-project.instructions.md     ← Load this first
├── step-00b-building-block-discovery.prompt.md                        ← Run before Step 01
├── step-01-current-state-technology-architecture-assessment.prompt.md ← Artifact 1
├── step-02-operational-performance-baseline.prompt.md                 ← Artifact 2
├── step-03-requirements-improvement-objective-sketch.prompt.md        ← Artifact 3
├── step-04-risk-constraint-technical-debt-inventory.prompt.md         ← Artifact 4
├── step-05-reusable-replaceable-components-catalog.prompt.md          ← Artifact 5
└── step-06-current-state-information-report-synthesis.prompt.md       ← Final synthesis
```

---

## File Descriptions

### `step-00-information-gathering.existing-project.instructions.md`
**Type:** Instructions file (load as project or system context)

The overarching instructions for any AI assistant operating in Phase 1
on an existing project. Contains the full framework orientation — the
SDD cycle, all six Core Principles applied to existing-project work,
the three-timeframes discipline (Observed / Documented Intent /
Desired Future), the multi-repo evidence-scoping framework, the
code-access calibration modes, interview mode selection, version
re-verification discipline, output standards, common pitfalls, and
the connection to Phase 2.

Load this file as project-level instructions in your AI environment
before using any of the prompt files.

*Use in: Claude Project Instructions, VS Code AI instructions,
Cursor rules, or equivalent.*

---

### `step-00b-building-block-discovery.prompt.md`
**Type:** Interview Prompt | **SDD Step:** Specify (building-block inventory)

**New in v1.1.** Conducts a short, structured inventory of the AI
capabilities — MCP connectors, Skills, specialized agents, code
access — available for this Phase 1 run. Produces a brief
toolset-augmentation document that informs every subsequent step's
interview-mode and code-access decisions.

Run this prompt *after* the initial Specify interview (which captures
the improvement objective and scope) and *before* Step 01. It is
short — typically under ten minutes — and its value is
disproportionate to its cost: it prevents Steps 01–06 from assuming
capabilities that aren't available, or from failing to leverage
capabilities that are.

**Key design decision:** Capability discovery is explicit and happens
once, not rediscovered under pressure mid-Step-03 when a missing
connector blocks evidence gathering.

---

### `step-01-current-state-technology-architecture-assessment.prompt.md`
**Type:** Interview Prompt → Action Prompt | **SDD Step:** Specify → Implement

Conducts a structured interview to inventory what the system is
actually built from — languages, runtimes, frameworks, data stores,
services, versions, deployment topology, integrations — then produces
the Current-State Technology & Architecture Assessment. Evaluates
every stack element against all six Core Principles and surfaces
divergences between documented intent and observed behavior.

**Key design decision:** The codebase is the primary source of
evidence. Documentation, memory, and stated intent are secondary and
must be cross-checked. Where code and documentation disagree, the
divergence itself is the finding.

**Key output elements:** Stack inventory with version-specific rows,
application architecture, deployment topology, compliance posture as
implemented, testing and documentation state, known pain points and
tensions, ecosystem drift watch, discovery gaps, confidence summary.

---

### `step-02-operational-performance-baseline.prompt.md`
**Type:** Interview Prompt → Action Prompt | **SDD Step:** Specify → Implement

Conducts a structured interview to establish the **measured
before-picture** of the system — reliability, performance, change-cost
(DORA-style: deployment frequency, lead time, change failure rate,
MTTR), run-cost, incident history, observability state. Produces the
Operational & Performance Baseline.

**Key design decision:** Qualitative claims ("the system is slow,"
"deploys are painful") are replaced with measurements or explicitly
tagged as UNMEASURED. Every dimension the improvement is intended to
move must have a baseline row — otherwise improvement success will be
asserted rather than demonstrated.

**Key output elements:** Reliability rows, performance rows,
change-cost rows, run-cost rows, incident history, observability
gaps, measurement gaps, every row tagged MEASURED / ESTIMATED /
BELIEVED / UNMEASURED.

---

### `step-03-requirements-improvement-objective-sketch.prompt.md`
**Type:** Interview Prompt → Action Prompt | **SDD Step:** Specify → Implement

Conducts a structured interview to separate what the system must
continue to do (Must-Keep), what it must do differently (Must-Change),
what would be nice but can wait (Nice-to-Improve), and what is
currently incidental and open to change. Produces the Requirements &
Improvement Objective Sketch and sharpens the improvement objective
from "we need to modernize" into a measurable outcome.

**Key design decision:** The improvement objective is a Phase 1
*output*, not a Phase 1 input. Practitioners arrive with vague goals;
Phase 1 sharpens them into something specific enough to drive Phase 2
decisions.

**Key output elements:** Must-Keep register, Must-Change register with
each outcome linked to a baseline row from Step 02, Nice-to-Improve
backlog with re-evaluation triggers, Incidental register, sharpened
improvement objective, principal tensions.

---

### `step-04-risk-constraint-technical-debt-inventory.prompt.md`
**Type:** Interview Prompt → Action Prompt | **SDD Step:** Specify → Implement

Conducts a structured interview to inventory current-state compliance
posture (including claimed vs. enforced), security risks, hard
constraints on change, project and operational risks, and technical
debt. Produces the Risk, Constraint & Technical Debt Inventory.
Includes a required worst-case-scenario synthesis that seeks the
common mechanism across branches.

**Key design decision:** Expect 2–4 net-new Must-Changes and 1–2 MC
amendments to emerge from register construction. This is by design —
the inventory examines the system through threat and constraint lenses
that the prior three steps don't use, and new must-changes surface
naturally.

**Key output elements:** Compliance register (with
standards-conformance framing for non-regulated projects), Security
Risk register, Hard Constraint register, Project / Operational Risk
register, Technical Debt register with principle mappings, worst-case
scenario narrative, priority-ordered Phase 2 input, cross-phase
handoff notes.

---

### `step-05-reusable-replaceable-components-catalog.prompt.md`
**Type:** Interview Prompt → Action Prompt | **SDD Step:** Specify → Implement

Conducts a structured interview to catalog every meaningful component
in the subject repository with an explicit disposition: Keep, Upgrade,
Replace, Retire, or Net-new. Every disposition links back to the
Must-Change register or an explicit practitioner decision. Produces
the Reusable & Replaceable Components Catalog.

**Key design decision:** Expect 3–5 scope expansions to existing
Must-Changes, not net-new Must-Changes. The catalog examines every
component individually, which reveals work the higher-level Step 03/04
registers couldn't enumerate. Scope expansion is preferred over new MC
authorship unless the expansion is architecturally distinct.

**Key output elements:** Per-category component catalog (source, tests,
scripts, deps, configs, docs, build, CI/CD), disposition-ratio
interpretation (Keep-heavy / Retire-heavy / Upgrade-heavy / Sunset
patterns), MC-to-component coverage map, scope-expansion register,
Phase 2 handoff notes.

---

### `step-06-current-state-information-report-synthesis.prompt.md`
**Type:** Action Prompt + Evaluation Prompt | **SDD Step:** Implement → Correctness Verification

**This is the only file in this directory that is not an interview
prompt.** It is an action prompt — the practitioner pastes all five
completed artifacts into the session and the AI synthesizes them into
the Current-State Information Report, then immediately conducts a
built-in self-evaluation.

**Key design decision:** Step 06 is synthesis-only. If Step 06 is
producing net-new findings, decisions, or dispositions, something was
missed in Steps 01–05 — pause Step 06 and fix the upstream gap. When
self-rating principles in the scorecard, CONDITIONAL is preferred over
PASS-with-caveats. A CONDITIONAL rating with explicit rationale
surfaces a decision point; a PASS with buried caveat is easier to
miss. Aim for 4–5 PASS + 1–2 CONDITIONAL on a well-executed Phase 1.

**Key output elements:** Executive summary, consolidated context,
consolidated baselines, consolidated registers, priority-ordered
Phase 2 input, worst-case preservation, self-evaluation scorecard,
gap and handoff enumeration, source & evidence register.

The Current-State Information Report is the primary handoff artifact
from Phase 1 to Phase 2. When Phase 2 tool sets activate, the report
becomes their primary input context. The AI in Phase 2 does not start
from zero — it starts from the structured current-state findings here.

---

## MCP Servers and AI Tool Augmentation

*New in v1.1.* This tool set is designed to work well with standard
Claude capabilities, but certain MCP (Model Context Protocol)
connectors materially improve productivity. **These are strongly
encouraged but not strictly required.** When a connector is
unavailable or fails, the tool set degrades gracefully into
copy-paste requests to the practitioner — nothing blocks.

Meaningful connectors for this tool set:

- **GitHub MCP** — Enables direct consultation of the project's issue
  tracker (used in Steps 01 and 03 for issue-to-register
  classification), direct access to code across peer repos (used in
  Step 01 multi-repo evidence scoping), and pull-request and release
  history (used in Step 02 release-cadence measurement). When
  unavailable: practitioner pastes issue lists, code excerpts, and
  release dates manually.

- **Context7 (or equivalent library-documentation connector)** —
  Enables authoritative lookups for library and framework documentation
  during Step 01 stack evaluation (current stable versions, EOL status,
  upstream support windows). When unavailable: the AI uses training-data
  knowledge with a confidence caveat, and the practitioner is prompted
  to confirm current values.

- **Direct code access** (Claude Code, Cursor with repo-connected
  session, filesystem access, or equivalent) — Enables the AI to verify
  claims against the actual codebase rather than practitioner
  description. Materially raises confidence levels and enables the
  Search-primary or Hybrid code-access modes described in Step 00. When
  unavailable: the Interview-only mode is used, findings are tagged
  with lower confidence, and verification candidates are flagged for
  follow-up.

The implementer is expected to be an expert in their own AI environment
and is best positioned to decide how to enable these connectors for a
specific Claude client, deployment, or organizational policy context.
This tool set does not prescribe implementation details.

The Building Block Discovery prompt (step-00b) formally captures which
of these are available for a given Phase 1 run and documents the
graceful-degradation posture to be used where anything is missing.

---

## How to Use This Tool Set

### Prerequisites

Before opening any prompt file, load
`step-00-information-gathering.existing-project.instructions.md` as
project-level instructions in your AI environment. This gives every AI
session the framework context, behavioral guidelines, the
three-timeframes discipline, multi-repo scoping framework, code-access
calibration modes, interview mode selection, and output standards it
needs without requiring the practitioner to re-establish context in
each session.

### Recommended Sequence

The six discovery artifacts are designed to build on each other. While
they can be run in any order, this sequence is recommended because
each artifact provides useful context for the next:

```
0. Initial Specify interview (via step-00 instructions)
   ↓ (sharpened improvement objective, scope boundary, constraint envelope)
0b. step-00b-building-block-discovery.prompt.md
   ↓ (toolset-augmentation document: MCP / skills / code access available)
1. step-01-current-state-technology-architecture-assessment.prompt.md
   ↓ (what the system is built from, as deployed)
2. step-02-operational-performance-baseline.prompt.md
   ↓ (how the system behaves in production — measured)
3. step-03-requirements-improvement-objective-sketch.prompt.md
   ↓ (what must be kept, changed, or deferred)
4. step-04-risk-constraint-technical-debt-inventory.prompt.md
   ↓ (what could go wrong, what is fixed, what is owed)
5. step-05-reusable-replaceable-components-catalog.prompt.md
   ↓ (what to keep, upgrade, replace, or retire)
6. step-06-current-state-information-report-synthesis.prompt.md
   ↓ (synthesis of all five → Current-State Information Report)
```

**Running each prompt:**
1. Open a new AI session.
2. Confirm
   `step-00-information-gathering.existing-project.instructions.md`
   is loaded as project context.
3. Optionally paste completed prior artifacts (and the step-00b
   toolset-augmentation document) above the kickoff line for
   additional context.
4. Paste the **System Instructions** section from the prompt file as
   your system prompt (if not already loaded via the instructions
   file).
5. Paste the **Kickoff** line to begin.
6. Answer questions or react to drafts — the AI interviews or drafts
   conversationally, following the interview-mode selection
   appropriate to the step (question-by-question for Steps 01–02;
   draft-and-react for Steps 03–05; synthesis-only for Step 06).
7. Review the output artifact against the prompt's evaluation
   checklist before accepting it as complete.

**Running the synthesis (Step 06):**
1. Open a new AI session with a large context window.
2. Paste all five completed artifacts in recommended sequence order.
3. Paste the synthesis kickoff line.
4. Review both the Current-State Information Report and the
   self-evaluation scorecard.

### Iterating

The SDD cycle is iterative. If the Step 06 self-evaluation returns a
CONDITIONAL or FAIL gate on any principle, cycle back to the relevant
artifact prompt, fill the gap, and re-run Step 06. This is expected
behavior, not a failure — the gate system exists to catch gaps before
they become Phase 2 problems.

---

## The Self-Evaluation Scorecard

Step 06's built-in self-evaluation is the phase gate that determines
whether Phase 1 is complete. It is not optional and it is not a
formality. It is the mechanism that makes the Current-State Information
Report trustworthy as a Phase 2 input.

The scorecard evaluates the report against all six Core Principles and
produces a gate status for each:

| Gate Status | Meaning | Phase 2 Action |
|-------------|---------|---------------|
| **PASS** | Sufficient for Phase 2 to proceed on this dimension | Proceed |
| **CONDITIONAL** | Sufficient with documented caveats; specific gaps must be addressed within Phase 2 before relevant decisions are made | Proceed with documented remediation plan |
| **FAIL** | Insufficient; Phase 2 cannot responsibly proceed on this dimension | Cycle back to Phase 1 |

A single FAIL gate does not block all of Phase 2 — it blocks Phase 2
on that specific dimension. The team must cycle back to the relevant
Phase 1 artifact prompt, fill the gap, and re-run synthesis before
Phase 2 makes decisions in that area.

CONDITIONAL gates allow Phase 2 to proceed with documented caveats.
Each conditional pass must have a named remediation action, a
responsible owner, and a target date. Conditional passes that
accumulate without remediation degrade into silent failures over time.

The gate system's value is in its honesty. A Current-State Information
Report that passes all six gates with documented confidence is worth
more to Phase 2 than a report that appears comprehensive but contains
low-confidence claims passed off as established findings. CONDITIONAL
is preferred over PASS-with-caveats — a CONDITIONAL rating with
explicit rationale surfaces a decision point; a buried caveat is
easier to miss.

---

## Common Pitfalls

**Starting discovery without specifying.** Starting code-reading,
dashboard-browsing, and interviewing without defining what needs to be
discovered produces sprawling, unfocused output. The SDD Specify step
is not overhead — it is what makes the discovery useful.

**Trusting documentation over code.** Documentation represents what
someone intended to be true at some point in the past. Code represents
what is running now. When they disagree, the code wins as a description
of current behavior. The disagreement itself is a finding — document
it; don't resolve it silently.

**Trusting memory over evidence.** Practitioners often describe systems
from confident memory. Memory is a useful starting point for
hypotheses, not a substitute for verification. "We already do X" is a
hypothesis until confirmed in the code or running system.

**Collapsing the three timeframes.** Mixing observed current behavior,
documented intent, and desired future state produces improvement plans
that fix symptoms rather than causes. Keep them distinct in every
artifact.

**Classifying differences as defects prematurely.** Unfamiliar patterns
in the codebase are not automatically technical debt. Ask before
labeling. Some oddities encode forgotten constraints, compliance
obligations, or integrations that the practitioner no longer routinely
thinks about.

**Skipping the baseline capture.** If Phase 1 does not measure the
dimensions the improvement is meant to move, improvement success will
be asserted rather than demonstrated, and regressions introduced during
improvement will be invisible. Baselines are not optional for
existing-project work — they are the evidence against which improvement
is judged.

**Letting the improvement objective stay vague.** "Modernize the
stack," "fix the tech debt," and "improve performance" are starting
points, not objectives. A vague objective produces a vague Phase 2 and
an unfocused Phase 3. Sharpen the objective in this phase.

**Proposing solutions in this phase.** The temptation is strong in
existing-project work — the problems are visible and the fixes seem
obvious. Resist. Phase 1 discovers and structures; Phase 2 decides.
Surfacing a candidate improvement area is in scope; prescribing a
solution is not.

**Producing a report that serves humans but not AI.** Narrative prose
buried in unstructured sections is insufficient for downstream AI
consumption. Structure, label, and format every output for machine
parseability alongside human readability. If a Phase 2 AI tool set
cannot load the Current-State Information Report as context and produce
useful analysis from it, the report structure needs work.

**Accepting a synthesis without reviewing the scorecard.** The
self-evaluation scorecard is the phase gate. A CONDITIONAL or FAIL
gate that is ignored or deprioritized does not go away — it surfaces
as a problem in Phase 2 when it is significantly more expensive to
address.

---

## Connecting to Phase 2

The Current-State Information Report is the direct input to every
Phase 2 tool set:

- **Improvement Scope & Sequencing Tool Set** — consumes the
  Must-Change register, priority-ordered Phase 2 input, and
  scope-expansion register
- **Cost Modeling Tool Set** — consumes the Step 02 run-cost and
  change-cost baselines, the component-disposition migration scope,
  and the hard-constraint envelope
- **Architecture & Design Tool Set** — consumes the current
  architecture, extension-point candidates, and principal tensions
- **Threat Modeling Tool Set** — consumes the Security Risk register,
  compliance posture (claimed vs. enforced), and divergences register
- **Benchmark & Verification Tool Set** — consumes the measured
  baselines from Step 02 and the per-MC Phase 6 verification methods

In existing-project work, Phase 2 transforms this evidence into an
**improvement plan**: scoped, sequenced, cost-modeled, risk-assessed,
and measurable against the baselines captured in Phase 1. Phase 2 does
not re-discover the system. It analyzes, evaluates, and decides —
using the Current-State Information Report as the evidence base. The
quality of Phase 1 directly determines the quality of Phase 2.

---

## Dogfooding & Calibration Guidance

This tool set is refined through dogfooding runs — running the tool
set on real projects and capturing observations about where it works,
where it doesn't, and what should change.

**Expected dogfooding observation count per complete Phase 1 run is
20–30.** Counts below 10 warrant skepticism about self-criticism rigor
— either the tool set is already mature for that project type
(possible) or the practitioner is being insufficiently critical (more
likely). Counts above 50 suggest foundational tool set issues requiring
a larger revision than incremental version improvements.

Observations captured during a run are reviewed end-of-phase and
categorized as Accept (goes into next version), Refine (modified and
goes in), Defer (real but not now), or Reject (not a real improvement).
Accepted observations drive the version increment.

---

## Version History

| Version | Date | Source | Summary |
|---------|------|--------|---------|
| v1.0 | 2026-04-18 | Initial authoring | Initial existing-project variant derived from greenfield tool set. Six step prompts + instructions file + README. |
| **v1.1** | **2026-04-20** | **Diamonds dogfooding run** | Added step-00b (Building Block Discovery). Expanded step-00 with multi-repo evidence scoping, code-access calibration, three-timeframes worked example, version re-verification, interview mode selection. Added issue-tracker consultation to steps 01 and 03. Added local evidence collection to step 02. Added standards-conformance framing and worst-case common-mechanism discipline to step 04. Added disposition-ratio interpretation, scope-expansion expectation, and artifact-inheritance warning to step 05. Added synthesis-only discipline and scorecard rigor guidance to step 06. Added MCP Servers section and observation-count calibration to README. |

---

*Part of the AI-Centric Software Development Playbook*
*Phase 1 Information Gathering (Existing Projects) Tool Set — v1.1*
