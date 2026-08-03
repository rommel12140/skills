# skills

Two agent skills: one for prose, one for interface work.
Each runs either as a constraint before the work is made, or as an audit over work that already exists.

## copy-review

Checks writing against a catalog of AI-writing tells and against the project's own voice.
It covers anything a person reads: landing pages, docs, READMEs, emails, UI microcopy, release notes.
Findings come back by ID with a proposed rewrite, and every number in the text is checked against the figures the project has declared it may cite.
Code blocks, quoted material, tables, and blockquotes are exempt.

## design-review

Checks pages, components, decks, and artifacts against a catalog of AI-generated design tells, across thirty-one gates.
Findings come back by ID and severity with a fix written for the stack in use (plain HTML and CSS, React with Tailwind, or Webflow).
Ten of the gates cannot be answered from source, so the skill renders the page with `chrome-devtools-axi` and judges the pixels; if it cannot render, it reports those gates as unchecked rather than passed.

## No score

Neither skill reports a score.
A composite slop number has no reliable predictive value and hides which specific thing is wrong, so both skills report findings instead: see `copy-review/references/why-no-score.md` and `design-review/references/why-no-score.md`.

## Install

```
npx skills add rommel12140/skills --skill copy-review -g
npx skills add rommel12140/skills --skill design-review -g
```

## voice.md

Both skills read a project's `voice.md` before their own catalogs and treat it as authoritative.
Copy `voice.template.md` into the root of a project as `voice.md` and fill it in, leaving any section empty rather than guessing.
Without it the skills still run on the global catalog alone, and they say so in their output; `design-review` reports gate `X1` as skipped, since it has nothing to check the visual language against.

## Attribution

The catalogs adapt material from several MIT and Apache-2.0 projects.
`ATTRIBUTION.md` records what was taken from each and what was not.
