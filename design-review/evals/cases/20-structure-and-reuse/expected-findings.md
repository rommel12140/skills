# Expected findings

Reject writing `OverduePanel.tsx` from scratch.
Build the panel from the existing `ui/Panel` and add a variant if the overdue state needs one, after checking the showcase page.
Record which existing components were checked.

Name `BillingCard2` as a near-duplicate of `BillingCard` and fold it into one component with a variant.
Name the twice-defined status pill as a part used by two screens and file it once under `features/`, not under one page.
Keep Billing-only parts and their CSS in `pages/billing/`, and do not leave new files loose in the flat folder.

Split the 1,400-line Billing file by responsibility so each file sits under about 300 lines.
Keep styles beside their components and preserve cascade order when moving them.
Add any new shared component or variant to the showcase page.

Preserve the accepted look.
Compare captures of Billing and Customers before and after at the widths and themes the skill names, because both screens use edited parts.
Keep those rendered comparisons unchecked, since no fixture or browser was supplied.

Do not move the other screens' files out of the flat folder as a side effect; propose that reorganization separately.
Do not file parts in `features/` or `ui/` in advance on the guess that they may be shared later.
Do not claim these written expectations prove model behavior.
