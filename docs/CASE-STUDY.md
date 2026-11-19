# Case study: Memento Mori

A running, modular portfolio case study of Memento Mori, a page that shows
a life as a grid of weeks, with a skull behind it. It also has a companion
version for a TRMNL e-ink display. This is a repo-only doc: it is never built
or shipped.

## How this file works

- **Modules, not chapters.** Each `##` section stands alone, so a write-up can
  pick modules and drop the rest without leaving a gap.
- **Tag lines.** Every module opens with an italic tag line:
  - **Core**: the spine of any version.
  - **Optional**: for the long form or a specific audience, named in brackets.
  - **Evidence**: what to show beside the text, marked `[ ]` until it has been
    captured.
- **Running.** When work is worth telling, add or amend a module and add a row
  to *Log of additions*. Facts and dates come from `DECISION-LOG.md`. This file
  is where they become a story.
- **Placeholders** go in `[[double brackets]]` for the owner to fill in (role,
  tools, metrics, reflections). Never invent them.

## Suggested cuts

| Form | Modules |
|---|---|
| Short | 1, 2, 6, 10 |
| Standard | 1, 2, 3, 4, 6, 7, 10 |
| Long | 1–10 |

## 1. Overview

*Core. Evidence: [ ] screenshot of the grid for a sample birth date; [ ] photo of the TRMNL display.*

Memento Mori asks for a birth date and a gender, then draws that life as
weeks: 52 boxes to a row, one row per year of expected life. Weeks already
lived are filled in, the current week is red, and the rest are empty
outlines. Behind the grid sits a pixel-art skull.

- **Role:** [[your role, e.g. sole designer and developer]]
- **Timeline:** the first commit landed on 2026-04-14 with the app already
  working. The skull was redesigned on 2026-11-07. [[when the work actually
  started, and how long it took before the first commit]]
- **Tools:** HTML, CSS and plain JavaScript in a single file, with no build
  step; a TRMNL e-ink display; Claude Code for later changes. [[design tools,
  anything else you used]]

## 2. The problem

*Core. Evidence: [ ] the Seneca quote as it appears above the grid.*

The page opens with Seneca: "Whatever time has passed is owned by death. We
die every day." The idea is old, but a lifetime is too large a number to feel.
Counted in weeks it becomes about 4,000 boxes, few enough to see on one page,
with a large share already filled in.

[[What made you build this? A moment, a book, a habit you wanted to support.]]

## 3. Reframing the brief

*Optional [long form; design audiences]. Evidence: [ ] screenshot of the original skull-reveal version.*

A life-in-weeks chart is a known format. This project's twist was to make the
grid a memento mori and not just a calendar. In the first version, the weeks
you had lived were drawn darker where they fell inside a skull shape, so the
skull emerged as your life was used up.

That turned the chart from a measurement into a reminder. Its weakness was
that a young user saw almost none of the skull, and an older one saw a
partial, lumpy one (see module 6).

[[Was the skull there from the start, or added along the way? What else did
you consider?]]

## 4. Choosing whose life expectancy

*Core. Evidence: [ ] the gender step in the input flow.*

The grid needs an end, and the project picked the US average life expectancy
at birth as reported by the CDC: 73 years for men, 79 for women and 76 for
everyone else. Gender is asked for only to choose one of those three numbers.

That trade-off is worth naming in a write-up. An average is honest about where
the number comes from, but it is not a prediction for anyone, and a national
average leaves out everything else that shapes a lifespan. The TRMNL version
skips the question and uses a single configurable lifespan, defaulting to 80.

[[Did you consider other sources or a custom lifespan field in the browser
version? Why gender rather than nothing?]]

## 5. Input as a ritual

*Optional [interaction designers]. Evidence: [ ] screen recording of the four steps.*

The birth date isn't typed into a date field. It is picked in four tap-through
steps: a grid of years, then months, then days (impossible days are disabled),
then gender. Each step shows what has been chosen so far and has a Back
button.

[[Why steps instead of a date field? Mobile ergonomics, pacing, or making
entering your birth date feel deliberate?]]

## 6. Redrawing the skull

*Core. Evidence: [ ] before/after screenshots at the same birth date.*

By November 2026, the generated skull looked janky. It was rasterised from
ellipses and curves onto a 52-wide grid, so its edges cut through cells
unevenly, and it showed only in weeks already lived.

The redesign moved the skull behind the grid. It is now a hand-drawn 21×25
pixel-art image in which each skull pixel covers exactly a 2×2 block of week
cells. Its edges fall in the gaps between boxes, so no box is split by the
outline. The boxes on top went the other way: each lived week gets its own
random grey, between 70% and 90% lightness, and the grid reads like texture
over a single clear skull.

One decision was made by looking. A near-black skull was tried first and was
far too heavy over the unlived weeks, so it became a soft mid-grey.

It is also a reversal of module 3's idea. The skull no longer appears over
time; it is always there.

[[How do you feel about losing the "emerging" skull? Did anyone react to the
change?]]

## 7. One idea, two surfaces

*Optional [hardware or e-ink audiences]. Evidence: [ ] photo of the TRMNL device; [ ] the 800×480 render.*

The same grid also runs on a TRMNL e-ink display as a private plugin. That
version is laid out for an 800×480 canvas with only four greys: white, light
grey, dark grey and black. TRMNL renders the page once in a headless
browser and captures it, so there is no input flow. The birth date and
lifespan come from plugin settings instead.

An ambient display changes what the piece is. In a browser it is something
you visit; on a desk it is something you live next to.

[[How long have you had it on a display? Has it changed how you think about
your weeks?]]

## 8. Saying no on the record

*Optional [long form; product audiences]. Evidence: none needed.*

Some things the project deliberately doesn't do, all visible in how it is
built:

- **No accounts and no server.** The birth date is stored only in the
  browser's localStorage and never leaves the device.
- **No build step or dependencies.** Each version is one HTML file.

One question is still open. The TRMNL version keeps the old reveal-the-skull
rendering after the browser version moved on. [[Decide whether to port the
new skull to e-ink, and why.]]

## 9. Working with an AI collaborator

*Optional [audiences interested in AI-assisted workflows]. Evidence: [ ] jonmorris/memento-mori#1 description and screenshots.*

The day after the first commit, the project added a `CLAUDE.md` setting rules
for AI-assisted changes: think before coding, keep it simple, touch only what
the task needs, and define how success will be checked.

The skull redesign was done that way. The owner described the problem in a
sentence. Claude replaced the skull, checked the result by taking screenshots
in a headless browser, adjusted it, and opened a pull request. The owner then
allowed Claude to merge its own PRs once they pass. Later, these running
records were set up so that decisions and their reasons stay written down as
the project moves.

[[What worked and what didn't when working with Claude? Where did you step
in?]]

## 10. Outcome and reflection

*Core. Evidence: [ ] [[any usage, feedback or personal-use evidence]].*

[[What happened after it shipped: who uses it, how often you look at it, any
feedback or numbers.]]

[[What you'd do differently, and what the project taught you.]]

## Log of additions

| Date | Module | Change |
|---|---|---|
| 2026-11-19 | 1–10 | Initial draft from git history, the code and jonmorris/memento-mori#1 |
