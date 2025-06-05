# Web-Traffic-Intelligence-by-Python
Welcome to this in-depth, hands-on project where I analyze real website data using Python. In this project, I explore user engagement trends and assess the performance of different acquisition channels to derive actionable insights for optimization.



# 📊 Project Title: Web Traffic Intelligence: User Behavior & Channel Performance Dashboard

Welcome to this in-depth, hands-on project where I analyze real website data using Python. In this project, I explore user engagement trends and assess the performance of different acquisition channels to derive actionable insights for optimization.


##### Completed by: Dr. Maisha Tabassum | Data Analyst
##### Date: 03 June 2025



 ## 🎯 Tools Used: 
 **Numpy, Pandas, Matplotlib, Seaborn, Jupyter Notebook** 



## 📝 Project Description:
This project explores user behavior and marketing channel performance using website traffic data. Leveraging Python (Pandas, Matplotlib, Seaborn) in Jupyter Notebook, I performed exploratory data analysis (EDA) to uncover actionable insights about user sessions, engagement patterns, and traffic sources over time.

**Key business questions addressed include:**

- Identifying top-performing channels by traffic and engagement

- Comparing engagement rates across traffic sources

- Detecting peak traffic hours and session trends

- Analyzing correlations between engagement rate and sessions

These insights can guide digital marketing strategy, content planning, and channel optimization efforts. This project demonstrates my ability to turn raw analytics data into strategic recommendations—essential for data-driven decision-making in digital businesses.


# In this project, you'll learn:

✅ How to clean and preprocess website traffic data

✅ Perform detailed exploratory data analysis (EDA)

✅ Uncover traffic trends, bounce rates, and engagement behavior

✅ Create compelling visualizations with Pandas, Matplotlib, and Seaborn

✅ Derive actionable insights to improve website performance and decision-making


## 🧠 Business Questions to Solve

- **Traffic Trends Over Time**: What patterns or trends can you observe in website sessions and users over time?
- **Top Performing Marketing Channels**: Which marketing channel brought the highest number of users to the website, and how can we use this insight to improve traffic from other sources?
- **Channel Effectiveness – Engagement Time**: Which channel has the highest average engagement time, and what does that tell us about user behavior and content effectiveness?
- **Engagement Rate by Channel**: How does engagement rate vary across different traffic channels?
- **Engaged vs. Non-Engaged Sessions**: Which channels are driving more engaged sessions compared to non-engaged ones, and what strategies can improve engagement in underperforming channels?
- **Traffic by Hour of Day**: At what hours of the day does each channel drive the most traffic?
- **Correlation Between Sessions and Engagement Rate**: Is there any correlation between high traffic (sessions) and high engagement rate over time?





## 🎯 Business Impact:
The insights uncovered can guide digital marketing strategy, improve content planning, and optimize traffic channels to enhance user retention and conversion.


# 🚀 Starting the Analysis  (Data Loading, Data Cleaning & Preparation  and  Analysis to answer the Businesss Questions)



```python
# Importing Required Libraries

import numpy as np                 # For numerical operations
import pandas as pd                # For data manipulation and analysis 
import matplotlib.pyplot as plt    # For basic plotting
import seaborn as sns              # For statistical data visualization

# To ensure plots show directly below your code cells
%matplotlib inline   

# Using "whitegrid" style for enhanced readability and polished aesthetics in plots
sns.set(style="whitegrid")

```


```python
# loading the dataset

df = pd.read_csv("website_data.csv", encoding="utf-8")
```


```python
'''📊 Data Overview  

Now, let's take a quick look at the dataset'''

df.head()
```


```python
# Rename all columns by assigning a new list of column names

df.columns =['channel group', 'Hour',	'Users',	'Sessions', 'Engaged sessions', 'Avg engagement time per session',
             'Engaged sessions per user',	'Events per session',	'Engagement rate',	'Event count', 'Date']

df.columns = df.columns.str.lower().str.replace(' ', '_')
```


```python
df.head()
```


```python
# 🔍  Checking dataset structure, column data types, non-null values, and memory usage
df.info()
```


```python
# Convert date column from object to datetime
df['date'] = pd.to_datetime(df['date'], format='%d/%m/%Y')
```


```python
df.info()
```


```python
df.head()
```


```python
df.describe()
```


```python
# 🔍 Check for missing values
missing_values = df.isnull().sum()

# Display columns with missing values
print("Missing values per column:")
print(missing_values)
```

### This dataset is **complete** with no missing values in any column.



```python
# 🔍 Check for duplicate rows
duplicate_rows = df.duplicated().sum()

print(f"Total duplicate rows: {duplicate_rows}")

# Display duplicate rows (if any)
if duplicate_rows > 0:
    print(df[df.duplicated()])
```

### This dataset is clean, with no missing values and no duplicate rows—great for ensuring accurate analysis.



```python
# 🕒 Merge 'date' and 'hour' columns to create a full timestamp
df['date_hour'] = pd.to_datetime(df['date']) + pd.to_timedelta(df['hour'], unit='h')

# Display the updated dataframe
print(df[['date', 'hour', 'date_hour']].head())
```


```python
df.info()
```


```python
df.head(3)
```


```python
# Generate summary statistics
df.describe()
```


```python
# Summary of numerical columns
df.describe(include=[np.number])

```


```python

# 📊 Step 3: Summary of categorical columns
df.describe(include=[object])
```

## 📈Traffic Trends Over Time
### 🤔Business Questions :  What patterns or trends can you observe in website sessions and users over time❓  


```python
df.columns
```


```python
# Group data by date-hour and sum sessions/users
df_grouped = df.groupby('date_hour')[['sessions', 'users']].sum()

# Plot the trend
plt.figure(figsize=(10, 5))
df_grouped.plot()
plt.title("Sessions & Users Over Time")
plt.xlabel("Datetime")
plt.ylabel("Count")
plt.legend(["Sessions", "Users"])
plt.xticks(rotation=45)
plt.grid(True)
plt.show()
```


```python

```
