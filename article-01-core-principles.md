# Core Principles — Your Compass for Every Decision

*Part 1 of The AI-Centric Software Development Playbook*

---

## Why Principles Come First

Before we write a line of code, before we select a stack, before we even gather requirements — we need a shared framework for evaluating every decision we make. That framework is what this article establishes.

In traditional development, principles like security, maintainability, and operational readiness tend to surface at different stages. Security gets a review before launch. Maintainability becomes a concern when someone inherits the codebase. Cost overruns get noticed at the quarterly budget review. By then, the decisions that created those problems were made months ago, buried under layers of subsequent work.

In AI-centric development, this pattern becomes significantly more dangerous. AI moves fast. It generates code, configurations, specifications, and architectural proposals at a pace that makes retroactive principle enforcement impractical. If you don't embed your principles into the process from the start — into the prompts, the evaluation criteria, the automated checks — the AI will optimize for whatever you did ask for and ignore everything you didn't.

The six Core Principles defined here are designed to travel with you across every phase of development. They are not a checklist to satisfy at a single gate. They are a concurrent lens, applied at every decision point, from the first information-gathering prompt to the last production monitoring alert.

There is a practical reason we begin with principles before discussing tools, prompts, or process: **the Core Principles drive every decision about what we include in our toolkit.** When we evaluate a prompt, a skill, an MCP integration, or any other building block, the question is always — does this help us apply and enforce our principles? A tool that accelerates development but undermines Correctness Verification does not belong. A prompt that generates code without considering Security is incomplete. The principles are the filter through which the entire toolkit is assembled.

---

## The Six Core Principles

The first four principles define *what you are optimizing for*. The last two define *how you know you are getting it right*.

### 1. Security

Security is not a feature. It is a property of the entire system, and it must be considered from the earliest design conversations through post-deployment monitoring.

**Subcategories:**

- **Threat Modeling** — Identify what can go wrong before deciding how to build. AI can assist in generating threat models from architecture diagrams and data flow descriptions, but the engineer must validate that the model accounts for the right adversaries and attack vectors. Threat models should be living documents, updated as the system evolves.
- **Zero-Trust Design** — Assume no component, user, or service is inherently trusted. Design authentication, authorization, and encryption at every boundary. This affects architecture decisions early — it is far cheaper to design for zero-trust than to retrofit it.
- **Continuous Audit Hooks** — Build the infrastructure for security auditing into the system from day one. Logging, monitoring, and alerting should not be afterthoughts. If you cannot audit it, you cannot secure it.
- **Compliance Preparation** — Whether the requirement is SOC 2, HIPAA, GDPR, PCI-DSS, or an industry-specific standard, the time to prepare is during design, not before launch. AI can help map compliance requirements to architectural decisions, but the requirements themselves must be identified early. Compliance is an evolutionary process — it begins with understanding what applies and designing to satisfy it incrementally, not as a scramble at the end.

**How it applies across phases:** During information gathering, Security asks "what are the known vulnerabilities in candidate technologies?" During stack selection, it asks "does this choice introduce or mitigate risk?" During implementation, it runs continuous scans. During deployment, it monitors for drift. It never stops asking.

---

### 2. Maintainability

A system that works today but cannot be understood, tested, or modified tomorrow is a liability, not an asset. Maintainability is the principle that ensures the work survives contact with time.

**Subcategories:**

- **Testing Strategy** — Define what gets tested, how, and to what standard. Unit tests, integration tests, end-to-end tests, property-based tests — each serves a different purpose. The strategy should be established during design, not invented during implementation. AI can generate test cases, but the team defines the strategy.
- **Documentation** — In an AI-centric workflow, documentation serves two audiences: humans and AI. Documentation must be living (updated as the system changes), queryable (structured so that questions can be answered from it), and AI-parseable (formatted so that AI tools can consume and reason about it). Inline comments, architecture decision records, API documentation, and operational runbooks all fall under this umbrella.
- **Technical Debt Control** — Debt will accumulate. The question is whether it accumulates intentionally (with documentation and a payoff plan) or invisibly (discovered only when something breaks). AI can track debt, flag it during code review, and prioritize repayment — but only if the team establishes what constitutes debt and how to measure it.
- **Observability and Debuggability** — When something goes wrong, how quickly can the team understand what happened? Structured logging, distributed tracing, error classification, and diagnostic tooling should be designed into the system, not bolted on after the first outage.

