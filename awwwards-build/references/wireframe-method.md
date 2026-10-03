# Wireframe method

The method is a **recommendation** derived from the studied winners and their makers' accounts.
It is not any one studio's process.
Where a step rests on a studio account or an observation, the step says so; sources are in `evidence.md`.

The aim: the wireframe proves why the page has this sequence, why each section has this shape, and how a visitor moves between them.
The drawings can be rough.
The decisions must be precise enough that whoever builds the page does not have to invent its argument while styling it.

## What the studios disclose

Their working artifacts differ, so no single fidelity is correct.

| Studio account | What it says | What the method takes from it |
| --- | --- | --- |
| Abeto, Igloo Inc | Grey mockups and sketches to map the journey, key interactions and navigation; quick untextured "previs" renders for sections a still cannot explain | Draw the journey early; use a rough moving prototype where a still is ambiguous |
| Exo Ape, 2026 interview | A 3 to 4 hour discovery workshop; UX inside discovery; wireframes detailed enough to pass for design, with type and imagery; early technical tests where needed; one direction presented to the client | Raise fidelity where uncertainty demands it; present one confident direction |
| Monavon and Lallé, 2025 | Designer and developer together from the first client meeting; references narrowed from about 20 to 3; multiple layouts and motion concepts tested together, with front-end feasibility checks during design | Select references for specific structural problems; test feasibility before committing the page to an interaction |
| Obys, 2026 | Started from a custom typeface that became the identity's foundation; deliberately left awards, archives and extended case studies off the site | Content selection is design work; a mature identity can shape structure before grey boxes |
| Siena Film Foundation makers | Extensive prototyping of a dual local and global navigation | An unusual navigation or central interaction needs a working prototype, not a box with a note |

**Recommendation:** content-first and narrative-first are complementary passes.
Content-first establishes the facts, images, demonstrations and actions that exist.
Narrative-first establishes the order in which they change the visitor's understanding.
Move between the passes when the story demands evidence the project does not have, and never invent facts to complete a composition.

## Page task

Write in plain language:

- the audience and their arrival context;
- the page's purpose and the intended next action;
- what a visitor must understand or believe before that action is reasonable;
- the shortest useful route for a returning visitor.

Name the dominant behaviour: persuade through a sequence, help people compare, let them browse a collection, explain a process, or serve as reference.
A page can do more than one, but its opening makes the dominant one clear.
Reference tools such as persistent contents rails belong where finding a specific item is the task, not on a persuasion page.

**Output:** a short brief and one sentence stating the page's argument.
Example: a specialist installer's page might argue that it can execute complex installations and coordinate the trades, then ask for a project enquiry or a showroom visit.
That sentence already demands outcome evidence and process evidence.

## Content and evidence inventory

One row per fact or claim:

| Field | Content |
| --- | --- |
| Claim | The statement, in the project's words |
| Source | Where it is confirmed, or "unconfirmed" |
| Asset | The image, video, object, document or demonstration that proves it, with dimensions, usable crops and focal subject |
| Concern | The visitor question it answers |
| Destination | Where it leads, if anywhere |

Open every image before assigning it.
A placeholder states what must be shown ("close view of the seal meeting the frame corner"), never just "image".
Use approximate real copy lengths when final copy is missing.
Mark an unsupported result or missing photograph as a dependency.
Every number must be confirmed or listed in `voice.md`; anything else is left out.

**Output:** a content and evidence map stating what each material can actually prove.

## Sequence

Write each beat as **concern → answer → evidence**, then why it follows the beat before it.
Remove beats that repeat a claim or exist because homepages usually have them (a services band, a stats strip, a testimonial carousel with nothing specific in it).
Move optional depth to a project page, product detail, disclosure or archive when it interrupts the argument.

Different briefs produce different sequences:

- a known product can open on a purchase proposition and inspection options;
- an unfamiliar invention may need orientation, mechanism and proof before configuration;
- a studio can lead with work and let its methods explain the quality already shown;
- a place can lead with the experience, then access, practical detail and booking.

Stop when the argument is made and the remaining concerns are answered.
Do not target a section count.
Observed range: Igloo's makers describe three sections; the inspected Lando page has about nine content beats; both work because each beat has a job.

**Explore structures privately.**
Sketch at least two structurally different sequences: they change what the visitor meets first, where the proof sits, or how the work is explored.
Moving an image to the other side is not a different structure.
Choose the one that explains the material more clearly or makes the task easier, keep a familiar component when it is the best fit, and present only the chosen structure with one line on why the alternative lost.

**Output:** an ordered outline with the job and evidence of each beat and the reason for each transition.

## Section briefs

Fill this for every section before choosing a pattern or component:

