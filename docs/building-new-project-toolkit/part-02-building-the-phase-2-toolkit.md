# Part 02 — Building the Phase 2 Toolkit for New Projects

## A Working Session on Commitment-Grade Toolkit Construction

**Series:** AI-Centric Software Development Playbook
**Subseries:** Practice — Working sessions that demonstrate the
framework in application
**Companion:** Part 4 — Phase 2: Analysis & Stack Selection
**Previous in subseries:** Part 1 — Building the Phase 1 Toolkit

---

## What This Section Is

The previous section in this subseries documented the Phase 1
toolkit's construction — the framework applied to itself, producing
six prompts plus an instructions file for information gathering.
This article documents the next working session: building the Phase
2 toolkit for Analysis & Stack Selection.

The article assumes Article 10's frame and does not re-establish it.
The framework-applied-to-itself claim, the Core Principles as
decision filters, the SDD cycle compressed into a single session —
all of this is in Article 10 and applies here without restatement.

What this article reports is what was *different* about the Phase 2
session. The differences are substantive enough to warrant their
own article rather than a continuation of Article 10's narrative.

---

## Why Phase 2 Is Different Work

Phase 1 gathers evidence. Phase 2 makes commitments.

That distinction is not stylistic. It changes the character of
every prompt, every output, every decision the toolkit must support.
A Phase 1 prompt produces an artifact that captures what is known
and what remains uncertain. A Phase 2 prompt produces an artifact
that the team will be held to — a cost projection that becomes the
economic baseline, a stack decision that constrains every subsequent
phase, a benchmark target that becomes the measuring stick from
implementation through production.

The Phase 2 toolkit had to support work that is consequential in a
way Phase 1's work is not. This shaped the entire session.

| Dimension | Phase 1 | Phase 2 |
|-----------|---------|---------|
| Output character | Evidence and options | Scored decisions and commitments |
| AI role | Research strategist | Analytical partner supporting commitment-grade decisions |
| Session pattern (within prompts) | Long conversational interviews | Context paste → small clarification → analytical output |
| Number of prompts | 6 | 7 |
| Gate mechanism | Self-evaluation embedded in synthesis | Dedicated Readiness Review prompt |
| Governance content | None | ADR, override mechanism, revision triggers |
| Handoff to next phase | One Information Report | Six artifacts as a coherent package |

The session began with this distinction explicit. The first
question of the elicitation interview was about session-isolation
versus persistent-context — and the practitioner's answer (session-
isolated, with the instructions file playing a lighter coordinating
role) reflected the recognition that Phase 2 prompts are
analytically distinct rather than steps in a single research
narrative. The toolkit's structure followed from that opening
choice.

---

## The Eight-Question Elicitation Interview

The Phase 1 session was conversational. Decisions surfaced as the
work proceeded, often in response to practitioner pushback when
something felt wrong. The Phase 2 session was deliberately
different.

Before any artifact was built, an eight-question elicitation
interview ran first. Each question targeted a structural decision
that would shape the toolkit. The questions were asked one at a
time, in order, with the AI's reasoning briefly stated before each
question and the practitioner's answer received before the next was
asked.

This pattern was not pre-planned. It emerged from the recognition
that Phase 2 had more cross-cutting structural decisions than Phase
1, and resolving them up front would prevent rework later.

The eight questions and their answers shaped the entire toolkit.
Reporting them here is the most reusable content of this article —
practitioners building their own phase toolkits can use this as a
template for their own elicitation interviews.

### Question 1 — Persistent Context vs. Session Isolation

*Should the Phase 2 instructions file work like Phase 1's — loaded
once as persistent context across all prompts — or is Phase 2 more
session-isolated, with each prompt self-contained?*

**Answer: Session-isolated. The instructions file plays a lighter
coordinating role.**

This was the most consequential structural decision of the session.
It meant each prompt would carry its own behavioral rules, its own
system instructions, its own clarification protocol. The
instructions file would orient the AI to the framework but would
not need to be re-read in each session because each prompt's system
instructions would be self-sufficient.

Downstream effect: every prompt is longer than its Phase 1
counterpart, because each must contain the framework context that
Phase 1 prompts could rely on the instructions file to carry.

### Question 2 — Interview-First or Action-First

