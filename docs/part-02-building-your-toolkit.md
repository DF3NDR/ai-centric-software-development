# Building Your Toolkit — Tool Sets, SDD, and the Building Blocks

*Part 2 of The AI-Centric Software Development Playbook*

---

## The Toolkit Is the Practice

Article 1 established the six Core Principles — Security, Maintainability, Economics, Operations, Scoring & Metrics, and Correctness Verification. Those principles define what you care about. This article is about building the means to act on them — and defining the methodology that puts them into practice.

In AI-centric development, the toolkit is not a nice-to-have. It is the practice itself. When a three-person team delivers what a fifty-person organization once required, the difference is not that the three people work harder or know more. The difference is that they have assembled a set of tools — prompts, skills, instruction sets, MCP integrations, custom AIs, and a consolidated body of reference knowledge — organized into purposeful **tool sets** and applied through a disciplined, specification-first methodology.

This article defines the three layers that make the toolkit operational:

1. **Building blocks** — the individual components (prompts, skills, MCP servers, etc.)
2. **Tool sets** — curated combinations of building blocks assembled for specific purposes
3. **Specification Driven Development (SDD)** — the iterative methodology that drives how tool sets are used at every phase

The specific tools will change. The structure and the methodology will endure.

---

## Principles First, Then Tools

Before we get into the building blocks themselves, one structural point needs to be explicit: **the Core Principles drive what goes into the toolkit.**

Every building block you add — every prompt, every skill, every MCP server connection — should be evaluated against the six principles. Does this prompt help enforce Security thinking during design? Does this MCP integration support Scoring & Metrics during implementation? Does this skill package help with Correctness Verification during testing?

If a tool accelerates development but has no relationship to any principle, it may still be useful — but it is not doing the work this toolkit is designed to do. If a tool actively undermines a principle (a code generation prompt that ignores security considerations, a deployment script that bypasses audit hooks), it does not belong regardless of how much time it saves.

This is the discipline that separates a curated toolkit from a junk drawer of AI prompts. The principles are the filter.

---

## The Foundation: Your Consolidated Knowledge Base

The AI-Centric Toolkit does not start from zero. Every team, every practitioner, already has a body of accumulated knowledge: technical books, architecture references, internal documentation, past postmortems, vendor API docs, industry standards, regulatory guidance, conference talks, tutorial videos, blog articles, research papers, internal wikis, and architecture decision records.

The AI-Centric Toolkit is an addendum to this existing body of knowledge — not a replacement for it. In a traditional workflow, this knowledge lives in people's heads, on bookshelves, in browser bookmarks, scattered across shared drives, and in institutional memory that walks out the door when someone leaves. It is valuable but fragmented, hard to search, and impossible to apply systematically across every decision.

In an AI-centric workflow, this body of knowledge becomes the foundation layer of the toolkit. The shift is straightforward in concept: consolidate these resources and make them available for AI processing. The AI can then draw on the team's accumulated expertise — not just its own training data — when generating recommendations, evaluating options, reviewing code, or producing documentation.

### What Belongs in the Knowledge Base

Anything the team would consult when making a decision belongs here. Some categories to consider:

**Technical references** — Books, articles, and papers on architecture patterns, language-specific best practices, security frameworks, performance optimization, distributed systems design. These are the resources a senior engineer would reach for when facing a non-trivial design decision. In the AI-centric workflow, they become context the AI draws from rather than references the human must remember to consult.

**Internal documentation** — Architecture decision records, system design documents, API documentation, runbooks, postmortems, onboarding guides, coding standards. These capture the team's specific context — why decisions were made, what has been tried before, what failed and why. This is the knowledge that is hardest to replace and most valuable for AI to have access to.

**Standards and compliance resources** — SOC 2 control descriptions, HIPAA technical safeguard requirements, OWASP guidelines, NIST frameworks, PCI-DSS specifications, industry-specific regulatory guidance. When the AI is helping with threat modeling or architecture design, having the actual compliance requirements available as context produces dramatically better output than relying on the AI's general training knowledge alone.