| Field | Decision |
| --- | --- |
| Purpose | The understanding or action this section must produce |
| Incoming context | What the previous section has established |
| Claim and evidence | The actual statement and the material that supports it |
| Dominant element | The image, object, text, comparison or control people notice first |
| Relationship | Sequence, comparison, scale, cause and effect, classification, detail and context, or invitation |
| Composition | Relative spans, alignment anchors, crop, density, and what the empty space does |
| Action | Label, destination and why here, or an explicit decision that no action is needed |
| Transition | What persists, changes or concludes as the next section arrives |
| Narrow layout | Reading order, crop, essential control and content priority on a small viewport |
| Interaction states | Initial, active and completed states, including reversal or exit |
| Dependencies | Missing facts, assets or behaviour that block acceptance |

Example: a showroom section's dominant element might be a large video of the space, because the visitor must picture the place before deciding to visit; its supporting information is the address and a visit action.
The product-family section before it has a different relationship (classification) and so gets a different arrangement.

**Output:** section briefs that explain the geometry in terms of the content.

## Whole-page wireframe

Draw the full page at desktop width and at a narrow width with the chosen content.
Draw the hero together with at least its successor: a hero that consumes the whole concept leaves the rest of the page with no reason to exist.

- Preserve the distinctions that change composition: portrait or landscape, short statement or long explanation, one object or many, comparison or sequence.
- Use real images or recognisable thumbnails where their shape determines the layout; grey and rough crops elsewhere.
- Set one shared alignment system, then vary spans and offsets inside it.
  Show the main horizontal edges, text starts and repeated caption relationships.
- Let a dominant image cross the content width when the evidence benefits from scale; let narrow text sit inside a broad field when concentration matters.
  Do not centre every section by default.
- Review the page as one continuous strip.
  Mark where it invites scanning, reading, inspection or action, and change scale, density, relationship or scroll behaviour when the job changes.
  Peer items in a useful collection stay comparable; do not vary them for variety's sake.

Text wireframes are acceptable when no drawing tool is available.
Use relative positions and real labels, for example:

```text
Product browsing                           Showroom invitation

             Tall product photo            Large continuous video of the space
                         Short context
  Product photo      Product photo          Visit proposition     Address
                                                                  Book a visit
```

**Output:** a coherent full-page composition with an explainable rhythm and real reading order.

## Motion as states

For each interactive or transitional section, record:

- what the visitor sees on entry, what changes during interaction, and what remains after;
- the trigger, available controls, focus order, scroll ownership, reversal behaviour and escape route;
- which information must stay readable during the change;
- the still or ordinary document flow used under reduced motion, on touch, and when media fails.

| Section relationship | Decide in the wireframe | Can wait |
| --- | --- | --- |
| Object and explanation | Which part moves, which explanation stays, how the matching part is identified | Final easing and material rendering |
| Collection to project | Which selected item persists into the detail view, and how visitors return | Final transition treatment |
| Large image to contextual grid | Whether the image becomes a grid item and what the new grouping means | Parallax amplitude |
| Process stages | Which evidence accompanies each stage, and whether stages can be reached directly | Small decorative responses |
| Physical invitation | How media, address and action stay associated across the boundary | Final grading |

Essential evidence survives without hover or a timed reveal.
Where a still drawing leaves the relationship ambiguous, make a rough animation, clickable prototype or browser experiment.
"Animate on scroll" is not a motion decision.

**Output:** a state sequence per interactive section and a small prototype for the structurally uncertain one.

## Narrow screens and real navigation

Revisit hierarchy before shrinking anything.

- Decide which crop communicates the same fact, which side information joins the reading flow, and which secondary material becomes optional depth.
- A multi-image composition may keep selected offsets if it stays legible (observed: Telha Clarke's mobile capture keeps its scattered image field and archive action while recomposing the text).
- A technical comparison may need stacked, paired rows with persistent labels.
- Show the real navigation, the primary control, and what is visible in the opening viewport.
- Give horizontal browsing a visible affordance and a direct alternative when the hidden items matter.
- Long text grows; never trap it in a fixed-height panel.
- Draw long names and captions.

**Output:** a narrow layout that keeps the argument and makes every primary task reachable.

## Prototype the hardest boundary, then build

Test the section most likely to fail together with its predecessor and successor: slow scroll, fast scroll, reversal, tap, keyboard, and return from a destination.
Confirm the visitor can identify the current item and continue after the effect ends.
A transition can look right in isolation and still produce an unreadable handoff or a dead end in the full page.

Build in semantic reading order with real content.
Reuse components around stable content contracts (project metadata, media captions, product options, navigation controls).
Let a section's composition be specific where its argument needs it; one universal heading, body and button shell must not dictate every section.
Test variable content and missing media before visual work locks the layout.

**Output:** a structural prototype and the acceptance evidence in `acceptance.md`.

## When to send the wireframe back

Return it for revision if the argument depends on an unsupported claim, a missing dominant asset, an unintelligible interaction, or a task that cannot be completed at narrow width.
Minor polish can wait.
A missing structural decision cannot be fixed later by a typeface or by motion.
