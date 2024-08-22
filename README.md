# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df
```
![359350378-8adc30dc-e6fa-4ce7-923b-899cdd2beab1](https://github.com/user-attachments/assets/39d687dc-4871-4a4d-a5de-0e03f0d5bdaf)

```
df.isnull().sum()
```
![359351563-13144857-3459-4933-96d3-07cd6fa8447f](https://github.com/user-attachments/assets/1abd3d7d-53b3-4066-872e-a06cec2dbffe)
```
df.isnull().any()
```
![359351697-d4d731aa-d185-4f8d-84b2-1ff0c54e716c](https://github.com/user-attachments/assets/a48f5789-6444-4df5-8ce8-2e328964a2b1)
```
df.dropna()
```
![359351735-b31c1c7a-d5c5-4b5e-a152-e7bcaa6d8fa0](https://github.com/user-attachments/assets/e5aa5c25-f732-4146-86f8-98e9b0961db2)
```
f.fillna(0)
```
![359352182-56a32cbf-d6aa-4713-9484-452a985c3e48](https://github.com/user-attachments/assets/c0ca3c63-5c23-47e3-b56d-0c119c0786d3)
```
df.fillna(method = 'ffill')
```
![359352219-089ea242-272f-4db3-88c1-3b53e6c18a3c](https://github.com/user-attachments/assets/f9451134-1e19-43ff-b77c-d7e9ac430bc3)
```
df.fillna(method = 'bfill')
```
![359352694-f9d31d4c-5e67-4006-b883-b5281bb06b10](https://github.com/user-attachments/assets/e1655994-2c5c-4e65-b820-0783b44b53cb)
```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![359353217-9a88b1a8-967f-4d68-9c77-894d7d56a784](https://github.com/user-attachments/assets/bec96253-ff50-4898-bcf4-b7e9533a80ba)
```
import pandas as pd
ir=pd.read_csv('iris.csv')
ir
```
![359353340-c65cec8b-a7ba-453d-8043-11f54b91d134](https://github.com/user-attachments/assets/37ced75c-dee7-4ef0-9c7f-3fd452bf0f47)
```
ir.describe()
```
![359353400-18034d3a-7649-48bf-81a2-69ba90a69434](https://github.com/user-attachments/assets/e0ce049a-0bd2-4b91-b124-abfc79ce6286)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![359353458-96f053eb-fbef-4ac3-b1a5-62c09bd42b35](https://github.com/user-attachments/assets/d942ccce-f2b7-41b0-b73f-019f0eb9fbbc)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![359354582-f45130a9-d76e-4bf1-af6d-3bd3552a6cdd](https://github.com/user-attachments/assets/3ba00df8-5f9f-4e7c-bf32-2c96db2e2484)
```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![359354640-c8963449-c62d-4b40-bbef-94c0a7488dd9](https://github.com/user-attachments/assets/391bc27b-ee2f-4355-811a-5beaffeb7340)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![359354640-c8963449-c62d-4b40-bbef-94c0a7488dd9](https://github.com/user-attachments/assets/d8e2c3bd-84c1-49b4-8bd2-1cd2e953542f)
```
sns.boxplot(x='sepal_width',data=delid)
```
![359354785-81b792c4-cd80-4032-9c05-22457713dfd0](https://github.com/user-attachments/assets/bf893d14-7f27-401b-88fc-48cbcb3204ef)
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("heights.csv")
dataset
```
![359354841-c93bec2d-309a-45e4-9a6d-75f39f58ac5c](https://github.com/user-attachments/assets/158c0d13-8ca8-4e33-8f14-1b14cb4e29e2)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
```
![359354893-03c2cfd9-c5cd-4cfc-a359-5d7f02a1ec3e](https://github.com/user-attachments/assets/7698de16-346c-46b2-bfd6-2b4bf7210e7c)
```
low = q1 - 1.5*iqr
low
```
![359354945-aaca6523-248b-4508-b13c-fcd82d1fa7eb](https://github.com/user-attachments/assets/c267156c-2aa9-4997-9563-0f1eeab31ed0)
```
high = q3 + 1.5*iqr
high
```
![359354992-f962ad79-8194-4807-9e6f-d17f8af04474](https://github.com/user-attachments/assets/71797e00-982d-4a5f-886f-142235614a28)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![359355044-0f6402ad-42e5-44db-9d30-062ce99ea2d8](https://github.com/user-attachments/assets/853beddb-b851-4e09-ba6b-0fd05f24d3e7)
```
z = np.abs(stats.zscore(df['height']))
z
```
![359355118-06ddc9cb-0f93-4790-a2c3-4969e030e7e1](https://github.com/user-attachments/assets/6fbe74b7-c9d6-404d-bb4d-63d6be74aa9d)
```
df1 = df[z<3]
df1
```
![359355159-da00179b-e8aa-4af7-9bc1-0d4086d550a0](https://github.com/user-attachments/assets/ea014d13-9a1b-49b8-85ce-043a7de9dc6f)






# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
