# Resize overflow and clipped fragments

Mode: Refine.
A woodworking studio's page has a large condensed "RECENT WORK" heading pinned while the reader scrolls, over a plain ruled list of three projects.
The owner's screenshot at 1280 wide shows the last letter of the heading cut off by the right edge of the screen.
Behind the current job ticket in the workshop chapter, three older tickets peek out to the left with their words cut through, reading as "Ta", "Tab" and "Cof".
The owner also says the phone page is not as good as the desktop page.

Synthetic supplied diagnostic evidence:

- The heading is sized by a script that measures its box once on load; the pinned box keeps a fixed pixel width from the first layout.
- A page loaded at 1600 wide and narrowed to 1280 ends the heading at 1607 px; a fresh load at 1280 fits.
- The older tickets are offset by fixed pixel values, so the visible strip varies from 11 px to 48 px across widths.
- A floating contact tab sits over the list's right edge at 1024 wide.
- On the phone, project labels sit beside their names and wrap mid-word; the ticket stamp is 9 px tall.

Give the reproduction order, corrections and acceptance checks.
