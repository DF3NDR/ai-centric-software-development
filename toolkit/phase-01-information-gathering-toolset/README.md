# Phase 1: Information Gathering — Tool Set
## AI-Centric Software Development Playbook

---

## Overview

This directory contains the complete tool set for **Phase 1: Information
Gathering** of the AI-Centric Software Development Playbook. It is the
first phase of a seven-phase framework for building software with small,
AI-augmented teams.

Phase 1 answers the questions every subsequent phase depends on: what
exists in the technology landscape, what comparable systems have built
and learned, what the system needs to do, what risks and constraints
apply, and what can be reused rather than built from scratch. Done well,
it gives the team a shared, evidence-grounded foundation before any
design or architecture decisions are made. Done poorly — or skipped —
every subsequent phase builds on assumptions rather than evidence.

The primary output of this phase is the **Information Report** — a
structured document synthesized from five research artifacts, designed
for both human decision-making and AI consumption in every subsequent
phase. It is the handoff artifact to Phase 2 (Analysis & Stack
Selection).

---

## Framework Context

This tool set is part of the
[AI-Centric Software Development Playbook](../../README.md),
a practitioner's framework for small teams (1–5 people) that use AI
tools to deliver what large organizations once required.

Three framework concepts are essential to understanding how this tool
set works:

### The Six Core Principles

Every artifact in this tool set is filtered through six principles that
travel with the project from Phase 1 through deployment. The first four
define *what you are optimizing for*. The last two define *how you know
you are getting it right*.

| Principle | What It Asks in Phase 1 |
|-----------|------------------------|
| **Security** | What are the known vulnerabilities in candidate technologies? What compliance requirements apply? What is the domain threat landscape? |
| **Maintainability** | How well-documented are the options? What is the community health? What is the talent pool? |
| **Economics** | What are the actual licensing and infrastructure costs? What does development velocity look like at scale? What are AI tooling costs? |
| **Operations** | What is the deployment story? What are the scaling characteristics and known failure modes? What observability tooling exists? |
| **Scoring & Metrics** | What quantitative benchmarks exist? What scoring criteria will Phase 2 need? What baselines can comparable systems provide? |
| **Correctness Verification** | Are claims cross-referenced? Are sources dated? Are confidence levels assigned? Are research gaps explicitly documented? |

The principles are not evaluated at the end of Phase 1. They shape what
information is gathered, how it is evaluated, and what questions are
asked — from the first interview through the final synthesis.

### Specification Driven Development (SDD)

All work in this phase follows the SDD cycle — the same iterative,
specification-first methodology that drives every phase of the
framework. The cycle does not change; the tool sets that power it do.
```
Specify → Plan → Detail → Task → Implement
```

| SDD Step | What Happens in Phase 1 | Output |
|----------|------------------------|--------|
| **Specify** | Interview the practitioner to define what information is needed and why | Research Specification |
| **Plan** | Break the research into organized sections by domain of inquiry | Research Plan |
| **Detail** | Generate specific, evaluable research questions per section | Research Requirements Document |
| **Task** | Convert questions into concrete, actionable research tasks | Task list with acceptance criteria |
| **Implement** | Execute research, evaluate findings, synthesize into artifacts | Five research artifacts + Information Report |

The cycle is iterative. When implementation reveals gaps in the
specification, cycle back. When findings in one area raise new
questions in another, add them to the task list. The SDD cycle is
not a one-way pipeline — it is a structured loop.

### Tool Sets

A tool set is a curated combination of building blocks — prompts,
instructions, skills, MCP connections, and resources — assembled for
a specific purpose. This directory contains the Phase 1 tool set: the
instructions file that provides overarching context, and the individual
prompt files that produce each research artifact.

---

