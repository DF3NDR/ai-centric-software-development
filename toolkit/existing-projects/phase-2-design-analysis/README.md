# Phase 2 Analysis & Improvement Planning Tool Set — Existing Projects

**AI-Centric Software Development Playbook**

**Toolset Version:** v1.0 (initial authoring 2026-04-22, structured to v1.2 conventions established by the Phase 1 existing-projects toolset)

---

## What This Tool Set Is For

This directory contains the **existing-project variant** of the Phase 2
Analysis & Improvement Planning Tool Set. It is used when a practitioner
has completed Phase 1 on an existing system — producing a Current-State
Information Report — and now needs to transform that evidence into a
sequenced, scoped, cost-modeled, principle-weighted **improvement plan**
that Phases 3 through 7 can execute.

The greenfield variant lives at
`toolkit/phase-02-analysis-stack-selection-toolset/` and asks
*"which technologies should we choose?"*. This variant asks
*"in what order do we change what we have, by which mechanism, at
what cost, and what does failure look like?"* — the inputs come
from Phase 1; the outputs are decisions, not discoveries.

The SDD cycle, the six Core Principles, the phase-gate discipline,
and the principle-weighted scoring approach are identical across
variants. What changes is the unit of decision and the output shape:
Phase 2 produces an Improvement Plan rather than a stack selection.

---

## The Six Core Principles in This Phase

Every decision in this phase is evaluated against all six principles,
with **explicit weights** set in Step 02. Phase 1 left principle
weighting as a CONDITIONAL — Phase 2 resolves it. Every Must-Change
sequencing decision, every mechanism choice, every cost trade-off is
filtered through the weighted principles.

| Principle | What This Phase Asks |
|-----------|---------------------|
| **Security** | Which sequencing choices reduce security risk fastest? Which mechanism alternatives have the smallest security surface? Which deferrals carry acceptable risk? |
| **Maintainability** | Which mechanism alternatives produce the most maintainable result? How does sequencing affect long-term change cost? Where does the plan add documentation debt? |
| **Economics** | Does the plan fit the budget envelope (time, infrastructure, AI-tool cost, opportunity cost)? Which choices materially shift cost? Where is cost concentrated? |
| **Operations** | Which sequencing keeps the system operable throughout the cycle? Which mechanism changes affect deployability or observability? Where do operational risks cluster? |
| **Scoring & Metrics** | Are principle weights assigned and justified? Do per-MC cost estimates carry MEASURED / ESTIMATED / BELIEVED / UNMEASURED tags? Are acceptance criteria measurable? |
| **Correctness Verification** | Does every mechanism choice have a verification method named? Are the chosen mechanisms ones whose correctness can actually be checked at Phase 6? |

Decisions Phase 2 makes without principle-grounding are decisions
Phase 3 and onward will revisit at higher cost.

---

## Specification Driven Development (SDD)

All work in this phase follows the SDD cycle. The cycle does not
change; the tool set that powers it does.

```
Specify → Plan → Detail → Task → Implement
```

| SDD Step | What Happens in This Phase | Output |
|----------|---------------------------|--------|
| **Specify** | Load and validate the Phase 1 Information Report; capture practitioner intent for this planning cycle | Phase 2 Planning Specification |
| **Plan** | Identify the decision areas the plan must cover (weighting, mechanisms, sequencing, cost, risk) | Phase 2 Decision Plan |
| **Detail** | Each decision area becomes a step prompt producing decision artifacts | Decision Requirements Documents (per step) |
| **Task** | Convert decisions into actionable items — sequenced MCs, mechanism choices with rationale, cost line items | Task list with acceptance criteria |
| **Implement** | Execute decisions through the step prompts; synthesize into the Improvement Plan | Five decision artifacts + Improvement Plan |

The cycle is iterative. When mechanism decisions in Step 03 reveal a
weighting question (Step 02) that wasn't fully resolved, cycle back.
When sequencing in Step 04 reveals a cost question (Step 05) that
forces re-sequencing, cycle back.

---

## Directory Contents

```
phase-02-analysis-improvement-planning-existing-project-toolset/
├── README.md                                                          ← You are here
├── analysis-improvement-planning.existing-project.instructions.md     ← Load this first
├── step-00-building-block-discovery.prompt.md                         ← Run after loading Phase 1 Report
├── step-01-phase-1-input-validation.prompt.md                         ← Artifact 1
├── step-02-principle-weighting.prompt.md                              ← Artifact 2
├── step-03-mechanism-decisions.prompt.md                              ← Artifact 3
├── step-04-sequencing-and-tiering.prompt.md                           ← Artifact 4
├── step-05-cost-modeling-and-capacity-check.prompt.md                 ← Artifact 5
└── step-06-improvement-plan-synthesis.prompt.md                       ← Final synthesis
```

