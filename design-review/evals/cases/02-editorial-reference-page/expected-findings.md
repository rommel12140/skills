# Case 02 - editorial reference page

Input: the anti-slop research brief, built 3 August 2026 under this catalog.
Stack: plain HTML and CSS, with the Tailwind browser runtime and DaisyUI over CDN.
`voice.md`: absent.

This case is the false-positive guard.
It is also the first real run of the catalog, and it found three things that were genuinely wrong.

## Gates that fired on the first pass

### A1 - Failing contrast - P0 - CONFIRMED, FIXED

20 text elements measured below their threshold against the computed background.

| Element | Size | Measured | Needed |
| :--- | :--- | :--- | :--- |
| Masthead eyebrow, `opacity-60` | 12px | 3.80 | 4.5 |
| Evidence footnote, `opacity-55` | 12px | 3.36 | 4.5 |
| Stat strip labels | 11.5px | 3.80 | 4.5 |
| DaisyUI `thead` cells | 14px | 3.80 | 4.5 |
| Mermaid edge labels | 16px | 4.43 | 4.5 |

Two causes, and the second is the interesting one:

1. Low `opacity-*` utilities on small text. Raising them to `opacity-75` cleared it.
2. **Stacked dimming.** DaisyUI dims `.label-text`, and the `(recommended)` spans inside the decision forms dimmed it again. Two independently reasonable choices compounded to 2.64:1 on 12px text. Neither author would have caught this by reading source, which is why `A1` is marked render-required.

After fixing: 253 text elements checked, zero failures.

Record this in the case as a fixed finding, not a passing one.
The eval input should remain the pre-fix page so the gate keeps being exercised.

### T1 - Default display face - P0 - CONFIRMED, ACCEPTED

The page declares no `font-family`.
It inherits the browser default sans, which is exactly the condition `T1` describes.

### T2 - One face at every size - P1 - CONFIRMED, ACCEPTED

No display and body pairing.

### C2 - Untouched component-library palette - P0 - CONFIRMED, ACCEPTED

DaisyUI's stock `luxury` theme, unmodified.

## Gates that passed

| ID | Why it passed |
| :--- | :--- |
| C1 | Two `gradient` matches, both inside quoted catalog text. Exempt. |
| C4 | All colours reference token variables via `color-mix`. |
| L1 | Masthead is left-aligned, not a centred column. |
| L2 | No three-card row anywhere. Sections use two-column or asymmetric grids. |
| L3 | Not the default page shape. |
| K1 | Uniform `rounded-box` radius, but no shadows at all, so no false elevation hierarchy. Borderline, recorded as a pass. |
| M1 | Zero `transition-all`. |
| I1 | Zero emoji. |
| CP1 | Section numbers 01 to 08 correspond to real sections on a reference page and serve navigation. This is the `CP1` exemption, not a violation. |
| X2 | Reference page carrying reference furniture. Correct match. |

## Gates skipped

| ID | Reason |
| :--- | :--- |
| CP3 | `voice.md` absent, so the allowed-numbers list does not exist. Every figure on the page was read from the GitHub API, but the gate cannot verify that. |
| X1 | `voice.md` absent, so there is no "Visual language" section to check against. |

## The tension this run exposed

`T1`, `T2`, and `C2` are all direct consequences of building the artifact on the recommended CDN fallback design system.

That fallback is the correct choice under Lavish's own design guidance, which says to use it when the subject project has no design system to match.
`global-agent-config` has none, so the fallback applied.

So `design-review` will flag every artifact built the recommended way.

Three ways out, and this needs a decision rather than a default:

1. Add an exemption class for internal review artifacts, where matching a house system beats having a distinct one.
2. Define a small house design system for the captain's own artifacts, which removes the fallback and makes the gates pass honestly.
3. Accept the findings as standing known deviations and record them per artifact.

Option 2 is the only one that makes the gates mean something.
Option 1 creates a hole that will widen.
