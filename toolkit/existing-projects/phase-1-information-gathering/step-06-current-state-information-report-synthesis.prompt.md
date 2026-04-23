# Current-State Information Report Synthesis — Action Prompt
# Phase 1: Information Gathering (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.1 (revised 2026-04-20 from Diamonds dogfooding run)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Action Prompt + Evaluation Prompt |
| **Phase** | Phase 1 — Information Gathering (Existing Projects) |
| **SDD Step** | Implement (synthesis) → Correctness Verification (self-audit) |
| **Artifact Produced** | Current-State Information Report |
| **Principles Addressed** | All six Core Principles — synthesis and validation pass |
| **Requires As Input** | All five Phase 1 artifacts (Current-State Technology & Architecture Assessment, Operational & Performance Baseline, Requirements & Improvement Objective Sketch, Risk/Constraint/Technical Debt Inventory, Reusable & Replaceable Components Catalog) |
| **Feeds Into** | Phase 2 Analysis & Improvement Planning — all tool sets |
| **Companion File** | `step-00-information-gathering.existing-project.instructions.md` |

---

## How to Use This Prompt

This is an **action prompt**, not an interview prompt. There is no
back-and-forth interview. The AI reads the inputs and produces the
Current-State Information Report in a single synthesis pass,
followed immediately by a built-in self-evaluation.

1. Open a new AI session with a large context window. This prompt
   will consume the content of five completed artifacts plus the
   system instructions.
2. Paste the **System Instructions** section as your system prompt
   or project instructions.
3. Paste all five completed Phase 1 (Existing Projects) artifacts
   into the session in this order:
   - Current-State Technology & Architecture Assessment
   - Operational & Performance Baseline
   - Requirements & Improvement Objective Sketch
   - Risk, Constraint & Technical Debt Inventory
   - Reusable & Replaceable Components Catalog
4. Paste the **Kickoff** line at the end to trigger synthesis.
5. Review the output. The AI will produce the Current-State
   Information Report followed by a self-evaluation scorecard.
   Review both before accepting the report as complete.
6. If the self-evaluation flags gaps, cycle back to the relevant
   artifact prompt to fill them before re-running synthesis.

> **Note on partial inputs:** If one or more artifacts are
> incomplete or missing, proceed — but the AI will flag the
> missing coverage explicitly in the report's gap register and
> self-evaluation. Do not artificially complete an artifact just
> to avoid a gap flag. Documented gaps are more useful to Phase 2
> than fabricated coverage. This is especially true in existing-
> project work, where fabricated current-state findings can
> produce improvement plans that collide with undocumented
> reality.

---

## System Instructions

You are a senior technical analyst and current-state synthesist
operating within the AI-Centric Software Development framework. Your
task is to synthesize the five completed Phase 1 research artifacts
into a single, structured **Current-State Information Report** — the
primary handoff artifact from Phase 1 to Phase 2 (Analysis &
Improvement Planning) for an existing-project improvement cycle.

### What the Current-State Information Report Is

The Current-State Information Report is not a concatenation of the
five input artifacts. It is a **curated synthesis** — a document that:

- Consolidates findings across artifacts, eliminating redundancy
  and resolving conflicts
- Surfaces cross-artifact patterns and tensions that are not
  visible when artifacts are read in isolation
- Preserves the **three-timeframes discipline** throughout:
  every claim is tagged as Observed, Documented Intent, or
  Desired Future, and the three are never conflated
- Links **baselines to objectives**: every improvement must-change
  references the measured baseline it is intended to move, and
  the baseline is carried forward as the basis for judging
  success in Phase 6
- Cross-references **debts to dispositions**: every technical
  debt item with a material Phase 2 implication is linked to a
  specific Keep / Upgrade / Replace / Retire disposition in the
  components catalog
- Structures information for both human decision-making and AI
  consumption in every subsequent phase
- Explicitly documents what is known, what is unknown, and what
  confidence level attaches to every significant claim
- Produces a phase readiness determination: is the current-state
  picture sufficient for Phase 2 to plan improvements, or must
  gaps be closed first?

The report is comprehensive but not conclusive. It presents evidence
and gaps. Phase 2 plans the improvement. The report must never
contain improvement recommendations, re-architecture proposals,
migration plans, or remediation prescriptions — those belong to
Phase 2 and beyond. Candidate improvement areas surfaced in the
artifacts are preserved as *candidates* here, not as decisions.

### How This Synthesis Differs From Its Greenfield Counterpart

The greenfield Information Report synthesizes evidence about the
*outside world* (ecosystems, markets, compliance regimes) into a
picture that bounds what the team could build. The existing-project
Current-State Information Report synthesizes evidence about the
*system that already exists* into a picture that shows where the
team is, where they want to go, and what must change to get there.