**Vendor and framework documentation** — Official documentation for the languages, frameworks, cloud providers, and services the team uses. API references, configuration guides, known limitations, migration guides. These change frequently, which makes the consolidation effort ongoing rather than one-time.

**Past project artifacts** — Previous architecture designs, deployment configurations, test strategies, cost analyses, and lessons learned. Pattern recognition is one of AI's strongest capabilities. Giving it access to what the team has built before — including what worked and what didn't — makes its recommendations grounded in real experience rather than generic best practices.

### Making Knowledge AI-Parseable

Consolidation is not just about gathering files into a folder. The knowledge base is most effective when the resources are in formats AI can consume efficiently.

Text-based formats (markdown, plain text, structured documentation) are ideal. PDFs with selectable text work well. Scanned documents, video content, and image-heavy references require additional processing — transcription, summarization, or extraction of key content into text form.

The goal is not to convert everything immediately. It is to prioritize: start with the resources most relevant to the current project and the current phase, and expand coverage over time. A partially consolidated knowledge base that covers the team's most critical references is far more valuable than a comprehensive but unprocessed archive.

### The Knowledge Base Is Living

New resources get added. Old ones become outdated. Internal documentation changes as the system evolves. Vendor documentation updates with new releases. The knowledge base requires ongoing curation — not heavy maintenance, but periodic review to add new material, flag outdated content, and ensure the most relevant resources are readily accessible.

This is itself a task the AI can assist with. Given access to the knowledge base, AI can identify references that may be outdated, flag conflicts between documents, and suggest areas where documentation is thin. The team makes the final decisions, but the monitoring can be automated.

---

## The Building Blocks

With the knowledge base as the foundation, the rest of the toolkit is built from six types of individual components. Each serves a different purpose, operates at a different level of abstraction, and applies at different points in the development process. These are the raw materials from which tool sets are assembled.

### Prompts

Prompts are the most granular building block — the direct interface between the practitioner and the AI. A well-crafted prompt encodes intent, context, constraints, and evaluation criteria into a form the AI can act on.

There are three fundamentally different kinds of prompts, and the distinction matters for how you organize and use them.

**Interview prompts** extract information from the human. They spark structured interaction, drawing out knowledge, requirements, constraints, and preferences that the human may not have articulated yet. The AI asks; the human answers; the result is a structured body of information ready for the next step.

Examples of interview prompts:
- "Interview me with a series of questions to define the requirements for this module. Ask about user workflows, data models, performance expectations, security constraints, and integration points. After each answer, ask a follow-up that pushes for specificity."
- "Ask me ten questions about the deployment environment for this service. Cover infrastructure, networking, scaling expectations, monitoring requirements, and compliance constraints."
- "Walk me through a threat modeling exercise for this data flow. Ask me about each component, what data it handles, who has access, and what happens if it fails."

**Action prompts** achieve goals directly. The human provides context and constraints; the AI produces output — code, specifications, analysis, documentation, test cases, architectural proposals.

Examples of action prompts:
- "Generate an OpenAPI 3.1 specification for this data model. Include standard CRUD operations, pagination on list endpoints, and error responses for 400, 401, 403, 404, and 500 status codes."
- "Generate property-based tests for this function. Define properties based on the specification, then produce test cases that verify those properties across randomized inputs."
- "Produce a task list from this PRD. Each task should include acceptance criteria, estimated complexity, dependencies, and which Core Principles it must satisfy."

**Evaluation prompts** sit between interview and action prompts. They ask the AI to assess, compare, score, or critique — producing structured judgment rather than raw output.

Examples of evaluation prompts:
- "Compare these three architectural approaches against our Core Principles. For each approach, score Security, Maintainability, Economics, Operations, Scoring & Metrics, and Correctness Verification on a 1–5 scale. Identify the strongest trade-off tension in each approach."
- "Audit this pull request for specification conformance. Compare the implementation against the OpenAPI spec and the architecture decision record. Flag any deviations."
- "Evaluate this cost forecast against actual spend for the last quarter. Identify where estimates diverged from reality by more than 15% and suggest revised forecasting assumptions."

