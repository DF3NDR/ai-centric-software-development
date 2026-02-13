# The AI-Centric Software Development Playbook

## A Practitioner's Guide to Building Software in the Age of AI

**Series Format:** 8–10 standalone articles, cross-linked, each self-contained but building on a shared framework.

**Tone:** Calm, methodical, example-driven. Practitioner-to-practitioner. The intro/manifesto (written last) will be bolder and more visionary.

**Audience:**
- Primary: Senior engineers, architects, full-stack developers already working with AI tools
- Secondary (mid-level): Engineers building the skill set to work within AI-driven toolkits
- Intro article accessible to: CTOs, engineering managers, technical leadership

**Timeline Thesis:** 18–24 months before this approach is fully operational for teams on the leading edge.

**Core Philosophy:** This is not about replacing engineers. It is about multiplying the leverage of skilled practitioners by giving them orchestration tools — prompts, skills, instruction sets, MCP servers, custom AIs — that compress what large teams once did into small, highly capable units. The fundamentals of computer science, architecture, and design thinking remain essential. What changes is the *interface* through which that knowledge is applied.

**Core Methodology — Specification Driven Development (SDD):** At every phase, the team follows an iterative, specification-first workflow: (1) interview prompts gather needs and context, (2) a plan document is produced and broken into sections or epics, (3) each section is specified through a detailed Project Requirement Document (PRD), (4) the PRD drives a well-defined task list, and (5) implementation prompts produce results. This SDD cycle is the engine of the framework. Building blocks are organized into **tool sets** — curated combinations of prompts, skills, MCP servers, instructions, and resources assembled for specific purposes within the SDD cycle.

**Key Structural Principle:** The phases are not waterfall stages. They are concurrent streams of thinking with natural checkpoints. Core Principles are evaluated at *every* phase, not bolted on at the end.

---

## The Core Principles

These are the six guiding principles — the lens through which every decision is evaluated at every phase. They are not a checklist to complete at a single stage. They travel with you from information gathering through deployment and beyond. The first four define *what* you're optimizing for. The last two define *how you know* you're getting it right.

### Security
- Threat modeling
- Zero-trust design
- Continuous audit hooks
- Compliance preparation (SOC 2, HIPAA, etc.) — build for it early, not as a scramble at the end

### Maintainability
- Testing strategy
- Documentation (living, queryable, AI-parseable)
- Technical debt control
- Observability and debuggability

### Economics
- Cost forecasting (dev time, infrastructure, licensing, AI tool costs)
- Speed-to-market
- Resource scaling (team size, compute, services)

### Operations
- Scalability
- Reliability
- Interoperability
- Governance (ownership, review gates, decision authority)
- Post-deployment monitoring — designed early, not added later

### Scoring & Metrics

Every Core Principle needs measurable outcomes — not just human intuition that "it looks right." The toolkit must include ways to define, track, and evaluate metrics against benchmarks at each phase. Without scoring, the principles are aspirations. With scoring, they become enforceable.

- Define quantitative benchmarks wherever possible for each principle (performance targets, cost ceilings, coverage thresholds, uptime SLAs)
- AI generates scorecards at each phase checkpoint — humans review and approve, but the measurement itself is automated
- Scoring applies at every level: architecture decisions, code quality, test coverage, deployment readiness, operational health
- Simple example: unit test coverage percentage as a Maintainability metric
- Complex example: security posture scoring across all attack surfaces as a Security metric
- Track score trends over time — regression is as important to catch as initial failure
- Scoring criteria evolve with the project: early phases score design decisions, later phases score runtime behavior

### Correctness Verification

Scoring tells you *how well* something performs. Correctness verification tells you whether it is *right*. In an AI-driven workflow, this is critical: the AI produces enormous volumes of output (code, specs, configurations, documentation) and human review alone cannot scale to verify all of it. The toolkit must include verification mechanisms that go beyond human-centric review.

