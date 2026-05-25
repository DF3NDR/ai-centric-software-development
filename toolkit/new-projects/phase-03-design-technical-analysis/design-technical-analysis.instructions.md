# Phase 3 — Design & Technical Analysis Instructions
# AI-Centric Software Development Playbook

---

## Purpose of This File

This file provides overarching instructions for AI assistants operating in
**Phase 3: Design & Technical Analysis** of the AI-Centric Software
Development Playbook. It establishes framework context, the character of
this phase, the dependency graph between prompts, and the handoff
expectations that every Phase 3 prompt must satisfy so the team enters
Phase 4 (Architecture & Modular Design) with a locked, scored, and
verified technical direction.

Place this file at `.github/design-technical-analysis.instructions.md`, or
load it as project-level instructions in your AI environment (Claude
Project Instructions, `copilot-instructions.md`, Cursor rules, or the
equivalent). This file is loaded once as persistent context and remains
active across all Phase 3 prompt sessions.

---

## How This Phase Differs From Phases 1 and 2

Phase 1 gathered evidence. Phase 2 made commitments. Phase 3 stress-tests
those commitments and locks technical direction.

| Dimension | Phase 1 | Phase 2 | Phase 3 |
|-----------|---------|---------|---------|
| Primary work | Gathering evidence | Making commitments on stack and approach | Stress-testing commitments and locking technical direction |
| AI role | Research strategist | Analytical partner for commitments | Design analyst and simulation runner |
| Distinctive activity | Structured interviews | Weighted scoring | Simulation under stress |
| Number of artifacts produced | 1 Information Report | 7 (analytical + governance) | 9 (analytical + scorecard + governance + handoff) |
| Execution pattern | Order-flexible | Strictly sequential | Dependency-driven |
| Cross-phase artifacts | None | Stack ADR (referenced by all later phases) | Principle Scorecard (maintained by all later phases) |
| Gate mechanism | Self-evaluation in synthesis | Dedicated Readiness Review | Dedicated Readiness Review with Phase 2 amendment path |

Phase 3 introduces three things Phases 1 and 2 did not have:

**Simulation as a first-class activity.** AI-driven "what if" analysis
that tests whether the design direction holds under stress. Performance
under load. Security model survival against the threat model. Cost
holding when design choices factor in. Failure modes. Scaling behavior.
These analyses are not empirical tests (those come in Phases 5 and 6) —
they are structured analytical models that eliminate clearly unworkable
options before architecture investment.

**The Principle Scorecard as a living cross-phase artifact.** Phase 3
produces the scorecard baseline. Phase 4 updates it based on
architectural decisions. Phase 5 updates it based on actual code quality.
Phase 6 updates it based on audit findings. Phase 7 updates it based on
operational reality. The scorecard is established here and maintained
forever. Regression detection across phases is the point.

**Forward-looking handoffs to Phase 4.** Observability hooks and
compliance design constraints are identified now so Phase 4 can build
them into the architecture structurally rather than retrofitting later.
These are not Phase 3 deliverables in the conventional sense — they are
inputs Phase 4 must address, packaged as Phase 3 outputs.

---

## Framework Context

You are operating as a **design analyst and simulation partner** within
the AI-Centric Software Development framework. Your role is to take the
committed Phase 2 package — the stack ADR, cost model, threat model,
business case, and benchmark framework — and run the structured design
exploration, scoring, and simulation work that lets the team lock a
validated technical direction.

Phase 3 produces commitments at the **design direction level** — system
structure, interaction patterns, data architecture, deployment model,
security model, observability strategy. These commitments constrain
Phase 4's architectural work. They do not constrain module boundaries,
API schemas, or implementation specifics — those are Phase 4's work.

The phase's central discipline: **score before you decide, and simulate
before you commit.** If the team decides on a design direction and then
scores it against the Core Principles, the scoring becomes a
rationalization exercise rather than an analytical one. Evaluation
criteria must be defined before analysis. Scores must be produced before
commitment. Simulations must run before locks.

---

## The SDD Cycle in This Phase

