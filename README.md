# skills

Four agent skills: one for prose, one for interface work, one for page structure and component systems, one for the daily report.
The writing skill supports constraints and audits; the design skill supports building, scoped refinement and audits; the build skill wireframes pages and specifies component systems.

## copy-review

Checks writing against a catalog of AI-writing tells and against the project's own voice.
It covers anything a person reads: landing pages, docs, READMEs, emails, UI microcopy, release notes.
Findings come back by ID with a proposed rewrite, and every number in the text is checked against the figures the project has declared it may cite.
Code blocks, quoted material, tables, and blockquotes are exempt.

## design-review

Designs, builds, refines and audits websites and interfaces against an Awwwards standard of art direction, typography, motion, usability and execution.
Its catalog of AI-generated design tells remains the floor, with a build playbook, primary-source award research, craft references, worked examples and regression evals above it.
Motion references cover GSAP, Lenis, kinetic type, page transitions, Three.js, React Three Fiber and shaders, with starter patterns and performance and accessibility budgets.
Persuasion pages require a brand-derived signature, an expressive opening or handoff and a later narrative transformation, while operational pages preserve task-focused behavior.
Refinement preserves accepted work, while reviews return concrete findings and stack-appropriate fixes.
Rendered checks use `chrome-devtools-axi` when available; source-only work leaves visual and motion judgments explicitly unchecked.
The skill also applies relevant checks to static artifacts, and never promises an award or reports a synthetic quality score.

## awwwards-build

Wireframes a page, designs its sections and builds its components to the standard of recent Awwwards Sites of the Day, in one pass from a brief.
It works in order: the page's one-sentence argument, an inventory of the evidence that actually exists, a sequence of beats, a brief for every section, desktop and narrow wireframes, motion as states, then the component set and its acceptance gates.
The motion plan assigns a level to every section and prototypes the signature early; removing unsupported imagery requires an equally strong honest visual replacement.
Every rule is labelled as observed on a winner, stated by the studio that made it, or this skill's own recommendation, and it never presents a recommendation as an Awwwards requirement: no section count, grid, radius or timing is one.
Its sources were re-checked against award records, studio case studies, live pages and published Carbon, GOV.UK and W3C numbers before it was written; they are cited in `awwwards-build/references/evidence.md`.
Use it when the deliverable is a page's structure, its sections or a component system; `design-review` covers general builds, refinement and audits, and audits what this skill produces.

## eod

Writes the owner's end-of-day report from whatever he dictated, in his format: a dated line, one main-outcome paragraph, then up to four priority bullets in priority order.
It is built against a corpus of three of his own EODs, from 28, 29 and 30 July 2026, which together are the authority on format, tone, length and punctuation; every derived rule carries an ID and names which of the three support it.
What the three do differently is his to vary and is never normalised: the greeting, the punctuation around the date, where the blank lines fall, how many bullets, which separator follows a workstream name, and how he capitalises his own project names from one sentence to the next.
The rule that outranks the rest: it assembles and orders, it does not re-word. The roughness in dictated speech is the voice, so a sentence that comes out grammatically better than it went in is a defect.
Dictation is the primary mode and works with nothing else available. On request it will read the day's commits and merged pull requests to fill gaps, but found work is offered to him rather than written into a bullet, and it never pads to four.

## No score

No skill here reports a score.
A composite slop number has no reliable predictive value and hides which specific thing is wrong, so the review skills report findings instead: see `copy-review/references/why-no-score.md` and `design-review/references/why-no-score.md`.
`eod` rates nothing at all. It reports a day, and a day is not graded.

## Install

```
npx skills add rommel12140/skills --skill copy-review -g
npx skills add rommel12140/skills --skill design-review -g
npx skills add rommel12140/skills --skill awwwards-build -g
npx skills add rommel12140/skills --skill eod -g
```

## voice.md

`copy-review` and `design-review` read a project's `voice.md` before their own catalogs and treat it as authoritative.
Copy `voice.template.md` into the root of a project as `voice.md` and fill it in, leaving any section empty rather than guessing.
Without it the skills still run and disclose the missing project voice.
`design-review` reports gate `X1` as unchecked, proceeds with explicit assumptions, and uses the supplied brief and accepted baseline for the broader context review.

`eod` does not read `voice.md`.
A `voice.md` scopes one project's outward copy, and an EOD is neither outward copy nor scoped to one project: one day of the corpus alone covers four.
Its authority is `eod/references/corpus.md`, three of the owner's own EODs, which is his writing rather than a project's.

## Attribution

The catalogs adapt material from several MIT and Apache-2.0 projects.
`ATTRIBUTION.md` records what was taken from each and what was not.
