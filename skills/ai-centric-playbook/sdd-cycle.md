# The SDD Cycle — Reference

**Load this file when:** guiding a practitioner through an SDD step, writing or evaluating specifications / plans / PRDs / task lists, when the cycle mechanics are unclear, or when the practitioner asks "which step am I at?" / "what comes next?"

---

## The Cycle

```
Specify → Plan → Detail → Task → Implement
   ↑                                   │
   └───────────────────────────────────┘
              (iterative)
```

Five steps. Iterative, not linear. Applies at every phase of the Playbook. The tool sets that power each step change per phase; the methodology does not.

---

## Step 1: Specify

### Purpose

Gather needs, context, and constraints from the practitioner in a structured way. The output is a **specification** of what is needed — not what will be built, but what must be understood before building can begin.

### How It Works

- AI uses **interview-style prompts** to draw out:
  - Requirements (functional, non-functional)
  - Context (domain, constraints, ecosystem)
  - Edge cases the practitioner hasn't surfaced yet
  - Dependencies (on other work, on external systems, on decisions not yet made)
  - Acceptance criteria — what "done" looks like
- Practitioner answers; AI follows up on vague answers with specificity questions
- AI surfaces gaps proactively — Core Principle dimensions not addressed, stakeholders not considered, constraints unstated

### What Good Output Looks Like

A **structured specification** — not a transcript of raw answers. Organized by concern, with requirements separated from assumptions, with explicit acknowledgment of what is known / unknown / TBD.

### Common Pitfalls

- **Gathering without specifying** — sprawling unfocused output with no clear connection to downstream decisions
- **Stream-of-consciousness context dumps** accepted instead of structured interview
- **Multiple questions per turn** — overwhelms the practitioner; single-focus answers are higher quality
- **Failing to surface gaps** — silent omissions in Core Principle dimensions

### Phase Adaptation

| Phase | What Specify looks like |
|-------|-------------------------|
| 1 (Information Gathering) | Define what information is needed and why; research specification |
| 1 (Existing project) | Define what must be discovered about the current system; sharpen the improvement objective |
| 2 | Define evaluation criteria and decision scope for stack / plan |
| 3 | Define what design artifacts are needed (data models, API contracts, etc.) |
| 4 | Define module boundaries, contracts, extension points |
| 5 | Define what outputs are needed per task (code, tests, docs, config) |
| 6 | Define verification scope and acceptance gates |
| 7 | Define operational readiness criteria and evolution triggers |

---

## Step 2: Plan

### Purpose

Transform the specification into a **plan document** — broken into sections or epics — coherent chunks of work that can be specified in detail and implemented independently.

### How It Works

- Take the specification from Step 1
- Divide it into sections based on:
  - Natural boundaries (separate concerns, independent workstreams)
  - Sequencing dependencies (what must come before what)
  - Principle concentration (sections where specific principles dominate)
- Produce a plan listing the sections with brief descriptions

### What Good Output Looks Like

A plan with:
- Clear section boundaries (each section is independently specifiable)
- Explicit dependencies between sections (A must complete before B begins)
- Approximate effort indication (rough, not precise)
- No implementation detail yet — plan is about *what needs to be specified in detail*, not *how to build it*

### Common Pitfalls

- **Collapsing Specify and Plan** — treating them as one step produces plans that miss requirements
- **Over-granular sections** — sections so small each one needs its own plan; collapse them
- **Under-granular sections** — monolithic sections that can't be detailed independently; split them
- **Linear sequencing everywhere** — most sections can be specified in parallel; don't serialize unnecessarily

### Phase Adaptation

Plan's role shifts across phases:

- Phase 1: sections = domains of inquiry (tech landscape, compliance, risk, etc.)
- Phase 2: sections = decisions to make (stack selection, sequencing, scope)
- Phase 4: sections = modules to design
- Phase 5: sections = implementation workstreams

The plan is always a bridge between broad specification and detailed requirements.

---

## Step 3: Detail

### Purpose

Each section from the plan becomes a **Project Requirement Document (PRD)** with a well-defined layout. The PRD embeds the six Core Principles as **concrete requirements** — not aspirational goals.

