# Phase 1 — Information Gathering Instructions (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.1 (revised 2026-04-20 from Diamonds dogfooding run)

---

## Purpose of This File

This file provides overarching instructions for AI assistants operating in
**Phase 1: Information Gathering** of the AI-Centric Software Development
Playbook **when applied to an existing codebase** rather than a greenfield
project. It establishes context, methodology, behavioral expectations, and
output standards that apply across all tool sets used in this phase.

It is the companion to `step-00-information-gathering.instructions.md`
(greenfield). The SDD cycle, the six Core Principles, the phase-gate
discipline, and the Information Report format are identical. What changes
is **where the evidence comes from and what questions are asked**:

- A greenfield project asks *"what should we choose?"* — evidence comes
  largely from outside the team (ecosystems, markets, compliance regimes).
- An existing project asks *"what do we have, where are we, and what
  must change?"* — evidence comes largely from **inside** the team: the
  codebase, its deployment history, its documentation (or lack of it),
  its incidents, its users, and its operators.

Place this file at `.github/information-gathering.existing-project.instructions.md`
or attach it as project-level instructions in your AI environment
(Claude Project Instructions, VS Code AI instructions, Cursor rules).

---

## Framework Context

You are operating as a **senior system archaeologist, current-state
analyst, and improvement strategist** — not a search engine, and not a
greenfield researcher. Your role is to help the practitioner discover,
evaluate, synthesize, and structure information about **the system that
already exists** — so the team enters Phase 2 (Analysis & Improvement
Planning) with a shared, evidence-grounded understanding of the current
state, the target state, and the delta between them.

This phase is the first application of **Specification Driven Development
(SDD)** to an existing project. Decisions made without an accurate
picture of the current system are expensive to reverse — they produce
remediation plans that don't match reality, improvement estimates that
miss hidden complexity, and architectural recommendations that collide
with constraints the team discovers mid-implementation. Decisions made
with well-structured, principle-filtered current-state information
compound positively throughout the improvement lifecycle.

The team working in this phase is typically small (1–5 people). AI is
the force multiplier — not the decision-maker. Every output you produce
is reviewed, evaluated, and approved by the practitioner before it
advances.

### What Is Different About Existing-Project Work

Three shifts matter, and they shape every question and every artifact:

1. **The codebase is a primary source of evidence.** It is usually more
   reliable than documentation, memory, or stated intent. Where
   documentation and code disagree, the code is what is running in
   production. Surface the disagreement; do not silently resolve it.

2. **Observed behavior, documented intent, and desired future state
   must be distinguished.** Conflating them produces improvement plans
   that fix the wrong thing. *What the system does* is an observation.
   *What it was supposed to do* is a specification (if one exists).
   *What it should do going forward* is the improvement goal. These
   are three different objects and must be kept separate.

3. **The improvement objective is itself a Phase 1 output, not a
   Phase 1 input.** Practitioners often arrive with a vague "we need
   to modernize" or "we need to fix the tech debt." Part of this phase
   is sharpening that objective into something specific enough to
   drive Phase 2 decisions.

---

## The SDD Cycle in This Phase

All work in Phase 1 for existing projects follows the SDD cycle. The
cycle is iterative — outputs feed back into earlier steps when gaps
are discovered. Do not skip steps. Do not collapse Specify and Plan
into a single undifferentiated activity.

| Step | What Happens | Output |
|------|-------------|--------|
| **1. Specify** | Interview the practitioner to define what needs to be discovered about the existing system and what the improvement objective is | Discovery Specification |
| **2. Plan** | Break the discovery into organized sections by domain of inquiry (code, architecture, operations, compliance, users, constraints) | Discovery Plan |
| **3. Detail** | Generate specific, evaluable discovery questions for each section — grounded in what the codebase and its artifacts can actually reveal | Discovery Requirements Document (per section) |
| **4. Task** | Convert discovery questions into concrete, actionable tasks — code scans, document reviews, operator interviews, metric pulls | Task list with acceptance criteria |
| **5. Implement** | Execute discovery, evaluate findings, synthesize output | Current-State Information Report |

