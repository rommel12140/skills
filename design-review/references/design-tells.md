# Design tells

Forty-two entries in ten categories.
Every entry has a stable ID, a severity, whether it needs a rendered page, and a gate phrased so that an affirmative answer fails.

Stack-specific fixes live in `fixes-by-stack.md`, keyed by the same IDs.

## Severity

| Level | Meaning | Action |
| :--- | :--- | :--- |
| P0 | Reads as machine-made on sight, or is factually wrong | Fix every occurrence |
| P1 | An obvious smell | Fix on every pass |
| P2 | Cosmetic | Lower priority |

## Categories

| Prefix | Category | Origin |
| :--- | :--- | :--- |
| T | Typography | upstream |
| C | Colour and gradients | upstream |
| L | Layout and composition | upstream |
| K | Components | upstream |
| M | Motion | upstream |
| I | Icons | upstream |
| CP | Copy and microcopy in UI | upstream |
| IM | Imagery | upstream |
| A | Accessibility and contrast | hallmark |
| X | Context fit | the captain's own rules |

---

## T - Typography

### T1 - Default display face - P0 - render: no

Gate: Is the display or heading font Inter, Roboto, Open Sans, Poppins, Lato, Montserrat, or a system default?
Detect: `font-family` declarations, `@font-face` sources, Google Fonts links, Webflow font settings.
Why: these are the fonts that appear when nobody chose a font.
Instead: pick a display face with a point of view and pair it with a body face that stays readable at small sizes.

### T2 - One face at every size - P1 - render: no

Gate: Does the page use a single typeface for display, body, and interface text with no pairing?
Why: it flattens the hierarchy and removes the strongest available signal of intent.
Instead: a display and body pairing at minimum. Optionally a third for interface or monospace detail.

### T3 - Italic display type - P2 - render: no

Gate: Is any `h1` through `h6`, hero title, or section title set in `font-style: italic`?
Exempt: a face whose italic is a genuine design decision and appears consistently.
Why: reflexive italic on headings reads as emphasis applied without a reason.
Instead: use weight, size, or colour for hierarchy.

---

## C - Colour and gradients

### C1 - The purple-to-blue diagonal gradient - P0 - render: no

Gate: Does the page contain a linear gradient running from a purple or indigo to a blue, on a hero, a button, or a background?
Detect: `linear-gradient` declarations, gradient fills in Webflow, gradient utility classes.
Why: it is the single most recognisable machine-design signature.
Instead: a flat colour drawn from the project's own palette. If a gradient is genuinely wanted, take both stops from the brand and keep the hue travel short.

### C2 - Untouched component-library palette - P0 - render: no

Gate: Are the shadcn, DaisyUI, Material, or Bootstrap default colours still in place?
Detect: default theme names in config, unmodified CSS variables, `btn-primary` rendering the library's stock colour.
Why: the design has not been made, only installed.
Instead: define the palette in tokens first, then let the components read from it.

### C3 - Gradient-mesh blobs and neon-on-dark - P0 - render: yes

Gate: Does the page use abstract gradient-mesh backgrounds, floating blurred colour blobs, or neon accents on a dark field as atmosphere?
Why: decoration with no relationship to the page's subject.
Instead: if the background needs to do something, let it do something the content needs. Otherwise leave it flat.

### C4 - Colour declared outside the tokens - P1 - render: no

Gate: Is any colour value declared outside the design token layer? Hex, `rgb()`, `hsl()`, or `oklch()` sitting inline or in a component file.
Why: it is how a palette drifts, and it makes theming impossible.
Instead: add the value to the token set and reference it.

### C5 - Pure black as a surface or text colour - P1 - render: no

Gate: Is `#000000`, `black`, or `rgb(0, 0, 0)` used as a page background, a surface, or body text?
Detect: colour declarations and token definitions. Check the dark theme as well as the light one.
Why: pure black is the value that appears when nobody picked a value, and against white it gives small text enough contrast to shimmer.
Instead: an off-black from the project's own palette, usually the darkest neutral with a trace of the brand hue in it.

---

## L - Layout and composition

### L1 - The centred hero template - P0 - render: yes

Gate: Is the hero a centred column: eyebrow, centred headline, centred subhead, one or two centred buttons?
Why: it is the default hero, chosen by nothing.
Instead: break the axis. Set the headline left with the supporting text in a narrow second column, or lead with an image, a quote, or a number.

### L2 - Three equal-width icon-topped cards - P0 - render: no

