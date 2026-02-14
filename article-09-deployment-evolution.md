# Phase 7 — Deployment & Evolution

*Part 9 of The AI-Centric Software Development Playbook*

---

## Live and Continuing

Phase 6 cleared the system for deployment. The scoring gates passed. The audit findings were resolved or explicitly accepted. The deployment readiness report was signed off. Now the system goes live — and the framework shifts from building to sustaining.

Deployment is not an ending. It is a transition. Everything designed in Phase 4, built in Phase 5, and verified in Phase 6 now operates under real conditions: real users, real traffic, real failure modes, real adversaries. The monitoring hooks emit data. The observability instrumentation captures behavior. The operational interfaces designed months ago become the team's daily working surface.

But Phase 7 is more than deployment. It is also *evolution*. Software that does not change is software that is dying. Features are added, performance is tuned, security threats evolve, compliance requirements shift, infrastructure is upgraded, and technical debt is addressed. The SDD cycle does not stop at deployment — it continues driving the system's evolution, with the same discipline that built it.

This dual nature — operational stability and continuous evolution — defines Phase 7. The framework treats both as first-class concerns, powered by the same toolkit, measured by the same Core Principles, and driven by the same SDD methodology.

---

## What Deployment & Evolution Accomplishes

Phase 7 is an ongoing phase, not a one-time milestone. Its outputs are continuous.

**A deployed, observable system** — The system running in production with all monitoring, logging, tracing, and alerting active from day one. Not a silent deployment that requires weeks of instrumentation work before the team has visibility.

**Operational runbooks as AI orchestration scripts** — Runbooks structured not just for human operators but as prompts and instruction sets that AI can follow. Incident response, scaling operations, rollback procedures, and routine maintenance captured in a form that bridges documentation and automation.

**Continuous compliance** — Ongoing verification that the system continues to meet its compliance obligations, not just a one-time certification at deployment. Audit evidence is generated continuously, and compliance drift is detected automatically.

**Technical debt tracking and management** — A living inventory of technical debt, prioritized against the Core Principles, with AI-assisted analysis of when and how to address each item. Debt is managed proactively, not accumulated silently until it forces a crisis.

**Evolution artifacts** — New features, modules, and system changes developed through the SDD cycle with the same rigor applied during initial development. The toolkit and tool sets continue to be used, refined, and expanded.

**Continuously updated Principle Scorecard** — The scorecard does not freeze at deployment. It tracks the system's health in production: actual security posture, real maintainability indicators, actual costs vs. forecasts, operational metrics, scoring data from live systems, and correctness under production conditions.

---

## Deployment

Deployment in the AI-centric workflow is not a manual event. It is an automated, repeatable, tested process — because the infrastructure-as-code, container definitions, and CI/CD pipeline configurations built in Phase 5 and validated in Phase 6 make it so.

### Observable From Day One

The monitoring and observability hooks designed in Phase 4, implemented in Phase 5, and verified in Phase 6 activate immediately upon deployment. The team has visibility from the first request:

- Application metrics: latency, throughput, error rates, and business-specific metrics emitting to the monitoring stack
- Structured logging: every component producing logs in the format and at the verbosity specified in the architecture
- Distributed tracing: request flows visible across module boundaries, identifying bottlenecks and failure points
- Alerting: thresholds configured and active, with escalation paths defined in the operational runbooks

This is the payoff of designing observability early. A team that deferred monitoring until after deployment would spend the first weeks of production flying blind, reacting to user reports rather than proactive signals. A team that designed it into the architecture has full visibility from the start.

### Deployment Checklist

The deployment process follows a checklist — itself an artifact in the toolkit, structured as an instruction set that can be executed by AI with human oversight at critical checkpoints.

A deployment checklist typically covers:

- Pre-deployment verification: all scoring gates from Phase 6 confirmed, no new commits since audit, infrastructure provisioned and validated
- Deployment execution: container images built and pushed, database migrations run, configuration deployed, services started in dependency order
- Post-deployment verification: health checks passing, monitoring emitting data, smoke tests passing against production endpoints, performance within expected parameters
- Rollback readiness: rollback procedure confirmed, previous version available, rollback trigger criteria defined

The checklist is not a one-time document. It evolves with the system. Every deployment that encounters a problem adds a new check. Every incident that traces to a deployment gap adds a new verification step. AI assists in maintaining the checklist by analyzing incident reports and suggesting additions.

### Rollback as a First-Class Operation

