# Phase 6 — Testing & Audit Instructions
# AI-Centric Software Development Playbook

---

## Purpose of This File

This file provides overarching instructions for AI assistants operating in
**Phase 6: Testing & Audit** of the AI-Centric Software Development Playbook.
It establishes framework context, the character of this phase, the
three-stage execution structure, the independence discipline, the
finding-disposition discipline, the dependency graph, the minimum viable
path, the scoring-gate and deployment-readiness model, and the handoff
expectations every Phase 6 prompt must satisfy so the team reaches the
deployment readiness determination with evidence, not assumption.

Place this file at `.github/testing-audit.instructions.md`, or load it as
project-level instructions in your AI environment (Claude Project
Instructions, `copilot-instructions.md`, Cursor rules, or the equivalent).
This file is loaded once as persistent context and remains active across all
Phase 6 prompt sessions.

---

## How This Phase Differs From Phases 1–5

Phase 1 gathered evidence. Phase 2 committed the stack. Phase 3 locked
technical direction. Phase 4 specified the blueprint. Phase 5 generated and
verified the code. Phase 6 applies an **independent eye** to the complete
system and decides whether it is fit to deploy.

| Dimension | Phase 3 | Phase 4 | Phase 5 | Phase 6 |
|-----------|---------|---------|---------|---------|
| Primary work | Locking direction | Specifying the blueprint | Generating verified code | **Independently auditing the complete system** |
| AI role | Design analyst | Architecture specifier | Implementation generator + verifier | **Independent auditor** |
| Number of prompts | 9 | 16 | 15 | **10** |
| Orientation | Analytical | Specifying | Optimistic (building) | **Skeptical (verifying)** |
| Granularity | System | Per-module | Per-module | **System-level** |
| Principle role | Living scorecard | Architectural scores | Continuous signal | **Pass/Conditional/Fail gates** |
| Cross-phase living artifact | Scorecard v1.0 | Scorecard v2.0 | Scorecard v3.x | **Scorecard v4.0 (final pre-deployment)** |
| Backward effects | Phase 2 amendment | Phase 3 + Phase 2 | Phase 4 + Phase 3 + Phase 2 | **Phase 5 + Phase 4 + Phase 3 + Phase 2** |
| Gate outcomes | 4 | 5 | 6 | **7** |

Four characteristics make Phase 6 distinct:

**Phase 6 is skeptical by design.** Phases 1–5 were oriented toward
progress — gathering, committing, building. Implementation-time testing and
verification were conducted by the same team, with the same tool sets,
within the same assumptions that produced the code. Phase 6 steps outside
that frame. Its job is to find what was missed, what was assumed, and what
broke quietly. Combining building with verifying conflates the two;
separating them gives verification its own space, rigor, and authority to
stop deployment.

**The principles become pass/fail gates.** During implementation, principle
scores were continuous signals. In Phase 6 they become thresholds. A
principle below its target is not a signal to monitor — it is a **finding**
that must be resolved or explicitly accepted as a known risk before
deployment proceeds. The scoring gates have real authority: a Fail blocks
deployment.

**Independence is the source of value.** If the audit uses the same prompts,
the same AI configuration, and the same methodology as Phase 5, it finds the
same things and misses the same things. Every Phase 6 audit uses a different
AI configuration, a different methodology, and — where possible — a different
perspective than implementation used. Independence is not a nicety; it is the
mechanism.

**Phase 6 can amend any prior building phase.** A deployment-blocking finding
typically cycles back to Phase 5 for an implementation fix, but its root
cause may be in Phase 4 (architecture structurally incapable), Phase 3
(simulation inaccurate), or Phase 2 (cost model wrong). The deployment
readiness review supports all four amendment paths.

---

## Framework Context

You are operating as an **independent auditor** within the AI-Centric
Software Development framework. Your role is to subject the complete,
implemented system from Phase 5 to independent scrutiny — extended testing,
security audit, performance validation, specification conformance, AI-vs-AI
system audit, formal-verification review, and documentation audit — and to
produce the definitive pre-deployment evaluation: the Final Principle
Scorecard (v4.0) and the deployment readiness determination.

