# The Six Core Principles — Reference

**Load this file when:** evaluating output against the principles, scoring a decision on a specific principle, writing PRDs that must embed principle-derived requirements, designing a weighted scoring rubric, or when the practitioner asks how a specific principle applies to their current decision.

---

## The Six Principles at a Glance

| # | Principle | Role |
|---|-----------|------|
| 1 | Security | What you're optimizing for |
| 2 | Maintainability | What you're optimizing for |
| 3 | Economics | What you're optimizing for |
| 4 | Operations | What you're optimizing for |
| 5 | Scoring & Metrics | How you know you're getting it right |
| 6 | Correctness Verification | How you know you're getting it right |

Principles are **concurrent evaluation criteria**, not a sequential checklist. They apply at every phase, every decision point, from first research through production operations.

---

## 1. Security

### What It Asks

- What can go wrong?
- What are the known vulnerabilities in candidate technologies?
- What compliance regimes apply, and which are actually enforced end-to-end vs. claimed on paper?
- Where are authentication, authorization, and trust boundaries actually enforced in the code?
- What secrets exist and how are they managed?
- What has the incident history been, and what classes of incident recur?

### Scope

Security is a property of the entire system, not a feature. It must be considered from earliest design through post-deployment monitoring. Key dimensions:

- **Threat modeling** — Who might attack, what they'd want, how they'd get it
- **Zero-trust design** — Every boundary authenticates, every request is validated
- **Continuous audit hooks** — The system produces evidence that it behaved correctly
- **Compliance preparation** — SOC 2, HIPAA, GDPR, PCI-DSS, etc. — planned in, not retrofitted

### Common Failure Modes

- **Claimed vs. enforced divergence** — a compliance standard listed in docs that isn't implemented end-to-end
- **Implicit trust boundaries** — code paths where input validation is "someone else's problem"
- **Secrets in plaintext** — hardcoded, environment-variable-exposed, or in config files checked into VCS
- **CVE accumulation during dormancy** — dependencies that were clean at publish become vulnerable in place
- **Absent incident history documentation** — no record means recurring classes cannot be identified

### How to Score (Phase 6 verification)

| Gate | PASS requires |
|------|--------------|
| Greenfield | Compliance requirements identified with architecture implications; threat actor profile established; known vulnerability history documented for candidate technologies; security tooling availability assessed |
| Existing project | Current compliance posture documented with evidence (not claims); live threat surface enumerated from actual deployment topology; known vulnerabilities in current dependency graph inventoried; historical security incidents summarized with root causes and remediation status |

### Interactions with Other Principles

- **Security ↔ Economics** — Security costs (tooling, audit, compliance certification). Under-investment shows up later as incident cost. Phase 2 weighting usually favors Security; document if it doesn't.
- **Security ↔ Maintainability** — Secrets rotation, patch cadence, dependency updates are maintainability work. A secure system that can't be updated becomes insecure.
- **Security ↔ Operations** — Observability is what turns "we have no incidents" from belief into measurement. Without operational visibility, security posture is asserted.

---

## 2. Maintainability

### What It Asks

- Can this be understood by someone who wasn't in the room?
- Is this tested, documented, and structured for change?
- What is the gap between documented intent and observed behavior?
- How queryable is the documentation — can AI answer practical questions from docs alone?
- How steep is the contributor ramp-up?

### Scope

Documentation serves two audiences: humans and AI. Living documentation is queryable, AI-parseable, and kept current through explicit mechanisms.

- **Testing strategy** — Unit, integration, end-to-end; measured coverage; real coverage vs. performative coverage
- **Living documentation** — Structured for AI consumption (consistent headers, tables, metadata, cross-references)
- **Technical debt control** — Debt inventoried with code-level grounding; not just "old code is debt" framing
- **Observability and debuggability** — Questions answerable from dashboards vs. questions requiring code reading

### Common Failure Modes

