
# Walmart Sales Data Analysis & MySQL ETL Project

## 📌 Project Overview

This project demonstrates an end-to-end data processing workflow using a Walmart sales dataset obtained from **Kaggle**.

The dataset is loaded and processed using **Python and Pandas** in **Jupyter Notebook**, followed by data cleaning and transformation. The processed data is then loaded into **MySQL Server** using **SQLAlchemy** and **PyMySQL**.

The project helps demonstrate practical skills in:

* Data ingestion
* Data cleaning
* Data transformation
* Python/Pandas
* Database connectivity
* ETL workflow
* Loading data into MySQL
* SQL data validation

---

## 🔄 Project Workflow

```text
             Kaggle
                │
                │ Dataset
                ▼
          CSV / Raw Data
                │
                ▼
       Jupyter Notebook
        (Anaconda/Python)
                │
                │ Pandas
                ▼
       Data Cleaning &
       Transformation
                │
                ▼
            SQLAlchemy
                │
             PyMySQL
                │
                ▼
          MySQL Server
                │
                ▼
         Walmart Table
```

---

## 🛠️ Technologies Used

| Technology       | Purpose                              |
| ---------------- | ------------------------------------ |
| Python           | Data processing and scripting        |
| Pandas           | Data cleaning and transformation     |
| Jupyter Notebook | Development environment              |
| Anaconda         | Python environment management        |
| Kaggle           | Dataset source                       |
| MySQL            | Target database                      |
| SQLAlchemy       | Database connection and data loading |
| PyMySQL          | MySQL database driver                |

---

## 📂 Project Structure

```text
Walmart-Data-Project/
│
├── data/
│   └── walmart.csv
│
├── notebooks/
│   └── walmart_analysis.ipynb
│
├── sql/
│   └── walmart_queries.sql
│
├── README.md
│
└── requirements.txt
```

---

## 📥 Dataset

The dataset used in this project was obtained from **Kaggle**.

After downloading the dataset, the CSV file is placed inside the `data` directory.

Example:

```text
data/
└── walmart.csv
```

---

## ⚙️ Environment Setup

### 1. Install Anaconda

Install Anaconda and use **Jupyter Notebook** to run the project.

Launch Jupyter Notebook using Anaconda Navigator or Anaconda Prompt:

```bash
jupyter notebook
```

---

### 2. Install Required Libraries

Install the required Python libraries:

```bash
pip install pandas pymysql sqlalchemy
```

The libraries can also be installed inside a Jupyter Notebook:

```python
!pip install pandas pymysql sqlalchemy
```

---

## 📊 Load Dataset Using Pandas

The dataset is loaded into a Pandas DataFrame:

```python
import pandas as pd

df = pd.read_csv("../data/walmart.csv")
```

Basic dataset inspection:

```python
df.head()
```

```python
df.shape
```

```python
df.columns
```

```python
df.dtypes
```

Check for missing values:

```python
df.isnull().sum()
```

---

## 🧹 Data Cleaning

The dataset is cleaned and transformed using Pandas before loading it into MySQL.

Examples of data-cleaning operations include:

### Remove duplicates

```python
df.drop_duplicates(inplace=True)
```

### Handle missing values

```python
df.fillna(0, inplace=True)
```

### Change data types

```python
df["quantity"] = df["quantity"].astype(int)
```

Additional transformations can be performed depending on the requirements of the dataset.

---

## 🗄️ MySQL Database Setup

Create a database in MySQL:

```sql
CREATE DATABASE walmart;
```

Select the database:

```sql
USE walmart;
```

The processed dataset will be loaded into a table named:

```text
walmart
```

---

## 🔌 Connect Python to MySQL

SQLAlchemy and PyMySQL are used to connect Jupyter Notebook to MySQL.

```python
import sqlalchemy as sal

engine = sal.create_engine(
    "mysql+pymysql://username:password@localhost:3306/walmart"
)

conn = engine.connect()
```

Replace `username` and `password` with your MySQL credentials.

---

## 📤 Load Data into MySQL

The Pandas DataFrame is loaded into MySQL using `to_sql()`:

```python
df.to_sql(
    "walmart",
    con=conn,
    index=False,
    if_exists="append"
)
```

### Parameters

* `walmart` → Target MySQL table
* `con=conn` → SQLAlchemy database connection
* `index=False` → Prevents the Pandas index from being inserted
* `if_exists="append"` → Adds records to the existing table

---

## 🔍 Data Validation in MySQL

After loading the data, the records can be validated using SQL.

### Check number of rows

```sql
SELECT COUNT(*)
FROM walmart;
```

### View records

```sql
SELECT *
FROM walmart
LIMIT 10;
```

### Check table structure

```sql
DESCRIBE walmart;
```

### Check for duplicates

```sql
SELECT column1, column2, COUNT(*)
FROM walmart
GROUP BY column1, column2
HAVING COUNT(*) > 1;
```

---

## 📈 Key Concepts Demonstrated

This project demonstrates the following data-engineering concepts:

* Data ingestion from an external source
* CSV file processing
* Pandas DataFrame operations
* Data cleaning
* Missing-value handling
* Duplicate handling
* Data type conversion
* Python-to-MySQL connectivity
* SQLAlchemy
* PyMySQL
* Loading data into a relational database
* SQL data validation
* Basic ETL workflow

---

## 🔧 Requirements

The main Python dependencies are:

```text
pandas
pymysql
sqlalchemy
```

You can create a `requirements.txt` file containing:

```text
pandas
pymysql
sqlalchemy
```

Then install all dependencies with:

```bash
pip install -r requirements.txt
```

---

## 📝 Note

`psycopg2` is not required for this project because it is a PostgreSQL database driver.

The database connection used here is:

```text
Python
   ↓
SQLAlchemy
   ↓
PyMySQL
   ↓
MySQL
```

---

## 🚀 Future Improvements

Possible improvements to this project include:

* Automating the data ingestion process
* Creating a scheduled ETL pipeline
* Adding data-quality checks
* Creating a proper data warehouse structure
* Creating fact and dimension tables
* Adding SQL analytics queries
* Connecting the MySQL database to Power BI
* Creating an interactive sales dashboard
* Deploying the pipeline to AWS

---

## 👨‍💻 Project Skills

This project demonstrates practical experience with:

**Python | Pandas | SQL | MySQL | SQLAlchemy | PyMySQL | Jupyter Notebook | ETL | Data Cleaning | Data Engineering**