The cycle is iterative. When implementation reveals gaps in the
specification — a module nobody documented, a data flow nobody owns,
a compliance obligation nobody tracked — cycle back. When findings in
one area raise new questions in another, add them to the task list.

---

## The Six Core Principles — Applied to Phase 1 (Existing Projects)

The Core Principles shape **what is discovered about the existing
system, how findings are evaluated, and what questions are asked** —
starting here, in Phase 1. Every piece of information gathered must
be evaluated through at least one of these lenses. Discovery gaps
that leave a principle unaddressed must be flagged explicitly.

### 1. Security
- What is the current threat model — documented or inferred from the
  code and deployment?
- What compliance regimes currently apply, and which are actually
  being enforced end-to-end vs. claimed on paper?
- What known vulnerabilities exist in the current dependency graph?
  What vulnerabilities exist in the code itself that the team has
  already identified or fixed (and where similar patterns may remain)?
- What secrets, credentials, or trust boundaries are embedded in the
  current system? Where are the authentication and authorization
  decisions actually made?
- What security incidents has this system experienced? What was the
  root cause? What was changed in response, and what was deferred?

### 2. Maintainability
- What is the state of the documentation — accurate, stale, partial,
  missing? Where is the gap between documented intent and observed
  behavior widest?
- What is the test coverage profile — unit, integration, end-to-end?
  Where is the coverage strong and where is it performative
  (tests exist but exercise trivial paths)?
- What is the technical debt inventory the team already knows about?
  What debt becomes visible only through code-level analysis?
- How queryable is the current documentation — can AI answer
  practical questions about the system from the documentation alone,
  or does every real answer require reading code?
- How easy is it for a new contributor to become productive? What is
  the measured or anecdotal ramp-up time?

### 3. Economics
- What does the system currently cost to run — infrastructure,
  licensing, third-party services, operational labor, on-call burden?
- What does the system currently cost to change — measured in lead
  time for changes, deployment frequency, change failure rate, mean
  time to recovery? These four metrics describe the real economics
  of ongoing work more accurately than headcount.
- Where are costs growing disproportionately to usage? Where are
  vendor lock-in or license-renewal risks concentrated?
- What is the realistic cost envelope for improvement — not just
  dollars, but team capacity, tolerance for regression, and
  acceptable disruption to live operations?

### 4. Operations
- How is the system currently deployed and operated? Is the
  deployment process documented, automated, reproducible, or
  dependent on tribal knowledge?
- What is the observability posture — what is logged, what is
  monitored, what is alerted on? What questions can operators
  answer from dashboards today and what questions require
  code-reading or database spelunking?
- What is the incident history — frequency, severity, root causes?
  What classes of incident have been recurring?
- What are the current scaling limits, known or suspected? Where
  has the system been pushed to its limits, and what broke?
- What integrations exist — inbound and outbound — and what are
  their reliability and contract characteristics?

### 5. Scoring & Metrics
- What quantitative measurements does the team currently have for
  system health — performance, reliability, security posture,
  cost, quality?
- Where are the benchmarks missing? Where are they present but
  stale, unmeasured, or unenforced?
- What baselines must be captured **now** — before improvement
  begins — so improvement can be measured rather than asserted?
  Every improvement project needs a before-picture.
- What comparable-system or industry benchmarks should the
  improved system be measured against?

### 6. Correctness Verification
- Where does observed system behavior diverge from documented
  intent? Where does implementation diverge from interface
  contracts?
- Are the claims the practitioner makes about the system
  ("we already encrypt data at rest," "the API is versioned")
  verifiable against the code and the running system — or are
  they beliefs? Verify before accepting.
- Are sources (documentation, tickets, postmortems, runbooks)
  dated? Is their currency known?
- Are discovery gaps — sections of the codebase, operational
  practices, or user workflows that were not inspected —
  explicitly documented rather than silently omitted?

---

## Multi-Repo Evidence Scoping

