# Component method and rules

Everything here is a **recommendation** unless marked Published (a design system or W3C states it) or Observed (read from a live winner and dated in `evidence.md`).
Sizes are starting values for a new brand, not Awwwards requirements.
Every component also has to pass the gates in `acceptance.md`.

The lesson from the award sample is a coherent relationship between a control and its subject: a racing control, a piece of correspondence, a sheet of architectural paper, a media object.
A distinctive hover alone is not that.

## The method

### Brand evidence and component jobs

Collect the logo geometry, product or packaging marks, icon vocabulary, approved type usage, voice guidance, and examples of the client's real tools or materials.
For every proposed detail, record its source and the component job it supports.
Use an industry mark only when it is relevant to the task and consistent with the rest of the identity.
With no brand evidence, state a provisional direction and use restrained, legible controls until the identity exists.
Do not invent decorative lore to justify a generic kit.

Make a component inventory from real tasks and content.
For each item record the semantic role, expected action, variants, input methods, applicable states, content extremes and any async operation.
Separate a destination link, an action button, a single choice, a multiple choice and a binary setting before styling any of them.

Observed examples of identity carried by a familiar control:

- Lando Norris: the Store control stays a contained rectangle with compact corners, a heavy label and a bag glyph; the racing energy lives around it, so the ordinary silhouette anchors the expression.
- Trevor Noah: the call to action separates its coloured pill (which carries a playful transform) from the stable link and readable label, so the hit area never moves.
- Illoca: the studio rooted the identity in architectural paper, stacked drawings, trace overlays and pencil marks; its controls are a compact navigation strip and a clearly contained call to action.
  That vocabulary belongs to architecture and is not permission to put graph paper on unrelated brands.

### A small visual grammar

Choose one primary control silhouette, a secondary treatment, a type treatment, an icon stroke convention and a focus treatment.
Share spacing relationships rather than giving every component its own radius or shadow.
Keep semantic colours for error, warning and success separate from brand decoration.
A brand accent that fails contrast on a surface needs a different foreground and background pairing, not smaller text or a shadow.

Starting values, adjusted through real-content review:

| Token family | Starting value | Change when |
| --- | --- | --- |
| Interactive targets | 44 px minimum in both axes for standalone controls; 48 px default; 56 px for a prominent action | Larger text, coarse pointers, task emphasis |
| Control text | 16 px for entered values and ordinary controls; 14 to 16 px supporting labels; natural tracking | The brand face's real metrics |
| Control padding | 16 to 24 px horizontal; 8 px label to icon gap | Long labels, heavy letterforms, inset material layers |
| Edges | 1 px resting border, 2 px for stronger separation; one radius family such as 4 or 8 px | A documented brand shape; pills only when the identity has them |
| Icons | 16 to 20 px glyph inside the larger target; one stroke convention, often 1.5 to 2 px | Optical weight at actual size |
| Supporting text | 14 px, line height 1.4 to 1.5 | Longer instructions; never shrink to avoid wrapping |
| Focus | 2 to 3 px solid outline with 2 px offset where practical | Surface contrast, clipping, forced colours |

Use minimum heights and content-driven widths, not fixed dimensions that clip translations or zoomed text.
Use relative units so controls follow the user's text settings.

### Prove the quiet state before adding motion

Lay out primary, secondary, text and icon buttons beside a text field, select, checkbox, radio, switch, tag and inline link, with real labels.
They read as one family without becoming interchangeable.
Check silhouettes with no hover, the real clickable region, and the perceived centring of text and icons.
Then extend the grammar to menus, tabs, cards, overlays, tables and feedback states.

### State contract

Every interactive component has rest, hover where supported, visible keyboard focus, pressed feedback, and an intentional unavailable state if the product uses one.
Persistent selection is different from a momentary press.
Loading, error and success exist only where the component takes part in an operation; mark the rest not applicable instead of inventing them.
An unavailable state prevents activation and explains why when that is useful.
Native disabled controls leave the tab order, so put any needed explanation next to the control, not in a tooltip that needs focus.
`aria-disabled` keeps a control discoverable but does not stop activation by itself; the code must also block it.

