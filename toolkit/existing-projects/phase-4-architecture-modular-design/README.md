# Phase 4 — Architecture & Modular Design Tool Set (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Purpose

This tool set supports **Phase 4: Architecture & Modular Design** when
applied to an **existing codebase** that has completed Phases 1
(Information Gathering), 2 (Analysis & Improvement Planning), and 3
(Design & Technical Analysis).

Phase 4's job here is **transforming the locked Phase 3 design
specifications into an implementation-ready architectural blueprint,
integrated into the architecture the system already has.** Phase 3
specified the chosen mechanisms (contracts, refactors, information
architectures, schemas, observability touchpoints, verification
instruments) at design level. Phase 4 baselines the as-is architecture,
maps every design specification onto the module set, specifies each
affected module's change to implementation-readiness depth, formalizes
the interface contracts machine-readably, and hands Phase 5 a blueprint
it can build from without re-litigating decisions.

This is the existing-projects variant of Phase 4. The greenfield variant
(`toolkit/new-projects/phase-04-architecture-modular-design/`) draws
module boundaries from a blank slate and invents the cross-cutting
frameworks. The existing-projects variant is different — the system
already has modules, patterns, security posture, data reality, docs, and
de facto ownership. This toolkit **codifies that reality first** (with
provenance tags), then specifies precisely what changes within it, at a
depth that follows each module's disposition (NEW / CHANGED / UNTOUCHED /
RETIRED).

> **Companion Skill.** This toolkit has a companion **AI-Centric
> Playbook Skill** at `skills/ai-centric-playbook/` (SKILL.md + reference
> files on the Six Core Principles, the SDD cycle, and the
> building-blocks framework). Load it when a decision benefits from that
> depth — the instructions file explains when.

---

## When to Use This Tool Set

Use this tool set when:

- The subject is an existing codebase, not a greenfield project
- Phase 3 (Design & Technical Analysis) is complete with a Design
  Specification Bundle whose self-evaluation scorecard is at PASS or
  CONDITIONAL (not FAIL)
- Any Phase 3 → Phase 2 amendment cycle (Phase 3 Channel 2) is resolved
  — Phase 4 cannot responsibly begin while a Phase 2 amendment is open
- The team is ready to commit module boundaries, module change
  specifications, and formal interface contracts that Phase 5 will
  implement against

Do *not* use this tool set when:

- The project is greenfield — use the greenfield Phase 4 toolkit
- Phase 3 has not produced a Design Specification Bundle — run Phase 3
  first
- The Phase 3 bundle carries an unresolved Phase 2 Amendment Package —
  resolve the amendment cycle first
- The intent is to re-design the Phase 3 specifications — Phase 4
  architects against them; re-design routes through the amendment
  channels

---

## Tool Set Files

