---
name: implementation
description: Implement the active specification using the repository's operational guidance.
---

# Domain Skill: Implementation

## Purpose

Implement the active specification using the repository's operational guidance.

This skill is responsible for producing production-ready code, verification artifacts, and implementation feedback. It follows the repository's instruction system but does not evolve it directly.

The objective is to satisfy the active specification with the minimum necessary changes while preserving correctness, maintainability, and repository consistency.

---

## Responsibilities

During every implementation session:

1. Review the repository instructions.
2. Review the active specification.
3. Implement the required work.
4. Verify the implementation.
5. Record implementation findings.
6. Stop.

---

## Repository Inputs

Review before modifying code:

- `AGENTS.md`
- Active `SPECS.md`
- Relevant domain skills
- `LEARNINGS.md`
- `REVIEWER_FINDINGS.md`

Inspect the repository before making assumptions.

---

## Implementation Principles

- Implement the active specification.
- Inspect before assuming.
- Modify only files required by the specification.
- Prefer existing repository patterns over introducing new ones.
- Preserve existing architecture and conventions.
- Keep changes focused and intentional.

---

## Documentation Responsibilities

Implementation may write to `BLOCKED.md`, `LEARNINGS.md`, and `.logs/` only. It must not perform high-level documentation changes — those belong to Repository Evolution.

### BLOCKED.md

Update when implementation cannot continue because of:

- missing credentials,
- unavailable services,
- missing dependencies,
- environment failures,
- unresolved external blockers.

Record the exact error and halt further implementation.

---

### LEARNINGS.md

Record repository discoveries made during implementation.

Examples include:

- non-obvious repository behavior,
- recurring implementation patterns,
- hidden architectural constraints,
- unexpected repository quirks.

When a discovery appears reusable across future work, create an **Evolution Candidate** rather than modifying repository guidance directly.

---

### Logs

Pipe terminal stdout/stderr into `.logs/run-<timestamp>.log` for each run.

---

## Escalation

When implementation discovers reusable repository knowledge:

1. Record it in `LEARNINGS.md`.
2. Mark it as an Evolution Candidate (see `LEARNINGS.template.MD` for the required fields).
3. Continue implementation whenever possible.

Repository guidance is promoted during Repository Evolution, not during implementation. Implementation may only propose guidance changes via Evolution Candidates in `LEARNINGS.md`; it must not edit `AGENTS.md`, skills, templates, `SPECS.md`, `TECH_DEBT.md`, or `REVIEWER_FINDINGS.md`.

---

## Verification

Before considering implementation complete:

- [ ] Active specification satisfied.
- [ ] Required verification completed.
- [ ] Modified files are intentional.
- [ ] No unrelated files changed.
- [ ] Implementation findings documented where appropriate.
- [ ] No high-level documentation was modified (only `BLOCKED.md`, `LEARNINGS.md`, and `.logs/`).

Implementation sessions map their completion to the exit codes in `AGENTS.md` Section 6 (`0_DONE` when the spec item is complete and verified; `1_BLOCKED` when halted with a blocker recorded in `BLOCKED.md`).
