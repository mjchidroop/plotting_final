# Exp 6 Analysis and Visualization of COVID-19 Dataset using Python

**Date:**

## AIM:

To analyse a large real-world COVID-19 dataset using Python and visualize key trends and relationships using multiple types of graphs for meaningful insights.

## DESIGN STEPS:

### Step 1:

Clone the repository from GitHub.

### Step 2:

Create a Python project in the preferred IDE (VS Code/PyCharm/Jupyter Notebook).

### Step 3:

Create the Python program for analysing and visualizing the COVID-19 dataset using **Pandas** and **Matplotlib** libraries.

### Step 4:

Load the **`covid_cases.csv`** dataset using Pandas and explore the dataset by displaying its shape and column names.

### Step 5:

Check and handle missing values in the dataset, if any.

### Step 6:

Perform basic data exploration by finding the total number of records and generating the statistical summary using the `describe()` function.

### Step 7:

Use Matplotlib to create different visualizations:

* **Line Graph:** Trend of confirmed cases over time globally.
* **Bar Chart:** Top 10 countries by total confirmed cases.
* **Pie Chart:** Case distribution of the top 5 affected countries.
* **Scatter Plot:** Relationship between confirmed cases and deaths.
* **Histogram:** Distribution of active cases.

### Step 8:

Add appropriate titles, axis labels, legends, and other necessary labels to the graphs.

### Step 9:

Execute the program and analyze the generated visualizations to identify meaningful trends and relationships in the COVID-19 dataset.

## PROGRAM:
```python
import pandas as pd
import matplotlib.pyplot as plt

url = "https://raw.githubusercontent.com/mjchidroop/plotting_final/main/covid_case.csv"
data = pd.read_csv(url)

print("Dataset loaded successfully.")

print("First 5 rows:")
print(data.head())

print("\nDataset Shape:")
print(data.shape)

print("\nColumn Names:")
print(data.columns)

print("\nMissing Values:")
print(data.isnull().sum())

data = data.dropna()
data['Date'] = pd.to_datetime(data['Date'])

print("\nTotal Records:", len(data))

print("\nStatistical Summary:")
print(data.describe())

global_cases = data.groupby('Date')['Confirmed'].sum()

plt.figure(figsize=(10, 5))
plt.plot(global_cases.index, global_cases.values, color='tab:blue')
plt.title("Global Confirmed COVID-19 Cases Over Time")
plt.xlabel("Date")
plt.ylabel("Confirmed Cases")
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

top10 = data.groupby('Country')['Confirmed'].sum().sort_values(ascending=False).head(10)

plt.figure(figsize=(10, 5))
top10.plot(kind='bar', color='tab:orange')
plt.title("Top 10 Countries by Confirmed Cases")
plt.xlabel("Country")
plt.ylabel("Confirmed Cases")
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

top5 = data.groupby('Country')['Confirmed'].sum().sort_values(ascending=False).head(5)

plt.figure(figsize=(8, 8))
plt.pie(top5, labels=top5.index, autopct='%1.1f%%', startangle=140)
plt.title("Top 5 Countries Case Distribution")
plt.axis('equal')
plt.show()

plt.figure(figsize=(8, 5))
plt.scatter(data['Confirmed'], data['Deaths'], alpha=0.5, color='tab:red')
plt.title("Confirmed Cases vs Deaths")
plt.xlabel("Confirmed Cases")
plt.ylabel("Deaths")
plt.tight_layout()
plt.show()

plt.figure(figsize=(8, 5))
plt.hist(data['Active'], bins=20, color='tab:green', edgecolor='black')
plt.title("Distribution of Active Cases")
plt.xlabel("Active Cases")
plt.ylabel("Frequency")
plt.tight_layout()
plt.show()

print("Total records analysed:", len(data))
print("Number of countries:", data['Country'].nunique())
print("Date range:", data['Date'].min().date(), "to", data['Date'].max().date())
print("Top 5 countries by confirmed cases:")
print(top5)
```

## OUTPUT:

*(Paste the execution output showing the dataset information, statistical summary, and generated Line Graph, Bar Chart, Pie Chart, Scatter Plot, and Histogram.)*



## RESULT:

The COVID-19 dataset was successfully analysed using Python. The dataset was explored using Pandas, and meaningful trends and relationships were visualized using different types of graphs such as line graph, bar chart, pie chart, scatter plot, and histogram using Matplotlib.
