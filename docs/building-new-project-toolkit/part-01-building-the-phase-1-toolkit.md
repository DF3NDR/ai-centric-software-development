# Part 10 — Building the Phase 1 Toolkit
## A Working Session Applying the Framework to Itself

**Series:** AI-Centric Software Development Playbook
**Subseries:** Practice — Working sessions that demonstrate the
framework in application
**Companion:** Article 3 — Phase 1: Information Gathering

---

## What This Article Is

The first nine articles of this series establish the framework. They
describe the methodology, the principles, the phases, the toolkit
philosophy. They are prescriptive — they tell practitioners what to do.

This article is different. It documents the actual working session
that produced the Phase 1 toolkit — seven files (one instructions
file plus six prompt files) that operationalize Phase 1 of the
framework. The working session was conducted in a single Claude
session, building each artifact in turn, with the framework articles
attached as project knowledge.

The article is organized around a single observation that shaped
how the work proceeded:

> **The Phase 1 toolkit was built by applying the framework to itself.**
> The Specification Driven Development cycle structured the construction.
> The six Core Principles filtered the design decisions. The toolkit
> philosophy — building blocks organized into tool sets — produced the
> file structure.

This is not after-the-fact rationalization. The session began with
an explicit decision: if the framework is correct, then the framework
should produce its own tooling well. If applying the framework to
toolkit construction surfaced contradictions or awkward fits, those
were signals to refine the framework — not to abandon it.

The framework held. The article documents how.

---

## Why This Article Exists

Three reasons.

**First, the framework's coherence is testable.** A methodology that
cannot be applied to its own construction is suspect. The session
demonstrated that SDD applied to toolkit construction produces
toolkits, and that the Core Principles applied as filters produce
better toolkit decisions than ad-hoc choice. Reporting this is
evidence the framework works in practice, not only in description.

**Second, practitioners building their own toolkits need a worked
example.** Article 2 (Building Your Toolkit) is conceptual — it
describes the building blocks and tool sets without showing one
being constructed end-to-end. This article shows the construction.
A practitioner building a Phase 1 toolkit for their own context can
use this as a reference for which decisions matter, where the
trade-offs surface, and what completed artifacts look like.

**Third, the structural decisions made during this session are
load-bearing.** Some choices that may look minor in the finished
toolkit — the dual-format data flow representation, the hard
structural scope boundaries, the per-principle weighting — are the
decisions that prevent the toolkit from drifting into anti-patterns
under pressure. Documenting why each was chosen makes the toolkit
maintainable. Future practitioners adapting the toolkit can change
what they want, but they will know which structural defenses they
are removing.

---

## The Session at a Glance

The working session produced seven files in a single Claude session:

| File | Type | Purpose |
|------|------|---------|
| `information-gathering.instructions.md` | Instructions | Persistent project context for all Phase 1 sessions |
| `technology-landscape-assessment.prompt.md` | Interview → Action | What exists in the technology space |
| `competitive-market-scan.prompt.md` | Interview → Action | What others built and what it reveals |
| `requirements-sketch.prompt.md` | Interview → Action | What the system must do |
| `risk-constraint-inventory.prompt.md` | Interview → Action | What could go wrong, what is fixed |
| `reusable-components-catalog.prompt.md` | Interview → Action | What can be adopted rather than built |
| `information-report-synthesis.prompt.md` | Action + Evaluation | Synthesis of all five into the Phase 2 handoff |

The session lasted approximately one work session. The framework's
GitHub repository was attached as project knowledge throughout, so
every decision could be checked against the source articles. This
mattered — several times during the session, a tempting design
choice was rejected after rereading the relevant article and finding
the framework had already considered the trade-off.

---

## Applying SDD to Toolkit Construction

The SDD cycle has five steps: Specify, Plan, Detail, Task, Implement.
The session followed the cycle, with toolkit construction as the
implementation work.

### Specify — Defining What the Toolkit Must Do

The session opened with a question: what does a Phase 1 toolkit
need to be?

Article 3 establishes Phase 1 as information gathering — research
into the technology landscape, competitive environment, compliance
requirements, and project constraints, producing a structured
Information Report. The toolkit's job is to make this work
repeatable and principle-grounded.

The specification that emerged in the first part of the session:

- The toolkit produces five research artifacts plus a synthesis
- Each artifact corresponds to a research domain Article 3 names
- Each artifact applies all six Core Principles as evaluation
  filters
- The synthesis produces the Information Report and includes a
  built-in self-evaluation that determines Phase 2 readiness
- The toolkit is delivered as text files (markdown) to be loaded
  into AI environments — not as code, not as runnable tooling

The specification was not produced as a separate document. It
emerged from the opening conversation and was implicit in the
session's first decisions. In a more formal application of SDD,
this would have been written down as a specification artifact. In
practice, with a single practitioner and a single AI session, the
specification lived in the conversation context and was checked
against the framework articles as needed.

This is a useful observation: SDD's formality scales with
team size and project duration. A single-practitioner session over
a few hours can compress Specify, Plan, Detail, and Task into
conversational decisions, as long as Implement produces artifacts
that can be checked against the framework's standards. A multi-week
team project building a critical toolkit would warrant explicit
specification artifacts at each step.

### Plan — Structuring the Construction

The plan that emerged: build the instructions file first to
establish the framework context, then build the five interview
prompts in the recommended execution order, then build the
synthesis prompt last because it consumes the others.

This order was load-bearing for one reason: each subsequent
prompt could reference and build on the structural patterns
established in the previous one. The first prompt (Technology
Landscape Assessment) made structural decisions about how
interviews unfold, what the output template looks like, how
confidence is captured, how gaps are documented. The next four
prompts inherited those patterns. The synthesis prompt inherited
the consolidated patterns and added the gate evaluation
mechanism.

If we had built the synthesis prompt first or built the prompts
in parallel, we would have lost the structural consistency that
makes the toolkit feel like a coherent set rather than seven
independent files.

### Detail — Generating the Per-Prompt Specifications

For each prompt, the session produced an implicit specification
through clarifying questions. What is this prompt's purpose? What
inputs does it require? What does the output look like? What
behavioral rules govern the AI? What evaluation criteria define
success?

The clarifying questions were asked by Claude during the working
session — not pre-planned, but emerging as the work proceeded. Some
questions had obvious answers from the framework articles. Others
required practitioner judgment. The valuable pattern was that the
clarifying questions surfaced decisions that would otherwise have
been made silently.

For example, when building the threat-model adjacent components of
the Risk & Constraint Inventory, the session paused to ask: should
compliance constraints and security risks be in the same section
or separated? The framework's articles do not give a direct answer.
Practitioner judgment said separate — they are different categories
that require different treatment. The decision was made explicitly
and documented in the prompt's behavioral rules.

This is the SDD Detail step in compressed form: practitioner
judgment applied to surface decisions that the framework does not
prescribe in detail.

### Task — Building Each Artifact

Each prompt was built as a complete artifact in a single response.
The session produced one prompt at a time, in order, with the
practitioner reviewing each before moving to the next.

The "task" in SDD terms was: produce the next prompt in the
sequence, conforming to the structural patterns established by
previous prompts, applying all six Core Principles, and embedding
the design decisions surfaced during clarification.

### Implement — The Artifacts Themselves

The implementation step is the artifacts themselves: seven files,
each a complete, self-contained document with metadata, system
instructions, kickoff line, output format template, evaluation
checklist, and cross-references to companion files.

---

## Applying Core Principles to Toolkit Decisions

The toolkit's structural decisions were filtered through the six
Core Principles. Some decisions trace cleanly to a single principle.
Others sit at intersections.

### Security Filtered the Risk & Constraint Inventory

The most security-consequential decision in the toolkit was in the
Risk & Constraint Inventory: separating compliance constraints from
security risks structurally rather than treating them as siblings
within a single risk register.

The framework's Article 1 (Core Principles) makes clear that
Security covers threat modeling, zero-trust design, continuous audit
hooks, and compliance preparation. These are related but distinct.
Compliance is non-negotiable; risks are negotiable. Conflating them
in a single section causes both to be treated identically — which
typically means compliance gets the analytical depth security risks
deserve, and security risks get the checkbox treatment compliance
demands.

The structural defense: four explicit categories in the Risk &
Constraint Inventory output template — compliance constraints,
security risks, hard constraints, and project/operational risks —
each with its own table, its own treatment, its own behavioral rule.
The AI cannot conflate them because the template does not allow it.