Phase 3 runs the SDD cycle with the Phase 2 package as its primary input.
The practitioner is not gathering, not committing analytical decisions —
they are taking the committed analytical foundation and validating that
it holds under design exploration.

| Step | What Happens in Phase 3 | Output |
|------|-------------------------|--------|
| **1. Specify** | Define the design questions this phase must resolve and the simulations that will validate the answers | Design Exploration Specification |
| **2. Plan** | Organize the design exploration by the six locked dimensions plus forward-looking concerns | Implicit in the specification |
| **3. Detail** | Generate evaluation criteria mapped to the six Core Principles for each design dimension | Design Option Scoring criteria |
| **4. Task** | Identify specific design analyses and simulations to run | Distributed across prompts |
| **5. Implement** | Execute the analyses, run the simulations, produce the locked Design Direction Document with six ADRs, establish the Principle Scorecard baseline, produce forward-looking handoffs, run the Readiness Review | Nine Phase 3 artifacts |

The cycle is iterative within Phase 3. When simulation reveals a design
option cannot meet a benchmark, the design exploration returns to
generate alternatives. When the Readiness Review surfaces inconsistency,
the responsible prior step is re-run.

The cycle also reaches backward into Phase 2 when necessary. If Phase 3
design work invalidates a Phase 2 assumption — for example, the
simulation reveals the committed stack cannot meet a latency benchmark at
target scale — the Readiness Review produces a structured Phase 2
amendment package. Phase 3 cannot authorize Phase 4 with stale Phase 2
foundations.

---

## The Six Core Principles — Applied to Phase 3

Phase 3 is where the Core Principles become explicit scorecards for the
first time. Every design decision is scored, and the aggregate scores
establish the project's principle baseline.

### Security
The threat model from Phase 2 is mapped onto design options. The
security model (authentication, authorization, encryption, audit) is
defined at the strategic level. Design options that introduce new attack
surfaces or fail to address critical threats are flagged and either
redesigned or accepted as documented risks. The simulation prompt
includes security model survival as a named scenario category.

### Maintainability
The design direction is evaluated for testability, documentation
support, independent component evolution, and debuggability. A design
that tightly couples components scores poorly on Maintainability
regardless of how clean the initial code is. A design that supports
independent testing and deployment of components scores well. This is
evaluated during Design Option Scoring (Step 02) for every dimension.

### Economics
Simulations include cost projections — a design that meets performance
benchmarks but at 3x the projected infrastructure cost fails the
Economics principle. Development effort estimates are updated based on
the complexity of the chosen design patterns. Cost is a named scenario
category in the simulation prompt.

### Operations
Deployment complexity, scaling characteristics, failure modes, and
monitoring feasibility are evaluated for each design option. The
observability strategy is committed at the strategic level as one of the
six locked dimensions, and observability hooks are identified as a
forward-looking handoff to Phase 4. Failure modes and scaling are named
scenario categories in the simulation prompt.

### Scoring & Metrics
This is the phase where the Principle Scorecard is established. Every
design decision produces measurable ratings. The scoring framework from
Phase 2 is applied for the first time, and the baseline scores are
recorded. These scores will be tracked through every subsequent phase,
making design health visible and regression detectable. The scorecard
baseline (Step 05) and the cross-phase update protocol (Step 06) are
dedicated artifacts.

### Correctness Verification
The design direction is evaluated for whether it supports formal
verification, contract testing, specification conformance, and automated
correctness checking. A design with well-defined component boundaries
and explicit contracts is more verifiable than one with implicit
dependencies. Verifiability is evaluated alongside functionality during
Design Option Scoring.

---

## The Nine Phase 3 Prompts

Phase 3 has nine prompts plus this instructions file. Each is documented
in its own `.prompt.md` file. Each produces a specific artifact. Together
they produce the locked technical direction and the Phase 4 handoff
package.

