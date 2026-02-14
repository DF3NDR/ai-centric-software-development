# Phase 5 — Implementation

*Part 7 of The AI-Centric Software Development Playbook*

---

## Where Discipline Pays Off

Phases 1 through 4 invested in gathering information, analyzing options, locking design direction, and specifying architecture at the module level. That investment was deliberate. The return arrives here.

Implementation in an AI-centric workflow is fundamentally different from traditional coding — not because AI writes code instead of humans, but because the relationship between specification and code changes. In a traditional workflow, specifications are aspirational. The code is what matters, and the specification is a reference that drifts from reality as implementation decisions are made. In the AI-centric workflow, specifications are authoritative. AI generates code *from* specifications, tests verify code *against* specifications, and correctness checking ensures specifications and code stay aligned throughout development.

This only works if the specifications are precise. A module specification from Phase 4 that defines exact interfaces, data models, security constraints, and performance requirements produces AI-generated code that is largely correct on first pass. A vague specification produces code that requires extensive human rework — and at that point, the AI has added overhead rather than leverage.

Phase 5 is where the quality of everything that came before becomes measurable. Good specifications produce good code quickly. Poor specifications produce the same friction that AI-centric development was supposed to eliminate.

---

## What Implementation Accomplishes

Phase 5 transforms the architectural blueprint from Phase 4 into working, tested, scored, and verified code. The outputs include:

**Working module implementations** — Code that conforms to the module specifications, passes the generated tests, satisfies the security constraints, and meets the performance benchmarks. Each module is implemented independently, building from its own specification and the shared architectural standards.

**Test suites** — Unit tests, integration tests, property-based tests, and contract tests generated alongside the code. Tests are not an afterthought — they are produced as part of the implementation cycle, driven by the specifications and the testing strategy from Phase 4.

**Monitoring and observability implementations** — The monitoring hooks, logging integrations, health check endpoints, and tracing instrumentation specified in the architecture are built during implementation, not deferred to a pre-deployment sprint.

**Infrastructure-as-code** — Deployment configurations, container definitions, CI/CD pipeline definitions, and environment configurations. These are code artifacts subject to the same versioning, testing, and review standards as application code.

**Continuous scoring data** — Automated metrics collected at every commit: test coverage, code complexity, security scan results, dependency audit status, performance benchmark results, and specification conformance check outcomes. This data feeds the Principle Scorecard and makes implementation health visible in real time.

**Updated Principle Scorecard** — The scorecard from Phase 4, continuously updated as implementation progresses. Principle scores that improve as code is written confirm that implementation is on track. Scores that degrade trigger immediate review.

---

## The SDD Cycle in Phase 5

Implementation uses the SDD cycle at the module level. Each module goes through its own cycle, with the module specification from Phase 4 as the starting input.

### Step 1: Specify — Confirm the Module Scope

Before generating code, the practitioner reviews the module specification with AI, confirming scope and identifying any ambiguities or gaps that need resolution. An interview prompt from the Implementation tool set structures this:

- Review the module specification. Are there any interface definitions that are ambiguous or incomplete?
- Are there dependencies on other modules that are not yet implemented? How will they be mocked or stubbed during development?
- Are there security constraints that require specific implementation patterns?
- What is the test coverage target for this module? What types of tests are required?
- Are there performance benchmarks specific to this module?

This step often surfaces specification gaps that were not visible during Phase 4. When gaps are found, the specification is updated before implementation begins — not patched during coding.

### Step 2: Plan — Break the Module into Implementation Sections

The module implementation is organized into sections — logical chunks of work that can be implemented, tested, and verified independently:

- Data models and schema migrations
- Core business logic
- API endpoint implementations
- Authentication and authorization enforcement
- Integration with other modules (via API contracts)
- Test suites (unit, integration, property-based, contract)
- Monitoring and observability instrumentation
- Infrastructure-as-code (deployment configuration, container definitions)

Each section becomes an epic in the implementation plan. The order matters — data models before business logic, business logic before API endpoints, core implementation before monitoring instrumentation. Dependencies between sections are made explicit.

### Step 3: Detail — Produce Implementation PRDs

