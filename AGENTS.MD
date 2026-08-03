
# AGENTS.md

## 1. Project Snapshot
* **Tech Stack:** [To be populated during Stage 1 Architect Interview]
* **Build Command:** `[e.g., pnpm build]`
* **Test Command:** `[e.g., pnpm test]`
* **Lint/Format Command:** `[e.g., pnpm lint]`

---

## 2. Instruction Priority 

When instructions conflict, follow them in this order:

1. Direct user request
2. Active SPECS.md
3. AGENTS.md
4. Domain skill documents
5. Existing project conventions

## 3. Core Operating Directives

* **Interview First:** When facing ambiguous specs, missing context, or architectural trade-offs, interview the developer before writing code. Interview only when unanswered questions materially affect correctness, architecture, security, or user-visible behavior.
* **Don't Assume:** Verify assumptions using repo search tools, live logs, or direct inspection. Never invent API schemas, path structures, or external dependencies.
* **Define "Done" Observably:** A task is complete only when the required implementation is finished and verified by an observable signal appropriate to the change (for example, passing tests, successful builds, green terminal logs, or expected application behavior).
* **Surgical Edits:**  Modify only files directly required by the active spec, including shared dependencies, tests, configuration, and documentation. Do not refactor adjacent unprompted code or change code formatting styles outside your scope.
* **Implement by Logical Units:** Respect the logical reading order of `SPECS.md`, but implement shared foundational dependencies (data models, base utilities) before consuming feature UI—regardless of list position.
* **Detailed Git Commit Messages:** When commits are requested or running in autonomous mode, use structured commit messages. Write structured commit messages detailing *what* changed, *why* it changed, and *which spec item* was satisfied. Never issue generic commits (e.g., "fixed bug"). 
* **Point Docs at Live Code:** Reference exact file paths (`src/services/auth.ts`) rather than describing logic in prose. Keep markdown docs sparse and code-pointer heavy to eliminate doc drift.
* **Include Code Blueprints:** Every custom pattern or skill document must contain concrete, copy-pasteable inline code examples showing the target pattern.
* **Prevent Repeat Mistakes:** If an iteration fails because of agent behavior, update the relevant rule, skill, or spec before retrying. If the same class of mistake repeats, strengthen AGENTS.md or the appropriate skill document so future iterations cannot make the same error.

---

## 4. Domain Skill Routing

Before performing domain-specific work, load the corresponding skill document if it exists and follow its guidance unless it conflicts with higher-priority instructions.

* **Frontend Development:** `.agents/skills/frontend.md` [Populate path during setup]
* **Backend & API Routes:** `.agents/skills/backend.md` [Populate path during setup]
* **Database & Migrations:** `.agents/skills/database.md` [Populate path during setup]
* **Testing & Verification:** `.agents/skills/testing.md` [Populate path during setup]

If the skill file is missing, continue using AGENTS.md alone and report the missing skill.

---

## 5. Autonomous File & Artifact Handlers

Check, maintain, or update these operational files based on runtime events:

* **`BLOCKED.MD` (The Handbrake):** If you hit an environment blocker, missing secret, or failing third-party endpoint, write the exact error and requirements to `BLOCKED.MD` and halt immediately. Do not attempt speculative workarounds.
* **`TECH_DEBT.MD` (Compromise Tracker):** If you must make a temporary trade-off, bypass a standard pattern, or introduce non-reusable code to satisfy the active spec, document the file path, reason, and remediation path in `TECH_DEBT.MD`. Add a `// TECHDEBT:` comment in code.
Only create TECH_DEBT entries for intentional compromises that should be revisited. Do not record ordinary implementation decisions.

* **`LEARNINGS.MD` (Edge Case Archive):** After resolving a non-obvious bug or repository quirk, append a concise root-cause summary and fix pattern to `LEARNINGS.MD` so future sessions avoid repeating the issue.
* **`REVIEWER_FINDINGS.MD` (Audit Log):** On session startup, read `REVIEWER_FINDINGS.MD`. Address any listed architectural regressions, rule violations, or unhandled edge cases flagged by background reviewer agents. If the file is absent, continue normally.
* **`PROMPTS.MD` (Loop Scripts & Prompts):** Store reusable autonomous execution prompts, CLI invocation flags, and Ralph Loop bash scripts in `PROMPTS.MD`.

---

## 6. Execution Loop & Logging Standards

When running inside an autonomous execution loop:

* **Session Isolation:** Treat every loop run as a fresh environment. Read `AGENTS.md` and active `SPECS.md`, execute one spec item, run test suites, update docs, commit, and terminate.
* **Save Iteration Logs:** Pipe all terminal stdout/stderr for each run into `.logs/run-<timestamp>.log`. You may create the directory automatically. 
* **Standard Exit Codes:**
  * `0_DONE` — All items in `SPECS.md` are completed, verified, and checked off.
  * `1_BLOCKED` — Execution halted; blocker details written to `BLOCKED.MD`.
  * `2_BUDGET_EXCEEDED` — Token or context window limit reached; state committed for resumption.
  * `3_STUCK` — Tests repeatedly failing or loop making no git progress across iterations.


## 7. Planning

Before modifying code:

- Inspect affected files.
- Identify dependencies.
- Confirm assumptions through repository inspection.
- Implement the change with the narrowest appropriate scope while preserving maintainability, correctness, and consistency with the existing architecture.

## 8. Verification

Before committing:

- Run the required verification for the modified scope.
- Ensure modified files are intentional.
- Confirm no unrelated files changed.

## 9. Security

- Never commit secrets.
- Never invent credentials.
- Never disable security checks merely to satisfy tests




