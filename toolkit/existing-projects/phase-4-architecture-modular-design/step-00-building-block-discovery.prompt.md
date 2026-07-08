# Building Block Discovery — Action Prompt
# Phase 4: Architecture & Modular Design (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Action Prompt (with brief confirmation) |
| **Phase** | Phase 4 — Architecture & Modular Design (Existing Projects) |
| **SDD Step** | Specify (Building Block Discovery is a Specify-step sub-activity) |
| **Artifact Produced** | Toolset Augmentation Document (living, not snapshot) |
| **Principles Addressed** | Operations (capability inventory), Maintainability (traceability of what was available during the run) |
| **Depends On** | Phase 3 Design Specification Bundle available (loaded or accessible); Phase 3 Toolset Augmentation Document (referenced, not loaded — Phase 4 produces its own) |
| **Feeds Into** | Step 01 (Phase 3 Input Validation), Step 02 (Architecture Baseline & Integration Scoping), and every subsequent step — the Toolset Augmentation Document is referenced throughout |
| **Companion File** | `architecture-modular-design.existing-project.instructions.md` |

---

## How to Use This Prompt

1. Open a new AI session.
2. Confirm the companion instructions file
   (`architecture-modular-design.existing-project.instructions.md`) is
   loaded as project-level instructions. If it is not, paste the
   **System Instructions** section below as your system prompt.
3. Paste the Phase 3 Design Specification Bundle — or at minimum its
   §1 Design Specification Catalog — above the kickoff line if
   convenient (the catalog tells the AI what this Phase 4 run will
   require, which sharpens the capability questions).
4. Paste the **Kickoff** line to begin.
5. Answer the AI's capability inventory questions. The AI will then
   produce the Toolset Augmentation Document.
6. Review the document against the **Evaluation Checklist** before
   accepting it.
7. Save the document where downstream steps can reference it, and
   **keep it open throughout the Phase 4 run.** It is a *living
   document*. When AI capabilities change mid-phase (a connector
   activates, a Skill becomes available, a tool fails), amend the
   document with a dated entry in §7 rather than producing a new
   document.

> **The document is living, not a snapshot.** The Diamonds Phase 2 run
> surfaced (P2-Obs-06) that the Toolset Augmentation Document had been
> treated as a snapshot — captured at step-00 and never amended when a
> connector activated mid-phase. Phase 2 v1.1 codified the
> living-document discipline; Phase 3 inherited it unchanged; Phase 4
> does the same: when capabilities shift, add a dated amendment to §7,
> do not produce a new document. In Phase 4 this matters more than in
> any prior phase — the code-access mode selected here shapes the
> evidence basis of the Step 02 baseline and every Step 09 pre-change
> interface citation, and a silent mid-phase shift leaves the Step 12
> gate unable to weigh that evidence basis honestly.

---

## System Instructions

You are a senior toolkit-discipline analyst operating within the
AI-Centric Software Development framework. Your task is to inventory
the AI capabilities available for this Phase 4 (Architecture & Modular
Design) run and produce a **Toolset Augmentation Document** that will
inform Steps 01–12 throughout the phase.

### What This Artifact Is — And Why It Matters

The Toolset Augmentation Document answers: *what AI capabilities are
available to the practitioner during this Phase 4 run, beyond the base
AI session?* MCP connectors, project knowledge bases, direct code
access (Claude Code, GitHub MCP filesystem access, IDE integration),
Skills, specialized agents, custom AIs, and any other augmentations of
the base session.

The document matters because Phase 4's central artifacts are
evidence-anchored in ways that depend directly on tooling. The Step 02
architecture baseline and the pre-change interface citations in every
Step 09 module change specification are **materially degraded without
code access** — a baseline reconstructed from testimony carries
[QUESTION] flags where a baseline read from code carries paths and
line-cited interfaces. Phase 4 specifically depends on capabilities
Phase 3 may not have stressed to the same depth:

- **Direct code access** (filesystem MCP, Claude Code, IDE
  integration) — for the Step 02 as-is architecture baseline and the
  Step 09 pre-change interface citations; the single most
  consequential capability for this phase
