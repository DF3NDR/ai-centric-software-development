# Building a Phase 1 Toolkit for Existing Projects

The foundational articles in the **AI-Centric Software Development Playbook** described a framework: the six Core Principles, the Specification Driven Development cycle, the seven phases, and the idea that every team's toolkit is a practice to build rather than a product to purchase. A later article walked through the construction of a Phase 1 toolkit for greenfield projects — the "what should we choose?" variant.

This article covers the sibling work: the **Phase 1 toolkit for existing projects** — the "what do we have, where are we, and what must change?" variant. It covers three arcs of a single working session:

1. **Building** the toolkit — authoring the instructions file and six step prompts that make up a complete Phase 1 Existing Projects toolset
2. **Applying** it to a real project — running the full Phase 1 cycle on `@diamondslab/diamonds`, a TypeScript library we maintain, and capturing observations during the run
3. **Refining** it — reviewing the observations end-of-phase, producing a v1.1 revision of the toolkit, and packaging framework-level reasoning as a reusable skill

The artifacts from this work live in the `ai-centric-software-development` repository under `toolkit/phase-01-information-gathering-existing-project-toolset/` and `skills/ai-centric-playbook/`. This article describes the process, not the artifacts themselves — the files are available to pick up and use directly.

We've been deliberate about flagging choices we made that others might reasonably make differently. The framework is opinionated about principles; the toolkit is opinionated about how to apply them. Our opinions aren't the only defensible ones.

A note before we start: this is a **first revision**. We ran one complete application of the toolkit on one project, captured what surfaced, and folded those observations into v1.1. The next revision — after another application on a different project profile — will almost certainly surface changes we haven't yet anticipated. What we're shipping is what works now, not what's finished.

---

## Section 1: Building the Toolkit

The greenfield toolkit was already in the repository, so we had a reference to work against rather than authoring from scratch. The question for the existing-projects variant was not *what structure do we use* — it was *what changes when the evidence comes from inside the team rather than outside it.*

### The three shifts that shape everything

We identified three structural shifts between greenfield and existing-project work before writing a single prompt. They turned out to drive nearly every downstream design decision:

**The codebase is a primary source of evidence.** In greenfield work, you're evaluating options that don't yet exist in your system — vendor docs, community health, comparable implementations. In existing-project work, the system is right there. The code, the deployment manifests, the dependency lockfiles, the incident history. These are more reliable than documentation, memory, or stated intent. Where they disagree, the code wins as a description of current behavior.

**Observed behavior, documented intent, and desired future state must be distinguished.** This is the discipline we call "the three timeframes." What the system does right now is an observation. What it was supposed to do is a specification (if one exists). What it should do going forward is the improvement goal. These are three different objects and conflating them produces improvement plans that fix symptoms rather than causes.

**The improvement objective is itself a Phase 1 output, not a Phase 1 input.** Practitioners arrive with vague goals — "we need to modernize," "we need to fix the tech debt." Part of Phase 1 is sharpening that into something specific enough to drive Phase 2 decisions. A greenfield Phase 1 takes a requirements sketch; an existing-project Phase 1 takes a system plus a vague goal and produces both a requirements sketch and a sharpened objective.

These three shifts became the opening section of the toolkit's instructions file, and they govern how every step prompt frames its questions.

### What we built

The v1.0 toolkit ended up as seven files:

| File | Role |
|------|------|
| `step-00-information-gathering.existing-project.instructions.md` | Load-once context file — framework orientation, behavioral rules, three-timeframes discipline |
| `step-01-current-state-technology-architecture-assessment.prompt.md` | Inventory what the system is built from, as deployed |
| `step-02-operational-performance-baseline.prompt.md` | The measured before-picture Phase 6 will judge improvement against |
| `step-03-requirements-improvement-objective-sketch.prompt.md` | Must-Keep / Must-Change / Nice-to-Improve / Incidental registers + sharpened objective |
| `step-04-risk-constraint-technical-debt-inventory.prompt.md` | Compliance, security risk, hard constraints, debt |
| `step-05-reusable-replaceable-components-catalog.prompt.md` | Per-component Keep / Upgrade / Replace / Retire dispositions |
| `step-06-current-state-information-report-synthesis.prompt.md` | Capstone — synthesizes everything, runs the self-evaluation scorecard |

