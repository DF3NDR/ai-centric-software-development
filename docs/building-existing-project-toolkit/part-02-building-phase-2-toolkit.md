# Building a Phase 2 Toolkit for Existing Projects

This is the second article in the series in which we implement our [AI-Centric Software Development Playbook](https://github.com/df3ndr/ai-centric-software-development) and develop toolkits by applying them to our real [Diamonds node module project](https://github.com/diamondslab/diamonds) — refining the results through a forging process of real-world usage.

The first article in this series covered the Phase 1 toolkit for existing projects — the "what do we have, where are we, and what must change?" variant of information gathering. That article documented building the toolkit, applying it to `@diamondslab/diamonds`, and folding the dogfooding observations into a v1.1 revision.

This article covers the sibling work: the **Phase 2 toolkit for existing projects** — the "given what we have, what do we improve in what order?" variant. Phase 1 surfaced what needs to change about Diamonds (22 Must-Changes, distributed across Foundation, Capability, and Productization tiers). Phase 2's job is deciding which mechanism to use for each change, in what sequence, at what cost, against an explicit capacity envelope. The output is an Improvement Plan that drives Phase 3 onward.

The article covers three arcs of a single working session, mirroring the Phase 1 article's structure:

1. **Building** the toolkit — authoring the instructions file and seven step prompts (step-00 through step-06) that make up a complete Phase 2 Existing Projects toolset
2. **Applying** it to Diamonds — running the full Phase 2 cycle on the Phase 1 Information Report, producing the Improvement Plan, and capturing observations along the way
3. **Refining** it — reviewing observations end-of-phase, producing a v1.1 revision of the toolkit, and surfacing a structural finding that fed back into the Phase 1 toolkit as a v1.3 revision

The artifacts live in the `ai-centric-software-development` repository. This article describes the process, not the artifacts themselves — the files are available to pick up and use directly.

A note before we start: this is the second article in the series, but it's still early in the framework's life. The Phase 2 toolkit is at v1.1, having gone through one complete dogfooding cycle. The toolkit will continue to evolve — what's shipping is what works now, not what's finished.

---

## Section 1: Building the Toolkit

Phase 2 differs from Phase 1 in a way that shaped the toolkit from the start: it's a **decision-heavy** phase, not a discovery-heavy one. Phase 1 elicits — the AI asks, the practitioner describes, evidence accumulates, the artifact accretes. Phase 2 proposes — the AI drafts a mechanism choice or sequencing decision, the practitioner reacts (accept, amend, reject), and decisions are recorded with rationale. That shift drives nearly every structural choice we made.

### Three shifts from Phase 1 that shape Phase 2

Just as the Phase 1 toolkit opened with three shifts that distinguished it from greenfield work, the Phase 2 toolkit opens with three shifts that distinguish it from Phase 1:

**From discovery to decision.** Phase 1's default interview mode is question-by-question because elicitation works best when focused. Phase 2's default is draft-and-react because decision-making works best when there's a concrete proposal on the table to react against. The exception is Step 01 (Phase 1 Input Validation), which is question-by-question because validation is a confirmation activity rather than a decision activity.

**From findings to mechanisms.** Phase 1 named Must-Changes — things that must change about the system. Most MCs have multiple plausible mechanisms — multiple specific ways to make the change happen. A dependency upgrade can be a patch bump or a replacement library. A breaking change can ship as a clean break with a major version bump or with a deprecation cycle and a shim window. A CI workflow can be authored directly in GitHub Actions or composed via reusable workflows. Phase 2's Step 03 chooses the mechanism for each MC that has multiple candidates. The choice is principle-weighted — under the Step 02 weights, different mechanisms score differently.

**From baseline to capacity.** Phase 1 captured baselines (the MEASURED rows that Phase 6 will judge improvement against). Phase 2 captures costs against those baselines plus a capacity envelope — how much practitioner time, how much AI-usage budget, what timeline. Phase 2's Step 05 produces a cost-vs-capacity check that may force re-sequencing if the plan exceeds capacity.

These three shifts became the opening section of the toolkit's instructions file, and they govern how every step prompt frames its work.

### What we built

The v1.0 toolkit for Phase 2 ended up as nine files:

| File | Role |
|------|------|
| `analysis-improvement-planning.existing-project.instructions.md` | Load-once context file — three shifts, behavioral rules, principle weighting discipline, cost-modeling tag discipline, phase gate criteria |
| `step-00-building-block-discovery.prompt.md` | Building Block Discovery — confirms Phase 1 Report loadability and inventories capability changes since Phase 1 |
| `step-01-phase-1-input-validation.prompt.md` | Validates Phase 1 understanding, produces a Validation Gap Register |
| `step-02-principle-weighting.prompt.md` | Assigns weights to the six Core Principles for this cycle, resolves Phase 1's Scoring & Metrics CONDITIONAL |
| `step-03-mechanism-decisions.prompt.md` | Per-MC mechanism choices with principle-weighted rationale, alternatives considered, verification methods, inter-MC dependencies |
| `step-04-sequencing-and-tiering.prompt.md` | Tiered sequence, minimum-viable-completion floor, stretch scope, worst-case plan-failure narrative |
| `step-05-cost-modeling-and-capacity-check.prompt.md` | Per-MC cost rows, per-tier and plan totals, capacity-vs-envelope comparison, capacity-bound recommendation |
| `step-06-improvement-plan-synthesis.prompt.md` | Capstone — synthesizes everything into the Improvement Plan, runs the self-evaluation scorecard, produces Phase 3 design briefs and Phase 5 task-list seed |
| `dogfooding-observations.md` | Captured during the run; the Phase 2 equivalent of Phase 1's same file |

The parallel to the Phase 1 toolkit is deliberate. A practitioner who has used the Phase 1 toolkit should find Phase 2 familiar in shape: same SDD cycle, same six principles, same phase-gate scorecard discipline at the end, same dogfooding-observations protocol. What changes is the question set, the output structure, and the interview mode default — shifted from elicitation framing to decision framing.

### Inherited discipline from Phase 1 v1.2

The most significant authoring choice we made was not a feature decision — it was *to author Phase 2 v1.0 to Phase 1 v1.2 conventions from the start, rather than letting Phase 2 develop its own structural shape and then retrofitting.*

Phase 1 v1.0 had been authored without a template, and Phase 1 v1.1 retrofitted structural improvements onto the already-authored prompts. The retrofit worked but cost more than authoring from the matured template would have. By the time we sat down to author Phase 2, we knew what the matured Phase 1 disciplines were — the three-timeframes framing, version re-verification, interview mode selection, tag discipline, scorecard rigor with target distributions, behavioral rules in a labeled section, version history per file. We applied them to Phase 2 v1.0 from the start.

This turned out to be the single most consequential decision for how the dogfooding played out, as we'll see in Section 2.

### Choices we made that others might not

**We made Step 01 a validation step rather than a re-discovery step.** An alternative would have Phase 2 re-interview the practitioner about the system's current state — what's there, what matters, what hurts — to refresh AI context. We chose validation-only because re-interviewing wastes the Phase 1 work and risks introducing inconsistencies between Phase 1's record and Phase 2's restatement. Step 01 confirms understanding ("Phase 1 records X — is that correct, and is there anything to add or amend?") rather than re-eliciting. The trade-off is that if Phase 1 was incomplete in some way, Step 01 may not catch it — which became important to handle, as we'll see when Cluster D surfaces during the Diamonds run.

**We placed the principle-weighting step (Step 02) before mechanism decisions (Step 03).** An alternative would defer weighting until cost-modeling time, when the practitioner can see what each principle would "cost" in different directions. We chose weighting-first because mechanism choices depend on which principles dominate the decision — without weights, mechanism rationale is hand-wavy. The trade-off is that weighting requires the practitioner to make a normative call before seeing the full picture, but the principle-weighting prompt includes a sanity-check phase that surfaces which downstream decisions are most weight-sensitive, so the call isn't fully blind.

**We made Step 04 sequencing produce a worst-case plan-failure narrative.** The Phase 1 toolkit had a worst-case mechanism narrative at Step 04; we ported it to Phase 2's sequencing step, where it serves the same structural-fragility check role — but for the *plan* rather than the *system*. The discipline is the same: keep writing until the common mechanism that produces all failure branches is named. Three unrelated bad outcomes are not done; a named common mechanism is. We weren't sure this would generalize from Phase 1's "what could the system do wrong" framing to Phase 2's "what could the plan do wrong" framing, but it did. The Diamonds run produced "load-bearing concentration" as the common mechanism — a useful synthesis we'll cover in Section 2.

**We made Step 06 synthesis-only.** Just as Phase 1 Step 06 is an action prompt rather than an interview, Phase 2 Step 06 consolidates Steps 01-05 into the Improvement Plan without further questioning. The discipline is stronger in Phase 2: if Step 06 is producing net-new mechanism choices, sequencing decisions, or cost estimates, something was missed in Steps 01-05 — pause Step 06 and fix the upstream gap, don't paper over it in synthesis. We surfaced this as an explicit behavioral rule because the temptation to "smooth things out in synthesis" is real.

**We surfaced two specific outputs from Step 06: Phase 3 design briefs and a Phase 5 task-list seed.** An alternative would treat Phase 6 (the Improvement Plan) as the only handoff artifact and let Phase 3 figure out for itself which MCs need design work. We chose to name them explicitly in Step 06's output because we'd noticed during the Diamonds Phase 1 run that some handoffs to downstream phases are clearer when the upstream phase makes them concrete. The Phase 5 task-list seed similarly: rather than letting Phase 5 start from zero, Step 06 produces an ordered list of seed tasks with acceptance criteria from Step 03's verification methods. Phase 5 refines into formal tasks but doesn't restart.

None of these decisions is unambiguously correct. Each could have been made differently by a team with different priorities. What matters is that they were made deliberately and documented in the toolkit files.

---

## Section 2: Applying It — The Diamonds Phase 2 Run

With the toolkit drafted, we ran it on Diamonds — continuing the application from Phase 1. The Phase 1 Information Report was the input. The intent: produce the Improvement Plan that would guide Diamonds' productization arc through subsequent phases.

The same project characteristics that made Diamonds a useful first test for Phase 1 carried forward to Phase 2:

- **Solo maintainer**, with a documented sub-5-hour-per-week ecosystem time budget (Diamonds-specific share roughly 2 hr/week)
- **Pre-production state**, with zero external adopters
- **22 Phase 1 Must-Changes** distributed across three tiers, with one Phase 1 CONDITIONAL gate (Scoring & Metrics) waiting to be closed

### The run itself

We ran all six numbered steps sequentially in a single extended session, plus the initial Specify interview and the step-00 Building Block Discovery prompt. The artifacts produced were:

- **Initial Specify**: confirmed subject (`@diamondslab/diamonds` v1.3.2, no drift from Phase 1), confirmed Phase 2 intent (produce the Improvement Plan), captured an in-line amendment to the toolkit's cost-modeling discipline (more on this shortly)
- **Step 00 — Building Block Discovery**: confirmed Phase 1 Report loadability, inventoried capability changes since Phase 1, noted that Context7 was not approved at session start
- **Step 01 — Phase 1 Input Validation**: confirmed all eight validation categories from the prompt, surfaced 5 validation gaps — of which 3 turned out to be gaps in the Phase 1 toolkit rather than gaps in Phase 2's understanding (a finding we'll return to)
- **Step 02 — Principle Weighting**: assigned Security 1.5× / Maintainability 1.5× / Economics 1.0× / Operations 1.0× / Scoring & Metrics 1.0× / Correctness Verification 1.5×; resolved the Phase 1 Scoring & Metrics CONDITIONAL; documented an explicit Operations deprioritization for next-cycle re-weighting
- **Step 03 — Mechanism Decisions**: triaged 22 MCs into 8 multi-mechanism (requiring Phase 2 decision) and 14 single-mechanism (forwarded as-is), drafted per-MC mechanisms in three batches of 4/3/1
- **Step 04 — Sequencing and Tiering**: confirmed Phase 1's suggested three-tier structure, identified a Coordinated Breaking-Change Block (MC-04 + MC-05 + MC-21 + MC-22 + MC-13) that lands together as v2.0, produced an 11-MC minimum-viable-completion floor with an 11-MC stretch scope, named "load-bearing concentration" as the common mechanism across worst-case plan-failure branches
- **Step 05 — Cost Modeling and Capacity Check**: per-MC cost rows totaling 41.75 maintainer-hours and ~$32 token cost across the full plan; capacity comparison showed the floor fits comfortably at ~7 weeks of Diamonds-specific time, the full plan at 5-10 months consistent with the open-ended timeline
- **Step 06 — Improvement Plan Synthesis**: consolidated all prior artifacts, ran the self-evaluation scorecard (4 PASS + 2 CONDITIONAL — Operations CONDITIONAL by explicit deprioritization, Correctness Verification CONDITIONAL pending Phase 3 verification-artifact specifications), produced Phase 3 design briefs for four MCs, produced the Phase 5 task-list seed

