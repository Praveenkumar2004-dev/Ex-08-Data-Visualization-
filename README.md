# Ex-07-Data-Visualization-

## AIM
To Perform Data Visualization on the given dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.

# CODE
Data Pre-Processing
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df=pd.read_csv("/content/Superstore.csv",encoding="ISO-8859-1")
df
df.isnull.sum()
df.info()
df.describe()
```

Which Segment has Highest sales?
```
sns.lineplot(x="Segment",y="Sales",data=df,marker='o')
plt.title("Segment vs Sales")
plt.xticks(rotation = 90)
plt.show()

sns.barplot(x="Segment",y="Sales",data=df)
plt.xticks(rotation = 90)
plt.show()
```

Which City has Highest profit?
```
df.shape
df1 = df[(df.Profit >= 60)]
df1.shape

plt.figure(figsize=(30,8))
states=df1.loc[:,["City","Profit"]]
states=states.groupby(by=["City"]).sum().sort_values(by="Profit")
sns.barplot(x=states.index,y="Profit",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("City")
plt.ylabel=("Profit")
plt.show()
```

Which ship mode is profitable?
```
sns.barplot(x="Ship Mode",y="Profit",data=df)
plt.show()
sns.lineplot(x="Ship Mode",y="Profit",data=df)
plt.show()


Sales of the product based on region.
```

Find the relation between sales and profit.
```
df["Sales"].corr(df["Profit"])
df_corr = df.copy()
df_corr = df_corr[["Sales","Profit"]]
df_corr.corr()
sns.pairplot(df_corr, kind="scatter")
plt.show()
```

Segment
```
grouped_data = df.groupby('Segment')[['Sales', 'Profit']].mean()
#Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
ax.legend()
plt.show()
```

City
```
grouped_data = df.groupby('City')[['Sales', 'Profit']].mean()
#Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('City')
ax.set_ylabel('Value')
ax.legend()
plt.show()
```

States
```
grouped_data = df.groupby('State')[['Sales', 'Profit']].mean()
#Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('State')
ax.set_ylabel('Value')
ax.legend()
plt.show()
```

Segment and Ship Mode
```
grouped_data = df.groupby(['Segment', 'Ship Mode'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index='Segment', columns='Ship Mode', values=['Sales', 'Profit'])
#Create a bar chart of the grouped data
fig, ax = plt.subplots()
pivot_data.plot(kind='bar', ax=ax)
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
plt.legend(title='Ship Mode')
plt.show()
```

Segment, Ship mode and Region
```
grouped_data = df.groupby(['Segment', 'Ship Mode','Region'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index=['Segment', 'Ship Mode'], columns='Region', values=['Sales', 'Profit'])
sns.set_style("whitegrid")
sns.set_palette("Set1")
pivot_data.plot(kind='bar', stacked=True, figsize=(10, 5))
plt.xlabel('Segment - Ship Mode')
plt.ylabel('Value')
plt.legend(title='Region')
plt.show()
```

# OUPUT
Data Pre-Processing

![DS1](https://github.com/Praveenkumar2004-dev/Ex-08-Data-Visualization-/assets/119559827/4da00e33-9985-4e4e-9edc-fdb85c656c69)
![DS2](https://github.com/Praveenkumar2004-dev/Ex-08-Data-Visualization-/assets/119559827/7fb1b639-5fe5-44e1-b7e7-f8dcc942c865)
![DS3](https://github.com/Praveenkumar2004-dev/Ex-08-Data-Visualization-/assets/119559827/bb73fbda-0e5c-4669-a246-caf16a20af2b)
![DS4](https://github.com/Praveenkumar2004-dev/Ex-08-Data-Visualization-/assets/119559827/43af5e19-6f15-40d5-a3d2-c4650a15b980)

Which Segment has Highest sales?

![DS5](https://github.com/Praveenkumar2004-dev/Ex-08-Data-Visualization-/assets/119559827/67b06ded-a881-4f35-85ab-bd9146d5b334)
![DS6](https://github.com/Praveenkumar2004-dev/Ex-08-Data-Visualization-/assets/119559827/3382406d-d9c6-480a-9288-3af5211b14be)

Which City has Highest profit?

![DS7](https://github.com/Praveenkumar2004-dev/Ex-08-Data-Visualization-/assets/119559827/40c0b9b2-8083-472f-b64e-f5f94984350a)

Which ship mode is profitable?

![DS8](https://github.com/Praveenkumar2004-dev/Ex-08-Data-Visualization-/assets/119559827/7e8a1d72-5a4d-45ff-96ee-7a8fcb33b41f)

Sales of the product based on region?

![DS9](https://github.com/Praveenkumar2004-dev/Ex-08-Data-Visualization-/assets/119559827/dc9cc555-4b6e-43de-b5e1-25b066cc1c55)

Find the relation between sales and profit

![DS10](https://github.com/Praveenkumar2004-dev/Ex-08-Data-Visualization-/assets/119559827/6b5273b7-7a53-4ebf-9ed9-ceef45739e83)

Find the relation between sales and profit based on the following category.

Segment

![DS11](https://github.com/Praveenkumar2004-dev/Ex-08-Data-Visualization-/assets/119559827/3e36299c-7997-467d-ad35-5d660d32c09c)

City

![DS12](https://github.com/Praveenkumar2004-dev/Ex-08-Data-Visualization-/assets/119559827/799bfd3e-e0be-4903-813f-f5d51e91bc9e)

States

![DS13](https://github.com/Praveenkumar2004-dev/Ex-08-Data-Visualization-/assets/119559827/77f62db0-24dd-405d-af3b-8764ab4ed61e)

Segment and Ship Mode

![DS14](https://github.com/Praveenkumar2004-dev/Ex-08-Data-Visualization-/assets/119559827/f895875f-e663-4943-9ccc-4f1686017067)

Segment, Ship mode and Region

![DS15](https://github.com/Praveenkumar2004-dev/Ex-08-Data-Visualization-/assets/119559827/746b8cf8-e5ea-45d8-b17d-b65248f6f6df)

# Result
Thus, Data Visualization is performed on the given dataset and save the data to a file.

