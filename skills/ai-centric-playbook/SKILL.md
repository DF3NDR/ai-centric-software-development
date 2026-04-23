---
name: ai-centric-playbook
description: Use this skill when the conversation involves the AI-Centric Software Development Playbook — a principle-driven, specification-first framework for small-team AI-orchestrated software development. Invoke when the user mentions "the Playbook," "AI-Centric Software Development," "Core Principles" in a software-process context, "SDD cycle" or "Specification Driven Development" when referring to the framework, "tool set" or "toolkit" in a Playbook-aligned context, any of the seven phases (Information Gathering, Analysis & Stack Selection, Design & Technical Analysis, Architecture & Modular Design, Implementation, Testing & Audit, Deployment & Evolution), or when asked to build/evaluate prompts, skills, instruction sets, or MCP servers consistent with the framework. Also invoke when the user asks how to apply principle-driven reasoning to a software decision (security / maintainability / economics / operations / scoring & metrics / correctness verification) in a way that suggests they are working within this framework.
---

# AI-Centric Software Development Playbook

## What This Skill Is

This skill encodes the framework knowledge from the **AI-Centric Software Development Playbook** — a methodology for small-team (1–5 person) AI-orchestrated software delivery. The Playbook's central thesis is that skilled practitioners using AI as a force multiplier can deliver what large organizations once required. Human judgment, architectural thinking, and domain expertise remain irreplaceable; what changes is the interface through which that knowledge is applied.

## When to Invoke This Skill

Invoke this skill when the practitioner is:

- Applying the framework to a real project at any of the seven phases
- Building, evaluating, or revising prompts, skills, instruction sets, MCP servers, or tool sets
- Making a software decision that should be filtered through the six Core Principles
- Asking about SDD cycle mechanics (Specify → Plan → Detail → Task → Implement)
- Crossing a phase boundary and needs the handoff expectations
- Uncertain whether something (a concern, a decision, a request) falls inside the framework's scope

Do **not** invoke this skill for:

- General software engineering questions unrelated to the Playbook
- Tasks where the practitioner is explicitly working outside the framework
- Purely informational requests about specific technologies (those are regular knowledge questions)

## The Framework in One Page

### The Central Thesis

> Small teams (1–5 people) orchestrating AI tools can deliver what large organizations once required. The fundamentals of computer science, architecture, security, and design thinking remain essential. What changes is the *interface* through which that knowledge is applied.

### The Six Core Principles

Every decision, output, and evaluation passes through these six concurrent lenses (not a sequential checklist):

| # | Principle | What It Asks |
|---|-----------|-------------|
| 1 | **Security** | What can go wrong? What are the known vulnerabilities? What compliance applies? |
| 2 | **Maintainability** | Can this be understood by someone not in the room? Is it tested, documented, structured for change? |
| 3 | **Economics** | What does this cost across the full lifecycle? How does cost change at scale? |
| 4 | **Operations** | How does this deploy? How does it scale? How do we know when it's wrong? |
| 5 | **Scoring & Metrics** | What quantitative benchmarks measure this? Without scoring, principles are aspirations. |
| 6 | **Correctness Verification** | Is it right, not just performant? Without verification, scores are self-reported grades. |

Principles 1–4 are *what you're optimizing for*. Principles 5–6 are *how you know you're getting it right*.

For depth on each principle — their concrete questions, common pitfalls, and how they interact — load `core-principles.md`.

### The SDD Cycle

All work follows **Specification Driven Development**:

```
Specify → Plan → Detail → Task → Implement
```

- **Specify** — Interview-style prompts gather needs, context, constraints
- **Plan** — Transform specification into sections/epics
- **Detail** — Each section becomes a Project Requirement Document (PRD) embedding Core Principles as concrete requirements
- **Task** — PRD drives an actionable task list with acceptance criteria
- **Implement** — Produce results; evaluate against PRD; score; verify; iterate

**Key behaviors:**
- Iterative, not linear — output feeds back into specification
- Applies at every phase — tool sets change; methodology doesn't
- Specifications are living documents

For depth on the cycle mechanics, how it adapts per phase, and common pitfalls, load `sdd-cycle.md`.

### The Toolkit

**Six building block types** combined into **tool sets** for specific purposes:

