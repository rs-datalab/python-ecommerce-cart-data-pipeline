# E-commerce Cart Data Processing (DummyJSON)

## Overview

This project processes e-commerce cart, product, and user data from the DummyJSON API to create a clean, analysis-ready dataset and summary tables.

It focuses on transforming nested JSON data into structured tabular form, validating records, and generating useful aggregated insights.

---

## Objective

- Convert nested cart JSON data into a flat, item-level dataset
- Clean and validate cart, product, and user data
- Enrich cart items with product and user attributes
- Generate summary tables for analysis

---

## Dataset

Data is sourced from the DummyJSON API:

- Carts
- Products
- Users

The data simulates a simple e-commerce environment with:
- cart-level information
- product details
- user attributes

---

## Tools

- Python
- pandas
- requests

---

## What This Project Does

- Loads JSON data from the DummyJSON API
- Explodes nested `products` data so each row represents one cart item
- Renames columns using consistent `snake_case` naming
- Validates records based on required IDs and positive quantities
- Separates invalid records into a `bad_records` dataset
- Merges cart, product, and user data into one dataset
- Creates summary tables at user and category level

---

## Key Findings

- Users vary significantly in total spend and purchase volume
- Some categories contribute disproportionately to total revenue
- A small number of invalid records were identified due to missing fields or non-positive quantities

---

## Outputs

- `clean_cart_items.csv` → cleaned, enriched cart item dataset
- `bad_records.csv` → invalid records with rejection reasons
- `user_summary.csv` → user-level summary
- `category_summary.csv` → category-level summary

---

## Repo Structure


ecommerce-cart-data-processing/
├── notebooks/
│   └── ecommerce_cart_data_pipeline.ipynb
├── outputs/
│   ├── clean_cart_items.csv
│   ├── bad_records.csv
│   ├── user_summary.csv
│   └── category_summary.csv
├── README.md
└── requirements.txt


---

## Notes

- Each row in the final dataset represents one cart item
- Cart-level values are repeated across item rows and handled carefully in aggregations
- This project focuses on data cleaning, validation, and aggregation rather than production deployment

---