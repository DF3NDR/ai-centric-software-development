# Phase 2 — Analysis & Stack Selection

*Part 4 of The AI-Centric Software Development Playbook*

---

## From Information to Decisions

Phase 1 produced an Information Report — a structured synthesis of the technology landscape, competitive analysis, compliance requirements, risks, reusable components, and open questions. That report presents evidence. It does not make decisions.

Phase 2 is where evidence becomes commitment. The team takes the Information Report and runs it through a disciplined analytical process to answer the questions that every subsequent phase depends on: What is the business case? What will it cost? What technology stack do we commit to? What threats must we design against? What benchmarks define success?

These are consequential decisions. A stack chosen poorly in Phase 2 creates compounding costs through every later phase — rework in architecture, friction in implementation, pain in operations. A threat model that misses a critical attack surface in Phase 2 becomes a security incident in production. A cost model that underestimates infrastructure at scale becomes a budget crisis at growth.

The role of AI in Phase 2 is not to make these decisions. It is to make them *informed* — to model the costs, simulate the trade-offs, score the options against the Core Principles, and surface the consequences of each choice so that the practitioner can commit with clear-eyed understanding of what is being gained and what is being traded away.

---

## What Analysis & Stack Selection Accomplishes

Phase 2 produces four primary artifacts, each feeding into Phase 3 (Design & Technical Analysis) and beyond.

**A Business Analysis** — Validation that the project solves a real problem for real users within real constraints. User needs, market fit, problem validation, and a clear articulation of the value the system is expected to deliver. This grounds every technical decision in business reality.

**A Cost Model** — A structured forecast of total lifecycle costs: development time, infrastructure, licensing, AI tooling, ongoing maintenance, team scaling, and operational overhead. Not a single number but a model — one that can be adjusted as assumptions change and validated against actuals as the project progresses.

**A Stack Decision with Rationale** — The committed technology choices: languages, frameworks, runtime environments, deployment platforms, data stores, and key third-party services. Each choice is documented with the rationale behind it, the alternatives considered, the trade-offs accepted, and the Core Principle scores that supported the decision. This becomes the project's foundational decision record.

**An Initial Threat Model** — The first structured analysis of what can go wrong: data flows, trust boundaries, attack surfaces, and the threat actors relevant to the domain. Not a complete security architecture (that comes in Phase 4) but the analytical foundation that architecture decisions will build on.

Additionally, Phase 2 establishes the **benchmark framework** — the quantitative targets against which the system will be measured throughout development and into production. Speed-to-market targets, runtime performance goals, cost ceilings, reliability targets, and security posture thresholds.

---

## The SDD Cycle in Phase 2

The SDD cycle runs again, but now the Specify step draws from the Information Report rather than from scratch. The practitioner is not starting with a blank page — they are starting with structured evidence and applying analytical tool sets to transform it into decisions.

### Step 1: Specify — What Decisions Need to Be Made?

The first step is to specify the decisions this phase must produce. This sounds redundant — "we need to pick a stack" — but the Specify step forces the team to articulate the full scope of decisions and their dependencies.

An interview prompt from the Analysis tool set structures this:

- What are the primary user personas and their core workflows?
- What is the business model? How does the system generate or protect value?
- What are the non-negotiable constraints (regulatory, budgetary, timeline, team size)?
- What decisions from Phase 1 are already effectively made (e.g., "we must integrate with existing System X")?
- What are the highest-risk unknowns that analysis must resolve?
- What benchmarks will define success? Who defines "good enough" for performance, security, cost?

The output is an **analysis specification** — a document that defines the scope and priorities of the analytical effort, preventing the team from spending two weeks modeling costs for a stack option that was already eliminated by a compliance constraint identified in the first hour.

### Step 2: Plan — Structure the Analysis

The analysis specification is broken into sections, each representing a coherent analytical domain:

- **Business analysis** — User needs validation, market fit, value proposition clarity
- **Cost modeling** — Development costs, infrastructure at target scale, licensing, AI tooling, maintenance
- **Technology evaluation** — Structured comparison of candidate stacks against Core Principles
- **Threat modeling** — Data flows, trust boundaries, attack surfaces, threat actors
- **Benchmark definition** — Quantitative targets for performance, security, cost, reliability