### Maintainability Filtered the Output Standards

Every Phase 1 prompt produces output structured for both human
reading and AI consumption. This is a Maintainability decision —
the framework's Article 1 names "queryable, AI-parseable
documentation" as a Maintainability concern.

Specifically, every output template uses:

- Consistent header structure across artifacts
- Tables for comparative or structured data
- Explicit metadata: source, date, confidence
- IDs on key items so cross-references are stable
- Semantic section labels rather than narrative-only prose

These choices are not stylistic. They are what make the Phase 1
artifacts usable as input to Phase 2 tool sets. A Phase 2 AI loading
the Information Report can parse it because the structure was
designed for parsing. A narrative-only Information Report fails the
Maintainability principle even if it is well-written.

### Economics Filtered the Toolkit Scope

A toolkit can grow indefinitely. Phase 1 alone could plausibly have
ten or twelve artifacts: separate prompts for compliance research,
infrastructure assessment, security tooling evaluation, deployment
options, talent pool analysis, vendor reliability scoring, and so on.

Article 1 names Economics as cost forecasting and resource scaling.
Applied to toolkit construction, the Economics principle asks: what
is the minimum set of artifacts that produces a usable Phase 1
output, and where does adding more produce diminishing returns?

The session settled on five research artifacts plus one synthesis.
Adding more would have produced incremental coverage at significant
cost — each additional prompt requires construction, maintenance,
and practitioner attention every time Phase 1 runs. Five was the
threshold where each artifact carried distinct, non-overlapping
value.

This was a real decision, not a default. Earlier in the session,
there was discussion about whether to build a separate Compliance
Research prompt distinct from the Risk & Constraint Inventory.
Economics-of-toolkit-scope said no — compliance research can be a
section within the Risk & Constraint Inventory rather than a
separate artifact, because the practitioner running Phase 1 will
encounter compliance through the risk lens anyway.

### Operations Filtered the Synthesis Prompt's Design

The Information Report Synthesis is operationally different from
the other six prompts. It is the only action-oriented prompt — the
practitioner pastes completed artifacts in and the AI synthesizes,
rather than the AI interviewing the practitioner.

This was an Operations decision. Article 1 names Operations as
covering scalability, reliability, and governance. Applied to the
synthesis prompt, the question was: how does the Information Report
become trustworthy enough to authorize Phase 2?

Two operational mechanisms:

**A built-in self-evaluation scorecard.** The synthesis prompt
produces the Information Report and immediately scores it against
the six Core Principles, producing PASS / CONDITIONAL / NOT READY
gates. The scorecard is not optional and not separate — it is the
final section of the synthesis output.

**A reverse-format optimized for the next phase.** The Information
Report's structure is designed for Phase 2 tool sets to load as
context. Section 9 (Phase 2 Readiness Inputs) is essentially a
pre-formatted handoff that Phase 2 tool sets can consume directly.

Both mechanisms address operational concerns: how does Phase 1's
output get consumed reliably downstream, and how does the team know
when Phase 1 is actually done?

### Scoring & Metrics Drove the Self-Evaluation Scorecard

The most important single mechanism in the Phase 1 toolkit is the
self-evaluation scorecard at the end of the synthesis prompt. This
is the Scoring & Metrics principle made operational.

The scorecard evaluates the Information Report against six gates:

| Gate | What It Asks |
|------|-------------|
| Security | Is there enough threat and compliance content for Phase 2 to model from? |
| Maintainability | Is documentation quality assessed for candidate technologies? |
| Economics | Is there enough cost data for Phase 2 to model from? |
| Operations | Are deployment and scaling characteristics covered? |
| Scoring & Metrics | Are quantitative benchmarks present, or only qualitative claims? |
| Correctness Verification | Are confidence levels assigned and gaps explicitly registered? |

Each gate returns PASS, CONDITIONAL, or NOT READY. The structural
defense is that the AI must produce gate determinations — it cannot
skip them, cannot mark them all PASS by default, and must justify
each determination with citations to the report.

A team that runs the toolkit honestly and gets all six PASS gates
has a defensible Information Report. A team that gets a NOT READY
gate has a documented signal to return to a specific research
artifact and remediate. This is not bureaucracy. It is the
mechanism that makes the toolkit's output trustworthy.

### Correctness Verification Filtered the Confidence Discipline

