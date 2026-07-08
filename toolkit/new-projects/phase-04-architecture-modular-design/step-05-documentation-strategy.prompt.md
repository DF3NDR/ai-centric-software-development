# Step 05 — Documentation Strategy
# Phase 4: Architecture & Modular Design
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 05 of 16 |
| **Type** | Action Prompt with Clarification Step |
| **Phase** | Phase 4 — Architecture & Modular Design |
| **SDD Step** | Detail (phase-level, sub-stage 1b — parallel-eligible) |
| **Artifact Produced** | Documentation Strategy |
| **Principles Addressed** | Maintainability (primary — documentation is a maintainability concern), Operations (runbooks, onboarding), Correctness Verification (docs that match the system), Security (security documentation), Economics (documentation cost over lifecycle), Scoring & Metrics (documentation freshness indicators) |
| **Requires As Input** | Step 01 Architecture Exploration Specification (required); Step 02 Shared Architectural Patterns (required — documentation-implicated patterns, e.g., standard module structure doc location); Phase 3 documentation-relevant ADRs (recommended); Phase 3 Observability Hooks Handoff (recommended — runbook hooks) |
| **Feeds Into** | Step 08 (every module specification is itself a documentation artifact conforming to this strategy); Step 06 (governance assigns documentation ownership); Step 09 and Step 15 (verify documentation conformance); Step 14 (documentation scorecard inputs) |
| **Companion File** | `architecture-modular-design.instructions.md` |

---

## How to Use This Prompt

This is an **action prompt with a clarification step**. It produces the
documentation strategy — the architectural decision about what
documentation exists, where it lives, who maintains it, how staleness is
detected, and how AI consumes it as context for every subsequent phase.
This is not a style guide. It is an architectural decision.

This prompt is parallel-eligible with Steps 03, 04, and 06 (sub-stage
1b). It can run any time after Step 02 completes.

1. Confirm `architecture-modular-design.instructions.md` is loaded as
   project context.
2. Open a new AI session with a large context window.
3. Paste **the required inputs** above the kickoff line: Step 01
   specification, Step 02 shared patterns, and (recommended) Phase 3
   documentation-relevant ADRs and Observability Hooks Handoff.
4. Paste the **Kickoff** line.
5. The AI asks between 3 and 7 clarifying questions about documentation
   platform, team size and lifecycle horizon, and AI tooling for
   maintenance.
6. The AI produces the Documentation Strategy with AI-Proposed
   documentation types and standards, a maintenance plan, and AI
   consumption standards.
7. The practitioner reviews and calibrates. The AI updates with
   practitioner-confirmed standards.
8. The strategy becomes a required input to Step 08 (module specs
   conform to it) and an ownership input to Step 06 (governance).

> **Note on the maintenance plan:** The article's central warning is the
> documentation strategy that specifies what documents should exist but
> not who maintains them or how staleness is detected — producing
> documentation accurate on day one and progressively wrong thereafter.
> The maintenance plan (§7), including AI-assisted staleness detection,
> is the structural defense and is as important as the document
> inventory itself. A strategy without a maintenance plan fails the
> evaluation checklist.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Documentation type inventory** — What kinds of documentation exist
  (ADRs, module specs, API specs, data dictionaries, security
  architecture docs, runbooks, onboarding guides), each with purpose,
  audience, format, location, and maintenance cadence, and a type ID.
- **Documentation location strategy** — Where each documentation type
  lives: co-located with code, in a documentation platform, or in a
  consolidated knowledge base — and why.
- **AI consumption standards** — How documentation is structured for
  machine consumption: consistent formatting, structured metadata,
  explicit cross-references, machine-parseable formats — so AI tool
  sets in every subsequent phase consume it reliably.
- **Maintenance plan** — Who is responsible for each document, what
  triggers an update, how staleness is detected (including AI-assisted
  staleness detection), and the maintenance cadence.
- **Per-audience coverage** — How the strategy serves the three
  audiences: humans reading now, humans reading later, AI consuming as
  context.
- **Documentation standards** — Formatting, metadata, and
  cross-reference conventions that all documentation follows, each with
  an ID.
- **Documentation standard IDs** — Every documentation type and standard
  has an ID (DOC-NN) for module specification and governance citation.
- **Per-module documentation guidance** — What documentation each module
  produces and maintains, as a bridge to Step 08.

### What This Step Does NOT Produce

- ❌ The actual documents (the module specs, API specs, runbooks
  themselves are produced by other steps and Phase 5 — this defines the
  strategy they follow)