| File | Type | Purpose |
|------|------|---------|
| `architecture-modular-design.existing-project.instructions.md` | Load-once context | Three shifts from the greenfield variant; the nested SDD cycle; six principles applied; scorecard inheritance; three feedback channels; ID series; behavioral rules; output standards; dependency graph; common pitfalls. The structural document — every step prompt references back to it. |
| `step-00-building-block-discovery.prompt.md` | Action prompt (with brief confirmation) | Capability inventory for the Phase 4 run — living document (§7 amendments). Phase 4 sharpening: code access matters more here than in any prior phase. |
| `step-01-phase-3-input-validation.prompt.md` | Interview → Action | Validates the Phase 3 Design Specification Bundle (and the Phase 2/Phase 1 context behind it); produces the Validation Gap Register with the two-scope split (Channel 1). |
| `step-02-architecture-baseline-and-integration-scoping.prompt.md` | Action prompt (with clarification) | The as-is module inventory (preliminary M-NN), change surface map, contract-protocol inventory (which Step 11 sub-templates run), framework depth calibration, and the run's minimum viable path. |
| `step-03-shared-patterns-and-standards.prompt.md` | Action prompt (with clarification) | SP-NN patterns — existing practice codified, extensions tagged. Every element carries [EXISTING-CODIFIED] / [EXTENDED] / [NEW]. |
| `step-04-security-architecture-framework.prompt.md` | Action prompt (with clarification) | SEC-NN controls + TB-NN trust boundaries for the change surface, grounded in the Phase 1 risk/constraint/technical-debt inventory. |
| `step-05-data-architecture-framework.prompt.md` | Action prompt (with clarification) | DA-NN constraints — classification, ownership, integrity, migration posture; integrates Phase 3 schema-type specifications with the existing data reality. |
| `step-06-documentation-strategy.prompt.md` | Action prompt (with clarification) | DOC-NN types and standards with a maintenance plan — reconciled with existing docs and the Phase 3 IA specification when one exists. |
| `step-07-governance-model.prompt.md` | Action prompt (with clarification) | GOV-NN ownership, review gates, decision authority — de facto ownership codified, gaps closed; explicit regardless of team size. |
| `step-08-module-impact-map.prompt.md` | Action prompt (with clarification) | The Stage 2 gateway: M-NN manifest with dispositions, brief-to-module mapping with coverage check, boundary decisions with rejected alternatives, SIC-NN strategic interface contracts, per-module constraint assignments. |
| `step-09-module-change-specification.prompt.md` | Parameterized action prompt (runs once per NEW/CHANGED module) | The core blueprint: one implementation-ready module change specification per affected module — eight required sections at disposition-appropriate depth, plus invalidation checks and the per-artifact scorecard contribution. |
| `step-10-cross-module-consistency.prompt.md` | Evaluation prompt (module-set validation — not the gate) | Validates conformance (Step 09 interfaces vs SIC-NN), coverage (every brief lands; no gaps or overlaps), and citations (assigned constraints honored). Determination: CONSISTENT / INCONSISTENCIES FOUND. |
| `step-11-formal-interface-contracts.prompt.md` | Parameterized conditional action prompt (runs once per protocol) | Machine-readable contracts derived from Step 09 detailed interfaces — six protocol sub-templates (language-level interface / REST-OpenAPI / gRPC-protobuf / event schema / data-artifact schema / other-declared). |
| `step-12-architecture-synthesis-and-readiness-review.prompt.md` | Action + Evaluation (synthesis + the gate) | The Architecture Blueprint Bundle, the scorecard refresh (inherited weights, Phase 3 baseline, target distribution check), the five-outcome readiness determination, and the Phase 3 / Phase 2 Amendment Packages when channels fire. |
| `dogfooding-observations.md` | Living log | Captured during Phase 4 cycles for end-of-phase review. |

---

## Recommended Sequence