## Directory Contents
```
phase-1-information-gathering/
├── README.md                                    ← You are here
├── information-gathering.instructions.md        ← Load this first
├── technology-landscape-assessment.prompt.md    ← Artifact 1
├── competitive-market-scan.prompt.md            ← Artifact 2
├── requirements-sketch.prompt.md               ← Artifact 3
├── risk-constraint-inventory.prompt.md          ← Artifact 4
├── reusable-components-catalog.prompt.md        ← Artifact 5
└── information-report-synthesis.prompt.md       ← Final synthesis
```

---

## File Descriptions

### `information-gathering.instructions.md`
**Type:** Instructions file (load as project or system context)

The overarching instructions for any AI assistant operating in Phase 1.
Contains the full framework orientation — the SDD cycle, all six Core
Principles applied to this phase, behavioral guidelines, output
standards, common pitfalls, and the connection to Phase 2. Load this
file as project-level instructions in your AI environment before using
any of the prompt files.

*Use in: Claude Project Instructions, VS Code AI instructions,
Cursor rules, or equivalent.*

---

### `technology-landscape-assessment.prompt.md`
**Type:** Interview Prompt → Action Prompt | **SDD Step:** Specify → Implement

Conducts a structured conversational interview to gather what is needed,
then produces the Technology Landscape Assessment. Covers frameworks,
languages, platforms, services, and tools available for the kind of
system being built — evaluated across all six Core Principles for
maturity, community health, security posture, economic characteristics,
and operational fit.

**Key output elements:** Candidate technology comparison tables per
category, principle assessments per category, ecosystem trend analysis,
principal tensions identified, confidence-rated findings.

---

### `competitive-market-scan.prompt.md`
**Type:** Interview Prompt → Action Prompt | **SDD Step:** Specify → Implement

Conducts a structured interview to gather competitive and market
intelligence, then produces the Competitive & Market Scan. Covers
comparable systems, their technology choices and outcomes, validated
patterns across multiple implementations, documented failure modes,
security incidents, operational patterns, and build-vs-buy lessons.

**Key design decision:** Explicitly separates *direct competitors*
(market intelligence) from *technical reference implementations*
(pattern mining) — and enforces the distinction between patterns
(appearing in 2+ independent implementations) and anecdotes (single
examples). Both distinctions matter for how Phase 2 weights the evidence.

**Key output elements:** Comparable systems catalog, recurrent technology
patterns with evidence, failure pattern analysis, security and compliance
baseline from comparables, operational SLA benchmarks.

---

### `requirements-sketch.prompt.md`
**Type:** Interview Prompt → Action Prompt | **SDD Step:** Specify → Implement

Conducts a structured interview to capture an initial articulation of
what the system needs to do, then produces the Requirements Sketch. This
is *not* the final requirements document — that comes in Phase 3 through
the SDD Detail step. It is the initial capture of user needs, business
goals, constraints, and non-negotiable requirements that will shape every
subsequent decision.

**Key behavioral constraint:** The AI is explicitly prohibited from
allowing solution assumptions to masquerade as requirements. If the
practitioner says "we need a REST API," the prompt pushes back: what user
or business need does that serve? The requirement is the need; the API
is a Phase 2 decision.

**Key output elements:** Must-have vs. should-have requirements
classified by priority, non-negotiable constraints with sources, scale
and performance boundaries, reliability requirements, success and failure
definitions, requirements conflicts surfaced explicitly, principle
coverage summary.

---

### `risk-constraint-inventory.prompt.md`
**Type:** Interview Prompt → Action Prompt | **SDD Step:** Specify → Implement

Conducts a structured interview across four distinct risk and constraint
categories, then produces the Risk & Constraint Inventory. The four
categories — compliance constraints, security risks, hard constraints,
and project/operational risks — are kept explicitly separate because they
require different treatment in downstream phases.

**Key design decision:** Compliance constraints are non-negotiable
external obligations — they are satisfied or the project faces
regulatory consequence. Security risks are threats to be analyzed and
mitigated. Conflating them produces an inventory where neither gets the
treatment it deserves. This prompt enforces the distinction structurally.