- **Formal Verification** — At each stage of development, AI can generate formal proofs or verification models that mathematically demonstrate correctness of critical components. This is a powerful example of where AI augments but does not replace the engineer: the AI builds the formal verification, but the engineer must verify that the verification itself is sound. The human confirms the proof is asking the right question, not just that it found an answer.
- **Automated Correctness Checks** — Static analysis, type checking, contract testing, property-based testing, invariant enforcement — layered verification that catches classes of errors without human review of every line
- **AI-vs-AI Verification** — Using separate AI processes to review, challenge, and validate the output of the primary AI. One AI generates; another AI audits. Neither is trusted blindly.
- **Specification Conformance** — Automated checks that generated code, APIs, and configurations actually conform to the specs and architecture documents produced in earlier phases
- **Regression and Drift Detection** — Continuous verification that the system still meets its correctness criteria as changes accumulate — not just at release gates but throughout development and post-deployment
- **The Engineer's Role** — Verification does not remove the engineer from the loop. It changes *what* the engineer reviews: instead of reading every line of code, the engineer validates verification strategies, reviews edge cases the verification surfaces, and confirms that the right things are being verified. The judgment moves up a level of abstraction.

> **Note:** These six principles and their subcategories are not fixed. They will be iterated on as the series develops. Additional subcategories or even new top-level principles may emerge as we work through each phase.

---

## The Toolkit: Building Blocks, Tool Sets, and Specification Driven Development

The Core Principles come first because they drive every decision about what we include in the toolkit. When we evaluate a prompt, a skill, an MCP integration, or any other building block, the question is always: *does this help us apply and enforce our Core Principles?* A tool that accelerates development but undermines Correctness Verification does not belong. A prompt that generates code without considering Security is incomplete. The principles are the filter.

At each phase, we are assembling and refining a toolkit. The specific tools will change over time — what matters is the *types* of resources and the *thinking* behind how they're assembled.

### The Foundation: Consolidated Knowledge Resources

The AI-Centric Toolkit does not replace the traditional toolkit — it extends it. Every team already has a body of accumulated knowledge: documents, articles, technical references, videos, books, internal wikis, architecture decision records, past postmortems, vendor documentation, and industry standards. This existing body of work is valuable. What changes is how it is used.

In the AI-centric workflow, these traditional resources are consolidated and made available for processing by AI. A book on distributed systems design becomes a reference the AI can draw from when evaluating architecture options. An internal postmortem becomes context the AI uses when generating threat models. A vendor's API documentation becomes input the AI uses when generating integration code. The team's collected knowledge — in all its forms — becomes part of the AI's working context.

This consolidation is itself a toolkit-building activity. It requires organizing, indexing, and in some cases converting resources into formats that AI can consume effectively. It is ongoing, not one-time. As new resources are added and old ones become outdated, the consolidated knowledge base evolves alongside the toolkit.

### Types of Building Blocks
- **Consolidated Knowledge Base** — The team's existing traditional resources (documents, articles, videos, books, internal wikis, standards, references) organized and made available for AI processing. This is the foundation that all other building blocks draw from.
- **Prompts** — Interview-style prompts that extract information from humans ("Ask me 10 questions to define the requirements for this module") and action-oriented prompts that achieve goals directly ("Generate the OpenAPI spec from this data model")
- **Skills** — Reusable instruction sets and context packages that give AI the right framing for specific tasks
- **Instruction Sets** — Detailed playbooks that guide AI through multi-step processes
- **MCP Servers** — Connections between AI and real tools (git, databases, CI/CD, testing frameworks, monitoring)
- **Custom / Domain-Specific AIs** — Purpose-built AI configurations tuned for specific roles or phases
- **[Other types TBD]** — The taxonomy of building blocks will evolve as the field matures

### Tool Sets

Building blocks are individual components. **Tool sets** are curated combinations of building blocks assembled for a specific purpose. A tool set brings together the prompts, skills, MCP servers, instructions, and resources needed for a particular kind of work within a particular phase.

For example, a "Requirements Specification" tool set might include: an interview prompt designed to elicit requirements, a skill that provides domain-specific context, an MCP connection to the project's existing documentation, an instruction set for structuring the output, and references from the consolidated knowledge base. The tool set is the unit of work — the practitioner selects the right tool set for the task at hand and follows its embedded workflow.

### Specification Driven Development (SDD)

SDD is the core methodology of the AI-Centric framework. It defines *how* tool sets are used at every phase through an iterative, specification-first cycle:

1. **Specify** — Use interview prompt(s) from a tool set designed for this purpose to gather needs, context, and constraints. The AI interviews the practitioner; the output is a structured specification of what is needed.
2. **Plan** — The specification is developed into a plan document, which may range from a brief design brief to a comprehensive project plan depending on the phase. The plan is broken into sections or epics (borrowing the Agile term).
3. **Detail** — Each section is taken through another interactive or interview prompt that produces a Project Requirement Document (PRD) with a well-defined layout specific to the phase and the type of work.
4. **Task** — The PRD is included as a resource for a task-generation prompt that breaks the requirements into a well-defined, actionable task list.
5. **Implement** — An implementation prompt (or set of prompts) produces the results — code, documentation, configurations, test suites, architectural artifacts, or whatever the phase requires.

This cycle is iterative. The output of implementation feeds back into specification for the next section, the next phase, or refinement of the current work. Each step in the cycle has its own tool set, and the tool sets themselves are refined over time based on what produces the best results.

SDD is what gives the framework its structure. Without it, the toolkit is a collection of parts. With it, the parts become a process.

> **Note:** This series is deliberately tool-agnostic. We describe *what* each building block does and *why* you need it — not which specific product to use. The tools will shift. The process and thinking endure.

---

## Series Outline

---

### Article 1: Core Principles — Your Compass for Every Decision

**Purpose:** Establish the framework that the entire series depends on. Before we touch any phase, readers need to understand the principles and how they function as concurrent evaluation criteria — not a sequential checklist. Critically, introduce Scoring & Metrics and Correctness Verification as the mechanisms that make principles *enforceable* rather than aspirational.

**Key Ideas:**
- Why these principles exist: they prevent AI (and humans) from optimizing for the wrong thing
- How they interact: a decision that scores well on Economics but poorly on Security isn't a good decision — it's a deferred crisis
- The scoring / trade-off model: how to weigh principles against each other for a given project
  - Are some principles non-negotiable (e.g., Security in a healthcare app)?
  - Who sets the weighting? The team, the project context, or both?
- How Core Principles travel with you across every phase — not a gate at one stage but a lens at all stages
- Subcategories and how to expand them for your project's needs
- The role of AI in *enforcing* principle-based thinking: prompts that force trade-off conversations, scorecards that AI fills in and humans review
- **Scoring & Metrics:** Every principle needs quantitative benchmarks. AI generates scorecards; humans validate. Simple example: unit test coverage as a Maintainability metric. Complex example: security posture scoring across attack surfaces.
- **Correctness Verification:** Scoring measures *how well*; correctness verification confirms *whether it's right*. Human review cannot scale to verify all AI output. The toolkit must include formal verification, automated correctness checks, AI-vs-AI validation, and specification conformance testing. The engineer's role shifts from reviewing every line to validating verification strategies — judgment moves up a level of abstraction.
- The formal verification example: AI builds the proof, but the engineer verifies the proof is asking the right question. This is the paradigm in miniature — AI does the volume work, the human does the judgment work.

**Expandable Sections:**
- Deep dive into each principle and its subcategories
- Example scorecards / decision matrices
- Correctness verification patterns for each principle
- Formal verification approaches and when they're worth the investment
- Sample prompts for principle-driven evaluation
- How compliance and governance weave through Security and Operations

---

### Article 2: Building Your Toolkit — Tool Sets, SDD, and the Building Blocks

**Purpose:** Before diving into phases, establish what the toolkit *is*, how it's assembled, and how it's used. Introduces three essential concepts: building blocks (the individual components), tool sets (curated combinations of building blocks for specific purposes), and Specification Driven Development (the iterative methodology that drives every phase). Critically, establish that the Core Principles from Article 1 drive what goes into the toolkit — every building block must serve the principles.

**Key Ideas:**
- **The Consolidated Knowledge Base:** The AI-Centric Toolkit is an addendum to — not a replacement for — the team's existing body of knowledge. Documents, articles, technical references, videos, books, internal wikis, architecture decision records, past postmortems, vendor documentation, and industry standards are consolidated and made available for AI processing. This traditional knowledge becomes the foundation the entire toolkit draws from.
- Core Principles as the filter: every building block is evaluated against the six principles before inclusion — does it help us apply and enforce what we care about?
- The taxonomy of building blocks (consolidated knowledge base, prompts, skills, instruction sets, MCP servers, custom AIs)
- Interview prompts vs. action prompts vs. evaluation prompts — different tools for different moments
- Skills as reusable context packages — what makes a good one
- MCP servers as the bridge between AI reasoning and real-world tooling
- **Tool Sets:** Building blocks are individual components; tool sets are curated combinations assembled for a specific purpose. A tool set brings together the prompts, skills, MCP servers, instructions, and resources needed for a particular kind of work. The practitioner selects the right tool set for the task and follows its embedded workflow.
- **Specification Driven Development (SDD):** The core methodology of the framework. At every phase, the team follows an iterative, specification-first cycle: (1) Specify — interview prompts gather needs and context, (2) Plan — output becomes a plan document broken into sections/epics, (3) Detail — each section is specified via a PRD prompt, (4) Task — the PRD drives a well-defined task list, (5) Implement — implementation prompts produce results. This cycle is iterative — output feeds back into specification for refinement. Each step has its own tool set.
- The living nature of the toolkit: it evolves as the project evolves, as the tools evolve, as the team learns
- Starting small: you don't need a complete toolkit on day one — you build it as you go through the phases

