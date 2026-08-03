# Evals

Three cases.
Each holds an input and the findings a correct pass must produce.

These exist to answer one question: did editing the skill make it better or quietly worse.

| Case | Input | What it measures |
| :--- | :--- | :--- |
| `01-generic-saas-hero` | A page carrying planted tells | Recall. Every planted ID must be found. |
| `02-editorial-reference-page` | A page built under this catalog | False positives. Nothing above P2 may be reported. |
| `03-webflow-export` | A real Webflow export | That the Webflow fix column is usable, not theoretical. |

Cases 02 and 03 matter more than case 01.

Any anti-slop catalog can find slop.
The failure mode that makes a reviewer stop trusting a tool is the false positive, and case 02 is the guard against it.
The measured false-positive rate on the published writing catalogs sits around 4%, so this is not hypothetical.

## Running a case

There is no test runner.
A run is an agent pass over the input in audit mode, with the output compared to `expected-findings.md`.

A runner before we know the skills are useful would be machinery ahead of need.
If the eval set grows past a handful of cases, revisit that.

## Grading

| Result | Meaning |
| :--- | :--- |
| Pass | Every expected ID found, no unexpected finding above P2 |
| Recall miss | An expected ID was not found |
| False positive | A finding above P2 that the case does not expect |
| Wrong fix | The ID was found but the fix named the wrong stack |

A recall miss and a false positive are not equally bad.
A false positive costs the reviewer's trust, and trust does not come back.

## Case 02 note

The input for case 02 is the anti-slop research brief built on 3 August 2026.
It was designed under this catalog, so it doubles as a live check on both the catalog and the page.
If the catalog flags it above P2, either the catalog is wrong or the page is.
Both answers are worth having, so record which one it was.
