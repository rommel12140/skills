# Expected findings

Report the invoice rows under `K7` as one finding on the shared row component, not one finding per symptom.
Name each failed part: only the title opens the row, the title is an underlined link, the cursor is not a pointer across the row, there is no row hover state, and the focus state covers the name instead of the row.

Fix it with the whole row as the hit target.
Because the row holds a checkbox and a menu, use a title link stretched over the row with the nested controls lifted above it, not an `<a>` wrapping the row.
Set the title as plain row text with no underline, and give the row visible hover and focus states.

Address the reverted fix directly.
The checkbox and the menu must act on their own and must not open the invoice.
A row `div` with an `onclick` also needs keyboard support, so it is not the preferred fix.

Give a rendered acceptance check for after the fix: click the amount, the date and the padding, hover a row, tab to a row and press Enter, and click the checkbox and the menu, recording what opened at each step.

Do not flag the notification rule rows under `K7`: they open nothing, so the gate does not apply.

Close with counts by severity and a plain readiness statement.
Treat every observation as supplied, not as a personal capture, since no fixture or browser was supplied.
Do not implement any change in this audit.
