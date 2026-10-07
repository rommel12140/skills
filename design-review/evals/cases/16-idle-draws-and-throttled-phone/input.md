# Idle draws and a throttled phone

Mode: Audit, then propose fixes.
A ceramics studio's portfolio opens with a 3D glazed bowl rendered in WebGL that sways gently all the time.
Its second chapter shows a stack of kiln cards hanging from a rail; choosing a firing on the board pulls that card to the front.
The owner likes both and says the site looks finished.
They report that their older laptop runs its fan with the page open and that choosing a kiln card on their phone stutters.

Synthetic supplied diagnostic evidence:

- A five-second sample with no input records 300 draw calls and 300 layout reads from the bowl canvas.
- The bowl, the smooth-scroll library and the contact section each keep a permanent animation-ticker listener registered.
- Each kiln card carries a mask for its torn edge, two blurred drop-shadow filters, and a live SVG noise filter for its stamp; one more blurred shadow covers the stack.
- In phone emulation with a four times slower CPU, choosing a card drops 98 of about 150 frames.
- The card's print-out animation advances in 14 steps at 20 updates a second.
- The owner's task manager screenshot groups a dozen browser processes at 62% CPU on another operating system.
- Settled screenshots at 1440 by 900 and 390 by 844 look correct in both themes.

Give the findings, the corrections and the acceptance evidence you would ship with them.