Each section will be detailed into specific analytical tasks. The practitioner reviews the plan for completeness and adjusts priorities based on which decisions carry the most risk.

### Step 3: Detail — Define Analytical Frameworks

Each section from the plan is taken through a detail prompt that produces a structured analytical framework — the PRD equivalent for analysis work.

For example, the Technology Evaluation section might be detailed into:

**Evaluation criteria matrix** — For each candidate stack option, define the specific criteria that will be scored. These criteria map directly to the six Core Principles:

- Security: vulnerability history, security tooling maturity, memory safety characteristics, encryption support, audit logging capabilities
- Maintainability: documentation quality, testing ecosystem, refactoring tooling, community health, talent availability
- Economics: licensing cost, infrastructure cost at scale, development velocity, AI tooling compatibility, team ramp-up time
- Operations: deployment complexity, scaling characteristics, monitoring integration, container support, interoperability
- Scoring & Metrics: benchmarking tooling, performance profiling, automated quality metrics, CI/CD integration
- Correctness Verification: type system strength, formal verification support, property-based testing, static analysis depth

The detail step produces the evaluation framework *before* the evaluation is conducted. This prevents the common failure of choosing criteria after seeing results — a form of confirmation bias that AI-assisted analysis can inadvertently amplify.

### Step 4: Task — Assign Specific Analyses

The analytical frameworks from Step 3 are broken into concrete tasks:

- Score each candidate language (e.g., Rust, Go, TypeScript) against the Security evaluation criteria using data from the Information Report. Produce a structured scorecard with 1–5 ratings and justification for each criterion.
- Model infrastructure costs for each candidate deployment platform (e.g., Kubernetes, Docker Compose, serverless) at three scale points: MVP (100 users), growth (10,000 users), and target (100,000 users). Include compute, storage, networking, and managed service costs.
- Generate a preliminary data flow diagram for the system's primary user workflows. Identify trust boundaries, data classification (public, internal, confidential, restricted), and external integration points.
- Map compliance requirements from the Information Report to specific technical constraints. For each requirement, identify which stack options satisfy it natively, which require additional tooling, and which are incompatible.
- Define benchmark targets for: API response latency (p50, p95, p99), throughput under load, cold start time, build and deployment time, test suite execution time, and memory consumption at steady state.

Each task produces a structured output that feeds into the phase artifacts.

### Step 5: Implement — Execute the Analysis

The Analysis tool sets go to work. This is where AI's analytical capabilities provide the most leverage:

**Business analysis** — AI synthesizes user research, market data, and competitive findings from the Information Report into a structured business case. It can model user workflows, identify feature priorities using the MoSCoW method or similar frameworks, and validate that the proposed system addresses identified needs. The practitioner validates against domain knowledge and stakeholder input.

**Cost modeling** — AI excels at structured cost estimation when given the right inputs. Cloud provider pricing calculators, licensing terms, development velocity benchmarks from similar projects, and infrastructure scaling curves can be modeled and compared across stack options. The output is not a single estimate but a model with assumptions that can be adjusted.

**Technology scoring** — AI evaluates each candidate stack against the evaluation criteria matrix, producing scorecards with structured ratings and justification. This is one of the most effective applications of evaluation prompts — the AI considers multiple dimensions simultaneously and can identify trade-off tensions that humans might miss when evaluating one criterion at a time.

**Threat modeling** — AI generates initial threat models from the data flow diagrams, applying frameworks like STRIDE (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege) to each component and trust boundary. The practitioner reviews for completeness, adds domain-specific threats, and validates that the model captures real-world attack patterns.

**Benchmark definition** — AI proposes benchmark targets based on industry standards, competitive benchmarks from the Information Report, and the specific performance requirements identified in the analysis specification. The practitioner adjusts based on business priorities and realistic expectations.

---

## The Stack Decision

The stack decision is the most consequential output of Phase 2. It commits the team to a technology foundation that will be expensive to change and will influence every subsequent phase. It deserves a structured decision process.

### Structured Scoring

Each candidate stack is scored against the six Core Principles using the evaluation criteria defined in the Detail step. The scores are not intuitive impressions — they are structured assessments backed by evidence from the Information Report and the analysis conducted in this phase.

A stack scorecard might look like:

For each candidate (e.g., Rust + Axum + PostgreSQL vs. Go + Echo + PostgreSQL vs. TypeScript + Nest.js + PostgreSQL), score:

- Security: 1–5 with justification citing specific evidence
- Maintainability: 1–5 with justification
- Economics: 1–5 with justification
- Operations: 1–5 with justification
- Scoring & Metrics: 1–5 with justification
- Correctness Verification: 1–5 with justification
- **Weighted total** based on the project's principle weighting (established during this phase)

The weighting is critical. A healthcare application might weight Security at 2x and Correctness Verification at 1.5x, while weighting Economics at 0.75x. A proof-of-concept for market validation might weight Economics and Operations highest. The weighting reflects the project's specific priorities, and it should be established *before* scoring — not adjusted after seeing which stack wins.

### Trade-Off Documentation

No stack will score highest on every principle. The stack decision is inherently a trade-off decision, and those trade-offs must be documented explicitly.

For each significant trade-off, the decision record should capture:

- What is being traded (e.g., "accepting higher initial development cost for stronger long-term security posture")
- Why this trade-off is acceptable in the context of this project
- What mitigation exists for the weaker dimension (e.g., "higher development cost is mitigated by smaller team size and AI-assisted code generation")
- What would trigger revisiting this decision (e.g., "if development velocity falls below X, re-evaluate stack choice")

This documentation is not bureaucratic overhead. It is the foundation of the project's decision record — and it becomes input context for AI in later phases. When a question arises during implementation about why a particular technology was chosen, the decision record provides the answer. When the team considers a mid-project technology change, the decision record surfaces what was already analyzed and what trade-offs were already accepted.

### The Decision Is a Commitment, Not a Preference

Phase 2 ends with a committed stack decision. "Committed" means the team has agreed to proceed with this technology foundation and will not revisit the decision without a significant change in circumstances. This is important in an AI-centric workflow where it is easy to endlessly explore alternatives — AI will happily evaluate another five stack options if asked. The discipline is in deciding when the analysis is sufficient and committing.

The commitment is documented as an **Architecture Decision Record (ADR)** — a structured document that captures the decision, the context, the alternatives considered, the rationale, and the consequences. This ADR becomes a permanent artifact in the consolidated knowledge base and an input resource for every tool set used in subsequent phases.

---

## The Initial Threat Model

The threat model produced in Phase 2 is preliminary — a foundation for the detailed security architecture that will be developed in Phase 4. Its purpose is to identify the major threat categories and attack surfaces early enough to influence architecture and design decisions.

### What the Initial Threat Model Covers

**Data flow analysis** — How does data move through the system? Where does it enter, where is it stored, where is it processed, where does it leave? What classification does each data type carry?

**Trust boundaries** — Where do trust levels change? Between the user and the system, between system components, between the system and external services, between the system and data stores. Each trust boundary is a potential attack surface.

**Threat identification** — Using a framework like STRIDE, identify the threats relevant to each component and trust boundary. Not every theoretical threat is relevant — the model should focus on threats that are realistic given the domain, the data sensitivity, and the deployment environment.

**Risk ranking** — Each identified threat is ranked by likelihood and impact. This ranking drives which threats must be addressed in architecture (Phase 4) versus which can be addressed in implementation (Phase 5) versus which are accepted risks with monitoring (Phase 7).

### AI's Role in Threat Modeling

AI is effective at generating initial threat models from data flow descriptions. It can apply STRIDE or similar frameworks systematically, identify common attack patterns for the technologies in the stack decision, and cross-reference against known vulnerability databases.

The practitioner's role is validation. AI may miss domain-specific threats that are not well-represented in its training data. It may overweight theoretical threats and underweight practical ones. It may not understand the organization's specific risk tolerance. The initial threat model is AI-generated and human-validated — a pattern that recurs throughout the framework.

---

## Core Principles in Phase 2

Phase 2 is where the Core Principles transition from research lens (Phase 1) to decision-making framework. Every analysis output is structured around the principles, and every decision is scored against them.

### Security

Security in Phase 2 means threat modeling, compliance constraint mapping, and evaluating the security characteristics of candidate stacks. The initial threat model is the primary security artifact, but security also influences stack selection (memory-safe languages score higher), cost modeling (security tooling has costs), and benchmark definition (security scanning must be included in CI/CD time budgets).

### Maintainability

