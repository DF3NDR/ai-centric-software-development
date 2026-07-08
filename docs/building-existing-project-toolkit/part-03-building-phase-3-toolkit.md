# Building a Phase 3 Toolkit for Existing Projects

This is the third article in the series in which we implement our [AI-Centric Software Development Playbook](https://github.com/df3ndr/ai-centric-software-development) and develop toolkits by applying them to our real [Diamonds node module project](https://github.com/diamondslab/diamonds) — refining the results through a forging process of real-world usage.

The first two articles covered the Phase 1 toolkit (the "what do we have, where are we, and what must change?" variant of information gathering) and the Phase 2 toolkit (the "given what we have, what do we improve in what order?" variant). Phase 1 surfaced 22 Must-Changes about Diamonds; Phase 2 chose a mechanism for each, sequenced them into tiers, and costed the plan against a capacity envelope. The output of Phase 2 was an Improvement Plan.

This article covers the sibling work: the **Phase 3 toolkit for existing projects** — the "how do we specify the chosen mechanisms in design-level detail?" variant. Phase 2 decided *which* approach to take for each change; Phase 3 produces the design specifications that let Phase 5 build those mechanisms without re-litigating decisions. Where Phase 2 output was uniform (a mechanism decision per Must-Change), Phase 3 output is heterogeneous — a formal interface contract, a refactor specification, a documentation information architecture, an evidence schema, an observability touchpoint design, a set of verification instruments. Six different artifact shapes, one toolkit.

The article covers three arcs of a single working stream, mirroring the prior articles' structure:

1. **Building** the toolkit — authoring the instructions file and seven step prompts (step-00 through step-06) that make up a complete Phase 3 Existing Projects toolset, including a single Step 03 prompt that dispatches to six artifact-type sub-templates
2. **Applying** it to Diamonds — running the full Phase 3 cycle on the Phase 2 Improvement Plan, producing six design specifications plus coordination and verification strategy, and capturing observations along the way
3. **Refining** it — reviewing observations end-of-phase, producing a v1.1 revision of the toolkit, and routing one cluster upstream to a Phase 2 v1.2 revision through the toolkit's Channel 1 feedback mechanism

The artifacts live in the `ai-centric-software-development` repository under `toolkit/existing-projects/phase-3-technical-analysis/`. This article describes the process, not the artifacts themselves — the files are available to pick up and use directly.

A note before we start: the Phase 3 toolkit is at v1.1, having gone through one complete dogfooding cycle. As with the prior phases, what's shipping is what works now, not what's finished.

---

## Section 1: Building the Toolkit

Phase 3 differs from Phase 2 in a way that shaped the toolkit from the start: Phase 2 was decision-heavy, Phase 3 is **specification-heavy**. Phase 2 chose among candidate mechanisms; the output of a Phase 2 step was a decision with rationale. Phase 3 takes each chosen mechanism and specifies it at the level of detail Phase 5 implementation can build against — an interface signature, a refactor's before/after, a doc set's layer structure and cross-link graph, a schema's field-by-field shape. The output of a Phase 3 step is an artifact specification, not a choice. That shift drives nearly every structural decision.

### Three shifts from Phase 2 that shape Phase 3

Just as the Phase 2 toolkit opened with three shifts that distinguished it from Phase 1, the Phase 3 toolkit opens with three shifts that distinguish it from Phase 2:

**From decisions to specifications.** Phase 2 answered "which mechanism?" Phase 3 answers "specify that mechanism precisely enough that Phase 5 doesn't re-decide." The Phase 2 mechanism choice for MC-04 was "a formal `IDeploymentStrategy` interface plus a conformance test suite." Phase 3's job is to actually specify the interface — its 15 lifecycle methods across five phases, the pre/main/post hook structure, the JSDoc security-boundary conventions, the 17-test conformance scope. The decision was the input; the specification is the output.

**From one artifact shape to six.** Every Phase 2 step produced the same shape of output (a mechanism decision, a sequencing tier, a cost row). Phase 3's design briefs come in fundamentally different shapes: a *contract* (formal interface), a *refactor* (a change to existing code preserving an invariant), an *information architecture* (documentation structure), a *schema* (an evidence artifact's layout), *observability touchpoints* (where instrumentation inserts), and *verification artifacts* (test suites, proxy-reader question sets, auditor-persona prompts). We could have authored six separate step files. We chose a single unified Step 03 prompt that dispatches to six sub-templates. This is the most distinctive structural decision of the Phase 3 toolkit, and it gets its own subsection below.

**From a fresh scorecard to an inherited one.** Phase 1 and Phase 2 each ran a principle scorecard baselined for the phase. Phase 3 does not re-baseline. It inherits Phase 2's weights (Security 1.5×, Maintainability 1.5×, Correctness Verification 1.5×, Economics/Operations/Scoring 1.0×) and its frame, and each design specification contributes a per-artifact scorecard that aggregates up. A phase that re-weights would be second-guessing Phase 2; a phase that ignores scoring would drop the discipline. Phase 3 threads between: same weights, per-artifact contributions, and a synthesis-time refresh that either resolves or carries forward the Phase 2 CONDITIONALs.

