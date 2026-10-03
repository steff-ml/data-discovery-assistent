# Templates

One template per interface in [design/interfaces.md](../design/interfaces.md). A run copies the templates it needs into its own folder and fills them in.

## Run folder

```
runs/<yyyy-mm>-<short-name>/
  01-research-question.md      I1   lead
  02-search-scope.md           I2   agent, confirmed by lead (CP1)
  03-dataset-inventory.md      I3   agent
  04-feasibility-dossier.md    I4   agent
  05-lead-calls.md             I5   lead, written before reading 04's recommendations
  06-agreement-report.md       I6   agent (CP2)
  07-value-hypotheses.md       I7   agent, selected by lead (CP3)
  08-pretotype-data-<idea>.md  I8   agent, plus 08-pretotype-data-<idea>.csv
  09-pretotype-<idea>.md       I9   agent, approved by lead (CP4)
  10-demand-signals.md         I10  lead
  11-demand-report.md          I11  agent (CP5)
  12-decision-log.md           I12  agent, every checkpoint
```

## Conventions

- Every file starts with a header (YAML front matter) naming the run, interface, stage, author, status, date and intent codes.
- Text in `<angle brackets>` is a placeholder. HTML comments (`<!-- -->`) are guidance and can be deleted.
- `<idea>` is the short id of a value idea from 07, e.g. `trial-matcher`.