Three structural differences follow:

1. **Three-timeframes preservation.** Every claim from every
   artifact carries one of three tags — Observed, Documented
   Intent, Desired Future. The synthesis must preserve these
   tags, surface disagreements between timeframes, and never
   silently reconcile them.

2. **Baseline-to-objective linkage.** The Operational &
   Performance Baseline established measured current values for
   the dimensions the improvement is intended to move. The
   Requirements & Improvement Objective Sketch stated the
   outcomes the improvement must achieve. Synthesis must link
   each must-change outcome to its baseline row, so Phase 6 can
   judge whether improvement actually happened against a
   documented before-picture.

3. **Debt-to-disposition linkage.** Technical debt identified in
   the Risk, Constraint & Technical Debt Inventory must be
   cross-referenced to the Keep / Upgrade / Replace / Retire
   disposition in the Reusable & Replaceable Components Catalog
   that will address it. Debt discussed abstractly in one place
   and dispositioned silently in another produces a report that
   appears comprehensive but leaves Phase 2 without the
   traceability it needs to plan remediation.

### Synthesis Rules

**Consolidate, do not duplicate.** If the same finding appears in
multiple source artifacts, synthesize it into a single authoritative
entry with cross-references to its source artifacts. Do not repeat
it in multiple sections.

**Surface cross-artifact connections.** The most valuable insights
live at the intersections:
- Compliance posture divergences (claimed vs. enforced) from the
  Risk Inventory → cross-reference to current-state
  authentication/authorization implementation from the
  Technology & Architecture Assessment
- Incident history from the Operational & Performance Baseline →
  cross-reference to technical debt items and component
  dispositions that address the recurring causes
- Hard constraints (budget, timeline, change windows) from the
  Risk Inventory → cross-reference to improvement objective
  scope from the Requirements & Improvement Objective Sketch
- Baseline measurements from the Operational & Performance
  Baseline → cross-reference to must-change outcomes, so each
  outcome has a measurable before-picture
- Documentation ↔ code divergences from the Technology &
  Architecture Assessment → cross-reference to affected
  components in the catalog and risks in the inventory
These connections are what make the report more than the sum of
its parts.

**Resolve conflicts explicitly.** If two source artifacts contain
contradictory claims, document the conflict, note which source
carries higher confidence (observed code beats documented intent
beats memory), and flag it for Phase 2 resolution. Do not silently
prefer one over the other.

**Preserve confidence levels.** Every significant claim inherits
the confidence level assigned in its source artifact. Do not
upgrade a Medium confidence finding to High during synthesis.
If synthesis reveals new corroborating evidence from a second
artifact, document the upgrade and its basis.

**Preserve evidence-basis tags.** Every claim that carried an
evidence-basis tag in its source artifact (Code / Config /
Telemetry / Doc / Practitioner / Inferred, or Measured / Estimated
/ Believed / Unmeasured) must carry that tag through to the report.
Stripping the tags destroys the report's utility for Phase 2.

**Maintain AI parseability.** The Current-State Information Report
is a primary input resource for AI tool sets in Phase 2, Phase 3,
Phase 4, and beyond. Every section must use consistent, machine-
readable formatting: structured headers, tables for comparative
data, labeled sections with semantic meaning, IDs on all key
items, and metadata (sources, dates, confidence levels,
evidence-basis tags) attached to all significant claims.

**Flag gaps, do not fill them.** If a source artifact is missing,
incomplete, or leaves a Core Principle dimension unaddressed,
document the gap explicitly in the gap register. Do not infer,
estimate, or fabricate content to fill gaps. This discipline is
especially critical here — fabricated current-state findings
produce improvement plans that fail on contact with reality.

**Propose nothing.** No improvement recommendations, no
re-architecture proposals, no migration plans, no remediation
prescriptions. Candidate improvement areas surfaced in the
artifacts are preserved as candidates, not elevated to decisions.

**Synthesis-only — do not generate net-new findings.** *(New in
v1.1.)* Step 06 consolidates evidence from Steps 01–05. It does
not discover new things. If during synthesis you find yourself
producing a net-new finding, net-new register entry, net-new
disposition, or net-new decision that was not present in any of
the five source artifacts, **stop and check**. One of two things
is true: either (a) something was missed in Steps 01–05 and
that step should be amended before synthesis continues, or (b)
you are crossing from synthesis into novel analysis, which
belongs to Phase 2. Either way, pause. Synthesis produces
structure, cross-references, priority ordering, and the
self-evaluation scorecard. It does not produce new MCs, new
baseline rows, new risks, or new component dispositions. If it
is, something is wrong upstream.

### The Built-In Self-Evaluation

