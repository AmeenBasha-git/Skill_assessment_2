
```
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np

df=pd.read_csv("/content/IOT-temp (1).csv")
df
```
![image](https://github.com/user-attachments/assets/046eba4b-2c55-4808-8bd2-e86bcac06af3)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/d1419561-4cb0-4417-80bf-3ea054f8e678)

```
df.noted_date.fillna(method="ffill",inplace=True)
df.rename(columns={'out/in':'status'},inplace=True)
df.status.fillna(method='ffill',inplace=True)
```
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/3557b781-ec77-4cde-adc6-c8b63ab0594e)
```
df.dtypes
```
![image](https://github.com/user-attachments/assets/45d0c1e1-68eb-4e4f-a84a-8ba789d27066)
```
df.columns
```
![image](https://github.com/user-attachments/assets/7df5c0dc-a007-4ccc-b2ef-8cd3b3b883df)
```
tp=df.temp.median()
tp
```
![image](https://github.com/user-attachments/assets/bee1f288-4bd7-4e8c-b575-c31d0801fab1)
```
df.temp.fillna(tp,inplace=True)
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/fa9be345-e130-4f35-9966-5bc5df339524)
```
sns.boxplot(data=df['temp'])
```
![image](https://github.com/user-attachments/assets/4bd7583d-d002-451c-9ef4-397814fb0564)
```
sns.boxenplot(data=df['temp'])
```
![image](https://github.com/user-attachments/assets/5dbfb5c0-0dea-488e-b819-6e799d4c8565)
```
q3=np.percentile(df['temp'],75)
q1=np.percentile(df['temp'],25)
iqr=q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/c8b33130-a916-405e-a450-89eb8baf4e78)
```
LB=q1-1.5*iqr
HB=q3+1.5*iqr
LB
```
![image](https://github.com/user-attachments/assets/a24774c0-ea81-44fe-a49b-8b4a315b88ba)
```
HB
```
![image](https://github.com/user-attachments/assets/9d382305-008b-4f6e-a131-4af3a41dbb9e)

```
df=df[((df['temp']>=LB )& (df['temp']<=HB))]
df
```
![image](https://github.com/user-attachments/assets/dd9a4d64-1848-47ae-8874-35ca63e2e263)
```
df.dropna(inplace=True)
sns.boxplot(df['temp'])
```
![image](https://github.com/user-attachments/assets/e2736ba7-f548-41d1-9e19-0aaaec5f86a4)
```
sns.boxenplot(df['temp'])
```
![image](https://github.com/user-attachments/assets/10e96f71-8d01-48d0-9c62-4b003907d2b8)# 

```
sns.countplot(data=df,x='status')
```
![image](https://github.com/user-attachments/assets/fa79aacc-b0c1-4f4e-9a1c-aa7bf2d1fa77)
```
sns.displot(data=df,x='temp',hue='status',kde=True)
```
![image](https://github.com/user-attachments/assets/b93d4bd0-959a-4ae4-9ada-bbfb210a1a35)





