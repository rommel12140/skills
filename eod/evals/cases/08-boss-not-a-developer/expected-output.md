# Case 08 - expected output

Developer process in, jobs and their state out.
The weekly planning does not appear at all.

## Reference output

```
EOD for today 8/14/26

Insight detail page. Pretty happy, it's all coming from GHL now. Tomorrow, gonna keep testing on the widget.

 - Insight detail page is done. GHL has everything the pages need, including reading time.
 - Worked out how much of the page Webflow can handle on its own, turns out most of it, so nothing extra is needed.
 - Same thing on the widget is still being tested, gonna keep testing on the widget tomorrow.
 - Moving scrubs, newsletter popup copy is updated. Done.
```

## What the input said and what the report says

Left is his note. Right is what reaches his boss. The rule is `R1`.

| His note | What must reach the report |
| :--- | :--- |
| merged the insight detail page today | Insight detail page is done |
| 27% of the stylesheet survives so no external stylesheet needed | Worked out how much of the page Webflow can handle on its own, turns out most of it |
| the Embed version is in validation | Same thing on the widget is still being tested |
| GHLs read API omits rawHTML so the body comes from the published site | GHL has everything the pages need |
| planned next week with the team, friday and sunday like always | nothing at all |

## Automatic fail

| If this survives to output | Rule |
| :--- | :--- |
| merged, merge | `R1` |
| stylesheet, CSS, external stylesheet | `R1` |
| validation, in validation | `R1` |
| API, read API, rawHTML, endpoint | `R1` |
| Embed version, as the name of a build target | `R1` |
| a bullet about planning next week | `R2` |
| the planning named as a priority anywhere in the report | `R2` |
| `27%` | `R1`, see below |

## Checklist

### The reader (`R1`)

- [ ] Zero words from the developer-process list in `references/voice-rules.md`, checked by sense and not only by string.
- [ ] Every bullet names a thing and says what state it is in: done, in progress, or tomorrow.
- [ ] Product and tool names survive untouched: GHL, Webflow, the widget, the newsletter popup, Moving scrubs, the insight detail page.
- [ ] The insight page is reported as done. `merged` is how it got there and is not the report.
- [ ] The stylesheet audit reaches the report as what it got him, not as what he measured.
- [ ] `published site` and `live` are allowed if he used them. They are what his boss can see. See `R1` on sense versus string.

### The number

- [ ] `27%` does not appear.

`H2` says numbers ship only as reported, which permits a number. `R1` removes this one, because 27% measures a stylesheet and a stylesheet is not a job his boss tracks. The finding his boss needs is that most of the page is handled without anything extra.

A number that measures a job rather than a mechanic still ships. `two mockups` in specimen C is that kind of number and would survive here.

### Recurring work (`R2`)

- [ ] No bullet for the weekly planning.
- [ ] The planning is not folded into another bullet as a clause either.
- [ ] `ate a chunk of the afternoon` does not rescue it. Time spent is not state changed.
- [ ] Nothing else was dropped along with it. The other four items all reach the report.

### Wording (`W1`), on everything `R1` did not move

| Must appear | Fails the case |
| :--- | :--- |
| Pretty happy, it's all coming from GHL now | I am pleased that the content now comes from GHL |
| gonna keep testing on the widget tomorrow | will continue testing on the widget tomorrow |
| turns out most of it | and it turns out that most of it is |
| Moving scrubs | Moving Scrubs |

- [ ] `its` to `it's` is the only apostrophe restored, and it pulls no other change with it.
- [ ] `GHLs` to `GHL's` is not needed anywhere, because the possessive belonged to the sentence `R1` removed.
- [ ] `Moving scrubs` keeps his lowercase `s` (`V5`).
- [ ] The restatements under `R1` move the mechanic and nothing else. His register, contractions and fragments stay.

### Format and assembly

- [ ] Date line is `EOD for today 8/14/26`. His note said `eod 8/14`, so the year is his year and the rest is the fixed wording (`F1`).
- [ ] No greeting, since his notes carry none (`G1`).
- [ ] The 30 July shape: blank line after the date line, blank line before the first bullet (`F5`).
- [ ] Four bullets, which is the ceiling and here it is also the count of things that moved (`F3`).
- [ ] The widget is reported unfinished (`B3`).
- [ ] Zero characters above U+007F (`V1`).

## Judgement calls, either way passes

The stylesheet audit may be its own bullet, as above, or folded into the insight page bullet. He said `did the stylesheet audit too`, and `too` reads as secondary.

`the body comes from the published site` may be kept or dropped. `published site` is his boss's world and passes `R1`. Dropping it and letting `GHL has everything the pages need` carry the point also passes.

The order of the first two bullets may swap.

What fails either way is a sentence that explains how any of it was carried out.

## Why this case exists

It is the only case that runs both rules from his 4 August 2026 ruling in one pass, and the two rules pull in different directions.

`R2` deletes something he actually reported. `R1` rewrites something he actually said, in a file whose first rule is that his wording is not rewritten.

A run that gets one and misses the other is the common failure. A run that writes an accurate engineering summary of the day fails outright, however well it reads.