These three shifts became the opening of the toolkit's instructions file, and they govern how every step prompt frames its work.

### The unified Step 03 and its six sub-templates

The decision not to author six separate step files deserves explicit treatment, because it was the authoring choice most likely to have gone another way.

The Phase 2 Improvement Plan named six design briefs for Diamonds: four primary (MC-04 extension contract, MC-21 Signer-injection refactor, MC-07 documentation information architecture, MC-12 release-evidence schema) and two supplementary (observability touchpoints, verification-artifact specifications). Each is a different artifact *type*. A naive toolkit would give each type its own step prompt — `step-03a-contract`, `step-03b-refactor`, and so on. That structure breaks down immediately: a project's Phase 2 plan might have three contracts and no schema, or one of each, or five refactors. The number and mix of briefs is a per-project variable, not a fixed sequence.

So Step 03 is a single prompt with a common intake (confirm the brief, confirm its artifact type, carry over any Step 01 gaps), then a dispatch to one of seven sub-templates — six named types plus an "Other (declared shape)" escape hatch — and a common synthesis (per-artifact scorecard, Phase 2 invalidation check, Phase 5 implementability check, forward-handoff notes, cross-brief references). The practitioner runs Step 03 once per brief. The sub-templates are:

| Sub-template | For briefs specifying… |
|--------------|------------------------|
| A — Contract | a formal interface: method set, signatures, security boundaries, conformance scope, worked reference implementation |
| B — Refactor | a change to existing code that must preserve an invariant: before/after, migration surface, the preserved invariant |
| C — IA (Information Architecture) | documentation structure: layer structure, doc-set composition, cross-link graph, style guide, per-doc scope |
| D — Schema | an evidence or data artifact's layout: file set, manifest, field-by-field shape, validation |
| E — Observability Touchpoints | where instrumentation inserts: touchpoint inventory, what's observed, alerting posture, watch-trigger integration |
| F — Verification Artifacts | test suites, proxy-reader question sets, auditor-persona prompts, conformance harnesses — *instruments, not descriptions* |

The unified structure is what makes Phase 3 handle an arbitrary brief mix. It's also what makes Step 03 the longest prompt in any of the three toolkits — the common scaffolding plus seven sub-templates is a large file. We judged the length worth it: one large, well-organized prompt beats six smaller prompts that share 60% of their content and drift apart over revisions.

### The two Phase 3 → Phase 2 feedback channels

Phase 2's dogfood produced the first inter-phase feedback loop (a Phase 2 observation that traced to a Phase 1 toolkit gap, landing Phase 1 v1.3). We designed the Phase 3 toolkit to make that loop first-class from v1.0, with *two* structural channels rather than one:

- **Channel 1 (upstream toolkit gaps)** — Step 01's Validation Gap Register carries a two-scope split, exactly as Phase 2 v1.1's did: Phase 3 local gaps versus upstream Phase 2 toolkit gaps. When Phase 3 work reveals that the Phase 2 *toolkit* was structurally incomplete, the gap queues for a Phase 2 toolkit revision in a separate session.
- **Channel 2 (Phase 2 run amendment)** — Step 06's synthesis includes an Amendment Package that fires when Phase 3 design work reveals a specific Phase 2 *mechanism choice* is untenable. This is distinct from Channel 1: Channel 1 fixes the toolkit; Channel 2 amends the Improvement Plan for this run.

Building both channels in from v1.0 was a direct application of the Phase 2 lesson. We'll see in Section 4 that Channel 1 fired and Channel 2 did not — and that the difference between them is precisely the distinction the design anticipated.

### What we built

The v1.0 toolkit for Phase 3 ended up as ten files:

| File | Role |
|------|------|
| `design-technical-analysis.existing-project.instructions.md` | Load-once context — three shifts, six artifact types, the two feedback channels, inherited scorecard discipline, behavioral rules |
| `step-00-building-block-discovery.prompt.md` | AI capability inventory (living document), inherited from Phase 2 |
| `step-01-phase-2-input-validation.prompt.md` | Validates Phase 2 understanding; Validation Gap Register with the two-scope split (Channel 1) |
| `step-02-design-brief-triage.prompt.md` | Classifies each brief by artifact type, dependencies, and Step 03 execution order |
| `step-03-per-artifact-design-specification.prompt.md` | The unified prompt with six sub-templates; run once per brief |
| `step-04-inter-artifact-coordination.prompt.md` | Coordination Register — cross-artifact references, shared decisions, landing cohorts, inter-brief conflicts |
| `step-05-verification-strategy.prompt.md` | Refines Step 03 verification specs into Phase 6-executable instruments |
| `step-06-design-specification-synthesis.prompt.md` | Capstone — Design Specification Bundle, scorecard refresh, amendment package (Channel 2) |
| `README.md` | Navigation, sequence, scorecard/gate, dependency map, version history |
| `dogfooding-observations.md` | Captured during the run; the Phase 3 equivalent of the prior phases' file |