**How it applies across phases:** During design, Maintainability asks "can this be understood by someone (or some AI) who wasn't in the room?" During implementation, it asks "is this tested, documented, and structured for change?" Post-deployment, it asks "can we diagnose problems and evolve the system without fear?"

---

### 3. Economics

Every decision has a cost. Economics is the principle that ensures those costs are understood, forecasted, and weighed against the value they create.

**Subcategories:**

- **Cost Forecasting** — Development time, infrastructure costs, licensing fees, AI tool costs, ongoing maintenance burden. These should be estimated during analysis, tracked during implementation, and validated post-deployment. AI can assist with estimation (especially for infrastructure and licensing), but the team must define what is acceptable.
- **Speed-to-Market** — Time has value. A feature delivered three months late may have zero value if the market has moved. Speed-to-market is a legitimate economic consideration, but it must be weighed against the other principles — shipping fast with poor security or no test coverage is not a savings, it is a deferred cost.
- **Resource Scaling** — How does the cost structure change as the system grows? As the team grows? As usage scales? Decisions made during stack selection and architecture have outsized impact on long-term resource economics. A choice that is cheap at prototype scale may be ruinous at production scale, and vice versa.

**How it applies across phases:** During information gathering, Economics asks "what does each option actually cost?" During stack selection, it asks "what are the total lifecycle costs, not just the initial build?" During implementation, it tracks actuals against estimates. Post-deployment, it validates forecasts and identifies optimization opportunities.

---

### 4. Operations

Operations is the principle concerned with how the system behaves in the real world — at scale, under failure, alongside other systems, and under organizational governance.

**Subcategories:**

- **Scalability** — Can the system handle growth in users, data, and traffic without architectural rework? Scalability decisions made during design constrain what is possible later. Identify the expected growth vectors early and design for them.
- **Reliability** — What is the uptime target? What are the failure modes? How does the system degrade gracefully? Reliability is not just about preventing failures; it is about ensuring that when failures occur, the impact is contained and recovery is fast.
- **Interoperability** — Systems do not exist in isolation. APIs, data formats, authentication protocols, and integration patterns must be designed for compatibility with the broader ecosystem. An API-first approach naturally supports interoperability, but the team must define what "compatibility" means in their context.
- **Governance** — Who owns what? Who approves changes to critical modules? What are the review gates? Governance is particularly important in small teams where individuals may be responsible for multiple domains. Clear ownership prevents both gaps and conflicts.
- **Post-Deployment Monitoring** — Monitoring must be designed early, not added later. The hooks, interfaces, dashboards, and alerting strategies that the operations team needs in production should be specified during architecture and built during implementation. If you wait until deployment to think about monitoring, you will monitor the wrong things.

**How it applies across phases:** During design, Operations asks "how does this run in production?" During architecture, it asks "where do monitoring hooks go?" During implementation, it asks "are the operational interfaces being built alongside the features?" Post-deployment, it watches everything.

---

### 5. Scoring & Metrics

The first four principles define what matters. Scoring & Metrics is the principle that makes those definitions measurable. Without it, principles are aspirations — things the team believes in but cannot verify. With it, principles become enforceable constraints that produce concrete, trackable outcomes.

**Why this is a Core Principle, not just a practice:** In an AI-driven workflow, the volume of decisions and outputs is too large for intuition-based evaluation. When AI generates hundreds of lines of code, dozens of configuration options, or multiple architectural proposals in a single session, the team needs automated, quantitative ways to evaluate quality. Scoring provides that.

