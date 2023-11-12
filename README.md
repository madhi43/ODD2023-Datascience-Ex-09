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
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-09/assets/103943383/8fb92778-e70f-4cda-a1ae-d315bcc01c72)


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
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-09/assets/103943383/3aeeff96-e01f-4b51-99ec-6d6907ffe7e8)


### 1.Which day of the week has the highest total bill amount?
```
sns.barplot(x=df['day'],y=df['total_bill'],hue=df['day'])
plt.legend(loc="center")
plt.title("Highest Total Bill Amount of day of the week")
plt.show()
```

![image](https://github.com/madhi43/ODD2023-Datascience-Ex-09/assets/103943383/a7212447-f300-49da-8d18-82d0fa2b93cf)



### 2.What is the Average Tip amount given by smokers and non-smokers?
```
sns.boxplot(x=df['smoker'],y=df['tip'],hue=df['smoker'])
plt.title("Averaga tip amount given by somkers and non-smokers")
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-09/assets/103943383/e2dd0152-8a19-4713-afae-e5b6a0190b45)


### How does the tip percentage vary based on the size of dining party?
```
df["tip_percent"]=df["tip"]/df["total_bill"]
sns.scatterplot(x=df['size'],y=df['tip_percent'],data=df)
plt.title("Tip percentage by dining party size")
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-09/assets/103943383/9d698209-6f64-4b4b-b2de-a8eecb5632e5)




### 4.Which gender tends to leave higher tips?
```
sns.boxplot(x=df['sex'],y=df['tip'],hue=df['sex'])
plt.title("Tips based on gender")
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-09/assets/103943383/cd8af189-1b83-4b6c-879a-641af11854ea)

### 5.Is there any relationship between the bill amount and the day of the week?
```
sns.scatterplot(x=df['day'],y=df['total_bill'],hue=df['day'])
plt.legend(loc="best")
plt.title("Total bill amount by day of the week")
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-09/assets/103943383/6d6587ca-0820-4ebe-be58-cee7141c8cd4)


### 6. how does the distribution of total bill amounts vary across different time periods (lunch vs dinner)

```
sns.histplot(data=df,x="total_bill",hue="time",element="step",stat="density")
plt.title("Distribution of total bill amounts by time of day")
plt.show()
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-09/assets/103943383/8b35a9bc-a258-4e40-bd90-a7e051beec2f)


### Why dining party size group tends to have the highest average total bill amount?
```
sns.barplot(x=df['size'],y=df['total_bill'],hue=df['size'])
plt.title("Average total bill amount by dining party size")
plt.show()
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-09/assets/103943383/832900c4-dab1-49ef-bdf9-fb5f502c0d2a)


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


