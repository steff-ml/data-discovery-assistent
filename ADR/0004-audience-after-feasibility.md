# 4. The data product audience is identified after feasibility

- Status: accepted
- Date: 2026-10-03
- Relates to: [intent.yml](../intent/intent.yml) `stakeholders.data_product_audience`, `system.outputs`, `goals.G3`, `success_criteria.S6`

## Context

Pretotypes test demand, so they need a target audience. Who that audience is depends on which value ideas are still possible, and that depends on what data turns out to be feasible. For example, if individual-level data cannot be used and only population-level data remains, use cases aimed at individual patients and their audiences drop out.

## Decision

The audience is not an input. The pipeline order is:

1. Discover datasets.
2. Assess feasibility.
3. Derive value hypotheses that remain possible given the feasibility findings.
4. Identify the audience for each value hypothesis.
5. Build pretotypes that test that audience's demand.

## Alternatives considered

- **Audience as an input up front.** Rejected: fixes value ideas before knowing what data allows, leading to pretotypes that promise products the data cannot support.

## Consequences

- "Value hypotheses with target audience" is an explicit output between the feasibility dossier and the pretotypes.
- Every pretotype must name its audience and be consistent with the feasibility findings (S6).
- The order is easy to undo by accident (e.g. by adding an audience field to the input form); this ADR is the reason not to.