**Key output elements:** Compliance and regulatory constraint table with
architecture implications, threat actor profiles, data exposure risk
table, attack surface inventory, hard constraint register, project and
operational risk tables, priority risk register consolidated across all
categories, worst-case security scenario, cross-phase handoff notes.

---

### `reusable-components-catalog.prompt.md`
**Type:** Interview Prompt → Action Prompt | **SDD Step:** Specify → Implement

Conducts a structured interview across four component categories, then
produces the Reusable Components Catalog. Covers internal existing
assets, open-source libraries, managed API services and platforms, and
standard patterns and reference architectures.

**Key design decision:** Every managed service requires a documented
exit strategy — how difficult is migration if the vendor is acquired,
discontinued, or doubles pricing? This requirement is enforced at
adoption time, when the team has full leverage, rather than discovered
under pressure two years into production.

**Key output elements:** Build-vs-buy summary by functional area,
evaluated and recommended components per category with principle
assessments, evaluated and rejected components with documented rationale,
license and compliance register, dependency risk summary, build scope
reduction estimate for Phase 2 cost modeling, catalog index.

---

### `information-report-synthesis.prompt.md`
**Type:** Action Prompt + Evaluation Prompt | **SDD Step:** Implement → Correctness Verification

**This is the only file in this directory that is not an interview
prompt.** It is an action prompt — the practitioner pastes all five
completed artifacts into the session and the AI synthesizes them into
the Information Report, then immediately conducts a built-in
self-evaluation.

The Information Report is the primary handoff artifact from Phase 1 to
Phase 2. When Phase 2 tool sets activate, the Information Report becomes
their primary input context. The AI in Phase 2 does not start from zero
— it starts from the structured findings here.

**Key output elements:** Executive summary, project context snapshot,
technology landscape with cross-references to compliance and competitive
findings, competitive intelligence structured for Phase 2 use, compliance
and regulatory map, consolidated risk register, reusable components with
build scope reduction estimate, principal tensions documented for Phase 2
navigation, Phase 2 readiness inputs section, gap register, source and
confidence register, self-evaluation scorecard.

---

## How to Use This Tool Set

### Prerequisites

Before opening any prompt file, load
`information-gathering.instructions.md` as project-level instructions
in your AI environment. This gives every AI session the framework
context, behavioral guidelines, and output standards it needs without
requiring the practitioner to re-establish context in each session.

### Recommended Sequence

The five research artifacts are designed to build on each other. While
they can be run in any order, this sequence is recommended because each
artifact provides useful context for the next:
```
1. technology-landscape-assessment.prompt.md
   ↓ (what exists)
2. competitive-market-scan.prompt.md
   ↓ (what others built and learned)
3. requirements-sketch.prompt.md
   ↓ (what this system must do)
4. risk-constraint-inventory.prompt.md
   ↓ (what could go wrong and what is fixed)
5. reusable-components-catalog.prompt.md
   ↓ (what can be adopted rather than built)
6. information-report-synthesis.prompt.md
   ↓ (synthesis of all five → Information Report)
```

**Running each prompt:**
1. Open a new AI session
2. Confirm `information-gathering.instructions.md` is loaded as
   project context
3. Optionally paste completed prior artifacts above the kickoff line
   for additional context
4. Paste the **System Instructions** section from the prompt file
   as your system prompt (if not already loaded via the instructions
   file)
5. Paste the **Kickoff** line to begin
6. Answer questions one at a time — the AI interviews you
   conversationally
7. Review the output artifact against the prompt's evaluation checklist
   before accepting it as complete

**Running the synthesis:**
1. Open a new AI session with a large context window
2. Paste all five completed artifacts in recommended sequence order
3. Paste the synthesis kickoff line
4. Review both the Information Report and the self-evaluation scorecard

### Iterating

The SDD cycle is iterative. If the synthesis self-evaluation returns a
CONDITIONAL or FAIL gate on any principle, cycle back to the relevant
artifact prompt, fill the gap, and re-run synthesis. This is expected
behavior, not a failure — the gate system exists to catch gaps before
they become Phase 2 problems.

