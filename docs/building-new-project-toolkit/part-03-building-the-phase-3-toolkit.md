# Article 12 — Building the Phase 3 Toolkit
## A Working Session on Design-Phase Toolkit Construction

**Series:** AI-Centric Software Development Playbook
**Subseries:** Practice — Working sessions that demonstrate the
framework in application
**Companion:** Article 5 — Phase 3: Design & Technical Analysis
**Previous in subseries:**
- Article 10 — Building the Phase 1 Toolkit
- Article 11 — Building the Phase 2 Toolkit

---

## What This Article Is

The two previous articles in this Practice subseries documented the
Phase 1 and Phase 2 toolkit construction sessions. This article
documents the third: building the Phase 3 toolkit for Design &
Technical Analysis.

The article assumes the framework-applied-to-itself meta-frame
established in Article 10 and the comparative pattern from Article
11. It does not re-establish either. It reports what was different
about the Phase 3 session — and what those differences demonstrate
about the framework's coherence claim by the third iteration.

---

## Why Phase 3 Is Different Work

Phase 1 gathered evidence. Phase 2 made commitments. Phase 3
stress-tests those commitments and locks technical direction.

That triple distinction shapes everything Phase 3 produces. Phase 1
prompts were conversational because the practitioner's domain
knowledge was the primary input. Phase 2 prompts were action-
oriented because structured evidence existed. Phase 3 prompts are
action-oriented like Phase 2 — but Phase 3 has substantively more
work to do and produces qualitatively different artifact types.

| Dimension | Phase 1 | Phase 2 | Phase 3 |
|-----------|---------|---------|---------|
| Primary work | Gathering | Committing | Stress-testing and locking |
| Number of prompts | 6 | 7 | 9 |
| Distinctive activity | Structured interviews | Weighted scoring | Simulation under stress |
| Execution pattern | Order-flexible | Strictly sequential | Dependency-driven |
| Cross-phase living artifacts | None | Stack ADR (referenced) | Principle Scorecard (actively updated) |
| Backward effects on prior phases | None | None | Phase 2 amendment cycle |
| Gate determination outcomes | 3 (PASS/CONDITIONAL/FAIL) | 3 | 4 (split NOT READY into Phase 3 gaps vs. Phase 2 amendment) |

The Phase 3 session began with this distinction explicit. The
first elicitation question was about the number of artifacts and
prompt boundaries — a question that did not appear in Phase 2's
interview because Phase 2's artifacts were more clearly delineated
by the source article. Phase 3's article names three primary
artifacts plus four tool sets plus ADRs plus two forward-looking
concerns, and the practitioner had to choose how to organize that
substantive content into discrete prompts.

---

## The Eight Questions That Shaped Phase 3

Phase 2's session settled with an eight-question elicitation. Phase
3 also used eight questions — but the questions covered different
ground. Each was specific to Phase 3's substantively richer work.
Reporting them in full preserves the most reusable content for
practitioners building their own complex phase toolkits.

### Question 1 — Number of Artifacts and Prompt Boundaries

*Phase 3 names three primary artifacts, four tool sets, ADRs for
locked design decisions, and two forward-looking concerns. How
should this be structured into discrete prompts?*

**Answer: Hybrid (Option C) — six locked dimensions through a
single committed artifact (the Design Direction Document) with one
ADR per dimension as supporting commitments.**

This was the structural decision that determined Phase 3's artifact
count. Phase 2 had seven prompts; Phase 3 settled on nine. The
two additional prompts came from splitting concerns that Phase 2
could have folded together (the scorecard baseline and its update
protocol; the two forward-looking handoffs).

The choice rejected mapping prompts directly to the article's four
tool sets (which would have produced four or five prompts and
hidden important governance separations). It also rejected mapping
prompts to every significant work unit (which would have produced
twelve or more prompts and fragmented the toolkit).

The hybrid was the most flexible at this point. The session noted
that future iterations could consolidate prompts that prove
redundant or split prompts that prove overloaded.

### Question 2 — Simulation Prompt Design

*Simulation is Phase 3's most distinctive new activity. How should
the simulation prompt work?*

**Answer: A structured simulation prompt with named scenario
categories — performance, security, cost, failure modes, scaling —
running all relevant scenarios within a single execution.**