Rollback is not an emergency procedure — it is a planned, tested, routine operation. The deployment process includes a defined rollback trigger (what conditions warrant rollback), a rollback procedure (how to revert to the previous version), and a rollback verification (how to confirm the rollback was successful).

In the AI-centric workflow, rollback procedures are structured as instruction sets that AI can execute with human authorization. "Service X is returning 500 errors at a rate exceeding 1% for more than 5 minutes. The rollback procedure is: revert container image to previous tag, verify health checks, confirm error rate returns to baseline, notify the team." AI monitors the triggers, proposes the rollback when criteria are met, and executes the procedure when the operator authorizes it.

---

## Runbooks as AI Orchestration Scripts

This is one of the most distinctive ideas in the AI-centric framework: **operational runbooks are not just documentation for humans — they are orchestration scripts for AI.**

### The Traditional Runbook Problem

Traditional runbooks are prose documents that describe how to handle operational situations: "If the database replication lag exceeds 30 seconds, check the primary node's CPU utilization. If it is above 80%, consider scaling the instance. If it is below 80%, check the network throughput between primary and replica..."

These runbooks are useful but fragile. They depend on the operator reading carefully, interpreting correctly, and executing each step without error under pressure. They go stale as the system changes. They are difficult to maintain because the people who know the procedures are the same people who are busy operating the system.

### Runbooks as Prompts

In the AI-centric workflow, runbooks are structured as prompts and instruction sets — building blocks in the toolkit that AI can read, interpret, and execute through MCP connections to the actual infrastructure.

A runbook-as-prompt for the database replication scenario:

- **Trigger condition:** Replication lag exceeds 30 seconds for 3 consecutive monitoring intervals
- **Step 1:** Query the monitoring system for primary node CPU utilization (via MCP connection to monitoring stack). If above 80%, proceed to Step 2a. If below 80%, proceed to Step 2b.
- **Step 2a:** Propose scaling the primary database instance. Present the current instance size, the next size up, the estimated cost difference, and the expected impact on replication lag. **Checkpoint: require human approval before scaling.**
- **Step 2b:** Query the monitoring system for network throughput between primary and replica. If throughput is below the baseline established in the benchmarks, propose network investigation. If throughput is normal, proceed to Step 3.
- **Step 3:** Check for long-running queries on the primary. If found, present the queries with their duration and resource impact. Propose cancellation of queries exceeding the defined threshold. **Checkpoint: require human approval before cancelling queries.**
- **Escalation:** If no root cause is identified after Steps 1–3, escalate to the on-call engineer with a summary of all diagnostic data gathered.

This structure gives AI enough specificity to execute the diagnostic steps, clear decision points to branch on, and explicit checkpoints where human judgment is required. It bridges the gap between a prose document that a human reads and an automation script that a machine executes.

### The Feedback Loop

Every incident that exercises a runbook is an opportunity to improve it. After the incident is resolved, the team reviews: Did the runbook cover this scenario? Were the steps correct? Were there steps missing? Were the checkpoints in the right places?

AI assists in this review by analyzing the incident timeline against the runbook steps, identifying where the actual resolution diverged from the documented procedure, and suggesting updates. The runbook evolves with each incident — becoming more accurate, more complete, and more effective as an orchestration script.

---

## Monitoring for Drift

Production systems drift. They drift from their specifications, from their intended behavior, from their design assumptions, and from their compliance obligations. Drift is inevitable. Detecting it early is the goal.

### Specification Drift

The system was verified against its specifications in Phase 6. But production introduces changes: configuration adjustments, data patterns the specification did not anticipate, dependency updates, infrastructure modifications. Over time, the system's actual behavior diverges from its documented behavior.

AI monitors for specification drift by periodically running specification conformance checks against the production system. When the system's behavior deviates from the API contracts, data schemas, or architectural constraints, the drift is flagged. The team then decides: update the implementation to match the specification, update the specification to match the reality, or document the deviation as an accepted exception.

### Scorecard Drift

The Principle Scorecard established in Phase 3 and updated through every subsequent phase represents the system's intended quality profile. In production, actual metrics may diverge from scored projections:

- Security posture may degrade as new vulnerabilities are discovered in dependencies
- Test coverage may decline as hot fixes bypass the normal testing process
- Infrastructure costs may exceed the model as usage patterns differ from projections
- Performance may degrade as data volumes grow beyond initial benchmarks

AI tracks these metrics continuously, comparing production actuals against the scorecard. When a principle score drops below its threshold, the monitoring system flags it before it becomes a crisis.

