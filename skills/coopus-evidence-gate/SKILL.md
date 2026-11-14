---
name: coopus-evidence-gate
description: >
  Block unverified claims. Use before reporting a bug, vulnerability, or CVE,
  before saying "fixed", "done", or "tests pass", when reviewing code or
  AI-generated findings, when delivering work, and when proposing a new rule,
  lint, or do-not-copy entry. Requires a reproducing input, PoC, or failing
  test for every problem; fail-to-pass proof plus passing existing tests for
  every fix; labels the rest as speculation; separates writer and reviewer;
  and only lets evidence-backed, human-approved rules into the guardrails.
---

# coopus-evidence-gate

## One job

Claims without evidence do not enter conclusions. That includes new rules: no real case and no human approval, no rule.

## Reporting problems (bug, vulnerability, code review)

1. List many candidates. Don't report "only the certain ones"; the AI cannot be certain on its own, so evidence does the filtering.
2. A candidate is "confirmed" only with one of:
   - An input or PoC that triggers it, with its output.
   - A test that fails now.
3. Anything without evidence is "speculation": state what evidence is missing, and keep it out of conclusions and summaries.
4. Severity states two things: where the attacker or trigger enters, and what privilege it needs. If you cannot state both, downgrade one level and say why.

Format:

```
[confirmed | speculation] <one-line problem>
Location: <file:line>
Evidence: <input / PoC / failing test, with output>
Severity: <high/medium/low>, entry: <...>, privilege: <...>
```

## Claiming fixed or done

1. The same reproducing test fails before the change and passes after; attach both outputs.
2. All existing tests pass; attach the command and an output summary.
3. Tick each acceptance criterion in the spec, each with its evidence.
4. Deliver with evidence: test output, repro steps, screenshots, or run logs. The human reviews evidence, not code.

## Writer and reviewer are separate

- Writing and reviewing happen in different sessions or different models.
- The reviewer may not modify tests or acceptance criteria. If a test looks wrong, report it to the human.
- The writer may add new tests.
- The writer may update a test only when it became invalid because the approved requirements changed.
- The writer must never delete a test, skip it, or loosen an assertion or condition to make it pass.
- If a test fails and the requirement did not change, fix the code, not the test.
- If unsure whether the requirement changed, stop and ask.
- List every test change in the reply: `Test change: <test>, <added | updated>, <reason>`.

## New rules (self-improvement)

1. A new rule comes from a real case: when, what happened, where the evidence is.
2. Objective checks (tests, type checks, lint, repro steps, real data) may be run and fixed by the AI itself.
3. Judgment calls (is the design good, is the copy right) scored by another AI are reference only and cannot become rules.
4. The AI only proposes, in this format; the rule takes effect after human approval:

```
Proposed rule: <one-line rule>
Case: <when, what happened>
Evidence: <link, output, file>
Check: <command if automatable; otherwise "human judgment">
```

5. Prefer rules that can be automated (lint, test, script) over prompt text; they are more reliable.

## Don't

- Don't say "should be fixed" or "looks fine". If it was not run, write "unverified".
- Don't put speculation in summaries, titles, or commit messages.
- Don't edit rule files, skills, or `docs/do-not-copy.md` yourself.
- Don't propose a permanent rule from a one-off error; confirm it reproduces first.

## Verify it was done right

- Every "confirmed" has evidence that can be re-run; every "speculation" says what is missing.
- Every "done" has a fail-to-pass record and existing-test results.
- Every test change is listed with its reason; no test was deleted, skipped, or loosened.
- New rules use the "Proposed rule" format; none takes effect before human approval.

## Stop and ask

- When it cannot be reproduced and no test can be written: report as speculation and ask whether to keep digging.
- When unsure whether a failing test is invalid because the approved requirements changed, or when the fix requires changing acceptance criteria.
- When a possible security issue's PoC would touch production or other people's data: do not run it, ask first.
