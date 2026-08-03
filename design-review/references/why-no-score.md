# Why this skill reports no score

Several published anti-slop skills compute a numeric score and map it to a risk band.
This skill deliberately does not.

## The evidence

The reasoning comes from the writing side of this problem, where someone actually measured it.

`conorbronsdon/avoid-ai-writing` maintains a detector, a corpus of 875 human and 779 machine-generated paragraphs, and a `PROOF.md` reporting how its own detector performs.

| Measure | Result |
| :--- | :--- |
| Document-level ROC-AUC | 0.623 |
| Paragraph-level ROC-AUC | 0.501 pooled |
| False-positive rate at threshold 5 | 4.2% (95% CI 3.1 to 5.8) |

An ROC-AUC of 0.5 is chance.
The project's own conclusion is that "the composite score cannot reliably separate machine text from human text."

No equivalent measurement exists for design.
Nobody has built a corpus of human-designed and machine-designed pages and tested a scoring rule against it.
So a design slop score is in a worse position than a copy slop score: it is unvalidated rather than validated-and-failed.

## What follows

A number carries authority.
Presenting an unvalidated one invites two failures:

1. Treating a low score as evidence the design is good.
2. Treating a high score as evidence it was machine-generated.

Neither inference is supported.

The individual tells are still real.
A purple-to-blue gradient behind Inter over three icon-topped cards is a weak design decision on its own merits, independent of who or what made it.
That argument survives without a score, and it is the argument this skill makes.

## What this skill reports instead

A list of findings, each with an ID, the evidence, and a fix for the stack in use.
The closing line is a count by severity, which counts findings rather than judging the design as a whole.

A reviewer can disagree with any single finding on its merits.
That is the intended interaction.