The parallel to the Phase 1 and Phase 2 toolkits is deliberate: same SDD cycle, same six principles, same phase-gate discipline, same dogfooding protocol. What changes is that Step 03 is heterogeneous, the scorecard is inherited rather than baselined, and there are two feedback channels rather than one.

### Inherited discipline from Phase 2 v1.1

As with Phase 2, the most consequential authoring choice was not a feature — it was *to author Phase 3 v1.0 to the matured conventions of the phase before it.* Phase 2 v1.0 had been authored to Phase 1 v1.2's disciplines and surfaced only 7 observations as a result. We authored Phase 3 v1.0 to Phase 2 v1.1's disciplines from the start: the living-document Building Block Discovery step, the two-scope validation split, the behavioral-rules section, scorecard rigor with target distributions, per-file Version History, the same cross-reference conventions.

We'll see in Section 2 that this produced a different observation count than the compounding-inheritance thesis alone would predict — because Phase 3 also introduced genuinely new structural surface (six artifact types, two channels, cross-brief coordination, a multi-session run) that no amount of inheritance could pre-empt.

### Choices we made that others might not

**We used one Step 03 prompt with sub-templates rather than one prompt per artifact type.** Covered above. The alternative — a prompt per type — is more discoverable ("I have a schema brief, I open the schema prompt") but can't handle an arbitrary brief mix without the practitioner assembling a per-project sequence by hand. We chose the unified prompt and paid for it in file length.

**We made Step 02 a triage step rather than folding triage into Step 01.** An alternative would have Step 01's validation also classify the briefs by type and order. We split them because validation is a confirmation activity (is our understanding of Phase 2 correct?) and triage is a planning activity (what type is each brief, what depends on what, in what order do we run Step 03?). Conflating them muddies both.

**We inherited the scorecard rather than re-baselining it.** An alternative would run a fresh Phase 3 scorecard. We rejected that because Phase 2 already set the weights against this cycle's objective, and re-weighting in Phase 3 would either duplicate or silently contradict Phase 2. Phase 3 contributes per-artifact scores into the inherited frame and refreshes at synthesis — nothing more.

**We built both feedback channels into v1.0.** An alternative would ship Channel 1 (the Phase 2 lesson) and add Channel 2 only if a run demonstrated the need. We built both because the distinction — toolkit gap versus run-plan amendment — is structural, and a design specification that invalidates a Phase 2 mechanism choice has nowhere clean to go without Channel 2. Building it cost little; not having it would have forced an awkward workaround the first time a brief invalidated a mechanism.

None of these is unambiguously correct. Each was made deliberately and documented in the toolkit files.

---

## Section 2: Applying It — The Diamonds Phase 3 Run

With the toolkit drafted, we ran it on Diamonds — continuing the application from Phase 2. The Phase 2 Improvement Plan was the input. The intent: produce the design specifications that would drive Phase 5 implementation of the library's v2.0.

The same project characteristics carried forward: solo maintainer, pre-production, zero external adopters. But Phase 3 introduced an operational difference from the prior runs — it spanned **two sessions** with a handoff between them, which turned out to matter (Section 5).

### The run itself, across two sessions

Session 1 ran step-00 through the first three Step 03 briefs and paused, producing a handoff document. Session 2 resumed from that handoff, completed the remaining three briefs, and ran Steps 04 through 06 plus the end-of-phase review. The artifacts produced were:

- **Step 00 — Building Block Discovery**: hybrid code-access mode with explicit flags; noted the intermittent behavior of one code-search tool (which became a revision item)
- **Step 01 — Phase 2 Input Validation**: confirmed the Phase 2 plan and objective; surfaced two upstream-toolkit validation gaps (VG-P3-U-01, VG-P3-U-02) that routed to Channel 1
- **Step 02 — Design Brief Triage**: six briefs classified across the artifact types; Step 03 execution order fixed as MC-04 → MC-21 → MC-12 → MC-07 → Observability → Verification
- **Step 03 — six design specifications**: MC-04 (Contract), MC-21 (Refactor), MC-12 (Schema) in Session 1; MC-07 (IA), Observability, Verification in Session 2. Each produced a 6-PASS per-artifact scorecard
- **Step 04 — Inter-Artifact Coordination**: a Coordination Register with no inter-brief conflicts; shared artifacts assigned single owners (the migration doc co-authored across MC-04 and MC-21; the logging strategy shared by MC-04 and Observability); the v2.0 Coordinated Breaking-Change cohort (MC-05 + MC-04 + MC-21 + MC-22 + MC-13) recorded canonically
- **Step 05 — Verification Strategy**: the four verification instruments refined to Phase 6-executable form — a 17-case conformance suite, a byte-identity refactor test, a five-question proxy-reader set with answer keys, and a four-spoke auditor-persona prompt with a seeded-discrepancy check
- **Step 06 — Design Specification Bundle**: the capstone. The phase-gate scorecard refresh reported **6 PASS / 0 CONDITIONAL / 0 FAIL**, resolving both Phase 2 CONDITIONALs — Operations (the observability brief designed baseline touchpoints without silently elevating the weight) and Correctness Verification (the verification brief plus Step 05 produced executable instruments, not descriptions). The Channel 2 amendment package was empty