This was the choice that shaped Step 03's most distinctive
structural feature: the output template has sections only for the
five named categories. If a needed simulation does not fit one of
these categories, the response is to amend Step 01 to include it as
a sixth category and re-run Step 03 — not to add a "miscellaneous"
section.

The choice rejected the two natural alternatives — one prompt run
multiple times (fragmented output, inconsistent depth) and a
single prompt covering all scenarios without category structure
(unscoped exploration that produces output but no signal).

The named-category structure became Step 03's spine and one of the
Phase 3 toolkit's most consequential structural defenses.

### Question 3 — Principle Scorecard Handling

*The Principle Scorecard is established in Phase 3 but updated by
Phases 4–7. How should this be split between Phase 3 prompts?*

**Answer: Split into two prompts — baseline production (Step 05)
and cross-phase update protocol (Step 06).**

This was the structural decision that created the framework's
first cross-phase governance contract. Step 05 produces the Phase
3 scorecard; Step 06 governs how Phases 4–7 update it. The
separation reflects that these are different concerns — one is
analytical (calibrating current and target scores), one is
governance (regression detection rules, update cadence, change
control).

The choice rejected the alternatives that would have either
embedded the protocol in the scorecard (mixing analytical and
governance concerns) or pushed protocol definition to later phases
(requiring each subsequent phase to invent governance, which
would produce inconsistent updates and undetectable drift).

The split established a pattern the framework had not previously
used: a prompt that has no Phase 3 content dependencies and
produces a contract for phases that have not yet begun. This is
structurally novel and will likely recur in other phases.

### Question 4 — Design ADR Generation Pattern

*The Phase 3 Design Direction Document captures six locked
dimensions. How should the matching ADRs be produced?*

**Answer (initial): One prompt that takes the dimension as a
parameter and produces one ADR per execution, with a structural
requirement that all six ADRs be produced before downstream prompts
can proceed.**

**Answer (refined by Question 7): The Design Direction Document
and the six ADRs are produced together by a single prompt as a
paired artifact, in one execution.**

This question's answer changed during the session. The initial
choice was a prompt run six times. The Question 7 discussion of the
document-and-ADR relationship revealed that the initial choice
would create a drift risk — the Document and the ADRs could fall
out of sync if produced separately.

The refinement consolidated the work into a single execution that
produces the Document with six dimension sections inline followed
by the six ADRs as Part B. Each ADR still gets full analytical
treatment within the execution; the structural defense is the
evaluation checklist's requirement that all six ADRs exist and
match the Document's commitments.

This iteration is worth reporting. The session changed its
structural decision mid-session because a later question revealed
the initial choice would create a problem. Treating the elicitation
interview as immutable would have locked in a choice that the
session itself had grounds to revise. The framework's iterative
character at the toolkit level worked exactly as the SDD cycle
predicts it should.

### Question 5 — Forward-Looking Concerns

*Observability hooks and compliance design constraints are Phase 3
forward-looking concerns for Phase 4. Should they be folded into
existing prompts, combined into one prompt, or each get their own?*

**Answer: Two separate prompts (Option C) — observability hooks
and compliance design constraints each as a focused Phase 4
handoff.**

This was the decision that made forward-looking concerns first-
class artifacts rather than subsections of the Design Direction
Document. The session recognized that the two concerns have
different Phase 4 audiences (observability architecture work vs.
security/data/audit architecture work) and different content
character (insertion points and capture specifications vs.
regulatory constraints and compatibility analysis).

The choice rejected folding both into Step 04 (would have produced
a Design Direction Document too overloaded to serve its primary
purpose) and combining them into a single forward-looking prompt
(would have mixed concerns with different audiences and content
character).

The result added two prompts to Phase 3's count, bringing the
toolkit to nine prompts. This was a deliberate complexity
investment — making forward-looking work first-class in exchange
for clearer Phase 4 handoffs.

### Question 6 — Phase 3 Readiness Review and Backward Effects on Phase 2

*The Phase 3 article warns that design work can invalidate Phase 2
assumptions. How should the Readiness Review handle this?*

**Answer: Three-tier structure (per-principle, per-artifact, cross-
artifact) plus a "Phase 2 amendment required" output path producing
a concrete remediation package when alignment fails.**