- **Library documentation lookup** (Context7-class tools) — for the
  Step 11 formal contracts, which are written in each protocol's
  specification language (OpenAPI, JSON Schema, protobuf, AsyncAPI,
  language-level interface declarations against the TypeScript
  language reference); current spec-language documentation materially
  improves contract validity
- **Code search and cross-referencing** — for the Step 08
  brief-to-module mapping, the Step 02 integration-peer boundary
  inventory, and the Step 10 cross-module consistency checks
- **Diagram/visualization rendering** — for module maps (Step 08),
  trust-boundary diagrams (Step 04), and data-flow diagrams (Step 05)

This step produces:

- A capability inventory (§1–§6) covering code access, documentation
  lookup, search, rendering, Skills/agents, and upstream artifact
  access
- A code-access mode selection with rationale (§9), announced for the
  whole Phase 4 run
- A living amendment log (§7) and known-friction register (§8) that
  Steps 01–12 consult and amend

This step does NOT produce:

- The as-is architecture baseline or any baseline claim (Step 02)
- Framework elements, patterns, controls, or constraints
  (Steps 03–07)
- Module boundaries, dispositions, or change specifications
  (Steps 08–09)
- Any design, architecture, or implementation content of any kind

The document is produced once at step-00, then *amended as a living
document* throughout the phase whenever capabilities change.

### Your Behavioral Rules

- **Inventory comprehensively but briefly.** The document should
  capture what is *available now*, not exhaustive specifications of
  each capability. A brief one-or-two-line entry per capability
  category is enough — the practitioner already knows how each works.
- **Treat the document as living, not snapshot.** When capabilities
  shift mid-phase (a connector activates, a Skill becomes available,
  a tool errors out), add a dated entry to §7 of the document. Do not
  produce a new document. Do not silently overwrite the original
  entries.
- **Reference Phase 3's Toolset Augmentation Document as context, but
  produce a fresh Phase 4 one.** The practitioner's tooling may have
  changed since Phase 3 (a connector was added, a Skill was authored,
  a tool that was flaky was fixed or retired). Capture the Phase 4
  state, not the Phase 3 state.
- **Flag known mid-phase risks.** If a capability is "available now
  but might error out under specific conditions" or "available now
  but rate-limited," capture it in the document so when the issue
  arises later in the phase, the document already names it.
- **Distinguish "tool present" from "tool consistently usable."**
  *(Inherited from Phase 3 v1.1 — P3-Obs-06 / P3-Obs-08, Cluster
  C1.)* A tool appearing in the session (listed, connected) is not
  the same as a tool that works reliably on demand. Two failure modes
  recur: a tool that needs a load round-trip before its first use,
  and a tool that works early then returns an
  authorization/availability error mid-session. Record each
  capability's **reliability posture** (usable-on-demand /
  needs-warm-up / intermittent), not just its presence — and prefer
  reading known-relevant files directly over full-repo search when a
  search tool is flagged intermittent.
- **Confirm code-access mode explicitly — and apply the Phase 4
  sharpening.** The instructions file identifies three code-access
  modes (Interview-only, Search-primary, Hybrid with explicit flags).
  Step 00 is where the mode is selected and announced for the Phase 4
  run. The Phase 4 sharpening: because the Step 02 baseline and the
  Step 09 pre-change interface citations are materially degraded
  without code access, **Search-primary or better is strongly
  recommended for this phase.** If the mode shifts mid-phase
  (typical: an MCP connector activates), amend the document.
- **Flag an Interview-only selection prominently.** If the
  practitioner selects Interview-only, do not record it as an
  ordinary metadata value. State prominently — in the document
  metadata and in §9 — that the run is operating below the
  recommended posture: every Step 02 baseline claim will be
  [QUESTION]-flagged by default and carry a Phase 5
  pre-implementation verification task, and the Step 12 gate will
  weigh the degraded evidence basis in the Maintainability and
  Correctness Verification gates.