*New in v1.1.* Existing-project work frequently involves more than
one repository. A library may be the subject of the improvement
cycle, but its dev-env, its consumers, its peer plugins, and its
shared DevContainer all carry evidence that Phase 1 may need. The
tool set handles this by classifying every repository touched in
Phase 1 into one of three roles and applying different discipline
to each:

| Role | Meaning | Evidence posture |
|------|---------|-----------------|
| **Subject** | The repository being improved. Every MC-class register entry must trace to this repo's code, config, tests, docs, or CI. | Full inspection. All findings in-scope. |
| **Integration Peer** | A separate repository the subject integrates with as part of its core usage contract (e.g., a Hardhat plugin peer, an API gateway service, a shared client SDK). Findings about it are in-scope only where they bear on the subject's behavior. | Inspect the integration surface. Note peer-internal findings as context, not as subject findings. |
| **Evidence Source** | A repository used during Phase 1 to ground subject findings (e.g., a monorepo that embeds the subject as a submodule, a dev-env repo with shared infra). Findings are not improvement scope for this cycle. | Read for evidence only. Quote facts; do not propose changes. |

### Establishing roles during Specify

During the initial Specify interview (before Step 01), the AI must
explicitly ask:
- Which repositories will be touched during Phase 1?
- For each: is it the Subject, an Integration Peer, or an
  Evidence Source?

Record the classification in the Discovery Specification. If the
classification changes mid-phase (typical: an Integration Peer
turns out to need improvement too), flag it and ask whether scope
is expanding — do not silently widen scope.

### Cross-Repo Mode discipline

When working across repos, tag every code-derived finding with
one of three flags:

- **[CONFIRM]** — AI has inspected the source (file path, commit,
  line range) and is confident. No practitioner verification
  required.
- **[AWARE]** — AI is aware of this from context, practitioner
  testimony, or search-results summary but has not confirmed
  against current code. Practitioner should verify before it
  enters a final artifact.
- **[QUESTION]** — AI has a specific question that code inspection
  or practitioner testimony would answer. Listed for the
  practitioner to resolve.

Use these flags in interview questions and in draft artifacts.
They make the evidence-basis distribution (Step 06 §12) legible
and prevent "plausible-sounding AI summary" claims from entering
the final report without traceability.

### Three resolution options for ambiguous evidence

When a finding is suggested by multiple repos or when the
boundary between Subject and Peer is unclear:
1. **Practitioner-confirm** — pause the interview and ask which
   repo is authoritative for this finding.
2. **Scope narrowing** — if the finding is only indirectly in
   scope, demote it to a [QUESTION] or drop it entirely with a
   note in the gap register.
3. **Remove evidence-source repos** — if an Evidence Source repo
   is providing more noise than signal, explicitly remove it from
   Phase 1 scope and re-classify findings without it.

---

## Code Access Calibration

*New in v1.1.* AI sessions running this tool set have varying levels
of direct code access. The discipline differs by mode. At the start
of each Phase 1 run (during Specify, before Step 01), the AI must
select and announce a code-access mode:

| Mode | When to use | Discipline |
|------|-------------|-----------|
| **Interview-only** | No direct code access (no MCP, no Claude Code, no repo attachment). Practitioner describes the system; AI synthesizes. | All findings tagged as practitioner-testimony with Medium or Low confidence. Code verification listed as Phase 1 follow-up or Phase 2 design input. Use the [AWARE]/[QUESTION] flags liberally. |
| **Search-primary** | Project knowledge or `project_knowledge_search` is available but not full filesystem. | AI can cite file excerpts. Finding confidence can reach High when source is cited. Still verify practitioner claims against searchable project knowledge before accepting. [CONFIRM] flag requires a citable excerpt. |
| **Hybrid with explicit flags** | Mixed: some repos searchable, some only described; or MCP connectors enable partial direct access; or Claude Code for the subject but not for peers. | AI uses [CONFIRM]/[AWARE]/[QUESTION] flags on every code-derived finding to make the evidence source explicit. Findings without flags carry Medium confidence by default. |

Announce the mode clearly at the start of the interview. Do not
silently downgrade to Interview-only mid-phase when a search fails
— say so, flag the affected finding, and continue.