This was the question that introduced the framework's first
explicit backward-effects mechanism. Phase 1 and Phase 2 ran the
framework forward; their gates never needed to send work back to
prior phases because no prior phases existed. Phase 3 is the first
phase where the gate must handle the possibility that the prior
phase's commitments are now wrong.

The choice rejected the simpler alternatives. Option A (treating
Phase 2 alignment as one cross-artifact consistency check) would
have produced a vague "Phase 2 alignment failed" signal without
remediation guidance. Option B (a fourth gate dimension) would
have added structure without resolving how the gate should
respond when that dimension fails.

The chosen approach produces a concrete amendment package — which
Phase 2 ADRs need amendment, which cost model figures need
revision, which benchmark targets need adjustment — each with the
driving Phase 3 finding that necessitates the change. The
practitioner returns to Phase 2 with a structured remediation list,
not an interpretive puzzle.

This decision shaped Step 09's most consequential novel content
(the §5.2 Phase 2 Amendment Package) and produced a governance
pattern the framework's articles do not explicitly prescribe.

### Question 7 — Design Direction Document and Design ADRs Relationship

*The Design Direction Document and the six ADRs serve different
purposes (consolidated narrative vs. formal commitment per
dimension). How should they relate?*

**Answer: Produced together by a single prompt and treated as a
coherent pair — versioned together, updated together, structurally
unable to drift apart.**

This question's answer revised the Question 4 decision, as noted
above. The session recognized that treating the Document as the
canonical source (Option A) or the ADRs as canonical (Option B)
would each create a drift risk in opposite directions. The pairing
(Option C) is the structural answer to a question Phase 2 did not
have to address — what is the relationship between the consolidated
view and the per-decision records?

The pairing structurally prevents drift because the Document and
the ADRs are produced in the same execution and versioned together.
Part A's dimension sections reference Part B's ADRs by number.
Part B's ADRs document the commitments Part A presents. The cross-
artifact consistency check in Step 04 §C verifies each Part A
commitment matches the corresponding Part B ADR.

This pattern is reusable. Any phase that produces both a
consolidated artifact and per-decision records can apply the same
pairing structure to prevent drift.

### Question 8 — Execution Order and Parallel Work Permission

*Phase 1 was order-flexible; Phase 2 was strictly sequential.
Phase 3 has more potential parallelism. How should execution
order work?*

**Answer: Dependency-driven with explicit input requirements
(Option C). Each prompt's metadata names its exact required
inputs. The practitioner runs prompts in any order consistent
with the dependency graph documented in the instructions file.**

This was the structural decision that made Phase 3 the first
phase with documented parallelism. The session recognized that
Step 06 (Scorecard Update Protocol) has no Phase 3 content
dependencies and can run any time. Steps 05, 07, and 08 can run
in parallel once Step 04 completes. Forcing the work to run
sequentially would add time without adding safety.

The choice rejected strict sequence (would have ignored
parallelism opportunities) and minimal sequence (would have left
practitioners without clear guidance on what depends on what).

The dependency-driven approach required the instructions file to
document the dependency graph authoritatively. Without the
documented graph, practitioners would have to derive ordering
from prompt metadata tables, producing inconsistent execution
patterns. The graph became the most operationally important
single element of the Phase 3 instructions file.

---

## What These Eight Questions Demonstrated

The Phase 2 article noted that the eight-question elicitation
pattern took less than a third of the session and prevented the
rework that conversational decision-making would have required.
The Phase 3 session took a similar amount of time on elicitation
but covered substantially more structural ground per question.

The pattern is reusable but the questions are not. Every Phase 3
question targeted a structural decision specific to Phase 3's
work. None of them appeared in Phase 2's interview, and none of
them will appear in Phase 4's interview without modification. The
pattern that transfers is "settle structural decisions before
building"; the content that does not transfer is "these specific
eight questions."

A practitioner building their own Phase 3 toolkit can use these
eight questions as a template. A practitioner building their own
Phase 4 toolkit will need to derive Phase 4's questions from
Phase 4's substantive content.

---

## What Phase 3 Required That Phase 2 Did Not

Beyond the structural decisions made in the eight-question
interview, Phase 3 required three toolkit elements Phase 2 did not
need.

### Dependency-Driven Execution as a First-Class Pattern

