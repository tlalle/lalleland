# Raw source data

The original address-book workbook goes here, as `.xlsx` — not CSV. A CSV export
discards merged cells, hidden rows and columns, cell fill colours, notes, data
validation and filter state, all of which carry meaning in a spreadsheet that has
been maintained by hand.

Files in this folder are **immutable**. Nothing in the pipeline writes to them.
Profiling opens them read-only and checksums them before and after to prove the
original is unchanged; all output is written elsewhere.

Do not clean or tidy a file before committing it. The inconsistencies are the
specification — removing them hides the exact cases that break the import later.

Note that this folder's contents become part of git history permanently. If the
workbook holds real names, emails or phone numbers, confirm that is acceptable
for this repository before pushing, or commit a copy with personal details
scrambled and the structure left fully intact.
