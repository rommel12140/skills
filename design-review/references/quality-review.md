# Review the floor and the bar

Use the catalog to catch defaults and the criteria below to judge the actual design.
These are separate questions.
A page can avoid every catalog tell and still have weak imagery, flat hierarchy, a borrowed concept or unfinished behavior.

## Evidence before judgment

Read the brief, `voice.md`, accepted baseline and any specific rejection before reviewing.
Identify the page's job and the stack.
If this is a reported defect, first reproduce it in the user's flow and viewport as closely as possible.
Capture the failing state before changing it.
Source inspection can locate a cause but cannot establish what the user saw.

Record the build or revision, route, viewport, input, state and capture used for each visual claim.
Look at actual images, not only screenshot paths printed by tools.
Use browser geometry and computed styles to explain a visible discrepancy, not as a substitute for seeing it.
A static screenshot can establish composition but cannot prove motion quality or interactivity.
A recording alone cannot prove keyboard navigation or accessible names.

Use render flags in [the catalog](design-tells.md) as the source of truth for which gates need a browser.
Count gates from the catalog rather than relying on a duplicated total in prose.
For positive craft judgments, rendered evidence is necessary even if no catalog gate fired.

## Positive design review

Use descriptive finding labels such as `Type hierarchy` or `Section handoff` when no catalog ID applies.
Do not create a pseudo-precise composite score.

| Quality | Evidence of a strong result | A reason to revise |
| :--- | :--- | :--- |
| Concept | A particular subject, object or process shapes the composition and behavior | The page survives any business-name substitution unchanged |
| Page argument | A clear task, relevant proof and a next step | Sections exist because a template expected them |
| Typography | Distinct roles, expressive but readable display, precise spacing | A new font sits on an otherwise unchanged generic layout |
| Composition | Dominance, balanced density, common edges and purposeful rhythm | Everything has equal weight, or whitespace conceals missing proof |
| Imagery | Real subject, strong crop, consistent treatment, legible overlays | Missing, dirty, unrelated or poorly framed imagery |
| Surfaces | Clear layers and controls, deliberate states and restrained separators | Bare-text actions, excessive rules, arbitrary stripes or oversized panels |
| Motion | It explains a relationship and remains coherent in intermediate states | Repeated reveal effects, delayed context, dead controls or jumpy reversal |
| Responsive design | The idea is recomposed for a phone and varied content | Desktop mechanics shrink, disappear, clip or create a long scroll trap |
| Usability | The main journey is understandable without explanation | Essential information appears only on hover or after an effect completes |
| Delivery | Fast useful rendering, stable layout, complete states and recovery | Font flashes, broken links, console failures or indefinite loaders |

For each weak area, explain the visible cause and a concrete correction.
Name strengths specifically so a refinement preserves them.
Do not call a site award-level solely because it is clean, unusual, animated or technically valid.

## Before showing the candidate

This is the internal presentation gate, not an extra request for user approval.
Fix applicable blockers before sharing the candidate as finished.
When an external limitation prevents a check, mark it unchecked and describe the limited readiness honestly.

### Brief and preservation

- The reader, job, primary action and actual proof are clear.
- The design direction can be explained through concrete choices.
- Approved typography, colors, layout, objects and behavior remain intact wherever scope protects them.
- Real content replaces draft material; numbers and claims have sources.
- Template adaptation retains the authorized structure, density and interaction behavior.
- A previous rejected variation has not survived in an untested route, breakpoint or state.

### Pixels and composition

- Inspect 1280x800 first, then wider desktop and a true 390x844 mobile viewport, with a 320 CSS px stress check and relevant intermediate widths.
- Confirm `innerWidth` and viewport metadata instead of assuming a resized desktop window is a phone.
- Check hero context and primary action, each section, footer, navigation, modal/sheet and embedded preview.
- Inspect image-heading alignment, column boundaries, consistent control baselines and optical gaps.
- Check actual image crops, sharpness and color relationships at display size.
- Check long headings, unusual names, multiline descriptions and realistic CMS content.
- Inspect cold load, settled load and font failure separately.
- Confirm no accidental overflow, zero-sized images, clipped glyphs, orphaned labels or overlapping borders.

