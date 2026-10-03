# Acceptance

Acceptance is pass or fail, gate by gate.
A distinctive look cannot compensate for a failed gate.
Each gate has a stable ID so a second pass can report resolved, still open, or new against the first.

Attach evidence to every gate: a marked wireframe, a section brief, an asset source, a prototype state, a measurement, or a render.
"Not applicable" needs a reason tied to the page or component's job.
A gate marked `render: required` is judged from the rendered page through `chrome-devtools-axi`, at 1280 by 800 and at a narrow touch viewport.
If the page cannot be rendered, report that gate as unchecked; never as passed.
Over a plan or source alone, a render-required gate can fail when the plan states the defect outright ("every section fades in and slides up"), but it cannot pass: report it unchecked with a note on what the source shows.

No score.
Close the report with the count of failed and unchecked gates.

## Page and wireframe gates

Run before visual refinement, again on the built page.

| ID | Gate: fails if | Render |
| --- | --- | --- |
| W1 | The opening does not identify the subject or give the intended audience a reason to continue | required |
| W2 | A section has no distinct job, or its evidence is not identified | no |
| W3 | Reading only the main statements does not give a coherent account of the offer or work | no |
| W4 | A transition cannot be explained without referring to visual novelty | no |
| W5 | A section could be removed without losing a specific answer, proof or useful action | no |
| W6 | The section count came from a target, a template, or habit (services band, stats strip, generic testimonials) rather than the argument | no |
| W7 | A photograph, object, claim, number or caption has no known role, source or usable treatment, or a number is neither confirmed nor listed in `voice.md` | no |
| W8 | The narrow layout loses the argument, or a key piece of information or action is unreachable there | required |
| W9 | Long names, realistic paragraph lengths and awkward crops were not tried | no |
| W10 | The main next action is missing at the decision points, or leads to an unidentified destination | no |
| W11 | The least certain transition was not tested with its neighbouring sections | no |
| W12 | A critical asset, factual claim, or primary navigation behaviour remains undefined | no |
| W13 | Output attributes a recommendation to Awwwards or to a studio, or presents a starting value as a winner's requirement | no |
| W14 | The page has no brand-derived signature storyboard, a section has no motion level, or the 3D/shader decision is missing | no |
| W15 | Removing an unverified dominant visual leaves no equally strong, honestly sourced or original illustrative replacement | required |

## Section and composition gates

| ID | Gate: fails if | Render |
| --- | --- | --- |
| S1 | Layout differences do not follow differences in content relationship; sections alternate at random | required |
| S2 | An equal three-card feature band, or repeated icon-topped claims, was added by habit | required |
| S3 | The hero's promise is not advanced by the next section, or the page rebuilds the opening composition repeatedly | required |
| S4 | The full-page strip has no readable change in density and scale, or has arbitrary empty gaps | required |
| S5 | Captions or claims are detached from their evidence, or a crop removes the relevant detail | required |
| S6 | Supporting text competes equally with the evidence it explains | required |
| S7 | Alignment has no shared anchors, or an asymmetric section has no reason for its edges | required |
| S8 | An interaction-dependent section lacks understandable initial, active and final states | required |
| S9 | Essential content or navigation needs hover, or has no meaningful reduced-motion or still treatment | required |
| S10 | A long pinned or horizontal experience has no clear continuation or direct escape route | required |
| S11 | Two adjacent sections share the same reveal, or any section uses the universal fade-and-rise | required |
| S12 | A section carries a numbered or pseudo-technical label, or reference furniture sits on a persuasion page | required |
| S13 | The visual language comes from a generic kit (glowing nodes, connected dots, gradient blobs, floating glass, neon on dark, emoji icons) instead of the client's world | required |
| S14 | A persuasion page has no expressive opening or first handoff, no later narrative transformation, or only hovers, a progress line and minor reveals; the planned signature does not command its intended composition | required |
| S15 | A signature scene breaks on reverse, fast scroll, direct entry, resize, interruption or route return; reduced motion merely hides it or leaves empty pin distance | required |
| S16 | Motion has no measured frame and asset budget, rendering continues unnecessarily offscreen, or failed media/WebGL leaves content inaccessible | required |

For `W14`, operational and reference pages can use a compact branded state transition or a distinctive still composition when movement would obstruct the task.
For `S14`, record explicit static briefs and reduced-motion versions as exceptions, not as failures.
These gates require ambitious composition and authored behavior, not a mandatory library or arbitrary 3D object.

## Component gates

Per component, and once for the family.