*Should Phase 2 prompts maintain Phase 1's interview-first pattern
where the AI asks questions before producing output, or should some
prompts be action-oriented — paste context, produce output, with
perhaps a lighter clarification step?*

**Answer: Mostly action-oriented. Clarification limited to single-
digit but non-zero number of questions.**

Phase 1's interview-first pattern was appropriate when the
practitioner's domain knowledge was the primary input. Phase 2's
primary input is the Information Report plus prior Phase 2
artifacts — structured evidence that already exists. Long
interviews would be wasteful.

The "single-digit but non-zero" constraint was specific. Single-
digit because more than that suggests the prompt is trying to
extract information that should have come from inputs. Non-zero
because pure action prompts that produce output without any
clarification miss genuinely ambiguous cases that require
practitioner input.

### Question 3 — ADR Placement

*How does the Architecture Decision Record fit into the toolkit?
Embedded in the Stack Evaluation prompt, or its own dedicated
prompt?*

**Answer: Its own dedicated prompt (Step 05). Principle weighting
should be folded into Business Analysis (Step 01).**

This was the structural decision that made Phase 2's commitment
work visible. By separating the ADR from the Stack Evaluation
scoring, the toolkit preserved the distinction between **analysis**
(Step 04 ranks candidates) and **commitment** (Step 05 documents
the practitioner's authorized choice).

The ADR as its own prompt also allowed Step 04 to remain purely
analytical with no recommendation language, and allowed Step 05 to
be governance-focused with no scoring content. Two clean scopes
rather than one mixed-scope prompt.

The folded-in placement of principle weighting was a related
choice. Weighting is a business judgment, not a technical exercise.
It belongs where the business case is captured. Pulling it out into
a separate prompt would have over-formalized what is essentially a
single decision per project.

### Question 4 — Cost Modeling Pricing Data

*How should the Cost Modeling prompt handle external pricing data?
Practitioner-supplied paste-in, structured placeholders, or MCP
integration?*

**Answer: Option C — MCP noted as the intended integration upgrade
path, with practitioner-supplied data working today.**

This decision was pragmatic. Live MCP integration with cloud
provider pricing APIs is the right long-term answer, but the
toolkit had to work today with manual paste-in. The structural
defense was making the upgrade path visible in the prompt itself
— an explicit "Planned Upgrade Path: MCP Integration" section that
documents what the team will build toward.

The deeper pattern this decision exposed: a toolkit can be designed
so that its known limitations document themselves. A future
practitioner reading the Cost Modeling prompt sees not only how to
use it today but also what investment would improve it. This is
maintainability applied to the toolkit's own evolution.

### Question 5 — Threat Modeling (Three-Part Question)

*A) Framework choice — STRIDE default or practitioner selection?
B) Data flow representation — text tables, Mermaid diagrams, or
both? C) Scope boundary enforcement — soft note, hard structural
constraint, or middle ground?*

**Answer: A2 (practitioner selection via clarification), B3 (both,
with tables canonical), C2 (hard structural constraint — output
template literally cannot accommodate Phase 4-level detail).**

This was the one question of the eight where the practitioner
initially gave a single answer ("Option C") to a three-sub-part
question. The AI flagged the ambiguity and asked for clarification
on each sub-part. The practitioner gave the three-part answer
above.

This small exchange is worth reporting because it shows
clarification working in real time. The session would have produced
a coherent but suboptimal Threat Modeling prompt if the AI had
guessed at the practitioner's intent. By stopping to disambiguate,
the prompt was built with three deliberate decisions rather than
one defaulted one.

The C2 decision in particular shaped the prompt's most
distinctive structural feature: the output template has no fields
for control implementation, encryption schemes, audit logging
architecture, or other Phase 4 work. Threats are identified at
trust boundary level rather than module level. The Phase 4 handoff
package frames items as architectural questions Phase 4 must
answer, not as answers. The prompt cannot drift into Phase 4
territory because it has nowhere to put Phase 4 content.

### Question 6 — Benchmark Calibration and Versioning

*A) How are benchmark targets calibrated for realism? B) How are
benchmarks versioned to detect drift?*

