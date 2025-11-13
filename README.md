# 🧾 Slooze Take Home Challenge - Data Science & Analytics

### Inventory, Purchase & Sales Analysis for Business Optimization

---
# Slooze Take Home Challenge 

This README explains where files live, how the notebooks are organized, and step-by-step instructions to run the analysis locally on Windows (PowerShell). It is written so a reviewer can reproduce results quickly.

---

**Project purpose (one line):** inventory, sales and purchases analysis for a retail wine & spirits business — to help with ordering, supplier evaluation, and stock optimization.

---

## Where files are located (important paths)

- Raw data (provided): `D:\slooze_challenge\Data\`
   - Sales: `SalesFINAL12312016.csv`
   - Purchases: `PurchasesFINAL12312016.csv`
   - Invoice purchases: `InvoicePurchases12312016.csv`
   - Beginning inventory: `BegInvFINAL12312016.csv`
   - Ending inventory: `EndInvFINAL12312016.csv`
   - Purchase prices / costs: `2017PurchasePricesDec.csv`

- Project work folder: `slooze_challenge\`
   - Cleaned data (created by notebook 01): `slooze_challenge\Slooze_Analysis\data\cleaned\`
   - Notebooks: `slooze_challenge\notebooks\`
   - Results (CSVs, PNGs): `slooze_challenge\Slooze_Analysis\results\`
   - Requirements: `slooze_challenge\requirements.txt`

---

## Notebook overview - what each notebook does (short, shareable descriptions)

- `01_data_cleaning.ipynb` - Load the raw CSVs from `Data/`, inspect headers and sample rows, normalize columns (date, sku, quantity, revenue), save cleaned CSVs into `data/cleaned/`. This is where you should adjust column-name mappings if your CSV headers differ.

- `02_sales_analysis.ipynb` - Load `sales_cleaned.csv` and produce: SKU summary (`sku_summary.csv`), monthly totals (`monthly_sales.csv`), and a `monthly_revenue.png` chart. These are the key outputs for sales performance.

- `03_inventory_optimization.ipynb` - Merge sales and price data (if available), compute inventory value estimates, and run ABC classification (`sku_abc.csv`). Useful for prioritizing SKUs.

- `04_forecasting.ipynb` - Simple demand forecast demo (rolling average). Produces a small forecast CSV for the top SKU; optional ARIMA forecast if `pmdarima` is installed.

- `05_eoq_reorderpoint.ipynb` - Calculates EOQ and Reorder Point suggestions using sales and (if available) unit cost data. Saves `sku_eoq_rop.csv`.

- `06_final_insights.ipynb` - Gathers the most important CSV outputs and prints a concise, human-readable summary and practical recommendations for business stakeholders.

---

## Step-by-step run instructions (Windows / PowerShell)

1) Open PowerShell and change into the analysis folder:

```powershell
cd D:\slooze_challenge\Slooze_Analysis
```

2) (Optional) Activate a virtual environment if you have one. Example (if venv at `D:\slooze_challenge\.venv`):

```powershell
& 'D:\slooze_challenge\.venv\Scripts\Activate.ps1'
```

If you don't have a venv and want to create one in-place:

```powershell
python -m venv .venv
& '.venv\Scripts\Activate.ps1'
```

3) Install requirements:

```powershell
python -m pip install -r .\requirements.txt
```

4) Recommended: run notebooks interactively with Jupyter so you can inspect and adjust as needed:

```powershell
jupyter notebook
# then open and run notebooks in order: 01 -> 02 -> 03 -> 04 -> 05 -> 06
```

Alternative: execute all notebooks automatically (non-interactive):

```powershell
.\run_all.ps1
```

Notes:
- If a notebook fails during `nbconvert` execution, open it in Jupyter to inspect the failing cell. Most failures are due to column names that differ from the heuristics in the cleaning notebook.

---

## Expected outputs (where to look)

- Cleaned CSVs: `Slooze_Analysis/data/cleaned/` (e.g., `sales_cleaned.csv`)
- Key results: `Slooze_Analysis/results/` - `sku_summary.csv`, `monthly_sales.csv`, `monthly_revenue.png`, `sku_abc.csv`, `sku_eoq_rop.csv`, and forecast CSVs.

Share these CSVs and the `monthly_revenue.png` figure when preparing a short stakeholder email or slide.

---

## Quick troubleshooting & tips

- "Module not found" when running a notebook: make sure you activated the correct venv and installed packages from `requirements.txt`.
- `nbconvert` execution errors: run the failing notebook in Jupyter to get a full stack trace and inspect inputs.
- Wrong SKU/quantity mapping: open `data/cleaned/sales_cleaned.csv` to see how the script mapped columns. If mapping is wrong, tell me the exact column header and I will update the cleaning notebook to map them explicitly.

---





## Author & contact

Your Name — KASAK
Email: arorakasak2005@gmail.com

---