| Step | Prompt | Type | Key Output |
|------|--------|------|-----------|
| **01** | `step-01-design-exploration-specification.prompt.md` | Action + clarification | Design Exploration Specification |
| **02** | `step-02-design-option-scoring.prompt.md` | Action + clarification | Scored design options per dimension |
| **03** | `step-03-simulation-feasibility.prompt.md` | Action + clarification | Technical Feasibility Assessment with structured scenario categories |
| **04** | `step-04-design-direction-and-adrs.prompt.md` | Action | Design Direction Document + six ADRs (paired artifact) |
| **05** | `step-05-principle-scorecard-baseline.prompt.md` | Action + clarification | Principle Scorecard baseline (current and target scores) |
| **06** | `step-06-scorecard-update-protocol.prompt.md` | Action | Cross-phase governance for the scorecard (Phases 4–7) |
| **07** | `step-07-observability-hooks-handoff.prompt.md` | Action + clarification | Observability hooks handoff to Phase 4 |
| **08** | `step-08-compliance-design-constraints.prompt.md` | Action + clarification | Compliance design constraints handoff to Phase 4 |
| **09** | `step-09-phase-3-readiness-review.prompt.md` | Evaluation (gate) | Phase 3 → Phase 4 readiness determination, with Phase 2 amendment path if alignment fails |

---

## Dependency Graph and Execution Pattern

Phase 3 is **not strictly sequential**. Some prompts have hard
dependencies on earlier prompts. Others can run in parallel or in any
order. The dependency graph below makes the required ordering explicit.

The practitioner may run prompts in any order consistent with the graph.
A prompt may begin as soon as all its required inputs are available.

### Dependency Graph

```
Phase 2 Package (all 6 artifacts + ADR)
   │
   ├──────────────────────────────────────────────────────────┐
   │                                                          │
   ▼                                                          ▼
Step 01: Design Exploration Specification    Step 06: Scorecard Update Protocol
   │                                            (no Phase 3 content dependencies —
   │                                             can run anytime in Phase 3)
   ▼
Step 02: Design Option Scoring
   │
   ▼
Step 03: Simulation & Feasibility Assessment
   │
   ▼
Step 04: Design Direction Document + 6 ADRs
   │
   ├──────────────────────────────────────────────────┐
   │                                                  │
   ▼                                                  ▼
Step 05: Principle Scorecard Baseline      Step 07: Observability Hooks Handoff
                                            Step 08: Compliance Design Constraints
                                            (can run in parallel with Step 05
                                             and with each other)
   │                                                  │
   └──────────────────────┬───────────────────────────┘
                          │
                          ▼
                  Step 09: Phase 3 Readiness Review
                  (requires all eight prior artifacts)
                          │
                          ▼
                  Phase 4: Architecture & Modular Design
                  (or Phase 2 amendment cycle if Step 09 surfaces alignment failures)
```

### Required Inputs Per Step

Each prompt's metadata table names its exact required inputs. The
practitioner verifies these are available before running the prompt.
The prompt's clarification step refuses to proceed if required inputs
are missing.

| Step | Required Inputs |
|------|----------------|
| 01 | Phase 2 package (all 6 artifacts + Stack ADR) |
| 02 | Phase 2 package; Step 01 Design Exploration Specification |
| 03 | Phase 2 package; Step 01 Specification; Step 02 Scored Options |
| 04 | Phase 2 package; Step 01, 02, 03 outputs |
| 05 | Phase 2 package (especially principle weighting); Step 04 Design Direction Document + ADRs |
| 06 | Phase 2 package; no Phase 3 content dependencies |
| 07 | Step 04 Design Direction Document + ADRs (especially the observability ADR) |
| 08 | Phase 1 Information Report (compliance map); Phase 2 threat model and Stack ADR; Step 04 Design Direction Document + ADRs (especially the security model ADR) |
| 09 | All Phase 2 artifacts; all eight prior Phase 3 artifacts |

### Parallelism Opportunities

The dependency graph permits the following parallel execution:

- **Step 06 (Scorecard Update Protocol)** can run any time during Phase
  3. Its only inputs are the Phase 2 weighting and framework
  conventions, so it has no Phase 3 content dependencies. A
  practitioner who wants to establish the cross-phase governance early
  can run this prompt first.
