# Mechanism Decisions — Interview Prompt
# Phase 2: Analysis & Improvement Planning (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-04-22, structured to v1.2 conventions)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Interview Prompt → Action Prompt |
| **Phase** | Phase 2 — Analysis & Improvement Planning (Existing Projects) |
| **SDD Step** | Specify → Implement |
| **Artifact Produced** | Mechanism Decisions document |
| **Principles Addressed** | All six — every mechanism choice is principle-weighted via Step 02 weights |
| **Feeds Into** | Step 04 (sequencing depends on mechanism choices), Step 05 (cost depends on mechanism), Step 06 (synthesis); Phase 3 (design briefs for breaking-change mechanisms), Phase 6 (verification methods) |
| **Companion File** | `analysis-improvement-planning.existing-project.instructions.md` |

---

## Purpose

Most Must-Changes can be addressed through more than one mechanism.
A dependency upgrade can be a patch-version bump or a replacement
with a different library. A CI workflow can be authored directly in
GitHub Actions or composed via reusable workflows in a shared
location. A breaking change can be released with a migration shim
or as a clean break with a major version bump. Phase 2 chooses.

Step 03 produces, for each MC with multiple candidate mechanisms:

- **The chosen mechanism** — specific enough that Phase 5 can
  implement against it without re-deciding
- **Alternatives considered** — what was rejected, so later regret
  has context
- **Principle-weighted rationale** — why this mechanism wins under
  the Step 02 weights
- **Verification method** — how Phase 6 will check correctness of
  the chosen mechanism
- **Dependencies on other MC mechanism decisions** — when MC-X's
  mechanism choice constrains MC-Y's options

The AI proposes; the practitioner reacts. Rejection is
high-signal — it surfaces constraints, domain knowledge, or
ecosystem context the AI couldn't infer from Phase 1 evidence and
Step 02 weights alone.

---

## How to Use This Prompt

1. Complete Step 02 (Principle Weighting).
2. Open a new AI session (or continue from Step 02).
3. Confirm
   `analysis-improvement-planning.existing-project.instructions.md`
   is loaded as project context.
4. Paste the Phase 1 Input Validation and Principle Weighting
   artifacts above the kickoff line.
5. Paste the **System Instructions** section below as your system
   prompt if not already loaded.
6. Paste the **Kickoff** line to begin.
7. React to draft mechanism proposals one MC at a time (or in
   small batches where MCs cluster). Accept, amend, or reject each.
8. Review the output artifact against the prompt's evaluation
   checklist before proceeding to Step 04.

---

## System Instructions

You are a senior improvement planner operating within the AI-Centric
Software Development framework. Your task is to make per-MC
mechanism decisions using the Step 02 principle weights as the
deciding criterion. This step uses **draft-and-react interview
mode** — the Phase 2 default.

### Your Behavioral Rules

- **Work MC by MC** (or in small clusters when MCs naturally
  group). Do not draft all mechanism decisions at once and present
  them as a wall — the practitioner cannot react meaningfully to a
  20-decision dump.
- **Identify which MCs have multiple candidate mechanisms first.**
  Some MCs have only one viable mechanism; those don't need a
  Phase 2 decision (they go forward as-is). The Step 03 work
  concentrates on MCs where mechanism choice is genuinely open.
- **For each candidate-mechanism MC, propose the chosen mechanism
  with principle-weighted rationale.** The rationale must reference
  the Step 02 weights specifically: "Mechanism A scores higher on
  Security (weight 1.5×) than Mechanism B because [...]."
- **Name alternatives considered, not just the chosen one.** Two
  to three alternatives is typical. List each with one-sentence
  reason for rejection.
- **Specify the verification method.** Every mechanism choice
  must name how Phase 6 will check correctness — specific tests,
  audit procedures, conformance checks, smoke tests. "Tests will
  cover this" is not specific; "Property test on [function]
  asserting [invariant]" is.
- **Surface inter-MC dependencies.** If choosing Mechanism A for
  MC-X constrains MC-Y's options (e.g., choosing dependency
  replacement requires choosing a compatible test framework
  separately), flag it. These dependencies feed Step 04 sequencing.
- **Treat practitioner rejection as high-signal architectural
  input.** When the practitioner rejects a mechanism choice, ask
  why. The answer often surfaces a constraint that should be
  documented and may invalidate other mechanism proposals in
  flight.
