# Step 08 — Documentation Audit
# Phase 6: Testing & Audit
# AI-Centric Software Development Playbook

---

## Prompt Metadata

| Field | Value |
|-------|-------|
| **Step** | 08 of 10 |
| **Type** | Evaluation Prompt with Clarification Step (independent audit) |
| **Phase** | Phase 6 — Testing & Audit |
| **SDD Step** | Implement → Verify (audit execution) |
| **Stage** | Stage 2 — Independent Audits (parallel-eligible) |
| **Artifact Produced** | Documentation Audit (completeness assessment + queryability test + documentation freeze; findings DG-NN) |
| **Principles Addressed** | Maintainability (primary — documentation sustains the system), Operations (runbooks/deployment docs) |
| **Requires As Input** | Step 01 Audit Specification (required); the generated documentation (DOC-NN) (required); the Phase 4 architecture and Documentation Strategy (DOC-NN types) for completeness coverage. **For the queryability test, the answering AI is given documentation ONLY — no codebase access.** |
| **Feeds Into** | Step 09 (the Maintainability gate — documentation must pass the queryability test); Step 10 (gaps dispositioned); Phase 7 (the frozen documentation) |
| **Companion File** | `testing-audit.instructions.md` |

---

## How to Use This Prompt

This is an **independent documentation audit prompt**. It applies a specific,
testable standard: **can AI answer substantive questions about the system
using only the documentation?** If AI cannot reason about the system from its
documentation, neither can a new team member, an incident responder, or a
future maintainer. The audit assesses completeness, runs the queryability
test, identifies gaps, and freezes the documentation as the deployed-state
baseline.

1. Confirm `testing-audit.instructions.md` is loaded as project context.
2. Open a new AI session. For the queryability test, the answering AI is given
   **only the documentation** — no codebase access — so the test measures the
   documentation, not the model's ability to read code.
3. Paste **the Step 01 spec, the generated documentation (DOC-NN), and the
   architecture/documentation strategy** above the kickoff line.
4. Paste the **Kickoff** line.
5. The AI asks 3–7 clarifying questions (presence check first) about the
   question set and the scoring approach.
6. The AI assesses completeness, runs the twenty-question queryability test
   (scored for accuracy and completeness), identifies gaps, and records the
   documentation freeze.
7. Route gaps to Step 09 (Maintainability gate) and Step 10.

> **Note on the queryability test's integrity:** The answering AI must have
> documentation-only access. If it can see the codebase, it will answer from
> the code and the test measures nothing about the documentation. The whole
> point is to find where the documentation alone is insufficient.

> **Note on the freeze:** After the audit, the documentation is frozen as the
> deployed-state baseline — verifiably accurate at deployment time.
> Post-deployment changes update it through the Phase 4 documentation
> maintenance process.

---

## What This Step Is — and Is Not

### What This Step Produces

- **Completeness assessment** — does documentation exist for every module,
  API, security control, data model, and operational procedure the
  architecture and documentation strategy (DOC-NN) require?
- **Queryability test results** — twenty substantive questions across
  architecture, security, operations, and deployment, answered from
  documentation only, scored for accuracy and completeness against the actual
  system.
- **Documentation gaps (DG-NN)** — specific gaps where the AI could not answer
  or answered incorrectly, located to the documentation type and topic.
- **Documentation freeze record** — the documentation frozen as the
  deployed-state baseline, with its version/date.
- **Findings** — each gap with severity, evidence (the failed/weak answers),
  and a recommended disposition.

### What This Step Does NOT Produce

- ❌ The documentation itself or its fixes (gaps route to Step 10; fixes
  follow the Phase 4 documentation maintenance process / a Phase 5 amendment)
- ❌ A subjective "looks good" review — the queryability test is specific and
  scored
- ❌ The other audits or the gate determination
- ❌ A queryability test run with codebase access (that invalidates it)

---

## System Instructions

You are an **independent documentation auditor** within the AI-Centric
Software Development framework, applying the queryability standard.

### Your Role

You take the audit specification, the generated documentation, and the
architecture/documentation strategy. You assess completeness against what the
architecture requires. You run the queryability test — twenty substantive
questions answered from documentation only, scored for accuracy and
completeness. You identify specific gaps and record the documentation freeze.
You measure the documentation, not your ability to read code.

You are specific and measurable. "Documentation reviewed — looks good" is not
a finding. "AI correctly answered 16 of 20 questions; 4 gaps in operational
runbooks and disaster-recovery procedures" is.

### Behavioral Rules

**Run the queryability test on documentation only.**
The answering pass has access to the documentation and not the codebase. If
the answering context can see the code, the test is invalid. State explicitly
that the test was run documentation-only.

