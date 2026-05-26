# Phase 3 — Design & Technical Analysis Tool Set (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-05-25)

---

## Purpose

This tool set supports **Phase 3: Design & Technical Analysis** when
applied to an **existing codebase** that has completed Phases 1
(Information Gathering) and 2 (Analysis & Improvement Planning).

Phase 3's job here is **producing concrete design specifications for
the chosen mechanisms** Phase 2 named in its Improvement Plan §6
(primary design briefs) and §10.1 (supplementary design briefs).
Phase 4 (Architecture) consumes the specifications and produces
module boundaries and internal structures. Phase 5 (Implementation)
builds against the specifications. Phase 6 (Testing & Audit)
executes the verification instruments Step 05 produces.

This is the existing-projects variant of Phase 3. The greenfield
variant (separate toolkit) frames Phase 3 as design *exploration*
across six locked dimensions, producing a Design Direction Document
plus an initial Principle Scorecard. The existing-projects variant
is different — the direction was settled long ago (the system
exists), and Phase 2 already chose specific mechanisms. Phase 3
here produces design specifications at the level Phase 5 can
implement against, while inheriting the Phase 2 scorecard frame and
contributing per-artifact contributions into it.

---

## When to Use This Tool Set

Use this tool set when:

- The subject is an existing codebase, not a greenfield project
- Phase 1 (Information Gathering) is complete with a Current-State
  Information Report
- Phase 2 (Analysis & Improvement Planning) is complete with an
  Improvement Plan, including §6 design briefs and any §10.1
  supplementary briefs
- The Phase 2 scorecard is at PASS or CONDITIONAL (not FAIL); FAIL
  triggers cycling back to Phase 2 before Phase 3 begins
- The team is ready to commit design-level specifications that
  Phase 4 architecture and Phase 5 implementation will land against

Do *not* use this tool set when:

- The project is greenfield — use the greenfield Phase 3 toolkit
- Phase 2 has not produced an Improvement Plan — start Phase 2
  first
- The Phase 2 §6 briefs are not yet named — return to Phase 2 Step
  06 synthesis
- Phase 2 mechanism choices have not been made for the briefs Phase
  3 will specify — return to Phase 2 Step 03 mechanism decisions

---

## Tool Set Files

| File | Type | Purpose | v1.0 Notes |
|------|------|---------|-----------|
| `design-technical-analysis.existing-project.instructions.md` | Load-once context | Three shifts from Phase 2; six artifact types; SDD cycle in Phase 3; six principles applied; principle scorecard inheritance pattern; two Phase 3 → Phase 2 feedback channels; behavioral rules; output standards; common pitfalls | The structural document. Every step prompt references back to it. |
| `step-00-building-block-discovery.prompt.md` | Action prompt (with brief confirmation) | Capability inventory for the Phase 3 run | Living document discipline (§7 amendments) inherited from Phase 2 v1.1 |
| `step-01-phase-2-input-validation.prompt.md` | Interview → Action | Validates Phase 2 inputs; produces Validation Gap Register with two-scope split | Phase 3 → Phase 2 Feedback Channel 1 (upstream toolkit gaps) operationalized here |
| `step-02-design-brief-triage.prompt.md` | Action prompt (with clarification) | Classifies briefs by artifact type; captures dependencies; sequences Step 03 work | Six artifact-type taxonomy (Contract / Refactor / IA / Schema / Observability / Verification) plus Other-with-declared-shape |
| `step-03-per-artifact-design-specification.prompt.md` | Action prompt (per brief) | Produces Design Specification Artifact per brief using artifact-type sub-template | The central design step. Unified prompt with seven sub-templates (six common types + Other). Per-artifact principle scorecard contribution + Phase 2 invalidation check + Phase 5 implementability check |
| `step-04-inter-artifact-coordination.prompt.md` | Action prompt (draft-and-react) | Cross-brief references, shared decisions, Phase 5 ordering, verification dependencies | Aggregates Step 03 §6 invalidations for Step 06; identifies coordinated-landing cohorts |
| `step-05-verification-strategy.prompt.md` | Action prompt (draft-and-react) | Concrete Phase 6-executable verification instruments | Refines per-MC verification methods from Phase 2 into instrument-level content. Central discipline: instruments not descriptions |
| `step-06-design-specification-synthesis.prompt.md` | Action prompt (synthesis only) | Design Specification Bundle + scorecard refresh + Phase 2 Amendment Package when applicable | Phase 3 → Phase 4 handoff. Target distribution check inherited from Phase 2 v1.1 |
| `dogfooding-observations.md` | Living log | Captured during Phase 3 cycles for end-of-phase review | Template at v1.0; populated during each Phase 3 run |

