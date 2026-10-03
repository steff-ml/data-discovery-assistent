# 3. Two-level go/no-go: the system recommends per dataset, the product lead decides per product

- Status: accepted
- Date: 2026-10-03
- Relates to: [intent.yml](../intent/intent.yml) `stakeholders.decision_makers`, `non_goals`, `principles.PR1`, `glossary.go_no_go`

## Context

The system produces go/no-go recommendations, but the decision that matters is whether to build a data product. It was not defined how dataset-level verdicts relate to that product decision, or who makes it.

## Decision

- **Dataset level:** the system gives a go / no-go / needs-review recommendation per dataset, which is reviewed by a human.
- **Product level:** the data product lead decides, driven by demand. If a pretotype's demand signal stays below its kill threshold, the product is a no-go.

## Alternatives considered

- **The system scores or decides at product level.** Rejected: conflicts with keeping humans in the loop, and demand is a judgement the product lead owns.
- **Aggregate dataset verdicts into a product verdict.** Rejected: feasible data does not imply demand; demand drives build decisions.

## Consequences

- The system's last output for a product idea is evidence (feasibility dossier, pretotype results), not a verdict.
- Automation stops at dataset recommendations; review and decision tooling should support the product lead rather than replace them.
- Evaluation of the system (S3) is about dataset-level recommendations only.
