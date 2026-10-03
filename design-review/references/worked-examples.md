# Worked corrections

These are fictional, generalized examples of recurring failure patterns.
They describe observable changes, not guaranteed approvals or universal styling recipes.
Use the original brief and accepted design system to choose actual values.

## Clean landing page with no point of view

**Before:** A business page has a centered heading in a newly chosen font, three service cards and the same fade-up on every section.
It has no broken links and no overflow, but its only proof is generic stock photography.

**After:** For a workshop selling custom timber stairs, use a close photograph of an actual joint as the hero's dominant evidence.
Set a short claim on the same structural edge as the image; give the enquiry action a recognizable button treatment.
Follow with a completed staircase, a readable process explanation and the specifications a buyer needs.
Use a crop reveal only where it exposes a construction detail, then leave the specification section still.
Keep the palette and type decisions tied to the workshop's existing material.

**Check:** At 1280x800, identify the product, proof and next step without scrolling.
At 390 CSS px, the crop still shows the joint and the complete claim remains readable.
If replacing the workshop name with a software company makes the page equally plausible, the content or concept is still generic.

## Minimal login that became a product brochure

**Before:** A sign-in screen gains a giant headline, a sample dashboard, explanation cards, a technical security paragraph and an animated illustration to fill its empty space.

**After:** Give the actual wordmark a deliberate size and location.
Compose a compact sign-in area with its title, the supported sign-in choices, necessary trust text and truthful status.
Use a brand-specific response only while sign-in is occurring; remove fabricated demonstrations and repeated headings.
On mobile, put the mark and task in one clear reading order.

**Check:** A returning user can identify the correct action immediately.
Error, waiting, signed-out and completed states keep the same structure.
Whitespace frames the task instead of forcing the form to the bottom of a tall panel.

## Report dialog that reads like an unformatted document

**Before:** A 760 px dialog contains a colored top stripe, labels in a narrow side column, seven horizontal rules, repeated section headings, source metadata and a large action row.
The design gets quieter by turning every action into a blue word.

**After:** Try a 640 px content-width dialog with 28 px inset, a 24 px title, 14 px metadata beside or directly beneath it, and a single reading column.
Use 16 px body text with roughly 1.5 line height and deliberate section gaps.
Keep only dividers that separate distinct controls or groups.
Retain compact visible buttons for actions and put secondary provenance in a named disclosure.
If the user asked for a side sheet, move the accepted interior into that shell without restyling it again.

**Check:** Title, period, content and action are visibly distinct at desktop and phone widths.
Focus enters and returns correctly, long text scrolls in one intentional region, and action labels do not collide with rules.
The exact dimensions are a trial composition, not a mandatory modal recipe.

## Better cards without adding another strip

**Before:** The user likes a row of stage cards and its selected color.
A refinement adds progress bars, tiny status labels and a new palette while leaving the count hierarchy almost unchanged.

**After:** Keep the approved number of cards, colors and ordering.
Align titles and metadata, make counts use comparable numeral widths, and group the primary state with its action.
Within the selected card, give the important substate clear dominance through proportion and spacing instead of an arbitrary accent border.
Use the same inset and baseline relationships across the row.

**Check:** The meaningful difference between states is readable at a glance.
The change is visible in the hierarchy, while the accepted structure and information remain intact.
Do not treat existing user-designed cards as permission to run a destructive catalog cleanup.

## Portfolio reveal guessed from a screenshot

**Before:** An image moves upward and fades in over a long pinned section.
The heading arrives near the end, the persistent background object disappears, and the accordion is disabled until the timeline finishes.
The reference actually reveals content over an apparently stationary image.

**After:** Inspect forward, reverse and interrupted scroll in the reference.
Use a crop or mask over the appropriate fixed/sticky layer when that is the observed mechanism.
Bring the section heading into readable presence at entry, preserve the accepted continuous object, and keep accordion controls usable throughout.
Tune the transition interval against content rather than adding a timer.
The next section can be a quiet reading area instead of repeating the same reveal.

**Check:** Compare entry, middle and settled frames, then reverse and jump directly to the section anchor.
Click the accordion during the handoff and repeat its open/close sequence.
On reduced motion, show a complete static section with immediate context and no residual blank pinned area.

## Hospitality styling applied to an operations tool

**Before:** A reservation interface uses a large display serif for operational labels, a deep colored side panel, tilted receipt paper and an italic slogan.
The elements all relate loosely to hospitality, yet the work is harder to scan and the existing product identity disappears.

**After:** Restore the accepted product palette and UI type roles.
Use real reservation times, clear row hierarchy, aligned quantities and a compact detail surface that preserves context.
Retain an industry-derived detail only if it improves understanding, such as an actual order grouping.
Remove simulated stationery that competes with the task.

**Check:** A person can compare reservations and open the corresponding order without interpreting a decorative scene.
Do not generalize this correction into a ban on serifs or green; both may be appropriate on a different page with a different job.

## Template adaptation that passed a content check

**Before:** A service mockup contains no old company names, but loses the template's marquee, several photographs and a key section transition.
One replacement heading wraps to five lines where the template held two; one card is much taller than its siblings.
A logo is soft at display size.

**After:** Restore the authorized template's structural and motion relationships.
Choose subject-correct imagery for each slot and make the real logo sharp and legible on its actual background.
Edit the new heading to fit the intended phrase length without losing its claim, then inspect the actual font and line count.
Preserve all required content and remove unsupported sections only when authorized, including their surrounding visual remnants.

**Check:** Compare template and candidate at identical viewport sizes, scroll positions and states.
Confirm every image remains nonzero on an emulated phone, labels stay aligned, and first/repeated interaction behavior matches the intended template.
A string audit is one part of this check, not the visual verdict.

## Loading that changes the whole page shape

**Before:** An otherwise detailed dashboard becomes a bare loading sentence on refresh.
After the data arrives, cards and rows jump into place.
On failure, the same loading sentence remains indefinitely.

**After:** Keep the page shell and use skeletons matching the title, row density and principal content areas.
Swap content in without changing the key geometry.
Use one loading status, a static reduced-motion skeleton, and an unavailable state with a compact Retry action.
Preserve data that remains usable during a partial failure.

**Check:** Simulate fast, slow, empty, failed and partial responses.
No artificial minimum delay is added, no error is disguised as loading, and the skeleton does not announce each decorative shape to a screen reader.