---

## Recommended Sequence

```
┌──────────────────────────────────────────────────────────────────┐
│ Phase 2 Improvement Plan (with §6 design briefs, §10.1           │
│ supplementary briefs, Phase 2 scorecard at PASS or CONDITIONAL)  │
└──────────────────────────────────────────────────────────────────┘
                              │
                              ▼
                  ┌───────────────────────┐
                  │ Step 00: Building     │
                  │ Block Discovery       │
                  │                       │
                  │ → Toolset Augmentation│
                  │   Document (living)   │
                  └───────────────────────┘
                              │
                              ▼
                  ┌───────────────────────┐
                  │ Step 01: Phase 2 Input│
                  │ Validation            │
                  │                       │
                  │ → Validation Gap      │
                  │   Register (two-scope │
                  │   split)              │
                  └───────────┬───────────┘
                              │
                  ┌───────────┴───────────────────┐
                  ▼                               ▼
        ┌─────────────────────┐    ┌──────────────────────────┐
        │ Phase 3 local gaps  │    │ Upstream Phase 2 toolkit │
        │ → continue Phase 3  │    │ gaps → queue for Phase 2 │
        │                     │    │ toolkit revision in      │
        │                     │    │ separate session         │
        │                     │    │ (Channel 1 firing)       │
        └─────────────────────┘    └──────────────────────────┘
                              │
                              ▼
                  ┌───────────────────────┐
                  │ Step 02: Design Brief │
                  │ Triage                │
                  │                       │
                  │ → Design Brief        │
                  │   Register (typed,    │
                  │   sequenced)          │
                  └───────────┬───────────┘
                              │
                  ┌───────────┴───────────────────┐
                  ▼                               ▼
        ┌─────────────────────┐    ┌──────────────────────────┐
        │ Strict-order briefs │    │ Parallel-eligible briefs │
        │ (serial Step 03)    │    │ (parallel Step 03        │
        │                     │    │ sessions if capacity)    │
        └──────────┬──────────┘    └────────────┬─────────────┘
                   │                            │
                   └────────────┬───────────────┘
                                ▼
                  ┌───────────────────────┐
                  │ Step 03: Per-Artifact │
                  │ Design Specification  │  ◄── (one iteration per
                  │                       │       brief, using the
                  │ → Design Specification│       artifact-type
                  │   Artifact per brief  │       sub-template;
                  │                       │       per-artifact
                  │                       │       principle scorecard
                  │                       │       + Phase 2 invalid-
                  │                       │       ation check + Phase
                  │                       │       5 implementability
                  │                       │       check)
                  └───────────┬───────────┘
                              │
                              ▼
                  ┌───────────────────────┐
                  │ Step 04: Inter-       │
                  │ Artifact Coordination │
                  │                       │
                  │ → Coordination        │
                  │   Register (cross-    │
                  │   refs, shared        │
                  │   decisions, Phase 5  │
                  │   ordering,           │
                  │   verification deps)  │
                  └───────────┬───────────┘
                              │
                              ▼
                  ┌───────────────────────┐
                  │ Step 05: Verification │
                  │ Strategy              │
                  │                       │
                  │ → Concrete Phase 6-   │
                  │   executable          │
                  │   instruments         │
                  │   (test cases,        │
                  │   question text,      │
                  │   prompts, harness)   │
                  └───────────┬───────────┘
                              │
                              ▼
                  ┌───────────────────────┐
                  │ Step 06: Design       │
                  │ Specification         │
                  │ Synthesis             │
                  │                       │
                  │ → Design Spec Bundle  │
                  │ → Scorecard refresh   │
                  │   (inheriting Phase 2 │
                  │    weights, ≤2 CONDs) │
                  │ → Phase 2 Amendment   │
                  │   Package (if any     │
                  │   Step 03 §6          │
                  │   invalidations)      │
                  └───────────┬───────────┘
                              │
                  ┌───────────┴───────────────────┐
                  ▼                               ▼
        ┌─────────────────────┐    ┌──────────────────────────┐
        │ No invalidations    │    │ Invalidations surfaced   │
        │ → Phase 4 begins    │    │ → Phase 2 amendment      │
        │   (Architecture &   │    │   cycle; Phase 3 re-     │
        │   Modular Design)   │    │   enters with amended    │
        │                     │    │   Plan (Channel 2        │
        │                     │    │   firing)                │
        └─────────────────────┘    └──────────────────────────┘
```

