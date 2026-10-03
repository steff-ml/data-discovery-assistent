# 1. The system is a pre-investment filter, not a data catalog or build pipeline

- Status: accepted
- Date: 2026-10-03
- Relates to: [intent.yml](../intent/intent.yml) `system.description`, `goals`, `non_goals`

## Context

Finding out whether a data product is feasible requires expert effort (what data exists, where, in which schema, whether it can be combined, under which licence). That effort is paid before any demand is proven, so promising data products are neglected or built without validation. The first draft of the intent described the system as one "for discovering and managing data assets".

## Decision

The system is a cheap filter that runs before expert effort is committed: discover datasets, assess feasibility, test demand with pretotypes. Data management and building data products are explicit non-goals.

## Alternatives considered

- **Data catalog / data management tool** (original description). Rejected: overlaps with existing catalogs (DataHub, Collibra) and does not address the cost-before-demand problem.
- **End-to-end build pipeline.** Rejected: invests in building before demand is known, which is the problem being solved.

## Consequences

- The system stops at pretotypes; anything beyond that is a separate effort.
- Success is measured by speed and quality of go/no-go decisions, not by catalog coverage.
- Discovered datasets are not maintained or governed by the system after assessment.
