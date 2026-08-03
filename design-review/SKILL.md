---
name: design-review
description: >
  Audit or generate interface work against a catalog of AI-generated design
  tells. Use when building or reviewing any page, component, slide deck, or
  artifact that a person will look at. Reports findings by ID and severity
  with a fix for the stack in use. Never reports a score.
---

# design-review

## Two modes

**Constraint** runs before building.
The catalog acts as rules on what gets made.

**Audit** runs over existing work on request.
It produces findings.

State which mode is running in the first line of output.

## Procedure

1. Read the project's `voice.md`, in particular the "Visual language" section.
   If it is absent, say so.
   Gate `X1` cannot run without it and must be reported as skipped rather than guessed.
2. Load `references/design-tells.md`.
3. Identify the stack: plain HTML and CSS, React with Tailwind, or Webflow.
   The fix column depends on it.
4. Walk P0 gates first, then P1, then P2.
5. For any gate marked `render: required`, capture the page with `chrome-devtools-axi` and judge the pixels.
   Do not answer a render-required gate from source.
   If the page cannot be rendered, report those gates as unchecked rather than passed.
6. Report.
   Do not compute a score.
   See `references/why-no-score.md` if asked why.

## Render-required gates

Ten of the thirty-one gates cannot be answered from source: `C3`, `K2`, `L1`, `L4`, `M2`, `M3`, `IM1`, `A1`, `A3`, `X1`, `X3`.

Capture at 1280x800 before any wider viewport.
A hero that fits at 1440x900 and fails at 1280x800 is a real failure, because the smaller size is the common laptop.

## Output contract

One finding per line item:

```
<ID> · <severity> · <file:line or selector>
Found:  <the evidence, quoted from source or described from the render>
Why:    <one sentence>
Fix:    <the fix for the stack in use, not all three>
```

Rules on output:

- Every finding names a fix.
  A finding with no fix is an opinion and must be dropped.
- Quote the evidence.
  A finding a reviewer cannot locate is not actionable.
- Report skipped gates explicitly, with the reason.
  Silence must never be confused with a pass.
- Close with a count by severity.
  A count of findings, not a judgement about the design.

## Re-audit

On a second pass, report by ID against the first pass:
resolved, still open, or newly introduced.
This is what the stable IDs are for.
Do not re-argue a finding the first pass already made.

## What this skill does not do

It does not decide whether a design is good.
It decides whether a design defaulted.
Those overlap but are not the same question, and the second one is the one that can be checked.