Phase 1 and Phase 2 did not have a dependency graph. Phase 1 was
order-flexible because the six prompts were largely independent.
Phase 2 was strictly sequential because each step built linearly
on the prior. Phase 3's work is more distributed — some prompts
genuinely have no dependency on others, and the toolkit must
communicate this without losing structural coherence.

The dependency graph in the instructions file is the structural
defense. It documents which prompts depend on which others, where
parallelism is permitted, and what each prompt requires as input.
The practitioner runs prompts in any order consistent with the
graph. The structural defense against premature execution lives in
each prompt's clarification step — a prompt presented with
incomplete inputs will not produce its artifact.

This pattern is likely to appear in subsequent phases. Phase 4
architecture work has distinct concerns (module boundaries, API
specification, security architecture, data architecture) that have
different dependencies on each other. Phase 4's toolkit will
likely also use dependency-driven execution with a documented
graph.

### Cross-Phase Living Artifacts

Phase 2's Stack ADR is a permanent commitment that later phases
reference. Phases 4–7 do not update it. The Phase 3 Principle
Scorecard is fundamentally different — Phases 4, 5, 6, and 7
actively update it per the Step 06 protocol.

This is the framework's first true cross-phase living document.
The session had to address several questions Phase 2 did not face:
What format conventions must later phases preserve? What governs
when later phases update? How is regression detected across
phases? Who owns the document at each phase? What constitutes a
substantive change vs. an amendment?

The Step 06 protocol is the structural answer. It is a governance
contract for Phases 4–7. The pattern will likely recur — Phase 4
may produce architecture decisions that later phases inherit and
elaborate; Phase 5 may produce implementation artifacts that later
phases reference. Each cross-phase artifact will need its own
governance protocol.

### Structured Backward-Effects Handling

Phase 1 and Phase 2 ran the framework forward. Phase 3 is the
first phase where prior-phase commitments can be invalidated. A
Phase 3 simulation may reveal the Phase 2 stack cannot meet a
benchmark at scale. A Phase 3 compliance constraint may conflict
with the Phase 2 deployment model. A Phase 3 design exploration
may reveal Phase 2 weighting was wrong.

The Step 09 Readiness Review's structured Phase 2 amendment
package is the framework's answer to this. When alignment fails,
the gate does not produce a vague signal — it produces a concrete
remediation list naming exactly what Phase 2 must amend, with the
driving Phase 3 finding for each amendment.

This pattern will likely recur in Phases 4, 5, 6, and 7. Each
subsequent phase can potentially invalidate prior-phase
commitments. The framework needs a governance pattern for
structured backward effects — Phase 3's amendment cycle is the
first instance of that pattern.

---

## Where Phase 3 Construction Strained the Framework

Honest reporting of where the framework's articles did not fully
prescribe the toolkit's construction. By the third iteration,
these strains accumulate evidence about where the framework will
need refinement.

### The Framework Does Not Prescribe Dependency-Driven Execution

Article 2 (Building Your Toolkit) describes tool sets as
combinations of building blocks. Article 5 (Phase 3: Design &
Technical Analysis) describes the SDD cycle as iterative and
references multiple tool sets for the phase but does not
prescribe how prompts within a phase relate.

The Phase 3 session settled dependency-driven execution through
Question 8. The answer was a reasonable extrapolation from the
substantive content of Phase 3, but it was a choice rather than a
deduction. Future revisions of Article 2 or Article 5 could
codify dependency-driven execution as the standard pattern for
phases with distributed work.

### The Framework Does Not Specify Cross-Phase Artifact Lifecycle

Article 5 describes the Principle Scorecard as established in
Phase 3 and updated at every phase transition. It does not
specify how those updates are governed, what constitutes a
regression, who owns the scorecard at each phase, or what
distinguishes amendments from substantive changes.

The Phase 3 session invented the Step 06 protocol to fill this
gap. The choices about tiered regression thresholds, three
regression categories, format inheritance rules, and tiered
override authority are reasonable but are extensions rather than
direct applications of framework principles.

This is the most significant strain reported in any Practice
article so far. The framework's emphasis on Scoring & Metrics as
a Core Principle implies that scorecards must be governed across
phases, but the articles do not specify the governance pattern.
Future articles will likely need to codify cross-phase artifact
lifecycle mechanics.

