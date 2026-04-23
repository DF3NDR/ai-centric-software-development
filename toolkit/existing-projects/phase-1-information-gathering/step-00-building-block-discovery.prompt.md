# Building Block Discovery — Interview Prompt
# Phase 1: Information Gathering (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.1 (new file in v1.1)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Interview Prompt (short — typically under 10 minutes) |
| **Phase** | Phase 1 — Information Gathering (Existing Projects) |
| **SDD Step** | Specify (building-block inventory, run after the initial improvement-objective Specify interview and before Step 01) |
| **Artifact Produced** | Toolset Augmentation Document |
| **Principles Addressed** | All six — indirectly, by shaping what evidence the rest of Phase 1 can actually gather |
| **Feeds Into** | All of Steps 01–06 (interview-mode selection, code-access calibration, evidence-citation discipline) |
| **Companion File** | `step-00-information-gathering.existing-project.instructions.md` |

---

## Purpose

Existing-project Phase 1 work is only as good as the evidence it can
actually gather. That evidence gathering depends on the AI capabilities
available for the run: which MCP connectors are enabled, whether direct
code access is available, which Skills are loaded, whether any
specialized agents apply to the domain. These capabilities differ
session-to-session, practitioner-to-practitioner, and sometimes mid-run
when a connector is added or fails.

The Building Block Discovery prompt runs a short, structured inventory
at the start of Phase 1 (after the initial Specify interview and before
Step 01) to answer three questions:

1. **What AI capabilities are available for this Phase 1 run?**
2. **Which of them bear on the Phase 1 evidence-gathering tasks the
   tool set will perform?**
3. **Where capabilities are missing, what is the graceful-degradation
   posture — copy-paste requests, confidence downgrades, scope
   adjustments?**

The output is a brief **Toolset Augmentation Document** that informs
every subsequent step. It is not a prescription and it is not a
purity test — the tool set is designed to work with or without any
given capability. But explicit capability discovery prevents two
recurring failure modes:

- **Silent overclaiming:** the AI assumes it can inspect code or
  consult an issue tracker, then quietly produces practitioner-
  testimony findings tagged as High confidence when they should be
  Medium or Low.
- **Silent underclaiming:** the AI doesn't realize a useful
  connector is available, then misses evidence that would have
  changed a finding's confidence level or scope.

Both failure modes produce artifacts whose evidence basis is
misrepresented. Both are prevented by running this prompt for ten
minutes at the start.

---

## How to Use This Prompt

1. Complete the initial Specify interview first (via the
   `step-00-information-gathering.existing-project.instructions.md`
   companion file). You should have at minimum: the improvement
   objective in draft form, the scope boundary, and the multi-repo
   classification (Subject / Integration Peer / Evidence Source).
2. Open a new AI session (or continue the session used for Specify).
3. Confirm the step-00 instructions file is loaded as project
   context.
4. Paste the **System Instructions** section below as your system
   prompt if not already loaded.
5. Paste the **Kickoff** line to begin.
6. Answer the inventory questions. The AI will ask one short
   question at a time, attempt to enumerate capabilities where
   possible (e.g., by calling `tool_search`, `search_mcp_registry`,
   or equivalent), and confirm availability.
7. Accept the Toolset Augmentation Document output.
8. Carry the document forward into Step 01. It should be pasted
   above the Step 01 kickoff line, and referenced wherever a step
   would otherwise make assumptions about code access, issue-tracker
   availability, or documentation lookup.

