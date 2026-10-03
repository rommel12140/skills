# Expected decisions

Reproduce cold navigation and the actual phone viewport before changing source.
Treat the heading shift as a first-load composition defect and the zero-sized wrapper as a responsive layout defect.
Successful image requests and a settled screenshot do not clear either defect.

Fix critical-font discovery and the fallback's metrics/line fit using a deliberate loading strategy.
Do not hide the whole page indefinitely behind `document.fonts.ready` or wait through a fabricated loader.
Use the real supported font axes and license; no copied commercial font files from reference sites.
Fix responsive sizing at the responsible wrapper and inspect its crop and focal subject.

Check cold/warm cache, blocked font, slower network, 1280x800, true mobile dimensions, 320px stress width and text enlargement.
See actual first-paint and settled states, not geometry alone.
Do not claim real-phone performance from desktop emulation.