Gate: Does any section render three sibling cards of equal width where each one opens with an icon?
Detect: a grid with exactly three children sharing a class, each containing an `svg` or icon component above a heading. Search for `grid-cols-3` near a repeated card class.
Why: it is the training distribution's default feature section.
Instead: break the row. Unequal spans, a numbered list with hanging numerals, or one annotated screenshot carrying all three claims.

### L3 - The full default page shape - P0 - render: no

Gate: Does the page run hero, three features, testimonial, CTA, footer, in that order?
Why: the structure is the template, not the argument.
Instead: decide what the page has to prove, then order the sections so each one earns the next.

### L4 - Hero content below the fold - P1 - render: yes

Gate: At 1280x800, is any of the hero's essential content (headline, primary action) below the fold?
Why: 1280x800 is the common laptop, and heroes are routinely tuned at 1440x900 where the problem is invisible.
Instead: reduce the vertical padding, shrink the display size, or move the action up.

### L5 - Hairlines and crosshairs as decoration - P1 - render: yes

Gate: Does the page draw vertical rules, horizontal hairlines, or crosshair marks that no content aligns to?
Exempt: a rule that separates real content, and a grid the layout genuinely sits on.
Why: the lines are there to make the page look constructed, and a line nothing aligns to is the opposite of construction.
Instead: delete them. If the layout has a grid worth showing, align the content to it first, then decide whether the line still adds anything.

### L6 - Rotated vertical text - P1 - render: no

Gate: Is any text rotated to run vertically, as a side label, a section marker, or an edge caption?
Detect: `writing-mode: vertical-rl`, and `transform: rotate(90deg)` or `rotate(-90deg)` on a text element.
Exempt: a language set vertically by convention, and a table header where rotation is the only way the column fits.
Why: it is the agency-portfolio flourish, applied because the margin was empty rather than because the text belongs there.
Instead: set the text horizontally where the reader is already looking, or cut it. Most rotated labels are labels nobody needed.

---

## K - Components

### K1 - Uniform rounding and shadow - P1 - render: no

Gate: Do all surfaces carry the same corner radius and the same shadow, typically a large radius with a soft large shadow?
Why: no radius or elevation hierarchy means every element claims the same importance.
Instead: build a radius scale and an elevation scale, then assign by role. Flat for structure, raised for the thing that lifts.

### K2 - Reflexive glassmorphism - P0 - render: yes

Gate: Does the page use frosted or translucent panels with backdrop blur where a solid surface would work?
Why: it is applied as a style rather than to solve a layering problem, and it usually costs contrast.
Instead: a solid surface. Reserve blur for cases where content genuinely passes behind the panel.

### K3 - Icon in a rounded-square chip - P1 - render: no

Gate: Are icons wrapped in a rounded square or circle with a tinted background?
Why: it is the stock feature-card ornament.
Instead: set the icon inline with the text, at text size, or remove it. Most of these icons carry no meaning.

### K4 - Colour-accent border cards - P1 - render: no

Gate: Do cards or callouts carry a coloured left or top border as their only distinguishing mark?
Why: it substitutes a stripe for a design decision.
Instead: distinguish by surface, spacing, or type. If the colour carries status, pair it with a label so it is not the only signal.

### K5 - Colour dots that carry no state - P1 - render: no

Gate: Does a coloured dot sit before nav links, list rows, badges, or headings without indicating a state?
Exempt: a dot reporting real state, such as a service being up or a slot being open, used once or twice rather than on every row.
Why: it is the stock ornament for making a list look like a dashboard, and it teaches the reader that colour means nothing here.
Instead: remove the dot. Where something genuinely has state, keep it and add a text label, so colour is not the only signal.

---

## M - Motion

### M1 - transition-all - P1 - render: no

Gate: Does any rule use `transition: all` or the `transition-all` utility?
Why: it animates properties nobody chose, including layout properties, and it costs performance.
Instead: name the properties. `transition: background-color 150ms, transform 150ms`.

### M2 - Focus ring that fades in - P1 - render: yes

Gate: Does the focus ring transition into existence rather than appearing immediately?
Why: keyboard users need the ring to be present the instant focus lands.
Instead: exclude the focus ring from transitions.

### M3 - Glowing nodes and connected dots - P0 - render: yes

Gate: Does the page use thin lines with glowing circle nodes, connected-dot networks, halos, or pulsing dots as decoration?
Why: it is generic technology iconography that means nothing about this product.
Instead: draw the real thing. If a system is being shown, draw the system. If nothing needs drawing, leave it out.

