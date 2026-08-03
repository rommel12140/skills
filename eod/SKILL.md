---
name: eod
description: >
  Write the owner's end-of-day report in his own format and voice: a dated line,
  one main-outcome paragraph, then up to four priority bullets. Use when he says
  "write my EOD", "EOD for today", "here's what I did today", or dictates a day's
  work in any order and any state of roughness. Can check itself against the day's
  commits and merged PRs when asked. Never invents work.
---

# eod

This skill writes one person's end-of-day report.
It is not a general standup or status-report generator, and it should not be adapted into one.

`references/specimen.md` holds his own EOD for 30 July 2026 and is the authority on format, tone, length and punctuation.
`references/voice-rules.md` holds the rules derived from it, each with an ID.
Read the specimen before applying any rule. When the two disagree, the specimen wins.

## The one rule that gets broken

**Preserve his wording. This skill assembles and orders. It does not re-word.**

His words on it: "The roughness is my voice. Follow my voice, and making it smoother is kinda like feeling AI sloppish."

You may choose which of his notes become which bullet, put the bullets in priority order, drop a duplicate, and fix a genuine typo that would confuse a reader.

You may not replace his verb with a more standard one, regularise a tense, complete a fragment, reorder a clause for flow, expand or contract a contraction he chose, drop a trailing "and stuff" or "or whatever", or swap a dictated word for a tidier synonym.

If a phrase is intelligible, it ships as he said it, whether or not an editor would keep it.
The only wording written fresh is a connective joining two of his fragments, and even then prefer one he already used.

This is `W1` in `references/voice-rules.md`, it outranks every other rule there, and the worked example in that file is the fastest way to check a draft against it.
Every sentence in the specimen that an editor would fix is a sentence this skill must leave alone.

## The shape

```
EOD for today M/D/YY

<one paragraph: the day's centre of gravity, how it went, closing on tomorrow>

 - <workstream>. <what happened>
 - <workstream>: <what happened>
 - <workstream>. <what happened>
 - <what happened>
```

Bullets are one leading space, a hyphen, one space.
Most important priority first.
Four is the ceiling. Two priorities produce two bullets.

## Two modes for gathering the day

**Dictation** is the primary mode and must work with nothing else available.
He says what he did, in any order, in any state of roughness. This skill does the assembling.
Never require a repository, a network call, or a tool to be present.

**Evidence** is secondary and runs only when he asks it to fill gaps or check itself.
It reads what actually happened from local evidence for the day in question:

- Commits: `git log --since="<date> 00:00" --until="<date> 23:59" --author=<him> --oneline` in each repository under discussion.
- Merged pull requests: `gh-axi pr list --state merged` and filter to the day. Use `gh-axi` for anything on GitHub, not raw `gh`.

Rules on evidence, all of them `H1`:

- Evidence never becomes a bullet on its own.
  Anything found that he did not mention is offered to him below the report, as a question, and is inserted only if he says yes.
- Evidence never contradicts him into the report.
  If he said a thing shipped and no commit shows it, ask; do not silently downgrade it.
- If evidence gathering fails or there is no repository, say so in one line and produce the report from dictation anyway.

## Procedure

1. Read `references/specimen.md`, then `references/voice-rules.md`.
2. Take what he gave you. Do not ask him anything he has already answered.
3. Group the day into workstreams, at most four. Fold small items into the workstream they belong to.
4. Order the workstreams by priority. Infer the order when it is obvious from what he said: what he spent the day on, what he led with, what he called out as the focus.
5. Assemble the main outcome from his own phrasing. It names the centre of gravity, says how it went, and closes on tomorrow. It is not a summary of the bullets (`M1`).
6. Assemble the bullets in priority order, from his own phrasing. Each names its workstream, then says what happened (`B1`).
7. Run the self-check below.
8. Output the report, then one line naming the order you chose, then anything you need to ask.

Steps 5 and 6 say assemble rather than write on purpose.
The sentences are already his. Your job is which ones go where, not how they read (`W1`).

## Ordering

The priority order is his call, not yours.
Infer it, state it in one line under the report, and let him reorder:

```
Order: ProfitsX Homepage first since that's where the day went, then Moving Scrubs, then Growth Engine, then the kitchen mockup. Say the word if you want it shuffled.
```

One line. Do not present options, do not explain the reasoning twice, and do not ask him to confirm before writing the report.

## Self-check before output

Run all of these. A failure is a rewrite, not a caveat.

1. **Dashes.** Count non-ASCII characters with a script. `grep -o` returns zero on U+2014 and U+2013 even when the text is full of them, so `grep` is not evidence.

   ```
   python3 -c "import sys;t=open(sys.argv[1],encoding='utf-8').read();print([(i,c,hex(ord(c))) for i,c in enumerate(t) if ord(c)>127])" FILE
   ```

   An empty list passes. Anything else is `V1` and must be fixed before output.

2. **Banned constructions** (`V2`). Walk the list in `references/voice-rules.md`.
3. **Format** (`F1` to `F5`). Date line unpadded, ` - ` markers, no headers, no bold, no emoji, no tables.
4. **No padding** (`F3`). Bullet count equals the number of priorities he actually reported.
5. **Nothing invented** (`H1`). Every claim, number and completion traces to something he said or accepted.
6. **Unfinished stays unfinished** (`B3`).
7. **Voice not raised** (`V4`). Contractions intact, short declarative runs not merged, separators after workstream names still varied (`B2`, `B5`).
8. **Wording preserved** (`W1`). Put his notes and your draft side by side, sentence by sentence. For every sentence that changed, name why. "It reads better" is a failure, not a reason. Anything left that is only a grammar improvement gets reverted to his wording.

## Output contract

The report itself is plain text and pastes into a chat window unchanged.

Everything that is not the report goes after it: the order line, questions, anything evidence turned up.
Never put a preamble above the date line, and never put a sign-off or a closing summary inside the report.

Do not offer a score, a rating, or a judgement of the day.

Do not offer a cleaned-up alternative version alongside the report.
There is one report and it is in his words.

## voice.md

This skill does not read a project's `voice.md`.

`voice.md` scopes one project's outward copy: its reader, what it sells them, the figures that copy may cite, its visual language.
An EOD is not outward copy and is not scoped to one project.
The specimen alone spans ProfitsX, MovingScrubs, a growth engine animation and a kitchen mockup, so there is no single `voice.md` that could apply, and picking one would impose one client's register on his account of his own day.

The authority for this skill is `references/specimen.md`, which is his writing rather than a project's.

One narrow exception: if he names a project that has a `voice.md`, its "Words this project uses" section may be consulted for how a product noun is spelled.
Even then `V5` outranks it. He spells it the way he says it that day.
