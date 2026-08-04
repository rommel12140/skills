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

`references/corpus.md` holds three of his own EODs, from 28, 29 and 30 July 2026, and is the authority on format, tone, length and punctuation.
`references/voice-rules.md` holds the rules derived from them, each with an ID and a line naming which specimens support it.
Read the corpus before applying any rule. When a rule and a specimen disagree, the specimen wins and the rule is wrong.

## Read all three, not one

The three days differ in ways that matter, and most of what a single day would teach you to enforce turns out to be his to vary: the greeting, the punctuation around the date, where the blank lines go, how many bullets, which separator follows a workstream name, whether the report closes on tomorrow, and how he capitalises his own project names from one sentence to the next.

Before writing anything, read the "What varies across the three" table in `references/corpus.md`.
Every row in it is a thing this skill has already got wrong once.

Where the three agree, enforce it. Where they differ, reproduce whatever he did that day and never pick a canonical form.

## Who reads it

**His boss, and his boss is not a developer.**

His words: "My boss isn't a developer so he doesn't understand merge, he just wants to know what job is done and stuff."

The distinction is not technical versus non-technical. His own three EODs are full of product and tool names and every one of them is correct: Webflow, GHL, GHL Login, popups, thank you pages, webinars, homepage, components, templates, sitemap, mockups. Those stay, because his boss knows the tools the business runs on.

What never appears is developer process: merged, pull request, PR, branch, commit, validation, pipeline, code review, refactor, stylesheet, CSS, API, endpoint, repository, deploy, build step, test suite.

A job is done, in progress, or tomorrow. How it got there is not the report.

The corpus already does this, which is where the rule came from: `Webinars are done. GHL Login is done. Resources is done. Thank you pages, wired up.` Named things, and their state.

This is `R1` in `references/voice-rules.md`, it carries `W1`'s severity, and it outranks fluency. An accurate sentence that names developer process is a failure, not a near miss. The worked before-and-after in that file is the fastest way to check a draft against it.

The second rule from the same ruling is `R2`: anything on a fixed recurring schedule stays out of the bullets. His words: "Never add priority for planning the week. We are doing that every Friday and Sunday for the next week." Bullets are for work that changed state. That is not a licence to drop real work that happens to recur, and the test is whether the thing moved, not whether it repeats.

## The one rule that gets broken

**Preserve his wording. This skill assembles and orders. It does not re-word.**

His words on it: "The roughness is my voice. Follow my voice, and making it smoother is kinda like feeling AI sloppish."

You may choose which of his notes become which bullet, put the bullets in priority order, drop a duplicate, and fix a genuine typo that would confuse a reader.

You may not replace his verb with a more standard one, regularise a tense, complete a fragment, reorder a clause for flow, expand or contract a contraction he chose, drop a trailing "and stuff" or "or whatever", or swap a dictated word for a tidier synonym.

If a phrase is intelligible, it ships as he said it, whether or not an editor would keep it.
The only wording written fresh is a connective joining two of his fragments, and even then prefer one he already used.

This is `W1` in `references/voice-rules.md`, it outranks every other rule there, and the worked examples in that file are the fastest way to check a draft against it.
Every sentence in the corpus that an editor would fix is a sentence this skill must leave alone.

His whitespace counts too (`W2`): the 28 July main outcome opens with a leading space and one of its bullets has a double space mid-sentence, and neither gets tidied.

## The shape

```
<greeting, only if he used one>
<date line, containing EOD for today and M/D/YY>
<one paragraph: the day's centre of gravity and what happened to it>
 - <what happened>
 - <what happened>
 - <what happened>
```

That order never changes. Almost everything else about it does:

| Part | Fixed | His to vary |
| :--- | :--- | :--- |
| Greeting | nothing | present or absent, on its own line or folded into the date line |
| Date line | the words `EOD for today`, and `M/D/YY` unpadded with a two-digit year | where the colon goes, or whether there is one |
| Blank lines | none of them | after the greeting, after the date line, before the first bullet |
| Main outcome | one paragraph, on one line, opening with the day's centre of gravity | length, whether it states a feeling, whether it closes on tomorrow |
| Bullets | the ` - ` marker, priority order, four as a ceiling | how many, whether each names its workstream, which separator follows the name |