Every Phase 1 prompt requires confidence levels (High / Medium /
Low) on key claims and explicit gap registration for unresolved
questions. This is the Correctness Verification principle applied
to research output.

The structural defense is that confidence is a required field, not
a stylistic option. The output templates have confidence columns in
every comparative table. The behavioral rules explicitly state that
unverified claims cannot be silently included — they must be
labeled or flagged.

This was a session-level decision that traced directly to the
framework. Article 1 names Correctness Verification as covering
formal verification, specification conformance, AI-vs-AI audits,
and property-based testing. Applied to research output, none of
those map directly. But the underlying principle — that scoring
without verification is self-reported grades — does map. The
toolkit's expression of Correctness Verification at the research
phase is confidence discipline and gap honesty.

---

## The Structural Decisions That Carry Weight

Some decisions made during the session look minor in the finished
toolkit but are actually load-bearing. These are the structural
defenses that prevent the toolkit from drifting into anti-patterns
under pressure.

### One Question at a Time, in Conversation

Every interview prompt instructs the AI to ask questions one at a
time and wait for an answer before proceeding. This is not a
politeness convention — it is a structural defense against the
failure mode where the AI dumps a list of fifteen questions at the
practitioner, who then attempts to answer all fifteen quickly and
shallowly.

The framework names "thoughtful, evidence-grounded" as the standard
for Phase 1 output. Quick, shallow answers do not produce evidence-
grounded output. The one-question-at-a-time pattern is what makes
the depth possible.

### Explicit Output Templates, Not Free-Form Generation

Every prompt has a complete output template — exact section
headers, table structures, metadata fields. The AI fills in the
template; it does not generate output structure freely.

The structural defense is consistency across artifacts. When five
research artifacts produce outputs in different shapes, the
synthesis cannot consume them as a coherent set. When all five use
the same structural conventions — the same confidence column
labels, the same gap register format, the same metadata header —
the synthesis can read them mechanically.

This is also a Maintainability decision. A practitioner returning
to the Information Report six months later needs to navigate it
quickly. Consistent structure makes navigation possible.

### Built-In Evaluation Checklists

Every prompt ends with an evaluation checklist — specific criteria
the practitioner uses to verify the output before accepting it.
The checklists are concrete, not aspirational. "Comparative data is
in tables, not narrative prose" is a checklist item; "the output
should be high quality" is not.

The structural defense is that the checklist gives the practitioner
a defensible accept/reject decision. Without it, "is this good
enough?" becomes a vibes-based judgment. With it, the practitioner
checks specific items and either passes or returns the artifact for
revision.

### The Synthesis Self-Evaluation as a Required Final Section

The synthesis prompt's self-evaluation scorecard is not optional
and not separate. It is the final section of the synthesis output.
The AI cannot skip it, and the practitioner cannot accept the
synthesis without seeing the scorecard's gate determinations.

This is the strongest structural defense in the entire Phase 1
toolkit. It is the mechanism that makes Phase 1 → Phase 2 handoff
trustworthy. A toolkit that produces an Information Report without
self-evaluation produces a document that looks complete but may
not be. A toolkit that produces an Information Report plus
scorecard produces a document plus its own quality determination.

---

## What the Session Got Right, and What Required Iteration

Two patterns from the working session are worth reporting honestly,
because they show the framework being applied in practice rather
than in idealized form.

### What Got Right on First Pass

The five-research-artifacts-plus-synthesis structure was settled
in the opening minutes of the session and never revisited. The
framework's Article 3 effectively names these artifacts, and the
session followed the article's structure rather than reinventing it.

The interview-then-output pattern for the five research prompts was
also settled early. The article's example workflow is interview-
based, and the session adopted it without challenge.

The instructions file as persistent project context (rather than
being repeated in each prompt) was a clean choice that produced no
friction throughout the session.

### What Required Iteration

The synthesis prompt's structure was not obvious. The first attempt
produced a synthesis that read as an aggregation — the five
research artifacts concatenated rather than synthesized. The
practitioner pushed back: aggregation is not synthesis. Synthesis
surfaces cross-artifact patterns and tensions that none of the
individual artifacts contain on their own.

