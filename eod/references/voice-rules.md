# Voice rules

Every rule here was derived from `corpus.md`, which holds three of his own EODs, or from his standing writing rules.
Each rule has a stable ID so a finding can be named, and a **Support** line naming which specimens back it.

| Specimen | Day |
| :--- | :--- |
| A | 30 July 2026 |
| B | 29 July 2026 |
| C | 28 July 2026 |

## How to read the Support line

- **A, B, C** means all three do it. Enforce it.
- **Two of three** means it is common but not required. Follow it when his notes support it, never impose it.
- **Varies** means the three disagree. Reproduce whatever he did that day and never pick a canonical form. These are the rules most likely to be broken by someone trying to be helpful.
- **One specimen** means it is attested once. Preserve it when it appears; never require it.

A rule supported by one specimen and contradicted by another is a bug in the rule, not an inconsistency in him.
Several rules in the first version of this file were facts about 30 July rather than facts about him, and they are marked below where they were corrected.

## Severity

| Level | Meaning | Action |
| :--- | :--- | :--- |
| P0 | Breaks the format, states something untrue, or rewrites him | Never ship |
| P1 | Reads as somebody else's writing | Fix before output |
| P2 | Cosmetic drift | Fix when cheap |

`W1` outranks every other rule in this file.
Where another rule seems to ask for a smoother sentence, it does not. Read `W1` again.

---

## W - Wording

### W1 - Preserve his wording. The skill assembles and orders, it does not re-word - P0

Support: A, B, C.

This is the first rule in the file because it is the one that gets broken.

His words on it: "The roughness is my voice. Follow my voice, and making it smoother is kinda like feeling AI sloppish."

**What the skill may do**

- Choose which of his notes become which bullet.
- Put the bullets in priority order.
- Drop a duplicate.
- Fix a genuine typo that would confuse a reader.

**What the skill must not do**

- Replace his verb with a more standard one.
- Regularise a tense.
- Complete a sentence fragment.
- Reorder a clause for flow.
- Expand or contract a contraction he chose.
- Drop a trailing "and stuff", "etc.", or "or whatever".
- Swap a dictated word for a tidier synonym.

If a phrase is intelligible, it ships as he said it, whether or not an editor would keep it.

The only wording that may be written fresh is a connective needed to join two of his fragments.
Even then, prefer a connective he already used.

**Worked example**

This is the ruling that produced the rule. Left is what he wrote on 30 July. Right is what a first version of this skill produced from the same day's notes, and every line on the right is a defect.

| He wrote | The skill wrote |
| :--- | :--- |
| Tomorrow, I have ALL my AI colleagues, which I can delegate like importing to webflow, and stuff. | Tomorrow, I have ALL my AI colleagues so I can delegate stuff like the webflow import. |
| Piecing up together to create one Homepage from the fintech, private equity, and other templates. | Pulling one Homepage together out of the fintech template, the private equity one, and some others. |
| noting all the things we've talked about yesterday | noting all the things we talked about yesterday |
| Components are being built now. | Components are being built right now. |
| Conceptualize for a better growth engine with the new inspiration. | Conceptualized a better growth engine off the new inspiration. |
| Prepared the info and brand settings for the kitchen mockup, tomorrow I'm gonna send the mockup. | Prepped the info and brand settings for the kitchen mockup, sending the mockup tomorrow. |

Every entry on the right is grammatically better and every one is less him.

Look at what was actually removed: a trailing "and stuff", a non-standard verb form ("Piecing up together", and "Conceptualize" where standard English wants a past tense), a contraction, a dictated "I'm gonna", and a clause order that reads the way a person talks rather than the way a person edits.

None of those were errors. They were the voice.

**More attested non-standard grammar, from B and C**

Each of these ships exactly as written:

- `it is hard to implement and fix 3D animations in webflow than just html`
- `and other that needs to be wired`
- `Little some help to Ron`
- `Moving scrubs was more finished than I thought`
- `gonna start forming basic wireframe which is already planned out`
- `On which pages are static, which pages are story telling with animations.`
- `Just wanted to make a feel of what to add in webflow.`

Apply this rule from the examples rather than from the description. They are easier to check a draft against than any wording of the principle.

### W2 - His whitespace is his - P0

Support: C, which is the only specimen that has any to preserve.

