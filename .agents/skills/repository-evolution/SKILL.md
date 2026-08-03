---
name: repository-evolution
description: Prepare the repository for implementation by planning, interviewing, and evolving repository guidance.
---

# Domain Skill: Repository Evolution

## Purpose

Prepare the repository for implementation.

This skill coordinates repository planning, interviews the developer when required, maintains the repository's operational documentation, and evolves repository guidance based on previous implementation sessions.

The objective is to ensure future implementation work becomes more predictable, reusable, and autonomous.

---

## Responsibilities

During every Repository Evolution session:

1. Review the current repository guidance.
2. Review pending implementation learnings.
3. Interview the developer to resolve planning or architectural uncertainty.
4. Produce or update planning artifacts.
5. Promote reusable knowledge into repository guidance.
6. Verify the repository's instruction system remains consistent.

---

## Repository Inputs

Review these documents before making planning decisions:

- `AGENTS.md`
- Active `SPECS.md`
- Domain skills
- `LEARNINGS.md`
- `REVIEWER_FINDINGS.md`

If a required operational document does not exist, create it using the corresponding template from `.agents/templates/`.

Never invent the structure of repository documents.

---

## Repository Outputs

Depending on the session, this skill may create or update:

- `AGENTS.md`
- `SPECS.md`
- Domain skills
- Repository templates
- `LEARNINGS.md`
- `TECH_DEBT.md`
- `BLOCKED.md`
- `REVIEWER_FINDINGS.md`
- `PROMPTS.md`

Only modify documents whose evolution is justified by the current session.

---

## Interviewing

Interview the developer only when repository inspection cannot confidently resolve:

- architectural decisions,
- reusable repository conventions,
- planning uncertainty,
- instruction evolution.

Ask one question at a time.

Do not interview for feature-specific implementation details.

---

## Knowledge Promotion

Treat `LEARNINGS.md` as the repository evolution backlog.

Each pending learning should be evaluated to determine whether it should:

- remain a historical learning,
- become repository guidance,
- expand an existing domain skill,
- create a new domain skill,
- update a repository template,
- or be rejected as feature-specific.

Promote only reusable repository knowledge.

### Evolution Candidates

An **Evolution Candidate** is a proposal written by an Implementation session into `LEARNINGS.md`, requesting that the next Repository Evolution session change repository guidance. It is the only channel through which Implementation may propose guidance changes.

Each candidate must be evaluated against the following fields (see `LEARNINGS.template.MD`):

- **Status:** `PENDING` | `ACCEPTED` | `REJECTED`
- **Suggested Target:** which document or skill it proposes to change
- **Confidence:** Low | Medium | High
- **Suggestion:** the concrete instruction change proposed
- **Rationale:** why it should become repository guidance rather than remain feature-specific

When evaluating a candidate:

1. Confirm it is reusable repository knowledge, not feature-specific detail.
2. Check it does not weaken a **critical invariant** (see Guardrails below).
3. Decide to accept, reject, or defer it.
4. Update the candidate's `Status` in `LEARNINGS.md` to record the outcome.

---

## Guardrails

Repository Evolution may update `AGENTS.md`, skills, and templates to keep the instruction system effective. This authority is bounded: it must never remove or weaken **critical invariants**:

- security controls (e.g., 2FA, secrets handling),
- architectural constraints,
- the ownership model defined in `AGENTS.md` §5.

When an evolution change touches a critical invariant, flag it for explicit developer approval rather than applying it silently.

---

## Planning

When implementation is requested:

- reuse an existing active specification when appropriate;
- otherwise create one using the repository template;
- identify dependencies;
- define observable verification;
- describe what must be implemented rather than how.

---

## Principles

- Prefer repository inspection over assumptions.
- Prefer interviews over guessing.
- Prefer evolving existing documentation over creating new documents.
- Prefer reusable repository guidance over feature-specific documentation.
- Keep repository instructions concise, consistent, and implementation-agnostic.

---

## Verification

Before concluding a Repository Evolution session:

- [ ] Repository guidance has been reviewed.
- [ ] Pending learnings have been evaluated.
- [ ] Evolution Candidates have been resolved (accepted, rejected, or deferred).
- [ ] No critical invariant was weakened without explicit developer approval.
- [ ] Planning artifacts are ready for implementation.
- [ ] Repository instructions remain consistent.
- [ ] New reusable knowledge has been captured where appropriate.

Repository Evolution sessions map their completion to the exit codes in `AGENTS.md` Section 6 (`0_DONE` when planning is complete and guidance is consistent).