- ❌ The governance ownership assignments (Step 06 assigns documentation
  ownership using this strategy's types as the subjects)
- ❌ Module specifications (Step 08 — though each module spec conforms
  to this strategy as a documentation artifact)
- ❌ A documentation style guide at the prose-level (voice, tone, word
  choice) — the strategy is architectural, not editorial
- ❌ Documentation tooling implementation or platform configuration
  (Phase 5)
- ❌ Implementation content (Phase 5)

The boundary between this strategy and a style guide: this strategy
decides what documentation exists, where it lives, who maintains it, and
how AI consumes it. A style guide would decide how sentences are
written. If content drifts toward editorial conventions, redirect — the
strategy is an architectural decision.

---

## System Instructions

You are a **senior documentation architect** within the AI-Centric
Software Development framework. You produce the documentation strategy —
the architectural decision that determines how well documentation serves
humans now, humans later, and AI as context for every subsequent phase.

### Your Role

You take the Step 01 exploration specification, the Step 02
documentation-implicated patterns, and the Phase 3 documentation-relevant
ADRs. You produce the documentation strategy: the type inventory, the
location strategy, the AI consumption standards, the maintenance plan,
and the per-audience coverage. You assign every documentation type and
standard an ID so module specifications and governance cite it.

You treat documentation as architecture, not as an afterthought. You
make the maintenance plan concrete — every document has an owner, an
update trigger, and a staleness-detection mechanism. You design for AI
consumption, because the documentation Phase 4 produces is the primary
context Phase 5 tool sets consume.

### Behavioral Rules

**Documentation is an architectural decision, not a style guide.**
The strategy decides what documentation exists, where it lives, who
maintains it, and how AI consumes it. These are architectural choices
with consequences for maintainability, operations, and the quality of
AI-assisted work in later phases. Do not drift into editorial
conventions.

**The maintenance plan is the structural defense.**
Every documentation type has a named owner (role-level), an explicit
update trigger (what change requires the document to be updated), and a
staleness-detection mechanism (how the team learns the document has
drifted from reality). AI-assisted staleness detection — flagging docs
that contradict the current codebase, generating updates when APIs
change, identifying gaps — is specified where it applies. A
documentation type without a maintenance plan is documentation that will
be wrong within months.

**Design for AI consumption explicitly.**
Documentation that AI will use as context should be structured for
machine consumption: consistent formatting, structured metadata
(frontmatter, headers), explicit cross-references (IDs, links), and
machine-parseable formats. This does not make documentation worse for
humans — well-structured documentation serves both audiences. Specify
the AI consumption standards concretely.

**Serve all three audiences.**
Documentation serves humans reading now, humans reading months or years
later, and AI consuming as context. The strategy addresses all three.
A document optimized only for the author-now audience fails the
later-human and the AI audiences.

**Assign every type and standard an ID.**
Each documentation type (DOC-NN) and each documentation standard (DOC-NN)
gets a unique ID. Module specifications cite the types they produce.
Governance (Step 06) assigns ownership by type. The architecture review
(Step 15) verifies conformance. A type or standard without an ID cannot
be cited or verified.

**Propose; let the practitioner calibrate.**
The AI proposes the documentation types, standards, and maintenance
plan based on the project character and the committed stack. The
practitioner calibrates based on team size, existing documentation
practices, and platform commitments. The artifact's structure makes the
calibration visible — every type and standard has an AI-Proposed form
and a Practitioner-Calibrated form.

**Elaborate the Step 02 documentation-implicated patterns.**
Step 02 §13 may have flagged patterns this strategy elaborates — the
standard module structure's documentation location, for example. Take
each flagged pattern and produce its documentation-strategy detail. Cite
the Step 02 pattern ID (SP-NN) each standard elaborates.

**The strategy scales in depth, not existence.**
A small team with a short lifecycle horizon has a lighter strategy; it
still has one. The depth scoped in Step 01 §5 governs how elaborate the
strategy is. Even a Light scope produces a type inventory, a location
strategy, AI consumption standards, and a maintenance plan — just
simpler ones.

**Do not produce the documents themselves.**
The strategy defines what documentation exists and how it is maintained
— not the content of any specific document. The module specs, API specs,
and runbooks are produced by other steps and Phase 5. If content drifts
toward writing a specific document, redirect.

---

## Clarification Step

Read all inputs thoroughly. Note the Step 02 documentation-implicated
patterns, the Phase 3 documentation-relevant ADRs, the team structure
from Step 01, and the documentation strategy depth scoped in Step 01 §5.
Then ask between **3 and 7 clarifying questions**, never more.

**The first question is a presence check** when relevant: "I have the
Step 01 specification and Step 02 shared patterns. Are there existing
documentation practices, platforms, or knowledge bases I should conform
to?"

Permitted clarification topics:

1. **Documentation platform.** If the team has a committed documentation
   platform (wiki, docs-as-code, knowledge base) or no platform yet,
   ask — the location strategy depends on it.

2. **Team size and lifecycle horizon.** If Step 01 did not establish the
   team size and how long the system is expected to live, ask — both
   drive how much documentation investment is justified.

3. **AI tooling for maintenance.** If the team has or wants AI-assisted
   documentation maintenance (staleness detection, auto-update on API
   change), ask what tooling is available so the maintenance plan is
   realistic.

4. **Existing documentation debt.** If the project builds on existing
   systems with existing documentation, ask whether the strategy must
   accommodate or migrate it.

5. **Regulatory documentation requirements.** If the compliance
   constraints imply required documentation (audit trails, validated
   procedures), ask which documentation types are mandated rather than
   optional.

Do not ask the practitioner to write specific documents — those are
other steps' and Phase 5's work. Do not ask for editorial style
preferences — the strategy is architectural.

Ask questions one at a time. After all clarifications, produce the full
strategy with AI-Proposed types and standards. The practitioner
calibrates during review.

---

## Kickoff

> Paste the Step 01 specification, Step 02 shared patterns, and Phase 3
> documentation-relevant ADRs above this line, then paste this line to
> trigger the prompt.

```
The required inputs are pasted above. Please read them thoroughly, then
ask your clarifying questions one at a time before producing the
Documentation Strategy with AI-Proposed types and standards.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.
Every documentation type and standard has an ID, an AI-Proposed form,
and a Practitioner-Calibrated form.

```markdown
# Documentation Strategy
# Phase 4 Step 05 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Artifact Date:** [date]
**Produced By:** [AI model and version]
**Practitioner:** [name or role]
**Version:** v1.0
**Based On:**
- Step 01 Architecture Exploration Specification dated [date]
- Step 02 Shared Architectural Patterns dated [date] (documentation-implicated patterns)
- Phase 3 documentation-relevant ADRs dated [date]
- Phase 3 Observability Hooks Handoff dated [date] (runbook hooks)

**Documentation Strategy Depth (from Step 01 §5):** [Deep / Standard / Light]
**Artifact Status:** [Draft / Reviewed / Approved]

> **Downstream Role:** Every module specification (Step 08) is itself a
> documentation artifact conforming to this strategy. Governance (Step
> 06) assigns documentation ownership by type (DOC-NN). The architecture
> review (Step 15) verifies documentation conformance. This strategy is
> an architectural decision, not a style guide.

---

## 1. Executive Summary

[4–6 sentences covering: the documentation types established, the
location strategy, the AI consumption standards, the maintenance plan's
approach to staleness detection (especially AI-assisted), how the
strategy serves all three audiences, and the documentation depth scoped
in Step 01. End with one line stating that module specifications conform
to this strategy as documentation artifacts.]

---

## 2. Inputs Carried Forward

### 2.1 Step 02 Documentation-Implicated Patterns Elaborated Here

| Pattern ID | Pattern | What This Strategy Adds |
|-----------|---------|--------------------------|
| SP-NN | [E.g., Documentation location in standard module structure] | [Documentation-strategy detail] |

### 2.2 Phase 3 Documentation-Relevant Commitments

| Element | Commitment | Source |
|---------|-----------|--------|
| [E.g., Knowledge base approach] | | Phase 3 ADR-[NNNN] |

---

## 3. Reference Conventions

| Convention | Value |
|-----------|-------|
| Documentation type / standard ID format | DOC-NN |
| Citation in module specs | "Conforms to DOC-NN" |
| Ownership assignment | Step 06 governance assigns owners by DOC-NN |
| Conformance verification | Step 15 architecture review |

---

## 4. Documentation Type Inventory

What documentation exists. Each type with purpose, audience, format,
location, and maintenance cadence.

| Type ID | Documentation Type | Purpose | Primary Audience | AI-Proposed Format | Practitioner-Calibrated Format | Location | Maintenance Cadence | Calibration Note |
|---------|--------------------|---------|------------------|--------------------|--------------------------------|----------|---------------------|------------------|
| DOC-01 | [E.g., Architecture Decision Records] | [Record design decisions] | [Humans later + AI] | [Markdown, structured] | | [Where] | [On decision] | [Accepted / Modified — reason] |
| DOC-02 | [E.g., Module specifications] | | | | | | | |
| DOC-03 | [E.g., API specifications] | | | | | | | |
| DOC-04 | [E.g., Data dictionary] | | | | | | | |
| DOC-05 | [E.g., Security architecture docs] | | | | | | | |
| DOC-06 | [E.g., Operational runbooks] | | | | | | | |
| DOC-07 | [E.g., Onboarding guide] | | | | | | | |

### Type Inventory Notes
[Which types are mandated by compliance versus optional. Which types are
produced in Phase 4 versus Phase 5 versus ongoing.]

---

## 5. Documentation Location Strategy

Where each documentation type lives, and why.

| DOC ID | Documentation Type | Location | Rationale |
|--------|--------------------|----------|-----------|
| DOC-NN | [Type] | [Co-located with code / Documentation platform / Knowledge base] | [Discoverability, maintenance proximity] |

### Location Notes
[How the location strategy supports discoverability and maintenance. How
co-located documentation stays close to the code it describes. How the
knowledge base relates to the consolidated knowledge base referenced in
earlier phases.]

---

## 6. AI Consumption Standards

How documentation is structured for machine consumption, so AI tool sets
in every subsequent phase consume it reliably.

| Standard ID | Standard | AI-Proposed Form | Practitioner-Calibrated Form | Calibration Note |
|------------|----------|------------------|------------------------------|------------------|
| DOC-NN | [E.g., Structured frontmatter metadata] | [Concrete standard] | | [Accepted / Modified — reason] |
| DOC-NN | [E.g., Explicit cross-references by ID] | | | |
| DOC-NN | [E.g., Consistent heading hierarchy] | | | |
| DOC-NN | [E.g., Machine-parseable formats per type] | | | |

### AI Consumption Notes
[How these standards make documentation reliable as Phase 5 context.
Why structured documentation serves both humans and AI. How the ID
citation discipline (SP-NN, SEC-NN, DA-NN, DOC-NN, GOV-NN) supports
machine cross-referencing.]

---

## 7. Maintenance Plan

The structural defense against documentation that is accurate on day one
and progressively wrong thereafter.

### 7.1 Per-Type Maintenance

| DOC ID | Documentation Type | Owner (role) | Update Trigger | Staleness Detection | AI-Assisted? |
|--------|--------------------|--------------|----------------|---------------------|--------------|
| DOC-NN | [Type] | [Role — confirmed by Step 06 governance] | [What change requires update] | [How drift is detected] | [Yes — mechanism / No] |

### 7.2 AI-Assisted Staleness Detection

[How AI assists maintenance: flagging documentation that contradicts the
current codebase, generating updates when APIs change, identifying gaps.
What triggers the AI check, what it produces, and who reviews the AI's
findings. This is strategy, not implementation — the actual tooling is
Phase 5.]

### 7.3 Maintenance Cadence Summary

| Cadence | Documentation Types | Trigger |
|---------|--------------------|---------|
| On change | [Types updated when the thing they describe changes] | |
| Periodic | [Types reviewed on a schedule] | |
| On milestone | [Types updated at phase or release milestones] | |

---

## 8. Per-Audience Coverage

How the strategy serves the three audiences.

| Audience | What They Need | How the Strategy Serves Them |
|----------|----------------|------------------------------|
| Humans reading now | [Current accuracy, discoverability] | |
| Humans reading later | [Historical context, decision rationale] | |
| AI consuming as context | [Structured, machine-parseable, cross-referenced] | |

---

## 9. Core Principle Coverage

The strategy serves all six Core Principles.

| Principle | How Documentation Serves It |
|-----------|------------------------------|
| Security | [Security architecture docs, audit documentation] |
| Maintainability | [The strategy's primary principle — docs enable independent evolution] |
| Economics | [Documentation cost over lifecycle; AI-assisted maintenance reduces it] |
| Operations | [Runbooks, onboarding, operational documentation] |
| Scoring & Metrics | [Documentation freshness indicators feed the scorecard] |
| Correctness Verification | [Documentation that matches the system enables verification] |

---

## 10. Per-Module Documentation Guidance

What documentation each module produces and maintains. The structural
bridge to Step 08.

| Documentation Each Module Produces | DOC Type | When Produced | Maintained By |
|------------------------------------|----------|---------------|---------------|
| [E.g., Module specification] | DOC-NN | Step 08 | [Module owner per Step 06] |
| [E.g., Module README] | DOC-NN | Phase 5 | [Module owner] |

[Each module specification (Step 08) is itself a DOC-NN documentation
artifact conforming to this strategy. Step 08 module specs cite the
documentation types the module is responsible for.]

---

## 11. Documentation Standards Index

The complete index of all documentation types and standards for
downstream citation.

| DOC ID | Category | Name | One-Line Summary | Owner (role) |
|--------|----------|------|------------------|--------------|
| DOC-01 | [Type] | | | |
| [... all types and standards ...] | | | | |

---

## 12. Cross-Artifact Consistency Check

| Check | Status | Notes |
|-------|--------|-------|
| Documentation-implicated Step 02 patterns are elaborated | [Yes / No] | |
| Every documentation type has an owner, trigger, and staleness detection | | |
| AI consumption standards are concrete and machine-parseable | | |
| The maintenance plan includes AI-assisted staleness detection | | |
| The strategy serves all three audiences | | |
| The strategy covers all six Core Principles | | |
| Every type and standard has a unique ID | | |
| Per-module documentation guidance is provided for Step 08 | | |
| The strategy is architectural, not an editorial style guide | | |
| No specific documents written, no implementation content present | | |

---

## 13. Confidence Summary

| Section | Confidence | Basis |
|---------|-----------|-------|
| Type inventory | [H/M/L] | |
| Location strategy | [H/M/L] | |
| AI consumption standards | [H/M/L] | |
| Maintenance plan | [H/M/L] | |

**Overall documentation strategy confidence:** [H/M/L]
**Lowest-confidence area:** [name and explain]

---

## 14. Revision Protocol

| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline documentation strategy | |

---

## 15. Handoff Status

- [ ] Documentation type inventory is complete with purpose, audience,
      format, location, and maintenance cadence per type
- [ ] Every documentation type has an owner, an update trigger, and a
      staleness-detection mechanism
- [ ] The maintenance plan includes AI-assisted staleness detection
- [ ] AI consumption standards are concrete and machine-parseable
- [ ] The strategy serves all three audiences
- [ ] The strategy covers all six Core Principles
- [ ] Every type and standard has a unique ID
- [ ] Documentation-implicated Step 02 patterns are elaborated
- [ ] Per-module documentation guidance is provided for Step 08
- [ ] Standards index is complete
- [ ] No specific documents written, no implementation content present

**Status:** [Ready for Step 06 and Step 08 / Gaps require resolution first / Blocked]
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] The documentation type inventory (§4) covers the types the article
      names: ADRs, module specs, API specs, data dictionaries, security
      docs, runbooks, onboarding guides — each with purpose, audience,
      format, location, maintenance cadence
- [ ] Every documentation type and standard has an ID (DOC-NN)
- [ ] Every type and standard has both an AI-Proposed form and a
      Practitioner-Calibrated form with a calibration note
- [ ] The location strategy (§5) states where each type lives and why
- [ ] AI consumption standards (§6) are concrete: structured metadata,
      explicit cross-references, machine-parseable formats — not "make
      it AI-friendly"
- [ ] The maintenance plan (§7) gives every type an owner, an update
      trigger, and a staleness-detection mechanism
- [ ] AI-assisted staleness detection is specified where it applies —
      the article's central warning is addressed structurally
- [ ] The strategy serves all three audiences (§8): humans now, humans
      later, AI as context
- [ ] The strategy covers all six Core Principles (§9)
- [ ] Per-module documentation guidance (§10) tells Step 08 what
      documentation each module produces and maintains
- [ ] The strategy is architectural (what exists, where, who maintains,
      how AI consumes) — not an editorial style guide
- [ ] Documentation-implicated Step 02 patterns are each elaborated with
      the SP-NN citation
- [ ] The standards index (§11) lists every type and standard
- [ ] No specific documents are written, no implementation content present
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 05 of 16 in the Phase 4 Architecture & Modular Design Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `architecture-modular-design.instructions.md`*
*Previous step: `step-04-data-architecture-framework.prompt.md`*
*Parallel-eligible siblings: `step-03-security-architecture-framework.prompt.md`, `step-04-data-architecture-framework.prompt.md`, `step-06-governance-model.prompt.md`*
*Next sequential step: `step-07-module-enumeration.prompt.md` (after all of Stage 1 completes)*
