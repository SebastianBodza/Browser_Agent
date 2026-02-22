# Prompt - UI Verification (Light Mode Warning Flow)

Validate the light-mode warning flow on `https://bitbasti.com`.

## Test Goal

When switching from dark mode to light mode:

1. A warning popup/dialog should appear that the website is optimized for dark mode.
2. The user should be able to switch back to dark mode by clicking the popup button.
3. After the popup is accepted, switching to light mode again should not show the popup again.

## Execution Rules

- Use only `agent-browser` commands.
- Record full video of the run.
- Capture annotated screenshots for each key checkpoint.
- Save raw snapshots/logs needed to prove results.

## Required Output

Create `report.md` in this folder with:

- `PASS: TRUE` or `PASS: FALSE`
- criterion-by-criterion result
- exact steps performed
- links to screenshots, logs, and video

