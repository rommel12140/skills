# Typography that carries the design

An excellent type system makes the subject recognizable, the hierarchy immediate and the text comfortable to use.
A font name, price or foundry cannot do that by itself.
Choose the face, words, size, width, spacing and surrounding composition together.

## Select with real content

Start from the accepted identity if one exists.
For new work, compare a small shortlist using the actual hero sentence, a paragraph, a button, a date, a price and a long title.
Inspect the rendered specimen on desktop and phone before importing the family throughout the site.

Judge specific properties:

- Letter construction: apertures, terminals, stroke contrast, proportions, width and overall texture.
- Readability: x-height, distinguishable `I/l/1` and `O/0`, punctuation, diacritics and dense small text.
- Voice: why those shapes belong to this subject rather than to a generic idea of luxury or technology.
- Range: real weights, italics, numeral styles, language coverage and optical sizes needed by the content.
- Production: permitted web use, WOFF2 files, supported axes, loading behavior and a compatible fallback.

Default display faces in `T1` still require a deliberate decision.
Do not replace an accepted type system merely because its UI uses a common sans.
A single well-chosen family can supply distinct display, text and interface roles through cuts, width, weight and optical size.
For new expressive work, a deliberate display/body pairing is a useful default; record the evidence for a single-family exception to `T2`.
An arbitrary second font does not fix a weak hierarchy.

## Pair roles, not fashionable names

Give the expressive face a clear job and give reading text a stable companion.
Look for useful contrast in construction, width or texture, with compatible visual size and rhythm.
Avoid pairing two nearly identical sans faces that differ only enough to look inconsistent.
Avoid making the heading, body and metadata all compete for personality.
Start with two families at most unless the content supplies a reason for more.
A mono face belongs where alignment or a real technical convention helps, not on every label.

Possible systems:

| Job | Display | Body and UI | Proof to inspect |
| :--- | :--- | :--- | :--- |
| Image-led hospitality | Characterful display cut or restrained serif | Open, readable text face | Type holds up against varied photos; booking controls stay obvious |
| Industrial product | A firm grotesk or selected condensed cut | Text cut with clear numerals | Product terms and measurements stay readable at small sizes |
| Editorial or cultural work | Expressive title face tied to the material | Quiet text cut | Long titles, quotations, captions and multilingual text coexist |
| Operations interface | Existing brand face with deliberate heading weights | Stable UI family and tabular figures | Dense rows remain comparable and actions distinct |