**Expandable Sections:**
- Consolidating traditional resources: formats, indexing, and making knowledge AI-parseable
- Starter prompt patterns (interview-style, action-oriented, evaluation-style)
- Tool set composition patterns — how to assemble effective tool sets
- The SDD cycle in detail — worked examples at different phases
- How to evaluate and select MCP integrations
- Organizing your toolkit for team access
- Version control and iteration on prompts/skills/tool sets

---

### Article 3: Phase 1 — Information Gathering

> **Note on SDD in Phase Articles:** Each phase article (Articles 3–9) follows the SDD methodology defined in Article 2. The SDD cycle — Specify, Plan, Detail, Task, Implement — is applied within each phase using phase-appropriate tool sets. The articles will demonstrate how the cycle works in the context of each phase, with the tool sets and building blocks that are most relevant.

**Purpose:** How to use AI to scan, summarize, triage, and synthesize the information landscape before any design decisions are made.

**Key Ideas:**
- Pull public repos, APIs, existing frameworks — let AI summarize fast
- Competitive scan: what stacks win, what breaks, what documentation is poor
- Feature triage: AI ranks must-haves versus nice-to-haves based on market data and user research
- Identify reusable components, open standards, common pitfalls
- **Core Principles applied here:**
  - Security: What are the known vulnerabilities in candidate technologies? What compliance requirements will apply?
  - Maintainability: How well-documented are the options? What's the community health?
  - Economics: What are the licensing costs? What's the talent pool for each stack?
  - Operations: What's the deployment story? How mature is the tooling?
- Output: A crisp, structured report — ready to feed into analysis and design phases

**Expandable Sections:**
- Sample prompts for information gathering
- How to structure the output report so it's AI-parseable for later phases
- Techniques for competitive analysis with AI
- How to validate AI-gathered information (trust but verify)

---

### Article 4: Phase 2 — Analysis & Stack Selection

**Purpose:** Transform gathered information into decisions. Business analysis, cost modeling, stack selection, initial threat modeling.

**Key Ideas:**
- Run business analysis with AI: user needs, market fit, problem validation
- Cost modeling: development time, infrastructure, licensing, ongoing maintenance
- Stack decision-making: how to evaluate languages, frameworks, infrastructure choices
  - Example considerations: Rust for safety, container-first (Docker/K8s/Wasm), etc.
- Initial threat modeling: data flows, attack surfaces, trust boundaries
- Set benchmarks: speed-to-market targets, runtime performance goals, cost ceilings
- **Core Principles applied here:**
  - How does each stack option score across all six Core Principles?
  - What trade-offs are we accepting and why?
  - Document the rationale — this becomes the decision record

**Expandable Sections:**
- AI-assisted cost modeling techniques
- Sample prompts for business analysis
- How to run AI-simulated "what if" scenarios for stack choices
- Decision record templates

---

### Article 5: Phase 3 — Design & Technical Analysis

**Purpose:** Take the analysis output and begin scoring, simulating, and locking in design direction. This is where Core Principles become explicit scorecards.

**Key Ideas:**
- Take the Phase 2 report, plug in the Core Principles — start scoring
- Architecture sketch: modular, API-first, container-ready
- Let AI simulate: "If we go with this stack, does security hold? Does speed hold? What breaks?"
- Build the scorecard: each decision gets evaluated against Maintainability, Operations, Economics, Security
- Identify monitoring and observability hooks *now* — where will you need visibility later?
- Compliance considerations: what needs to be in place, and how do early design choices affect that?
- Final lock: what language, what infrastructure, what patterns we actually commit to

