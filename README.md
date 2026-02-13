#  ETL Data Pipeline Project

##  Project Overview

This project demonstrates a complete **ETL (Extract, Transform, Load)** pipeline using CSV files and a SQLite database.

The pipeline:

* Extracts data from multiple CSV files
* Transforms and cleans the data
* Loads the processed data into a SQLite database

This project is implemented using **Python** and **Jupyter Notebook**.

---

##  Project Structure

```
├── customers.csv
├── orders.csv
├── products.csv
├── database.sqlite
├── task14_etl.ipynb
└── README.md
```

---

## 🛠 Technologies Used

* Python 3.x
* Pandas
* SQLite
* Jupyter Notebook

---

##  ETL Process

### 1️ Extract

Data is extracted from:

* `customers.csv`
* `orders.csv`
* `products.csv`

Example:

```python
import pandas as pd

customers = pd.read_csv("customers.csv")
orders = pd.read_csv("orders.csv")
products = pd.read_csv("products.csv")
```

---

### 2️ Transform

Transformation steps include:

* Removing null values
* Handling duplicates
* Correcting data types
* Merging datasets
* Creating calculated columns

Example:

```python
merged_data = orders.merge(customers, on="customer_id")
merged_data = merged_data.merge(products, on="product_id")

merged_data["total_price"] = merged_data["quantity"] * merged_data["price"]
```

---

### 3️ Load

The cleaned and transformed data is loaded into a SQLite database:

```python
import sqlite3

conn = sqlite3.connect("database.sqlite")
merged_data.to_sql("final_table", conn, if_exists="replace", index=False)
conn.close()
```

---

##  How to Run the Project

1. Clone the repository:

```bash
git clone https://github.com/your-username/your-repo-name.git
```

2. Navigate to the project folder:

```bash
cd your-repo-name
```

3. Install required libraries:

```bash
pip install pandas
```

4. Open Jupyter Notebook:

```bash
jupyter notebook
```

5. Open `task14_etl.ipynb` and run all cells.

---

##  Output

* Cleaned and merged dataset
* Final data stored in `database.sqlite`
* SQL table created: `final_table`

---

##  Learning Outcomes

* Understanding ETL workflow
* Working with multiple CSV files
* Data cleaning and transformation
* Loading data into SQLite
* Building a structured data pipeline

---

##  Author
pratheep M
Pratheep Roz

---
