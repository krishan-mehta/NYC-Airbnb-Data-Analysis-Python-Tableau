# NYC-Airbnb-Data-Analysis-Python-Tableau

This project explores Airbnb listings across New York City to identify trends in pricing, reviews, room types, and host activity across different boroughs. The analysis provides insights into the Airbnb market landscape using data visualization and preprocessing techniques in Python.

---

## 📁 Dataset

The dataset contains Airbnb listing information from various neighborhoods in NYC, including:

- Host details  
- Neighbourhood groups  
- Room types  
- Price  
- Number of reviews  
- Booking activity  
- Geographic location  

---

## 🧹 Data Preprocessing

### ✅ Handling Outliers

To ensure a clean and realistic dataset:

- Outliers in the `price` and `number_of_reviews` fields were **detected and removed** using the **IQR (Interquartile Range) method**.
- This helped eliminate extreme values that could skew the analysis.

### ✅ Handling Missing Values

- Missing values were replaced with `NaN` using **`pandas`**, ensuring they could be handled cleanly during visual analysis or ignored when necessary.

```python
import pandas as pd
import numpy as np

# Load data
df = pd.read_csv('AB_NYC_2019.csv')

# Replace blanks with No Host Name and No Name
df['host_name'] = df['host_name'].fillna('No Host Name')
df['name'] = df['name'].fillna('No Name')

# Remove outliers using IQR for price
lower_q = df["price"].quantile(0.25)
lower_q

higher_q = df["price"].quantile(0.75)
higher_q

iqr = higher_q - lower_q
iqr

upper_boundary = higher_q + 1.5 * iqr
upper_boundary

lower_boundary = lower_q - 1.5 * iqr
lower_boundary

df_new = df[(df["price"] < upper_boundary) & (df["price"] > lower_boundary)]
```

## 📊 Visualizations & Dashboards

An interactive dashboard was created using **Tableau** to analyze:

- Top Hosts by Reviews  
- Average Price by Neighbourhood Group  
- Booking Volume Trends by Month  
- Room Type Distribution  
- Heatmaps of Review Activity  
- Geographical Mapping of Listings  

---

## 🔍 Key Insights

### 💰 Price Trends

- **Manhattan** has the highest average price (£145.90), followed by **Brooklyn (£105.70)**.  
- **Bronx** is the most affordable borough on average (£77.37).  

### 👥 Host Popularity

- **Yasu & Akiko** are the top hosts by total reviews, primarily located in **Hell’s Kitchen, Manhattan**.  

### 🛏️ Room Types

- **Entire homes/apartments** receive the most bookings across all boroughs.  
- **Bronx entire homes** get the highest monthly reviews on average (2.283).  

### 🗓️ Booking Seasonality

- **June is peak season**, with nearly 13,000 bookings.  
- Bookings dip in **early spring and fall months**.  

### 🌍 Neighbourhood Distribution

- Over **84% of listings** are concentrated in **Brooklyn and Manhattan**.  
- **Staten Island and Bronx** are underrepresented in the Airbnb ecosystem.  

---

## 📌 Summary Stats

- **Total Hosts:** 35,388  
- **Total Reviews:** 1,099,504  
- **Total Neighbourhoods:** 219  
- **Avg Monthly Reviews:** 1.378  

---

## ⚙️ Tools & Libraries Used

- **Python** (Pandas, NumPy)  
- **Tableau** (for interactive dashboard)  

---

## 📷 Dashboard Snapshot

> This dashboard was built using Tableau, showcasing layered insights about the NYC Airbnb landscape.

---

## 🚀 Future Work

- Incorporate sentiment analysis on host reviews.  
- Build a machine learning model to predict price or popularity.  
- Add temporal dynamics to track changes year over year.  

---

## 📬 Contact

Feel free to reach out or contribute to this project!

📧 your_email@example.com  
🔗 [Your LinkedIn or GitHub Profile](https://github.com/yourusername)
