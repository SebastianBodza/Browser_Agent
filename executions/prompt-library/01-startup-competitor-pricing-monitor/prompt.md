# Prompt - Competitor Pricing Monitor

Track pricing and plan changes across 5 competitor websites. Search for german based startups for enterprise Chatbots and LLM platforms like Langdock. For each competitor, collect current plan names, monthly price, yearly price (if available), and key limits/features. What USP does the product have?

Keep in mind to always use the current browser session with `agent-browser --auto-connect` and before creating a full height screenshot scroll to the bottom so all content loads. 

## Objective
Collect current plan names, monthly price, yearly price (if available), and key limits/features for each competitor.

## Required Steps
0. Search for alternatives to Langdock in the german startup ecosystem focused on enterprise chatbot and LLM platforms. Identify 5 competitors with clear pricing pages.
1. Open each pricing page and wait for full load.
2. Capture full-page and annotated screenshots.
3. Extract structured pricing data from visible cards/tables.
4. Compare with previous baseline if available.

## Output
Create `report.md` with:
- `PASS: TRUE/FALSE` (TRUE if data extraction is complete for all competitors)
- extracted table (site, plan, price, limits)
- detected changes vs baseline
- evidence links to screenshots/video/logs