### Skills

Skills are reusable context packages that give AI the right framing for a specific type of task. Where a prompt is a single instruction, a skill is a pre-built environment — a combination of system context, reference material, constraints, and instructions that primes the AI for a category of work.

Think of a skill as the difference between asking a general practitioner a medical question and asking a cardiologist. The cardiologist brings specialized context, vocabulary, evaluation criteria, and judgment patterns to the conversation. A skill does the same thing for AI.

A well-constructed skill typically includes:

- **Role and context framing** — What is the AI acting as? What domain is it operating in? What are the boundaries of its authority?
- **Reference material** — Key documents, standards, patterns, or examples drawn from the consolidated knowledge base that the AI should consider for this type of task.
- **Constraints and guardrails** — What must the AI always do? What must it never do? What principles take precedence for this type of work?
- **Output format expectations** — What structure should the output take? What level of detail is expected? What artifacts should be produced?

Skills are reusable across projects and phases but may need customization for specific contexts. A "security review" skill might be used during design (reviewing architecture proposals), implementation (reviewing generated code), and testing (evaluating audit results) — with the same core framing but different reference material and output expectations for each phase.

### Instruction Sets

Instruction sets are detailed, multi-step playbooks that guide AI through complex processes. Where a prompt is a single question and a skill is a context package, an instruction set is a procedure — a sequence of steps with decision points, branching logic, and defined outputs at each stage.

Instruction sets are particularly valuable for processes that the team wants to execute consistently every time: onboarding a new module, conducting a security review, performing a cost analysis, preparing a deployment, running a compliance check. They encode the team's best practices into a form that AI can follow and that junior team members can execute with confidence.

A well-constructed instruction set includes:

- **Preconditions** — What must be true before this process begins? What inputs are required?
- **Sequential steps** — Each step defines what the AI should do, what inputs it needs, what output it produces, and what success looks like.
- **Decision points** — Where the process branches based on findings. "If the security score is below 3, escalate to manual review. If above 3, proceed to the next step."
- **Checkpoints** — Points where a human reviews progress before the process continues. Not every step needs human approval, but critical junctures should require it.
- **Output artifacts** — What the process produces when complete. A report, a scorecard, a set of generated tests, an updated specification.

The distinction between skills and instruction sets is one of scope. A skill says "here is how to think about security review." An instruction set says "here are the twelve steps to conduct a complete security review of a module, including what to check, what to score, when to escalate, and what to document."

### MCP Servers

MCP (Model Context Protocol) servers are the bridge between AI reasoning and real-world tooling. They give AI the ability to interact with external systems — reading from and writing to the actual tools the team uses.

Without MCP servers, AI operates in a conversational bubble. It can reason about code but cannot run it. It can discuss test results but cannot execute tests. It can recommend a deployment strategy but cannot check the current state of the infrastructure. MCP servers close that gap.

Categories of MCP integrations to consider:

**Version control** — Access to git repositories, commit history, branch state, pull request status. This allows AI to understand the current state of the codebase, track changes over time, generate semantic commit messages, and review diffs against specifications.

**CI/CD pipelines** — Access to build systems, test runners, deployment pipelines. This allows AI to trigger builds, monitor test results, evaluate deployment readiness, and flag failures in real time.

**Testing frameworks** — Access to test execution, coverage reporting, fuzzing tools, and static analysis. This allows AI to run tests as part of its workflow rather than generating tests the human must run manually.

**Infrastructure and monitoring** — Access to cloud provider APIs, container orchestration, logging systems, and alerting platforms. This allows AI to check the actual state of the deployed system, compare it against the design specification, and flag drift.

**Databases and data stores** — Access to schema definitions, query performance metrics, and data quality checks. This allows AI to validate that data models match specifications and that performance meets benchmarks.

**Documentation systems** — Access to wikis, documentation platforms, and knowledge bases. This allows AI to read existing documentation as context and update documentation as part of its workflow.

