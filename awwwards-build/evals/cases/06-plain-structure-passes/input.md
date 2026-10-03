# Case 06 input

Mode: acceptance pass over an existing plan, no browser available.
Run the source-checkable gates in `references/acceptance.md` against this plan.

> **Product page plan for a maker of cast-iron cookware, three pan sizes**
>
> Argument: our pans are heavy because the base is thick, and the thick base is what keeps the heat even; pick the size that fits your hob and household.
>
> 1. Opening: one pan photographed from the side on a hob, base edge in sharp focus, with the name, the price range and "Choose a size".
>    Next section follows directly so the thickness claim lands while the photo is still in mind.
> 2. Why it is heavy: a cutaway photo of the base beside two short paragraphs, the caption naming the measured base thickness from the spec sheet (6 mm).
>    The photo is the dominant element; the paragraphs sit in a narrower column inside its field.
> 3. Choosing a size: a plain comparison table of the three pans with diameter, weight, hob fit and price, each row ending in an "Add to basket" button.
> 4. Care: a short numbered list of the four seasoning steps, because order matters, with one photo of the oil being wiped in.
> 5. Footer: delivery, returns and contact.
>
> Signature: the opening's full-width side profile becomes the cutaway in section 2, exposing the thickness that the argument is about.
> The pan holds its position as its exterior mask opens across the frame; the image scale changes from whole pan to the base detail while the measured thickness label enters beside the cut face.
> The first handoff introduces the material; the later cutaway state explains why its mass matters, then releases into ordinary reading flow.
> Motion levels: opening signature, section 2 narrative, size table still, care still, footer responsive links.
> 3D decision: use registered owned photographs and a controlled mask, because the actual surface and cut face are stronger evidence than an invented model; no WebGL needed for this concept.
> The native-scroll scene spans 1.5 desktop viewport heights, maps directly to progress, reverses to the same states, and has a visible "Choose a size" anchor throughout.
> On phones the same image-to-detail relationship uses a shorter crop transition without pinning.
> Reduced motion shows the exterior and cutaway together in normal flow; JavaScript or image failure leaves the caption, spec and size action available.
> Prototype budget: 60fps on the chosen test phone, 600KB for the paired photos, no ongoing rendering when settled or offscreen.
> Buttons use immediate focus and 160ms color feedback, with no moving hit areas.
> The table has no narrative animation.
> Buttons: contained, 48 px tall, the same silhouette in every row, with a visible focus ring.
> Loading: prices come from the shop API; the table renders with skeleton cells at the real column widths until they arrive.
> If the price request fails or times out after ten seconds, the price cells read "Price unavailable" with one "Load prices again" button for the table, and the other columns stay visible.
> The opening's price range comes from the same request: a skeleton the width of the range while loading, "See sizes for prices" if it fails.
> Add to basket keeps its width with a busy label while the basket responds, ignores repeat presses, and times out after ten seconds.
> Success writes "Added. View basket" beside the row, linking to the basket; failure or timeout writes "Not added. Press again to retry" and re-enables the button, and a retry cannot add the pan twice.
> Header: the maker's name linking home, and a basket link whose count updates when a pan is added.
> Each button's accessible name includes the pan's diameter.
> At narrow widths the table becomes stacked rows that keep their column labels.
>
> Facts available: three sizes, base thickness 6 mm, the diameters, weights, hob fit and prices in the spec sheet, four seasoning steps.
