# Expected decisions

Reproduce the overflow by loading wide and narrowing without reload, and the fragments at several widths, before changing source.
Size the heading in CSS from its column width and the viewport height and remove the measuring script; a resize handler that re-measures is a weaker fix than no measurement.
Make the pinned box recompute its geometry on resize.

Treat the heading over a plain ruled list as an uncomposed section, not only an overflow: propose a lockup, an index or a transition the subject supplies, while keeping the accepted content and order.

For the tickets, measure the overlap as a share of the rail's width so the stack reads the same on a narrow phone and a wide desktop, and narrow the visible strips before the words when the rail is short.
Each ticket behind shows a whole item, such as its number, or nothing of the text.
Verify with a hit test over every text run at 320, 390, 768, 1024, 1280, 1440 and 2560, not by inspecting one width.

Reserve space for the floating tab so no content runs under it.
Compose the phone as its own page: stack labels under names, enlarge the stamp and small indicators, and capture at a true phone viewport with touch emulation and DPR 3.

Acceptance checks: no element passes either edge at the seven widths, the same after a wide-to-narrow resize and back, zero partially visible text runs, and before and after captures at 1440, 1024 and 390.
Do not restyle the accepted colour, type or motion of the chapter beyond the named defects.
