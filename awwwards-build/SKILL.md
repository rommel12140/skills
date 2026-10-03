---
name: awwwards-build
description: >
  Wireframe a web page, design its sections, and specify and build its interface
  components to an Awwwards Site of the Day standard in one pass. Use when a
  page has to be planned from a brief before it is built: its argument, section
  sequence, section briefs and desktop and narrow wireframes. Also use when the
  deliverable is a component system or component specification (buttons, links,
  fields, selection controls, forms, navigation, tabs, cards, tags, tooltips,
  modals, drawers, tables, skeletons, empty and error states, custom cursors).
  Produces the plan, the build, and pass or fail acceptance evidence. For page
  builds whose structure is settled, visual polish, template adaptation,
  refinement, or audits, use design-review.
---

# awwwards-build

## What this is for

Building a page that would stand next to recent Awwwards Sites of the Day, from a brief, without a second pass to find out what the page was meant to say.

The studied winners have no shared section count, grid, or opening animation.
What they share is that content, sequence, composition, and controls were decided together and each one answers to the subject.
This skill makes an agent take those decisions in order and leave evidence for each.

## This skill or design-review

| Situation | Use |
| --- | --- |
| The deliverable is a wireframe, a section sequence, or a page structure decided from a brief | `awwwards-build` |
| The deliverable is a component system or a component specification | `awwwards-build` |
| A page structure exists but a section or component set has to be redesigned | `awwwards-build`, from the stage that is missing |
| A page build whose structure is settled, visual polish, template adaptation, or a scoped refinement | `design-review` in Build or Refine |
| Existing work needs review | `design-review` in Audit |
| Finishing a build from this skill | Run this skill's acceptance gates, then `design-review` in Audit over the rendered result |

This skill decides structure and component behaviour, and proves they work.
`design-review` owns art direction, typography, motion craft and the catalog of AI-generated design tells, and audits what this skill produces.
When they disagree on a visual tell, type or motion craft, `design-review` is the authority; when they disagree on structure or component behaviour, this skill is.

## Three kinds of evidence

Every rule and example in the references carries one of these labels, and output must keep them apart.

- **Observed:** read from a live page, its rendered structure, an official Awwwards capture, or a published sketch, and dated.
- **Studio account:** what the makers say about their own process.
- **Recommendation:** a synthesis or starting value proposed for this skill.

Never present a recommendation as an Awwwards requirement or as a studio's method.
No Awwwards rule sets a section count, grid, radius, timing, or palette, and output must not imply one.
Starting tokens and motion timings in this skill are recommendations; none were measured on award winners.

## Inputs

1. Read the project's `voice.md` if one exists, in particular its audience, allowed numbers, and visual language sections.
   If it is absent, say so and continue; do not invent a voice or a brand.
2. Collect the brief, the real copy or copy notes, and the real assets.
   Open every image before assigning it to a section.
3. If the brief names no audience, next action, or subject, write the gap down as a dependency and keep going on what is known.
   Ask only when the missing fact would change the page's argument.

## Procedure

Run the stages in order.
Go back when a later stage disproves an earlier decision.
Each stage has an output; the output is the evidence that the stage ran.

1. **Page task.**
   Write the audience, arrival context, purpose, and intended next action in plain language, then the one sentence the page argues.
   Name the page's dominant behaviour: persuade, compare, browse a collection, explain a process, or serve as reference.
   Method: `references/wireframe-method.md`.
2. **Content and evidence inventory.**
   For each fact or claim: its source, the asset that proves it, the visitor concern it answers, and where it leads.
   Mark missing proof as a dependency.
   Never fabricate a number, client, testimonial, certification, or capability to fill a layout.
3. **Sequence.**
   Write each beat as visitor concern, answer, evidence, and the reason it follows the previous beat.
   Stop when the argument and the remaining concerns are answered, not at a target count.
   Sketch at least two structurally different sequences privately, choose one, and present only the chosen one with a line on why the other lost.
4. **Section briefs.**
   Fill the section brief for every beat before choosing a pattern or a component.
   Choose patterns from `references/section-catalog.md` because the content calls for them, never to fill a page.
5. **Whole-page wireframe.**
   Draw the full page at desktop and narrow widths with real copy lengths and real image shapes, the hero together with its successor.
   Apply the composition rules in `references/section-catalog.md`.
6. **Motion as states.**
   For each interactive or transitional section, record entry, active, and exit states, the trigger, what stays readable, scroll ownership, reversal, the escape route, and the reduced-motion still.
   Each motion performs that section's argument and differs from the one above it.
7. **Components.**
   Build from brand evidence, a small visual grammar, an explicit state contract, and a motion contract, then apply the per-component rules.
   Method and rules: `references/component-rules.md`.
8. **Build.**
   Build in semantic reading order with real content.
   Prototype the least certain section boundary together with its neighbours before polishing anything else.
9. **Acceptance.**
   Run every gate in `references/acceptance.md`.
   Gates marked `render: required` are judged from the rendered page via `chrome-devtools-axi`, at 1280 by 800 first and then a narrow touch viewport.
   If the page cannot be rendered, report those gates as unchecked, never as passed.
   Then hand the rendered page to `design-review` in audit mode.

## Standing rules

These override anything a reference site or design system does.

- Buttons stay recognisable as buttons at rest, including low-emphasis variants.
  A bare text action that only becomes a button on hover is a defect.
- Pending content uses a skeleton that matches the layout it predicts: same media ratio, line count, row height, and column widths.
  No full-page spinner, no glossy sweep, no pulsing dots, no fake progress.
- No numbered or pseudo-technical labels: no "01 Studio", "Section 02", "Q-01", or invented codes.
  Use the real names of things.
  The same goes for numbered navigation that only exists to look technical.
- No AI-slop visual language: glowing nodes and connected dots, gradient blobs, floating glass, neon on dark, emoji as icons, rows of three equal icon-topped cards.
- No universal fade-and-rise reveal.
  Each animation performs its own section's argument and differs from its neighbour.
- Visual language comes from the client's world and the page's job.
  Reference-page furniture (index rails, numbered clauses, sticky tables of contents) does not go on a persuasion page.
- Copy in the build follows the project's `voice.md` and `copy-review`; no em or en dashes in authored text.

## Output contract

The handoff, in this order:

1. Page task and the one-sentence argument.
2. Content and evidence inventory, with dependencies marked.
3. Chosen sequence with the reason for each transition, and one line on the rejected structure.
4. Section briefs.
5. Desktop and narrow wireframes, as annotated text diagrams or a rendered low-fidelity page.
6. Motion state notes per interactive section.
7. Component specification: one record per component, using the template in `references/acceptance.md`.
8. The built page or the files changed.
9. Acceptance report: every gate by ID with pass, fail, not applicable with a reason, or unchecked with a reason.

No score.
A count of failed gates closes the report, as a count and not a judgement.

## What this skill does not do

It does not choose typefaces or audit motion craft; `design-review` covers those.
It does not certify accessibility conformance; its accessibility gates are a build bar, not an audit.
It does not promise an award.
Sources, dated observations, and the published numbers behind each rule live in `references/evidence.md`.