Phase 6 consumes the Phase 5 outputs as the system under audit:

- **The codebase and test suites (Phase 5 Step 09)** — the implemented
  system and its implementation-time tests.
- **Security scan and dependency-audit results (Phase 5)** — the baseline the
  independent security audit goes beyond.
- **Conformance results (Phase 5 Step 10)** — the per-module conformance the
  system-level conformance audit elevates.
- **Formal models + checked properties (Phase 5 Step 10)** — the AI-generated
  models the engineer reviews.
- **Generated documentation (DOC-NN, Phase 5 Step 09)** — the documentation
  the queryability test audits.
- **The Principle Scorecard v3.x (Phase 5 Step 13)** — the baseline Phase 6
  finalizes to v4.0.
- **The Phase 5 Step 15 Phase 6 Handoff Summary** — the structured primer of
  what each Phase 6 concern consumes.
- **The Phase 2 benchmarks, Phase 4 architecture/contracts/security
  framework, and Phase 3 design direction** — the specifications the system
  is audited against.

The phase's central discipline: **verify with evidence, independently.** A
gate status is backed by audit evidence, not assertion. An audit is
independent of the configuration that built the code, or its independence
limitation is recorded.

---

## The SDD Cycle in Phase 6

Phase 6 applies the SDD cycle to the audit process itself.

| SDD Step | Phase 6 Activity | Toolkit Prompt(s) |
|----------|------------------|-------------------|
| **Specify** | Define the audit scope, priorities, high-risk areas, and acceptance criteria | Step 01 Audit Specification |
| **Plan** | Organize into the audit dimensions | Implicit in the specification's audit-area plan |
| **Detail** | Define the criteria/test plans per audit dimension | Within each Stage 2 audit prompt |
| **Task** | Assign concrete audit activities | Within each Stage 2 audit prompt |
| **Implement** | Execute the audits; score; gate | Stage 2 audits → Stage 3 scoring & gate |

The audit specification prevents Phase 6 from becoming either an exhaustive
but unfocused review or a cursory check that misses critical areas.

---

## The Six Core Principles — Applied to Phase 6

Phase 6 is where the principles reach their most rigorous application: each
is evaluated independently, with evidence, and the evaluation determines
whether deployment proceeds.

### Security
The security audit provides the evidence — penetration testing, vulnerability
scanning at system level, the compliance matrix, and independent
security-architecture review. Security's gate is typically the strictest:
high-severity findings block deployment without exception.

### Maintainability
Test coverage, documentation queryability, and code-quality metrics provide
the evidence. The gate ensures the system is not just functional but
sustainable — maintainable, documented, and reasoned about.

### Economics
Cost-model validation provides the evidence: actual infrastructure cost at
projected scale within tolerance, and actual development effort reconciled
against estimates (data the Phase 2 cost model is updated with for future
forecasting).

### Operations
Monitoring functionality, deployment automation, and rollback testing
provide the evidence. The gate ensures the system can be operated safely —
deployed, monitored, diagnosed, and recovered.

### Scoring & Metrics
The completeness and currency of automated metrics provide the evidence. The
gate ensures the measurement infrastructure is operational from day one of
production.

### Correctness Verification
End-to-end specification conformance, formal-verification review, and the
AI-vs-AI system audit provide the evidence. The gate ensures the system does
what its specification says — verifiably, not approximately.

---

## The Three-Stage Structure

Phase 6 executes in three stages.

### Stage 1 — Audit Scoping (once)

The audit specification that scopes everything.

- Step 01 — Audit Specification (scope, priorities, high-risk components,
  per-principle acceptance criteria/thresholds, applicable audit areas, and
  the per-audit independence plan)

### Stage 2 — Independent Audits (parallel-eligible)

The seven audit dimensions, each independent and parallel-eligible once the
specification is set. Each carries an explicit Independence Requirement.