Each section is taken through a detail prompt that produces an implementation PRD. This is where the SDD cycle provides its most distinctive value during implementation: the PRD bridges the gap between the architectural specification (what the module should do) and the task list (what the developer or AI should build).

An implementation PRD for the "Core business logic" section of a module might specify:

- The specific functions or methods to implement, with input/output types derived from the module specification
- The invariants that must hold (e.g., "account balance must never be negative after a transaction")
- The error handling strategy for each failure mode
- The logging and metrics to emit from each operation
- The test properties that should be verified (for property-based testing)
- Which formal verification targets apply to this section, if any
- The Core Principle requirements: security checks on every input, test coverage above threshold, performance within budget

### Step 4: Task — Generate the Task List

The PRD is broken into concrete, actionable tasks. Each task is specific enough for an AI implementation prompt to produce correct output:

- Implement the `create_transaction` function conforming to the interface definition in the module spec. Accept validated `TransactionRequest`, enforce the non-negative balance invariant, emit the `transaction.created` event, and return `TransactionResult`. Include error handling for insufficient funds, invalid account, and concurrent modification.
- Generate property-based tests for `create_transaction`: the balance after a successful transaction must equal the previous balance minus the amount; a failed transaction must not modify the balance; the function must be idempotent for duplicate transaction IDs.
- Implement the authorization middleware for the transactions API. Enforce the RBAC policy from the security architecture: `transaction.create` requires the `transactor` role, `transaction.read` requires `viewer` or `transactor`.
- Generate the OpenAPI specification conformance test for the `/transactions` endpoint. Verify all request/response shapes, status codes, and error formats match the API contract.

The task list is the final specification before AI generates code. Its precision directly determines the quality of the generated output.

### Step 5: Implement — Generate, Test, Score, Verify, Refine

This is the core implementation loop. For each task, the implementation tool set:

**Generates code** — An action prompt produces code from the task specification, using the module specification, shared architectural standards, and coding skills as context. The generated code is a first draft, not a final product.

**Runs tests** — The generated tests (and any existing tests) are executed immediately. Failures are fed back to AI for correction. This is not a separate testing phase — it is an integral part of the generation loop.

**Scores against principles** — Automated metrics are collected: test coverage, code complexity, security scan results, linting, and specification conformance. These scores are compared against the thresholds established in earlier phases.

**Verifies correctness** — Specification conformance checks verify that the generated code matches the API contracts and module specification. For critical components, formal verification or property-based testing provides deeper assurance. AI-vs-AI review offers an independent audit.

**Refines** — When tests fail, scores fall below thresholds, or verification identifies issues, the code is refined. AI generates corrections; the practitioner reviews significant changes. The loop continues until all checks pass.

This loop — generate, test, score, verify, refine — is the implementation feedback cycle. It runs for every task, for every module. The speed of the cycle is one of the primary advantages of AI-centric development: a cycle that might take a human developer hours of coding, testing, and debugging can complete in minutes when AI handles the generation and the verification framework is automated.

---

## The Implementation Feedback Loop

The generate-test-score-verify-refine cycle is the tactical loop. Above it sits a strategic feedback loop that operates at the module and project level.

### Module-Level Feedback

As each module section is implemented, the module's aggregate scores are updated. If implementing the business logic section drops test coverage below the threshold (because new code was added without proportional test coverage), the scoring system flags it before the next section begins. If a security scan on the authorization middleware reveals a vulnerability pattern, it is addressed before the integration section is started.

Module-level feedback prevents the accumulation of problems across sections. Each section is validated before the next begins — not as a bureaucratic gate, but as an automated check that keeps implementation quality stable.

### Project-Level Feedback

As modules are completed, the project-level Principle Scorecard is updated. Cross-module integration tests run. Contract tests verify that Module A's expectations of Module B match Module B's actual implementation. The project's aggregate scores across all six principles are visible at all times.

Project-level feedback catches systemic issues that module-level checks might miss. A pattern of declining test coverage across multiple modules suggests a testing strategy problem, not a module-specific issue. A recurring security finding across modules suggests an architectural gap.

### Feedback Into Earlier Phases

Sometimes implementation reveals problems that trace back to earlier phases. A module specification that seemed complete in Phase 4 may prove ambiguous when AI tries to generate code from it. A data architecture decision from Phase 3 may create performance problems that were not predicted by simulations. A cost model from Phase 2 may prove too optimistic when actual development effort is measured.

