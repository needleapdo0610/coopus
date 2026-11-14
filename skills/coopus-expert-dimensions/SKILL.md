---
name: coopus-expert-dimensions
description: >
  List the dimensions an expert in a domain would check, with depth, instead of
  role-playing "act as an expert". Use when designing an architecture, choosing
  a technology, entering an unfamiliar domain (security, data, pricing, legal,
  UX, infra), or when the user asks "what would an expert consider", "what am I
  missing", "what dimensions matter". For each dimension gives what it asks,
  trade-offs, when it fails in this scenario, and the signal or number an
  expert uses to judge it.
---

# coopus-expert-dimensions

## One job

List the dimensions an expert in the domain would check, each with depth, apply them to the user's design, and find what it has not considered.

## How

1. Name the domains involved; there may be several, e.g. "architecture + security + cost".
2. For each domain, list the dimensions an expert checks, usually five to eight. Be specific: "data consistency", "availability", "observability", "migration path", "cost", not "quality" or "performance".
3. For each dimension, answer four things:

```
### <dimension>
Asks: <one line, e.g. "when two copies disagree, which one wins">
Trade-offs: what A sacrifices, what B sacrifices
Fails here when: <a concrete scenario in the user's design>
Expert judges by: <number or signal, e.g. p99 latency, RPO/RTO, monthly cost, error rate>
Status: covered / partly covered / not covered
```

4. End with the "not covered" and "partly covered" dimensions, ranked by risk, each with one next step.
5. Look up external facts and standards (service limits, regulations) with a source; if you cannot, mark "unverified".

## Don't

- Don't write "As a senior architect, I think...". Role-play changes tone, not coverage.
- Don't list dimension names only. A list without trade-offs and failure cases is breadth, not depth.
- Don't hand over "the best answer". The goal is for the user to learn how this domain judges.
- Don't pad with dimensions irrelevant to this scenario.

## Verify it was done right

- Every dimension has all four fields, and "Fails here when" cites a concrete element of the user's design.
- Every "Expert judges by" is something measurable or observable.
- At least one dimension is "not covered" or "partly covered". If all are covered, check whether the dimensions are too shallow.

## Stop and ask

- When scale, budget, or constraints are unknown and would reverse the trade-offs: ask one question, with your default number.
- In domains that need licensed judgment (law, medicine, finance): state that this is a checklist, not professional advice.