*(The list above is the v1.0 snapshot. Subsequent revisions added the Building Block Discovery prompt in v1.1 and renamed the instructions file in v1.2. The current nine-file inventory is listed at the end of this article.)*

The parallel to the greenfield set is deliberate. A practitioner who has used the greenfield toolkit should find the existing-projects variant familiar: same SDD cycle, same six principles, same phase-gate scorecard discipline at the end. What changes is the question set and the output structure — shifted from landscape-evaluation framing to current-state-inventory framing.

### Choices we made that others might not

**We named the step files `step-NN-*.prompt.md`.** This implies sequential execution, which is mostly accurate (the prompts are designed to run in order) but awkward for the instructions file, which is loaded continuously rather than "run at step 00." We noticed this awkwardness late in the session and left the naming for a v1.2 revision. Others might choose `NN-*.prompt.md` with a separate `instructions.md` outside the numbered sequence from the start.

**We treated Step 05 — the components catalog — as an interview prompt producing a catalog artifact.** An alternative would treat it as a more mechanical inventory operation: run a dependency scan, parse the lockfile, enumerate the directory tree, and classify everything programmatically. We chose interview-style because the practitioner's judgment on disposition (Keep / Upgrade / Replace / Retire) requires context that mechanical inventory can't supply. But for larger codebases, the mechanical approach would be faster and the interview could focus only on the items where disposition is contested. Which is right depends on the project's size and the practitioner's available time.

**We put baseline capture (Step 02) before requirements sharpening (Step 03).** An alternative would sharpen the objective first — you know what you're trying to improve, therefore you know what to measure. We reversed it because practitioners arrive with vague objectives and sharpen them as they learn more about the current system. Measuring first forces confrontation with facts that often reshape the objective. Measuring after risks measuring the wrong things.

**We made the Step 06 synthesis prompt an *action* prompt rather than an *interview* prompt.** The practitioner pastes all five prior artifacts into a single session and the AI synthesizes without further questioning. The alternative — a final interview to validate the synthesis — would catch more drift, at the cost of session time. We chose speed because the prior five steps already provide extensive practitioner input; Step 06 is meant to consolidate, not re-discover.

None of these decisions is unambiguously correct. Each could have been made differently by a team with different priorities. What matters is that they were made deliberately and documented, not defaulted into.

---

## Section 2: Applying It — The Diamonds Run

With the toolkit drafted, we ran it on `@diamondslab/diamonds` — a TypeScript library we maintain that deploys ERC-2535 Diamond Proxy smart contracts on Hardhat. The project has three characteristics that made it a useful first test:

- **Solo maintainer** (one of us), with a documented sub-5-hour-per-week ecosystem time budget
- **Pre-production state** — used in three private projects we also maintain, with no external adopters
- **A genuine improvement goal that wasn't yet sharp** — we described it as "productize the library" at the start of the session, which was vague enough to be a real test of Step 03's objective-sharpening discipline

This approach of applying a toolkit to a real project as a test — what software teams call dogfooding — is what we used to stress-test the toolkit as we built it.

### The run itself

We ran all six steps sequentially in a single extended session. The artifacts produced were:

- Step 01 — Technology & Architecture Assessment: 27 findings spanning framework coupling, build tooling, test architecture, CI absence, security gate configuration, and a measured-version surprise (the repository version was v1.3.2, not the v1.2.1 we initially worked from — caught during Step 02 pre-interview verification)
- Step 02 — Operational & Performance Baseline: 14 additional findings including a full CVE posture scan, build-and-test-cycle timing under 21 seconds, zero external adoption, and a <5-hour-per-week maintainer-time budget
- Step 03 — Requirements & Improvement Objective Sketch: 9 Must-Keeps, 20 Must-Changes (which grew to 22 across Steps 04 and 05), 7 Nice-to-Improves, 8 Incidentals, and a sharpened objective shifting from "productize" to "make the library adoption-ready for external Solidity developers and auditors"
- Step 04 — Risk, Constraint & Technical Debt Inventory: added 2 new Must-Changes (private-key refactor and dev-env smoke test), amended 1 existing one, and produced a worst-case scenario synthesis that named the underlying mechanism across all branches
- Step 05 — Components Catalog: 8-category catalog with approximately 100 distinct components classified; no net-new Must-Changes but five scope expansions to existing ones
- Step 06 — Information Report: consolidated all prior artifacts, ran the self-evaluation scorecard (5 PASS + 1 CONDITIONAL), produced the Phase 2 readiness determination

