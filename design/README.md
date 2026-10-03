# System design

Design of the Data Discovery Assistant, derived from [intent.yml](../intent/intent.yml). Decisions are recorded in [ADR/](../ADR/README.md); the choice of visual language is [ADR 9](../ADR/0009-mermaid-shared-visual-language.md).

## Views

| View | Shows | Notation | Changes |
|---|---|---|---|
| [Flow](flow.md) | Per phase: who does what, and in which order | Responsibility matrix (Markdown table) + UML sequence diagram (Mermaid) | Every iteration |

Everything is plain text in git: the AI reads and edits the source, you read the rendered view. Diagrams render on GitHub and in VS Code's Markdown preview (with a Mermaid extension such as *Markdown Preview Mermaid Support*).

## Actors

The prototype has two actors. They are the columns of the responsibility matrix and the lanes of the sequence diagram.

| Actor | Role | Rule of thumb |
|---|---|---|
| **You** | Decide and review | Every checkpoint is yours (PR1) |
| **AI agent** | Search, read, assess, draft | Cites every claim; never the last word on decisions |

## Notation

**Responsibility matrix.** One row per stage. Columns: You, AI agent, what the stage produces, the intent IDs it serves, and open hotspots. A dash means the actor has no part in that stage.

**Sequence diagram.** Meant to be shared on its own, so it carries a title and a reading key, uses plain language and no intent IDs (those stay in the matrix). Columns are the actors plus external sources; time runs top to bottom.

| Element | Meaning |
|---|---|
| Solid arrow | A request or hand-over of work |
| Dashed arrow | A result returned |
| Shaded block | A phase |
| `loop` frame | Repeated per item |
| `alt` frame | A branch, e.g. a checkpoint outcome |
| ✋ note or `alt` option | Checkpoint: the flow waits for the data product lead (CP# in the matrix) |
| Note on **AI agent** | Work the agent does internally, with the intent ID it serves |

**IDs.** Intent: goals G1–G3, constraints C1–C5, principles PR1–PR6, success criteria S1–S7. Design: checkpoints CP#, hotspots H# (open questions, listed per phase). Decisions: ADR #.

## How an iteration works

1. **Walk** a phase from start to end and check each stage against the intent.
2. **Mark** anything the intent does not decide as a hotspot (`H#`).
3. **Assign** each stage to actors in the responsibility matrix, and check the rules of thumb above.
4. **Resolve** hotspots. A resolved hotspot is removed; if the decision is significant, it gets an ADR.
5. **Update** the matrix and diagram, and add a line to the view's changelog.
