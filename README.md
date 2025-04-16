# EXNO2DS
# AIM:
   To perform Exploratory Data Analysis on the given data set.

# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

# CODING AND OUTPUT

Name : Santhose Arockiaraj J
Reg No : 212224230248
### DATA ANALYSIS
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

df=pd.read_csv("/content/titanic_dataset.csv")
df
```
![image](https://github.com/user-attachments/assets/0e058a48-dbb7-4405-9d46-19f629f83020)
```
df.info()
```
![image](https://github.com/user-attachments/assets/d7fb363b-ff1b-478b-9478-55d102f76f9f)\
```
df.shape
```
![image](https://github.com/user-attachments/assets/65724f0d-434b-44a2-829c-e28475e77a9f)
```
df.set_index("PassengerId",inplace=True)
df.describe()
```
![image](https://github.com/user-attachments/assets/dbf6938c-e91b-4a91-9b76-c52587cb9670)

### CATEGORICAL DATA ANALYSIS

```
df.nunique()
```
![image](https://github.com/user-attachments/assets/4f9cf8c5-b41e-48a2-a913-7a824f8514e5)
```
df["Survived"].value_counts()
```
![image](https://github.com/user-attachments/assets/b338b2db-20e8-4681-a509-176ea07d368f)
```
per=(df["Survived"].value_counts()/df.shape[0]*100).round(2)
per
```
![image](https://github.com/user-attachments/assets/d5364461-2f05-4afa-a0c2-48093e81c6af)

### UNIVARIATE ANALYSIS
```
sns.countplot(data=df,x="Survived",palette={"0": "blue", "1": "orange"})
```
![image](https://github.com/user-attachments/assets/aa153ee4-231c-4250-a2fe-a664358967d0)
```
df.Pclass.unique()
```
![image](https://github.com/user-attachments/assets/0a0ce476-6cd5-495b-863c-4f857d976c4c)
```
df.rename(columns={"Sex":"Gender"},inplace=True)
df
```
![image](https://github.com/user-attachments/assets/fca71c4a-3251-452a-9f79-4bfba5c82c95)

### BIVARIATE ANALYSIS
```
sns.catplot(x='Gender',col="Survived",kind="count",data=df,height=5,aspect=.7, palette={"male": "blue", "female": "orange"})
```
![image](https://github.com/user-attachments/assets/b93fe6cb-b7be-4e8d-b708-7865221f5292)
```
sns.catplot(x="Survived",hue="Gender",data=df,kind="count")
```
![image](https://github.com/user-attachments/assets/5cab0a60-eee7-4b78-af5f-b87a91b028f6)
```
df.boxplot(column="Age",by="Survived")
```
![image](https://github.com/user-attachments/assets/dfc3c315-c7b1-4414-88a9-3092a44b646c)
```
sns.scatterplot(x=df["Age"],y=df["Fare"])
```
![image](https://github.com/user-attachments/assets/87dc323e-a764-4906-8b94-ba90f7f669fb)
```
sns.jointplot(x="Age",y="Fare",data=df)
```
![image](https://github.com/user-attachments/assets/e9dc388e-edee-4cef-8c07-ebe7280a948d)

### MULTIVARITE ANALYSIS
```
fig,ax1=plt.subplots(figsize=(8,5))
pt=sns.boxplot(ax=ax1,x="Pclass",y="Age",hue="Gender",data=df)
```
![image](https://github.com/user-attachments/assets/9a6cac77-b723-444b-bda1-1c54f44fe6e0)
```
sns.catplot(data=df,col="Survived",x="Gender",hue="Pclass",kind="count")
```
![image](https://github.com/user-attachments/assets/90a8e8b7-22d9-474e-8bf0-a380050c1d10)
```
##Co-relation
numeric_df = df.select_dtypes(include=np.number)
# Drop 'PassengerId' column before calculating correlation
corr = numeric_df.drop(columns=['PassengerId'], errors='ignore').corr() 
sns.heatmap(corr, annot=True)
```
![image](https://github.com/user-attachments/assets/e8213644-b6ae-4b4f-868b-59cad14b56f3)
```
sns.pairplot(df)
```
![image](https://github.com/user-attachments/assets/bc203da7-9c24-47da-b8ac-1e4700238aac)

# RESULT
 Thus, performed Exploratory Data Analysis on the given data set.

   