---

## File Descriptions

### `analysis-improvement-planning.existing-project.instructions.md`
**Type:** Instructions file (load as project or system context)

The overarching instructions for any AI assistant operating in Phase 2
on an existing project. Contains the framework orientation, the
behavioral expectations specific to decision-heavy planning work,
the principle-weighted scoring approach, the draft-and-react interview
mode that dominates Phase 2 work, the Phase-1-input-validation
discipline, the worst-case-plan-failure discipline applied at Step 04,
the cost-modeling tag conventions, output standards, common pitfalls,
and the connection to Phase 3.

Load this file as project-level instructions in your AI environment
before using any of the prompt files.

*Use in: Claude Project Instructions, VS Code AI instructions,
Cursor rules, or equivalent.*

---

### `step-00-building-block-discovery.prompt.md`
**Type:** Interview Prompt | **SDD Step:** Specify (building-block inventory)

Conducts a short, structured inventory of the AI capabilities — MCP
connectors, Skills, specialized agents, code access — available for
this Phase 2 run. Adapted from the Phase 1 equivalent with Phase 2
emphases: confirms that the Phase 1 Information Report is loadable as
context, identifies whether the practitioner's tooling has changed
since Phase 1 (new connectors, removed access, model upgrades), and
notes if a Custom AI configuration is being introduced for Phase 2
work that wasn't used in Phase 1.

Run this prompt *after* loading the Phase 1 Information Report and
*before* Step 01.

---

### `step-01-phase-1-input-validation.prompt.md`
**Type:** Interview Prompt → Action Prompt | **SDD Step:** Specify → Implement

Loads the Phase 1 Current-State Information Report and confirms the
AI's understanding of it. Specifically validates: the Must-Change
register (count, scope, priority indications), the baseline rows that
each MC links to, the constraint envelope (hard constraints), the
sharpened improvement objective, the worst-case mechanism narrative,
the Phase 1 self-evaluation scorecard, and any flagged CONDITIONAL or
FAIL gates that Phase 2 must address.

**Key design decision:** Phase 2 does not re-discover what Phase 1
already established. Step 01's job is to validate and load — not to
re-interview the practitioner. The discipline is *confirm understanding
of recorded findings*, not *re-elicit findings from memory*.

**Key output elements:** Confirmed MC register summary, confirmed
constraint envelope, confirmed objective, validation gaps register
(if Phase 2 spots something Phase 1 should have addressed), open
questions for the practitioner to resolve before Phase 2 work
continues.

---

### `step-02-principle-weighting.prompt.md`
**Type:** Interview Prompt → Action Prompt | **SDD Step:** Specify → Implement

Assigns explicit weights to the six Core Principles for this
improvement cycle. The weights affect every downstream decision —
mechanism choices weight differently if Security is 2× vs. 1×,
sequencing changes if Operations dominates, cost ceilings depend on
what counts as expensive. Phase 1's Step 06 self-evaluation
flagged principle weighting as the CONDITIONAL gate; Phase 2's
Step 02 resolves it.

**Key design decision:** Weights are explicit, justified, and
durable. A "we'll weight Security higher" without quantitative
expression and rationale is not a decision — it's a sentiment.
Output the weights as a row per principle with weight, rationale,
and the project characteristic that drove the choice.

**Key output elements:** Principle-weight table with weight,
rationale, and source characteristic per principle; check that
weights collectively make sense (no single principle dominates
unintentionally); identification of which downstream decisions are
most weight-sensitive.

---

### `step-03-mechanism-decisions.prompt.md`
**Type:** Interview Prompt → Action Prompt | **SDD Step:** Specify → Implement

For each Must-Change that has multiple candidate mechanisms,
chooses one and documents the road not taken. The Phase 1
Information Report often surfaces MCs with multiple ways to address
them (the Diamonds run had several: lodash patch-bump vs. replacement,
simpler-CI vs. unified-DevContainer, OSS doc-site tool selection).
Step 03 resolves these.

**Key design decision:** Default to draft-and-react mode. The AI
proposes a mechanism choice based on the weighted principles, the
practitioner reacts (accept, amend, reject), and the chosen
mechanism is documented along with the alternatives considered and
the rationale. Rejection of a draft is high-signal input — treat
it with architectural weight.