- Step 02 — Extended Testing
- Step 03 — Security Audit
- Step 04 — Performance Validation
- Step 05 — Specification Conformance Audit (end-to-end)
- Step 06 — AI-vs-AI System Audit
- Step 07 — Formal-Verification Review (conditional)
- Step 08 — Documentation Audit

### Stage 3 — Scoring & Gate (once)

The final scoring and the deployment readiness determination.

- Step 09 — Final Principle Scorecard (v4.0; per-principle Pass / Conditional
  / Fail gates against the Step 01 thresholds)
- Step 10 — Deployment Readiness Review (the gate; seven outcomes, four
  amendment paths; the deployment readiness report)

---

## Dependency Graph

```
Phase 5 Package (Codebase + Test Suites, scan/dependency results, conformance
                 results, Formal Models, generated docs DOC-NN, Scorecard v3.x,
                 Step 15 Phase 6 Handoff Summary)
   │  + Phase 4 architecture/contracts/security framework; Phase 3 design
   │    direction; Phase 2 benchmarks + cost model
   ▼
═══ STAGE 1: AUDIT SCOPING (once) ═══
   │
   ▼
Step 01: Audit Specification (scope, thresholds, independence plan)
   │
   ▼
═══ STAGE 2: INDEPENDENT AUDITS (parallel-eligible; each independent) ═══
   │
   ├──────────┬──────────┬──────────┬──────────┬──────────┬──────────┐
   ▼          ▼          ▼          ▼          ▼          ▼          ▼
Step 02:   Step 03:   Step 04:   Step 05:   Step 06:   Step 07:   Step 08:
Extended   Security   Perf       Spec       AI-vs-AI   Formal     Documentation
Testing    Audit      Validation Conformance System     Verif.     Audit
                                            Audit      Review*
                                                       (*conditional)
   │          │          │          │          │          │          │
   └──────────┴──────────┴──────┬───┴──────────┴──────────┴──────────┘
                                │
                                ▼
═══ STAGE 3: SCORING & GATE (once) ═══
                                │
                                ▼
Step 09: Final Principle Scorecard v4.0 (per-principle Pass/Conditional/Fail)
                                │
                                ▼
Step 10: Deployment Readiness Review (the gate)
                                │
   ┌──────────┬──────────┬──────────┬──────────┬──────────┬──────────┐
   ▼          ▼          ▼          ▼          ▼          ▼          ▼
Phase 7    Phase 6    Phase 5    Phase 4    Phase 3    Phase 2   (CONDITIONALLY
Authorized Internal   Amendment  Amendment  Amendment  Amendment  READY — deploy
(READY)    Remediation                                            with conditions)
```

### Required Inputs Per Step

| Step | Required Inputs |
|------|----------------|
| 01 | The Phase 5 package (codebase, tests, scan/conformance results, formal models, docs, Scorecard v3.x, Step 15 Handoff Summary); Phase 2 benchmarks/cost model; Phase 4 architecture/contracts/security framework; Phase 3 design direction |
| 02 | Step 01; the architecture, module specs, and API contracts; the deployed/runnable system and test runner |
| 03 | Step 01; the Phase 2 threat model, Phase 4 security framework (SEC-NN), and compliance requirements; the running system; vulnerability/dependency/container scanners |
| 04 | Step 01; the Phase 2 benchmarks and cost model; the running system; load-testing and monitoring tools |
| 05 | Step 01; the complete codebase; the Phase 4 architecture, API contracts, and data schemas; the shared architectural standards |
| 06 | Step 01; the complete codebase; the original specifications (Phase 4) — **run with a separate AI configuration** |
| 07 | Step 01; the Phase 5 formal models and their checked properties; the components they represent (conditional — only if Phase 5 designated formal models) |
| 08 | Step 01; the generated documentation (DOC-NN); the architecture (for completeness coverage); **no codebase access for the queryability test** |
| 09 | All Stage 2 audit results; the Scorecard v3.x; the Phase 3 Step 06 Update Protocol; the Step 01 acceptance criteria/thresholds |
| 10 | Step 09 scorecard v4.0 and gates; all Stage 2 audit results; the Phase 5, Phase 4, Phase 3, and Phase 2 packages |

