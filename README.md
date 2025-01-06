# Home Sales Analysis with SparkSQL  

## Overview of the Analysis  

In this challenge, we use PySpark and SparkSQL to analyze home sales data. The dataset includes information on home prices, features, and construction dates, among other attributes. The goals of this project are:  
- To calculate key metrics about home sales using SparkSQL.  
- To explore Spark's functionality, including creating temporary views, caching tables, and partitioning data.  
- To measure and compare runtimes for cached and uncached queries.  

This project demonstrates the efficiency and scalability of Spark in handling large datasets and performing advanced SQL operations.

---

## Repository Structure  

```  
Home_Sales/  
│  
├── Home_Sales.ipynb       # Main notebook for analysis  
├── Resources/             # Data files and supporting materials  
│   ├── home_sales_revised.csv  
├── README.md              # Project documentation  
└── Output/                # Optional: Output files (e.g., formatted parquet data)  
```  

---

## Dataset  

The dataset (`home_sales_revised.csv`) contains the following key attributes:  

- **Bedrooms**: Number of bedrooms in the house.  
- **Bathrooms**: Number of bathrooms in the house.  
- **Floors**: Number of floors in the house.  
- **View**: A rating for the view of the house.  
- **Price**: The sale price of the home.  
- **Square Feet**: The size of the house in square feet.  
- **Year Built**: The year the home was constructed.  

---

## Analysis Steps  

### Step 1: Data Preparation  

1. Renamed the starter code file as `Home_Sales.ipynb`.  
2. Imported necessary PySpark SQL functions.  
3. Loaded the `home_sales_revised.csv` data into a Spark DataFrame.  
4. Created a temporary table named `home_sales` for querying with SparkSQL.  

### Step 2: SparkSQL Queries  

Answered the following questions using SparkSQL:  

1. **Average price of four-bedroom houses sold for each year**:  
   - Rounded to two decimal places.  

2. **Average price of homes built in each year that have three bedrooms and three bathrooms**:  
   - Rounded to two decimal places.  

3. **Average price of homes built in each year with specific conditions**:  
   - Homes with three bedrooms, three bathrooms, two floors, and at least 2,000 square feet.  
   - Rounded to two decimal places.  

4. **Average price of homes by "view" rating with average price ≥ $350,000**:  
   - Measured and recorded the query runtime.  

### Step 3: Caching and Query Optimization  

1. Cached the `home_sales` table using Spark's caching functionality.  
2. Verified that the table was cached.  
3. Re-ran the query on cached data to calculate the average price of homes by "view" rating and recorded the runtime. Compared it with the uncached runtime.  

### Step 4: Partitioning and Parquet Data  

1. Partitioned the data by the `date_built` column and saved it in Parquet format.  
2. Created a temporary table for the Parquet data.  
3. Re-ran the query on the partitioned data and recorded the runtime. Compared it with both cached and uncached runtimes.  

### Step 5: Uncaching the Table  

1. Uncached the `home_sales` table.  
2. Verified that the table was successfully uncached using PySpark.  

---

## Results  

### Key Metrics  

- **Average Price for Four-Bedroom Houses by Year**:  
  - (Example) *2019: $303,263.70, 2020: $298,353.78, etc.*  

- **Average Price of Homes with Three Bedrooms and Bathrooms by Year Built**:  
  - (Example) *2010: $292,859.62, 2015: $288,770.30, etc.*  

- **Average Price for Specific Conditions**:  
  - (Example) *2010: $285,010.22, 2015: $297,609.97, etc.*  

- **Average Price by "View" Rating (≥ $350,000)**:  
  - (Example) *View 31: $399,856.95, View 85: $1,056,336.74, etc.*  

### Runtime Comparison  

| Query Type                | Runtime (seconds) |  
|---------------------------|-------------------|  
| Uncached Query            | 1.341833353042603 |  
| Cached Query              | 0.222343921661377 |  
| Partitioned Data Query    | 0.036556243896484 |  

### Observations  

- **Caching** significantly reduced query runtime compared to uncached execution.  
- **Partitioning** further improved runtime by reducing the data scanned during query execution.  

---

## Summary  

Using PySpark and SparkSQL, we analyzed and optimized queries on the home sales dataset. The caching and partitioning techniques demonstrated how Spark can handle large datasets efficiently, delivering faster insights compared to traditional methods.  

### Recommendations  

1. **Adopt Spark for Large-Scale Data**:  
   - The scalability and efficiency of Spark make it an ideal choice for analyzing large datasets.  

2. **Implement Partitioning for Regular Analysis**:  
   - Partitioning data by key fields (e.g., year built) can optimize query performance for routine reporting.  

3. **Use Caching for Frequently Accessed Data**:  
   - Caching temporary tables can save time when running repeated queries.  

---

## How to Run the Project  

1. **Clone the Repository**  
   ```bash  
   git clone https://github.com/your-username/Home_Sales.git  
   cd Home_Sales  
   ```  

2. **Set Up the Environment**  
   - Install PySpark and other dependencies:  
     ```bash  
     pip install pyspark  
     ```  

3. **Run the Notebook**  
   - Open `Home_Sales.ipynb` in Jupyter Notebook or a compatible environment.  
   - Run all cells to reproduce the analysis and results.  

---

## Tools and Technologies  

- **PySpark**: For large-scale data processing and SQL querying.  
- **SparkSQL**: To perform SQL operations on the dataset.  
- **Parquet**: For optimized data storage and retrieval.  
- **Jupyter Notebook**: Interactive environment for running PySpark code.  
