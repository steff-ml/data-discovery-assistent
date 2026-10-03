---
run: <run-id>
interface: I8
artifact: Pretotype dataset
idea: <idea-id>
stage: 8
written_by: agent
status: draft
date: <yyyy-mm-dd>
data_file: 08-pretotype-data-<idea-id>.csv
intent: [C2, C3, C5, ADR 5]
---

# Pretotype dataset · <idea-id>

<!-- Data card for the CSV file next to this one. C2: no individual-level real data. -->

## Contents

| Column | Meaning | Origin | Real source |
|---|---|---|---|
| <column> | <what it holds> | <real / synthetic> | <Dxx or "none"> |

## Synthetic parts

<!-- H11 is still open: how realistic synthetic data must be. -->

- **Why synthetic:** <privacy-sensitive / does not exist>
- **How generated:** <method, distributions or rules used, what it was based on>
- **What it does not show:** <limits a viewer should know about>

## Gaps not filled

<!-- Data that exists but cannot be obtained, e.g. paywalled (ADR 5). -->

| Data | Source | Why not obtainable |
|---|---|---|
| <what> | <name> | <paywall / licence / other> |

## Labelling

- Every synthetic value is marked in the CSV: <how, e.g. column `is_synthetic` or a suffix>
- The pretotype shows that data is synthetic: <how>