### What the run produced that we didn't expect

The most consequential finding of the run was not in any individual step — it was a mechanism that surfaced only during Step 04's worst-case scenario exercise: **the gap between what Diamonds claims and what Diamonds can prove.** The library works, has local quality gates, and has achieved its core design goal (auditor reproducibility from deployment records alone). But these claims are internal — visible only to the maintainer — and the evidence chain that would make them external is not yet built. Every one of the 22 Must-Changes, read that way, is trust infrastructure.

That framing — *the claims-versus-proof gap as the organizing mechanism of the improvement cycle* — became the executive summary of Step 06's report and the single most useful synthesis of the entire run.

It wouldn't have surfaced from any individual step's questions. It emerged from the worst-case narrative discipline in Step 04, which forced us to describe three alternative bad-outcome branches and then keep writing until the mechanism producing *any* of them was named. Three unrelated bad outcomes became one underlying problem.

This is the kind of insight that validates the framework's insistence on having a worst-case exercise at all.

### Observations captured during the run

We followed a protocol we'd agreed on at the start: capture observations about the toolkit *as we worked through it*, without acting on them during the run. Each observation recorded what happened, why it was a problem or a working pattern, what toolkit change would address it, and a priority. By the end of the six steps, we had 26 observations across the six steps plus the initial Specify interview.

Some were bugs (of our own AI reasoning, more often than of the toolkit itself). The most embarrassing: at one point, we marked `scripts/deploy-rpc.ts` as "Keep" because the source module it wrapped (`RPCDeploymentStrategy.ts`) was current. The practitioner had to correct us — the wrapper script was outdated even though the source was current. This is the kind of inheritance-by-association reasoning error that produces plausible-looking catalog entries with the wrong disposition. Observation 23 captured it; Cluster P in the v1.1 revision addresses it explicitly.

Some observations validated patterns we'd designed for. The three-timeframes discipline caught an orphan `scripts/devops/` directory full of 15 shell scripts that looked current (recently edited, referenced 2025-era tooling) but turned out to be copy-in from a different project that had never been wired into Diamonds' CI, husky hooks, or documentation. Without explicit attention to observed-vs-documented-vs-desired, those scripts would have been treated as part of the current scaffold.

Some surfaced genuine gaps. We had no mechanism in the toolkit to enumerate available AI capabilities — MCP connectors, skills, specialized agents — at the start of a run. We worked around this by asking the practitioner directly during the initial Specify interview, but this was ad-hoc; it should have been a formal step. Observation 1 and Observation 2 flagged this. The v1.1 revision added a dedicated Building Block Discovery prompt (authored as `step-00b-*.prompt.md`), and the v1.2 revision renamed it to `step-00-building-block-discovery.prompt.md` — the leading numbered step — once the instructions file was moved out of the numbered sequence.

The full dogfooding observations file is in the repository at `toolkit/phase-01-information-gathering-existing-project-toolset/dogfooding-observations.md`. It contains all 26 observations with their source step, nature, evidence, proposed changes, priority, and current status (all now Acted as of v1.1).

### One number worth sharing

A full Phase 1 run on a small-to-medium library takes — we measured — approximately one extended session (several hours of practitioner time) plus the follow-up review. The 26 observations across that run produced 19 change clusters in the review, all of which were accepted (one with refinement) and folded into the v1.1 revision.

Put differently: **for every hour of applying the toolkit on a real project, we got roughly 3–4 actionable improvements to the toolkit itself.** That's the characteristic of a working dogfood process — the applications and the refinements are mutually productive.

### Choices we made during the run that others might not

**We ran all six steps in one session.** An alternative is to split the run across days or weeks, giving the practitioner time to verify claims between steps. We chose single-session because the context accumulation between steps is substantial and losing it forces expensive re-establishment. The trade-off is that late-session fatigue can reduce observation quality. We noticed this in Step 06 and compensated by scheduling the end-of-phase review for a separate session.

**We treated observation capture as mandatory but action on observations as deferred.** The alternative — fix observations as they surface — would produce a working toolkit at the end of the run but lose the characterization of *where* the toolkit's problems cluster. We wanted the clustering data. This is a genuine trade-off; teams that need a working toolkit faster might reasonably invert the priority.

