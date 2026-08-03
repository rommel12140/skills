# Evals

Five cases.
Each holds an input and what a correct pass must produce.

These exist to answer one question: did editing the skill move it closer to the specimen or quietly further from it.

| Case | Input | What it measures |
| :--- | :--- | :--- |
| `01-rough-dictated-day` | Notes for 30 July 2026, out of order, in his phrasing | Phrasing fidelity. The output must land on `references/specimen.md`, wording included. |
| `02-two-priorities` | A day with two workstreams | That the skill does not pad to four bullets. |
| `03-unfinished-work` | A day where the headline item did not land | That in-progress work is reported in progress. |
| `04-dash-and-banned-word` | A draft report carrying a planted em dash and a planted banned word | That the self-check catches both. |
| `05-rough-stays-rough` | Deliberately rough, ungrammatical notes | That the skill does not quietly edit him. |

Cases 01 and 05 are the ones that matter most, and they test the same rule from two sides.

Case 01 is the only case whose correct answer already exists and was written by the owner, so it is the only one that can measure fidelity against a real target.
Case 05 has no authored answer, which is the situation the skill is in every actual evening, and it checks that `W1` holds anyway.

## Running a case

There is no test runner.
A run is an agent pass over `input.md` with the `eod` skill loaded, compared against `expected-output.md`.

A runner before we know the skill is useful would be machinery ahead of need.
If the case set grows past a handful, revisit that.

## Grading

Each case's `expected-output.md` names what must hold.
Cases 01 and 05 additionally carry a table of exact phrasings, and those are graded literally: the left column appears in the output or the run fails.

| Result | Meaning |
| :--- | :--- |
| Pass | Every rule in the case's `expected-output.md` holds |
| Re-wording | A sentence came out grammatically better than it went in. Fails the case outright (`W1`). |
| Fabrication | A claim, number or completion not present in the input. Fails the case outright. |
| Format break | A P0 in the `F` family: wrong date shape, wrong bullet marker, headers, bold, emoji |
| Padding | More bullets than the input has priorities |
| Voice drift | Register raised, contractions changed, declarative runs merged, separators standardised |
| Missed violation | Case 04 only: a planted dash or banned word survived to output |

These are not equally bad.
A format break is visible and gets fixed in one pass.
A fabrication goes out under his name to people who will act on it.
A re-wording is the one that is hardest to see, because every instance of it looks like an improvement.

## Case 01 note

The expected output is the specimen itself, so this case doubles as a check that the rules in `references/voice-rules.md` still describe the thing they were derived from.

Grade the six-row phrasing table first. If a row fails, the run fails, whatever else it got right.

An earlier version of this case allowed the output to carry the notes' own wording rather than his, and graded that as acceptable variation.
The captain ruled against it on 4 August 2026: "The roughness is my voice. Follow my voice, and making it smoother is kinda like feeling AI sloppish."
The allowance was the failure, so the case was inverted to catch it.

If a run of case 01 produces something the owner would not have written, the rules are wrong, not the specimen.

## Case 05 note

There is no authored answer for this day, which is the point.
The reference output in `expected-output.md` is one correct assembly, not the only one, but its table of phrasings is not negotiable.

The temptation this case exists to catch: a run that reads the notes, understands the day perfectly, and reports it in clean prose.
That run is wrong, and it will look better than a passing run to anyone grading on writing quality alone.

## Case 04 note

The dash check must be run with a script that counts characters above U+007F.
A `grep -o` for an em dash returns zero matches on files that are full of them, so a case-04 pass proved by `grep` is not a pass.
