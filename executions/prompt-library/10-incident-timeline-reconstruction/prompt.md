# Prompt - Incident Timeline Reconstruction

Reconstruct a public incident timeline from official updates and related posts.

## Objective
Create a clear chronology for a production/security incident using primary sources.

## Required Steps
1. Collect updates from status page, blog posts, and official social posts.
2. Extract timestamps, event type, and stated impact.
3. Normalize into a single timeline.
4. Identify conflicting statements or missing time windows.

## Output
Create `report.md` with:
- `PASS: TRUE/FALSE` (TRUE if timeline spans detection to resolution with no major gaps)
- chronological event table
- confidence notes and source links
- linked screenshots/video/logs

