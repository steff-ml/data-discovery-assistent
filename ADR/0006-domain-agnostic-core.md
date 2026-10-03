# 6. Domain-agnostic core, beyond rare disease and biomedical data

- Status: accepted
- Date: 2026-10-03
- Relates to: [intent.yml](../intent/intent.yml) `principles.PR5`, `success_criteria.S7`, `risks`

## Context

All current material is about Duchenne Muscular Dystrophy (DMD). A system shaped only around DMD would risk overfitting to biomedical registries, ontologies and trial data, while the underlying problem (expensive feasibility work before demand is known) exists in any domain.

## Decision

The core of the system must work outside rare disease and outside biomedical data. Domain knowledge, such as DMD ontologies and known sources, is supplied as configuration or context, not hard-coded.

## Alternatives considered

- **A DMD or rare-disease specialised tool.** Rejected: faster to build, but limits reuse and bakes domain assumptions into the architecture.

## Consequences

- Design must keep a clear boundary between the generic pipeline and domain context.
- DMD remains the first validation case; a second domain outside rare disease is validated later (S7, deferred until after the first DMD run).
- Some DMD-specific shortcuts are off-limits, even when they would speed up the first run.
