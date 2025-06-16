# 🦆 Duckflow CRM

**Duckflow CRM** is a quick, one-day proof-of-concept that helps you turn messy CRM exports into clear, visual insights—within minutes, and without the need for an external database.

- **Engine:** [DuckDB](https://duckdb.org/) (in-process SQL OLAP)
- **Notebook:** Jupyter (Python 3.10+)
- **Visualization:** Matplotlib

> 💡 **Why DuckDB?**  
> DuckDB allows analysts to process everything locally (CSV → SQL → chart) while still handling millions of rows with sub-second query speeds.

---

## ✨ Features & Workflow

| Step        | Goal                                             | Outcome                    |
|-------------|--------------------------------------------------|----------------------------|
| **1. Load**     | Import raw CSVs (`contacts`, `deals`) into DuckDB      | Zero-config ingestion      |
| **2. Clean**    | Handle nulls, fix data types                          | Consistent tables          |
| **3. Enrich**   | Derive company size segments, date parts, etc.        | Enhanced analytics         |
| **4. Analyze**  | Run SQL snippets or simple "recipes" in Python        | KPIs & cohorts             |
| **5. Visualize**| Create bar/line charts with a few lines of Python     | Instant visual storytelling|

> Screenshots are available in **`/screenshots`** for a preview without running the code.

---

## 🚀 Quick Start

```bash
git clone https://github.com/<your-user>/Duckflow-CRM.git
cd Duckflow-CRM
python -m venv .venv && source .venv/bin/activate   # optional
pip install duckdb pandas matplotlib jupyter
jupyter notebook hubspot_analysis.ipynb
```

Run the notebook cells from top to bottom. Tweak queries as needed!

---

## 📁 Repository Structure

```
Duckflow-CRM/
├── contacts.csv              # Synthetic contact data
├── deals.csv                 # Synthetic deals data
├── hubspot_analysis.ipynb    # Main notebook
├── README.md                 # This file
└── screenshots/              # Visual previews (optional)
```

---

## 🗂️ Data Schema

**contacts.csv**

| Column        | Type  | Example                                   |
|---------------|-------|-------------------------------------------|
| contact_id    | str   | C0042                                     |
| email         | str   | user42@corp.com                           |
| industry      | str   | Healthcare                                |
| created_at    | date  | 2024-04-17                                |
| owner         | str   | Alice                                     |
| company_size  | int   | 120                                       |
| country       | str   | USA                                       |

**deals.csv**

| Column      | Type  | Example     |
|-------------|-------|-------------|
| deal_id     | str   | D0108       |
| contact_id  | str   | C0042       |
| stage       | str   | Closed Won  |
| amount      | int   | 12000       |
| close_date  | date  | 2024-08-05  |
| source      | str   | Referral    |

---

## 🛣️ Potential Extensions

- **Auto-SQL:** Integrate an LLM to translate natural language into DuckDB queries
- **Interactive Dashboard:** Use Streamlit or Plotly for live filtering and exploration
- **Parquet/Arrow Output:** Support for lightweight downstream BI tools
- **Notebook CI Tests:** Add automated tests with `papermill` and `pytest`

---

## 📜 License

MIT License — fork, remix, and build as you wish!

---

Made with ☕, 🐍, and a sprinkle of 🦆.