**Subcategories:**

- **Benchmark Definition** — For each of the other five principles, define quantitative benchmarks wherever possible. Performance targets, cost ceilings, test coverage thresholds, uptime SLAs, vulnerability scan pass rates, verification coverage. These benchmarks should be established during analysis and refined as the project matures.
- **Automated Scorecards** — AI generates scorecards at each phase checkpoint. The measurement itself is automated; the human reviews and approves. This inverts the traditional model where humans do the measurement and hope they didn't miss anything.
- **Multi-Level Scoring** — Scoring applies at every level of abstraction: architecture decisions get scored during design, code quality gets scored during implementation, deployment readiness gets scored before release, operational health gets scored in production. The granularity changes, but the practice is continuous.
- **Trend Tracking** — A single score is a snapshot. Trends tell you whether the system is improving or degrading. Regression detection — catching a score that drops from one phase to the next — is as important as initial measurement. AI is well-suited to tracking trends and flagging regressions across large volumes of metrics.
- **Evolving Criteria** — Scoring criteria are not static. Early phases score design decisions and trade-off rationale. Later phases score runtime behavior and operational performance. The criteria evolve with the project, and the team must revisit and update them at each major phase transition.

**Examples:**

A simple example: unit test coverage percentage as a Maintainability metric. The team sets a threshold (say, 80%). AI-generated code that falls below the threshold is flagged automatically. The engineer reviews the gaps and decides whether to add tests or accept the shortfall with documentation.

A more complex example: security posture scoring across all identified attack surfaces. Each attack surface gets a score based on the controls in place (encryption, authentication, input validation, audit logging). The aggregate score represents the system's overall security posture, tracked from design through production.

**How it applies across phases:** Scoring is the mechanism that makes every other principle visible. During analysis, it scores stack options. During design, it scores architectural decisions. During implementation, it scores code quality. During testing, it becomes a pass/fail gate. Post-deployment, it monitors operational health. At every phase, it answers the question: "Are we actually meeting the standards we set for ourselves?"

---

### 6. Correctness Verification

Scoring tells you *how well* something performs. Correctness Verification tells you *whether it is right*.

This distinction is critical in AI-centric development. AI produces enormous volumes of output — code, specifications, configurations, documentation, test cases, architectural proposals. Human review alone cannot scale to verify all of it. A senior engineer can review a pull request, but when AI generates an entire module from a specification, the review problem changes in kind, not just in degree.

Correctness Verification is the principle that ensures the toolkit includes mechanisms for verifying that AI output is actually correct — not just plausible, not just passing tests, but demonstrably right.

**Why this is a Core Principle, not just a testing practice:** Testing tells you that the code does what the tests say it should do. Correctness Verification asks a deeper question: does the code do what the *specification* says it should do? Does the specification capture what the *requirements* actually need? Are the requirements themselves internally consistent? Each layer of verification catches a different class of error.

**Subcategories:**

- **Formal Verification** — At each stage of development, AI can generate formal proofs or verification models that mathematically demonstrate correctness of critical components. A formal proof does not just test examples; it proves properties hold for all possible inputs. This is the most rigorous form of correctness verification, and AI is increasingly capable of generating these proofs.

  This is also the clearest example of the human-AI dynamic in this paradigm: *the AI builds the formal verification, but the engineer must verify that the verification itself is sound.* The human confirms the proof is asking the right question — that the properties being verified are the ones that actually matter, that the model accurately represents the real system, and that the boundary conditions are correct. The judgment moves up a level of abstraction. The engineer is not checking every line of code; the engineer is checking that the proof structure is valid.

- **Automated Correctness Checks** — Below the level of formal verification, a rich set of automated tools can catch classes of errors without human review of every line: static analysis, type checking, contract testing, property-based testing, invariant enforcement, linting, and more. These should be layered — each tool catches a different kind of error, and the combination provides coverage that no single tool achieves alone.

