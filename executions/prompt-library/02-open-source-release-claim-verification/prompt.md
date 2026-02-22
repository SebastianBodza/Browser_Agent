# Prompt - Open Source Release Claim Verification

Verify whether release-note claims are actually visible in product/docs UI.

## Objective
Given a release note URL and 3 listed claims, verify each claim with direct visual or textual evidence.

## Required Steps
1. Open release notes and capture claim list.
2. Navigate docs/product pages where claims should be present.
3. Capture screenshots of supporting evidence for each claim.
4. Mark each claim as verified, partially verified, or not found.

## Output
Create `report.md` with:
- `PASS: TRUE/FALSE` (TRUE only if all claims verified)
- per-claim verdict table
- step log with URLs visited
- linked screenshots/video/logs