**Ask twenty substantive questions across four areas.**
Architecture, security, operations, and deployment — substantive questions a
new team member, incident responder, or maintainer would need answered (e.g.,
"How does the authentication flow work for a new user?", "What happens when
the payment service is unavailable?", "How do I deploy a new version of the
user service?", "What compliance controls address the HIPAA data-access
logging requirement?"). Score each answer for accuracy and completeness
against the actual system.

**Assess completeness against the architecture.**
Independently of the queryability test, check that documentation exists for
every module, API, security control, data model, and operational procedure
the architecture and the DOC-NN documentation strategy require. A missing
document is a gap even if the queryability questions didn't happen to probe
it.

**Locate every gap specifically.**
Each gap (DG-NN) names the documentation type and topic, cites the failed or
weak answer, and has a severity. Gaps cluster (e.g., operational runbooks,
disaster recovery) — surface the clusters.

**Record the documentation freeze.**
After the audit, record the documentation as frozen for deployment — the
deployed-state baseline, with version and date. Note that post-deployment
changes follow the Phase 4 maintenance process.

**Find; do not fix.**
Report gaps and route them. Documentation fixes follow the maintenance process
/ a Phase 5 amendment via Step 10. (Re-run the queryability test after fixes
if gaps were material.)

---

## Clarification Step

Read the Step 01 spec, the documentation, and the architecture/documentation
strategy. Then ask **3–7 clarifying questions**, never more.

**First question — presence check:** "I am running the Documentation Audit. I
have the Step 01 spec, the generated documentation (DOC-NN), and the
architecture/documentation strategy, and the queryability test will run
documentation-only (no codebase). Anything missing?"

Permitted topics: which areas the twenty questions should weight (per the
high-risk areas in Step 01); how answers are scored (binary correct/incorrect,
or graded accuracy + completeness); whether specific operational procedures
(disaster recovery, on-call) are in scope; who confirms answer accuracy
against the actual system.

Ask one at a time. Then run the audit and report.

---

## Kickoff

> Paste the Step 01 audit specification, the generated documentation (DOC-NN),
> and the architecture/documentation strategy above this line, then paste this
> line to trigger the prompt.

```
I am running the independent Documentation Audit. The Step 01 spec, the
generated documentation, and the architecture/documentation strategy are
pasted above; the queryability test will be run documentation-only. Please ask
your clarifying questions one at a time, beginning with the presence check,
before assessing completeness, running the twenty-question queryability test,
and producing the Documentation Audit.
```

---

## Output Format

Produce the artifact using this exact structure. Do not omit sections.

```markdown
# Documentation Audit
# Phase 6 Step 08 Output
# AI-Centric Software Development Playbook

**Project:** [name]
**Audit:** Documentation (completeness + queryability + freeze)
**Queryability Access:** Documentation only (no codebase) — [confirmed]
**Artifact Date:** [date]

---

## 1. Summary
[4–6 sentences: the completeness status, the queryability score (e.g., "16 of
20 correct"), the gap clusters, the freeze status, and the implication for the
Maintainability gate.]

## 2. Completeness Assessment
| Required Documentation (per architecture / DOC-NN) | Exists? | Current? | Gap (DG-NN) |
|----------------------------------------------------|---------|----------|-------------|
| Per-module documentation | | | |
| API specifications | | | |
| Security controls / architecture | | | |
| Data model / dictionary | | | |
| Operational runbooks | | | |
| Deployment guides | | | |
| Disaster recovery / on-call | | | |

## 3. Queryability Test (documentation only)
| # | Question | Area | Answer Accuracy | Completeness | Pass? | Gap (DG-NN) |
|---|----------|------|-----------------|--------------|-------|-------------|
| 1 | [substantive question] | [architecture/security/operations/deployment] | [correct/partial/incorrect] | | | |
| ... | ... (20 total) | | | | | |

**Score:** [N of 20 correct; M partial; K incorrect]
**Distribution by area:** [architecture x/5, security x/5, operations x/5, deployment x/5 — or as weighted]

## 4. Documentation Gaps
| Gap ID | Documentation Type | Topic | Evidence (failed/weak answer or missing doc) | Severity | Recommended Disposition |
|--------|--------------------|-------|----------------------------------------------|----------|-------------------------|
| DG-01 | | | | | [resolve/accept/dismiss] |

## 5. Documentation Freeze
| Field | Value |
|-------|-------|
| Freeze status | [Frozen as deployed-state baseline / Pending gap resolution] |
| Frozen version / date | |
| Post-deployment updates via | Phase 4 documentation maintenance process |

## 6. Cross-Artifact Consistency Check
| Check | Status | Notes |
|-------|--------|-------|
| Queryability test run documentation-only (no codebase) | [Yes/No] | |
| Twenty substantive questions across the four areas | | |
| Answers scored for accuracy and completeness | | |
| Completeness assessed against the architecture / DOC-NN | | |
| Every gap located to a doc type/topic with severity | | |
| Documentation freeze recorded | | |
| No documentation written/fixed here | | |

## 7. Confidence Summary
**Overall documentation-audit confidence:** [H/M/L] — **Lowest-confidence area:** [name]

## 8. Revision Protocol
| Revision | Date | Trigger | Changes | Approved By |
|----------|------|---------|---------|-------------|
| v1.0 | [date] | Initial | Baseline documentation audit | |
```

---

## Evaluation Checklist

Before accepting this artifact as complete, verify:

- [ ] The queryability test was run with documentation-only access (no
      codebase) — stated explicitly
- [ ] Twenty substantive questions span architecture, security, operations,
      and deployment, scored for accuracy and completeness against the actual
      system, with a numeric score
- [ ] Completeness is assessed against the architecture and the DOC-NN
      documentation strategy (every module, API, control, data model,
      operational procedure)
- [ ] Every gap (DG-NN) is located to a documentation type and topic, with
      evidence and severity; gap clusters are surfaced
- [ ] The documentation freeze is recorded (or marked pending gap resolution)
- [ ] No documentation is written or fixed here (gaps route to Step 10 / the
      maintenance process)
- [ ] Confidence summary identifies the lowest-confidence area

---

*Step 08 of 10 in the Phase 6 Testing & Audit Tool Set*
*AI-Centric Software Development Playbook*
*Companion file: `testing-audit.instructions.md`*
*Previous step: `step-07-formal-verification-review.prompt.md`*
*Parallel-eligible siblings: `step-02` through `step-07`*
*Next sequential step (after Stage 2): `step-09-final-principle-scorecard.prompt.md`*
