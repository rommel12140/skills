# Evals

Eight cases.
Each holds an input and what a correct pass must produce.

These exist to answer one question: did editing the skill move it closer to the corpus or quietly further from it.

| Case | Input | What it measures |
| :--- | :--- | :--- |
| `01-rough-dictated-day` | Notes for 30 July 2026, out of order, in his phrasing | Phrasing fidelity. The output must land on specimen A in `references/corpus.md`, wording included. |
| `02-two-priorities` | A day with two workstreams | That the skill does not pad to four bullets. |
| `03-unfinished-work` | A day where the headline item did not land | That in-progress work is reported in progress. |
| `04-dash-and-banned-word` | A draft report carrying a planted em dash and a planted banned word | That the self-check catches both. |
| `05-rough-stays-rough` | Deliberately rough, ungrammatical notes | That the skill does not quietly edit him. |
| `06-greeting-hyphens-and-three-bullets` | Notes for 28 July 2026, in his phrasing | Fidelity on a second shape. Greeting, trailing colon, leading whitespace, hyphen separators, three bullets, no tomorrow line. |
| `07-url-and-defended-detour` | Notes for 29 July 2026, in his phrasing | Fidelity on a third shape. Greeting on the date line, inline unlabelled URL, a defended detour, `++` and `+` constructions. |
| `08-boss-not-a-developer` | A Friday's notes, real work described in developer process terms, plus the weekly planning | That the report is written for his boss. Developer process comes out (`R1`) and the recurring planning never reaches a bullet (`R2`). |

Cases 01, 05, 06, 07 and 08 are the ones that matter most.

01, 06 and 07 are the three cases whose correct answers already exist and were written by the owner, so they are the only ones that measure fidelity against a real target. They are deliberately three different shapes: most of what 01 would teach you to enforce, 06 or 07 contradicts. Run all three after any change to `voice-rules.md`.

05 has no authored answer, which is the situation the skill is in every actual evening, and it checks that `W1` holds anyway.

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
| Normalising | Something he varies was made consistent: a greeting added or dropped, date punctuation regularised, blank lines inserted, project-name capitalisation reconciled. Fails the case. |
| Missed violation | Case 04 only: a planted dash or banned word survived to output |
| Written for an engineer | Case 08 mainly: a sentence names how the work was carried out rather than what job is now done. Fails the case (`R1`). |
| Recurring work promoted | Case 08 mainly: something on a fixed schedule took a bullet. Fails the case (`R2`). |

These are not equally bad.
A format break is visible and gets fixed in one pass.
A fabrication goes out under his name to people who will act on it.
A re-wording is the one that is hardest to see, because every instance of it looks like an improvement.

## Case 01 note

The expected output is specimen A itself, so this case doubles as a check that the rules in `references/voice-rules.md` still describe the thing they were derived from.

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

## Cases 06 and 07 note

These exist because the first two versions of this skill were built on 30 July alone, and several rules turned out to be facts about that one day rather than facts about him.

They are the guard against that happening again. A rule that has quietly become a requirement rather than a preference fails here before it reaches him.

Between them they are the only coverage of `G1`, `W2`, `B7`, `B8`, `V7` and `V8`, and the only cases where the correct report has no closing line about tomorrow and states no feeling.

## Case 08 note

This is the only case that covers `R1` and `R2`, the two rules from his ruling of 4 August 2026, and it runs both in one pass.

The other seven cases all measure whether the skill sounds like him. This one measures whether the report is any use to the person who reads it.
A run can pass every one of the other seven and still fail this one, by reporting the day accurately to an engineer.

The two rules pull against each other and against `W1`, which is why they are graded together rather than in separate cases.
`R2` deletes something he actually reported. `R1` rewrites something he actually said, in a skill whose first rule is that his wording is not rewritten.
Grade the restatements for whether the mechanic came out and nothing else moved with it.

The common failure is getting one rule and missing the other: dropping the planning but keeping `merged`, or restating everything cleanly and still giving the planning a bullet because it took most of the afternoon.

## Case 04 note

The dash check must be run with a script that counts characters above U+007F.
A `grep -o` for an em dash returns zero matches on files that are full of them, so a case-04 pass proved by `grep` is not a pass.
