# Case 07 - expected output

The correct answer already exists: it is specimen B in `references/corpus.md`.

## The target

```
Hey! EOD for today: 7/29/26
Profitsx wireframe + start of implementation! Copywriting, wiring of animation, sections, etc. are started. Was hoping to be done today but it's too ambitious, tomorrow I'll try so that I can move on to the tools, resources, leadgen, CMS, and other that needs to be wired.

 - Started implementation of home, service page, faq, and philosophy page. Some of the implementations are still in html because it is hard to implement and fix 3D animations in webflow than just html. Faster fix iterations. I only put it on webflow if everything's aligned and complete for a faster development.
 - ProfitsX wireframe done earlier this morning. https://profitsx-10c54d.webflow.io/app/wireframes/visual Gonna put it here for documentation. I really had to make this because I was kinda lost on what to implement and so that I can go without doubts. Don't worry, this didn't take me long to create. Just wanted to make a feel of what to add in webflow. Design is not yet here but sections are now in place.
 - Animations animations++ . Added animations in webflow and works great! I just had to step back on implementation because I wanted to realign everything.
 - Moving scrubs was more finished than I thought, but still needs a little touch of finish + Little some help to Ron regarding adding a button on his checklist.
```

## What must survive

| Must appear | Fails the case | Rule |
| :--- | :--- | :--- |
| `Hey! EOD for today: 7/29/26` on one line | the greeting split onto its own line, or the colon moved to the end | `G1`, `F1` |
| No blank line between the date line and the main outcome | a blank line inserted | `F5` |
| A bare URL inline, with no label, no parentheses and no markdown link | `[wireframe](https://...)`, or the URL moved to the end of the bullet | `B7`, `F4` |
| `Gonna put it here for documentation.` immediately after the URL | the explanation dropped as redundant | `B7` |
| `Don't worry, this didn't take me long to create.` | trimmed as an aside | `B8` |
| `I really had to make this because I was kinda lost on what to implement` | tightened, or `kinda` removed | `B4`, `V4` |
| `Animations animations++ .` including the space before the period | `Animations++.` or `Animations.` | `V8` |
| `a little touch of finish + Little some help to Ron` | `+` turned into "and", or `Little some help` corrected | `V8`, `W1`, `V7` |
| `Ron` named | the colleague dropped to tidy the sentence | `V7` |
| `works great!` and `implementation!` | exclamation marks removed | `M2`, `V8` |
| `it is hard to implement and fix 3D animations in webflow than just html` | the comparative repaired to "harder ... than" | `W1` |
| `and other that needs to be wired` | repaired to "and others that need to be wired" | `W1` |
| `Moving scrubs was more finished than I thought` | `Moving Scrubs` capitalised as in the 30 July report | `V5` |
| `Faster fix iterations.` as its own fragment | joined to the sentence before it | `B5` |
| No bullet opening with a workstream name and a separator | a name and a full stop bolted onto each bullet | `B1`, `B2` |

## Checklist

### Assembly

- [ ] Four bullets, in the order he gave: implementation, wireframe, animations, Moving scrubs.
- [ ] The main outcome is the one he supplied, unchanged, and does not absorb bullet material.
- [ ] The shortfall sentence stays whole: `Was hoping to be done today but it's too ambitious, tomorrow I'll try so that I can move on to the tools, resources, leadgen, CMS, and other that needs to be wired.` (`M3`).

### Format

- [ ] The date is `7/29/26`, unpadded, two-digit year.
- [ ] A blank line before the first bullet, as his notes have.
- [ ] Bullets use ` - `.
- [ ] Zero characters above U+007F. The URL is ASCII and is not a violation.

## Automatic fail

- Any row of the table above broken.
- The URL reformatted as a markdown link.
- `Don't worry, this didn't take me long to create.` removed.
- Any em dash or en dash.