**Key output elements:** Per-MC mechanism table with chosen
mechanism, alternatives considered, principle-weighted rationale,
verification method (how Phase 6 will check correctness of this
choice), and dependencies on other MC mechanism decisions.

---

### `step-04-sequencing-and-tiering.prompt.md`
**Type:** Interview Prompt → Action Prompt | **SDD Step:** Specify → Implement

Produces the dependency-respecting sequence of MCs with explicit
tier boundaries (typically: Foundation / Capability / Productization
or equivalent). Identifies the minimum-viable-completion floor (the
subset that produces a defensible improvement-cycle outcome if
capacity runs out) and the stretch scope. Includes the
**worst-case-plan-failure narrative** that asks: if this plan fails
in execution, what's the common mechanism producing the failure
across branches?

**Key design decision:** Sequencing is a principle-weighted
decision. A plan that addresses Security MCs first is a different
plan from one that addresses Productization MCs first; the
weighting from Step 02 determines which is right. Tier boundaries
make capacity trade-offs explicit — Phase 2 explicitly names what
gets cut first.

**Key output elements:** Tiered sequence with dependencies named,
minimum-viable-completion floor with rationale, stretch scope with
rationale, worst-case-plan-failure narrative seeking common
mechanism across failure modes, sequencing rationale tied to
principle weights.

---

### `step-05-cost-modeling-and-capacity-check.prompt.md`
**Type:** Interview Prompt → Action Prompt | **SDD Step:** Specify → Implement

Produces per-MC cost estimates with MEASURED / ESTIMATED /
BELIEVED / UNMEASURED tags. Checks whether the tiered plan from
Step 04 fits the budget envelope (time, infrastructure, AI-tool
cost, opportunity cost). Identifies cost concentrations and the
sensitivity of the plan to cost overruns.

**Key design decision:** Cost modeling uses the same tagging
discipline as Phase 1 baselines. Solo OSS work uses rough
ESTIMATED tags ("MC-02 = 1 hour" rather than "$300 of labor");
enterprise teams produce MEASURED budget commitments with line
items. The tag tells downstream phases how much to trust the
estimate.

**Key output elements:** Per-MC cost row with tag and rationale,
per-tier cost summary, total cost vs. budget envelope comparison,
cost-concentration analysis (which MCs dominate cost), capacity
check (does the plan fit available capacity given the constraint
envelope), re-sequencing recommendation if the plan exceeds
capacity.

---

### `step-06-improvement-plan-synthesis.prompt.md`
**Type:** Action Prompt + Evaluation Prompt | **SDD Step:** Implement → Correctness Verification

**This is the only file in this directory that is not an interview
prompt.** The practitioner pastes all five completed Phase 2
artifacts into the session and the AI synthesizes them into the
Improvement Plan, then immediately conducts the built-in
self-evaluation. The Improvement Plan is the primary handoff
artifact from Phase 2 to Phases 3 through 7.

**Key design decision:** Step 06 is synthesis-only. If Step 06 is
producing net-new mechanism choices, net-new sequencing, or
net-new cost estimates that were not present in Steps 01–05,
something was missed upstream — pause Step 06 and fix the upstream
gap. The scorecard rigor discipline applies: CONDITIONAL is
preferred over PASS-with-caveats; aim for 4–5 PASS + 1–2
CONDITIONAL on a well-executed Phase 2.

**Key output elements:** Executive summary, the Plan
(tiered sequence with per-MC entries containing chosen mechanism,
dependencies, acceptance criteria seed, principle weights
addressed, cost estimate with tag), cost summary, principle-
weighted scorecard, minimum-viable-completion floor vs. stretch
scope, Phase 3 design briefs, Phase 5 task-list seed, worst-case
plan-failure narrative, self-evaluation scorecard, source register.

---

## MCP Servers and AI Tool Augmentation

This tool set is designed to work well with standard Claude
capabilities, but certain MCP connectors materially improve
productivity. **These are strongly encouraged but not strictly
required.** When a connector is unavailable or fails, the tool set
degrades gracefully into copy-paste requests to the practitioner —
nothing blocks.

Meaningful connectors for this tool set:

- **GitHub MCP** — Enables direct consultation of the project's
  issue tracker when an MC's mechanism choice depends on
  understanding open issues, PRs, or release history that Phase 1
  surfaced. Also useful for cross-repo dependency-check during
  sequencing. When unavailable: practitioner pastes relevant issue
  excerpts on request.

- **Context7 (or equivalent library-documentation connector)** —
  Enables authoritative lookups for library and framework
  documentation when a mechanism choice depends on understanding
  upstream-current options, migration paths, or compatibility
  windows. When unavailable: the AI uses training-data knowledge
  with a confidence caveat and the practitioner confirms
  current values.

