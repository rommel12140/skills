---
name: design-review
description: >
  Design, build, refine, or audit websites and interfaces against an Awwwards
  standard of art direction, typography, motion, usability, performance and
  execution.
  Use for new pages, visual polish, template adaptation, components, phone
  layouts, loading states, colour and design reviews.
  Treats idle CPU, dropped frames on a throttled phone and fit at every width
  as design gates.
  Preserves accepted work, measures before and after, and checks the rendered
  page alongside source.
  Also audits visual artifacts where applicable.
  Reports evidence and fixes,
  never a synthetic quality score or a promise of winning an award.
---

# design-review

Make the first presented candidate feel designed for its subject, complete in use and cheap to run.
The [design-tells catalog](references/design-tells.md) is the floor.
Passing it does not establish excellent design.
A distinctive concept, deliberate typography, strong content, composed layouts, well-executed behavior and a page that stays quiet while the visitor reads establish the higher bar.

One pass means the agent does its own investigation, construction, measurement and revision before asking the user to review.
It does not mean showing an untested first render or promising a jury outcome.
The owner reviews the real page in a real browser, often on a slower machine or a phone, and judges from what they see first.
Anything they would notice in the first ten seconds, the agent must have seen and fixed before presenting.

## Choose the scope

State **Build**, **Refine**, or **Audit** in the first progress update.
The former **Constraint** mode maps to Build or Refine.

- **Build:** create a direction and implement the requested page or interface.
- **Refine:** improve a named part of existing work, preserving accepted content, behavior and design decisions.
- **Audit:** inspect and report findings; do not implement changes unless requested.

For a dedicated component system or wireframing deliverable, use the sibling Awwwards build skill instead.
A template adaptation is Refine: preserve its composition and interaction structure unless the brief authorizes changes.
For a deck or other static artifact, apply the composition, type, imagery and content checks; mark web-only behavior checks inapplicable.
A request for review alone is not permission to rebuild, deploy or publish.

## Read the right references