### Interaction and motion

- Complete the primary journey with mouse, keyboard and touch where available.
- Check first and repeated hover, interrupted animation, rapid open/close, back/forward and direct anchors.
- Inspect entry, intermediate, settled and reverse frames of significant motion.
- Confirm context appears before the content needs it and controls respond when they look usable.
- Run reduced motion from initial load and after a preference change.
- Confirm touch users do not need hover and ordinary scrolling is not trapped.
- Verify focus appears immediately, moves appropriately, returns from modal surfaces and remains visible.
- Confirm a failed asset or route cannot leave a covering layer or hidden content indefinitely.

### Data and recovery

- Inspect loaded, loading, empty, stale, partial, unavailable, error and retry states where the product supports them.
- Skeletons match the final layout and stop when loading finishes or fails.
- Status wording reflects the actual state, with a useful recovery action when possible.
- Buttons remain visibly actionable, with consistent dimensions in busy states.
- No missing data is converted into a fabricated zero, success or decorative statistic.
- Forms have labels, meaningful validation and a correct success result.

### Accessibility and delivery

- Check text and applicable non-text contrast in the rendered composite.
- Check keyboard order, semantics, accessible names, meaningful alt text and custom control behavior.
- Test 200% text enlargement and reflow at 320 CSS px; retain a legitimate two-dimensional table's appropriate scrolling without making the whole page scroll sideways.
  See [WCAG Reflow](https://www.w3.org/WAI/WCAG22/Understanding/reflow.html).
- Test text-spacing overrides and reduced motion, rather than only checking that media queries exist.
- Check the console, missing requests, broken destinations and browser support relevant to the brief.
- Record network, CPU, cache and device conditions for performance measurements.
- Inspect a trace through the busiest animation and a realistic interaction, not only page load.
- If release is authorized, verify the released revision and key flow after deployment.

## Performance targets with real provenance

Google's good Core Web Vitals thresholds are LCP at most 2.5 seconds, INP at most 200 ms and CLS at most 0.1, assessed at the 75th percentile and segmented by mobile/desktop.
See [Web Vitals](https://web.dev/articles/vitals).
These are field thresholds, not an Awwwards scoring formula.

Use lab measurements to diagnose regressions before release.
Record transfer weight, largest assets, main-thread work and frame behavior under matched conditions.
A Lighthouse navigation run does not measure field INP; its TBT can indicate interactivity risk but is not a substitute.
If there is no field sample or physical phone, say so.
Do not describe desktop emulation as measured real-phone performance.

Set a page-specific asset and rendering budget after measuring the representative slice.
Record initial JS, fonts, hero media, deferred media and the largest interaction cost.
Prefer a useful first render with deferred enhancement to a long custom loading sequence.
If the budget fails, identify the dominant cost and optimize it while preserving the chosen visual effect.
Do not claim that deleting the central design idea is performance polish unless that tradeoff is authorized.

## Prioritize and report

P0 findings block the main task, accessibility or factual trust, or violate a hard visual constraint.
P1 findings visibly weaken clarity, craft or repeated use.
P2 findings are local polish issues.
For accepted existing deviations, record the exception and scope instead of treating the catalog as permission to remove them.

Do not count the same root cause repeatedly under several labels.
A weak common button component may produce several visible examples but needs one systemic fix.
If the failure recurs, update the acceptance check to reproduce it explicitly.

A concise report should give:

- The mode, scope and actual readiness.
- What is working and should be preserved.
- The consequential findings with evidence, severity and stack-appropriate corrections.
- Skipped or unverified checks and accepted exceptions.
- Counts by severity for an audit, without a quality score.

Use a live preview when possible and a brief recording for important motion.
Keep the claim proportional to the evidence: ready for visual review is not the same as approved, deployed or guaranteed to win.
