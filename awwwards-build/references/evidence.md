# Evidence

What the skill's rules rest on, with sources.
All sources were checked on 3 October 2026.
Live sites change after judging, so observations are dated and must not be read as current design rules.

## Evidence classes

- **Observed:** read from a live page's DOM, computed CSS or accessibility tree, from an official Awwwards capture, or from a published sketch.
- **Studio account:** the makers' description of their own work.
- **Published:** a design system's or W3C's stated specification.
- **Recommendation:** this skill's synthesis or starting value.

## Award sample

A purposeful sample, not a statistical one.
Awards establish provenance; they say nothing about conversion or comprehension.
Developer Awards were confirmed from the DEV badge in Awwwards directory listings: every entry page shows a "DEV AWARD" score block, so that block alone is not proof.

| Site | Recognition | Makers |
| --- | --- | --- |
| Lando Norris | SOTD 17 Nov 2025; Developer Award; Site of the Year 2025; Site of the Year Users' Choice 2025 | OFF+BRAND |
| Trevor Noah | SOTD 3 Sep 2026; Developer Award | OFF+BRAND |
| Illoca | SOTD 4 Sep 2026; Developer Award | Unseen Studio |
| Igloo Inc | SOTD 23 Jul 2024; Developer Award; Site of the Year 2024; Developer Site of the Year 2024 | abeto with Bureaux |
| Messenger | Developer Site of the Year 2025 | abeto |
| Opal Tadpole | SOTD 11 Jan 2024; E-commerce of the Year 2024 | Claudio Guglieri, Ingamana, and credited collaborators |
| Siena Film Foundation | SOTD 18 Mar 2025; Site of the Month, March 2025; Developer Award | Niccolò Miranda, Federico Valla, G-NS Studio |
| Telha Clarke | SOTD 16 Feb 2026; Developer Award | Thomas Monavon, Grégory Lallé, Studio Paack |
| Fluid Glass | SOTD 30 Mar 2026; Developer Award | Exo Ape |

