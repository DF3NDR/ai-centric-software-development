# Building Blocks and Tool Sets — Reference

**Load this file when:** building, evaluating, or revising prompts / skills / instruction sets / MCP servers / tool sets; when the practitioner asks how to compose a tool set for a specific purpose; when reviewing tool set quality against Core Principles.

---

## The Six Building Block Types

| # | Block | Granularity | Role |
|---|-------|-------------|------|
| 1 | Consolidated Knowledge Base | Foundation | Team's body of reference material, made AI-parseable |
| 2 | Prompts | Most granular | The direct interface between practitioner and AI |
| 3 | Skills | Medium | Reusable context packages activated on demand |
| 4 | Instruction Sets | Medium-large | Multi-step playbooks with decision points |
| 5 | MCP Servers | Infrastructure | Bridges between AI reasoning and real tooling |
| 6 | Custom AIs | Large / durable | Purpose-built AI configurations for specific roles |

Each building block operates at a different level of abstraction and applies at different points in development.

---

## 1. Consolidated Knowledge Base

### What It Is

The team's existing body of knowledge (documents, articles, technical references, videos, books, wikis, ADRs, postmortems, vendor docs) consolidated and made available for AI processing. **The foundation all other building blocks draw from.**

### Key Properties

- Text-based formats preferred (markdown, plain text, structured docs)
- PDFs with selectable text work; scanned documents and video-only content require processing (transcription, summarization, extraction)
- **Living** — added to, revised, pruned; not one-time construction
- Prioritized — start with resources most relevant to current project and phase; expand coverage over time

### When to Use

Always. Every other building block is more effective when it has access to a well-consolidated knowledge base.

### Common Failure Modes

- **"Dump everything" approach** — consolidating without curating produces a knowledge base where relevant content is buried
- **Stale without curation** — outdated content mixed with current creates worse-than-nothing confusion
- **Format-blind consolidation** — scanned PDFs, video-only content, proprietary formats that AI can't parse

---

## 2. Prompts

The most granular building block. Three types, each with a distinct role.

### Type 2a: Interview Prompts

**Purpose:** Extract information from humans through structured questioning.

**Used in:** SDD Specify and Detail steps.

**Properties:**
- Ask one question at a time
- Follow up on vague answers with specificity
- Map every question to at least one Core Principle
- Surface gaps proactively
- Structure output for downstream AI consumption

**Example kickoffs:**
- "I need to produce a [artifact] for my [project type]. Please interview me one question at a time..."
- "Ask me the questions you need to [understand / specify / plan] [X]."

### Type 2b: Action Prompts

**Purpose:** Direct AI to produce specific outputs.

**Used in:** SDD Implement step.

**Properties:**
- Clear specification of the output format
- Evaluation criteria embedded (what done looks like)
- References to relevant skills, standards, PRDs
- Produce-then-self-check pattern where verification is cheap

**Example patterns:**
- "Generate the [artifact] from this [specification]."
- "Produce [output] conforming to [spec], referencing [skill / standard]."

### Type 2c: Evaluation Prompts

**Purpose:** Score or assess outputs against criteria.

**Used throughout:** as quality gates, especially at phase boundaries.

**Properties:**
- Explicit scoring rubric with per-criterion rationale
- PASS / CONDITIONAL / FAIL levels (with CONDITIONAL preferred over PASS-with-caveats)
- Reference to the specification the output is being evaluated against
- Structured output (scores + rationale + recommendations)

### Prompt-Quality Checklist

A well-designed prompt:

- [ ] States the type explicitly (interview / action / evaluation)
- [ ] Names its SDD step
- [ ] Names the phase it belongs to
- [ ] Filters through the six Core Principles
- [ ] Has a clear kickoff line and expected output format
- [ ] Includes behavioral rules the AI must follow
- [ ] Has an evaluation checklist for accepting the output
- [ ] Is version-controlled
- [ ] References the skills, instruction sets, or resources it depends on
- [ ] Degrades gracefully when optional connectors are missing

---

## 3. Skills

### What They Are

Reusable context packages. Encapsulate domain knowledge, standards, patterns, or expertise that can be attached to any prompt — **activated on demand**, not loaded into every conversation.

### Key Properties

- **Modular** — a skill addresses one domain; multiple skills combine
- **Version-controlled** — skills evolve; changes tracked
- **Focused** — a bloated skill that covers everything is harder to maintain than three focused skills
- **Load-on-demand** — the AI invokes when the conversation requires; doesn't consume context otherwise
- **Described for triggering** — skill metadata (name, description) must be specific enough that the AI knows when to invoke

### When to Use

- Cross-cutting expertise the AI needs across many prompts (coding standards, industry conventions, framework idioms)
- Reusable reference material (this skill itself — Playbook framework reference)
- Domain-specific knowledge (medical terminology, financial instruments, ERC standards, etc.)
- Tool-specific patterns (Kubernetes idioms, PostgreSQL best practices)

