# Python DA Assignment 1: Data Analysis Using NumPy and Pandas

## Project Overview

This project is **Python DA Assignment 1: Data Analysis Using NumPy and Pandas**. The assignment demonstrates fundamental data analysis operations using **NumPy** and **Pandas** in a Jupyter Notebook.

The assignment covers NumPy array creation and analysis, temperature calculations, array slicing, Pandas Series operations, and Pandas DataFrame exploration and manipulation.

---

## Project Information

| Category | Details |
|---|---|
| Assignment | Python DA Assignment 1 |
| Project Title | Data Analysis Using NumPy and Pandas |
| Programming Language | Python |
| Libraries | NumPy, Pandas |
| Development Environment | Jupyter Notebook |
| Notebook File | `Python_DA_Assignment_1.ipynb` |
| Instruction File | Assignment Instructions PDF |

---

## Objectives

The main objectives of this assignment are:

- To create and manipulate NumPy arrays.
- To inspect NumPy array properties such as shape, data type, and number of elements.
- To perform mathematical calculations using NumPy.
- To perform array slicing and indexing.
- To create and manipulate Pandas Series.
- To use `loc` and `iloc` for data access.
- To apply Boolean filtering.
- To create and explore Pandas DataFrames.
- To filter and group DataFrame data.
- To calculate value counts, unique values, and regional averages.
- To modify, add, and remove DataFrame data.

---

# 1. NumPy Array Operations

## 1.1 Creating a 1D NumPy Array

The first step was to create a one-dimensional NumPy array containing the Week 1 temperature values.

### Code

```python
temperatures_w1 = np.array([22.5, 25.3, 20.8, 23.4, 26.1, 24.8, 21.9])
```

### Output

```text
[22.5 25.3 20.8 23.4 26.1 24.8 21.9]
```

---

## 1.2 Inspecting the Array

The shape, data type, and number of elements were inspected.

### Code

```python
print("Shape:", temperatures_w1.shape)
print("Data Type:", temperatures_w1.dtype)
print("Number of Elements:", temperatures_w1.size)
```

### Output

```text
Shape: (7,)
Data Type: float64
Number of Elements: 7
```

---

## 1.3 Celsius to Fahrenheit Conversion and Statistics

The temperatures were converted from Celsius to Fahrenheit using:

**Fahrenheit = (Celsius × 9/5) + 32**

The maximum, minimum, and mean temperatures were also calculated.

### Code

```python
temperatures_f = (temperatures_w1 * 9/5) + 32

print("Temperatures in Fahrenheit:", temperatures_f)
print("Maximum Temperature:", np.max(temperatures_w1))
print("Minimum Temperature:", np.min(temperatures_w1))
print("Mean Temperature:", np.mean(temperatures_w1))
```

### Output

```text
Temperatures in Fahrenheit:
[72.5  77.54 69.44 74.12 78.98 76.64 71.42]

Maximum Temperature: 26.1
Minimum Temperature: 20.8
Mean Temperature: 23.542857142857144
```

---

## 1.4 Array Slicing

The first three days, weekend temperatures, and middle three days were extracted.

### Code

```python
print("First Three Days:", temperatures_w1[:3])
print("Weekend Temperatures:", temperatures_w1[-2:])
print("Middle Three Days:", temperatures_w1[2:5])
```

### Output

```text
First Three Days: [22.5 25.3 20.8]
Weekend Temperatures: [24.8 21.9]
Middle Three Days: [20.8 23.4 26.1]
```

---

## 1.5 Creating a 2D Temperature Array

A two-dimensional NumPy array containing temperatures for Week 1 and Week 2 was created.

### Code

```python
temperatures = np.array([
    [22.5, 25.3, 20.8, 23.4, 26.1, 24.8, 21.9],
    [19.2, 22.5, 21.3, 24.0, 23.5, 22.8, 20.1]
])

print(temperatures)
```

### Output

```text
[[22.5 25.3 20.8 23.4 26.1 24.8 21.9]
 [19.2 22.5 21.3 24.  23.5 22.8 20.1]]
```

---

## 1.6 Inspecting and Extracting Data from the 2D Array

### Code

```python
print("Shape:", temperatures.shape)
print("Data Type:", temperatures.dtype)
print("Total Number of Elements:", temperatures.size)
print("Week 1 Temperatures:", temperatures[0])
print("Week 2 Temperatures:", temperatures[1])
print("Week 1 Weekend:", temperatures[0, -2:])
print("Week 2 Weekend:", temperatures[1, -2:])
```

### Output

```text
Shape: (2, 7)
Data Type: float64
Total Number of Elements: 14

Week 1 Temperatures:
[22.5 25.3 20.8 23.4 26.1 24.8 21.9]

Week 2 Temperatures:
[19.2 22.5 21.3 24.  23.5 22.8 20.1]

Week 1 Weekend:
[24.8 21.9]

Week 2 Weekend:
[22.8 20.1]
```

