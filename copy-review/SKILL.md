---
name: copy-review
description: >
  Write or review prose against a catalog of AI-writing tells and the project's
  own voice. Use when drafting or editing any copy a person will read: landing
  pages, marketing copy, documentation, READMEs, emails, UI microcopy, release
  notes. Reports findings by ID with a proposed rewrite. Never reports a score.
---

# copy-review

## Two modes

**Constraint** runs before drafting.
The catalog acts as a set of rules on what gets written.

**Audit** runs over existing text on request.
It produces findings.

State which mode is running in the first line of output.

## Procedure

1. Read the project's `voice.md`.
   If it is absent, say so in the output and continue on the global catalog alone.
   Do not invent a voice.
2. Load `references/copy-tells.md`.
3. Walk P0 entries first, then P1, then P2.
4. Check every number in the text against the allowed figures in `voice.md`.
   Anything unlisted is an `H1` finding.
5. Apply the competitor test (`VO1`) last, to the piece as a whole.
6. Report.
   Do not compute a score.
   See `references/why-no-score.md` if asked why.

In constraint mode, steps 3 to 5 apply to what you are about to write rather than to text that already exists.

## Exemptions

A pattern inside any of these is not a finding:

- Fenced code blocks and inline code.
- Quoted source material, including quoted examples of bad writing.
- Tables and blockquotes.
- Proper nouns and product names.
- A term that `voice.md` lists under "Words this project uses".

The catalog contains examples of the patterns it bans.
Those examples are quoted material and are exempt.

## Output contract

One finding per line item:

```
<ID> · <severity> · <location>
Found:   "<the exact text>"
Why:     <one sentence>
Instead: "<the proposed rewrite>"
```

Rules on output:

- Every finding carries a proposed rewrite.
  A finding without one is an opinion, and it must be dropped rather than shipped.
- Never rewrite in place without showing the original.
- Where a flagged word is being used correctly, say so and drop the finding.
  The measured false-positive rate on this class of pattern sits around 4% and is uneven across registers, so this will happen regularly and is not a failure.
- Close with a count by severity.
  A count of findings, not a judgement about the text.

## What this skill does not do

It does not judge whether text was written by a machine.
It cannot, and no published tool in this category can.
It judges whether each sentence is doing work.
