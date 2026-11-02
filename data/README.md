# Data

The data files are too large to commit (~7M rows), so they are not tracked by git. Follow the steps below to rebuild them locally.

## Source

Home Mortgage Disclosure Act (HMDA) Loan Application Register (LAR), **2016**, published by the CFPB:
https://www.consumerfinance.gov/data-research/hmda/

## Subset definition

- First-lien loans
- Owner-occupied properties
- 1–4 family properties

This leaves 7,036,352 rows and 45 columns.

**Target (`action_taken`):** approved (originated or approved) vs. denied. Withdrawn applications, incomplete files, and purchased loans are dropped.

## Layout

- `raw/`: the original downloaded file(s), unmodified
- `processed/`: cleaned, subset data ready for modeling

*TBD: exact download URL/filename and the cleaning script or notebook that produces `processed/`.*