| Family | Additional states |
| --- | --- |
| Buttons | Busy, failed, succeeded; selected for real toggle buttons |
| Fields and selects | Empty, filled, read-only, invalid, pending validation, valid when useful; open and selected for pickers |
| Checkboxes, radios, switches | Checked or on, unchecked or off; mixed only for checkboxes; pending and failed for saved settings |
| Navigation and tabs | Current route or selected panel, expanded, collapsed, nested disclosure; loading and error belong to the destination or panel |
| Cards and tables | Selected where selection exists; loading, partial data, empty, permission-limited, error |
| Tags | Static, or explicitly selectable or dismissible; no interactive states on a plain badge |
| Tooltips | Closed, delayed open, open on hover or focus, dismissed |
| Modals and drawers | Closed, opening, open, closing; dirty, submitting, failed, completed when relevant |
| Skeletons | Pending, replaced by content, replaced by an explicit failure; never permanent |
| Empty and error states | A stable explanation; action states belong to the recovery control |
| Custom cursors | Default, contextual hover, pointer down where meaningful; native fallback |

### Motion contract: one change per animation

For each interaction specify the trigger, the animated layer, start and end values, duration, easing, interruption behaviour and the reduced-motion result.
A press communicates pressure, a switch a binary change, a tab marker selection, a drawer location.
Those are different arguments and get different responses; none of them is a shared fade and rise.

Published basis: Carbon separates productive and expressive motion, ties duration to distance and scale, and publishes 70, 110, 150, 240, 400 and 700 ms tokens, with a productive standard curve of `cubic-bezier(0.2, 0, 0.38, 0.9)` and entrance curve of `cubic-bezier(0, 0, 0.38, 0.9)`.

Starting timings (recommended, not measured on award sites):

| Interaction | Treatment | Timing and easing | Reduced motion |
| --- | --- | --- | --- |
| Button hover and press | Surface or border change; optional 1 px inner compression on press | Hover 120 ms ease-out; press 80 ms; release 120 ms | Immediate surface change, no compression |
| Link hover | Strengthen the existing underline, or move an existing directional mark up to 2 px | 120 ms ease-out | Static underline change |
| Field focus or validation | Immediate outline; optional colour change | Focus immediate; colour 100 ms linear | Immediate |
| Checkbox and radio | Swap the mark; optional short stroke reveal | 100 ms ease-out | Immediate mark |
| Switch | Thumb travels the track | 140 ms `cubic-bezier(0, 0, 0.38, 0.9)` | Immediate position and state |
| Dropdown or small menu | Reveal from the trigger edge, at most 4 px travel | Open 150 ms entrance curve; close 100 ms ease-in | Immediate |
| Tabs | Selection indicator moves; reading surface stays still | 160 ms standard curve | Immediate |
| Card hover | One relevant crop, underline or material response; stable outer hit area | 180 ms ease-out | Static border or underline |
| Tooltip | Optional opacity change after intentional hover | 500 ms hover delay; 100 ms linear; immediate on focus | Immediate after the delay |
| Modal | Short surface appearance and dimming | Open 180 ms ease-out; close 120 ms ease-in | Immediate |
| Drawer | Travels from its own edge, no bounce | Open 240 ms; close 180 ms; standard curve | Immediate placement |
| Skeleton | Stable geometry; optional quiet luminance change | 1200 ms ease-in-out cycle, short-lived | Static shapes |
| Success or error message | Readable at once; optional local colour settle | At most 120 ms linear | Immediate |

Availability and state announcements never wait for decoration.
Rapid reversal continues from the current visual state instead of queuing another full animation.
The shell and hit area stay still while inner layers move.
The 450 ms and 750 ms declarations observed on winners belong to brand moments, not routine task controls.

### Verify the assembled set

Build a specimen surface with real content, a keyboard route, a small touch viewport, a slow-data mode and forced error states.
Show states side by side and also exercise the real transitions; a static grid of rectangles proves nothing about keyboard behaviour or recovery.
Record each accepted component's numbers in the component record (`acceptance.md`) so the set can grow without drift.

## Per-component rules

### Primary buttons

Contained surface, short action label, optional icon, stable hit area, explicit focus indicator.
Start at 48 px minimum height, 16 to 24 px horizontal padding, 16 px label, 8 px icon gap; 56 px when the action earns emphasis.
A real destination may be an anchor styled as a button; an action is a native `button`.
Corner shape, edge, accent placement and glyph weight come from the brand.
Hover strengthens the existing affordance, press acknowledges activation, and focus stays distinct from hover.
During an operation keep the width and focus, expose busy, and say what is happening; its pending result gets a layout-matched skeleton.
Show success only after confirmation; keep a nearby failure message with a working recovery.

**Reject:** a primary action reduced to bare text; magnetic movement that shifts the target; several equally dominant actions in one decision; hidden disabled reasons; fake progress; duplicate submission.
**Accept when:** the action is obvious in a still image, Enter and Space behave natively, and a slow or failed operation neither moves nor erases the control.

