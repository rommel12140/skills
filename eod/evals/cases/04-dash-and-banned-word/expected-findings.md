# Case 04 - expected findings

Every finding below must be reported.
A pass also requires the corrected report at the end.

## Findings

### V1 - em dashes - P0

Two of them: after "a productive one" in the main outcome, and after "Import complete" on the first bullet.
Replace each with a period, a comma, a colon, parentheses or a plain hyphen.

The check must be run with a script that counts characters above U+007F:

```
python3 -c "import sys;t=open(sys.argv[1],encoding='utf-8').read();print([(i,c,hex(ord(c))) for i,c in enumerate(t) if ord(c)>127])" FILE
```

A run that reports "no dashes found" on the strength of `grep -o` fails the case even if the rest of the audit is right.
`grep -o` returns zero matches on these characters. The emoji on the first bullet is caught by the same script and is a separate finding.

### V2 - banned words - P0

- `seamless`
- `empower`
- `faster, smarter, better`, tricolon padding
- `It's not just an import, it's the foundation`, the banned "not just X, it's Y" construction
- The closing paragraph, which restates the report back to the reader

### F1 - date line - P0

`EOD for today 08/06/2026` is padded and four-digit.
Correct: `EOD for today 8/6/26`.

### F4 - formatting - P0

- Bold on two bullet names.
- One emoji.
- `Webflow` capitalised. He writes `webflow`, so this is also `V5`.

### F2 - bullet marker - P0

Bullets start at column zero. They need the leading space: ` - `.

### F3 and H1 - invented bullets - P0

He reported two workstreams. The draft has four.
`Growth Engine animation: polishing continues` and `Kitchen mockup: awaiting client feedback` are fabrications, padded in to reach four.
This is the most serious finding in the case, more serious than the dashes, because it goes out under his name as fact.

### M1 - main outcome is a summary of the bullets - P0

The paragraph restates the two bullets and adds nothing about how the day went or what tomorrow holds.
It also drops what he actually said about tomorrow: the pricing page.

### V4 - register raised - P1

"a productive one", "Our seamless workflow continues to", "the foundation for everything that follows".
None of this is his voice. It is written prose over dictated speech.

### W1 - his wording replaced - P0

Set the draft against what he actually said and every sentence has been rewritten.

| He said | The draft says |
| :--- | :--- |
| profitsx homepage import finished, all sections in webflow now | Import complete. All sections are now live in Webflow. |
| added the utm passthrough on the two remaining forms | Added UTM passthrough to the two remaining forms. |
| tomorrow i'm on the pricing page | dropped entirely |

`live in Webflow` also invents a claim: he said the sections are in webflow, not that anything is live.

## Corrected report

```
EOD for today 8/6/26

ProfitsX homepage. Import finished, all sections in webflow now. MovingScrubs, added the utm passthrough on the two remaining forms. Tomorrow I'm on the pricing page.

 - ProfitsX Homepage: Import finished, all sections in webflow now.
 - MovingScrubs. Added the utm passthrough on the two remaining forms.
```

The notes for this day are three short lines, so the main outcome and the bullets necessarily overlap.
That is the correct outcome. `M1` asks the paragraph not to be a summary of the bullets, but the fix for a thin day is not to invent colour to fill the paragraph out. `H1` outranks `M1`.

`utm` stays lowercase because that is how he wrote it.

## Grading

| Result | Meaning |
| :--- | :--- |
| Pass | All findings above reported, corrected report produced, zero characters above U+007F in the correction |
| Missed violation | Any planted dash, emoji or banned word survives |
| False proof | The dash check was run with `grep` rather than a character count |
| Re-worded correction | The correction is clean prose rather than his sentences. Fixing the dashes and keeping the editor's voice fails the case. |
| Worst case | The two invented bullets survive into the correction |
