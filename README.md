# Komplex-Code

A small set of working rules that help a coding assistant run a project in a steady, repeatable way. This repository is not an application. It is a set of instructions and templates that shape how work gets planned, carried out, and improved over time.

## What this is

When you hand a coding assistant a project, it can drift: it invents details, edits files it should not touch, or repeats the same mistake. This harness tries to prevent that by writing down, in one place, how the assistant should behave.

The whole system is built around two ideas:

1. **Do the work.** Implement what the plan asks for, verify it, and stop.
2. **Improve the rules.** Between work sessions, look at what went wrong and make the rules better.

These two jobs are kept separate on purpose. The person doing the work should not also be the person rewriting the rules, or the rules never get a chance to settle.

## How it is organised

```
AGENTS.MD                     The master set of rules the assistant follows
.agents/skills/
  implementation/SKILL.md     Rules for the "do the work" sessions
  repository-evolution/SKILL.md  Rules for the "improve the rules" sessions
.agents/templates/            Blank copies of the working documents
```

### The master rules

[`AGENTS.MD`](AGENTS.MD) is the single source of truth. It covers:

- **Priority.** When instructions conflict, which one wins.
- **Core habits.** Interview before guessing, verify before claiming done, keep edits small, write useful commit messages.
- **Skill routing.** Which skill to load for which kind of session.
- **Document ownership.** Who is allowed to write to each working document.
- **The execution loop.** How a session starts, runs, and reports whether it finished, got blocked, or ran out of budget.

### The two skills

[`.agents/skills/implementation/SKILL.md`](.agents/skills/implementation/SKILL.md) governs the sessions that build things. Its job is to satisfy the active plan with the smallest sensible change, verify the result, and record anything it learned. It is deliberately not allowed to rewrite the rules.

[`.agents/skills/repository-evolution/SKILL.md`](.agents/skills/repository-evolution/SKILL.md) governs the sessions that improve the rules. It reviews what the implementation sessions learned, decides what is worth keeping, and updates the master rules and templates. It has one hard limit: it may not remove or weaken critical safeguards, such as security controls or the ownership model, without explicit approval.

### The working documents

These files are created as needed, each from a matching template in `.agents/templates/`:

- **`SPECS.md`** — the active plan of what to build. Implementation checks off completed items as it goes.
- **`BLOCKED.MD`** — a record of anything that stopped work, and why.
- **`learnings/pending/`** — new discoveries and plan deviations, each in its own file, awaiting evaluation.
- **`learnings/archive/`** — evaluated learning records, moved here once processed.
- **`TECH_DEBT.MD`** — a list of intentional shortcuts that should be revisited later.
- **`REVIEWER_FINDINGS.MD`** — an audit log of regressions and rule violations.
- **`PROMPTS.MD`** — reusable prompts and scripts for running sessions.

## How a session flows

1. Read the master rules and the active plan.
2. Do one item of the plan.
3. Run the checks, confirm the result, and check off the completed item in `SPECS.md`.
4. Record anything learned (in `learnings/pending/`) or anything that blocked progress.
5. Report an exit code: done, blocked, budget exceeded, or stuck.

Between sessions, a separate pass reviews only the new learnings in `learnings/pending/`, decides what is worth keeping, and moves them to `learnings/archive/`.

## Getting started

1. Fill in the project details at the top of [`AGENTS.MD`](AGENTS.MD) (tech stack, build command, test command).
2. Create a `SPECS.md` from the template in `.agents/templates/` describing the first piece of work.
3. Run an implementation session against that plan.
4. After a few sessions, run a repository evolution session to fold what you learned back into the rules.

## Notes

- This is a starting point, not a finished product. Expect to adjust the rules as you use them.
- The domain skill files (frontend, backend, database, testing) are placeholders. Create them under `.agents/skills/` when you have enough conventions to capture.