```
┌────────────────────────────────────────────────────────────────────┐
│ Phase 3 Design Specification Bundle (scorecard at PASS or          │
│ CONDITIONAL; any Phase 2 amendment cycle resolved)                 │
│ + Phase 2 Improvement Plan + Phase 1 Current-State Report          │
└────────────────────────────────────────────────────────────────────┘
                              │
                              ▼
              ═══ STAGE 1: BASELINE & FRAMEWORKS ═══
                              │
                              ▼
                  ┌───────────────────────┐
                  │ Step 00: Building     │
                  │ Block Discovery       │──→ Toolset Augmentation
                  └───────────┬───────────┘    Document (living)
                              ▼
                  ┌───────────────────────┐
                  │ Step 01: Phase 3      │──→ Validation Gap Register
                  │ Input Validation      │    (two-scope split)
                  └───────────┬───────────┘
                  ┌───────────┴────────────────────┐
                  ▼                                ▼
        ┌─────────────────────┐    ┌───────────────────────────┐
        │ Phase 4 local gaps  │    │ Upstream toolkit gaps →   │
        │ → continue Phase 4  │    │ queue for Phase 3 (or 2/1)│
        │                     │    │ toolkit revision session  │
        └─────────────────────┘    │ (Channel 1 firing)        │
                              │    └───────────────────────────┘
                              ▼
                  ┌───────────────────────┐
                  │ Step 02: Architecture │──→ Baseline & Scoping
                  │ Baseline & Integration│    Document (as-is M-NN,
                  │ Scoping               │    change surface, protocol
                  └───────────┬───────────┘    inventory, depth, MVP)
                              ▼
                  ┌───────────────────────┐
                  │ Step 03: Shared       │──→ SP-NN register
                  │ Patterns & Standards  │    (provenance-tagged)
                  └───────────┬───────────┘
          ┌──────────────┬────┴─────────┬──────────────┐
          ▼              ▼              ▼              ▼
     ┌─────────┐   ┌─────────┐   ┌───────────┐  ┌──────────┐
     │ Step 04 │   │ Step 05 │   │ Step 06   │  │ Step 07  │
     │ Security│   │ Data    │   │ Docs      │  │ Govern-  │
     │ SEC/TB  │   │ DA-NN   │   │ DOC-NN    │  │ ance GOV │
     └────┬────┘   └────┬────┘   └─────┬─────┘  └────┬─────┘
          └──────────────┴───────┬─────┴─────────────┘
                (parallel-eligible sub-stage 1b)
                              ▼
                    ═══ STAGE 2: MODULES ═══
                              │
                              ▼
                  ┌───────────────────────┐
                  │ Step 08: Module       │──→ M-NN manifest with
                  │ Impact Map            │    dispositions + SIC-NN
                  └───────────┬───────────┘    + constraint assignments
                              ▼
                  ┌───────────────────────┐
                  │ Step 09: Module Change│ ◄── (one run per NEW/CHANGED
                  │ Specification (×N)    │      module; independent
                  └───────────┬───────────┘      modules in parallel)
                              ▼
                  ┌───────────────────────┐
                  │ Step 10: Cross-Module │──→ CONSISTENT /
                  │ Consistency           │    INCONSISTENCIES FOUND
                  └───────────┬───────────┘
                              ▼
               ═══ STAGE 3: CONTRACTS & HANDOFF ═══
                              │
                              ▼
                  ┌───────────────────────┐
                  │ Step 11: Formal       │ ◄── (conditional; one run
                  │ Interface Contracts   │      per protocol from the
                  └───────────┬───────────┘      Step 02 inventory)
                              ▼
                  ┌───────────────────────┐
                  │ Step 12: Architecture │──→ Blueprint Bundle +
                  │ Synthesis & Readiness │    scorecard refresh +
                  │ Review (the gate)     │    five-outcome gate
                  └───────────┬───────────┘
       ┌──────────┬───────────┼──────────────────────┐
       ▼          ▼           ▼                      ▼
 ┌──────────┐ ┌─────────┐ ┌──────────────┐ ┌─────────────────┐
 │ READY /  │ │NOT READY│ │ NOT READY —  │ │ NOT READY —     │
 │ CONDITION│ │(Phase 4 │ │ Phase 3      │ │ Phase 2         │
 │ -ALLY    │ │ gaps) → │ │ amendment    │ │ amendment       │
 │ READY →  │ │remediate│ │ (Channel 2) →│ │ (Channel 3) →   │
 │ Phase 5  │ │+ re-gate│ │ Phase 3 cycle│ │ cascades through│
 │ begins   │ │         │ │ + re-entry   │ │ Phase 3 + 4     │
 └──────────┘ └─────────┘ └──────────────┘ └─────────────────┘
```

The diagram shows all **three Phase 4 feedback channels**:

- **Channel 1** (upstream toolkit gaps from Step 01) — fires when an
  upstream toolkit was structurally incomplete; queues for that
  toolkit's revision; does *not* block this Phase 4 cycle
- **Channel 2** (Phase 3 run amendment from Step 12) — fires when
  architecture work surfaces that a specific Phase 3 design
  specification is untenable; *blocks* Phase 5 handoff until resolved
- **Channel 3** (Phase 2 run amendment from Step 12) — fires when
  architecture-level evidence invalidates a Phase 2 commitment
  (mechanism or cost envelope); *blocks*, and cascades through a Phase 3
  re-entry before Phase 4 resumes

---

## The Minimum Viable Path

