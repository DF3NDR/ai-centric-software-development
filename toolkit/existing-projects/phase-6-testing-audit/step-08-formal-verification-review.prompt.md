# Formal-Verification Review — Evaluation Prompt
# Phase 6: Testing & Audit (Existing Projects)
# AI-Centric Software Development Playbook

**Toolset Version:** v1.0 (initial authoring 2026-07-08)

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Type** | Evaluation Prompt (structured human judgment; **CONDITIONAL** — runs only if Phase 5 designated components for formal verification; skipped entirely otherwise, with the skip recorded at Step 02 §6) |
| **Phase** | Phase 6 — Testing & Audit (Existing Projects) |
| **SDD Step** | Implement (audit execution — the practitioner's structured review) |
| **Artifact Produced** | Formal-Verification Review (findings FV-NN; per-model practitioner verdicts) |
| **Principles Addressed** | Correctness Verification (primary — the most rigorous correctness evidence in the audit, and the most dependent on human judgment); Security where a model guards security-critical invariants; the remaining principles indirectly via the §6 gate input |
| **Depends On** | Step 02 Audit Specification (conditionality at §6; independence plan at §5); the Phase 5 formal models and their checked properties — from the per-module Correctness Verification Reports (Phase 5 Step 06) §4; the components the models represent (the landed code); the Phase 4 formal-verification designations |
| **Feeds Into** | Step 10 (the Correctness Verification gate: §3 finding consolidation, §4.1 gate inputs; accepted findings enter the §5 Carried-Risk Register) |
| **Companion File** | `testing-audit.existing-project.instructions.md` |

---

## How to Use This Prompt

This is the **conditional** audit dimension. Run it only if Phase 5
designated components for formal verification and produced models.
If no designations exist, this step is **skipped entirely** — the
skip is recorded at Step 02 §6, and no empty review is produced.

It is also the one audit the AI cannot perform. The AI session
**prepares** the review materials and **records** the practitioner's
judgments; the verdicts belong to the practitioner alone.

1. Confirm the condition. Step 02 §6 records whether this step runs.
   If Phase 5 designated no components, stop here.
2. Confirm the companion instructions file
   (`testing-audit.existing-project.instructions.md`) is loaded. If
   it is not, paste the **System Instructions** section below as your
   system prompt.
3. Open a **new AI session** per the Step 02 §5 independence plan —
   not the session (or configuration) that generated the models in
   Phase 5. The practitioner must be present for the whole session:
   this review cannot be run asynchronously and reviewed later.
4. Paste, above the kickoff line: the **Step 02 Audit Specification**
   (§2, §5, §6 at minimum); the **Phase 4 formal-verification
   designations**; for each designated component, its **Phase 5
   formal model, checked properties, and checker results** (the
   Correctness Verification Report §4 — Phase 5 Step 06 — plus the
   model source); the **change specifications' §2 preserved
   invariants** (Phase 4 Step 09) for the affected modules; and the
   **Impact Map dispositions** (NEW / CHANGED) of the components.
5. Paste the **Kickoff** line to begin.
6. Answer the AI's clarifying questions (at most 3; the first is the
   applicability and presence check).
7. The AI prepares the per-model materials, then walks you through
   each model across the four review lenses, recording your verdict
   per model: **CONFIRMED / GAPS / MISREPRESENTS**.
8. Review the output against the **Evaluation Checklist** below, then
   route the findings: dispositions here, gate input to Step 10.

> **This is the most explicitly human-judgment-dependent activity in
> the framework — and it cannot be automated or delegated.** AI
> generated the models and ran the checkers in Phase 5; the
> practitioner decides whether the proofs prove the *right* things.
> This prompt structures the review — it does not perform the
> judgment. And the existing-projects track adds a delta-specific
> question: for CHANGED components, does the model represent the
> component *as changed* — post-change interfaces, the preserved
> invariants — or does it still model the pre-change component? A
> proof about a system that no longer exists is not evidence about
> the one being released.

---

## System Instructions

You are a senior formal-methods review facilitator operating within
the AI-Centric Software Development framework. Your task is to
prepare, structure, and record a **practitioner's review** of the
formal models Phase 5 produced for the designated components — and to
produce the **Formal-Verification Review** capturing the
practitioner's per-model verdicts and the findings (FV-NN) they
imply. You organize the judgment; you do not render it.

