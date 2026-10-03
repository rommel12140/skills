# Motion with an argument

Excellent motion clarifies a change, expresses the subject or carries the reader between related ideas.
It has a designed beginning, middle, interruption and end.
Smoothness alone does not make a useful animation, and a moving page is not necessarily a better page.

## Specify the behavior before the library

For every significant motion, record:

| Field | What to decide |
| :--- | :--- |
| Purpose | What the reader understands because this moves |
| Trigger | Hover, focus, activation, data change, scroll progress or route change |
| Subject | Which element moves, which stays fixed, and which owns the coordinate system |
| Path | Translation, crop, scale, rotation, replacement, material or type change |
| Timing | Duration or scroll interval, easing, overlap and settling |
| Interruption | Reverse, rapid repeat, resize, route exit and direct-anchor entry |
| Interaction | When controls become usable and where focus goes |
| Fallback | Reduced motion, touch, unsupported features, slow asset and failed asset |
| Cost | Main-thread, paint, GPU, transfer and cleanup requirements |

If the purpose is only to make the page feel modern, remove the motion and improve composition first.
Use one coherent motion character, such as precise and responsive or measured and continuous.
Vary the action performed by adjacent narrative sections without assigning every component a different easing curve.
Repeated buttons and accordions should behave consistently.

## Inspect a reference as a sequence

Observe the actual reference in a browser, including slow forward scrolling, fast scrolling, reversing and entering from a link.
Capture or record start, intermediate and settled frames.
Identify whether the effect comes from a moving image, a moving crop over a fixed image, sticky positioning, a camera, a mask, or section overlap.
Look at the heading and navigation as closely as the image.
A full-page screenshot cannot tell these mechanisms apart.
Do not claim an exact duration, library or easing from appearance alone.
Label it as measured, source-reported or inferred.

Borrow the principle that serves the new page, not an unrelated site's full animation vocabulary.
An existing custom interaction is evidence of a deliberate choice; inspect its source and states before replacing it.
In Webflow, check CSS, native interactions, Lottie and custom scripts for competing ownership of the same property.

## Practical timing and easing

These are starting ranges for prototyping, not official award criteria or measurements of the cited winners.
Tune against travel distance, size, input method and task urgency.

| Behavior | Starting range | Test |
| :--- | :--- | :--- |
| Press and small state feedback | 80 to 160 ms | Immediate acknowledgment, no delay before the operation |
| Button or icon hover | 120 to 220 ms | Settles quickly; repeated entry does not queue |
| Accordion or compact disclosure | 180 to 320 ms | Feels attached to its trigger; readable while opening |
| Menu or side sheet | 240 to 420 ms | Origin and destination remain understandable |
| Route continuity transition | 300 to 600 ms | Does not hold the user hostage to a complete sequence |
| Expressive reveal | 500 to 900 ms | Earns the time; ordinary content remains accessible |

Useful prototype curves:

- `cubic-bezier(0.2, 0.8, 0.2, 1)` for a responsive entrance that settles.
- `cubic-bezier(0.4, 0, 0.2, 1)` for a balanced movement between states.
- Linear progress when the visual should track a measured quantity or scroll position directly.

Choose a curve by the intended movement, not its name.
Large overshoots imply elasticity; do not apply them to a precise reporting interface without a reason.
Avoid slow ease tails that make a control appear unresponsive.
Keep keyboard focus indication immediate.
Staggers of roughly 30 to 70 ms can explain a short sequence, but cap the total sequence so the last item does not wait behind a long list.
Never stagger an entire page's reading text by default.

## Scroll should remain the user's control

Use native scrolling as the baseline.
Tie meaningful transformations to progress rather than elapsed time when the reader controls the scene.
A conceptual mapping is `p = clamp((scroll - start) / distance, 0, 1)`.
Derive start and distance from real layout, refresh after relevant resize or font changes, and avoid scattered magic offsets.

For a project handoff, an example sequence is:

- At entry, the next section's heading already gives context.
- Through the middle, the preview expands within a crop while an existing background object stays continuous.
- Before the main content becomes dominant, its title and controls are usable.
- At the settled view, no instructional text or object is hidden behind a completed timeline.

On reverse scroll, that same state relationship unwinds without a jump.
Direct section links land on a usable composition without needing the earlier animation to have run.
The scrollbar, touch scrolling, keyboard scrolling and browser history must still work.
Avoid compulsory pauses, blank scroll distances and input locks.
Do not attach `pointer-events: none` or `inert` to useful controls merely because a decorative reveal is unfinished.

