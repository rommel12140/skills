# Motion revision validation

Date: 4 October 2026.
Scope: the motion and 3D revision to `design-review` and `awwwards-build`.
This records an editorial regression walkthrough and starter-code browser checks, not an independent agent generation run or an award-quality certification.
No subagent evaluation was run.

## Behavioral walkthrough

Inputs were evaluated against the revised contracts and then compared with their expected decisions.
The chair scenario supplies hypothetical render and device observations; they must never be reported as measurements made by the evaluating agent.

| Case | Decision checked | Result of editorial walkthrough |
| --- | --- | --- |
| Build 06, plain supporting structures | Keep the table, care list and contained controls; require a substantial product signature | Source plan supports `W14`; render gates remain unchecked; removing the signature would fail `S14` |
| Build 07, flat persuasion | Accessibility and a progress line cannot substitute for authored motion | `W14` and `S14` fail with a concrete lamp articulation/material direction; unobserved performance stays unchecked |
| Build 08, ambitious accessible | Accept a chair assembly scene and kinetic type with meaningful alternate versions | Scoped motion gates pass against the supplied hypothetical evidence only; blank alternate versions and delayed purchase access fail the mutation checks |
| Review 09, subject-led build | Prevent the previous permission to omit motion entirely | Expected behavior now requires signature, section levels, opening/handoff and later development; full generation remains untested |
| Review 11, focused sign-in | Avoid importing promotional theater into an operational screen | Task-focused composition and truthful state feedback remain valid; no mandatory WebGL or promotional content |
| Review 13, flat persuasion | Detect a weak positive craft result even with no catalog violations | P1 motion-direction finding, preserving the useful table and form |
| Review 14, ambitious accessible | Preserve accepted 3D when its behavior and budgets are supported | Accept against the supplied evidence; independent browser verification remains unclaimed |
| Review 15, missing visual provenance | Remove false proof while retaining visual strength | Requires an owned or original replacement and prototype; full generation remains untested |

The checks establish consistency and intended decisions, not how reliably a fresh model will follow them.
The generation cases should be run on future skill revisions when independent evaluation is authorized.

## Starter-code checks

All JavaScript and JSX fences in [motion recipes](../references/motion-recipes.md) and [WebGL craft](../references/webgl.md) were extracted into an isolated local harness and bundled with esbuild.
Package versions used: GSAP 3.15.0, Lenis 1.3.26, Three.js 0.186.1, React 19.3.0, and React Three Fiber 9.8.1.
R3F was bundle-checked; its example was not runtime-tested as a full React application.

The DOM and Three.js recipes were exercised through `chrome-devtools-axi` with an original procedural two-part assembly and inline poster/text content.
This was an integration harness, not a finished design candidate.

| Check | Observed result |
| --- | --- |
| ScrollTrigger forward and reverse, 1280 by 800 | Progress followed the same timeline in both directions; intermediate values included 0.5, 0.9375 and 0.28125, with corresponding mask states |
| 390 by 844 mobile/touch emulation | No horizontal overflow; coarse pointer used native scrolling; narrative stage recomposed in normal flow without the desktop's extra scroll height; forward/reverse progress and mask agreed, including the initially visible scene |
| Kinetic type | Accessible heading retained the complete phrase; teardown restored unsplit markup |
| Reduced-motion startup in a separate forced-preference browser | No moving-story class, text splitting or mounted spatial scene; resolved content remained in flow |
| Normal and reduced route adapter | Route callback completed and focus reached the incoming heading without an input-covering overlay |
| Two GLSL fragment recipes with their shared vertex shader | Both compiled and produced nonzero color pixels in a WebGL render target; no shader errors |
| Three.js context loss and restoration | Canvas hid on loss, poster state returned, and rendering resumed after restoration |
| Offscreen scene | Changing progress while offscreen produced no extra pose/render calls |
| Teardown | Zero remaining ScrollTriggers; scene resources disposed once; canvas hidden and narrative class removed |
| Rejected model promise | Poster remained, canvas stayed hidden, and no unhandled rejection occurred |
| Route disposal before a late model result | Late resource was disposed once without being mounted |

The starter was corrected during these checks so the poster's visual layer hides only after a successful frame and restores on loss/disposal.
The scroll recipe was also recomposed into separate media/explanation columns on desktop and ordinary flow on phones, avoiding sticky media covering its explanation or leaving a long mobile scroll area.
Attaching ScrollTrigger after the timeline is built and synchronizing initial progress corrected a mismatch between the mask and scene state when the phone loaded partway into the reveal.

Not established by this harness: physical-phone frame performance, production asset weights, full screen-reader conformance, real router history/error integration, background-tab profiling, and a live operating-system reduced-motion preference change.
Those remain required checks when adapting the patterns to a production page.
The shader and component tests are not evidence that a finished page meets the proposed budgets.

## Repository checks

- Both skill entrypoints passed the skill-creator frontmatter validator.
- Local Markdown reference targets were checked for existence.
- Changed and added files were checked for long dash punctuation and private task material.
- `git diff --check` passed.

Research limits, including the screenshot-export restriction and the inconclusive live ice-world visit, are recorded in [motion research](../references/motion-research.md).