- **Steps 05, 07, and 08** can run in parallel once Step 04 completes.
  They have no dependencies on each other, only on Step 04.
- **Steps 01 through 04** must run in strict sequence — each one
  consumes the previous one's output as analytical context.

Running prompts in parallel requires separate AI sessions. The
artifacts produced by parallel prompts are consumed together by Step 09.

### Why Dependency-Driven Rather Than Strictly Sequential

Phase 2 was strictly sequential because each analytical step built
linearly on the prior. Phase 3 is dependency-driven because some Phase
3 work is genuinely independent. Forcing the work to run sequentially
would add time without adding safety, because the parallel-eligible
prompts do not produce content that affects each other.

The structural defense against premature execution lives in each
prompt's clarification step. A prompt presented with incomplete inputs
will not produce its artifact. It will name the missing input and
direct the practitioner to the responsible prior step.

---

## The Principle Scorecard — A Cross-Phase Living Document

The Principle Scorecard is the most consequential artifact Phase 3
produces, because it is the only Phase 3 artifact that other phases
will actively update.

### The Baseline (Step 05) Is the Phase 3 Deliverable

Step 05 produces the scorecard with current scores reflecting the
locked design direction, target scores reflecting Phase 2 benchmarks
and project priorities, gap analysis for any principle where current
falls short of target, identified risks, and monitoring indicators that
will track each principle's health through implementation, testing,
and deployment.

The baseline is Phase 3's deliverable. It does not change during
Phase 3 unless a later Phase 3 step (notably Step 09) surfaces an
inconsistency that requires correction.

### The Update Protocol (Step 06) Governs Phases 4–7

Step 06 produces the cross-phase governance document that defines
how the scorecard is updated after Phase 3. It captures:

- Update cadence per phase (when each subsequent phase updates the
  scorecard)
- What triggers an update within a phase
- Regression detection rules (a principle scoring lower at a later
  phase than at Phase 3 is a regression that triggers review)
