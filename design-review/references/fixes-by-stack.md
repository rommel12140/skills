# Fixes by stack

Keyed to the IDs in `design-tells.md`.
Report only the column matching the stack in use.

Webflow fixes are Designer operations and class changes, not CSS to paste.
Pasting CSS into a Webflow embed defeats the class system and is not a fix.

---

## T1 - Default display face

- **HTML/CSS**: replace the `@font-face` or font link, then set the display face on a `--font-display` token and the body face on `--font-body`.
- **React/Tailwind**: change `fontFamily.display` and `fontFamily.sans` in the theme, not per-component classes. Remove any `font-[Inter]` arbitrary values.
- **Webflow**: upload the display face under Site settings, Fonts. Set it on the `h1` through `h6` tag selectors so it inherits, rather than on individual elements.

## T2 - One face at every size

- **HTML/CSS**: introduce a second token and apply it to headings only.
- **React/Tailwind**: add `font-display` to the heading components; leave body on the default sans.
- **Webflow**: set the display face on the heading tag selectors, body face on the Body (All Pages) selector.

## T3 - Italic display type

- **HTML/CSS**: remove `font-style: italic` from heading rules.
- **React/Tailwind**: drop the `italic` utility from heading components.
- **Webflow**: clear the italic style on the affected tag selector, not on each instance.

---

## C1 - Purple-to-blue gradient

- **HTML/CSS**: replace the `linear-gradient` with a flat token colour. If a gradient stays, take both stops from the brand palette.
- **React/Tailwind**: remove `bg-gradient-to-*` with `from-purple-*`/`to-blue-*`. Use a single `bg-[--color-surface]` token.
- **Webflow**: open the background gradient editor and either delete the gradient or set both stops to swatches from the project's global palette.

## C2 - Untouched library palette

- **HTML/CSS**: define the palette in `:root` custom properties and point the component CSS at them.
- **React/Tailwind**: override the theme colours in the Tailwind config or the DaisyUI theme block. Do not restyle components individually.
- **Webflow**: create global swatches, then reassign every element that currently uses a default colour.

## C3 - Gradient-mesh blobs and neon-on-dark

- **HTML/CSS**: delete the decorative layers. If the background must carry something, use a flat surface token.
- **React/Tailwind**: remove the absolutely positioned blurred divs and the `blur-3xl` utilities.
- **Webflow**: delete the decorative div blocks from the hero. They are usually absolutely positioned children with a large blur filter.

## C4 - Colour outside the tokens

- **HTML/CSS**: move the value into `:root` and reference it.
- **React/Tailwind**: replace arbitrary values such as `bg-[#7c3aed]` with a theme colour.
- **Webflow**: convert the one-off colour into a global swatch, then reapply it.

## C5 - Pure black as a surface or text colour

- **HTML/CSS**: change the value in the token definition to an off-black, then grep for `#000`, `#000000`, `black`, and `rgb(0, 0, 0)` to catch the rules that bypassed the token.
- **React/Tailwind**: replace `bg-black` and `text-black` with a named theme colour. Reaching for the utility again is how the value comes back.
- **Webflow**: edit the black swatch in the global palette, which updates every element using it. Then check for elements set to the built-in Black rather than to the swatch, because those do not follow.

---

## L1 - Centred hero

- **HTML/CSS**: change the hero container from a centred column to a grid. Put the headline in the first span and the supporting text in a narrower second span.
- **React/Tailwind**: replace `text-center items-center mx-auto` on the hero with a `grid` and explicit spans.
- **Webflow**: change the hero wrapper's layout from flex-centre to grid, then place the heading and supporting text in different columns.

## L2 - Three equal-width icon-topped cards

- **HTML/CSS**: replace the three-column grid with an ordered list using hanging numerals, or with unequal spans.
- **React/Tailwind**: replace `grid-cols-3` with an asymmetric span layout, drop the icon chip, and lead each item with its claim.
- **Webflow**: unlink the third card from its symbol or component instance, then re-lay the section on the 12-column grid with unequal spans.

## L3 - Default page shape

- **HTML/CSS**: reorder the sections so each one earns the next. This is an editing decision, not a CSS one.
- **React/Tailwind**: same. Reorder the section components in the page file.
- **Webflow**: reorder the sections in the Navigator panel.

## L4 - Hero content below the fold at 1280x800

- **HTML/CSS**: reduce the hero's vertical padding and the display font size at that breakpoint.
- **React/Tailwind**: lower `py-*` on the hero and add a smaller display size at the `lg` breakpoint.
- **Webflow**: reduce the section padding on the Desktop breakpoint, and check the 1280 preview rather than only the widest.

## L5 - Hairlines and crosshairs as decoration

- **HTML/CSS**: delete the absolutely positioned rule divs and the crosshair pseudo-elements. Where a rule genuinely separates content, put a `border` on the content element rather than drawing a layer over it.
- **React/Tailwind**: remove the decorative overlay component. It is usually an absolutely positioned div carrying `border-l` on repeated children, or a `repeating-linear-gradient` background.
- **Webflow**: delete the line div blocks from the section in the Navigator. They are usually 1px absolutely positioned children of the section wrapper, so the section itself needs no change.

