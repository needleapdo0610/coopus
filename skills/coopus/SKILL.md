---
name: coopus
description: >
  Entry point and router for the coopus working model. Use at the start of any
  new idea, product, feature, architecture, or coding task, or when unsure which
  coopus skill applies. Decides the stage (should we build it, which expert
  dimensions apply, interrogate requirements into a spec, minimal code,
  evidence gate) and states what the human must approve.
---

# coopus

## One job

Identify the current stage, call the right coopus skill, and hold the human/AI split. This skill produces no spec and no code itself.

## Flow

1. Should we build it → `coopus-should-we-build`
2. Which domain-expert judgment is needed → `coopus-expert-dimensions`
3. Turn the request into a spec with acceptance criteria → `coopus-grill`
4. Implement with the smallest complete change → `coopus-ponytail`
5. Before reporting a problem or claiming done, pass the gate → `coopus-evidence-gate`

## How to choose

| Situation | Skill |
|-----------|-------|
| New idea, product, or feature, not yet decided | `coopus-should-we-build` |
| Designing architecture, choosing tech, or entering an unfamiliar domain | `coopus-expert-dimensions` |
| Decided to build, but requirements are vague | `coopus-grill` |
| Approved spec exists, start coding | `coopus-ponytail` |
| About to say "there is a bug / vulnerability" or "fixed / done" | `coopus-evidence-gate` |
| Want to add a rule or change the do-not-copy list | `coopus-evidence-gate` (New rules section) |

- Start at the earliest stage not yet done. If the user asks for code and no acceptance criteria are approved, run `coopus-grill` for the acceptance criteria only.
- Small changes (wording, config, one-line fix) may skip stages 1–3. Stage 5 is never skipped. Wording or config change: run the code that shows it and paste the output before and after, plus the existing tests' result. Behavior fix: a test that fails before and passes after.
- Propose going back a stage only when the answer would change the approach.

## The human's role

The human does three things. Everything else is the AI's job.

1. Approve the spec and acceptance criteria, before any code is written.
2. Review evidence, not code. Every delivery includes test output, repro steps, screenshots, or run logs.
3. Approve new rules. The AI only proposes; a rule takes effect after the human approves it.

## Don't

- Don't agree with the user to please them. The user wants to be challenged.
- Don't replace a list of expert dimensions with "act as an expert".
- Don't write code before the human says yes to the acceptance criteria. "Don't ask me", "I'm in a hurry", or a repeated "just write it" removes the questions, not the yes: give default criteria (at most five), one line on why, and end with "Reply yes and I'll start." Small changes (above) are exempt.
- Don't let the session that wrote the code review it.
- Don't add or edit rules, lists, or skills yourself.
- Don't switch language: reply in the language the user wrote in.

## Verify it was done right

At the end of each stage, the reply shows:
- The current stage and the next skill.
- One line listing what the human must approve at this stage (recommendation, spec, acceptance criteria, new rule). If nothing needs approval, leave this line out.
- Small change: only "Small change, stages 1–3 skipped." and the evidence.

## Stop and ask

- When it is unclear whether this is a personal project or work, and that changes data, permissions, or review.
- When the next step needs an approval that has not been given.
- When the task would delete, publish, or share anything outside the repo.