### What the run produced that we didn't expect

The most consequential moment of the entire Phase 2 run happened during the initial Specify interview, before any of the numbered steps. We were discussing capacity envelopes and the practitioner observed:

> *"Your toolkit's cost-modeling assumes one quantity — time. But in AI-Centric Software Development practice, there are two distinct quantities you keep collapsing: the work's intrinsic complexity (estimated as developer-hours, roughly stable across humans) and the maintainer's actual time spent (which is shaped by AI acceleration and may differ from developer-hours by an order of magnitude). A naive 22-MC plan at '100+ hours of work, 2 hours per week, equals one year' is correct arithmetic on the wrong quantity."*

The practitioner was right. The Phase 2 toolkit's cost-modeling tag discipline used time as a single dimension. That works for pre-AI estimation where developer-hours and maintainer-hours were effectively equivalent. It doesn't work for AI-Centric practice, where the AI does most of the typing and the maintainer does most of the deciding.

We made an in-line amendment during the Specify interview: cost-modeling for this Diamonds run would use a **three-quantity model** — dev-hours (Senior Developer baseline), an AI-acceleration multiplier (per work category), and derived maintainer-hours (bound by the capacity envelope). The practitioner then took it further: the dev-hour figure can be roughly equated to AI token usage (their working ratio: 6,000 tokens per Senior dev-hour), which makes the dev-hour figure not just a comparative-size indicator but a directly measurable cost predictor in dollar terms.