### When NOT to Use

- One-off knowledge applicable to a single prompt (inline it in the prompt)
- Phase-specific tool set content (belongs in the phase tool set directory)
- Information that changes per session (pass as context, not as skill)

### Skill Structure (Anthropic Agent Skills Pattern)

```
my-skill/
├── SKILL.md                    ← entry point with YAML frontmatter (name, description)
├── [reference-file-1].md       ← domain depth, load on demand
├── [reference-file-2].md       ← specific topic depth
└── [resources/]                ← optional: code templates, data files
```

The SKILL.md frontmatter contains:
- `name` — kebab-case identifier
- `description` — specific triggering criteria (when to invoke)

The reference files are loaded on demand, not preemptively.

### Skill Quality Checklist

- [ ] Description names specific triggers (when to invoke)
- [ ] Description names anti-triggers (when NOT to invoke) if ambiguous
- [ ] Reference files are independently loadable
- [ ] Cross-references between files are explicit
- [ ] Skill avoids scope creep into phase-specific or project-specific content
- [ ] Skill has a version history
- [ ] Skill declines gracefully when a reference file isn't needed (don't force load)

---

## 4. Instruction Sets

### What They Are

Multi-step playbooks for complex workflows. Define **sequences of operations with decision points, quality gates, and conditional paths**.

### Key Properties

- Longer and more structured than prompts
- Include branching (if X, then Y; else Z)
- Named phases or stages within the workflow
- Quality gates at stage boundaries
- Usually loaded at session or project level (like `.github/copilot-instructions.md` or `CLAUDE.md`)

### When to Use

- Multi-step workflows that recur (release process, incident response, code review)
- Sessions that need consistent behavioral context (project instructions)
- Workflows with decision points that depend on intermediate outputs

### When NOT to Use

- Single-step operations (use a prompt)
- Context-setting without workflow (use a skill)

### Instruction Set vs. Skill — the Boundary

| | Skill | Instruction Set |
|---|-------|-----------------|
| Role | Reference knowledge, activated on demand | Workflow playbook, loaded session-wide |
| Lookup pattern | AI decides when to invoke | Always in effect during session |
| Structure | Reference files loaded by need | Sequential steps + decision branches |
| Example | "Playbook framework reference" | "Phase 1 instructions file" |

The Phase 1 `step-00-information-gathering.existing-project.instructions.md` file is an instruction set — it's loaded at session start and governs behavior throughout. This skill you're reading now is a skill — it's invoked when the conversation needs framework-level reasoning.

---

## 5. MCP Servers

### What They Are

Bridges between AI reasoning and real-world tooling. Version control, CI/CD, monitoring, databases, issue trackers, etc.

### When They're the Right Tool

- Dynamic state the AI needs to query or modify (not static content)
- External systems that expose APIs (GitHub, Linear, Postgres, Slack)
- Capabilities the AI needs *live* access to (current repo state, current issue list, current build status)

### When They're NOT the Right Tool

- Static reference content (use skills, project knowledge, or knowledge base)
- One-off lookups (use search or web fetch)
- Content that rarely changes (copy it into project knowledge)

### Graceful Degradation Principle

Tool sets should work without any specific MCP connector. Where a connector is missing, the tool set degrades into copy-paste requests to the practitioner — slower, not broken. An MCP server should be **strongly encouraged but not strictly required**.

---

## 6. Custom AIs

### What They Are

Purpose-built AI configurations — specific system prompts, skills, tool access, sometimes model tuning — tailored for particular roles or tasks.

### When to Use

- Long-running specialized roles (a "code reviewer AI," a "threat modeler AI")
- Configurations that benefit multiple practitioners on the same team
- Workflows where consistency of AI behavior across sessions is valuable

### When NOT to Use

- One-off tasks (use a prompt)
- Rapidly changing requirements (custom AIs are slower to iterate than prompts)

---

## Tool Sets — Combinations for a Specific Purpose

A **tool set** is a curated combination of building blocks assembled for a specific purpose within a specific phase.

### Tool Set Pattern

Every well-formed tool set includes:

1. **An instructions file** (instruction set) — session-wide context and guardrails
2. **Interview or action prompts** — the operations the tool set performs
3. **Skills** relevant to the domain or task type
4. **MCP connectors** where live state matters (strongly encouraged, not required)
5. **Evaluation prompts** — quality gates and self-checks
6. **Output templates** — structured artifact formats for downstream consumption
7. **Resources** — reference materials, examples, standards

### Example: Requirements Specification Tool Set (Phase 1)

```
Components:
  - Instructions file (sets framework context, behavioral rules)
  - Interview prompt (gathers requirements conversationally)
  - Domain skill (e.g., this Playbook skill, or a domain-specific skill)
  - MCP connector to existing docs (strongly encouraged)
  - Output template (structured Requirements Sketch format)
  - Evaluation prompt (checks completeness against all six Core Principles)
```

### Example: Architecture Review Tool Set (Phase 4)