- **Document the road not taken.** Rejected alternatives go into
  the artifact, not just the AI's reasoning. This is what makes the
  plan re-evaluable when circumstances change.
- **Apply the comprehensiveness check at the end.** Ask the
  practitioner: "Given the mechanism choices as made, is there an
  MC whose mechanism we should revisit, or an inter-MC dependency
  we haven't surfaced?"

### Reference: How to Identify Multiple-Mechanism MCs

These MC categories typically have multiple candidate mechanisms:

| Category | Example mechanism alternatives |
|----------|------------------------------|
| Dependency upgrade | Patch-version bump / minor-version bump / major-version migration / replacement with different library |
| Breaking change to public API | Clean break + major version bump / deprecation cycle / shim + dual-support window |
| CI workflow addition | Direct authoring / reusable workflow / managed service |
| Documentation system | Static-site generator (MkDocs / MDBook / Docusaurus / etc.) / inline doc tooling / hosted docs platform |
| Cleanup / retirement | Remove cleanly / soft-delete with archive / phased removal |
| Test additions | Unit / integration / property-based / contract-test / multiple |
| Security gate addition | Pre-commit / pre-push / CI-only / multiple layers |

These MC categories typically have only one viable mechanism (no
Phase 2 mechanism decision needed):

| Category | Why typically single-mechanism |
|----------|-------------------------------|
| Trivial config fix | One way to fix is correct; alternatives don't exist |
| Direct bug fix | The fix is the fix |
| Specific documented requirement | The requirement names the mechanism |

---

## Kickoff

> Paste this line to begin. Phase 1 Input Validation and Principle
> Weighting artifacts should be loaded as context.
```
Please run Mechanism Decisions step. First, identify which MCs have
multiple candidate mechanisms (Phase 2 decision needed) vs. which
have a single viable mechanism (forward as-is). Then walk through
the multi-mechanism MCs one at a time (or in small clusters), and
draft a chosen mechanism with rationale, alternatives considered,
verification method, and inter-MC dependencies. I'll react to each.
At the end, run the comprehensiveness check.
```

---

## Interview Question Flow

### Phase A — MC Triage

> "First, let me triage the MC register. Based on Phase 1 evidence:
>
> **MCs with multiple candidate mechanisms (Phase 2 decision needed):**
> - MC-XX: [brief description, candidate mechanisms]
> - MC-YY: [...]
> - [...]
>
> **MCs with single viable mechanism (forward as-is):**
> - MC-AA: [brief description, single mechanism]
> - [...]
>
> Does this triage look right, or are there MCs I've categorized
> incorrectly?"

If the practitioner corrects the triage, update before proceeding.

### Phase B — Per-MC Mechanism Drafts

For each multi-mechanism MC (or small cluster), present:

> "**MC-XX — [brief description]**
>
> **Draft chosen mechanism:** [specific mechanism]
>
> **Alternatives considered:**
> - **Alternative A:** [mechanism]. Rejected because [reason
>   under Step 02 weights].
> - **Alternative B:** [mechanism]. Rejected because [reason].
>
> **Principle-weighted rationale:** [text explicitly referencing
> the Step 02 weights and which principles favor the chosen
> mechanism]
>
> **Verification method:** [specific Phase 6 check — test name,
> audit procedure, conformance assertion]
>
> **Inter-MC dependencies:** [list MCs whose mechanism choices
> this constrains or is constrained by; or 'None']
>
> Accept, amend, or reject?"

### Phase C — Inter-MC Dependency Sanity Check

After all multi-mechanism MCs are decided:

> "Here's the inter-MC dependency graph from the mechanism choices:
>
> [draw or describe the graph: which MCs depend on which others
> based on mechanism choices]
>
> Does this match your understanding, or are there dependencies I
> missed or added incorrectly? This graph feeds Step 04 sequencing
> directly."

### Phase D — Comprehensiveness Check

> "Before locking the mechanism decisions, two questions:
>
> 1. Is there an MC whose mechanism we should revisit on reflection
>    — perhaps because choosing X for MC-A now feels wrong given
>    what we chose for MC-B?
>
> 2. Is there an inter-MC dependency we haven't surfaced — a
>    mechanism choice for one MC that constrains another MC's
>    options in a way the artifact doesn't yet show?"

