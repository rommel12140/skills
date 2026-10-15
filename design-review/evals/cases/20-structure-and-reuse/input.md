# Structure and reuse in a dashboard refactor

Mode: Refine.
A fictional operations dashboard is a Vite and React app with no strong folder convention yet.
The owner asks for a new "Overdue invoices" panel on the Billing screen and says the current look is accepted.
No browser or implementation fixture is supplied. Work only from the following synthetic observations.

- The Billing screen is one 1,400-line file that renders the header, four panels, two tables and all their styles.
- `src/components/` is one flat folder of 150 files from every screen, with names such as `BillingCard.tsx`, `BillingCard2.tsx` and `HomeCard.tsx`.
- `BillingCard2.tsx` is a copy of `BillingCard.tsx` with a red border and one extra footer line.
- A shared `ui/Panel.tsx` already supports a title, a body and an optional footer, and a showcase page lists it with two variants.
- A status pill used on Billing and Customers is defined twice, once in each screen's file.
- The planned approach is to write a new `OverduePanel.tsx` from scratch in `src/components/` with its own card styles.

What do you build, where does each part go, and what do you check before presenting?
Do not claim a rendered pass.
