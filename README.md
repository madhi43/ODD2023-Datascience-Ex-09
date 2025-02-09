# Ex-09-Data-Visualization-

## AIM
To Perform Data Visualization on a complex dataset and save the data to a file. 

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


# CODE AND OUTPUT

```
import seaborn as sns
import pandas as pd
import matplotlib.pyplot as plt
df=sns.load_dataset("tips")
print (df)
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-09/assets/103943383/15f31b41-5455-419f-98d4-0e0bc9a13826)


```
df.isnull().sum()
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-09/assets/103943383/c35a5889-bb0a-439b-a1e0-3088ffd4c201)


### Finding Outliers
```
plt.figure(figsize=(5,5))
plt.title("Data with outliers")
df.boxplot()
plt.show()
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-09/assets/103943383/5b6bde70-bddd-48ce-b50f-2e74b645825f)


### Removing Outliers
```
plt.figure(figsize=(5,5))
cols=['total_bill','tip','size']
Q1=df[cols].quantile(0.25)
Q3=df[cols].quantile(0.75)
IQR=Q3-Q1
df=df[-((df[cols]<(Q1 - 1.5 * IQR))[df[cols]>(Q3 + 1.5 + IQR)]).any(axis=1)]
df.boxplot()
plt.show()
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-09/assets/103943383/2894ce29-765f-48bc-82f2-0116c4a17a27)


### 1.Which day of the week has the highest total bill amount?
```
sns.barplot(x=df['day'],y=df['total_bill'],hue=df['day'])
plt.legend(loc="center")
plt.title("Highest Total Bill Amount of day of the week")
plt.show()
```

![image](https://github.com/madhi43/ODD2023-Datascience-Ex-09/assets/103943383/ec97f586-6a1b-48ad-b91e-97e56f4e631a)



### 2.What is the Average Tip amount given by smokers and non-smokers?
```
sns.boxplot(x=df['smoker'],y=df['tip'],hue=df['smoker'])
plt.title("Averaga tip amount given by somkers and non-smokers")
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-09/assets/103943383/49278f9b-e8d2-4497-9089-bacae8dd6128)


### 3. How does the tip percentage vary based on the size of dining party?
```
df["tip_percent"]=df["tip"]/df["total_bill"]
sns.scatterplot(x=df['size'],y=df['tip_percent'],data=df)
plt.title("Tip percentage by dining party size")
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-09/assets/103943383/c99e4573-8e02-468e-988d-79da4be609d1)




### 4.Which gender tends to leave higher tips?
```
sns.boxplot(x=df['sex'],y=df['tip'],hue=df['sex'])
plt.title("Tips based on gender")
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-09/assets/103943383/f7df3354-18a6-4210-aceb-e8d43934116e)

### 5.Is there any relationship between the bill amount and the day of the week?
```
sns.scatterplot(x=df['day'],y=df['total_bill'],hue=df['day'])
plt.legend(loc="best")
plt.title("Total bill amount by day of the week")
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-09/assets/103943383/b8f20359-1a69-4b62-82a1-a4717594a59c)


### 6. how does the distribution of total bill amounts vary across different time periods (lunch vs dinner)

```
sns.histplot(data=df,x="total_bill",hue="time",element="step",stat="density")
plt.title("Distribution of total bill amounts by time of day")
plt.show()
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-09/assets/103943383/b7c9924c-07fd-47a6-af32-0a3af64fee06)



### Why dining party size group tends to have the highest average total bill amount?
```
sns.barplot(x=df['size'],y=df['total_bill'],hue=df['size'])
plt.title("Average total bill amount by dining party size")
plt.show()
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-09/assets/103943383/1e1b7402-9771-4e04-9419-a863692b22e8)


### What is the distribution of tip amount for each day of the week?
```
sns.boxplot(x="day",y="tip",data=df)
plt.title("Tip amount by day of week")
plt.show()
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-09/assets/103943383/b58de83c-1d7a-4a51-ae49-0425f607152c)


### How does the tip amount vary based on the type of service (lunch vs dinner)
```

sns.violinplot(x="time",y="tip",data=df)
plt.title("Tip amount by time of day")
plt.show()
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-09/assets/103943383/9a8c5a51-737b-48dc-ad3e-a1b91e151a1d)

### Is there any correaltion between the total bill amount?
```
sns.scatterplot(x="total_bill",y="tip",data=df)
plt.title("Correlation between tip amount and totalbill amount")
plt.show()
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-09/assets/103943383/a78f2b0a-0710-490a-a5da-2ff765b94ee6)


# RESULT

Thus the Data Visualization on a complex dataset is performed and saved the data to a file


