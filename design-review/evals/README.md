# Design-review evals

These cases test building decisions, scoped refinement and evidence-based review.
All scenarios and fixtures are synthetic and self-contained.
They generalize recurring failure patterns without reproducing private projects or conversations.

| Case | Main check |
| :--- | :--- |
| [Generic source-only page](cases/01-generic-saas-hero/input.md) | Find planted source tells without inventing a rendered pass |
| [Editorial reference page](cases/02-editorial-reference-page/input.md) | Respect page purpose and accepted typography; avoid false positives |
| [Webflow template adaptation](cases/03-webflow-template/input.md) | Preserve composition, assets and interactions; give native-stack fixes |
| [Accepted card refinement](cases/04-protected-refinement/input.md) | Improve hierarchy without adding strips or replacing approved decisions |
| [Report surface and buttons](cases/05-report-surface/input.md) | Improve reading structure while keeping controls recognizable |
| [Reference motion](cases/06-motion-sequence/input.md) | Observe mechanism, context, interruptions and repeated behavior |
| [First load and mobile](cases/07-font-and-mobile/input.md) | Check cold fonts, true viewport and image visibility |
| [Loading and recovery](cases/08-loading-states/input.md) | Match content geometry and distinguish missing data from loading |
| [A complete new build](cases/09-subject-led-build/input.md) | Produce a subject-specific page through internal revision |
| [Context fit](cases/10-context-fit/input.md) | Reject an industry motif that obstructs the actual task |
| [Quiet sign-in](cases/11-task-focused-login/input.md) | Compose the requested task without unnecessary product promotion |
| [Award and type claims](cases/12-evidence-and-typography/input.md) | Separate official criteria, measured evidence and recommendations |
| [Flat persuasion](cases/13-flat-persuasion/input.md) | Fail token motion despite clean semantics and no banned decoration |
| [Ambitious accessible motion](cases/14-ambitious-accessible/input.md) | Preserve substantial 3D and type with authored alternate versions and supplied performance evidence |
| [Visual replacement](cases/15-visual-replacement/input.md) | Replace unverified dominant imagery with equally strong honest art direction |
| [Idle draws and a throttled phone](cases/16-idle-draws-and-throttled-phone/input.md) | Treat idle rendering and per-frame effects as P0 design defects with measured acceptance |
| [Resize overflow and fragments](cases/17-resize-overflow-and-fragments/input.md) | Fit after a resize, no partial words in a stack, and the phone as its own composition |
| [Flat palette and stock loader](cases/18-flat-palette-and-stock-loader/input.md) | Colour from the site's own family and a loader drawn from its mark |

The subject-led build case also requires the new motion minimum.
Cases 16 to 18 cover the performance, fit, phone, colour and loader gates added to the skill on 8 October 2026; they were written as editorial regression checks and have not been run by an independent agent.
See [motion revision validation](motion-validation.md) for executed checks and untested scope.

## Run a case

Give an agent the skill and one case's `input.md`, plus the referenced fixture when present.
Do not give it `expected-findings.md` until grading.
Use the mode requested by the input and the tools actually available.
For a building task, judge the resulting implementation and preview, not an unexecuted plan.
A fresh authorized worker is useful for a behavioral evaluation; never delegate when the task prohibits it.

The Markdown scenarios supply explicit hypothetical observations where a real browser fixture is unnecessary.
An agent may reason from those observations but must not claim it personally captured or tested them.
For HTML fixtures, run through an authorized local preview and inspect the browser when evaluating rendered gates.
When no browser is supplied, grade source analysis and evidence honesty only.
Do not make a rendered-quality claim from the expected answer.

Compare the result with the case's `expected-findings.md`.
Record the skill revision, model when known, tools, mode, findings, unacceptable outcomes and any untested requirement.
A static editorial walkthrough can check coverage and contradictions; label it as such rather than as an independent agent run.

## Grade the decision, not a phrase

| Outcome | Meaning |
| :--- | :--- |
| Pass | Required decisions and findings are present, with no prohibited result |
| Recall miss | A specified defect is ignored |
| False positive | An accepted or task-appropriate choice is treated as a defect without evidence |
| Scope failure | The agent changes protected work or implements an audit-only request |
| Evidence failure | It claims a visual, interaction, source or performance check it did not perform |
| Incomplete build | It stops at a plan or polished hero while requested content or states remain unfinished |
| Wrong correction | It identifies a problem but prescribes an unsuitable stack, task or behavior |

Use catalog IDs where they fit and descriptive craft findings for other defects.
Equivalent concrete fixes can pass; the eval does not require matching wording or one visual style.
Severity can differ with demonstrated impact, but unsupported certainty and preservation violations fail regardless of severity.
Do not turn the case results into a synthetic design score.
