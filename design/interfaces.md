# Interfaces

What passes between the data product lead and the AI agent, derived from the "Produces" column in [flow.md](flow.md). Each interface is an artifact: a file one actor writes and the other reads. Conventions: [README.md](README.md).

**Status:** register drafted; a first template per interface is in [templates/](../templates/README.md). Conventions below are in use.

## Register

| ID | Artifact | From → To | Stage | Purpose | Open |
|---|---|---|---|---|---|
| **Phase 1** | | | | | |
| I1 | Research question | Lead → Agent | 1 | The question, domain background and known sources that start a run | H1 |
| I2 | Search scope | Agent → Lead | 1, CP1 | Search terms, entities and ontologies; the lead confirms or adjusts it | |
| I3 | Dataset inventory | Agent → Agent, Lead | 2–3 | Every dataset found and verified, with where and when it was found | |
| I4 | Feasibility dossier | Agent → Lead | 4–5 | Per dataset: rubric ratings with sources, go/no-go recommendation, confidence flag. Plus how datasets link and which gaps remain | |
| I5 | Lead's calls | Lead → Agent | 6 | The lead's own go/no-go per dataset, made before reading the agent's | |
| I6 | Agreement report | Agent → Lead | 6, CP2 | Where the lead and the agent agree and differ | |
| **Phase 2** | | | | | |
| I7 | Value hypotheses | Agent → Lead | 7, CP3 | Value ideas, each with target audience and falsifiable hypothesis; the lead picks which to test | |
| I8 | Pretotype dataset | Agent → Agent, Lead | 8 | The data behind a pretotype, real or synthetic, every part labelled | H11 |
| I9 | Pretotype | Agent → Lead | 9, CP4 | The pretotype itself plus its hypothesis, demand metric, kill threshold and data flags | |
| I10 | Demand signals | Lead → Agent | 10 | Reactions and commitments collected from the audience | |
| I11 | Demand report | Agent → Lead | 10, CP5 | Demand compared with the kill threshold | |
| **Both phases** | | | | | |
| I12 | Decision log | Agent → Lead | all CPs | Every checkpoint decision with its reason, plus open privacy issues and data gaps | H8 |

**Not in this register:** how the agent talks to external data sources (agent design: H2, H3) and how the lead shares pretotypes with the audience (outside the system).

## Conventions

- **One folder per run**, e.g. `runs/2026-10-dmd-therapy-eligibility/`, holding all artifacts of that run, numbered in flow order.
- **Markdown files with a short structured header** (YAML front matter): readable for the lead, parseable for the agent, versioned in git. This follows the same reasoning as [ADR 9](../ADR/0009-mermaid-shared-visual-language.md).
- **Datasets** (I8) as CSV next to the Markdown, so they can be opened in any tool.
- **Every artifact names the run, its stage and the intent codes it serves**, so it can be traced back.

## Changelog

- v1 (2026-10-03): first template per interface in templates/; conventions adopted. I5 and I6 kept as separate files for now (could later merge into the dossier).
- v0 (2026-10-03): register of 12 interfaces from flow.md v9; proposed conventions.
