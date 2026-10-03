# 7. v1 is single-user and favours learning over polish

- Status: accepted
- Date: 2026-10-03
- Relates to: [intent.yml](../intent/intent.yml) `principles.PR6`, `stakeholders`

## Context

The system is built and used by one person, who is the data product lead, the domain expert reviewer and the decision-maker. The goal of v1 is to learn what works, not to run efficiently at scale.

## Decision

- v1 serves a single user.
- It may use capable, heavier models and tools.
- A rework to simpler models and tools is planned. Demand decides when and how.

## Alternatives considered

- **Optimise cost and simplicity from the start.** Rejected: slows down learning before it is known which parts of the system are worth keeping.
- **Design for multiple users or teams now.** Rejected: no such users yet.

## Consequences

- Technical debt is accepted on purpose; the later rework is the plan, not a correction.
- No multi-user concerns (access management, collaboration, shared state) in v1.
- Self-review bias is a known risk, since the user also reviews the system's output. It is mitigated by recording one's own go/no-go before looking at the system's (S3).