### What the run produced that we didn't expect

The most consequential moment of the Phase 3 run was not in any design brief — it surfaced during the very first step of Session 2, when the toolkit's currency re-verification discipline caught something the prior phases' equivalent never had.

The Phase 2 Improvement Plan was written against Diamonds v1.3.2 and assumed the productization arc would ship as v2.0. Between Phase 2 and the resumption of Phase 3, the library had advanced to **v1.5.0** — and, more consequentially, a *separate* productization effort had shipped a mechanism the Phase 2 plan had scheduled for the future v2.0 release: the publish workflow (with OIDC trusted publishing and provenance) that MC-12's release-evidence schema was designed to extend. A Phase-2-scheduled dependency had shipped early, via a parallel track, while the design cycle was mid-flight.

This is the Phase 3 analog to Phase 2's cost-model surprise — a discovery that the toolkit's own discipline surfaced, and that reshaped how we thought about the phase. The naive reading is alarming: "the plan is out of date, an amendment is required." The correct reading, which the currency check forced us to reason through, is subtler. A dependency arriving early does not *invalidate* a mechanism choice — it *de-risks* one. MC-12's design (a six-file evidence bundle with a four-spoke auditor flow) was still correct and still necessary; the shipped provenance-only flow was exactly the substrate MC-12 was designed to build on, and MC-12's own rejected-alternatives had already noted that provenance alone was insufficient for the auditor-reproducibility goal. So the right move was a **grounding update, not a Channel 2 amendment**: reference the now-real workflow concretely instead of treating it as unbuilt, and leave the mechanism unchanged.

That distinction — *grounding update versus amendment when reality moves under a plan mid-cycle* — is the single most useful synthesis of the run. It wouldn't have surfaced from any design brief. It emerged from the §7 currency-re-verification discipline the toolkit inherited from Phase 2, applied at a step start, catching a drift that the discipline's original framing ("has a patch shipped?") only partly anticipated. The toolkit caught the event; the toolkit's *framing* of the event needed sharpening. That became a revision item (Section 3).

### Observations captured during the run

We followed the same protocol: capture observations about the toolkit as we worked, act on none of them until end-of-phase. By the end of the run we had **14 observations** (P3-Obs-01 through P3-Obs-14).

Fourteen sits between Phase 1's 26 and Phase 2's 7, and the position is informative. The compounding-inheritance thesis from the Phase 2 article predicted a low count — Phase 3 v1.0 inherited Phase 2 v1.1's matured disciplines, so the structural-discovery work was largely done. And indeed the inherited disciplines produced few observations. But Phase 3 introduced genuinely new structural surface that inheritance could not pre-empt: six heterogeneous artifact types, two feedback channels, cross-brief coordination, a multi-session handoff, and the concurrent-release currency event. The new surface is where most of the 14 clustered.

The lesson refines the inheritance thesis rather than contradicting it: **inheritance lowers the floor, but genuinely new structural surface raises it back.** A phase that is mostly a variation on its predecessor (as Phase 2 was on Phase 1) surfaces few observations. A phase that introduces new structural machinery (as Phase 3 did) surfaces more — not because the toolkit is worse, but because there is more genuinely new surface to stress.

Some observations were tooling-reliability findings (a code-search tool that worked early then returned an authorization error mid-session — the "present but not consistently usable" pattern). Some validated the design (the two-scope validation split cleanly caught the two upstream-toolkit gaps). Some were positive calibrations (a well-specified verification brief — shape plus a few worked examples — made Step 05 near-mechanical). Two of the fourteen routed upstream to Phase 2, and one recorded a downstream citation drift; those three became the Channel 1 cluster (Section 4).

### Choices we made during the run that others might not

**We ran Phase 3 across two sessions rather than one.** The prior runs were single-session. Phase 3's six briefs plus three synthesis steps were too much for one session without fatigue degrading the capstone, so we split after the first three briefs and wrote a handoff. The trade-off is that a session boundary is a context-loss risk; we mitigated it with an explicit handoff document and a currency re-check at the resume point — which is exactly the check that caught the crossover.

