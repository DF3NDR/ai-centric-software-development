# Phase 2 — Analysis & Improvement Planning (Existing Projects)
# Tool Set README

**Toolset Version:** v1.1
**Series:** AI-Centric Software Development Playbook
**Track:** Existing Projects
**Phase:** Phase 2 — Analysis & Improvement Planning
**Inputs From:** Phase 1 (Information Gathering / Current-State Analysis)
**Outputs To:** Phase 3 (Design), Phase 4 (Architecture), Phase 5 (Implementation), Phase 6 (Testing), Phase 7 (Deployment)

---

## What This Tool Set Does

This tool set transforms a Phase 1 Current-State Information Report
into a **principle-weighted, sequenced, cost-modeled, capacity-checked
Improvement Plan** — the artifact that drives every subsequent phase.

Phase 1 surfaced what needs to change about an existing project.
Phase 2 decides which changes to make in which order with which
mechanisms at what cost. The decisions are principle-weighted because
not every project optimizes the six Core Principles equally —
Phase 2's Step 02 makes the weighting explicit and traceable.

The toolset produces six numbered artifacts plus a capstone
Improvement Plan. Each artifact feeds the next; the Improvement Plan
feeds the downstream phases.

### Tool Set Files

| File | Role |
|------|------|
| `analysis-improvement-planning.existing-project.instructions.md` | Load-once context; defines the AI role, behavioral rules, principle weighting discipline, **three-quantity cost-modeling discipline (v1.1)**, phase gate criteria |
| `step-00-building-block-discovery.prompt.md` | Building-block inventory; **produces the Toolset Augmentation Document (treated as living, not snapshot, per v1.1)** |
| `step-01-phase-1-input-validation.prompt.md` | Validates Phase 1 understanding; **produces Validation Gap Register split into Phase 2 local gaps and Upstream toolkit gaps (v1.1)** |
| `step-02-principle-weighting.prompt.md` | Assigns weights to the six Core Principles; resolves Phase 1 Scoring & Metrics CONDITIONAL |
| `step-03-mechanism-decisions.prompt.md` | Chooses mechanisms for multi-mechanism MCs; produces inter-MC dependency graph |
| `step-04-sequencing-and-tiering.prompt.md` | Tiered sequence; minimum-viable-completion floor; stretch scope; worst-case plan-failure narrative |
| `step-05-cost-modeling-and-capacity-check.prompt.md` | Per-MC cost rows with **three-quantity model (v1.1)**; per-tier and plan totals; capacity-vs-envelope comparison; capacity-bound recommendation |
| `step-06-improvement-plan-synthesis.prompt.md` | Capstone synthesis; Improvement Plan + Self-Evaluation Scorecard; Phase 3 Design Briefs; Phase 5 Task-List Seed; **Phase 7 Calibration Handoff when applicable (v1.1)** |
| `dogfooding-observations.md` | Phase 2 dogfooding observation record from the Diamonds run; v1.1 revision plan; Phase 1 v1.3 queue note |

---

## Recommended Sequence

The toolset is designed for sequential execution with the
practitioner reacting at each step. A complete Phase 2 cycle
typically runs:

```
Initial Specify interview
       │  (via instructions file)
       ▼
step-00 Building Block Discovery
       │  (5-10 minutes; produces LIVING Toolset Augmentation Document)
       ▼
step-01 Phase 1 Input Validation
       │  (question-by-question; produces VG Register split into
       │   Phase 2 local + Upstream toolkit per v1.1)
       ▼
step-02 Principle Weighting
       │  (draft-and-react; resolves Phase 1 Scoring & Metrics CONDITIONAL)
       ▼
step-03 Mechanism Decisions
       │  (draft-and-react; MC triage + per-MC drafts in batches —
       │   4 default, 2-3 for cross-referenced clusters, 1 for
       │   independent cleanup MCs per v1.1)
       ▼
step-04 Sequencing and Tiering
       │  (draft-and-react; includes worst-case plan-failure narrative
       │   with common-mechanism naming)
       ▼
step-05 Cost Modeling and Capacity Check
       │  (draft-and-react; three-quantity cost model per v1.1:
       │   dev-hours + AI-acceleration multiplier + maintainer-hours +
       │   token-count + token-cost; capacity-bound recommendation if
       │   plan exceeds envelope)
       ▼
step-06 Improvement Plan Synthesis
       │  (synthesis-only; Improvement Plan + Self-Evaluation Scorecard;
       │   Phase 3 Design Briefs; Phase 5 Task-List Seed; Phase 7
       │   Calibration Handoff when BELIEVED multipliers used per v1.1)
       ▼
Phase 3 (Design & Technical Analysis) — Existing Projects toolkit
       (when authored)
```

Each step assumes the prior step's artifact is loaded as context.
Steps are typically run in separate AI sessions to keep context
focused, but a single long session with sufficient context window
also works.

---

