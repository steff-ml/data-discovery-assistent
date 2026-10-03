# 5. Privacy: never touch, flag, use synthetic data, resolve at build stage

- Status: accepted
- Date: 2026-10-03
- Relates to: [intent.yml](../intent/intent.yml) `constraints.C1`–`C3`, `system.feasibility_rubric.privacy_risk`, `risks`

## Context

Data about people, especially in small populations such as rare diseases, can identify individuals even without names (e.g. "3 patients with an exon 45 deletion in Belgium"). The system needs a rule for what to do when discovery or feasibility work runs into such data.

## Decision

- The system only accesses open data or data the user has explicit permission for (C1).
- It never ingests, stores or outputs individual-level data (C2).
- It never touches data that could introduce a privacy problem. Any step that finds a privacy concern flags it, and the pretotype uses a synthetic dataset with the same structure instead (C3).
- Resolving privacy questions is deliberately deferred to the build stage. Flagged concerns are carried forward in the decision log.
- Data that a value idea needs but that does not exist is also replaced by a synthetic dataset, so demand can be tested before the data problem is solved. (Added 2026-10-03.)
- Data that exists but cannot be obtained (e.g. paywalled) is not replaced silently: the gap is flagged, and a pretotype that depends on it is normally not shared. (Added 2026-10-03.)
- Synthetic data is always labelled as synthetic and never presented as a real source.

## Alternatives considered

- **Small-count suppression on real data** (e.g. show "fewer than 10" for small counts). Rejected: still involves handling real data about people and requires tuning a threshold; at this stage the goal is to test demand, not to solve privacy.
- **Resolve privacy during feasibility.** Rejected: expensive, and wasted if there turns out to be no demand.

## Consequences

- Demand can be tested even for products whose real data is sensitive.
- Pretotypes may look less realistic when they run on synthetic data.
- Every product that passes the demand test may carry open privacy issues or data gaps into the build stage; the decision log must make these visible.
