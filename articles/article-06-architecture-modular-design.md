# Phase 4 — Architecture & Modular Design

*Part 6 of The AI-Centric Software Development Playbook*

---

## The Blueprint

Phase 3 locked in a validated technical direction — the system's structure, interaction patterns, data architecture, deployment model, security model, and observability strategy. Those are strategic commitments. Phase 4 transforms them into a concrete blueprint that implementation can build from.

This is where the system becomes real on paper before it becomes real in code. Module boundaries are drawn. API contracts are specified. Security boundaries are defined at the component level. Data schemas take shape. The documentation strategy is established. Governance — who owns what, who reviews what, who approves changes to what — is formalized.

Architecture is the most consequential design activity in the entire process. Every decision made here reverberates through implementation, testing, deployment, and operations. A well-drawn module boundary makes independent development, testing, and deployment possible. A poorly drawn one creates coupling that fights the team at every turn. An API contract that is precise and complete enables parallel development and AI-assisted code generation. One that is vague forces developers to make assumptions that diverge.

In the AI-centric workflow, architecture carries an additional responsibility: **the architecture must be specified precisely enough that AI can build from it.** Vague architecture produces vague AI output. A module described as "handles user stuff" will produce worse AI-generated code than one specified with explicit responsibilities, interfaces, data models, error handling contracts, and security constraints. The quality of the architecture directly determines the quality of AI-assisted implementation.

---

## What Architecture & Modular Design Accomplishes

Phase 4 produces the comprehensive architectural specification — the set of artifacts that implementation (Phase 5) will build from. These artifacts are both human-readable documentation and machine-parseable specifications.

**Module Specification Documents** — For each module in the system, a detailed specification covering: purpose and responsibilities, public interfaces, data models, dependencies on other modules, security constraints, performance requirements, test strategy, and monitoring hooks. Each module specification is a self-contained document that can be handed to an implementation tool set as input context.

**API Specifications** — Formal, machine-readable API contracts for every boundary in the system. OpenAPI specifications for REST APIs, protobuf definitions for gRPC services, GraphQL schemas where applicable, and event schema definitions for asynchronous communication. These are not documentation artifacts — they are executable contracts that drive code generation, contract testing, and specification conformance checking.

**Security Architecture** — The detailed security design, building on the initial threat model from Phase 2 and the security model from Phase 3. Authentication flows, authorization policies, encryption strategies (at rest and in transit), audit logging specifications, and trust boundary enforcement mechanisms for every module boundary.

**Data Architecture** — Schema definitions, data flow diagrams at the component level, consistency and transaction strategies, migration plans, and data classification mappings. Where Phase 3 chose the storage model, Phase 4 specifies exactly what is stored, where, how it flows between components, and what integrity constraints apply.

**Documentation Strategy** — The plan for how documentation will be created, maintained, and consumed throughout the system's lifecycle. This is not a style guide — it is an architectural decision about what kinds of documentation exist, where they live, who maintains them, and how AI tools consume and update them.

**Governance Model** — Module ownership assignments, review gate definitions, change approval workflows, and escalation paths. In a small team, governance must be explicit precisely because there are few people — ambiguity about ownership creates both gaps and conflicts.

**Updated Principle Scorecard** — The scorecard from Phase 3, updated with scores reflecting the detailed architecture. Architectural decisions that improve or degrade principle scores are documented, and any regression from Phase 3 baseline triggers review.

---

## The SDD Cycle in Phase 4

Phase 4 is typically the most intensive application of the SDD cycle, because each module goes through its own Specify-Plan-Detail-Task-Implement sequence. The phase-level SDD cycle organizes the overall architectural work. Module-level SDD cycles produce individual module specifications.

### Phase-Level SDD

**Specify** — Define the scope of the architectural work. What modules need to be specified? What are the boundaries between them? What shared architectural patterns apply across all modules? What architectural decisions remain open from Phase 3?

An interview prompt from the Architecture tool set guides this:

- Based on the design direction, what are the natural module boundaries?
- Which modules are core to the system's value proposition and which are supporting infrastructure?
- What shared concerns (authentication, logging, error handling, configuration) should be standardized across modules?
- What are the inter-module communication patterns?
- What governance model fits the team size and structure?

