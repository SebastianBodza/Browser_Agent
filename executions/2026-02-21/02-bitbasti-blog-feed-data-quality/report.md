# Run Report - bitbasti blog feed data quality

PASS: TRUE

## Scope
- Target: `https://bitbasti.com`
- Date: `2026-02-21`
- Session: `bitbasti-feed-20260221`

## Acceptance Criteria
1. At least 5 blog cards are visible on the homepage.
2. Each visible card has title, publish date, and `Read more` link.
3. Top 5 visible titles and dates are extracted in the report.

## Steps Executed
1. Opened homepage and waited for network idle.
2. Captured full-page and annotated screenshots.
3. Captured full accessibility snapshot.
4. Parsed snapshot for level-2 headings, `time:`, and `Read more` links.
5. Saved extraction log and closed browser.

## Results
- Criterion 1: PASS
  - Found 5 visible blog cards in the homepage list.
- Criterion 2: PASS
  - For each of the 5 cards, snapshot evidence included:
    - level-2 heading (title),
    - `time:` value (publish date),
    - `Read more` link.
- Criterion 3: PASS
  - Extracted 5 titles with dates.

## Extracted Top 5 Posts
1. `CVE-2025-55182 (React2Shell) - Real-World Attack Analysis` - `December 8, 2025`
2. `Real-Time TTS Streaming with Orpheus and SNAC on a single RTX 3090` - `April 24, 2025`
3. `From Llama to LLaSA - GRPO with WER and custom repetition penalty` - `March 31, 2025`
4. `Azure and the Bing API Shutdown - No Notice, No API` - `March 5, 2025`
5. `Faster LLMs with Quantization - How to get faster inference times with quantization` - `January 17, 2025`

## Evidence
- Video:
  - `artifacts/video/run.webm`
- Screenshots:
  - `artifacts/screenshots/01-home-full.png`
  - `artifacts/screenshots/02-home-annotated.png`
- Logs:
  - `artifacts/logs/snapshot-home.txt`
  - `artifacts/logs/extracted-headings-dates-readmore.txt`

