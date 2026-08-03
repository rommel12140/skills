# skills

Three agent skills: one for prose, one for interface work, one for the daily report.
The first two run either as a constraint before the work is made, or as an audit over work that already exists.

## copy-review

Checks writing against a catalog of AI-writing tells and against the project's own voice.
It covers anything a person reads: landing pages, docs, READMEs, emails, UI microcopy, release notes.
Findings come back by ID with a proposed rewrite, and every number in the text is checked against the figures the project has declared it may cite.
Code blocks, quoted material, tables, and blockquotes are exempt.

## design-review

Checks pages, components, decks, and artifacts against a catalog of AI-generated design tells, across thirty-one gates.
Findings come back by ID and severity with a fix written for the stack in use (plain HTML and CSS, React with Tailwind, or Webflow).
Ten of the gates cannot be answered from source, so the skill renders the page with `chrome-devtools-axi` and judges the pixels; if it cannot render, it reports those gates as unchecked rather than passed.

## eod

Writes the owner's end-of-day report from whatever he dictated, in his format: a dated line, one main-outcome paragraph, then up to four priority bullets in priority order.
It is built against one specimen, his own EOD for 30 July 2026, which is the authority on format, tone, length and punctuation; the derived rules carry IDs so a violation can be named.
Dictation is the primary mode and works with nothing else available. On request it will read the day's commits and merged pull requests to fill gaps, but found work is offered to him rather than written into a bullet, and it never pads to four.

## No score

No skill here reports a score.
A composite slop number has no reliable predictive value and hides which specific thing is wrong, so the review skills report findings instead: see `copy-review/references/why-no-score.md` and `design-review/references/why-no-score.md`.
`eod` rates nothing at all. It reports a day, and a day is not graded.

## Install

```
npx skills add rommel12140/skills --skill copy-review -g
npx skills add rommel12140/skills --skill design-review -g
npx skills add rommel12140/skills --skill eod -g
```

## voice.md

`copy-review` and `design-review` read a project's `voice.md` before their own catalogs and treat it as authoritative.
Copy `voice.template.md` into the root of a project as `voice.md` and fill it in, leaving any section empty rather than guessing.
Without it the skills still run on the global catalog alone, and they say so in their output; `design-review` reports gate `X1` as skipped, since it has nothing to check the visual language against.

`eod` does not read `voice.md`.
A `voice.md` scopes one project's outward copy, and an EOD is neither outward copy nor scoped to one project: the specimen alone covers four.
Its authority is `eod/references/specimen.md`, which is the owner's own writing rather than a project's.

## Attribution

The catalogs adapt material from several MIT and Apache-2.0 projects.
`ATTRIBUTION.md` records what was taken from each and what was not.