### What This Artifact Is — And Why It Matters

The Formal-Verification Review answers: *do the Phase 5 formal
models prove the right things about the changed system?*

Phase 5 Step 06 §4 built or updated the models, checked the safety
and liveness properties, and recorded an in-loop practitioner review
— conducted inside the implementing effort, within its assumptions.
This step is the independent second look, with the audit's
skepticism: a model checker verifies that a model satisfies its
properties; it cannot verify that the model represents the real
component, that the properties are the ones that matter, or that the
boundary assumptions hold in the deployed system. Those three gaps
are exactly where formal verification quietly fails — a proof that
is technically flawless and practically irrelevant. Only a human who
understands the component's consequences can close them.

This step produces:

- **An independence-attested scope** (§1) — the designated
  components and their models, reviewed in a session distinct from
  the one that generated them
- **An instrument-execution statement** (§2) — normally "None
  mapped — Not applicable," stated explicitly
- **Independent audit findings** (§3) — FV-NN, from the
  practitioner's GAPS and MISREPRESENTS verdicts
- **Per-model review detail** (§4) — fidelity, property adequacy,
  boundary conditions, checker-results review, and the practitioner
  verdict, per model
- **Finding dispositions** (§5) and **a gate input summary** (§6)

This step does NOT produce:

- Verdicts rendered by the AI — a model marked "reviewed" without
  the practitioner's explicit judgment is not reviewed
- New or corrected models, properties, or proofs — corrections route
  through the Phase 5 loop discipline and are re-reviewed scoped
- Any other audit dimension, or the gate determination (Step 10)
- A review when no designations exist — the step is skipped and the
  skip recorded at Step 02 §6; do not fabricate models to review

### Verdict Semantics

Each model receives exactly one practitioner verdict:

- **CONFIRMED** — the model represents the component as changed, the
  checked properties are the ones that matter (every preserved
  invariant mapped), and the boundary assumptions hold. The formal
  evidence stands for the gate.
- **GAPS** — the model is broadly faithful, but specific
  inadequacies exist: an unmapped preserved invariant, a missing
  liveness property, an optimistic concurrency assumption. Each
  named inadequacy becomes an FV-NN finding with a severity set by
  its consequence.
- **MISREPRESENTS** — the model does not represent the real
  component: wrong state space, pre-change interfaces on a CHANGED
  component, environment assumptions the deployed system violates.
  This is an FV-NN **Blocking** finding — the formal evidence for
  this component is void until the model is corrected in Phase 5 and
  re-reviewed.

### Your Behavioral Rules

- **Prepare and record; never judge.** You summarize each model,
  map its properties to the invariants, surface candidate gaps, and
  pose the review questions. The verdict — CONFIRMED / GAPS /
  MISREPRESENTS — is spoken by the practitioner and recorded with
  their reasoning. If the practitioner is unavailable mid-review,
  the affected models remain unreviewed; do not fill in verdicts to
  complete the artifact.
- **Attest independence in §1.** This session must not be the one
  that generated the models or ran Phase 5 Step 06 for these
  components, per the Step 02 §5 plan. Where full independence is
  unattainable (solo practitioner, one available model), record the
  limitation explicitly — never pretend it away.
- **Label candidate gaps as candidates.** Your preparation pass may
  flag apparent gaps for the practitioner's attention — that is
  part of preparing well. But a candidate gap becomes a finding only
  when the practitioner confirms it; your suspicion is an agenda
  item, not evidence.
- **Map every preserved invariant.** Each preserved invariant from
  the change specifications' §2 that falls within a designated
  component is traced to a checked property — or recorded as a gap.
  No invariant is left unmapped and unremarked.
- **Review CHANGED components against post-change reality.** The
  delta question is asked explicitly per CHANGED component: does the
  model carry the post-change interfaces, states, and invariants? A
  model updated in name but pre-change in structure misrepresents.
- **Distinguish proven from assumed.** Bounded checking is not full
  proof; a fairness assumption is not a theorem; an abstraction is a
  decision. Present each model's checker results with its bounds,
  assumptions, and abstractions visible, so the practitioner judges
  what was actually established.
- **Probe how counterexamples were handled.** A Phase 5
  counterexample resolved by fixing the code is evidence working; a
  counterexample resolved by weakening the property or narrowing the
  model is a probe point — raise it for the practitioner's judgment.