We added token-count and token-cost as derived dimensions, captured the three-quantity model as observations P2-Obs-01 and P2-Obs-02, and proceeded through Steps 02-06 with the amended discipline.

The model worked well in practice. Per-MC cost rows came out clean. Per-category multipliers (mechanical cleanup 10×, doc authorship 8×, config edit 5×, novel design 3×) produced credible distributions. The plan totaled 218 dev-hours of intrinsic complexity, 41.75 maintainer-hours actual practitioner time, 1.31M tokens, and roughly $32 in API cost at Opus 4.7 pricing. Capacity comparison was honest: the floor fits, the full plan is realistically a 5-10 month effort under the existing time budget.

That framing — *three quantities, not one, in cost modeling* — became the most consequential v1.1 revision item, and we'll cover it in Section 3.

### Other observations from the run

Compared to Phase 1's 26 observations across its complete run, Phase 2 produced only 7. We had expected the calibration range to be 15-25 observations (lower than Phase 1's range because Phase 2 v1.0 inherited Phase 1's matured disciplines). Seven was meaningfully under-range.

The under-range count has a clean structural explanation: **Phase 2 v1.0 was authored to Phase 1 v1.2 conventions from the start.** The structural improvements that surfaced during Phase 1's dogfood — the three-timeframes discipline, version re-verification, interview mode selection, behavioral rules in a labeled section, scorecard rigor — were already in Phase 2 v1.0. The observations that did surface clustered around things Phase 1's dogfood couldn't have surfaced because they didn't exist there yet: cost modeling, inter-phase feedback channels, mid-phase capability availability.

The 7 observations broke down as:

- **4 from the initial Specify interview** (P2-Obs-01..04), all four driven by the cost-model gap and its downstream implications
- **1 from Step 01** (P2-Obs-05) — the Validation Gap Register surfacing gaps in the Phase 1 toolkit rather than Phase 2 local gaps, which the toolkit's template didn't distinguish
- **1 from Step 03** (P2-Obs-06) — Context7 became available mid-step after being unavailable at step-00, revealing that the Toolset Augmentation Document had been treated as a snapshot rather than a living document
- **1 from Step 03** (P2-Obs-07) — meta-observation that the batch-sizing pattern improvised during the run (4 MCs / 3 MCs / 1 MC) worked well and was worth codifying

The Phase 1 article noted that for every hour of toolkit application on a real project, the team got roughly 3-4 actionable improvements to the toolkit itself. Phase 2's ratio was different: roughly one actionable improvement per hour, with the improvements concentrated in one substantive cluster (cost modeling) and several smaller refinements. The lower density is what *successful inheritance* looks like.

### Choices we made during the run that others might not

**We made the cost-model amendment in-line rather than pausing to revise the toolkit first.** When the practitioner surfaced the dev-hour-vs-maintainer-hour distinction during the initial Specify interview, an alternative would have been to stop, revise step-05 to v1.0.1, and resume. We chose to apply the amendment in-line, capture it as an observation, and revise to v1.1 at end-of-phase. The choice was pragmatic — we were focused on producing the Improvement Plan, and the discipline of capturing-but-not-acting on observations during a run is itself the dogfood protocol. The trade-off is that the actual Phase 5 cost numbers in the Improvement Plan use a discipline that isn't in any committed version of the toolkit until v1.1 lands. The Plan documents this explicitly; future practitioners who pick up the v1.1 toolkit get the discipline from the start.

**We accepted Step 03's batch-sizing improvisation rather than forcing the prompt's stated default.** The Step 03 prompt advised drafting 4-6 MCs per batch. We had 8 multi-mechanism MCs. The natural batching was 4 (high-weight-sensitive: MC-01 + MC-04 + MC-08 + MC-11) / 3 (mid-sensitivity, cross-referenced: MC-07 + MC-12 + MC-21) / 1 (independent cleanup: MC-19). We deviated from the prompt's default and the batching worked. That's a positive observation worth codifying — the v1.1 revision adds explicit batch-sizing guidance to Step 03 documenting the pattern.

**We treated the Coordinated Breaking-Change Block as a single landing event rather than four independent MCs.** When Step 03's per-MC mechanism choices revealed that MC-04 (extension contract), MC-05 (Defender retirement), MC-21 (private-key refactor), and MC-22 (dev-env smoke test) were all breaking changes that interlocked, we made the Step 04 sequencing decision to land them together as v2.0 rather than as four separate breaking-change events. The Phase 1 article noted that the Diamonds project has zero external adopters, which means the cost of multiple breaking-change events is low — but the cost of one coordinated event is also low and produces a cleaner CHANGELOG and a single migration narrative. Under different adoption conditions, the trade-off could go either way.

**We accepted "load-bearing concentration" as the worst-case common mechanism.** The Step 04 worst-case narrative discipline forced us to keep writing until we'd named the underlying mechanism producing all failure branches. Three branches surfaced: the Coordinated Block stalling on unforeseen MC-04 complexity, the doc-heavy Tier 3 quietly losing Layer 3 documentation under capacity pressure, and the burst-then-dormant cadence pattern from Phase 1 reasserting before completion. The common mechanism — that the plan has too few "natural pause points" because its structurally-correct choices (coordinated breaking changes, layered documentation) produce blocks that are themselves the smallest defensible units of work — is a useful synthesis that goes directly into Phase 7 watch-triggers. It wouldn't have surfaced without the discipline of pushing past three unrelated bad outcomes.

---

## Section 3: Refining It — The v1.1 Revision

At the end of the Diamonds Phase 2 run, we had two things: a complete Improvement Plan ready for Phase 3 (which was the point of the exercise), and 7 observations about the toolkit itself (which was the purpose of the dogfood). The next work was converting the observations into a revised toolkit.

### The review process

We used the same three-pass review structure that the Phase 1 dogfood had used:

1. **Pass 1 — Cluster.** Group observations that propose changes to the same file, address the same gap, or validate the same pattern. The 7 observations reduced to 6 clusters (labeled A through F). The lower 7-to-6 ratio than Phase 1's 26-to-19 reflects the tight coupling of P2-Obs-01 and P2-Obs-02 (the cost-model fix is one structural change, not two).