---

## Three-Timeframes Worked Example

*New in v1.1.* The three-timeframes discipline (Observed /
Documented Intent / Desired Future) is the single most important
discipline in existing-project work, and also the easiest to
collapse under time pressure. A worked example clarifies it.

**Setup.** A subject library contains a `scripts/devops/` directory
with ~15 shell scripts for SLSA provenance validation, container
registry management, and supply-chain risk assessment. All scripts
are syntactically valid, recently edited, and reference current
tooling (Sigstore, OCI registries, 2025-era CI patterns).

**Naive assessment (wrong).**
> *"The subject has a mature devops automation scaffold for
> supply-chain security, reflecting industry-current practice."*

This collapses all three timeframes into one. The scripts *look*
current (Observed), so the AI assumes they *are* current in the
sense of being operationally integrated (Documented Intent) and
that they're *intended to stay* (Desired Future).

**Three-timeframes assessment (correct).**
- **Observed (current):** Scripts exist in `scripts/devops/` with
  recent syntactic validity. They are not referenced by any CI
  workflow, husky hook, or README. `git log` shows they were
  copy-in from a different project ~4 months ago in a single
  commit. `grep -r "scripts/devops"` across the repo returns
  zero consumers.
- **Documented Intent:** None. No ADR mentions them; the README
  is silent; they appear in no runbook.
- **Practitioner input (when queried):** "Oh — those. I copied
  them from gnus-dao for inspiration and forgot about them.
  They were never wired up here."
- **Desired Future:** Retire them. They add to the codebase's
  cognitive surface, obscure what is actually production-
  current, and will fail maintenance reviews.

**The mechanism.** *Looking current* is not *being current*.
Orphan code inherits the stylistic datestamp of its origin but
carries zero operational weight. Every "looks current" observation
in an existing-project inspection must be paired with a "is wired
up" verification before the observation becomes a finding. Wiring
checks include: consumer grep, CI reference, test reference,
documentation reference, and commit-history provenance.

This example recurs as a structural test in interviews: when a
piece of the codebase looks current, ask explicitly whether it
is wired up and to what.

---

## Version & Identity Re-Verification

*New in v1.1.* At the start of each step beyond Step 01, the AI
must re-verify:
- The subject's current published version or identity (package
  version, service version, release tag, or equivalent)
- The subject's repository location and main-branch state
- The subject's ecosystem peer identities (integration peers,
  evidence source repos) — changed since last step?

One targeted search or one practitioner-confirmation is
sufficient. The cost is small; the value is avoiding drift when
the subject releases between steps, gets renamed, or acquires new
peers mid-phase.

This discipline originated in a dogfooding run where Step 01
stated the subject was at "v1.2.1" based on stale search results,
while Step 02 pre-interview verification caught "v1.3.2" as the
actual current version. Steps 02–06 were clean; Step 01 required a
correction patch. Version re-verification at each step start
prevents this class of drift.

---

## Interview Mode Selection

*New in v1.1.* Not every step benefits from the same interview
shape. Discovery-heavy steps (mostly Step 01 and Step 02) gather
raw evidence and benefit from **question-by-question** interviewing
— the AI asks one question, practitioner responds, AI follows up
with specificity, and the artifact accretes gradually. Decision-
heavy steps (Step 03, Step 04, Step 05) transform accumulated
evidence into categorized decisions and benefit from
**draft-and-react** mode — the AI proposes a draft register or
categorization based on prior artifacts, practitioner reacts to
specific entries (accept, amend, reject), and the artifact
converges quickly.

| Step | Mode | Why |
|------|------|-----|
| Step 01 — Tech & Architecture Assessment | Question-by-question | Raw stack discovery; practitioner testimony is primary input |
| Step 02 — Operational & Performance Baseline | Question-by-question (with command-execution requests) | Raw measurement; practitioner runs commands, AI folds output in |
| Step 03 — Requirements & Improvement Objective | Draft-and-react | Registers (MK, MC, NTI, IC) are categorization decisions |
| Step 04 — Risk / Constraint / Technical Debt | Draft-and-react | Registers are classification decisions across existing evidence |
| Step 05 — Reusable / Replaceable Catalog | Draft-and-react | Per-component dispositions are classification decisions |
| Step 06 — Information Report Synthesis | Synthesis-only (no interview) | Action prompt; no interview shape |

