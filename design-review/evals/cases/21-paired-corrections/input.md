# Paired corrections on accepted components

Mode: Refine.
A fictional photography studio's site has an accepted row of four package cards and an account panel listing connected calendars.
The owner likes the cards' palette, order and content, and asks for them to look visibly better.
No browser or implementation fixture is supplied.
Work only from the following synthetic observations.

- One earlier attempt added a coloured status strip and a footer badge to each card and left the type and spacing unchanged; it was rejected as adding instead of changing.
- A second attempt changed only the card border from 1px to 1.5px; it was rejected because no difference was visible.
- The cards' text sits 8px from the card edge while the image inside each card sits 20px from it, so text and image start on different lines.
- The selected card has a heavy saturated fill that the owner called too loud; the unselected cards have no hover or focus state at all.
- In the account panel, each calendar row shows Reconnect and Disconnect as equal solid buttons in the same fill.
- A draft fix turned Disconnect into 11px grey text with no boundary, and a tester could not find it.
- The account rows use 32px vertical padding and loose line spacing, so only two of six calendars fit in the panel's visible area.

Describe the corrections and what you check before presenting.
Do not claim a rendered pass.
