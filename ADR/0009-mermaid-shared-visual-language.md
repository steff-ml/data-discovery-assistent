# 9. Mermaid as the shared visual language for human–AI system design

- Status: accepted
- Date: 2026-10-03
- Relates to: [design/README.md](../design/README.md); [design_philosophy.md](../intent/design_philosophy.md#system-design-methodology)

## Context

This system is designed by a human and an AI agent working together, and the system itself divides work between a human and AI. Design diagrams are therefore read, edited and reasoned about by both. A diagram that only a human can read (an image, a drawing tool's file) cannot be reliably updated by the AI; a format that only renders well for machines is hard for the human to review.

## Decision

- Design diagrams are written in **Mermaid**, stored as text in the repository, and changed through normal versioned edits.
- The format must be **interpretable by both**: readable as source by an AI agent, and rendered visually for the human.
- Diagrams must make the **split of responsibilities between human and AI** clearly visible. The exact swimlane format is still being settled.

## Alternatives considered

- **HTML pages** (as used for earlier swimlane diagrams on claude.ai). Visually rich, but presentation and content are mixed, which makes changes hard to review and verbose for an AI to edit.
- **Drawing tools** (draw.io, Excalidraw, Miro). Good for humans; files are not meant to be read or edited as text, and changes are hard to review.
- **PlantUML.** Has native swimlanes in activity diagrams, which Mermaid lacks, but needs a Java or server renderer and does not render natively on GitHub or in VS Code.

## Consequences

- Every design change is visible in git history, and the AI can update diagrams directly.
- Mermaid has no native swimlane diagram, so separating responsibilities has to be done with workarounds (subgraphs per actor, or a sequence diagram with actors as lanes). Layout control is limited.
- Rendering in VS Code needs a Mermaid extension.
