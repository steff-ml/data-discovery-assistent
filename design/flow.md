# Flow view

How work moves from research question to product decision, and who does what. Conventions: [README.md](README.md).

**Actors:** the **data product lead** decides and reviews · the **AI agent** does the work: searches, reads, assesses, drafts, builds · the **pretotype audience** reacts to pretotypes.

## Phase 1 · Discovery and feasibility

From research question to a reviewed feasibility dossier.

### Responsibility matrix

| # | Stage | Data product lead | AI agent | Produces | Intent | Open |
|---|---|---|---|---|---|---|
| 1 | Scope the question | Write question and domain background; **CP1: confirm scope** | Turn the question into search terms, entities and ontologies | Scope | PR5, PR4 | H1 |
| 2 | Discover sources | – | Search for candidate datasets | Candidate list | G1, C1 | H2 |
| 3 | Verify sources | – | Check each dataset exists; drop what does not; record provenance and check date | Dataset inventory | C5, PR2 | |
| 4 | Assess feasibility | – | Read documentation and licence; rate each dataset with a source per claim; flag privacy concerns; never access restricted data | Dossier entry per dataset | G2, C1, C3, C4, PR2, PR3 | H3 |
| 5 | Assess combinability | – | Map shared identifiers and ontologies; name data gaps | Combination assessment | G2 | H5 |
| 6 | Review | Record own go/no-go per dataset *before* seeing the agent's; **CP2: worth continuing?** | Compare the lead's calls with its own; write the decision log | Reviewed dossier, decision log | PR1, S3, ADR 3 | H4, H8, H9 |

### Sequence

```mermaid
---
title: "Data Discovery Assistant · Phase 1: discovery and feasibility"
config:
  fontFamily: "Arial, Helvetica, sans-serif"
  themeVariables:
    fontFamily: "Arial, Helvetica, sans-serif"
  sequence:
    wrap: true
    width: 240
    actorMargin: 90
    noteMargin: 16
    boxMargin: 12
    messageMargin: 40
    noteFontFamily: "Arial, Helvetica, sans-serif"
    messageFontFamily: "Arial, Helvetica, sans-serif"
    actorFontFamily: "Arial, Helvetica, sans-serif"
---
sequenceDiagram
    autonumber
    actor Lead as Data product lead
    participant Agent as AI agent
    participant Src as External data sources

    Note over Lead,Src: How to read this diagram. Time runs from top to bottom, so follow the numbered steps. A solid arrow hands over work, and a dashed arrow returns a result. A loop box repeats for each item, and an alt box shows alternative outcomes. ✋ marks a checkpoint (CP) where nothing continues until the data product lead decides. Codes in brackets refer to intent.yml, where G is a goal, C a constraint, PR a principle and S a success criterion.

    rect rgba(74, 111, 165, 0.10)
    Note over Lead,Src: DISCOVERY. Find out which data exists. [G1]
    Lead->>Agent: Research question and domain background [PR5]
    Agent-->>Lead: Proposed search scope
    Note over Lead: ✋ CP1. The lead confirms or adjusts the scope. [PR1, PR4]
    Lead->>Agent: Approved scope
    Agent->>Src: Search catalogs, databases and literature [C1]
    Src-->>Agent: Candidate datasets
    Note over Agent: The agent keeps only datasets that really exist and records where and when each was found. [C5, PR2]
    end

    rect rgba(90, 138, 74, 0.10)
    Note over Lead,Src: FEASIBILITY. Can the data actually be used? [G2]
    loop For each dataset
        Agent->>Src: Read documentation and licence [C1, C4]
        Src-->>Agent: Documentation
        Note over Agent: The agent rates access, licence, format, quality and freshness, backs every statement with a source, and flags privacy concerns. [PR2, PR3, C3]
    end
    Note over Agent: The agent checks which datasets can be linked together and names the data gaps. [G2]
    Agent-->>Lead: Feasibility dossier with go, no-go or unsure per dataset
    end

    rect rgba(184, 134, 11, 0.12)
    Note over Lead,Src: REVIEW. The lead decides. [PR1]
    Note over Lead: The lead makes their own go/no-go per dataset before reading the agent's advice. [S3]
    Lead->>Agent: The lead's go/no-go calls
    Agent-->>Lead: Where the lead and the agent agree and differ
    alt ✋ CP2. Worth continuing
        Lead->>Agent: Continue to Phase 2 to test demand [G3]
    else ✋ CP2. Nothing worth testing, even with synthetic data
        Lead->>Agent: Stop and record why [PR2]
    end
    end
```

