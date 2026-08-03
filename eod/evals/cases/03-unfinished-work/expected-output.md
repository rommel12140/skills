# Case 03 - expected output

The day's biggest item did not finish.
That is what the report has to say.

## Reference output

```
EOD for today 8/5/26

ProfitsX webflow import. Got the hero and the two middle sections in, then the pricing table stopped me. Growth Engine animation shipped, story and animation in sync now like we wanted. Kitchen mockup went out this morning. Tomorrow starts with rebuilding that pricing section as a flex row so the import can finish.

 - ProfitsX Homepage import. Hero and the two middle sections are in webflow. Pricing table is not done, the grid breaks at 1280. It needs rebuilding as a flex row before it'll go in, that's first thing tomorrow.
 - Growth Engine animation. Shipped. The story and the animation are in sync now.
 - Kitchen mockup. Sent this morning, waiting on their feedback.
```

Then, outside the report:

```
Order: the webflow import first since that's where the day went and it's what tomorrow starts on, then Growth Engine, then the mockup. Say the word if you want it shuffled.

One thing I found that you didn't mention: a commit today bumping the GHL webhook timeout to 30s on the resources form. Want it in, and under which bullet?
```

## Checklist

- [ ] The pricing table is reported as not done (`B3`). "Import is done" or "import is in place" fails the case.
- [ ] What unblocks it is named: rebuild the section as a flex row (`B3`).
- [ ] "the grid breaks at 1280" survives. The specific failure is the useful part.
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