- **Stale documentation** — edited recently, meaningful content not updated in a year
- **Performative test coverage** — tests exist, exercise trivial paths, miss critical logic
- **Tribal knowledge concentration** — single-person bus factor on modules, integrations, operational procedures
- **Documentation that serves humans but not AI** — narrative prose where machine-parseable structure was needed
- **Orphan code accumulating silently** — scripts, modules, devDeps that look current because they're recent but are never referenced

### How to Score (Phase 6 verification)

| Gate | PASS requires |
|------|--------------|
| Greenfield | Documentation quality assessed for candidate technologies; community health data with quantitative indicators; testing ecosystem evaluated; talent pool assessed |
| Existing project | Documentation accuracy assessed (not just existence); test coverage profile measured with current numbers; known technical debt inventoried with code-level grounding; contributor ramp-up friction documented |

### Interactions with Other Principles

- **Maintainability ↔ Economics** — Maintainability is economics at a different time horizon. Under-investment in tests/docs shows up as change-cost inflation within 12–18 months.
- **Maintainability ↔ Scoring & Metrics** — Unmeasured maintainability (no coverage metric, no doc-currency metric, no ramp-up metric) is unimproved maintainability. Phase 1 must capture baselines.
- **Maintainability ↔ Correctness Verification** — Tests are correctness verification when well-designed; maintenance burden when performative. The distinction matters.

---

## 3. Economics

### What It Asks

- What does this actually cost across the full lifecycle?
- How does cost change at scale?
- What does the system cost to **run** — infrastructure, licensing, third-party services, operational labor?
- What does the system cost to **change** — lead time, deployment frequency, change failure rate, MTTR?
- Where is vendor lock-in concentrated? Where are license / pricing cliffs approaching?

### Scope

Every decision has a cost. Economics covers:

- **Cost forecasting** — Development time, infrastructure, licensing, AI tool costs
- **Speed-to-market** — Time from decision to shippable output
- **Resource scaling** — Cost behavior as load, users, data, or complexity grows
- **Change economics** — The DORA-style four key metrics (deployment frequency, lead time, change failure rate, MTTR) describe real operational economics more accurately than headcount

### Common Failure Modes

- **Estimating without measuring** — stack cost projections built from vendor price sheets without current usage data
- **Ignoring maintainer-time** — a "free" OSS dependency costs maintenance attention, CVE remediation, upgrade work
- **Missing exit cost** — managed services without documented exit strategy cost more to leave than to enter
- **Speed-without-correctness optimization** — "ship fast" that produces rework exceeding the savings
- **Unmeasured change economics** — no DORA baseline means improvement is asserted, not demonstrated

### How to Score (Phase 6 verification)

| Gate | PASS requires |
|------|--------------|
| Greenfield | Actual cost data present (not estimates) for licensing and infrastructure at target scale; development velocity indicators documented for candidate stacks; AI tooling costs estimated; build scope reduction quantified |
| Existing project | Current run-cost measured (infrastructure, licensing, third-party, operational labor); change-cost indicators captured (deployment frequency, lead time, change failure rate, MTTR); realistic improvement-budget envelope defined |

### Interactions with Other Principles

- **Economics ↔ Security** — Security investment vs. incident-cost-if-skipped. The harder trade-off is near-term cost vs. probabilistic tail risk.
- **Economics ↔ Maintainability** — Short-term delivery pressure vs. long-term change-cost. Frequent trade-off; must be documented, not defaulted.
- **Economics ↔ Operations** — Observability investment has direct operational cost and indirect incident-cost savings. Phase 2 must weight honestly.

---

## 4. Operations

### What It Asks

- How does this deploy?
- How does this scale?
- How do we know when something is wrong?
- What integrations exist — inbound and outbound — and what are their reliability characteristics?
- What is the current incident response capability — on-call, runbooks, post-incident review?

### Scope

Operational concerns must be designed in early, not added later.

- **Scalability** — Horizontal, vertical, data-layer; known limits; limits that haven't been tested
- **Reliability** — SLOs, actual vs. target, error-rate trends, availability posture
- **Interoperability** — Contracts with internal and external systems; how failures propagate
- **Governance** — Ownership, review gates, decision authority, escalation paths
- **Post-deployment monitoring** — What's logged, what's monitored, what's alerted on, noise ratio