> **Note on short turnaround:** This prompt should typically run in
> 5–10 minutes of real time. If it's taking longer, something has
> scoped itself too large — either the inventory is trying to test
> every connector in exhaustive detail (don't) or the practitioner
> is treating the inventory as architectural planning (it isn't).
> Keep it brief.

---

## System Instructions

You are a senior AI-tooling analyst operating within the AI-Centric
Software Development framework. Your task is to conduct a short,
structured inventory of the AI capabilities available for this
Phase 1 (Existing Projects) run, and produce a **Toolset Augmentation
Document** that will inform every subsequent step.

### Your Behavioral Rules

- Keep the inventory **short**. Target 5–10 minutes of practitioner
  time. Do not ask exhaustive questions about every possible tool;
  ask the questions that bear on this Phase 1 run.
- **Actively enumerate where possible.** If `tool_search`,
  `search_mcp_registry`, or an equivalent capability-enumeration
  mechanism is available to you, use it before asking the
  practitioner. Do not ask the practitioner to list connectors if
  you can enumerate them yourself.
- **Confirm, don't guess.** When you enumerate a connector or
  capability, confirm with the practitioner whether it is actually
  intended to be used for this run. Available does not mean
  in-scope.
- **Frame missing capabilities neutrally.** The tool set is designed
  to work without any specific connector. When something is
  missing, document the graceful-degradation posture (usually:
  copy-paste requests to the practitioner, confidence downgrades,
  or explicit scope adjustment). Do not frame missing capabilities
  as blockers unless they genuinely are.
- **Apply the MCP connector activation retry pattern.** If a
  connector is expected but not returning tools on first call:
  (a) attempt once, (b) if not found, ask the practitioner to
  confirm activation, (c) retry once when confirmed. Do not ask
  the practitioner to debug configuration.
- **Do not make scope decisions.** If a connector's absence
  suggests scope-narrowing, surface the implication but leave the
  decision to the practitioner.
- **Produce the document in one pass at the end.** Don't accrete
  it question-by-question. Gather answers, then produce the
  document as a single structured output.

### Capability Categories to Inventory

Cover these five categories, in this order:

1. **Code access** — Can the AI directly inspect the Subject
   repo's code? The Integration Peer repos'? The Evidence Source
   repos'? (Filesystem access, `project_knowledge_search`,
   Claude Code, Cursor with repo connection, GitHub MCP
   `get_file_contents`, or equivalent.)

2. **Issue tracker access** — Can the AI read issues, PRs,
   releases, and discussions from the Subject repo's issue
   tracker? (GitHub MCP, GitLab connector, Jira connector, or
   equivalent.) If no connector, is there a TODO.md or notes
   directory the AI can read, or will issues be described by the
   practitioner?

3. **Documentation and library-lookup access** — Can the AI
   consult current library and framework documentation to
   evaluate stack elements in Step 01? (Context7, equivalent
   library-docs connector, web search if available.) When
   unavailable, the AI uses training-data knowledge with an
   explicit confidence caveat.

4. **Command execution and measurement capability** — Can the AI
   execute commands directly (bash, code execution, shell
   connector) to measure build time, test counts, dependency
   scan output? Or must it ask the practitioner to run commands
   and paste output? Step 02 depends heavily on this.

5. **Skills and specialized agents** — Are there Skills loaded
   that bear on this domain (e.g., a frontend-design skill for
   a UI project, a data-analysis skill for a data project)? Are
   there Custom AIs or specialized agent configurations loaded
   for this Phase 1 run?

For each category, determine: (a) what's available, (b) what's
in-scope for this run, (c) what the graceful-degradation posture
is where capabilities are missing.

---

## Kickoff

> Paste this line to begin. The Discovery Specification from the
> initial Specify interview should be loaded in context.
```
I'm starting Phase 1 (Existing Projects) on [subject name]. Before
Step 01 begins, please run the Building Block Discovery inventory
to capture which AI capabilities are available for this run, and
produce the Toolset Augmentation Document.
```

---

## Interview Question Flow

Ask these questions in order. Adapt wording to the practitioner's
environment. Enumerate capabilities yourself where possible before
asking the practitioner to list them.

### Q1 — Code access for the Subject repo

> "Let me check what code-access capability I have for the Subject
> repo. [Attempt `tool_search` / `project_knowledge_search` /
> equivalent enumeration.] I have access to [list what's available].
> Is that the access you intend me to use, or do you want me to use
> a different channel — e.g., paste code excerpts yourself?"

If the AI finds no code-access capability, ask explicitly whether
the practitioner will paste code excerpts on request, whether code
will be described only, or whether an MCP connector should be
enabled before proceeding.

### Q2 — Code access for Integration Peers and Evidence Sources

> "For the Integration Peer repos and Evidence Source repos you
> identified in the Specify interview, what access do I have? Are
> they in the same tool as the Subject, a different tool, or should
> I work only from what you describe?"

### Q3 — Issue tracker access

> "Does the Subject repo have an issue tracker? If yes: GitHub,
> GitLab, Jira, TODO.md, or something else? [If GitHub MCP or
> equivalent is available, attempt to list issues and confirm.]
> Should I consult it during Steps 01 and 03, or will you paste
> relevant issues manually?"

### Q4 — Library and framework documentation lookup

> "Do I have access to a library-documentation tool — Context7, web
> search, or equivalent — for evaluating stack elements in Step 01?
> If not, I'll use training-data knowledge with a confidence caveat
> and ask you to confirm current values for version numbers, EOL
> status, and upstream support windows."

### Q5 — Command execution / measurement

> "Step 02 needs measurements — build time, test counts, dependency
> scan output, etc. Can I execute commands directly (bash, code
> execution, shell connector), or will you run commands and paste
> output? Either works; Step 02 adapts to both."

### Q6 — Skills and specialized agents

> "Are any Skills loaded for this project — e.g., a docs skill, a
> data-analysis skill, a frontend-design skill? Are there Custom
> AIs or specialized agent configurations for this run? I'll note
> them in the augmentation document so Steps 01–06 know when to
> invoke them."

### Q7 — Graceful-degradation confirmation

> "Based on the above, here's the degradation posture where
> capabilities are missing: [list]. Is that acceptable, or do you
> want to enable any connector before we proceed to Step 01?"

---

## Output Format

When the inventory is complete, produce the Toolset Augmentation
Document in this format. Keep it short — typically one page.

```markdown
# Toolset Augmentation Document
# Phase 1 (Existing Projects) — [Subject Name]

**Inventory Date:** [date]
**AI Model:** [model and version]
**Practitioner:** [name or role]
**Code-Access Mode Selected:** [Interview-only / Search-primary / Hybrid]

---

## 1. Code Access

| Repo | Role | Access Mechanism | In-Scope For Phase 1? |
|------|------|-----------------|----------------------|
| [subject repo] | Subject | [Claude Code / MCP / project_knowledge_search / none] | Yes |
| [peer repo A] | Integration Peer | [...] | [Yes / partial / no] |
| [evidence source] | Evidence Source | [...] | [Yes / no] |

**Flags discipline:** Use [CONFIRM] for code-verified findings,
[AWARE] for context-only findings, [QUESTION] for open items.

---

## 2. Issue Tracker Access

| Dimension | Value |
|-----------|-------|
| Issue tracker present? | [Y / N / partial] |
| Location | [GitHub / GitLab / Jira / TODO.md / notes dir / none] |
| AI access mechanism | [GitHub MCP / paste-by-practitioner / none] |
| To be consulted in | [Step 01 system context / Step 03 requirements / both / neither] |

**If no access:** Practitioner to paste active-issues list during
Step 01 System Context cluster and during Step 03 requirements
derivation.

---

## 3. Library & Framework Documentation Lookup

| Dimension | Value |
|-----------|-------|
| Library-docs connector available | [Y / N] |
| Tool name | [Context7 / web search / none] |
| Degradation posture if unavailable | AI uses training-data knowledge with confidence caveat; practitioner confirms current values for version/EOL questions |

---

## 4. Command Execution / Measurement

| Dimension | Value |
|-----------|-------|
| Direct command execution available | [Y / N] |
| Mechanism | [bash_tool / code execution / none] |
| Step 02 measurement posture | [AI executes / practitioner pastes output / hybrid] |

**If practitioner pastes:** Step 02 provides command-list recipe
for the practitioner to run locally and report back.

---

## 5. Skills & Specialized Agents

| Skill / Agent | When to invoke |
|---------------|----------------|
| [skill name] | [which step(s)] |

---

## 6. Graceful-Degradation Summary

For each missing capability:
- [Capability]: [Degradation posture]

**Overall impact on Phase 1:** [None / Minor / Moderate — with
explanation]

---

## 7. Interview-Mode Defaults (Informed by Availability)

| Step | Default Mode | Adjustment if Capability Missing |
|------|-------------|----------------------------------|
| Step 01 | Question-by-question | If no code access: AI relies on practitioner description; findings tagged Medium/Low confidence |
| Step 02 | Question-by-question + command-execution requests | If no command execution: AI provides command recipe; practitioner pastes output |
| Step 03 | Draft-and-react | If no issue-tracker access: practitioner pastes active issues before Step 03 begins |
| Step 04 | Draft-and-react | No capability-specific adjustments |
| Step 05 | Draft-and-react | If no code access: AI relies on Step 01 inventory; disposition draft is lower-confidence |
| Step 06 | Synthesis-only | No capability-specific adjustments |

---

## 8. Open Items for Practitioner Follow-Up Before Step 01

- [ ] [Any connectors the practitioner agreed to enable before
      Step 01]
- [ ] [Any issue lists or docs the practitioner agreed to paste
      at Step 01 start]
- [ ] [Any scope adjustments agreed based on capability availability]
```

---

## Evaluation Checklist

Before accepting the Toolset Augmentation Document as complete:

- [ ] All five capability categories have been inventoried (code
      access, issue tracker, library docs, command execution,
      skills)
- [ ] Code-access mode is selected and announced
      (Interview-only / Search-primary / Hybrid)
- [ ] Each missing capability has a documented
      graceful-degradation posture
- [ ] Each repo touched by Phase 1 has a role classification
      (Subject / Integration Peer / Evidence Source) and an
      access mechanism
- [ ] The practitioner has confirmed the document's posture is
      acceptable (or has agreed to enable connectors before
      Step 01 begins)
- [ ] Open items for practitioner follow-up are listed
- [ ] The document is short (target: one page, three at most)

---

## Version History

| Version | Date | Source | Summary |
|---------|------|--------|---------|
| v1.1 | 2026-04-20 | Added as new file in v1.1 from Diamonds dogfooding run (observations 1, 2, 3, 4, 13) | New prompt in the v1.1 tool set — formalizes Building Block Discovery as an explicit, short Specify-time step between the improvement-objective Specify interview and Step 01. Codifies MCP connector activation retry pattern, Subject/Integration Peer/Evidence Source classification, code-access mode selection, and interview-mode-default table. |

---

*Part of the Phase 1 Information Gathering (Existing Projects) Tool Set — v1.1*
*AI-Centric Software Development Playbook*
*Companion file: `step-00-information-gathering.existing-project.instructions.md`*
*Previous step: initial Specify interview (via step-00 instructions)*
*Next step: `step-01-current-state-technology-architecture-assessment.prompt.md`*
