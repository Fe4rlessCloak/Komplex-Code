# Architectural Audit Findings

Generated from a code review or architectural audit. The implementation agent should read this file before beginning work and resolve all `Pending` findings that are in scope.

---

## Audit

- **Date:** YYYY-MM-DD
- **Reviewer:** [Name or AI]
- **Repository Revision:** [Commit / Branch] (optional)

---

## Summary

| ID | Severity | Status | File(s) |
|----|----------|--------|---------|
| REV-001 | High | Pending | `src/api/users.ts` |
| REV-002 | Low | Resolved | `src/components/Button.tsx` |

---

## Findings

### REV-001 — Missing Request Validation

- **Severity:** High
- **Status:** Pending
- **Files:** `src/api/users.ts`
- **Rule Violated:** `.agents/skills/backend.md` §2.1

#### Problem

Describe the architectural issue.

#### Why It Matters

Explain the impact.

#### Required Action

Provide concrete implementation instructions.

#### Verification

Describe how to confirm the issue is resolved.

Example:

- All API inputs validated by Zod.
- `pnpm test src/api` passes.
- Existing endpoints continue to function.

---

### REV-002 — ...

...