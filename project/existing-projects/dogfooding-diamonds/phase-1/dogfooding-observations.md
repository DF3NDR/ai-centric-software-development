# Dogfooding Observations — Phase 1 (Existing Projects) Toolset
## Diamonds Project Application

**Purpose:** Capture toolset-level observations during the
Diamonds dogfooding run for end-of-Phase-1 review and
incorporation into a revised Phase 1 (Existing Projects)
Tool Set.

**Strategy (Option B):** Observations are recorded at the end
of each step as the toolset runs them, but *changes to the
toolset itself are deferred* until all six steps complete.
This preserves experimental integrity — the toolset we're
dogfooding stays frozen for the full run.

**Review discipline:** At the start of each subsequent step,
re-read this file briefly. Not to change the toolset, but to
work around known gaps deliberately rather than rediscovering
them.

---

## Observation Format

Each observation captures:
- **ID** — sequential numbering
- **Source step** — which Phase 1 step surfaced it
- **Nature** — bug / gap / enhancement / pattern
- **Evidence** — concrete instance from the dogfooding run
- **Proposed toolset change** — specific file + specific edit
- **Priority** — High (invalidates outputs if not fixed) / Medium (degrades quality) / Low (polish)
- **Status** — Open / Acted (at end of phase)

---

## Observations

### Observation 1 — Building Block Discovery missing from Specify step

- **Source step:** Specify (pre-Step 01)
- **Nature:** Gap
- **Evidence:** I did not proactively surface MCP / Skill / Custom AI discovery during the Specify phase. Practitioner had to raise it by citing `part-02-building-your-toolkit.md`. I was treating the six `Step` prompts as the complete toolkit — missing that prompts are one building-block type among six (Consolidated Knowledge Base, Prompts, Skills, Instruction Sets, MCP Servers, Custom AIs).
- **Proposed toolset change:** Add an explicit "Building Block Discovery" section to `step-00-information-gathering.existing-project.instructions.md`. Should be in the Specify portion of the instructions, with a concrete prompt for the AI to search MCP registry, consider Skill additions, and document the augmented toolset before beginning Step 01. Also: README "How to Use This Tool Set" should add Building Block Discovery as substep 3 between "load instructions" and "Recommended Sequence."
- **Priority:** High — affects every Phase 1 run; without it, available building blocks go unused.
- **Status:** Acted (v1.1 toolset revision)

### Observation 2 — Consider a formal step-00b-building-block-discovery prompt file

- **Source step:** Specify
- **Nature:** Enhancement
- **Evidence:** Observation 1's issue would be cleanly solved by promoting Building Block Discovery from "section in instructions" to its own prompt file (`step-00b-building-block-discovery.prompt.md`). This would parallel how Step 06's synthesis is its own file rather than a section of an existing prompt.
- **Proposed toolset change:** Create `step-00b-building-block-discovery.prompt.md`. Contents: an interview-style prompt that walks the practitioner + AI through scanning available MCPs (via `search_mcp_registry` if in Claude), considering Skill additions, and producing a toolset-augmentation document before Step 01. Follow greenfield convention for file naming (e.g. compare to greenfield `research-specification`).
- **Priority:** Medium — the Observation 1 fix gets most of the value; this is the cleanest structural version.
- **Status:** Acted (v1.1 toolset revision)

### Observation 3 — Multi-repo evidence scoping lacks toolset guidance

- **Source step:** Step 01
- **Nature:** Gap
- **Evidence:** The toolset assumes one repo is the subject and gives no guidance on how to consult sibling repos as evidence without contaminating findings-about-the-subject. Three repos had to be reasoned about: Diamonds main (subject), hardhat-diamonds (integration peer), diamonds-dev-env (monorepo evidence source). In the first third of Step 01 I mixed evidence from all three into a single mental model until the practitioner pushed back on a CI finding that turned out to be from hardhat-diamonds.
- **Proposed toolset change:** Add a subsection under the three-timeframes discipline in `step-00` titled **"Multi-repo evidence scoping — how to use sibling repos as evidence sources without contaminating subject findings."** Content should cover: (a) classifying each repo as Subject / Integration Peer / Evidence Source at Specify time; (b) when searching, the Explicit Cross-Repo Mode discipline — announce cross-repo searches, attribute findings to subject repo, flag uncertainty with [CONFIRM]; (c) three resolution options for ambiguous evidence: practitioner-confirm, scope narrowing, or remove evidence-source repos.
- **Priority:** High — any existing-project assessment touching multiple repos will hit this, and Diamonds is not unusual.
- **Status:** Acted (v1.1 toolset revision)

