# Motion direction before layout is finished

These are skill requirements and recommendations, not award rules.
Research and implementation live in the sibling `design-review` skill: [observed mechanisms](../../design-review/references/motion-research.md), [DOM and navigation recipes](../../design-review/references/motion-recipes.md), and [3D, shaders and budgets](../../design-review/references/webgl.md).
The planning contract below remains usable without that sibling installed; consult the linked primary library documentation before implementation if necessary.

## Plan one signature moment

A signature is a specific transformation that a visitor could describe afterwards, tied to the brand's own object, material, process or typography.
It commands a meaningful part of the composition and connects at least two states of the page's argument.
A tiny underline, moving margin rule, logo spin or generic floating primitive does not qualify by being called a signature.

For a boat builder, a hull can move from an exterior silhouette to exposed ribs while actual construction details enter beside it.
For a type foundry, a word can change axis and layout to demonstrate the typeface's range while its specimen stays selectable.
For a glazing company, an architectural image can pass through the proportions of its real opening system, then become a project detail.
These are possible interpretations, not motifs to transplant between industries.

Write this contract before finalizing the wireframe:

```text
Source in the brand's world:
What the visitor will understand or remember:
Dominant visual and provenance:
Entry, transformation, resolution, next-section handoff:
Timeline positions or scroll interval and easing character:
What stays readable and operable throughout:
3D/shader decision and implementation owner:
Phone composition and touch behavior:
Reduced-motion composition and no-WebGL/no-JS alternative:
Frame, asset and loading budgets:
Prototype evidence, including interruption and reverse:
```

Keep one signature as the main event rather than competing full-screen spectacles.
It can continue across several sections.
Every page plans a signature, but an operational or reference page can express it through a compact state transition or a distinctive still composition when that serves the task better.
An explicit static brief, protected existing design or reduced-motion preference takes precedence.

## Give every section a motion level

Use words in planning notes, never invented codes on the page.

| Level | Page job | Required decision |
| --- | --- | --- |
| Still | Read proof, compare values, complete a form, recover between scenes | Why stillness improves this beat; how the incoming motion resolves into it |
| Responsive | Confirm input or show an available action | Hover, focus, press, open, close, interruption and touch equivalents |
| Narrative | Show a relationship, change of scale, material, sequence or context | Entry, intermediate and final compositions, scroll ownership and reverse |
| Signature | Make the page's central idea tangible and memorable | Full storyboard, moving prototype, scene handoff and alternate versions |

A persuasion page's normal-motion version has, at minimum:

- An expressive opening or first section handoff that establishes its visual world.
- A later narrative transformation that develops the argument or proof.
- Consistent feedback for controls and navigation.
- One of those narrative beats developed into the signature moment.

One continuous scene can meet both narrative beats if its later state changes meaning, scale or evidence.
This is a coverage requirement, not a quota of effects or a requirement to animate every section.
Still tables, body copy, care instructions and forms remain valid.
All-still persuasion pages, or pages with only token hovers and minor reveals, fail even when their typography and semantics are sound.

## Decide whether depth earns its place

Ask what a camera, material or deformation can show that flat placement cannot show as clearly or as memorably.

| Intent | Buildable mechanism | Strong alternate version |
| --- | --- | --- |
| Explain assembly | Three.js or R3F model groups driven by scroll, baked animation or an exploded view | Labeled assembly stills in reading order |
| Make a material inspectable | Lit close-up, matcap or constrained refraction over owned imagery | Carefully lit photograph with the same crop and detail |
| Move through a world | One camera path, staged objects, DOM context at each beat | Composed views with direct section navigation |
| Carry a project into its detail | Shared image crop, framework transition or one persistent WebGL plane | Immediate navigation to the same image and title |
| Express a type identity | Line masks, variable axis change, intentional reflow | Strong final typesetting with real words |

3D is a positive option to prototype, not a reward added after the rest is finished.
When DOM, SVG, video or type better serves the subject, name that choice and build it with equal ambition.
Do not import a WebGL stack for an irrelevant spinning object.

## Replace the banned default with craft

| Banned default | Stronger option to develop |
| --- | --- |
| Glowing connected dots, halos, pulsing nodes | A real object undergoing a readable transformation; a physical assembly, edited process footage, or a typographic state change |
| Three equal icon-topped cards | One dominant demonstration with supporting evidence, unequal project imagery, or a genuine comparison with aligned values |
| Universal fade and small rise | A crop revealing workmanship, a material changing under light, type assembling by phrase, an object separating into parts, or an image continuing across a boundary |
| Generic gradient mesh blobs | Light derived from a real material, a constrained palette and directional shader field attached to an object, with controlled noise and a sharp focal hierarchy |
| Floating glass panels or neon atmosphere | Actual product glazing, metal, paper, pigment or fabric with intentional thickness, roughness and lighting; keep controls legible in HTML |
| Pseudo-technical labels and ornamental numbering | Real product names, dimensions with sources, maker's marks, meaningful captions and type hierarchy |
| Emoji UI icons | Existing brand marks, commissioned pictograms, purposeful material silhouettes or plain text controls |
| Index rails or reference furniture on persuasion pages | Section-to-section continuity through subject, image, type or camera; a clear primary action in ordinary flow |

Removing a banned effect creates a design assignment.
It does not justify a blank field of large text and hairlines.

## Preserve visual strength when evidence changes

Record what each removed asset was doing: establishing scale, showing a person, demonstrating a mechanism, adding texture, or carrying the hero.
Replace that role at comparable compositional strength using verified material or an original illustrative treatment.
For owned photography, specify subject, viewpoint, light, crop and intended slot.
For generated imagery or 3D, state what is illustrative and avoid invented customer evidence, product performance, completed work or endorsements.
For type-led art direction, specify scale, line structure and motion behavior rather than enlarging an ordinary paragraph.
Review the replacement in the whole page at desktop and phone sizes.
If a critical factual asset is still unavailable, keep that dependency open while completing the honest illustrative direction.

## Acceptance evidence

Capture entry, mid-transformation, resolved and reverse states at 1280 by 800 and a phone viewport.
Test fast scroll, direct anchors, keyboard continuation, route return, resize, preference changes and asset failure.
Measure the busiest scene with the same device and throttling before and after optimization.
Apply `W14`, `W15`, `S14`, `S15` and `S16` in [acceptance](acceptance.md).
A plan can explicitly fail these gates, but it cannot establish a rendered pass.
