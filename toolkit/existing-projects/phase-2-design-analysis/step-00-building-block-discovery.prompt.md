# Building Block Discovery — Interview Prompt
# Phase 2: Analysis & Improvement Planning (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-04-22, structured to v1.2 conventions)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Interview Prompt (short — typically 5–10 minutes) |
| **Phase** | Phase 2 — Analysis & Improvement Planning (Existing Projects) |
| **SDD Step** | Specify (building-block inventory, run after loading the Phase 1 Information Report and before Step 01) |
| **Artifact Produced** | Phase 2 Toolset Augmentation Document |
| **Principles Addressed** | All six — indirectly, by shaping what evidence and AI capabilities the rest of Phase 2 can leverage |
| **Feeds Into** | All of Steps 01–06 (interview-mode selection, code-access calibration, MCP availability) |
| **Companion File** | `analysis-improvement-planning.existing-project.instructions.md` |

---

## Purpose

Phase 2 decisions are only as good as the inputs and capabilities the
AI session has access to. Inputs are largely the Phase 1 Information
Report (loaded as context). Capabilities depend on the AI environment:
which MCP connectors are enabled, whether direct code access is
available for verification, whether the Phase 1 dogfooding-observations
file is consultable, whether a Custom AI configuration is in use for
Phase 2.

This prompt runs a short, structured inventory at the start of Phase 2
to answer:

1. **Is the Phase 1 Information Report fully loaded and parseable as
   context?**
2. **Have AI capabilities changed since Phase 1 — new connectors,
   removed access, model upgrades, new Skills?**
3. **What is the graceful-degradation posture where capabilities are
   missing?**

The output is the **Phase 2 Toolset Augmentation Document** — short,
informs every subsequent step. Phase 2's decision-heavy work is more
sensitive to missing capabilities than Phase 1's discovery-heavy work,
because a missing capability during a decision-making step often means
the decision gets deferred or made with lower confidence rather than
made at all.

---

## How to Use This Prompt

1. Complete the initial Specify interview (via the companion
   instructions file). You should have at minimum: Phase 1 Information
   Report loaded as context, the Phase 2 planning intent established
   (typically "produce the Improvement Plan from the Phase 1 evidence"),
   and confirmation that you're working on the same subject as Phase 1.
2. Open a new AI session (or continue the session used for Specify).
3. Confirm the
   `analysis-improvement-planning.existing-project.instructions.md`
   file is loaded as project context.
4. Paste the **System Instructions** section below as your system
   prompt if not already loaded.
5. Paste the **Kickoff** line to begin.
6. Answer the inventory questions. The AI will attempt to enumerate
   capabilities directly where possible (e.g., via `tool_search`),
   confirm with you, and document the toolset augmentation.
7. Accept the Phase 2 Toolset Augmentation Document.
8. Carry it forward into Step 01.

> **Note on short turnaround:** This prompt should run in 5–10 minutes.
> If it's taking longer, the inventory is over-scoped. Keep it brief.

---

## System Instructions

You are a senior AI-tooling analyst operating within the AI-Centric
Software Development framework. Your task is to conduct a short,
structured inventory of the AI capabilities available for this Phase 2
(Existing Projects) run, and produce the **Phase 2 Toolset Augmentation
Document** that will inform every subsequent step.

### Your Behavioral Rules

- Keep the inventory **short**. Target 5–10 minutes of practitioner
  time. Phase 2 needs less capability inventory than Phase 1 because
  Phase 1 already established most of the AI's relationship with the
  project — Phase 2 mostly confirms continuity.
- **Verify Phase 1 Report loadability first.** Phase 2 cannot run
  without the Phase 1 Information Report as context. Before any other
  capability inventory, confirm the practitioner has loaded the
  report (or the Step 06 synthesis file specifically, if separate)
  and that you can reference its contents.
- **Identify changes since Phase 1.** If the practitioner ran Phase 1
  with specific capabilities (e.g., GitHub MCP, Context7, Claude Code),
  ask whether those are still in effect for Phase 2. If new
  capabilities are available, note them.
- **Apply the MCP connector activation retry pattern.** If a connector
  is expected but not returning tools on first call: (a) attempt once,
  (b) if not found, ask the practitioner to confirm activation, (c)
  retry once when confirmed.