### The Framework Does Not Address Backward-Effects Cycles

The framework's articles describe the SDD cycle as iterative
within a phase. They do not explicitly address what happens when
work in a later phase invalidates a commitment in an earlier
phase.

The Phase 3 session invented the structured amendment cycle to
fill this gap. The Step 09 §5.2 Phase 2 Amendment Package, the
five-subsection structure, the amendment cycle process — all of
these are extensions to the framework's stated patterns.

This strain is worth flagging because backward effects will
become more common as more phases are built. Phase 4 architecture
can invalidate Phase 3 design commitments. Phase 5 implementation
can invalidate Phase 4 architecture commitments. Phase 6 testing
can invalidate any prior phase's commitments. Each will need a
backward-effects pattern. Future framework revisions will likely
need to codify the pattern explicitly.

### The Framework Does Not Prescribe Four-Determination Gate Outcomes

Article 4 (Phase 2) describes the validation checkpoint with
implicit READY / NOT READY semantics. Phase 2's toolkit refined
this to PASS / CONDITIONAL / NOT READY. Phase 3 refined it
further to READY / CONDITIONALLY READY / NOT READY (Phase 3
gaps) / NOT READY (Phase 2 amendment required).

The four-outcome structure is a reasonable refinement, but it is
an extension. The framework's articles do not prescribe how many
determination outcomes a gate should have or how to distinguish
different remediation paths. Future articles may codify gate
outcome conventions or may leave the count to each phase's
toolkit.

---

## What Phase 3's Session Demonstrated About Toolkit Maturation

Article 11 named three observations about building toolkits
beyond the first one. Phase 3 reinforced two of them and refined
the third.

**Pattern inheritance, not content inheritance.** Phase 3 reused
patterns from Phase 1 and Phase 2: confidence levels, gap
registers, evaluation checklists, AI-proposes-practitioner-
calibrates, override mechanisms with tiered authority,
cross-artifact consistency checks, evidence citation requirements,
prohibition on adjusting weights or criteria during scoring. None
of the actual content transferred. Phase 2's seven prompts were
wrong for Phase 3's nine. Phase 1's interview-first pattern was
wrong for Phase 2's action-orientation was wrong for Phase 3's
dependency-driven. The pattern of reusing patterns held.

**Elicitation gets easier with each phase.** Phase 2 took a third
of its session on elicitation. Phase 3 took a similar amount of
elicitation time on substantially more structural ground. The
practitioner's intuition for which decisions matter sharpened
between Phase 2 and Phase 3. The session noted that Phase 4's
elicitation will likely move faster still — though Phase 4's
substantive content may require more decisions, the practitioner's
pattern recognition will be sharper.

**Framework demands increase as toolkits accumulate — with
acceleration.** This is the refinement of Article 11's third
observation. Article 11 noted that subsequent toolkits must be
internally consistent and consistent with prior toolkits' patterns.
Phase 3 demonstrated that the consistency burden accelerates non-
linearly. Phase 1 had no prior toolkit to be consistent with.
Phase 2 had one. Phase 3 had two. Phase 4 will have three. By the
fifth or sixth phase, the consistency burden may require dedicated
review effort — a "framework consistency check" that verifies new
toolkit decisions do not silently contradict prior toolkit
decisions.

This acceleration is not a problem if the consistency burden is
recognized and addressed. It becomes a problem if practitioners
assume each new toolkit is independent and discover the contra-
dictions only when downstream phases struggle to integrate.

---

## The Coherence Claim by the Third Iteration

Article 10 reported that the framework produced its own tooling.
Article 11 reported that the framework produced coherent tooling
across two different working sessions for two phases with
different characters. Article 12's question is whether the
framework's coherence claim holds at three iterations.

The Phase 3 toolkit is internally coherent. Its nine prompts
build on each other through documented dependencies. Its cross-
artifact consistency checks verify the dependencies are honored.
Its gate evaluates the package as a coherent whole. By any
internal measure, Phase 3 holds together.

The Phase 3 toolkit is coherent with Phases 1 and 2. It uses
patterns Phase 1 and Phase 2 established (confidence levels, gap
registers, evaluation checklists, override mechanisms). It
inherits Phase 2's principle weighting and benchmark framework as
inputs. Its Readiness Review extends Phase 2 Step 07's three-tier
structure to four tiers with the new Phase 2 amendment dimension.
The three toolkits coexist without contradiction.