### Observation 4 — Interview prompts assume no code access

- **Source step:** Step 01
- **Nature:** Gap
- **Evidence:** The Step 01 prompt (and by extension all interview prompts) is written as a conversational interview of the practitioner, implicitly assuming the AI is gathering evidence through dialogue. With `project_knowledge_search` and similar tool access, the natural AI behavior shifts toward "search first, then ask only about what I can't see." The toolset doesn't describe this shift. I had to propose Option C (hybrid with [CONFIRM]/[AWARE]/[QUESTION] flags) to the practitioner mid-interview because neither pure-interview nor pure-search was right.
- **Proposed toolset change:** Add a "Code Access Calibration" section to `step-00` describing three modes: (a) Interview-only — no code access, pure practitioner Q&A; (b) Search-primary — AI has code access, verifies before asking; (c) Hybrid with explicit flags — [CONFIRM] / [AWARE] / [QUESTION] pattern. Instruct the AI to choose mode at Specify time based on available tools, and to announce the mode to the practitioner. The hybrid flags themselves should be formalized in the `step-00` output-discipline section.
- **Priority:** High — every interview prompt in the toolset is affected.
- **Status:** Acted (v1.1 toolset revision)

### Observation 5 — Three-timeframes discipline demonstrably works

- **Source step:** Step 01
- **Nature:** Pattern (positive — toolset working as designed)
- **Evidence:** Finding F-02 (gnus-dao orphan devops infrastructure) would have been missed by naive discovery. A greenfield-style assessment would have listed "has devops tooling ✓" and moved on. The three-timeframes discipline (Observed / Documented Intent / Desired Future) forced me to actually read what the code *was* rather than accept what the directory structure *suggested*. Result: 14+ orphaned scripts with misattributed provenance surfaced and dispositioned.
- **Proposed toolset change:** None — the discipline works. Consider adding this as a **case study** in the `step-00` file to make the value concrete for future practitioners. A before/after example ("what a naive assessment would have reported vs. what three-timeframes caught") would anchor the abstract principle.
- **Priority:** Low — enhancement, not fix.
- **Status:** Acted (v1.1 toolset revision)

### Observation 6 — Explicit Cross-Repo Mode effectiveness

- **Source step:** Step 01
- **Nature:** Pattern (positive — process working as designed)
- **Evidence:** Option A (Explicit Cross-Repo Mode) with [CONFIRM] / [AWARE] / [QUESTION] flags caught contamination in 3/3 instances during Step 01, plus 1 self-caught inventory omission (RPCDeploymentStrategy). Without the discipline, each contamination would have become an incorrect finding in the artifact.
- **Proposed toolset change:** If Observation 3 is acted on, the [CONFIRM]/[AWARE]/[QUESTION] flag pattern should be described there as the practical tool. The three flags map cleanly: [CONFIRM] = finding I want you to verify before logging, [AWARE] = finding I'm logging without blocking, [QUESTION] = genuine question I can't answer from code.
- **Priority:** Medium — tied to Observation 3 resolution.
- **Status:** Acted (v1.1 toolset revision)

### Observation 7 — project_knowledge_search returns relevant but not complete results

- **Source step:** Step 01
- **Nature:** Pattern (AI behavior to warn against)
- **Evidence:** My initial inventory of `src/strategies/` listed four items (`Base`, `Local`, `OZDefender`, plus the interface). A later search mid-Step 01 revealed there are actually five — `RPCDeploymentStrategy` is the production-current deployment path and I had missed it entirely. A single `project_knowledge_search` returns *relevant* results but not *complete* ones. Brownfield inventory assessments must not treat a single search as exhaustive.
- **Proposed toolset change:** Add a "Comprehensiveness Check" pattern to `step-01`. Before artifact production, include a practitioner-facing question: "Given my admitted possibility of inventory miss, is there any structurally important area you suspect I haven't surfaced and that belongs in the assessment?" This catches maintainer knowledge that wouldn't naturally surface via AI search alone.
- **Priority:** Medium — non-exhaustive search is a class of AI risk that shows up across all steps.
- **Status:** Acted (v1.1 toolset revision)

### Observation 8 — Local evidence collection pattern needs formalization