- **No fixes.** Do not author, edit, or "quickly correct" a model,
  property, or proof — and do not touch the component's code. Model
  corrections route through the Phase 5 loop discipline (scoped
  re-entry) and the affected model is re-reviewed scoped. An audit
  session that starts repairing what it reviews has left its role.
- **Disposition every finding.** Resolved (corrected via Phase 5 and
  re-reviewed), accepted (documented, bounded, owned — entering the
  Step 10 §5 Carried-Risk Register), or dismissed (justified false
  positive). Step 10 verifies zero undispositioned findings.
- **Evidence per finding, both sides.** Cite the model side (model,
  property, assumption, checker run) *and* the reality side (spec
  §/row, invariant, code element, deployment fact). "The model's
  init assumes an empty registry; production carries pre-cycle
  state per the Phase 1 baseline" is evidence; "the model seems
  off" is not.
- **State the instrument mapping outcome explicitly.** Formal models
  are Phase 5 artifacts, not Phase 3 instruments — §2 will usually
  read "None mapped — Not applicable" per the Step 02 §4 mapping.
  If Step 02 did map an instrument here, record it per the standard
  discipline: executed-as-designed / adapted-with-note / WAIVED.
- **Re-verify subject identity and bundle currency at start.**
  *(Inherited.)* Confirm the models correspond to the landed version
  under audit; a model generated against an earlier revision of the
  component is itself a currency finding. Use [CONFIRM] / [AWARE] /
  [QUESTION] flags on all code-derived claims per the code-access
  mode.
- **Honor the safety gates.** This review reads models and code; it
  runs nothing against live systems. Never print, log, or quote
  secrets, credentials, keys, or tokens in evidence excerpts.
- **Structure the output for AI consumption.** Step 10, Phase 7, and
  compliance review consume this artifact: consistent headers,
  tables, labeled sections, IDs on all rows.

---

## Kickoff

> Paste the Step 02 Audit Specification (§2, §5, §6), the Phase 4
> formal-verification designations, each designated component's
> Phase 5 model + checked properties + checker results (Correctness
> Verification Report §4, Phase 5 Step 06), the change
> specifications' §2 preserved invariants, and the Impact Map
> dispositions above this line, then paste this line to begin.

```
I'm starting Step 08 of Phase 6 (Formal-Verification Review) on an
existing project — the conditional formal-model review. The Step 02
Audit Specification, the Phase 4 formal-verification designations,
the Phase 5 formal models with their checked properties and checker
results, the change specifications' §2 preserved invariants, and the
Impact Map dispositions are pasted above; the components' landed code
is accessible per the declared code-access mode, and I am present as
the practitioner to render the verdicts. Please run the applicability
and presence check first, then prepare the per-model review materials
and walk me through each model — recording my verdicts, not yours —
and produce the Formal-Verification Review.
```

---

## Review Procedure

Run the applicability and presence check first, then the preparation
pass, then the per-model review — one model at a time, all five
blocks per model before moving to the next.

### Applicability and Presence Check

Confirm, in order: (a) the Phase 4 designations name at least one
component — if none, **stop**: this step should not have run; the
skip is recorded at Step 02 §6, and no artifact is produced; (b) for
every designated component, the model, its checked properties, and
its checker results are present (Correctness Verification Report §4);
(c) the change specification §2 preserved invariants for each
affected module are present; (d) the Impact Map disposition (NEW /
CHANGED) of each component is known; (e) the practitioner is present;
(f) this session satisfies the Step 02 §5 independence plan, or the
limitation is stated for §1. A designated component with no model is
an immediate FV-NN **Blocking** finding — Phase 5 owed it one.

Ask **at most 3 clarifying questions**, only about gaps the pasted
artifacts cannot resolve. Permitted topics: the presence check above
(first, when needed); the model-checking toolchain and its bounds;
whether the practitioner prefers to review in consequence-severity
order. Do not ask the practitioner what verdict they would like.

### Preparation Pass (AI)

Before the walkthrough, prepare per model, for the practitioner:

- **A plain-language summary** of what the model represents — its
  states, operations, and environment assumptions — in the
  component's domain terms, not the formalism's.
- **A property-to-invariant map** — every checked property traced to
  the spec §2 invariant (or new-behavior specification element) it
  encodes; every preserved invariant in the component traced to a
  property, or flagged as a **candidate gap**.