The SDD cycle accommodates this. When implementation feedback reveals a specification problem, the specification is updated (cycling back through the module-level SDD). When it reveals an architectural problem, the architecture is revised (cycling back to Phase 4). When it reveals an analytical problem, the analysis is revisited (cycling back to Phase 2 or 3). The phases are not a one-way pipeline — they are connected by feedback loops that maintain consistency between specification and reality.

---

## Correctness Verification in Practice

Phase 5 is where Correctness Verification moves from architectural aspiration to running code. The verification strategies designed in earlier phases are now implemented and executed.

### Specification Conformance

Every module is continuously checked against its specification. API endpoints are tested against their OpenAPI contracts. Data models are validated against their schema definitions. Module interfaces are verified against their documented contracts. These checks run automatically — in the CI/CD pipeline, on every commit, with every AI-generated code update.

Specification conformance catches drift. In traditional development, specifications and code diverge over time as implementation decisions override design intentions. In the AI-centric workflow, conformance checking keeps them aligned. When they diverge, the system flags it — and the team decides whether the code should be corrected or the specification should be updated.

### Formal Verification

For critical components — financial calculations, authentication logic, state machines, concurrency controls — AI can generate formal verification models that prove correctness properties mathematically. This is the most rigorous level of correctness checking and the clearest example of the human-AI collaboration pattern in this framework.

The process: AI generates a formal model (in TLA+, Alloy, or a similar specification language) that represents the component's behavior. The model includes safety properties ("the balance must never be negative") and liveness properties ("every pending transaction must eventually resolve"). AI then runs the model checker to verify these properties hold.

The engineer's role: review the model itself. Does it accurately represent the real component? Are the properties the right ones to verify? Are the boundary conditions correct? The AI did the formal work. The engineer verifies that the formal work is about the right thing. This is judgment at a higher level of abstraction — and it is the level where human expertise is most valuable.

Formal verification is not appropriate for every component. It is most valuable where correctness failures have severe consequences (financial loss, data corruption, security breach) and where the component's behavior can be specified precisely. The team decides during Phase 4's module specification which components warrant formal verification.

### AI-vs-AI Review

A separate AI process — ideally using a different model, a different prompt configuration, or a different review framework — audits generated code against the specification. The reviewing AI does not see the generating AI's reasoning or process. It operates independently, looking for:

- Logic errors that tests might not catch
- Security vulnerabilities: injection points, authentication bypasses, authorization gaps
- Specification drift: behavior that diverges from the documented contract
- Performance concerns: inefficient algorithms, unnecessary allocations, blocking operations in async contexts
- Maintainability issues: unclear naming, missing error handling, inadequate logging

When the reviewing AI and the generating AI disagree, the engineer arbitrates. The disagreement itself is valuable — it surfaces issues that a single AI perspective might miss.

### Property-Based Testing

Property-based tests define properties that should hold for all inputs, then test those properties against randomly generated inputs. They complement traditional example-based unit tests by exploring the input space more broadly.

AI is effective at both defining properties (derived from the specification) and generating the test harness. The practitioner reviews the properties to ensure they capture the right invariants. "For any valid input, the output length should equal the input length" is a property. "The function returns the correct result for the three examples in the specification" is an example-based test. Both are useful. Properties catch classes of bugs that examples miss.

---

## Version Control in the AI-Centric Workflow

Version control in AI-centric development serves the same fundamental purposes as in traditional development — tracking changes, enabling collaboration, supporting rollback — but with additional requirements driven by the AI workflow.

### Semantic Commits

Commits are structured so that AI can track, summarize, and reason about the change history. Each commit includes:

- A clear description of what changed and why
- References to the relevant task from the SDD task list
- References to the module specification section that the change implements
- Any principle score changes the commit introduces

This structure allows AI to answer questions like "What changes were made to the authentication module since the last security review?" or "Which commits affected the transaction processing logic?" without parsing diffs.

### AI-Comprehensible History

