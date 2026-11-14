---
name: coopus-should-we-build
description: >
  Challenge whether an idea, product, startup, or feature should be built at
  all before discussing how. Use when the user shares a new idea, product
  concept, startup plan, or feature request, or asks "should I build this",
  "is this worth it", "who would use this". Runs a pro/con debate covering
  target users, their scenarios, why they would switch, and existing
  alternatives, then gives a build / don't-build recommendation with
  confidence, assumptions, and what evidence would flip it.
---

# coopus-should-we-build

## One job

Before discussing how, decide whether it should be built, and end with a build / don't-build recommendation.

## How

1. Restate the idea in one or two sentences: whose problem it solves. If you cannot, ask first.
2. List target users, at least two different roles. For each:
   - Scenario: when, doing what, they hit this problem.
   - Today: the method or tool they use now.
   - Why switch: how much better the new way must be for them to switch.
3. Market comparison: list existing alternatives, including "do nothing" and manual workarounds. Look them up yourself, with source and date; if you cannot, mark "unverified".
4. Con: the three strongest arguments against. Write them as a real skeptic would; no straw men.
5. Pro: the three strongest arguments for.
6. Key unknowns: facts whose answer would change the conclusion. For each, the cheapest way to test it (five interviews, a landing page, one dataset).
7. Recommendation, fixed format:

```
Recommendation: build / don't build / validate first
Confidence: high / medium / low, one-line reason
Depends on:
1. ...
Flips if: seeing <evidence> changes it to <opposite>
Next: <cheapest validation, or hand off to coopus-grill>
```

## Don't

- Don't discuss implementation, tech choices, or timelines at this stage.
- Don't say "build" because the user seems keen. Write the con side first (step 4); it reduces agreeing by default.
- Don't use market numbers without a source.
- Don't answer "it depends". If information is missing, the recommendation is "validate first", with what to validate.

## Verify it was done right

- At least two user roles, each with scenario, current method, and reason to switch.
- Three pros and three cons, with at least one con the user did not raise.
- All five recommendation fields filled; "Flips if" names observable evidence, not "if things change".
- Every external fact has a source or is marked "unverified".

## Stop and ask

- When the target user or the problem is unclear: ask one question, with your guess.
- When the recommendation is "don't build" or "validate first" and the user has already invested a lot: state it plainly, let the human decide, and do not proceed on your own.
- When the judgment needs internal company data or private data.