In every mode, load the [design-tells catalog](references/design-tells.md).
For Build, read [the build playbook](references/build-playbook.md), [typography](references/typography.md), and [layout and surfaces](references/layout-and-surfaces.md).
For every web Build, read [motion](references/motion.md), including its signature and minimum-motion requirements.
Read it in Refine or Audit when judging or changing animation or transitions.
Use [motion recipes](references/motion-recipes.md) for GSAP, Lenis, kinetic type, hover and route implementation, and [WebGL craft](references/webgl.md) for Three.js, React Three Fiber, shaders and rendering budgets.
Read [motion research](references/motion-research.md) when choosing a mechanism from award winners or explaining its provenance.
For Refine, load the relevant craft reference and the preservation rules in the playbook.
For Audit, read [the quality review](references/quality-review.md) and the catalog, then load the craft reference for each weak area.
Read [award research](references/award-research.md) when selecting a direction or explaining the bar.
Use [worked examples](references/worked-examples.md) to distinguish a substantive correction from a cosmetic one.
Every mode ends with the applicable [self-check](references/quality-review.md#before-showing-the-candidate) and the gates in this file.
Use [stack-specific fixes](references/fixes-by-stack.md) for catalog findings.

## Non-negotiable constraints

- Read the project's `voice.md`, visual-language rules and established components before choosing a style.
  User instructions and accepted design decisions take precedence over this skill's defaults.
  If `voice.md` is absent, say so, proceed with explicit assumptions, and mark `X1` unchecked.
  Do not invent a brand history, approved palette or permitted statistic.
- Derive the visual language from the client's real material and the page's job.
  Identify a specific form, object, process, image treatment or typographic behavior that earns its place.
  An industry association alone does not justify an ornament.
- Keep the existing bans: decorative glowing networks, halos, pulsing dots, generic gradient meshes, floating glass, neon-on-dark atmosphere, equal icon-topped feature triplets, emoji iconography, and universal fade-up reveals.
  Pair every removed default with a stronger subject-derived composition or behavior using [the replacement table](references/motion.md#stronger-alternatives-to-the-banned-defaults).
- Do not add decorative numbered labels or invented pseudo-technical codes.
  Genuine data, ordered steps and useful reference navigation retain their meaning; never manufacture numbering to make a persuasion page look designed.
- Keep buttons recognizable as buttons, and keep non-buttons from looking like buttons.
  Improve their proportions, hierarchy and states without turning actions into bare text.
  A status such as a stamp or a tag must not read as a control.
  Use layout-matched skeletons for content loading and preserve meaningful failure and recovery states.
- Match layout to the job.
  Persuasion needs an argument and proof; reference needs retrieval; an application needs visible state and an obvious next action.
- The work must prove something.
  A project section whose images are illustrative, whose cards link nowhere and whose only action is a technology list proves nothing, however well framed.
  Show the product's real screens whole, name an outcome, and link to the work.
- Nothing unfinished or backstage ships in public.
  No placeholder portrait, no internal note about a font licence, no developer control a visitor can open.
- The page has an ending.
  A persuasion page closes with a contact or next step, not with its last content section.
- Preserve what the user already likes.
  The catalog constrains additions; it does not authorize deleting deliberate existing elements or replacing an accepted design system.
  Record a justified exception instead of silently redesigning.
- Write concrete copy without long dash punctuation, inflated claims or generic promotional phrases.
  Do not add technical implementation commentary to the product unless it changes a user's decision.

## Performance is a design constraint

A page that looks finished and burns a processor core while the visitor reads is not finished.
This gate is the one most often skipped, and the one that most often sends shipped work back.

- An idle page does no rendering work.
  Over five seconds without input, a WebGL or canvas scene submits zero draws, measures nothing, and the page runs no animation ticker.
  Render on demand: request a frame only when scroll, pointer, entrance, visibility or size changes, and let the requests stop once the input settles.
  A decorative time-based sway or ambient loop rests at a fixed pose whenever nothing else moves.
  Never keep a permanent ticker or `requestAnimationFrame` listener registered; join the loop for the motion and leave when it finishes.
  A hidden tab cancels pending frames and listeners, and recovers when shown.
  The check is a five-second idle sample with the draw count and script time recorded, before and after.
- Anything that moves animates only `transform` and `opacity`.
  No `filter`, `mask`, `clip-path`, blur, `backdrop-filter`, live SVG filter or changing shadow on a moving element or its ancestors.
  Paint grain, noise, a stamp or a torn edge once as a still image or a plain strip, then move it.
  Shadows on moving layers are plain `box-shadow` on a static shape, never a blurred filter recomputed each frame.
  A shadow for a whole stack is one soft shadow on the ground, not one per item.
- Motion runs at the display rate.
  A sequence stepped at twenty updates a second reads as lag even when no frame is dropped, unless the steps are themselves the design and are presented as such.
- Budget the first screen for a slow device.
  Defer each section's setup until it is near, keep hero script work small and batched, and adapt rendering resolution to measured GPU time.
  A phone fetches its own lighter poster and model.
  Reduce mesh and texture cost before adding realism, and bake detail into existing maps rather than adding per-frame shader work.
- Measure on a throttled profile, not only on the development machine.
  The acceptance check is the interaction that moves the most, run in phone emulation with a four times slower CPU, and the count of frames over 25 ms during it.
  Report that count before and after and keep the trace.
- Weight has its own line in the report.
  Record bytes for models, textures, posters and fonts before and after, and keep download size separate from decoded GPU memory.

## Fit at every width, and after a resize

- No element passes either screen edge at 320, 390, 768, 1024, 1280, 1440 and 2560 wide.
- Check again after resizing the window from wide to narrow and back, without reloading.
  A heading fitted by script to a pinned box keeps the old width after a resize and grows past the edge.
  Size display type in CSS from its column width and the viewport height, with `clamp()`, container units or viewport units, never by a script that measures once.
- Pinned and scroll-linked boxes recompute their geometry on resize, and the check includes a reverse scroll through them.
- Floating controls such as a contact tab or theme switch reserve their space.
  No content runs under them at any width where they show.
- Overlapped or stacked elements never show partial words.
  Every text run on an element behind another is wholly visible or wholly covered, at every width.
  Measure the overlap as a share of the container's width so the stack reads the same on a narrow phone and a wide desktop, and narrow the visible strips before the words when the container is short.
  Verify with a hit test that samples every text run along its middle line, not by looking at one width.
- Product screenshots are shown whole.
  A cropped screen reads as a broken fragment, not as a detail.

## The phone is its own composition

- Desktop being right is the start, not proof.
  Compose the phone page so a visitor who only ever sees the phone would call it finished.
- Stack labels under their names when a row cannot hold both.
- Indicators, loaders, stamps and small type are larger on the phone, not scaled down with the layout.
- Capture at a true phone viewport with touch emulation and a device pixel ratio of 3, not a narrowed desktop window.
- Use native scrolling on coarse pointers, and recompose a scroll-driven stage into normal flow when its extra scroll height makes no sense on a phone.
- Check the phone in both themes, with reduced motion, and on the throttled profile above.

## Colour from the site's own world

- From the second section down, a page that is one ink on one flat ground is unfinished, however clean.
  Give each chapter or section a ground and an accent drawn from its own material: the product's screens, the photographs already on the page, the hero's object.
- Never import a colour family the site does not already own.
  If the site is greens, cream and gold, a purple, blue or orange chapter is wrong even when it is pleasant on its own, and the owner will send it back.
  Extend the existing family by tone and value before adding a hue.
- Carry each colour through.
  The section's name takes its accent wherever it links to that section, the header takes each section's ground as it passes, and every ground has a light counterpart in the light theme.
- Measure every text element against its rendered background in both themes at desktop and phone widths, and report the lowest ratio.
  A card the same value as its ground is invisible, whatever its border says.
- Colour is paint, not script.
  No scroll-linked colour animation; a palette change should add no script work and a few hundred bytes of CSS.

## No generic loaders, progress bars or decorative slop

- A plain progress line, a spinner, a percentage counter or a stock skeleton is a template's loading state, and it reads as generated.
  Draw the loading indicator from the site's own mark with an asset already on the page: one path, one fill, no new image, font, library or request.
- Progress never reverses and never invents completion.
  Stalled loading shows stalled progress, a failed asset lets the page become usable within a fixed deadline, and a returning visitor skips the indicator.
- The loader hands into the hero's own entrance instead of cutting to it.
- A large heading over a plain ruled list is the same class of failure as a stock loader.
  Compose the section: a lockup, an index, a transition that uncovers its sentence, something the subject supplies.
- Written sentence-case support text beats a monospace label layer.

## Motion performs the section's argument

- Each narrative animation performs its section's argument and differs from the preceding animated section.
  A ticket prints out of its rail at a printer's even speed; a product walkthrough is one camera move through the product; a title travels to its place and uncovers the sentence it introduces.
  Keep a consistent motion character and repeated control behavior, with two named eases reused across the page.
- Plan a signature moment and a motion level for every section.
  Still sections create reading intervals around the signature; they do not excuse a flat persuasion page.
  A progress line and small hover effects alone do not meet this bar.
- Every moving thing has a reverse.
  Scrolling back plays the sequence back cleanly, with no muddy intermediate frame, ghost text or long empty pinned stretch.
- Reduced motion and the site's own motion switch place every element directly, with no delays.
- A pointer may add a shortcut; the keyboard and screen-reader route stays the visible controls.
- Keep operational and reference pages focused on their tasks, and honor explicit static briefs.

## Measure before and after

Every refinement ships with the same measurements taken on the build before the change and the build after it.

- Matched captures at 1440 by 900, 1280 by 800 and 390 by 844, in both themes, with the same scroll position, light and frozen animation time.
- When the change is meant to be local, a pixel comparison proving the difference stays inside the changed element's bounds, with the rest moving by at most a few channel levels.
- Frame sequences of each changed animation, captured by pausing the page's own timeline at fixed times, so the real timing shows.
- The idle draw count, the throttled-phone frame count and the byte budget from the performance gate.
- Three alternating cold loads per build on a laptop and a phone profile, with medians for first paint, largest paint and blocking time, and the run-to-run spread stated.
  A change inside the spread is not an improvement and is not a regression; say so.
- What was not measured: real devices, the live deployment, or a number from the owner's machine that a local profile cannot reproduce.

## Show the real page before landing

- Present a running preview of the candidate and, beside it, the current site at the same path, so the owner compares both in the same browser.
- Put the before and after captures in a review folder with a short README in plain sentences: what changed, what did not, what was measured, what was not checked.
- Reproduce the owner's screenshot in your own capture before claiming a defect is fixed, and before claiming a reported defect does not exist.
  Do not remove an element on the strength of a screenshot you could not reproduce.
- Never restate the owner's machine-level number as your own.
  A local profile can show the page's unnecessary work; it cannot attribute a process total from another operating system.
- When the owner sends a reference, open it and read its mechanism in a browser instead of guessing from a still.

## Build or refine

1. Establish the reader, task, primary action, proof, assets, constraints and protected baseline.
   Read before asking for missing information; proceed on reversible choices with stated assumptions.
   Replace removed unverified visual material with equally strong verified imagery or an original illustrative treatment, without presenting generated material as factual proof.
2. Write a short direction in working notes: page argument, visual source, type roles, colour roles, composition and signature moment.
   Specify one brand-derived signature moment, motion levels per section, the 3D or shader decision, the render-on-demand plan, and the phone and reduced-motion versions.
   For persuasion pages, require an expressive opening or first handoff, a later narrative transformation, a closing section and consistent control feedback.
3. Inspect relevant reference behavior in a browser.
   Describe the mechanism and why it fits before borrowing it.
   Reference images and source inspection do not prove timing, usability or smoothness.
4. Build a representative slice with real copy, intended fonts, the actual visual material where relevant and working controls.
   Prototype the signature motion and its transition to the next section in that slice, with asset, idle and frame budgets.
   Check the hero, a content section and their handoff at 1280 by 800 and on a true phone viewport, then after a resize, before repeating the system across the page.
5. Finish all requested sections, routes and states.
   Keep semantic content useful from the first render, then refine layout and motion together from the moving prototype.
   Do not hide missing content behind animation or loaders.
6. Run the gates in this file and the self-check, correct faults, and rerun the affected checks.
   Repeated corrections become explicit regression checks against the actual rejected state.
7. Present the candidate with its preview, the before and after evidence, the concrete design decisions and any unchecked evidence.
   Follow existing authority for commit, release and publication; this skill adds no approval round.

## Review both the floor and the bar

First walk the catalog's P0, P1 and P2 gates.
Then walk the gates in this file: performance, fit, phone, colour, loaders and motion.
Then assess the positive qualities in `quality-review.md`: concept and subject fit, content, type, composition, surfaces, motion, responsiveness, accessibility and delivery.
An empty findings list is not a claim of excellence.
Name what is strong and identify the most consequential remaining weakness, with a visible reason.

Use `chrome-devtools-axi` when available, or the environment's authorized browser tool.
Capture 1280 by 800 before wider desktop views, plus a true phone viewport, plus the 320 stress width, plus a capture after a wide-to-narrow resize.
Inspect the pixels, keyboard path and actual state changes.
For moving work, inspect the sequence, interruptions and reverse travel as well as settled frames.
Record a five-second idle sample and a throttled-phone trace of the heaviest interaction.
Do not declare rendered checks passed from source, DOM geometry alone, a tool's success message or a test count.
If rendering is unavailable, complete useful source review and explicitly mark visual, motion and performance judgments unchecked.

## Regressions the catalog did not catch

These failures reached shipped pages that passed the catalog, and each went back for correction.
Treat each as a gate; the fix beside it is the one that held.

| Failure seen on a shipped page | Gate | Fix that held |
| :--- | :--- | :--- |
| A display heading grew past the screen edge after the window was narrowed | Fit after resize | Size the heading in CSS from column width and viewport height; remove the measuring script |
| A section was a huge heading over a plain ruled list | Composed section | A two-word lockup over a chapter index, with the second word travelling to uncover the sentence |
| A plain progress line under the hero read as generated | Loader from the site's mark | The hero's own silhouette filling from base to tip as assets arrive |
| Every section after the hero was one ink on one flat ground | Colour from the site's world | Each chapter in its own product's colours, kept inside the site's existing family after purple, blue and orange were rejected |
| A 3D hero object drew 300 frames in 5 idle seconds and held a core | Idle page draws nothing | Render on demand, rest the sway, leave the ticker when motion ends |
| Picking an item in a stack of cards dropped 98 of 150 frames on a throttled phone | Transform and opacity only | Plain paint drawn once, box shadows instead of filters, a still image instead of a live noise filter |
| A stack of cards showed clipped word fragments on the cards behind | No partial words | Overlap measured as a share of the rail's width so each card behind shows exactly its number |
| The phone page was the desktop page squeezed | Phone as its own composition | Labels stacked under names, larger indicators, a lighter phone poster, native scrolling |
| Product screens were cropped inside identical frames | Screens shown whole | Full-height screens named in visual order, one camera move between steps |
| The page ended at its last content section | A page has an ending | A closing contact band |
| A placeholder portrait and an internal font note were public | Nothing backstage ships | Remove or finish before release |

## Output contract

Keep the user-facing report short; retain detailed checks in task notes when needed.
For each finding, use a catalog ID or a descriptive craft label, severity, location, evidence and a stack-appropriate fix.
Stable IDs are review bookkeeping, never labels to add to the interface.

```text
K5 | P1 | .report-action, phone viewport
Found: The action looks like adjacent metadata and has no visible button boundary.
Why: The next step is difficult to recognize.
Fix: Apply the established compact button treatment and verify focus and pressed states.
```

```text
PERF | P0 | hero canvas, idle
Found: 300 draws and 300 layout reads in a five-second idle sample; the ticker never sleeps.
Why: The page holds a processor core while the visitor reads, and a slower machine shows it as heat and lag.
Fix: Request frames only on scroll, pointer, entrance, visibility and size changes; rest the sway; leave the ticker after the motion ends; rerun the idle sample.
```

Every finding must be locatable and name a correction.
Keep observed facts separate from a proposed direction and from unverified assumptions.
Label each as observed, with the evidence named, or as judgment.
Record accepted exceptions and skipped checks with reasons.
Close an audit with finding counts by severity and a plain readiness statement: ready for visual review, needs revision, or insufficient evidence.
Do not assign a quality score or estimate award odds; see [why no score](references/why-no-score.md).
On re-audit, mark earlier findings resolved, still open or newly introduced.
Preserve the accepted baseline and verify that a correction did not reintroduce an earlier rejection.