- **AI-vs-AI Verification** — Using separate AI processes to review, challenge, and validate the output of the primary AI. One AI generates; another AI audits. The auditing AI operates with a different prompt, a different context, or even a different model — specifically to avoid the blind spots of the generating AI. Neither is trusted blindly. The engineer reviews disagreements between the two.

- **Specification Conformance** — Automated checks that verify generated code, APIs, and configurations actually conform to the specifications and architecture documents produced in earlier phases. When an OpenAPI spec says an endpoint returns a 404 for missing resources, specification conformance testing verifies that it actually does — not as a one-time test, but as a continuous check that runs with every build.

- **Regression and Drift Detection** — Continuous verification that the system still meets its correctness criteria as changes accumulate. This is not just test regression (did a test start failing?) but specification regression (did the system's behavior drift from its documented design?). AI can compare current behavior against baseline specifications and flag drift that traditional test suites would miss.

- **The Engineer's Role** — Correctness Verification does not remove the engineer from the loop. It changes *what* the engineer reviews. Instead of reading every line of code, the engineer validates verification strategies, reviews edge cases that verification surfaces, and confirms that the right things are being verified. The volume work shifts to AI. The judgment work stays with the human.

**Examples:**

A straightforward example: property-based testing on a data transformation function. Instead of writing specific test cases, the team defines properties ("the output should always have the same number of records as the input," "no field should be null after transformation"). AI generates hundreds of random inputs and verifies the properties hold. The engineer defines the properties; the AI does the exhaustive checking.

A more rigorous example: formal verification of a state machine in a payment processing module. AI generates a TLA+ or Alloy model of the state machine and proves that it cannot reach an invalid state (e.g., a payment cannot be both "completed" and "refunded"). The engineer reviews the model to confirm it accurately represents the actual system and that the safety properties cover the real-world risks. The AI did the mathematical proof. The engineer verified that the proof was about the right thing.

**How it applies across phases:** During design, Correctness Verification asks "can we prove this architecture avoids the failure modes we identified in threat modeling?" During implementation, it asks "does this code conform to the spec, and can we prove critical properties hold?" During testing, it becomes the deepest layer of validation. Post-deployment, it watches for drift between documented behavior and actual behavior.

---

## How the Principles Work Together

The six principles are not independent checkboxes. They interact, reinforce each other, and sometimes create tension that requires deliberate trade-off decisions.

### Reinforcement

Some principle combinations are naturally synergistic. Strong Security practices (audit hooks, zero-trust) directly support Operations (monitoring, governance). Good Maintainability (documentation, testing) makes Correctness Verification easier — well-documented specs are easier to verify against. Scoring & Metrics makes every other principle visible and trackable.

### Tension

Other combinations create legitimate trade-offs. Economics (speed-to-market) may conflict with Correctness Verification (formal proofs take time). Security (defense in depth) may conflict with Economics (every security layer has a cost). Maintainability (comprehensive documentation) may conflict with Economics (documentation takes effort).

These tensions are not bugs in the framework. They are the decisions the team must make consciously and document explicitly. The role of the principles is not to eliminate trade-offs but to ensure they are *visible*. A decision to ship without formal verification of a non-critical module is reasonable if the team documents the decision, scores the risk, and plans to revisit. A decision to skip security review to hit a deadline is a different kind of risk entirely.

### Weighting

Not every principle carries equal weight on every project. A healthcare application may treat Security and Correctness Verification as non-negotiable, with Economics as a secondary concern. A proof-of-concept for market validation may prioritize Economics and Operations (speed, scalability testing) while accepting known Maintainability debt.

The team defines the weighting at the start of the project, during Phase 2 (Analysis & Stack Selection), and revisits it at major phase transitions. AI can help model the implications of different weighting schemes, but the weighting itself is a human decision rooted in business context.

---

## The Role of AI in Enforcing Principles

In a traditional workflow, principles are enforced through process: code reviews, architecture review boards, compliance audits, QA gates. These processes depend on human attention, and human attention does not scale.

In an AI-centric workflow, principles can be embedded directly into the tools. This is one of the most significant advantages of the approach — and one of the reasons the toolkit matters so much.

### Prompts That Force Trade-Off Conversations

Every major decision prompt can include the six principles as required evaluation criteria. Instead of asking AI "What stack should we use?" the prompt becomes: "Evaluate these three stack options against our six Core Principles. For each principle, provide a score from 1–5 with justification. Flag any principle where the score is below 3."

This does not replace human judgment. It ensures that the judgment is informed by a structured evaluation rather than gut instinct or familiarity bias.

### Scorecards That AI Fills and Humans Review

At each phase checkpoint, AI generates a scorecard — a structured document that rates the current state of the project against each principle and its subcategories. The human reviews the scorecard, challenges the ratings, and signs off. Over time, the scorecards create a traceable history of how the project's health has evolved.

### Verification That Runs Continuously

Correctness checks, specification conformance tests, security scans, and performance benchmarks can run continuously in the CI/CD pipeline. AI does not get tired, does not skip steps under deadline pressure, and does not forget to check the edge case it found last week. The engineer designs the verification strategy; the tooling executes it relentlessly.

### Alerts on Principle Violations

When a commit drops test coverage below the threshold, when a dependency introduces a known vulnerability, when infrastructure costs exceed the forecast, when a specification conformance check fails — the toolkit can alert immediately. The engineer intervenes on exceptions rather than reviewing everything.

---

## Expanding the Framework

The six principles defined here are a starting point. They are deliberately broad enough to apply to most software projects, but every project will have specific concerns that merit additional subcategories or even new top-level principles.

Some candidates that may emerge as you work through the phases:

- **User Experience / Product Fit** — Does the thing we're building actually solve the problem it's supposed to solve? This may warrant its own principle or may be addressed through Economics (market fit) and Scoring (user satisfaction metrics).
- **Extensibility / Modularity** — The ability to add features without rewriting existing code. This overlaps with Maintainability and Operations but may deserve explicit tracking on projects where plug-in architectures or platform thinking are central.
- **Ethical Considerations** — When AI is involved in both building and using the system, questions of bias, fairness, transparency, and accountability may need explicit principle-level attention.

The framework is designed to grow. As you work through the phases described in the rest of this series, you will encounter decisions that don't fit neatly into the six principles. When that happens, the right response is not to force-fit the decision but to ask whether the framework needs to expand.

---

## What Comes Next

This article establishes the foundation. Every subsequent article in this series will reference these six principles explicitly. Each phase of the AI-centric development process will include:

- A description of what the phase accomplishes
- How AI tools support the phase
- How each Core Principle is applied and evaluated during the phase
- Scoring checkpoints and correctness verification relevant to the phase
- Expandable sections for deeper dives

The next article covers **Building Your Toolkit** — the prompts, skills, instruction sets, MCP servers, and custom AIs that form the building blocks of the AI-centric workflow. It also introduces a foundational concept: the AI-Centric Toolkit is not a replacement for your existing body of knowledge — it is an addendum to it. Every team already has accumulated resources: documents, technical references, articles, videos, books, internal wikis, architecture decision records, past postmortems, and industry standards. In the AI-centric workflow, these traditional resources are consolidated and made available for processing by AI, becoming part of the working context that informs every phase.

The toolkit is how the principles become operational. The principles tell you *what to care about*. The toolkit gives you the means to *act on it* — at every phase, at every decision point, at a pace that matches the speed of AI-assisted development.

Without the principles, the toolkit has no direction. Without the toolkit, the principles remain theory. Together, they become the daily practice of building software.

---

*This is a living document. The principles, subcategories, and examples will be expanded and refined as the series develops. Every part of this framework is open to iteration.*

*Next in the series: [Article 2 — Building Your Toolkit: Prompts, Skills, MCP Servers, and Custom AIs]*