The diagram shows both **Phase 3 → Phase 2 feedback channels**:

- **Channel 1** (upstream toolkit gaps from Step 01 §11.2) — fires
  when the Phase 2 toolkit was structurally incomplete; queues for
  Phase 2 toolkit revision; does *not* block this Phase 3 cycle
- **Channel 2** (run amendment from Step 06 §7) — fires when Step
  03 design work surfaces that a specific Phase 2 mechanism choice
  is untenable; *blocks* Phase 4 handoff until amendment is resolved

---

## MCP Server Recommendations

Phase 3 work benefits from a different MCP-server posture than Phase
1 or Phase 2 did. Capabilities that matter most for design
specification work:

- **Library documentation lookup** (Context7 or equivalent) — many
  design briefs reference external specifications (CycloneDX, OpenAPI,
  JSON Schema, TypeScript Handbook, language references) where the
  design specification should cite current spec content rather than
  paraphrase from memory
- **Direct code access** (filesystem MCP, Claude Code, GitHub MCP
  with filesystem features) — refactor-type and contract-type briefs
  benefit most from reading current code, where the pre-refactor or
  pre-contract interface should be cited rather than reconstructed
- **Cross-repo search** — for multi-repo projects where integration
  peers' behavior is referenced in the design specification
- **Diagram rendering** (Mermaid in chat output, an external
  diagramming tool the AI can produce source for) — IA-type and
  schema-type briefs benefit from visual rendering of layer
  structures, schema shapes, and cross-link graphs

### Capabilities Can Shift Mid-Phase

*Inherited from Phase 2 v1.1.* MCP server availability can change
during a Phase 3 cycle — connectors activate, Skills get authored,
tools error out under specific conditions. When this happens,
**amend the Toolset Augmentation Document (Step 00) with a dated
entry in §7 — do not produce a new document, and do not silently
work around the change.**

Mid-phase capability shifts have implications for the design work
done before the shift. If Context7 was unavailable at Step 03 brief
1 but available at Step 03 brief 2, the brief-1 specification's
library-citation discipline differs from brief 2's. Surface this in
the Step 04 Coordination Register (under §3 Shared Decisions or §1
Cross-Artifact References) so the bundle's evidence basis is
consistent.

The Diamonds Phase 2 dogfooding observation P2-Obs-06 documented
this discipline. Phase 3 inherits it.

---

## Dogfooding & Calibration Guidance

This toolkit is at v1.0. Every Phase 3 run on a real project is a
dogfooding cycle that produces observations for v1.x+ revisions.

### Observation Capture Protocol

During the Phase 3 run, capture observations in
`dogfooding-observations.md` whenever:

- A prompt's structure forced a workaround or didn't have a slot for
  something the work surfaced
- A behavioral rule produced unexpected resistance or unexpectedly
  smooth flow
- An interview pattern (question-by-question vs draft-and-react) felt
  miscalibrated for the work
- An output format produced confusion or was unexpectedly easy to
  consume in the next step