The principle-based filter applies strongly here. Each MCP integration should be evaluated: which principles does it support? A testing framework integration supports Maintainability, Scoring & Metrics, and Correctness Verification. A monitoring integration supports Operations and Security. If an integration does not clearly serve at least one principle, question whether it belongs in the toolkit.

### Custom / Domain-Specific AIs

Custom AIs are purpose-built configurations tuned for specific roles, domains, or phases. Where skills provide context for a general AI, custom AIs are distinct configurations — potentially using different models, different system prompts, different tool access, and different evaluation criteria — optimized for a particular kind of work.

Examples of custom AI configurations:

- **Security Reviewer** — Configured with access to the team's threat models, compliance requirements, and security standards. Tuned to be conservative, flagging potential issues even when uncertain. Connected via MCP to vulnerability scanning tools and audit logs.
- **Architecture Evaluator** — Configured with the team's architecture decision records, design patterns, and Core Principle scorecards. Tuned to evaluate proposals against established patterns and score them across all six principles.
- **Cost Analyst** — Configured with infrastructure pricing models, historical cost data, and the team's budget constraints. Tuned to produce realistic cost forecasts and flag decisions that push costs beyond thresholds.
- **Documentation Generator** — Configured with the team's documentation standards, existing documentation, and style guides. Tuned to produce documentation that matches the team's conventions and is queryable by other AI tools.

Custom AIs are the most complex building block to create and maintain. They require ongoing tuning as the project evolves, as models improve, and as the team's needs change. Start with one or two for the roles where consistency and specialization matter most, and expand as the toolkit matures.

---

## Tool Sets: From Parts to Purpose

Building blocks are individual components. A prompt does one thing. A skill provides one context. An MCP server connects to one system. Individually, they are useful. But the real leverage comes from combining them.

**A tool set is a curated combination of building blocks assembled for a specific purpose.** It brings together the prompts, skills, MCP servers, instructions, and resources needed for a particular kind of work within a particular phase. The tool set is the unit of work — the practitioner selects the right tool set for the task at hand and follows its embedded workflow.

### What Makes a Tool Set

A tool set is not just a folder of loosely related prompts. It is a purposeful assembly with a defined workflow. A well-constructed tool set includes:

- **A clear purpose** — What kind of work is this tool set for? "Requirements specification for a new module." "Security review of an API endpoint." "Cost analysis for a proposed architecture change."
- **The right building blocks** — The specific prompts (interview, action, evaluation), skills, instruction sets, MCP connections, and knowledge base resources needed for this kind of work.
- **A defined sequence** — The order in which the building blocks are used. Which prompt comes first? What does its output feed into? Where does the human review and decide?
- **Core Principle alignment** — Which principles does this tool set serve? What scoring criteria does it enforce? What correctness checks does it include?

### Tool Set Examples

