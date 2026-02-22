# Prompt - Blog Feed Data Quality Verification

Verify and extract the latest visible blog feed cards on `https://bitbasti.com`.

## Test Goal

Check the homepage feed quality with these criteria:

1. At least 5 blog cards are visible.
2. Each visible card contains:
   - a post title,
   - a publish date,
   - a `Read more` link.
3. Extract the top 5 visible titles and publish dates into the report.

## Execution Rules

- Use `agent-browser` commands only.
- Record full run video.
- Capture full and annotated screenshots.
- Save raw snapshot logs and extraction logs.

## Required Output

Create `report.md` in this folder with:

- `PASS: TRUE` or `PASS: FALSE`
- criteria results
- extracted top 5 titles + dates
- linked screenshots, video, and logs

