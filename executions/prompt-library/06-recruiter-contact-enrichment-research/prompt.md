# Prompt - Recruiter Contact Enrichment Research

Research public contact channels for a target company hiring team.

## Objective
Find verifiable public recruiter contacts and hiring channels without scraping private data.

## Required Steps
1. Start from company careers page and official social profiles.
2. Identify recruiter/team contact endpoints (email aliases, forms, public profiles).
3. Validate links and capture evidence.
4. Mark confidence level per contact source.

## Output
Create `report.md` with:
- `PASS: TRUE/FALSE` (TRUE if at least 5 verified contact channels found)
- contact table (type, source URL, confidence)
- compliance note (public data only)
- linked screenshots/video/logs