Sticky scenes need an intentional height and a clear release.
Mobile often needs a shorter progress interval, simpler crop or static composition, not the desktop scene compressed into a tall tunnel.
Test short phone heights, dynamic browser chrome and orientation changes.
If a smooth-scroll library is used, verify anchors, focus scrolling, nested scroll areas, reduced motion and router restoration before keeping it.

## Give sections different jobs

| Section argument | Motion that can perform it | Adjacent contrast |
| :--- | :--- | :--- |
| Show material or workmanship | Change a crop to reveal a meaningful detail | Follow with a still, readable explanation |
| Explain a before/after | A controlled comparison using matched imagery | Keep the evidence labels stationary |
| Show a process | Reveal the real dependency or transformation | Follow with a compact static result |
| Move from work index to case study | Preserve the selected image's identity across the transition | Let the detail page settle into reading |
| Display a changed state | Update the affected row or control locally | Keep unrelated data stationary |

Do not replace the banned universal fade-up with a different universal effect.
Do not add decorative cursor trails, magnetic targets, glowing nodes or arbitrary 3D just to increase activity.
Useful movement can be small; an inactive section can be entirely still.

## Controls and route transitions

Use one owner for each animated property.
Cancel or reverse the current transition on a new input rather than piling up timelines.
Test first hover, second hover, focus, activation, pointer leaving midway and rapid open/close.
A button's label, accessible name, hit area and focus target must survive the visual effect.
No hover effect should be the sole clue that a control exists.

For route transitions, preserve the relationship between the selected item and the incoming content where useful.
Update the URL, document title, focus and scroll restoration correctly.
Provide a working navigation path when the animation API is unavailable or the next route fails.
Do not leave a transition overlay intercepting input after an error.
The [View Transition API](https://developer.mozilla.org/en-US/docs/Web/API/View_Transition_API) can coordinate old and new views; it does not supply application routing or accessibility behavior for you.

## Performance is part of the movement

Prefer transform and opacity for suitable effects, while recognizing that large layers, masks, blur and texture work can still be expensive.
Avoid layout reads followed by writes inside repeated animation callbacks.
Batch measurements, update efficiently, and do not drive every animation frame through application component state.
Use `will-change` sparingly and remove unnecessary promoted layers.
Pause off-screen and background-tab animation; disconnect observers, timelines and listeners on teardown.

For WebGL or canvas, cap rendering resolution when necessary, optimize textures and geometry, defer noncritical assets and provide a useful static fallback.
Keep navigation and reading content in semantic HTML.
A GPU effect that runs well on the development machine is not proof of mobile smoothness.

At 60 Hz, the whole frame has about 16.7 ms; at 120 Hz, about 8.3 ms.
Application work must leave room for rendering and browser overhead.
Inspect a performance trace through the busiest transition, record dropped frames or long tasks, and test representative hardware when available.
Compare baseline and candidate under the same cache, network and CPU conditions.
A Lighthouse load score does not measure the entire scrolling experience.
See [browser rendering performance guidance](https://web.dev/articles/rendering-performance).

## Reduced motion and failure paths

Treat reduced motion as an authored version of the same experience.
Remove parallax, camera travel, large zooms, continuous drift and unnecessary spatial transitions.
Keep content, order, selected states and controls immediately available.
A static hero image should carry the same subject as the animated one.
A disclosure can change state immediately without losing its expanded content or focus behavior.

Implement `prefers-reduced-motion` in CSS and in any JavaScript animation owner, including preference changes during a session.
Do not merely shorten every duration while leaving long pinned scroll areas and hidden initial states.
Do not disable motion globally in a way that breaks completion callbacks or leaves overlays mounted.
Test the reduced version as a separate user journey.
[WCAG Animation from Interactions](https://www.w3.org/WAI/WCAG22/Understanding/animation-from-interactions.html) is a Level AAA criterion; this skill adopts reduced-motion support as a design requirement without calling it an AA rule.

Provide pause, stop or hide controls for qualifying automatically moving content that lasts more than five seconds and runs alongside other content, unless essential.
Avoid flashing and never require motion or a hover gesture to discover essential information.
See [Pause, Stop, Hide](https://www.w3.org/WAI/WCAG22/Understanding/pause-stop-hide.html).

## Motion acceptance

The section's argument remains clear without its effect.
The moving version adds a specific relationship, emphasis or piece of information.
The sequence works forward, backward, on repeat and when interrupted.
Context appears early enough, and controls respond whenever they appear usable.
Cold load, direct navigation, reduced motion and missing assets all yield a usable result.
Only claim smoothness on the devices and conditions actually inspected.
