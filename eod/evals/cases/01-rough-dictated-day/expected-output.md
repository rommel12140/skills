# Case 01 - expected output

The correct answer for this case already exists: it is `references/specimen.md`, written by the owner from the same day.

A run passes when the checklist below holds.
It does not have to match the specimen word for word.

## The target

```
EOD for today 7/30/26

ProfitsX development. Exciting, everything's coming together, drafting stage is done. Focused on Homepage today (noting all the things we've talked about yesterday). MovingScrubs, wired up the resources automation from GHL. A little slower today with less AI help. Tomorrow, I have ALL my AI colleagues, which I can delegate like importing to webflow, and stuff.

 - ProfitsX Homepage. Piecing up together to create one Homepage from the fintech, private equity, and other templates. Components are being built now. Not yet done but tomorrow, we'll be able to import it to webflow. Homepage is being focused right now because once this is done, the other pages will be easier since we now have the full concept.
 - Moving Scrubs: Added a new popup component for the resources page for download. Before, it was direct download, right now they have to fill up the form to receive the resource. Webinars are done. GHL Login is done. Resources is done. Thank you pages, wired up. Exit and newsletter popups are done.
 - Growth Engine 3D animation. Conceptualize for a better growth engine with the new inspiration. This helps our story and animation to be in sync. Hoping to ship it together tomorrow.
 - Prepared the info and brand settings for the kitchen mockup, tomorrow I'm gonna send the mockup.
```

## Checklist

### Format

- [ ] First line is exactly `EOD for today 7/30/26`. Not `07/30/26`, not `2026-07-30`.
- [ ] One blank line after it, one blank line after the main outcome.
- [ ] Exactly four bullets, each marked with one leading space, a hyphen, a space.
- [ ] No blank lines between bullets.
- [ ] No headers, bold, italics, tables, code fences, links or emoji.
- [ ] Zero characters above U+007F, proved by script and not by `grep`.

### Main outcome

- [ ] One paragraph, no line breaks inside it.
- [ ] Names ProfitsX as the day's centre of gravity, not a run through all four bullets (`M1`).
- [ ] Carries the feeling he gave: exciting, coming together, drafting stage done (`M2`).
- [ ] Keeps the honest note on pace: slower today, less AI help (`M3`). Dropping or softening this fails the case.
- [ ] Closes on tomorrow and the AI colleagues (`M4`).

### Bullets

- [ ] Order is ProfitsX Homepage, Moving Scrubs, Growth Engine, kitchen mockup.
- [ ] Each of the first three opens by naming its workstream.
- [ ] The separator after the workstream name is not standardised across all four (`B2`).
- [ ] Bullet 1 says the homepage is not done and names what unblocks it (`B3`).
- [ ] Bullet 1 keeps the reason homepage came first (`B4`).
- [ ] Bullet 2 keeps the short declarative run: webinars, GHL login, resources reported as separate sentences, not merged into a list (`B5`).
- [ ] Bullet 4 stays short. One sentence is correct here (`B6`).

### Voice

- [ ] First person throughout, `we` for the work and `I` for himself (`V3`).
- [ ] Contractions intact (`V4`).
- [ ] `GHL` capitalised, `webflow` lowercase, `Homepage` capitalised (`V5`).
- [ ] `ALL` capitalised, once (`V6`).

### Honesty

- [ ] No fact in the output that is absent from the input.
- [ ] No number anywhere. The input has none.
- [ ] Nothing in progress reported as done.

## Known acceptable variation

- `MovingScrubs` and `Moving Scrubs` are both correct. The specimen uses both in one report.
- Sentence wording inside a bullet may differ. Facts, order and register may not.
- The order line under the report is expected and is not part of the report.

## Automatic fail

- A fifth bullet.
- A completion the input did not report.
- Merging the webinars, GHL login and resources sentences.
- Any em dash or en dash.