### How It Works

For each section in the plan, produce a PRD that specifies:
- **What the section must deliver** (functional requirements)
- **Security constraints** — specific, verifiable (not "the system shall be secure")
- **Maintainability expectations** — test coverage targets, doc requirements, specific quality bars
- **Economic constraints** — budget (time, cost, effort), scaling targets, cost ceilings
- **Operational requirements** — deployment approach, observability, SLO targets
- **Scoring criteria** — how success will be measured; baseline + target
- **Verification methods** — how correctness will be checked

### What Good Output Looks Like

A PRD that:
- A different practitioner or AI could implement against without ambiguity
- Has principle requirements as **concrete rows**, not as prose
- Distinguishes must-have from should-have from nice-to-have
- Names acceptance criteria explicitly

### Common Pitfalls

- **Aspirational principle statements** — "Security is important" is not a requirement; "Authentication uses OAuth 2.1 with PKCE; authorization uses RBAC with policy-as-code" is
- **Missing verification methods** — requirements that cannot be checked are decoration
- **PRDs that skip principles** — a PRD silent on Operations is incomplete
- **PRDs treated as final** — a PRD is living; it updates when Detail surfaces new understanding

### Phase Adaptation

- Phase 1: Discovery Requirements Documents — what to investigate per section
- Phase 3: Design PRDs — data models, API contracts, architectural decisions
- Phase 4: Module PRDs — boundaries, contracts, extension points, test strategy per module
- Phase 5: Implementation PRDs — specific code artifacts and their requirements

The PRD is the specification in its most actionable form. Downstream steps implement against it; Phase 6 verifies against it.

---

## Step 4: Task

### Purpose

The PRD drives a **well-defined, actionable task list**. Tasks are the unit of work an AI or practitioner can act on.

### How It Works

For each requirement in the PRD, produce one or more tasks with:
- **Clear description** — what needs to be done, unambiguously
- **Acceptance criteria** — how to know it's done
- **Dependencies** — on other tasks, external inputs, decisions
- **Estimated complexity** — rough (S/M/L), not precise hours
- **Which Core Principles** the task must satisfy
- **Verification criteria** — how correctness will be checked

### What Good Output Looks Like

A task list that:
- Maps clearly back to PRD requirements (traceability)
- Has no ambiguous tasks — every task states what "done" means
- Surfaces dependencies explicitly — sequencing is visible
- Includes verification tasks alongside implementation tasks
- Respects the principle that evaluation is part of implementation (not a separate later phase)

### Common Pitfalls

- **Tasks without acceptance criteria** — "implement the auth module" has no done-state
- **Orphan tasks** — tasks not traceable to a PRD requirement
- **Missing verification tasks** — implementation tasks without paired verification tasks
- **Over-decomposition** — tasks so small they add sequencing overhead without value
- **Under-decomposition** — tasks so large they can't be evaluated or handed to a fresh session

### Task Template

```
Task ID: T-NN
Description: [what is being done]
Source: PRD section [X] requirement [Y]
Acceptance criteria:
  - [specific verifiable outcome 1]
  - [specific verifiable outcome 2]
Dependencies: [T-NN, T-MM, external decision X]
Complexity: S/M/L
Principles to satisfy: [list]
Verification method: [how done is checked]
```

---

## Step 5: Implement

### Purpose

Produce results: code, documentation, configurations, test suites, architectural artifacts, deployment scripts, or whatever the phase requires. Output is **evaluated against the PRD and task list**. Scoring & Metrics are applied. Correctness Verification runs. If output doesn't meet the specification, **iterate**.

### How It Works

For each task:
1. AI produces the output (code, doc, artifact) using an **action prompt** combined with the relevant skills and standards
2. Output is evaluated against the task's acceptance criteria
3. **Evaluation prompts** score the output against relevant Core Principles
4. **Verification** runs — tests, formal checks, AI-vs-AI audits as appropriate
5. Gaps identified: either iterate (refine the output) or cycle back (refine the specification if the gap is a spec problem, not an output problem)

### What Good Output Looks Like