Award sources:
[Lando Norris](https://www.awwwards.com/sites/lando-norris),
[Trevor Noah](https://www.awwwards.com/sites/trevor-noah),
[Illoca](https://www.awwwards.com/sites/illoca),
[Igloo Inc](https://www.awwwards.com/sites/igloo-inc),
[Opal Tadpole](https://www.awwwards.com/sites/opal-tadpole),
[Siena Film Foundation](https://www.awwwards.com/sites/siena-film-foundation),
[Telha Clarke](https://www.awwwards.com/sites/telha-clarke),
[Fluid Glass](https://www.awwwards.com/sites/fluid-glass),
[2025 annual winners](https://www.awwwards.com/annual-awards/winners),
[2024 hall of fame](https://www.awwwards.com/annual-awards/hall-of-fame/2024),
[Sites of the Year collection](https://www.awwwards.com/websites/sites_of_the_year/),
[Sites of the Month](https://www.awwwards.com/websites/sites_of_the_month/),
[directory search](https://www.awwwards.com/websites/).

## Studio accounts

| Source | What it says | Used for |
| --- | --- | --- |
| [abeto, Igloo Inc case study](https://www.awwwards.com/igloo-inc-case-study.html) | Three sections; Bureaux supplied moodboards, renders, 3D assets and a content outline; grey mockups and sketches mapping the journey; untextured previs for hard sections; identical ice blocks looked too similar, so each project got its own; a particle model per external link; UI moved to WebGL for text glitches and scrambles | Wireframe fidelity; prototype the uncertain section; differentiate collection items; small section counts |
| [abeto, Messenger case study](https://www.awwwards.com/messenger.html) | Custom control over outline thickness; UI rendered in WebGL; one finger on mobile, mouse only on desktop | Deliberate stroke character; simple input demands (not evidence of keyboard or screen-reader support) |
| [OFF+BRAND, Lando Norris](https://www.itsoffbrand.com/our-work/lando-norris) | Motion drawn from racing and his personality; his life on and off the track | Identity carried by familiar controls; subject-led opening |
| [OFF+BRAND, Trevor Noah](https://www.itsoffbrand.com/our-work/trevor-noah) | A living collage; flat 2D assets with a peeling Polaroid effect | Material layer separate from the hit area; cards drawn from the concept |
| [Unseen, Illoca](https://unseen.co/projects/illoca/) | May 2026; identity rooted in paper, stacked drawings, trace overlays and pencil marks | Brand evidence from the client's own materials |
| [Exo Ape interview, idid.team](https://idid.team/en/articles/other/netherland-shiftbrain-03/) | June 2026; 3 to 4 hour discovery workshop; UX in discovery; highly detailed wireframes with type and imagery; early technical prototypes for 3D; one direction presented, not options | Fidelity where uncertainty demands it; present one structure |
| [Monavon and Lallé, Codrops](https://tympanus.net/codrops/2025/02/25/from-concept-to-code-inside-the-creative-process-of-thomas-monavon-gregory-lalle/) | Designer and developer together from the first client meeting; references narrowed from about 20 to 3; multiple layouts and motion concepts in design; front-end feasibility tests during design | Reference selection; explore structures internally; test feasibility early |
| [Obys, Awwwards case study](https://www.awwwards.com/the-new-obys.html) | July 2026; a custom typeface became the identity's foundation; awards, archives and extended case studies deliberately left off the site | Content selection as design work |
| [Telha Clarke case study](https://www.awwwards.com/reshaping-telha-clarkes-digital-home.html) | Three or four highlighted projects flow into a contextual image grid; one animated widget is the primary call to action across the site; motion treated as navigation | Focused work sequence; contextual image field |
| [Fluid Glass case study](https://www.awwwards.com/fluid-glass-case-study.html) | Lead generation and the showroom justified a dedicated video module; motion studies at UX and component level; a dedicated process section in photography and video | Invitation to a real next step; process with working evidence |
| [Siena Film Foundation case study](https://www.awwwards.com/siena-film-foundation-case-study.html) | Left menu is local navigation, right panel global; poster and footage modes; extensive prototyping of the dual navigation | Collection as an interactive field; prototype unusual navigation |
| [iyO case study](https://www.awwwards.com/iyo-case-study-selling-the-worlds-first-audio-computer.html) | July 2026; homepage to feel it, product page to understand it, store to engage; the founder walked the team through the hardware; scroll-driven exploded view | Sequence across pages; stable explanation with changing object |
| [Claudio Guglieri, Tadpole](https://guglieri.com/work/tadpole) | Project account and credits | Provenance for the Opal captures |

Excluded: a 2026 Codrops interview with OFF+BRAND about presenting the Lando hero could not be retrieved, so nothing here depends on it.

## Observed, October 2026

Read in Chrome through `chrome-devtools-axi` at 1440 by 1000 CSS px, with `getBoundingClientRect` and `getComputedStyle`.
These are dated examples, not sizing prescriptions.

| Site and element | Measured | Lesson |
| --- | --- | --- |
| Lando Norris, Store control | 118.26 by 60; padding 0 13.33 px; 1 px border; 7.2 px radius; 16.67 px label at weight 800; split decorative characters `aria-hidden`, readable text in a screen-reader-only sibling | Keep one accessible label when decorating or duplicating visible text |
| Lando Norris, menu trigger | Native button, 60 by 60, 9.87 px radius, Rive canvas inside; name and `aria-expanded` change on open; colour transitions 750 ms `cubic-bezier(0.65, 0.05, 0, 1)`; Escape left it open with focus on the trigger | A branded glyph can keep button semantics; test Escape and focus return rather than trusting an award |
| Lando Norris, Business enquiries | 170.75 by 40 | Below the 44 px bar; do not copy sizes without checking |
| Lando Norris, page | 12 DOM sections; horizontal history 3530 px tall; onward bridge about 476 px | Exploration and routing get different spans |
| Trevor Noah, Get Tickets | Link `href="/shows"` holding `.button_pill` and `.button_label`; 166.28 by 58.09; 32 px padding; 21.42 px label at weight 500; pill transform 450 ms `cubic-bezier(0.17, 0.67, 0.3, 1.33)`; wrapper clip-path 1200 ms with 200 ms delay (an entrance, not hover) | Material layer moves, hit area stays; separate entrance from response |
| Trevor Noah, menu and social links | Menu 58.09 px circle; social links 49.56 px squares, each named | Icon size, visible shape and hit area are separate decisions |
| illoca.com, now serving Plamo | "Try Plamo" 133.88 by 48, 4 px radius, padding 6 16 6 6, solid fill; Products trigger 72.33 by 15 at 13 px | Current production, not the award state; small visible triggers need a hit-area check |
| Fluid Glass, page | Eight body modules; four product families; grid of 24 tracks at 39.75 px with 18 px gaps (1368 px); nested scroller 1000 by 10181 | A fine shared grid carries varied spans |
| Telha Clarke, page | Arrival, studio, three selected projects, image field around "All Work (31)", vision, method, footer; sections labelled 01 to 04 | Focused proof then breadth; numbered labels excluded from this skill |
| Siena Film Foundation, page | Enter splash and onboarding overlay, then one full-frame film with title, credits, recognition, quotes, Explore action and a ticket-style picker | The collection is the opening; the gate is a cost |

Contrast of observed solid pairs, by WCAG relative luminance: Lando 12.26:1, Trevor 14.69:1, Illoca/Plamo 9.70:1.
These cover the observed pairs only, not other states or moving backgrounds.

Official captures used for section analysis:
[Lando desktop](https://www.awwwards.com/inspiration/desktop-lando-norris),
[Fluid Glass showroom](https://www.awwwards.com/inspiration/showroom-fluid-glass),
[Fluid Glass process](https://www.awwwards.com/inspiration/process-component-fluid-glass),
[Telha Clarke parallax grid](https://www.awwwards.com/inspiration/parallax-grid-telha-clarke),
[Telha Clarke mobile](https://www.awwwards.com/inspiration/mobile-telha-clarke),
[Opal hand sequence](https://www.awwwards.com/inspiration/the-hand-flip-opal-tadpole),
[Opal explanation](https://www.awwwards.com/inspiration/explain-it-like-i-m-a-5-yo-opal-tadpole),
[Opal technical view](https://www.awwwards.com/inspiration/show-don-t-tell-opal-tadpole),
[Siena filmstrip](https://assets.awwwards.com/awards/element/2025/02/67c1d9d03b360064251603_static.jpeg),
[Igloo project sketch](https://assets.awwwards.com/awards/gallery/2024/09/concept-02.jpg).

Not established from the winners: a full accessibility, reduced-motion, forced-colours or mobile audit of any site; hover timings that were not observed; a reusable accessible custom cursor.
No winner is called accessible or inaccessible as a whole.

## Published specifications

| Source | Value used |
| --- | --- |
| [Carbon button](https://www.carbondesignsystem.com/building-blocks/core/components/button/specifications) | Heights 24, 32, 40, 48 (productive and expressive), 64, 80 px |
| [Carbon text input](https://www.carbondesignsystem.com/building-blocks/core/components/text-input/specifications) | 8 px label gap, 4 px helper gap, 16 px horizontal padding, 1 px bottom border, 2 px focus and invalid |
| [Carbon checkbox](https://www.carbondesignsystem.com/building-blocks/core/components/checkbox/specifications) | 16 px box, 1 px border, 8 px label padding |
| [Carbon radio](https://www.carbondesignsystem.com/building-blocks/core/components/radio-button/specifications) | 20 px icon, 8 px dot, 8 px label margin |
| [Carbon toggle](https://www.carbondesignsystem.com/building-blocks/core/components/toggle/specifications) | 48 by 24 px track, 18 px handle |
| [Carbon tabs](https://www.carbondesignsystem.com/building-blocks/core/components/tabs/specifications) | 32, 40, 48 px |
| [Carbon data table specs](https://www.carbondesignsystem.com/building-blocks/core/components/data-table/specifications) and [guidelines](https://www.carbondesignsystem.com/building-blocks/core/components/data-table/guidelines) | Rows 24, 32, 40, 48, 64 px; skeletons instead of spinners for delayed data |
| [Carbon motion](https://www.carbondesignsystem.com/building-blocks/foundations/motion/overview) | Productive and expressive; 70, 110, 150, 240, 400, 700 ms; standard `cubic-bezier(0.2, 0, 0.38, 0.9)`, entrance `cubic-bezier(0, 0, 0.38, 0.9)`; duration grows with distance |
| [Carbon loading](https://www.carbondesignsystem.com/building-blocks/core/patterns/loading) | Skeletons for container and data components, not action controls; inside a modal, never the modal itself |
| [Carbon tag](https://www.carbondesignsystem.com/building-blocks/core/components/tag/guidelines) | Read-only, dismissible, selectable and operational variants |
| [Carbon tooltip](https://www.carbondesignsystem.com/building-blocks/core/components/tooltip/guidelines) | No interactive content; use a toggletip |
| [Carbon modal](https://www.carbondesignsystem.com/building-blocks/core/components/modal/guidelines) | Size from content; move up a size when scrolling is excessive |
| [Carbon empty states](https://www.carbondesignsystem.com/building-blocks/core/patterns/empty-states) | Empty-state types and next actions |
| [GOV.UK text input](https://design-system.service.gov.uk/components/text-input/) | Labels above inputs; no placeholder as label, hint or example |
| [GOV.UK select](https://design-system.service.gov.uk/components/select/) | Last resort; reduce options by asking questions first |
| [GOV.UK checkboxes](https://design-system.service.gov.uk/components/checkboxes/) and [radios](https://design-system.service.gov.uk/components/radios/) | Fieldset and legend grouping |
| [GOV.UK validation](https://design-system.service.gov.uk/patterns/validation/) | Not on leaving a field; on continue or submit; in-field validation only when research supports it; keep answers, summary with focus, "Error:" in the title |
| [GOV.UK error summary](https://design-system.service.gov.uk/components/error-summary/) and [error message](https://design-system.service.gov.uk/components/error-message/) | Summary at the top with links; matching field messages |
| [GOV.UK tag](https://design-system.service.gov.uk/components/tag/) | Status only, never a link or button; February 2026 colour and contrast change made tags easier to tell from buttons |
| [WCAG 2.5.8](https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum.html) | AA, 24 by 24, exceptions for spacing, equivalent, inline, user agent control, essential |
| [WCAG 2.5.5](https://www.w3.org/WAI/WCAG22/Understanding/target-size-enhanced.html) | AAA, 44 by 44 |
| [WCAG 2.4.13](https://www.w3.org/WAI/WCAG22/Understanding/focus-appearance.html) | AAA, area of a 2 px perimeter, 3:1 change between focused and unfocused |
| [WCAG contrast](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html), [non-text contrast](https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html), [focus not obscured](https://www.w3.org/WAI/WCAG22/Understanding/focus-not-obscured-minimum.html), [animation from interactions](https://www.w3.org/WAI/WCAG22/Understanding/animation-from-interactions.html), [reflow](https://www.w3.org/WAI/WCAG22/Understanding/reflow.html), [status messages](https://www.w3.org/WAI/WCAG22/Understanding/status-messages.html), [content on hover or focus](https://www.w3.org/WAI/WCAG22/Understanding/content-on-hover-or-focus.html) | As stated in the accessibility gates |
| [APG switch](https://www.w3.org/WAI/ARIA/apg/patterns/switch/) | Label must not change with state; Space toggles, Enter optional |
| [APG disclosure navigation](https://www.w3.org/WAI/ARIA/apg/patterns/disclosure/examples/disclosure-navigation/) | Site navigation does not use the menu role |
| [APG tabs](https://www.w3.org/WAI/ARIA/apg/patterns/tabs/), [combobox](https://www.w3.org/WAI/ARIA/apg/patterns/combobox/), [modal dialog](https://www.w3.org/WAI/ARIA/apg/patterns/dialog-modal/) | Keyboard models referenced in the component rules |

Smaller dense-interface sizes from Carbon are not adopted, because this skill's bar is a 44 px target.

## How the research was checked

The material came from two research passes on 3 October 2026, one on components and one on wireframing and sections.
Before it became this skill, every award date and badge, every studio account above, the published numbers, and every live measurement were re-checked against the sources.
All live measurements reproduced.
Corrections made at that point: the GOV.UK tag change is described as colour and contrast only; the Obys starting point is a typeface; the GOV.UK in-field validation exception is scoped to research-backed cases; presenting two structures became exploring two privately and presenting one, after the Exo Ape account; the Siena entry gate is recorded; Developer Awards cite directory badges; Messenger's category is named; one unretrievable interview claim was dropped.
