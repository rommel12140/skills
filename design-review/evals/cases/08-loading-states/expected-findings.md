# Expected decisions

Identify `K6` and distinguish initial content loading from background refresh and session checking.
Preserve the page shell, filter controls and usable loaded data.
Use skeleton geometry matching summary blocks and table columns where content is genuinely pending.
Do not use unrelated card silhouettes, decorative pulsing dots or a full-page spinner as the content layout.

Model loaded, pending, empty, partial, failed and retry outcomes separately.
No records is a completed result, not a loading state.
Keep a visible recovery button, truthful state wording and stable busy controls.
Use a static reduced-motion skeleton, hide decorative shapes from assistive technology and announce status appropriately once.

The brief session check may use the accepted animation because the content geometry is not yet known.
It still needs bounded failure/recovery handling and must not manufacture a minimum waiting time.
Test fast, slow, empty, partial, offline/failed and successful responses.