**Plan** — Organize the architectural work into sections. Typically, this breaks down into:

- Shared architectural patterns and standards (cross-cutting)
- Module specifications (one per module)
- API contract definitions (one per boundary)
- Security architecture (cross-cutting)
- Data architecture (cross-cutting with module-specific elements)
- Documentation strategy
- Governance model

Each section becomes an epic in the architectural plan.

**Detail, Task, Implement** — Each section goes through its own SDD cycle, producing the specific artifacts described above. The cross-cutting sections (shared patterns, security, data, documentation, governance) are typically completed first, since they establish constraints that individual module specifications must satisfy.

### Module-Level SDD

Each module specification is produced through its own SDD cycle:

**Specify** — An interview prompt defines the module's scope: what it does, what it does not do, what it depends on, what depends on it, what data it owns.

**Plan** — The module specification is organized into sections: purpose, interfaces, data model, security, performance, testing, monitoring.

**Detail** — Each section is specified through a PRD prompt that produces detailed requirements. The API interfaces section, for example, produces the input and output schemas for every operation the module exposes.

**Task** — The PRD sections are broken into specific tasks: "Define the OpenAPI spec for the user authentication endpoints," "Specify the database schema for the session store," "Define the authorization policy for each endpoint."

**Implement** — The implementation tool set generates the artifacts: OpenAPI specs, schema definitions, authorization policies, test strategy documents, monitoring hook specifications.

This nested SDD structure — phase-level cycles containing module-level cycles — is what makes Phase 4 manageable despite its complexity. Each module is specified independently, with shared architectural constraints providing consistency.

---

## API-First Design

In the AI-centric workflow, API-first design is not merely a best practice — it is an enabling architecture. Formal API specifications are the contracts that make AI-assisted development, parallel development, contract testing, and specification conformance checking possible.

### What API-First Means in Practice

**Specifications before code.** Every API boundary gets a formal specification (OpenAPI, protobuf, GraphQL schema, or event schema) before any implementation code is written. The specification is the authoritative definition of the contract. Implementation must conform to it, not the other way around.

**Machine-readable contracts.** API specifications are not prose descriptions — they are machine-readable documents that can be consumed by code generators, test generators, documentation generators, and specification conformance checkers. An OpenAPI spec that defines a 404 response for a missing resource is a testable contract, not a suggestion.

**Auto-generated artifacts.** From the API specifications, the toolkit can auto-generate: server stubs, client SDKs, request/response validation, API documentation, contract tests, and mock servers. This is one of the highest-leverage applications of AI in the entire framework — a well-defined spec can produce a substantial portion of the implementation scaffolding.

**Contract testing between modules.** When Module A calls Module B's API, the contract test verifies that Module B actually implements the contract that Module A depends on. Contract tests are generated from the API specifications and run continuously. They catch integration breaks before they reach production.

### API Specifications as AI Context

When implementation begins in Phase 5, the API specification for each module becomes a primary input resource for the implementation tool set. AI generates code that conforms to the spec, tests that validate the spec, and documentation that describes the spec. The precision of the specification directly determines the quality of the AI-generated output.

A vague specification produces code that requires extensive human review and correction. A precise specification produces code that is largely correct on first generation and can be verified automatically against the spec. This is the architectural payoff of Phase 4's discipline: time invested in precise specifications is returned many times over during implementation.

---

## Security Architecture

The security architecture elaborates the security model from Phase 3 and the threat model from Phase 2 into component-level security design.

### Zero-Trust at Every Boundary

Zero-trust means no component trusts any other component by default. Every inter-module call is authenticated and authorized. Every data access is checked against the authorization policy. Every trust boundary has explicit security controls.

In architectural terms, this means:

- **Authentication** at every module boundary — not just at the system perimeter. How modules authenticate to each other (mTLS, JWT, API keys) is specified for each boundary.
- **Authorization** policies defined per-endpoint, per-operation. The authorization model (RBAC, ABAC, capability-based) is chosen and the policies are specified as part of the module specification.
- **Encryption** strategy defined for data at rest and in transit. Which data stores are encrypted, what key management strategy is used, and what encryption is applied to inter-module communication.
- **Audit logging** specification for every security-relevant operation. What is logged, where it is stored, what retention policies apply, and how it connects to the monitoring and alerting strategy.

