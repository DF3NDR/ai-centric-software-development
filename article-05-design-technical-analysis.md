# Phase 3 — Design & Technical Analysis

*Part 5 of The AI-Centric Software Development Playbook*

---

## Stress-Testing Before Committing

Phase 2 produced a stack decision, a business case, a cost model, an initial threat model, and a benchmark framework. Those artifacts represent the team's best analytical judgment — but analysis and design are different disciplines. Analysis asks "what should we choose?" Design asks "does the choice actually hold up when we start building on it?"

Phase 3 is the bridge between analysis and architecture. Its purpose is to take the Phase 2 outputs, subject them to structured design exploration and simulation, score every significant decision against the Core Principles, and lock in a validated technical direction before the team invests in detailed architecture and implementation.

This is the phase where problems are cheapest to find. A design flaw discovered here costs a conversation with AI. The same flaw discovered during implementation costs days of rework. Discovered in production, it costs an incident. Phase 3 exists to front-load that discovery through deliberate, principle-scored exploration of the design space.

---

## What Design & Technical Analysis Accomplishes

Phase 3 produces three primary artifacts.

**A Design Direction Document** — Not a full architecture (that comes in Phase 4), but a validated set of design commitments: the system's high-level structure (modular, layered, service-oriented), its primary interaction patterns (API-first, event-driven, request-response), its deployment model (containerized, serverless, hybrid), and its data architecture (relational, document, event-sourced, polyglot). Each commitment is scored against the Core Principles and documented with rationale.

**A Principle Scorecard** — A structured evaluation of the emerging design against all six Core Principles. This is the first formal scorecard of the project — the baseline against which all subsequent phases will be measured. Each principle receives a score with justification, and any principle scoring below the project's threshold triggers either a design revision or an explicit acceptance of risk.

**A Technical Feasibility Assessment** — The results of AI-driven simulations and "what if" analyses that test whether the design direction holds under stress. Can the chosen stack meet the performance benchmarks at target scale? Does the security model survive the threats identified in the threat model? Does the cost model hold when the design choices are factored in? Where are the breaking points?

Additionally, Phase 3 identifies two critical forward-looking concerns:

**Monitoring and observability hooks** — Where in the design will the team need visibility during operations? These are identified now so that architecture (Phase 4) can incorporate them structurally rather than bolting them on after the fact.

**Compliance design constraints** — How do the compliance requirements identified in Phase 1 and mapped in Phase 2 translate into concrete design constraints? What must be true about data handling, access control, audit logging, and encryption for the system to satisfy its regulatory obligations?

---

## The SDD Cycle in Phase 3

The SDD cycle in Phase 3 draws from all Phase 2 artifacts as input context. The Specify step defines what design questions need to be answered. The Plan step organizes the design exploration. The Detail step produces structured evaluation criteria. The Task step assigns specific simulations and analyses. The Implement step executes them and produces the phase artifacts.

### Step 1: Specify — What Design Questions Must Be Answered?

Before exploring design options, the team specifies the questions this phase must resolve. An interview prompt from the Design Analysis tool set structures this:

- Given the stack decision, what are the viable high-level system structures? (monolith with clean layers, microservices, modular monolith, service mesh)
- What interaction patterns does the system require? (synchronous APIs, asynchronous messaging, event streaming, batch processing)
- What data architecture fits the domain? (single relational database, polyglot persistence, event sourcing, CQRS)
- What deployment model aligns with the operations requirements and cost constraints?
- Where are the highest-risk design decisions — the ones where a wrong choice would be most expensive to reverse?
- What must the design prove before the team commits to detailed architecture?

The output is a **design exploration specification** — a document that scopes the design work and identifies which decisions carry the most risk and deserve the most rigorous analysis.

### Step 2: Plan — Organize the Design Exploration

The design exploration specification is broken into sections, each representing a coherent design domain:

- **System structure** — High-level structural options, their trade-offs, and their fitness for the project's requirements
- **Interaction patterns** — API design philosophy, communication between components, external integration strategy
- **Data architecture** — Storage models, data flow patterns, consistency requirements, migration strategy
- **Deployment model** — Container strategy, orchestration, environment management, CI/CD implications
- **Cross-cutting concerns** — Security model, observability strategy, compliance constraints, extensibility approach
- **Simulation scenarios** — Specific "what if" questions that must be answered through AI-driven analysis

