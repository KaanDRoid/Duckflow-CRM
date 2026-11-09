# Duckflow CRM

A small, one-day proof of concept for analysing CRM exports with DuckDB inside a Jupyter notebook. Two CSV exports (contacts and deals) are loaded into an in-memory DuckDB database, cleaned and enriched with SQL, and summarised with a few Matplotlib charts. No database server is needed.

## Data

Both files are synthetic, HubSpot-style exports:

- `contacts.csv`: 100 contacts. Columns: `contact_id`, `email`, `industry` (5 missing), `created_at`, `owner` (Alice, Bob, Charlie, Diana), `company_size` (9 to 498, so 93 of the 100 contacts end up in the Enterprise segment), `country`.
- `deals.csv`: 150 deals linked to contacts by `contact_id`. Columns: `deal_id`, `contact_id`, `stage` (Discovery, Proposal, Negotiation, Closed Won, Closed Lost), `amount` (17 missing), `close_date` (all in 2024), `source`.

## What the notebook does

1. Loads both CSVs into DuckDB with `read_csv_auto`.
2. Cleaning: missing `industry` becomes `Unknown`, missing `amount` becomes 0.
3. Enrichment: adds a `size_segment` column (Small up to 10 employees, Medium up to 50, Enterprise above) and stores it as the `enriched_contacts` table.
4. Charts: top 5 industries by total deal amount, and total deal amount per month of `close_date`.
5. Example question: total deal amount with enterprise companies per contact owner.

## Results

Total deal amount with enterprise companies by owner (all deal stages):

| Owner   | Total amount |
|---------|-------------:|
| Diana   | 455,483 |
| Alice   | 323,488 |
| Bob     | 250,386 |
| Charlie | 172,062 |

## How to run

```bash
git clone https://github.com/KaanDRoid/Duckflow-CRM.git
cd Duckflow-CRM
pip install -r requirements.txt
jupyter notebook hubspot_analysis.ipynb
```

Run the cells from top to bottom.

## Repo layout

```
hubspot_analysis.ipynb   # the analysis notebook
contacts.csv             # synthetic contacts
deals.csv                # synthetic deals
requirements.txt
LICENSE                  # MIT
```