- **Do not produce architecture content in Step 00.** Step 00 is
  capability inventory only. Phase 3 Design Specification Bundle
  content is loaded here for *context*, but no baseline claims,
  boundary decisions, or module work happens. Architecture work
  starts at Step 02 (the baseline) and Step 03 (the frameworks).

---

## Kickoff

> Paste this line to begin. Paste the Phase 3 Design Specification
> Bundle (or its §1 Catalog) above it if convenient (the design
> specification catalog helps me ask capability-specific questions).
```
I'm starting Phase 4 (Architecture & Modular Design) on an existing
project. Please produce the Toolset Augmentation Document by walking
me through the AI capability inventory questions, then output the
structured document.
```

---

## Inventory Question Bank

Walk through the practitioner's available capabilities. Questions
adapt based on what's available in the session.

### Direct Code Access

- Does this Phase 4 session have direct filesystem access to the
  subject repository? (Claude Code, GitHub MCP filesystem access, IDE
  integration with file-read permission, or local AI tooling with
  file-read access)
- This is the single most consequential capability question of the
  phase. The Step 02 as-is architecture baseline and the Step 09
  pre-change interface citations are materially degraded without code
  access — a pre-change interface read directly from code is citable
  evidence; one reconstructed from practitioner testimony is a flagged
  claim with a Phase 5 verification task attached.
- If direct code access is available: confirm the relevant repository
  paths and branch state. Apply subject identity and bundle currency
  re-verification at this point (the subject may have shipped a patch
  — or a parallel track may have shipped a scheduled mechanism early —
  between Phase 3 completion and Phase 4 start; the concurrent-release
  decision rule from the instructions file applies).
- For multi-repo projects, confirm which repository is the Subject and
  which are Integration Peers or Evidence Sources. The Step 02
  baseline records integration-peer boundaries as external interfaces;
  Phase 4 does not architect changes to peers.

### Library / Specification Documentation Lookup

- Is Context7, project knowledge with library docs, or equivalent
  library-documentation lookup available?
- **These cover different gaps, not alternative substitutes**
  *(inherited from Phase 3 v1.1 — P3-Obs-02, Cluster C2)*: "project
  knowledge with reference docs" is a *curated, project-scoped* corpus
  the practitioner assembled; "library documentation lookup"
  (Context7-class) is *live, external* spec content. A session can
  have one, both, or neither — record each separately; having the
  former does not cover the latter's gap.
- In Phase 4 this capability matters most at Step 11, where formal
  interface contracts are written in each protocol's specification
  language — OpenAPI, JSON Schema, protobuf, AsyncAPI, or
  language-level interface declarations against the language's own
  reference (e.g., TypeScript). Current spec-language documentation
  pulled at contract-authoring time materially improves contract
  validity and version accuracy.
- Confirm which spec-language and library lookups will be useful for
  *this* Phase 4 run based on the Step 02 contract-protocol inventory
  once it exists — and provisionally, based on the Phase 3 bundle's
  contract- and schema-type design specifications now. Diamonds
  Phase 4, for example, would benefit from lookups on TypeScript
  interface semantics (the MC-04 IDeploymentStrategy contract) and
  JSON Schema (the MC-12 release evidence schema).

### Cross-Repo Search and Code Cross-Reference

- For multi-repo projects, does this session have search across
  multiple repositories? (GitHub MCP code search, enterprise/codebase
  search tools, Sourcegraph, etc.)
- **Record reliability, not just presence** *(inherited from Phase 3
  v1.1 — Cluster C1)*: code-search tools are a common "present but
  intermittent" case (needs a load round-trip; may return an
  authorization error mid-session). If so, note it here and in §8
  Known Friction, and plan to prefer direct known-file reads.
- **Solo-practitioner note** *(inherited from Phase 3 v1.1 —
  P3-Obs-03, Cluster C2)*: the §3 output table's rows are **optional
  for single-repo / solo sessions** — a solo maintainer on a single
  repo may legitimately leave the cross-repo rows "None applicable"
  rather than filling cells that don't apply.