**We designed the observability brief at baseline Operations weight, resisting the temptation to "do it properly."** Phase 2 had explicitly deprioritized Operations to 1.0× for this cycle, with next-cycle re-weighting planned. The observability brief could easily have designed alerting, dashboards, and paging infrastructure — and silently elevated Operations to 1.5× in the process. We held the line: the brief designs touchpoints and names severities but defers the alerting infrastructure to a future cycle, keeping Operations at its Phase 2 weight. Silent re-weighting inside a design brief would have corrupted the inherited scorecard.

**We required the verification brief to produce instruments, not descriptions — but deferred full enumeration to Step 05.** The verification brief specified each instrument as a shape plus two or three worked examples (one real test case, one real proxy-reader question, the auditor-prompt skeleton), and Step 05 enumerated the rest. The alternative extremes — full enumeration in the brief (duplicating Step 05) or bare descriptions (leaving Correctness Verification CONDITIONAL) — were both worse. The shape-plus-examples middle is what let Step 06 resolve the CV CONDITIONAL cleanly.

---

## Section 3: Refining It — The v1.1 Revision

At the end of the Diamonds Phase 3 run we had two things: a complete Design Specification Bundle ready for Phase 4 (the point of the exercise), and 14 observations about the toolkit itself (the purpose of the dogfood).

### The review process

We used the same three-pass review as the prior phases:

1. **Pass 1 — Cluster.** The 14 observations reduced to **8 clusters** (labeled C1 through C8).
2. **Pass 2 — Per-cluster decision.** Accept / Accept-with-refinement / Defer / Reject, plus a routing decision (Phase 3 v1.1 / upstream Phase 2 v1.2 / cross-cutting). We accepted all eight; two were Accept-with-refinement (bundling related edits). One cluster (C5) routed upstream to Phase 2 v1.2 rather than landing in Phase 3.
3. **Pass 3 — Revise.** Produce the v1.1 files, and (this time) the upstream v1.2 files as well.

The cluster breakdown:

| Cluster | Source observations | Scope | Decision |
|---------|--------------------|-------|----------|
| C1 — Tool-reliability precision | P3-Obs-06, P3-Obs-08 | Phase 3 v1.1 (step-00) | Accept |
| C2 — Step-00 wording / solo-fit | P3-Obs-02, P3-Obs-03 | Phase 3 v1.1 (step-00) | Accept with refinement |
| C3 — Skill discoverability | P3-Obs-01 | Phase 3 v1.1 (instructions, README) | Accept |
| C4 — Sub-template question completeness | P3-Obs-07 | Phase 3 v1.1 (step-03) | Accept |
| C5 — Upstream Phase 2 toolkit gaps | P3-Obs-04, P3-Obs-05, P3-Obs-09 | **Phase 2 v1.2** (not Phase 3) | Accept, routed upstream |
| C6 — Concurrent-release currency event | P3-Obs-10, P3-Obs-11 | Phase 3 v1.1 (step-01, instructions) | Accept |
| C7 — Cross-artifact taxonomy & single-source | P3-Obs-12, P3-Obs-13 | Phase 3 v1.1 (step-03, step-04) | Accept with refinement |
| C8 — Positive calibration | P3-Obs-14 | Phase 3 v1.1 (step-05) | Accept |

The Accept-with-refinement rate of 2 out of 8 is consistent with the roughly-one-in-several ratio the prior phases saw — enough scrutiny to refine, not so much as to suggest we were accepting under-developed observations.

### The revision itself

Phase 3 v1.1 changed 7 of the 10 files. Three (step-02, step-06, and the dogfooding-observations template) were unchanged — no cluster affected them, and we held to the Phase 2 discipline of revising only files a specific cluster justifies. The changes:

- **Instructions file**: added the AI-Centric Playbook Skill reference to the Purpose section (C3); added a "concurrent-release / dependency-shipped-early currency event" to the currency re-verification behavioral rule, with the grounding-update-versus-amendment decision rule the Diamonds crossover forced us to reason through (C6).
- **README**: added the companion-Skill note (C3).
- **Step 00**: distinguished "tool present" from "tool consistently usable," with a reliability posture recorded per capability and the "worked earlier, failed later" pattern named explicitly (C1); clarified that project-knowledge-with-docs and library-documentation-lookup cover different gaps rather than being substitutes (C2); marked the cross-repo-search rows optional for single-repo / solo sessions (C2).
- **Step 01**: extended the currency category to check whether a Phase-2-scheduled mechanism shipped early via a parallel track, applying the same grounding-versus-amendment rule (C6).
- **Step 03**: added a "purpose / lifecycle role" question to the Contract sub-template's conformance section, asked *before* harness location, with a generalized "purpose before mechanism" pattern note for the other sub-templates (C4); added a code-observable-versus-process classification to the observability sub-template's watch-trigger integration, so process-only triggers map to "no touchpoint (watched via process)" rather than an invented one (C7); added a single-source-of-truth rule for any artifact referenced by three or more briefs (C7).
- **Step 04**: made single-owner assignment mandatory for any 3+-brief artifact — the receiving end of the step-03 single-source rule (C7).
- **Step 05**: added an "upstream shape makes Step 05 mechanical" calibration note — a well-specified verification brief (shape plus worked examples) turns Step 05 into enumeration rather than design (C8).

