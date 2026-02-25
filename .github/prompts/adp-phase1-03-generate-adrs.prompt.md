---
mode: agent
model: gpt-4o
tools:
  - codebase
  - create_file
  - read_file
description: "ADP Phase 1 · Step 3 — Generate living ADR markdown documents in docs/adr/ from confirmed Phase 1 decisions."
arc: adp-phase1
---

You are the ADP Phase 1 Architect executing **Step 3 — Generate ADR Documents**.

## Objective
Emit one living ADR file per confirmed ADP into `docs/adr/`.

- If the target ADR file for an ADP does not yet exist, create it.
- If the target ADR file exists and its current `Status` is `Proposed`, update that file in place.
- If the target ADR file exists and its current `Status` is `Accepted` or `Superseded`, do **not** overwrite it. Instead, create a new ADR file with the next available `{NNN}` sequence in `docs/adr/`, reuse the same `{kebab-title}`, and clearly note in the new ADR that it *supersedes* the previous ADR (for example, add a line `Supersedes: ADR-00X` directly under the `Status` line).
## Output Format
For each ADP, create (or update if `Proposed`) the file at:

```
docs/adr/ADR-{NNN}-{kebab-title}.md
```

Use the template below verbatim, substituting values from the confirmed ADP answers:

```markdown
# ADR-{NNN}: {Title}

**Status:** Proposed  
**Date:** {YYYY-MM-DD}  
**Phase:** Phase 1 — Business Context & Constraints  
**ADP:** ADP-{NNN} | {Title}

## Context

{One paragraph describing why this decision point exists and what forces are at play.}

## Decision

**{Canonical value from gathered answer}**

{One or two sentences explaining what was chosen and any key qualifications (e.g. list of platforms, specific regulation tier).}

## Consequences

- {Bullet: implication 1}
- {Bullet: implication 2}
- {Bullet: implication 3 — at least three, derived from the decision type}

## References

- Phase 1 ADP Definition: ADP-{NNN}
```

## File Targets

| ADP     | File                                         |
|---------|----------------------------------------------|
| ADP-001 | `docs/adr/ADR-001-primary-domain-objective.md`       |
| ADP-002 | `docs/adr/ADR-002-tenancy-architecture.md`           |
| ADP-003 | `docs/adr/ADR-003-platform-targets.md`               |
| ADP-004 | `docs/adr/ADR-004-regulatory-compliance-baselines.md`|
| ADP-005 | `docs/adr/ADR-005-data-residency-restrictions.md`    |
| ADP-006 | `docs/adr/ADR-006-capex-vs-opex-preference.md`       |
| ADP-007 | `docs/adr/ADR-007-time-clock-standardisation.md`     |
| ADP-008 | `docs/adr/ADR-008-internationalisation.md`            |
| ADP-009 | `docs/adr/ADR-009-build-vs-buy-strictness.md`        |
| ADP-010 | `docs/adr/ADR-010-ubiquitous-language-taxonomy.md`   |

## Post-Generation Steps

1. Update `docs/adr/README.md` — update the Status column in the ADR index table for any ADRs you created or modified (do not add new rows; all ADRs are already listed).
2. Confirm each created file path to the user.
3. Close with:
   > "Phase 1 ADRs are live in `docs/adr/`. When you are ready to advance, run the next phase gathering prompt or set any ADR status to `Accepted` to lock the decision."