**Answer: A1 (AI proposes targets, practitioner adjusts —
practitioner owns realism). B2 (versioned with explicit "changes
require ADR" governance).**

The A1 decision kept domain judgment with the practitioner. The AI
can propose targets based on comparable-system data and stack
characteristics, but it lacks domain context that determines
whether a target is achievable on this team's actual workload. The
prompt's structure makes the calibration step visible by including
both AI-Proposed and Practitioner-Calibrated value fields in every
benchmark definition.

The B2 decision treated benchmarks as governance artifacts rather
than working documents. Phase 3, 5, 6, and 7 tool sets reference
benchmarks by version number throughout the project lifecycle. A
benchmark that quietly shifts between phases is a measuring stick
that lies. The version log and the "substantive changes require a
new ADR" protocol are the structural defense against silent drift.

### Question 7 — Gate Placement

*Where should the Phase 2 gate live? In the ADR prompt, as its own
dedicated prompt, or distributed across the analytical prompts?*

**Answer: Option B — its own dedicated Readiness Review prompt
(Step 07).**

This was the second-most-consequential structural decision of the
session, after Question 1's session-isolation choice. By giving the
gate its own prompt, the toolkit cleanly separated three concerns:

- The ADR (Step 05) commits the stack decision and documents *what
  was decided and why*
- The benchmark framework (Step 06) defines *the measuring sticks
  the team will track against*
- The Readiness Review (Step 07) determines *whether the package as
  a whole is ready to authorize Phase 3*

A combined ADR/gate prompt would have conflated commitment with
readiness assessment. The practitioner can commit a stack with the
ADR but still have a NOT READY gate because, for example, the
threat model has gaps the ADR cannot fix. The two are different
governance acts and deserve separate artifacts.

### Question 8 — Naming Convention and Execution Order

*Should prompts use the `step-NN-name.prompt.md` numbered convention
the practitioner was already using for the instructions file, or
should they use Phase 1's descriptive-only names? Is the proposed
execution order correct?*

**Answer: Use the numbered convention. The execution order is
correct.**

This was the smallest of the eight questions but produced the
toolkit's most visible structural feature: the directory listing
shows execution order at a glance. Phase 1's descriptive-only file
names left order as a recommendation in the README. Phase 2's
numbered convention encodes order in the file system itself, which
matches the article's emphasis that Phase 2 execution order is
load-bearing rather than recommended.

---

## What the Eight Questions Demonstrated

The elicitation interview took less than a third of the session's
duration but determined the structure of the entire toolkit.
Every prompt built afterward followed from one or more of these
eight decisions.

This pattern is worth naming directly: **structural decisions are
cheap to make up front and expensive to retrofit.** A toolkit built
without an elicitation interview will have its structural decisions
made implicitly during construction, often inconsistently across
prompts, and the inconsistencies will surface as friction during
use. The eight-question interview made structure explicit before
implementation, which is the SDD pattern applied at the toolkit
level.

A practitioner building their own phase toolkit can adopt this
pattern directly. The questions will differ — Phase 3's questions
are about design simulation; Phase 4's are about module specification
formality — but the pattern is the same. Settle structural decisions
before building. Document them. Build to those decisions.

---

## What Phase 2 Required That Phase 1 Did Not

Beyond the structural decisions made in the eight-question interview,
Phase 2 required new toolkit elements that Phase 1 did not need.

### Governance Artifacts as First-Class Toolkit Elements

Phase 1 produced research artifacts. Phase 2 produced research
artifacts plus governance artifacts — the ADR (Step 05) and the
Readiness Review (Step 07) are governance documents, not analysis.

The ADR follows the standard ADR convention used widely in the
software industry, adapted with framework-specific extensions:
principle weighting traceability, divergence rationale when the
committed stack is not the top-ranked stack, measurable revision
triggers with named sources of truth and defined actions, and an
amendment log for non-substantive corrections.

The Readiness Review introduced the override mechanism as a
structural element. The framework's articles emphasize that
principles are not optional, but the practitioner sometimes faces
external pressures — regulatory deadlines, executive decisions —
that make proceeding with a NOT READY gate the right business
choice. The override mechanism in Step 07 makes this visible rather
than negotiated. The AI's determination stands. The practitioner's
override stands alongside it. Both are in the audit trail. A team
that overrides multiple gates per phase silently is operating
outside the framework. A team that overrides one gate with
documented justification is operating with discipline under
pressure.

Building governance artifacts required different reasoning than
building analytical ones. Analytical prompts ask "what is the right
output structure for this analysis?" Governance prompts ask "what
is the right structure for this commitment to remain durable when
read years later?" The two questions produce different artifacts.

### Cross-Artifact Consistency as a First-Class Concern

Phase 1's six artifacts were independent enough that consistency
between them was a desirable property rather than a structural
requirement. Phase 2's seven artifacts are tightly coupled — the
cost model uses the committed stack from the ADR, the benchmarks
are calibrated against the committed stack, the threat model's
stack implications feed Stack Evaluation's Security scoring, the
ADR cites the Step 04 ranking and either commits to it or
documents divergence.

This coupling meant the Readiness Review's most distinctive
feature — the cross-artifact consistency check — was not optional.
It is the structural defense against the failure mode where six
artifacts each pass their own evaluation but disagree with each
other. The article's validation checkpoint criteria are explicit
about this: *"Does the cost model reflect the chosen stack? Does
the threat model cover the data flows implied by the business
analysis?"* The Readiness Review makes these checks structural
rather than aspirational.

### Hard Structural Scope Boundaries

Phase 1 prompts trusted the AI's judgment about scope. Phase 2
prompts cannot. The risk of Phase 2 prompts drifting into Phase 3
or Phase 4 work is significant — threat modeling can drift into
control implementation, stack evaluation can drift into
architecture recommendations, benchmark definition can drift into
instrumentation strategy.

The structural defense is the prohibition list and the absence of
the relevant fields in output templates. The Threat Modeling
prompt has explicit "What This Step Does NOT Produce" lists naming
control implementation, encryption schemes, audit logging
architecture. The output template has no fields for these. If the
AI tries to produce them, there is nowhere to put the content.

This pattern is more aggressive than Phase 1's behavioral rules.
Phase 1 said "do not produce X." Phase 2 says "do not produce X,
and the template does not have a slot for X anyway." The structural
defense is what the behavioral rule alone cannot guarantee.

---

## Where Phase 2 Construction Strained the Framework

Three places where the framework's articles did not fully prescribe
the toolkit's construction. These are honest reports of edges, not
criticisms.

### The Framework Does Not Explicitly Prescribe Action-First Prompts

Article 2 (Building Your Toolkit) describes interview prompts and
action prompts as distinct building block types. Article 4 (Phase
2: Analysis & Stack Selection) describes Phase 2's analytical work
without explicitly prescribing whether the prompts should be
interview-first or action-first.

The Phase 2 session settled this through the eight-question
interview's second question. The answer (action-first with single-
digit clarification) reflected the reality that Phase 2's primary
input is structured evidence rather than practitioner knowledge —
but this reality was not stated explicitly in the framework's
articles. The toolkit's choice was a reasonable extrapolation, but
it was a choice rather than a deduction.