The commit history is an input resource for AI in later phases. During testing (Phase 6), AI can trace a failing test back through the commits that affected the relevant code. During deployment (Phase 7), AI can summarize what changed between releases. During operations, AI can correlate a production issue with the commits deployed in the most recent release.

This requires discipline in commit structure — not squashing everything into "fixed stuff" or generating meaningless AI commit messages. Each commit should be a meaningful, traceable unit of change.

---

## Core Principles in Phase 5

Implementation is where principles become measurable reality rather than scored projections.

### Security

Security in Phase 5 means continuous scanning on every commit: dependency vulnerability audits, static analysis for common vulnerability patterns, secrets detection, and security-focused code review (human and AI-vs-AI). Security is not a gate at the end of implementation — it is a continuous check that runs with every code change.

### Maintainability

Maintainability in Phase 5 means test coverage scoring, documentation generation (AI generates inline documentation, API docs, and module-level README files alongside code), and code quality metrics (complexity, coupling, cohesion). These metrics are tracked at the module level and the project level, with thresholds that trigger review when exceeded.

### Economics

Economics in Phase 5 means tracking actual development effort against the estimates from Phase 2 and Phase 4. When a module takes significantly longer than estimated, it is a signal — either the estimate was wrong (update the cost model) or the implementation is more complex than the architecture anticipated (investigate whether the architecture needs revision). AI can flag effort deviations automatically.

### Operations

Operations in Phase 5 means building the monitoring and observability interfaces alongside the features — not after. Health check endpoints, structured logging, metrics emission, distributed tracing instrumentation, and alerting hook points are implemented as first-class concerns, tested like any other feature, and verified against the observability specifications from Phase 4.

### Scoring & Metrics

This principle is fully operational in Phase 5. Automated metrics are collected at every commit: test coverage, code complexity, security scan results, specification conformance, performance benchmark results. These feed the continuously updated Principle Scorecard. Scoring is not a periodic review — it is a real-time signal.

### Correctness Verification

Correctness Verification is fully operational: specification conformance checking on every build, property-based testing for invariant-heavy components, formal verification for critical paths, and AI-vs-AI review as an independent audit layer. The verification strategy defined in Phase 4 is implemented and running.

---

## Tool Sets for Phase 5

### Code Generation Tool Set

**Purpose:** Generate module implementations from specifications and task lists.

**Building blocks:**
- The module specification, API contracts, and implementation PRD as input resources
- A skill that provides coding standards, security patterns, error handling conventions, and logging requirements for the project
- An action prompt that generates code from a specific task, conforming to the specification and the shared architectural standards
- MCP connections to the testing framework (run tests immediately after generation) and version control (commit with semantic structure)
- An evaluation prompt that scores generated code against the specification before human review

### Testing Tool Set

**Purpose:** Generate and execute test suites alongside implementation.

**Building blocks:**
- The module specification and API contracts as input resources (tests are derived from specs, not from implementation)
- An action prompt that generates unit tests, integration tests, and property-based tests from the specification
- An action prompt that generates contract tests from API specifications
- MCP connections to the test runner and coverage reporting tools
- A skill that provides testing patterns: property definition, edge case identification, boundary condition coverage
- An evaluation prompt that assesses test quality — "Do these tests verify the specification, or do they just verify the implementation?"

### Correctness Verification Tool Set

**Purpose:** Run specification conformance checks, formal verification, and AI-vs-AI review.

**Building blocks:**
- The module specification, API contracts, and data schemas as the reference specifications
- An instruction set for specification conformance checking: compare implemented behavior against documented contracts, flag deviations
- An action prompt for formal verification: generate formal models for designated critical components, define safety and liveness properties, run model checking
- A separate AI configuration (different model or different prompt) for AI-vs-AI review, operating independently from the generating AI
- MCP connections to static analysis tools, type checkers, and linting frameworks
- An evaluation prompt that synthesizes verification results into a module-level correctness report

### Scoring & Monitoring Tool Set

**Purpose:** Collect and track principle-based metrics continuously during implementation.

**Building blocks:**
- MCP connections to: test coverage tools, code complexity analyzers, security scanners, dependency audit tools, performance benchmarking frameworks
- An instruction set that defines what metrics to collect, at what frequency, and what thresholds trigger alerts
- An action prompt that generates the updated Principle Scorecard from current metrics
- An evaluation prompt that compares current scores against the Phase 4 baseline and flags regressions
- An action prompt that generates a human-readable implementation health report summarizing scores, trends, and items requiring attention

