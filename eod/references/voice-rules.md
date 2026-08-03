# Voice rules

Every rule here was derived from `specimen.md` or from the owner's standing writing rules.
Each has a stable ID so a finding can be named.

Severity is the same three levels the other skills in this repo use.

| Level | Meaning | Action |
| :--- | :--- | :--- |
| P0 | Breaks the format or states something untrue | Never ship |
| P1 | Reads as somebody else's writing | Fix before output |
| P2 | Cosmetic drift | Fix when cheap |

---

## F - Format

### F1 - Date line - P0

The first line is `EOD for today M/D/YY`.
Month and day unpadded, year two digits.
`EOD for today 7/30/26`, not `07/30/2026`, not `2026-07-30`, not `Thursday, July 30`.
One blank line follows it.

### F2 - Bullet marker - P0

Every bullet is one leading space, a hyphen, one space: ` - `.
Not a bare `-` at column zero, not `*`, not a bullet character, not `1.`, not an indented sublist.
No blank lines between bullets.

### F3 - At most four bullets, never padded - P0

One bullet per priority, in priority order, most important first.
Four is the ceiling, not the target.
Two reported priorities produce two bullets.
Inventing a fourth to reach four is fabrication, which is `H1`.

If more than four things happened, fold the smaller ones into the bullet they belong under, or leave them out and say so outside the report.

### F4 - Plain text only - P0

No markdown headers, no bold, no italics, no tables, no code fences, no emoji, no links.
The report pastes into a chat window unchanged.
Anything that renders differently in a chat window than in a file is a defect.

### F5 - Structure - P0

Date line, blank line, one main-outcome paragraph, blank line, then the bullets.
Nothing else. No title, no sign-off, no "let me know if you want changes" inside the report.

---

## M - Main outcome

### M1 - Not a summary of the bullets - P0

The paragraph names the day's centre of gravity and says how it went.
It is allowed to mention a workstream the bullets also cover, but it must not restate each bullet in order.
If the paragraph can be reconstructed by shortening the bullets, rewrite it.

### M2 - Carries feeling - P1

The specimen opens `Exciting, everything's coming together`.
The paragraph says how the day felt, in his words, when he gave a signal for it.
Do not manufacture a feeling he did not express. Flat is better than invented.

### M3 - Honest about pace - P0

If he reported the day was slow, blocked, or short, that stays in.
`A little slower today with less AI help`.
Never soften it, never drop it, never turn it into an achievement.

### M4 - Closes on tomorrow - P1

The last sentence points at the next day.
`Tomorrow, I have ALL my AI colleagues, which I can delegate like importing to webflow, and stuff`.

### M5 - One paragraph - P1

Roughly four to six sentences. The specimen has six, in 55 words, so they are short.
No line breaks inside it.

---

## B - Bullets

### B1 - Opens by naming the workstream - P0

`ProfitsX Homepage.` / `Moving Scrubs:` / `Growth Engine 3D animation.`
A bullet that opens with a bare verb is allowed when the specimen does it (`Prepared the info and brand settings for the kitchen mockup`), but it is the exception, not the pattern.

### B2 - Do not standardise the separator - P1

The specimen uses a full stop after some names and a colon after others.
Vary it the way he does. Making every bullet use a colon is a finding.

### B3 - Unfinished stated as unfinished - P0

Work in progress is reported in progress, with what unblocks it.
`Not yet done but tomorrow, we'll be able to import it to webflow`.
Never round an in-progress item up to done.

### B4 - Reason included where it explains a choice - P1

When he said why something got the attention, keep it.
`Homepage is being focused right now because once this is done, the other pages will be easier since we now have the full concept`.
Do not invent a rationale he did not give.

### B5 - Short declarative runs stay - P1

`Webinars are done. GHL Login is done. Resources is done.`
Do not merge these into one list sentence. The repetition is the point.

### B6 - Length follows the day - P2

One sentence is a complete bullet when one sentence is what happened.
Do not top up a thin bullet to match a fat one.

---

## V - Voice

### V1 - No em dashes or en dashes - P0

Never emit an em dash (U+2014) or an en dash (U+2013), in the report or anywhere else.
Use a period, a comma, a colon, parentheses, or a plain hyphen `-`.

Verify by counting non-ASCII characters with a script.
`grep -o` returns zero on these characters even when the text is full of them, so `grep` is not evidence.

```
python3 -c "import sys;t=open(sys.argv[1],encoding='utf-8').read();print([(i,c,hex(ord(c))) for i,c in enumerate(t) if ord(c)>127])" FILE
```

An empty list is the pass condition.

### V2 - Banned constructions - P0

None of these, in the report or in the commentary around it:

- "it's not just X, it's Y", "X isn't just Y"
- "in today's fast-paced world", "in an era where", "let's dive in"
- unlock, unleash, elevate, empower, supercharge, seamless, robust, cutting-edge, game-changer, revolutionize, delve, leverage used as a verb
- tricolon padding: "faster, smarter, better"
- rhetorical-question openers: "Ever wondered why...?"
- a closing summary that restates the report back to the reader
- hedged nothing-claims: "helps you do more of what matters"

### V3 - First person, his pronouns - P0

`we` for the work, `I` for himself.
No third person, no passive rewrite that removes him from his own day.

### V4 - Contractions and spoken register - P1

`everything's`, `we'll`, `I'm gonna`, `and stuff`.
This is dictated speech lightly tidied.
Raising it into written prose is a finding, not an improvement.

### V5 - His spelling of names - P0

`ProfitsX`, `MovingScrubs` or `Moving Scrubs`, `GHL`, `webflow`, `Homepage`.
Spell each name the way he said it that day.
Do not normalise a name across the report, and do not correct his capitalisation.

### V6 - Emphasis by capitals, sparingly - P2

`ALL my AI colleagues`.
At most once per report, and only where he stressed it.

---

## H - Honesty

### H1 - Never invent - P0

No work, no number, no completion, no rationale, and no feeling that was not reported.
An EOD is a factual record of one person's day.

If evidence mode surfaced work he did not mention, offer it outside the report and let him decide.
Never place it in a bullet on your own.

### H2 - Numbers only as reported - P0

Any figure in the report came from him, or from evidence he accepted.
The specimen cites zero numbers, so there is no house expectation of them.