### Secondary buttons

Same height, label metrics, focus treatment and basic silhouette as the primary.
A visible 1 or 2 px stroke and a quiet surface that stays distinct from what is behind it.
Lower emphasis comes from surface and colour, never tiny text or a smaller target.
Same hover, press, busy, unavailable and recovery logic when it runs an operation.
A cancel action is easy to find without competing with the affirmative one.

**Reject:** an outline that vanishes over imagery; an unrelated pill shape; a hover that turns every secondary into a primary.
**Accept when:** the hierarchy holds at rest, on focus, on hover and in high contrast.

### Text buttons

A low-emphasis action that is still a recognisable bounded control: a quiet permanent surface or visible stroke, at least a 44 px target, 12 to 16 px horizontal padding, the same label treatment as other buttons.
Underlined text is reserved for links.
Focus shows the whole control boundary.

**Reject:** a ghost action that only becomes a button on hover; typographic styling that disguises an action as prose or a link.
**Accept when:** someone unfamiliar can identify it as a control before pointing at it.

### Icon buttons

A 16 to 20 px glyph inside a 44 px minimum square target, 48 px by default, with a visible surface or boundary at rest.
Stroke and optical weight match the type and brand marks.
Do not redraw a standard close, search or disclosure symbol until its meaning changes.
A concise accessible name always; a tooltip supplements the name and never creates it.
`aria-pressed` only on a real toggle, `aria-expanded` only on a real disclosure.
Remote actions need persistent loading and failure feedback outside the tooltip.

Observed: Lando's menu trigger is a native button wrapping a Rive canvas; its accessible name and `aria-expanded` change on open, so a branded glyph kept button semantics.
The same probe found Escape did not close the menu or move focus, which is why the gates test Escape explicitly rather than trusting an award.

**Reject:** ambiguous decorative icons as actions; emoji; tiny close controls; unlabelled SVG buttons; a delete action told apart only by red.
**Accept when:** the action stays named with images off and works by keyboard, touch and screen reader.

### Links

Anchors with real destinations.
Prose links are identifiable at rest, normally underlined with sufficient contrast; start with a 1 to 2 px underline offset clear of descenders and tune to the face.
Standalone navigation links get the 44 px target; inline prose links keep text flow under the inline exception.
Character can come from underline shape, a conventional directional glyph or a relevant annotation mark.
Hover strengthens the underline; focus gets its own indicator; current page uses `aria-current`; visited state helps in reading contexts.

**Reject:** hover-only discoverability; context-free "Read more"; `href="#"` running an action; a cursor effect as the only affordance.
**Accept when:** purpose and destination are clear without animation and open-in-new-tab still works.

### Text inputs and textareas

Persistent label, field boundary, value, optional hint, optional prefix or suffix, nearby error text.
Start with a 48 px field, 16 px entered text, 16 px horizontal padding, 6 to 8 px label gap.
A textarea sized to the expected answer (often three to five lines), about 12 px vertical padding, user resizing kept.
Minimum heights, never fixed ones.
Published: GOV.UK puts labels above fields and rules out placeholders as labels, hints or examples.
The brand may shape edges, background, type metrics and the hint's voice; it never changes native editing, selection, autofill, paste or password-manager behaviour.
States: empty, filled, hover, focus, read-only, disabled, invalid, pending check, and valid where it means something.
Read-only values stay readable and selectable.
An error keeps the value and offers a correction; a green tick on every field is not required.
Focus appears immediately.

**Reject:** placeholder-only labels; animated borders that hide focus; decorative prefixes mistaken for values; clipped text; shaking invalid fields.
**Accept when:** long values, multi-line errors, autofill, mobile keyboards and 200% text all remain usable.

### Selects, dropdowns and comboboxes

Choose by task: native select to pick a value, combobox to search a long set, menu button to choose a command, radios for a short set worth comparing.
Published: GOV.UK treats the select as a last resort and suggests asking questions that reduce the options first.
Persistent label, selected value or prompt, disclosure cue, popup, option states, help and error text.
Start at 48 px for the trigger and 44 to 48 px for options, 12 to 16 px padding, room for label and checkmark; the popup stays aligned or clearly anchored to the trigger.
States: closed, open, hovered option, keyboard-active option, committed selection, disabled option, loading results, no matches, failure, invalid required selection.
Keyboard-active and selected are different states.
Remote results get a layout-matched option skeleton and a readable status announcement.
Brand the container and selected marker, never the keyboard model (W3C combobox pattern).

