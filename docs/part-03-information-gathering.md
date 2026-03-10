# Phase 1 — Information Gathering

*Part 3 of The AI-Centric Software Development Playbook*

---

## The Starting Point

Every software project begins with a question: *What are we building, and what do we need to know before we start?*

In traditional development, information gathering is often informal and unevenly distributed. A senior engineer reads some docs, scans a few GitHub repos, asks around about what frameworks the industry is using, maybe writes up a summary in a wiki page. The results depend heavily on who does the work, what they happen to know already, and how much time they're given. Important questions go unasked because nobody thought to ask them. Blind spots survive because no one had time to scan broadly enough.

In AI-centric development, information gathering becomes the first structured application of the SDD cycle. The goal is the same — understand the landscape before committing to decisions — but the process is disciplined, the coverage is broader, and the output is a structured artifact that feeds directly into the next phase.

This is where the toolkit earns its first return. Every interview prompt, every evaluation skill, every MCP connection to existing documentation starts producing value here. And this is where the Core Principles begin their work — not as a review gate at the end, but as the lens through which every piece of gathered information is evaluated.

---

## What Information Gathering Accomplishes

Phase 1 answers the questions that every subsequent phase depends on. Skip it or do it poorly, and every later decision sits on an unstable foundation. Do it well, and the team enters design and analysis with a shared understanding grounded in evidence rather than assumption.

The outputs of this phase include:

**A technology landscape assessment** — What exists? What frameworks, languages, platforms, services, and tools are available for the kind of system being built? What are their strengths, weaknesses, maturity levels, and community health? Where is the ecosystem heading?

**A competitive and market scan** — Who else has built something similar? What stacks did they choose? Where did those choices succeed and where did they break? What can be learned from their documentation, their architectures, their public failures and successes?

**A requirements sketch** — What does the system need to do? This is not the final requirements document — that comes later through the SDD Detail step — but an initial capture of user needs, business goals, constraints, and non-negotiable requirements that will shape every subsequent decision.

**A risk and constraint inventory** — What compliance requirements apply? What security concerns are inherent to the domain? What are the known hard constraints (budget, timeline, team size, existing infrastructure)? What are the things that could go wrong if ignored?

**A reusable components catalog** — What can be reused? Open-source libraries, existing internal modules, API services, standard patterns. What has already been solved, and what genuinely needs to be built from scratch?

All of this is captured in a structured **Information Report** — the primary artifact of Phase 1 — designed to be both human-readable and AI-parseable so that it can serve as input context for every tool set used in subsequent phases.

---

## The SDD Cycle in Phase 1

This is the first time the SDD cycle runs in a new project. The cycle applies to information gathering just as it applies to code implementation — the only difference is what is being specified, planned, detailed, tasked, and implemented.

### Step 1: Specify — What Do We Need to Know?

Before gathering information, specify what information is needed and why. This seems obvious, but without this step, information gathering drifts into unfocused browsing. The practitioner uses an interview prompt from the Information Gathering tool set to define the scope.

The interview prompt asks structured questions:

- What is the high-level purpose of the system being built?
- What domain does it operate in? What are the domain-specific constraints?
- What are the known technical requirements (performance, scale, reliability)?
- What compliance or regulatory requirements apply?
- What is the team's existing expertise? Where are the knowledge gaps?
- What is the timeline and budget envelope?
- Are there existing systems this needs to integrate with?
- Who are the users? What are their primary workflows?

The output of this step is a **research specification** — a structured document that defines the scope, priorities, and boundaries of the information-gathering effort. It prevents the common failure mode of gathering everything about everything and producing a report that is comprehensive but useless.

### Step 2: Plan — Organize the Research

The research specification is developed into a research plan. The plan breaks the information-gathering effort into distinct research areas — sections or epics, each focused on a coherent domain of inquiry.

A typical plan might include:

- **Technology landscape** — Survey available frameworks, languages, and platforms relevant to the project type
- **Competitive analysis** — Identify similar systems, analyze their technology choices and outcomes
- **Regulatory and compliance** — Identify all applicable compliance requirements and their technical implications
- **Infrastructure options** — Survey hosting, deployment, and operational platform options
- **Security landscape** — Identify domain-specific threats, common vulnerability patterns, and security tooling
- **Existing assets** — Catalog reusable components, internal libraries, and third-party services
- **User and market research** — Understand user needs, workflows, and expectations