### Least Privilege by Default

Every module, every service account, every human operator gets the minimum permissions needed for their function. Permissions are granted explicitly, not inherited by default. The architecture specifies the permission model for each module — what resources it can access, what operations it can perform, and what it is explicitly prohibited from doing.

### Security as Architectural Input

The threat model from Phase 2, updated through Phase 3's design analysis, is an input to every module specification. Each module's security section addresses: what threats from the threat model apply to this module, what controls mitigate those threats, and what residual risks remain.

---

## Documentation Strategy

In the AI-centric workflow, documentation serves three audiences: humans reading it now, humans reading it months or years from now, and AI consuming it as context for tool sets in every subsequent phase. The documentation strategy established in Phase 4 determines how well all three audiences are served.

### Documentation as Architecture

The documentation strategy is not an afterthought — it is an architectural decision. Phase 4 specifies:

**What documentation exists** — Architecture decision records, module specifications, API specifications, data dictionaries, security architecture documents, operational runbooks, onboarding guides. Each type is defined with its purpose, audience, format, and maintenance cadence.

**Where documentation lives** — Co-located with code (inline comments, README files), in a documentation platform (wiki, docs-as-code), or in the consolidated knowledge base. The location strategy determines discoverability and maintenance.

**How documentation is maintained** — Who is responsible for keeping each document current? What triggers an update? How is staleness detected? In the AI-centric workflow, AI can assist with maintenance — flagging documentation that contradicts the current codebase, generating updates when APIs change, and identifying gaps. But the strategy must define when and how this happens.

**How AI consumes documentation** — Documentation that AI will use as context for tool sets should be structured for machine consumption: consistent formatting, structured metadata, explicit cross-references, and machine-parseable formats. This does not make documentation less readable for humans — well-structured documentation is better for both audiences.

### Documentation Starts Here

Phase 4 is where the documentation strategy moves from plan to practice. The module specifications, API specs, security architecture, and data architecture documents produced in this phase are the first substantial documentation artifacts. They set the standard for everything that follows.

If these documents are well-structured, precise, and maintained, they create a momentum that carries through implementation and into operations. If they are vague, inconsistent, or immediately abandoned, the documentation strategy fails regardless of how well it was planned.

---

## Governance Model

In a small team, governance might seem unnecessary — everyone knows what everyone else is doing. But governance is precisely about the moments when that assumption breaks down: when someone is out, when the team grows, when a critical module needs changes, when a decision needs to be reversed.

### Module Ownership

Every module has a designated owner. The owner is responsible for: the module's specification, its implementation quality, its test coverage, its documentation currency, and approving changes that affect its public interfaces. In a three-person team, one person might own multiple modules. The ownership is explicit regardless of team size.

### Review Gates

Phase 4 defines what changes require review and by whom:

- Changes to API contracts require review by the owners of all modules that depend on the changed API
- Changes to security-related code require review by the security-responsible team member (or a security-focused AI review as a supplement)
- Changes that affect the data schema require review by the data architecture owner
- Changes that affect deployment configuration require review by the operations-responsible team member

### Decision Authority

When there is disagreement about a design or implementation choice, who decides? The governance model defines escalation paths and decision authority per domain. In a small team, this is usually simple — but it must be explicit. "We'll figure it out when it comes up" is not a governance model.

---

## Designing for Extensibility

A well-architected system is one that can grow without being rewritten. Phase 4 designs for extensibility by establishing the patterns through which new capabilities are added.

**Module addition via APIs** — New modules plug into the system through the same API contracts that existing modules use. The architecture defines how new modules are registered, how they discover and communicate with existing modules, and what standards they must conform to.

**Extension points** — Where the system is expected to grow, explicit extension points are designed: plugin interfaces, hook systems, event subscriptions, or configuration-driven behavior. These are specified in the architecture, not invented during implementation.

**Backward compatibility** — API versioning strategy, schema migration patterns, and deprecation policies are defined so that existing modules and external consumers are not broken when the system evolves.

Extensibility is a Maintainability concern, but it also affects Economics (how much does it cost to add a feature?) and Operations (can new modules be deployed without disrupting existing ones?). The architecture should make extension the default path, not the exception.

---

## Core Principles in Phase 4