## L6 - Rotated vertical text

- **HTML/CSS**: remove the `writing-mode` declaration or the rotate transform, then place the text horizontally or delete the element.
- **React/Tailwind**: drop `[writing-mode:vertical-rl]` or `rotate-90` from the label, and check whether the column it occupied is still needed.
- **Webflow**: clear the rotation in the text block's Effects panel, or delete the text block. Shrinking the font is not the fix.

---

## K1 - Uniform rounding and shadow

- **HTML/CSS**: define a radius scale and an elevation scale as tokens, then assign by role.
- **React/Tailwind**: define `borderRadius` and `boxShadow` scales in the theme and stop using `rounded-2xl shadow-lg` as a default.
- **Webflow**: create classes for each elevation role rather than applying the same combo class everywhere.

## K2 - Reflexive glassmorphism

- **HTML/CSS**: replace the translucent panel with a solid surface token and remove `backdrop-filter`.
- **React/Tailwind**: remove `backdrop-blur-*` and `bg-white/10`, use a solid surface colour.
- **Webflow**: clear the background blur filter and set an opaque background colour.

## K3 - Icon in a rounded-square chip

- **HTML/CSS**: remove the chip wrapper and set the icon inline at text size.
- **React/Tailwind**: delete the wrapping div carrying `rounded-lg bg-primary/10 p-3`.
- **Webflow**: delete the icon wrapper div and place the icon inline, or remove it.

## K4 - Colour-accent border cards

- **HTML/CSS**: remove `border-left`, distinguish by surface colour or spacing. If the colour carries status, add a text label.
- **React/Tailwind**: drop `border-l-4 border-primary`, use a distinct surface token and a status label.
- **Webflow**: remove the left border on the card class and add a status text element.

## K5 - Colour dots that carry no state

- **HTML/CSS**: delete the dot element, or the `::before` that draws it. Where the dot reports real state, keep it and put a text label beside it.
- **React/Tailwind**: remove the `h-2 w-2 rounded-full bg-*` span from the shared list item or nav link component. Removing it once clears every instance.
- **Webflow**: delete the dot div from the list item or nav link. If it sits inside a component, edit the component so it clears everywhere rather than deleting instances one by one.

---

## M1 - transition-all

- **HTML/CSS**: name the properties explicitly in the `transition` shorthand.
- **React/Tailwind**: replace `transition-all` with `transition-colors`, `transition-transform`, or `transition-opacity`.
- **Webflow**: in the element's Transitions panel, remove "All properties" and add each property separately.

## M2 - Focus ring fading in

- **HTML/CSS**: exclude `outline` and `box-shadow` from the transition on focusable elements.
- **React/Tailwind**: narrow the transition utility so it does not cover the ring, or add `focus-visible:transition-none`.
- **Webflow**: remove the transition on the focus state of the element.

## M3 - Glowing nodes and connected dots

- **HTML/CSS**: delete the decoration. If a system needs showing, draw the actual system.
- **React/Tailwind**: remove the SVG or canvas decoration component.
- **Webflow**: delete the decorative embed or Lottie element.

---

## I1 - Emoji as iconography

- **HTML/CSS**: replace with an icon from the project's set, or remove and rely on the label.
- **React/Tailwind**: same, and check empty states and toast messages, where emoji collect.
- **Webflow**: replace the emoji text with an icon element, or delete it.

## I2 - Stock Lucide set

- **HTML/CSS**: choose icons that name the specific thing, and match their stroke weight to the type.
- **React/Tailwind**: same. Set a consistent `strokeWidth` rather than accepting the default.
- **Webflow**: replace the icon assets. Check the stroke weight reads at the size used.

---

## CP1 - Invented pseudo-technical labels

- **HTML/CSS**: replace with a real section name, or delete the label.
- **React/Tailwind**: same. These usually live in a section header component.
- **Webflow**: edit the eyebrow text element, or delete it.

## CP2 - Arrow glyphs on links

- **HTML/CSS**: remove the trailing character. If direction matters, use an icon that moves on hover.
- **React/Tailwind**: remove the arrow from the link component's children.
- **Webflow**: delete the arrow text or icon inside the link block.

## CP3 - Unlisted quantitative claim

- Stack-independent. Use a figure from `voice.md`, source the new one and add it there, or remove the claim.

## CP4 - Copy tells in interface strings

- Stack-independent. Extract the strings and run `copy-review` over them.

## CP5 - Fabricated version, build, or live status

- **HTML/CSS**: delete the version eyebrow, the footer build string, and any static "last sync" or counter line. Where a reading should be live, replace the hardcoded string with the value from its source.
- **React/Tailwind**: these are usually literal strings in a hero or footer component. Delete them, or pass the real value in as a prop so it cannot go stale.
- **Webflow**: delete the eyebrow text element and the footer version text. Where the reading should be real, bind it to a CMS field rather than typing it into the Designer.