Each research area becomes a section that will be detailed and tasked independently. The practitioner reviews the plan and adjusts — adding areas that were missed, removing areas that are out of scope, reprioritizing based on what matters most for this project.

### Step 3: Detail — Define the Research Questions

Each section from the plan is taken through a detail prompt that produces a structured set of research questions and evaluation criteria. This is the PRD equivalent for information gathering — not a product requirements document, but a **Research Requirements Document** that specifies exactly what needs to be found, how it will be evaluated, and what format the findings should take.

For example, the Technology Landscape section might be detailed into:

- What programming languages are viable for this project type? Evaluate each against: performance characteristics, security features, ecosystem maturity, team expertise, hiring market, AI tooling support.
- What frameworks exist for the core functionality? Evaluate each against: documentation quality, community activity (commits, issues, releases in last 12 months), license compatibility, integration with target deployment environment.
- What are the known failure modes of each candidate technology? Source from: postmortems, CVE databases, community forums, production experience reports.

The detail step transforms a vague research area ("survey available frameworks") into a specific, evaluable set of questions. This specificity is what makes AI-assisted research productive rather than meandering.

### Step 4: Task — Assign the Specific Searches and Analyses

The research questions from Step 3 are broken into concrete, actionable tasks. Each task is a single, well-defined research action with clear output expectations.

Examples:

- Search public repositories for Rust web frameworks with more than 1,000 GitHub stars. For each, capture: name, star count, last commit date, open issues count, license, stated performance benchmarks.
- Retrieve and summarize the OWASP Top 10 for the current year. Map each vulnerability category to the project's likely attack surface.
- Identify three to five systems similar to the proposed project. For each, determine: technology stack (if publicly known), scale of operation, known technical challenges, documentation quality.
- Query the consolidated knowledge base for any internal postmortems or architecture decision records related to the domain or candidate technologies.
- Survey container orchestration options (Docker Compose, Kubernetes, Wasm-based alternatives). For each, capture: learning curve, operational complexity, cost at target scale, community support.

The task list is specific enough that AI can execute many of these tasks directly — through web search, repository analysis, documentation retrieval, and knowledge base queries. The practitioner reviews the task list for completeness and prioritizes the order of execution.

### Step 5: Implement — Execute the Research

With the tasks defined, the Information Gathering tool set goes to work. This is where AI provides its most immediate productivity gain in the entire development process.

AI can execute many research tasks faster and more comprehensively than a human working alone:

- Scanning and summarizing documentation across dozens of frameworks in minutes
- Pulling repository statistics, commit history, and community health indicators
- Cross-referencing compliance requirements against technology capabilities
- Synthesizing information from multiple sources into structured comparisons
- Identifying patterns, gaps, and contradictions across the gathered data

The practitioner's role during implementation is not passive. It includes:

- Reviewing AI-gathered information for accuracy and completeness
- Applying domain expertise to evaluate claims AI cannot verify
- Identifying gaps in the research — questions that the task list missed
- Iterating: when findings in one area reveal new questions, cycling back to the Detail or Task step to expand the research

The output of the implementation step is the raw research findings — organized by section, structured according to the research requirements, and ready to be synthesized into the Information Report.

---

## The Information Report

The primary artifact of Phase 1 is the **Information Report** — a structured document that synthesizes all research findings into a format that is both useful for human decision-making and consumable by AI in subsequent phases.

### Structure

The Information Report is not a dump of everything found. It is a curated synthesis, organized to support the decisions that will be made in Phase 2 (Analysis & Stack Selection) and Phase 3 (Design & Technical Analysis).

A well-structured Information Report typically includes:

**Executive Summary** — A concise overview of the key findings, major options, significant risks, and recommended areas for deeper analysis. This section exists for human readers who need the headlines without reading every detail.