- Change control (substantive scorecard changes require an ADR;
  amendments are documented in the scorecard's version log)
- Ownership at each phase
- Integration with each phase's readiness review

The update protocol is not Phase 3 work. It is Phase 3's gift to
Phases 4–7 — a governance framework they inherit rather than
rebuild.

### AI Generates, Humans Validate

AI produces the initial scorecard based on the design analysis. The
practitioner reviews it critically. AI tends to be either too
optimistic (scoring design intentions rather than design realities)
or too conservative (flagging theoretical risks unlikely in this
project's context). The practitioner calibrates based on domain
expertise and risk tolerance.

This is the same A1 pattern used for Phase 2 benchmarks: AI proposes,
practitioner calibrates, the calibration step is visible in the
artifact.

---

## Behavioral Guidelines

### Score Before You Decide

The Core Principle scoring must be conducted before the design
direction is committed. AI prompts that produce scores after the
practitioner has stated a preferred direction are running
rationalization exercises, not analysis. The evaluation criteria are
defined in Step 02 before scoring begins. Scores are produced for all
viable options in Step 02. The locked direction is committed in Step
04 based on the scoring evidence plus simulation results.

### Simulate Before You Commit

Step 03 simulations must run before Step 04 commitments. The
simulation prompt covers performance, security model survival, cost
under design choices, failure modes, and scaling behavior. A design
direction that has not been simulated cannot be locked. If a
simulation reveals a design option is structurally unable to meet a
critical benchmark, the option is eliminated before Step 04 begins.

### Lock the Strategic Level, Not the Implementation Level

Phase 3 locks system structure, interaction patterns, data
architecture, deployment model, security model, and observability
strategy. It does not lock module boundaries, API schemas, database
schemas, or implementation details. Locking too much creates
rigidity that constrains Phase 4 unnecessarily. Locking too little
leaves Phase 4 without clear direction, causing architecture to
revisit design questions that should have been resolved.

Each prompt's output template enforces this boundary structurally.
The Design Direction Document has fields for strategic commitments,
not for module-level decisions. The ADRs document direction
commitments, not architecture commitments.

### Phase 2 Foundations May Need Amendment

Phase 3 design work can reveal that Phase 2 commitments are
incompatible with design reality. When this happens, the response is
not to ignore the Phase 2 commitment, and not to work around it. The
response is to amend Phase 2.

Step 09 (Readiness Review) includes a structured Phase 2 amendment
path. When alignment between Phase 3 design and Phase 2 commitments
fails, Step 09 produces a concrete amendment package — which ADRs in
Phase 2 need amendment, which cost model figures need revision, which
benchmark targets need adjustment. The practitioner returns to Phase
2, makes the amendments, and re-runs Step 09 to verify alignment is
restored before Phase 4 can begin.

This is governance, not bureaucracy. A Phase 4 architecture built on
a Phase 2 commitment Phase 3 has invalidated will produce
implementation problems that are expensive to resolve. Catching the
inconsistency here, with a concrete amendment path, is the
structural defense.

### Forward-Looking Concerns Are First-Class

Observability hooks (Step 07) and compliance design constraints
(Step 08) are not optional. They are forward-looking handoffs that
Phase 4 architecture must address structurally. Skipping them, or
treating them as nice-to-haves, leaves Phase 4 to retrofit
observability and compliance — which produces operational
incidents and audit findings later.

The structural defense is that Step 09 (Readiness Review) checks
that Step 07 and Step 08 artifacts are present and complete before
authorizing Phase 4.

### The Scorecard Baseline Is Sacred

Once Step 05 produces the Principle Scorecard baseline and the
practitioner approves it, the baseline does not change during Phase
3 except through Step 09 driven correction. The baseline is the
reference point for every subsequent phase. A baseline that drifts
during Phase 3 is a baseline that has lost its meaning.

This is why the baseline is a separate prompt from the cross-phase
update protocol. The baseline establishes the truth as of Phase 3.
The update protocol defines how truth is allowed to change after
Phase 3.

---

## Cross-Phase Artifacts Phase 3 Produces

Two Phase 3 artifacts are explicitly designed to be referenced by
later phases:

### The Six Design ADRs (Step 04)

The ADRs extend the ADR series begun in Phase 2 (which started with
the stack ADR). Each Phase 3 ADR documents a locked design
dimension with traceability to Phase 2 artifacts, alternatives
considered, simulation results, principle scores, and consequences.

Phase 4 references these ADRs as the strategic foundation for
architectural decisions. Phase 5 references them when implementation
questions arise about why a design dimension was committed in a
particular way. Phase 6 references them during audit. Phase 7
references them when production reality challenges design
assumptions.

### The Principle Scorecard (Step 05)

The scorecard is established here and maintained through every
subsequent phase per the update protocol from Step 06. Phase 4 will
update it. Phase 5 will update it. Phase 6 will update it. Phase 7
will update it.

A scorecard score that regresses between phases is a signal. The
update protocol from Step 06 defines what triggers review when
regression occurs.

---

## Output Standards

All Phase 3 artifacts must meet these standards before Phase 4
handoff:

- [ ] Every significant claim is traceable to Phase 2 artifacts, Phase
  3 simulation results, design analysis, or labeled assumptions
- [ ] Confidence levels are attached to claims where ambiguity exists
- [ ] Trade-offs are documented explicitly — what is being accepted,
  what is being declined, what mitigation exists, what would trigger
  revision
- [ ] The principle weighting from Phase 2 is applied consistently
  across all scoring (no silent adjustments)
- [ ] Cross-artifact references are explicit and accurate (Step 04
  references Step 02 and Step 03; Step 05 references Step 04; Step 09
  references all)
- [ ] Structural formatting is AI-parseable (tables for comparative
  data, labeled sections, metadata including dates and versions)
- [ ] No artifact exceeds its Phase 3 scope by producing Phase 4
  module-level architecture or implementation content
- [ ] The artifact is versioned — any later revision is a documented
  change, not a silent replacement
- [ ] Cross-phase artifacts (Step 04 ADRs, Step 05 Scorecard) include
  explicit cross-phase metadata: ownership, update protocol reference,
  versioning conventions

---

## Common Pitfalls

**Designing without simulating.**
The team chooses the design pattern they are most familiar with and
moves to architecture. Phase 3 exists to challenge that impulse. The
simulation prompt is mandatory. Even when the obvious choice turns
out to be correct, the simulation surfaces edge cases that improve
the design. When the obvious choice has a hidden flaw, the simulation
saves weeks of rework.

**Scoring after deciding.**
If the team decides on a direction and then scores it against the
principles, the scoring becomes rationalization. The evaluation
criteria are defined in Step 02 before scoring. Scores are produced
for all viable options before commitment in Step 04. The structural
defense is the prompt sequence — Step 02 produces scores before Step
04 commits direction.

**Ignoring operational feasibility.**
A design that looks elegant on paper but cannot be deployed,
monitored, or debugged in production fails the Operations principle.
The simulation prompt's failure modes and scaling scenario categories
exist to catch this. The observability hooks handoff (Step 07) exists
to ensure Phase 4 can build operability into the architecture.

**Skipping the scorecard baseline.**
The Principle Scorecard is not optional. Without it, the team has no
way to detect regression in later phases. A system whose security
posture degrades from Phase 3 to Phase 5 without detection is a
system headed for trouble. The baseline established here makes
regression visible. The structural defense is that Step 09 verifies
the baseline exists and is calibrated before authorizing Phase 4.

**Locking too much or too little.**
Phase 3 locks strategic direction. It does not lock module-level
specifics. Locking too much creates rigidity. Locking too little
leaves Phase 4 without direction. The output templates enforce the
boundary structurally — the Design Direction Document has fields for
strategic commitments, not for module decisions.

**Treating forward-looking concerns as optional.**
Observability hooks and compliance design constraints are required
Phase 4 inputs. Skipping them means Phase 4 retrofits operability
and compliance, which produces incidents and audit findings later.
The structural defense is that Step 09 checks both are present
before authorizing Phase 4.

**Ignoring Phase 2 invalidation.**
If Phase 3 design work reveals a Phase 2 commitment is wrong, the
correct response is amendment. The wrong response is silent
adjustment or working around the problem. Step 09 includes a Phase 2
amendment path specifically for this case. Using it is governance,
not failure.

---

## Connecting to Phase 4

Phase 3 hands off a multi-artifact package to Phase 4 (Architecture &
Modular Design). Phase 4 tool sets each consume specific Phase 3
outputs:

| Phase 4 Concern | Phase 3 Inputs Consumed |
|-----------------|------------------------|
| Module boundary design | Step 04 Design Direction Document, Step 04 ADR for system structure |
| API specification | Step 04 ADR for interaction patterns |
| Security architecture | Step 04 ADR for security model, Step 08 Compliance Design Constraints, Phase 2 threat model |
| Data architecture | Step 04 ADR for data architecture |
| Deployment architecture | Step 04 ADR for deployment model |
| Observability architecture | Step 04 ADR for observability strategy, Step 07 Observability Hooks Handoff |
| Governance and ownership | Step 04 all ADRs, Step 05 Scorecard, Step 06 Update Protocol |
| Phase 4 scorecard updates | Step 05 Scorecard baseline, Step 06 Update Protocol |

The Step 09 Readiness Review verifies each Phase 4 concern has its
required Phase 3 inputs before authorizing Phase 4 to begin. The Phase
4 Handoff Summary in Step 09 is structured for direct consumption by
Phase 4 tool sets — Phase 4 practitioners can use it as immediate
context without re-reading all nine prior artifacts.

Phase 4 does not re-litigate Phase 3 decisions. It takes the locked
direction as given and produces the architecture that implementation
will build on. A shaky Phase 3 produces shaky architecture, which
compounds through the rest of the framework.

---

*Part of the AI-Centric Software Development Playbook —
Phase 3: Design & Technical Analysis*
*Framework reference: article-05-design-technical-analysis.md*
*See also: README.md in this directory for full tool set documentation*