### Common Failure Modes

- **Observability as afterthought** — logs added after incidents reveal gaps, not before
- **Happy-path-only testing** — scaling limits discovered under real load, not during design
- **Undefined ownership** — systems that work until they don't, then no one owns the response
- **Integration contracts implicit** — inter-service communication without explicit contracts; failure modes ambiguous
- **Runbook absence** — incident response improvised each time because runbooks don't exist or are stale

### How to Score (Phase 6 verification)

| Gate | PASS requires |
|------|--------------|
| Greenfield | Deployment and orchestration options covered with operational complexity assessed; scaling characteristics and known limits documented; observability tooling availability assessed; integration patterns documented |
| Existing project | Current deployment topology documented; observability state assessed (what is logged, monitored, alerted — and what is not); incident history summarized; known scaling limits documented; integration inventory complete |

### Interactions with Other Principles

- **Operations ↔ Economics** — Operational infrastructure (monitoring, alerting, runbooks, on-call) is ongoing cost that produces incident-rate benefit. Quantify both sides.
- **Operations ↔ Security** — Incident detection is a security capability. Unmonitored systems cannot report compromise.
- **Operations ↔ Scoring & Metrics** — DORA-style metrics are operational metrics. Without them, operational improvement is invisible.

---

## 5. Scoring & Metrics

### What It Asks

- What quantitative benchmarks measure this principle / this system / this decision?
- Where are the benchmarks missing? Where are they present but stale, unmeasured, or unenforced?
- What baselines must be captured **now** — before improvement begins — so improvement can be measured rather than asserted?
- What comparable-system or industry benchmarks apply?

### Scope

Scoring & Metrics is *how you know you're getting it right* on Principles 1–4. Without scoring, principles are aspirations.

- **Quantitative benchmarks per principle** — Security (CVE counts, compliance coverage %), Maintainability (test coverage, doc-currency age), Economics (run-cost $/month, change-cost lead time), Operations (uptime %, MTTR)
- **AI-generated scorecards at phase checkpoints** — Scored by AI, reviewed by human, approved before phase advances
- **Trend tracking** — Regression matters as much as absolute levels; a 70% coverage that was 85% last quarter is a worse signal than a stable 70%
- **Measurement tags** — Every numeric value is tagged MEASURED / ESTIMATED / BELIEVED / UNMEASURED

### Common Failure Modes

- **Qualitative claims masquerading as measurement** — "the system is fast," "deploys are painful," "we're secure" are not measurements
- **Baselines captured after improvement** — no before-picture means no improvement proof
- **Principles weighted equally by default** — most projects weight some principles higher; unequal weighting must be explicit, not accidental
- **Benchmarks set once, never revisited** — targets that made sense at Phase 2 are stale by Phase 6; re-validate
- **Scorecard as formality** — CONDITIONAL ratings dismissed as close-enough-to-PASS; CONDITIONAL is preferred over PASS-with-caveats because it surfaces decision points

### How to Score (Phase 6 verification)

| Gate | PASS requires |
|------|--------------|
| Greenfield | Quantitative benchmarks present with sources and dates — no qualitative-only claims in benchmark-relevant sections; comparable-system SLA and performance data present |
| Existing project | Baseline measurements captured for every dimension the improvement is intended to move, before improvement begins; qualitative claims replaced with measurements or explicitly tagged UNMEASURED |

### Interactions with Other Principles

- **Scoring ↔ All four optimization principles** — Scoring is *the mechanism* by which Security, Maintainability, Economics, and Operations become actionable. Without scoring, they are values; with scoring, they are targets.
- **Scoring ↔ Correctness Verification** — Scoring tells you how well something performs; verification tells you whether it is right. A high-scoring incorrect system is a high-scoring incorrect system.

---

## 6. Correctness Verification

### What It Asks

- Is it right, not just performant?
- Does observed behavior match specified behavior?
- Are claims verified (cited, dated, cross-referenced) or asserted (practitioner memory, stale docs)?
- Are divergences between documented intent and observed behavior surfaced rather than silently reconciled?
- Are discovery gaps — areas not inspected — explicitly registered?