- **Direct code access** (Claude Code, Cursor with repo-connected
  session, filesystem access, or equivalent) — Enables the AI to
  verify mechanism choices against the actual codebase rather than
  Phase 1 finding descriptions. Materially raises confidence levels
  for mechanism decisions involving specific code paths or
  integration patterns. When unavailable: mechanism decisions are
  tagged with Phase 1 finding references as evidence basis.

The implementer is expected to be an expert in their own AI
environment and is best positioned to decide how to enable these
connectors. This tool set does not prescribe implementation details.

---

## How to Use This Tool Set

### Prerequisites

Before opening any prompt file:

1. Load `analysis-improvement-planning.existing-project.instructions.md`
   as project-level instructions in your AI environment.
2. Load the Phase 1 Current-State Information Report as context.
3. If available, load the v1.2 ai-centric-playbook skill for
   framework-level reasoning depth.

### Recommended Sequence

The six discovery artifacts are designed to build on each other.

```
0. Initial Specify interview (via instructions file)
   ↓ (load Phase 1 Information Report; sharpen Phase 2 intent)
0b. step-00-building-block-discovery.prompt.md
   ↓ (toolset-augmentation document for this Phase 2 run)
1. step-01-phase-1-input-validation.prompt.md
   ↓ (confirmed understanding of Phase 1 inputs; validation gaps)
2. step-02-principle-weighting.prompt.md
   ↓ (principle weights; rationale; sensitivity analysis)
3. step-03-mechanism-decisions.prompt.md
   ↓ (per-MC mechanism choices; alternatives considered; verification methods)
4. step-04-sequencing-and-tiering.prompt.md
   ↓ (tiered sequence; minimum-viable floor; worst-case plan-failure narrative)
5. step-05-cost-modeling-and-capacity-check.prompt.md
   ↓ (per-MC cost rows; capacity check; re-sequencing if needed)
6. step-06-improvement-plan-synthesis.prompt.md
   ↓ (synthesis of all five → Improvement Plan + self-evaluation scorecard)
```

**Running each prompt:**
1. Open a new AI session.
2. Confirm
   `analysis-improvement-planning.existing-project.instructions.md`
   is loaded as project context.
3. Paste the Phase 1 Information Report and completed prior Phase 2
   artifacts (and the step-00 toolset-augmentation document) above
   the kickoff line for additional context.
4. Paste the **System Instructions** section from the prompt file
   as your system prompt (if not already loaded via the instructions
   file).
5. Paste the **Kickoff** line to begin.
6. React to drafts — Phase 2 prompts default to draft-and-react
   mode for their decision-heavy work. Practitioner rejection of
   a draft is high-signal input.
7. Review the output artifact against the prompt's evaluation
   checklist before accepting it as complete.

**Running the synthesis (Step 06):**
1. Open a new AI session with a large context window.
2. Paste all five completed Phase 2 artifacts in recommended sequence
   order, plus the Phase 1 Information Report for cross-reference.
3. Paste the synthesis kickoff line.
4. Review both the Improvement Plan and the self-evaluation scorecard.

### Iterating

The SDD cycle is iterative. If the Step 06 self-evaluation returns
a CONDITIONAL or FAIL gate on any principle, cycle back to the
relevant artifact prompt, fill the gap, and re-run Step 06. This is
expected behavior, not a failure — the gate system exists to catch
gaps before they become Phase 3 problems.

---

## The Self-Evaluation Scorecard

Step 06's built-in self-evaluation is the phase gate that determines
whether Phase 2 is complete. It evaluates the Improvement Plan
against all six Core Principles, **applying the weights established
in Step 02**, and produces a gate status for each:

| Gate Status | Meaning | Phase 3 Action |
|-------------|---------|---------------|
| **PASS** | Sufficient for Phase 3 to proceed on this dimension | Proceed |
| **CONDITIONAL** | Sufficient with documented caveats; specific gaps must be addressed within Phase 3 before relevant decisions are made | Proceed with documented remediation plan |
| **FAIL** | Insufficient; Phase 3 cannot responsibly proceed on this dimension | Cycle back to Phase 2 |

A single FAIL gate does not block all of Phase 3 — it blocks Phase 3
on that specific dimension. CONDITIONAL gates allow Phase 3 to
proceed with documented caveats. The discipline of preferring
CONDITIONAL over PASS-with-caveats applies — a CONDITIONAL with
explicit rationale surfaces a decision point; a buried caveat in
a PASS is easier to miss.

