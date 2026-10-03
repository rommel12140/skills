# Layout, color, imagery and components

Use these decisions to make the page feel composed and complete in use.
The dimensions below are starting points, not award requirements.
Preserve an accepted design system and tune values against real content and rendered pixels.

## Establish a composition

Choose a dominant element in each viewport and give everything else a clear relationship to it.
The dominant element should carry the page's argument: work, product, place, claim or operational state.
Large type and large imagery should not compete accidentally.
A quiet login or table can meet a high design bar through proportion and detail without becoming a promotional scene.

Define a container and meaningful alignment lines.
A 12-column desktop grid and 4-column mobile grid can help, but the content decides the spans.
At wide desktop, try 48 to 80 px side margins and 24 to 40 px gutters; on phones, start with 20 to 24 px side margins and 16 to 24 px gaps.
Do not force those values into a dense application or an existing site that uses a different system.

Use a small spacing scale, such as 4, 8, 12, 16, 24, 32, 48, 64 and 96 px.
A relationship matters more than membership in the scale: related text sits closer together than unrelated groups.
Try 64 to 120 px between major desktop sections and 40 to 72 px on phones, then tune by density and visual continuity.
Long empty scroll is not evidence of refinement.

Align repeated headings, imagery, metadata and actions to common edges.
Measure the actual image boundary, not just its wrapper, including padding inherited from nested containers.
If an image is full bleed, make that deliberate; otherwise align it to the text's column.
Check left and right edges at intermediate widths as well as desktop and phone.
Avoid percentage-minus-gutter widths whose parent can collapse to zero.

At 1280x800, keep the essential hero claim and primary action visible in the intended opening composition.
Treat this as a regression viewport, not a claim that all visitors use that size.
Use content-driven height rather than `100vh` when a fixed height would crop the action.
Test short screens and safe areas before using a full-height scene.

## Design density for the job

On a persuasion page, each section should advance a decision with proof.
Remove reference rails, decorative clause numbers and repetitive explanation that interrupt the argument.
A pricing comparison can use a table when it helps compare actual options; the ban is on irrelevant reference furniture, not on useful data structure.

On an operational screen, group by the questions a person asks: what changed, what needs attention, what can I do next?
Bring an urgent prerequisite to the place it blocks work.
Keep related dates, titles and status near one another.
Use aligned rows for comparable records instead of inventing a large card for each value.
Keep summaries and drill-downs distinct.
A command center should reveal the work, not the application's architecture.

Minimalism removes redundancy and clarifies relationships.
It does not remove the user's ability to recognize a control, hide important state, or leave a page empty.
A sparse page may need stronger proof, a better image or more useful grouping.
A busy page may need fewer labels, better priorities or secondary detail moved into a relevant disclosure.
Diagnose which problem is present before removing or adding content.

## Color as a controlled system

Start with the client's existing colors or a source in the selected visual material.
Define roles for canvas, surface, primary ink, secondary ink, action, border, focus and each meaningful status.
Use tokens and verify every state against its actual background.
Try one dominant surface family and one main action accent before adding more; this is an organizing choice, not a fixed color ratio.
Let imagery carry much of the chromatic richness when appropriate.

Use a colored surface only when it establishes hierarchy, a real brand moment or a meaningful state.
An arbitrary accent strip at the top of a modal does none of those jobs.
A divider earns its place by separating or aligning something.
If spacing already establishes the relationship, remove the redundant rule.
Borders must not cross labels or controls.
Keep elevation for actual layering, such as a dialog above a page, rather than giving every region the same shadow.
Use radii that relate to the brand and component size; avoid assigning every surface the same large rounding.

WCAG AA text contrast is at least 4.5:1 for ordinary text and 3:1 for large text, defined as at least 18 pt or 14 pt bold.
Do not round a failing ratio up.
For applicable control boundaries, states and meaningful graphics, use at least 3:1 against adjacent colors.
These are accessibility floors, not evidence of visual quality.
See [Contrast Minimum](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html) and [Non-text Contrast](https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html).

Measure over the rendered composite, including alpha, scrims, overlays, gradients, photography and changing video frames.
Do not rely on a color token's standalone ratio.
Use a controlled text area, local scrim, different crop or separate solid surface when text cannot remain readable over media.
Pair status color with meaningful wording or shape.

## Art-direct real imagery

Choose an asset by what it proves before judging how well it fills the rectangle.
Prefer the actual product, people, process, place or completed work when permission and quality allow.
A dramatic photo of the wrong subject is still wrong.
Do not put stranger portraits under service labels or use a random wall to stand for a construction portfolio.
Do not generate a replacement logo when the real mark is available.