**Technology Landscape** — The candidate technologies, frameworks, and platforms, with structured evaluations against the criteria defined in the Detail step. Not just a feature comparison — an assessment of maturity, community health, known failure modes, and fit for the project's specific needs.

**Competitive Analysis** — What similar systems exist, what technology choices they made, and what can be learned from their approaches. Successes, failures, and patterns worth emulating or avoiding.

**Regulatory and Compliance Map** — The compliance requirements that apply to this project, mapped to their technical implications. Which requirements affect architecture decisions? Which constrain technology choices? Which will require ongoing operational processes?

**Risk and Constraint Inventory** — The known risks, hard constraints, and potential pitfalls identified during research. Each risk should include: likelihood, impact, which Core Principles it affects, and any mitigation options identified.

**Reusable Components Catalog** — The libraries, services, patterns, and internal assets that can be leveraged. For each, an assessment of fitness for purpose, maintenance status, and integration complexity.

**Research Gaps and Open Questions** — What the research could not answer. What requires deeper investigation. What depends on decisions not yet made. These gaps become inputs to Phase 2.

### Designed for AI Consumption

The Information Report serves double duty. Human stakeholders read it to build shared understanding. AI consumes it as context for every tool set used in subsequent phases.

This dual purpose has practical implications for how the report is structured:

- Use consistent, machine-parseable formatting — structured headers, tables, labeled sections
- Include metadata — what sources were consulted, when the research was conducted, confidence levels for key findings
- Avoid burying critical information in narrative prose — surface key facts, evaluations, and risks in structured formats that AI can extract and reason about
- Cross-reference sections — the compliance map should reference specific technologies from the landscape assessment; the risk inventory should reference specific compliance requirements

When the team moves to Phase 2 and uses a Stack Selection tool set, the Information Report becomes a resource in that tool set. The AI does not start from zero — it starts from the structured findings of Phase 1.

---

## Core Principles in Phase 1

Phase 1 is not a principle-free zone where the team simply gathers data. The Core Principles shape *what* is gathered, *how* it is evaluated, and *what questions* are asked. This is the first opportunity to embed principle-driven thinking into the project, and it is the cheapest place to catch problems that would be expensive to fix later.

### Security

Security-relevant information gathering starts here, not during implementation or testing.

- What are the known vulnerabilities in candidate technologies? Check CVE databases, security advisories, and community-reported issues.
- What compliance requirements apply? Identify them now, not when someone asks for a SOC 2 report six months before launch.
- What is the threat landscape for this domain? Healthcare, finance, e-commerce, government — each has different adversaries and attack patterns.
- What security tooling is available for candidate technology stacks? Static analysis, dependency scanning, runtime protection — if a stack has poor security tooling, that is a significant risk factor.

The information gathered here feeds directly into the threat modeling that happens in Phase 2. If the security landscape is not understood during information gathering, threat modeling operates on incomplete data.

### Maintainability

Maintainability-relevant information gathering assesses the long-term viability of candidate technologies and approaches.

- How well-documented are the candidate technologies? Good documentation correlates with maintainability. If a framework's documentation is sparse, incomplete, or outdated, maintaining a system built on it will be harder.
- What is the community health? A framework with active contributors, regular releases, and responsive issue triage is a safer long-term bet than one with a declining contributor base.
- What is the testing ecosystem? Does the technology have mature testing frameworks, property-based testing support, and integration testing patterns?
- What is the talent pool? If the team grows, can qualified engineers be hired? If the original team members leave, can the system be maintained by successors?

### Economics

Economics-relevant information gathering captures the cost dimensions that will drive decisions in Phase 2.

- What are the licensing costs for candidate technologies and services? Open-source is not free — it has support, integration, and maintenance costs. Commercial licenses have direct costs that scale with usage.
- What are the infrastructure costs at target scale? Cloud provider pricing, container orchestration costs, database hosting, monitoring services. Gather actual pricing data, not estimates.
- What is the development velocity for candidate stacks? Some technologies enable faster initial development but slower iteration. Others have higher upfront learning costs but faster long-term velocity. Both patterns have economic implications.
- What are the AI tooling costs? In an AI-centric workflow, the AI tools themselves represent a cost line. Model API costs, MCP server hosting, custom AI configuration and maintenance — these should be estimated early.