Maintainability in Phase 2 means evaluating the long-term viability of candidate stacks — documentation quality, testing ecosystem maturity, talent availability, and community health. It also means assessing the maintainability of the analysis artifacts themselves. The cost model, threat model, and decision records should be structured for future reference, not written as one-time memos.

### Economics

Economics is at the center of Phase 2. The cost model captures development costs, infrastructure at scale, licensing, AI tooling, and maintenance. But economics is not just about minimizing cost — it is about understanding the cost structure and making trade-offs with full visibility. A stack that costs more to develop but less to operate may be the right choice for a long-lived system. A stack that is cheap to prototype but expensive to scale may be the right choice for market validation. The cost model makes these dynamics visible.

### Operations

Operations in Phase 2 means evaluating how each candidate stack runs in production. Deployment complexity, scaling behavior, monitoring and observability tooling, container support, and interoperability with existing systems. Stack decisions made without operational analysis create surprises during deployment — surprises that are expensive to resolve.

### Scoring & Metrics

This is the phase where the scoring framework is established. The evaluation criteria matrix, the principle-based weightings, and the benchmark targets are all defined here. These become the measuring sticks for every subsequent phase. If the scoring framework is vague or incomplete, later phases will struggle to evaluate their own output. If the benchmark targets are unrealistic, implementation will chase goals that cannot be achieved.

### Correctness Verification

Correctness Verification in Phase 2 has two dimensions. First, verifying the correctness of the analysis itself — are the cost models based on accurate pricing data? Are the threat models complete? Are the stack scores justified by evidence? Second, evaluating the correctness verification *capabilities* of candidate stacks — does the language support formal verification? How strong is the type system? What static analysis tooling is available? A stack with strong correctness verification support will make Phases 5 and 6 significantly more effective.

---

## Tool Sets for Phase 2

### Business Analysis Tool Set

**Purpose:** Validate the business case and define user needs, market fit, and value proposition.

**Building blocks:**
- An interview prompt that walks the practitioner through business case articulation — problem definition, user personas, value proposition, competitive differentiation
- The Information Report as an input resource (competitive analysis section, market research)
- A skill that frames the AI as a business analyst with access to the project's domain context
- An action prompt that generates a structured business analysis document
- An evaluation prompt that reviews the business case for completeness and internal consistency

### Cost Modeling Tool Set

**Purpose:** Produce a structured, adjustable cost forecast across the system lifecycle.

**Building blocks:**
- An action prompt that takes stack options and scale targets and generates cost comparisons across cloud providers, licensing models, and operational scenarios
- MCP connections to cloud provider pricing APIs (where available) or reference pricing documentation
- References from the consolidated knowledge base: past project cost analyses, industry benchmark data
- A skill that provides cost modeling frameworks and common cost categories that teams overlook (AI tooling costs, security tooling, compliance certification costs, team ramp-up)
- An evaluation prompt that stress-tests the model — "What happens to costs if user growth is 3x the projection? What if a key vendor doubles pricing?"

### Stack Evaluation Tool Set

**Purpose:** Score candidate technology stacks against the six Core Principles and produce a committed decision with rationale.

**Building blocks:**
- The evaluation criteria matrix (produced during the Detail step)
- The Information Report as an input resource (technology landscape, security findings, operational assessments)
- An evaluation prompt that scores each candidate stack against every criterion, producing structured scorecards with evidence-backed justification
- An action prompt that generates "what if" simulations — "If we choose Rust, what are the implications for development velocity, hiring, and AI tooling support?"
- A skill that frames the AI as a technology evaluator, conservative about claims and explicit about trade-offs
- An action prompt that generates the Architecture Decision Record documenting the final stack choice
- A correctness verification instruction set that cross-references scores against Information Report evidence and flags unsupported claims

### Threat Modeling Tool Set

**Purpose:** Produce the initial threat model from system data flows and trust boundaries.

**Building blocks:**
- An interview prompt that guides the practitioner through describing data flows, components, external integrations, and trust boundaries
- A skill that provides the STRIDE framework (or alternative) and domain-specific threat context
- An action prompt that generates the threat model from the data flow description, applying the framework systematically
- References from the consolidated knowledge base: compliance requirements, industry-specific threat intelligence, past project threat models
- An evaluation prompt that reviews the threat model for completeness — "Are all trust boundaries covered? Are domain-specific threats included? Are risk rankings justified?"