**We accepted one CONDITIONAL rating in the final scorecard.** The Scoring & Metrics principle flagged that Phase 1 hadn't assigned quantitative weights across the six principles. An alternative would force the weighting in Phase 1 to achieve a full PASS. We chose CONDITIONAL because weighting is genuinely a Phase 2 decision — Phase 1 gathers the information Phase 2 uses to set weights. A CONDITIONAL rating with explicit rationale surfaces this for Phase 2 more clearly than a buried caveat in a PASS.

---

## Section 3: Refining It — The v1.1 Revision and the Skill

At the end of the Diamonds run, we had two things: a complete Phase 1 Information Report ready for Phase 2 (which was the point of the exercise), and 26 observations about the toolkit itself (which was the purpose of the dogfood). The next work was converting the observations into a revised toolkit.

### The review process

We used a three-pass review:

1. **Pass 1 — Cluster.** Group observations that propose changes to the same file, address the same gap, or validate the same pattern. The 26 observations reduced to 19 clusters (labeled A through S).
2. **Pass 2 — Per-cluster decision.** For each cluster: Accept, Accept with refinement, Defer, or Reject. We accepted all 19. One (Cluster E, on the comprehensiveness check pattern) got a refinement — the check would be added to Steps 03 and 05 only, not Step 04, because Step 04's register construction was systematic enough that blind spots would surface through the register itself.
3. **Pass 3 — Revise.** Produce the v1.1 files.

The "Accept with refinement" rate of roughly 1 out of 19 felt about right. A higher rate would have suggested we were accepting draft observations without enough review. A lower rate (straight Accept on everything) would have suggested insufficient scrutiny.

### The revision itself

V1.1 changed every one of the seven toolkit files plus added one new file (the Building Block Discovery prompt) and updated the README. The total changes:

- **Instructions file (`step-00`)**: Added six new sections — Multi-Repo Evidence Scoping, Code Access Calibration, a three-timeframes worked example, Version & Identity Re-Verification, Interview Mode Selection, and an MCP connector activation retry pattern. The three-shifts opening section stayed the same; these additions were disciplines the Diamonds run revealed were tacit rather than explicit.
- **Step 01**: Added an issue-tracker presence question to the System Identification cluster and a "Verification Tasks for Next Step" subsection to the artifact template.
- **Step 02**: Added a "Local Evidence Collection" subsection specifying when and how to prompt the practitioner to execute commands (audit scans, timing wrappers, git log for release cadence) and fold output into baseline rows.
- **Step 03**: Switched default interview mode to draft-and-react (the AI proposes registers based on prior artifacts; practitioner reacts). Added an Issue Tracker Consultation section mandating classification of every open issue into Must-Change / Nice-to-Improve / Incidental / Dropped. Added a Comprehensiveness Check pattern at the end of the question bank.
- **Step 04**: Added the expectation that 2–4 net-new Must-Changes will surface in this step (not a Step 03 failure — by design). Added standards-conformance framing for projects without regulatory compliance burden. Added a common-mechanism discipline for the worst-case narrative.
- **Step 05**: Switched to draft-and-react mode. Added the expectation that 3–5 scope expansions will surface (not new MCs — scope expansion is preferred). Added an artifact-inheritance warning (Keep on a source module does not confer Keep on its wrapper scripts). Added a Disposition Ratio Interpretation section taxonomizing four patterns (healthy productized / brownfield cleanup / active capability expansion / sunset) with Phase 2 sequencing implications.
- **Step 06**: Added an explicit synthesis-only discipline (if Step 06 is producing net-new findings, something was missed upstream). Added scorecard rigor guidance (CONDITIONAL preferred over PASS-with-caveats, target 4–5 PASS + 1–2 CONDITIONAL on a well-executed Phase 1).
- **New file: Building Block Discovery prompt**. Short (typically under 10 minutes) inventory of available AI capabilities — MCP connectors, code access, skills — run after the initial Specify interview and before Step 01. Produces a Toolset Augmentation Document that informs every subsequent step.
- **README**: Added a brief MCP Servers section (GitHub MCP, Context7, direct code access — strongly encouraged but not strictly required, with graceful degradation to copy-paste when unavailable). Added dogfooding calibration guidance (20–30 observations per complete run is the expected range). Added a Version History table.

Every revised file carries its own Version History entry documenting what changed and why. This is intentional — a practitioner picking up the files a year from now shouldn't have to read this article to understand the v1.1 changes.

### The skill

