# First load and mobile

Mode: Refine.
The settled desktop screenshot looks correct.
Users report a visibly different heading on first load and a missing project image on phones.

Synthetic supplied diagnostic evidence:

- Warm navigation uses the intended licensed variable face.
- Cold navigation paints a fallback, then changes the title from two lines to four before settling at three.
- The critical font is discovered only after a late stylesheet.
- A mobile ancestor sets the media wrapper to zero height.
- The image request succeeds and its natural dimensions are correct.
- The prior reviewer resized a desktop window but did not check `innerWidth` or mobile viewport metadata.

Give the reproduction order, corrections and acceptance checks.