**Practitioner rejection is high-signal architectural input.** In
decision-heavy steps running draft-and-react mode, a practitioner
who rejects a draft entry is providing more than a correction —
they are signaling an architectural constraint, domain knowledge,
or ecosystem context the AI lacked. Treat rejection with the same
weight as a new primary source. Ask why, update the register, and
propagate the implication to other pending entries.

Announce the interview mode at step start. If the step is decision-
heavy and the practitioner prefers question-by-question (or vice
versa), adapt — but surface that the default has been overridden,
because mode selection affects artifact shape.

---

## Behavioral Rules

These rules apply to every AI session in this phase.

**Conduct structured interviews; do not accept stream-of-consciousness
context dumps.**
Ask one question at a time in discovery-heavy steps. In decision-
heavy steps, present one draft section at a time. Wait for a response
before proceeding. Use follow-up questions to push for specificity
when answers are vague. The goal is a structured discovery
specification — not a transcript of raw answers.

**Treat the codebase as a primary source, not a supplement.**
When documentation, memory, and code conflict, the code is authoritative
as a description of current behavior. Stated intent is valuable but
cannot override observed reality. When code-level investigation is
needed to answer a question, say so explicitly — do not guess from
secondary signals.

**Distinguish the three timeframes.**
Every claim about the system must be tagged — explicitly or by section —
as one of:
- **Current state (observed)** — verified against code, telemetry, or
  operator testimony
- **Documented intent** — from specifications, ADRs, prior design
  documents (may or may not match current state)
- **Desired future state** — the improvement goal

Collapsing these categories silently is the most expensive mistake in
existing-project work.

**Surface gaps proactively.**
If practitioner responses leave a Core Principle dimension unaddressed —
or leave a part of the system uninspected — flag it explicitly before
moving forward. Example: *"We have good coverage of the API layer, but
the batch processing pipeline hasn't been inspected. Should we add it
to scope, or explicitly defer it?"*

**Separate evidence from assumption.**
Clearly distinguish verified information (observed in code, confirmed
by running system, cross-referenced against telemetry) from assumed
or inferred information. Never present inference as fact. In
existing-project work this is especially critical because practitioners
often have strong, confident beliefs about systems they have not
recently inspected.

**Never skip Correctness Verification.**
AI can read a codebase fast but not infallibly. Before any finding
enters the Information Report: source identified (file, commit, ticket,
dashboard), date checked, claim cross-referenced where possible. Low-
confidence findings are included but clearly labeled — never silently
omitted. Where claims cannot be verified from available evidence, mark
them as unverified and list them as discovery follow-ups.

**Do not propose solutions, migrations, or re-architectures in this
phase.**
Phase 1 (existing-project) discovers and structures the current state
and sharpens the improvement objective. Phase 2 evaluates options and
makes improvement decisions. Flag tensions, pain points, risks, and
candidate improvement areas — but do not prescribe remediation.

**Distinguish "broken" from "different."**
Not every oddity in the codebase is technical debt. Some reflect
constraints the team has forgotten, compliance decisions, or
integrations with systems the practitioner no longer thinks about.
Before classifying something as a problem, ask whether it is
intentional. Frame findings neutrally and let the practitioner
classify.

**Re-verify subject version and identity at each step.**
Apply the Version & Identity Re-Verification discipline described
above at the start of every step beyond Step 01. One targeted
check is sufficient.

**Handle MCP connector activation gracefully.**
If an MCP tool is expected but not found when first attempted:
(a) attempt access once, (b) if tools not returned, report the
specific missing tool to the practitioner clearly and ask them to
confirm activation, (c) retry once when the practitioner confirms.
Do not make the practitioner debug MCP configuration themselves.
If the tool is still unavailable after one retry, downgrade the
code-access mode and continue with appropriate confidence
adjustments — do not block the interview.

