# Evals

Four cases.
Each holds an input and what a correct pass must produce.

These exist to answer one question: did editing the skill move it closer to the specimen or quietly further from it.

| Case | Input | What it measures |
| :--- | :--- | :--- |
| `01-rough-dictated-day` | Rough notes for 30 July 2026, out of order | Fidelity. The output must land on `references/specimen.md`. |
| `02-two-priorities` | A day with two workstreams | That the skill does not pad to four bullets. |
| `03-unfinished-work` | A day where the headline item did not land | That in-progress work is reported in progress. |
| `04-dash-and-banned-word` | A draft report carrying a planted em dash and a planted banned word | That the self-check catches both. |

Case 01 is the one that matters most.
It is the only case where the correct answer already exists and was written by the owner, so it is the only case that can measure fidelity rather than plausibility.

## Running a case

There is no test runner.
A run is an agent pass over `input.md` with the `eod` skill loaded, compared against `expected-output.md`.

A runner before we know the skill is useful would be machinery ahead of need.
If the case set grows past a handful, revisit that.

## Grading

An output is not graded on being word-identical to the expected file.
Two writers given the same notes produce different sentences, and that is not a failure.

| Result | Meaning |
| :--- | :--- |
| Pass | Every rule in the case's `expected-output.md` holds |
| Format break | A P0 in the `F` family: wrong date shape, wrong bullet marker, headers, bold, emoji |
| Fabrication | A claim, number or completion not present in the input. Fails the case outright. |
| Padding | More bullets than the input has priorities |
| Voice drift | Register raised, contractions removed, declarative runs merged, separators standardised |
| Missed violation | Case 04 only: a planted dash or banned word survived to output |

Fabrication and format breaks are not equally bad.
A format break is visible and gets fixed in one pass.
A fabrication goes out under his name to people who will act on it.

## Case 01 note

The expected output is the specimen itself, so this case doubles as a check that the rules in `references/voice-rules.md` still describe the thing they were derived from.

Do not grade case 01 on word-for-word equality.
Grade it on the checklist in its `expected-output.md`: every fact present, no fact added, the format exact, and the register still spoken rather than written.

If a run of case 01 produces something the owner would not have written, the rules are wrong, not the specimen.

## Case 04 note

The dash check must be run with a script that counts characters above U+007F.
A `grep -o` for an em dash returns zero matches on files that are full of them, so a case-04 pass proved by `grep` is not a pass.
