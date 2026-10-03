# Motion and 3D research

Research date: 4 October 2026.
This is a purposeful craft sample, not a statistical claim about award winners.
Keep **live observation**, **maker account**, **published documentation**, and **recommendation** separate.
An award record establishes recognition, not present-day accessibility, performance or conversion.
The current live site can differ from its judged version.

## Recognition and live sample

| Work | Verified recognition | Why study it |
| --- | --- | --- |
| [Lando Norris](https://www.awwwards.com/sites/lando-norris) by OFF+BRAND | Site of the Year 2025 in the [annual winners](https://www.awwwards.com/annual-awards/winners); daily record and Developer Award provenance also recorded in the [structural research](../../awwwards-build/references/evidence.md) | A recognizable person and racing equipment organize a large motion system |
| [Fluid Glass](https://www.awwwards.com/sites/fluid-glass) by Exo Ape | Site of the Day, 30 March 2026; its record includes the developer jury's scored evaluation | Motion within a restrained architectural composition, including loader, masks, navigation and continuous project browsing |
| [Igloo Inc](https://www.awwwards.com/sites/igloo-inc) by abeto and Bureaux | Site of the Year and Developer Site of the Year 2024 in the [official hall of fame](https://www.awwwards.com/annual-awards/hall-of-fame/2024) | One material world, real-time entrance, distinct project objects and scene transitions |
| [Lusion v3](https://www.awwwards.com/sites/lusion-v3) | Site of the Day, 2 October 2023; the [official directory](https://www.awwwards.com/websites/%23DAF0F6/?page=14) lists Developer Award and Site of the Year 2023 | Older technical comparison: real-time material, flexible image surfaces and persistent visual continuity |

The sample combines recent 2025/2026 work with earlier spatial work whose maker accounts explain the implementation.
It does not claim the older sites are recent releases.

## What the live inspection established

Chrome was controlled through `chrome-devtools-axi` at 1280 by 800.
The inspection used DOM/state queries, scroll input and exported WebGL canvas frames where available.
Full-page screenshot export reported success but did not create files; the underlying tool reported a workspace-path restriction.
Canvas exports were inspected directly, but do not include overlaid HTML.
These limits matter: this pass does not establish whole-page pixel quality, accessibility conformance or physical-device frame rates for any winner.

| Live observation | Mechanism and implication | Limit |
| --- | --- | --- |
| [Lando Norris](https://landonorris.com/): a viewport-sized `.gl` canvas renders the portrait against the drawn brand field; headings, project names and destinations also exist in HTML | The dominant subject is rendered material, while the page retains a document layer; this is much more substantial than a margin ornament | No exact shader, easing or mobile-performance claim follows from the canvas frame |
| Lando forward samples at scroll 0, 650 and 1350px, followed by reversal to 650px: helmet bands cross the portrait during the opening; the later dark field holds a smaller portrait/video rectangle with oversized moving type; reversal returns that composition | The subject changes scale and context while the brand field persists; the opening and later beat are different compositions | Canvas samples exclude HTML controls and do not establish the entire loading or timing sequence |
| [Fluid Glass](https://fluid.glass/): an actual nested `.scroll.lenis` scroller, 8696px of content at this viewport, with product, showroom, project and process sections | Scroll ownership must target the real container; a window scroll measurement alone would miss its choreography | Mechanism corroborated by the maker account below; no full motion recording or reduced-motion audit claimed |
| Fluid Glass scroll samples at 0, 600, 1600 and 3000px: a large asset's vertical transform changes from 0 to about 300px, then settles near 586px; text lines resolve from separate vertical offsets toward their baselines | Image parallax and staggered line timing have different jobs; the motion system is present even in a restrained layout | These are sampled transforms, not a measured easing curve or frame-rate test |
| [Lusion](https://lusion.co/): the first large canvas showed lit blue, white and dark sculptural forms in a cropped field; after wheel input the reel became a bent image surface, then project images occupied a two-column field | The same visual layer carries different material and editorial states; at sampled wrapper offsets near -1620px and -3035px, the scene changes role rather than repeating a reveal | Native `window.scrollTo` did not drive its custom scroller; wheel events were needed for the sampled sequence |
| Lusion reverse input returned the wrapper near -1553px and the bent reel composition reappeared | Reverse is part of the authored sequence; compare the intermediate surface, not only the final screenshot | The playing reel has time-varying content, so repeated frames are not pixel-identical |
| [Igloo Inc](https://www.igloo.inc/): the loader appeared, then the inspected DOM exposed an empty WebGL host without readable content or an exportable canvas | Live inspection was inconclusive; use the maker's published sequence as a studio account, not as a claimed observed pass | No assertion that its current live sequence, keyboard path or fallback worked in this environment |

No measured easing values or loading durations were inferred from screenshots.
The ranges in [motion](motion.md) and code values in [recipes](motion-recipes.md) are recommendations.

## Maker accounts: mechanisms worth building

### abeto: material continuity through the whole page

The [Igloo case study](https://www.awwwards.com/igloo-inc-case-study.html), published 31 October 2024, describes a real-time coded intro, unique ice forms for each project, and transitions combining displacement, frost and chromatic aberration.
The footer's particles form different objects for different links.
The team prototyped untextured camera journeys and worked on code and 3D together in the browser.
They report custom compressed volume export, staged texture loading and shader compilation to control startup cost.
The stack includes Three.js, Svelte and GSAP.

**Recommendation:** plan entrance, projects and exit as states of one material idea, with different silhouettes so items remain distinguishable.
Prototype the camera handoff before detailed shading.
Do not copy the glow/glitch styling or canvas-only UI as defaults; provide semantic HTML and authored alternate versions independently.

### Exo Ape: restraint with an actual motion system

The [Fluid Glass case study](https://www.awwwards.com/fluid-glass-case-study.html), published 7 May 2026, reports early motion studies for page transitions, menus, buttons and hover states.
Its logo entrance resolves into the site; the navigation island adapts to context and opens at the end of the page.
Projects continue from one case study into the next.
Nuxt supplies the frontend, and GSAP ScrollTrigger drives scroll interactions with SVG detail.

**Recommendation:** a restrained visual system still needs deliberate arrival, section handoffs and route behavior.
Keep the material reference in apertures, crops and timing instead of decorating every section with an icon.
Use a truthful, skippable-by-readiness loader rather than adding a fixed delay to imitate an entrance.

### OFF+BRAND: a camera and asset pipeline designed together

In [Aether 1](https://tympanus.net/codrops/2025/08/06/building-aether-1-sound-without-boundaries/), published 6 August 2025, the makers describe fictional earbuds, baked GLB animation driven by `AnimationMixer`, a single camera with separate position and target paths, and GSAP-controlled scene compositing.
They report a low-resolution fluid buffer, simplified raycast proxies, matcap-based glass and approximations for costly post effects.
The claimed 60fps on an iPhone SE is their measurement, not this research pass's result.
Their custom infinite-scroll work also exposed broken state and history risks before revision.

**Recommendation:** prototype camera, material and DOM as one sequence; reduce expensive buffer resolution and invisible geometry before giving up the idea.
Keep native scrolling and bounded scenes as the baseline, with direct navigation and an equally composed reduced-motion version.
This source supports implementation craft, not the banned glow or an invented commercial product claim.

### Stefan Vitasovic: type, video geometry and route rhythm

The maker's [2025 portfolio account](https://tympanus.net/codrops/2025/03/05/case-study-stefan-vitasovic-portfolio-2025/), published 5 March 2025, describes masked character segments assembling into words, bent/displaced video planes, shared geometry and only rendering needed meshes.
The published code uses a 0.5-second route crossfade and character durations starting at 1.25 seconds with 0.025-second index increments.
Those are source-reported values, not recommended universal timings.
Its mobile version uses HTML video while retaining the motion principles.
The reported stack includes React, Motion, Three.js and R3F.

**Recommendation:** connect type construction to the subject, cap text-sequence duration, and preserve the same visual concept when changing the rendering mechanism for phones.
Do not copy infinite scrolling or long type delays into a transactional journey.

### Active Theory: overlap design and implementation

The official [Designing with Code talk page](https://www.awwwards.com/andy-thelander-from-active-theory-designing-with-code.html), published 5 September 2017, summarizes Andy Thelander's account of iterative prototyping and overlapping design and development, with technical experiments influencing visual style.
This research inspected the published talk summary, not a complete video transcript.
It is historical process evidence rather than a current library recommendation.

**Recommendation:** build a rough moving scene before approving a static layout for a spatial idea.
The prototype should decide camera, material, text and performance together, rather than reserve animation for the end of implementation.

### Locomotive: scroll infrastructure is only one layer

The current [Locomotive Scroll documentation site](https://scroll.locomotive.ca/) identifies v5 as a wrapper around Lenis, with separate observation strategies, native scrollbar behavior and mobile parallax disabled by default unless opted in.
These are the library author's statements, not an audit of every site using it.

**Recommendation:** choose one scroll owner, then author the actual narrative timeline on top.
Smooth input is not itself the signature, and installing both Lenis and a Lenis-based wrapper does not add craft.

## Synthesis for the skills

- A large opening is one valid canvas for the brand's world, not a compulsory loader or a reason to delay useful content.
- The signature can be a spatial object, material scene, cinematic image handoff or substantial kinetic type.
- A page-wide motion plan makes entrances, transitions, controls and intentional stillness part of one direction.
- Performance engineering preserves the idea through batching, baking, staging and authored alternate versions.
- Studio accounts do not establish accessible semantics, reduced-motion behavior, focus restoration or failure recovery; those remain acceptance work for the new build.
- Removing an unverified asset should replace its compositional role with verified imagery or honest original illustration, not remove visual ambition.

See [motion direction](../../awwwards-build/references/motion-direction.md), [implementation patterns](motion-recipes.md), and [scene and shader recipes](webgl.md) for the buildable consequences.