The last piece of work was packaging framework-level reasoning as a reusable Claude skill. The motivation was portability: the toolkit assumes a practitioner has the Playbook articles available as project knowledge (they're the source of framework context). A skill removes that assumption — any Claude session with the skill available gets framework context without needing the articles.

The skill ended up as four files:

- **`SKILL.md`** — Entry point with YAML frontmatter (`name:` and `description:` following the Anthropic Agent Skills spec) defining when to invoke. One-page summary of the framework — thesis, six principles, SDD cycle, building blocks, seven phases. Pointers to three reference files for depth.
- **`core-principles.md`** — One section per principle, each with what it asks, scope, common failure modes, Phase 6 PASS criteria, and interactions with other principles. Plus applied patterns (coverage audit, weighted scoring, trade-off documentation template).
- **`sdd-cycle.md`** — One section per SDD step with purpose, mechanics, good-output patterns, and common pitfalls. Plus a phase-by-phase adaptation table showing how the vocabulary shifts from Phase 1 through Phase 7 while the methodology stays constant.
- **`building-blocks-and-toolsets.md`** — One section per building block type with properties, when-to-use, when-NOT-to-use, and quality checklists. Plus three example tool set compositions and two applied patterns (building a new tool set, evaluating an existing one).

The skill lives in the repository at `skills/ai-centric-playbook/`. It's scoped deliberately tight — framework-level reasoning only, no phase-specific content. Phase-specific guidance stays in the phase tool sets themselves.

### Choices we made about refinement that others might not

**We folded the observations into a single v1.1 revision rather than shipping incremental revisions.** An alternative would produce v1.0.1, v1.0.2, etc. — one per accepted observation — which would make the change history more granular. We chose the single revision because 19 clusters all acting on the same toolkit at the same time is effectively one coherent round of work, and granular versioning would obscure the fact that they were a single dogfood's worth of feedback.

**We used Version History tables rather than inline CHANGELOG entries.** An alternative is a single `CHANGELOG.md` at the toolkit root. We chose per-file Version History because the changes are per-file — a practitioner revising Step 03 wants to know what changed in Step 03, not scroll through changes across all seven files.

**We scoped the skill to framework-level reasoning only.** An alternative would include phase-specific references in the skill — "here's what Phase 1 typically looks like, here's what Phase 4 typically looks like." We rejected that because the skill would bloat and would duplicate content that already lives in phase tool sets. Tight scope makes the skill maintainable.

**We used YAML frontmatter following the Anthropic Agent Skills format.** This is Claude-specific. Other AI environments (Cursor, Copilot, open-source LLMs) may use different formats. The content below the frontmatter is portable, but the triggering mechanism isn't. We chose Claude-specific because Claude is our primary environment; teams using other environments should expect to adapt.

---

## On First Revisions and What's Not Finished

We started this article by noting that this is a first revision. That framing matters.

The Diamonds run was one project profile — a small, solo-maintained, pre-production TypeScript library. The toolkit is calibrated to what that profile revealed. Several disciplines we added in v1.1 (the disposition-ratio interpretation, the three-timeframes worked example, the multi-repo evidence scoping) generalized well in our drafting, but generalization is hypothesis until tested. A larger team's codebase, a regulated-industry project, or a mature production system with real external users will almost certainly reveal gaps we haven't anticipated.

The next planned work is a second application on a different project profile — likely one with a genuinely different disposition ratio (our suspicion is that the brownfield-cleanup pattern that dominated the Diamonds catalog is itself a first-productization-pass pattern; a healthy productized library under ongoing improvement would show Keep-dominant ratios we haven't yet seen tested).

What v1.2 already landed, beyond the v1.1 revision content:

- **File naming cleanup.** The `step-` prefix was dropped from the instructions file, making its role (load-once context) distinct from the numbered step prompts. The Building Block Discovery prompt was renumbered from `step-00b` to `step-00`, taking its place as the genuine first numbered step. This addresses the naming awkwardness we flagged during the v1.1 session.

What we expect to change in v1.3 and beyond:

- **The tool set template.** Extract the patterns that worked (prompt metadata header, system instructions, kickoff, output format, evaluation checklist, version history) into a reusable skeleton before Phase 2 authoring produces a divergent shape. Retrofitting a template onto already-authored toolsets is harder than authoring from the template, so doing this before Phase 2 fully lands is time-valuable.
- **Whatever the next application reveals.** The toolkit should continue to evolve. A version that never increments suggests we stopped applying and observing, not that we reached completion.

---

## Where We Go Next — Phase 2 for Existing Projects

The Diamonds Information Report is the handoff artifact to Phase 2. Phase 2 — Analysis & Improvement Planning — takes the current-state picture and the sharpened objective, and produces a sequenced improvement plan: what work happens first, how it's costed, what the decision framework is for the choices Phase 1 explicitly deferred.

The Phase 2 toolkit for existing projects does not yet exist. Authoring it is the next piece of work in this series. Our intuition, going in:

- Phase 2 is more decision-heavy than Phase 1. Phase 1 gathers and structures; Phase 2 chooses. That suggests draft-and-react mode throughout (we added it to half of Phase 1 as the dogfood revealed the need; Phase 2 should probably default to it).
- Phase 2 needs stronger integration with Phase 1 outputs than Phase 1 needed with greenfield inputs. The current-state registers, the baseline rows, the component dispositions, the must-changes — these flow directly into Phase 2 decision-framework inputs. The Phase 2 toolkit will likely start with a prompt that loads the Phase 1 Information Report and validates it rather than re-discovering.
- Phase 2 produces a plan. That plan must embed the Core Principles as concrete sequencing and scoping decisions, not as aspirational notes. The same PRD discipline that applies to Phase 3 onward applies to Phase 2's output.

We'll author the Phase 2 toolkit, dogfood it on Diamonds (continuing the real application), and write the next article in this series.

---

## What the Toolkit Files Actually Look Like

We've referenced the files throughout this article without reproducing them. The v1.2 inventory of the Phase 1 Existing Projects toolkit is nine files:

- `toolkit/phase-01-information-gathering-existing-project-toolset/README.md` — navigation, recommended sequence, MCP guidance, version history
- `toolkit/phase-01-information-gathering-existing-project-toolset/information-gathering.existing-project.instructions.md` — load-once context file (renamed in v1.2, previously `step-00-*`)
- `toolkit/phase-01-information-gathering-existing-project-toolset/step-00-building-block-discovery.prompt.md` — AI capability inventory (added in v1.1 as `step-00b`, renumbered in v1.2)
- `toolkit/phase-01-information-gathering-existing-project-toolset/step-01-current-state-technology-architecture-assessment.prompt.md` — current-state inventory
- `toolkit/phase-01-information-gathering-existing-project-toolset/step-02-operational-performance-baseline.prompt.md` — measured before-picture
- `toolkit/phase-01-information-gathering-existing-project-toolset/step-03-requirements-improvement-objective-sketch.prompt.md` — registers and sharpened objective
- `toolkit/phase-01-information-gathering-existing-project-toolset/step-04-risk-constraint-technical-debt-inventory.prompt.md` — risk, constraint, debt
- `toolkit/phase-01-information-gathering-existing-project-toolset/step-05-reusable-replaceable-components-catalog.prompt.md` — per-component dispositions
- `toolkit/phase-01-information-gathering-existing-project-toolset/step-06-current-state-information-report-synthesis.prompt.md` — capstone synthesis and scorecard

Plus the dogfooding record and the skill, referenced throughout the article:

- `toolkit/phase-01-information-gathering-existing-project-toolset/dogfooding-observations.md` — the 26 observations from the Diamonds run, all with status Acted (v1.1)
- `skills/ai-centric-playbook/SKILL.md` and three reference files — framework-level reasoning packaged as a Claude skill

Every file is version-stamped, has a Version History table, and is intended to be picked up and used directly rather than studied in the abstract.

---

## Closing Note

The central claim of the Playbook — that small teams orchestrating AI can deliver what large organizations once required — depends on the toolkit work being real and usable, not theoretical. A framework without toolkits is a philosophy. A toolkit without applications is untested. A toolkit applied only once is suggestive but not validated.

This article describes one iteration through one cycle: build, apply, refine. The artifacts are in the repository and can be used today. The next iteration is coming. The framework's value compounds when practitioners adopt, apply, observe, and refine — and share what they find.

We'd be interested to hear what breaks when this toolkit meets a project that isn't Diamonds.

---

*Part of the AI-Centric Software Development Playbook series. Previous articles cover the framework's foundations (Articles 0–9) and the Phase 1 toolkit for greenfield projects. Next up: the Phase 2 toolkit for existing projects.*