# Step 06 — Scorecard Update Protocol
# Phase 3: Design & Technical Analysis
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 06 of 09 |
| **Type** | Action Prompt with Lightweight Clarification Step (governance-focused) |
| **Phase** | Phase 3 — Design & Technical Analysis |
| **SDD Step** | Implement (governance) |
| **Artifact Produced** | Scorecard Update Protocol — cross-phase governance document |
| **Principles Addressed** | Scoring & Metrics (primary), Correctness Verification (through regression detection rules) |
| **Requires As Input** | Phase 2 Step 01 Business Case & Principle Weighting (required for governance conventions); Phase 2 Step 06 Benchmark Framework (required for reference patterns); no Phase 3 content dependencies |
| **Feeds Into** | Step 05 (referenced by the scorecard baseline for the update protocol citation); Step 09 (Readiness Review); Phase 4, 5, 6, 7 (all subsequent phases inherit this protocol when updating the scorecard) |
| **Companion File** | `design-technical-analysis.instructions.md` |

---

## How to Use This Prompt

This is an **action prompt with a lightweight governance-focused
clarification step**. It produces the cross-phase protocol that
governs how the Principle Scorecard (established in Step 05) is
updated by Phases 4, 5, 6, and 7. The protocol is the framework's
structural defense against silent scorecard drift across phases.

This prompt is unusual in two ways:

1. **It has no Phase 3 content dependencies.** Its inputs are
   Phase 2 conventions and framework principles. It can be run any
   time during Phase 3 — including before Steps 01–05 complete.
   Some practitioners prefer to run it early to establish
   governance before analytical work begins.
2. **It produces a contract for future phases.** The protocol must
   be precise enough that Phase 4, 5, 6, and 7 toolkits can inherit
   it without inventing their own governance, and flexible enough
   to accommodate the different work each phase performs.

1. Confirm `design-technical-analysis.instructions.md` is loaded as
   project context.
2. Open a new AI session.
3. Paste **the Phase 2 Step 01 output** and **the Phase 2 Step 06
   output** above the kickoff line.
4. Paste the **Kickoff** line.
5. The AI asks between 3 and 5 lightweight governance clarification
   questions about cross-phase conventions, regression thresholds,
   and ownership.
6. The AI produces the Scorecard Update Protocol.
7. Review the output against the Evaluation Checklist before
   accepting.
8. The protocol is referenced by Step 05 (scorecard baseline) and
   inherited by Phases 4–7 when they update the scorecard.

> **Note on early execution:** This prompt can run before Steps
> 01–05. If it does, the references to "Step 05 baseline" remain
> structurally accurate — they refer to the artifact Step 05 will
> produce, not the current state of Step 05.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Update cadence per phase** — When each subsequent phase
  (Phase 4, 5, 6, 7) updates the scorecard, and what triggers
  within-phase updates
- **Regression detection rules** — What constitutes a regression
  in this project's context, with explicit thresholds
- **Change control protocol** — How amendments differ from
  substantive changes, and what governance applies to each
- **Ownership at each phase** — Who owns the scorecard update at
  each phase, with named approval authority
- **Integration with phase readiness reviews** — How the scorecard
  participates in Phase 4, 5, 6, and 7 readiness gates
- **Versioning conventions** — The version numbering scheme across
  phases, building on the Step 05 baseline's v1.0
- **Format inheritance rules** — What format conventions Phase 4–7
  updates must preserve from the Step 05 baseline
- **Cross-phase audit trail requirements** — How the update history
  is documented and preserved

### What This Step Does NOT Produce

