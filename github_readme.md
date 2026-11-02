# Antarctic Sub-Glacial Database & Telemetry Generator

This repository contains the Python generation script and database schema for the **Antarctic Sub-Glacial Ice Core Isotope & Microbial Viability Database**, developed as part of the SQL & Data Science Database Assignment.

---

## 📂 Repository Contents
* `generate_database.py` (or Jupyter Notebook): The end-to-end Python script utilizing `sqlite3`, `random`, and `numpy` to build the database, enforce constraints, inject realistic missing values/duplicates, and populate 1,200+ records.
* `antarctic_ice_core_lab.db`: The compiled SQLite database file outputted by the generation script.

---

## 🗄️ Schema Architecture
The database is fully normalized in Third Normal Form (3NF) across three related tables:
1. **`drilling_sites`** (Parent table tracking Antarctic sectors and ice sheet thickness).
2. **`ice_cores`** (Child table connected via `site_id` Foreign Key logging extraction depths).
3. **`microbial_specimen_logs`** (Fact table featuring a **Compound Primary Key** `(core_id, sample_id)`, foreign key linking, and rigorous `CHECK` constraints).

---

## 📊 Data Types Representation
The database satisfies all rubric requirements across 12 total columns:
* **Nominal:** `sector_code`, `strain_classification`
* **Ordinal:** `viability_status_tier` (*Dormant* $\rightarrow$ *Stressed* $\rightarrow$ *Resilient* $\rightarrow$ *Mutated*)
* **Interval:** `chamber_temperature_celsius` (Arbitrary zero reference scale)
* **Ratio:** `extraction_depth_m`, `ice_sheet_thickness_m`, `cellular_mass_ug` (Meaningful absolute zero)

---

## 🚀 How to Run the Script

1. Ensure you have Python installed along with the required libraries (`numpy`).
2. Run the Python script or open the Google Colab notebook:
   ```bash
   python generate_database.py
   ```
3. The script will safely create and populate `antarctic_ice_core_lab.db` with over 1,200 rows, complete with deliberate sensor dropouts (`NULL` values) and duplicate records to ensure high database realism.