---

# 2. Pandas Series

## 2.1 Creating a Pandas Series

A Pandas Series was created using marks with custom rank-based indices.

### Code

```python
marks = pd.Series(
    [95, 92, 89, 85, 80],
    index=['Rank1', 'Rank2', 'Rank3', 'Rank4', 'Rank5']
)

print(marks)
```

### Output

```text
Rank1    95
Rank2    92
Rank3    89
Rank4    85
Rank5    80
dtype: int64
```

---

## 2.2 Accessing and Filtering Series Data

Integer indexing, `loc`, `iloc`, and Boolean filtering were used.

### Code

```python
print("Mark of 1st Rank Student:", marks.iloc[0])

print("Marks of Top 3 Ranks:")
print(marks.loc[['Rank1', 'Rank2', 'Rank3']])

print("Mark of 3rd Rank Student:", marks.iloc[2])

print("Ranks with Marks Greater than 90:")
print(marks[marks > 90])
```

### Output

```text
Mark of 1st Rank Student: 95

Marks of Top 3 Ranks:
Rank1    95
Rank2    92
Rank3    89
dtype: int64

Mark of 3rd Rank Student: 89

Ranks with Marks Greater than 90:
Rank1    95
Rank2    92
dtype: int64
```

---

## 2.3 Modifying, Removing, and Calculating CGPA

Rank 1 was changed to 100, Rank 5 was removed, and CGPA was calculated by dividing the remaining marks by 10.

### Code

```python
marks.loc['Rank1'] = 100

print("After Modifying Rank1:")
print(marks)

marks = marks.drop('Rank5')

print("After Removing Rank5:")
print(marks)

cgpa = marks / 10

print("CGPA:")
print(cgpa)
```

### Output

```text
After Modifying Rank1:
Rank1    100
Rank2     92
Rank3     89
Rank4     85
Rank5     80
dtype: int64

After Removing Rank5:
Rank1    100
Rank2     92
Rank3     89
Rank4     85
dtype: int64

CGPA:
Rank1    10.0
Rank2     9.2
Rank3     8.9
Rank4     8.5
dtype: float64
```

---

# 3. Pandas DataFrame

## 3.1 Creating the Transactions DataFrame

A transaction DataFrame containing Transaction ID, Product Category, Region, and Amount was created.

### Code

```python
transactions = pd.DataFrame({
    'TransactionID': [101, 102, 103, 104, 105, 106, 107, 108, 109, 110],
    'ProductCategory': [
        'Electronics', 'Clothing', 'Electronics', 'Furniture',
        'Clothing', 'Electronics', 'Furniture', 'Clothing',
        'Furniture', 'Electronics'
    ],
    'Region': [
        'North', 'South', 'North', 'East', 'West',
        'North', 'East', 'West', 'South', 'North'
    ],
    'Amount': [200, 150, 300, 450, 200, 250, 300, 180, 350, 400]
})

print(transactions)
```

### Output

```text
   TransactionID ProductCategory Region  Amount
0            101     Electronics  North     200
1            102        Clothing  South     150
2            103     Electronics  North     300
3            104       Furniture   East     450
4            105        Clothing   West     200
5            106     Electronics  North     250
6            107       Furniture   East     300
7            108        Clothing   West     180
8            109       Furniture  South     350
9            110     Electronics  North     400
```

---

## 3.2 DataFrame Exploration

The complete DataFrame, head, tail, shape, column names, data types, and basic information were examined.

### Code

```python
print("Transactions DataFrame:")
print(transactions)

print("\nHead:")
print(transactions.head())

print("\nTail:")
print(transactions.tail())

print("\nShape:")
print(transactions.shape)

print("\nColumn Names:")
print(transactions.columns)

print("\nData Types:")
print(transactions.dtypes)

print("\nBasic Information:")
transactions.info()
```

### Key Output

```text
Shape:
(10, 4)

Column Names:
Index(['TransactionID', 'ProductCategory', 'Region', 'Amount'], dtype='str')

Data Types:
TransactionID      int64
ProductCategory      str
Region               str
Amount             int64
```

The DataFrame contained **10 transactions and 4 columns**.

---

## 3.3 Selecting Columns and Filtering Transactions

The ProductCategory and Amount columns were selected. The last three columns were retrieved, and transactions from the North region with Amount greater than 200 were filtered.

### Code

```python
print("ProductCategory and Amount:")
print(transactions[['ProductCategory', 'Amount']])

print("\nLast Three Columns:")
print(transactions.iloc[:, -3:])

print("\nRegion is North and Amount is Greater than 200:")
print(transactions[
    (transactions['Region'] == 'North') &
    (transactions['Amount'] > 200)
])
```

### Output