A future revision of Article 2 or Article 4 could prescribe this
explicitly: prompts whose primary input is the practitioner's
domain knowledge are interview-first; prompts whose primary input
is structured evidence are action-first. This would close the gap
the Phase 2 session had to fill through elicitation.

### The Framework Does Not Specify Governance Artifact Structure

The ADR is mentioned in Article 4 as the format for the stack
decision: "the commitment is documented as an Architecture Decision
Record (ADR) — a structured document that captures the decision,
the context, the alternatives considered, the rationale, and the
consequences."

The standard ADR format is well-established, but the framework-
specific extensions — principle weighting traceability, divergence
rationale, measurable revision triggers, the amendment log — were
the session's invention. They are consistent with the framework's
emphasis on principle scoring and explicit trade-offs, but they are
extensions rather than direct applications.

Future articles may codify these extensions as the framework's ADR
template, or may continue to leave the ADR's specifics to
practitioner judgment. The Phase 2 toolkit's ADR template is one
defensible interpretation. It is not the only one.

### The Framework Does Not Prescribe Override Mechanisms

Article 4's validation checkpoint describes what Phase 2 must
produce before Phase 3 begins. It does not address what happens
when the validation checkpoint fails but the team must proceed
anyway. The override mechanism in Step 07 was the session's
response to a failure mode the framework's articles do not
explicitly address.

The session's reasoning: every team will encounter situations
where a gate fails but external constraints force advancement. The
framework's principles are not optional, but practical work
sometimes requires acknowledging that a principle will be
violated. The structural defense is making the violation visible
and documented rather than letting it happen silently.

