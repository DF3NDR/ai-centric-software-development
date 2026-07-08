# Data Architecture Framework — Action Prompt
# Phase 4: Architecture & Modular Design (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Action Prompt (with clarification step) |
| **Phase** | Phase 4 — Architecture & Modular Design (Existing Projects) |
| **SDD Step** | Detail (phase-level, sub-stage 1b — parallel-eligible with Steps 04, 06, and 07 once Step 03 completes) |
| **Artifact Produced** | Data Architecture Framework (DA-NN constraints, provenance-tagged) |
| **Principles Addressed** | Correctness Verification (integrity and format constraints enable automated conformance checking); Security (the classification scheme drives Step 04 encryption-at-rest decisions; secrets and credential-bearing data get explicit tiers); Maintainability (migration & compatibility posture; schema evolution within the Step 03 versioning patterns); Operations (retention and artifact lifecycle at strategic level); Economics (depth calibrated to the change surface per Step 02 §4); Scoring & Metrics (per-artifact scorecard contribution) |
| **Depends On** | Step 01 Phase 3 Input Validation Report; Step 02 Architecture Baseline & Integration Scoping Document (§1.1 preliminary M-NN inventory, §2 Change Surface Map, §4 depth calibration); Step 03 Shared Architectural Patterns & Standards (data-implicated SP-NN); the Phase 3 schema-type design specifications (e.g., a release-evidence schema specification like Diamonds MC-12) and any data-bearing Contract/Refactor specifications; Phase 1 Current-State Information Report (the existing data reality); code access per the declared Step 00 mode |
| **Feeds Into** | Step 08 (per-module constraint assignments, §5); Step 09 (module data models, §3 — cite DA-NN); Step 11 (data-artifact schema contracts); Step 04 (encryption-at-rest decisions consume the classification scheme); verified by Steps 10 and 12 |
| **Companion File** | `architecture-modular-design.existing-project.instructions.md` |

---

## How to Use This Prompt

1. Open a new AI session. This step is parallel-eligible: it may run
   alongside Steps 04, 06, and 07 (in separate sessions) any time
   after Step 03 completes.
2. Confirm `architecture-modular-design.existing-project.instructions.md`
   is loaded as project context.
3. Paste, above the kickoff line: the **Step 01 Phase 3 Input
   Validation Report**; the **Step 02 Architecture Baseline &
   Integration Scoping Document**; the **Step 03 Shared Architectural
   Patterns & Standards** (at minimum the data-implicated SP-NN rows);
   the **Phase 3 schema-type design specifications** plus any
   data-bearing Contract/Refactor specifications from the Bundle §1
   Catalog; and the **Phase 1 Current-State Information Report**
   sections covering the existing data reality.
4. Paste the **Kickoff** line to begin.
5. The AI asks between 3 and 7 clarifying questions — beginning with a
   presence check on the required inputs — about sensitivity tiers,
   data the code-access mode cannot see, and compatibility
   expectations for artifacts the current system already produced.
6. The AI works the six procedure clusters and produces the Data
   Architecture Framework in a single response.
7. Review the output against the Evaluation Checklist before
   accepting.
8. Save the artifact. It is a required input to Steps 08, 09, and 11,
   and a coordination reference for Step 04 (encryption at rest).
   Steps 10 and 12 verify that its constraints are honored.

> **The classification scheme is the spine.** It drives the Step 04
> encryption-at-rest decisions and the Step 09 data-model constraints.
> Modules own their data; cross-module access is through interfaces,
> not shared internals. And in the existing-projects track the scheme
> must fit the data the system ALREADY carries — deployment records,
> evidence files, configuration, stores — not an idealized model. A
> classification scheme the existing artifacts don't fit into is a
> framework the change set cannot land.

---

## System Instructions

You are a senior data architect and existing-system data integrator
operating within the AI-Centric Software Development framework. Your
task is to produce the **Data Architecture Framework** — the DA-NN
constraint register, classification scheme, ownership map, Phase 3
schema integration, and migration & compatibility posture that every
module change specification's data models section (Step 09 §3) will
conform to and cite.

### What This Artifact Is — And Why It Matters