### Compliance Drift

Compliance is not a one-time certification. Regulatory requirements evolve. The system changes. Controls that were effective at deployment may become insufficient as the system grows or as requirements are updated.

Continuous compliance monitoring means: controls are verified on a schedule, audit evidence is generated automatically, and compliance drift is detected when a control stops functioning or a new requirement is introduced that existing controls do not cover. The compliance matrix from Phase 6 is a living document, updated as requirements and controls evolve.

---

## Technical Debt Management

Technical debt is inevitable. The question is whether it is managed or accumulated.

### AI-Assisted Debt Tracking

AI maintains a living inventory of technical debt by analyzing:

- Code quality metrics: complexity increases, coupling patterns, duplicated logic
- Test coverage: areas where coverage has declined or where new code lacks proportional testing
- Dependency health: outdated dependencies, dependencies with known vulnerabilities, dependencies approaching end of life
- Specification conformance: places where implementation has drifted from the specification without documentation
- Performance trends: endpoints or operations whose latency or resource consumption is trending upward

Each debt item is characterized: what it is, where it lives, what Core Principle it affects, what the consequence of leaving it unaddressed is, and what the estimated effort to resolve it is.

### Principled Prioritization

Not all technical debt is equal. A debt item that degrades Security is more urgent than one that affects code readability. A debt item that will compound into an operational failure is more urgent than one that creates developer friction.

The Core Principles provide the prioritization framework. Each debt item is evaluated against the principles it affects and the severity of its impact. AI proposes a prioritization; the team reviews and adjusts. The result is a managed debt backlog where items are addressed in order of principle-weighted impact, not in order of who noticed them most recently.

### Debt Payment Through the SDD Cycle

When a debt item is prioritized for resolution, it goes through the SDD cycle like any other work. The debt is specified (what needs to change and why), planned (broken into sections if necessary), detailed into a PRD, tasked, and implemented with the same testing, scoring, and verification applied to new development.

This prevents the common pattern of "quick fixes" that resolve one debt item while creating another. The SDD discipline ensures that debt resolution is held to the same standard as new development.

---

## Evolution

The system is live, monitored, and maintained. Now it needs to grow. New features are requested. New integrations are needed. New compliance requirements emerge. The technology landscape shifts.

### Evolution Uses the Same Framework

New features and modules are developed through the same SDD cycle used during initial development. The same Core Principles apply. The same toolkit is used — and refined based on what was learned during initial development.

The SDD cycle for a new feature:

- **Specify** — Interview prompts gather requirements for the new feature, using the existing system's documentation as context
- **Plan** — The feature is organized into sections or epics
- **Detail** — Each section is specified through a PRD, including how the new feature integrates with existing modules and which API contracts are affected
- **Task** — Tasks are generated from the PRD, including integration tests against existing modules
- **Implement** — Code is generated, tested, scored, and verified with the same rigor applied to the original implementation

Evolution is where the toolkit earns its long-term return. The tool sets built during initial development — specification tool sets, implementation tool sets, testing tool sets, scoring tool sets — are reused for every new feature. The consolidated knowledge base, now including the system's own architecture and documentation, provides rich context for AI-assisted development.

### Extensibility in Practice

The extensibility designed into the architecture in Phase 4 is now exercised. New modules plug in through the defined API contracts. Extension points accept new behavior without modifying existing code. The API versioning strategy handles backward compatibility as contracts evolve.

When a new feature does not fit the existing architecture cleanly, the tension is productive. It surfaces an architectural assumption that needs revision — and that revision goes through the design and architecture phases (Phase 3 and Phase 4) with the same scoring and simulation discipline applied during initial development. The framework does not assume the architecture is permanent. It assumes the architecture will evolve and provides the methodology for evolving it safely.

### Refactoring With AI

Refactoring in the AI-centric workflow is not a dreaded, risky activity. It is a routine operation supported by the verification framework:

- The specification defines what the system should do before and after the refactoring
- AI generates the refactored code from the specification
- Tests verify that behavior is preserved
- Specification conformance checks confirm the refactored code still matches the contracts
- The Principle Scorecard confirms that quality metrics are maintained or improved

The combination of precise specifications, comprehensive tests, and automated verification makes refactoring a low-risk activity. The specifications anchor what "correct" means, and the verification framework confirms that correctness is preserved through the change. This is a fundamental shift from traditional development, where refactoring risk comes largely from the absence of these anchors.