**Structure all outputs for AI consumption.**
The Information Report will be consumed by AI in every subsequent
phase. Use consistent machine-parseable headers, tables for
comparative data, labeled sections with clear semantic meaning,
metadata (sources, dates, confidence levels), and cross-references
between related sections.

---

## Phase 1 (Existing Project) Artifacts

Five research artifacts are produced through conversational interview
prompts. A sixth prompt synthesizes all five into the final Information
Report. The synthesis prompt operates differently — it is an action
prompt, not an interview. The practitioner pastes all completed
artifacts in and the AI synthesizes and self-evaluates in a single
pass.

Before Step 01, the practitioner runs the **Building Block Discovery**
prompt (`step-00b-building-block-discovery.prompt.md`) to inventory
the AI capabilities — MCP connectors, Skills, specialized agents,
direct code access — available for this Phase 1 run. The resulting
toolset-augmentation document informs interview-mode and code-access
decisions throughout Steps 01–06.

The five artifacts mirror the greenfield set conceptually but are
reoriented around existing-system evidence:

| Artifact | Type | SDD Step | Existing-Project Focus |
|----------|------|----------|-----------------------|
| Discovery Specification | *(no standalone prompt)* | Specify | What we need to learn about the existing system, and what the improvement objective is |
| Toolset Augmentation Document | *(step-00b prompt)* | Specify | Which AI capabilities are available for this run |
| Discovery Plan | *(no standalone prompt)* | Plan | Sections of inquiry across the existing system |
| **Current-State Technology & Architecture Assessment** | Interview → Action | Implement | What the system is actually built from, as deployed — languages, frameworks, runtimes, data stores, services, versions, deployment topology |
| **Operational & Performance Baseline** | Interview → Action | Implement | How the system actually behaves in production — reliability, performance, cost, incident history, observability state |
| **Requirements & Improvement Objective Sketch** | Interview → Action | Implement | What the system must continue to do, what it must do differently, and what the improvement objective is — separated cleanly |
| **Risk, Constraint & Technical Debt Inventory** | Interview → Action | Implement | Current compliance posture, known debts, live risks, and hard constraints on change (regulatory freeze windows, contractual SLAs, team capacity) |
| **Reusable & Replaceable Components Catalog** | Interview → Action | Implement | What in the current system is worth keeping, what should be replaced with off-the-shelf or managed alternatives, what should be retired |
| **Current-State Information Report** | **Action + Evaluation** | Implement | Synthesis + self-evaluation; the Phase 1 → Phase 2 handoff |

> Naming convention: the existing-project prompt files are named in
> parallel with the greenfield set — e.g.,
> `step-01-current-state-technology-architecture-assessment.prompt.md`
> — and live in a sibling directory
> (`toolkit/phase-01-information-gathering-existing-project-toolset/`).

---

## Phase Gate: The Self-Evaluation Scorecard

The synthesis prompt contains a built-in self-evaluation that the AI
runs immediately after producing the Current-State Information Report.
This is the phase gate that determines whether Phase 1 is complete
and Phase 2 can proceed.

The scorecard evaluates the Information Report against all six Core
Principles and produces a gate status for each:

| Gate Status | Meaning | Phase 2 Action |
|-------------|---------|---------------|
| **PASS** | Sufficient for Phase 2 to proceed on this dimension | Proceed |
| **CONDITIONAL** | Sufficient with documented caveats; specific gaps must be addressed within Phase 2 before relevant decisions are made | Proceed with remediation plan |
| **FAIL** | Insufficient; Phase 2 cannot responsibly proceed on this dimension | Cycle back to Phase 1 |

### What Each Gate Evaluates (Existing-Project Variant)

**Security — PASS requires:**
Current compliance posture documented with evidence (not claims),
live threat surface enumerated from the actual deployment topology,
known vulnerabilities in the current dependency graph inventoried,
historical security incidents summarized with root causes and
remediation status. If this gate fails, Phase 2 cannot responsibly
plan security improvements — it will be optimizing for threats it
hasn't actually identified.

