# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repository Is

This is a **content and methodology repository**, not a software project. It contains the **AI-Centric Software Development Playbook** — a published article series plus a companion library of AI prompts, instruction files, and skills that operationalize the methodology.

There is **no build, test, lint, or run step**. Everything is Markdown (plus exported HTML and images). "Development" here means authoring and revising articles and toolkit prompt files while keeping the framework's terminology and structure internally consistent. Validation is editorial and structural (cross-references resolve, terminology matches, version tables updated), not automated.

Git uses Conventional Commits with topic prefixes seen in history: `docs:`, `feat:`, `fix:`, `toolkit:`, `skills:`, `media:`, `rename:`.

## The Framework (must stay internally consistent across all files)

Every article and prompt is *about* — and must conform to — these shared concepts. Changing terminology in one place means changing it everywhere it appears.

- **Six Core Principles**, evaluated *concurrently* at every phase (never a sequential checklist): Security, Maintainability, Economics, Operations, Scoring & Metrics, Correctness Verification. Principles 1–4 are *what you optimize for*; 5–6 are *how you know you're getting it right*.
- **SDD — Specification Driven Development**: the iterative cycle `Specify → Plan → Detail → Task → Implement`. It is the engine of the framework; the cycle is constant, the tool sets change per phase.
- **Building blocks → Tool sets**: six building-block types (Consolidated Knowledge Base, Prompts, Skills, Instruction Sets, MCP Servers, Custom AIs) are curated into *tool sets* for a specific purpose. Prompts come in three flavors: interview, action, evaluation.
- **Seven phases** (concurrent streams with checkpoints, not waterfall): 1 Information Gathering · 2 Analysis & Stack Selection · 3 Design & Technical Analysis · 4 Architecture & Modular Design · 5 Implementation · 6 Testing & Audit · 7 Deployment & Evolution.

The canonical source for the framework is `00-series-outline.md` and `skills/ai-centric-playbook/`. When in doubt about a definition, defer to those.

## Repository Layout

- **`docs/part-NN-*.md`** — the article series (the prose). Part 0 Manifesto, Part 1 Core Principles, Part 2 Building Your Toolkit, then Parts 3–9 cover the phases. **Article numbering is offset from phase numbering: Part N = Phase N−2** (Part 3 = Phase 1 … Part 9 = Phase 7). `docs/html/` holds exported HTML renderings of these.
- **`docs/building-new-project-toolkit/` and `docs/building-existing-project-toolkit/`** — meta-articles documenting *how the toolkit prompts themselves were built*, phase by phase. These describe the authoring process, distinct from the toolkit they produce.
- **`toolkit/new-projects/` and `toolkit/existing-projects/`** — the actual tool sets, one directory per phase. This is the most-edited part of the repo. Two parallel tracks: greenfield ("new") and brownfield ("existing").
- **`skills/ai-centric-playbook/`** — a Claude skill encoding framework-level reasoning. `SKILL.md` is the entry point; it lazy-loads `core-principles.md`, `sdd-cycle.md`, `building-blocks-and-toolsets.md` on demand. Keep the skill in sync when the framework definitions change.
- **`project/{new,existing}-projects/dogfooding-*/phase-N/dogfooding-observations.md`** — observation logs from applying the toolkit to a real project (see Dogfooding below).
- **`00-series-outline.md`** — master outline: audience, thesis, full principle/SDD/phase definitions. **`README.md`** — public landing page.
- **`images/`** — article media. `mkdir/` is an empty stray directory; ignore it.

## Toolkit File Conventions

Each `toolkit/<track>/phase-NN-*/` directory is a self-contained tool set and follows a consistent structure:

- **`README.md`** — overview, framework context, directory contents, per-file descriptions, usage sequence, the **self-evaluation scorecard / phase gate** (PASS / CONDITIONAL / FAIL, or the 5-outcome variant in Phase 4), an **artifact dependency map**, common pitfalls, the connection to the next phase, and a **Version History** table.
- **`*.instructions.md`** — the persistent project-context file. It is loaded once into the AI environment and is active across every prompt session in that phase. Carries the framework orientation, SDD cycle, the six principles applied to the phase, behavioral guidelines, output standards, and the dependency graph.
- **`step-NN-*.prompt.md`** — one prompt per artifact, run in its own AI session. Internal structure to preserve when editing or adding prompts:
  - A **Prompt Metadata** table (Step N of M, Type, Phase, SDD Step, Artifact Produced, Principles Addressed, Requires As Input, Feeds Into, Companion File).
  - **How to Use This Prompt**, a **What This Step Is — and Is Not** section (explicit produces / does-NOT-produce lists), the System Instructions, a **Kickoff** line, and an **evaluation checklist** the output is reviewed against.

**Cross-prompt coherence via ID series.** Later phases rely on ID citation discipline (e.g. Phase 4's `SP-NN` patterns, `SEC-NN` controls, `M-NN` modules, `SIC-NN` contracts; Phase 3 hooks as `H-NN`; Phase 2 threats as `T-NN`). One step *establishes* an ID series, downstream steps *cite* it, and consistency/review/gate steps *verify* the citations. When editing a prompt, preserve these IDs and their cross-references — an un-ID'd pattern cannot be cited or verified.

### Naming differs between the two tracks (don't "normalize" without intent)

- `toolkit/new-projects/` uses zero-padded, suffixed dirs: `phase-01-information-gathering-toolset`, `phase-02-analysis-stack-selection`, … and `step-NN-*.prompt.md`.
- `toolkit/existing-projects/` uses unpadded, differently-suffixed dirs: `phase-1-information-gathering`, `phase-2-design-analysis`, `phase-3-technical-analysis`, with `step-00-*` building-block-discovery steps and an `*.existing-project.instructions.md` naming variant.

Match the conventions of the directory you are editing. A README's "Directory Contents" block may still show an older directory name — verify against the real path before relying on it.

## The Dogfooding Feedback Loop (how the toolkit evolves)

Tool sets are **living artifacts** refined by application, not designed once. The loop:

1. Apply a phase's toolkit to a real testbed project (the recurring one is **"Diamonds"** / `@diamondslab/diamonds`).
2. Capture issues as numbered observations (`P<phase>-Obs-NN`) in that phase's `dogfooding-observations.md` — recorded during the run but **acted on only at end-of-phase review** (Option B protocol).
3. Cluster observations and land a versioned toolkit revision; bump the README **Version History** table (semver, e.g. v1.0 → v1.1). Commit messages reference the dogfood run (e.g. "update to … v1.1 after dogfooding").

An observation surfaced in one phase may be routed to a *different* phase's revision queue or carried forward as a handoff item — note the routing explicitly, as the existing observation files do.

## When Editing Here

- Keep the framework vocabulary exact (principle names, SDD step names, phase names/numbers). These are the load-bearing terms across dozens of files.
- A change to a definition in `00-series-outline.md` or the skill usually implies coordinated edits in the relevant `docs/part-*` article, the affected `toolkit/*/README.md` and prompt files, and possibly the building-* meta-articles.
- When revising a toolkit prompt, also check: its phase README's dependency map and file description, any ID series it establishes or cites, the phase gate criteria, and the Version History table.
