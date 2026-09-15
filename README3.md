# ECE2112 PA 2
## Submitted by: Jia Bernice C. Magcamit
## Section: 2ECE-A

---

##  Overview
This repository contains the solution for **Programming Assignment 3 (PA3)** in ECE 21112. The assignment focuses on data wrangling, indexing, filtering, and slicing operations using the `pandas` library in Python on the classic `cars.csv` (mtcars) dataset.

---

## Objectives

By completing this lab, students will learn to:

Load CSV files into Pandas DataFrames.

Extract specific rows and columns using label-based and positional indexing.

Apply conditional filters to DataFrame columns.

Generate subsetted copies of data while leaving the original dataset untouched.

Instructions & Guidelines

Dataset: Work with the provided cars.csv file (the same dataset from Experiment 3), which includes vehicle performance metrics alongside the Model column.

Environment: Implement all answers within a single Jupyter Notebook and import Pandas using the standard alias (import pandas as pd).

Initial Setup: Read cars.csv into a DataFrame variable named cars.

Dynamic Solutions: Rely strictly on Pandas slicing, indexing, and Boolean logic to derive outputs—never hardcode tables or values.

Data Integrity: Keep the primary cars DataFrame unmodified by storing all extracted subsets in separate DataFrames or Series.

Row Sequence: Maintain the original row order of the dataset throughout your operations unless instructed to reorder.

Output Verification: Ensure every generated output is clearly displayed in a run cell within the notebook.

### Problem A: Dataset Inspection & Positional Slicing

1. **Display Dataset Shape & Column Names**
   - **Task:** Load `cars.csv` using Pandas and display its dimensions (shape) and all column names.
   - **Code:**
     ```python
     import pandas as pd

     cars = pd.read_csv('cars.csv')
     print("Shape of cars:", cars.shape)
     print("Column names of cars:", cars.columns.tolist())
     ```
   - **Output:**
     - **Shape:** `(32, 12)` (32 rows, 12 columns)
     - **Columns:** `['Model', 'mpg', 'cyl', 'disp', 'hp', 'drat', 'wt', 'qsec', 'vs', 'am', 'gear', 'carb']`

2. **Positional Slicing (Rows 6 to 10)**
   - **Task:** Extract rows 6 through 10 (1-based index) into a variable named `cars_6_to_10`.
   - **Code:**
     ```python
     cars_6_to_10 = cars.iloc[5:10]
     ```
   - **Result:** Extracts index 5 through index 9 (Valiant, Duster 360, Merc 240D, Merc 230, Merc 280).

3. **Subsetting Specific Columns**
   - **Task:** From `cars_6_to_10`, select and display only `Model`, `mpg`, `cyl`, `hp`, and `gear` in that specific order.
   - **Code:**
     ```python
     cars_6_to_10[['Model', 'mpg', 'cyl', 'hp', 'gear']]
     ```

---

### Problem B: Conditional Selection & Slicing

1. **Filtering by Model (Full Record)**
   - **Task:** Extract all details for the model `'Toyota Corolla'`.
   - **Code:**
     ```python
     toyota = cars[cars['Model'] == 'Toyota Corolla']
     ```

2. **Filtering by Model with Specific Columns**
   - **Task:** Extract the `Model`, `mpg`, `hp`, and `wt` columns for the `'Pontiac Firebird'`.
   - **Code:**
     ```python
     pontiac = cars.loc[cars['Model'] == 'Pontiac Firebird', ['Model', 'mpg', 'hp', 'wt']]
     ```

---

### Problem C: Multi-Condition Data Extraction

- **Task:** Extract specific attributes (`Model`, `mpg`, `cyl`, `hp`, `gear`) for the models `'Datsun 710'`, `'Lotus Europa'`, and `'Ferrari Dino'`. Print the shape of the filtered result.
- **Code:**
  ```python
  models = ["Datsun 710", "Lotus Europa", "Ferrari Dino"]
  selected_cars = cars.loc[cars["Model"].isin(models), ["Model", "mpg", "cyl", "hp", "gear"]]

  print("Shape of selected_cars:
", selected_cars.shape)
  ```
- **Output Shape:** `(3, 5)`

