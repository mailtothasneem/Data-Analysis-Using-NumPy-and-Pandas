# Data-Analysis-Using-NumPy-and-Pandas
“Data analysis project demonstrating the use of NumPy and Pandas for dataset creation, exploration, manipulation, and summarization. Includes examples of indexing, slicing, grouping, aggregation, and visualization for practical insights.”

## 📌 Project Overview

This project demonstrates fundamental **data analysis operations using Python, NumPy, and Pandas**. The assignment focuses on creating and manipulating arrays, working with Pandas Series and DataFrames, exploring datasets, filtering and selecting data, performing aggregation, and modifying DataFrame contents.

The project was completed using **Jupyter Notebook** and covers practical data analysis operations that form a foundation for further learning in **Data Analytics and Data Science**.

---

## 🎯 Objectives

The main objectives of this assignment are:

* Create and manage datasets using Python dictionaries and Pandas DataFrames.
* Create and perform operations on NumPy arrays.
* Understand array shape, data type, and number of elements.
* Perform NumPy indexing and slicing.
* Apply mathematical calculations using NumPy.
* Create and manipulate Pandas Series.
* Understand `loc` and `iloc` for accessing data.
* Apply Boolean filtering to Pandas Series and DataFrames.
* Create and explore Pandas DataFrames.
* Select specific columns and rows.
* Filter records based on conditions.
* Find unique values and value counts.
* Perform grouping and aggregation using `groupby()`.
* Modify existing DataFrame values.
* Add and remove DataFrame columns.
* Remove specific rows from a DataFrame.

---

## 🛠️ Tools & Technologies

* **Python 3**
* **NumPy**
* **Pandas**
* **Jupyter Notebook**
* **Anaconda / Python Environment**

### Libraries Used

```python
import numpy as np
import pandas as pd
```

The notebook uses NumPy and Pandas for numerical computing and data manipulation.

---

# 📚 Topics Covered

## 1. NumPy Array Operations

NumPy was used to create and analyze numerical arrays.

### 1D NumPy Array

A one-dimensional array was created using weekly temperature values:

```python
temp_w1 = [22.5, 25.3, 20.8, 23.4, 26.1, 24.8, 21.9]
temp_w1 = np.array(temp_w1)
```

The array was inspected using:

```python
temp_w1.shape
temp_w1.dtype
temp_w1.size
```

The resulting array contains **7 elements**, has a shape of `(7,)`, and uses the `float64` data type.

---

## 2. Temperature Conversion

The Celsius temperatures were converted into Fahrenheit using:

**Fahrenheit = (Celsius × 9/5) + 32**

```python
temp_fa = (temp_w1 * 9/5) + 32
```

The resulting Fahrenheit values were:

```text
[72.5, 77.54, 69.44, 74.12, 78.98, 76.64, 71.42]
```

The project also calculated:

* Maximum temperature: **78.98°F**
* Minimum temperature: **69.44°F**
* Mean temperature: **74.3771°F**

---

## 3. NumPy Indexing and Slicing

Array indexing and slicing were used to retrieve specific portions of the temperature data.

### First Three Days

```python
temp_fa[0:3]
```

### Last Two Days

```python
temp_fa[-2:]
```

### Middle Three Days

```python
temp_fa[2:5]
```

This demonstrates how NumPy can efficiently access subsets of an array.

---

## 4. Two-Dimensional NumPy Array

A 2D array was created to represent temperatures for two different weeks.

```python
temp2d = [
    [22.5, 25.3, 20.8, 23.4, 26.1, 24.8, 21.9],
    [19.2, 22.5, 21.3, 24.0, 23.5, 22.8, 20.1]
]

arr_2d = np.array(temp2d)
```

The array was inspected using:

```python
arr_2d.shape
arr_2d.dtype
arr_2d.size
```

Results:

* Shape: `(2, 7)`
* Data type: `float64`
* Number of elements: `14`

The project also extracted the complete temperature values for each week and the last two days of each week.

---

# 🐼 Pandas Series

## 5. Creating a Pandas Series

A Pandas Series was created using student marks and custom index labels.

