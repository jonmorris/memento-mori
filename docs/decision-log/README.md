# Pending decision-log entries

Each file here is one decision waiting to be folded into the table in
`../DECISION-LOG.md`. It is named `YYYY-MM-DD-short-name.md` and holds exactly
one table row. That file's "How to keep this file" section has the rules and
the fold command.

To print the pending entries and count them, from the repo root:

```bash
cat docs/decision-log/2*.md; ls docs/decision-log/2*.md | wc -l
```
