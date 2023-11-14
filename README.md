# Ex-09-Data-Visualization - 2

## AIM:
To Perform Data  Visualization on a complex dataset and save the data to a file. 

# Explanation:
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM:
### STEP 1:
Read the given Data
### STEP 2:
Clean the Data Set using Data Cleaning Process
### STEP 3:
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4:
Apply data visualization techniques to identify the patterns of the data.


# CODE AND OUTPUT:
```
Name: Karthick P

Reg no: 212222100021
```
```
import seaborn as sns
import pandas as pd
import matplotlib.pyplot as plt
df=sns.load_dataset("tips")
print(df)
```
<img width="230" alt="278807457-1b3fbb99-9a74-4b53-8ce2-497d3d66105e" src="https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-09/assets/119559695/58477b4c-beff-4909-84dc-2b66716acf76">



```
df.isnull().sum()
```

<img width="250" alt="278807508-6bde75cc-013e-40a1-a33f-c2d87d475f84" src="https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-09/assets/119559695/93202b5d-e9eb-4e5f-8710-07e9b0369bff">

```

plt.figure(figsize=(5,5))
plt.title("data with outliners")
df.boxplot()
plt.show()
```
<img width="218" alt="278807545-eee15327-56f0-41cd-8ac6-b521415b95fb" src="https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-09/assets/119559695/d3a35b9f-5ee7-4059-a81d-8346e4c9d699">



```
plt.figure(figsize=(5,5)) 
cols=["size","tip","total_bill"]
q1=df[cols].quantile(0.25)
q3=df[cols].quantile(0.75)
iqr=q3-q1
df=df[~((df[cols]<(q1-1.5*iqr))|(df[cols]>(q3+1.5*iqr))).any(axis=1)]
plt.title("dataset after removing outliners")
df.boxplot()
plt.show()
```
<img width="218" alt="278807616-7927a9a1-2722-43d4-8917-ea4d9e6f0450" src="https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-09/assets/119559695/3fdee909-78bc-4371-aac5-d9d7f1b9762f">


```
sns.barplot(x=df["day"],y=df["total_bill"],hue=df["day"])
plt.legend(loc="center")
plt.title("highest total bill amount by day of the week")
```
<img width="283" alt="278807645-ea4ba09f-7399-4a56-8f27-a2185acb7016" src="https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-09/assets/119559695/66b4dcdb-93b2-4184-a81b-27507f9d2888">



```
sns.boxplot(x=df["smoker"],y=df["tip"],hue=df["smoker"])
plt.title("average tip amount given by smokers and non-smokers")
```
<img width="280" alt="278807697-3ef7ca9a-79d7-43e8-b4ff-0efcbf23dfcc" src="https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-09/assets/119559695/a400e7a5-0b0d-41ff-9994-6e34204e87a4">


```
df["tip_percent"]=df["tip"] / df["total_bill"]
sns.scatterplot(x=df['size'], y=df['tip_percent'],data=df)
plt.title("Tip Percentage by Dining Party Size")
```
<img width="289" alt="278807741-85297eb7-efe1-4495-a2d6-4576d383d014" src="https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-09/assets/119559695/e7768070-80b2-4586-8e33-05c27071ef94">

```
sns.boxplot(x=df["sex"],y=df["tip"],hue=df["sex"])
plt.title("tips based on gender")
```
<img width="279" alt="278807799-04734581-41dd-4f5b-b2e4-85afc1bb9093" src="https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-09/assets/119559695/4600bdb0-c35d-457a-bacd-d87b79efe26f">

```
sns.scatterplot(x=df["day"],y=df["total_bill"],hue=df["day"])
plt.legend(loc="best")
plt.title("total bill amount by day of te week")
```
<img width="293" alt="278807838-2fda0016-1b0c-45e9-9f26-102c96d4c22c" src="https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-09/assets/119559695/da4cad05-eae7-45d5-baad-4a211a92e141">

```
sns.histplot(data=df, x="total_bill", hue="time", element="step", stat="density")
plt.title("Distribution of Total Bill Amounts by Time of Day")
plt.show()
```
<img width="293" alt="278807865-7d378417-a9a6-4a10-909a-83d61a1e9da9" src="https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-09/assets/119559695/ceb2d2e9-566c-43ae-aeec-4794303cc3d5">



```
sns.barplot(x=df["size"],y=df["total_bill"],hue=df["size"])
plt.title("average total bill amount by dinning party size")
```

<img width="286" alt="278807884-0c0dbc52-ce62-4957-9da0-dc77048fd09e" src="https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-09/assets/119559695/70925a4a-b005-4ec2-b639-1ef74f3a49e8">


```
sns.boxplot(x="day", y="tip", data=df)
plt.title("Tip Amount by Day of Week")
plt.show()
```
<img width="278" alt="278807916-f24cff71-ea97-44d8-8c43-5fe29d3fb0ba" src="https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-09/assets/119559695/b72c30a1-baf7-4fd3-b574-21b767b3213e">


```
sns.violinplot(x="time",y="tip",data=df)
plt.title("tip amount time of day")
```

<img width="284" alt="278807943-85c6cfba-377f-4a38-9487-a90556035ac8" src="https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-09/assets/119559695/eca12e0c-dbef-4765-8202-87255b22ada8">


```
sns.scatterplot(x="total_bill",y="tip",data=df)
plt.title("Correlation between Tip Amount and Total Bill Amount")
plt.show()
```

<img width="280" alt="278807977-67b651a6-ac90-4793-8d11-b99af66067ca" src="https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-09/assets/119559695/516c93d3-655e-419e-9f20-765346238103">


# RESULT:
Thus, Data Visualization on a complex dataset and save the data to a file has been performed successfully.