```python
marks = pd.Series(
    [95, 92, 89, 85, 80],
    index=['Rank1', 'Rank2', 'Rank3', 'Rank4', 'Rank5']
)
```

The Series demonstrates the use of:

* Values
* Custom indexes
* Integer position
* Label-based access

---

## 6. Series Indexing and Slicing

Different methods were used to access Series data.

### Using `iloc`

```python
marks.iloc[0]
```

This retrieves the first value based on its integer position.

### Using `loc`

```python
marks.loc[['Rank1', 'Rank2', 'Rank3']]
```

This retrieves values using their index labels.

### Boolean Filtering

```python
marks[marks > 90]
```

This filters the Series and returns students whose marks are greater than 90.

---

## 7. Manipulating a Pandas Series

The Series was modified by:

### Updating a value

```python
marks['Rank1'] = 100
```

### Removing an entry

```python
marks = marks.drop('Rank5')
```

### Calculating CGPA

```python
CGPA = marks / 10
```

A DataFrame was then created containing both `Marks` and `CGPA`.

---

# 📊 Pandas DataFrame

## 8. Creating a DataFrame

A transaction dataset was created using a Python dictionary.

The dataset contains the following columns:

| Column            | Description                   |
| ----------------- | ----------------------------- |
| `TransactionID`   | Unique transaction identifier |
| `ProductCategory` | Product category              |
| `Region`          | Sales region                  |
| `Amount`          | Transaction amount            |

The product categories include:

* Electronics
* Clothing
* Furniture

The regions include:

* North
* South
* East
* West

The DataFrame contains **10 transactions and 4 columns**.

---

# 🔎 Data Exploration

## 9. Exploring the DataFrame

The following Pandas operations were performed:

### Display first rows

```python
df_data.head()
```

### Display last rows

```python
df_data.tail()
```

### Check DataFrame shape

```python
df_data.shape
```

Result:

```text
(10, 4)
```

### Display column names

```python
df_data.columns
```

### Check data types

```python
df_data.dtypes
```

The DataFrame contains:

* `TransactionID` – integer
* `ProductCategory` – string
* `Region` – string
* `Amount` – integer

---

## 10. Selecting Columns

Specific columns were selected from the DataFrame:

```python
df_data[['ProductCategory', 'Amount']]
```

The last three columns were retrieved using:

```python
df_data.iloc[:, -3:]
```

This demonstrates column selection using Pandas indexing.

---

# 🔍 Filtering Data

## 11. Conditional Filtering

Transactions were filtered where:

* Region is **North**
* Amount is **greater than 200**

```python
filter_df = df_data[
    (df_data['Region'] == 'North') &
    (df_data['Amount'] > 200)
]
```

The matching transactions were:

| TransactionID | ProductCategory | Region | Amount |
| ------------: | --------------- | ------ | -----: |
|           103 | Electronics     | North  |    300 |
|           106 | Electronics     | North  |    250 |
|           110 | Electronics     | North  |    400 |

This demonstrates how multiple conditions can be combined using Boolean operators.

---

# 📈 Aggregation and Summary

## 12. Value Counts

The number of transactions in each product category was calculated using:

```python
df_data['ProductCategory'].value_counts()
```

Results:

| Product Category | Count |
| ---------------- | ----: |
| Electronics      |     4 |
| Clothing         |     3 |
| Furniture        |     3 |

Electronics has the highest number of transactions in the dataset.

---

## 13. Unique Values

Unique regions were identified using:

```python
df_data['Region'].unique()
```

The dataset contains four unique regions:

```text
North
South
East
West
```

---

## 14. GroupBy and Mean Calculation

The average transaction amount for each region was calculated using:

```python
mean_amount = df_data.groupby('Region')['Amount'].mean()
```

Results:

| Region | Average Amount |
| ------ | -------------: |
| East   |          375.0 |
| North  |          287.5 |
| South  |          250.0 |
| West   |          190.0 |

Based on the calculated averages, **East has the highest average transaction amount**, while **West has the lowest average transaction amount**.

---

# ✏️ DataFrame Manipulation

## 15. Updating Data

The amount for Transaction ID `102` was changed from `150` to `165`.