| # | Building Block | Purpose |
|---|---------------|---------|
| 1 | Consolidated Knowledge Base | Team's existing references made AI-parseable |
| 2 | Prompts | Interview / Action / Evaluation |
| 3 | Skills | Reusable context packages (like this one) |
| 4 | Instruction Sets | Multi-step playbooks |
| 5 | MCP Servers | Bridges to real-world tooling |
| 6 | Custom AIs | Purpose-built configurations |

A **tool set** is a curated combination of building blocks assembled for a specific purpose — e.g., a Phase 1 Information Gathering tool set combines an instructions file, interview prompts, MCP connectors to docs and issue trackers, and a synthesis prompt with self-evaluation.

For depth on building blocks, tool set assembly patterns, and how to build/evaluate them, load `building-blocks-and-toolsets.md`.

### The Seven Phases

Concurrent streams of thinking with natural checkpoints — not waterfall stages:

| Phase | Name | Primary Output |
|-------|------|---------------|
| 1 | Information Gathering | Information Report (greenfield) or Current-State Information Report (existing project) |
| 2 | Analysis & Stack Selection | Stack decisions / Improvement Plan with principle-weighted scoring |
| 3 | Design & Technical Analysis | Data models, API designs, architectural blueprints |
| 4 | Architecture & Modular Design | Modular specifications with security / testability / operational hooks |
| 5 | Implementation | Code + docs + configs + tests, generated, reviewed, verified |
| 6 | Testing & Audit | Conformance testing, correctness verification, final principle scorecard |
| 7 | Deployment & Evolution | Launch, observe, evolve; continuous compliance; feedback loop |

Core Principles are evaluated at every phase. Tool sets differ per phase; methodology is constant.

## Core Behavioral Expectations When Operating in This Framework

When invoked, observe these behaviors:

1. **Apply all six Core Principles concurrently**, not sequentially. Surface trade-offs between them; never resolve by omission.
2. **Orient every request inside the SDD cycle.** Identify which step the practitioner is at; guide them forward.
3. **Human judgment is primary.** The AI produces; the practitioner reviews, evaluates, approves. Never present AI output as final.
4. **Specifications precede implementation.** If the practitioner asks for code without a specification, help them create one first.
5. **Document decisions, trade-offs, and known risks explicitly.** The framework embraces tension between principles as productive — but tension must be named.
6. **Reference the Playbook articles by number when depth is needed** (Articles 0–9 plus series outline). The user's project knowledge may contain them.

## How to Use the Reference Files

This skill ships with three reference files. Load them on demand:

- **`core-principles.md`** — Load when depth on a specific principle is needed, when evaluating an output against the principles, or when designing a principle-weighted scoring rubric.
- **`sdd-cycle.md`** — Load when guiding a practitioner through an SDD step, when the cycle mechanics are unclear, or when writing specifications / PRDs / task lists.
- **`building-blocks-and-toolsets.md`** — Load when building, evaluating, or revising prompts / skills / instruction sets / MCP servers / tool sets; when the practitioner asks how to compose a tool set for a specific purpose; when reviewing tool set quality.

Do not load all three preemptively. Load when the conversation requires the depth.

## Scope Boundaries of This Skill

This skill covers **framework-level reasoning**. It does not cover:

- Specific phase tool sets — those live in `toolkit/phase-NN-*/` directories in the Playbook repository
- Specific technologies, languages, or stacks — those are domain knowledge
- Specific project contexts — those come from the practitioner or their project knowledge

When the practitioner needs phase-specific guidance (e.g., "how do I run a Phase 3 design session?"), the correct move is to direct them to the corresponding phase tool set. This skill provides the framework context that makes those tool sets comprehensible; it does not replace them.

## Related Resources

- **Playbook articles** — Articles 0 through 9 plus the series outline. These are the canonical source. If the practitioner's project knowledge contains them, reference them by number when depth is needed.
- **Phase tool sets** — One per phase, in `toolkit/phase-NN-*/` directories. Currently available: Phase 1 Information Gathering (greenfield and existing-project variants).
- **Dogfooding observations** — Patterns captured during real-project applications of the framework, which inform toolset revisions.

---

*AI-Centric Software Development Playbook — Skill v1.0 (2026-04-22)*
