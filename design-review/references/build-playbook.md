# From brief to finished page

Use this for new work and scoped refinement.
Keep the direction and verification notes in the task's normal working area, not as extra copy on the website.
The goal is a coherent first presentation after internal revision.

## Understand the job before the composition

Write down the following facts in a short brief.
Separate supplied facts from assumptions and unavailable material.

| Decision | Evidence needed | Consequence for the page |
| :--- | :--- | :--- |
| Reader and situation | Who arrives, what they know, device/context | Vocabulary, density, navigation and pace |
| Job | Decide, compare, buy, enquire, read, operate or explore | Page structure and primary action |
| Claim and proof | Real service, product, work, result, image or demonstration | What deserves the largest visual area |
| Identity | Existing site, logo, type, palette, physical material, voice | What to preserve and where distinction can come from |
| Content | Approved copy, numbers, images, captions and legal necessities | Real line lengths and section sequence |
| Constraints | Stack, CMS, licenses, localization, accessibility, supported devices | Feasible production system and fallback |
| Acceptance | What the user likes, dislikes and specifically asked to change | Protected baseline and regression checks |

Do not turn ordinary design choices into a long interview.
Ask only when a missing fact changes the concept or makes the result untruthful.
Keep building independent parts while a required fact is pending.
If assets are missing, use an honest representative asset or explicitly marked draft state; do not invent testimonials, client work or outcomes.
A final candidate cannot depend on placeholders that disguise missing proof.

## Derive a visual language

Collect real material from the client's world: product geometry, tools, architecture, documents, packaging, photography, production processes or existing marks.
Make a chain from source to design decision to reader benefit.
Reject a connection that ends at resemblance alone.

| Source | Potential decision | What earns it |
| :--- | :--- | :--- |
| A joinery workshop's joints and grain | Precise image boundaries, close crops, warm material photography | Makes workmanship inspectable |
| Film programming and projection | Poster hierarchy, frame-based navigation, a controlled reveal | Lets a visitor choose and understand films |
| A logistics yard | Real positions, movement and operational sequence | Explains where time is lost and how the product intervenes |
| Hospitality interiors and landscape | Image-led rhythm, quiet navigation, type selected against the photography | Helps a visitor judge the place and plan a stay |
| A reporting workflow | Aligned dates, comparable rows, visible status and compact actions | Shows what needs attention without opening every record |

These are possible translations, not industry templates.
A receipt-shaped card is not automatically appropriate for a restaurant operations screen.
The user may need a fast table, not simulated paper.
Ask whether the rest of the site already uses the proposed mark and whether it solves the current page's job.

## Choose a direction that can be described

Before coding the whole page, compare two plausible directions in working notes when the brief leaves room.
Choose one based on the content, brand and visitor task; do not require the user to choose between unfinished alternatives.
For narrow polish, use the accepted direction instead.

A useful direction specifies:

- A concept in one sentence tied to a concrete subject.
- The main contrast: type scale, image scale, density, placement or material.
- Display, body, UI and numeric type roles.
- Surface, ink, accent and status color roles.
- The opening composition and the sequence of proof.
- A signature behavior if it improves the experience, plus the sections that stay still.
- How it changes on small screens and with reduced motion.

Reject a direction whose description consists only of style adjectives.
It should predict actual choices and exclusions.
If changing the business name leaves the page equally plausible for any company, revisit the concept or proof.

## Compose the argument

Choose the order by what the reader needs to understand next.
Do not fill an inherited list of hero, features, testimonials and CTA.

For a persuasion page, a possible sequence is a concrete promise, visible proof, explanation, objections and a next step.
Use only the parts needed for this decision.
A portfolio can show work early, then use selected details to establish the maker's role and judgment.
A reference page can use indexes, dense tables and persistent navigation when retrieval benefits.
An application should put high-frequency work and exceptions within reach, with supporting detail available on demand.
A login screen normally needs identity, sign-in choices and meaningful status; it does not need a product tour added to fill space.

For each section, write its job, evidence, dominant element, intended density and handoff to the next section.
Vary visual rhythm through content and proportion: large image, compact comparison, detailed proof, quiet action.
Do not force every section into a card grid, alternating split layout or full-screen scene.
Use whitespace to group and pace actual content, not to conceal its absence.

## Prove the system in a browser

Build the hero, one representative content section, a control and their transition with real words and intended assets.
The representative section must contain the hardest content, not only the shortest heading.
Include a long title, realistic metadata and a loading or error state if this is an application.

Review that slice at 1280x800, a larger desktop and a phone viewport.
Check type texture, wrapping, image crop, usable controls and the first impression without animation.
If the direction fails here, change the system before repeating it throughout the site.
A moodboard or static mockup can help choose a direction; it does not replace this check.

Build shared tokens and components from the proven decisions.
Keep typography, colors, spacing, radii and motion roles centralized.
Avoid a universal card, shadow or reveal wrapper that forces unrelated content into the same shape.
In a CMS, test a realistic range of content lengths and image ratios.
In Webflow, preserve class and interaction relationships; use the native design system instead of piling on overriding embeds.

## Refine without regression

Record the accepted baseline before edits: screenshots at relevant sizes, existing interaction behavior, active theme and the user's protected elements.
List what is permitted to change and what the specific correction must achieve.

A request for better typography does not authorize a new palette.
A request to move a report into a side sheet does not authorize redesigning the report interior.
A request for richer motion does not authorize replacing the central object, project order or hero.
Compare the final candidate against the baseline, not against memory.
If a previous variation was rejected, remove its effects before building on the accepted version.

Improve craft where scope is tight: optical spacing, text hierarchy, common edges, control proportions, grouping, state feedback and transition continuity.
Do not satisfy a request for a distinct design by adding a status strip or label while leaving the actual composition untouched.

## Adapt an existing template faithfully

Inventory sections, navigation, image slots, decorative assets, breakpoints and interaction owners first.
Separate structure from replaceable content.
Record the intended role and geometry of every replacement.

- Keep the section order, layout relationships and existing animation unless change is authorized.
- Fit real copy to the template's rendered line count and density without changing its meaning.
  Character counts help estimate fit, but the actual font and words decide the result.
- Choose image subject before aspect ratio, then verify crop and focal point in the real slot.
- Replace the logo with the real asset and inspect sharpness at its display size.
- Check hidden menus, hover states, mobile variants, footer and embedded previews for old content.
- When removing an unsupported block is authorized, remove its stranded imagery, controls, padding and broken anchors together.
- Compare the finished page with the template at matching viewports and interaction states.
  A clean content audit does not prove visual fidelity.

## Finish and deliver

Complete every requested route, responsive layout and component state before adding optional flourishes.
Test the primary journey and recovery path with realistic content.
Use the [quality review](quality-review.md) before sharing the candidate.
Fix the system causing repeated defects rather than patching individual instances.
If a required asset or browser check is unavailable, name the limitation and avoid claiming completion of that part.
Present a live preview when possible, a few exact changes and the checks actually performed.
Ship only within the user's existing authorization, then verify the released version is the reviewed version.