---

## The Self-Evaluation Scorecard

The synthesis prompt's built-in self-evaluation is the phase gate that
determines whether Phase 1 is complete. It is not optional and it is
not a formality. It is the mechanism that makes the Information Report
trustworthy as a Phase 2 input.

The scorecard evaluates the Information Report against all six Core
Principles and produces a gate status for each:

| Gate Status | Meaning | Phase 2 Action |
|-------------|---------|---------------|
| **PASS** | Sufficient for Phase 2 to proceed on this dimension | Proceed |
| **CONDITIONAL** | Sufficient with documented caveats; specific gaps must be addressed within Phase 2 before relevant decisions are made | Proceed with documented remediation plan |
| **FAIL** | Insufficient; Phase 2 cannot responsibly proceed on this dimension | Cycle back to Phase 1 |

### What Each Gate Evaluates

**Security — PASS requires:**
Compliance requirements identified with architecture implications,
threat actor profile established, known vulnerability history
documented for candidate technologies, security tooling availability
assessed for candidate stacks. If this gate fails, Phase 2 threat
modeling will operate on incomplete data.

**Maintainability — PASS requires:**
Documentation quality assessed for candidate technologies,
community health data present with quantitative indicators (not
qualitative impressions), testing ecosystem evaluated, talent pool
and hiring market assessed. If this gate fails, Phase 2 stack scoring
on the Maintainability dimension will lack supporting evidence.

**Economics — PASS requires:**
Actual cost data present — not estimates — for licensing and
infrastructure at target scale, development velocity indicators
documented for candidate stacks, AI tooling costs estimated,
build scope reduction quantified from the components catalog.
If this gate fails, Phase 2 cost modeling will produce unreliable
projections.

**Operations — PASS requires:**
Deployment and orchestration options covered with operational
complexity assessed, scaling characteristics and known limits
documented, observability tooling availability assessed, integration
patterns documented for the candidate ecosystem. If this gate fails,
Phase 2 cannot reliably evaluate operational fit of stack candidates.

**Scoring & Metrics — PASS requires:**
Quantitative benchmarks present with sources and dates — no
qualitative-only claims in benchmark-relevant sections, comparable
system SLA and performance data present to support Phase 2 benchmark
definition. "Framework X is fast" fails this gate. "Framework X
achieves 50,000 req/s on a single-core benchmark per [source, date]"
passes it.

**Correctness Verification — PASS requires:**
Confidence levels (High / Medium / Low) assigned to all significant
claims, all key claims cite a specific source and a date, conflicts
between source artifacts are documented rather than silently resolved,
research gaps are explicitly registered in the gap register.
If this gate fails, Phase 2 will be working with unverified claims
that may not hold up under analysis.

### Gate Logic

A single FAIL gate does not block all of Phase 2 — it blocks Phase 2
on that specific dimension. The team must cycle back to the relevant
Phase 1 artifact prompt, fill the gap, and re-run synthesis before
Phase 2 makes decisions in that area.

CONDITIONAL gates allow Phase 2 to proceed with documented caveats.
Each conditional pass must have a named remediation action, a
responsible owner, and a target date. Conditional passes that
accumulate without remediation degrade into silent failures over time.

The gate system's value is in its honesty. An Information Report that
passes all six gates with documented confidence is worth more to Phase 2
than a report that appears comprehensive but contains low-confidence
claims passed off as established findings.

---

## Artifact Dependency Map
```
technology-landscape-assessment
        │
        ├──────────────────────────────────────┐
        │                                      │
competitive-market-scan              requirements-sketch
        │                                      │
        └──────────────┬───────────────────────┘
                       │
             risk-constraint-inventory
                       │
                       │
           reusable-components-catalog
                       │
                       ▼
          information-report-synthesis
          (consumes all five artifacts)
                       │
                       ▼
            Information Report
          [Phase 1 → Phase 2 handoff]
```