2. **Pass 2 — Per-cluster decision.** For each cluster: Accept, Accept with refinement, Defer, or Reject. We accepted all six. One (Cluster B) was accepted but routed to Phase 1 v1.3 rather than landing in Phase 2 v1.1, because the underlying gap was structurally a Phase 1 toolkit problem rather than a Phase 2 problem. One (Cluster C) was accepted with refinement — its scope was made additive (extending Step 06's output format) rather than structural (introducing new workflows).

3. **Pass 3 — Revise.** Produce the v1.1 files.

The cluster-by-cluster breakdown:

| Cluster | Observations | Scope | Decision |
|---------|--------------|-------|----------|
| A — Three-Quantity Cost Model | P2-Obs-01, P2-Obs-02 | Phase 2 v1.1 substantial | Accept |
| B — Phase 1 Budget Framing Gap | P2-Obs-03 | **Phase 1 v1.3** (not Phase 2 v1.1) | Accept, routed downstream |
| C — Phase 7 Empirical Calibration | P2-Obs-04 | Phase 2 v1.1 minor + Phase 7 future | Accept with refinement |
| D — Phase 2 → Phase 1 Feedback Channel | P2-Obs-05 | Phase 2 v1.1 moderate | Accept |
| E — Mid-Phase Capability Shift | P2-Obs-06 | Phase 2 v1.1 minor | Accept |
| F — Step 03 Batch Sizing | P2-Obs-07 | Phase 2 v1.1 trivial | Accept |

The "Accept with refinement" rate of 1 out of 6 felt about right — same approximate ratio as Phase 1's review (1 out of 19). A higher rate would suggest accepting under-developed observations; a lower rate (straight Accept on everything) would suggest insufficient scrutiny.

### The revision itself

V1.1 changed 7 of the 9 toolkit files. Two files (`step-02-principle-weighting.prompt.md` and `step-04-sequencing-and-tiering.prompt.md`) were unchanged — no observation affected them. Compared to Phase 1 v1.1, which changed every file and added one, Phase 2 v1.1 was a more contained revision. The total changes:

- **Instructions file**: Substantial revision to the Cost Modeling Tag Discipline section, expanding it from a single-dimension model to the three-quantity model. Added two reference tables (per-category multiplier defaults and token baselines). Added a tag-distribution honesty check with project-profile expected distributions. Added a capacity-bound recommendation discipline with four named resolution paths. Added a new behavioral rule for treating the Toolset Augmentation Document as living rather than snapshot.

- **Step 00 (Building Block Discovery)**: Added a "Document Is Living, Not Snapshot" subsection to the Purpose section. Added a new behavioral rule directing AI to amend the augmentation document with dated entries when capabilities shift mid-phase. Added a §7 Mid-Phase Amendments table to the Output Format with an example entry showing the Diamonds Context7-mid-Step-03 case.

- **Step 01 (Phase 1 Input Validation)**: Split the Validation Gap Register into §8.1 Phase 2 Local Gaps and §8.2 Upstream Toolkit Gaps in the Output Format. Added a behavioral rule for classifying each gap by scope, with explicit guidance distinguishing upstream-toolkit gaps from practitioner-forgot-to-mention items. Revised the Q8 interview question to ask for the classification.

- **Step 03 (Mechanism Decisions)**: Added explicit batch-sizing guidance to System Instructions documenting the 4/3/1 pattern improvised during the Diamonds run: default batch size 4 MCs; reduce to 2-3 when MCs share cross-references; reduce to 1 for independent cleanup-type MCs; never exceed 6.

- **Step 05 (Cost Modeling and Capacity Check)**: Substantial revision operationalizing the three-quantity cost model. Per-MC cost row format expanded to 8 columns (MC / Dev-hrs / DH Tag / Category & Multiplier / Maint-hrs / Tokens / Token Cost / Rationale). Added the same two reference tables that landed in the instructions file (for quick in-step access without context-switching). System Instructions, Output Format, tag-distribution honesty check, and Evaluation Checklist all updated. Added a behavioral rule that BELIEVED multipliers in any cost rows must be surfaced forward to Step 06 for the Phase 7 calibration handoff.

- **Step 06 (Improvement Plan Synthesis)**: Added a new §10.4 Phase 7 Calibration Handoff to the Output Format, required whenever Step 05 cost rows include BELIEVED-tagged multipliers (which is essentially every Phase 2 v1.0 plan). The new section names six quantities to track during Phase 5 execution (dev-hours, maintainer-hours, implied multiplier, token usage, implied ratio, API cost) with their expected tag-graduation paths. Added a behavioral rule enforcing the §10.4 inclusion when applicable.

- **README**: Updated the Tool Set Files table to describe per-file v1.1 features inline. Updated the Recommended Sequence diagram with v1.1 feature annotations. Added a "Capabilities can shift mid-phase" subsection under MCP Server Recommendations. Added a "Phase 2 → Phase 1 feedback channel is a feature" subsection under Dogfooding & Calibration Guidance. Added a new common pitfall: "Conflating Dev-Hours and Maintainer-Hours."

Every revised file carries its own Version History entry. The practitioner picking up a single file should be able to understand its evolution without reading this article — the file is self-describing.

### Choices we made about refinement that others might not

**We routed Cluster B downstream to Phase 1 v1.3 rather than absorbing it into Phase 2 v1.1.** The observation (P2-Obs-03) was that the Phase 1 toolkit captured budget as a single "zero budget" constraint without distinguishing commercial-services budget (which can legitimately be $0 for OSS) from AI-usage budget (which is structurally non-zero for any AI-Centric work). The gap was structurally a Phase 1 toolkit problem — Phase 1 should have captured budget as a two-layer construct from the start, so Phase 2 could plan against both layers. We could have papered over it in Phase 2 by adding a budget-disambiguation step at the top of Phase 2's Step 05, but that would have masked the real issue. Routing the cluster to Phase 1 v1.3 instead — even though it meant deferring the fix to a separate session — preserved the structural honesty.

**We made the three-quantity cost model substantial enough to require revision in both the instructions file and step-05.** An alternative would have put the model definition only in the instructions file (the load-once context document) and referenced it from step-05. We chose to duplicate the reference tables in both files because step-05 is the prompt where the model gets operationalized in per-MC cost rows, and the practitioner working through step-05 shouldn't have to context-switch back to the instructions file for multiplier values mid-row. The duplication is deliberate; the instructions file is the source of truth if the two ever drift.

**We treated P2-Obs-04 (Phase 7 calibration) as additive rather than structural.** The observation was that BELIEVED multipliers at v1.0 should graduate to ESTIMATED after one cycle and to MEASURED after 2-3, but the Phase 7 toolkit doesn't yet exist to capture the calibration. An alternative would have deferred the change until Phase 7 toolkit authoring. We chose to land the forward-handoff requirement in Phase 2 v1.1's step-06 anyway, because the Diamonds Phase 5 execution will start producing the calibration data soon — and naming what to track is the discipline that ensures the data actually gets captured. When the Phase 7 toolkit is authored, it inherits the tracking requirement; until then, the Diamonds Phase 5 work serves as the first empirical-validation cycle.

**We added meta-observations about the toolkit-authoring practice to this article that aren't in `dogfooding-observations.md`.** Section 4 will cover these in more detail — observations about the process of authoring the toolkit, not just observations about the toolkit content. They didn't belong in the formal observation log (which is scoped to toolkit-content gaps and patterns) but they're useful for practitioners considering the same authoring approach.

---

## Section 4: Meta-Observations from the Authoring Practice

This section captures patterns from the authoring practice itself — meta-observations distinct from the seven formal dogfooding observations in `dogfooding-observations.md`. These didn't belong in the formal observation log because they're about *how the toolkit was authored*, not about *what the toolkit needs to change*. But they're useful for practitioners considering the same approach.

### Inheritance from prior dogfood compounds

The Phase 1 toolkit went through a substantial v1.1 revision after its first dogfood. The Phase 2 toolkit was authored with Phase 1 v1.2's matured disciplines as the default — same prompt structure, same behavioral-rule pattern, same scorecard rigor framing, same Version History table format. This produced a Phase 2 v1.0 that surfaced 7 observations rather than the 15-25 we expected.

The under-range count is not a sign that the dogfooding protocol failed. It's a sign that the framework's improvement loop is doing what the foundational articles claimed it would — *the toolkit gets better with use*, and that improvement compounds across phases. Phase 2's structural shape was already mostly right at v1.0 because Phase 1's dogfood had done much of the structural-discovery work upstream.

The expected calibration range for future Phase 2 dogfooding runs on different project profiles may stay below the original 15-25 framing unless those project profiles are sufficiently different from Diamonds to stress the toolkit in genuinely new ways. A regulated-industry project, a multi-engineer team, or a mature productized library with real external users will almost certainly surface gaps Diamonds didn't. But the gaps will likely be additive to Phase 2's current shape, not structural revisions of it.

### The first revision should not try to be the last

Phase 2 v1.1 left two files unchanged from v1.0: step-02 (principle weighting) and step-04 (sequencing and tiering). Neither observation cluster affected them. An alternative authoring approach would scan every file for "improvements while we're in there" and produce a uniform revision across all files. We deliberately didn't.

A revision that touches every file produces ambiguity about which changes are evidence-driven and which are stylistic. Practitioners reading the version history later cannot easily tell what the dogfood actually surfaced versus what got swept along. The discipline we adopted — *only revise files where a specific observation cluster justifies the change* — preserves traceability. Steps 02 and 04 still work, the Diamonds run validated them, and they stay at v1.0 (carried forward into the v1.1 toolkit unchanged). The next dogfooding cycle may surface observations that touch them; that's when they'll move forward.

### Authoring discipline and the "discard the bad file" moment

One specific authoring practice deserves explicit naming because we got it wrong mid-session and had to correct.

When we started authoring Phase 1 v1.3 (after the Phase 2 v1.1 work was complete), we attempted to produce the v1.3 instructions file as a "delta description" — a document that described what changed from v1.2, with placeholder text in unchanged sections directing the reader to assemble the full file themselves. The intent was to save work by avoiding a full file reauthoring when only a few sections changed.

The result was a half-finished file masquerading as a finished one. We caught the mistake before proceeding to the next file, discarded the bad file, loaded the full v1.2 content into context, and authored the full v1.3 file with the changes integrated in their correct positions. The principle:

> **Author from the loaded source rather than from partial memory, especially when the source is available and voice-matching matters.**

This is the same lesson as the version-drift discipline we'd already encoded in Phase 1 v1.1 (re-verify subject version at each step start) — applied to the authoring practice rather than to the toolkit content. Both lessons share an underlying mechanism: *partial context produces deceptively plausible output*. The fix in both cases is the same: load the actual source before producing the output.

If we'd been writing Phase 1 v1.3 from scratch we would have authored full files from the start. The temptation to skip the full reauthoring came specifically from the small revision scope ("only a behavioral rule and a section change"). Small-scope revisions are most at risk because the cost of doing them right looks disproportionate to the change. The discipline is to do them right anyway.

### Cross-toolkit voice consistency

Phase 2 v1.1 and Phase 1 v1.3 were authored in the same session. This produced a voice consistency between the two toolkits that wouldn't have been guaranteed if they'd been authored separately. Specifically:

- The behavioral-rule sentences in both toolkits' Behavioral Rules sections follow the same imperative pattern ("Apply the two-layer budget framing." then explanation, not "You should apply...").
- The Version History rows in both toolkits follow the same three-column format (Version / Date / Source / Summary) with summary text written as prose paragraphs rather than bullet lists.
- The cross-references between files use the same convention ("(see §X in the companion instructions file)" rather than mixed conventions).

These are stylistic conventions that emerge from a single authoring session and would be expensive to retrofit later. The takeaway for practitioners considering the same authoring approach: **batch toolkit revisions in cross-toolkit sessions where possible**, because voice consistency is more valuable than the marginal session-management overhead.

### The dogfooding observation count is not a quality metric

It's tempting to treat observation count as a quality signal — more observations means more dogfooding rigor. The Phase 2 run pushes back on that framing. The 7 observations were thoroughly captured, properly clustered, and produced six clean revision items. The Phase 1 run's 26 observations were also thoroughly captured, but the higher count reflected the toolkit being earlier in its development life, not the dogfood being more rigorous.

A future Phase 2 run that produces fewer than 7 observations is not a worse run. It might mean the toolkit has matured further, or it might mean the project profile didn't stress it in new ways. The signal-bearing data is in *what the observations reveal*, not *how many surfaced*.

---

## Section 5: The Phase 2 → Phase 1 Feedback Channel Firing

The Phase 1 article ended with a forward-looking note about Phase 2 needing "stronger integration with Phase 1 outputs than Phase 1 needed with greenfield inputs." We knew the integration would matter; we hadn't yet seen what shape the back-pressure from Phase 2 onto Phase 1 would take. The Diamonds Phase 2 run produced the answer.

### What surfaced during Step 01

The Phase 2 toolkit's Step 01 is a Phase 1 Input Validation step — its job is to confirm the Phase 2 AI session understands the Phase 1 Information Report correctly before any Phase 2 decisions begin. The prompt walks through eight validation categories (subject identity, sharpened objective, constraint envelope, MC register, baseline rows, worst-case narrative, gate status, validation gaps) and produces a Validation Gap Register at the end.

The Diamonds Phase 2 run produced 5 validation gaps from Step 01. Three of them — VG-02, VG-03, VG-04 — were not gaps in Phase 2's understanding of Phase 1. They were gaps in *the Phase 1 toolkit's instrumentation for capturing certain kinds of information*. Specifically:

- **VG-02**: Phase 1 had recorded "zero budget" as HC-03 without distinguishing what kind of zero. Phase 2's cost modeling needed two layers — commercial-services budget and AI-usage budget — and Phase 1 had collapsed them.
- **VG-03**: Phase 1's capacity-envelope capture (HC-08) was bounded in terms that didn't yet distinguish dev-hours from maintainer-hours, which Phase 2's three-quantity cost model exposed as a meaningful distinction.
- **VG-04**: Phase 1's MK-07 ("Zero-budget / OSS-only operation") encoded the same conflation as HC-03 — treating the budget as a single layer when it was structurally two.

These gaps weren't visible during Phase 1. The Phase 1 scorecard rated Phase 1 5 PASS + 1 CONDITIONAL, and the CONDITIONAL was on Scoring & Metrics (waiting for Phase 2 to assign weights). All five MEASURED-tagged Phase 1 disciplines passed. The information that surfaces these gaps doesn't exist in Phase 1's universe — it surfaces only when Phase 2's cost-modeling step asks questions Phase 1 didn't anticipate.

### Why the toolkit caught this and earlier work might not have

Phase 2 v1.1's Step 01 prompt was authored with explicit two-scope classification for validation gaps. The relevant snippet from the prompt's behavioral rules:

> *Classify each validation gap by scope. Every gap is either:*
> - *Phase 2 local — Phase 2 must resolve this within its own six steps, or acknowledge it as documented limitation in the Improvement Plan.*
> - *Upstream toolkit — the gap exists because the Phase 1 toolkit itself was incomplete in some structural way that Phase 2 work surfaced.*

The split makes the inter-phase feedback channel explicit rather than implicit. Without it, the three upstream-toolkit gaps would have surfaced as "Phase 2 noticed Phase 1 didn't capture X well enough" — which is true but ambiguous. Does Phase 2 absorb the gap by adding a workaround? Does Phase 1 get a revision? Does the gap just go unfixed because nobody owns it?

The two-scope split forces the answer. Upstream-toolkit gaps don't block Phase 2 — Phase 2 proceeds with an amendment or workaround — but they do queue for Phase 1 toolkit revision in a separate session. The durable fix lives in the upstream toolkit, not in the downstream phase's workaround.

For the Diamonds run, this meant Phase 2 proceeded with an in-line three-quantity cost model amendment (capturing the discipline as it should be applied), produced the Improvement Plan against the amended discipline, and queued Phase 1 v1.3 to land the structural fix upstream. Three artifacts came out: the Improvement Plan (Phase 2 deliverable), the Phase 2 v1.1 revision (cost model formalized in the Phase 2 toolkit), and Phase 1 v1.3 (budget framing formalized in the Phase 1 toolkit).

### The framework's first inter-phase feedback loop, end-to-end

This is the first time we've seen the framework's improvement loop fire across phases rather than within one. Phase 1's dogfood produced Phase 1 v1.1 (within-phase loop). Phase 2's dogfood produced both Phase 2 v1.1 (within-phase loop) and Phase 1 v1.3 (inter-phase loop).

The foundational articles in the Playbook hypothesized this would happen. The framework's central claim about leverage rests partly on the idea that **toolkits get better with use, and that improvement compounds across phases as later phases stress upstream toolkits in ways that surface gaps the upstream phases couldn't catch.** Phase 2's dogfood is the first concrete demonstration that the hypothesis was right.

A second-order observation worth surfacing: the discipline that caught this — the two-scope split in Phase 2's Step 01 — wasn't in Phase 2 v1.0. We added it in Phase 2 v1.1 because the Diamonds run made the pattern visible. The first dogfood of Phase 2 was the dogfood that produced the discipline that makes the inter-phase feedback channel explicit. There is something recursive about a toolkit revision that adds the mechanism for surfacing its own next revision — but it's the kind of recursion the framework's central thesis predicts.

### Phase 1 v1.3 — what landed

Phase 1 v1.3 was a small, focused revision affecting three files in the Phase 1 toolkit:

- **`information-gathering.existing-project.instructions.md`** gained a new Two-Layer Budget Framing section between Framework Context and the SDD Cycle section, defining the discipline as load-once context for the entire Phase 1 toolkit. The Behavioral Rules section gained an "Apply the two-layer budget framing" rule. The Economics principle filter gained a cross-reference. The Phase Gate Economics PASS requirement was updated to require two-layer budget capture. A new common pitfall was added: "Conflating commercial-services budget with AI-usage budget."

- **`step-03-requirements-improvement-objective-sketch.prompt.md`** restructured its Non-Negotiable Constraints interview questions to split budget into commercial-services and AI-usage with a disambiguating follow-up scripted for the "zero budget" answer. The Must-Keep Compliance & Security Posture section gained an MK-25 example row showing how OSS-posture projects capture the "no commercial-tier services" claim with explicit two-layer framing.

- **`step-04-risk-constraint-technical-debt-inventory.prompt.md`** split the Hard Constraints section's H-01 budget row into H-01a (commercial-services / SaaS-tier) and H-01b (AI-usage), with the disambiguating follow-up scripted in the interview question bank.

The revision is small in line count but structurally consequential. Every future Phase 1 run will capture budget as two layers from the start, which means every future Phase 2 will have the two-layer envelope available without an in-line amendment. The gap closes once, and stays closed.

### Choices we made about Phase 1 v1.3 that others might not

**We made it Phase 1 v1.3 rather than Phase 1 v1.2.** During the Phase 2 v1.1 authoring, our references to "Phase 1 v1.2" turned out to be forward-looking aspiration — the uploaded Phase 1 files we were working from were labeled v1.1 in their headers, with no distinct v1.2 revision having been authored. Rather than retroactively label this revision as v1.2, we acknowledged the gap honestly in the v1.3 Version History rows: "v1.2 was not authored as a distinct revision — v1.3 follows v1.1 directly." This preserves the option for a future v1.2 if one is needed and keeps the version-history audit trail honest.

**We deliberately scoped Phase 1 v1.3 to Cluster B alone.** An alternative would have scanned the Phase 1 toolkit during the v1.3 session for "other improvements while we're in there" — a Phase 2 → Phase 1 backlog grooming pass. We chose not to. The Diamonds Phase 2 dogfood surfaced one upstream-toolkit gap (the budget framing). That's the change v1.3 lands. Future Phase 2 dogfoods on different project profiles may surface other upstream-toolkit gaps; those queue for v1.4, v1.5, etc. Tying revisions tightly to the dogfood data that produced them preserves traceability and prevents Phase 1 v1.3 from becoming a kitchen-sink revision whose changes nobody can attribute to specific evidence.

**We authored Phase 1 v1.3 as full files, not patches.** Earlier in the session, we'd attempted to author the v1.3 instructions file as a delta description with placeholder text in unchanged sections. We caught the mistake, discarded the half-finished file, loaded the full v1.2 content, and authored the full v1.3 file with changes integrated. (This is the "discard the bad file" moment that became Meta-Observation 3 in Section 4.) The discipline of authoring full files from loaded source rather than from partial memory is more expensive in tool calls but produces repository-ready output rather than assembly instructions. For Phase 1 v1.3 specifically, the full-file approach also made it easy to add a v1.3 Version History row in each file documenting the change — which a patch-only approach would have had to handle as a side artifact.

---

## Section 6: Lessons from the Authoring Practice

Two toolkits authored, two dogfoods run, two within-phase revision arcs, one inter-phase revision arc. The session that produced all of this is too short to draw final conclusions from, but a few patterns have surfaced consistently enough across the two arcs to be worth naming.

### The framework's central claim survives contact with reality

The Playbook's foundational articles claimed that small teams orchestrating AI can deliver what large organizations once required. The two toolkit-authoring arcs are a particular case of that claim — a single practitioner with AI assistance produced two complete toolkits, applied each to a real project, and folded the dogfood observations into revisions in roughly the timespan that traditional toolkit-development efforts would spend on initial scoping.

The work was real. The dogfooded toolkits are usable today. The Diamonds Improvement Plan is the genuine output of applying them — not a contrived example. The framework's central claim isn't proven by one practitioner's experience, but it survived the test of being applied to itself, which is the test most frameworks fail.

### Inheritance is the framework's compounding mechanism

The single most measurable consequence of the two arcs is that Phase 2 v1.0 surfaced 7 dogfooding observations against Phase 1 v1.0's 26. The lower count is structurally explained by Phase 2 v1.0 inheriting Phase 1 v1.2's matured disciplines. This is the compounding effect the framework's foundational articles promised: **each cycle's improvements raise the floor for subsequent work**, and the gains accumulate.

For practitioners thinking about adopting the framework, the implication is that the first phase's toolkit-authoring is the most expensive. Subsequent phases benefit from the structural decisions already made. The marginal cost of authoring Phase 3, Phase 4, Phase 5, Phase 6, and Phase 7 toolkits — assuming each gets dogfooded — should be progressively lower in proportion to the structural work already done upstream.

That's a falsifiable claim. We'll know whether it holds when the Phase 3 toolkit is authored and dogfooded.

### Dogfooding is non-negotiable, and one-cycle dogfooding is not enough

We dogfooded both toolkits on the same project (Diamonds). That was useful — continuity of context, accumulated practitioner judgment, consistent project profile — but it also means both toolkits are calibrated to the same project shape. A solo-maintained, pre-production, OSS TypeScript library is a particular calibration target. The toolkits work for it. We don't yet know whether they work for substantially different profiles.

The next planned applications include a regulated-industry project (different compliance posture), a multi-engineer team (different capacity model), and a mature productized library with real external users (different scorecard dynamics). Each will probably surface observations the Diamonds runs didn't. Each will probably drive another revision arc.

What the Diamonds runs validated is that the *dogfooding protocol* works — observations get captured, reviews produce coherent clusters, revisions land cleanly, and the loop closes within a manageable session structure. The protocol is portable across project profiles. The toolkits, calibrated against more profiles, will be more portable too.

### Voice consistency emerges from session structure, not enforcement

The Phase 2 article you are reading and the Phase 1 article that preceded it share a structural shape — three labeled sections (Building / Applying / Refining) with "Choices we made that others might not" patterns inside each, followed by meta-observations and a closing forward-look. We didn't enforce this consistency through a style guide. It emerged because the same practitioner authored both in adjacent sessions, with the Phase 1 article loaded as a structural model when the Phase 2 article was drafted.

The same pattern showed up in the toolkit revisions. Phase 2 v1.1 and Phase 1 v1.3 were authored in the same session — and their behavioral rules, Version History row formats, and cross-reference conventions came out matching as a side effect of being authored together. We didn't have to retrofit consistency. We just had to do the work in the right order.

The implication: **batch related authoring in single sessions where context-continuity matters.** Phase 3 toolkit authoring and the next dogfooding article will probably both benefit from being adjacent in the work queue, not separated by weeks of other work.

### The framework's improvement loop is itself the framework

A subtle observation surfaced during the Phase 2 v1.1 authoring that's worth making explicit. The Phase 2 v1.0 toolkit had no mechanism for surfacing upstream-toolkit gaps — its Step 01 captured validation gaps in a single register that didn't distinguish scope. The Diamonds Phase 2 run produced three upstream-toolkit gaps anyway, and we noticed the pattern.

Phase 2 v1.1 added the two-scope split to make the inter-phase feedback channel explicit. The next dogfood of Phase 2 (on a different project profile) will be able to surface upstream-toolkit gaps as a first-class output, because the mechanism for surfacing them now exists. The toolkit gained the ability to improve the toolkit that produced it.

This is what the Playbook's framing of "the toolkit is a practice to build, not a product to purchase" means in concrete terms. The toolkits we ship today are not the toolkits we'll ship in six months. Not because we'll have changed our minds, but because the toolkits themselves are continuously being improved by their use — and the improvement mechanisms compound. **The framework's improvement loop is not a feature of the framework. It is the framework.**

### Where this lands for practitioners considering adoption

For a team thinking about adopting the AI-Centric Software Development Playbook on their own work, the lessons from this arc compress to roughly the following:

1. **Start with the existing toolkit.** Don't author from scratch. The Phase 1 and Phase 2 toolkits in the repository are not theoretical — they're refined by real dogfooding cycles. Pick them up, apply them, and let the application surface what your project's profile reveals.

2. **Run the full dogfooding protocol from the start.** Observation capture during the run, end-of-phase review with three-pass clustering, revision-by-cluster with file-level Version History entries. The protocol is what produces compounding gains. Skipping it produces a toolkit that gets used once and never improves.

3. **Expect inter-phase feedback to surface as you progress through phases.** Phase 2's dogfood produced one upstream-toolkit gap that fed Phase 1 v1.3. Phase 3, Phase 4, Phase 5, Phase 6, and Phase 7 dogfoods will probably produce their own. The two-scope split in Phase 2's Step 01 is the mechanism that catches these. Future phases' equivalents (Phase 3's Step 01 will be Phase 2 Input Validation, and so on) should inherit the same pattern.