**Reject:** clickable divs as a list; hover-only options; a popup clipped by an ancestor; silently changing a required answer on focus.
**Accept when:** arrows, Escape, Enter, typeahead where relevant, touch scrolling, long labels and empty results all work.

### Checkboxes

Native checkbox with a visible label; related choices in a fieldset with a legend.
Start with an 18 to 20 px box, a clear 1 to 2 px boundary, 8 to 12 px label gap, and at least a 44 px clickable row.
Published for reference: Carbon draws a 16 px box with 1 px border and 8 px label padding; a small drawn box can sit inside a large clickable row, and the mark's size is never reported as the target's size.
The check can share the brand stroke but keeps its conventional meaning.
States: unchecked, checked, focus, hover, pressed, disabled, group invalid; indeterminate only for real partial selection.
An immediately saved preference also needs pending, confirmed and failed, and shows the last confirmed value.

**Reject:** a rounded mark that reads as a radio; prechecked consent; a decorative tick disconnected from the native value; colour-only checked state.
**Accept when:** clicking the label toggles it, Space works, wrapped labels align, and partial selection is announced.

### Radio buttons

Native same-name radios in a fieldset with a legend.
Start with a 20 px circle, 8 px dot, 8 to 12 px label gap, 44 px rows (Carbon publishes the same 20 px icon and 8 px dot).
Room for labels and helper text to be compared.
States: unselected, selected, hover, pressed, focus, disabled option, invalid group.
Choosing never navigates or submits, and never earns fake success feedback.

**Reject:** square radio marks; hidden defaults on consequential questions; independent toggling; layouts that make long labels hard to compare.
**Accept when:** one value is selected, arrow keys behave natively, and the question is announced with the options.

### Toggles and switches

A binary setting whose on and off meanings are clear.
Start with a 48 by 24 px track (Carbon publishes 48 by 24 with an 18 px handle), a thumb around 18 to 20 px, a 44 px target and a readable label.
Thumb position plus a second cue; colour alone fails.
States: on, off, hover, press, focus, unavailable, and pending save where a server is involved; a failed save is explained beside the setting and shows the confirmed state.
Published: the W3C switch pattern says the label must not change when the state changes; Space toggles, Enter optionally.

**Reject:** a switch that opens a page; a switch for more than two options; an unlabelled state; a decorative spring that delays feedback.
**Accept when:** the effect is predictable, the setting is announced, and a failure cannot leave the visible value contradicting the saved one.

### Form layout and validation

The field group is a component: question or legend, label, hint, input, error, and spacing to the next group.
Start with 24 px between groups, 6 to 8 px between label and field, 4 to 8 px between field and supporting text.
One reading order; group short related inputs horizontally only when that helps, and keep the order when they stack.

Published (GOV.UK): do not validate when the user leaves a field; validate when they try to continue or submit.
Validating before a field is finished is allowed only when user research shows it solves more problems than it causes; the character count is the example.
On failure, show the page again with every answer kept, put an error summary at the top and move focus to it, add "Error:" to the page title, and place a matching message beside each field.

Example copy: "Enter an email address with an @ symbol" and "We could not save the address. Your entries are still here."

**Reject:** red borders without text; toasts for field errors; cleared input; ticks on untouched fields; a disabled submit that hides what is missing.
**Accept when:** every error can be found, reached, fixed and resubmitted by keyboard without re-entering valid answers.

### Navigation and menus

Separate the navigation landmark, destination links, the current-location marker, disclosure buttons and any modal mobile panel.
Use real route names, never numbered labels.
Start with 44 to 48 px targets, 16 px labels, 12 to 16 px item padding, 16 to 24 px between independent controls.
The menu trigger stays a recognisable button; character lives in its material, an existing pictogram, or the active-route mark.
Published: W3C's disclosure navigation example does not use the `menu` role, because site navigation lacks the behaviour assistive technology expects of a menu widget.
States: current, open, closed, hover, focus, press, nested open, unavailable route.
Opening updates the trigger's name or state and makes revealed items reachable; closing removes them from the tab order.
A truly modal mobile menu follows the dialog contract; a non-modal disclosure never traps focus.
Hover supplements click and never replaces it; give a forgiving pointer path into submenus and no opening delay for keyboard.

**Reject:** letter-by-letter reveals so slow that links cannot be reached; focus left behind a modal panel; hidden links still in the tab order; hover-only submenus.
**Accept when:** current location, expanded state, Escape, focus return and touch operation are demonstrated.