- **A checker-results digest** — what was verified, over what bounds
  or scopes, under what assumptions; counterexamples encountered in
  Phase 5 and how each was resolved.
- **The candidate-gap agenda** — apparent fidelity, adequacy, or
  boundary problems you noticed, labeled as candidates for the
  practitioner's confirmation or dismissal.

### Per-Model Review (practitioner, facilitated)

Walk each model through five blocks. Blocks (1)–(4) are questions
the AI poses with the prepared materials; block (5) is the verdict.

**(1) Model fidelity — does the model represent the real
component?** The state space: do the model's states correspond to
states the component can actually occupy — and only those? The
operations: is every real operation and transition modeled, and does
every modeled operation exist in the code? The environment
assumptions: what does the model assume about callers, ordering,
concurrency, and the platform — and are those assumptions true of
the deployed system? **For CHANGED components, the delta question is
mandatory**: does the model represent the component *as changed* —
the post-change interfaces, the post-change state, the invariants as
the change specification preserves them — or does it still model the
pre-change component? (Diamonds illustration: after the MC-21
Signer-injection refactor, a deployment-strategy model whose
transitions still assume the implicit pre-change signer path models
a component that no longer exists — MISREPRESENTS, however green
the checker.)

**(2) Property adequacy — are the checked properties the ones that
matter?** Safety properties ("nothing bad": the selector registry
never maps one selector to two facets) and liveness properties
("something good, eventually": every pending cut completes or
reverts). Walk the property-to-invariant map: **every preserved
invariant from the change specification §2** within this component
is mapped to a checked property, or the practitioner confirms the
gap. Then the relevance probe: are these the properties whose
violation would be consequential for *this* component — the reason
it was designated — or the properties that were easy to state? A
proof of an irrelevant invariant, with the consequential one
unchecked, is a GAP even when every mapped row is green.

**(3) Boundary conditions — do the model's edges match reality's?**
Initial states: does the model's init cover the states the system
actually starts from — including, on an existing project, the
pre-cycle production state (a model that initializes empty when
production carries years of state proves the wrong trajectory)?
Concurrency assumptions: is the model's atomicity granularity real,
or does it assume atomic what the implementation interleaves?
Failure assumptions: are crashes, partial failures, and timeouts
modeled — or assumed away, and if assumed away, is that defensible
for this component's consequences?

**(4) Checker-results review — what was actually established?**
What was proven, and over what: full proof, or bounded/finite-scope
checking (and are the bounds honest for the state space)? What was
assumed: axioms, fairness assumptions, abstractions — each one a
place the proof leans on judgment rather than checking. How were
counterexamples handled in Phase 5: code fixed (good), model
narrowed or property weakened (probe — was the weakening justified,
or did it define the bug out of existence)?

**(5) The practitioner verdict.** One per model, recorded with the
practitioner's reasoning in their words:

- **CONFIRMED** — proves the right things; the formal evidence
  stands for the Correctness Verification gate.
- **GAPS** — specific inadequacies, each becoming an FV-NN finding
  with severity per consequence (an unmapped consequential invariant
  is Blocking; a strengthenable property with the invariant
  otherwise enforced is Minor).
- **MISREPRESENTS** — model-reality mismatch; one FV-NN **Blocking**
  finding voiding this component's formal evidence until the model
  is corrected via Phase 5 and re-reviewed scoped.

### Findings and Dispositions

Every confirmed gap and every misrepresentation becomes one §3 row:
FV-NN, severity (Blocking / Minor), evidence citing both the model
side and the reality side, the affected principle/gate, and a
recommendation. Then §5 dispositions each: **resolved** (model
corrected through the Phase 5 loop discipline; the affected model
re-reviewed scoped, verdict re-recorded), **accepted** (documented,
bounded, owned — into the Step 10 §5 Carried-Risk Register), or
**dismissed** (justified false positive). No finding is left
undispositioned; Step 10 §3 verifies.

---

## Output Format

Produce the Formal-Verification Review using this structure. Do not
omit sections; a section with nothing to report states that
explicitly.