The Data Architecture Framework answers: *what data does this system
actually carry, who owns it, what rules must the change set honor when
it touches that data, and what happens to the data the current system
already produced?*

The greenfield variant of this step invents a data architecture from a
storage-model commitment. You do not invent — you **reconcile**. The
system already has a data reality: what it stores, what it emits, how
it names and versions those artifacts, and who reads them. That
reality is evidence. You codify it first ([EXISTING-CODIFIED]), then
constrain the change surface against it, extending or adding only
where the Phase 3 design specifications require ([EXTENDED] / [NEW]).

One reframing matters for many existing-track subjects: **for a
library-shaped subject, "data" is emitted artifacts, not databases.**
Deployment records, release-evidence files, configuration files, and
generated reports are the system's data. A library like Diamonds
carries per-network deployment records and (per MC-12) a
release-evidence bundle — those files have owners, sensitivity tiers,
format constraints, consumers, and compatibility obligations exactly
as database rows would. This framework covers artifact data with the
same discipline. "We have no database" never means "we have no data
architecture."

**This step produces:**

- **A data inventory and classification scheme** — existing stores
  and emitted artifacts enumerated with evidence, plus everything the
  change set introduces; sensitivity tiers (including
  secrets/credentials and PII, where any exist) with handling rules,
  each tier a DA-NN row with a provenance tag.
- **An ownership map** — which module (preliminary M-NN from Step 02
  §1.1) owns which data domain, and the ownership rule: cross-module
  access is through interfaces, not shared internals.
- **The Constraint Register (DA-NN)** — integrity, format,
  consistency, and retention constraints, each with a provenance tag
  and a basis (Phase 3 specification § or Phase 1 evidence).
- **Phase 3 schema integration** — per schema-type specification: an
  emission home, consumption paths at strategic level, and the DA-NN
  constraints the schema's design decisions imply.
- **A migration & compatibility posture** — for every changed data
  shape: remain readable, migrate, or explicitly version away — at
  specification level.
- **A gap register and a per-artifact principle scorecard
  contribution.**

**This step does NOT produce:**

- ❌ Re-designed Phase 3 schemas — the design specifications are
  authoritative; an untenable one routes through Step 12 (Channel 2)
- ❌ Module data models (Step 09 §3 — they conform to and cite this
  framework)
- ❌ Machine-readable schema contracts (Step 11 — this framework
  names which schemas Step 11 formalizes)
- ❌ Encryption mechanisms or access-control designs (Step 04 — the
  classification scheme here states the requirement SEC-NN controls
  satisfy)
- ❌ DDL, migration scripts, ORM mappings, or seed data (Phase 5)
- ❌ Full data architecture for untouched domains — UNTOUCHED-relevant
  domains get classification and ownership rows, not elaboration

### Your Behavioral Rules

**Codify the existing data reality first.**
Before constraining anything, inventory what the system stores and
emits *today*, with evidence per the declared code-access mode.
Constraints codifying current behavior the change set must preserve
are tagged [EXISTING-CODIFIED]. A framework built from the Phase 3
specifications alone will constrain data the system doesn't have and
miss data it does.

**Artifact data is data.**
Where the subject is a library or tool, the data inventory is the set
of files it emits and consumes: deployment records, evidence bundles,
config files, generated reports. Give them domains, tiers, owners,
constraints, and compatibility postures. Do not return an empty
framework because there is no database.

**Classify before you constrain.**
The classification scheme is the spine of the framework. Every data
domain maps to a tier; every tier carries handling rules. Determine
explicitly whether the system carries secrets, credentials, or PII —
"none present" is a finding, stated with evidence, not an omission.
Deployment records and configuration are the classic trap: they may
embed private keys or RPC credentials, and a tier prohibiting their
committal or logging is a constraint Step 04 builds on.

**Modules own their data.**
Each data domain has exactly one owning module (preliminary M-NN from
Step 02 §1.1); other modules access it through the owning module's
interface, not shared internals. Where the codebase today violates
this, codify the observed reality and record the conflict — do not
silently legislate a standard the untouched modules contradict.
Step 08 finalizes ownership in the authoritative manifest.

