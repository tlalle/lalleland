# Raw source data

The original address-book workbook goes here, as `.xlsx` — not CSV. A CSV export
discards merged cells, hidden rows and columns, cell fill colours, notes, data
validation and filter state, all of which carry meaning in a spreadsheet that has
been maintained by hand.

**This folder is not committed.** `.gitignore` excludes its contents so that real
names, emails and phone numbers never enter git history, where they would be
permanent and effectively unpurgeable from clones and forks. The workbook lives
on local disk only; the pipeline that reads it is what gets versioned.

Files here are immutable. Nothing in the pipeline writes to them. Profiling opens
them read-only and checksums them before and after to prove the original is
unchanged; all output is written to `reports/`, which is also ignored.

Do not clean or tidy a file before dropping it here. The inconsistencies are the
specification — removing them hides the exact cases that break the import later.

One thing this arrangement does **not** do: file contents are still sent to the
model provider for inference when an agent reads them. Keeping data out of git
removes the storage and distribution exposure, not the processing one. If the
real contact details should never be processed by a model at all, build and test
against a copy with personal details scrambled and structure left intact, and run
the final pass over real data without an agent in the loop.