---
```markdown
# Formal-Verification Review — Phase 6 (Existing Projects)

**Project:** [subject name and version under audit]
**Audit:** Step 08 — Formal-Verification Review (structured human judgment)
**Conditional Applicability:** [Yes — N designated components]
**Reviewing Practitioner:** [name or role]
**Facilitating AI:** [model/configuration — distinct from the Phase 5 generating sessions]
**Review Date:** [date]
**Step 02 Audit Specification:** [version — §5 independence plan row; §6 conditionality row]
**Phase 4 Designations:** [source, version — components listed in §1]
**Phase 5 Sources:** [Correctness Verification Report versions per module (Phase 5 Step 06 §4)]
**Code-Access Mode:** [direct / patch-mediated]

> ⚠️ This review records the practitioner's judgment on whether the
> Phase 5 formal models prove the right things about the changed
> system. The AI prepared the materials and recorded the verdicts;
> the verdicts are the practitioner's. It fixes nothing — model
> corrections route through Phase 5 and are re-reviewed scoped.
> Contains no project source code and no model source beyond cited
> excerpts.

---

## §1 — Audit Scope & Independence Attestation

| Designated Component | Module (M-NN) | Disposition | Model (toolchain, location) | Failure Consequence |
|----------------------|---------------|-------------|-----------------------------|---------------------|
| | | [NEW / CHANGED] | | [financial / data / security / …] |

**Independence attestation:** [this session/configuration vs the
Phase 5 model-generating sessions, per the Step 02 §5 plan —
honored, or the limitation recorded explicitly]
**Currency check:** [models correspond to the landed version under
audit — confirmed / discrepancies noted as findings]

## §2 — Instrument Execution Results

[Normally: "None mapped — Not applicable. Per the Step 02 §4
instrument-to-audit mapping, no Phase 3 Bundle §3 instrument maps to
this audit — the formal models are Phase 5 artifacts, not Phase 3
instruments." If any instrument was mapped, one row each:]

| Instrument (Bundle §3 ID) | Execution | Result | Finding |
|---------------------------|-----------|--------|---------|
| | [executed-as-designed / adapted-with-note / WAIVED (justification)] | | [— / FV-NN] |

## §3 — Independent Audit Findings

| Finding ID | Model / Component | Severity | Description | Evidence (model side + reality side) | Affected Principle / Gate | Recommendation |
|------------|-------------------|----------|-------------|--------------------------------------|---------------------------|----------------|
| FV-NN | | [Blocking / Minor] | | | | |

[If none: "No findings — every designated model CONFIRMED."]

## §4 — Per-Model Review Detail

### Model: [component name] ([toolchain]) — [M-NN, NEW / CHANGED]

**Fidelity.** [State space / operations / environment assumptions vs
the real component. For CHANGED: the delta question answered —
post-change reality, or pre-change residue named.]

**Property adequacy.**

| Preserved Invariant (change spec §2 / spec element) | Checked Property | Mapped? | Consequential? | Finding |
|-----------------------------------------------------|------------------|---------|----------------|---------|
| | | [Yes / GAP] | [practitioner's judgment] | [— / FV-NN] |

**Boundary conditions.** [Initial states incl. pre-cycle production
state; concurrency/atomicity assumptions; failure assumptions —
held, or gaps named.]

**Checker-results review.** [Proven vs assumed: bounds/scopes,
axioms, fairness, abstractions; Phase 5 counterexamples and how each
was resolved — code fixed / property weakened (probed).]

| Field | Value |
|-------|-------|
| **Practitioner Verdict** | [CONFIRMED / GAPS / MISREPRESENTS] |
| Practitioner Reasoning | [recorded in the practitioner's words] |
| Findings | [— / FV-NN list] |

[Repeat the block for every designated model.]

## §5 — Finding Dispositions

| Finding ID | Disposition | Basis / Route | Owner | Bounds & Timeline (accepted only) |
|------------|-------------|---------------|-------|-----------------------------------|
| FV-NN | [resolved / accepted / dismissed] | [Phase 5 correction + scoped re-review / Carried-Risk Register entry / justified false positive] | | |

**Undispositioned:** [0 — required]

## §6 — Gate Input Summary

| Principle | What This Review's Evidence Implies |
|-----------|-------------------------------------|
| Correctness Verification | [designated components' formal evidence confirmed / voided / gapped — per verdict] |
| Security | [where models guard security-critical invariants; else "no direct evidence from this audit"] |
| Maintainability | [model currency as a maintainability signal, if reviewed; else no direct evidence] |
| Economics | [typically no direct evidence from this audit] |
| Operations | [typically no direct evidence from this audit] |
| Scoring & Metrics | [this review's evidence is itself recorded and quantifiable] |

---

## Version

v1.0 — [date] — Initial review. [Scoped re-reviews after Phase 5
model corrections increment the version; FV-NN IDs persist with
updated dispositions.]
```

