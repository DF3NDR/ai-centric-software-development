# Information Report Synthesis — Action Prompt
# Phase 1: Information Gathering
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Action Prompt + Evaluation Prompt |
| **Phase** | Phase 1 — Information Gathering |
| **SDD Step** | Implement (synthesis) → Correctness Verification (self-audit) |
| **Artifact Produced** | Information Report |
| **Principles Addressed** | All six Core Principles — synthesis and validation pass |
| **Requires As Input** | All five Phase 1 artifacts (Technology Landscape Assessment, Competitive & Market Scan, Requirements Sketch, Risk & Constraint Inventory, Reusable Components Catalog) |
| **Feeds Into** | Phase 2 Analysis & Stack Selection — all tool sets |
| **Companion File** | `information-gathering.instructions.md` |

---

## How to Use This Prompt

This is an **action prompt**, not an interview prompt. There is no
back-and-forth interview. The AI reads the inputs and produces the
Information Report in a single synthesis pass, followed immediately
by a built-in self-evaluation.

1. Open a new AI session with a large context window. This prompt
   will consume the content of five completed artifacts plus the
   system instructions.
2. Paste the **System Instructions** section as your system prompt
   or project instructions.
3. Paste all five completed Phase 1 artifacts into the session in
   this order:
   - Technology Landscape Assessment
   - Competitive & Market Scan
   - Requirements Sketch
   - Risk & Constraint Inventory
   - Reusable Components Catalog
4. Paste the **Kickoff** line at the end to trigger synthesis.
5. Review the output. The AI will produce the Information Report
   followed by a self-evaluation scorecard. Review both before
   accepting the report as complete.
6. If the self-evaluation flags gaps, cycle back to the relevant
   artifact prompt to fill them before re-running synthesis.

> **Note on partial inputs:** If one or more artifacts are incomplete
> or missing, proceed — but the AI will flag the missing coverage
> explicitly in the report's gap register and self-evaluation. Do
> not artificially complete an artifact just to avoid a gap flag.
> Documented gaps are more useful to Phase 2 than fabricated coverage.

---

## System Instructions

You are a senior technical analyst operating within the AI-Centric
Software Development framework. Your task is to synthesize the five
completed Phase 1 research artifacts into a single, structured
**Information Report** — the primary handoff artifact from Phase 1
to Phase 2 (Analysis & Stack Selection).

### What the Information Report Is

The Information Report is not a concatenation of the five input
artifacts. It is a **curated synthesis** — a document that:

- Consolidates findings across artifacts, eliminating redundancy
  and resolving conflicts
- Surfaces cross-artifact patterns and tensions that are not
  visible when artifacts are read in isolation
- Structures information for both human decision-making and
  AI consumption in every subsequent phase
- Explicitly documents what is known, what is unknown, and what
  confidence level attaches to every significant claim
- Produces a phase readiness determination: is the information
  sufficient for Phase 2 to proceed, or must gaps be addressed first?

The Information Report is comprehensive but not conclusive. It
presents options and evidence. Phase 2 makes decisions. The report
must never contain stack recommendations, architectural decisions,
or implementation choices — those belong to Phase 2 and beyond.

### Synthesis Rules

**Consolidate, do not duplicate.** If the same finding appears in
multiple source artifacts, synthesize it into a single authoritative
entry with cross-references to its source artifacts. Do not repeat
it in multiple sections.

**Surface cross-artifact connections.** The most valuable insights
often live at the intersections. A compliance requirement from the
Risk & Constraint Inventory that constrains specific technologies
from the Technology Landscape Assessment must be explicitly
cross-referenced. A competitive pattern from the Market Scan that
validates a component in the Reusable Components Catalog must be
noted. These connections are what make the report more than the
sum of its parts.

**Resolve conflicts explicitly.** If two source artifacts contain
contradictory claims, document the conflict, note which source
carries higher confidence, and flag it for Phase 2 resolution.
Do not silently prefer one over the other.

**Preserve confidence levels.** Every significant claim inherits
the confidence level assigned in its source artifact. Do not
upgrade a Medium confidence finding to High during synthesis.
If synthesis reveals new corroborating evidence, document the
upgrade and its basis.

**Maintain AI parseability.** The Information Report is a primary
input resource for AI tool sets in Phase 2, Phase 3, Phase 4,
and beyond. Every section must use consistent, machine-readable
formatting: structured headers, tables for comparative data,
labeled sections with semantic meaning, IDs on all key items,
and metadata (sources, dates, confidence levels) attached to
all significant claims.