---

## Common Pitfalls

### Generating Without Specifying Tasks

It is tempting to hand AI a module specification and say "implement this." The results are predictably poor. The SDD cycle exists to break implementation into specific, well-defined tasks before generation begins. Each task should be small enough that AI can produce correct output and specific enough that correctness can be verified. Skip the Detail and Task steps, and implementation becomes a negotiation between the practitioner and AI rather than a disciplined generation-verification loop.

### Ignoring Score Regressions

When a commit drops test coverage, introduces a complexity spike, or triggers a new security finding, the temptation is to address it later. Score regressions compound. A 2% coverage drop per module across ten modules is a 20% coverage loss at the project level. The scoring system exists to catch regressions early. Ignoring its signals undermines the entire framework.

### Treating AI Output as Final

AI-generated code is a first draft. It is often very good — especially when the specification is precise — but it is not infallible. The verification framework (tests, specification conformance, formal verification, AI-vs-AI review) exists because AI output requires validation. Treating generated code as final, skipping review, or merging without running checks introduces exactly the kind of risk the framework is designed to prevent.

### Deferring Monitoring Implementation

The monitoring and observability interfaces specified in Phase 4 must be built during implementation, not added before deployment. Deferring them creates a crunch at deployment time and usually results in incomplete observability. Build monitoring hooks alongside the features they observe. Test them. Verify they emit the metrics specified in the architecture.

### Losing Traceability

Every piece of generated code should trace back to a task, which traces to a PRD, which traces to a module specification, which traces to the architecture and design decisions. If this traceability is lost — through unstructured commits, ad hoc changes, or bypassing the SDD cycle — the verification framework cannot confirm that the implementation matches the specification. Traceability is the thread that connects intent to reality.

---

## Validation Checkpoint

Before moving to Phase 6, the team validates that implementation is complete and quality is sufficient.

- **Module completeness:** Is every module implemented against its specification? Are any specification sections unimplemented or partially implemented?
- **Test coverage:** Does every module meet or exceed its coverage target? Are unit, integration, property-based, and contract tests all in place?
- **Security:** Do all security scans pass? Are all dependency vulnerabilities resolved or documented as accepted risks? Does the authorization enforcement match the security architecture?
- **Specification conformance:** Does every module conform to its API contract, data schema, and interface specification? Are conformance checks automated and green?
- **Formal verification:** For components designated for formal verification, are the models complete and verified? Has the engineer reviewed the models for correctness?
- **Monitoring:** Are all monitoring hooks, logging integrations, health checks, and tracing instrumentation implemented and tested?
- **Infrastructure-as-code:** Are deployment configurations, container definitions, and CI/CD pipeline definitions complete and tested?
- **Principle Scorecard:** Are all six principle scores at or above the Phase 4 baseline? Are any regressions documented and accepted?
- **Traceability:** Can every implementation artifact be traced back to a specification? Are semantic commits complete and linked to tasks?

If gaps exist, the SDD cycle iterates at the module level. Phase 6 (Testing & Audit) will apply additional scrutiny, but it should not be used to compensate for incomplete implementation. Implementation should be solid before audit begins.

---

## What Comes Next

Phase 5 transforms architecture into working, tested, scored, and verified code. The implementation feedback loop — generate, test, score, verify, refine — runs for every task in every module, producing code that is traceable to specifications and measurable against the Core Principles.

Phase 6 applies a different lens. The next article covers **Testing & Audit** — where the team steps back from implementation and subjects the complete system to independent testing, security audits, performance validation, compliance verification, and documentation review. This is the phase where the Core Principles become pass/fail gates, where formal verification models from Phase 5 receive their engineer review, and where the system must demonstrate it meets the standards it was designed to satisfy.

---

*This is a living document. The tool sets, implementation patterns, and examples will be expanded and refined as the series develops. Every part of this framework is open to iteration.*

*Previous: [Article 6 — Phase 4: Architecture & Modular Design]*
*Next in the series: [Article 8 — Phase 6: Testing & Audit]*
