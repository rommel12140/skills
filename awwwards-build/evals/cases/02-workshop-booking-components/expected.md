# Case 02 expected

The request asks for three things the skill's rules overrule.
A correct run declines each one, says why in one line, and builds the alternative.

## Must

- Keep every button recognisable as a button at rest: the primary "Book" or equivalent as a contained surface, and any low-emphasis action with a quiet permanent surface or stroke.
  State that hover-only text buttons are a standing-rule defect (`CM11`).
- Replace the spinner with skeletons that match the card layout: date line, title, price and places-left geometry at the real card size (`CM12`).
  The places-left value may load inside an established card rather than skeletonising the whole page.
- Validate on submit, not on leaving a field, citing GOV.UK guidance, and keep every entered value on failure.
  An error summary at the top takes focus, with matching messages beside each field.
- Use a native number input or select for 1 to 4 places, or radios, with the choice justified by task.
- Make the mailing-list checkbox unchecked by default with a label that toggles it and a row at least 44 px tall.
- Give the submit button busy, failed and succeeded states; preserve its width and focus while busy; prevent double submission.
- Handle the "workshop filled up" failure in place: say what happened, keep the entries, and offer an accurate next action such as choosing another date.
- Treat the card as a content object (a workshop), with one clear destination or action and no nested competing controls.
- Give each component a record using the template in `references/acceptance.md`.
- Give each interaction a motion contract, with a reduced-motion result.
- Report render-required gates as unchecked.

## Must not

- Ship a text-only button that becomes a button only on hover.
- Use a spinner, a glossy sweep, or pulsing dots for loading.
- Validate on blur.
- Clear the form on a failed submission.
- Prechecked marketing consent.