For each image slot, decide subject, role, ratio, focal point, crop, text-safe region and fallback.
Inspect desktop and mobile crops independently.
Use responsive sources, explicit dimensions or aspect ratio, and appropriate compression.
Do not lazy-load the probable LCP hero image; defer lower-priority media.
Use video only when movement reveals something a still cannot, with a poster that works before playback and if autoplay fails.
Keep decorative media out of the accessibility tree and write useful alt text for informative imagery.

Inspect logos at their actual displayed size, including any descriptor below the main mark.
Use a vector or adequate raster resolution, natural proportions, deliberate clear space and a background where it reads.
A large raster logo scaled down in CSS can still look soft; a source with excessive transparent padding can misalign the apparent mark.
Do not redraw an identity without authorization.

## Buttons and controls

A crafted control has a consistent silhouette, optical alignment, understandable label and complete states.
Use the project's solid, outline or other recognizable button treatment for actions.
Use links for navigation where appropriate; an anchor serving as a primary CTA can still look like a button.
A request for smaller or cleaner buttons means refining size and hierarchy, not deleting their affordance.

Useful starting dimensions are 40 to 48 px control height with 14 to 20 px horizontal padding.
Dense desktop tools can use smaller visible controls with adequate hit area and spacing.
Start touch hit areas around 44 by 44 CSS px where practical.
WCAG 2.2 AA's target-size minimum is 24 by 24 CSS px or a qualifying spacing/other exception; 44 px is a comfort target here, not the AA threshold.
See [Target Size Minimum](https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum.html).

Keep label size, icon weight, icon gap, radius and baseline consistent across a control family.
Use icons that express a real action; do not add an icon chip to every button or heading.
Check default, hover, focus-visible, active, selected, disabled, busy, success and error where applicable.
Keep border widths stable across states.
Loading should preserve the button's dimensions and communicate progress without inventing percentages.
Focus must be visible immediately and must not be hidden by a sticky layer.
Test labels with actual content rather than forcing `nowrap` onto text that cannot fit.

Use native control semantics when possible:

| Need | Control behavior |
| :--- | :--- |
| Choose independent items | Checkbox with visible label and checked state |
| Choose one option | Radio group or a faithfully implemented equivalent |
| Turn a setting on/off immediately | Switch with a clear current state |
| Move between related views | Tabs with keyboard behavior and selected state |
| Show more detail | Disclosure or side sheet with a clear trigger and return path |

Do not change semantics just to make the control look less common.
A styled checkbox can retain its native input, label activation and keyboard behavior.
An underlined word alone is rarely an adequate selected-state system for a dense custom control.

## Dialogs, sheets and forms

Use a dialog for a focused task or decision that needs a bounded context.
Use a side sheet for contextual reading when the underlying list remains useful.
A mobile sheet may become a full-screen view with an obvious back or close control.
Do not nest accidental scrollbars or require the user to hunt below a long body for essential actions.

Start a reading dialog around 560 to 720 px wide, or a contextual desktop sheet around 400 to 640 px, then size to the content and viewport.
Use a clear title, quiet adjacent metadata, one reading column and restrained section hierarchy.
Keep padding consistent, commonly 24 to 32 px on desktop and 16 to 24 px on phones.
Do not stretch a short dialog to fill the screen or frame every paragraph with a divider.
Separate the primary action from supporting source links.
Use concise error text at the relevant field or action, with a recovery path.

Manage focus on open and close, support Escape where appropriate, and contain focus only for modal surfaces.
Keep underlying content inert for a modal, but never for an ordinary scroll reveal.
Use correct labeling and a visible close control.
Follow the [WAI dialog pattern](https://www.w3.org/WAI/ARIA/apg/patterns/dialog-modal/) and the relevant [tabs](https://www.w3.org/WAI/ARIA/apg/patterns/tabs/) or [checkbox](https://www.w3.org/WAI/ARIA/apg/patterns/checkbox/) pattern when building custom behavior.

## Loading, empty and failure states

Content loading uses skeletons matching the final layout's title, rows, image ratio and controls.
Match density and key dimensions, not every letter.
Keep the real page shell stable so the content can replace the skeleton without a jump.
Mark decorative skeleton shapes hidden from assistive technology and use a single understandable status for the region.
Set and clear `aria-busy` on the content region correctly; keep any live status positioned so announcements are not suppressed by that busy state.

Use restrained motion, if any, and stop shimmer for reduced motion.
A branded session-check animation can be appropriate before a content layout is known, but keep one truthful status and never prolong a completed load for theater.
Fast responses should not incur a minimum loader duration.
Do not show repeated "opening" and "checking" messages for the same state.

Empty, loading, stale and unavailable are distinct.
Do not replace an error with an endless skeleton or a fake zero.
Show what is unavailable, preserve usable content, and place Retry or the relevant recovery action nearby.
Keep error styling as deliberate as the loaded design without turning it into a large alarm panel.
For empty content, explain the next useful action only when there is one.