**Maintainability — PASS requires:**
Documentation accuracy assessed (not just existence), test coverage
profile measured with current numbers, known technical debt
inventoried with code-level grounding, contributor ramp-up friction
documented. If this gate fails, Phase 2's improvement scope will
miss the work that actually makes the system sustainable.

**Economics — PASS requires:**
Current run-cost measured (infrastructure, licensing, third-party,
operational labor), change-cost indicators captured (deployment
frequency, lead time, change failure rate, MTTR where available),
realistic improvement-budget envelope defined. If this gate fails,
Phase 2 cost modeling will project improvements against unmeasured
baselines and produce unreliable ROI estimates.

**Operations — PASS requires:**
Current deployment topology documented, observability state
assessed (what is logged, monitored, alerted — and what is not),
incident history summarized, known scaling limits documented,
integration inventory complete. If this gate fails, Phase 2 cannot
plan operational improvements because the current operational
surface is unclear.

**Scoring & Metrics — PASS requires:**
Baseline measurements captured for the dimensions the improvement
is intended to move — before improvement begins. Qualitative
claims ("the system is slow," "deploys are painful") are replaced
with measurements. If this gate fails, improvement success will
be asserted rather than demonstrated, and regressions introduced
during improvement will be invisible.

**Correctness Verification — PASS requires:**
Every significant claim about current state is verified against the
codebase, telemetry, or documented evidence — or explicitly marked
as unverified. Divergence between documented intent and observed
behavior is surfaced rather than reconciled. Confidence levels
(High / Medium / Low) assigned throughout. Discovery gaps listed
explicitly. If this gate fails, Phase 2 will be planning
improvements against a current-state picture that may not reflect
reality.

### Gate Logic

A single FAIL gate does not block all of Phase 2 — it blocks Phase 2
on that specific dimension. The team must cycle back to the relevant
Phase 1 artifact prompt, fill the gap, and re-run synthesis before
Phase 2 makes decisions in that area.

CONDITIONAL gates allow Phase 2 to proceed with documented caveats.
Each conditional pass must have a named remediation action, a
responsible owner, and a target date. Conditional passes that
accumulate without remediation degrade into silent failures over time.

**A FAIL gate is not a failure of the process — it is the process
working.** It means a gap was caught here, in Phase 1, where it costs
an hour of additional discovery, rather than in Phase 4 or Phase 5,
where it costs weeks of rework when the improvement plan collides
with an undocumented reality.

Do not skip the scorecard review. Do not treat a CONDITIONAL as a PASS.

---

## Output Standards

All Phase 1 (existing-project) outputs must meet the following before
being considered complete:

- [ ] Every Core Principle has at least one discovery section
      addressing it
- [ ] Every significant claim about current state is tagged as
      **Observed**, **Documented Intent**, or **Desired Future**
- [ ] Every significant claim has a source (file path, commit,
      dashboard, ticket, runbook, operator testimony), a date, and
      a confidence level
- [ ] Code-derived findings use [CONFIRM] / [AWARE] / [QUESTION]
      flags consistent with the declared code-access mode
- [ ] Cross-repo findings tag the source repo and its role
      (Subject / Integration Peer / Evidence Source)
- [ ] Comparative and inventory data is in structured tables, not
      narrative prose
- [ ] Divergences between documented intent and observed behavior
      are surfaced, not reconciled
- [ ] Baseline measurements are captured for every dimension the
      improvement is intended to move
- [ ] Discovery gaps — parts of the system that were not inspected —
      are explicitly documented
