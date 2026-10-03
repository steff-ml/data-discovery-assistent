---
run: <run-id>
interface: I4
artifact: Feasibility dossier
stage: 4-5
written_by: agent
status: draft
date: <yyyy-mm-dd>
intent: [G2, C1, C3, C4, PR2, PR3, ADR 3, ADR 8]
---

# Feasibility dossier

<!-- Lead: write 05-lead-calls.md from the per-dataset evidence BEFORE reading the Summary and the Recommendation lines (S3). -->

## Summary

| ID | Name | Recommendation | Confidence | Main reason |
|---|---|---|---|---|
| D01 | <name> | <go / no-go> | <high / medium / low> | <one line> |

## Per dataset

### D01 · <name>

| Criterion | Finding | Source |
|---|---|---|
| Findable | <persistent identifier? listed in catalogs?> | <url> |
| Accessible | <open download / API / registration / subscription / paywall / data access committee> | <url> |
| Interoperable | <identifiers and ontologies used> | <url> |
| Reusable | <licence, terms of use, redistribution, commercial use> | <url> |
| Quality | <coverage, granularity, completeness, known biases> | <url> |
| Freshness | <update frequency, last update> | <url> |
| Privacy risk | <none / flagged: why> | <url> |

- **Recommendation:** <go / no-go>
- **Confidence:** <high / medium / low>, because <what makes the agent more or less certain>
- **Reason:** <two or three sentences>

<!-- Repeat per dataset. Every finding needs a source (PR2). Where the agent could not verify something, say so (PR3). -->

## Combination

| Datasets | Shared identifier or ontology | Can be linked? | Notes |
|---|---|---|---|
| D01 + D02 | <e.g. HGVS variant notation> | <yes / partly / no> | <mapping needed, loss of granularity> |

## Data gaps

| Gap | Needed for | Targeted search result | Remaining status |
|---|---|---|---|
| <what is missing> | <which kind of value idea> | <found Dxx / nothing found> | <filled / privacy-sensitive / does not exist / exists but cannot be obtained> |
