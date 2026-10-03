# 2. DMD is a validation case, not the product

- Status: accepted
- Date: 2026-10-03
- Relates to: [intent.yml](../intent/intent.yml) `value`, `success_criteria.S1`; [business_case.md](../intent/business_case.md); [scientific_background.md](../intent/scientific_background.md)

## Context

The earlier work in this repository (`business_case.md`, `scientific_background.md`) makes the case for a Duchenne Muscular Dystrophy (DMD) data platform that links mutation profiles to therapy and trial eligibility. The first draft of the intent mixed the value of that DMD product with the value of the discovery system itself.

## Decision

The discovery system and the data products it evaluates are kept separate. DMD is the first validation case: its hand-curated source list is the reference set for measuring discovery recall, and the DMD data product is one possible output of the system.

## Alternatives considered

- **Build the DMD data platform directly**, as described in `business_case.md`. Rejected: commits expert effort before demand is proven, which the discovery system is meant to prevent.
- **Keep both in one intent.** Rejected: blurs what the system is for and makes success criteria ambiguous.

## Consequences

- `intent.yml` states system value (time and cost to a go/no-go) separately from output value (the DMD use cases).
- `business_case.md` and `scientific_background.md` become supporting material and validation input, not the system's specification.
- The DMD data product itself goes through the system's own go/no-go like any other idea.
