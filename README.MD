# Retail & E-commerce Data Cleaning and Analytics

## Overview

This project focuses on cleaning, standardizing, validating, and transforming retail and e-commerce data to support reliable business reporting. The source data contains inconsistent identifiers, timestamps, product labels, numeric formats, currencies, statuses, and missing values.

The project uses Python and Jupyter Notebooks to prepare a cleaned dataset and calculate business metrics for sales, customers, promotions, returns, fulfilment, payments, and inventory where the available fields support those analyses.

## Project Objectives

- Standardize order, customer, and transaction identifiers.
- Parse timestamps and standardize timezone-aware values.
- Normalize product names, SKU codes, categories, brands, and selected labels.
- Convert numeric fields such as prices, discounts, taxes, shipping costs, and refunds into usable numeric values.
- Flag questionable records and data-quality issues for review.
- Produce sales and operational analytics from the cleaned data.
- Document assumptions and limitations so ambiguous source values are not silently treated as certain.

## Repository Structure

```text
retail-ecommerce-analytics/
├── data/
│   ├── raw/
│   │   └── r-ecommerce_raw_data.csv
│   └── cleaned/
│       └── r-ecommerce_Cleaned.csv
├── notebooks/
│   ├── project1.ipynb
│   └── transformation.ipynb
├── docs/
│   └── Retail_Ecommerce_Analytics_UseCase.docx
├── README.md
└── requirements.txt
```

The raw dataset should be preserved unchanged. The cleaned CSV is an output of the cleaning workflow. Update the notebook file paths to match this folder structure.

## Technology Stack

- Python 3
- Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Seaborn

## Setup

### 1. Clone or download the project

Open a terminal in the project root directory.

### 2. Create and activate a virtual environment (recommended)

**Windows:**

```bash
python -m venv .venv
.venv\\Scripts\\activate
```

**macOS/Linux:**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
python -m pip install -r requirements.txt
```

### 4. Launch Jupyter

```bash
jupyter notebook
```

Open `notebooks/project1.ipynb` to run the cleaning workflow, then open `notebooks/transformation.ipynb` to run the analytics workflow.

## Workflow

1. **Explore the raw data:** inspect columns, data types, missing values, and inconsistent values.
2. **Clean and standardize:** normalize identifiers and labels, parse dates, convert numeric fields, and create review flags.
3. **Save the cleaned data:** export the cleaned dataset to `data/cleaned/r-ecommerce_Cleaned.csv`.
4. **Transform and analyze:** calculate sales metrics and explore customer, campaign, product, return, delivery, and inventory performance.
5. **Validate results:** check metric definitions, duplicates, missing data, currency assumptions, and reconciliation totals before interpreting results.

## Current Analytical Areas

The transformation notebook includes work on:

- Daily and monthly sales summaries
- Average order value and items per order
- Customer cohorts and repeat purchases
- Session conversion funnel
- Promotion and campaign performance
- Product and category sales rankings
- Return rates and refund values
- Delivery lead time and on-time delivery
- Inventory and stockout indicators

The availability and correctness of each metric depend on the source data, event definitions, and business rules. Results should be validated before being used for business decisions.

## Data Quality and Limitations

- Ambiguous timestamps without a reliable timezone should be flagged rather than assigned an assumed timezone.
- Currency conversion requires a documented exchange-rate source and rate date. Do not infer missing rates.
- Missing discounts, customer identifiers, and other business-critical fields should not be filled with arbitrary values.
- Negative quantities may represent returns or invalid sales; interpret them using event and return rules.
- Deduplication should use appropriate order-line and event-version keys, not just matching order IDs.
- Reference-data checks require authoritative product, customer, supplier, and inventory tables. Values derived from the dataset itself do not independently prove that a key is valid.
- Revenue calculations must define treatment of discounts, taxes, shipping, refunds, cancelled orders, test orders, and fraud-review orders.
- Inventory sell-through and customer lifetime value require documented definitions and suitable source data.

## Future Improvements

- Add automated tests for the documented data-quality scenarios.
- Produce separate exception and rejected-record datasets.
- Generate a repeatable end-to-end pipeline.
- Add a data-quality report and reconciliation checks.
- Export key analytical outputs to dedicated CSV files.
- Document metric definitions and assumptions alongside results.


