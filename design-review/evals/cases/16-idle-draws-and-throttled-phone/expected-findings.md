# Expected decisions

Raise a P0 performance finding for the idle bowl: 300 draws and 300 layout reads in five seconds without input, with tickers that never sleep.
Prescribe render on demand: request a frame only on scroll, pointer, entrance, visibility or size changes, rest the sway at a fixed pose, and leave the ticker when each motion ends.
Hidden tabs cancel pending frames and recover when shown.

Raise a P0 finding for the kiln cards: masks, blurred filters and a live noise filter are redrawn on every frame of every move.
Prescribe plain paint drawn once and then moved with transform and opacity only, box shadows on static shapes instead of filters, a still image for the stamp's ink, and one soft shadow for the whole stack.
Identify the 20-updates-a-second print as reading as lag on its own and move it to the display rate.

Preserve the bowl, the rail and the card motion; the finding is cost, not concept.
Do not propose removing the 3D object or replacing the rail with a list.

Acceptance evidence must include a five-second idle sample with the draw count before and after, the throttled-phone trace with the count of frames over 25 ms before and after, and matched captures showing no visual change.
Do not restate the owner's 62% figure as a measurement of this page or promise a new task-manager number; say what a local profile can and cannot attribute.
Settled screenshots clear no performance finding.
Do not claim the fix is verified on a real phone when only emulation ran.
