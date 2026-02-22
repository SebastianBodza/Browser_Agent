# Prompt - Legal Policy Change Monitor

Detect meaningful changes in legal pages (privacy, terms, cookies) between two checks.

## Objective
Compare current legal page content against a saved baseline and identify high-impact changes.

## Required Steps
1. Open each legal page and capture current text/screenshot.
2. Diff against baseline text/snapshot if available.
3. Classify changes as low, medium, or high impact.
4. Highlight any new data-sharing, retention, or tracking clauses.

## Output
Create `report.md` with:
- `PASS: TRUE/FALSE` (TRUE if all target pages checked and diffed)
- change summary table by page and severity
- exact snippets or references for high-impact changes
- linked screenshots/video/logs