Phase 4 is where the Core Principles produce their most tangible architectural benefits. The architecture itself should make the principles *easier* to satisfy in implementation.

### Security

Security in Phase 4 means specifying zero-trust enforcement, least privilege policies, encryption strategies, and audit logging at the component level. Every module specification includes a security section. Every API boundary has authentication and authorization defined. The security architecture document connects every control back to the threat model.

### Maintainability

Maintainability in Phase 4 means drawing module boundaries that support independent testing and deployment, establishing a documentation strategy that serves both humans and AI, and designing for extensibility. The architecture is evaluated: can a new team member understand this module from its specification? Can AI generate implementation from it?

### Economics

Economics in Phase 4 means validating that the architecture fits the cost model. Complex architectures cost more to build and operate. Phase 4 estimates the implementation effort per module and the operational overhead of the architectural patterns. If the architecture exceeds the cost model, either the architecture is simplified or the cost model is revised with explicit rationale.

### Operations

Operations in Phase 4 means specifying monitoring hooks, logging standards, health check endpoints, deployment configurations, and scaling parameters for every module. The observability strategy from Phase 3 becomes concrete specifications. Operational concerns are embedded in the architecture, not deferred to a pre-launch checklist.

### Scoring & Metrics

The Principle Scorecard is updated with scores reflecting the detailed architecture. Each module specification receives its own sub-scores. The aggregate scores are compared against the Phase 3 baseline. Improvements are documented. Regressions are reviewed and either corrected or explicitly accepted.

### Correctness Verification

Correctness Verification in Phase 4 means designing for verifiability. API contracts enable specification conformance testing. Module boundaries enable independent formal verification. Data integrity constraints enable automated correctness checking. The architecture should make it *structurally possible* to verify correctness at the component level — if the architecture makes verification difficult, it is architecturally deficient regardless of how well it performs.

---

## Tool Sets for Phase 4

### Module Specification Tool Set

**Purpose:** Produce detailed specifications for each module through the module-level SDD cycle.

**Building blocks:**
- An interview prompt that walks the practitioner through defining the module's scope, responsibilities, interfaces, data, security constraints, and performance requirements
- The Design Direction Document and shared architectural standards as input resources
- A skill that frames the AI as a module designer, enforcing consistency with shared patterns and completeness across specification sections
- An action prompt that generates the module specification document from the interview output and PRD
- An evaluation prompt that reviews the specification against the Core Principles — coverage, precision, and fitness for AI-assisted implementation

### API Contract Tool Set

**Purpose:** Produce formal, machine-readable API specifications for every boundary.

**Building blocks:**
- An action prompt that generates OpenAPI specs (or protobuf definitions, or event schemas) from module specifications
- The module specifications and data architecture as input resources
- A skill that enforces API design standards: consistent naming, standard error responses, pagination patterns, versioning strategy
- An evaluation prompt that reviews generated specs for completeness, consistency, and adherence to the security architecture
- A correctness verification instruction set that cross-references API specs against module specifications and data schemas for consistency

### Security Architecture Tool Set

**Purpose:** Produce the detailed security architecture, connecting threat model findings to component-level controls.

**Building blocks:**
- The threat model from Phase 2, the security model from Phase 3, and the module specifications as input resources
- A skill that frames the AI as a security architect with knowledge of zero-trust patterns, least privilege design, and compliance mapping
- An action prompt that generates the security architecture document: authentication flows, authorization policies, encryption strategy, audit logging specification
- An evaluation prompt that reviews the security architecture against the threat model — "Is every identified threat addressed by a control? Are there gaps?"
- References from the consolidated knowledge base: compliance control descriptions, security architecture patterns, past project security designs

### Documentation Strategy Tool Set

**Purpose:** Define and implement the documentation strategy for the project lifecycle.

**Building blocks:**
- An interview prompt that walks the practitioner through documentation needs: what types, where they live, who maintains them, how AI consumes them
- A skill that provides documentation strategy patterns and best practices for AI-parseable documentation
- An action prompt that generates the documentation strategy document and initial templates
- An evaluation prompt that assesses whether the strategy covers all six Core Principles and serves both human and AI audiences

### Architecture Review Tool Set

**Purpose:** Validate the complete architecture against the Core Principles and Phase 3 baseline.