Four is the ceiling and never a target. Three is attested. Two priorities produce two bullets.

When his notes give no signal on a varying part, follow the 30 July shape: no greeting, a blank line after the date line and another before the bullets. It is the most readable of the three and the safest default.

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

1. Read `references/corpus.md`, then `references/voice-rules.md`.
2. Take what he gave you. Do not ask him anything he has already answered.
3. Drop anything that happened on a fixed recurring schedule and did not move (`R2`). Weekly planning is the standing example. Keep the recurring thing only where something actually changed state inside it, and then the bullet is about what changed, not about the ritual.
4. Group the rest of the day into workstreams, at most four. Fold small items into the workstream they belong to.
5. Order the workstreams by priority. Infer the order when it is obvious from what he said: what he spent the day on, what he led with, what he called out as the focus.
6. For each workstream, decide what his boss is being told: the named thing and its state. Where a note describes developer process, the mechanic comes out and the outcome goes in (`R1`). Product and tool names stay as he said them.
7. Assemble the main outcome from his own phrasing. It names the centre of gravity and says what happened to it. It is not a summary of the bullets (`M1`). It carries the feeling and the tomorrow only if he gave them (`M2`, `M4`).
8. Assemble the bullets in priority order, from his own phrasing (`B1`, `B2`).
9. Reproduce his greeting, his date-line punctuation and his blank lines from the notes (`G1`, `F1`, `F5`). Where the notes give no signal, use the 30 July shape.
10. Run the self-check below.
11. Output the report, then one line naming the order you chose, then anything you need to ask.

Steps 7 and 8 say assemble rather than write on purpose.
The sentences are already his. Your job is which ones go where, not how they read (`W1`).

Steps 3 and 6 are the two his 4 August ruling added, and they are the only steps that decide what does not reach the page. Everything after them is assembly.

Step 9 is the one the corpus added. The report's furniture is his too, not a house style you supply.

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

2. **Written for his boss** (`R1`). Read the report as someone who does not write software. Every sentence names a thing and its state. If a sentence explains how the work was carried out rather than what job is now done, in progress, or tomorrow, it is a rewrite and not a caveat. Check the developer-process list in `references/voice-rules.md`, and check the sense as well as the string.
3. **Nothing recurring in the bullets** (`R2`). For each bullet, ask whether it happened because something moved or because it was Friday. Weekly planning never earns one.
4. **Banned constructions** (`V2`). Walk the list in `references/voice-rules.md`.
5. **Format** (`F1` to `F5`). Date is `M/D/YY` unpadded, ` - ` markers, no headers, no bold, no emoji, no tables. A bare URL is fine (`B7`).
6. **No padding** (`F3`). Bullet count equals the number of priorities he actually reported, less anything `R2` took out.
7. **Nothing invented** (`H1`). Every claim, number, link and completion traces to something he said or accepted. Restating a mechanic as an outcome under `R1` does not license a claim he did not make. If you cannot say what job it finished without guessing, ask below the report.
8. **Unfinished stays unfinished** (`B3`).
9. **Voice not raised** (`V4`). Contractions intact, short declarative runs and fragments not completed, separators after workstream names still varied (`B2`, `B5`).
10. **Wording preserved** (`W1`). Put his notes and your draft side by side, sentence by sentence. For every sentence that changed, name why. "It reads better" is a failure, not a reason. The only reasons that pass are a genuine typo, a dash replaced under `V1`, and a mechanic restated under `R1`, and that last one moves the mechanic and nothing else in the sentence. Anything left that is only a grammar improvement gets reverted to his wording.
11. **Nothing normalised** (the varies rules). Walk the "What varies across the three" table in `references/corpus.md` row by row against your draft. For each row, either his notes decided it or the default did. If you decided it because it looked more consistent, that is the failure this step exists to catch. Watch in particular for: a greeting added or dropped, the date-line punctuation regularised, blank lines inserted or removed, separators made uniform, and his project-name capitalisation reconciled between two occurrences (`V5`).

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

The authority for this skill is `references/corpus.md`, which is his writing rather than a project's.

One narrow exception: if he names a project that has a `voice.md`, its "Words this project uses" section may be consulted for how a product noun is spelled.
Even then `V5` outranks it. He spells it the way he says it that day.