- **Mandatory (every run):** Steps 00–10 and Step 12 — twelve steps.
  The toolkit has no "lightweight" mode; what scales for simple change
  surfaces is the *depth* of each artifact (calibrated at Step 02 §4),
  not the number of steps.
- **Conditional:** Step 11 runs once per protocol in the Step 02
  contract-protocol inventory. A library's public interface counts as a
  formalizable protocol (the language-level sub-template); a run that
  formalizes nothing must justify the exemption in Step 02 §3 and carry
  it into the Step 12 gate.
- **Parameterized:** Step 09 runs once per NEW/CHANGED module — N comes
  from the Step 08 manifest. UNTOUCHED modules get manifest rows only.

A single-module, single-protocol change surface runs twelve mandatory
steps + one Step 09 execution + one Step 11 execution.

---

## MCP Server Recommendations

Phase 4 work depends on code reality more than any prior phase. The
capabilities that matter most:

- **Direct code access** (filesystem MCP, Claude Code, GitHub MCP with
  filesystem features) — the Step 02 baseline and the Step 09
  pre-change interface citations are materially degraded without it.
  Search-primary or better is strongly recommended for this phase.
- **Library documentation lookup** (Context7 or equivalent) — Step 11
  contract formalization cites current spec content (OpenAPI, JSON
  Schema, protobuf, AsyncAPI, language references) rather than
  paraphrasing from memory.
- **Cross-repo search** — for multi-repo projects where integration
  peers' boundaries appear in the baseline and the Impact Map.
- **Diagram rendering** (Mermaid or equivalent) — module maps, trust
  boundary diagrams, and data-flow renderings benefit from visual form;
  ASCII fallbacks are acceptable.

### Capabilities Can Shift Mid-Phase

*Inherited from Phase 2 v1.1 / Phase 3 v1.1.* When capability
availability changes during the run, **amend the Step 00 Toolset
Augmentation Document with a dated §7 entry — do not produce a new
document, and do not silently work around the change.** Record each
tool's reliability posture (usable-on-demand / needs-warm-up /
intermittent), not just its presence. If the code-access mode shifts
mid-phase, flag the artifacts produced before the shift so the Step 12
bundle's evidence basis is consistent.

---

## Dogfooding & Calibration Guidance

This toolkit is at v1.0. Every Phase 4 run on a real project is a
dogfooding cycle that produces observations for v1.x+ revisions.

### Observation Capture Protocol

During the run, capture observations in `dogfooding-observations.md`
(IDs `P4-Obs-NN`) whenever:

- A prompt's structure forced a workaround or lacked a slot for
  something the work surfaced
- A behavioral rule produced unexpected resistance or unexpectedly
  smooth flow
- The disposition taxonomy (NEW/CHANGED/UNTOUCHED/RETIRED) or a
  provenance tag ([EXISTING-CODIFIED]/[EXTENDED]/[NEW]) felt over- or
  under-fitted
- A Step 11 protocol sub-template felt over- or under-fitted to a
  boundary
- A cross-step handoff lost or duplicated information
- An upstream inheritance pattern (weights, cost model, currency rule)
  felt miscalibrated

Capture is **fast and incomplete by design** — full analysis happens at
the end-of-phase three-pass review (cluster → decide → revise),
inherited from Phase 1 v1.3 / Phase 2 v1.1 / Phase 3 v1.1.

### The Feedback Channels Are Features

Step 01's upstream-scope gaps and Step 12's amendment packages are not
bug reports — they are the toolkit's normal mechanism for surfacing
inter-phase improvements. The first Phase 4 dogfood is expected to
surface some upstream Phase 3 toolkit gaps (Phase 3 didn't have to
anticipate every Phase 4 question), at most 0–1 run-amendment
invalidations, and calibration observations on the disposition and
provenance disciplines — the v1.0-original concepts that have not yet
been dogfooded.

---

## Common Pitfalls

*These are pitfalls specific to running this toolkit. The instructions
file has the comprehensive list applied to Phase 4 work in general.*