4. **Document the choices you made that others might not.** This is the discipline that makes a toolkit reviewable by someone else's team. Without explicit "we did X and here's why" notes, your toolkit looks like a list of opinions. With them, it looks like a working artifact other teams can fork, amend, and contribute back to.

5. **Don't try to finish.** The framework's central thesis is that the toolkit improves through use. A version 1.0 that never increments to 1.1 means you stopped applying and observing — not that you reached completion. The most concerning signal in any team's adoption of the framework would be a toolkit that has been frozen at one version for a long time without surfacing any observation worth acting on. That's not stability; that's atrophy.

---

## Section 7: What's Queued Next

The Phase 2 toolkit at v1.1 and the Phase 1 toolkit at v1.3 are the current state. The Diamonds Improvement Plan is the handoff to Phase 3. The next pieces of work that this session leaves queued:

**Phase 3 (Design & Technical Analysis) toolkit authoring.** Phase 2 produced four explicit Phase 3 design briefs (MC-04 extension contract, MC-21 Signer-injection refactor, MC-07 documentation information architecture, MC-12 release-evidence schema) plus two supplementary briefs (observability touchpoints for v2.0 mechanisms, verification-artifact specifications). These are the seeds for a Phase 3 existing-projects toolkit. The toolkit will need to take a Phase 2 Improvement Plan as input and produce design artifacts that Phase 4 (Architecture) and Phase 5 (Implementation) consume. Authoring this is a substantial session like Phase 1 and Phase 2 were.