These describe roles, not mandatory pairings.
[Public award observations](award-research.md#what-the-examples-actually-support) include a film site loading three distinct families and a safari site pairing PP Fragment with Inter.
Neither establishes a formula for the next project.
[Pangram Pangram's Fragment specimen](https://pangrampangram.com/products/fragment) shows related Sans, Glare, Serif and Text cuts with variable options; this is one way a family can provide internal contrast.
[P22's foundry catalog](https://p22.com/) illustrates historical letterform sources; use a specimen to judge suitability instead of assigning every heritage brand the same serif.
Check licenses and available files at the foundry before production.
Do not extract a commercial font from an inspiration site's network requests for reuse.

## Establish scale and optical relationships

The following are starting ranges for Latin-script layouts, not Awwwards criteria or accessibility guarantees.
Adjust for the face's actual apparent size, the copy and the viewport.
Use the project's working system where it is already appropriate.

| Role | Useful starting size | Line height | Important constraint |
| :--- | :--- | :--- | :--- |
| Large desktop display | 64 to 128 px | 0.95 to 1.10 | Intentional line breaks; no clipped accents or descenders |
| Phone display | 36 to 64 px | 1.00 to 1.12 | Read the complete phrase without horizontal overflow |
| Section heading | 28 to 56 px | 1.05 to 1.20 | Clear contrast from body and display |
| Reading text | 16 to 20 px | 1.45 to 1.70 | Roughly 45 to 75 characters per line as a starting measure |
| UI and compact metadata | 14 to 16 px | 1.30 to 1.50 | Real device legibility; no essential content reduced to tiny labels |
| Large numeric fact | Chosen against its label and surrounding data | Usually 1.00 to 1.15 | Unit, period and meaning remain connected |

Choose a few roles rather than a new size for every section.
A modular ratio such as 1.2 or 1.25 can organize intermediate sizes; an expressive display title can break that scale deliberately.
Make the principal contrast visible without requiring the visitor to read every word.
A heading barely larger than its paragraph usually needs a stronger role distinction, not a shadow or accent bar.

Example fluid token, to be tuned in the actual face:

```css
:root {
  --text-body: clamp(1rem, 0.94rem + 0.3vw, 1.125rem);
  --text-display: clamp(2.75rem, 1.1rem + 6vw, 7rem);
}

.hero-title {
  font-size: var(--text-display);
  line-height: 1;
  letter-spacing: -0.025em;
  max-inline-size: 11ch;
}

.prose {
  font-size: var(--text-body);
  line-height: 1.55;
  max-inline-size: 65ch;
}
```

This is a specimen, not a starter theme.
`ch` measures the zero glyph and does not guarantee a particular line count.
Retest after the real font loads, at browser zoom and with longer text.
Avoid viewport-only font sizes that defeat text enlargement.

## Tune spacing rather than just size

For large Latin display text, try tracking near -0.01em to -0.04em and inspect each word.
Do not apply tight tracking to scripts or faces that need their default spacing.
Body text generally starts at normal tracking.
Short uppercase labels may benefit from 0.04em to 0.10em tracking, but should not become a repeated decorative eyebrow.

Inspect awkward pairs, punctuation, apostrophes, numerals and ligatures at actual display size.
If a particular ligature is unreadable, test that feature or a different cut before replacing the entire face.
Do not arbitrarily disable all font features.
Align text optically with adjacent imagery and controls; a curved letter may need a small optical correction that the CSS box does not reveal.
For custom wordmarks, compare apparent gaps and corner geometry, not just equal bounding-box distances.
Keep wordmark edits within scope.

Prefer intentional phrase breaks over accidental one-word final lines.
Use `text-wrap: balance` where supported if it improves the heading, but inspect the result.
Use explicit breaks only when they survive the intended viewport and content range; allow a different mobile composition.
Do not insert nonbreaking spaces throughout a heading to force a desktop line count.

Make spacing express relationships.
The gap from label to value should be smaller than the gap to the next group.
Align repeated labels, baselines, dates and actions on common edges.
Use tabular numerals for changing or comparable numeric columns, proportional numerals for ordinary prose.
Right-align comparable quantities with their units consistently.

## Use variable fonts deliberately

A variable font can provide continuous weight, width, slant, italic or optical-size control, but only axes present in that font work.
Prefer semantic CSS properties such as `font-weight`, `font-stretch` and `font-optical-sizing` before low-level axis overrides.
Declare the actual supported range in `@font-face`; a static weight declaration can prevent the intended range from being used.
Do not fake width with `scaleX()` or assume every variable font includes `opsz`.
[MDN's variable-font guide](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Fonts/Variable_fonts) documents these axes and their CSS mappings.

Use optical sizing to preserve readability across sizes when the family supports it.
A display cut's fine strokes may fail in a small caption even when its nominal size matches the body font.
Animate font axes only if changing letterform is part of the concept.
Weight or width changes can reflow text and incur layout work; test actual motion and reserve the required space.
Do not make essential reading text oscillate.

## Treat font loading as part of the design

Self-host licensed WOFF2 files when suitable, load only necessary styles and subset only when all required characters remain supported.
Preload only genuinely critical above-the-fold font resources with the correct URL, type and CORS behavior.
Use an intentional `font-display` strategy and a metrically compatible fallback.
`swap` keeps text available but can shift layout; `optional` may leave a first-time visitor on the fallback.
Measure the tradeoff rather than imposing one choice on every site.
Google's [font-loading guidance](https://web.dev/articles/font-best-practices) discusses discovery, preload, display policy and layout shift.

A full-page hidden state waiting on `document.fonts.ready` is not a reliable fix for a visible swap.
Keep useful text and navigation available if a font fails or the connection is slow.
For a font-dependent entrance, use the specific font's readiness with a bounded fallback and a static readable result.
Check cold and warm cache separately.
Watch the actual first paint and subsequent wraps, not just the settled screenshot.

## Typography acceptance checks

- All requested languages, symbols and weights render without missing glyphs or synthetic styles.
- Display, reading text, labels and controls have clear roles in the actual composition.
- Long titles, real names, dates and amounts fit at 320 and 390 CSS px without losing information.
- Phone headings are composed deliberately and hero actions remain within the intended opening view.
- At 200% text enlargement, content and controls remain usable.
- User text-spacing overrides do not clip or hide content.
  WCAG's test values are 1.5 line height, 2 times font-size paragraph spacing, 0.12em letter spacing and 0.16em word spacing; these are override tolerances, not required default styles.
  See [Text Spacing](https://www.w3.org/WAI/WCAG22/Understanding/text-spacing.html).
- Cold-load fallback, final font and failed-font states remain readable and stable.
- The result works in grayscale before color is asked to carry hierarchy.
