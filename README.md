# Ex02-Outlier
## AIM
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them
## Explanation:
An Outlier is an observation in a given dataset that lies far from the rest of the observations. That means an outlier is vastly larger or smaller than the remaining values in the set. An outlier is an observation of a data point that lies an abnormal distance from other values in a given population. (odd man out). Outliers badly affect mean and standard deviation of the dataset. These may statistically give erroneous results.
## Algorithm:
Step1: Read the given Data.
<br>
Step2: Get the information about the data.
<br>
Step3: Detect the Outliers using IQR method and Z score.
<br>
Step4: Remove the outliers.
<br>
Step5: Plot the datas using Box Plot.
## Program
```
Developed by:Kavinesh M
Register number:212222230064
```
```
import pandas as pd
import seaborn as sns

age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
df=pd.DataFrame(age)
df

sns.boxplot(data=df)
sns.scatterplot(data=df)

q1=df.quantile(0.25)
q2=df.quantile(0.5)
q3=df.quantile(0.75)
iqr=q3-q1
iqr

low=q1-1.5*iqr
low

high=q3+1.5*iqr
high

aq=df[((df>=low)&(df<=high))]
aq.dropna()

df=df[((df>=low)&(df<=high))]
df.dropna()

sns.boxplot(data=df)
sns.scatterplot(data=df)

import pandas as pd
import seaborn as sns

af=pd.read_csv("heights.csv")
af
sns.boxplot(data=af)
sns.scatterplot(data=af)

min=af['height'].quantile(0.25)
max=af['height'].quantile(0.75)

max
min
iqr=max-min
iqr

dq=af[((af['height']>=min)&(af['height']<=max))]
dq

low=min-1.5*iqr
low

high=max+1.5*iqr
high

qm=af[((af['height']>=low)&(af['height']<=high))]
qm

import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats

data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df

sns.boxplot(data=df)
sns.scatterplot(data=df)

z=np.abs(stats.zscore(df))
print(df[z['weight']>3])

val=[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]

out=[]
def d_o(val):
  ts=3
  m=np.mean(val)
  sd=np.std(val)
  for i in val:
    z=(i-m)/sd
    if np.abs(z)>ts:
      out.append(i)
  return out
op=d_o(val)
op

 ir=pd.read_csv('iris.csv')
 ir
ir.describe()
sns.boxplot(x='sepal_width',data=ir)

c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)

rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']

delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid

sns.boxplot(x='sepal_width',data=delid)

```
## Output
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/f5f621aa-d494-4b84-8aca-0d0c1d4c1597)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/fa93ac20-632d-4cd8-b76a-68394840a306)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/f2eec7ab-9b53-44bc-af09-befb901029e4)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/d2461bb8-3783-4fe8-ba77-c287430ce408)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/e1767d6c-4928-4770-b641-0ced0bf87b33)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/d25bfaf1-bd9f-4bab-be51-9f708233beb3)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/54c42a23-1b12-4815-b7ab-a0f252b2d48d)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/a25c988b-353e-479a-98e4-b222f8120a49)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/b9348ba4-c099-4aca-98f8-87535647e524)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/62458e3c-31a6-45ff-b98c-fd3505ea37ac)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/a3f9baf3-040d-4245-ba93-f2155afbcdeb)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/82e11d56-b4c4-4ef5-9725-2ec3c863c757)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/6839c0f1-29ed-4026-b8c1-50acd9fdcd4f)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/e41a9dee-3de2-472c-8b63-c64c419beaa2)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/5a8c15a3-a066-41bc-8258-0df36b8f3c5f)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/12ac2ed2-8cb0-408b-8c68-9af01f2e8146)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/e4785692-85e1-49c3-a44c-77664609ed8b)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/4ae0bc50-f20e-4bb9-9925-7f0c40901beb)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/c0ad3428-8644-46b5-98a6-e0d56783c486)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/0b9f2034-cab0-4674-a63f-e8f7ef3c215b)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/b5d433c7-f75c-41b4-9297-299ac54ade10)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/8909a651-a861-469a-89a7-c77d5dda1709)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/ef7b319a-2002-4286-8619-80ac58775efc)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/2ffd4010-e7d6-4c04-bfd2-f036b2d532ef)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/b4b45961-92de-4d0a-a86a-325d9b3e888d)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/706585bd-abb0-4df9-b53c-4669d3cfb20f)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/f08030b4-0e11-4a9c-b500-2ae6ec883669)
![image](https://github.com/kavinesh8476/ODD2023---Datascience---Ex-02/assets/118466561/ff40cc12-e462-4cb7-91ed-a26ee384b0c5)
## Result
Hence the given set of data is read and the outliers are removed using the IQR method and Zscore method.