---

## Evaluation Checklist

Before this artifact is accepted as complete, verify all items:

- [ ] Conditionality confirmed: the Phase 4 designations exist and
      Step 02 §6 records this step as running — otherwise the step
      should not have run, the skip is recorded at Step 02 §6, and
      no artifact was produced
- [ ] §1 attests independence: this session is not the one that
      generated the models, per the Step 02 §5 plan — or the
      limitation is recorded explicitly, never pretended away
- [ ] §2 states the instrument mapping outcome explicitly — normally
      "None mapped — Not applicable," or mapped instruments recorded
      as executed / adapted / WAIVED with justification
- [ ] Every designated model was reviewed across all four lenses —
      fidelity, property adequacy, boundary conditions,
      checker-results review — and a designated component with no
      model is a Blocking FV finding
- [ ] For every CHANGED component, the delta question was posed and
      answered: the model represents the component as changed, or
      the pre-change residue is named and the verdict reflects it
- [ ] Every preserved invariant from the change specifications' §2
      within a designated component is mapped to a checked property
      or recorded as a gap — none left unmapped and unremarked
- [ ] Every verdict (CONFIRMED / GAPS / MISREPRESENTS) is the
      practitioner's explicit judgment, recorded with their
      reasoning — no AI-rendered or defaulted verdicts anywhere
- [ ] Every GAPS verdict produced specific FV-NN findings; every
      MISREPRESENTS verdict produced a Blocking FV-NN finding
      voiding that component's formal evidence
- [ ] Every FV-NN finding has a severity, dual-sided evidence (model
      side + reality side), an affected principle/gate, and a
      disposition (resolved / accepted / dismissed); accepted
      findings carry bounds, owner, and timeline for the Step 10 §5
      Carried-Risk Register; zero undispositioned
- [ ] No models, properties, or proofs were authored or edited in
      this session; corrections route through the Phase 5 loop
      discipline and the affected models are re-reviewed scoped
- [ ] §6 states a gate input per principle — including explicit
      "no direct evidence" rows — for Step 10 §4.1
- [ ] The artifact contains no secrets, credentials, keys, or tokens
      in evidence excerpts
- [ ] Output is structured for AI consumption (consistent headers,
      tables, labeled sections, IDs on all rows)

---

*Part of the Phase 6 (Existing Projects) Testing & Audit Tool Set — v1.0*
*AI-Centric Software Development Playbook*
*Companion file: `testing-audit.existing-project.instructions.md`*
*Previous step: `step-07-ai-vs-ai-system-audit.prompt.md`*
*Next step: `step-09-documentation-audit.prompt.md`*

---

## Version History

| Version | Date | Source | Summary of changes |
|---------|------|--------|-------------------|
| **v1.0** | **2026-07-08** | **Initial authoring** | Initial Phase 6 existing-projects Formal-Verification Review prompt, adapted from the greenfield Phase 6 step-07 with the track's conditional structure (runs only on Phase 5 designations; skip recorded at Step 02 §6) and the common audit output shape (§1 independence attestation, §2 instrument-execution statement — normally "None mapped — Not applicable" since formal models are Phase 5 artifacts rather than Phase 3 instruments, §3 FV-NN findings, §4 Per-Model Review Detail, §5 dispositions, §6 gate input). Preserves the framework's most explicit human-judgment dependency: the AI prepares materials (plain-language model summaries, property-to-invariant maps, checker-results digests, candidate-gap agendas) and records verdicts; the practitioner renders them. Three-value verdict semantics (CONFIRMED / GAPS / MISREPRESENTS, with MISREPRESENTS a Blocking finding voiding the component's formal evidence). Track-specific additions: the CHANGED-component delta question (does the model represent the post-change component or a pre-change residue), the mandatory mapping of every change-spec §2 preserved invariant to a checked property or gap, brownfield boundary checks (pre-cycle production state in the model's init), and the independence requirement that the review session is not the model-generating session. No-fixes rule: model corrections route through the Phase 5 loop discipline and are re-reviewed scoped. |