## Phase 2 · Demand testing

From a reviewed feasibility dossier to a product go/no-go. Starts only when CP2 in Phase 1 says "worth continuing".

### Responsibility matrix

| # | Stage | Data product lead | AI agent | Produces | Intent | Open |
|---|---|---|---|---|---|---|
| 7 | Derive value ideas | **CP3: choose which ideas to test** | Derive value ideas the feasibility findings still allow, each with a target audience and a falsifiable hypothesis | Value hypotheses | G3, ADR 4, PR4 | |
| 8 | Prepare data | – | Per idea: use real data where usable; generate a labelled synthetic dataset where data is missing, inaccessible or privacy-flagged | Pretotype dataset | C2, C3, C5, ADR 5 | H11 |
| 9 | Build pretotype | **CP4: approve before it goes out** | Build the pretotype with demand metric and kill threshold | Pretotype | G3, S6, PR1 | |
| 10 | Test demand | Share the pretotype with the audience; collect reactions | Compare demand signals with the kill threshold | Demand report | G3, S6 | H7 |
| 11 | Decide | **CP5: product go/no-go** | Record the decision and open issues (privacy, data gaps) | Decision log entry | ADR 3, PR2 | |

### Sequence

```mermaid
---
title: "Data Discovery Assistant · Phase 2: demand testing"
config:
  fontFamily: "Arial, Helvetica, sans-serif"
  themeVariables:
    fontFamily: "Arial, Helvetica, sans-serif"
  sequence:
    wrap: true
    width: 240
    actorMargin: 90
    noteMargin: 16
    boxMargin: 12
    messageMargin: 40
    noteFontFamily: "Arial, Helvetica, sans-serif"
    messageFontFamily: "Arial, Helvetica, sans-serif"
    actorFontFamily: "Arial, Helvetica, sans-serif"
---
sequenceDiagram
    autonumber
    actor Lead as Data product lead
    participant Agent as AI agent
    actor Aud as Pretotype audience

    Note over Lead,Aud: How to read this diagram. Time runs from top to bottom, so follow the numbered steps. A solid arrow hands over work, and a dashed arrow returns a result. A loop box repeats for each item, and an alt box shows alternative outcomes. ✋ marks a checkpoint (CP) where nothing continues until the data product lead decides. Codes in brackets refer to intent.yml, where G is a goal, C a constraint, PR a principle and S a success criterion. This phase starts when the lead decides at CP2 in Phase 1 that the data is worth continuing with.

    rect rgba(122, 94, 168, 0.10)
    Note over Lead,Aud: VALUE IDEAS. What could this data be used for, and by whom? [G3]
    Lead->>Agent: Reviewed feasibility dossier from Phase 1
    Agent-->>Lead: Value ideas, each with a target audience and a hypothesis [ADR 4]
    Note over Lead: ✋ CP3. The lead chooses which ideas to test. [PR1, PR4]
    Lead->>Agent: Ideas to test
    end

    rect rgba(184, 134, 11, 0.12)
    Note over Lead,Aud: PRETOTYPE. Build the cheapest thing that tests demand. [G3, S6]
    loop For each chosen idea
        alt Real data is usable
            Note over Agent: The agent uses public or aggregated real data. [C2]
        else Data is missing, not accessible or has a privacy concern
            Note over Agent: The agent generates a synthetic dataset with the same structure, clearly labelled as synthetic. [C3, C5, ADR 5]
        end
        Note over Agent: The agent builds the pretotype with a hypothesis, a demand metric and a kill threshold. [S6]
        Agent-->>Lead: Pretotype
        Note over Lead: ✋ CP4. The lead approves the pretotype before anyone outside sees it. [PR1]
    end
    end

    rect rgba(192, 57, 43, 0.08)
    Note over Lead,Aud: DEMAND TEST. Does anyone want this? [G3]
    Lead->>Aud: Share the pretotype
    Aud-->>Lead: Reactions and commitments
    Lead->>Agent: Demand signals
    Agent-->>Lead: Demand compared with the kill threshold
    alt ✋ CP5. Demand above the kill threshold
        Note over Lead: Product go. Building is a separate effort. [ADR 3]
    else ✋ CP5. Demand below the kill threshold
        Note over Lead: Product no-go. [ADR 3]
    end
    Lead->>Agent: Decision
    Note over Agent: The agent records the decision and any open privacy issues or data gaps. [PR2, ADR 5]
    end
```