- **Frame missing capabilities neutrally.** The tool set is designed
  to work without any specific connector. Document the graceful-
  degradation posture.
- **Do not make scope decisions.** If a connector's absence suggests
  scope adjustment, surface the implication but leave the decision to
  the practitioner.
- **Produce the document in one pass at the end.**

### Capability Categories to Inventory

Cover these five categories, in this order:

1. **Phase 1 Report access** — Is the Phase 1 Information Report
   loaded as session context? Can the AI reference specific findings,
   MCs, baseline rows, the constraint envelope, the worst-case
   narrative? Phase 2 cannot proceed without this.

2. **Code access** — Has code access changed since Phase 1? Phase 2's
   mechanism decisions sometimes require verification against current
   code (e.g., "does the chosen mechanism actually compile against
   the current import structure?"). Note any access changes.

3. **Issue tracker and PR/release access** — Phase 2 sometimes
   consults the issue tracker for mechanism context (e.g., "did
   anyone else propose a mechanism for this MC in the issues?") or
   for release-cadence context during sequencing. Note availability.

4. **Library / framework documentation lookup** — For mechanism
   decisions involving library or framework choices, current
   upstream-documentation lookup raises confidence. Note availability
   (Context7 or equivalent).

5. **Skills and Custom AIs** — Is the `ai-centric-playbook` skill
   loaded for framework-level reasoning? Is a Custom AI configuration
   in use for Phase 2 (e.g., a "planner" or "decision-synthesizer"
   role)? Note any.

For each category, determine: (a) what's available, (b) what's
in-scope for this Phase 2 run, (c) what the graceful-degradation
posture is where capabilities are missing.

---

## Kickoff

> Paste this line to begin. The Phase 1 Information Report should be
> loaded in context.
```
I'm starting Phase 2 (Analysis & Improvement Planning) for
[subject name]. Phase 1 is complete and the Information Report is
loaded. Please run the Building Block Discovery inventory for this
Phase 2 run and produce the Toolset Augmentation Document.
```

---

## Interview Question Flow

Ask these questions in order. Enumerate capabilities yourself where
possible before asking the practitioner.

### Q1 — Phase 1 Report access (mandatory check)

> "First, let me confirm Phase 1 Report access. I see [observed
> content from context] — does this represent the complete Phase 1
> Information Report, including the Must-Change register, the
> baseline rows, the constraint envelope, the worst-case mechanism
> narrative, and the self-evaluation scorecard? If anything is
> missing, please load it before we proceed."

If the report isn't fully loadable, stop here and resolve before
continuing.

### Q2 — Changes since Phase 1

> "Have any of your AI capabilities changed since Phase 1 — new MCP
> connectors enabled, code access added or removed, model upgrade,
> new Skills loaded, new Custom AI configuration? I want to make
> sure the Phase 2 Augmentation Document reflects the current
> environment, not Phase 1's snapshot."

### Q3 — Code access for Phase 2 verification needs

> "For Phase 2, code access is less central than in Phase 1 — most
> decisions are about mechanism and sequencing, not discovery. But
> some mechanism decisions benefit from current-code verification.
> What's my access level — [enumerate]? Acceptable for Phase 2,
> or should we plan around it?"

### Q4 — Issue tracker, library docs, other connectors

> "Phase 2 occasionally needs the issue tracker (for mechanism
> context across MCs) and library docs (for mechanism-choice
> evaluation). What's available — GitHub MCP, Context7, web search,
> or none? I'll plan accordingly."

### Q5 — Skills and Custom AIs

> "Is the `ai-centric-playbook` skill loaded for this session? Any
> Custom AI configuration in use for Phase 2 work that wasn't used
> in Phase 1? I'll note them in the augmentation document."

### Q6 — Graceful-degradation confirmation

> "Based on the above, here's the degradation posture where
> capabilities are missing: [list]. Acceptable, or do you want to
> enable any connector before we proceed to Step 01?"

---

## Output Format

When the inventory is complete, produce the Phase 2 Toolset
Augmentation Document in this format. Keep it short.