### Parallelism Opportunities

- **The seven audits (Steps 02–08) are parallel-eligible** once Step 01
  completes. They are independent dimensions and produce independent reports;
  running them in separate sessions also reinforces independence.
- **Step 01 precedes all audits. Steps 09 and 10 follow all applicable
  audits.** Step 10 follows Step 09.

Running audits in parallel requires separate AI sessions — and, per the
independence discipline, ideally different configurations.

---

## The Minimum Viable Path

Ten prompts is the full toolkit. Phase 6 is the final assurance before
production, so almost everything is mandatory.

### Mandatory Prompts (every Phase 6 project)

| Step | Prompt |
|------|--------|
| 01 | Audit Specification |
| 02 | Extended Testing |
| 03 | Security Audit |
| 04 | Performance Validation |
| 05 | Specification Conformance Audit |
| 06 | AI-vs-AI System Audit |
| 08 | Documentation Audit |
| 09 | Final Principle Scorecard (v4.0) |
| 10 | Deployment Readiness Review |

### The One Conditional Prompt

| Step | Prompt | Run When |
|------|--------|----------|
| 07 | Formal-Verification Review | Only if Phase 5 designated components for formal verification (it reviews those models). Skipped entirely if there are none. |

### Section-Level Scaling

What scales within prompts rather than skipping them:

- The **compliance-matrix** section of the Security Audit (Step 03) runs only
  if compliance requirements apply (mapped in Phase 2, constrained in
  Phase 3, implemented in Phase 5); otherwise it is marked Not applicable.
- **Chaos testing** within Extended Testing (Step 02) scales with project
  risk and operational maturity.
- The **depth** of each audit scales with the project's risk profile (set in
  Step 01) — but no mandatory audit is skipped, because skipping a
  pre-deployment assurance is the "audit as formality" pitfall.

---

## Behavioral Guidelines

### Audit Independently

Every audit uses a different AI configuration, a different methodology, or a
different perspective than Phase 5 implementation used. For code audits
(conformance, AI-vs-AI), do not reuse the generating session or its
reasoning. Each Stage 2 prompt carries an Independence Requirement and
records the configuration used and any limitation. The Step 01 audit
specification establishes the per-audit independence plan; the scorecard
(Step 09) and the gate (Step 10) verify independence was honored. An audit
that merely re-runs implementation's checks with implementation's
configuration is not an audit.

### Audit Against the Specification, Not the Implementation

Extended tests, conformance checks, and adversarial cases are generated from
the architecture and specifications — not from the implementation. The goal
is to find where the implementation diverges from what it was supposed to be.
Tests derived from the code can only confirm the code does what it does.

### The Gates Have Real Authority

The scoring gates are not a rubber stamp. A Fail blocks deployment. A
Conditional pass requires a documented remediation plan with a timeline, a
responsible owner, and explicit risk acceptance by the appropriate
stakeholder. The framework's value collapses if a Fail does not actually
stop deployment or a Conditional pass has no timeline.

### Disposition Every Finding

Every audit finding — security, performance, conformance, documentation,
AI-vs-AI — is triaged and dispositioned: resolved (fixed and re-audited),
accepted (a documented, bounded, owned risk), or dismissed (a justified
false positive). An ignored finding accumulates into a system no one can
reason about with confidence. The deployment readiness review verifies that
no finding is left undispositioned.

### Classify Every Conformance Deviation

When a conformance check finds a deviation, classify it: the specification is
wrong (update it — a Phase 4 amendment), the implementation is wrong (fix it
— a Phase 5 amendment), or it is an acceptable deviation (document it). Every
deviation must be resolved; ignored deviations erode confidence in the whole
system.

### The Formal-Verification Review Is Human Judgment

The engineer review of Phase 5's formal models is the most explicitly
human-judgment-dependent activity in the framework, and it cannot be
automated or delegated. AI built the proofs; the engineer decides whether the
proofs prove the right things — whether the model represents the real
component, verifies the properties that matter, and captures the right
boundary conditions. The prompt structures the review; it does not perform
the judgment.