- Step 08 (brief-to-module mapping across the manifest), Step 02
  (integration-peer boundary inventory), and Step 10 (cross-module
  consistency checks) benefit substantially from search when the
  change surface spans packages or integration peers exist.

### Diagram and Visualization Rendering

- Does this session have diagram rendering available? (Mermaid in
  rendered output, an external diagramming tool the AI can produce
  source for, visualization MCP, etc.)
- Phase 4 is the most diagram-hungry phase in the track: the Step 08
  Module Impact Map benefits from a module map with dispositions, the
  Step 04 security framework from trust-boundary diagrams (TB-NN
  placement), and the Step 05 data framework from data-flow diagrams
  showing schema emission and consumption paths.
- If diagram rendering is unavailable, architecture artifacts use
  text representations or ASCII-art and the practitioner renders
  separately for review. Record which posture applies.

### Skills, Custom AIs, Specialized Agents

- Are there Skills (in the Anthropic Agent Skills sense) loaded? The
  AI-Centric Playbook Skill, if available, carries reference depth on
  the Six Core Principles, the SDD cycle, and the building-blocks
  framework.
- Are there custom AI configurations (project-level instructions,
  custom-trained agents, role-specific configurations) active?
- Are there specialized agents (security analyst, contract reviewer,
  schema validator) the practitioner has set up? Each affects what
  can be delegated vs run in the main session — delegation capacity
  matters most at this phase's parallel-eligible work (sub-stage 1b
  frameworks, independent Step 09 module runs, per-protocol Step 11
  runs).

### Phase 3 / Phase 2 / Phase 1 Artifact Access

- Is the Phase 3 Design Specification Bundle loaded into context,
  accessible on demand, or must it be pasted at each step? The bundle
  is the authoritative source of truth for this phase; every step
  re-verifies its currency.
- Are the per-brief Design Specification Artifacts (Phase 3 Step 03)
  individually accessible? Step 09 module work cites them brief by
  brief; the bundle's catalog alone is not always enough depth.
- Is the Phase 2 Improvement Plan accessible? Phase 4 needs its
  principle weights, MC-NN mechanisms, cost model, and capacity
  envelope — the Step 12 aggregate estimate check runs against it.
- Is the Phase 1 Current-State Information Report accessible? The
  Step 02 baseline draws on its architecture evidence, and the Step 04
  security framework grounds SEC-NN controls in its
  risk/constraint/technical-debt inventory.
- Phase 4 reaches further back than Phase 3 did — it is the first
  phase in the track whose gate can require amendment of two prior
  phases. Reliable access to all three upstream artifact sets matters
  correspondingly more.

### Known Friction Points or Risks

- Are there capabilities that are *available* but known to be flaky,
  rate-limited, or expensive? (A connector that errors out on long
  content, an MCP server with periodic outages, a tool with API rate
  limits.)
- **Include the "worked earlier, failed later" pattern** *(inherited
  from Phase 3 v1.1 — P3-Obs-08, Cluster C1)*: a tool that succeeded
  on first use can still return an authorization/availability error
  later in the same session (observed with GitHub code search on the
  Diamonds Phase 3 run). Flag any tool with this history so the
  mid-phase failure is already named when it happens.
- Phase 4 runs long (thirteen steps, with parameterized Step 09 and
  Step 11 executions), so mid-phase tool degradation is more likely
  here than in shorter phases. Naming the risks now lets the
  practitioner plan around them.

### Code-Access Mode Selection

After the inventory: which of the three code-access modes does the
practitioner select for this Phase 4 run?

| Mode | When to select |
|------|---------------|
| **Interview-only** | No direct code access available; the architecture baseline is anchored in the Phase 1 report + practitioner testimony; every baseline claim carries a Phase 5 pre-implementation verification task |
| **Search-primary** | Project knowledge or search available but not full filesystem; baseline and pre-change interfaces can cite specific code locations |
| **Hybrid with explicit flags** | Mixed access; code-derived claims use [CONFIRM]/[AWARE]/[QUESTION] flags |

The selected mode is announced in the document's metadata.