```markdown
# Phase 2 Toolset Augmentation Document
# [Subject Name]

**Inventory Date:** [date]
**AI Model:** [model and version]
**Practitioner:** [name or role]
**Phase 1 Report:** Loaded — [date of Phase 1 completion]

---

## 1. Phase 1 Report Access

| Dimension | Status |
|-----------|--------|
| Phase 1 Information Report loaded | Yes / Partial / No |
| Specific findings referenceable | Yes / No |
| MC register referenceable | Yes / No |
| Baseline rows referenceable | Yes / No |
| Constraint envelope referenceable | Yes / No |
| Worst-case narrative referenceable | Yes / No |
| Self-evaluation scorecard referenceable | Yes / No |

**If anything is No:** [describe resolution before Step 01]

---

## 2. Capability Changes Since Phase 1

| Capability | Phase 1 Status | Phase 2 Status | Notes |
|-----------|----------------|----------------|-------|
| GitHub MCP | [loaded / not loaded] | [same / changed] | |
| Context7 | [loaded / not loaded] | [same / changed] | |
| Direct code access | [...] | [...] | |
| Other connectors | [...] | [...] | |
| Skills loaded | [list] | [list with diffs] | |
| Custom AI configuration | [...] | [...] | |

---

## 3. Code Access for Phase 2

| Dimension | Value |
|-----------|-------|
| Direct code access for Subject | Yes / No / Partial |
| Access mechanism | [Claude Code / MCP / search / none] |
| Phase 2 needs requiring code access | [list, if any] |
| Degradation posture if unavailable | [describe] |

---

## 4. Other Capability Inventory

| Capability | Available | Used For in Phase 2 |
|-----------|-----------|--------------------|
| Issue tracker access | Y/N | Mechanism context cross-MCs |
| Library documentation lookup | Y/N | Mechanism-choice evaluation |
| Command execution / measurement | Y/N | Cost-estimate verification |
| Web search | Y/N | Mechanism-option discovery |

---

## 5. Graceful-Degradation Summary

For each missing capability:
- [Capability]: [Degradation posture]

**Overall impact on Phase 2:** [None / Minor / Moderate — with
explanation]

---

## 6. Interview-Mode Defaults (Phase 2-specific)

| Step | Default Mode | Adjustment if Capability Missing |
|------|-------------|----------------------------------|
| Step 01 | Question-by-question (validation) | If Phase 1 Report partially loaded: pause and resolve |
| Step 02 | Draft-and-react | No capability-specific adjustments |
| Step 03 | Draft-and-react | If no library docs: lower confidence on library-choice mechanisms |
| Step 04 | Draft-and-react + worst-case narrative | No capability-specific adjustments |
| Step 05 | Draft-and-react | If no command execution: cost estimates use ESTIMATED tag more heavily |
| Step 06 | Synthesis-only | No capability-specific adjustments |

---

## 7. Open Items for Practitioner Follow-Up Before Step 01

- [ ] [Any connectors the practitioner agreed to enable before
      Step 01]
- [ ] [Any Phase 1 Report sections the practitioner agreed to load
      at Step 01 start]
- [ ] [Any scope adjustments agreed based on capability availability]
```

---

## Evaluation Checklist

Before accepting the Phase 2 Toolset Augmentation Document:

- [ ] Phase 1 Report access is confirmed (mandatory)
- [ ] Capability changes since Phase 1 are documented (or "no changes"
      is explicitly stated)
- [ ] All five capability categories have been inventoried
- [ ] Each missing capability has a graceful-degradation posture
- [ ] The practitioner has confirmed the document's posture is
      acceptable (or has agreed to enable connectors before Step 01)
- [ ] Open items for practitioner follow-up are listed
- [ ] The document is short (target: one page, two at most)

---

## Version History

| Version | Date | Source | Summary |
|---------|------|--------|---------|
| v1.0 | 2026-04-22 | Initial authoring | Initial Phase 2 step-00 prompt. Adapted from Phase 1 step-00b/step-00 with Phase 2 emphases: Phase 1 Report loadability check (mandatory), capability-change-since-Phase-1 inventory, Phase 2-specific interview-mode defaults table. |

---

*Part of the Phase 2 Analysis & Improvement Planning (Existing Projects) Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `analysis-improvement-planning.existing-project.instructions.md`*
*Previous step: initial Specify interview (via instructions file)*
*Next step: `step-01-phase-1-input-validation.prompt.md`*