**Skipping the baseline because "we know our own code."** Step 02 is
what makes the existing architecture *citable* — M-NN IDs, evidenced
boundaries, a change surface the whole phase hangs off. Familiarity is
not citability.

**Running Step 09 for every module in the manifest.** Depth follows
disposition. UNTOUCHED modules get manifest rows. Specifying them fully
burns the capacity envelope on work with no Phase 5 consumer.

**Running Step 09 with multiple modules in one session
unconditionally.** The default is one module per session — each change
specification deserves a fresh session anchored in its own inputs.
Parallel sessions for independent modules are the recommended
acceleration, per the Step 08 dependency notes.

**Treating Step 12 as synthesis-by-smoothing.** Step 12 is synthesis +
gate. Net-new boundary decisions, contracts, or constraints at synthesis
time mean something was missed upstream — pause and fix it there.

**Conflating the two invalidation levels.** "This design spec cannot
land as modules" is Channel 2 (Phase 3 amendment). "No design could land
this mechanism / the costs exceed the envelope" is Channel 3 (Phase 2
amendment, cascading). Diagnose the level before firing.

**Formalizing nothing because the project "has no APIs."** A library's
public interface, a CLI's command surface, an emitted artifact's schema
— all are formalizable contracts. Step 11's language-level and
data-artifact sub-templates exist precisely for projects without
REST/gRPC surfaces.

**Letting provenance tags decay into decoration.** [EXISTING-CODIFIED]
vs [NEW] is load-bearing: it separates what Phase 5 must *conform to*
from what Phase 5 must *build*. An untagged framework element is
unusable downstream.

---

## What's Available, What's Not

### Available in v1.0

- All thirteen step prompts with output formats and evaluation
  checklists
- Instructions file with the three shifts, three feedback channels,
  ID-series table, scorecard inheritance, behavioral rules, dependency
  graph, and output standards
- This README
- `dogfooding-observations.md` template (empty, ready for the first
  Phase 4 cycle)

### Not Yet Available (Queued for v1.1+ Based on Dogfooding)

- **Worked examples per step** — a Diamonds-derived worked example for
  the Impact Map and one module change specification would make the
  toolkit more illustrative; deferred to keep v1.0 lean
- **Additional Step 11 sub-templates** — if dogfoods produce recurring
  "other-declared" protocols, they graduate to named sub-templates
- **Disposition-taxonomy refinements** — SPLIT/MERGED dispositions (a
  module divided or two combined) are currently expressed as
  RETIRED+NEW pairs; if dogfooding shows that loses information, v1.1
  adds first-class dispositions
- **Greenfield ↔ existing cross-walk** — a mapping table for
  practitioners moving between the two Phase 4 variants

---

## Version History

| Version | Date | Source | Summary |
|---------|------|--------|---------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Phase 4 existing-projects toolkit. Sixteen files (instructions + 13 step prompts + README + dogfooding template). Three-stage structure (baseline & frameworks / modules / contracts & handoff) with sub-stage 1b and per-module and per-protocol parallelism. Module dispositions (NEW/CHANGED/UNTOUCHED/RETIRED) and framework provenance tags ([EXISTING-CODIFIED]/[EXTENDED]/[NEW]) as the v1.0-original disciplines. Three feedback channels (upstream toolkit gaps; Phase 3 run amendment; Phase 2 run amendment). Five-outcome readiness gate at Step 12 combining the track's synthesis+self-evaluation pattern with the greenfield Phase 4 gate. Step 11 unifies the greenfield variant's four API-contract prompts into one parameterized prompt with six protocol sub-templates (adding language-level interfaces and data-artifact schemas for library-shaped projects). Scorecard inheritance, two-scope validation split, three-quantity cost model, code-access calibration (with Phase 4 sharpening), multi-repo scoping, currency rules, and dogfooding protocol inherited from Phase 1 v1.3 / Phase 2 v1.1 / Phase 3 v1.1. |

---

*Part of the Phase 4 (Existing Projects) Architecture & Modular Design Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `architecture-modular-design.existing-project.instructions.md`*
