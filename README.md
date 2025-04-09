# Online-Retail-Dataset (UCI-Machine-Learning-Repository) Power-BI Dashboard Insights Visualizations
This repository contains a Power BI dashboard for analyzing the Online Retail Dataset (UCI Machine Learning Repository). It provides key business insights using DAX measures and interactive visualizations. This main heading covers all aspects of customer behavior, purchase patterns, and monetary analysis.
## 📊 Online Retail Analysis – Python & Power BI 🚀  

### **Overview**  
This repository contains a **comprehensive analysis and dashboard** for the **Online Retail Dataset** (UCI Machine Learning Repository). The project involves:  
✅ **Data Cleaning & Feature Engineering** using **Python (Pandas, NumPy, etc.)**  
✅ **Advanced Data Analysis** with **Python** and **DAX functions in Power BI**  
✅ **Interactive Dashboard in Power BI** for business insights  

### **Tech Stack**  
🔹 **Python** – Data cleaning, feature engineering, and exploratory analysis  
🔹 **Pandas & NumPy** – Data manipulation  
🔹 **Power BI** – Data visualization and dashboard creation  
🔹 **DAX (Data Analysis Expressions)** – Custom calculations for business insights  

---

## 🔍 **Python-Based Data Cleaning & Feature Engineering**  
### **Steps Performed**  
✔️ **Data Preprocessing** – Handling missing values, duplicates, and data type conversions  
✔️ **Feature Engineering**  
   - Added **Month, DayOfWeek, and Monetary Value**  
   - Calculated **Purchase Frequency** and **Average Order Value**  
   - Created **Customer Lifetime Value (CLV)**  
   - Defined **Target Variable** using Median Monetary Value  
✔️ **Data Transformation** – Aggregation and grouping for customer segmentation  

### **Key Python Code Snippets**  
```python
# Add Month Column
df['Month'] = pd.to_datetime(df['InvoiceDate']).dt.month  

# Calculate Monetary Value (Total Revenue per Customer)
df['TotalAmount'] = df['Quantity'] * df['UnitPrice']  
df['MonetaryValue'] = df.groupby('CustomerID')['TotalAmount'].transform('sum')  

# Create a Target Variable (High-Value Customers)
df['Target'] = (df['MonetaryValue'] > df['MonetaryValue'].median()).astype(int)  

# Calculate Purchase Frequency
df['PurchaseFrequency'] = df.groupby('CustomerID')['InvoiceNo'].transform('nunique')  

# Average Order Value
df['AverageOrderValue'] = df['MonetaryValue'] / df['PurchaseFrequency']  

# Customer Lifetime Value (CLV)
df['CLV'] = df['AverageOrderValue'] * df['PurchaseFrequency']
```

---

## 📊 **Power BI Dashboard – Insights & Visualizations**  
### **Metrics & KPIs**  
📌 **Total Revenue, Orders, AOV, CLV, Repeat Customers**  
📌 **Customer Segmentation (RFM Analysis – Recency, Frequency, Monetary)**  
📌 **Churn & Retention Rate**  

### **Charts & Visuals**  
📈 **Revenue & Orders Trend Over Time**  
📊 **Sales by Month, Day of the Week**  
📦 **Top Products & Categories**  
👥 **Customer Segmentation by Spending Patterns**  
🌍 **Sales by Country (Map Visualization)**  
📉 **Churn & Repeat Customer Analysis**  

### **DAX Functions Used**  
```DAX
# Total Revenue
TotalRevenue = SUM(Orders[TotalAmount])

# Average Order Value (AOV)
AOV = DIVIDE([TotalRevenue], DISTINCTCOUNT(Orders[InvoiceNo]))

# Customer Lifetime Value (CLV)
CLV = [AOV] * [PurchaseFrequency]

# Repeat Customer Rate
RepeatCustomerRate = DIVIDE(DISTINCTCOUNT(Customers[CustomerID]), COUNT(Customers[CustomerID]))
```

---

## ⚡ **How to Use**  
1️⃣ Clone the repository and install dependencies (`pandas`, `numpy`, etc.)  
2️⃣ Load the dataset and run Python scripts for preprocessing  
3️⃣ Open **Power BI** and import the cleaned dataset  
4️⃣ Explore **interactive insights and reports**!  

---

# Enhancements & Tips for Data Analysis

## 1️⃣ KPIs & Summary Cards
- **Conditional Formatting**: Implement conditional formatting to highlight performance metrics, using green for growth and red for decline.
- **Tooltips**: Add tooltips for deeper insights, such as providing a revenue breakdown by region when hovering over data points.

## 2️⃣ Sales Performance Trends
- **Revenue Over Time**: Include a forecast line in your revenue over time analysis to predict future trends based on historical data.
- **Sales by Day of the Week**: Utilize a heatmap instead of a column chart for better pattern recognition in sales data across different days.

## 3️⃣ Customer Segmentation & Behavior
- **RFM Analysis**: Conduct RFM (Recency, Frequency, Monetary) analysis and visualize customer segments using a clustered scatter chart.
- **Top 10 High-Value Customers**: Create a drill-through page to analyze individual details of your top 10 high-value customers for deeper insights.

## 4️⃣ Product & Order Analysis
- **Top-Selling Products**: Display the percentage contribution of each product to total sales to highlight key revenue drivers.
- **Order Frequency by Country**: Implement a bubble map to visualize order frequency by country for a more impactful presentation of geographical data.

## 5️⃣ Discount & Pricing Insights
- **Revenue Contribution by Price Range**: Overlay a density curve on your revenue contribution analysis to identify pricing sweet spots and optimize pricing strategies.

## 6️⃣ Customer Retention & Churn Analysis
- **New vs. Returning Customers**: Use a funnel chart to track conversion rates from new customers to loyal returning customers effectively.
- **Churn Risk Histogram**: Apply dynamic segments (e.g., High, Medium, Low Risk) to visualize churn risk across different customer segments.

## 📢 **Contributions & Feedback**  
💡 Feel free to fork, modify, and submit PRs  
📩 Have suggestions? Open an issue or reach out!  

---

⭐ **Star this repository if you find it useful!** 🚀