---

## Common Pitfalls

**Re-discovering what Phase 1 established.** Phase 2's Step 01 is
*input validation*, not re-interview. If Phase 2 finds itself
re-asking questions Phase 1 answered, something is wrong — either
Phase 1's report is unclear (cycle back to Phase 1) or Phase 2 is
exceeding its scope.

**Setting principle weights as sentiment, not decision.** "Security
is important to us" is a value statement, not a weight. "Security
is weighted 1.5× because we have three production environments and
external auditor engagement is expected within six months" is a
decision. Weights must be quantitative and have a rationale tied to
a project characteristic.

**Choosing mechanisms without principle grounding.** Mechanism
choices that don't trace back to the weighted principles are
choices made on instinct. Document the principle-weighted
rationale for every mechanism decision.

**Sequencing without dependency check.** A plan that puts MC-X
before MC-Y when MC-Y must complete first will fail in execution.
Step 04's dependency-respecting discipline is not optional.

**Cost estimates without tags.** An untagged cost estimate looks
like a measurement. Tagging it ESTIMATED or BELIEVED tells
downstream phases how much to trust it. The tag is not optional.

**Skipping the worst-case plan-failure narrative.** The narrative
catches over-ambitious plans, mis-sequenced dependencies, and
capacity-exceeded scopes before they're committed to. Phase 1's
worst-case narrative produced the most useful synthesis of the
Diamonds run; the same discipline applies here.

**Accepting a synthesis without reviewing the scorecard.** The
self-evaluation scorecard is the phase gate. A CONDITIONAL or FAIL
gate that is ignored or deprioritized does not go away — it
surfaces as a problem in Phase 3 when it is significantly more
expensive to address.

**Producing a plan that serves humans but not AI.** Phases 3
through 7 consume this plan as AI input context. Narrative prose
buried in unstructured sections is insufficient. Structure, label,
and format every output for machine parseability alongside human
readability.

---

## Connecting to Phase 3 and Beyond

The Improvement Plan is the primary handoff artifact from Phase 2
to every subsequent phase:

- **Phase 3 (Design & Technical Analysis)** consumes the Phase 3
  design briefs from Step 06, the chosen mechanisms from Step 03,
  and the principle weights from Step 02.
- **Phase 4 (Architecture & Modular Design)** consumes the
  sequencing from Step 04 and the mechanism choices that affect
  module boundaries.
- **Phase 5 (Implementation)** consumes the Phase 5 task-list seed
  from Step 06 and uses it as the starting point for implementation
  task authoring.
- **Phase 6 (Testing & Audit)** consumes the verification methods
  named per mechanism in Step 03 and uses them as the basis for
  the principle-weighted scorecard at Phase 6.
- **Phase 7 (Deployment & Evolution)** consumes the minimum-viable-
  completion floor and stretch scope from Step 04 to inform
  release planning and dormancy-prevention cadence.

In existing-project work, Phase 2 transforms Phase 1's evidence
into Phases 3–7's execution input. Phase 2 does not re-discover
the system; Phase 3 does not re-decide the plan. The quality of
Phase 2 directly determines the quality of every phase that
follows.

---

## Dogfooding & Calibration Guidance

This tool set is refined through dogfooding runs — running the
tool set on real projects and capturing observations about
where it works, where it doesn't, and what should change.

**Expected dogfooding observation count per complete Phase 2 run
is 15–25.** Phase 2 is shorter than Phase 1 (fewer discovery
unknowns, more confirmed inputs), so observation counts trend
lower. Counts below 8 warrant skepticism about self-criticism
rigor; counts above 40 suggest foundational tool set issues
requiring a larger revision than incremental version improvements.

Observations captured during a run are reviewed end-of-phase
and categorized as Accept, Refine, Defer, or Reject. Accepted
observations drive the version increment.

---

## Version History

| Version | Date | Source | Summary |
|---------|------|--------|---------|
| v1.0 | 2026-04-22 | Initial authoring | Initial existing-project Phase 2 variant. Authored to v1.2 conventions established by Phase 1 existing-projects toolset. Six step prompts plus instructions file plus step-00 Building Block Discovery plus README. Decision-heavy structure with draft-and-react default; principle weighting elevated to its own step (Step 02) resolving Phase 1's Scoring & Metrics CONDITIONAL; worst-case-plan-failure narrative discipline integrated into Step 04 Sequencing. |

---

*Part of the AI-Centric Software Development Playbook*
*Phase 2 Analysis & Improvement Planning (Existing Projects) Tool Set — v1.0*