Cross-artifact connections that the synthesis must surface:
- Compliance requirements (Risk & Constraint) → constrain technology
  choices (Technology Landscape)
- Competitive patterns (Competitive Scan) → validate component
  candidates (Reusable Components)
- Hard constraints (Risk & Constraint) → bound requirements
  (Requirements Sketch)
- Build scope reduction (Reusable Components) → feeds cost modeling
  inputs for Phase 2

---

## Common Pitfalls

**Gathering without specifying.** Starting research before defining
what needs to be found produces sprawling, unfocused output. The SDD
Specify step is not overhead — it is what makes the research useful.

**Breadth without depth.** AI makes broad scanning easy. The research
plan must explicitly identify which areas need deep investigation and
which need only surface awareness. A report that mentions fifty
frameworks but deeply evaluates none fails Phase 2.

**Trusting AI output without verification.** AI gathers information
fast and confidently — including outdated, misinterpreted, or
plausible-sounding information that doesn't hold up to scrutiny.
Correctness Verification is not optional. Sources must be cited,
dates must be checked, claims must be cross-referenced.

**Conflating compliance constraints with security risks.** Compliance
constraints are non-negotiable external obligations — they cannot be
mitigated away, only satisfied. Security risks are threats to analyze
and address. Conflating them produces a risk inventory where neither
gets the treatment it requires.

**Treating Phase 1 as principle-free.** Information gathering is not
neutral data collection. A technology landscape assessment that ignores
security vulnerability history is incomplete regardless of how
thorough it looks elsewhere. The Core Principles apply from the
first question.

**Producing a report that serves humans but not AI.** Narrative prose
buried in unstructured sections is insufficient for downstream AI
consumption. Structure, label, and format every output for machine
parseability alongside human readability. If a Phase 2 AI tool set
cannot load the Information Report as context and produce useful
analysis from it, the report structure needs work.

**Accepting a synthesis without reviewing the scorecard.** The
self-evaluation scorecard is the phase gate. A CONDITIONAL or FAIL
gate that is ignored or deprioritized does not go away — it surfaces
as a problem in Phase 2 when it is significantly more expensive to
address.

---

## Connecting to Phase 2

The Information Report is the direct input to every Phase 2 tool set:

- **Business Analysis Tool Set** — consumes the competitive findings,
  requirements sketch, and market context
- **Cost Modeling Tool Set** — consumes the technology landscape cost
  data, components catalog build scope reduction, and hard constraints
- **Stack Evaluation Tool Set** — consumes the technology landscape
  assessments, competitive technology patterns, and compliance map
- **Threat Modeling Tool Set** — consumes the risk inventory, threat
  actor profiles, and compliance requirements
- **Benchmark Definition Tool Set** — consumes the competitive SLA
  and performance benchmarks, and the requirements sketch performance
  targets

Phase 2 does not re-gather information. It analyzes, evaluates, and
decides — using the Information Report as the evidence base. The quality
of Phase 1 directly determines the quality of Phase 2. A shallow
Information Report produces shallow analysis. A principle-filtered,
well-verified, AI-parseable Information Report gives Phase 2 a strong
foundation.

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | [date] | Initial release — all six files |

---

## Related Resources

- [AI-Centric Software Development Playbook — Full Series](../../README.md)
- [Article 1 — Core Principles](../../articles/article-01-core-principles.md)
- [Article 2 — Building Your Toolkit](../../articles/article-02-building-your-toolkit.md)
- [Article 3 — Phase 1: Information Gathering](../../articles/article-03-information-gathering.md)
- [Phase 2 Tool Set](../phase-2-analysis-stack-selection/README.md)
  *(forthcoming)*

---

*Part of the AI-Centric Software Development Playbook*
*This tool set is a living artifact — it will be refined as the
methodology matures and as use in practice reveals improvements.*