### Scope

Correctness Verification is *how you know you're getting it right* in the absolute sense (not just in performance).

- **Formal verification** — Where applicable; formal models for critical logic
- **Specification conformance testing** — Does the implementation match the spec?
- **AI-vs-AI audits** — One AI produces, another AI audits; the adversarial loop catches blind spots
- **Property-based testing** — Invariants asserted over generated inputs, not just example inputs
- **Source attribution discipline** — Every significant claim has a source (file, commit, ticket, dashboard), a date, a confidence level

### Common Failure Modes

- **Trust without verification** — "I know this works" not backed by tests, telemetry, or recent inspection
- **Documented-intent-as-reality** — treating ADRs as current behavior without checking code
- **Memory as evidence** — practitioner's confident recollection unbacked by artifact; memory is hypothesis, not verification
- **Silent gap omission** — sections that couldn't be inspected left blank rather than flagged
- **Confidence inflation** — Medium becomes High during synthesis without new evidence

### How to Score (Phase 6 verification)

| Gate | PASS requires |
|------|--------------|
| Greenfield | Confidence levels (High / Medium / Low) assigned to all significant claims; all key claims cite a specific source and date; conflicts between source artifacts documented rather than silently resolved; research gaps explicitly registered |
| Existing project | Every significant claim about current state verified against the codebase, telemetry, or documented evidence — or explicitly marked as unverified; divergence between documented intent and observed behavior surfaced rather than reconciled; confidence levels throughout; discovery gaps listed |

### Interactions with Other Principles

- **Correctness Verification ↔ Scoring & Metrics** — Verification answers "is it right"; scoring answers "how well does it perform." Both are needed; neither substitutes.
- **Correctness Verification ↔ Security** — Security audit is correctness verification applied to the threat surface. Penetration testing, static analysis, formal verification of critical logic.
- **Correctness Verification ↔ Maintainability** — Contract tests, property-based tests, specification conformance tests are simultaneously correctness verification and maintainability infrastructure.

---

## Applying the Principles — Standard Patterns

### Pattern: Principle Coverage Audit (for any artifact)

For every significant artifact or decision, ask:

1. Which principles does this serve?
2. Which principles does this place at risk?
3. What trade-offs are being made across principles?
4. Are those trade-offs documented, or implicit?

If any principle is neither served nor at risk, ask whether that principle should be addressed or whether the artifact's scope legitimately excludes it.

### Pattern: Principle-Weighted Scoring

Phase 2 typically applies unequal weights:

| Project type | Typical weighting |
|-------------|-------------------|
| Security-critical (finance, health, regulated) | Security 2× weight; others 1× |
| Solo-maintainer OSS | Maintainability 1.5×, Economics 1.5×; Security and Operations 1× |
| High-throughput services | Operations 1.5×; others 1× |
| Early-stage product | Economics 1.5× (speed-to-market); Correctness Verification 0.5× (acceptable short-term) |

Weights are explicit, documented, and justified. A default-equal weighting is itself a choice that should be stated.

### Pattern: Trade-off Documentation

When a decision favors one principle over another, document:

```
Decision: [what was decided]
Favored principle(s): [which and why]
Principle(s) accepting cost: [which]
Trade-off reasoning: [why this balance makes sense here]
Cost acknowledged: [what we're giving up]
Revisit trigger: [what would cause us to revisit this]
```

This pattern prevents trade-offs from becoming silent defaults that decay into regret.

---

## Cross-References

- **SDD cycle application of the principles:** see `sdd-cycle.md` — principles enter the cycle at Specify (interview questions filter through them), persist through Plan and Detail (PRDs embed them as concrete requirements), shape Task (acceptance criteria reference them), and dominate Implement (outputs are evaluated against them).
- **Building tool sets that embed the principles:** see `building-blocks-and-toolsets.md` — every tool set must address all six principles or explicitly flag which are out of scope and why.

---

*AI-Centric Software Development Playbook — core-principles reference, part of the ai-centric-playbook skill v1.0 (2026-04-22)*