**Expandable Sections:**
- Scorecard templates and examples
- AI simulation prompts for design validation
- How to document design decisions for future AI consumption
- Trade-off analysis patterns

---

### Article 6: Phase 4 — Architecture & Modular Design

**Purpose:** Detailed architecture. This is where the blueprint becomes concrete: modules, APIs, security boundaries, documentation strategy, governance model.

**Key Ideas:**
- Modular breakdown: microservices, clean layers, or hybrid — whatever fits
- API-first design: OpenAPI specs, auto-generated stubs, contract testing
- Security baked in from the architecture level: zero-trust, least privilege, encryption strategy
- Documentation starts here — inline comments, diagrams, decision records that AI can parse and query
- Governance: ownership per module, review gates, who approves what
- Pre-baking observability: where do monitoring hooks go? What interfaces does incident response need?
- Designing for extensibility: how do new modules plug in via APIs without rework?
- **Core Principles applied here:**
  - Every architectural decision is scored
  - Trade-offs are documented and justified
  - The architecture itself should make the principles *easier* to satisfy downstream

**Expandable Sections:**
- API-first design patterns and prompts
- Security architecture patterns (zero-trust, least privilege)
- Documentation strategy: living docs that AI can maintain
- Module ownership and governance models

---

### Article 7: Phase 5 — Implementation

**Purpose:** Building the thing. AI-assisted coding, continuous validation, and the feedback loop between writing code and evaluating it against the Core Principles.

**Key Ideas:**
- AI-assisted coding: generate from specs, iterate with AI, run tests live
- Continuous security checks: automated scans, fuzzing, vulnerability detection as you code
- Benchmark as you go — catch performance regressions early
- Version control with semantic commits — structured so AI can track, summarize, and reason about changes
- The feedback loop: code → test → score against principles → verify correctness → refine
- Building monitoring and observability interfaces during implementation, not after
- **Correctness Verification in practice:**
  - AI generates formal verification for critical components — the engineer validates the verification itself
  - Specification conformance: automated checks that code matches the architecture and API specs from earlier phases
  - AI-vs-AI review: a separate AI process audits generated code for logic errors, security gaps, and spec drift
  - Property-based testing and invariant enforcement layered alongside traditional unit tests
- **Core Principles applied here:**
  - Security: continuous scanning, dependency audits
  - Maintainability: test coverage scoring, documentation generation, code quality metrics
  - Economics: tracking actual vs. estimated effort, flagging scope creep
  - Operations: deployment readiness checks, infrastructure-as-code validation
  - Scoring: automated metrics at every commit — coverage, complexity, performance, security posture

**Expandable Sections:**
- Prompts for AI-assisted code generation and review
- Formal verification patterns: when to use them, how AI generates them, how engineers validate them
- AI-vs-AI review workflows
- Continuous integration patterns with AI in the loop
- How to structure commits and PRs for AI comprehension
- Code quality scoring approaches and automated metrics dashboards

---

### Article 8: Phase 6 — Testing & Audit

**Purpose:** Verification, validation, and compliance. Automated test generation, security audits, performance validation, documentation freeze.

**Key Ideas:**
- Automated test suites: unit, integration, AI-generated edge cases
- Security audits: penetration testing, compliance checks, vulnerability scanning
- Performance validation against the benchmarks set in Phase 2
- Documentation freeze: make it queryable, not just readable — AI should be able to answer questions about the system from the docs alone
- Compliance verification: are we ready for SOC 2, HIPAA, or whatever applies?
- **Correctness Verification at scale:**
  - Formal verification review: the engineer audits AI-generated proofs and verification models from Phase 5 — confirming they ask the right questions, not just that they pass
  - End-to-end specification conformance: does the deployed system actually match the architecture, API contracts, and design decisions from earlier phases?
  - AI-vs-AI audit: independent AI review of the entire codebase against the original specs, flagging drift and undocumented changes
- **Core Principles applied here:**
  - This is the phase where principles become *pass/fail* gates
  - Every principle gets a final score before deployment
  - Correctness is verified, not assumed
  - Gaps are identified, prioritized, and either fixed or documented as known risks

**Expandable Sections:**
- AI-generated test case patterns
- Security audit checklists and prompts
- Formal verification audit: how the engineer reviews AI-generated proofs
- Specification conformance testing approaches
- Performance testing strategies
- Documentation quality evaluation (can AI answer questions about the system?)
- Scoring gate templates: what must pass before deployment proceeds

