# E-commerce Cart Data Pipeline Report

## Objective
Prepare raw nested cart, product, and user JSON data for analysis by converting it into a clean cart item dataset and summary tables.

## Dataset
Source: DummyJSON API  
Tables used: carts, products, users

## Workflow
- Loaded raw JSON files
- Flattened nested cart products into item-level rows
- Standardized column names to snake_case
- Validated key fields and separated invalid records
- Enriched cart items with product and user attributes
- Created user-level and category-level summary tables

## Outputs
- `clean_cart_items.csv`
- `bad_records.csv`
- `user_summary.csv`
- `category_summary.csv`

## Key Results
- Final cleaned dataset contains 198 cart-item rows
- 45 unique users represented in the user summary
- 24 product categories summarized
- No invalid cart records were found in this run
- Revenue and quantity vary notably across categories and users

## Assumptions and Limitations
- Cart totals are treated as source-provided values
- Validation is limited to basic ID presence and positive quantity checks
- No duplicate or reconciliation checks were added in this version

## Next Improvements
- Add cross-checks between cart totals and summed item totals
- Add duplicate detection
- Turn notebook logic into reusable Python scripts
- Add simple visualizations for category revenue and user spend