Every revised file carries a v1.1 Version History entry tagging the source cluster and observations, so a practitioner picking up a single file understands its evolution without reading this article.

### Choices we made about refinement that others might not

**We routed Cluster C5 upstream to Phase 2 v1.2 rather than absorbing it.** Two of the three C5 items were the same class of finding the Phase 2 article described routing to Phase 1 v1.3 — genuine gaps in the *upstream toolkit's* instrumentation, surfaced only when the downstream phase asked questions the upstream phase didn't anticipate. The Phase 2 Step 03 prompt had listed a Must-Change as multi-mechanism but provided no detail slot for it, and its NTI (Nice-to-Improve) references lacked cycle-versus-future tagging. The durable fix lives in the Phase 2 toolkit, not a Phase 3 workaround.

**We authored the upstream revision in the same arc, rather than only queuing it.** The Phase 2 article routed its upstream cluster to Phase 1 v1.3 and authored it. We did the same for Phase 3's upstream cluster, landing Phase 2 v1.2 in the same working stream (Section 4). Batching the two revisions together preserved voice consistency across the two toolkits — the same lesson the prior article drew about cross-toolkit sessions.

**We did not edit the generic dogfooding-observations template for the positive-calibration cluster.** Cluster C8's finding (well-specified upstream shape makes Step 05 mechanical) is genuinely useful, but it is *specific to this run*. We landed the reusable form of it in step-05 (where it guides future runs) and kept the run-specific finding in the populated observation instance — not in the generic template, which stays project-agnostic. Putting a Diamonds-specific calibration into a reusable template would have been a category error.

---

## Section 4: The Phase 3 → Phase 2 Feedback Channel Firing

The Phase 2 article documented the framework's first inter-phase feedback loop firing — a Phase 2 observation that traced to a Phase 1 toolkit gap and landed Phase 1 v1.3. Phase 3's run fired the same kind of loop, through the Channel 1 mechanism the Phase 3 toolkit had built in from v1.0. This time we can say something the Phase 2 article could not: the channel we designed *specifically to catch this* is the channel that caught it.

### What surfaced

Phase 3's Step 01 validation produced two upstream-toolkit gaps, and a third finding surfaced later during Step 04's coordination work:

- **VG-P3-U-01**: the Phase 2 Step 03 prompt listed one Must-Change (MC-21) as multi-mechanism in its triage section but had no corresponding detail block for it in the output — the prompt's template allowed a triaged MC to have no specification.
- **VG-P3-U-02**: Phase 2's mechanism drafts referenced Nice-to-Improve items in constraint chains without tagging whether each was this-cycle or future-cycle work, leaving Phase 3 to resolve the ambiguity by inference.
- **The cohort-citation drift**: a Session 1 design brief cited the coordinated breaking-change cohort against the wrong Plan section and dropped a member from the list — a downstream symptom of the Phase 2 plan not stating the cohort once, canonically.

None of these is a Phase 3 problem in the sense of something Phase 3 must fix within its own steps. They are gaps in the Phase 2 *toolkit's* instrumentation, surfaced only because Phase 3 consumed the Phase 2 plan and tripped over the missing detail. The two-scope split in Step 01 forced the classification: these are upstream-toolkit gaps, they don't block Phase 3, and they queue for a Phase 2 toolkit revision.

### Channel 1 fired; Channel 2 did not — and the difference is the design

The Phase 3 toolkit built two channels precisely because the two kinds of feedback are structurally different, and the Diamonds run demonstrated the distinction cleanly:

- **Channel 1 fired.** The upstream-toolkit gaps (VG-P3-U-01/02 and the cohort-citation drift) are gaps in the Phase 2 *toolkit*. They route to a Phase 2 toolkit revision. They do not touch the Diamonds Improvement Plan.
- **Channel 2 did not fire.** No Phase 3 design brief invalidated a Phase 2 *mechanism choice* for this run. Even the concurrent-release crossover — the run's most consequential surprise — resolved to a grounding update, not an amendment, because the shipped reality de-risked MC-12 rather than invalidating it. The Step 06 amendment package was empty.

That both channels behaved as designed — one firing for a toolkit gap, the other correctly staying silent for a run that had no mechanism invalidation — is the strongest validation the run produced that the two-channel design was the right structure. A single-channel toolkit would have had to force the upstream-toolkit gaps and the (absent) mechanism amendment through the same mechanism, muddying both.