- **Source step:** Step 02
- **Nature:** Enhancement
- **Evidence:** At the start of Step 02 I prompted the practitioner to run three scan commands locally (`yarn npm audit`, `yarn snyk:test`, `osv-scanner`) and paste the output. This converts BELIEVED-stale baseline rows into MEASURED ones and is the single highest-impact move of Step 02. The toolset doesn't describe this pattern — I improvised it based on Step 01's G-01 handoff.
- **Proposed toolset change:** Add a "Local Evidence Collection" subsection to `step-02`. Content: when to prompt the practitioner to execute commands vs. rely on AI tool access; what commands are typically useful at each step (audit commands for dependency scans, `time` wrappers for build/test benchmarks, `git log --tag` for release cadence, `wc -l` and similar for codebase metrics); how to fold scan output into baseline rows. Parallel section could be added to `step-01` for initial code inspection.
- **Priority:** Medium — works without the formalization (I did it on reflex), but new practitioners won't know to do this.
- **Status:** Acted (v1.1 toolset revision)

### Observation 9 — Subject version can drift silently between steps

- **Source step:** Step 02
- **Nature:** Bug (data hygiene)
- **Evidence:** Step 01 captured subject version as `v1.2.1` throughout. Step 02's re-verification revealed current is `v1.3.2`. The drift happened because I projected from a stale search result + practitioner-mentioned npm publish date without explicitly confirming the version string. The Step 01 artifact contains the wrong version number in multiple places.
- **Proposed toolset change:** Add a "Version & Identity Re-Verification" instruction at the start of every step beyond Step 01. Specifically: re-verify subject version identifier, package version, and any other first-order identifiers before continuing. One targeted search + practitioner confirmation is sufficient. Should appear in `step-00` behavioral rules.
- **Priority:** Medium — version drift is low-consequence but damages artifact accuracy; fixing in Step 06 synthesis is possible but should be unnecessary.
- **Status:** Acted (v1.1 toolset revision)

### Observation 10 — Step-01 hypothesis findings should flow into Step-02 as verification tasks

- **Source step:** Step 02
- **Nature:** Gap (cross-step linkage)
- **Evidence:** Step 01 logged F-14 as "OSV scan output suppression (suspected)." Step 02 happened to confirm it through the direct `osv-scanner` invocation, but only because the practitioner ran OSV among the audit commands. If the scan commands had been different, F-14 would have remained "suspected" in the final register. More broadly, Step 01 findings with "suspected" or "[CONFIRM needed]" tags should flow into Step 02 as explicit verification tasks rather than being re-encountered opportunistically.
- **Proposed toolset change:** Step-01's artifact template should include a "Verification Tasks for Step 02" subsection that lists all [CONFIRM] / "suspected" findings with explicit verification paths. Step-02 should then consume that subsection at its start and allocate measurement time to each. This converts the chance of confirmation into the discipline of confirmation.
- **Priority:** Medium — pattern will recur every Phase 1 run; toolset should bake it in.
- **Status:** Acted (v1.1 toolset revision)

### Observation 11 — Some findings surface better through measurement than interview

- **Source step:** Step 02
- **Nature:** Pattern
- **Evidence:** Several Step 02 findings (F-34 husky gate sub-2s runtime, F-35 full cycle under 21s, F-36 pending-tests root cause) could not have been produced by interview alone. Practitioner time estimates at that granularity are not reliable; only `time` measurements + test-output inspection reveal the actual numbers. Separately, F-13 (Snyk silent-skip) was upgraded from "confirmed" in Step 01 to "MEASURED bug with concrete evidence" in Step 02 because the scan output showed Snyk can run authenticated and return 24 issues — whereas the husky gate silently skips when unauthenticated. The measurement discipline is paying off.
- **Proposed toolset change:** None specific — this is more a design-philosophy observation that validates the MEASURED/ESTIMATED/BELIEVED/UNMEASURED tagging discipline in `step-02`. Consider calling out in `step-00` or `step-02` instructions: *"Some findings that appear to be practitioner-knowable are actually measurement-knowable. Prefer measurement over interview when the distinction matters."*
- **Priority:** Low — reinforcement of an existing discipline.
- **Status:** Acted (v1.1 toolset revision)

### Observation 12 — Existing issue tracker content never consulted