```text
ProductCategory and Amount:
  ProductCategory  Amount
0     Electronics     200
1        Clothing     150
2     Electronics     300
3       Furniture     450
4        Clothing     200
5     Electronics     250
6       Furniture     300
7        Clothing     180
8       Furniture     350
9     Electronics     400

Region is North and Amount is Greater than 200:
   TransactionID ProductCategory Region  Amount
2            103     Electronics  North     300
5            106     Electronics  North     250
9            110     Electronics  North     400
```

---

## 3.4 Category Counts, Unique Regions, and Regional Mean

The frequency of each product category, unique regions, and mean transaction amount for each region were calculated.

### Code

```python
print("Value Counts for ProductCategory:")
print(transactions['ProductCategory'].value_counts())

print("\nUnique Values in Region:")
print(transactions['Region'].unique())

print("\nMean Amount for Each Region:")
print(transactions.groupby('Region')['Amount'].mean())
```

### Output

```text
Value Counts for ProductCategory:
Electronics    4
Clothing       3
Furniture      3

Unique Values in Region:
['North', 'South', 'East', 'West']

Mean Amount for Each Region:
East     375.0
North    287.5
South    250.0
West     190.0
```

---

## 3.5 Modifying a Transaction Amount

The Amount for TransactionID 102 was changed from 150 to 165.

### Code

```python
transactions.loc[
    transactions['TransactionID'] == 102,
    'Amount'
] = 165

print(transactions)
```

### Result

TransactionID `102` was successfully updated:

```text
102    Clothing    South    165
```

---

## 3.6 Adding a Discount Column

A new Discount column was created using 10% of the transaction Amount.

### Code

```python
transactions['Discount'] = transactions['Amount'] * 0.10

print(transactions)
```

### Output

```text
TransactionID  Amount  Discount
101            200     20.0
102            165     16.5
103            300     30.0
104            450     45.0
105            200     20.0
106            250     25.0
107            300     30.0
108            180     18.0
109            350     35.0
110            400     40.0
```

---

## 3.7 Removing TransactionID 109

The row corresponding to TransactionID 109 was removed.

### Code

```python
transactions = transactions[
    transactions['TransactionID'] != 109
]

print(transactions)
```

### Result

TransactionID `109` was successfully removed, leaving **9 transactions**.

---

## 3.8 Removing the Discount Column

The final step was to remove the temporary Discount column.

### Code

```python
transactions = transactions.drop(columns=['Discount'])

print(transactions)
```

### Final Output

```text
   TransactionID ProductCategory Region  Amount
0            101     Electronics  North     200
1            102        Clothing  South     165
2            103     Electronics  North     300
3            104       Furniture   East     450
4            105        Clothing   West     200
5            106     Electronics  North     250
6            107       Furniture   East     300
7            108        Clothing   West     180
9            110     Electronics  North     400
```

---

# Final Results

The assignment successfully demonstrated:

- NumPy 1D and 2D array creation.
- NumPy array properties and slicing.
- Celsius-to-Fahrenheit conversion.
- Maximum, minimum, and mean calculations.
- Pandas Series creation and custom indexing.
- Integer position indexing using `iloc`.
- Label-based selection using `loc`.
- Boolean filtering.
- Series modification and deletion.
- CGPA calculation.
- Pandas DataFrame creation and inspection.
- Column selection and row filtering.
- Product category frequency analysis.
- Unique region identification.
- GroupBy and mean calculations.
- DataFrame value modification.
- Adding and deleting DataFrame columns.
- Removing specific DataFrame rows.

---

# Files Included

| File | Description |
|---|---|
| `Python_DA_Assignment_1.ipynb` | Completed Jupyter Notebook containing the Python code and outputs |
| Assignment Instructions PDF | Original assignment instructions provided for the task |
| `README.md` | Project documentation and summary |

---

# Tools and Technologies

- **Python**
- **NumPy**
- **Pandas**
- **Jupyter Notebook**
- **GitHub**

---

# How to Run the Project

1. Download or clone this repository.
2. Open `Python_DA_Assignment_1.ipynb` using Jupyter Notebook or JupyterLab.
3. Make sure Python is installed.
4. Make sure NumPy and Pandas are installed.
5. Run the notebook cells in sequence.
6. Review the displayed outputs for each assignment section.

Required libraries:

```python
import numpy as np
import pandas as pd
```

---

# Conclusion

This assignment provided practical experience in using **NumPy and Pandas for data analysis in Python**.

The NumPy section demonstrated array creation, inspection, mathematical calculations, temperature conversion, indexing, and slicing. The Pandas Series section demonstrated custom indexing, `loc`, `iloc`, Boolean filtering, modification, deletion, and CGPA calculation. The Pandas DataFrame section demonstrated data creation, exploration, filtering, aggregation, grouping, updating values, adding columns, and removing rows and columns.

Overall, the assignment successfully strengthened fundamental Python data analysis skills and provided hands-on experience working with structured data using **NumPy and Pandas** in a Jupyter Notebook environment.
