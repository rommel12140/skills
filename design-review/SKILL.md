---
name: design-review
description: >
  Design, build, refine, or audit websites and interfaces against an Awwwards
  standard of art direction, typography, motion, usability, and execution.
  Use for new pages, visual polish, template adaptation, components, and design
  reviews.
  Preserves accepted work and checks rendered states alongside source.
  Also audits visual artifacts where applicable.
  Reports evidence and fixes,
  never a synthetic quality score or a promise of winning an award.
---

# design-review

Make the first presented candidate feel designed for its subject and complete in use.
The [design-tells catalog](references/design-tells.md) is the floor.
Passing it does not establish excellent design.
A distinctive concept, deliberate typography, strong content, composed layouts and well-executed behavior establish the higher bar.

One pass means the agent does its own investigation, construction and revision before asking the user to review.
It does not mean showing an untested first render or promising a jury outcome.

## Choose the scope

State **Build**, **Refine**, or **Audit** in the first progress update.
The former **Constraint** mode maps to Build or Refine.

- **Build:** create a direction and implement the requested page or interface.
- **Refine:** improve a named part of existing work, preserving accepted content, behavior and design decisions.
- **Audit:** inspect and report findings; do not implement changes unless requested.

For a dedicated component system or wireframing deliverable, use the sibling Awwwards build skill instead.
A template adaptation is Refine: preserve its composition and interaction structure unless the brief authorizes changes.
For a deck or other static artifact, apply the composition, type, imagery and content checks; mark web-only behavior checks inapplicable.
A request for review alone is not permission to rebuild, deploy or publish.

## Read the right references

In every mode, load the [design-tells catalog](references/design-tells.md).
For Build, read [the build playbook](references/build-playbook.md), [typography](references/typography.md), and [layout and surfaces](references/layout-and-surfaces.md).
Read [motion](references/motion.md) before changing any animation or transition.
For Refine, load the relevant craft reference and the preservation rules in the playbook.
For Audit, read [the quality review](references/quality-review.md) and the catalog, then load the craft reference for each weak area.
Read [award research](references/award-research.md) when selecting a direction or explaining the bar.
Use [worked examples](references/worked-examples.md) to distinguish a substantive correction from a cosmetic one.
Every mode ends with the applicable [self-check](references/quality-review.md#before-showing-the-candidate).
Use [stack-specific fixes](references/fixes-by-stack.md) for catalog findings.

## Non-negotiable constraints

- Read the project's `voice.md`, visual-language rules and established components before choosing a style.
  User instructions and accepted design decisions take precedence over this skill's defaults.
  If `voice.md` is absent, say so, proceed with explicit assumptions, and mark `X1` unchecked.
  Do not invent a brand history, approved palette or permitted statistic.
- Derive the visual language from the client's real material and the page's job.
  Identify a specific form, object, process, image treatment or typographic behavior that earns its place.
  An industry association alone does not justify an ornament.
- Keep the existing bans: decorative glowing networks, halos, pulsing dots, generic gradient meshes, floating glass, neon-on-dark atmosphere, equal icon-topped feature triplets, emoji iconography, and universal fade-up reveals.
- Do not add decorative numbered labels or invented pseudo-technical codes.
  Genuine data, ordered steps and useful reference navigation retain their meaning; never manufacture numbering to make a persuasion page look designed.
- Keep buttons recognizable as buttons.
  Improve their proportions, hierarchy and states without turning actions into bare text.
  Use layout-matched skeletons for content loading and preserve meaningful failure and recovery states.
- Each narrative animation performs its section's argument and differs from the preceding animated section.
  Keep a consistent motion character and repeated control behavior.
  Sections with nothing to explain through motion stay still.
- Match layout to the job.
  Persuasion needs an argument and proof; reference needs retrieval; an application needs visible state and an obvious next action.
- Preserve what the user already likes.
  The catalog constrains additions; it does not authorize deleting deliberate existing elements or replacing an accepted design system.
  Record a justified exception instead of silently redesigning.
- Write concrete copy without long dash punctuation, inflated claims or generic promotional phrases.
  Do not add technical implementation commentary to the product unless it changes a user's decision.

## Build or refine

1. Establish the reader, task, primary action, proof, assets, constraints and protected baseline.
   Read before asking for missing information; proceed on reversible choices with stated assumptions.
2. Write a short direction in working notes: page argument, visual source, type roles, color roles, composition and the one interaction worth remembering if the job needs one.
   Include what stays still and how the mobile version works.
3. Inspect relevant reference behavior in a browser.
   Describe the mechanism and why it fits before borrowing it.
   Reference images and source inspection do not prove timing, usability or smoothness.
4. Build a representative slice with real copy, intended fonts, the actual visual material where relevant and working controls.
   Check the hero, a content section and their handoff at 1280x800 and on a phone viewport before repeating the system across the page.
5. Finish all requested sections, routes and states.
   Integrate motion after the static hierarchy works, then refine layout and motion together.
   Do not hide missing content behind animation or loaders.
6. Run the self-check, correct faults, and rerun the affected checks.
   Repeated corrections become explicit regression checks against the actual rejected state.
7. Present the candidate with its preview, the concrete design decisions and any unchecked evidence.
   Follow existing authority for commit, release and publication; this skill adds no approval round.

## Review both the floor and the bar

First walk the catalog's P0, P1 and P2 gates.
Then assess the positive qualities in `quality-review.md`: concept and subject fit, content, type, composition, surfaces, motion, responsiveness, accessibility and delivery.
An empty findings list is not a claim of excellence.
Name what is strong and identify the most consequential remaining weakness, with a visible reason.

Use `chrome-devtools-axi` when available, or the environment's authorized browser tool.
Capture 1280x800 before wider desktop views, plus a true mobile viewport.
Inspect the pixels, keyboard path and actual state changes.
For moving work, inspect the sequence, interruptions and reverse travel as well as settled frames.
Do not declare rendered checks passed from source, DOM geometry alone, a tool's success message or a test count.
If rendering is unavailable, complete useful source review and explicitly mark visual and motion judgments unchecked.

## Output contract

Keep the user-facing report short; retain detailed checks in task notes when needed.
For each finding, use a catalog ID or a descriptive craft label, severity, location, evidence and a stack-appropriate fix.
Stable IDs are review bookkeeping, never labels to add to the interface.

```text
K5 | P1 | .report-action, phone viewport
Found: The action looks like adjacent metadata and has no visible button boundary.
Why: The next step is difficult to recognize.
Fix: Apply the established compact button treatment and verify focus and pressed states.
```

Every finding must be locatable and name a correction.
Keep observed facts separate from a proposed direction and from unverified assumptions.
Record accepted exceptions and skipped checks with reasons.
Close an audit with finding counts by severity and a plain readiness statement: ready for visual review, needs revision, or insufficient evidence.
Do not assign a quality score or estimate award odds; see [why no score](references/why-no-score.md).
On re-audit, mark earlier findings resolved, still open or newly introduced.
Preserve the accepted baseline and verify that a correction did not reintroduce an earlier rejection.