---

## I - Icons

### I1 - Emoji as interface iconography - P0 - render: no

Gate: Are emoji used as bullets, section markers, status indicators, or button icons?
Exempt: interfaces genuinely about emoji, and user-generated content.
Why: emoji render differently on every platform and carry a tone the interface has not chosen.
Instead: a real icon set, or no icon.

### I2 - The stock Lucide set, unmodified - P1 - render: no

Gate: Are the most common Lucide glyphs used at default weight and size throughout? Zap, sparkles, rocket, shield, check-circle.
Why: they are the default icons of the default design.
Instead: choose icons that name the specific thing, adjust the weight to match the type, or drop icons entirely.

---

## CP - Copy and microcopy in UI

### CP1 - Invented pseudo-technical labels - P0 - render: no

Gate: Does the interface contain labels like Q-01, SECTION 01, Note 02.1, Route A, or Phase III where no such numbering exists in the product?
Why: it performs technical seriousness the content has not earned.
Instead: name the section. If numbering helps navigation on a reference page, use plain numbers that correspond to something real.

### CP2 - Arrow glyphs stapled to link text - P1 - render: no

Gate: Do links and buttons carry a trailing arrow character as decoration?
Exempt: an arrow that moves on interaction and indicates direction of travel.
Why: it is ornament applied uniformly rather than a wayfinding signal.
Instead: let the link text carry the meaning.

### CP3 - Unlisted quantitative claim - P0 - render: no

Gate: Does the interface state a figure not listed under "Numbers we are allowed to state" in `voice.md`?
Why: placeholder statistics survive into production more often than anyone expects.
Instead: use a listed figure, source the new one and add it to `voice.md`, or remove the claim.

### CP4 - Copy tells in interface strings - P1 - render: no

Gate: Do headings, button labels, empty states, or tooltips contain anything from the `copy-review` catalog?
Why: interface copy is written last and reviewed least.
Instead: run `copy-review` over the extracted strings.

### CP5 - Fabricated version, build, or live status - P0 - render: no

Gate: Does the interface state a version, build string, release stage, or live reading that is not true of the product? `V0.6`, `v0.6.2-rc.1`, `BETA`, `EARLY ACCESS`, `INVITE-ONLY PREVIEW`, `last sync 4s ago`, `Reservation 412 of 800`, a clock or a temperature wired to nothing.
Detect: eyebrows above the hero, footer strips, and the small type inside any product preview.
Exempt: a real version, a release stage the project is actually in, and a reading wired to real data.
Note: `CP1` covers section and step numbering. `CP3` exempts version numbers, because it checks claims against `voice.md` rather than checking whether the product has that version.
Why: it invents product state to make the page look like a running system, and unlike a wrong colour it is a factual claim that is false.
Instead: state the real version or stage, wire the reading to real data, or delete the element.

### CP6 - The middle dot as the default separator - P2 - render: no

Gate: Does any single line carry more than one middle dot, or is the middle dot the separator throughout the nav, the meta strips, the captions, and the footer?
Detect: search for the `·` character and for `&middot;`, and count per line rather than per page.
Why: one middle dot is a separator and four are a texture, and the texture is the tell.
Instead: ration it to one per line. Where more structure is needed, use a line break or a second column.

### CP7 - Placeholder people and companies - P0 - render: no

Gate: Does the interface name a person, contact, or company that does not exist? "John Doe", "Jane Smith", `name@example.com`, `(555) 123-4567`, "123 Main Street", an egg avatar or a stock user glyph, and invented brands such as "Acme", "Nexus", or "SmartFlow".
Detect: avatar image sources, testimonial attributions, the logo row, and the footer contact block. These are the four places a template's stand-ins survive longest.
Why: mockups made here have reached clients with the template's contact block still in them, which is how a client finds out the page was not built for them.
Instead: use the client's real people, contacts, and logos. Where a real one does not exist yet, remove the element rather than filling it, so the gap stays visible.

### CP8 - Figures with placeholder shape - P0 - render: no

Gate: Does any figure have the shape of a number nobody measured? `99.99%`, `50%`, `100%`, `1234567`, `10,000+`, `24/7`, `4.9/5`, or a row of stat tiles that are all round.
Exempt: a figure listed under "Numbers we are allowed to state" in `voice.md`, and a value read from live data.
Note: `CP3` asks whether a figure is sourced, and cannot run without `voice.md`. This gate asks whether the figure reads as invented, and runs either way.
Why: template content ships, and pages built here have gone out to clients carrying the sample data's round numbers.
Instead: use the measured figure, or cut the claim. Where a mockup genuinely needs sample data, make it uneven, because real data is uneven.