## MCP Server Recommendations

Phase 2 work benefits from these MCP connectors. The step-00
Building Block Discovery prompt inventories what's available and
documents graceful-degradation posture where capabilities are
missing.

| Capability | Recommended Connector | Used For |
|-----------|----------------------|----------|
| Issue tracker access | GitHub MCP (or equivalent) | Mechanism context cross-MCs; open-issue cross-reference during Step 03 |
| Library / framework currency | Context7 (or equivalent) | Mechanism choice evaluation (e.g., "is this library's current major version still maintained?") |
| Direct code access | Claude Code / equivalent | Mechanism verification (e.g., "does the chosen mechanism actually compile against current imports?") |
| Web search | Built-in or equivalent | Cross-validation when MCP-specific sources are unavailable |

**Capabilities can shift mid-phase.** *(New discipline per v1.1,
Cluster E from Diamonds dogfooding.)* The Toolset Augmentation
Document produced in step-00 is treated as living, not snapshot —
when a connector activates, fails, or upgrades between steps, the
augmentation document gets a dated amendment rather than being left
stale. Downstream AI sessions reading the document see both the
initial inventory and the amendment history.

### Connector Activation Retry Pattern

If a connector is expected but tools aren't visible on first call:
attempt once → if not found, ask the practitioner to confirm
activation → retry once when confirmed. This pattern handles the
common case where a connector was enabled in a previous session
but the current session needs to refresh.

---

## Dogfooding & Calibration Guidance

This tool set was authored by running the AI-Centric Software
Development framework on itself. The Phase 2 toolkit was authored
to v1.0 conventions inheriting Phase 1 v1.2's disciplines (matured
through Phase 1's own dogfooding), then dogfooded on
`@diamondslab/diamonds` during the Phase 2 cycle that followed
Phase 1's Diamonds cycle.

**Observation calibration target:** A complete Phase 2 dogfooding
run on a new project profile should typically surface **15-25
observations** about the toolkit itself — opportunities for
improvement, calibration signals, gaps that didn't show up in
prior runs. The Diamonds run surfaced 7 observations (under-range),
explained by Phase 2 v1.0 inheriting Phase 1 v1.2's mature
disciplines. Future runs on different project profiles
(regulated-industry, multi-engineer team, mature-productized
library, etc.) may surface different patterns.

**Observations during a run** should be captured as they surface
but not acted upon until end-of-phase review (Option B
discipline — same as Phase 1's dogfooding pattern). At end-of-Phase
the observations cluster; clusters become v1.x revision items.

**The Phase 2 → Phase 1 feedback channel is a feature.** *(New in
v1.1, Cluster D.)* Step 01's Validation Gap Register is split into
two scopes: Phase 2 local gaps (Phase 2 resolves within the cycle)
and Upstream toolkit gaps (the Phase 1 toolkit was incomplete in
some structural way that Phase 2 work surfaced; durable fix is a
Phase 1 toolkit revision queued separately). The Diamonds run
produced 5 VGs of which 3 were upstream toolkit gaps — the split
makes this inter-phase feedback channel explicit rather than
implicit. The pattern generalizes: Phase 3's Step 01 (Phase 2 Input
Validation, when authored) should inherit the same split, and so on
downstream.

### Phase 2 Dogfooding Observation Pattern

The companion `dogfooding-observations.md` file documents the
Diamonds Phase 2 run's 7 observations in full, plus the
end-of-Phase-2 review (cluster decisions, accept rates, v1.1
revision file map) and Phase 1 v1.3 queue note.

---

## Self-Evaluation Scorecard Discipline

The Step 06 synthesis includes a built-in self-evaluation
scorecard rating Phase 2 deliverables against the six Core
Principles using the Step 02 weights. **Scorecard rigor** is
applied: CONDITIONAL is preferred over PASS-with-caveats, and each
CONDITIONAL must name the specific Phase 3 decision required to
resolve.

**Expected distribution on a well-executed Phase 2:** 4-5 PASS +
1-2 CONDITIONAL. Uniformly-PASS suggests insufficient self-
evaluation rigor (every Phase 2 cycle typically has at least one
item where the Plan establishes mechanism but Phase 3 must produce
a specific design artifact). Multiple FAILs indicate Phase 2 has
not done its job — cycle back, fix the gap, do not pass FAILs
forward.

The Diamonds Phase 2 cycle rated 4 PASS + 2 CONDITIONAL — within
target range. CONDITIONALs were Operations (deferred to next cycle
by explicit weight choice; Phase 3 produces observability touchpoint
design) and Correctness Verification (Phase 3 produces specific
verification-artifact specifications alongside the four design
briefs).

---

## Common Pitfalls

### Pitfall: Treating Step 06 as a Decision-Making Step

Step 06 is **synthesis-only**. Every mechanism in the Plan must
trace to Step 03; every sequencing decision to Step 04; every cost
row to Step 05. If Step 06 is producing net-new content, something
was missed in Steps 01-05 — pause Step 06 and fix the upstream
gap.