## CP6 - The middle dot as the default separator

- **HTML/CSS**: keep one middle dot per line and replace the rest with a line break or a second column. A meta strip carrying four fields is a list, not a sentence.
- **React/Tailwind**: stop joining the array with `" · "`. Render the fields as flex children with a `gap-*` and no separator character.
- **Webflow**: split the single text element into separate text elements inside a flex wrapper with a gap, rather than typing the dots into the string.

## CP7 - Placeholder people and companies

- **HTML/CSS**: replace the name, email, phone, address, avatar `src`, and logo files with the client's real ones. Where a real one does not exist yet, delete the element so the gap is visible at review rather than at launch.
- **React/Tailwind**: testimonials and team members usually sit in an array in the page file. Empty the array and let the component render nothing, rather than leaving stand-in entries in it.
- **Webflow**: replace the text in the contact block and swap the avatar and logo assets. Where the people come from a CMS collection, delete the seeded template items rather than editing them, because a half-edited seed item is what ships.

## CP8 - Figures with placeholder shape

- **HTML/CSS**: replace the figure with the measured value, or remove the stat block. Add the new figure to `voice.md` so `CP3` can check it on the next pass.
- **React/Tailwind**: stat tiles are usually an array of objects in the page file. Remove the entries that have no measured value rather than rounding them to something plausible.
- **Webflow**: edit the number text elements, and where they come from a CMS collection, clear the seeded values. Check the published page as well as the Designer, since a stale figure can survive in a published version.

## CP9 - Performative section labels

- **HTML/CSS**: replace the eyebrow text with a plain name, or delete the eyebrow and let the heading carry the section.
- **React/Tailwind**: these arrive as a `label` or `eyebrow` prop on a section header component. Change the value at the call site, not in the component.
- **Webflow**: edit the eyebrow text element, or delete it and check the heading's top margin still holds without it.

---

## IM1 - Abstract 3D render stock

- **HTML/CSS**: replace with a real screenshot, a photograph of the work, or nothing.
- **React/Tailwind**: same, and check the image is not being served at hero size for a decorative role.
- **Webflow**: swap the asset, or delete the image element and let the layout close up.

## IM2 - Fake product UI built from divs

- **HTML/CSS**: replace the div tree with one `img` of a real screenshot, sized, with an `alt` describing what it shows. Where there is no product to screenshot, delete the block and let the hero close up.
- **React/Tailwind**: delete the mock preview component. Do not keep it behind a flag, because a flagged mock is a mock that ships.
- **Webflow**: delete the preview div block in the Navigator and put an image element in its place. The screenshot usually loads faster than the div tree it replaces.

---

## A1 - Failing contrast

- **HTML/CSS**: raise the foreground colour until it passes against the computed background. Do not solve it by increasing font size.
- **React/Tailwind**: replace `text-muted-foreground` or `text-gray-400` on small text with a token that passes.
- **Webflow**: change the text colour swatch. If the text sits over an image, add a solid scrim rather than lowering the image opacity.

## A2 - Border width shifting between states

- **HTML/CSS**: hold `border-width` constant across states and change colour instead.
- **React/Tailwind**: avoid `focus:border-2`. Use `focus:ring-2` with `ring-offset`, which does not affect layout.
- **Webflow**: set the same border width on default, hover, focus, and error states.

## A3 - Wrapping control labels

- **HTML/CSS**: shorten the label. If it cannot be shortened, widen the control or reduce its horizontal padding.
- **React/Tailwind**: same, and add `whitespace-nowrap` only after the label is genuinely short enough to fit.
- **Webflow**: shorten the button text, or widen the button and check every breakpoint.

## A4 - Custom mouse cursor

- **HTML/CSS**: remove `cursor: url(...)` and `cursor: none`, then delete the pointer-following element and its `mousemove` listener.
- **React/Tailwind**: delete the cursor component and its provider, and remove `cursor-none` from the body or layout wrapper.
- **Webflow**: delete the cursor interaction in the Interactions panel and remove the custom code embed that positions the follower. Both usually exist, and removing one leaves the other.

---

## X1 - Visual language not from the client's world

- Stack-independent, and the most expensive to fix, because it is a direction rather than a property.
- Return to `voice.md`, answer what the equivalent mark is in this industry, then rebuild the decorative layer from that answer.
- If `voice.md` has no "Visual language" section, this finding is a request to write one, not a code change.

## X2 - Layout does not match the page's job

- Stack-independent. Decide what the page is for, then remove the furniture that belongs to the other kind of page.
- Reference furniture on a persuasion page: remove the index rail, the clause numbering, and the sticky contents.
- Persuasion furniture on a reference page: remove the full-bleed hero, the staged reveals, and the closing CTA.

## X3 - Every section reveals identically

- **HTML/CSS**: remove the shared reveal class. Keep motion only where it performs the section's argument.
- **React/Tailwind**: remove the shared animation wrapper applied at the section level.
- **Webflow**: remove the page-level scroll interaction applied to every section, and rebuild motion only where it earns its place.