---

### Article 9: Phase 7 — Deployment & Evolution

**Purpose:** Getting it live, keeping it alive, and evolving it. Monitoring, incident response, runbooks as AI orchestration scripts, and continuous improvement.

**Key Ideas:**
- Roll out containerized, observable from day one
- Monitor for drift: AI flags when reality diverges from design scorecards
- Easy extension: plug new modules via APIs without destabilizing existing ones
- Technical debt: pay it forward, not later — AI tracks and prioritizes
- Incident response playbooks and runbooks as AI orchestration scripts
  - Runbooks structured so AI can read and execute them
  - Runbooks structured *as prompts* so AI follows them better than humans could
  - The bridge between documentation and automation
- Post-deployment monitoring: the hooks and interfaces designed in Phase 4 and built in Phase 5 come alive here
- Continuous compliance: ongoing audit, not one-time certification
- **Core Principles applied here:**
  - Security: continuous monitoring, incident response readiness
  - Maintainability: documentation stays current, tests stay green, debt stays managed
  - Economics: actual costs vs. forecasts, optimization opportunities
  - Operations: uptime, scaling behavior, interoperability in production

**Expandable Sections:**
- Deployment checklists (reference: Sylvain Kerkour's Rust production checklist as a model)
- Runbook-to-orchestration-script patterns
- Monitoring and alerting strategies
- Evolution and refactoring with AI assistance
- Incident response playbook templates

---

### Article 10 (Written Last): The Manifesto — Small Teams, Big AI, New Paradigm

**Purpose:** The bold, visionary introduction to the series. Explains *why* this matters, *why now*, and *who this is for*. Frames the entire series.

**Tone:** Manifesto. Confident. Forward-looking.

**Key Ideas:**
- The premise: software will very soon be created by very small teams (3–5 people) who are capable across the entire process — from conception through deployment
- These people aren't replacing specialists; they're orchestrating AI tools that perform specialist-level work
- AI becomes the principal interface for every aspect: ideation, analysis, architecture, development, testing, deployment, monitoring
- The fundamentals of computer science remain essential — what changes is the interface
- The 18–24 month timeline: why this is feasible now, not science fiction
- The "why now" catalysts: LLM coding capability, MCP ecosystem, custom AI configurations, agent frameworks
- This isn't about juniors replacing seniors — it's about seniors gaining leverage they've never had, and juniors needing new skills (toolkit fluency) alongside traditional CS foundations
- The counterargument: "people will always want to code" — yes, and people still ride horses. Professional software delivery is about outcomes, not typing speed
- The toolkit-first approach: before you build software, build the toolkit that lets AI help you build software
- **Specification Driven Development (SDD):** the methodology that makes the toolkit operational — an iterative, specification-first cycle (Specify → Plan → Detail → Task → Implement) applied at every phase, powered by curated tool sets
- Tool sets as the organizational unit: building blocks combined for purpose, not scattered prompts used ad hoc

**Expandable Sections:**
- The economics of small teams vs. large teams
- What "capable in every aspect" actually means
- The skill set evolution: what engineers need to learn, what becomes less relevant
- SDD as the new development paradigm — how it compares to Agile, TDD, and other methodologies
- Industry signals that this is already happening

---

## Appendices (Future Expansion)

### Appendix A: Prompt Library Starter Kit
- Interview prompts (requirements gathering, stakeholder alignment)
- Action prompts (spec generation, code generation, test generation)
- Evaluation prompts (scorecard filling, trade-off analysis, code review)
- Meta prompts (toolkit evaluation, process improvement)

### Appendix B: Incident Response as AI Orchestration
- How traditional runbooks become AI-executable scripts
- Structuring playbooks for AI consumption
- The feedback loop: incidents improve the playbook, which improves AI response

### Appendix C: References & Resources
- Sylvain Kerkour: Deploying Rust to Production Checklist (https://kerkour.com/rust-production-checklist)
- [Additional references TBD as series develops]

---

## Working Notes

- Every part of this outline can be expanded upon and added to
- Core Principles are not fixed — iterate as we work through phases
- Tool-agnostic by design: describe *what* and *why*, not *which product*
- The Paladin project serves as a real-world testbed but is not the focus of the series
- Each article should be self-contained but reference the shared Core Principles framework
- The toolkit itself is built incrementally — you don't need everything on day one