### Phase 2 v1.2 — what landed

Phase 2 v1.2 was a small, focused revision affecting one file: `step-03-mechanism-decisions.prompt.md` (already at v1.1 from the Phase 2 dogfood). Three completeness gates:

- A **§1.1↔§2 completeness check** — every Must-Change triaged as multi-mechanism must have a corresponding detail block, enforced in a new behavioral rule, a Phase D comprehensiveness question, an output-format note, and the evaluation checklist (VG-P3-U-01).
- **Per-NTI cycle-tagging** — each Nice-to-Improve item in a constraint chain is tagged this-cycle or future-cycle, in the mechanism-draft template and the output format (VG-P3-U-02).
- A **canonical cohort statement** — any coordinated breaking-change cohort is stated once, in one section, with a stable anchor and full membership, so downstream briefs cite one definition rather than several drifting copies (the cohort-citation drift).

The revision is small in line count but structurally consequential in the same way Phase 1 v1.3 was: every future Phase 2 run captures these completeness properties from the start, so every future Phase 3 consumes a plan that no longer has the gaps. The gaps close once, upstream, and stay closed.

### The loop, now two phases deep

Phase 1's dogfood produced Phase 1 v1.1 (within-phase). Phase 2's dogfood produced Phase 2 v1.1 (within-phase) and Phase 1 v1.3 (inter-phase). Phase 3's dogfood produced Phase 3 v1.1 (within-phase) and Phase 2 v1.2 (inter-phase). The pattern is now consistent across three phases: each phase's dogfood refines its own toolkit and routes one cluster upstream to refine the phase before it. The framework's central claim — that toolkits get better with use, and that the improvement compounds across phases as later phases stress upstream toolkits in ways the upstream phases couldn't catch — has now demonstrated itself three times, not once.

---

## Section 5: Meta-Observations from the Authoring Practice

A few patterns from the Phase 3 arc are worth naming, distinct from the fourteen formal observations.

### The multi-session handoff is where currency discipline earns its keep

Phase 3 was the first run to span two sessions. The session boundary was a genuine risk — context accumulated over Session 1 had to be reconstructed at the start of Session 2 from a handoff document rather than from live memory. The mitigation was the toolkit's own currency re-verification discipline, applied at the resume point. And it was precisely at that resume-point re-check that the concurrent-release crossover surfaced. The discipline that exists to protect against inter-step drift turned out to be the discipline that caught inter-*session* drift too. For any phase large enough to span sessions, the currency re-check is not boilerplate — it is the load-bearing safeguard at the seam.

### The inheritance thesis needs a second term

The Phase 2 article advanced a clean thesis: inheritance compounds, so later phases surface fewer observations. Phase 3's 14 (against Phase 2's 7) does not refute it — but it adds a term. Inheritance lowers the floor for the surface a phase *shares* with its predecessor; it does nothing for surface that is *genuinely new*. Phase 2 was mostly a variation on Phase 1's shape, so it inherited nearly everything and surfaced 7. Phase 3 introduced six heterogeneous artifact types, two feedback channels, cross-brief coordination, and a multi-session run — new machinery with no upstream analog — and surfaced 14. The refined thesis: **observation count tracks new structural surface, not toolkit maturity.** A mature toolkit that introduces a new mechanism will surface observations about that mechanism; that is the loop working, not failing.

### A discipline generalizes from "patch" to "parallel track"

The currency re-verification discipline was authored, in prior phases, around a narrow case: has a *patch* shipped between phases that needs re-anchoring? The Diamonds Phase 3 run stressed it with a case the narrow framing only partly covered — not a patch, but a *scheduled dependency shipping early via a parallel productization track*. The discipline caught the event (it asked "did anything ship?") but its framing didn't tell us what to *do* with the answer. The v1.1 revision generalized it: the currency check now names the parallel-track case explicitly and carries the grounding-update-versus-amendment decision rule. This is the same shape of lesson the prior articles kept surfacing — a discipline authored for the case in front of us, generalized once a real run presents the case we didn't anticipate. It argues, again, for treating every discipline as provisional until a differently-shaped project stresses it.

---

## Section 6: What's Queued Next

The Phase 3 toolkit at v1.1, the Phase 2 toolkit at v1.2, and the Phase 1 toolkit at v1.3 are the current state. The Diamonds Design Specification Bundle is the handoff to Phase 4. The next pieces of work this arc leaves queued:

**Phase 4 (Architecture & Modular Design) toolkit authoring.** Phase 3 produced six design specifications, a coordination register, and a verification strategy — the inputs Phase 4 architects against. The Phase 4 toolkit will take the Design Specification Bundle and produce module boundaries, internal structures, and the security-control and contract ID series that Phase 5 implements. Authoring it is a substantial session like the prior three, and it is already underway.