### Tabs

For related panels in one context, never instead of destination links.
Tab list, labelled tabs, selected indicator, associated panels, focus indicator.
Start at 48 px height and 16 px padding per tab (Carbon publishes 32, 40 and 48 px); a 2 to 3 px selected rule is one possible treatment, plus a shape or weight cue beyond colour.
Long labels and usable horizontal overflow without hiding the selected tab.
Selection and focus are separate; arrows move within the list, Tab moves into the panel (W3C tabs pattern).
Automatic activation only when switching is effectively instant; otherwise explicit activation with a matching skeleton in the panel and its own failure state.

**Reject:** panels sliding across the screen on every switch; a selected indicator identical to focus; focus lost when the panel loads.
**Accept when:** every panel is related to its tab, keyboard navigation works, and selection stays identifiable under reduced motion.

### Cards

Define the content object first: product, article, project, person or record.
Anatomy follows the object: relevant media, title, metadata, status where needed, and a clear destination or action.
Start with 16 to 24 px internal spacing and an image ratio chosen for the real content; do not give every object the same portrait, square or rounded box.
Observed: Trevor Noah's media takes a peeling Polaroid treatment drawn from the concept; Igloo's makers gave each project a distinct form after identical forms blurred together.
These are transferable decisions, not a demand for 3D cards.
Use an `article` or list item with real headings.
A whole-card link has no nested controls; several actions each get a named, independent target and the title link stays obvious.
States: rest, hover and focus within, selected only where selection exists, unavailable, loading skeleton, missing media, empty metadata, failed retrieval.

**Reject:** three interchangeable icon-topped marketing cards; hover lift as the only cue; tilt on every card; an invisible overlay stealing clicks from secondary controls.
**Accept when:** the object is identifiable without imagery and every action has an unambiguous target.

### Tags and badges

Separate static status labels from selectable filters, removable tokens and actions.
A static badge can be about 24 px high with 12 to 14 px text and 6 to 8 px padding, with no hover and no tab stop.
An interactive chip gets the 44 px target and the correct button or checkbox semantics; a remove control gets its own name and target.
Published: GOV.UK uses tags only for status, says not to make them links or buttons, and in February 2026 changed tag colours and contrast partly to make tags easier to tell from buttons.
Carbon defines separate read-only, dismissible, selectable and operational tags.
Do not mix the two systems' rules silently.
Use real domain words (Available, Draft, Awaiting approval) as adjectives, never verbs.

**Reject:** a coloured dot as the whole status; decorative serial numbers; a static badge that looks like the primary action.
**Accept when:** status, selection and action are distinguishable at rest, including in greyscale.

### Tooltips

Named trigger, short supplementary text, anchored container, optional pointer tip.
Start with 14 px type, 1.4 line height, 8 to 12 px padding, about 240 to 320 px width that shrinks to the viewport.
Never the home for required instructions or a control's only accessible name.
Published: Carbon forbids interactive elements in tooltips and sends that content to a toggletip with the disclosure pattern.
Show on focus as well as intentional hover, dismiss with Escape, stay visible while the pointer is over it, and persist until the trigger condition ends (WCAG content on hover or focus).
Flip or shift at viewport edges; give touch an alternative where the information matters.

**Reject:** essential information that disappears; links in a non-focusable tooltip; flicker while crossing a toolbar; clipped bubbles.
**Accept when:** the information is available without a mouse and never blocks the task it explains.

### Modals and drawers

One overlay contract, different spatial behaviour.
Labelled surface, optional description, content, visible close control, actions, and a backdrop only when modal.
Start a dialog around 480 to 640 px wide with 24 px padding and at least 16 px viewport gutters; a side drawer around 360 to 480 px on large screens, adapting to width and the on-screen keyboard.
Published: Carbon sizes modals from content and moves up a size, or to a full page, when scrolling gets excessive; content inside a modal may show a skeleton, the modal itself never does.
A dialog appears around its task; a drawer enters from the edge it occupies.
Handle open and closed, initial focus, scroll, dirty data, submission, error and completion.
Modal behaviour: focus moves inside, Tab is contained, the background is inert, Escape closes, focus returns to the invoker or the next logical place (W3C dialog pattern).
Choose initial focus deliberately for long or destructive content.
A non-modal drawer never claims modal semantics or traps focus.

**Reject:** hidden close controls; nested routine modals; data lost to a backdrop click; a visual overlay over live background controls.
**Accept when:** focus, dismissal, keyboard resizing, long content and failed submission have all been exercised.

