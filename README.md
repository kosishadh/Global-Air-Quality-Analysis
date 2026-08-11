# 🌍 Air Quality Data Analysis

## 📌 Project Overview

This project analyzes an air-quality dataset containing **480 records** from **40 cities across 36 countries**. The analysis focuses on air pollution levels, major pollutants, city and country comparisons, data quality, and relationships between different pollutants.

The project uses **Python, Pandas, NumPy, and Matplotlib** for data loading, cleaning, statistical analysis, and visualization.

---

## 📊 Dataset Information

The dataset contains **480 rows and 13 columns**.

### Columns

| Column               | Description                                   |
| -------------------- | --------------------------------------------- |
| `Country`            | Country where the measurement was recorded    |
| `City`               | City where the measurement was recorded       |
| `Continent`          | Continent of the city                         |
| `Month`              | Month of the observation                      |
| `AQI`                | Air Quality Index                             |
| `AQI_Category`       | Category corresponding to the AQI             |
| `PM2.5`              | Fine particulate matter concentration         |
| `PM10`               | Particulate matter concentration              |
| `NO2`                | Nitrogen dioxide concentration                |
| `SO2`                | Sulfur dioxide concentration                  |
| `CO`                 | Carbon monoxide concentration                 |
| `O3`                 | Ozone concentration                           |
| `Dominant_Pollutant` | Main pollutant identified for the observation |

---

## 🛠️ Technologies Used

* **Python**
* **Pandas** – data manipulation and analysis
* **NumPy** – numerical calculations and correlation analysis
* **Matplotlib** – data visualization
* **CSV** – dataset format

---

## 🔍 Analysis Performed

### 1. Dataset Overview

The dataset was inspected to determine:

* Number of rows
* Number of columns
* Column names
* Data types
* Missing values
* Overall structure of the dataset

### 2. Dataset Size

The dataset contains:

* **480 rows**
* **13 columns**
* **40 unique cities**
* **36 unique countries**

Each city contains **12 monthly observations** for the year 2024.

### 3. Data Types

The dataset contains:

* String columns for country, city, continent, month, AQI category, and dominant pollutant
* Integer values for AQI
* Floating-point values for pollutant measurements

### 4. Missing Value Analysis

Missing values were checked for every column.

**Result:** There are **no missing values** in the dataset.

```text
Country               0
City                  0
Continent             0
Month                 0
AQI                   0
AQI_Category          0
PM2.5                 0
PM10                  0
NO2                   0
SO2                   0
CO                    0
O3                    0
Dominant_Pollutant    0
```

---

## 📈 PM2.5 Statistical Analysis

The project examined the minimum, maximum, mean, median, and standard deviation of PM2.5 concentrations.

| Statistic          | Value |
| ------------------ | ----: |
| Minimum            |   3.4 |
| Maximum            | 108.4 |
| Mean               | 31.14 |
| Median             | 25.65 |
| Standard Deviation | 21.16 |

### Lowest PM2.5

The lowest PM2.5 concentration in the dataset was:

* **Country:** Iceland
* **PM2.5:** 3.4

### Highest PM2.5

The highest PM2.5 concentration was:

* **Country:** Pakistan
* **PM2.5:** 108.4

---

## 🏙️ 10 Most Polluted Cities

Cities were ranked according to their average PM2.5 concentration.

| Rank | City        | Average PM2.5 |
| ---: | ----------- | ------------: |
|    1 | Lahore      |         79.06 |
|    2 | New Delhi   |         75.56 |
|    3 | Ulaanbaatar |         69.44 |
|    4 | Dhaka       |         69.27 |
|    5 | Kathmandu   |         62.28 |
|    6 | Cairo       |         56.08 |
|    7 | Hanoi       |         51.88 |
|    8 | Beijing     |         48.08 |
|    9 | Jakarta     |         46.05 |
|   10 | Riyadh      |         40.80 |

The analysis shows that **Lahore has the highest average PM2.5 concentration** among the cities in this dataset.

---

## 🌎 Countries With the Highest Average PM2.5

Countries were also ranked according to their average PM2.5 concentration.

| Rank | Country      | Average PM2.5 |
| ---: | ------------ | ------------: |
|    1 | Pakistan     |         79.06 |
|    2 | Mongolia     |         69.44 |
|    3 | Bangladesh   |         69.27 |
|    4 | Nepal        |         62.28 |
|    5 | India        |         58.13 |
|    6 | Egypt        |         56.08 |
|    7 | Vietnam      |         51.88 |
|    8 | Indonesia    |         46.05 |
|    9 | China        |         43.11 |
|   10 | Saudi Arabia |         40.80 |

