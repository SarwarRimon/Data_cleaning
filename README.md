# FIFA21 Data Cleaning Project

This repository contains a Jupyter Notebook demonstrating a full data‑cleaning workflow on the FIFA 21 player dataset.  
The goal is to transform the raw dataset into a clean, analysis‑ready format by fixing data types, parsing text fields, and normalizing values.

---

## 📌 Project Contents

A clear, minimal view of the repository structure:

- Data/
  - fifa21_raw_data.csv        # Raw dataset used in the notebook
  - processed/                 # (suggested) cleaned outputs (create as needed)
- notebooks/
  - FIFA21_Data_Cleaning.ipynb # Main notebook with all cleaning steps
- scripts/                     # (optional) place for future reusable scripts
- README.md

Note: I replaced the dense ASCII tree with a simple bullet list for readability. If you prefer a compact tree view I can restore that style.

---

## 🧹 What the Notebook Cleans

The notebook performs step-by-step cleaning, including:

### ✔ Height & Weight Cleaning
- Converts feet/inches to centimeters: `5'7"` → **170.18 cm**
- Converts pounds to kilograms: `154lbs` → **69.85 kg**
- Handles inputs in both feet–inches and cm formats and normalizes to cm/kg

### ✔ Currency Columns Cleaning
Converts football value shorthand into plain integers (in Euros):

- `€67.5M` → **67500000**
- `€560K` → **560000**
- `€138.4M` → **138400000**

Cleaned Columns:
- Value
- Wage
- Release Clause

### ✔ Hits / Short-Format Number Cleaning
- Removes newline characters and extra whitespace
- Converts shorthand like `1.3K` → **1300**

### ✔ Team & Contract Splitting
Transforms combined team/contract lines like:

FC Barcelona  
2004 ~ 2021

Into separate fields:
- Team: `FC Barcelona`
- Contract: `2004 ~ 2021`

---

## ▶️ How to Run the Notebook

1. Clone the repository:
   ```bash
   git clone https://github.com/SarwarRimon/Data_cleaning.git
   cd Data_cleaning
   ```

2. Install dependencies (recommended inside a virtualenv):
   ```bash
   pip install pandas numpy jupyter
   ```

3. Launch Jupyter and open the notebook:
   ```bash
   jupyter notebook
   # then open notebooks/FIFA21_Data_Cleaning.ipynb
   ```

Run the notebook cells from top to bottom to reproduce the cleaning steps and export the cleaned dataset.

---

## 🎯 Output (what you get)

After running the notebook you will have:
- Cleaned numeric columns (value, wage, release clause)
- Normalized currency values as integers
- Standardized height & weight (cm / kg)
- Extracted and split textual fields (team, contract)
- Derived useful features that are ready for ML, analysis, and visualization

Suggested export files:
- Data/processed/players_21_clean.csv
- Data/processed/players_21_clean.parquet
- notebooks/outputs/cleaning_report.html (optional exported report)

---

## 🛠 Recommended Next Steps

- Convert notebook cells into reusable functions and a script (e.g., scripts/clean_fifa21.py)
- Add unit tests for:
  - currency parsing
  - height/weight parsing
  - team/contract splitting
- Add a small config (YAML/JSON) for parsing rules and imputation strategies
- Add a LICENSE (MIT recommended) if you want permissive reuse

---

## 💬 Contact
Maintainer: Sarwar Rimon (GitHub: @SarwarRimon)