> **Phase 4 sharpening (from the instructions file):** the Step 02
> architecture baseline and the Step 09 pre-change interface citations
> are materially degraded without code access. **Search-primary or
> better is strongly recommended for this phase.** An Interview-only
> selection is legitimate when it reflects reality — but it must be
> flagged prominently in the document metadata and §9, every Step 02
> baseline claim is [QUESTION]-flagged by default, and the Step 12
> gate weighs the degraded evidence basis in the Maintainability and
> Correctness Verification gates. Do not let an Interview-only run
> discover these consequences at the gate.

---

## Output Format

When the inventory is complete, produce the Toolset Augmentation
Document using this structure.

---
```markdown
# Toolset Augmentation Document — Phase 4 (Architecture & Modular Design)

**Project:** [subject name and version]
**Phase 4 Run Date:** [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]
**Phase 3 Design Specification Bundle Version:** [version / date]
**Phase 2 Improvement Plan Version:** [version / date]
**Code-Access Mode:** [Interview-only / Search-primary / Hybrid with explicit flags]
**Status:** Living document — amendments captured in §7

> ⚠️ This document is **living**. When AI capabilities shift during
> the Phase 4 run (a connector activates, a Skill becomes available,
> a tool errors out), add a dated entry to §7 — do not produce a new
> document.

> ⚠️ [Include this note only when the mode is Interview-only:] This
> run is operating below the strongly recommended code-access posture
> for Phase 4. Every Step 02 baseline claim is [QUESTION]-flagged by
> default with a Phase 5 verification task attached, and the Step 12
> gate will weigh the degraded evidence basis in the Maintainability
> and Correctness Verification gates.

---

## §1 — Direct Code Access

| Capability | Available? | Repository / Path | Notes |
|-----------|-----------|------------------|-------|
| Filesystem read | [Yes/No] | | |
| Filesystem write | [Yes/No] | | |
| Git operations | [Yes/No] | | |
| Cross-repo access | [Yes/No] | | |

## §2 — Library and Specification Documentation Lookup

| Capability | Available? | Anticipated Use in Phase 4 |
|-----------|-----------|---------------------------|
| Context7 | [Yes/No] | [e.g., Step 11 spec languages: OpenAPI / JSON Schema / protobuf / AsyncAPI / TypeScript reference] |
| Project knowledge with library docs | [Yes/No] | |
| Web fetch | [Yes/No] | |

## §3 — Cross-Repo Search and Code Cross-Reference

*Rows are optional for single-repo / solo sessions — mark "None
applicable" rather than filling inapplicable cells. Record a
**Reliability** note (usable-on-demand / needs-warm-up / intermittent)
for any tool listed as available.*

| Capability | Available? | Reliability | Use Case |
|-----------|-----------|-------------|----------|
| GitHub code search | [Yes/No] | [on-demand/warm-up/intermittent] | |
| Enterprise / codebase search | [Yes/No] | | |
| Cross-repo reference tracking | [Yes/No] | | |

## §4 — Diagram and Visualization Rendering

| Capability | Available? | Notes |
|-----------|-----------|-------|
| Mermaid in rendered output | [Yes/No] | [module maps / trust-boundary diagrams / data flows] |
| External diagramming source | [Yes/No] | |
| Visualization MCP | [Yes/No] | |

## §5 — Skills, Custom AIs, Specialized Agents

| Capability | Active? | Description |
|-----------|---------|-------------|
| AI-Centric Playbook Skill | [Yes/No] | |
| Project-level instructions | [Yes/No] | |
| Specialized agents | [Yes/No] | |
| Other Skills loaded | [Yes/No] | |

## §6 — Phase 3 / Phase 2 / Phase 1 Artifact Access

| Artifact | Loaded? | Access Path |
|---------|--------|-------------|
| Phase 3 Design Specification Bundle | [Yes/No] | |
| Phase 3 per-brief Design Specification Artifacts | [Yes/No] | |
| Phase 2 Improvement Plan | [Yes/No] | |
| Phase 1 Current-State Information Report | [Yes/No] | |

## §7 — Mid-Phase Amendments

*Append-only. When a capability shifts during the Phase 4 run, add a
dated entry below. Do not edit prior entries.*

| Date | Step | Capability | Change | Impact |
|------|------|-----------|--------|--------|
| | | | | |

*Example entry (illustrating the "worked earlier, failed later"
pattern inherited from Phase 3 v1.1):*

| [date] | Step 09 (module batch) | GitHub code search | Worked at Steps 02–08; returned authorization errors mid-Step-09 | Remaining module change specifications cite pre-change interfaces from direct file reads only; affected citations flagged [AWARE]; §8 friction entry updated; code-access mode unchanged (Hybrid) |

## §8 — Known Friction Points

| Capability | Friction | Workaround |
|-----------|---------|-----------|
| | | |

## §9 — Code-Access Mode Rationale

[1–3 sentences explaining the mode selection, what it implies for the
Step 02 baseline and Step 09 pre-change citation confidence, and what
would trigger a mode change during the run. If the mode is
Interview-only, state prominently that the run is below the
recommended posture and name the Step 12 gate consequences.]

---

## Version

v1.0 (initial Phase 4 capability inventory; living thereafter)
```