### Step 3: Detail — Define Design Evaluation Criteria

Each section is taken through a detail prompt that produces structured evaluation criteria — the PRD equivalent for design decisions.

The Design Evaluation PRD for each section specifies:

**What options exist** — The viable design approaches for this domain, based on the stack decision and the project's requirements.

**How each option will be scored** — Specific criteria mapped to the six Core Principles. For system structure, this might include:

- Security: How does this structure affect the attack surface? Does it support zero-trust between components? How granular is the access control model?
- Maintainability: Can individual components be tested in isolation? Can they be updated independently? How complex is the dependency graph?
- Economics: What is the development overhead of this structure? What is the operational cost? How does it affect team velocity?
- Operations: How does this structure deploy? How does it scale? How does it fail gracefully? Where do monitoring hooks go?
- Scoring & Metrics: Can performance be measured per-component? Can the system produce the metrics needed to evaluate the benchmarks?
- Correctness Verification: Can components be formally verified independently? Does the structure support contract testing between components? Can specification conformance be checked at the component level?

**What must be simulated** — The specific scenarios that AI should analyze to test whether the design holds. "If we use a modular monolith, can we still meet the latency benchmark under 10x projected load?" "If we use event sourcing for the order domain, what is the impact on query performance for the reporting module?"

### Step 4: Task — Assign Specific Design Analyses and Simulations

The evaluation criteria from Step 3 are broken into concrete tasks:

- Evaluate three system structure options (modular monolith, microservices, hybrid) against the six Core Principles using the evaluation criteria. Produce a scored comparison matrix with evidence-based justification for each rating.
- Simulate the performance characteristics of each data architecture option (PostgreSQL with JSONB, PostgreSQL + Redis, event-sourced with projections) against the latency and throughput benchmarks from Phase 2. Identify which options meet benchmarks at MVP scale, growth scale, and target scale.
- Map the initial threat model from Phase 2 onto each system structure option. For each, identify: new attack surfaces introduced by the structure, trust boundaries that need protection, and whether the security model from the threat model is fully addressable.
- Analyze the compliance requirements against each design option. Identify which requirements are satisfied natively by the design, which require additional components, and which are at risk.
- Identify monitoring and observability insertion points for each system structure option. For each, specify: what metrics should be captured, where logging hooks are needed, what tracing strategy applies, and what alerting thresholds make sense given the benchmarks.
- Estimate the development effort for each option at the structure level. Factor in team expertise from Phase 1, AI-assisted development velocity, and the complexity of the chosen stack.

### Step 5: Implement — Execute the Design Analysis

The Design Analysis tool sets go to work. This is where AI's simulation and analytical capabilities provide distinctive value.

**Design option scoring** — AI evaluates each design option against the full evaluation criteria matrix, producing structured scorecards. The output is not a recommendation — it is a transparent analysis that surfaces the trade-offs so the practitioner can make an informed decision.

**Performance simulation** — AI models the expected behavior of each design option under various load conditions, using the benchmarks from Phase 2 as targets. This is not a substitute for actual performance testing (that comes in Phases 5 and 6), but it identifies design options that are structurally unlikely to meet requirements before the team commits to them.

**Threat model mapping** — AI takes the initial threat model and maps it onto each design option, identifying how the attack surface changes with different structural choices. A microservices architecture introduces network-based attack vectors between services. A monolith reduces network attack surface but concentrates risk in a single deployment unit. These trade-offs should be visible before the architecture is detailed.

**Compliance analysis** — AI maps compliance requirements to design constraints, producing a structured matrix of requirements, the design elements that satisfy them, and gaps that need to be addressed in architecture. This prevents the common failure of discovering a compliance gap during audit preparation.

**Observability planning** — AI identifies the monitoring and observability hooks needed for each design option. This forward-looking analysis ensures that Phase 4 (Architecture) and Phase 5 (Implementation) build observability into the system rather than retrofitting it before deployment.

---

## The Principle Scorecard

The Principle Scorecard is Phase 3's most important artifact for ongoing project health. It establishes the baseline against which all subsequent work is measured.