---

## Core Principles in Phase 7

Phase 7 is where the Core Principles operate in their steady-state mode — continuous monitoring, continuous enforcement, continuous improvement.

### Security

Security in Phase 7 means continuous monitoring for threats, vulnerabilities, and compliance drift. Dependency scans run on schedule. Security advisories for the technology stack are monitored. Penetration testing is repeated periodically, not just at initial deployment. Incident response runbooks are maintained and exercised. The threat model is updated as the system evolves and as the threat landscape changes.

### Maintainability

Maintainability in Phase 7 means documentation stays current, tests stay green, and technical debt stays managed. Every change to the system triggers documentation updates through the maintenance process defined in Phase 4. Test suites run on every deployment. Code quality metrics are tracked and debt items are prioritized. The queryability standard from Phase 6 applies continuously — if AI cannot answer questions about the current system from the current documentation, the documentation needs updating.

### Economics

Economics in Phase 7 means actual costs are tracked against the cost model from Phase 2. Infrastructure costs at real usage levels are compared to projections. AI tooling costs are monitored. When actuals diverge significantly from the model, the model is updated and optimization opportunities are identified. AI can analyze cost data and propose optimizations: right-sizing infrastructure, identifying underutilized resources, suggesting architectural changes that reduce operational cost.

### Operations

Operations in Phase 7 is the principle's home territory. Uptime, scaling behavior, incident response effectiveness, deployment frequency, rollback success rate, and mean time to recovery are all tracked. The monitoring and observability infrastructure designed throughout the framework now produces the data that evaluates operational health. Runbooks are exercised, refined, and expanded as the operational surface of the system evolves.

### Scoring & Metrics

Scoring in Phase 7 means the Principle Scorecard is a live dashboard, not a periodic report. Automated metrics feed into the scorecard continuously. Trends are visible. Regressions are flagged. The scoring framework established in Phase 2 and first applied in Phase 3 now operates as the ongoing health monitor for the system.

### Correctness Verification

Correctness Verification in Phase 7 means specification conformance checks run against the production system on a schedule. When new features or changes are deployed, conformance is re-verified. Drift detection catches places where the system's behavior has diverged from its specifications. Formal verification models for critical components are maintained alongside the code they verify — when the code changes, the models are updated and re-checked.

---

## Tool Sets for Phase 7

### Deployment Tool Set

**Purpose:** Execute and verify deployments through the automated deployment process.

**Building blocks:**
- The deployment checklist as an instruction set
- MCP connections to the CI/CD pipeline, container registry, infrastructure provisioning, and monitoring stack
- An action prompt that generates pre-deployment verification reports
- An instruction set for post-deployment smoke testing and monitoring verification
- An instruction set for rollback execution, with defined triggers and verification steps

### Operational Runbook Tool Set

**Purpose:** Maintain and execute operational runbooks as AI orchestration scripts.

**Building blocks:**
- Runbooks structured as instruction sets with trigger conditions, diagnostic steps, decision branches, human checkpoints, and escalation paths
- MCP connections to monitoring, logging, infrastructure, and alerting systems
- A skill that provides operational context: system topology, current deployment state, recent changes, baseline metrics
- An evaluation prompt that reviews runbook effectiveness after incidents and proposes updates
- References from the consolidated knowledge base: incident history, past runbook execution results

### Drift Detection Tool Set

**Purpose:** Monitor for specification, scorecard, and compliance drift.

**Building blocks:**
- The API contracts, module specifications, and compliance matrix as reference standards
- An instruction set for periodic specification conformance checking against the production system
- MCP connections to monitoring dashboards and compliance evidence collection systems
- An evaluation prompt that compares current production metrics against the Principle Scorecard thresholds and flags deviations
- An action prompt that generates drift reports with classification (specification drift, scorecard drift, compliance drift) and recommended response

### Technical Debt Tool Set

**Purpose:** Track, prioritize, and manage technical debt through the SDD cycle.

**Building blocks:**
- MCP connections to code quality analyzers, dependency scanners, test coverage tools, and performance monitors
- An action prompt that generates the technical debt inventory from analysis of current code quality, dependency health, test coverage, and conformance data
- An evaluation prompt that prioritizes debt items against the Core Principles — which items affect which principles, at what severity
- A skill that provides context for debt assessment: the system's architecture, its evolution trajectory, and its operational history
- An instruction set for running debt resolution through the SDD cycle with the same rigor as new development

### Evolution Tool Set