The revised synthesis prompt added explicit synthesis rules as
behavioral instructions: consolidate without duplication, surface
cross-artifact connections, resolve conflicts explicitly, preserve
confidence levels, flag gaps without filling them. The output
template added Section 8 (Principal Tensions) and Section 9 (Phase 2
Readiness Inputs) — sections that could not exist in any individual
research artifact because they emerge only at synthesis.

The self-evaluation scorecard was added in a third pass. The
initial synthesis prompt produced a synthesized report but did not
evaluate it. The practitioner asked: how does Phase 2 know if this
is actually ready? The scorecard with PASS / CONDITIONAL / NOT
READY gates was added as the synthesis's final section, and the
behavioral rules were updated to make the scorecard mandatory.

This iteration is worth reporting because it shows the SDD cycle's
iterative nature working in real time. The synthesis prompt was
specified, planned, detailed, tasked, and implemented — and then
revisited because the implementation revealed gaps in the
specification. Phase 1 produced a Phase 1 toolkit, and Phase 1's
own SDD iteration improved the toolkit before it was finished.

---

## What This Session Suggests About Toolkit Construction

Three observations that may transfer to other practitioners
building their own toolkits.

**The framework articles must be loadable as project context during
construction.** The session's most consistent pattern was checking
decisions against the source articles. A toolkit built in a session
that does not have the framework attached will drift — not
maliciously, but because the practitioner's memory of the framework
is necessarily less complete than the framework itself. Attaching
the framework as project knowledge made the framework's
specifications enforceable in real time.

**The Core Principles work as decision filters, not as topics to
cover.** Several times during the session, a tempting design choice
surfaced that would have made the toolkit feel more complete or
more sophisticated. Filtering against the principles produced a
clear answer: this addition serves no principle, or this addition
serves one principle while undermining another. The principles
worked as a sieve. Choices that passed went into the toolkit;
choices that did not were dropped.

**Iteration is not failure.** The synthesis prompt required three
passes to settle. Each pass produced a better artifact. The SDD
cycle's iterative nature is not aesthetic — it is operational.
Practitioners who treat iteration as evidence of poor planning
produce toolkits that are quickly built and slowly useful.
Practitioners who treat iteration as the work itself produce
toolkits that take longer to build and immediately serve their
purpose.

---

## What Comes Next

The Phase 1 toolkit produced in this session is one of seven that
the framework requires. Phase 2 (Analysis & Stack Selection),
Phase 3 (Design & Technical Analysis), Phase 4 (Architecture &
Modular Design), Phase 5 (Implementation), Phase 6 (Testing &
Audit), and Phase 7 (Deployment & Evolution) each warrant their
own tool sets.

The Phase 2 toolkit was built in a subsequent working session. The
next article in this Practice subseries documents that session and
will surface a different set of structural decisions — Phase 2's
character is more decision-grade and less exploratory than Phase 1,
which produced a different shape of toolkit.

The Practice subseries will continue as further phase toolkits are
built. Over time, the subseries will cover all seven phases with
worked examples of toolkit construction, structural decisions made,
and iteration patterns observed. Practitioners building their own
toolkits will have a reference set of completed working sessions
to learn from rather than only the framework's prescriptive articles.

---

## Closing Observation

The Phase 1 toolkit was built by applying the framework to itself.
The SDD cycle structured the construction. The Core Principles
filtered the design decisions. The toolkit philosophy produced the
file structure.

This is not coincidence. A framework that produces good tooling
when applied to its own construction is a framework that produces
good tooling generally. A framework that fails to produce its own
tooling — that requires special exemptions or reverses its own
principles when applied to itself — is a framework that has
internal contradictions.

The framework held. That is the most important thing this session
demonstrated. The articles describing the methodology and the
articles produced by applying the methodology agree with each
other. The framework is coherent.

This is reportable evidence, not merely an aesthetic claim.
Practitioners considering whether to adopt the framework can
weight this evidence in their decision: the framework, applied to
itself, produces a usable toolkit. The toolkit it produces holds
up to its own evaluation criteria. This is the strongest internal
test the framework can pass.

---

*Article 10 — Practice subseries*
*Companion: Article 3 — Phase 1: Information Gathering*
*Next: Article 11 — Building the Phase 2 Toolkit (forthcoming)*
*This is a living document. Practice subseries articles will be
revised as toolkit construction patterns mature and new working
sessions surface additional patterns worth reporting.*