- **Source step:** Surfaced at Step 03; affects Steps 01 through 03
- **Nature:** Gap (significant)
- **Evidence:** Through Steps 01 and 02 I never asked whether Diamonds has an open GitHub issues list. An issue tracker is a standard brownfield evidence stream that captures accumulated practitioner knowledge about bugs, features, and tasks — which are *exactly* the Step 03 must-change and nice-to-improve candidates we are now trying to construct from scratch. By not consulting the tracker, I forced the practitioner to either reconstruct open issues from memory during the Step 03 interview or accept incomplete registers. The practitioner flagged this gap explicitly during Step 03.
- **Proposed toolset change:** Add a standing question to `step-01` in the "System Context" cluster: *"Does this project have an issue tracker — GitHub Issues, GitLab Issues, Jira, a TODO.md, a `notes/` directory, or any other backlog artifact? If yes, that tracker is evidence input for this step and for Step 03. List its location."* Then, in `step-03` (must-change and nice-to-improve register construction), add an explicit instruction: *"Consult the issue tracker enumerated in Step 01. Every open issue is a candidate for classification into must-change, nice-to-improve, or incidental. Do not construct registers from memory when a written backlog exists."* Both changes are low-effort and high-value.
- **Priority:** High — affects the quality of Step 03 registers on any project that has an issue tracker, which is nearly all of them. In an extreme case, this gap could produce a must-change register that omits bugs the practitioner explicitly recorded as needing fixes.
- **Status:** Acted (v1.1 toolset revision). **Mitigation applied during the Diamonds dogfooding run:** proceeded with the Step 03 interview but added an explicit issue-tracker consultation question before producing the Step 03 artifact, so the register was not artificially incomplete. **v1.1 formalization:** Issue Tracker Consultation section added to step-03 prompt, mandating classification of every open issue into MC / NTI / Incidental / Dropped; issue-tracker presence question added to step-01 System Identification cluster.

### Observation 13 — MCP connector activation is not deterministic in-session

- **Source step:** Step 03
- **Nature:** Technical / environmental
- **Evidence:** Practitioner added GitHub MCP server READ access. First `tool_search` after activation returned only Context7 tools; practitioner requested a retry; a second attempt returned the full GitHub tool suite (`list_issues`, `search_issues`, `issue_write`, etc.). Retry-on-user-prompt worked; no configuration change occurred between the two attempts. The MCP tool activation appears to have a propagation delay or requires a specific trigger that isn't immediately obvious.
- **Proposed toolset change:** Add a note to the Building Block Discovery pattern (Observation 1 / 2) — when practitioner activates a new MCP connector during a session, AI should: (a) attempt tool access once, (b) if tools not found, report clearly what's missing and ask practitioner to confirm activation, (c) retry once when practitioner confirms. Do not assume the first failed search means the connector isn't available. Do not make the practitioner debug the activation themselves.
- **Priority:** Low — this is a Claude/MCP-infrastructure behavior, not a toolset behavior, but worth documenting so future practitioners don't get confused.
- **Status:** Acted (v1.1 toolset revision)

### Observation 14 — GitHub issue count per practitioner vs. actual differs