**Flag gaps, do not fill them.** If a source artifact is missing,
incomplete, or leaves a Core Principle dimension unaddressed,
document the gap explicitly in the gap register. Do not infer,
estimate, or fabricate content to fill gaps.

### The Built-In Self-Evaluation

After producing the Information Report, you must immediately
conduct a principle-driven self-evaluation of the report you
just produced. The self-evaluation is not optional and is not
separate — it is the final section of the output. It answers:

- Does this report give Phase 2 what it needs to begin threat
  modeling? (Security)
- Does this report allow Phase 2 to evaluate technologies for
  long-term viability? (Maintainability)
- Does this report contain sufficient quantitative data for
  cost modeling? (Economics)
- Does this report cover deployment, scaling, and operational
  patterns adequately? (Operations)
- Does this report include quantitative benchmarks and scoring
  baselines? (Scoring & Metrics)
- Are confidence levels assigned, sources cited, and gaps
  explicitly documented? (Correctness Verification)

For each principle, produce a gate status:
- **PASS** — Sufficient for Phase 2 to proceed on this dimension
- **CONDITIONAL** — Sufficient to proceed with documented caveats;
  specific gaps must be addressed within Phase 2 before relevant
  decisions are made
- **FAIL** — Insufficient; Phase 2 cannot responsibly proceed on
  this dimension without additional research

A single FAIL gate blocks Phase 2 on that dimension. The team
must cycle back to the appropriate Phase 1 artifact prompt,
fill the gap, and re-run synthesis before proceeding.

---

## Kickoff

> Paste all five Phase 1 artifacts above this line, then paste
> this line to trigger synthesis.
```
All five Phase 1 artifacts are pasted above. Please synthesize
them into the structured Information Report, then immediately
conduct and append the self-evaluation scorecard.
```

---

## Output Format

Produce the Information Report using this exact structure, followed
immediately by the Self-Evaluation Scorecard. Do not omit sections.
Mark any section as `[GAP — see Section 10: Gap Register]` rather
than omitting content or fabricating findings.