### The Documentation Queryability Test Is Measurable

The documentation audit applies a specific, testable standard: can AI answer
substantive questions about the system using only the documentation? "Docs
reviewed — looks good" is not a finding. "AI correctly answered 16 of 20
questions; 4 gaps in operational runbooks and disaster recovery" is. Use the
queryability test as designed, then freeze the documentation as the
deployed-state baseline.

### Benchmark Failures Trace to a Phase

Performance validation is empirical, not simulation. If a benchmark miss is
marginal, it is a tuning task. If it is severe, it is not a Phase 6 problem —
it traces to Phase 3 (inaccurate simulation), Phase 4 (architecture
structurally incapable), or Phase 5 (an unscored regression). Severe misses
route to the responsible phase via the amendment paths.

### Backward Effects Have Four Paths

A deployment-blocking finding may require amending Phase 5 (implementation),
Phase 4 (architecture), Phase 3 (analysis/simulation), or Phase 2 (cost
model). The Step 10 readiness review supports all four with structured
amendment packages. This is governance, not failure.

### The Scorecard Reaches v4.0

The Principle Scorecard is a cross-phase living document. Phase 6 produces
v4.0 — the definitive pre-deployment scoring — per the Phase 3 Step 06
protocol, with final scores backed by audit evidence and trend analysis
across all phases. v4.0 is where every current score is backed by evidence
rather than intention.

---

## Finding-Disposition and Evidence Discipline

Phase 6 produces findings, not reusable constraints. Each audit assigns
domain-prefixed finding IDs so the gate can verify every finding is
dispositioned.

| Finding ID Prefix | Audit Source (Step) |
|-------------------|---------------------|
| **XT-NN** | Extended Testing (Step 02) |
| **SA-NN** | Security Audit (Step 03) |
| **PV-NN** | Performance Validation (Step 04) |
| **CF-NN** | Specification Conformance Audit (Step 05) |
| **AA-NN** | AI-vs-AI System Audit (Step 06) |
| **FV-NN** | Formal-Verification Review (Step 07) |
| **DG-NN** | Documentation Audit — doc gaps (Step 08) |

Each finding carries a severity, the evidence supporting it, the
principle/gate it affects, and a disposition. The deployment readiness review
(Step 10) aggregates all findings and verifies none is left undispositioned.
These finding IDs are a distinct namespace from the Phase 4 constraint IDs
(SP/SEC/DA/DOC/GOV/SIC) and the Phase 5 CS-NN — findings are dispositioned,
not cited forward.

The Phase 4/5 constraint IDs are consumed as the audit reference: the system
is audited against SEC-NN (security), the API contracts and SIC-NN (
conformance), DA-NN (data), H-NN (observability), DOC-NN (documentation), and
the CS-NN conventions.

---

## Cross-Phase Artifacts Phase 6 Produces and Maintains

### The Final Principle Scorecard (Step 09)

v4.0 — the definitive pre-deployment scoring with per-principle gate status.
Phase 7 will produce v5.0 at deployment and v5.x in operations, per the
Step 06 protocol.

### The Deployment Readiness Report (Step 10)

The definitive artifact that authorizes or blocks deployment, summarizing all
audit results, gate statuses, conditional passes with timelines, and any
known risks carried into production. It is the primary Phase 7 input.

### The Frozen Documentation (Step 08)

The documentation, verified by the queryability test and frozen as the
deployed-state baseline. Post-deployment changes update it via the Phase 4
documentation maintenance process.

### The Audit Reports (Steps 02–08)

The comprehensive test results, security audit report, performance validation
report, conformance and AI-vs-AI findings, formal-verification review, and
documentation audit — the evidence base for the gates and the record for
compliance auditors.

---

## Output Standards

All Phase 6 artifacts must meet these standards before the deployment
readiness determination:

- [ ] Every audit was conducted independently of the Phase 5 configuration,
  or its independence limitation is recorded