This is consistent with the framework's broader emphasis on
explicit documentation over silent decisions, but it is an
extrapolation. A future article may codify override mechanisms as
a framework concept, or may continue to leave them to practitioner
judgment within each phase's toolkit.

---

## What Phase 2's Session Suggests About Toolkit Maturation

Three observations specific to building toolkits beyond the first
one.

**Subsequent toolkits inherit pattern, not content.** The Phase 2
toolkit reused several patterns from Phase 1: confidence levels on
significant claims, gap registers for unresolved questions,
evaluation checklists per prompt, output templates with consistent
metadata headers. But none of the actual content transferred.
Phase 1's interview-first conversational tone was wrong for Phase
2's commitment-grade analytical work. Phase 1's single Information
Report synthesis was wrong for Phase 2's multi-artifact handoff.
Practitioners building subsequent phase toolkits should expect to
reuse patterns and rebuild content.

**The elicitation interview gets cheaper with each phase.** Phase
1's structural decisions were made conversationally, surfacing as
work proceeded. Phase 2's eight-question elicitation took less than
a third of the session and prevented the rework that conversational
decision-making would have required. The session's pattern
recognition was sharper because Phase 1's session had built the
practitioner's intuition for which decisions matter. Phase 3's
session will likely move faster still.

**The framework becomes more demanding as toolkits accumulate.**
Phase 1's toolkit was internally consistent because it had no prior
toolkit to be consistent with. Phase 2's toolkit had to be
internally consistent and consistent with Phase 1's patterns where
they applied. Phase 3's toolkit will have to be consistent with
both. As the toolkit set grows, the cost of inconsistency grows
with it. This is not a problem — it is the framework working as
intended. Coherence across the full toolkit set is what makes the
SDD cycle's iterative nature work in practice.

---

## What Comes Next

The Phase 2 toolkit produced in this session is the second of seven
that the framework requires. Phase 3 (Design & Technical Analysis),
Phase 4 (Architecture & Modular Design), Phase 5 (Implementation),
Phase 6 (Testing & Audit), and Phase 7 (Deployment & Evolution)
remain to be built.

Phase 3 will introduce its own challenges. The work shifts from
analytical decisions to design simulation — stress-testing the
committed stack against the threat model, the cost model, and the
benchmarks before architecture begins. The Phase 3 toolkit will
likely require simulation prompts, scoring infrastructure for the
Principle Scorecard baseline, and tooling for documenting
Architecture Decision Records that build on Phase 2's stack ADR.

Whether Phase 3's session will follow Phase 2's eight-question
elicitation pattern, or develop a different pattern appropriate to
design work, will be decided when the session begins. The Practice
subseries will continue to report what works and what requires
adjustment.

---

## Closing Observation

Phase 1's session demonstrated the framework producing usable
tooling when applied to itself. Phase 2's session demonstrated the
framework producing *coherent* tooling when applied to itself
across multiple toolkits. This is a stronger claim.

A framework that produces one good toolkit may have done so
accidentally, or may have produced a toolkit that fits one phase's
work but cannot scale to others. A framework that produces two
toolkits — different in character, different in shape, different
in governance posture — and produces them in a way that they
cohere with each other and the framework's own articles is a
framework that is doing something durable.

The Phase 1 toolkit's interview-first prompts and the Phase 2
toolkit's action-first prompts are different solutions because
they are solving different problems. The framework's principles
and methodology produce both correctly. The articles that describe
the methodology and the toolkits produced by applying the
methodology continue to agree with each other. The framework
remains coherent.

This is reportable evidence, layered onto Article 10's reportable
evidence. Two working sessions have now produced toolkits by
applying the framework to itself. Both produced usable artifacts.
Both surfaced patterns worth carrying forward. Both showed the
framework working under different conditions. The Practice
subseries will continue to accumulate this evidence as further
phase toolkits are built.

---

*Part 02 — Practice for new project subseries*
*Companion: Article 4 — Phase 2: Analysis & Stack Selection*
*Previous in subseries: Article 10 — Building the Phase 1 Toolkit*
*Next in subseries: Article 12 — Building the Phase 3 Toolkit (forthcoming)*
*This is a living document. Practice subseries articles will be
revised as toolkit construction patterns mature.*
