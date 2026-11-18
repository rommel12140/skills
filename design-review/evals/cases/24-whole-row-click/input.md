# Whole-row click on a list

Mode: Audit.
A fictional bookkeeping app's invoice list is under review.
No browser or implementation fixture is supplied.
Work only from the following synthetic observations.

- Each invoice row shows a client name, an amount, a due date, a status tag, a select checkbox and a three-dot menu.
- Only the client name is a link, and it is blue and underlined.
- Clicking the amount, the date or the row's padding does nothing, and the cursor stays an arrow there.
- Rows have no hover state.
- Tabbing lands on the client name link and shows a thin ring around the name only.
- An earlier fix made the row a `div` with an `onclick`; it was reverted because ticking the checkbox also opened the invoice.
- The settings page lists notification rules as plain rows that open nothing; their labels are not links.

Report the findings with their severity and fixes.
Do not implement changes.
Do not claim a rendered pass.