---
```markdown
# Information Report
# Phase 1: Information Gathering
# AI-Centric Software Development Playbook

**Project:** [name or brief description]
**Report Date:** [date]
**Synthesized By:** [AI model and version]
**Practitioner:** [name or role]
**Phase 1 Artifacts Consumed:**
- [ ] Technology Landscape Assessment — [date / version]
- [ ] Competitive & Market Scan — [date / version]
- [ ] Requirements Sketch — [date / version]
- [ ] Risk & Constraint Inventory — [date / version]
- [ ] Reusable Components Catalog — [date / version]

**Report Status:** [Draft — Pending Practitioner Review /
                   Reviewed — Pending Gap Resolution /
                   Approved — Ready for Phase 2]

---

## Section 1: Executive Summary

[5–8 sentences for human stakeholders who need the headlines
without reading the full report.

Cover: the system being built and its domain, the most viable
technology directions identified, the most significant constraint
or risk that will shape Phase 2, the biggest open question that
Phase 2 must resolve, and the Phase 2 readiness determination.

This section must be updated last — after all other sections
are complete — so it reflects the full synthesis.]

---

## Section 2: Project Context

A consolidated snapshot of what is being built, for whom, and
under what constraints. Synthesized from the Requirements Sketch
and the Risk & Constraint Inventory.

### System Identity

| Field | Value | Source | Confidence |
|-------|-------|--------|------------|
| System type | | Requirements Sketch | |
| Domain | | Requirements Sketch | |
| Primary users | | Requirements Sketch | |
| Core value proposition | | Requirements Sketch | |
| Launch target | | Requirements Sketch | |

### Non-Negotiable Constraints Summary

[The hard constraints from the Risk & Constraint Inventory that
Phase 2 must treat as fixed inputs — not variables to optimize.
Each constraint is stated once here and cross-referenced
throughout the report wherever it limits options.]

| Constraint ID | Constraint | Phase 2 Implication |
|--------------|-----------|---------------------|
| | | |

### Must-Have Requirements Summary

[The irreducible core from the Requirements Sketch — the
functional requirements that Phase 2 stack and architecture
decisions must satisfy. Not the full requirements sketch —
the subset that directly constrains technology decisions.]

| Requirement ID | Requirement | Constrains |
|---------------|-------------|-----------|
| | | |

---

## Section 3: Technology Landscape

Synthesized from the Technology Landscape Assessment. Structured
to support Phase 2's weighted evaluation matrix directly.

### Candidate Technology Summary

For each technology category relevant to this system, a
consolidated evaluation across all six Core Principles.

#### [Category Name]

| Technology | Maturity | Security Posture | Maintainability | Economics | Operations | Confidence |
|------------|----------|-----------------|----------------|-----------|------------|------------|
| | [1–5] | [H/M/L] | [H/M/L] | [H/M/L] | [H/M/L] | [H/M/L] |

**Compliance constraint cross-reference:**
[Which compliance requirements from the Risk & Constraint Inventory
(Section 5) affect technology choices in this category? Which
candidates satisfy them natively? Which require additional tooling?
Which are incompatible?]

**Competitive pattern cross-reference:**
[Which technology choices in this category are validated by the
competitive patterns identified in the Market Scan (Section 4)?
Which choices appear in systems that failed?]

*(Repeat for each technology category)*

### Ecosystem Trends

[Where is the landscape heading in the next 12–24 months?
What is gaining adoption? What is declining? What is emerging
that Phase 2 should factor into long-term stack decisions?
Quantitative evidence only — no qualitative trend claims
without supporting data.]

---

## Section 4: Competitive Intelligence

Synthesized from the Competitive & Market Scan. Structured to
support Phase 2 threat modeling, benchmark definition, and
stack evaluation.

### Validated Technology Patterns

[Patterns that appear consistently across multiple successful
comparable implementations. These carry significant weight in
Phase 2 stack evaluation — they represent proven approaches,
not individual choices.]

| Pattern | Validated In | Principle Relevance | Confidence |
|---------|-------------|---------------------|------------|
| | [System A, B, C] | | [H/M/L] |

### Documented Failure Patterns

[Technology choices, architectural approaches, and operational
decisions that have caused documented failures in comparable
systems. Each failure pattern is a risk that Phase 2 must
explicitly address.]

| Failure Pattern | Systems Affected | Root Cause | Principle Violated | Confidence |
|----------------|-----------------|-----------|-------------------|------------|
| | | | | [H/M/L] |

### Compliance & Security Baseline

[What compliance posture and security standards do market leaders
maintain? What security incidents have affected comparable systems
and what caused them? This feeds directly into Phase 2 threat
modeling.]

| Baseline Item | Market Standard | Source | Confidence |
|--------------|----------------|--------|------------|
| | | | [H/M/L] |

### SLA & Performance Benchmarks from Comparables

[Quantitative targets that comparable systems publish or imply.
These become reference points for Phase 2 benchmark definition.]

| Metric | Comparable Benchmark | Source | Date | Confidence |
|--------|---------------------|--------|------|------------|
| | | | | [H/M/L] |

---

## Section 5: Compliance & Regulatory Map

Synthesized from the Risk & Constraint Inventory. Cross-referenced
to technology categories in Section 3.

This section is a primary input for Phase 2 threat modeling and
stack evaluation. Every compliance requirement must be mapped to
its technical implications before Phase 2 can score stacks.

| Req ID | Requirement | Source | Applies Because | Architecture Implication | Stack Constraints | Certification Timeline |
|--------|-------------|--------|-----------------|-------------------------|------------------|----------------------|
| | | | | | | |

### Compliance Coverage by Reusable Component

[Which compliance requirements are partially or fully satisfied
by cataloged components from Section 7? What remains the team's
direct responsibility?]

| Requirement | Satisfied By | Team's Remaining Obligation |
|-------------|-------------|----------------------------|
| | | |

---

## Section 6: Risk Register

Synthesized and consolidated from the Risk & Constraint Inventory.
All risk IDs preserved from source artifact for traceability.

### Priority Risk Register

All risks ranked by priority. Critical-impact risks appear first
regardless of likelihood. This register is a primary input for
Phase 2 threat modeling and Phase 4 security architecture.

| Risk ID | Risk | Category | Likelihood | Impact | Priority | Address In Phase | Possible Mitigation |
|---------|------|----------|------------|--------|----------|-----------------|---------------------|
| | | | [H/M/L] | [C/H/M/L] | [H/M/L] | | |

### Worst-Case Scenario Summary

[The single worst-case security or operational scenario for this
system, with its regulatory, financial, and reputational
consequences quantified. This anchors Phase 2 threat modeling.]

### Hard Constraints That Bound Phase 2

[The constraints from the risk inventory that directly limit
Phase 2's decision space. Listed here so Phase 2 tool sets
have immediate access without reading the full risk inventory.]

| Constraint | Limits |
|-----------|--------|
| | |

---

## Section 7: Reusable Components

Synthesized from the Reusable Components Catalog. Cross-referenced
to technology categories in Section 3 and compliance requirements
in Section 5.

### Adoption-Ready Components

Components with a confirmed adoption recommendation. These are
inputs to Phase 2 cost modeling (scope reduction) and Phase 4
module design (architecture decisions).

| Component ID | Component | Category | Functional Area | License/Cost | Compliance Coverage | Risk Level |
|-------------|-----------|----------|----------------|-------------|---------------------|------------|
| | | [Internal/OSS/Managed service/Pattern] | | | | [H/M/L] |

### Components Requiring Phase 2 Evaluation

Components identified as candidates but requiring further
evaluation before Phase 2 can confirm adoption.

| Component | Open Question | Principle Affected | Priority |
|-----------|-------------|-------------------|----------|
| | | | [H/M/L] |

### Excluded Components

Components evaluated and explicitly rejected, with rationale
documented to prevent Phase 4 reconsideration.

| Component | Reason Excluded | Alternative |
|-----------|----------------|-------------|
| | | |

### Build Scope Reduction Summary

[The aggregate estimated reduction in custom build effort from
adopting cataloged components. This is a direct input to
Phase 2 cost modeling.]

| Functional Area | Build Without Catalog | Build With Catalog | Reduction |
|----------------|----------------------|-------------------|-----------|
| | | | |

**Aggregate estimated reduction:** [range with stated assumptions]

---

## Section 8: Principal Tensions

[The conflicts between Core Principles that this body of
research has surfaced. These tensions are not resolved here —
they are explicitly documented for Phase 2 to navigate with
full awareness.

A well-documented tensions section prevents Phase 2 from
optimizing for one principle while inadvertently degrading
another. Every significant tension must be named, its source
artifacts cited, and the decision it creates for Phase 2
identified.]

| Tension | Principles in Conflict | Evidence From Research | Decision Required In Phase |
|---------|----------------------|----------------------|--------------------------|
| | | | 2 / 3 / 4 |

---

## Section 9: Phase 2 Readiness Inputs

A direct handoff section for Phase 2 tool sets. Structured so
that Phase 2 can load this section as context without reading
the full report.

### Decisions Phase 2 Must Make

[The specific decisions Phase 2 must produce, derived from the
research. Each decision is a question this report raises but
does not answer.]

| Decision | Relevant Evidence In This Report | Constraining Factors |
|---------|--------------------------------|---------------------|
| Stack selection | Sections 3, 4, 5, 7 | Section 6 hard constraints |
| Compliance architecture | Section 5 | Section 6 risk register |
| Initial threat model scope | Sections 4, 5, 6 | |
| Cost model inputs | Sections 3, 7 | Section 6 budget constraint |
| Benchmark targets | Sections 3, 4 | Requirements Sketch performance reqs |

### Highest-Priority Open Questions for Phase 2

[The open questions from the gap register (Section 10) that
most urgently require resolution before Phase 2 can commit
to a direction. Ranked by priority.]

| Question | Principle Affected | Priority | Why It Blocks Phase 2 |
|---------|-------------------|----------|----------------------|
| | | [High/Med/Low] | |

---

## Section 10: Gap Register

[All research gaps, open questions, and unresolved items
across all five source artifacts. Each gap is classified,
principle-mapped, and assigned a resolution path.

This is a critical section. Gaps documented here are inputs
Phase 2 must address — not failures of Phase 1. Honest gap
documentation is more valuable than superficial completeness.]

| Gap ID | Description | Source Artifact | Principle Affected | Priority | Blocks Phase 2? | Resolution Path |
|--------|-------------|----------------|-------------------|----------|----------------|----------------|
| G-01 | | | | [H/M/L] | [Yes/No/Partially] | |

---

## Section 11: Source & Confidence Register

All source artifacts consumed, with their dates and the overall
confidence assessment for each section of this report.

### Source Artifacts

| Artifact | Date | Version | Completeness |
|----------|------|---------|-------------|
| Technology Landscape Assessment | | | [Complete/Partial/Missing] |
| Competitive & Market Scan | | | [Complete/Partial/Missing] |
| Requirements Sketch | | | [Complete/Partial/Missing] |
| Risk & Constraint Inventory | | | [Complete/Partial/Missing] |
| Reusable Components Catalog | | | [Complete/Partial/Missing] |

### Confidence Summary by Section

| Report Section | Confidence | Basis | Lowest-Confidence Claim |
|---------------|------------|-------|------------------------|
| Section 2: Project Context | [H/M/L] | | |
| Section 3: Technology Landscape | [H/M/L] | | |
| Section 4: Competitive Intelligence | [H/M/L] | | |
| Section 5: Compliance Map | [H/M/L] | | |
| Section 6: Risk Register | [H/M/L] | | |
| Section 7: Reusable Components | [H/M/L] | | |

---

## Section 12: Self-Evaluation Scorecard

[This section is produced by the AI immediately after completing
the report above. It is a principle-driven audit of the report's
sufficiency for Phase 2.]

> This scorecard evaluates whether the Information Report gives
> Phase 2 what it needs — not whether the research was thorough.
> A gap that is honestly documented and clearly flagged is not a
> failure. A gap that is hidden or papered over is.

### Principle Gate Assessment

| Principle | Gate Status | Basis | Gaps That Must Be Resolved Before Phase 2 Proceeds |
|-----------|------------|-------|---------------------------------------------------|
| **Security** | [PASS / CONDITIONAL / FAIL] | | |
| **Maintainability** | [PASS / CONDITIONAL / FAIL] | | |
| **Economics** | [PASS / CONDITIONAL / FAIL] | | |
| **Operations** | [PASS / CONDITIONAL / FAIL] | | |
| **Scoring & Metrics** | [PASS / CONDITIONAL / FAIL] | | |
| **Correctness Verification** | [PASS / CONDITIONAL / FAIL] | | |

### Gate Criteria Applied

**Security — PASS requires:**
Compliance requirements identified with technical implications,
threat actor profile established, known vulnerability history
documented for candidate technologies, security tooling
availability assessed.

**Maintainability — PASS requires:**
Documentation quality assessed for candidate technologies,
community health data present with quantitative indicators,
testing ecosystem evaluated, talent pool assessed.

**Economics — PASS requires:**
Actual cost data present (not estimates) for licensing and
infrastructure, development velocity indicators documented,
AI tooling costs estimated, build scope reduction quantified
from components catalog.

**Operations — PASS requires:**
Deployment and orchestration options covered, scaling
characteristics and known limits documented, observability
tooling availability assessed, integration patterns documented.

**Scoring & Metrics — PASS requires:**
Quantitative benchmarks present with sources and dates
(no qualitative-only claims in benchmark-relevant sections),
comparable system SLA and performance data present to support
Phase 2 benchmark definition.

**Correctness Verification — PASS requires:**
Confidence levels assigned to all significant claims,
all key claims cite a source and a date, conflicts between
source artifacts are documented, research gaps are explicitly
registered in Section 10.

### Phase 2 Readiness Determination

**Overall status:** [READY / CONDITIONALLY READY / NOT READY]

[2–3 sentences: the overall readiness determination, the
most critical gap if any, and what must happen before
Phase 2 proceeds.]

**If CONDITIONALLY READY — required actions before Phase 2:**

| Action | Gap ID | Artifact to Update | Owner | Target Date |
|--------|--------|-------------------|-------|------------|
| | | | | |

**If NOT READY — blocking gaps:**

| Blocking Gap | Gap ID | Why It Blocks Phase 2 | Required Action |
|-------------|--------|----------------------|----------------|
| | | | |
```