- **Source step:** Step 03
- **Nature:** Minor evidence-reconciliation pattern
- **Evidence:** Practitioner reported "8 issues" in the repo. GitHub MCP pull returned 10 total (7 open, 3 closed). The discrepancy is likely from the practitioner counting open issues with slightly imperfect recall, or including some closed-but-recently-interesting issues. Not a problem — just worth noting that self-reported counts of backlog items routinely differ from actual counts by small integers. This matters for toolset design because the Must-Change register construction (Step 03 Q2) depends on having the correct backlog, not the remembered backlog.
- **Proposed toolset change:** When integrating an issue-tracker consultation (per Observation 12's proposed fix), do not ask the practitioner for a count or list from memory. Pull the actual list via MCP/tool and present it back. If MCP unavailable, paste is the fallback but the AI should not trust practitioner-from-memory counts for the register construction.
- **Priority:** Low — sub-pattern of Observation 12's broader gap.
- **Status:** Acted (v1.1 toolset revision)

### Observation 15 — The "draft-and-react" interview mode is efficient for decision-heavy steps

- **Source step:** Step 03
- **Nature:** Pattern (positive — worth codifying)
- **Evidence:** Step 03 used a draft-and-react mode where I presented complete draft registers (Must-Keep, Must-Change, NTI, Incidental) for the practitioner to Accept/Amend/Drop/Move. This was substantially faster than asking question-by-question from a blank register. The practitioner could reason about the overall shape of each register and push back on specific items. For Step 03's 9 + 20 + 7 + 8 = 44 scope decisions, question-by-question would have required a long session; draft-and-react took four rounds of review and collected all decisions in a tight interview.
- **Proposed toolset change:** `step-03` should explicitly describe draft-and-react as the recommended interview mode for decision-heavy steps. Step-01 and Step-02 are discovery-heavy — question-by-question is appropriate. Step-03 is decision-heavy — draft-and-react is appropriate. The toolset should codify the distinction. Might apply to Step-04 (risk/debt register) and Step-05 (component catalog) too — both are decision-heavy.
- **Priority:** Medium — affects interview efficiency for practitioner time cost.
- **Status:** Acted (v1.1 toolset revision)

### Observation 16 — Practitioner-proposed architectural restructuring during Must-Change

- **Source step:** Step 03
- **Nature:** Pattern (positive)
- **Evidence:** During Must-Change register review (MC-04), practitioner rejected the draft and proposed a better architectural framing (multi-party strategies as separate npm packages following hub-and-spoke pattern rather than in-core implementations). The draft-and-react mode surfaced this because the draft was concrete enough to be disagreeable. A more abstract question ("what should multi-party deployment look like?") would have produced a more abstract answer that could have hidden the architectural insight.
- **Proposed toolset change:** None — this is a validation that draft-and-react enables practitioner-side course correction. Consider adding to `step-03`: *"If the practitioner rejects a draft MC and proposes a different direction, treat this as high-signal input. The draft's rejection is often more architecturally informative than the draft's acceptance."*
- **Priority:** Low — philosophical reinforcement, not a concrete gap.
- **Status:** Acted (v1.1 toolset revision)

### Observation 17 — Issue tracker as Must-Change input works as predicted

- **Source step:** Step 03
- **Nature:** Pattern (validates Observation 12's proposed fix)
- **Evidence:** Once the GitHub issue list was pulled, 4 of the 7 open issues directly mapped to must-change entries (MC-16 from Issue #9, MC-17 from Issue #10, MC-20 from Issue #5, MC-06/08 from Issue #3). 2 issues (#4 Foundry, #2 website) mapped to NTIs. 1 issue (#8 provider type) moved to NTI with practitioner-documented rationale. Zero issues were lost in the classification. If Observation 12 had been addressed before this dogfooding run started, these classifications would have happened at Step 03 naturally instead of requiring explicit retrieval.
- **Proposed toolset change:** Confirms Observation 12's proposed fix is the right shape. Additionally — when the issue tracker is consulted during Step 03, every open issue should be explicitly classified in the artifact (into MC, NTI, Incidental, or dropped with rationale) so no backlog item disappears silently.
- **Priority:** Medium — tied to Observation 12 resolution.
- **Status:** Acted (v1.1 toolset revision)

### Observation 18 — Register-construction surfaces new MCs beyond Step 03

- **Source step:** Step 04
- **Nature:** Pattern (worth codifying)
- **Evidence:** Step 04 register construction produced 2 new MCs (MC-21 private key refactor, MC-22 dev-env CI smoke test) and 1 MC amendment (MC-12 npm provenance) — items that were not surfaced during Step 03's Must-Change interview. Each emerged from a specific register question that Step 03 didn't ask: SR-03 forced the private-key question; SR-07 forced the provenance question; PR-06 forced the dev-env-CI question. Step 03's pillar-based framing was too high-level to surface these specific decisions.
- **Proposed toolset change:** The toolset README should explicitly say Step 04 is *not just categorization* — it produces new MCs and refines existing ones. Currently, `step-04.prompt.md` describes itself as "inventory" work, which may understate the net-new-output dimension. The prompt should explicitly tell practitioners: "Expect 2-4 net-new MCs to emerge here; expect 1-2 MCs from Step 03 to be amended. This is by design."
- **Priority:** Medium — affects practitioner expectation-setting and helps the step-03 vs step-04 division of labor become clearer.
- **Status:** Acted (v1.1 toolset revision)

### Observation 19 — Standards-conformance framing for brownfield Compliance works

- **Source step:** Step 04
- **Nature:** Pattern (positive — toolset discipline working)
- **Evidence:** For Diamonds (no regulatory compliance), the step-04 prompt's "compliance" framing was initially unclear. The standards-conformance reframing (claimed-vs-enforced conformance to standards Diamonds explicitly adopts: ERC-2535, Hardhat plugin conventions, npm publication hygiene, TypeScript declaration correctness) made the register tractable. The resulting CC register had 4 clean entries, all of which resolved inside existing MCs/NTIs — which is the *correct* outcome for a project with no direct compliance burden. Without the reframing, the Compliance register would have been either empty (losing useful information) or contaminated with non-compliance items.
- **Proposed toolset change:** `step-04.prompt.md` should describe the brownfield-specific alternative framing explicitly. Content: "If the project has no regulatory compliance burden (per Specify H-06), do not leave Compliance empty. Use the *standards-conformance* framing: for each standard or convention the project claims to implement or follow, document (a) the claim, (b) what's actually enforced, (c) any divergence. This typically produces 3-6 entries for a library like ours." This reframing is a repeatable pattern, not a Diamonds-specific improvisation.
- **Priority:** Medium — affects every brownfield Phase 1 application to a non-regulated project, which is most of them.
- **Status:** Acted (v1.1 toolset revision)

### Observation 20 — Worst-case-scenario narrative catches real synthesis

- **Source step:** Step 04
- **Nature:** Pattern (positive — toolset discipline working)
- **Evidence:** The worst-case scenario narrative, forced by step-04's discipline, produced a genuinely useful synthesis: naming the "gap between what Diamonds claims and what Diamonds can prove" as the underlying mechanism across all three branches (exploitable CVE / silent adopter walk / auditor flag). This insight was not present in Steps 01, 02, or 03 individually — it emerged only when the nightmare was explicitly articulated. The narrative also made clear *why* Tier 1 + Tier 3 partial completion is stronger than Tier 1 + Tier 2 partial completion (because productization scaffold closes the claims-vs-proof gap even when capability work hasn't landed).
- **Proposed toolset change:** None — this validates the worst-case-scenario discipline as net-positive. Consider adding to `step-04.prompt.md` instruction: "The narrative should explicitly seek a common mechanism across branches. If the narrative reads like three unrelated bad outcomes, the underlying synthesis has been missed; keep writing until the mechanism is named." This guidance would make the pattern repeatable.
- **Priority:** Low — enhancement to existing working discipline.
- **Status:** Acted (v1.1 toolset revision)

### Observation 21 — Step 05 catalog surfaces scope expansions to prior MCs

- **Source step:** Step 05
- **Nature:** Pattern (similar to Obs 18 about Step 04)
- **Evidence:** Step 05 catalog-construction surfaced five scope expansions to existing Must-Changes, not net-new MCs: (a) MC-01 gained a lodash Branch A/B choice (upgrade vs. replace), (b) MC-07 absorbed working example scripts (previously considered as candidate MC-23), (c) MC-19 expanded to include 5 additional devDep retirements (@socketsecurity/cli, web3, winston, abi2oas, uint32+types) plus the entire scripts/ directory (not just scripts/devops/), (d) MC-09 gained a specific Replace disposition for monitoring-troubleshooting.md, (e) multiple small docs dispositions fed into MC-07's content list. The expansions were consequential but none required net-new MC authorship — existing MCs absorbed the additional scope cleanly.
- **Proposed toolset change:** `step-05.prompt.md` should explicitly say: "Step 05 catalog-construction will typically surface 3-5 scope expansions to existing MCs. This is by design — the catalog examines every component individually, which reveals work the higher-level Step 03/04 registers couldn't enumerate. Scope expansion is preferred over new MC authorship unless the expansion is architecturally distinct."
- **Priority:** Medium — helps practitioners calibrate expectations and prevents over-proliferation of MCs.
- **Status:** Acted (v1.1 toolset revision)

### Observation 22 — Component catalog as productization diagnostic

- **Source step:** Step 05
- **Nature:** Pattern (positive — reveals structural insight)
- **Evidence:** The Step 05 disposition summary revealed that ~35% of Diamonds components are being Retired, not Kept or Upgraded. For a library claiming "productization" as the improvement objective, this is a strong diagnostic signal: the project is not yet productized in its current shape, and the improvement cycle involves significant subtraction. A productized library going through improvement typically shows Keep ≫ Upgrade ≫ Retire. Diamonds shows Keep > Retire > Upgrade, with Retire roughly equal to Upgrade. The ratio itself is informative — "this project is accumulating orphan tooling faster than it's being cleaned up, and the cycle is a long-overdue cleanup."
- **Proposed toolset change:** Add to `step-05.prompt.md` a "Disposition Ratio Interpretation" section describing: (a) Keep ≫ Upgrade ≫ Retire pattern (healthy productized library under improvement), (b) Keep ≈ Retire ≫ Upgrade pattern (brownfield cleanup cycle — expected for first productization pass), (c) Upgrade ≫ Keep ≈ Retire pattern (active capability-expansion cycle on stable foundation), (d) Retire ≫ Keep + Upgrade pattern (sunset / consolidation cycle; probably a scope boundary or project termination concern). Each pattern maps to a different Phase 2 sequencing strategy. Diamonds falls clearly in pattern (b); naming this pattern explicitly helps practitioners calibrate their Phase 2 approach.
- **Priority:** Medium — adds interpretive value to the disposition summary that currently exists as raw counts.
- **Status:** Acted (v1.1 toolset revision)

### Observation 23 — "Everything in scripts is old" is a correction that cascades

- **Source step:** Step 05
- **Nature:** Bug (of analyst behavior) — I assumed scripts/deploy-rpc.ts was current because Step 01 called RPCDeploymentStrategy current
- **Evidence:** I conflated "the strategy class is production-current" with "the example scripts are production-current." Practitioner had to correct: the class in src/strategies/RPCDeploymentStrategy.ts is production-current; the scripts/deploy-rpc.ts wrapper around it is an outdated example. Different artifacts, different dispositions. My draft catalog had deploy-rpc.ts and upgrade-rpc.ts as Keep before the correction.
- **Proposed toolset change:** In step-05.prompt.md, add explicit guidance: "A 'current' source module does not imply its example scripts are current. Treat example scripts and their source dependencies as independently cataloged. If a source module is marked Keep, that does not confer Keep status to scripts that happen to use it." Also: this observation reinforces Observation 7 (search returns relevant but not complete) — I should not have assumed by extension. The Comprehensiveness Check pattern from Step 03 Q4 should apply to Step 05 too: ask the practitioner whether any category of artifact is being treated incorrectly by inheritance from a related artifact's disposition.
- **Priority:** Medium — common AI-reasoning error that the toolset should warn against.
- **Status:** Acted (v1.1 toolset revision)

### Observation 23 — "Everything in scripts is old" is a correction that cascades

- **Source step:** Step 05
- **Nature:** Bug (of analyst behavior) — I assumed scripts/deploy-rpc.ts was current because Step 01 called RPCDeploymentStrategy current
- **Evidence:** I conflated "the strategy class is production-current" with "the example scripts are production-current." Practitioner had to correct: the class in src/strategies/RPCDeploymentStrategy.ts is production-current; the scripts/deploy-rpc.ts wrapper around it is an outdated example. Different artifacts, different dispositions. My draft catalog had deploy-rpc.ts and upgrade-rpc.ts as Keep before the correction.
- **Proposed toolset change:** In step-05.prompt.md, add explicit guidance: "A 'current' source module does not imply its example scripts are current. Treat example scripts and their source dependencies as independently cataloged. If a source module is marked Keep, that does not confer Keep status to scripts that happen to use it." Also: this observation reinforces Observation 7 (search returns relevant but not complete) — I should not have assumed by extension. The Comprehensiveness Check pattern from Step 03 Q4 should apply to Step 05 too: ask the practitioner whether any category of artifact is being treated incorrectly by inheritance from a related artifact's disposition.
- **Priority:** Medium — common AI-reasoning error that the toolset should warn against.
- **Status:** Acted (v1.1 toolset revision)

### Observation 24 — Step 06 as capstone works by consolidating, not re-analyzing

- **Source step:** Step 06
- **Nature:** Pattern (positive — toolset discipline working)
- **Evidence:** Step 06 produced the Information Report by synthesizing Steps 01-05 without re-performing any of their analytical work. Every baseline row, finding, and disposition in the Step 06 artifact traces to a specific prior-step source. The synthesis added value in four specific ways: (a) executive summary framing ("the gap between what Diamonds claims and what Diamonds can prove"), (b) priority-ordered Phase 2 input with tier structure, (c) minimum-viable-completion floor analysis, (d) forward handoffs to Phases 2/3/5/6/7 enumerated explicitly. No net-new findings, no net-new decisions. This is the correct shape for a capstone.
- **Proposed toolset change:** None — step-06.prompt.md appears to be working correctly. Consider a clarifying note: "Step 06 is synthesis-only. If Step 06 is producing net-new findings, decisions, or dispositions, something was missed in Steps 01-05 — pause Step 06 and fix the upstream gap."
- **Priority:** Low — validates existing design.
- **Status:** Acted (v1.1 toolset revision)

### Observation 25 — Scorecard self-evaluation with CONDITIONAL is more useful than uniformly green

- **Source step:** Step 06
- **Nature:** Pattern (positive)
- **Evidence:** The Step 06 scorecard rated 5 of 6 principles PASS and 1 (Scoring & Metrics) CONDITIONAL. The CONDITIONAL is about a decision Phase 2 must make (principle weighting) that Phase 1 correctly didn't prescribe — not a Phase 1 failure. Surfacing this as CONDITIONAL rather than padding it into PASS gives Phase 2 an explicit signal: "you must set weights before scoring begins." Uniformly-green scorecards are less useful for downstream phases because they hide decision points. Practitioner accepted the ratings as-is, confirming the honest grade is the useful grade.
- **Proposed toolset change:** Add to step-06.prompt.md: "When self-rating principles, CONDITIONAL is preferred over PASS-with-caveats. A CONDITIONAL rating with explicit rationale surfaces a decision point for the downstream phase; a PASS with buried caveat is easier to miss. Aim for 4-5 PASS + 1-2 CONDITIONAL on a well-executed Phase 1 — uniformly PASS suggests the self-evaluation wasn't honest, uniformly CONDITIONAL suggests Phase 1 didn't do its job."
- **Priority:** Medium — calibrates self-evaluation rigor for future Phase 1 runs.
- **Status:** Acted (v1.1 toolset revision)

### Observation 26 — Phase 1 dogfooding produced 26 observations; that's about right for one pass

- **Source step:** Step 06 (meta-observation on the dogfooding corpus)
- **Nature:** Pattern (quantitative calibration)
- **Evidence:** Phase 1 on Diamonds produced 26 dogfooding observations across 6 steps + Specify. This averages ~4 observations per step, weighted toward early steps (Step 01 and Step 02 each surfaced many) and decision-heavy steps (Step 03 and Step 05). The final observation count is large enough to drive a meaningful v1.1 toolset revision but small enough that end-of-phase review is tractable in a single session. If a future Phase 1 dogfooding run produces <10 observations, that likely means the run is going too smoothly — either the toolset is already mature for that project type (possible) or the practitioner is being insufficiently critical (more likely). If it produces >50, the toolset likely has foundational issues requiring a larger revision than incremental v1.1.
- **Proposed toolset change:** Add to README for the Phase 1 (Existing Projects) Tool Set: "Expected dogfooding observation count per complete Phase 1 run is 20-30. Counts below 10 warrant skepticism about self-criticism rigor; counts above 50 suggest foundational toolset issues rather than incremental improvements."
- **Priority:** Low — calibration guidance for future dogfooding runs.
- **Status:** Acted (v1.1 toolset revision)

---

## Phase 1 Closing — Observation Accounting

**Total observations: 26 across Steps 01-06 + Specify**

**By step of origin:**
- Specify (pre-Step 01): 1, 2 (Building Block Discovery)
- Step 01: 3, 4, 5, 6, 7 (multi-repo scoping, code access, three-timeframes, cross-repo mode, comprehensiveness)
- Step 02: 8, 9, 10, 11 (local evidence, version drift, verification flow, measurement vs interview)
- Step 03: 12, 13, 14, 15, 16, 17 (issue tracker, MCP activation, issue count, draft-and-react, architectural pushback, issue classification)
- Step 04: 18, 19, 20 (net-new MCs in Step 04, standards-conformance framing, worst-case synthesis)
- Step 05: 21, 22, 23 (scope expansions, disposition ratio diagnostic, scripts/inheritance error)
- Step 06: 24, 25, 26 (capstone as consolidation, scorecard rigor, observation-count calibration)

**By priority:**
- High: 4 observations (1, 3, 4, 12)
- Medium: 13 observations
- Low: 9 observations

**By status at Phase 1 close: all 26 Open.** None acted on during dogfooding per Option B protocol. End-of-Phase-1 review converted Open → Acted based on v1.1 toolset revision decisions.

**By status after v1.1 toolset revision (2026-04-20): all 26 Acted.** The end-of-Phase-1 review clustered the 26 observations into 19 change clusters (A–S), all of which were accepted (one — Cluster E — with a refinement to apply the comprehensiveness check to Steps 03 and 05 only, not Step 04). The accepted clusters drove the v1.1 toolset revision, delivered 2026-04-20 across 9 files: README.md (new MCP Servers section + observation-count calibration + Version History), step-00 (Multi-Repo Evidence Scoping, Code Access Calibration, Three-Timeframes Worked Example, Version & Identity Re-Verification, Interview Mode Selection, MCP connector retry pattern), step-00b (new file: Building Block Discovery prompt), step-01 (issue-tracker question, Verification Tasks subsection), step-02 (Local Evidence Collection, Verification Tasks subsection), step-03 (draft-and-react default, Issue Tracker Consultation section, Comprehensiveness Check), step-04 ("expect 2–4 net-new MCs" rule, standards-conformance framing for non-regulated projects, worst-case common-mechanism discipline), step-05 (draft-and-react default, scope-expansion expectation, artifact-inheritance warning, Disposition Ratio Interpretation section, Comprehensiveness Check), step-06 (synthesis-only discipline, scorecard rigor with CONDITIONAL-preferred guidance).

---

## End-of-Phase-1 Review Checklist

At the end of Step 06, review each observation above:

- [ ] Is the observation still relevant given the full Phase 1 experience?
- [ ] Is the proposed toolset change the right change, or should it be revised?
- [ ] Are there observations that should be merged?
- [ ] Are there observations that should be split into multiple changes?
- [ ] What is the priority ordering for acting on the changes?
- [ ] Which changes can be shipped in a v1.1 toolset revision; which need v2?

---

*Appended to at the end of each Phase 1 step. Acted on only after Step 06 synthesis completes.*
