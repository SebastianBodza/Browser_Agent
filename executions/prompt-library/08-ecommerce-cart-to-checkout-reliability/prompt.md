# Prompt - Ecommerce Cart-to-Checkout Reliability

Validate cart and checkout transitions for a storefront.

## Objective
Ensure a sample product can be added to cart and reach checkout without blocking errors.

## Required Steps
1. Open storefront and add one in-stock product to cart.
2. Verify cart quantity/price updates.
3. Continue to checkout and confirm checkout page loads.
4. Capture any errors, loops, or broken states.

## Output
Create `report.md` with:
- `PASS: TRUE/FALSE` (TRUE if full flow reaches checkout page)
- step result matrix
- blocking issues with severity
- linked screenshots/video/logs