C opens its main outcome with a leading space, and its third bullet has a double space mid-sentence: `which is already planned out.  Added animations and inspirations for profitsx.`

Neither is tidied. Reproduce the spacing his notes carry.

This does not license inventing whitespace. It means never stripping his.

---

## G - Greeting

### G1 - The greeting is optional and its form varies - P0

Support: varies. A has none, B has `Hey!` folded into the date line, C has `Hey! Good day,` on its own line followed by a blank line.

Never add a greeting he did not use.
Never remove one he did.
Never standardise the form or the placement.

If his notes open with a greeting, it opens the report the same way.

---

## F - Format

### F1 - The date is `M/D/YY`, the punctuation around it is not fixed - P0

Support: A, B, C for the date itself. Varies for everything around it.

The date is always month and day unpadded, year two digits, slashes: `7/30/26`, `7/29/26`, `7/28/26`.
Never ISO, never `07/30/2026`, never a weekday.

The rest of the line is his:

| Specimen | Date line |
| :--- | :--- |
| A | `EOD for today 7/30/26` |
| B | `Hey! EOD for today: 7/29/26` |
| C | `EOD for today 7/28/26:` |

The colon moves and sometimes is not there at all.
Reproduce what he used. Do not invent a canonical form.

The words `EOD for today` appear in all three, so those are fixed.

**Corrected from the first version of this file**, which required `EOD for today M/D/YY` exactly and would have rewritten B and C.

### F2 - Bullet marker - P0

Support: A, B, C. This is one of the few things that never varies.

Every bullet is one leading space, a hyphen, one space: ` - `.
Not a bare `-` at column zero, not `*`, not a bullet character, not `1.`, not an indented sublist.
No blank lines between bullets.

### F3 - At most four bullets, never padded - P0

Support: A and B have 4, C has 3.

One bullet per priority, in priority order, most important first.
Four is the ceiling. Three is attested in C, so it is a normal day and not a short one.

Inventing a bullet to reach four is fabrication, which is `H1`.

If more than four things happened, fold the smaller ones into the bullet they belong under, or leave them out and say so outside the report.

### F4 - Plain text only - P0

Support: A, B, C.

No markdown headers, no bold, no italics, no tables, no code fences, no emoji.
The report pastes into a chat window unchanged.

A bare URL is not a violation. See `B7`.

### F5 - Structure, and the blank lines that are not fixed - P0

The order is always: greeting if he used one, date line, one main-outcome paragraph, then the bullets.
Nothing else. No title, no sign-off, no "let me know if you want changes" inside the report.

The blank lines between those parts vary:

| Blank line | A | B | C |
| :--- | :--- | :--- | :--- |
| After the greeting | n/a | n/a | yes |
| After the date line | yes | no | no |
| Between the main outcome and the first bullet | yes | yes | no |

Support: varies. Reproduce his spacing for that day, and when the notes give no signal, A's shape is the safe default because it is the most readable of the three.

**Corrected from the first version of this file**, which required a blank line in both places and would have reformatted B and C.

---

## M - Main outcome

### M1 - One paragraph, naming the day's centre of gravity - P0

Support: A, B, C.

The paragraph names the centre of gravity and says what happened to it.
It opens with that name in all three: `ProfitsX development.`, `Profitsx wireframe + start of implementation!`, ` Profitsx and Mockups.`

It is not a summary of the bullets.
If the paragraph can be reconstructed by shortening the bullets, rewrite it, unless the day's notes are genuinely too thin to carry anything else, in which case `H1` wins and the overlap stands.

One paragraph, no line breaks inside it. Three to six sentences: A has 6 in 55 words, B has 3 in 46, C has 3 in 47.

### M2 - Feeling, when he gives it - P1

Support: two of three. A opens `Exciting, everything's coming together`. B carries it in punctuation: `wireframe + start of implementation!`, `works great!`. C states none.

Carry the feeling he expressed, in his words, including his exclamation marks.
Never manufacture one. C proves a flat report is a correct report.

**Downgraded from the first version of this file**, which treated feeling as expected.

### M3 - Honest about pace and over-ambition - P0

Support: A and B. Expect this, and never soften it.

A: `A little slower today with less AI help.`
B: `Was hoping to be done today but it's too ambitious, tomorrow I'll try so that I can move on to the tools, resources, leadgen, CMS, and other that needs to be wired.`

Two of the three days say the day fell short of the plan, and B's one sentence carries the miss, the retry and the queue behind it.

