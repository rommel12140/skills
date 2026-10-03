# Evals

Six cases.
Each holds an input and what a correct pass must produce.

These exist to answer one question: did editing the skill make it better or quietly worse.

| Case | Input | What it measures |
| :--- | :--- | :--- |
| `01-boatyard-homepage` | A brief for a small wooden-boat builder's homepage, with real assets listed | The full one-pass build: argument, inventory, sequence, briefs, wireframes, motion states, acceptance. No preset section count, no habit bands. |
| `02-workshop-booking-components` | A component request for a booking flow | The component method: recognisable buttons, layout-matched skeletons, submit-time validation, state contract, 44 px targets. |
| `03-planted-defaults` | A draft page plan carrying planted failures | Recall. Every planted gate ID must fail. |
| `04-false-attribution` | A request to state what Awwwards requires | That recommendations are never attributed to Awwwards or a studio (`W13`). |
| `05-missing-evidence` | A brief that asks for numbers and testimonials it cannot support | That gaps become dependencies and nothing is fabricated (`W7`). |
| `06-plain-structure-passes` | A sound plan that uses familiar structures | False positives. No gate may fail for plainness or lack of novelty. |

Cases 03 and 06 matter most.
03 proves the gates catch what they claim to catch.
06 proves the skill does not demand novelty for its own sake: a comparison table, plain paragraphs and ordinary controls are valid answers when they fit, and a skill that marks them down will push builds toward ornament.

## Running a case

There is no test runner.
A run is an agent pass over `input.md` with the `awwwards-build` skill loaded, compared against `expected.md`.

Cases 01 and 02 are generation cases.
Without a browser the agent cannot judge render-required gates; a correct run reports them as unchecked, and a run that reports them as passed fails the case.

A runner before we know the skill is useful would be machinery ahead of need.
If the case set grows past a handful, revisit that.

## Grading

| Result | Meaning |
| :--- | :--- |
| Pass | Every "must" in `expected.md` holds and no "must not" occurs |
| Recall miss | A planted gate ID did not fail (case 03) |
| False positive | A gate failed that the case does not expect (case 06 especially) |
| Attribution error | A recommendation was presented as an Awwwards rule or a studio's method |
| Fabrication | A number, client, testimonial or capability appeared that the input does not supply |

Fabrication and attribution errors fail a run outright, whatever else it got right.

## Dry runs at creation

Cases 02, 03 and 06 were run once each by a fresh agent with only the skill loaded, before the first commit.
02 declined all three overruled requests and built the alternatives.
03 failed every planted gate.
06 failed no structure or novelty gate on either run; each run found specification gaps in the plan itself, which were fixed in the input.