### Structure

For each Core Principle, the scorecard captures:

- **Current score** — A structured rating (1–5) based on the design direction, with justification citing specific design decisions and evidence
- **Target score** — What the principle should score by the time the system reaches production, based on the benchmarks and priorities established in Phase 2
- **Gap analysis** — Where the current design falls short of the target, why, and what must happen in later phases to close the gap
- **Risk items** — Specific risks to this principle that the design introduces or does not fully address
- **Monitoring indicators** — What metrics or signals will track this principle's health as the project progresses through implementation, testing, and deployment

### How the Scorecard Is Used

The scorecard is not a one-time document. It is updated at every phase transition:

- Phase 4 (Architecture) updates the scores based on architectural decisions
- Phase 5 (Implementation) updates based on actual code quality, test coverage, and security scan results
- Phase 6 (Testing) updates based on audit findings and performance validation
- Phase 7 (Deployment) updates based on operational reality

Score regression — a principle scoring lower at a later phase than it did at an earlier one — is a signal that something has gone wrong. The toolkit should flag regressions automatically, triggering review before the team proceeds.

### AI Generates, Humans Validate

AI produces the initial scorecard based on the design analysis. The practitioner reviews it critically. AI tends to be either too optimistic (scoring design intentions rather than design realities) or too conservative (flagging theoretical risks that are unlikely in the project's context). The practitioner calibrates based on domain expertise and risk tolerance.

The validated scorecard becomes part of the project's decision record and an input resource for every tool set used in subsequent phases.

---

## Design Simulations

Phase 3 is the appropriate place for AI-driven "what if" analysis — structured exploration of how design choices interact with each other and with the project's constraints.

### What Simulations Answer

Effective design simulations address specific, testable questions:

- "If we use a modular monolith with the Rust/Axum stack, can we meet the p99 latency target of 50ms at 10,000 concurrent users?" AI can model the expected performance based on published benchmarks, the data architecture choice, and the anticipated request patterns.
- "If we implement zero-trust between all internal service boundaries, what is the additional latency overhead and operational complexity?" AI can estimate the cost of mTLS, service mesh overhead, and authentication at every boundary.
- "If we choose event sourcing for the core domain, what is the development overhead compared to a traditional CRUD approach, given the team's experience level?" AI can estimate based on published complexity comparisons and the team profile from Phase 1.
- "If a primary database node fails, how does the system degrade under each data architecture option?" AI can model failover scenarios and identify which options maintain acceptable performance during degraded operation.

### What Simulations Do Not Replace

Design simulations are analytical models, not empirical tests. They identify likely outcomes and structural risks, but they do not replace:

- Actual performance benchmarking (Phase 5 and 6)
- Penetration testing (Phase 6)
- Load testing under realistic conditions (Phase 6)
- Production monitoring (Phase 7)

The value of simulation is in eliminating clearly unworkable options and identifying hidden trade-offs *before* the team invests in detailed architecture and implementation. A simulation that reveals a design option cannot meet a critical benchmark saves weeks of wasted effort. A simulation that identifies an unexpected security exposure saves a potential incident.

---

## Locking In Technical Direction

Phase 3 ends with a committed technical direction. This is distinct from the stack decision made in Phase 2. The stack decision chose the technologies. The technical direction locks in *how* those technologies will be used: the system structure, interaction patterns, data architecture, deployment model, and cross-cutting concern strategies.

### What Gets Locked

- System structure: modular monolith, microservices, hybrid, or another pattern — committed with rationale
- API philosophy: REST, gRPC, GraphQL, or hybrid — committed with rationale for which boundaries use which protocol
- Data architecture: storage model, consistency strategy, caching approach — committed with rationale
- Deployment model: container strategy, orchestration approach, environment topology — committed with rationale
- Security model: authentication strategy, authorization model, encryption approach, audit logging strategy — committed with rationale tied to the threat model
- Observability strategy: metrics, logging, tracing, and alerting approaches — committed with monitoring insertion points identified

### What Remains Open

Phase 3 does not lock in module boundaries, API specifications, database schemas, or implementation details. Those are the work of Phase 4 (Architecture & Modular Design). Phase 3 locks in the *direction* — the structural patterns and strategies that architecture will elaborate into detailed blueprints.

### The Commitment Is Documented

Every locked design decision becomes an Architecture Decision Record (ADR), extending the ADR series begun in Phase 2. Each ADR captures: the decision, the context (which Phase 2 artifacts informed it), the alternatives considered (from the design analysis), the simulation results, the Core Principle scores, and the consequences for later phases.

These ADRs become part of the consolidated knowledge base. They are input context for every tool set used in Phase 4 and beyond. When a question arises during architecture — "why did we choose event sourcing for the order domain?" — the ADR provides the answer with full traceability back to the analysis that supported it.

---

## Core Principles in Phase 3

Phase 3 is where the Core Principles become explicit scorecards for the first time. Every design decision is scored, and the aggregate scores establish the project's principle baseline.

### Security

Security in Phase 3 means mapping the threat model onto design options and ensuring the chosen direction addresses the identified threats. The security model (authentication, authorization, encryption, audit) is defined at the strategic level. Design options that introduce new attack surfaces or fail to address critical threats are flagged and either redesigned or accepted as documented risks.

### Maintainability

Maintainability in Phase 3 means evaluating whether the design direction supports testability, documentation, independent component evolution, and debuggability. A design that tightly couples components scores poorly on Maintainability regardless of how clean the initial code is. A design that supports independent testing and deployment of components scores well.

### Economics

Economics in Phase 3 means validating that the design direction stays within the cost model from Phase 2. Simulations should include cost projections — a design that meets performance benchmarks but at 3x the projected infrastructure cost fails the economics principle. Development effort estimates should be updated based on the complexity of the chosen design patterns.

### Operations

Operations in Phase 3 means ensuring the design direction is operable. Deployment complexity, scaling characteristics, failure modes, and monitoring feasibility are all evaluated. The observability strategy is defined here — where monitoring hooks go, what metrics are captured, what alerting thresholds apply. A design that performs well but cannot be diagnosed when problems occur fails the operations principle.

### Scoring & Metrics

This is the phase where the Principle Scorecard is established. Every design decision produces measurable ratings. The scoring framework from Phase 2 is applied for the first time, and the baseline scores are recorded. These scores will be tracked through every subsequent phase, making design health visible and regression detectable.

### Correctness Verification

Correctness Verification in Phase 3 means evaluating whether the design direction supports formal verification, contract testing, specification conformance, and automated correctness checking. A design with well-defined component boundaries and explicit contracts between components is more verifiable than one with implicit dependencies and shared mutable state. The verifiability of the design should be evaluated alongside its functionality.

---

## Tool Sets for Phase 3

### Design Exploration Tool Set

**Purpose:** Support SDD Steps 1–2 (Specify, Plan) — define design questions and organize the exploration.

**Building blocks:**
- An interview prompt that walks the practitioner through scoping the design exploration, referencing Phase 2 artifacts
- The Phase 2 artifacts as input resources (stack decision ADR, cost model, threat model, benchmarks)
- A skill that frames the AI as a systems design analyst with knowledge of common architectural patterns and their trade-offs
- An action prompt that generates the design exploration plan with sections and priorities

### Design Scoring Tool Set

**Purpose:** Support SDD Steps 3–5 (Detail, Task, Implement) — evaluate design options against the Core Principles.

**Building blocks:**
- A detail prompt that generates evaluation criteria for each design domain, mapped to the six Core Principles
- An evaluation prompt that scores each design option against the criteria, producing structured scorecards with evidence-based justification
- The Information Report and Phase 2 artifacts as input resources
- A skill that enforces rigorous trade-off analysis — the AI must identify what each option sacrifices, not just what it achieves
- An action prompt that generates the Principle Scorecard baseline from the evaluated design direction

### Simulation Tool Set

**Purpose:** Run AI-driven "what if" analyses that test design options under stress.

**Building blocks:**
- An action prompt that takes a design option, the benchmark targets, and the threat model and generates a structured feasibility assessment
- A skill that provides simulation framing — how to model performance, estimate costs, and project failure modes
- The benchmarks, cost model, and threat model as input resources
- An evaluation prompt that assesses simulation results — "Does this design option meet the benchmarks? Where does it break? What is the confidence level?"

### Direction Commitment Tool Set

**Purpose:** Document locked design decisions as ADRs and compile the Design Direction Document.

**Building blocks:**
- An action prompt that generates ADRs from design decisions, including context, alternatives, scores, and consequences
- The Principle Scorecard and simulation results as input resources
- A skill that provides ADR formatting standards and ensures traceability to Phase 2 artifacts
- An evaluation prompt that reviews the complete Design Direction Document for internal consistency and principle coverage
- A correctness verification instruction set that checks whether the locked direction addresses all compliance constraints and threat model findings

---

## Common Pitfalls

### Designing Without Simulating

It is tempting to choose the design pattern the team is most familiar with and move directly to architecture. Phase 3 exists specifically to challenge that impulse. Even when the "obvious" choice turns out to be correct, the simulation process surfaces edge cases and trade-offs that improve the final design. When the obvious choice turns out to have a hidden flaw, the simulation saves weeks or months of rework.

### Scoring After Deciding

If the team decides on a design direction and then scores it against the Core Principles, the scoring becomes a rationalization exercise rather than an analytical one. The evaluation criteria must be defined before the analysis is conducted, and the scores must be produced before the commitment is made. This is the same discipline applied to stack scoring in Phase 2, extended to design decisions.

### Ignoring Operational Feasibility

A design that looks elegant on paper but cannot be deployed, monitored, or debugged in production fails the Operations principle. Phase 3 should include explicit analysis of operational feasibility for each design option — deployment complexity, monitoring strategy, failure mode analysis, and scaling behavior. Design elegance that ignores operational reality is technical debt disguised as architecture.

### Skipping the Scorecard Baseline

The Principle Scorecard is not optional. Without it, the team has no way to detect regression in later phases. A system whose security posture degrades from Phase 3 to Phase 5 without detection is a system headed for trouble. The scorecard baseline, established here, makes regression visible.

### Locking Too Much or Too Little

Phase 3 should lock strategic direction — system structure, interaction patterns, data architecture, deployment model, security model, observability strategy. It should not lock module boundaries, API schemas, or implementation specifics. Locking too much creates rigidity that constrains Phase 4 unnecessarily. Locking too little leaves Phase 4 without clear direction, causing architecture to revisit design questions that should have been resolved.

---

## Validation Checkpoint

Before moving to Phase 4, the team validates that the Phase 3 artifacts are sufficient.

- **Design Direction Document:** Are the system structure, interaction patterns, data architecture, deployment model, security model, and observability strategy all committed with rationale?
- **Principle Scorecard:** Does every principle have a current score, a target score, a gap analysis, identified risks, and monitoring indicators? Are any scores below the project's threshold without an explicit risk acceptance?
- **Technical Feasibility:** Have the critical design questions been simulated? Do the simulation results support the locked direction? Are breaking points identified and documented?
- **ADRs:** Is every locked design decision documented as an Architecture Decision Record with traceability to Phase 2 artifacts?
- **Forward-looking concerns:** Are monitoring and observability hooks identified? Are compliance design constraints mapped to specific design elements?
- **Consistency with Phase 2:** Does the locked direction align with the stack decision, the cost model, the threat model, and the benchmarks? If direction locked in Phase 3 invalidates a Phase 2 assumption, has Phase 2 been updated?

If gaps exist, the SDD cycle iterates within Phase 3 before the team proceeds.

---

## What Comes Next

Phase 3 produces a validated technical direction — the strategic decisions that architecture will build on. The system's structure, interaction patterns, data architecture, deployment model, security model, and observability strategy are locked with scored rationale and documented trade-offs.

Phase 4 takes this direction and makes it concrete. The next article covers **Architecture & Modular Design** — where the design direction is elaborated into module boundaries, API specifications, security boundaries, a documentation strategy, and a governance model. This is where the blueprint becomes detailed enough to build from, and where the principles-first approach produces its most tangible architectural benefits.

---

*This is a living document. The tool sets, scoring patterns, simulation approaches, and examples will be expanded and refined as the series develops. Every part of this framework is open to iteration.*

*Previous: [Article 4 — Phase 2: Analysis & Stack Selection]*
*Next in the series: [Article 6 — Phase 4: Architecture & Modular Design]*