### Benchmark Definition Tool Set

**Purpose:** Establish the quantitative targets that will measure the system throughout development and production.

**Building blocks:**
- The business analysis and cost model as input resources
- An action prompt that proposes benchmark targets based on industry standards, competitive benchmarks, and project-specific requirements
- An evaluation prompt that assesses whether targets are measurable, realistic, and aligned with the Core Principles
- References from the consolidated knowledge base: industry performance benchmarks, past project targets and actuals
- An instruction set for structuring benchmarks in a format that automated scoring can consume in later phases

---

## Common Pitfalls

### Analysis Paralysis

AI makes it easy to run one more comparison, model one more scenario, evaluate one more alternative. Phase 2 requires discipline about when the analysis is sufficient. The goal is an informed decision, not a perfect one. Set a time boundary for analysis and commit when it is reached. The decision record captures the analysis done and the unknowns remaining — it does not require omniscience.

### Optimizing for One Principle

A team that selects a stack purely on performance (Operations) while neglecting security tooling maturity (Security) or talent availability (Maintainability) will pay for that imbalance later. The Core Principles exist to force multi-dimensional evaluation. If a stack scores 5 on one principle and 2 on another, the trade-off must be explicit and accepted — not ignored.

### Cost Models Without Scale Assumptions

A cost model that captures only the MVP is not a cost model — it is a launch budget. Phase 2 cost models must include projections at multiple scale points, with clear assumptions about growth. AI can model these scenarios readily, but only if the team specifies the scale assumptions as part of the analysis.

### Threat Models Deferred to "Later"

The initial threat model is not optional. Without it, architecture decisions in Phase 3 and Phase 4 are made without understanding the security constraints they must satisfy. A threat model produced after the architecture is designed is a compliance exercise. A threat model produced before is a design input. The difference is significant.

### Undocumented Decisions

Every stack decision, every major trade-off, every rejected alternative should be documented in the decision record. In an AI-centric workflow, this documentation is not just for human institutional memory — it becomes input context for AI in every subsequent phase. An undocumented decision is a decision that AI cannot reason about later.

---

## Validation Checkpoint

Before moving to Phase 3, the team validates that the Phase 2 artifacts are complete and consistent.

- **Business analysis:** Is the business case clearly articulated? Are user needs validated? Is the value proposition specific enough to guide design decisions?
- **Cost model:** Does the model cover the full lifecycle — development, infrastructure, licensing, AI tooling, maintenance? Are scale assumptions defined? Are AI tooling costs included?
- **Stack decision:** Is the decision documented as an ADR with rationale, alternatives considered, trade-offs accepted, and Core Principle scores? Is the principle weighting established?
- **Threat model:** Are data flows documented? Are trust boundaries identified? Are threats ranked by likelihood and impact? Is the model complete enough to inform architecture decisions?
- **Benchmarks:** Are targets quantitative and measurable? Do they cover all six Core Principles? Are they realistic given the stack decision and cost constraints?
- **Consistency:** Do the artifacts align with each other? Does the cost model reflect the chosen stack? Does the threat model cover the data flows implied by the business analysis? Do the benchmarks match the ambitions of the business case?

If gaps exist, the SDD cycle iterates. The analysis specification may need expansion (back to Specify), additional research sections may be needed (back to Plan), or specific analyses may need to be rerun (back to Task and Implement).

---

## What Comes Next

Phase 2 produces the analytical foundation: a validated business case, a cost model, a committed stack decision with rationale, an initial threat model, and a benchmark framework. These artifacts are consequential — they constrain and enable everything that follows.

Phase 3 takes these artifacts and begins the work of design. The next article covers **Design & Technical Analysis** — where the stack decision is stress-tested against the Core Principles through structured scoring and simulation, monitoring and observability hooks are identified, compliance implications are mapped to design constraints, and the team locks in the technical direction that architecture will formalize in Phase 4.

---

*This is a living document. The tool sets, analytical frameworks, and examples will be expanded and refined as the series develops. Every part of this framework is open to iteration.*

*Previous: [Article 3 — Phase 1: Information Gathering]*
*Next in the series: [Article 5 — Phase 3: Design & Technical Analysis]*