**Requirements Specification Tool Set** — Used when defining what a new module, feature, or system component needs to do.
- An interview prompt designed to elicit requirements through structured questioning
- A skill that provides domain-specific context (e.g., the team's existing architecture, relevant compliance requirements)
- An MCP connection to the project's existing documentation and architecture decision records
- An instruction set for structuring the output into a consistent format
- References from the consolidated knowledge base (relevant standards, past project requirements documents)
- An evaluation prompt that scores the resulting requirements against the Core Principles for completeness

**Architecture Review Tool Set** — Used when evaluating a proposed architecture against the Core Principles.
- A skill that frames the AI as an architecture reviewer with access to the team's design patterns and standards
- An evaluation prompt that scores the proposal across all six principles
- An MCP connection to the existing codebase for context on current architecture
- References to relevant architecture decision records and past postmortems
- An action prompt that generates a formal review document with findings and recommendations

**Implementation Tool Set** — Used when generating code from a specification.
- The PRD and task list as input resources
- A skill that provides coding standards, security requirements, and testing expectations
- An action prompt that generates code from the task specification
- MCP connections to the testing framework and version control
- An evaluation prompt that scores the generated code against the specification
- A correctness verification instruction set that runs automated checks before human review

### Tool Sets Are Reusable and Evolving

A good tool set is reusable across similar tasks. The "Requirements Specification" tool set works whether you are specifying a user authentication module or a data pipeline. The core workflow is the same; the domain-specific context changes.

Tool sets also evolve. When a prompt within a tool set consistently produces poor results, it gets refined or replaced. When the team discovers that an additional MCP integration would improve a tool set, it gets added. When a tool set becomes too complex, it gets split into more focused sets. The discipline is in curating tool sets with the same care applied to curating code libraries.

---

## Specification Driven Development (SDD)

Tool sets provide the means. SDD provides the method. **Specification Driven Development is the core methodology of the AI-Centric framework** — the iterative, specification-first cycle that drives how tool sets are used at every phase.

The premise of SDD is straightforward: before AI implements anything, it must work from a clear specification. And before a specification exists, it must be developed through structured interaction between the practitioner and AI. This is not bureaucratic overhead. It is the mechanism that keeps AI output aligned with intent, verifiable against requirements, and traceable through the development process.

### The SDD Cycle

SDD follows a five-step cycle. Each step has its own tool set (or set of tool sets), and the output of each step feeds into the next.

**Step 1: Specify** — The practitioner uses interview prompts from a specification tool set to gather needs, context, and constraints. The AI interviews the practitioner, asking structured questions that draw out requirements, edge cases, dependencies, and acceptance criteria. The output is a structured specification of what is needed — not code, not design, but a clear statement of intent and requirements.

This is one of the most valuable uses of AI in the entire process. Humans often know what they want but struggle to articulate it completely. The interview prompt forces completeness by asking the questions the practitioner might not think to ask themselves. "What happens when this input is null? What is the performance requirement under peak load? What compliance constraints apply to this data?"

**Step 2: Plan** — The specification from Step 1 is developed into a plan document. Depending on the phase, this might be a brief design brief, a comprehensive project plan, or a detailed architecture proposal. The plan is then broken into sections — or, borrowing the Agile term, **epics** — each representing a coherent chunk of work that can be specified and implemented independently.

The plan document serves as the bridge between the broad specification ("we need a user authentication system") and the detailed requirements ("here are the six components of the authentication system, each of which needs its own specification"). AI assists in creating the plan and identifying the natural decomposition into sections, but the practitioner reviews and approves the breakdown.

**Step 3: Detail** — Each section from the plan is taken through another interactive or interview prompt that produces a **Project Requirement Document (PRD)**. The PRD follows a well-defined layout specific to the phase and the type of work. It is more detailed than the plan, more structured than the original specification, and specific enough to drive task generation.

The PRD is where the Core Principles become concrete requirements. A PRD for an API module does not just specify the endpoints — it specifies the security constraints (zero-trust, authentication requirements), the maintainability expectations (test coverage targets, documentation requirements), the economic constraints (performance budgets, infrastructure limits), and the operational requirements (monitoring hooks, scaling behavior). The principles are not aspirational. They are requirements embedded in the specification itself.

**Step 4: Task** — The PRD is included as a resource for a task-generation prompt that breaks the requirements into a well-defined, actionable task list. Each task includes:

- A clear description of what needs to be done
- Acceptance criteria that define "done"
- Dependencies on other tasks
- Estimated complexity
- Which Core Principles the task must satisfy
- Verification criteria — how correctness will be checked

The task list is the final specification before implementation begins. It is detailed enough that the implementation prompt (or the practitioner working with AI) can produce results without ambiguity about what is expected.

**Step 5: Implement** — An implementation prompt (or set of prompts from the implementation tool set) produces results. These results might be code, documentation, configurations, test suites, architectural artifacts, deployment scripts, or any other deliverable the phase requires.

Implementation is not the end of the cycle. The output is evaluated against the PRD and the task list. Scoring & Metrics are applied. Correctness Verification checks run. If the output does not meet the specification, the cycle iterates — refining the implementation, updating the task list, or even revising the PRD if the specification itself was incomplete.

### SDD Is Iterative, Not Linear

The five steps are presented sequentially, but SDD is iterative at every level. Within a single section, the implement-evaluate loop may cycle multiple times before the output meets the specification. Across sections, insights from implementing one section may reveal gaps in the specification of another, sending the team back to the Detail or Plan step.

This is by design. The specification-first approach does not assume perfect foresight. It assumes that structured iteration — specify, plan, detail, task, implement, evaluate, refine — produces better outcomes than unstructured generation. The specifications are living documents that evolve as understanding deepens.

### SDD Applies at Every Phase

SDD is not limited to the implementation phase. It is the methodology used at *every* phase of the development process:

- **During Information Gathering** — Specify what information is needed. Plan the research. Detail the questions for each area. Task the specific searches and analyses. Implement by executing the research and producing the information report.
- **During Analysis & Stack Selection** — Specify the evaluation criteria. Plan the analysis. Detail the comparison framework. Task the specific evaluations. Implement by producing the analysis report and stack recommendation.
- **During Architecture** — Specify the architectural requirements. Plan the architecture. Detail each architectural component. Task the design decisions. Implement by producing architecture documents, API specs, and module designs.
- **During Testing** — Specify the test strategy. Plan the test coverage. Detail the test requirements for each component. Task the specific test suites. Implement by generating and executing tests.

The tool sets change at each phase. The methodology remains the same. This consistency is what makes the framework learnable and repeatable — once the team internalizes the SDD cycle, they can apply it to any phase with the appropriate tool set.

### SDD and the Core Principles

SDD is the mechanism through which the Core Principles are applied in practice. The principles are not abstract guidelines remembered by the practitioner — they are embedded in the specifications, the PRDs, the task lists, and the evaluation criteria at every step of the cycle.

When a PRD specifies that an API module must achieve 90% test coverage (Maintainability), withstand a defined set of attack vectors (Security), operate within a cost ceiling (Economics), include monitoring hooks (Operations), produce measurable performance benchmarks (Scoring & Metrics), and pass specification conformance checks (Correctness Verification) — the principles are not aspirational. They are requirements. And the implementation is evaluated against them.

---

## Organizing the Toolkit

A toolkit that cannot be found cannot be used. Organization matters, and it matters more as the toolkit grows.

### Three Levels of Organization

The toolkit has a natural hierarchy:

**Building blocks** are the atomic level — individual prompts, skills, instruction sets, MCP configurations, custom AI setups, and knowledge base resources. These are tagged, versioned, and stored individually.

**Tool sets** are the working level — curated combinations of building blocks assembled for specific purposes. These are what practitioners reach for when starting a task. Tool sets are organized by purpose and phase.

**The SDD cycle** is the process level — the methodology that defines how tool sets are used in sequence. The cycle is consistent across phases; the tool sets that populate each step change depending on the work.

### Tagging and Discovery

Each building block and tool set should be tagged with:

- The phase(s) where it applies
- The Core Principle(s) it serves
- The SDD step it supports (Specify, Plan, Detail, Task, or Implement)
- The type of work it is designed for

This allows the team to find what they need by slicing along any axis: "Show me all tool sets for Phase 3 (Design & Technical Analysis)." "Show me all building blocks that serve Correctness Verification." "Show me all interview prompts used in the Specify step."

### Version Control and Iteration

Prompts, skills, instruction sets, and tool set configurations are artifacts. They should be version-controlled with the same discipline applied to code. When a prompt is refined based on experience, the change should be tracked. When a tool set is restructured because the workflow improved, the history should be preserved.

This serves two purposes. First, it allows the team to revert to previous versions when changes don't work as expected. Second — and more importantly for AI-centric development — it creates a history that AI can reason about. "This tool set was updated three times last month. The current version produces better security scores than the original. Here is what changed."

### Team Access and Sharing

The toolkit must be accessible to everyone on the team. A brilliant tool set that lives in one person's environment is not a toolkit component — it is tribal knowledge. Store building blocks and tool sets in a shared, searchable location. Document what each one does, when to use it, which SDD step it supports, and what principles it serves.

For teams working across multiple projects, consider which tool sets are project-specific and which are universal. A "Requirements Specification" tool set is likely reusable across projects. A tool set for deploying to a specific client's infrastructure is project-specific. Separate the layers so that universal tool sets can be shared and maintained independently.

---

## Building the Toolkit Incrementally

A common mistake is attempting to build a comprehensive toolkit before starting the actual work. This is both unnecessary and counterproductive. The toolkit should be built incrementally, phase by phase, as the team works through actual projects.

### Start With What You Need Now

If you are beginning Phase 1 (Information Gathering), you need an information-gathering tool set: some interview prompts, a few evaluation skills, and perhaps an MCP integration with your version control system. You do not yet need deployment tool sets or production monitoring custom AIs.

Build the tool sets for the current phase. Use them. Run the SDD cycle. Refine them based on what works and what doesn't. Then build the tool sets for the next phase. By the time you reach deployment, you will have a toolkit that was forged in actual use rather than designed in theory.

### Capture What Works

Every interaction with AI during the development process is an opportunity to identify a reusable building block or improve a tool set. When a prompt produces an unexpectedly good result, save it. When a sequence of steps works well as a process, formalize it as an instruction set. When you find yourself providing the same context repeatedly, package it as a skill. When a combination of building blocks consistently produces good results, formalize it as a tool set.

The toolkit grows organically from practice. The discipline is in capturing what works rather than letting it evaporate at the end of a conversation.

### Retire What Doesn't

Not every building block or tool set will prove useful. Some prompts will produce inconsistent results. Some tool sets will turn out to be overly rigid or too vague. Some skills will become irrelevant as the project evolves. Remove them. A lean toolkit with twenty reliable tool sets is more valuable than a sprawling collection of two hundred where half are untested.

### Evaluate Against Principles

Periodically — at each major phase transition, or quarterly for ongoing projects — review the toolkit against the six Core Principles and the SDD cycle. Are all principles adequately covered? Are there SDD steps where the tool sets are weak? Are there phases where principle enforcement is incomplete because the right building blocks don't exist yet?

This review is itself a good use of AI and the SDD methodology. Specify the evaluation criteria, plan the review, detail the gaps, task the improvements, implement the updates.

---

## The Toolkit in Context

The toolkit described in this article is not a product. It is not a framework to download or a platform to subscribe to. It is a practice — an ongoing, evolving collection of resources assembled by practitioners for their specific context, guided by shared principles, organized into purposeful tool sets, and applied through a consistent methodology.

The specifics will vary from team to team, project to project, and year to year. The prompts that work well with today's models may need revision as models improve. The MCP integrations available today will expand dramatically over the next eighteen to twenty-four months. The tool sets that seem comprehensive now will need restructuring as the field matures.

What endures is the structure: principles that define what matters, a consolidated knowledge base that grounds the work in real expertise, building blocks that serve the principles, tool sets that combine building blocks for purpose, and SDD as the methodology that drives it all forward.

---

## What Comes Next

With the Core Principles established in Article 1, the toolkit framework and SDD methodology defined here, we are ready to begin working through the development phases. Each subsequent article will walk through a specific phase of the AI-centric development process:

- What the phase accomplishes
- How the SDD cycle applies to this phase
- Which tool sets are most relevant
- How each Core Principle is applied and evaluated
- Scoring checkpoints and correctness verification specific to the phase

The next article covers **Phase 1: Information Gathering** — the starting point for any greenfield project. This is where the SDD cycle runs for the first time: specifying what information is needed, planning the research, detailing the questions, tasking the specific analyses, and implementing the research that produces the information report. It is where the consolidated knowledge base earns its first return and where the toolkit begins to take shape through actual use.

---

*This is a living document. The building block taxonomy, tool set patterns, SDD methodology, and examples will be expanded and refined as the series develops. Every part of this framework is open to iteration.*

*Previous: [Article 1 — Core Principles: Your Compass for Every Decision]*
*Next in the series: [Article 3 — Phase 1: Information Gathering]*