**Diamonds Phase 3 dogfooding.** Once the Phase 3 toolkit exists, the natural next dogfood is to apply it to Diamonds. The four design briefs from Phase 2 Step 06 are the input. The output is a set of design artifacts that drive Phase 5 implementation. This is also where the Phase 2 → Phase 1 feedback channel pattern is likely to fire again: Phase 3's Step 01 will be Phase 2 Input Validation, with the same two-scope split, and any upstream-toolkit gaps that Phase 3 work surfaces will route to Phase 2 v1.2.

**Phase 5 execution on Diamonds.** This is the practitioner's separate downstream work — outside the toolkit-authoring scope of this article series, though Phase 5's actual experience will calibrate the AI-acceleration multipliers that Phase 2 v1.1's three-quantity cost model uses as BELIEVED defaults. The Improvement Plan's Section 10.4 (Phase 7 Calibration Handoff) names the six quantities to track during execution. The Diamonds Phase 5 run will be the first empirical-validation cycle for the broader framework.

**The third article in this series.** When Phase 3 toolkit work is complete (with its dogfooding and revision arc), the next article documents that arc. This article series will probably continue as long as there are phases left to author toolkits for, and we may produce one article per phase plus periodic synthesis pieces as patterns emerge across phases.

**Sketching the broader practice.** Two toolkits is not enough to claim the framework's improvement loop is robust. Five or six toolkits, each dogfooded on multiple project profiles, would be a meaningful evidence base. We're at the beginning of that evidence accumulation, not the middle of it.

