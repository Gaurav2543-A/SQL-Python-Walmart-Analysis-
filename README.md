# Walmart Sales Data Analysis Project

This project is an end-to-end data analysis solution designed to extract critical business insights from Walmart sales data. It leverages **Python** for data processing and analysis, **SQL** for advanced querying, and **structured problem-solving techniques** to answer key business questions. The project is ideal for data analysts looking to develop skills in **data manipulation, SQL querying, and data pipeline creation**.

---

## 📌 Project Overview

### **Objectives:**
- Perform **data cleaning and transformation** to ensure accurate analysis.
- Use **SQL queries** to generate business insights from Walmart’s sales dataset.
- Analyze **sales trends, customer behavior, and profitability** across multiple dimensions.
- Implement **feature engineering** for enhanced analysis.
- Load and analyze data using **MySQL and PostgreSQL**.
- Document the project and present findings clearly.

### **Tools & Technologies Used:**
- **Python Libraries:** `pandas`, `numpy`, `sqlalchemy`, `mysql-connector-python`, `psycopg2`
- **SQL Databases:** MySQL, PostgreSQL
- **Jupyter Notebook** for Python-based analysis
- **Kaggle API** for data retrieval

---

## 🚀 Project Workflow

### **1️⃣ Set Up the Environment**
- **Tools Used:** Jupyter Notebook (Python), SQL (MySQL/PostgreSQL)
- Install required Python libraries:
  ```bash
  pip install pandas numpy sqlalchemy mysql-connector-python psycopg2
  ```

### **2️⃣ Data Acquisition**
- **Dataset Source:** [Walmart Sales Dataset](https://www.kaggle.com/najir0123/walmart-10k-sales-datasets)
- **Kaggle API Setup:**
  1. Obtain your Kaggle API token from [Kaggle](https://www.kaggle.com/) (Profile → API → Create New Token).
  2. Place the `kaggle.json` file in the `.kaggle/` directory.
  3. Download dataset using:
     ```bash
     kaggle datasets download -d <dataset-path>
     ```
- Store the data in the `data/` folder for easy reference.

### **3️⃣ Data Exploration & Cleaning**
- Load the dataset into a Pandas DataFrame.
- Check for missing values, duplicate entries, and data inconsistencies.
- Convert relevant columns to appropriate data types (`datetime`, `float`, etc.).
- Validate data correctness before moving to analysis.

### **4️⃣ Feature Engineering**
- **Calculate `Total_Amount`**: `unit_price * quantity`.
- **Extract Time-Based Features**: Create `Day of the Week`, `Hour of Purchase`, etc.
- **Categorize Sales Periods**: Morning, Afternoon, Evening shifts.

### **5️⃣ Data Storage & SQL Analysis**
- **Load data into MySQL and PostgreSQL** using `sqlalchemy`.
- **Execute SQL queries** to analyze:
  - **Revenue trends** across branches and product categories.
  - **Best-selling products** and payment methods.
  - **Peak shopping hours** and customer behavior patterns.
  - **Profitability analysis** by branch and product type.

### **6️⃣ Key SQL Queries & Insights**
Some advanced SQL queries used in the project:
- **Total revenue per branch:**
  ```sql
  SELECT Branch, SUM(Totals) AS Total_Revenue FROM walmart GROUP BY Branch ORDER BY Total_Revenue DESC;
  ```
- **Most commonly used payment method per branch:**
  ```sql
  SELECT Branch, payment_method FROM (
      SELECT Branch, payment_method, COUNT(payment_method) AS method_count,
             RANK() OVER (PARTITION BY Branch ORDER BY COUNT(payment_method) DESC) AS rank2
      FROM walmart GROUP BY Branch, payment_method
  ) ranked_methods WHERE rank2 = 1;
  ```
- **Peak transaction hours per branch:**
  ```sql
  SELECT Branch, HOUR(STR_TO_DATE(time, '%H:%i:%s')) AS Peak_time, COUNT(*) AS Transactions
  FROM walmart GROUP BY Branch, Peak_time ORDER BY Transactions DESC;
  ```

### **7️⃣ Project Documentation & Publishing**
- Maintain **well-structured documentation** using Markdown (`README.md`) or Jupyter Notebook.
- Publish the project on **GitHub**, including:
  - `README.md` (this document)
  - Jupyter Notebooks
  - SQL query scripts
  - Data files (if possible) or instructions to download them.

---

## 📂 Project Structure

```plaintext
|-- data/                     # Raw and transformed data files
|-- sql_queries/              # SQL scripts for analysis
|-- notebooks/                # Jupyter notebooks for Python analysis
|-- README.md                 # Project documentation
|-- requirements.txt          # Required Python libraries
```

---

## 📊 Results & Insights

- **Sales Insights:**
  - Top revenue-generating branches and product categories identified.
  - Most commonly used payment methods per location.
- **Profitability Analysis:**
  - Most profitable products and cities.
  - Branches with the highest revenue growth.
- **Customer Behavior Trends:**
  - Analysis of peak shopping hours.
  - Buying preferences based on payment methods and categories.

---

## 🔮 Future Enhancements

Potential extensions for further analysis and automation:
- **Dashboard Integration:** Using Power BI or Tableau for interactive reporting.
- **Predictive Analytics:** Implement machine learning models for sales forecasting.
- **Automated Data Pipelines:** Use **Apache Airflow** or **AWS Glue** for real-time processing.
- **Expanding Data Sources:** Incorporate customer demographics and external sales data.

---

## 🙌 Acknowledgments

- **Data Source:** Kaggle’s Walmart Sales Dataset.
- **Inspiration:** Walmart’s business case studies on sales and supply chain optimization.
- **Contributors:** Open-source community contributions to SQL best practices and data analysis methodologies.

---

## 📢 Getting Started

To set up the project locally:
1. Clone the repository:
   ```bash
   git clone <repo-url>
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Set up Kaggle API and download the dataset.
4. Load the data into **MySQL/PostgreSQL** and execute the SQL queries.

**Happy Analyzing! 🎯**