If he reported the day was slow, blocked, short, or more ambitious than it turned out, that stays in, in his words.
Never soften it, never drop it, never turn it into an achievement.

C says nothing of the kind, so this is never invented either.

### M4 - Closing on tomorrow, when he does - P1

Support: two of three. A closes `Tomorrow, I have ALL my AI colleagues...`. B closes on `tomorrow I'll try so that I can move on to...`. C just ends on `how animation will go along.`

Common, not required.
When his notes point at tomorrow, the paragraph ends there. When they do not, the paragraph ends where he ended.

**Downgraded from the first version of this file**, which required a forward-looking close and would have invented one for C.

---

## B - Bullets

### B1 - Naming the workstream - P1

Support: varies, and it varies more than the first version of this file assumed.

A names the workstream in 3 of 4 bullets. C names it in all 3. B names it in none of the four: the name runs into the sentence (`ProfitsX wireframe done earlier this morning.`, `Moving scrubs was more finished than I thought`) or the bullet opens with a bare verb (`Started implementation of home, service page, faq, and philosophy page.`).

Prefer opening with the workstream when his notes make it obvious.
A bullet that opens with a bare verb or runs the name into the sentence is correct, and B is the proof.

Never bolt a name onto a bullet whose note already reads as a sentence.

### B2 - Four separator forms, do not standardise - P0

Support: varies. All four forms are attested:

| Form | Example | Specimen |
| :--- | :--- | :--- |
| Full stop | `ProfitsX Homepage.` | A |
| Colon | `Moving Scrubs:` | A |
| Hyphen | `Created Mockups - R&J for GHL...`, `Templates - Checked all around...` | C |
| None | the name runs into the sentence, or there is no name | A, B, C |

He mixes forms inside a single report.
Making every bullet use one form is a finding.

**Extended from the first version of this file**, which knew only the full stop and the colon.

### B3 - Unfinished stated as unfinished - P0

Support: A and B.

Work in progress is reported in progress, with what unblocks it where he gave it.

A: `Not yet done but tomorrow, we'll be able to import it to webflow`.
B: `Moving scrubs was more finished than I thought, but still needs a little touch of finish`.

Never round an in-progress item up to done.

### B4 - Reason included where it explains a choice - P1

Support: A and B, and B leans on it heavily.

A: `Homepage is being focused right now because once this is done, the other pages will be easier since we now have the full concept`.
B: `Some of the implementations are still in html because it is hard to implement and fix 3D animations in webflow than just html`.
B: `I really had to make this because I was kinda lost on what to implement`.

When he said why something got the attention or why he chose an approach, keep it.
Do not invent a rationale he did not give.

### B5 - Short declarative runs and fragments stay - P1

Support: A for the runs, B for the fragments.

A: `Webinars are done. GHL Login is done. Resources is done.`
B: `Faster fix iterations.`
A: `Thank you pages, wired up.`

Do not merge a run into one list sentence and do not complete a fragment into a full clause.
The repetition and the clipping are the point.

### B6 - Length follows the day - P2

Support: A, B, C.