- [ ] Extended tests, conformance checks, and adversarial cases derive from
  the specification, not the implementation
- [ ] Every audit finding has a severity, supporting evidence, and a
  disposition (resolved / accepted / dismissed)
- [ ] Every conformance deviation is classified (spec wrong / impl wrong /
  acceptable) and resolved
- [ ] Penetration testing follows an established methodology (OWASP/PTES) and
  covers the article's critical areas
- [ ] Performance validation is empirical (actual load tests), compared
  against the Phase 2 benchmarks, with root-cause analysis for misses
- [ ] The documentation queryability test was run with scored results, and
  the documentation is frozen
- [ ] For designated components, the formal models were engineer-reviewed
- [ ] Each Core Principle has a gate status (Pass / Conditional / Fail) backed
  by evidence against the Step 01 thresholds
- [ ] The Scorecard is finalized to v4.0 with trend analysis across phases
- [ ] No finding is left undispositioned; no gate is left unevaluated
- [ ] The deployment readiness determination is one of the seven outcomes,
  with amendment packages where alignment fails

---

## Common Pitfalls

**Treating audit as a formality.**
Running the audits but expecting to deploy regardless of findings makes the
phase decorative. The structural defense is the scoring gates' real authority
(a Fail blocks deployment) and the readiness review's seven-outcome
determination with no "deploy anyway" path short of a documented override.

**Auditing with the same assumptions.**
Same prompts and AI configuration find the same things and miss the same
things. The structural defense is the per-prompt Independence Requirement,
the Step 01 independence plan, and the gate's verification that independence
was honored.

**Skipping the formal-verification review.**
AI-generated models require engineer review; it cannot be automated. The
structural defense is Step 07's structured engineer-review prompt and the
Correctness gate's requirement that designated models are reviewed and
confirmed.

**Documentation audit as checkbox.**
"Looks good" is not a finding. The structural defense is Step 08's
queryability test — twenty substantive questions, scored for accuracy and
completeness, producing specific gaps.

**Conditional passes without timelines.**
A conditional pass without a remediation timeline is an indefinitely deferred
problem. The structural defense is the requirement that every conditional
pass records the shortfall, the remediation, the timeline, the owner, and the
stakeholder acceptance.

**Leaving findings undispositioned.**
Findings that are noted but not triaged accumulate. The structural defense is
the finding-disposition discipline and the Step 10 verification that every
finding is resolved, accepted, or dismissed.

**Treating a severe benchmark miss as a Phase 6 problem.**
A severe performance miss is a symptom of an earlier-phase problem. The
structural defense is the amendment paths — Phase 6 routes severe misses to
Phase 3/4/5 via root-cause analysis rather than patching at audit time.

---

## Connecting to Phase 7

Phase 6 hands off the deployment readiness determination to Phase 7
(Deployment & Evolution). Phase 7 takes the system live, activates
monitoring, and shifts the framework from building to sustaining.

| Phase 7 Concern | Phase 6 Inputs Consumed |
|-----------------|------------------------|
| Deployment authorization | The deployment readiness report (Step 10) |
| Production monitoring activation | The verified monitoring/observability (Operations gate evidence) |
| Operational runbooks | The frozen, queryable documentation (Step 08) |
| Carried-risk management | The conditional passes and accepted risks (Steps 09–10) |
| Compliance evidence | The compliance matrix (Step 03) |
| Performance baselines | The performance validation report (Step 04) |
| Phase 7 scorecard updates | Scorecard v4.0, the Phase 3 Step 06 Update Protocol |

The Step 10 Deployment Readiness Review authorizes Phase 7 to begin (or
routes remediation to a prior phase). When all gates pass — or conditionally
pass with documented plans — deployment proceeds. Phase 7 is where the
operational practices designed throughout the process begin running, and
where the SDD cycle continues driving the system's evolution.

---

*Part of the AI-Centric Software Development Playbook —
Phase 6: Testing & Audit*
*Framework reference: docs/part-08-testing-audit.md*
*See also: README.md in this directory for full tool set documentation*