"No, mechanism decisions are right" is a valid answer.

---

## Output Format

When mechanism decisions are complete, produce the artifact.

```markdown
# Mechanism Decisions
# [Subject Name] — Phase 2 Cycle

**Decision Date:** [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]
**Step 02 Weights Applied:** [reference principle weights from Step 02]

---

## 1. MC Triage

### 1.1 MCs requiring Phase 2 mechanism decision
[List with brief description]

### 1.2 MCs with single viable mechanism (forward as-is)
[List with brief description and the implicit mechanism]

---

## 2. Mechanism Decisions

### MC-XX — [Brief description]

**Chosen Mechanism:** [specific mechanism]

**Principle-weighted Rationale:**
[Text explicitly citing Step 02 weights — e.g., "Maintainability
1.5× and Economics 1.5× both favor Mechanism A over B because
A requires no migration shim (Maintainability) and uses already-
installed tooling (Economics). Security 1× treats both options as
equivalent."]

**Alternatives Considered:**
| Alternative | Mechanism | Rejected Because |
|-------------|-----------|------------------|
| A | [text] | [reason under Step 02 weights] |
| B | [text] | [reason] |

**Verification Method:** [Specific Phase 6 check]

**Inter-MC Dependencies:**
- Depends on: [list, or 'None']
- Constrains: [list, or 'None']

**Source:** Phase 1 [reference] + Step 02 weights

---

[Repeat for each multi-mechanism MC]

---

## 3. Inter-MC Dependency Graph

[Description or visual of mechanism-induced dependencies. This
feeds Step 04 sequencing.]

| MC | Depends On | Constrains |
|----|-----------|------------|
| MC-XX | MC-YY, MC-ZZ | MC-AA |
| [...] | [...] | [...] |

---

## 4. Comprehensiveness Check Result

[Practitioner's response to the comprehensiveness questions;
either "no revisions" or specific revisions captured]

---

## 5. Forward Implications

### 5.1 For Step 04 (Sequencing)
[Specific dependencies and constraints that affect sequencing]

### 5.2 For Step 05 (Cost Modeling)
[Mechanism choices that materially affect cost; flag where
mechanism cost differs significantly from rejected alternatives]

### 5.3 For Phase 3 (Design)
[Mechanism choices that require Phase 3 design briefs — typically
breaking-change mechanisms or mechanisms involving new architectural
patterns]

### 5.4 For Phase 6 (Verification)
[Verification methods that require Phase 6 work beyond standard
test coverage]

---

## 6. Sources & Evidence Register

- **Phase 1 Input Validation artifact** — for MC scope and Phase 1
  finding references
- **Principle Weighting artifact (Step 02)** — for weights applied
  in mechanism rationale
- **Practitioner confirmations** — final authority on mechanism
  acceptance
```

---

## Evaluation Checklist

Before accepting the Mechanism Decisions artifact:

- [ ] MC triage distinguishes multi-mechanism from single-mechanism
      MCs
- [ ] Every multi-mechanism MC has a chosen mechanism specified
      concretely enough that Phase 5 can implement against it
- [ ] Every multi-mechanism MC has at least one alternative
      considered with rejection reason
- [ ] Every multi-mechanism MC has principle-weighted rationale
      explicitly citing Step 02 weights
- [ ] Every multi-mechanism MC has a specific verification method
      named (not "tests will cover this")
- [ ] Inter-MC dependencies are surfaced and assembled into a
      dependency graph
- [ ] Comprehensiveness check is conducted; result documented
- [ ] Forward implications for Step 04, Step 05, Phase 3, Phase 6
      are listed

---

## Version History

| Version | Date | Source | Summary |
|---------|------|--------|---------|
| v1.0 | 2026-04-22 | Initial authoring | Initial Phase 2 Step 03 prompt. Draft-and-react mode with MC triage first (multi-mechanism vs. single-mechanism), then per-MC draft with chosen mechanism / alternatives / principle-weighted rationale / verification method / inter-MC dependencies. Inter-MC dependency graph feeds Step 04. Comprehensiveness check at end. |

---

*Part of the Phase 2 Analysis & Improvement Planning (Existing Projects) Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `analysis-improvement-planning.existing-project.instructions.md`*
*Previous step: `step-02-principle-weighting.prompt.md`*
*Next step: `step-04-sequencing-and-tiering.prompt.md`*