### Operations

Operations-relevant information gathering identifies the runtime and governance considerations that constrain architecture decisions.

- What deployment and orchestration options exist for candidate stacks? What is the operational complexity of each?
- What monitoring and observability tooling is available? If a technology stack has poor observability support, diagnosing production issues will be harder and slower.
- What are the scaling characteristics? How do candidate technologies behave under load? What are their known scaling limits?
- What integration patterns are standard in the candidate ecosystem? API conventions, data formats, authentication protocols — how well does each option play with the broader ecosystem?

### Scoring & Metrics

Scoring begins here by defining what will be measured and establishing baselines.

- What benchmarks exist for candidate technologies? Published performance benchmarks, community-reported throughput numbers, latency measurements under load.
- What scoring criteria will be used in Phase 2? The information gathered here should directly support the evaluation framework that Phase 2 will use.
- What metrics are available from existing systems? If there are predecessors or comparable systems, their performance data establishes realistic baselines.

The Information Report should include quantitative data wherever possible. "Framework X is fast" is not useful. "Framework X achieves 50,000 requests per second on a single-core benchmark, compared to 35,000 for Framework Y" is useful. AI is effective at gathering and structuring these comparisons, but the team must specify what to measure.

### Correctness Verification

Correctness Verification in Phase 1 is about verifying the accuracy of the gathered information itself. AI-gathered data is not inherently reliable. Sources may be outdated, benchmarks may be misleading, community sentiment may not reflect technical reality.

- Cross-reference claims across multiple sources. If one article claims a framework handles 100,000 concurrent connections and no other source confirms this, flag it.
- Distinguish between marketing material and independent evaluation. Vendor documentation describes what a technology is designed to do. Community experience reports describe what it actually does.
- Check dates. A performance benchmark from 2021 may not reflect the current state of a framework that has had three major releases since.
- Validate compliance interpretations. AI's understanding of regulatory requirements should be checked against the actual regulatory text and, when stakes are high, against legal or compliance expertise.

The Information Report should include confidence levels for key findings. "High confidence: Framework X is actively maintained (verified via commit history, release schedule, and issue response times)." "Medium confidence: Framework X outperforms Framework Y at scale (based on two independent benchmarks but not verified with project-specific workloads)." "Low confidence: Framework X is SOC 2 compliant (claimed by vendor but not independently verified)."

---

## Tool Sets for Phase 1

Phase 1 uses several tool sets, each supporting a different part of the SDD cycle. These are the first tool sets the team builds or selects, and they will be refined through use.

### Research Specification Tool Set

**Purpose:** Support SDD Step 1 (Specify) — define what information needs to be gathered.

**Building blocks:**
- An interview prompt that walks the practitioner through scoping the research effort — domain, constraints, team expertise, timeline, known requirements
- A skill that frames the AI as a research strategist, helping identify areas of inquiry the practitioner might overlook
- References from the consolidated knowledge base: past project research specifications, domain-specific research checklists
- An output template for the research specification document

### Research Planning Tool Set

**Purpose:** Support SDD Step 2 (Plan) — break the research into organized sections.

**Building blocks:**
- An action prompt that takes the research specification and generates a proposed research plan with sections, priorities, and estimated effort
- An evaluation prompt that reviews the plan against the six Core Principles — "Is there a section for each principle-relevant area? Are any principle dimensions missing from the research plan?"
- References from the consolidated knowledge base: past research plans, phase 1 checklists from previous projects

### Research Execution Tool Set

**Purpose:** Support SDD Steps 3–5 (Detail, Task, Implement) — define research questions, generate tasks, and execute the research.

**Building blocks:**
- A detail prompt that takes each research section and generates specific, evaluable research questions with evaluation criteria
- A task-generation prompt that breaks research questions into concrete, actionable tasks
- MCP connections to: web search and documentation retrieval, code repository analysis tools, the team's consolidated knowledge base, vulnerability and CVE databases
- A skill that provides the AI with domain context for evaluating research findings
- An evaluation prompt that assesses research quality — coverage, accuracy, confidence levels, gaps

