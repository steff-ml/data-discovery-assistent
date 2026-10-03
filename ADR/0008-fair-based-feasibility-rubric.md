# 8. Feasibility rubric based on FAIR, extended with quality, freshness and privacy

- Status: accepted
- Date: 2026-10-03
- Relates to: [intent.yml](../intent/intent.yml) `system.feasibility_rubric`, `problem.sub_problems`; [design_philosophy.md](../intent/design_philosophy.md)

## Context

Each discovered dataset needs a feasibility assessment that leads to a go/no-go recommendation. The problems listed in the intent (finding data, accessing it, combining it, licensing) closely match the FAIR principles: Findable, Accessible, Interoperable, Reusable (Wilkinson et al. 2016).

## Decision

The feasibility rubric uses the four FAIR dimensions plus three extensions:

- **quality:** coverage, granularity, completeness, known biases
- **freshness:** update frequency and date of last update
- **privacy_risk:** whether use or combination risks re-identification (see [ADR 5](0005-privacy-flag-and-synthesise.md))

## Alternatives considered

- **A custom rubric.** Rejected: harder to defend and to compare with existing assessments.
- **Plain FAIR.** Rejected: does not cover quality, freshness or privacy, which all affect go/no-go.

## Consequences

- The rubric defines the structure of the feasibility dossier, the system's main output.
- FAIR is widely used in scientific data management, so assessments are recognisable to data owners and researchers.
- Outside scientific data (ADR 6), FAIR may fit less naturally and may need revisiting.