```python
df_data.loc[
    df_data['TransactionID'] == 102,
    'Amount'
] = 165
```

---

## 16. Adding a New Column

A `Discount` column was created by calculating **10% of the Amount**.

```python
df_data['Discount'] = df_data['Amount'] * 0.10
```

For example:

```text
Amount = 200
Discount = 20
```

---

## 17. Removing a Row

The transaction with Transaction ID `109` was removed:

```python
df_data = df_data[
    df_data['TransactionID'] != 109
]
```

---

## 18. Deleting a Column

The temporary `Discount` column was removed using:

```python
df_data = df_data.drop(columns=['Discount'])
```

This demonstrates how Pandas can be used to modify an existing dataset by updating values, adding calculated columns, removing records, and deleting columns.

---

# 📌 Key Skills Demonstrated

Through this assignment, the following Python data analysis skills were practiced:

### NumPy

* Creating NumPy arrays
* 1D and 2D arrays
* Array properties
* Shape
* Data type
* Number of elements
* Mathematical calculations
* Indexing
* Slicing
* Maximum, minimum and mean calculations

### Pandas

* Creating Series
* Creating DataFrames
* Custom indexes
* `loc`
* `iloc`
* Boolean filtering
* Column selection
* Row selection
* `head()`
* `tail()`
* `shape`
* `columns`
* `dtypes`
* `unique()`
* `value_counts()`
* `groupby()`
* `mean()`
* Updating values
* Adding columns
* Removing rows
* Removing columns

---

# 📊 Dataset Summary

The transaction dataset used in the Pandas section contains:

* **10 initial transactions**
* **4 columns**
* **3 product categories**
* **4 regions**
* Transaction amounts ranging from **150 to 450** before the modification of Transaction ID 102
* A temporary `Discount` column calculated at 10% of the transaction amount

The dataset was created directly in Python using a dictionary and converted into a Pandas DataFrame.

---

# 💡 Key Insights

Some observations obtained from the analysis are:

1. **Electronics** has the highest number of transactions with 4 transactions.
2. **Clothing** and **Furniture** each have 3 transactions.
3. The dataset contains four regions: North, South, East and West.
4. **East** has the highest average transaction amount at **375.0**.
5. **West** has the lowest average transaction amount at **190.0**.
6. NumPy operations were used to calculate temperature statistics efficiently.
7. Pandas provided convenient methods for filtering, grouping, summarizing and manipulating tabular data.

---

# 🚀 Learning Outcomes

After completing this assignment, I gained practical experience in:

* Working with numerical data using NumPy.
* Working with structured data using Pandas.
* Understanding the difference between NumPy arrays and Pandas data structures.
* Accessing data using indexing and slicing.
* Filtering datasets using multiple conditions.
* Performing basic exploratory data analysis.
* Summarizing data using aggregation functions.
* Manipulating rows and columns in a DataFrame.
* Using Python for practical data analysis tasks.

---

# 📁 Project Structure

```text
Data-Analysis-Using-NumPy-and-Pandas/
│
├── Data analysis using NumPy and Pandas..ipynb
│
└── README.md
```

---

# ▶️ How to Run the Project

### 1. Clone the repository

```bash
git clone <your-repository-link>
```

### 2. Open the project folder

```bash
cd Data-Analysis-Using-NumPy-and-Pandas
```

### 3. Install the required libraries

```bash
pip install numpy pandas
```

### 4. Open the Jupyter Notebook

```bash
jupyter notebook
```

### 5. Open the notebook

Open:

```text
Data analysis using NumPy and Pandas..ipynb
```

Run the cells from top to bottom to reproduce the analysis.

---

# 👩‍💻 Author

**L Thasneem **

Aspiring AI Driven Data Analytics

---

## ⭐ Conclusion

This assignment provided hands-on practice with **NumPy and Pandas**, two important Python libraries used in data analysis. The exercises covered numerical array operations, Series, DataFrames, data exploration, filtering, aggregation, and data manipulation.

The project builds a strong foundation for progressing toward more advanced **Data Analytics, Data Visualization, and Data Science** concepts.

---

⭐ **If you find this project useful, feel free to star the repository!**