| ID | Gate: fails if | Evidence required |
| --- | --- | --- |
| CM1 | Purpose: the job is ambiguous at rest | Real label, semantic role, expected result, destination or action |
| CM2 | Brand: the only character is a generic effect or an arbitrary decorative label | A short rationale tied to a real brand asset, material, mark or behaviour |
| CM3 | Anatomy: the target is too small, the shape misleads, or geometry clips content | Visible shape and hit area dimensions; padding, radius, border, type size, tracking, icon size |
| CM4 | States: hover substitutes for focus, errors erase input, or a pending state never ends | The exercised state matrix, including real transitions |
| CM5 | Keyboard: focus is missing, wrongly trapped, lost, or behind the wrong layer | Tab and Shift+Tab route, activation, component keys, Escape where applicable |
| CM6 | Touch: the task needs hover or overlapping invisible targets | Small viewport and coarse pointer run; 44 px standalone targets |
| CM7 | Content: copy must be shortened to keep the design | Short and long labels, wrapped help and error text, long values, localised text, missing media |
| CM8 | Async: skeleton geometry jumps, existing work disappears, or operations duplicate | Slow request, success, empty, server failure, offline, repeated activation |
| CM9 | Motion: the target moves away, actions wait for decoration, or every component shares one reveal | Trigger, layer, timing, easing; reversal and reduced-motion recording |
| CM10 | Finish: baselines, optical alignment, icon strokes, corners or focus edges drift at actual size | Review on one touch and one desktop configuration (render required) |
| CM11 | Button recognition: any action, including a low-emphasis one, is not recognisable as a button at rest | Still render of every button variant at rest (render required) |
| CM12 | Loading: pending content uses a spinner, sweep, pulse or a skeleton that does not match the layout | Skeleton beside the loaded component at the same size (render required) |
| CM13 | Family: action hierarchy, geometry, focus grammar, icon weight, state vocabulary or async behaviour differ across components | Specimen surface with the set side by side |
| CM14 | Scope: the component deliverable turns into a generic redesign or an ornamental kit | The component inventory against the real tasks |

## Accessibility gates

WCAG levels are stated as published; the bar here is stricter in places on purpose.

| ID | Concern | Published | Bar for this skill |
| --- | --- | --- | --- |
| A1 | Text contrast | WCAG AA: 4.5:1, or 3:1 for large text | Measure real pairs in rest, hover, focus, error and selected; 4.5:1 for control labels (render required) |
| A2 | Non-text contrast | WCAG AA: 3:1 for visual information needed to identify controls and states | Boundaries, icons and state marks stay distinguishable on every surface (render required) |
| A3 | Targets | WCAG 2.5.8 AA: 24 by 24 with five exceptions; 2.5.5 AAA: 44 by 44 | 44 by 44 for standalone controls; inline text targets documented; expanded hit areas never overlap |
| A4 | Focus | Visible focus required; 2.4.13 AAA: area of a 2 px perimeter and a 3:1 change between states | A conspicuous unclipped indicator on light, dark, image and forced-colours surfaces (render required) |
| A5 | Focus not obscured | WCAG AA: the focused component is not entirely hidden by author content | The focused control and its label stay fully visible under sticky bars and overlays (render required) |
| A6 | Motion | Animation from interactions is AAA | Honour `prefers-reduced-motion`; remove cursor lag, tilt, large travel and decorative loops; keep every state and affordance |
| A7 | Reflow | Content at 320 CSS px wide, with a two-dimensional exception | Test narrow width, 200% text and 400% zoom; real data tables get a deliberate strategy (render required) |
| A8 | Status | Status messages programmatically determinable without moving focus | Announce busy, result and error once, at the right urgency; never every skeleton shape |
| A9 | Semantics | Native HTML first, ARIA for what native elements lack | Names, roles and states correct; canvas text, decorative duplicates, masked labels and cursor layers checked by hand |

An accessibility snapshot shows names and roles; it does not replace a keyboard pass and a screen-reader pass.
An award does not waive any of this.

## Component record

One per accepted component, so the set can grow without drift.

```text
Name and job:
Brand evidence:
Native element or complete interaction pattern:
Anatomy and target dimensions:
Type, spacing, edge, colour and icon tokens:
Variants and applicable states:
Keyboard and touch behaviour:
Loading, empty, failure and recovery behaviour:
Motion trigger, layer, values, timing, easing, interruption:
Reduced-motion and forced-colours behaviour:
Content extremes tested:
Evidence and remaining limitations:
Accepted or rejected, with reason:
```

## Report format

One line per gate:

```text
<ID> · <pass | fail | n/a | unchecked> · <where: section, selector or component>
Evidence: <what was checked, quoted or measured>
Fix:      <for a fail, the change to make>
```

A failed gate always names a fix.
A skipped or unchecked gate always names the reason.