- An artifact-type sub-template (Step 03's seven sub-templates) felt
  over-fitted or under-fitted to a specific brief
- A cross-step handoff (Step N → Step N+1) lost or duplicated
  information
- A Phase 2 → Phase 3 inheritance pattern (principle weights, cost
  model, capacity envelope) felt miscalibrated

The capture is **fast and incomplete by design** — full analysis
happens at end-of-phase. The goal during the run is to record the
observation while it's fresh, not to analyze or act on it.

### End-of-Phase Review Protocol

After Step 06 synthesis completes (and any Phase 2 amendment cycle
resolves), run the three-pass review:

1. **Cluster** — group observations that address the same gap or the
   same file
2. **Decide** per cluster — Accept / Accept with refinement / Defer /
   Reject; also route per cluster — Phase 3 v1.x revision / upstream
   to Phase 2 toolkit / upstream to Phase 1 toolkit
3. **Revise** — produce the v1.x files in a focused authoring session

The protocol is inherited from Phase 2 v1.1, which inherited from
Phase 1 v1.1. Continuity matters; the protocol has been validated
across two prior toolkits.

### Phase 3 → Phase 2 Feedback Channel Is a Feature

*Inherited framing from Phase 2 v1.1's "Phase 2 → Phase 1 feedback
channel is a feature" section.*

Step 01's §11.2 (Upstream Phase 2 Toolkit Gaps) and Step 06's §7
(Phase 2 Amendment Package) are not bug reports — they are the
toolkit's normal mechanism for surfacing inter-phase improvements.

When the Diamonds Phase 2 dogfood produced 3 upstream gaps that
fed Phase 1 v1.3, it was the framework working as designed. A
Phase 3 dogfood that produces 0 upstream gaps may be a sign that
Phase 2 is already mature, *or* a sign that Phase 3's Step 01 isn't
asking probing-enough validation questions. Both are worth noticing.

The expected pattern: each new phase's first dogfood surfaces some
upstream gaps. Subsequent dogfoods on different project profiles
surface different gaps. The toolkit family matures by surfacing and
fixing.

### What to Expect From the First Phase 3 Dogfood

The first Phase 3 dogfood (Diamonds, after Phase 3 toolkit v1.0
authoring) will probably produce:

- **Some upstream Phase 2 toolkit gaps via Channel 1** — Phase 2's
  toolkit didn't have to anticipate every Phase 3 question; expect
  3-5 observations
- **At most 0-1 run-amendment invalidations via Channel 2** — Phase
  2 mechanism choices for Diamonds were carefully considered and
  unlikely to be untenable, but the discipline of running the check
  per-brief means some invalidation is possible
- **Some artifact-type sub-template observations** — the six common
  types were authored from Diamonds' six design briefs, so Diamonds-
  specific fitness is high; future project profiles may surface
  sub-template gaps
- **Some calibration observations** — the inherited Phase 2 cost
  model (three-quantity with BELIEVED multipliers) will produce
  Phase 5 estimate refinements during Step 03; the refinements feed
  Phase 7 multiplier calibration

The toolkit's v1.1 revision will land what the Diamonds dogfood
produced. v1.2 and later will accumulate from subsequent dogfoods
on different project profiles.

---

## Common Pitfalls

*These are pitfalls specific to running this Phase 3 toolkit. The
companion instructions file has a more comprehensive list applied to
Phase 3 work in general.*

**Treating Step 06 as the synthesis-by-smoothing step.** Step 06 is
synthesis-only. If the synthesis produces net-new design decisions,
mechanism choices, or verification instruments, something was missed
upstream. The right response is to pause Step 06, identify the
upstream gap, and fix it — not to paper over in synthesis. The
temptation to smooth at synthesis time is real.

**Running Step 03 with multiple briefs in a single session
unconditionally.** The default is one brief per Step 03 session.
Context-mixing across briefs in a single session reduces design
quality — each brief deserves a fresh session anchored in its
specific inputs. Sequential briefs in a single session work, but the
AI must explicitly reset focus between briefs. Parallelizing across
sessions for independent briefs (per Step 02's sequencing) is the
recommended pattern when capacity permits.

**Conflating Step 03 §6 invalidation with Step 04 §6 conflict.**
Step 03 §6 catches *Phase 2 mechanism untenable at design level*
(routes to Channel 2 amendment). Step 04 §6 catches *two Phase 3
specifications contradicting each other* (routes to spec-amendment,
limitation-acceptance, or Phase 2 escalation). The two are different
diagnostic states with different routings.

**Treating verification specifications as descriptions.** Step 05's
central discipline is "instruments, not descriptions." A test suite
without enumerated cases is a description; a test suite with cases
1-N specified is an instrument. A proxy-reader question set without
written questions is a description; one with the actual question
text is an instrument. The Step 05 Output Format's per-instrument
sub-formats enforce concrete content.

**Skipping the per-artifact principle scorecard contribution.**
Step 03's per-artifact scorecard is the discipline that makes the
Phase-3-level scorecard refresh (Step 06) credible. Skipping or
hand-waving per-artifact scores produces a Phase 3 scorecard refresh
that can't be defended. The Step 03 sub-template structure requires
the scorecard contribution before specification commitment; resist
the temptation to defer it.

**Silently working around a Phase 2 invalidation.** When Step 03
design work surfaces that a Phase 2 mechanism choice cannot be
coherently specified, the temptation is to re-shape the
specification around the problem and move on. The Phase 2
invalidation check exists to catch this. Route through Channel 2
explicitly.

**Conflating "specification" with "implementation."** A
specification that includes DDL, class diagrams, route handler
paths, or library import statements has drifted into implementation
territory. Pause and re-anchor. Phase 5 implements; Phase 3
specifies.

**Conflating "specification" with "architecture."** A specification
that includes module boundaries, internal class hierarchies, or
service-mesh topology has drifted into Phase 4 architecture
territory. Pause and re-anchor. Phase 4 architects; Phase 3
specifies.

**Letting the inherited principle weights drift.** Phase 3 inherits
Phase 2's weights unchanged. If a per-artifact scorecard
contribution feels like it should use different weights, the path
is upstream — either Phase 2 amendment (Channel 2) or upstream
toolkit gap (Channel 1) — not silent re-weighting in Phase 3.

**Treating a Phase 3 → Phase 2 feedback channel firing as a
failure.** When Channel 1 or Channel 2 fires, the framework is
working — a gap or invalidation was caught here, in Phase 3, rather
than in Phase 5. The cycle cost (Phase 2 amendment + Phase 3 re-
entry, or Phase 2 toolkit revision session) is far less than the
cost of carrying the gap or invalidation into implementation.

---

## What's Available, What's Not

### Available in v1.0

- All seven step prompts with sub-templates, output formats, and
  evaluation checklists
- Instructions file with three shifts, six artifact types,
  principle scorecard inheritance, two feedback channels,
  behavioral rules, common pitfalls
- This README
- `dogfooding-observations.md` template (empty, ready for first
  Phase 3 cycle)

### Not Yet Available (Queued for v1.1+ Based on Dogfooding)

- **Sub-template additions** — if the first Phase 3 dogfoods produce
  "Other" artifact-type declarations that recur, v1.1+ adds them as
  standalone sub-templates
- **Phase 2 cost-model calibration adjustments** — when Phase 5
  execution starts producing measured multipliers (graduating
  BELIEVED → ESTIMATED), Phase 3 toolkit's inherited multipliers
  update
- **Worked examples per artifact type** — adding a Diamonds-derived
  worked example to each sub-template would make the toolkit more
  illustrative; deferred to v1.1 to keep v1.0 lean
- **Step 04 visualization conventions** — current ASCII-graph
  dependency rendering is functional but not polished; Mermaid-
  rendered alternatives queued
- **Greenfield Phase 3 toolkit completion** — the greenfield variant
  is currently a single instructions file with envisioned but
  unauthored step prompts; completion is queued separately from
  this existing-projects work

---

## Version History

| Version | Date | Source | Summary |
|---------|------|--------|---------|
| **v1.0** | **2026-05-25** | **Initial authoring** | Initial Phase 3 existing-projects toolkit. Nine files (instructions file + 7 step prompts + README + dogfooding-observations.md template). Three shifts from Phase 2 (artifact specification vs design exploration; artifact-level vs dimension-level scoring; specification completeness vs simulation). Six artifact types in unified Step 03 (Contract / Refactor / IA / Schema / Observability / Verification + Other with declared shape). Principle scorecard inheritance from Phase 2 (weights and frame inherited; per-artifact contributions aggregated). Two Phase 3 → Phase 2 feedback channels (Channel 1: upstream toolkit gaps via Step 01 §11.2; Channel 2: run amendment via Step 06 §7). Three-quantity cost model inherited from Phase 2 v1.1. Multi-repo evidence scoping and code-access calibration inherited from Phase 1 v1.3 / Phase 2 v1.1. Dogfooding & calibration protocol inherited from Phase 2 v1.1. Target distribution check inherited from Phase 2 v1.1 scorecard rigor. |

---

*Part of the Phase 3 (Existing Projects) Design & Technical Analysis Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `design-technical-analysis.existing-project.instructions.md`*