**Pakistan** has the highest average PM2.5 concentration among the countries represented in the dataset.

---

## 📉 PM2.5 vs PM10

A scatter plot was created to investigate the relationship between PM2.5 and PM10.

The calculated correlation coefficient is:

**0.9865**

This indicates a **very strong positive correlation** between PM2.5 and PM10 in this dataset. In general, observations with higher PM2.5 concentrations also tend to have higher PM10 concentrations.

> **Note:** The calculated correlation is approximately **0.986**, not 0.82 as stated in the original analysis notes.

---

## 📉 PM2.5 vs NO2

A second scatter plot was created to investigate the relationship between PM2.5 and NO2.

The calculated correlation coefficient is:

**0.7505**

This indicates a **strong positive relationship** between PM2.5 and NO2. Locations and months with higher PM2.5 levels generally tend to have higher NO2 concentrations as well.

---

## 📊 Visualizations

The project includes visualizations such as:

* Top 10 cities by average PM2.5
* Average PM2.5 by country
* PM2.5 vs PM10 scatter plot
* PM2.5 vs NO2 scatter plot

These visualizations help identify pollution patterns and relationships between pollutants.

---

## 📁 Project Structure

A suggested project structure is:

```text
air-quality-analysis/
│
├── data.csv
├── main.ipynb
├── README.md
```

---

## 🚀 How to Run the Project

### 1. Clone the repository

```bash
git clone <repository-url>
cd air-quality-analysis
```

### 2. Install the required libraries

```bash
pip install pandas numpy matplotlib
```

### 3. Make sure the dataset is available

Place `data.csv` in the project directory.

### 4. Run the Python script

```bash
python analysis.py
```

---

## 💻 Example Code

### Load the dataset

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

df = pd.read_csv("data.csv")
print(df.to_string())
```

### Find the 10 most polluted cities

```python
avg_pm2 = df.groupby("City")["PM2.5"].mean()

top_10_city = (
    avg_pm2
    .sort_values(ascending=False)
    .head(10)
)

print(top_10_city)

top_10_city.plot(kind="barh")
plt.xlabel("Average PM2.5")
plt.title("10 Most Polluted Cities")
plt.show()
```

### Calculate correlation

```python
correlation = np.corrcoef(
    df["PM2.5"],
    df["PM10"]
)[0, 1]

print("Correlation:", correlation)
```

---

## 🧹 Data Cleaning

The dataset was checked for missing values using:

```python
df.isnull().sum()
```

All columns returned **0 missing values**, so no missing-value imputation or row removal was required.

Basic checks were also performed for:

* Dataset dimensions
* Column names
* Data types
* Number of unique cities
* Number of unique countries
* Minimum and maximum pollutant values

---

## 🔑 Key Findings

1. The dataset contains **480 observations** covering **40 cities** and **36 countries**.
2. Each city has **12 monthly observations** for 2024.
3. There are **no missing values** in the dataset.
4. The mean PM2.5 concentration is **31.14**.
5. **Iceland** has the lowest recorded PM2.5 value at **3.4**.
6. **Pakistan** has the highest recorded PM2.5 value at **108.4**.
7. **Lahore** has the highest average PM2.5 among the cities analyzed.
8. **Pakistan** has the highest average PM2.5 among the countries analyzed.
9. PM2.5 and PM10 have an extremely strong positive correlation of approximately **0.986**.
10. PM2.5 and NO2 have a strong positive correlation of approximately **0.751**.

---

## 🎯 Project Objectives

The main objectives of this project are to:

* Explore air-quality data using Python
* Understand the structure and quality of the dataset
* Identify cities and countries with high pollution levels
* Calculate descriptive statistics
* Analyze relationships between pollutants
* Create meaningful visualizations
* Practice data analysis using Pandas, NumPy, and Matplotlib

---

## 📌 Conclusion

This project demonstrates how Python can be used to explore and analyze real-world air-quality data. The analysis identifies major differences in PM2.5 pollution across cities and countries and shows strong relationships between PM2.5, PM10, and NO2.

The results provide a useful overview of pollution patterns in the selected locations and demonstrate the importance of exploratory data analysis and visualization when working with environmental datasets.

---

## 👤 Author

Kosish Adhikari

Air Quality Data Analysis Project
