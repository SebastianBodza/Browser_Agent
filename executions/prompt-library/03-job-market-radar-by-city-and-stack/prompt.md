# Prompt - Job Market Radar by City and Stack

Collect recent jobs for a specific role/stack across multiple job boards.

## Objective
Find up to 30 postings for a role (example: `AI Engineer`) in selected cities, filtered to `junior-level`.

## Required Steps
1. Visit at least 3 job platforms.
2. Apply filters (location, seniority, keyword stack).
3. Extract title, company, location, posting age, and URL.
4. Remove duplicates by company + title + location.

## Output
Create `report.md` with:
- `PASS: TRUE/FALSE` (TRUE if at least 20 unique results collected)
- top findings and hiring signal summary
- CSV/markdown table link
- linked screenshots/video/logs

