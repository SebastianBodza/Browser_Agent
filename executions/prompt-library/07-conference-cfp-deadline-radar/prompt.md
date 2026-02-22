# Prompt - Conference CFP Deadline Radar

Build a near-term call-for-papers deadline tracker.

## Objective
Find upcoming CFP deadlines for AI/data conferences in the next 120 days.

## Required Steps
1. Search official conference sites and CFP pages.
2. Extract deadline, timezone, topic scope, and submission URL.
3. Normalize dates to ISO format.
4. Flag deadlines within 14 days as urgent.

## Output
Create `report.md` with:
- `PASS: TRUE/FALSE` (TRUE if at least 10 valid CFP entries found)
- prioritized CFP table
- urgent deadline summary
- linked screenshots/video/logs

