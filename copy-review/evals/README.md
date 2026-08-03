# Evals

Three cases.
Each holds an input and the findings a correct pass must produce.

| Case | Input | What it measures |
| :--- | :--- | :--- |
| `01-saas-landing-slop` | Copy carrying planted tells | Recall. Every planted ID must be found. |
| `02-clean-technical-prose` | Prose that is plain and correct | False positives. Nothing above P2 may be reported. |
| `03-captain-voice-sample` | Real writing from the captain's own projects | That the catalog does not flag the voice it is meant to protect. |

Cases 02 and 03 matter more than case 01.

The measured false-positive rate on published pattern sets of this kind sits around 4%, and it is uneven across registers.
Technical documentation trips these catalogs more often than marketing copy does, because precise technical prose legitimately repeats structure and vocabulary.
Case 02 exists for exactly that reason.

## Case 03 note

Source the input from prose the captain actually wrote and shipped.
Do not write a pastiche.
A pastiche tests the catalog against an imitation of the voice, which is the wrong target.

If the catalog produces findings above P2 on case 03, the catalog is wrong.
The voice is the specification here, not the thing being corrected.

## Running a case

An agent pass over the input in audit mode, output compared to `expected-findings.md`.
No test runner.

## Grading

| Result | Meaning |
| :--- | :--- |
| Pass | Every expected ID found, no unexpected finding above P2 |
| Recall miss | An expected ID was not found |
| False positive | A finding above P2 the case does not expect |
| No rewrite | The ID was found but no replacement was proposed, which the output contract forbids |