**Building blocks:**
- All Phase 4 artifacts as input resources
- The Phase 3 Principle Scorecard as the baseline
- An evaluation prompt that scores the complete architecture against all six principles, comparing to the Phase 3 baseline and flagging regressions
- A correctness verification instruction set that checks cross-artifact consistency: do API specs match module specifications? Does the security architecture cover all module boundaries? Does the data architecture support all module data requirements?
- An action prompt that generates the updated Principle Scorecard with detailed architectural scores

---

## Common Pitfalls

### Vague Module Specifications

A module specification that describes responsibilities in general terms rather than specific interfaces, data models, and contracts will produce vague AI-generated code in Phase 5. The test for specification quality is: can an AI implementation tool set produce a working module from this specification alone? If the answer is "only with significant human guidance," the specification needs more detail.

### Skipping API Formalization

Informal API contracts — described in prose rather than in OpenAPI specs or equivalent formal definitions — eliminate the possibility of auto-generated stubs, contract testing, and specification conformance checking. The investment in formal API specifications pays for itself many times over during implementation.

### Security as a Separate Layer

If the security architecture is a separate document disconnected from module specifications, it will be disconnected from the implementation. Security constraints belong *in* each module specification, not only in a standalone security document. The standalone document provides the comprehensive view; the module specifications apply it concretely.

### Documentation Strategy Without Maintenance Plan

A documentation strategy that specifies what documents should exist but not who maintains them or how staleness is detected will result in documentation that is accurate on day one and progressively wrong thereafter. The maintenance plan — including AI-assisted staleness detection — is as important as the initial documentation.

### Architecture Without Governance

In a small team where "everyone knows what's happening," the absence of formal ownership and review gates works until it doesn't. The first time two people make conflicting changes to the same module boundary, or a security-critical change bypasses review because "we were moving fast," the absence of governance becomes visible. Phase 4 is the time to establish it — not after the first conflict.

---

## Validation Checkpoint

Before moving to Phase 5, the team validates that the architecture is complete and implementation-ready.

- **Module specifications:** Does every module have a complete specification covering purpose, interfaces, data model, security, performance, testing, and monitoring? Is each specification precise enough for an AI implementation tool set to produce a working module?
- **API contracts:** Are all boundaries specified in machine-readable formats? Are contracts consistent with module specifications and with each other?
- **Security architecture:** Does every module boundary have authentication and authorization specified? Does the security architecture address every threat from the threat model? Are audit logging and encryption strategies defined?
- **Data architecture:** Are schemas defined? Are data flows documented at the component level? Are consistency and integrity constraints specified?
- **Documentation strategy:** Is it defined, including types, locations, ownership, maintenance triggers, and AI consumption patterns?
- **Governance model:** Are module owners assigned? Are review gates defined? Is decision authority clear?
- **Principle Scorecard:** Is the scorecard updated? Are any regressions from Phase 3 documented and accepted? Are all principles at or above the project's threshold?
- **Cross-artifact consistency:** Do all artifacts align? A module specification that references a data schema that doesn't exist, or an API contract that doesn't match the module's interface definition, is an architecture bug.

If gaps exist, the SDD cycle iterates. If a module specification is incomplete, its module-level SDD cycle runs again. If cross-artifact inconsistencies are found, the affected artifacts are revised until they align.

---

## What Comes Next

Phase 4 produces the complete architectural blueprint — module specifications, API contracts, security architecture, data architecture, documentation strategy, and governance model. These artifacts are precise enough to build from and structured enough for AI to consume as implementation context.

Phase 5 is where building begins. The next article covers **Implementation** — where AI-assisted coding, continuous validation, specification conformance checking, formal verification, and the full implementation feedback loop transform the architecture into a working system. This is where the discipline of Phases 1–4 pays its largest dividend: precise specifications produce high-quality AI-generated code, and the scoring and verification frameworks established in earlier phases ensure that quality is measured, not assumed.

---

*This is a living document. The tool sets, architectural patterns, and examples will be expanded and refined as the series develops. Every part of this framework is open to iteration.*

*Previous: [Article 5 — Phase 3: Design & Technical Analysis]*
*Next in the series: [Article 7 — Phase 5: Implementation]*
