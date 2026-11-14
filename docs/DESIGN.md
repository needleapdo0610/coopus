# coopus design

## Problem

A personal AI working model, packaged as a skills pack in the `SKILL.md` format so the same files work in Claude Code and Codex: decide whether to build, list the expert dimensions, turn vague requests into an approved spec, make the smallest complete change, and back every claim with evidence.

## Sources

- **grill-me** by Matt Pocock ([mattpocock/skills](https://github.com/mattpocock/skills), MIT). `coopus-grill` takes the questioning approach only: a decision tree, a recommended answer for every question, and looking up facts instead of asking. No text was copied.
- **ponytail** by Dietrich Gebert ([DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail), MIT). Its `SKILL.md` is forked as `coopus-ponytail`. The original license is kept in [`skills/coopus-ponytail/LICENSE-ponytail`](../skills/coopus-ponytail/LICENSE-ponytail) and the changes are listed in [`skills/coopus-ponytail/NOTICE.md`](../skills/coopus-ponytail/NOTICE.md).

## Own parts

- `coopus`: entry point that picks the stage and the next skill.
- `coopus-should-we-build`: con/pro debate, users and scenarios, market comparison, build / don't-build recommendation.
- `coopus-expert-dimensions`: the dimensions an expert checks, each with trade-offs, failure cases, and a measurable signal.
- `coopus-grill`: questions that change the approach, ending in a spec with acceptance criteria.
- `coopus-evidence-gate`: no claim of a bug, a fix, or a new rule without reproducible evidence and human approval.
- The do-not-copy list ([`templates/do-not-copy.md`](../templates/do-not-copy.md)) and the test-modification rules (add tests freely; update only on an approved requirement change; never delete, skip, or loosen; list every change).

## Non-goals

- No private or company information, local paths, or accounts in this repo.
- Evaluation tasks are maintained separately, not in this repo.
