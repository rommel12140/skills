# Copy tells

Twenty-five entries in eight categories.
Every entry has a stable ID, a severity, a gate phrased so that an affirmative answer fails, and a replacement.

## Severity

| Level | Meaning | Action |
| :--- | :--- | :--- |
| P0 | Reads as machine-written on sight, or states something untrue | Fix every occurrence |
| P1 | An obvious smell | Fix on every pass |
| P2 | Cosmetic | Lower priority |

## Categories

| Prefix | Category |
| :--- | :--- |
| V | Vocabulary |
| P | Phrase and construction |
| ST | Structure and rhythm |
| O | Openers and closers |
| F | Formatting |
| H | Honesty |
| SY | Sycophancy and chat residue |
| VO | Voice fit |

---

## V - Vocabulary

### V1 - Global banned vocabulary - P0

Gate: Does the text contain unlock, unleash, elevate, empower, supercharge, seamless, robust, cutting-edge, game-changer, revolutionize, delve, or leverage used as a verb?
Detect: word-boundary match, case-insensitive.
Exempt: leverage as a finance noun. Robust as a term of art in statistics or engineering, where it has a precise meaning.
Why: these carry the highest single-word signal in every published pattern set, and each one replaces a specific verb with a vague one.
Instead: name the concrete action. Use, raise, let you, make it possible to. Or delete the sentence, because a sentence built around one of these words is usually a sentence with no content.

### V2 - Project-specific banned words - P0

Gate: Does the text use anything listed under "Words this project does not use" in `voice.md`?
Detect: exact match against that list.
Why: the project has already decided this.
Instead: whatever `voice.md` says, or the nearest term from "Words this project uses".

### V3 - Corporate abstractions - P1

Gate: Does the text use streamline, optimize, innovative, solutions, offerings, capabilities, or ecosystem where a concrete noun would fit?
Exempt: optimize in a performance-engineering context, where it describes an actual optimization.
Why: each one names a category rather than a thing, so the reader learns nothing.
Instead: the actual thing. Not "our solutions", but the product's name. Not "streamline your workflow", but the step that gets removed.

### V4 - Paired adjectives - P2

Gate: Does the text pair two adjectives that mean nearly the same thing? "Comprehensive and thorough", "simple and easy", "fast and efficient".
Why: the second adjective adds no information and signals padding.
Instead: pick the more precise one and delete the other.

---

## P - Phrase and construction

### P1 - The not-just construction - P0

Gate: Does the text contain "it's not just X, it's Y", "X isn't just Y", or any variant?
Why: it promises a reframe and then delivers a synonym. It is the single most recognisable construction in machine-written marketing copy.
Instead: state Y directly. If Y is not worth stating on its own, the sentence has nothing in it.

### P2 - Era openers - P0

Gate: Does the text open a section with "In today's fast-paced world", "In an era where", "In the modern landscape", or a variant?
Why: it spends a sentence establishing that time exists.
Instead: delete it. The sentence after it is almost always the real opening.

### P3 - Tricolon padding - P1

Gate: Does the text use a three-item list where the items are near-synonyms? "Faster, smarter, better". "Secure, reliable, scalable".
Exempt: three genuinely distinct items.
Why: the rhythm carries the sentence, not the content.
Instead: one item, chosen because it is true and the others are not.

### P4 - Hedged nothing-claims - P1

Gate: Does the text make a claim that cannot be false? "Helps you do more of what matters." "Designed to fit the way you work."
Why: an unfalsifiable claim is not a claim.
Instead: the specific thing, for the specific person, with the number if there is one.

---

## ST - Structure and rhythm

### ST1 - Uniform sentence length - P1

Gate: Do the sentences in a paragraph all fall within a few words of the same length?
Detect: judgment, reading aloud is the reliable test.
Why: human prose varies. Even length is one of the few structural signals that holds up.
Instead: cut one sentence to four words. Let another run long. Vary it because the meaning wants it varied, not on a schedule.

### ST2 - Reflexive rule of three - P1

Gate: Does the piece reach for a three-item list every time it needs structure?
Why: it is a default shape rather than a chosen one, and it forces a third item that does not exist.
Instead: use the number of items there actually are. Two is a fine number. So is five.

### ST3 - Manufactured personality - P2

Gate: Does the text use staccato fragments to sound informal? "Simple. Fast. Yours."
Exempt: a project whose `voice.md` establishes this register deliberately.
Why: the shape performs a personality the text has not earned.
Instead: write the full sentence. If it is boring as a full sentence, the fragment did not make it interesting.

