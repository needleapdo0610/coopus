---
name: coopus-grill
description: >
  Interrogate a vague request into a buildable spec with acceptance criteria
  approved before any code is written. Use when the user wants something built
  but the requirements are fuzzy, says "grill me", "ask me questions first",
  "help me write a spec", or hands over a one-line task. Asks only questions
  whose answer changes the approach, numbered with a recommended answer, looks
  up facts itself, and lists remaining assumptions for confirmation. Based on
  Matt Pocock's grill-me, plus a should-we-build check first.
---

# coopus-grill

## One job

Before any code, turn a vague request into a spec with acceptance criteria, and get it approved by the human.

## How

1. Confirm "should we build it" has a conclusion. If not, run `coopus-should-we-build`; for a small task, three lines will do: the problem, who uses it, what happens if we don't.
2. Look up facts yourself: existing patterns in the repo, package versions, API limits. Don't ask the human for them.
3. Arrange the remaining decisions as a tree. Ask first the questions that affect the most later decisions.
4. At most three questions per round, in this format:

```
1. <question>
   Recommended: <your answer>, because <one-line reason>
   If the other option: <how the approach changes>
```

   "yes" or "1 yes" accepts the recommendation.
5. Ask only questions whose answer changes the approach. Record the rest as assumptions.
6. When no approach-changing questions remain, write the spec:

```
## Goal
## Out of scope
## Users and scenarios
## Approach
## Acceptance criteria
- [ ] <observable or automatically checkable, e.g. "input X returns Y", "test Z passes">
## How to prove it works
<tests, commands, repro steps, screenshots or logs to attach>
## Assumptions (confirm or reject)
- A1 ...
## Open
```

7. Ask the human to approve the spec, especially the acceptance criteria and assumptions. Only then hand off to `coopus-ponytail`.

## Don't

- Don't ask a dozen questions at once.
- Don't ask what the repo, docs, or web can answer.
- Don't write uncheckable criteria like "fast" or "intuitive". Rewrite them as numbers or concrete behavior.
- Don't write code before the spec is approved, and don't "build a first version and see".
- After approval, don't change acceptance criteria to make the implementation pass. To change them, ask the human.

## Verify it was done right

- Every question has a recommended answer and "if the other option".
- Every acceptance criterion maps to a check in "How to prove it works".
- All assumptions are listed so the user can answer each with yes or no.
- The last line of the reply says "Acceptance criteria pending approval" or "Approved, handing off to coopus-ponytail".

## Stop and ask

- After every round of questions: wait for answers before continuing.
- When two reasonable approaches differ a lot and no available information decides between them.
- When the request conflicts with the `coopus-should-we-build` conclusion.