```
Components:
  - Instructions file (Phase 4 context, reviewer posture)
  - Reviewer skill (architectural evaluation patterns)
  - Evaluation prompt (scores design against all six Core Principles)
  - MCP connector to codebase
  - Architecture decision records as project knowledge
  - Action prompt (generates review document)
```

### Example: Implementation Tool Set (Phase 5)

```
Components:
  - Instructions file (Phase 5 context, coding posture)
  - PRD + task list (inputs, from Phase 4 handoff)
  - Coding standards skill
  - Action prompt (code generation)
  - MCP to testing framework, VCS
  - Evaluation prompt (tests + principle scorecard)
  - Correctness verification instruction set (contract tests, property tests, AI-vs-AI audit)
```

### Tool Set Design Principles

1. **Every tool set must address all six Core Principles** or explicitly flag which are out of scope and why.
2. **Every tool set must include evaluation and verification components**, not just action components.
3. **Design for reusability across similar tasks**, not one-off use.
4. **Version-control all tool set configurations.**
5. **Tool set must have a README** that explains the recommended sequence, prerequisites, and graceful degradation for missing capabilities.
6. **Tool sets are living** — revise based on dogfooding observations, version explicitly.

### Tool Set Quality Checklist

- [ ] Instructions file is present and loaded as session context
- [ ] Every prompt in the tool set references Core Principles
- [ ] Every prompt has metadata (type, phase, SDD step, principles addressed, feeds-into)
- [ ] Every prompt has a kickoff line and an output format
- [ ] Every prompt has an evaluation checklist
- [ ] Skills relevant to the domain are identified
- [ ] MCP connectors are identified; graceful-degradation posture documented
- [ ] A recommended sequence is documented
- [ ] Dogfooding observations are captured and inform revision
- [ ] Version history is maintained

---

## Pattern: Building a New Tool Set

Follow the SDD cycle — even for the tool set itself.

### Step 1: Specify — what the tool set must do

- What phase does it belong to?
- What output does it produce?
- What practitioner workflow does it serve?
- What inputs does it consume (prior phase outputs, project knowledge)?
- Which Core Principles does it emphasize?

### Step 2: Plan — what building blocks are needed

- Instructions file (yes, almost always)
- Which prompt types (interview / action / evaluation)?
- Which skills apply?
- Which MCP connectors are helpful (but not required)?
- What resources (examples, templates, standards)?

### Step 3: Detail — PRD for each component

- For each prompt: metadata, system instructions, kickoff, question bank or output format, evaluation checklist
- For the instructions file: framework orientation, behavioral rules, Core Principles application, output standards
- For the README: recommended sequence, prerequisites, degradation posture

### Step 4: Task — build the components

- Author each prompt
- Author the instructions file
- Author the README
- Set up skills and MCP connector references

### Step 5: Implement — build and dogfood

- Run the tool set against a real project
- Capture observations during the run
- Review observations end-of-phase
- Revise into the next version (v1.1, v1.2, etc.)
- Version-control and document the changes in Version History

---

## Pattern: Evaluating an Existing Tool Set

When auditing a tool set for quality, apply in order:

### 1. Coverage Audit

- Does every prompt cover all six Core Principles, or explicitly exclude one?
- Are evaluation / verification prompts present, not just action prompts?
- Is there a phase-gate scorecard at the tool set's terminal step?

### 2. Traceability Audit

- Does each prompt's output feed cleanly into the next prompt's input?
- Are handoffs to downstream phases explicit?
- Is there a gap register for things not captured?

### 3. Degradation Audit

- Does the tool set work without optional MCP connectors?
- Is the degradation posture documented?
- Does the practitioner know what to do when a capability is missing?

### 4. Versioning Audit

- Is every file version-stamped?
- Is the Version History table maintained?
- Are dogfooding observations captured and consulted?

### 5. Readability Audit

- Can a fresh practitioner pick up the tool set and use it without author support?
- Is the README a navigation aid or a wall of text?
- Are the prompts self-contained (kickoff line works without context beyond the instructions file)?

---

## The Toolkit Is Not a Product — It Is a Practice

The Playbook's framing: **the toolkit is a practice to build, not a product to purchase**. Every team's toolkit is different. Components are added when needed, captured when they work, retired when they stop working. The purpose of understanding building blocks and tool set patterns is not to build The Perfect Toolkit but to build **your team's current toolkit**, knowing it will evolve.

- Start with what's needed now
- Capture what works
- Retire what doesn't
- Version-control and dogfood everything

---

## Cross-References

- **When building blocks serve specific principles:** see `core-principles.md` — every building block inclusion decision passes through the Core Principles filter
- **When building blocks fit into the SDD cycle:** see `sdd-cycle.md` — prompts, skills, and instruction sets map to specific SDD steps

---

*AI-Centric Software Development Playbook — building-blocks-and-toolsets reference, part of the ai-centric-playbook skill v1.0 (2026-04-22)*
