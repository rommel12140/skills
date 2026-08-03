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

## Corrected report

```
EOD for today 8/6/26

ProfitsX homepage import. Finished it, all the sections are in webflow now. MovingScrubs, added the utm passthrough on the two remaining forms. Tomorrow I'm on the pricing page.

 - ProfitsX Homepage. Import is done, all sections are in webflow.
 - MovingScrubs: Added the utm passthrough on the two remaining forms.
```

## Grading

| Result | Meaning |
| :--- | :--- |
| Pass | All findings above reported, corrected report produced, zero characters above U+007F in the correction |
| Missed violation | Any planted dash, emoji or banned word survives |
| False proof | The dash check was run with `grep` rather than a character count |
| Worst case | The two invented bullets survive into the correction |