The framework's articles, however, strained more in Phase 3 than
in Phase 2. The session had to invent dependency-driven execution
as a pattern, cross-phase artifact lifecycle mechanics, structured
backward-effects handling, and four-outcome gate determinations.
Each invention is a reasonable extrapolation from framework
principles, but each is also an extension the articles do not
explicitly prescribe.

This is the most honest report Article 12 can produce. The
framework's coherence holds at three iterations — but the
framework's prescriptive completeness diminishes as iterations
accumulate. Future framework revisions will likely need to codify
patterns that have so far been invented during sessions. The
Practice subseries is the evidence base for those revisions.

---

## What Comes Next

The Phase 3 toolkit produced in this session is the third of seven
the framework requires. Phases 4 (Architecture & Modular Design),
5 (Implementation), 6 (Testing & Audit), and 7 (Deployment &
Evolution) remain to be built.

Phase 4 will likely intensify the patterns Phase 3 established.
Architecture work has more distinct concerns than design work,
which will require even more careful dependency-driven execution.
Architecture artifacts may have cross-phase lifecycles like the
Principle Scorecard. Architecture decisions can invalidate Phase
3 design commitments, requiring a backward-effects pattern. Phase
4's elicitation will likely produce more structural decisions per
session than Phase 3's did.

Phase 5 (Implementation) will introduce concerns Phases 1–4 did
not address: actual code generation, AI-vs-AI review, formal
verification, specification conformance testing. These concerns
may require entirely new prompt types that have no analogue in
prior phases.

Phase 6 (Testing & Audit) is where the Principle Scorecard
becomes pass/fail gates. The Phase 3 scorecard baseline and the
Step 06 update protocol have already established the framework
this phase will use, but Phase 6 will add audit-specific patterns.

Phase 7 (Deployment & Evolution) is where the framework becomes
circular rather than linear. The scorecard is monitored in
production. New features run the SDD cycle with the same rigor as
initial development. Phase 7 may require its own kind of recursive
toolkit — a toolkit that produces toolkits as the project evolves.

The Practice subseries will continue to report what these
sessions produce.

---

## Closing Observation

The framework's coherence claim has now been tested at three
iterations. The Phase 1 session demonstrated the framework
producing usable tooling. The Phase 2 session demonstrated the
framework producing coherent tooling across two different phases.
The Phase 3 session demonstrated the framework producing tooling
that holds together internally and coheres with prior tooling
while strain accumulates against the framework's prescriptive
articles.

This is a more nuanced report than either Article 10 or Article
11 could produce. By the third iteration, the framework is doing
something it has not done before: it is approaching the edges of
its own prescriptive completeness. The Phase 3 toolkit required
inventions — dependency-driven execution, cross-phase artifact
lifecycle, backward-effects handling, four-outcome gates — that
the framework's articles do not explicitly prescribe.

The inventions are reasonable. They follow from framework
principles even when they extend framework articles. But the
pattern of necessary invention is itself an observation worth
reporting. A framework that requires inventions at every
iteration is a framework that is incomplete in ways its initial
articles did not anticipate. A framework that accepts those
inventions, documents them as patterns, and incorporates them
into future revisions is a framework that is maturing.

The Practice subseries is the evidence base. Articles 10, 11, and
12 collectively show the framework being applied to itself across
three iterations, with each iteration surfacing both confirmation
of the framework's coherence and identification of where the
framework needs refinement. This is what useful evidence looks
like for a methodology under development.

The framework held at three iterations. The framework will likely
need revision after seven. Both observations are reportable. Both
are honest.

---

*Article 12 — Practice subseries*
*Companion: Article 5 — Phase 3: Design & Technical Analysis*
*Previous in subseries:*
- *Article 10 — Building the Phase 1 Toolkit*
- *Article 11 — Building the Phase 2 Toolkit*

*Next in subseries: Article 13 — Building the Phase 4 Toolkit
(forthcoming)*

*This is a living document. Practice subseries articles will be
revised as toolkit construction patterns mature and the framework's
articles incorporate the patterns the sessions surface.*