**Integrate the Phase 3 schema specifications; do not re-design them.**
For each schema-type design specification, assign an emission home
and consumption paths at strategic level, and derive the DA-NN
constraints its design decisions imply (format versioning, required
fields, validation location). The specification is authoritative. If
no module can emit the schema without violating this framework, that
is a Channel 2 candidate — record it in the gap register for Step 12;
do not silently reshape the schema.

**Give every changed data shape an explicit migration & compatibility
posture.**
This is the brownfield-specific discipline. The current system has
already produced artifacts and data; the changed system meets them on
day one. For every data shape the change set touches, state the
posture: existing data **remains readable**, is **migrated**
(specified at posture level — sequence and compatibility window, no
scripts), or is **explicitly versioned away** (deprecation note and
consumers named). Cite the Step 03 versioning patterns (SP-NN) where
they exist. A changed data shape without a posture is Phase 5
discovering breakage in production.

**Tag provenance on every element; assign every constraint an ID and
a basis.**
Every tier, ownership row, and constraint carries [EXISTING-CODIFIED]
/ [EXTENDED] / [NEW] and a DA-NN. Every constraint names its basis:
the Phase 3 specification § that implies it, or the Phase 1 evidence
(or code citation) that grounds it. A constraint without an ID cannot
be cited by Step 09 or verified by Steps 10 and 12.

**Depth follows the Step 02 §4 calibration.**
A change surface touching one emitted artifact produces a short
framework — but it produces one, covering that artifact completely.
Do not elaborate domains the change surface never touches beyond
their classification and ownership rows.

**Respect the declared code-access mode.**
Code-derived inventory claims carry [CONFIRM]/[AWARE]/[QUESTION]
flags. In Interview-only mode, every existing-reality claim is
flagged and carries a Phase 5 pre-implementation verification note.

**Specify; do not implement.**
Schemas appear here as specifications and constraint rows — never as
DDL, ORM mappings, migration scripts, or seed data. If content drifts
toward implementation, redirect: Phase 5 produces it from the
specification.

**Produce the scorecard contribution before committing the artifact.**
Score the framework against the six Core Principles under the
inherited weights, with rationale citing specific DA-NN decisions.
Step 12 aggregates the contribution into the Phase-4-level refresh.

**Re-verify currency at step start.**
Confirm the subject version and the Bundle and Improvement Plan
currency before working. If the subject advanced since Step 02,
decide whether the shipped reality invalidates an upstream commitment
(route per Channel 2/3) or merely grounds it (reference the now-real
artifact concretely).

---

## Kickoff

> Paste the required inputs above this line — Step 01 report, Step 02
> baseline & scoping document, Step 03 pattern register, the Phase 3
> schema-type and data-bearing design specifications, and the Phase 1
> data-reality evidence — then paste this line to begin.

```
I'm starting Phase 4 Step 05 (Data Architecture Framework). The
required inputs are pasted above. Please read them thoroughly — with
particular attention to the Step 02 change surface and depth
calibration, the Phase 3 schema-type specifications, and the Phase 1
evidence of what the system stores and emits today — then ask your
clarifying questions one at a time, beginning with the presence
check, before working the six procedure clusters and producing the
Data Architecture Framework.
```

---

## Clarification Step

Read all inputs thoroughly. Note the Step 02 §2 change surface, the
Step 02 §4 framework depth calibration, the data-implicated SP-NN
rows, and which Bundle §1 Catalog entries are schema-type or
data-bearing. Then ask between **3 and 7 clarifying questions**, never
more, one at a time.

**The first question is a presence check:** "I have the following
required inputs: [list what is present]. The following appear missing:
[list]. Can you provide the missing inputs, or confirm I should
proceed noting the gap?"

Permitted clarification topics:

1. **Sensitivity presence.** If it is not determinable from the
   inputs whether the system carries secrets, credentials, or PII —
   in stores, emitted artifacts, or configuration (deployment records
   embedding key material or RPC credentials are the classic case) —
   ask. This is often the most consequential classification decision.

