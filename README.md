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

## Data Pre-Processing:
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

## Which Segment has Highest sales?
```
sns.lineplot(x="Segment",y="Sales",data=df,marker='o')
plt.title("Segment vs Sales")
plt.xticks(rotation = 90)
plt.show()

sns.barplot(x="Segment",y="Sales",data=df)
plt.xticks(rotation = 90)
plt.show()
```

## Which City has Highest profit?
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

## Which ship mode is profitable?
```
sns.barplot(x="Ship Mode",y="Profit",data=df)
plt.show()
```
```
sns.lineplot(x="Ship Mode",y="Profit",data=df)
plt.show()
```

## Sales of the product based on region.
```
states=df.loc[:,["Region","Sales"]]
states=states.groupby(by=["Region"]).sum().sort_values(by="Sales")
sns.barplot(x=states.index,y="Sales",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("Region")
plt.ylabel=("Sales")
plt.show()

df.groupby(['Region']).sum().plot(kind='pie', y='Sales',figsize=(6,9),pctdistance=1.7,labeldistance=1.2)
```

## Find the relation between sales and profit.
```
df["Sales"].corr(df["Profit"])
df_corr = df.copy()
df_corr = df_corr[["Sales","Profit"]]
df_corr.corr()
sns.pairplot(df_corr, kind="scatter")
plt.show()
```

## Segment:
```
grouped_data = df.groupby('Segment')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
ax.legend()
plt.show()
```

## City:
```
grouped_data = df.groupby('City')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('City')
ax.set_ylabel('Value')
ax.legend()
plt.show()
```

## States:
```
grouped_data = df.groupby('State')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('State')
ax.set_ylabel('Value')
ax.legend()
plt.show()
```

## Segment and Ship Mode:
```
grouped_data = df.groupby(['Segment', 'Ship Mode'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index='Segment', columns='Ship Mode', values=['Sales', 'Profit'])
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
pivot_data.plot(kind='bar', ax=ax)
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
plt.legend(title='Ship Mode')
plt.show()
```

## Segment, Ship mode and Region:
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

## OUTPUT
## Data Pre-Processing:
![1](https://github.com/Adhithya4116/Ex-08-Data-Visualization-/assets/118707079/71271f66-56d1-448f-8e99-49f4bc80c4be)
![2](https://github.com/Adhithya4116/Ex-08-Data-Visualization-/assets/118707079/ddbd46cd-6e18-4283-85f4-abdd34c62677)
![3](https://github.com/Adhithya4116/Ex-08-Data-Visualization-/assets/118707079/6578f0c8-0b04-46f0-b32b-9dd6380cb25d)

![4](https://github.com/Adhithya4116/Ex-08-Data-Visualization-/assets/118707079/8f717ada-740b-45cf-bcdd-68e735b0e053)

## Which Segment has Highest sales?
![5](https://github.com/Adhithya4116/Ex-08-Data-Visualization-/assets/118707079/ac12204c-1ce5-4a24-816d-94dad5be0871)
![6](https://github.com/Adhithya4116/Ex-08-Data-Visualization-/assets/118707079/acc771f3-849b-4295-903e-fdcb17a4d48e)

## Which City has Highest profit?
![7](https://github.com/Adhithya4116/Ex-08-Data-Visualization-/assets/118707079/6d51cc8f-fd91-474b-8d77-6305cab6a751)

## Which ship mode is profitable?
![8](https://github.com/Adhithya4116/Ex-08-Data-Visualization-/assets/118707079/6bef5ba0-b5fa-431b-89d2-8fffbd9bf1c0)

## Sales of the product based on region.
![9](https://github.com/Adhithya4116/Ex-08-Data-Visualization-/assets/118707079/d2f6fe60-b1e5-4669-a945-0fa9a006ddef)

![10](https://github.com/Adhithya4116/Ex-08-Data-Visualization-/assets/118707079/1dd501e6-70fb-4b81-a9e5-704163e6e47a)

## Find the relation between sales and profit:
![11](https://github.com/Adhithya4116/Ex-08-Data-Visualization-/assets/118707079/e4ded10e-1fa7-40b7-b60f-03953456d29d)

## Find the relation between sales and profit based on the following category.
## segment:
![12](https://github.com/Adhithya4116/Ex-08-Data-Visualization-/assets/118707079/b1b54921-5434-49b5-b63d-6ddde90940ec)

## City:
![13](https://github.com/Adhithya4116/Ex-08-Data-Visualization-/assets/118707079/353dda62-d868-4f5b-a8e0-1eefaf6e9f5f)

## States:
![14](https://github.com/Adhithya4116/Ex-08-Data-Visualization-/assets/118707079/7beb8b8b-e45a-4e43-afc7-1ae5770bd776)

## Segment and Ship Mode:
![15](https://github.com/Adhithya4116/Ex-08-Data-Visualization-/assets/118707079/d22faa23-31ee-43e6-8db6-6ebe29f548db)

## Segment, Ship mode and Region:
![16](https://github.com/Adhithya4116/Ex-08-Data-Visualization-/assets/118707079/f5675408-6132-4666-80b2-13b794ae2dfe)

## Result:

Thus, Data Visualization is performed on the given dataset and save the data to a file.
















