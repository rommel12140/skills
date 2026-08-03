# Case 06 - expected output

The correct answer already exists: it is specimen C in `references/corpus.md`.

This case grades the report's furniture as strictly as its words.

## The target

```
Hey! Good day,

EOD for today 7/28/26:
 Profitsx and Mockups. Generated two mockups, one for GHL (R&J) and one for Construction Company (Reico). Profitsx, added the sitemap, added a few animations and started implementing in pages starting with navbar, footer, and planning of the rest of the contents and how animation will go along.
 - ProfitsX detailed planning and specification on how the pages will go, especially the animations. On which pages are static, which pages are story telling with animations.
 - Created Mockups - R&J for GHL and Reico for Webflow.
 - Templates - Checked all around the templates and gonna start forming basic wireframe which is already planned out.  Added animations and inspirations for profitsx.
```

## What must survive, and what a 30-July-only skill breaks

| Must appear | Fails the case | Rule |
| :--- | :--- | :--- |
| `Hey! Good day,` on its own line, then a blank line | greeting dropped, or folded into the date line | `G1` |
| `EOD for today 7/28/26:` with the trailing colon | `EOD for today 7/28/26` | `F1` |
| No blank line after the date line | a blank line inserted, because 30 July had one | `F5` |
| A leading space before `Profitsx and Mockups.` | the space stripped | `W2` |
| The double space in `planned out.  Added animations` | collapsed to one space | `W2` |
| `Created Mockups - R&J for GHL and Reico for Webflow.` | the hyphen changed to a colon or a full stop | `B2` |
| `Templates - Checked all around the templates` | same | `B2` |
| Three bullets | a fourth added to reach the ceiling | `F3` |
| `Profitsx` in the main outcome and `profitsx` in bullet 3 | both normalised to `ProfitsX` | `V5` |
| `one for GHL (R&J) and one for Construction Company (Reico)` | codes expanded, or the parentheses dropped | `V7` |
| No closing line about tomorrow | a tomorrow line invented to satisfy `M4` | `M4`, `H1` |
| No stated feeling | a feeling invented to satisfy `M2` | `M2`, `H1` |

The last two rows are the point of this case as much as the whitespace is.
`M2` and `M4` describe two of the three days. This is the third, and a skill that requires them will invent them.

## The one thing the notes cannot decide

His notes attach the main outcome directly under the date line, so the absence of a blank line there is his and is graded.

They say nothing about whether a blank line precedes the first bullet: the bullet material arrives in a separate chunk, which is a fact about how he dictates rather than about how he lays out the report. Either form passes there.

That is the honest boundary of this case. `F5` says reproduce his spacing when the notes carry a signal and use the 30 July shape when they do not, and this case exercises both halves of that sentence.

## Checklist

### Wording (`W1`)

- [ ] `gonna start forming basic wireframe which is already planned out` survives. Not "going to start forming a basic wireframe".
- [ ] `On which pages are static, which pages are story telling with animations.` survives as written, including `story telling` as two words.
- [ ] `Checked all around the templates` is not tightened to "reviewed the templates".
- [ ] No fragment completed, no tense regularised.

### Assembly

- [ ] Order is ProfitsX planning, mockups, templates, as his notes state.
- [ ] The summary note becomes the main outcome, not a fourth bullet.
- [ ] The line naming the order is not inside the report.

### Format

- [ ] The date is `7/28/26`, unpadded, two-digit year.
- [ ] Bullets use ` - `, one leading space, hyphen, space.
- [ ] Zero characters above U+007F.
- [ ] No headers, bold, tables or emoji.

## Automatic fail

- Any row of the table above broken.
- A fourth bullet.
- A tomorrow line or a feeling that he did not give.
- Any em dash or en dash.