---

## O - Openers and closers

### O1 - Rhetorical question opener - P0

Gate: Does a section open with a question the reader did not ask? "Ever wondered why...?" "What if you could...?"
Why: it assumes the reader's interior state and delays the point.
Instead: open with the point.

### O2 - Dive-in transitions - P0

Gate: Does the text contain "let's dive in", "let's explore", "let's take a look", "buckle up"?
Why: it announces the content instead of delivering it.
Instead: delete. Start the section.

### O3 - Restating closer - P0

Gate: Does the piece close by summarising what the reader has just read?
Exempt: a reference document where a summary genuinely serves lookup.
Why: it adds length without adding information, and it signals that the writer had nothing left to say.
Instead: end on the last real point, or on what the reader should do next.

### O4 - Machine sentence openers - P1

Gate: Do sentences open with Certainly, Moreover, Additionally, Furthermore, Notably, Importantly, or It's worth noting?
Why: these are connective tissue with no direction. Moreover and Furthermore in particular claim a logical relationship they rarely deliver.
Instead: state the relationship if there is one ("that matters because"), or delete the opener and let the sentences sit next to each other.

---

## F - Formatting

### F1 - Dash used as punctuation - P0

Gate: Does the text contain an em dash or an en dash used as punctuation?
Detect: literal match on the characters themselves.
Exempt: quoted source material. Numeric ranges where the en dash is typographically correct and the project uses it.
Why: this is a standing rule in the captain's global instructions, and it applies to every character emitted.
Instead: a period, a comma, a colon, or parentheses. Where a sentence only works with a dash, a plain hyphen.

### F2 - Emoji as bullets or labels - P0

Gate: Does the text use emoji to introduce list items, mark section headings, or act as interface labels?
Exempt: text that is genuinely about emoji.
Why: it substitutes decoration for structure.
Instead: a normal bullet, or a real heading.

### F3 - Title Case In Body Copy - P2

Gate: Are headings inside body copy set in Title Case rather than sentence case?
Exempt: a project whose established style uses title case throughout.
Why: it is inconsistent with how the surrounding prose reads.
Instead: sentence case.

### F4 - Markdown leaking into plain text - P1

Gate: Does output destined for a plain-text surface contain markdown syntax? Asterisks for emphasis, hash headings, backticks.
Why: the reader sees the syntax, not the formatting.
Instead: plain text, or the target surface's own formatting.

---

## H - Honesty

### H1 - Unlisted number - P0

Gate: Does the text state a figure, percentage, count, or timespan that is not listed under "Numbers we are allowed to state" in `voice.md`?
Detect: extract every numeric claim, compare against the list.
Exempt: numbers that are structural rather than claims. Version numbers, dates, prices read from the live product, quantities the reader supplied.
Why: this is the mechanism that catches invented statistics without needing to judge whether a figure is plausible.
Instead: use a listed figure, source the new one and add it to `voice.md`, or remove the claim.
Note: when `voice.md` is absent, this gate cannot run. Say so rather than guessing.

### H2 - Unsourced quote - P0

Gate: Does the text attribute a statement to a person or organisation without a source that can be checked?
Why: fabricated quotes are the highest-cost failure in this catalog.
Instead: source it, or remove it.

---

## SY - Sycophancy and chat residue

### SY1 - Acknowledgement before answering - P1

Gate: Does the text open by acknowledging the request before addressing it? "Great question." "Happy to help with that." "Absolutely."
Why: it is conversational residue that does not belong in written copy.
Instead: answer.

### SY2 - Praise directed at the reader - P1

Gate: Does the text compliment the reader's question, idea, or situation?
Why: the reader did not ask to be flattered, and it reads as filler.
Instead: delete it.

---

## VO - Voice fit

### VO1 - The competitor test - P0

Gate: Could this sentence be pasted onto a competitor's site without becoming false?
Detect: judgment. Apply to every claim sentence. Do not apply to connective or descriptive prose, which is allowed to be ordinary.
Why: a sentence that survives the swap is not saying anything about this product. This is the single most useful gate in the catalog and the one that catches copy the word lists miss entirely.
Instead: replace the abstraction with the specific thing this product does, the number it does it in, or the person it does it for. If none of those exist, the sentence should not either.

Worked example.

Fails: "We help teams ship faster with a platform built for modern development."
Passes: "Your test suite runs on four machines instead of one. A 40 minute suite finishes in 11."

The second cannot be pasted onto a competitor's site, because it is a claim about this product that would be false about theirs.