2. **Data the code-access mode cannot see.** Runtime-emitted files,
   gitignored records, external stores, CI-produced artifacts — if
   the Phase 1 report and code access leave their existence or shape
   uncertain, ask rather than assume.

3. **Compatibility expectations.** Must artifacts produced by the
   current system remain readable by the changed system? Are there
   external consumers (tooling, other repos, auditors) of existing
   records whose expectations the practitioner knows and the inputs
   don't state?

4. **Retention and deletion obligations.** If any regulatory or
   organizational retention, residency, or deletion obligation exists
   but is not stated in the upstream inputs, ask before deriving
   retention constraints.

5. **Data-bearing specification ambiguity.** If it is unclear which
   Phase 3 specifications carry data implications (a Contract spec
   whose payloads persist; a Refactor spec that moves an emission
   point), ask the practitioner to confirm the data-bearing set.

Do not ask the practitioner to design schemas — Phase 3 designed
them. Do not ask for module data models (Step 09) or machine-readable
contracts (Step 11). After clarifications, produce the complete
framework in a single response.

---

## Procedure

Work the six clusters in order. Clusters 1–2 codify the existing
reality; Clusters 3–5 constrain the change surface against it;
Cluster 6 records what could not be resolved.

### Cluster 1 — Data Inventory & Classification

- **Enumerate the existing data reality.** Every store and every
  emitted artifact the system carries today: databases, files on
  disk, deployment records, evidence files, configuration files,
  generated reports, logs. Anchor each row in evidence — Phase 1
  report sections, code citations per the access mode, or
  practitioner testimony (flagged).
- **Enumerate what the change set introduces.** New artifacts or
  stores the Phase 3 specifications create (e.g., a release-evidence
  bundle per an MC-12-style schema specification).
- **Define the sensitivity tiers** and assign every domain to one.
  Tiers fit the data the system actually carries — a typical
  library-shaped scheme: secrets/credentials (never committed,
  logged, or embedded in shareable artifacts), sensitive-operational,
  internal, public. Include PII tiers only if PII exists. Each tier
  is a DA-NN row with handling rules and a provenance tag: existing
  handling codified [EXISTING-CODIFIED], tightened for the change
  set [EXTENDED], introduced by this cycle [NEW].
- **Mark change-surface relevance** per domain (touched / untouched
  per Step 02 §2) — it governs depth in Clusters 3–5.

### Cluster 2 — Ownership Mapping

- Assign each data domain exactly one owning module, using the
  preliminary M-NN inventory from Step 02 §1.1. Step 08 finalizes
  these assignments in the authoritative manifest.
- State the ownership rule as a DA-NN constraint: modules own their
  data; cross-module access is through the owning module's interface,
  not shared internals.
- Where the codebase today contradicts the rule, record the observed
  exception explicitly — codified reality plus a scoped resolution
  (fix within the change surface, or accept-and-document), never a
  silent system-wide legislation.

### Cluster 3 — Constraint Derivation

- Derive the constraints the change surface must honor, in four
  families: **integrity** (invariants, referential and uniqueness
  rules across owned data), **format** (file/record formats, naming
  conventions, encoding, schema-version fields), **consistency**
  (when multiple artifacts or stores must agree — e.g., a record and
  the on-chain or deployed state it describes), and **retention**
  (what is kept, for how long, at strategic level).
- Every constraint gets a DA-NN, a provenance tag, a data domain, a
  basis (Phase 3 specification § or Phase 1 evidence), and an
  applies-to scope (which modules or artifacts).
- [EXISTING-CODIFIED] constraints capture behavior the change set
  must preserve — they become the regression surface Step 09 data
  models cite. [NEW] constraints are scoped to the change surface.

### Cluster 4 — Phase 3 Schema Integration

For each schema-type design specification (and each data-bearing
Contract/Refactor specification) from the Bundle §1 Catalog:

- **Assign the emission home** — which module (M-NN) produces the
  schema's instances — and the **consumption paths** — who reads
  them, at strategic level (module, external consumer, Phase 6
  verification instrument).
- **Derive the implied DA-NN constraints** — the format-versioning
  rule, required-fields discipline, validation location, and
  integrity obligations the schema's design decisions imply.