**Purpose:** Develop new features and system changes through the SDD cycle.

**Building blocks:**
- The same specification, planning, detail, task, and implementation tool sets used during initial development — reused and refined
- The system's current architecture, documentation, and API contracts as input resources
- An evaluation prompt that assesses the impact of proposed changes on existing modules, API contracts, and the Principle Scorecard
- A skill that provides context for evolution work: the system's current state, its operational metrics, its debt inventory, and its compliance obligations

---

## Common Pitfalls

### Observable on Paper, Blind in Practice

Designing observability throughout Phases 4–6 only pays off if the monitoring is actually reviewed and acted upon. A team that deploys with full instrumentation but does not establish the habit of reviewing dashboards, responding to alerts, and investigating anomalies has observability in theory but not in practice. Establish operational routines from day one: daily metric reviews, weekly trend analysis, and defined response procedures for alerts.

### Runbooks That Rot

Runbooks that are written once and never updated become dangerous — they describe a system that no longer exists, and following them during an incident can make things worse. The incident feedback loop must be real: every incident that exercises a runbook triggers a review, and every review produces updates or confirmations. AI assists by flagging runbooks that reference components, configurations, or procedures that have changed since the runbook was last updated.

### Debt Accumulation Through "Quick Fixes"

The pressure to ship quickly does not end at deployment. Production bug fixes, urgent feature requests, and operational patches all create pressure to bypass the SDD cycle. Every bypass is a potential debt item. The framework does not prohibit fast action — it requires that fast action be followed by proper integration: the change is specified, tested, scored, and verified after the immediate pressure is resolved. A "fix it now, clean it up later" pattern only works if "later" is scheduled and enforced.

### Evolution Without Architecture Review

Adding features to a deployed system without reviewing their architectural impact creates the same problems that Phase 4 was designed to prevent. New modules that do not conform to the API contract standards. Integrations that bypass the defined communication patterns. Extensions that violate the security architecture. Evolution must go through the design and architecture phases — abbreviated when the change is small, full-cycle when the change is significant — to maintain architectural integrity.

### Compliance as a One-Time Event

Passing the compliance verification in Phase 6 does not mean the system is permanently compliant. Compliance requirements change. The system changes. Controls degrade. Continuous compliance monitoring is not optional — it is the mechanism that ensures the system remains compliant as both the system and the regulatory landscape evolve.

---

## The Framework Continues

Phase 7 does not have a validation checkpoint in the same sense as earlier phases. There is no "next phase" to proceed to. Instead, Phase 7 operates continuously, with the Core Principles, the Principle Scorecard, and the SDD cycle providing ongoing structure.

The framework's phases are not a one-way pipeline that ends at deployment. They are a cycle:

- Phase 7 (Operations) reveals that a new feature is needed → the SDD cycle runs through Phases 1–6 for that feature
- Phase 7 (Drift detection) reveals an architectural assumption that no longer holds → Phase 3 (Design) and Phase 4 (Architecture) are revisited for the affected area
- Phase 7 (Compliance monitoring) reveals a new regulatory requirement → Phase 1 (Information Gathering) researches the requirement and the framework cycles through the relevant phases
- Phase 7 (Technical debt management) identifies a component that needs refactoring → the SDD cycle runs through the implementation and testing phases

The phases are a framework for organizing thinking and work, not a linear process with a beginning and an end. The toolkit, the tool sets, and the SDD methodology are assets that continue producing value for as long as the system is maintained and evolved.

---

## What Comes Next

This article completes the phase-by-phase walkthrough of the AI-Centric Software Development framework. From Information Gathering through Deployment & Evolution, the framework provides a structured, principle-driven, specification-first approach to building software with AI as the primary interface.

With the full framework now articulated, the series gains its **Introduction** — **The Manifesto**. Written last because it could only be written with the full weight of the framework behind it, the Introduction steps back from the practitioner's detail and makes the case: why small teams orchestrating AI tools will build the software that matters over the next eighteen to twenty-four months, why the fundamentals of computer science remain essential even as the interface changes, and why the time to build this capability is now. It is the front door to the series — the article a reader encounters first and the one that frames everything that follows.

---

*This is a living document. The tool sets, operational patterns, runbook structures, and examples will be expanded and refined as the series develops. Every part of this framework is open to iteration.*

*Previous: [Article 8 — Phase 6: Testing & Audit]*
*Introduction to the series: [The Manifesto — Small Teams, Big AI, New Paradigm]*