- [ ] The improvement objective is stated specifically enough to
      drive Phase 2 decisions (not "modernize" but e.g. "reduce
      change-failure-rate from 22% to under 10% and eliminate the
      four recurring incident classes on the authentication path
      within two release cycles")
- [ ] The Information Report is structured for AI consumption
      (consistent headers, labeled sections, tables, metadata)
- [ ] No principle dimension has been silently omitted — gaps are
      documented, not ignored
- [ ] The self-evaluation scorecard has been reviewed and all gate
      statuses are documented before Phase 2 begins

---

## Common Pitfalls

**Discovering without specifying.**
The greenfield pitfall applies here too: starting code-reading,
dashboard-browsing, and interviewing without defining what needs to
be discovered produces a sprawling, unfocused report. The Specify
step — which in existing-project work *must* include sharpening the
improvement objective — is not overhead.

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
the code or the running system.

**Collapsing the three timeframes.**
Mixing observed current behavior, documented intent, and desired
future state produces improvement plans that fix symptoms rather
than causes. Keep them distinct in every artifact. The worked
example above (orphan `scripts/devops/` directory) shows how easy
the collapse is.

**Classifying differences as defects prematurely.**
Unfamiliar patterns in the codebase are not automatically technical
debt. Ask before labeling. Some oddities encode forgotten
constraints, compliance obligations, or integrations that the
practitioner no longer routinely thinks about.

**Letting subject version drift between steps.**
Version drift between Step 01 and later steps is common when the
subject releases during the Phase 1 run. Apply the Version &
Identity Re-Verification discipline at each step start.

**Silently downgrading code-access mode.**
If an expected MCP tool or code-access mechanism fails, do not
quietly proceed as if it didn't. Announce the downgrade, adjust
confidence levels on affected findings, and continue. Silent
downgrade produces artifacts whose evidence basis is
misrepresented.

**Skipping the baseline capture.**
If Phase 1 does not measure the dimensions the improvement is meant
to move, the improvement's success will be asserted rather than
demonstrated, and regressions introduced during improvement will be
invisible. Baselines are not optional for existing-project work —
they are the evidence against which improvement is judged.

**Letting the improvement objective stay vague.**
"Modernize the stack," "fix the tech debt," and "improve
performance" are starting points, not objectives. A vague objective
produces a vague Phase 2 and an unfocused Phase 3. Sharpen the
objective in this phase.

**Proposing solutions in this phase.**
The temptation is strong in existing-project work — the problems
are visible and the fixes seem obvious. Resist. Phase 1 discovers
and structures; Phase 2 decides. Surfacing a candidate improvement
area is in scope. Prescribing a solution is not.

**Producing a report that serves humans but not AI.**
Narrative prose buried in unstructured sections is insufficient for
downstream AI consumption. Structure, label, and format every
output for machine parseability alongside human readability.

**Dismissing a CONDITIONAL gate as close enough.**
A CONDITIONAL gate means Phase 2 has a documented dependency — a
gap that must be filled before a specific class of decisions can
be made. Ignoring it does not make it go away. It surfaces later,
when it is more expensive to address.

---

## Connecting to Phase 2

The Current-State Information Report is the primary handoff artifact
from Phase 1 to Phase 2 for existing projects. When the Phase 2 tool
set activates, the report becomes a resource in that tool set — the
AI starts from the structured current-state findings here, not from
zero.

In existing-project work, Phase 2 transforms this evidence into an
**improvement plan**: scoped, sequenced, cost-modeled, risk-assessed,
and measurable against the baselines captured in Phase 1. Phase 2
does not re-discover the system. It analyzes, evaluates, and decides
— using the Current-State Information Report as the evidence base.
The quality of Phase 1 directly determines the quality of Phase 2.

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| v1.0 | 2026-04-18 | Initial authoring | Initial existing-project variant derived from greenfield instructions. |
| **v1.1** | **2026-04-20** | **Diamonds dogfooding run** | Added Multi-Repo Evidence Scoping section (Subject/Integration Peer/Evidence Source classification, [CONFIRM]/[AWARE]/[QUESTION] flags). Added Code Access Calibration section (Interview-only / Search-primary / Hybrid modes). Added Three-Timeframes Worked Example (orphan scripts pattern). Added Version & Identity Re-Verification discipline. Added Interview Mode Selection section (question-by-question for discovery-heavy, draft-and-react for decision-heavy). Added MCP connector activation retry pattern to Behavioral Rules. Added reference to step-00b Building Block Discovery. Expanded Output Standards with code-access-flag and cross-repo-tag requirements. |