**Diamonds Phase 4 dogfooding.** Once the Phase 4 toolkit exists, the natural next dogfood applies it to Diamonds, continuing the real application. Phase 4's Step 01 will be Phase 3 Input Validation, with the same two-scope split — and any upstream-toolkit gaps it surfaces will route to Phase 3 v1.2, the same way Phase 3 routed to Phase 2 v1.2.

**Phase 5 execution on Diamonds.** The design specifications drive the actual v2.0 implementation — the practitioner's downstream work, outside this article series' toolkit-authoring scope, but the first cycle that will graduate the Phase 2 cost model's BELIEVED multipliers toward MEASURED and validate the verification instruments against real code.

**The fourth article in this series.** When the Phase 4 toolkit work is complete, with its dogfooding and revision arc, the next article documents it. The series will likely continue one article per phase, with periodic synthesis pieces as cross-phase patterns accumulate.

---

## Closing Note

The Phase 1 article said a framework without toolkits is a philosophy, a toolkit without applications is untested, and a toolkit applied once is suggestive but not validated. The Phase 2 article added that a framework whose toolkits don't feed back into each other across phases is still a hypothesis about the improvement loop. The Phase 3 arc lets us close that hypothesis one notch further: the inter-phase loop is not a one-time event. It has now fired for three consecutive phases, each dogfood refining its own toolkit and routing a cluster upstream — Phase 1 v1.1, then Phase 1 v1.3 from Phase 2, then Phase 2 v1.2 from Phase 3. Three phases is not proof, but it is a pattern, and the pattern is the one the foundational articles predicted.

Phase 3 also showed something the prior phases hadn't: that a toolkit's disciplines get stressed in genuinely new ways as the phases introduce new machinery, and that the currency discipline in particular earns its keep exactly when reality moves under a plan mid-cycle. The most valuable output of the run was not any of the six design specifications — it was the moment the toolkit's own currency check caught a parallel-track release the plan didn't know about, and forced us to reason out the difference between grounding an artifact and amending a plan.

We've described one more iteration through the build-apply-refine cycle, plus a second inter-phase revision. The artifacts are in the repository and can be used today. The next iteration — Phase 4 — is already in motion.

We'd be interested to hear what breaks when this toolkit meets a Phase 2 plan that isn't Diamonds' — and what a project with a genuinely different brief mix (five schemas and no refactors; a dozen contracts) reveals about the unified Step 03 that a six-brief run couldn't.

---

## What the Toolkit Files Actually Look Like

The current v1.1 inventory of the Phase 3 Existing Projects toolkit is ten files, under `toolkit/existing-projects/phase-3-technical-analysis/`:

- `README.md` — navigation, recommended sequence, phase-gate scorecard, artifact dependency map, version history
- `design-technical-analysis.existing-project.instructions.md` — load-once context (three shifts, six artifact types, the two feedback channels, inherited scorecard discipline; concurrent-release currency event per v1.1; Skill reference per v1.1)
- `step-00-building-block-discovery.prompt.md` — AI capability inventory, living document (tool present-vs-usable reliability, solo-fit, complementary lookup clarification per v1.1)
- `step-01-phase-2-input-validation.prompt.md` — Phase 2 validation; Validation Gap Register with the two-scope split (Channel 1); parallel-track currency check per v1.1
- `step-02-design-brief-triage.prompt.md` — per-brief artifact-type classification, dependencies, Step 03 order
- `step-03-per-artifact-design-specification.prompt.md` — the unified prompt with six sub-templates (purpose-before-mechanism, code-vs-process watch-triggers, single-source-of-truth per v1.1)
- `step-04-inter-artifact-coordination.prompt.md` — Coordination Register (mandatory single owner for 3+-brief artifacts per v1.1)
- `step-05-verification-strategy.prompt.md` — refinement to Phase 6-executable instruments (upstream-shape calibration per v1.1)
- `step-06-design-specification-synthesis.prompt.md` — capstone bundle, scorecard refresh, Channel 2 amendment package

Plus the dogfooding record and the upstream change from the Channel 1 firing:

- `project/existing-projects/dogfooding-diamonds/phase-3/dogfooding-observations.md` — the 14 observations from the Diamonds Phase 3 run, with the end-of-phase three-pass review and the eight clusters
- `toolkit/existing-projects/phase-2-design-analysis/step-03-mechanism-decisions.prompt.md` — revised to v1.2, implementing the three completeness gates from Cluster C5

Every file is version-stamped, has a Version History table, and is intended to be picked up and used directly rather than studied in the abstract.

---

*Part of the AI-Centric Software Development Playbook series. The previous articles in this series covered the [Phase 1 toolkit for existing projects](./part-01-building-phase-1-toolkit.md) and the [Phase 2 toolkit for existing projects](./part-02-building-phase-2-toolkit.md). Next up: the Phase 4 toolkit for existing projects, with its corresponding Diamonds dogfood.*
