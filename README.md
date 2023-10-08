# Ex02-Outlier
### AIM:
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

### EXPLANATION:
An Outlier is an observation in a given dataset that lies far from the rest of the observations. That means an outlier is vastly larger or smaller than the remaining values in the set. An outlier is an observation of a data point that lies an abnormal distance from other values in a given population. (odd man out). Outliers badly affect mean and standard deviation of the dataset. These may statistically give erroneous results.

### ALGORITHM:

### Step1: 
Read the given Data.
### Step2:
Get the information about the data.
### Step3:
Detect the Outliers using IQR method and Z score.
### Step4:
Remove the outliers.
### Step5: 
Plot the datas using Box Plot.

### PROGRAM:
```
DEVELOPED BY:DIVYA.K
REGISTER NO:212222230035
```
IQR:
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
```
Z SCORE
```

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
### OUTPUT

![image](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/f3f478e2-7067-43bb-97d9-2b358a3457d4)



![265188915-fa93ac20-632d-4cd8-b76a-68394840a306](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/ed79c491-c463-4b18-a2e9-30596b33dc8d)





![265188955-f2eec7ab-9b53-44bc-af09-befb901029e4](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/07efeec8-2849-4ae9-9131-2dc29f42c019)


![265188978-d2461bb8-3783-4fe8-ba77-c287430ce408](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/7970ff61-1016-491d-bd5b-1a7827ccd0b6)


![265188996-e1767d6c-4928-4770-b641-0ced0bf87b33](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/a7a4b055-aeed-4561-9dae-10a9cb1a59a7)


![265189016-d25bfaf1-bd9f-4bab-be51-9f708233beb3](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/a6f3ece1-3df1-4098-9ed7-0dcf0910b299)


![265189042-54c42a23-1b12-4815-b7ab-a0f252b2d48d](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/2113c69e-2f52-4504-8e8f-15c6ba4bfb60)


![265189078-a25c988b-353e-479a-98e4-b222f8120a49](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/52ec1916-47b3-4b40-a286-f64b961841fa)



![265189108-b9348ba4-c099-4aca-98f8-87535647e524](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/83eb50f0-ba23-422c-8d79-8c8a01b1be70)


![265189128-62458e3c-31a6-45ff-b98c-fd3505ea37ac](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/eb34952f-b0b5-40e4-8bff-d48d9827fb68)





![265189146-a3f9baf3-040d-4245-ba93-f2155afbcdeb](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/0160d345-7dcb-4dbb-a9d3-ff158b548626)



![265189183-82e11d56-b4c4-4ef5-9725-2ec3c863c757](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/2e9e39f9-2ca3-4e0a-a75b-9b97c55b0115)




![265189320-6839c0f1-29ed-4026-b8c1-50acd9fdcd4f](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/4ae5966c-b5b1-48b7-8ca7-51b2a05cf068)



![265189403-e41a9dee-3de2-472c-8b63-c64c419beaa2](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/3ebdfd68-a4d1-428a-b960-29e5a1210485)

![265189449-5a8c15a3-a066-41bc-8258-0df36b8f3c5f](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/cb999a5b-275d-4dc7-961f-7800b5451501)





![265189468-12ac2ed2-8cb0-408b-8c68-9af01f2e8146](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/b1655335-1978-42ff-a039-dd4c1dc9d77b)




![265189742-e4785692-85e1-49c3-a44c-77664609ed8b](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/afd03d2b-4d17-44c5-95f1-4738904fb61c)
![image](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/ff1ca552-5a59-4084-a416-30ee22a387ff)


![265189927-c0ad3428-8644-46b5-98a6-e0d56783c486](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/8bf48df0-c437-48d0-bd28-e5a5bffefa9e)


![265189951-0b9f2034-cab0-4674-a63f-e8f7ef3c215b](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/40ee6f3e-2b00-4a45-a5ef-0c0abc224dbd)


![265189973-b5d433c7-f75c-41b4-9297-299ac54ade10](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/44a6d879-dd03-4132-8658-353833b9ef44)


![265189990-8909a651-a861-469a-89a7-c77d5dda1709](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/fb4e9a0f-86a2-4092-9294-f96cbb5bf1a4)


![265190010-ef7b319a-2002-4286-8619-80ac58775efc](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/ba5c5483-98ee-4faf-845d-17ab9e64644b)

![265190033-2ffd4010-e7d6-4c04-bfd2-f036b2d532ef](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/45045707-51f5-4d57-ba92-b3d3a6d0f3f7)

![265190062-b4b45961-92de-4d0a-a86a-325d9b3e888d](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/b73d670c-2a80-49e3-af56-3971c1c59963)

![265190078-706585bd-abb0-4df9-b53c-4669d3cfb20f](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/307a59d0-092a-4b97-adf3-4b8ab5141b8e)

![265190103-f08030b4-0e11-4a9c-b500-2ae6ec883669](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/c22957a3-809a-4c0a-b88c-dc48cdc31661)



![265190116-ff40cc12-e462-4cb7-91ed-a26ee384b0c5](https://github.com/divyakumars/ODD2023---Datascience---Ex-02/assets/119393621/c4453ca9-1838-4506-bf6c-b9304d4fb03e)



### RESULT:
Hence the given set of data is read and the outliers are removed using the IQR method and Zscore method.
























