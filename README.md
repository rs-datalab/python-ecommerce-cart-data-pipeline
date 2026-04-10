# E-commerce Cart Data Pipeline

## Overview

This project processes e-commerce cart, product, and user data from the DummyJSON API to create a clean, analysis-ready dataset and summary tables.

It focuses on transforming nested JSON data into structured tabular form, validating records, enriching cart items with product and user attributes, and generating outputs that can be used for downstream analysis.

## Objective

The goal of this project is to:

- convert nested cart JSON data into a flat, item-level dataset
- clean and validate cart, product, and user data
- enrich cart items with product and user attributes
- generate summary tables for analysis

## Dataset

**Source:** DummyJSON API

The project uses three source files:

- carts
- products
- users

Together, these simulate a small e-commerce environment with:

- cart-level transaction data
- product metadata
- user-level attributes

## Tools

- Python
- pandas
- JSON handling

## What This Project Does

The notebook performs an end-to-end data preparation workflow:

- loads raw JSON data for carts, products, and users
- inspects and extracts records from nested JSON structures
- explodes nested `products` data so each row represents one cart item
- renames fields using consistent `snake_case` naming
- validates records based on required IDs and positive quantities
- separates invalid rows into a dedicated `bad_records` output
- merges cart items with product and user attributes
- creates summary tables at the user and category level
- exports cleaned outputs to CSV

## Highlights

This project produces several useful analytical outputs:

- users vary significantly in total spend and purchase volume
- some product categories contribute disproportionately to total revenue
- the final cleaned dataset contains 198 cart-item rows
- 45 unique users appear in the user-level summary
- 24 product categories are represented in the category summary
- no invalid cart records were found in this run

## Outputs

The project exports the following files:

- `clean_cart_items.csv` — cleaned, enriched cart item dataset
- `bad_records.csv` — invalid records with rejection reasons
- `user_summary.csv` — user-level summary table
- `category_summary.csv` — category-level summary table
- `report.md` — short written summary of the workflow and results

## Project Structure

```text
python-ecommerce-cart-data-pipeline/
├── notebooks/
│   └── ecommerce_cart_data_pipeline.ipynb
├── outputs/
│   ├── bad_records.csv
│   ├── category_summary.csv
│   ├── clean_cart_items.csv
│   └── user_summary.csv
├── raw_data/
│   ├── carts.json
│   ├── fetch_json_dummyjson
│   ├── products.json
│   └── users.json
├── README.md
├── report.md
└── requirements.txt
```

## How to Run

1. Open the notebook in Jupyter Notebook, JupyterLab, or VS Code.
2. Make sure the raw JSON files are available in the `raw_data/` folder.
3. Install the required dependencies if needed.
4. Run the notebook from top to bottom.
5. Review the exported CSV files in the `outputs/` folder.

## Notes

- Each row in the final dataset represents one cart item.
- Cart-level values are repeated across item rows and should be handled carefully in aggregations.
- Missing product brand values are filled with `"Unknown"` during enrichment.
- Validation in this version is limited to presence checks and positive quantity checks.
- This project focuses on data cleaning, validation, enrichment, and aggregation rather than production deployment.

## Future Improvements

Potential next steps include:

- adding reconciliation checks between cart totals and summed item totals
- adding duplicate detection and handling
- turning the notebook workflow into reusable Python scripts
- adding simple visualizations for category revenue and user spend
- extending validation logic beyond basic presence and positivity checks