### Pitfall: Silently Upgrading Tags

Tags (MEASURED / ESTIMATED / BELIEVED / UNMEASURED) are
auditable artifacts. Validation must not silently upgrade BELIEVED
to MEASURED; cost modeling must not silently upgrade ESTIMATED to
MEASURED. Tag changes are calibration events with rationale, not
stylistic choices.

### Pitfall: Conflating Dev-Hours and Maintainer-Hours

*(New pitfall per v1.1, Cluster A.)* In AI-Centric Software
Development practice, dev-hours (Senior Developer baseline without
AI) and maintainer-hours (actual practitioner time spent) are
distinct quantities. AI acceleration may decouple them by an order
of magnitude. The capacity envelope binds maintainer-hours, not
dev-hours. Step 05's three-quantity cost model formalizes the
distinction — every per-MC row carries dev-hours with tag, an
AI-acceleration multiplier with category attribution, and derived
maintainer-hours.

### Pitfall: Skipping the Worst-Case Plan-Failure Narrative

Step 04's worst-case narrative discipline is the Plan's
structural-fragility check. The discipline requires naming a common
mechanism producing all failure branches (not just enumerating
three unrelated bad outcomes). The common-mechanism naming is what
makes the narrative actionable — Step 06 surfaces it forward and
Phase 7 can establish watch-triggers against it.

### Pitfall: Treating Operations Deprioritization as Permanent

Step 02's principle weighting may explicitly deprioritize
Operations (1.0× weight) for a current cycle — typically when the
subject is pre-production with zero adopters. The deprioritization
is documented and forward-noted: next cycle's Phase 2 typically
elevates Operations as adoption ramps up. The Step 06 scorecard's
Operations CONDITIONAL (a common pattern) names this forward
handoff explicitly.

---

## Connecting to Phase 3

The Improvement Plan's Section 6 (Phase 3 Design Briefs) is the
primary handoff. Each design brief names:
- The MC and its chosen mechanism (from Step 03)
- The design questions Phase 3 must resolve
- Constraints inherited from Phase 1
- The verification method Phase 6 will use

When the Phase 3 (Design & Technical Analysis) toolkit is authored,
its Step 01 (Phase 2 Input Validation) inherits the same scope
split that Phase 2's Step 01 introduced — Phase 3 local gaps vs.
Upstream (Phase 2) toolkit gaps. The pattern repeats.

---

## Version Table

| Toolkit Version | Date | Notes |
|----------------|------|-------|
| v1.0 | 2026-04-22 | Initial authoring. Authored to v1.2 Phase 1 conventions (matured through Phase 1's own dogfooding). |
| **v1.1** | **2026-05-22** | **Revisions from Diamonds Phase 2 dogfooding (7 observations, 6 clusters, 5 accepted for v1.1, 1 routed to Phase 1 v1.3).** Three-quantity cost model formalized in instructions file and step-05; Toolset Augmentation Document treated as living per step-00 and instructions file; Validation Gap Register split (Phase 2 local + Upstream toolkit) per step-01; Phase 7 Calibration Handoff requirement added to step-06; batch-sizing guidance refined in step-03. step-02 and step-04 unchanged. |

---

## Version History

| Version | Date | Source | Summary |
|---------|------|--------|---------|
| v1.0 | 2026-04-22 | Initial authoring | Initial Phase 2 toolkit README. Eight tool set files, six-step sequence diagram, MCP connector recommendations, dogfooding calibration guidance, scorecard discipline, common pitfalls, connection to Phase 3. |
| **v1.1** | **2026-05-22** | **Diamonds Phase 2 dogfooding run (Clusters A, D, E)** | Updated Tool Set Files table to reflect v1.1 revision summary per file. Updated Recommended Sequence diagram to mark v1.1 features inline (LIVING augmentation doc, VG register split, batch sizing, three-quantity cost model, Phase 7 calibration handoff). Added "Capabilities can shift mid-phase" subsection under MCP Server Recommendations (Cluster E). Expanded Dogfooding & Calibration Guidance section with new "Phase 2 → Phase 1 feedback channel is a feature" subsection (Cluster D). Added new common pitfall "Conflating Dev-Hours and Maintainer-Hours" (Cluster A). Updated Version Table with v1.1 entry summarizing the revision arc. dogfooding-observations.md added to Tool Set Files list. |

---

*Part of the AI-Centric Software Development Playbook — Phase 2 (Existing Projects) Tool Set, v1.1*
*Companion files: `analysis-improvement-planning.existing-project.instructions.md` and step-00 through step-06 prompts*
*Dogfooding record: `dogfooding-observations.md`*
*Phase 1 toolkit reference (current at v1.2; v1.3 queued for Cluster B): `toolkit/existing-projects/phase-1-information-gathering/`*