## Hotspots

| ID | Stage | Open question | Intent |
|---|---|---|---|
| H1 | 1 | In what form is domain background supplied (free text, ontology list, known sources)? | PR5 |
| H2 | 2 | Which discovery channels: data catalogs (e.g. re3data, Google Dataset Search), web search, literature, model knowledge? | G1, S1 |
| H3 | 4 | Documentation only, or also sample the data? | PR4 |
| H4 | 6 | What happens to datasets the agent is unsure about? | PR3 |
| H5 | 5 | Does the flow loop back to discovery when data gaps are found, or go straight to synthetic data? | G1, G2, ADR 5 |
| H7 | 10 | Is sharing with the audience and collecting reactions done by the lead outside the system (as drawn), or by the agent? | G3, S6 |
| H8 | 6, 11 | Format and storage of the decision log | PR2, S5 |
| H9 | 6 | What makes Phase 1 "worth continuing" now that synthetic data can fill gaps? | ADR 3, ADR 5 |
| H10 | all | Which language model and tools does the agent use? | PR6 |
| H11 | 8 | How realistic must synthetic data be for a pretotype to be credible? | C3, S6 |

H6 (checkpoint to choose which ideas get a pretotype) is resolved as CP3.

## Changelog

- v7 (2026-10-03): split into two self-contained diagrams, one per phase, each with its own title, reading key and responsibility matrix.
- v6 (2026-10-03): Phase 2 added to the same diagram. Synthetic data step added for data that is missing, inaccessible or privacy-flagged (intent C3 and ADR 5 extended). New checkpoints CP3 (choose ideas), CP4 (approve pretotype), CP5 (product go/no-go). CP2 reworded to "worth continuing". H6 resolved; H11 added. Pretotype audience added as an actor.
- v5 (2026-10-03): explicit font and spacing so notes render inside their boxes; matrix column renamed to data product lead; context view removed and H10 moved here.
- v4 (2026-10-03): reading key in full sentences at the top; intent codes back in the diagram; automatic text wrapping so notes render inside their boxes.
- v3 (2026-10-03): diagram made self-explanatory for sharing: title, built-in reading key, plain language, no intent IDs (those stay in the matrix); human lane renamed "Data product lead".
- v2 (2026-10-03): two actors (You, AI agent) for the prototype; checks previously assigned to code are done by the agent.
- v1 (2026-10-03): replaced the single flowchart with a responsibility matrix and a sequence diagram per phase; human checkpoints renamed CP1, CP2 to avoid clashing with goal IDs. Phase 1 redrawn; phase 2 pending.
- v0 (2026-10-03): first draft from intent.yml v0.6.