### Tables

A semantic table with caption, column headers, data cells and explicit row actions.
48 px rows for ordinary interactive data, 64 px where two lines help (Carbon publishes 24, 32, 40, 48 and 64 px rows).
16 px cell padding, 14 to 16 px text; align comparable numbers consistently with tabular numerals, and align headers with their data.
The 44 px target still applies to sorting, selection, expansion and row actions.
Brand through typography, rule weight, selection treatment and the data's own vocabulary; a 1 px separator is usually enough structure.
Sortable headers contain a button and announce the sort.
Row selection and row navigation stay distinct.
On narrow screens keep relationships through a deliberate responsive strategy or labelled horizontal scrolling.
A data grid's application keyboard model is extra complexity, not the default.
States: sorting, selection, expansion, partial data, pagination, loading, no results, first-use empty, permission limits, retrieval failure.
Published: Carbon recommends skeletons instead of spinners for delayed table data; use skeleton rows at the real column widths.

**Reject:** row actions hidden until hover on touch; whole-row click handlers fighting checkboxes; reordered columns that lose labels; a centred loader replacing the table.
**Accept when:** headers stay associated, sorting is announced, long values are retrievable, and loading keeps the table's geometry.

### Loading skeletons

Match the expected component's media ratio, text widths, line count, row height, gutters and responsive layout.
A card skeleton predicts that card; a table skeleton predicts its columns.
Keep loaded content and controls in place during background refresh.
Quiet neutral fills with enough separation from the background; the reduced-motion version is static.
Hide skeleton pieces from assistive technology, mark the region busy, and announce loading or completion once when useful.
Published: Carbon uses skeletons for container and data components, not for action controls; the initiating button stays stable with a busy label.

**Reject:** indefinite skeletons; unrelated geometry; focusable fake controls; an empty result reported as still loading; a glossy sweep, pulsing dots, fake progress or a full-page spinner.
**Accept when:** slow, successful, empty, failed and reduced-motion outcomes all keep context and terminate correctly.

### Empty states

Separate first use, no matches, and a collection emptied by the user's own action.
A concise explanation, an optional relevant illustration, and one useful next action where one exists, placed inside the collection or panel that is empty.
Start with 24 to 32 px internal space, 16 px body text, and the established button sizes.
Use the client's real nouns and, if useful, an object from the client's world.
A filtered empty result keeps the query and offers "Clear filters" or another accurate action; first use explains what can be created or added.

**Reject:** a decorative astronaut or trophy with no context; vague encouragement; an empty state shown while still fetching; competing calls to action.
**Accept when:** the cause and the next step are apparent, including to a screen reader.

### Error states

Separate invalid input, unavailable data, failed save, permission denial and missing resource.
Place the state at the smallest useful scope: field, card, panel, and the whole task only when necessary.
A clear problem statement, what is still intact, a correction or recovery action, and a reference detail only if useful.
14 to 16 px text at normal line height, a meaningful icon where it helps, the established action target.
Error colour supplements text and shape.
Calm and specific; humour never covers a lost save or a permission denial.
Keep values, and distinguish a failed request from a successful response with zero records.
Announce inserted status without moving focus for every minor update (WCAG status messages).

**Reject:** blaming copy; raw stack traces; a bare "Retry" with unclear scope; redirecting away from recoverable work; endless automatic retries.
**Accept when:** a simulated offline or server failure produces a truthful explanation and a working recovery with no duplicate side effects.

### Custom cursors

Default to the native cursor.
Add a custom one only when it communicates a specific operation in a suitable media component, such as dragging through an image collection, using the client's mark or short contextual language rather than a generic floating ring.
The real pointer position stays clear and never covers the target.
No universal size.
Enable following behaviour only for fine pointers with hover, with a native fallback; restore text, link, edit and resize cursors inside controls.
Hide decorative layers from assistive technology, set `pointer-events: none`, and drop following or lag under reduced motion.
A drag feature also needs keyboard and non-drag alternatives.
The studied winners use expressive pointer work, but no reusable accessible cursor implementation or reliable timing was established from them.

**Reject:** a lagging cursor over fields; a custom pointer as the only call to action; a cursor effect required on touch.
**Accept when:** turning it off removes no information and no capability.

## Family review

The set passes a family review: the same action hierarchy, geometry relationships, focus grammar, icon weight, state vocabulary and async behaviour across components.
Individual components can have different purposeful motion and still belong to one family.