### Report Synthesis Tool Set

**Purpose:** Compile research findings into the structured Information Report.

**Building blocks:**
- An action prompt that takes raw research findings and synthesizes them into the Information Report format — executive summary, technology landscape, competitive analysis, compliance map, risk inventory, reusable components catalog, gaps and open questions
- A skill that provides report structure guidelines and formatting standards
- An evaluation prompt that reviews the report against the Core Principles — "Does the report include sufficient information to evaluate candidate technologies against all six principles?"
- A correctness verification instruction set that cross-references key claims, checks source dates, and flags low-confidence findings

---

## Common Pitfalls

Phase 1 has characteristic failure modes. Recognizing them helps the team avoid them.

### Gathering Without Specifying

The most common failure is starting research without defining what needs to be found. This produces a sprawling collection of information with no clear connection to the decisions it should support. The SDD Specify step exists to prevent this. Time spent defining the research scope is never wasted.

### Breadth Without Depth

AI makes it easy to scan broadly. The risk is producing a report that mentions fifty frameworks but deeply evaluates none. Breadth is valuable for initial awareness, but the research plan should explicitly identify which areas need deep investigation and which need only a surface scan.

### Trusting AI Output Without Verification

AI can summarize documentation, extract metrics, and synthesize comparisons with impressive speed. It can also confidently present outdated information, misinterpret benchmarks, and generate plausible-sounding assessments that do not hold up to scrutiny. The Correctness Verification principle applies here: cross-reference, check dates, distinguish marketing from evidence, and flag confidence levels.

### Ignoring Core Principles During Research

If the team gathers extensive information about performance and features but neglects to research compliance requirements, security tooling maturity, or operational complexity, Phase 2 will be working with an incomplete picture. The Core Principles should shape the research plan from the start — each principle generates questions that the research must address.

### Producing a Report Nobody Can Use

A report that is comprehensive but unstructured is nearly as bad as no report at all. The Information Report must be organized for both human decision-making and AI consumption in later phases. If a report cannot be given to an AI tool set in Phase 2 as input context and produce useful results, the structure needs work.

---

## Validation Checkpoint

Before moving to Phase 2, the team validates that the Information Report is sufficient. This is a principle-driven review:

- **Security:** Does the report include enough information to begin threat modeling? Are compliance requirements identified? Are vulnerability patterns for candidate technologies documented?
- **Maintainability:** Does the report assess documentation quality, community health, testing ecosystems, and talent availability for candidate technologies?
- **Economics:** Does the report include actual cost data — licensing, infrastructure at scale, development velocity indicators? Are AI tooling costs estimated?
- **Operations:** Does the report cover deployment options, monitoring tooling, scaling characteristics, and integration patterns?
- **Scoring & Metrics:** Does the report include quantitative data that can support structured evaluation in Phase 2? Are benchmarks sourced and dated?
- **Correctness Verification:** Are confidence levels assigned to key findings? Are claims cross-referenced? Are research gaps explicitly identified?

If significant gaps exist, the team cycles back to the appropriate SDD step — adding research questions (Detail), generating new tasks (Task), or executing additional research (Implement). The SDD cycle is iterative. The validation checkpoint is where iteration is triggered, not where shortcuts are approved.

---

## What Comes Next

Phase 1 produces a structured Information Report that captures the technology landscape, competitive analysis, compliance requirements, risks, reusable components, and open questions. It is comprehensive but not conclusive — it presents options and evidence, not decisions.

Phase 2 transforms that evidence into decisions. The next article covers **Analysis & Stack Selection** — where the team uses the Information Report as input context for business analysis, cost modeling, stack evaluation, initial threat modeling, and benchmark definition. The SDD cycle runs again, but now the Specify step draws from the Information Report rather than from scratch. The decisions made in Phase 2 will constrain everything that follows.

---

*This is a living document. The tool sets, research patterns, and examples will be expanded and refined as the series develops. Every part of this framework is open to iteration.*

*Previous: [Article 2 — Building Your Toolkit: Tool Sets, SDD, and the Building Blocks]*
*Next in the series: [Article 4 — Phase 2: Analysis & Stack Selection]*
