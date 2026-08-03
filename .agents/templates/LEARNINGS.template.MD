# Repository Quirks & Edge Cases

Record only non-obvious repository-specific issues that future sessions are likely to repeat. Do not document ordinary bugs or feature implementations.

---

## [LEARNING-001] – Short Title

- **Date Recorded:** YYYY-MM-DD
- **Affected Subsystem:** `e.g., Prisma Migrations`
- **Related Files:** `src/db/...`
- **Related Spec:** `SPECS.md` (optional)

### Symptom

Describe the observable failure.

### Root Cause

Explain the underlying technical reason.

### Prevention Rule

A concise rule future agents should follow.

### Blueprint

```typescript
// Minimal correct implementation
```

### Verification

How to confirm the fix works.

Examples:

- `pnpm test` passes
- Build succeeds
- API returns HTTP 200
- Migration completes successfully

### Evolution Candidate 

- **Status:** PENDING | ACCEPTED | REJECTED
- **Suggested Target:** `frontend.md`
- **Confidence:** Low | Medium | High

#### Suggestion 

Describe what repository instruction should be added or changed.

#### Rationale

Explain why this should become repository guidance rather than remain feature-specific.