---

## Closing Note

The Phase 1 article closed by saying: *"A framework without toolkits is a philosophy. A toolkit without applications is untested. A toolkit applied only once is suggestive but not validated."* The Phase 2 article extends that observation: a framework whose toolkits don't yet feed back into each other across phases is still a hypothesis about how the improvement loop works in practice.

The Diamonds Phase 2 run produced the first concrete demonstration of an inter-phase feedback loop firing end-to-end. One observation surfaced during Phase 2 that traced its root cause to a Phase 1 toolkit gap. The loop closed: Phase 1 v1.3 landed the structural fix upstream, and future Phase 2 runs will work against an envelope that no longer has the gap. The framework's improvement claim isn't proven by one inter-phase loop firing, but it survived its first test of doing what the foundational articles said it would.

We've described one iteration through two cycles: build Phase 1, apply, refine; build Phase 2, apply, refine, and route one observation upstream to refine Phase 1 further. The artifacts are in the repository and can be used today. The next iteration is coming.

We'd be interested to hear what breaks when these toolkits meet a project that isn't Diamonds — and what patterns surface that ours didn't.

---

## What the Toolkit Files Actually Look Like

The current v1.1 inventory of the Phase 2 Existing Projects toolkit is nine files:

- `toolkit/phase-02-analysis-improvement-planning-existing-project-toolset/README.md` — navigation, recommended sequence, MCP guidance, dogfooding & calibration guidance, common pitfalls, version history
- `toolkit/phase-02-analysis-improvement-planning-existing-project-toolset/analysis-improvement-planning.existing-project.instructions.md` — load-once context file (three shifts, behavioral rules, principle weighting discipline, three-quantity cost-modeling discipline, phase gate criteria)
- `toolkit/phase-02-analysis-improvement-planning-existing-project-toolset/step-00-building-block-discovery.prompt.md` — AI capability inventory (living document with mid-phase amendments section per v1.1)
- `toolkit/phase-02-analysis-improvement-planning-existing-project-toolset/step-01-phase-1-input-validation.prompt.md` — confirms Phase 1 understanding, produces Validation Gap Register split into Phase 2 local gaps and Upstream toolkit gaps (per v1.1)
- `toolkit/phase-02-analysis-improvement-planning-existing-project-toolset/step-02-principle-weighting.prompt.md` — assigns weights to the six Core Principles, resolves Phase 1's Scoring & Metrics CONDITIONAL
- `toolkit/phase-02-analysis-improvement-planning-existing-project-toolset/step-03-mechanism-decisions.prompt.md` — per-MC mechanism choices with principle-weighted rationale (batch-sizing guidance per v1.1: default 4 MCs, reduce to 2-3 for cross-referenced clusters, reduce to 1 for independent cleanup MCs)
- `toolkit/phase-02-analysis-improvement-planning-existing-project-toolset/step-04-sequencing-and-tiering.prompt.md` — tiered sequence, minimum-viable-completion floor, stretch scope, worst-case plan-failure narrative with common-mechanism naming
- `toolkit/phase-02-analysis-improvement-planning-existing-project-toolset/step-05-cost-modeling-and-capacity-check.prompt.md` — three-quantity cost model with per-category multipliers, capacity-vs-envelope comparison, four named capacity-bound recommendation paths (per v1.1)
- `toolkit/phase-02-analysis-improvement-planning-existing-project-toolset/step-06-improvement-plan-synthesis.prompt.md` — capstone synthesis with §10.4 Phase 7 Calibration Handoff for plans using BELIEVED multipliers (per v1.1)

Plus the dogfooding record:

- `toolkit/phase-02-analysis-improvement-planning-existing-project-toolset/dogfooding-observations.md` — the 7 observations from the Diamonds Phase 2 run, with end-of-Phase-2 review and v1.1 revision outcome

And the upstream change from the Phase 2 → Phase 1 feedback channel firing:

- `toolkit/phase-01-information-gathering-existing-project-toolset/` — three files revised to v1.3 (instructions file, step-03, step-04) implementing the two-layer budget framing

Every file is version-stamped, has a Version History table, and is intended to be picked up and used directly rather than studied in the abstract.

---

*Part of the AI-Centric Software Development Playbook series. The previous article in this series covered the [Phase 1 toolkit for existing projects](./part-01-building-phase-1-toolkit.md). Next up: the Phase 3 toolkit for existing projects, with its corresponding Diamonds dogfood.*
