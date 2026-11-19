# Decision log

A dated list of the decisions made in this project, one line each. It is an
index, not a second source of truth: each row names the file and section that
hold the reasoning. In this repo that is:

- `docs/DECISIONS.md`: the why behind each decision, one section per decision.
- `CLAUDE.md`: how changes are made (working conventions).
- jonmorris/memento-mori pull requests, and the git history where nothing else
  records the why.

A Ref of "git history" means the reason was never written down, and the
commit is the only record.

## How to keep this file

- **Add a file, not a row.** A new decision goes in `docs/decision-log/` as its
  own file named `YYYY-MM-DD-short-name.md` (lowercase, hyphenated), holding
  exactly one table row. Never edit the table on a branch: rows appended to
  the same last line by parallel branches always conflict, and separate files
  never do.
- **Fold on main.** Appending the waiting entries to the end of the table, in
  filename order (date, then name), and deleting their files is one command.
  Run it from the repo root, on main, in a commit of its own, whenever the
  folder gets long:

  ```bash
  cat docs/decision-log/2*.md >> docs/DECISION-LOG.md && git rm -q docs/decision-log/2*.md
  ```

  The glob sorts by filename and skips the folder's `README.md`. It relies on
  the `## Log` table staying the last thing in this file.
- **One row per decision, not per commit.** A reversed decision gets a new row
  of kind Reversed. The old row stays.
- **Say the decision, not the change** ("Past weeks drawn in random greys",
  not "edit index.html").
- **Kind** is one of: Product, Design, Content, Engineering, Process,
  Deferred, Reversed. This list is the only place the kinds are defined. The
  repo has no code to keep them in.
- **Ref** names the file → section holding the why. If no why is written
  anywhere, write it there first.
- **Check an entry by eye**, because there is no validator: one line, starting
  and ending with `|`, four cells, a Date matching the filename, a Kind from
  the list, and a non-empty Decision and Ref.

## Log

| Date | Kind | Decision | Ref |
|---|---|---|---|
| 2026-04-14 | Product | A life is shown as a grid of weeks: 52 per row, one row per year of expected life | git history (99c4866) |
| 2026-04-14 | Product | Expected lifespan is US average life expectancy by gender: 73 male, 79 female, 76 other | DECISIONS.md → Life expectancy by gender |
| 2026-04-14 | Design | Lived weeks are drawn dark where they fall inside a skull shape, so the skull appears as life passes | git history (99c4866) |
| 2026-04-14 | Design | Birth date is entered in tap-through steps (year, month, day, then gender) instead of a date field | git history (99c4866) |
| 2026-04-14 | Content | A Seneca quote ("We die every day") frames the grid | git history (99c4866) |
| 2026-04-14 | Engineering | One static HTML file with no build, no dependencies and no backend; the birth date lives only in the browser's localStorage | git history (99c4866) |
| 2026-04-14 | Engineering | Saved data moved to a new storage format, and the older birth-date-only key is still read and migrated | git history (99c4866) |
| 2026-04-14 | Product | A second version drives a TRMNL e-ink display as a private plugin | DECISIONS.md → A TRMNL e-ink version |
| 2026-04-15 | Process | AI-assisted changes follow the CLAUDE.md guidelines: think first, keep it simple, surgical diffs, verify | CLAUDE.md |
| 2026-11-07 | Reversed | The skull no longer emerges from lived weeks; a pixel-art skull sits behind the whole grid instead | DECISIONS.md → Pixel skull behind the grid; past weeks in random greys |
| 2026-11-07 | Design | Past weeks are drawn in a random grey each, between 70% and 90% lightness | DECISIONS.md → Pixel skull behind the grid; past weeks in random greys |
| 2026-11-07 | Process | Claude merges its own pull requests once they merge cleanly and the change is verified | DECISIONS.md → Claude merges its own passing PRs |
