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

```
df.isnull().sum()
```

```
plt.figure(figsize=(5,5))
plt.title("Data with outliers")
df.boxplot()
plt.show()
```

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

```
sns.barplot(x=df['day'],y=df['total_bill'],hue=df['day'])
plt.legend(loc="center")
plt.title("Highest Total Bill Amount of day of the week")
plt.show()
```

```
sns.boxplot(x=df['smoker'],y=df['tip'],hue=df['smoker'])
plt.title("Averaga tip amount given by somkers and non-smokers")
```

```
df["tip_percent"]=df["tip"]/df["total_bill"]
sns.scatterplot(x=df['size'],y=df['tip_percent'],data=df)
plt.title("Tip percentage by dining party size")
```

```
sns.boxplot(x=df['sex'],y=df['tip'],hue=df['sex'])
plt.title("Tips based on gender")
```

```
sns.scatterplot(x=df['day'],y=df['total_bill'],hue=df['day'])
plt.legend(loc="best")
plt.title("Total bill amount by day of the week")
```

```
sns.histplot(data=df,x="total_bill",hue="time",element="step",stat="density")
plt.title("Distribution of total bill amounts by time of day")
plt.show()
```

```
sns.barplot(x=df['size'],y=df['total_bill'],hue=df['size'])
plt.title("Average total bill amount by dining party size")
plt.show()
```

```
sns.boxplot(x="day",y="tip",data=df)
plt.title("Tip amount by day of week")
plt.show()
```

```
sns.violinplot(x="time",y="tip",data=df)
plt.title("Tip amount by time of day")
plt.show()
```

```
sns.scatterplot(x="total_bill",y="tip",data=df)
plt.title("Correlation between tip amount and totalbill amount")
plt.show()
```

# RESULT