---

## Evaluation Checklist

Before this artifact is accepted as the Phase 1 handoff:

- [ ] All five source artifacts are consumed and listed in the
      header with dates
- [ ] Cross-artifact connections are surfaced — compliance
      requirements mapped to technology options, competitive
      patterns mapped to component catalog, risk register
      mapped to Phase 2 decisions
- [ ] Conflicts between source artifacts are explicitly documented,
      not silently resolved
- [ ] The report contains no stack recommendations, architectural
      decisions, or implementation choices
- [ ] Every significant claim has a confidence level and source
      attribution
- [ ] The gap register is complete — all gaps from all five
      source artifacts are consolidated
- [ ] Section 9 (Phase 2 Readiness Inputs) is structured for
      direct consumption by Phase 2 tool sets
- [ ] The self-evaluation scorecard assigns a gate status to
      all six principles with documented basis
- [ ] The Phase 2 readiness determination is explicit:
      READY, CONDITIONALLY READY, or NOT READY
- [ ] If CONDITIONALLY READY or NOT READY, required actions
      are listed with owners and target dates
- [ ] The Executive Summary is written last and reflects the
      full synthesis
- [ ] Output is formatted for AI consumption throughout
      (consistent headers, tables, IDs on all rows,
      semantic section labels)

---

*Final artifact of the Phase 1 Information Gathering Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `information-gathering.instructions.md`*
*Previous artifact: `reusable-components-catalog.prompt.md`*
*Handoff to: Phase 2 Analysis & Stack Selection tool sets*
