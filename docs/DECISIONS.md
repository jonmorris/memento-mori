# Decisions

The reasoning behind decisions in this project, one section per decision.
`DECISION-LOG.md` is the dated index; its Ref column points at sections here.

This file was started on 2026-11-19, after most of the history below. Each
section says where its reason comes from. Where nothing records the reason,
it says so instead of guessing.

## Life expectancy by gender

`index.html` sizes the grid from US average life expectancy at birth: 73 years
for male, 76 for other and 79 for female. The code comment cites "CDC, recent
figures". Asking for gender only serves to pick one of these three numbers.

The TRMNL version has no gender step. It takes a single lifespan setting,
which defaults to 80 years.

Source: the `LIFESPANS` comment in `index.html`.

## A TRMNL e-ink version

`trmnl.html` draws the same grid for a TRMNL e-ink display: an 800×480 canvas
with a 2-bit palette (white, `#aaaaaa`, `#555555`, black). It is built to run
as a TRMNL Private Plugin, so the birth date and lifespan become Liquid merge
variables. TRMNL renders the page once in a headless browser and captures the
result, so the script runs at render time and needs no interaction.

Source: the comments at the top of `trmnl.html`'s style and script blocks.

## Pixel skull behind the grid; past weeks in random greys

Until this change, lived weeks revealed a skull: a 52×N map rasterised from
ellipses and curves decided which past weeks were drawn dark. The owner found
the result janky. The shapes didn't land cleanly on whole cells, and the skull
only showed in the part of life already lived.

The replacement is a hand-drawn 21×25 pixel-art skull drawn as the grid's
background. Each skull pixel covers exactly a 2×2 block of week cells, and its
edges fall in the middle of the gaps, so no box is split by the outline. The
boxes sit on top in one consistent style. At the owner's request, each past
week is a random grey between 70% and 90% lightness. A near-black skull was
tried first and was too heavy over the future weeks, so the skull is a soft
mid-grey (`#b4b4b4`).

The greys are picked again on each page load. `trmnl.html` still uses the old
reveal-the-skull approach; whether to port the change there is undecided.

Source: the owner's request and jonmorris/memento-mori#1.

## Claude merges its own passing PRs

The owner allowed Claude to merge pull requests it opened once they pass.
In this repo, which has no CI, "pass" means the PR merges cleanly and the
change has been checked by running it.

Source: the owner's instruction in the session that merged
jonmorris/memento-mori#1.

## Running project records

Decisions are indexed in `DECISION-LOG.md`, and the story of the project is
kept as a modular portfolio case study in `CASE-STUDY.md`. Both are repo-only
docs. The log is an index: the reasoning stays in this file.

New log entries go in as one file per decision under `docs/decision-log/` and
are folded into the table on main. Rows appended to the end of the same table
by parallel branches always conflict, and separate files never do.

The repo has no package manifest, test runner or CI, so the convention runs
without tooling. The fold is a shell command, and entries are checked by eye.
If the project gains a toolchain, a validator and a test that checks every
entry file are the obvious next step.

Source: the owner's request on 2026-11-19.