- ❌ The scorecard itself (Step 05's role)
- ❌ Phase 4–7 specific update content (those phases produce their
  own updates within this protocol)
- ❌ Modifications to Phase 2 weighting or benchmarks (those are
  inputs)
- ❌ Implementation plans for what to do when regression is detected
  beyond the framework-level response (each phase's toolkit handles
  remediation)
- ❌ A statement that the protocol "guarantees" regression detection
  — the protocol enables detection; ensuring detection actually
  happens is the work of each phase

---

## System Instructions

You are a **senior governance analyst** within the AI-Centric
Software Development framework. You produce the cross-phase
governance protocol that makes the Principle Scorecard a trustworthy
measuring stick across the project lifecycle.

### Your Role

You take the Phase 2 weighting conventions, the Phase 2 benchmark
framework patterns, and the framework's principles. You produce a
governance protocol that:

- Specifies when and how each subsequent phase updates the
  scorecard
- Defines regression detection rules with explicit thresholds
- Establishes change control distinguishing amendments from
  substantive changes
- Names ownership at each phase
- Integrates with each phase's readiness review
- Preserves cross-phase format consistency

You are precise and unambiguous. Vague governance produces
predictable failures — silent drift, undocumented overrides,
disagreements about whether a regression occurred. Specific
governance produces visible behavior.

### Behavioral Rules

**Specify update cadence per phase explicitly.**
For each subsequent phase, name when the scorecard is updated.
Typically: Phase 4 updates once at architecture completion; Phase 5
updates per implementation milestone; Phase 6 updates per audit
cycle; Phase 7 updates monthly in production and after significant
incidents. Project-specific cadences may differ — capture the
practitioner's choices during clarification.

**Define regression thresholds in measurable terms.**
"If a principle scores lower" is incomplete. Lower by how much?
Sustained how long? Compared to which baseline? The protocol must
specify: minimum score delta that constitutes a regression
(typically 1.0 on the 1–5 scale, or 0.5 for high-weight principles),
the comparison baseline (typically the prior phase's score, with
explicit options for comparing to Phase 3 baseline), and the
window over which the regression must persist before triggering
review.

**Distinguish amendments from substantive changes.**
Amendments are clarifications, corrections, or refinements that
do not change scores or risk assessments. Substantive changes
include any score change, any risk item addition or removal, any
target adjustment, or any monitoring indicator change. The
protocol governs each differently.

**Name ownership at each phase with role-level specificity.**
Owners are typically roles (architecture lead at Phase 4, security
officer at Phase 6) rather than individuals — roles survive team
turnover. The practitioner may specify named individuals during
clarification if the project requires it.

**Integrate with phase readiness reviews.**
Phase 4, 5, 6, and 7 each have their own readiness reviews. The
scorecard must participate in each — typically as a required input,
with the readiness review verifying the scorecard was updated
appropriately and any regression was addressed. The protocol
specifies what each readiness review must verify about the
scorecard.

**Preserve format inheritance rules.**
The Step 05 baseline established the format. Phase 4–7 updates
must produce matching format — the same five elements per
principle, the same scoring scale, the same metadata conventions.
The protocol names which format conventions are mandatory and
which are flexible.

**Document the cross-phase audit trail.**
Every update produces a version log entry. Substantive changes
require additional documentation: trigger (what caused the change),
prior values (current/target scores before the change), new values,
approving authority. The audit trail is what makes the scorecard's
history reconstructible years later.

**Override mechanism is governance, not analytics.**
If a phase's readiness review detects regression, the default
response is remediation before the phase completes. If the
practitioner chooses to authorize phase completion despite
unresolved regression, the override is documented per the protocol
— named authority, specific rationale, accepted risk, conditions
for revisit. Same pattern as the Phase 2 Step 07 override mechanism.

**Specify regression categories.**
Not all regressions are equivalent. A 1-point drop in a high-weight
principle is more consequential than a 1-point drop in a low-weight
principle. The protocol can specify regression categories (e.g.,
Critical Regression, Material Regression, Minor Regression) with
different escalation paths for each.

---

## Clarification Step

Read the Phase 2 Step 01 (weighting) and Phase 2 Step 06 (benchmark
framework) inputs. The clarifications focus on cross-phase
governance conventions the practitioner wants to establish. Ask
between **3 and 5 questions**, focused on governance specifics
rather than analytical content.

Permitted clarification topics:

1. **Update cadence per phase.** Default cadences are: Phase 4 at
   architecture completion; Phase 5 per implementation milestone;
   Phase 6 per audit cycle; Phase 7 monthly. If the practitioner
   has different expectations, ask.

2. **Regression threshold calibration.** Default thresholds are:
   1.0-point drop on the 1–5 scale constitutes regression; 0.5-point
   drop for principles weighted above 20. If the practitioner wants
   different thresholds, ask.

3. **Ownership at each phase.** Default ownership is by role
   (architecture lead, security officer, ops lead). If the
   practitioner has named individuals or different role
   assignments, ask.

4. **Override authority.** Default override authority is the
   practitioner who authorized Phase 3 in Step 09. If a separate
   authority is required for cross-phase governance overrides,
   ask.

5. **Project-specific regression categories.** If the project has
   regulatory or organizational requirements that create
   project-specific regression categories (e.g., compliance-
   related regressions trigger different escalation), ask.

Do not ask:
- About analytical content of the scorecard itself
- About Phase 3 work products
- For interpretation of what each principle means
- For specific update content for any future phase

Ask questions one at a time. After clarifications, produce the
protocol in a single response.

---

## Kickoff

> Paste the Phase 2 Step 01 and Step 06 outputs above this line,
> then paste this line to trigger the prompt.

```
The Phase 2 Step 01 Business Case & Principle Weighting and the
Phase 2 Step 06 Benchmark Framework are pasted above. Please ask
your governance clarifying questions one at a time before
producing the Scorecard Update Protocol.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit
sections.

```markdown
# Scorecard Update Protocol
# Phase 3 Step 06 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Artifact Date:** [date]
**Produced By:** [AI model and version]
**Practitioner:** [name or role]
**Authorization Authority:** [name or role]
**Status:** [Draft / Approved]

**Based On:**
- Phase 2 Step 01 Business Case & Principle Weighting dated [date]
- Phase 2 Step 06 Benchmark Framework dated [date]

**Governs:** Phase 3 Step 05 Principle Scorecard Baseline (and all
subsequent updates by Phases 4, 5, 6, 7)

> **Cross-Phase Governance Notice:** This protocol governs how the
> Principle Scorecard changes from Phase 3 through Phase 7. Phase 4,
> 5, 6, and 7 toolkits inherit this protocol. Updates that bypass
> this protocol are governance defects. Phase tool sets reference
> the scorecard by version; silent drift is detectable as
> structural inconsistency between expected and actual scorecard
> versions.

---

## 1. Executive Summary

[4–6 sentences covering: the cadence summary across phases, the
regression detection threshold, the override mechanism, and the
ownership pattern. End with one line stating that Phase 4 inherits
this protocol unchanged unless a superseding governance ADR is
produced.]

---

## 2. Scope of This Protocol

This protocol governs:
- All updates to the Principle Scorecard from Phase 4 through
  Phase 7
- Regression detection across phase transitions
- Change control distinguishing amendments from substantive changes
- Cross-phase ownership and authorization
- Integration with each phase's readiness review
- Audit trail requirements

This protocol does not govern:
- The Phase 3 baseline itself (Step 05's content)
- The Phase 2 weighting or benchmarks (those are inputs that the
  scorecard reflects, not subjects of this protocol)
- Phase-specific update content (each phase's toolkit produces
  that content within this protocol)

---

## 3. Update Cadence Per Phase

### 3.1 Phase 4 — Architecture Update

| Field | Value |
|-------|-------|
| When updated | At Phase 4 architecture completion, before Phase 4 readiness review |
| Additional within-phase triggers | Any architectural decision that materially affects a principle's current score |
| Version produced | v2.0 |
| Owner | [Default: architecture lead] |
| Approval authority | [Default: Phase 4 decision authority] |
| Required reflection in artifact | Updated current scores reflecting architectural commitments; updated gap analysis showing what closed and what remains |

### 3.2 Phase 5 — Implementation Update

| Field | Value |
|-------|-------|
| When updated | Per implementation milestone (typically end of each major iteration or deployable unit) |
| Additional within-phase triggers | Security scan findings, test coverage changes, AI-vs-AI review findings, significant technical debt accumulation |
| Version produced | v3.0 for major implementation milestone; v3.x for within-milestone updates |
| Owner | [Default: implementation lead] |
| Approval authority | [Default: Phase 5 decision authority] |
| Required reflection in artifact | Updated current scores based on actual code quality, test coverage, security scan results |

### 3.3 Phase 6 — Testing & Audit Update

| Field | Value |
|-------|-------|
| When updated | After each audit cycle (penetration test, performance validation, compliance audit, documentation review) |
| Additional within-phase triggers | Any audit finding that affects a principle's score |
| Version produced | v4.0 |
| Owner | [Default: audit lead or security officer] |
| Approval authority | [Default: Phase 6 decision authority] |
| Required reflection in artifact | Updated current scores based on audit evidence; updated risk items based on findings; updated monitoring indicators if audit revealed indicator gaps |

### 3.4 Phase 7 — Deployment Update

| Field | Value |
|-------|-------|
| When updated | At initial deployment (v5.0); monthly in production (v5.x); after any production incident materially affecting principle health |
| Additional within-phase triggers | Sustained breach of monitoring indicator thresholds, security incidents, sustained benchmark misses, compliance findings |
| Version produced | v5.0 at launch; v5.x in operations |
| Owner | [Default: operations lead with security officer for security principle] |
| Approval authority | [Default: operations lead, with escalation for material changes] |
| Required reflection in artifact | Updated current scores based on production telemetry, incident history, operational reality |

---

## 4. Versioning Convention

### 4.1 Version Numbering

| Version | Phase | Trigger |
|---------|-------|---------|
| v1.0 | Phase 3 | Step 05 baseline |
| v1.x | Phase 3 | Within-Phase 3 baseline amendments |
| v2.0 | Phase 4 | Architecture completion update |
| v2.x | Phase 4 | Within-Phase 4 amendments |
| v3.0 | Phase 5 | First implementation milestone |
| v3.x | Phase 5 | Subsequent implementation milestones and amendments |
| v4.0 | Phase 6 | Testing & audit completion |
| v4.x | Phase 6 | Per-audit-cycle updates |
| v5.0 | Phase 7 | Deployment |
| v5.x | Phase 7 | Ongoing operational updates |
| v6.0+ | Phase 7+ | Subsequent major framework cycles |

### 4.2 What Constitutes a Version Increment

- **Major version (vN.0):** Phase transition; substantive
  scorecard update reflecting completion of a phase's work
- **Minor version (vN.x):** Within-phase amendment; substantive
  change that does not constitute phase completion
- **No version increment for non-substantive corrections:** Typos,
  formatting cleanup, link corrections — logged in the artifact's
  amendment log but do not increment version

---

## 5. Regression Detection Rules

### 5.1 What Constitutes a Regression

A regression occurs when:

| Condition | Threshold |
|-----------|-----------|
| Score decline for a high-weight principle (weight ≥ 20) | Current score drops by ≥ 0.5 from prior version |
| Score decline for a standard-weight principle (weight < 20) | Current score drops by ≥ 1.0 from prior version |
| Risk item escalation | A risk item moves from non-Critical to Critical |
| Monitoring indicator breach | A monitoring indicator crosses its "threshold for concern" sustained over the indicator's measurement window |

### 5.2 Regression Categories

| Category | Definition | Escalation Path |
|----------|-----------|-----------------|
| Critical Regression | High-weight principle drops by ≥ 1.0; OR any principle drops to score of 2 or below; OR Critical risk item added | Immediate practitioner review; phase may not complete without remediation or documented override |
| Material Regression | High-weight principle drops by 0.5–1.0; OR standard-weight principle drops by ≥ 1.0; OR monitoring indicator sustained breach | Practitioner review before phase readiness review; remediation plan required |
| Minor Regression | Standard-weight principle drops by 0.5–1.0; OR risk item escalation that is not Critical | Documented in amendment log; addressed within phase if feasible, deferred with rationale if not |

### 5.3 Baseline Comparison Rules

Regressions are detected by comparing the current version to:

- **The immediately prior version** (default comparison)
- **The Phase 3 baseline** (v1.0) for any principle being measured
  for cumulative drift
- **The Phase 4 architecture version** (v2.0) for principles where
  Phase 4 established a meaningful intermediate baseline

The protocol uses immediate-prior comparison by default; Phase 3
baseline comparison is used when cumulative drift is the concern;
Phase 4 baseline comparison is used when Phase 4 architectural
work materially changed the principle's character.

---

## 6. Change Control Protocol

### 6.1 Amendments (Within-Phase, Non-Substantive)

Amendments do not change scores, risk assessments, or monitoring
indicators. Examples:
- Clarifying language in gap analysis
- Correcting a citation
- Refining a monitoring indicator's tool name (without changing
  what is measured)
- Updating ownership when a role transitions

Process:
1. Update the artifact in place
2. Increment minor version (vN.0 → vN.1)
3. Log in the amendment log with description and date
4. Notify the phase's owner

### 6.2 Substantive Changes (Within-Phase or Phase Transition)

Substantive changes affect scores, risk assessments, monitoring
indicators, or targets. Examples:
- Any current score change
- Any target score change
- Risk item addition, removal, or criticality change
- Monitoring indicator addition, removal, or threshold change

Process:
1. Document the trigger (what caused the change)
2. Record prior values
3. Record new values
4. Document rationale
5. Obtain approval from the phase's authorization authority
6. Increment version (minor for within-phase; major for phase
   transition)
7. Log in the version log with full audit trail entry

### 6.3 Cross-Phase Substantive Changes

If a later phase needs to change content the prior phase
established (e.g., Phase 5 finds a Phase 4 risk item was wrong),
the change is:

1. A new entry in the current phase's update, not an edit of the
   prior phase's entry
2. Documented with explicit reference to what the prior phase had
   said
3. Approved by both the current phase's authority and the prior
   phase's authority if available

Prior-phase entries are never silently overwritten.

---

## 7. Integration With Phase Readiness Reviews

Each phase has a readiness review that gates progression to the
next phase. The scorecard participates in each.

### 7.1 Phase 4 Readiness Review Integration

The Phase 4 readiness review verifies:
- Scorecard v2.0 has been produced
- All six principles have updated current scores reflecting
  architectural commitments
- Any regression from v1.0 has been addressed per §5
- Gap analysis is updated to reflect what architecture closed and
  what remains for Phase 5

### 7.2 Phase 5 Readiness Review Integration

The Phase 5 readiness review verifies (for each implementation
milestone):
- Scorecard v3.x has been produced for the milestone
- Current scores reflect actual code quality, test coverage,
  security scan results
- Any regression from v2.0 has been addressed
- Monitoring indicators are now measurable (Phase 5 should have
  built the measurement infrastructure)

### 7.3 Phase 6 Readiness Review Integration

The Phase 6 readiness review verifies:
- Scorecard v4.0 has been produced
- Audit findings are reflected in current scores
- Any regression from v3.x has been addressed
- All current scores are now backed by audit evidence rather than
  intention

### 7.4 Phase 7 Readiness Review Integration

The Phase 7 readiness review (at deployment) verifies:
- Scorecard v5.0 has been produced
- Current scores reflect production-ready state
- Monitoring indicators are operational and producing data
- Any regression from v4.0 has been addressed

The Phase 7 ongoing operational updates (v5.x) do not have a
formal readiness review — they are continuous governance with
incident-driven escalation per §5.

---

## 8. Cross-Phase Audit Trail Requirements

Every version of the scorecard preserves a complete audit trail.

### 8.1 Required Audit Trail Elements Per Version

| Element | Required Content |
|---------|-----------------|
| Version number | Per §4 |
| Date | When the version was produced |
| Owner | Per §3 |
| Approver | Per §3 |
| Change summary | What changed from the prior version |
| Triggers | What caused each substantive change |
| Prior values | For each substantive change, the prior value |
| New values | For each substantive change, the new value |
| Regression flag | Whether any regression was detected per §5 |
| Regression resolution | How any detected regression was addressed |
| Override applied | Whether any override was applied per §9 |

### 8.2 Audit Trail Persistence

The audit trail is preserved within the scorecard artifact itself —
not in a separate log. This ensures the artifact is self-contained
and the history travels with the document.

When a new major version is produced (phase transition), prior
major versions are not deleted. They are preserved as historical
context.

---

## 9. Override Mechanism

If a phase's readiness review detects regression that cannot be
remediated before the phase must complete (regulatory deadline,
executive decision, business commitment), the practitioner may
authorize phase completion via override.

### 9.1 Override Authority

| Override Type | Authority Required |
|--------------|--------------------|
| Minor regression override | Phase's authorization authority |
| Material regression override | Phase's authorization authority + practitioner who authorized Phase 3 |
| Critical regression override | Phase's authorization authority + practitioner + named stakeholder (typically security officer for security regressions) |

### 9.2 Override Documentation Requirements

Every override is documented with:

| Element | Required Content |
|---------|-----------------|
| Override date | |
| Regression overridden | Specific principle and score delta |
| Authority granting override | Per §9.1 |
| Rationale | Specific business or schedule reason — generic rationale not acceptable |
| Risk accepted | Concrete description of what could go wrong |
| Mitigation in place | What the team is doing to compensate |
| Conditions for revisit | What would trigger reverting the override |
| Target remediation date | When the team commits to closing the gap |

### 9.3 Override Cumulative Tracking

The audit trail tracks all overrides across the project lifecycle.
A team that overrides multiple regressions per phase is operating
outside the framework's principles — the cumulative count is a
governance indicator in itself.

---

## 10. Format Inheritance Rules

The Step 05 baseline established the scorecard format. Subsequent
phases must preserve specific format conventions to maintain
cross-phase consistency.

### 10.1 Mandatory Format Conventions

Phases 4–7 updates must preserve:

- The six-principle structure (no principles added or removed)
- The five-element-per-principle structure (current, target, gap
  analysis, risk items, monitoring indicators)
- The 1–5 scoring scale with documented meaning
- The AI-Proposed and Practitioner-Calibrated value pattern (for
  any score changes)
- The cross-phase metadata section (§7 in Step 05 baseline)
- The version log structure (per §8)

### 10.2 Flexible Format Conventions

Phases 4–7 updates may adapt:

- The Cross-Principle Dashboard format (different phases may have
  different summary needs)
- The phase-specific subsections (e.g., Phase 5 may add a
  per-milestone subsection)
- The visual presentation (formatting choices that do not affect
  semantic content)

### 10.3 Adding Content vs. Changing Content

Phases 4–7 may add new content within existing structures (e.g.,
new risk items, new monitoring indicators) without invoking the
substantive change protocol. They may not silently change existing
content; per §6.2, any change to existing scores, risks, or
indicators is a substantive change.

---

## 11. Ownership Summary

Consolidated ownership across phases.

| Phase | Primary Owner | Approval Authority | Override Authority |
|-------|--------------|-------------------|--------------------|
| 3 (Step 05 baseline) | [Default: design lead / practitioner] | [Default: practitioner] | Per §9.1 |
| 4 | [Default: architecture lead] | [Default: Phase 4 decision authority] | Per §9.1 |
| 5 | [Default: implementation lead] | [Default: Phase 5 decision authority] | Per §9.1 |
| 6 | [Default: audit lead] | [Default: Phase 6 decision authority] | Per §9.1 |
| 7 launch | [Default: operations lead] | [Default: practitioner] | Per §9.1 |
| 7 ongoing | [Default: operations lead with security officer] | [Default: operations lead] | Per §9.1 |

[Project-specific ownership from clarification, if different from
defaults, replaces the defaults above.]

---

## 12. Protocol Revision Protocol

This protocol itself may need revision over the project lifecycle.

### 12.1 Amendments to This Protocol

Non-substantive corrections (typos, citation fixes) are logged in
this artifact's amendment log without versioning.

### 12.2 Substantive Changes to This Protocol

Substantive changes to this protocol — changing regression
thresholds, changing ownership patterns, changing override
authorities — require a new ADR that documents the change and
supersedes the relevant section of this protocol.

The new ADR is added to the project's ADR series (following the
numbering convention established by the Phase 2 stack ADR and the
Phase 3 design ADRs).

| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline protocol | |

---

## 13. Handoff Status

- [ ] Update cadence specified for all four subsequent phases
- [ ] Regression detection rules include explicit thresholds
- [ ] Regression categories defined with escalation paths
- [ ] Change control protocol distinguishes amendments from
      substantive changes
- [ ] Cross-phase substantive change rules are explicit
- [ ] Phase readiness review integration specified for all four
      subsequent phases
- [ ] Audit trail requirements specified per version
- [ ] Override mechanism documented with authority levels and
      required documentation
- [ ] Format inheritance rules distinguish mandatory from flexible
      conventions
- [ ] Ownership summary covers all phases

**Status:** [Ready for inheritance by Phases 4–7 / Gaps require
resolution first / Blocked]
```

---

## Evaluation Checklist

Before accepting this protocol as complete, verify:

- [ ] Update cadence is specified for Phase 4, Phase 5, Phase 6,
      and Phase 7 with concrete triggers
- [ ] Regression detection thresholds are numeric and measurable
      (not "if a principle declines")
- [ ] Regression categories (Critical, Material, Minor) have
      distinct escalation paths
- [ ] Baseline comparison rules distinguish immediate-prior,
      Phase 3 baseline, and Phase 4 baseline comparisons
- [ ] Change control distinguishes amendments (non-substantive)
      from substantive changes with clear examples
- [ ] Cross-phase substantive change rules prohibit silent
      overwriting of prior-phase entries
- [ ] Phase readiness review integration is specified for each of
      Phase 4, 5, 6, and 7
- [ ] Audit trail requirements name specific elements that every
      version must include
- [ ] Override mechanism has tiered authority by regression
      category
- [ ] Override documentation requirements are specific and force
      concrete rationale and accepted risk
- [ ] Format inheritance rules name what is mandatory (six
      principles, five elements per principle, 1–5 scale,
      AI/Practitioner pattern, metadata) and what is flexible
- [ ] Ownership summary covers all phases with named roles
- [ ] Protocol's own revision protocol allows for changes via
      superseding ADRs
- [ ] No analytical content (no scoring, no specific scorecard
      values) — the protocol governs the scorecard but does not
      contain it

---

*Step 06 of 9 in the Phase 3 Design & Technical Analysis Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `design-technical-analysis.instructions.md`*
*Previous step: `step-05-principle-scorecard-baseline.prompt.md`*
*Next step: `step-07-observability-hooks-handoff.prompt.md`*