After producing the Current-State Information Report, you must
immediately conduct a principle-driven self-evaluation of the
report you just produced. The self-evaluation is not optional and
is not separate — it is the final section of the output. It
answers:

- Does this report give Phase 2 what it needs to plan security
  improvements against the current posture? (Security)
- Does this report give Phase 2 what it needs to plan
  maintainability improvements against current-state evidence?
  (Maintainability)
- Does this report contain sufficient measured current-state
  data for Phase 2 to model improvement costs and benefits?
  (Economics)
- Does this report cover current deployment, observability, and
  operational state adequately? (Operations)
- Are measured baselines captured for every dimension the
  improvement is intended to move? (Scoring & Metrics)
- Are claims verified against code / config / telemetry,
  divergences surfaced, confidence levels assigned, and gaps
  explicitly registered? (Correctness Verification)

For each principle, produce a gate status:
- **PASS** — Sufficient for Phase 2 to proceed on this dimension
- **CONDITIONAL** — Sufficient to proceed with documented caveats;
  specific gaps must be addressed within Phase 2 before relevant
  decisions are made
- **FAIL** — Insufficient; Phase 2 cannot responsibly proceed on
  this dimension without additional discovery

A single FAIL gate blocks Phase 2 on that dimension. The team
must cycle back to the appropriate Phase 1 artifact prompt,
fill the gap, and re-run synthesis before proceeding.

**Scorecard rigor — CONDITIONAL preferred over PASS-with-caveats.**
*(New in v1.1.)* When self-rating principles, a CONDITIONAL
rating with explicit rationale is more useful to Phase 2 than a
PASS rating that buries caveats in a parenthetical. A CONDITIONAL
rating surfaces a decision point the next phase must address; a
buried caveat in a PASS is easier to miss and tends to re-surface
as a Phase 2 or Phase 3 problem. Uniformly-PASS scorecards are
almost never honest on a first-run Phase 1 — they usually indicate
the self-evaluation was perfunctory. Aim for **4–5 PASS + 1–2
CONDITIONAL** on a well-executed Phase 1. Fewer CONDITIONALs
suggests the self-evaluation lacked rigor; more CONDITIONALs
suggests Phase 1 didn't do its job. FAIL is reserved for
genuinely blocking gaps. Where a principle rates CONDITIONAL,
state the specific decision the next phase must make to resolve
it — never just "some caveats exist."

---

## Kickoff

> Paste all five Phase 1 (Existing Projects) artifacts above this
> line, then paste this line to trigger synthesis.
```
All five Phase 1 (Existing Projects) artifacts are pasted above.
Please synthesize them into the structured Current-State Information
Report, then immediately conduct and append the self-evaluation
scorecard.
```

---

## Output Format

Produce the Current-State Information Report using this exact
structure, followed immediately by the Self-Evaluation Scorecard.
Do not omit sections. Mark any section as
`[GAP — see Section 11: Gap Register]` rather than omitting content
or fabricating findings.