### CP9 - Performative section labels - P1 - render: no

Gate: Does a section, sidebar, or quote block carry a crafted label in place of a functional one? "Field notes", "On our desks", "Currently on the bench", "Loose plates", "Quietly trusted by".
Why: the label performs a temperament instead of naming what sits under it, so the reader has to read the section to find out what the section is.
Instead: name it plainly. "Testimonials", "Latest writing", "Trusted by", "What we are working on now". Where the content is obvious without a label, drop the label.

---

## IM - Imagery

### IM1 - Abstract 3D render stock - P1 - render: yes

Gate: Does the page use glossy 3D blobs, floating geometric shapes, or abstract render stock imagery?
Why: it fills space without saying anything about the product.
Instead: show the product, the people who use it, or the work it produces. If none of those can be shown, show nothing.

### IM2 - Fake product UI built from divs - P0 - render: no

Gate: Is a product preview built out of styled divs rather than an image? A fake dashboard, a fake terminal with a window bar and three dots, a fake task list, a fake chat thread.
Detect: a deep div tree in the hero or a feature section with no `img` inside it, carrying window chrome, monospace text rows, or repeated identical list items.
Why: it shows an interface the product may not have, assembled to fill the space where a screenshot would go.
Instead: a screenshot of the real product. Where there is nothing to screenshot yet, show nothing, because an empty hero is more honest than an invented one.

---

## A - Accessibility and contrast

### A1 - Failing contrast - P0 - render: yes

Gate: Does any text, icon, or focus ring fail its contrast threshold against its computed background?
Detect: compute against the rendered background, not the declared one. Overlays, gradients, and translucent panels change the actual value.
Why: low-contrast grey on white is a house style in machine-made interfaces, and it is a genuine barrier.
Instead: raise the foreground contrast until it passes. Do not solve it by making the text larger.

### A2 - Border width shifting between states - P2 - render: no

Gate: Does an input's border width change between default, hover, focus, and error?
Why: the element moves by a pixel on interaction, and neighbouring content shifts with it.
Instead: hold the width constant and change the colour, or use an outline that does not affect layout.

### A3 - Wrapping control labels - P1 - render: yes

Gate: Does any button label, primary nav link, tab label, breadcrumb, or CTA wrap to two or more lines?
Why: a wrapped control reads as broken, and it usually means the label is doing too much.
Instead: shorten the label. If it cannot be shortened, widen the control.

### A4 - Custom mouse cursor - P1 - render: no

Gate: Does the page replace the system cursor with an image, hide it, or attach a following element to the pointer?
Detect: `cursor: url(...)`, `cursor: none`, and any component tracking `mousemove` to position a dot or a ring.
Why: it overrides the cursor size, contrast, and shape a person set in their operating system, which for some people is the setting that makes a screen usable.
Instead: keep the system cursor. Where hover feedback is wanted, put it on the element being hovered.

---

## X - Context fit

These three are the captain's own rules.
No published skill encodes them, and they catch what the catalogs above cannot.

### X1 - Visual language not drawn from the client's world - P0 - render: yes

Gate: Does the page's visual language come from generic software decoration rather than from the client's industry and the page's job?
Requires: the "Visual language" section of `voice.md`. Without it, report this gate as skipped.
Ask: what is the equivalent mark in this industry, and does the rest of the site already use it?
Why: this is what separates a page made for this client from a page made for anyone.
Instead: take the motif from the client's own material. Their forms, their instruments, their documents, their product, their trade.

### X2 - Layout does not match the page's job - P0 - render: no

Gate: Does the page use reference furniture on a persuasion page, or persuasion furniture on a reference page?
Reference furniture: index rails, numbered clauses, sticky tables of contents, dense tables.
Persuasion furniture: full-bleed heroes, staged reveals, testimonial blocks, closing CTAs.
Why: an index rail kills a persuasion page, and a hero wastes a reference page.
Instead: decide what the page is for, then pick the furniture that serves it.

### X3 - Every section reveals identically - P1 - render: yes

Gate: Does every section animate in with the same opacity 0 to 1 plus a small translateY?
Why: an animation applied uniformly is decoration, not communication.
Instead: each animation should perform its section's argument, and should differ from the one above it. A section with no argument to perform should not animate at all.