Outputs that:
- Pass the task's acceptance criteria cleanly
- Score acceptably on the relevant Core Principles
- Are reviewed and approved by the practitioner — AI never self-accepts
- Are documented (sources, dates, confidence levels where applicable)
- Have trade-offs named if they exist

### Common Pitfalls

- **AI self-accepting output** — AI produces, AI evaluates, no human review; quality drifts silently
- **Skipping evaluation for speed** — implementation without evaluation accumulates debt
- **Iteration without root-cause analysis** — revising output when the spec was wrong; fix the spec, not the output
- **Missing verification** — "it compiles" is not verification
- **Ignoring CONDITIONAL gates** — self-evaluation flagged an issue; it was dismissed; problem surfaces later

---

## The Iterative Nature

SDD is **not a one-way pipeline**. Common cycle-back patterns:

| Trigger | Cycle back to |
|---------|--------------|
| Implement reveals ambiguous task | Task (refine acceptance criteria) |
| Implement reveals missing requirement | Detail (amend PRD) |
| Detail reveals missing section | Plan (add section) |
| Plan reveals missing context | Specify (amend specification) |
| Specify reveals unknown domain constraint | Re-enter Specify with new question set |

The key behavior: **cycle back explicitly, not silently**. When you return to an earlier step, document why and what changed. This preserves traceability.

---

## Phase-by-Phase SDD Adaptation

| Phase | Specify asks | Plan produces | Detail produces | Task produces | Implement produces |
|-------|-------------|--------------|-----------------|---------------|-------------------|
| 1 | What info is needed? | Research plan | Discovery Requirements Doc | Research task list | Information Report |
| 2 | What decisions must be made? | Decision framework | Decision PRDs | Evaluation tasks | Decision document + Improvement Plan |
| 3 | What design is needed? | Design plan | Design PRDs | Design tasks | Data models, APIs, blueprints |
| 4 | What modules exist? | Module plan | Module PRDs | Module-design tasks | Module specifications |
| 5 | What must be built? | Build plan | Implementation PRDs | Build tasks | Code, docs, configs, tests |
| 6 | What verifies correctness? | Verification plan | Verification PRDs | Verification tasks | Scored conformance report |
| 7 | What evolves, what's watched? | Operations plan | Runbook PRDs | Operational tasks | Live system + feedback loops |

The vocabulary changes; the methodology doesn't.

---

## Core Behaviors When Operating in the SDD Cycle

1. **Identify where the practitioner is.** Before helping, know which step they're at. If unclear, ask.
2. **Do not skip steps.** A practitioner asking for code (Step 5) without a PRD (Step 3) needs help creating the PRD first.
3. **Make cycle-backs explicit.** When reverting to an earlier step, document what changed and why.
4. **Treat specifications as living documents.** They evolve as understanding deepens.
5. **Apply all six Core Principles at every step**, not just at Phase 6 verification.

---

## Pattern: Starting Fresh in a New Phase

When entering a new phase, the SDD cycle restarts:

```
New phase begins
  ↓
Specify (new interview-style prompt, new question set, new specification)
  ↓
Plan (new plan for this phase's work)
  ↓
Detail (new PRDs specific to this phase)
  ↓
Task (new task list)
  ↓
Implement (this phase's specific outputs)
  ↓
Evaluate against prior phase's handoff criteria + this phase's Core Principle scoring
  ↓
Phase gate: pass / conditional / fail / cycle back
```

The cycle's consistency is what makes the framework learnable. Once a practitioner runs the cycle once at Phase 1, they know how Phase 2 through 7 will feel.

---

## Cross-References

- **Core Principles embedded at each step:** see `core-principles.md` — principles enter at Specify (interview filter), persist through Detail (PRD requirements), shape Task (acceptance criteria), dominate Implement (output evaluation)
- **Tool sets that power each step:** see `building-blocks-and-toolsets.md` — interview prompts (Specify), planning prompts (Plan), PRD templates + action prompts (Detail, Task), action + evaluation prompts (Implement)

---

*AI-Centric Software Development Playbook — sdd-cycle reference, part of the ai-centric-playbook skill v1.0 (2026-04-22)*