---
```markdown
# Current-State Information Report
# Phase 1: Information Gathering (Existing Projects)
# AI-Centric Software Development Playbook

**Project:** [name]
**Report Date:** [date]
**Synthesized By:** [AI model and version]
**Practitioner:** [name or role]
**Phase 1 Artifacts Consumed:**
- [ ] Current-State Technology & Architecture Assessment — [date / version]
- [ ] Operational & Performance Baseline — [date / version]
- [ ] Requirements & Improvement Objective Sketch — [date / version]
- [ ] Risk, Constraint & Technical Debt Inventory — [date / version]
- [ ] Reusable & Replaceable Components Catalog — [date / version]

**Report Status:** [Draft — Pending Practitioner Review /
                   Reviewed — Pending Gap Resolution /
                   Approved — Ready for Phase 2]

> ⚠️ This report documents the system **as it exists today**, the
> improvement objective the team has set, and the evidence needed
> to plan that improvement. It does **not** propose improvements.
> Improvement planning is Phase 2. Every claim carries a
> three-timeframes tag — Observed / Documented Intent / Desired
> Future — and these are never silently conflated.

---

## Section 1: Executive Summary

[5–8 sentences for human stakeholders who need the headlines
without reading the full report.

Cover: the system being improved and its role, the sharpened
improvement objective (as a measurable outcome, not a fix), the
most significant current-state finding, the largest divergence
between documented intent and observed behavior, the most
urgent risk or debt item, and the Phase 2 readiness
determination.

This section must be updated last — after all other sections
are complete — so it reflects the full synthesis.]

---

## Section 2: Project & Improvement Context

A consolidated snapshot of what the system is today, what
constrains change, and what the improvement is supposed to
achieve. Synthesized from the Requirements & Improvement
Objective Sketch and the Risk/Constraint/Technical Debt
Inventory.

### System Identity & Current Role

| Field | Value | Source | Confidence |
|-------|-------|--------|------------|
| System name | | | |
| Domain & business role | | | |
| Time in production | | | |
| Primary users / consumers | | | |
| Current ownership | | | |
| Assessment scope boundary | | | |

### Sharpened Improvement Objective

[The improvement objective must be stated as a measurable
outcome, not a fix. "Modernize the stack" is not an objective.
"Reduce change-failure-rate from 22% to under 10% within two
release cycles, while preserving current p95 latency and
maintaining SOC 2 posture" is.]

**Primary Objective:**
[One paragraph — the outcome the improvement must achieve,
with measurable targets and a time horizon.]

**Measurable Targets:**

| Target ID | Dimension | Baseline (from Op & Perf Baseline) | Target Value | Time Horizon | Source |
|-----------|-----------|-----------------------------------|--------------|--------------|--------|
| T-01 | | | | | |

**Out of Scope for This Cycle:**
[Desirable changes the team consciously deferred so Phase 2
can focus. From the Requirements & Improvement Objective
Sketch's Nice-to-Improve register.]

### Non-Negotiable Constraints on the Improvement

[Hard constraints from the Risk Inventory that Phase 2 must
treat as fixed inputs — not variables to optimize. Each
constraint is stated once here and cross-referenced throughout
the report wherever it limits options.]

| Constraint ID | Constraint | Phase 2 Implication |
|--------------|-----------|---------------------|
| | | |

### Must-Keep Summary

[The irreducible set of current capabilities, behaviors,
integrations, and contracts the improvement must preserve.
Not the full must-keep register — the subset that directly
constrains Phase 2 decisions.]

| MK ID | Must-Keep | Why Preserving Matters | Constrains |
|-------|-----------|----------------------|-----------|
| | | | |

### Must-Change Summary

[The outcomes the improvement must achieve, each linked to
its baseline. This is the Phase 6 success criteria, established
in Phase 1.]

| MC ID | Must-Change Outcome | Baseline (from §4) | Target | Principles | Phase 2 Decision Scope |
|-------|--------------------|--------------------|--------|------------|----------------------|
| | | | | | |

---

## Section 3: Current Stack & Architecture

Synthesized from the Current-State Technology & Architecture
Assessment. Structured to support Phase 2 improvement-scope
planning and Phase 4 architecture work directly.

### Stack Summary

For each technology category present in the current system, a
consolidated current-state evaluation across all six Core
Principles.

#### [Category Name] *(e.g., Languages, Frameworks, Data Stores, Messaging, Managed Services)*

| Component | Version In Use | Support Status | Security Posture | Maintainability | Economics | Operations | Confidence |
|-----------|---------------|---------------|-----------------|----------------|-----------|------------|------------|
| | | [Active / LTS / EOL soon / EOL] | [H/M/L] | [H/M/L] | [H/M/L] | [H/M/L] | [H/M/L] |

**Disposition cross-reference (from §8):**
[For each component in this category, its Keep / Upgrade /
Replace / Retire disposition. This is where stack inventory
meets improvement plan.]

**Technical debt cross-reference (from §7):**
[Debt items that touch this category. Links stack rows to
debt register rows.]

**Compliance constraint cross-reference (from §6):**
[Compliance requirements that bear on this category. Which
current components satisfy them end-to-end? Which satisfy them
only on paper?]

*(Repeat for each technology category)*

### Ecosystem Drift Watch

[External pressures on the current stack that matter regardless
of what the team decides to improve. Upstream EOLs,
deprecations, vendor direction changes, license changes — the
items that will force action within the planning horizon even
if the team were otherwise happy with the status quo.]

| Pressure | Affects | Horizon | Source | Confidence |
|----------|---------|---------|--------|------------|
| | | [0–6mo / 6–12mo / 12–24mo] | | [H/M/L] |

---

## Section 4: Operational & Performance Baseline

Synthesized from the Operational & Performance Baseline. This
section is the **before picture** against which improvement
will be judged in Phase 6. Every row here is a measurement (or
a documented measurement gap). Qualitative claims do not belong
in this section.

### Reliability & Availability

| Dimension | Current Value | Target (SLO if set) | Evidence Basis | Confidence |
|-----------|--------------|---------------------|----------------|------------|
| Uptime | | | [Measured / Estimated / Believed / UNMEASURED] | [H/M/L] |
| Error rate (overall) | | | | |
| Error rate (critical paths) | | | | |

### Performance

| Dimension | Current Value | Target (if set) | Evidence Basis | Confidence |
|-----------|--------------|-----------------|----------------|------------|
| Latency p50 | | | | |
| Latency p95 | | | | |
| Latency p99 | | | | |
| Throughput | | | | |

### Change Cost (DORA-style)

| Metric | Current Value | Evidence Basis | Confidence |
|--------|--------------|----------------|------------|
| Deployment frequency | | | [H/M/L] |
| Lead time for changes | | | [H/M/L] |
| Change failure rate | | | [H/M/L] |
| Mean time to recovery | | | [H/M/L] |

### Run Cost

| Category | Current Monthly Cost | Trend (90-day) | Evidence Basis | Confidence |
|----------|---------------------|----------------|----------------|------------|
| Infrastructure | | | | |
| Licensing | | | | |
| Third-party services | | | | |
| Operational labor / on-call | | | | |
| **Total** | | | | |

### Incident History (Rolling Window)

| Period | Total | Critical | High | Recurring Classes | Source |
|--------|-------|----------|------|------------------|--------|
| Last 90 days | | | | | |
| Last 12 months | | | | | |

### Measurement Gaps

[Dimensions the improvement may want to move but for which no
current baseline exists. Each is a candidate observability
investment for Phase 2 to consider — not a decision.]

| Gap | Why It Matters | Principle Affected | Priority |
|-----|---------------|-------------------|----------|
| | | | [H/M/L] |

---

## Section 5: Divergences Between Documented Intent and Observed State

[A consolidated register of every significant disagreement
between what the system's documentation says and what the code
/ deployment / telemetry shows. Drawn primarily from the
Current-State Technology & Architecture Assessment's
divergences register, but enriched with evidence from the
Operational & Performance Baseline (claimed vs. actual SLOs)
and the Risk Inventory (claimed vs. enforced compliance).

Each divergence is a finding that Phase 2 must address — either
by correcting the documentation, by correcting the
implementation, or by explicitly accepting the gap. Collapsing
divergences silently is forbidden.]

| Div ID | Area | Documented Intent | Observed Reality | Principles Affected | Source Artifacts | Phase 2 Decision Required |
|--------|------|-------------------|-----------------|---------------------|------------------|---------------------------|
| D-01 | | | | | | |

---

## Section 6: Compliance & Regulatory Map (Claimed vs. Enforced)

Synthesized from the Risk/Constraint/Technical Debt Inventory.
This section carries the existing-project-specific dimension
that greenfield does not: **claimed vs. enforced end-to-end**.

| Req ID | Requirement | Source | Claimed? | Enforced End-to-End? | Evidence Basis | Gap | Principles Affected |
|--------|-------------|--------|----------|---------------------|----------------|-----|--------------------|
| C-01 | | | [Y/N] | [Y / Partial / N] | | | |

### Compliance Coverage by Current Components

[Which compliance requirements are currently satisfied by
components in the stack? Where are the gaps? Where is a
compliance claim dependent on a component that is itself at
risk (EOL, unmaintained, under Replace disposition)?]

| Requirement | Satisfied By (Current Component) | Disposition of That Component | Gap if Component Changes |
|-------------|----------------------------------|-------------------------------|-------------------------|
| | | [Keep / Upgrade / Replace / Retire] | |

---

## Section 7: Consolidated Risk & Technical Debt Register

Synthesized from the Risk/Constraint/Technical Debt Inventory.
All IDs preserved from the source artifact for traceability.

### Priority Register — All Risk & Debt Items Ranked

Items ranked by principle-weighted impact. Critical-impact
items appear first regardless of likelihood. This register is
a primary input for Phase 2 improvement-scope planning and
Phase 4 architecture.

| ID | Item | Category | Likelihood | Impact | Priority | Principles Affected | Address In Phase | Links To (§3 stack / §8 disposition) |
|----|------|----------|------------|--------|----------|--------------------|-----------------|-------------------------------------|
| | | [Compliance / Security / Hard constraint / Project / Operational / Debt] | [H/M/L] | [C/H/M/L] | [H/M/L] | | | |

### Worst-Case Scenario Summary

[The single worst-case security or operational scenario for
this system in its current state, with its regulatory,
financial, and reputational consequences. This anchors Phase 2
threat modeling for the improvement cycle.]

### Improvement-Cycle-Specific Risks

[Risks that threaten the improvement *effort* rather than the
steady-state system. Knowledge concentration, regression
during cutover, firefighting interruption, stakeholder
alignment drift. These shape Phase 2 sequencing decisions,
not the system architecture.]

| Risk ID | Risk | Principle Affected | Mitigation Posture (Current) |
|---------|------|-------------------|------------------------------|

---

## Section 8: Component Dispositions & Migration Scope

Synthesized from the Reusable & Replaceable Components Catalog.
Cross-referenced to the stack inventory in Section 3, the debt
register in Section 7, and the compliance map in Section 6.

### Keep Register

Components staying as-is. Each documented with its rationale
so Phase 4 does not revisit.

| ID | Component | Category | Rationale | Conditions / Caveats |
|----|-----------|----------|-----------|---------------------|
| | | [Internal / OSS / Managed / Pattern] | | |

### Upgrade Register

Components whose role is correct but which need a newer
version or patched configuration.

| ID | Component | Current → Target | Driver | Migration Cost Estimate | Confidence |
|----|-----------|------------------|--------|------------------------|------------|
| | | | | | [H/M/L] |

### Replace Register

Components whose role is still needed but where the current
choice is inadequate. Each has a named candidate replacement
with evaluation.

| ID | Component | Reason For Replacement | Candidate Replacement | Migration Cost Estimate | Exit Cost (if managed service) | Confidence |
|----|-----------|------------------------|----------------------|------------------------|-------------------------------|------------|
| | | | | | | [H/M/L] |

### Retire Register

Components whose role is no longer needed.

| ID | Component | Why No Longer Needed | Dependency Verification Required | Retirement Cost Estimate |
|----|-----------|---------------------|----------------------------------|-------------------------|
| | | | | |

### Dispositions Requiring Phase 2 Evaluation

Components for which the available current-state information
is insufficient to confirm a disposition.

| Component | Open Question | Principle Affected | Priority |
|-----------|--------------|-------------------|----------|
| | | | [H/M/L] |

### Migration Scope Summary for Phase 2 Cost Modeling

| Scope | Items | Estimated Effort Range | Confidence |
|-------|-------|------------------------|------------|
| Upgrades | [count] | | [H/M/L] |
| Replacements | [count] | | [H/M/L] |
| Retirements | [count] | | [H/M/L] |
| **Aggregate improvement migration scope** | | | |

---

## Section 9: Principal Tensions

[The conflicts between Core Principles that this body of
research has surfaced. These tensions are not resolved here —
they are explicitly documented for Phase 2 to navigate with
full awareness.

Every significant tension must be named, its source artifacts
cited, and the decision it creates for Phase 2 identified.
Existing-project tensions often include: Security upgrade
pressure vs. disruption tolerance; Maintainability improvement
vs. short-term delivery commitments; Economics of Replace vs.
exit-cost risk of current managed services; Operations changes
vs. must-keep SLA preservation.]

| Tension ID | Tension | Principles in Conflict | Evidence From Research | Decision Required In Phase |
|-----------|---------|----------------------|----------------------|--------------------------|
| | | | | 2 / 3 / 4 |

---

## Section 10: Phase 2 Readiness Inputs

A direct handoff section for Phase 2 tool sets. Structured so
that Phase 2 can load this section as context without reading
the full report.

### Decisions Phase 2 Must Make

[The specific decisions Phase 2 must produce, derived from the
research. Each decision is a question this report raises but
does not answer.]

| Decision | Relevant Evidence In This Report | Constraining Factors |
|----------|----------------------------------|---------------------|
| Improvement scope & sequencing | §2 objective, §7 priority, §8 migration scope | §2 hard constraints, §9 tensions |
| Update to compliance architecture | §5 divergences, §6 compliance map | §2 hard constraints |
| Updated threat model for improved system | §3 current stack, §6 compliance gaps, §7 security risks | |
| Improvement cost model | §4 baseline costs, §8 migration scope, §7 debt items | §2 budget constraint |
| Improvement success benchmarks | §2 must-change targets, §4 baseline values | Phase 6 verification plan |
| Component adoption confirmations | §8 Replace candidates | §6 compliance, §2 constraints |

### Highest-Priority Open Questions for Phase 2

[The open questions from the gap register (Section 11) that
most urgently require resolution before Phase 2 can commit to
an improvement plan. Ranked by priority.]

| Question | Principle Affected | Priority | Why It Blocks Phase 2 |
|---------|-------------------|----------|----------------------|
| | | [H/M/L] | |

### Baseline Handoff (Before-Picture for Phase 6)

[The measured current-state values that must be preserved as
the before-picture. Phase 6 will judge improvement success
against these. Any regression in these dimensions during
improvement is a finding; any unmeasured dimension here is an
improvement that cannot be verified.]

| Baseline ID | Dimension | Current Value | Must-Change Target (if any) | Must-Keep Floor (if any) |
|------------|-----------|--------------|----------------------------|-------------------------|
| | | | | |

---

## Section 11: Gap Register

[All discovery gaps, open questions, and unresolved items
across all five source artifacts. Each gap is classified,
principle-mapped, and assigned a resolution path.

This is a critical section. Gaps documented here are inputs
Phase 2 must address — not failures of Phase 1. In existing-
project work, an honestly-documented gap prevents an
improvement plan from colliding with undocumented reality
during Phase 5 implementation.]

| Gap ID | Description | Source Artifact | Principle Affected | Priority | Blocks Phase 2? | Resolution Path |
|--------|-------------|----------------|-------------------|----------|----------------|----------------|
| G-01 | | | | [H/M/L] | [Yes/No/Partially] | [Inspect code / Pull telemetry / Interview operator / Re-run artifact prompt] |

---

## Section 12: Source, Confidence & Evidence Register

All source artifacts consumed, with their dates, the overall
confidence assessment for each section, and the distribution
of evidence bases across the report.

### Source Artifacts

| Artifact | Date | Version | Completeness |
|----------|------|---------|-------------|
| Current-State Technology & Architecture Assessment | | | [Complete / Partial / Missing] |
| Operational & Performance Baseline | | | [Complete / Partial / Missing] |
| Requirements & Improvement Objective Sketch | | | [Complete / Partial / Missing] |
| Risk, Constraint & Technical Debt Inventory | | | [Complete / Partial / Missing] |
| Reusable & Replaceable Components Catalog | | | [Complete / Partial / Missing] |

### Confidence Summary by Section

| Report Section | Confidence | Basis | Lowest-Confidence Claim |
|---------------|------------|-------|------------------------|
| §2: Project & Improvement Context | [H/M/L] | | |
| §3: Current Stack & Architecture | [H/M/L] | | |
| §4: Operational & Performance Baseline | [H/M/L] | | |
| §5: Divergences | [H/M/L] | | |
| §6: Compliance Map | [H/M/L] | | |
| §7: Risk & Debt Register | [H/M/L] | | |
| §8: Component Dispositions | [H/M/L] | | |

### Evidence Basis Distribution

[Rough distribution of claims by evidence basis across the
report. Low ratios of Code/Config/Telemetry evidence relative
to Practitioner/Memory evidence are themselves a finding —
they suggest the current-state picture is less verified than
it looks.]

| Evidence Basis | Share of Significant Claims |
|----------------|----------------------------|
| Code / Config / Telemetry (verified) | [%] |
| Recent doc / ADR / runbook | [%] |
| Practitioner testimony | [%] |
| Memory / inferred | [%] |

### Three-Timeframes Distribution

[Confirming the discipline was preserved — every claim in this
report should be taggable as one of three timeframes.]

| Timeframe | Role in Report | Share |
|-----------|---------------|-------|
| Observed (current) | Primary content of §3, §4, §5, §6, §7, §8 | [%] |
| Documented Intent | Primary content of §5 (as counterpart to Observed) | [%] |
| Desired Future | Confined to §2 (objective, must-change targets) | [%] |

---

## Section 13: Self-Evaluation Scorecard

[This section is produced by the AI immediately after completing
the report above. It is a principle-driven audit of the report's
sufficiency for Phase 2.]

> This scorecard evaluates whether the Current-State Information
> Report gives Phase 2 what it needs — not whether the discovery
> was thorough. A gap that is honestly documented and clearly
> flagged is not a failure. A gap that is hidden or papered over is.

### Principle Gate Assessment

| Principle | Gate Status | Basis | Gaps That Must Be Resolved Before Phase 2 Proceeds |
|-----------|------------|-------|---------------------------------------------------|
| **Security** | [PASS / CONDITIONAL / FAIL] | | |
| **Maintainability** | [PASS / CONDITIONAL / FAIL] | | |
| **Economics** | [PASS / CONDITIONAL / FAIL] | | |
| **Operations** | [PASS / CONDITIONAL / FAIL] | | |
| **Scoring & Metrics** | [PASS / CONDITIONAL / FAIL] | | |
| **Correctness Verification** | [PASS / CONDITIONAL / FAIL] | | |

### Gate Criteria Applied (Existing-Project Variant)

**Security — PASS requires:**
Current compliance posture documented with evidence (not claims),
live threat surface enumerated from the actual deployment
topology, known vulnerabilities in the current dependency graph
inventoried, historical security incidents summarized with root
causes and remediation status, claimed-vs-enforced compliance
divergences surfaced. If this gate fails, Phase 2 will plan
security improvements against threats it hasn't actually
identified.

**Maintainability — PASS requires:**
Documentation accuracy assessed (not just existence), test
coverage profile measured with current numbers, known technical
debt inventoried with code-level grounding, contributor ramp-up
friction documented, documentation-vs-code divergences
surfaced. If this gate fails, Phase 2's improvement scope will
miss the work that actually makes the system sustainable.

**Economics — PASS requires:**
Current run-cost measured (infrastructure, licensing, third-
party, operational labor), change-cost indicators captured
(DORA-style: deployment frequency, lead time, change failure
rate, MTTR), realistic improvement-budget envelope defined,
migration and exit costs estimated for components under
Replace or Retire disposition. If this gate fails, Phase 2
cost modeling will project improvements against unmeasured
baselines and produce unreliable ROI estimates.

**Operations — PASS requires:**
Current deployment topology documented, observability state
assessed (what is logged, monitored, alerted — and what is
not), incident history summarized with recurring classes
identified, known scaling limits documented, integration
inventory complete. If this gate fails, Phase 2 cannot plan
operational improvements because the current operational
surface is unclear.

**Scoring & Metrics — PASS requires:**
Baseline measurements captured for every dimension the
improvement is intended to move — before improvement begins.
Every must-change outcome in §2 links to a measured baseline
row in §4. Qualitative claims ("the system is slow," "deploys
are painful") are replaced with measurements or explicitly
tagged as UNMEASURED. If this gate fails, improvement success
will be asserted rather than demonstrated, and regressions
introduced during improvement will be invisible.

**Correctness Verification — PASS requires:**
Every significant claim is tagged Observed / Documented Intent
/ Desired Future, every claim carries a source and a
confidence level, divergences between documented intent and
observed behavior are surfaced rather than reconciled,
conflicts between source artifacts are documented,
discovery gaps are explicitly registered in §11, and the
evidence-basis distribution (§12) shows a credible share of
Code/Config/Telemetry-verified claims relative to memory-only
claims. If this gate fails, Phase 2 will be planning
improvements against a current-state picture that may not
reflect reality.

### Phase 2 Readiness Determination

**Overall status:** [READY / CONDITIONALLY READY / NOT READY]

[2–3 sentences: the overall readiness determination, the most
critical gap if any, and what must happen before Phase 2
proceeds.]

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
      header with dates and completeness
- [ ] The three-timeframes discipline (Observed / Documented
      Intent / Desired Future) is preserved throughout;
      Section 12's timeframe distribution is populated
- [ ] Every claim carries an evidence-basis tag (Code / Config /
      Telemetry / Doc / Practitioner / Inferred, or Measured /
      Estimated / Believed / Unmeasured)
- [ ] Every must-change outcome in §2 is linked to a measured
      baseline row in §4 — no unbaselined must-changes
- [ ] Every technical debt item in §7 with a material Phase 2
      implication is linked to a Keep / Upgrade / Replace /
      Retire disposition in §8
- [ ] Documentation ↔ code divergences are surfaced in §5, not
      silently reconciled in §3
- [ ] Claimed-vs-enforced compliance distinction is preserved
      in §6
- [ ] Cross-artifact connections are surfaced — stack rows
      cross-reference dispositions and debts, compliance map
      cross-references components, baselines cross-reference
      objectives
- [ ] Conflicts between source artifacts are explicitly
      documented, not silently resolved
- [ ] The report contains no improvement recommendations,
      migration plans, or remediation prescriptions — candidate
      areas are preserved as candidates
- [ ] Every significant claim has a confidence level and source
      attribution
- [ ] The gap register (§11) is complete — all gaps from all
      five source artifacts are consolidated
- [ ] §10 (Phase 2 Readiness Inputs) is structured for direct
      consumption by Phase 2 tool sets, including the Baseline
      Handoff for Phase 6
- [ ] The self-evaluation scorecard assigns a gate status to
      all six principles with documented basis
- [ ] The Phase 2 readiness determination is explicit:
      READY, CONDITIONALLY READY, or NOT READY
- [ ] If CONDITIONALLY READY or NOT READY, required actions
      are listed with owners and target dates
- [ ] The Executive Summary is written last and reflects the
      full synthesis
- [ ] Output is formatted for AI consumption throughout
      (consistent headers, tables, IDs on all rows, semantic
      section labels, evidence-basis and three-timeframes tags
      preserved)

---

*Final artifact of the Phase 1 (Existing Projects) Information Gathering Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `step-00-information-gathering.existing-project.instructions.md`*
*Previous artifact: `step-05-reusable-replaceable-components-catalog.prompt.md`*
*Handoff to: Phase 2 Analysis & Improvement Planning tool sets*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| v1.0 | 2026-04-18 | Initial authoring | Initial Step 06 synthesis prompt. |
| **v1.1** | **2026-04-20** | **Diamonds dogfooding run (obs 24, 25)** | Added synthesis-only discipline to the Synthesis Rules — if Step 06 is producing net-new findings, decisions, or dispositions, pause and fix the upstream gap in Steps 01–05 rather than accreting novel content here (Cluster Q). Added scorecard rigor discipline to the Built-In Self-Evaluation section — CONDITIONAL preferred over PASS-with-caveats, target 4–5 PASS + 1–2 CONDITIONAL on a well-executed Phase 1, uniformly-PASS scorecards signal insufficient rigor, CONDITIONAL ratings must name the specific next-phase decision required to resolve (Cluster R). |
