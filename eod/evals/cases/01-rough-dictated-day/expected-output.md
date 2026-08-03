# Case 01 - expected output

The correct answer for this case already exists: it is `references/specimen.md`, written by the owner from the same day.

This case grades **phrasing fidelity**.
The input notes are already in his words, so a correct run reproduces those words.

## The target

```
EOD for today 7/30/26

ProfitsX development. Exciting, everything's coming together, drafting stage is done. Focused on Homepage today (noting all the things we've talked about yesterday). MovingScrubs, wired up the resources automation from GHL. A little slower today with less AI help. Tomorrow, I have ALL my AI colleagues, which I can delegate like importing to webflow, and stuff.

 - ProfitsX Homepage. Piecing up together to create one Homepage from the fintech, private equity, and other templates. Components are being built now. Not yet done but tomorrow, we'll be able to import it to webflow. Homepage is being focused right now because once this is done, the other pages will be easier since we now have the full concept.
 - Moving Scrubs: Added a new popup component for the resources page for download. Before, it was direct download, right now they have to fill up the form to receive the resource. Webinars are done. GHL Login is done. Resources is done. Thank you pages, wired up. Exit and newsletter popups are done.
 - Growth Engine 3D animation. Conceptualize for a better growth engine with the new inspiration. This helps our story and animation to be in sync. Hoping to ship it together tomorrow.
 - Prepared the info and brand settings for the kitchen mockup, tomorrow I'm gonna send the mockup.
```

## The six phrasings that must survive

Each row is a checkable expectation. The left column must appear in the output.
The right column is what a first version of this skill produced instead, and each one fails the case.

| Must appear | Fails the case |
| :--- | :--- |
| Tomorrow, I have ALL my AI colleagues, which I can delegate like importing to webflow, and stuff. | Tomorrow, I have ALL my AI colleagues so I can delegate stuff like the webflow import. |
| Piecing up together to create one Homepage from the fintech, private equity, and other templates. | Pulling one Homepage together out of the fintech template, the private equity one, and some others. |
| noting all the things we've talked about yesterday | noting all the things we talked about yesterday |
| Components are being built now. | Components are being built right now. |
| Conceptualize for a better growth engine with the new inspiration. | Conceptualized a better growth engine off the new inspiration. |
| Prepared the info and brand settings for the kitchen mockup, tomorrow I'm gonna send the mockup. | Prepped the info and brand settings for the kitchen mockup, sending the mockup tomorrow. |

Every entry in the right column is grammatically better than the left, and that is exactly why it fails.
His ruling: "The roughness is my voice. Follow my voice, and making it smoother is kinda like feeling AI sloppish."

Grade this table first. If any row fails, the run fails, whatever else it got right.

## Checklist

### Wording (`W1`)

- [ ] All six rows above hold.
- [ ] No verb replaced with a more standard one.
- [ ] No tense regularised.
- [ ] No fragment completed. "Thank you pages, wired up." stays a fragment.
- [ ] No clause reordered for flow.
- [ ] No contraction expanded or introduced.
- [ ] No trailing "and stuff" dropped.
- [ ] No dictated word swapped for a tidier synonym. "gonna" survives.
- [ ] Any sentence that differs from the notes can be justified by grouping, ordering, capitalisation at the start of a sentence, or a genuine typo. Nothing is justified by reading better.

### Format

- [ ] First line is exactly `EOD for today 7/30/26`. Not `07/30/26`, not `2026-07-30`.
- [ ] One blank line after it, one blank line after the main outcome.
- [ ] Exactly four bullets, each marked with one leading space, a hyphen, a space.
- [ ] No blank lines between bullets.
- [ ] No headers, bold, italics, tables, code fences, links or emoji.
- [ ] Zero characters above U+007F, proved by script and not by `grep`.

### Assembly

- [ ] Order is ProfitsX Homepage, Moving Scrubs, Growth Engine, kitchen mockup.
- [ ] The notes' feeling block, which arrives last, is assembled into the main outcome rather than left as a fifth bullet.
- [ ] The parenthetical about yesterday, which arrives at the end of the ProfitsX block, is placed in the main outcome.
- [ ] The main outcome names ProfitsX as the centre of gravity and does not run through all four bullets (`M1`).
- [ ] The pace note survives (`M3`). Dropping or softening it fails the case.
- [ ] Bullet 1 says the homepage is not done and names what unblocks it (`B3`), and keeps the reason it came first (`B4`).
- [ ] Bullet 2 keeps webinars, GHL login and resources as separate sentences (`B5`).
- [ ] The separator after the workstream name is not standardised across all four (`B2`).
- [ ] `GHL` capitalised, `webflow` lowercase, `Homepage` capitalised (`V5`).

### Honesty

- [ ] No fact in the output that is absent from the input.
- [ ] No number anywhere. The input has none.
- [ ] Nothing in progress reported as done.

## Acceptable variation

Narrow, and narrower than it used to be.

- `MovingScrubs` and `Moving Scrubs` are both correct. The specimen uses both in one report.
- Capitalising the first word of a sentence his notes left lowercase.
- Where in the report a given sentence lands, as long as it lands somewhere sensible.
- A connective joining two of his fragments, where one is needed and none of his fit.

Rewriting a sentence is not acceptable variation. That was the previous version of this case and it was wrong.

## Automatic fail

- Any row of the six-row table broken.
- A fifth bullet.
- A completion the input did not report.
- Merging the webinars, GHL login and resources sentences.
- Any em dash or en dash.
