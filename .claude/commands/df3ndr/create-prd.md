---
description: Turn a rough request into a structured Change Plan (PRD) after asking clarifying questions.
argument-hint: <short description of the change, feature, hardening, or operational task>
---

# Create a Change Plan (PRD)

You are scoping a piece of work — a feature, change, hardening, migration, or
operational task — for the project described in `CLAUDE.md`. Produce a clear,
actionable **Change Plan** — a requirements document a careful operator (or a
future you) can execute without re-deriving the intent. This is planning only:
**do not implement anything yet.**

The initial request is:

> $ARGUMENTS

Resolve the input as follows:
- If it points to an **epic overview** (`…/Milestone-NN/Epic-MM/overview/e<m>-<slug>.md`,
  produced by `/breakout-epics`), build the PRD from that — it already carries the
  objective, acceptance criteria, tasks, owner gates, and risks. This is the normal
  entry point.
- If it's a free-text change/task, work from that.
- If empty, ask the user which epic overview or change they want planned before doing
  anything else.

## Process

1. **Read the request** and skim relevant context before asking anything —
   `CLAUDE.md`, the **epic overview** this PRD expands (if given) plus its parent
   `Milestone-NN/overview/milestone-*.md` and the `*-project-plan.md` above it, and any
   component, service, or environment notes the project keeps. Don't ask what the repo
   already answers.
2. **Ask only the most essential clarifying questions** (3–5 max) to close real
   gaps. Cover the "what" and "why," plus the operational specifics that planning the
   work actually needs:
   - **Which components / services / systems** are in scope?
   - **Blast radius & users** — is anything user-facing or production? Who/what is
     affected if it goes wrong?
   - **Change window** — can this happen anytime, or only during a maintenance window?
   - **Reversibility** — is there a clean rollback, and is a backup or snapshot needed
     first?
   - **Success / done criteria** — how will we know it worked?
   Skip any question whose answer is reasonably inferable from the request or the repo.
3. **Generate the Change Plan** using the structure below, folding in the answers.
4. **Save it** in the epic's own directory as
   `project/<Area>/<project-name>/Milestone-NN/Epic-MM/prd-e<m>-<slug>.md` (alongside the
   `overview/e<m>-<slug>.md` it expands; create the dir if needed). Match the epic's
   number and slug (e.g. `prd-e1-iac-bootstrap.md`). For a one-off change outside a
   project tree, fall back to `project/tasks/prd-<slug>.md`.

### Formatting the clarifying questions

- **Number** each question (1, 2, 3…).
- List options as **A, B, C, D** so the user can answer "1A, 2C, 3B".
- Always allow a free-text answer — these are real decisions, not a quiz.

Example:

```
1. Which components are in scope for this change?
   A. A single service / module
   B. Two closely coupled components
   C. The whole subsystem
   D. Other (please specify)

2. Is any of this user-facing / production right now?
   A. Yes — live, serving users
   B. Partially — staging or low-traffic only
   C. No — internal/dev tooling only
```

## Change Plan structure

Generate a Markdown document with these sections:

1. **Overview & Problem** — what the change is and the problem/risk it addresses. State the goal in one or two sentences.
2. **Goals** — specific, measurable objectives (e.g. "Block direct external access to the admin port," "Cut p95 request latency below 400 ms").
3. **Scope — Components & Services** — exact systems, services, modules, files, ports, domains, or resources in scope. Be explicit; this defines the blast radius.
4. **Stakeholders & Impact** — who/what is affected (end users, specific features, other maintainers). Note any user-facing impact.
5. **Operational Requirements** — the concrete, numbered things the change must do (e.g. "1. Access to the admin endpoint must be restricted to the internal network." "2. All HTTP must redirect to HTTPS."). Clear and verifiable.
6. **Security & Compliance Considerations** — auth, secrets, exposed surface, least-privilege, logging/audit. Any step that needs elevated privileges or touches sensitive resources (credentials, keys, certificates, production data, infrastructure config) must be called out as requiring **explicit human approval** — never plan to route around that.
7. **Non-Goals (Out of Scope)** — what this change deliberately will *not* do.
8. **Risk, Rollback & Recovery** — what can go wrong, the rollback path, and whether a **backup or snapshot is required before starting**. Prefer reversible actions (e.g. a graceful reload) over destructive ones.
9. **Validation / Success Metrics** — how success is verified after the change (health checks, a request/probe, service status, log lines, a security-scan result, a latency number).
10. **Open Questions** — anything still unresolved.

## Output

- **Format:** Markdown (`.md`)
- **Location:** `project/<Area>/<project-name>/Milestone-NN/Epic-MM/` (the epic's own
  directory, beside its `overview/e<m>-<slug>.md`). Fallback for one-offs: `project/tasks/`.
- **Filename:** `prd-e<m>-<slug>.md` (match the epic number + slug; e.g.
  `prd-e1-iac-bootstrap.md`). One-off fallback: `prd-<slug>.md`.

## Final instructions

1. Do **NOT** start implementing the change — this command only produces the plan.
2. You **must** ask the clarifying questions before writing the plan (unless the
   request is already fully specified and the repo answers every gap).
3. Fold the user's answers back in to sharpen the plan.
4. When done, point the user to `/generate-tasks` to turn this plan into an
   executable task list.