One sentence is a complete bullet when one sentence is what happened (`Created Mockups - R&J for GHL and Reico for Webflow.`).
Six sentences is a complete bullet when six is what happened (B's wireframe bullet).
Do not top up a thin bullet to match a fat one.

### B7 - Links go inline and unlabelled - P1

Support: B, the only specimen with a link.

`ProfitsX wireframe done earlier this morning. https://profitsx-10c54d.webflow.io/app/wireframes/visual Gonna put it here for documentation.`

The bare URL sits in the flow of the bullet, with no link text, no parentheses, no "see:", and no markdown link syntax.
The sentence after it says why it is there.

When he gives a link, place it the same way.

### B8 - He addresses the reader and defends time spent - P1

Support: B.

`Don't worry, this didn't take me long to create.`

The wireframe could read as a detour, so he pre-empts the challenge before anyone raises it.
`I really had to make this because I was kinda lost on what to implement and so that I can go without doubts.` does the same job.

When his notes carry a line like this, it stays, in his words.
It is not an aside to be trimmed, and it is not something to add on his behalf.

---

## V - Voice

### V1 - No em dashes or en dashes - P0

Support: A, B, C. Zero across the corpus. Also his standing rule.

Never emit an em dash (U+2014) or an en dash (U+2013), in the report or anywhere else.
Use a period, a comma, a colon, parentheses, or a plain hyphen `-`.

The hyphen as a separator after a workstream name (`B2`) is a plain hyphen and is correct.

Verify by counting non-ASCII characters with a script.
`grep -o` returns zero on these characters even when the text is full of them, so `grep` is not evidence.

```
python3 -c "import sys;t=open(sys.argv[1],encoding='utf-8').read();print([(i,c,hex(ord(c))) for i,c in enumerate(t) if ord(c)>127])" FILE
```

An empty list is the pass condition.

This is the one place `W1` yields. If his notes carry a dash character, replace the character and change nothing else about the sentence.

### V2 - Banned constructions - P0

Support: his standing rules. Zero occurrences across the corpus.

None of these, in the report or in the commentary around it:

- "it's not just X, it's Y", "X isn't just Y"
- "in today's fast-paced world", "in an era where", "let's dive in"
- unlock, unleash, elevate, empower, supercharge, seamless, robust, cutting-edge, game-changer, revolutionize, delve, leverage used as a verb
- tricolon padding: "faster, smarter, better"
- rhetorical-question openers: "Ever wondered why...?"
- a closing summary that restates the report back to the reader
- hedged nothing-claims: "helps you do more of what matters"

### V3 - First person, his pronouns - P0

Support: A, B, C.

`we` for the work, `I` for himself.
No third person, no passive rewrite that removes him from his own day.

### V4 - Contractions and spoken register - P0

Support: A, B, C.

`everything's`, `we'll`, `I'm gonna`, `didn't`, `it's`, `kinda`, `gonna`, `and stuff`, `etc.`.

This is dictated speech, and the roughness in it is the voice.
Raising it into written prose is a finding, not an improvement.

"Lightly tidied" is not a licence to edit. See `W1`: the tidying allowed is a genuine typo, nothing else.

### V5 - His spelling of names, per occurrence - P0

Support: A, B, C, and all three vary inside a single report.

| Specimen | Spellings in that one report |
| :--- | :--- |
| A | `ProfitsX`, `MovingScrubs`, `Moving Scrubs` |
| B | `Profitsx`, `ProfitsX`, `Moving scrubs` |
| C | `Profitsx`, `ProfitsX`, `profitsx` |

Spell each name the way he spelled it **at that occurrence**.

Two occurrences that disagree are never reconciled with each other.
C writes `Profitsx` in the main outcome and `profitsx` in the third bullet, and both are correct.

Also: `GHL` capitalised, `webflow` and `html` lowercase, `Webflow` capitalised where he capitalised it in C.

**Extended from the first version of this file**, which said his spelling wins but did not say it wins per occurrence.

### V6 - Emphasis by capitals, sparingly - P2

Support: A.

`ALL my AI colleagues`.
At most once per report, and only where he stressed it.

### V7 - People and client names as he writes them - P1

Support: B and C.

`Ron`. `R&J`. `Reico`.

Client codes travel with what the client is, in his parentheses: `one for GHL (R&J) and one for Construction Company (Reico)`.

Never expand a code he abbreviated, never abbreviate a name he wrote out, and never drop a colleague's name to make a sentence tidier.

### V8 - Playful constructions are voice - P1

Support: B, with the exclamation marks also in A's register.

`Animations animations++ .` including the space before the period.
`Profitsx wireframe + start of implementation!`
`+` as a mid-sentence connector: `a little touch of finish + Little some help to Ron`.
`works great!`

Reproduce these exactly, spacing included.
An editor removes the space before the period in `animations++ .` and normalises `+` to "and". Both are findings.

---

## H - Honesty

### H1 - Never invent - P0

Support: all three, in the sense that nothing in them is unaccounted for.

No work, no number, no completion, no rationale, no link and no feeling that was not reported.
An EOD is a factual record of one person's day.

If evidence mode surfaced work he did not mention, offer it outside the report and let him decide.
Never place it in a bullet on your own.

`H1` outranks `M1`. On a thin day, a main outcome that overlaps the bullets is correct and inventing colour to avoid the overlap is not.

### H2 - Numbers only as reported - P0

Support: A has none. B has none. C has `two mockups`, which is a count of the two named mockups in the same sentence.

Any figure in the report came from him, or from evidence he accepted.
There is no house expectation of numbers.
