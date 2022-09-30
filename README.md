## AIM
To perform Multivariate Exploratory Data Analysis on the given data set.
## EXPLANATION
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
## ALGORITHM
### STEP 1
Import the built libraries required to perform EDA and outlier removal.

### STEP 2
Read the given csv file

### STEP 3
Convert the file into a dataframe and get information of the data.

### STEP 4
Return the objects containing counts of unique values using (value_counts()).

### STEP 5
Plot the counts in the form of Histogram or Bar Graph.

### STEP 6
Use seaborn the bar graph comparison of data can be viewed.

### STEP 7
Find the pairwise correlation of all columns in the dataframe.corr()

### STEP 8
Save the final data set into the file

## CODE
```
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

df = pd.read_csv("/content/drive/MyDrive/Colab Notebooks/Semester 3/19AI403 _Intro to DS/Exp_3/SuperStore.csv")
df

df.head()

df.info()

df.describe()

df.tail()

df.shape

df.columns

df.isnull().sum()

df.duplicated()

df['Postal Code'] = df['Postal Code'].fillna(df['Postal Code'].mode()[0])

df.isnull().sum()

states=df.loc[:,["State","Sales"]]
states=states.groupby(by=["State"]).sum().sort_values(by="Sales")
plt.figure(figsize=(17,7))
sns.barplot(x=states.index,y="Sales",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("STATES")
plt.ylabel=("SALES")
plt.show()

states=df.loc[:,["Segment","Sales"]]
states=df.groupby(by=["Segment"]).sum()
sns.barplot(x=states.index,y="Sales",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("SEGMENT")
plt.ylabel=("SALES")
plt.show()

sns.barplot(df["Ship Mode"],df["Sales"],hue=df["Category"])

df.corr()
sns.heatmap(df.corr(),annot=True)

plt.figure(figsize=(10,7))
sns.scatterplot(df['Sub-Category'], df['Sales'], hue=df['Ship Mode'])
plt.xticks(rotation = 90)
```
## OUTPUT 
### Dataset
![image](https://user-images.githubusercontent.com/113017853/193247866-299e3da8-9455-4278-a83b-e50238d5ca8d.png)

### Dataset Head 
![image](https://github.com/SandeepaNagaraj/Ex-04-Multivariate-Analysis/blob/main/2.png)

### Dataset Info
![image](https://user-images.githubusercontent.com/113017853/193247966-c1c496eb-c66f-4c37-9e8b-17339731cb23.png)

### Dataset Describe

![image](https://user-images.githubusercontent.com/113017853/193248012-24b5ec56-6314-4a0c-b749-923ff6959a74.png)

### Dataset Tail

![image](https://user-images.githubusercontent.com/113017853/193248066-1fd73cc7-3c76-410f-9d83-c97ff5bee167.png)

### Dataset Shape

![image](https://user-images.githubusercontent.com/113017853/193248099-b38d7bb2-407a-4711-b5bd-12fc32dd0426.png)

### Dataset Columns

![image](https://user-images.githubusercontent.com/113017853/193248141-eff09835-54e5-41c1-823f-339469ddc1aa.png)

### Null Values - Pre Cleaning

![image](https://user-images.githubusercontent.com/113017853/193248171-9e4b6e55-a908-4152-ab48-b2576c0614a5.png)

### Dataset Duplicated

![image](https://user-images.githubusercontent.com/113017853/193248198-73608e2e-2249-4e55-85ea-b08f16f34f75.png)

### Null Values - Post Cleaning

![image](https://user-images.githubusercontent.com/113017853/193248231-b70ca50a-b5ab-44aa-9566-17bf63c0f75e.png)

### Multivariate Analysis - State

![image](https://user-images.githubusercontent.com/113017853/193248275-9611fd50-cbb7-4878-ad98-f1e199cf209d.png)

### Multivariate Analysis - Segment

![o](https://github.com/SandeepaNagaraj/Ex-04-Multivariate-Analysis/blob/main/3.png)

### Multivariate Analysis - Ship Mode & Category vs Sales
![image](https://user-images.githubusercontent.com/113017853/193248347-8f25a04a-effc-4ea8-be78-9b580164ee2c.png)

### Multivariate Analysis - Heat Map

![image](https://user-images.githubusercontent.com/113017853/193248595-a925af4a-750e-4270-8475-fe67e9798493.png)

### Multivariate Analysis - Sub-Category & Ship Mode vs Sales

![image](https://user-images.githubusercontent.com/113017853/193248656-c688b281-1e01-4335-8408-06a5534c2894.png)































##RESULT
```
The given dataset is read and Multivariate analysis is performed. The inferences are:

Most sales were from the California State
Most sales were from Consumer Segment
Most sales were from "New York City"
Most Sales were shipped on the Same Day and is most from Technology
Highest sale was from Machines Sub-category and is shipped in standard class
```
