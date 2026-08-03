# Why this skill reports no score

Several published anti-slop skills compute a numeric score and map it to a risk band.
This skill deliberately does not, and the reason is a measurement one of those projects published about itself.

## The evidence

`conorbronsdon/avoid-ai-writing` maintains a detector, a test corpus of 875 human and 779 machine-generated paragraphs, and a `PROOF.md` reporting how the detector performs.

Its own numbers:

| Measure | Result |
| :--- | :--- |
| Document-level ROC-AUC | 0.623 |
| Paragraph-level ROC-AUC | 0.501 pooled |
| False-positive rate at threshold 5 | 4.2% (95% CI 3.1 to 5.8) |

An ROC-AUC of 0.5 is chance.
The project's own summary of the paragraph-level figure is "a coin flip", and its stated conclusion is that "the composite score cannot reliably separate machine text from human text."

The authors also decline to publish the false-positive rate as a headline claim, because the corpus lacks register diversity and its machine samples come only from ChatGPT between 2022 and 2024.

## What follows

A score would be a number with no demonstrated predictive value, presented with the authority that numbers carry.
It would invite two failures:

1. Treating a low score as evidence the writing is good, when the measure cannot support that.
2. Treating a high score as evidence the writing is machine-generated, when it cannot support that either.

The underlying patterns are still real and still worth removing.
They are worth removing because each one, individually, is weak writing.
That argument survives without the score, and it is the argument this skill makes.

## What this skill reports instead

A list of findings, each naming the exact text, the reason, and a proposed replacement.
The closing line is a count by severity, which is a count of findings and not a judgement about the text as a whole.

A reviewer can disagree with any single finding on its merits.
That is the intended interaction.