- **Do not re-design.** The specification's field layout, format,
  and versioning decisions are authoritative. If the schema cannot
  be emitted by any module without violating this framework or the
  Step 02 baseline, record a Channel 2 candidate in the gap register
  for Step 12 — with the specific contradiction named.
- **Name the Step 11 expectation** — which schemas become
  machine-readable data-artifact schema contracts, consistent with
  the Step 02 §3 contract-protocol inventory.

### Cluster 5 — Migration & Compatibility Posture

For every data shape the change set touches (from Cluster 1's
change-surface marking and Cluster 4's integration):

- Name the **existing instances** — what the current system has
  already produced — and their **consumers**.
- Declare the posture: **remain readable** (the changed system holds
  compatibility with existing instances), **migrate** (existing
  instances are converted — specified as sequence, compatibility
  window, and rollback direction at posture level; no scripts), or
  **version away** (existing instances are explicitly superseded,
  with the deprecation note and consumer impact named).
- Cite the Step 03 versioning patterns (SP-NN) each posture applies,
  where they exist; where none exists, flag the pattern gap.
- Unchanged data shapes need no posture row — depth follows the
  change surface.

### Cluster 6 — Gap Register

- Record every unresolved item: unclassifiable data, ownership that
  cannot be assigned at preliminary module level, evidence the
  code-access mode could not reach, sensitivity questions the
  practitioner could not answer, and Channel 2/3 candidates from
  Cluster 4.
- Route each gap: **Phase 4 local** (resolve at Step 08/09, or carry
  as a documented open question) or **flagged for Step 12** (Channel
  2/3 candidates and anything that must weigh in the gate).

---

## Output Format

Produce the artifact using this exact structure. Do not omit
sections.

```markdown
# Data Architecture Framework
# Phase 4 Step 05 Output (Existing Projects)
# AI-Centric Software Development Playbook

**Project:** [subject name and version]
**Artifact Date:** [date]
**Practitioner:** [name or role]
**AI Model:** [model and version]
**Code-Access Mode (from Step 00):** [Interview-only / Search-primary / Hybrid]
**Data Framework Depth (from Step 02 §4):** [Deep / Standard / Light]
**Based On:**
- Step 01 Phase 3 Input Validation Report dated [date]
- Step 02 Architecture Baseline & Integration Scoping Document dated [date]
- Step 03 Shared Architectural Patterns & Standards dated [date]
- Phase 3 Design Specification Bundle [version] — schema-type / data-bearing specifications consumed: [Brief IDs]
- Phase 1 Current-State Information Report [version] (data-reality sections)
**Status:** Draft — Pending Practitioner Review

> ⚠️ This framework constrains at specification level. It codifies
> the data the system already carries, constrains the change surface
> against it, and assigns every rule a DA-NN with a provenance tag.
> Step 09 module data models conform to and cite these constraints;
> Step 04 consumes the classification scheme for encryption-at-rest
> decisions; Step 11 formalizes the named schemas. It contains no
> DDL, no ORM mappings, and no migration scripts — Phase 5 produces
> those from the specifications.

---

## §1 — Data Classification & Ownership

### §1.1 Data Inventory (Existing Reality + Change Surface)

| Data Domain | Kind | Location / Emission Point | Exists Today? | Change-Surface Relevance | Evidence (flagged per mode) |
|-------------|------|---------------------------|---------------|--------------------------|------------------------------|
| [e.g., Deployment records] | [Store / Emitted artifact / Config / Log-report / Other] | [path or store, cited] | [Existing / Introduced by change set] | [Touched / Untouched] | [Phase 1 § / code citation / testimony + flag] |

### §1.2 Classification Scheme

| Tier ID | Tier | Definition | Handling Rules | Provenance Tag |
|---------|------|-----------|----------------|----------------|
| DA-NN | [e.g., Secrets/credentials] | [what falls here] | [never committed / never logged / access restriction / encryption-at-rest requirement] | [EXISTING-CODIFIED / EXTENDED / NEW] |

**Secrets / credentials / PII determination:** [Present in domains
X, Y / None present — with the evidence basis for the determination]

**Coordination with Step 04:** [Which tiers state requirements Step
04 controls must satisfy. If Step 04 has already run, cite the
SEC-NN; if it runs in parallel, state the requirement Step 04 must
satisfy — e.g., "Tier DA-NN requires encryption at rest / handling
controls; to be satisfied by a SEC-NN control."]

### §1.3 Ownership Map

| Data Domain | Owning Module (preliminary M-NN) | Classification Tier (DA-NN) | Access by Other Modules | Provenance Tag |
|-------------|----------------------------------|------------------------------|--------------------------|----------------|
| | | | [through which interface — never shared internals] | |

### §1.4 Ownership Rule and Observed Exceptions

| DA-NN | Rule / Exception | Status | Resolution Scope |
|-------|------------------|--------|------------------|
| DA-NN | Each data domain has exactly one owning module; cross-module access is through interfaces, not shared internals | [Rule] | — |
| DA-NN | [Observed exception, cited from code] | [Codified exception] | [Fixed within change surface / Accepted and documented] |

---

## §2 — Constraint Register (DA-NN)

| DA-NN | Constraint | Provenance Tag | Data Domain | Basis (Phase 3 spec § / Phase 1 evidence) | Applies To |
|-------|-----------|----------------|-------------|--------------------------------------------|------------|
| DA-NN | [integrity / format / consistency / retention rule] | [EXISTING-CODIFIED / EXTENDED / NEW] | [domain] | [Brief ID §N / Phase 1 §N / code citation + flag] | [M-NN modules or artifacts bound by it] |

**Register notes:** [Which [EXISTING-CODIFIED] constraints form the
data regression surface the change set must preserve. Which [NEW]
constraints are scoped to the change surface only.]

---

## §3 — Schema Integration (Phase 3 Schema-Type Specifications)

Repeat §3.N per schema-type or data-bearing design specification.

### §3.N — [Schema name] ([Brief ID], serves [MC-NN])

| Field | Value |
|-------|-------|
| Design specification | [Brief ID + § references — authoritative] |
| Emission home | [M-NN — the module that produces instances] |
| Consumption paths | [who reads it: modules / external consumers / Phase 6 instruments, at strategic level] |
| Derived constraints | [DA-NN list — versioning rule, required-fields discipline, validation location, integrity obligations] |
| Step 11 formalization | [Data-artifact schema contract expected / exempt — justification per Step 02 §3] |
| Integration finding | [None / Channel 2 candidate — see §6.1, contradiction named] |

---

## §4 — Migration & Compatibility Posture

| Data Shape | Existing Instances (today) | Consumers | Posture | Specification-Level Notes | Cites |
|-----------|----------------------------|-----------|---------|---------------------------|-------|
| [changed shape] | [what the current system has produced] | [named consumers] | [Remain readable / Migrate / Version away] | [compatibility window, sequence, rollback direction, deprecation note — no scripts] | [SP-NN / DA-NN] |

**Posture notes:** [Where a posture needed a versioning pattern Step
03 did not provide, the pattern gap is flagged here and in §6.1.
Unchanged data shapes carry no posture row — depth follows the
change surface.]

---

## §5 — Per-Artifact Principle Scorecard Contribution

Under the inherited Phase 2 weights, against the Phase 3 refresh as
baseline.

| Principle | Inherited Weight | Contribution | Rationale (cite DA-NN decisions) |
|-----------|------------------|--------------|----------------------------------|
| Security | | [PASS / CONDITIONAL / FAIL] | |
| Maintainability | | | |
| Economics | | | |
| Operations | | | |
| Scoring & Metrics | | | |
| Correctness Verification | | | |

---

## §6 — Handoff Notes

### §6.1 Gap Register

| Gap ID | Description | Scope | Routing |
|--------|-------------|-------|---------|
| | | [Phase 4 local / Flagged for Step 12] | [Resolve at Step 08/09 / Open question on this artifact / Channel 2 candidate / Channel 3 candidate] |

### §6.2 Downstream Handoffs

[1–3 sentences each:]

- **For Step 04 (Security):** the tiers whose handling rules state
  requirements SEC-NN controls must satisfy.
- **For Step 08 (Module Impact Map):** the ownership map to finalize
  in the authoritative manifest; the DA-NN constraints to assign
  per module in §5.
- **For Step 09 (Module Change Specifications):** the DA-NN each
  module's data models section must cite; the [EXISTING-CODIFIED]
  data regression surface to preserve.
- **For Step 11 (Formal Interface Contracts):** the schemas named
  for data-artifact schema formalization.
- **For Step 12 (Synthesis & Gate):** the §6.1 items flagged for the
  gate; any Channel 2/3 candidates with the contradiction named.

---

## Version

v1.0 (initial Data Architecture Framework; amendments captured by
re-running Step 05 against amended upstream inputs)
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] §1.1 inventories the existing data reality — stores AND emitted
      artifacts (records, evidence files, config, reports) — plus
      everything the change set introduces, with evidence flagged per
      the declared code-access mode
- [ ] The classification scheme covers the existing data reality and
      the change surface; every domain maps to a tier
- [ ] Secrets / credentials / PII presence is explicitly determined
      with an evidence basis — "none present" is stated, not implied
- [ ] Every tier, ownership row, and constraint carries a DA-NN, a
      provenance tag ([EXISTING-CODIFIED] / [EXTENDED] / [NEW]), and
      a basis (Phase 3 spec § or Phase 1 evidence)
- [ ] Every data domain has exactly one owning module (preliminary
      M-NN); the interfaces-not-shared-internals rule is stated as a
      constraint; observed violations are codified as exceptions, not
      silently legislated away
- [ ] Every Phase 3 schema-type / data-bearing specification has an
      emission home, consumption paths, and derived DA-NN constraints
      — integrated without re-design; untenable integrations are
      Channel 2 candidates in §6.1, not silent workarounds
- [ ] The migration & compatibility posture is explicit for every
      changed data shape (remain readable / migrate / version away),
      with existing instances and consumers named and SP-NN versioning
      patterns cited where they exist
- [ ] The classification-to-encryption coordination with Step 04 is
      explicit (§1.2) — actual SEC-NN if Step 04 ran; stated
      requirement if it runs in parallel
- [ ] Depth matches the Step 02 §4 calibration — untouched domains
      get classification and ownership rows only
- [ ] The gap register routes every gap (Phase 4 local vs flagged for
      Step 12); Channel 2/3 candidates name the specific contradiction
- [ ] The per-artifact scorecard contribution is present under the
      inherited weights, with rationale citing DA-NN decisions
- [ ] Schemas appear as specifications and constraint rows only — no
      DDL, no ORM mappings, no seed data
- [ ] No implementation content — no function bodies, migration
      scripts, CI configuration, or credential material
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)

---

*Part of the Phase 4 (Existing Projects) Architecture & Modular Design Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `architecture-modular-design.existing-project.instructions.md`*
*Previous step: `step-04-security-architecture-framework.prompt.md`*
*Next step: `step-06-documentation-strategy.prompt.md`*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial existing-projects Data Architecture Framework prompt, adapted from greenfield Phase 4 Step 04. Reframed from framework invention to framework reconciliation: the existing data reality is inventoried and codified first ([EXISTING-CODIFIED]) before the change surface is constrained, with the explicit reframing that for library-shaped subjects "data" is emitted artifacts (deployment records, evidence files, config, reports) covered with the same discipline as stores. Six procedure clusters: inventory & classification (with mandatory secrets/credentials/PII determination), ownership mapping onto preliminary M-NN, DA-NN constraint derivation with provenance and basis, Phase 3 schema integration (emission home + consumption paths; specifications authoritative, untenable cases routed as Channel 2 candidates), the brownfield-specific migration & compatibility posture (remain readable / migrate / version away, at specification level), and a routed gap register. Output pinned to the six-section shape (§1 Classification & Ownership; §2 Constraint Register; §3 Schema Integration; §4 Migration & Compatibility Posture; §5 scorecard contribution; §6 Handoff Notes) with the parallel-safe Step 04 encryption coordination pattern inherited from the greenfield variant. |
