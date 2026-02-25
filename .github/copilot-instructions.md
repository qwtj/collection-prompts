# Copilot Instructions — ADP Gathering Workflows

This repository uses **Architecture Decision Points (ADPs)** to lock architectural reality before any code is written. Every ADP is gathered interactively through sequenced Copilot prompts and recorded as a living **Architecture Decision Record (ADR)** under `docs/adr/`.

## Ground Rules
- **Never assume an ADP.** Always confirm each value with the user before advancing.
- **One question at a time.** Use the `askQuestions` tool when available; otherwise use letter-based choices (A, B, C…).
- **Scan first.** Before any gathering begins, scan `docs/adr/` for ADPs already captured. Skip those already decided.
- **Idempotent writes.** Generating ADR files must not overwrite a file whose status is `Accepted` or `Superseded`.
- **Ubiquitous language.** Once ADP-010 is captured and the initial ADR set is finalized, all subsequent identifiers in generated non-ADR files (application code and downstream documentation) must honor its taxonomy.

## Phase Registry
| Phase | ADP Range | Phase Identifier |
|-------|-----------|------------------|
| Phase 1 – Business Context & Constraints | ADP-001 – ADP-010 | `phase1` |

The phase identifier is internal metadata for Copilot workflows and is not the ADR `Status` field.
## ADR Output Convention
- Path: `docs/adr/ADR-{NNN}-{kebab-title}.md`
- Status values: `Proposed` → `Accepted` → `Deprecated` → `Superseded`
- One ADR per ADP.