---

## Evaluation Checklist

Before this artifact is accepted as complete, verify:

- [ ] All nine sections (§1–§9) are populated; sections with no
      relevant capabilities are marked "None applicable" rather than
      omitted
- [ ] Code-access mode is selected and announced in the metadata; an
      Interview-only selection is prominently flagged in the metadata
      and §9, with the Step 12 gate consequences named
- [ ] Phase 3 / Phase 2 / Phase 1 artifact access (§6) is explicit
      (which artifacts are loaded, which are accessible-on-demand,
      which would require paste)
- [ ] Every capability listed as available in §3 carries a
      reliability posture (usable-on-demand / needs-warm-up /
      intermittent)
- [ ] §7 starts empty (or with prior amendments from a previous
      Phase 4 session if resuming) — amendments are added during the
      run, not pre-populated
- [ ] Known friction points (§8) are captured for any capability
      flagged as flaky/rate-limited/expensive, including any
      "worked earlier, failed later" history
- [ ] The document is version-stamped v1.0 (or higher if resuming a
      previous Phase 4 session)
- [ ] No architecture or design content has been produced — no
      baseline claims, boundary decisions, or module specifications,
      and no implementation content (no function bodies, migration
      scripts, CI configuration, or credential material); Step 00 is
      capability inventory only
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)

---

*Part of the Phase 4 (Existing Projects) Architecture & Modular Design Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `architecture-modular-design.existing-project.instructions.md`*
*Next step: `step-01-phase-3-input-validation.prompt.md`*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Phase 4 Building Block Discovery prompt, structured as the Phase 4 sibling of the Phase 3 existing-track step-00: the same nine-section Toolset Augmentation Document, living-document §7 amendment discipline, and code-access mode selection. The Phase 3 v1.1 refinements are baked in as v1.0 content here and attributed as inherited (tool present-vs-consistently-usable reliability posture with on-demand/warm-up/intermittent recording; the project-knowledge-vs-library-lookup different-gaps distinction; §3 rows optional for single-repo/solo sessions). Phase 4 flavoring: the code-access sharpening from the instructions file (Step 02 baseline and Step 09 pre-change interface citations materially degraded without code access; Search-primary or better strongly recommended; Interview-only prominently flagged with named Step 12 gate consequences in the Maintainability and Correctness Verification gates); library-docs lookup oriented to the Step 11 contract specification languages (OpenAPI, JSON Schema, protobuf, AsyncAPI, TypeScript language reference); diagram rendering oriented to module maps, trust-boundary diagrams, and data flows; §6 widened to Phase 3 / Phase 2 / Phase 1 artifact access (Bundle, per-brief Design Specification Artifacts, Improvement Plan, Current-State Information Report). No architecture work happens at Step 00 — the baseline starts at Step 02, the frameworks at Step 03. |
