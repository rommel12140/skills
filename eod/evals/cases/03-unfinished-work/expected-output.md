# Case 03 - expected output

The day's biggest item did not finish.
That is what the report has to say.

## Reference output

```
EOD for today 8/5/26

Webflow import for the ProfitsX homepage. Growth engine animation, shipped it. Kitchen mockup went out this morning. The pricing table is fighting me so the import is not done, that's first thing tomorrow.

 - ProfitsX homepage. Webflow import, started it, got the hero and the two middle sections in, but the pricing table is fighting me. The grid breaks at 1280. Not done. I need to rebuild that section as a flex row before it'll go in, that's first thing tomorrow.
 - Growth engine animation. Shipped it. The story and the animation are in sync now like we wanted.
 - Kitchen mockup. Went out this morning, waiting on their feedback.
```

"the pricing table is fighting me", "not done", "that's first thing tomorrow" and "like we wanted" are all his and all survive intact.
"so the import is not done" in the main outcome is a connective joining two of his fragments, which is the one thing `W1` allows to be written fresh.

Then, outside the report:

```
Order: the webflow import first since that's where the day went and it's what tomorrow starts on, then Growth Engine, then the mockup. Say the word if you want it shuffled.

One thing I found that you didn't mention: a commit today bumping the GHL webhook timeout to 30s on the resources form. Want it in, and under which bullet?
```

## Checklist

- [ ] The pricing table is reported as not done (`B3`). "Import is done" or "import is in place" fails the case.
- [ ] What unblocks it is named: rebuild the section as a flex row (`B3`).
- [ ] "the grid breaks at 1280" survives. The specific failure is the useful part.
- [ ] "the pricing table is fighting me" survives in his words (`W1`). "The pricing table is proving difficult" or "the pricing table blocked me" fails.
- [ ] "I need to rebuild that section as a flex row" keeps him as the subject. "It needs rebuilding" fails.
- [ ] "like we wanted" is not dropped from the animation bullet.
- [ ] The main outcome does not open on the shipped animation to make the day sound better. The import is the centre of gravity and it goes first (`M1`, `M3`).
- [ ] The kitchen mockup is reported as sent and waiting, not as approved or closed.
- [ ] Three bullets, not four (`F3`).
- [ ] `1280` and `30s` are the only numbers, and `30s` appears only outside the report unless he accepts it.

### Evidence handling

- [ ] The GHL webhook commit does not appear in any bullet (`H1`).
- [ ] It is offered below the report, as a question, with what it was.
- [ ] It is not presented as a correction to what he said.
- [ ] If no repository is available, the report is still produced from dictation, with one line saying evidence could not be read.

## Automatic fail

- The pricing table reported as done or as "mostly done" without saying it is unfinished.
- The webhook commit inserted as a fourth bullet.
- Any em dash or en dash.
