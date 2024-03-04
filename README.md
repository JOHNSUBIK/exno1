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
### Developed By: John Paul J
### Register Number: 212223230093
1) Read and display DataFrame
```
import pandas as pd
df=pd.read_csv('/content/SAMPLEDS.csv')
df
```
OUTPUT:
![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/a55fe917-4e95-4bb9-9c82-d9630c17c8b4)
2) Display head
```
df.head()
```
OUTPUT:
![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/8b7dd54f-5afd-415b-a148-7074a36fa828)
3) Display tail
```
df.tail()
```
OUTPUT:

![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/81903b6f-b5a0-4789-ac20-97f4635b8fa0)

4) Info of datafram
```
df.info()
```
OUTPUT:

![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/33ee706c-e0c0-4e3a-a56f-516a59410504)

5) Describe about the dataframe
```
df.describe()
```
OUTPUT:

![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/fd27411f-154d-488e-a9b4-f749e0a184bf)

6) Shape of the datafram
```
df.shape
```
OUTPUT:

![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/0af65e74-4bee-4d32-b583-edceaf5fd9c1)

7) Checking tha NUll values
```
df.isnull().sum()
```
OUTPUT:

![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/661d16c4-c5e3-4c77-93be-d302d4d3d346)

8) Drop the Null values
```
x=df.dropna(how='any')
x
```
OUTPUT:

![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/22b5d530-8cab-4b0d-bb57-fe603e91a5e4)

9) Drop the Null values in Total
```
tot=df.dropna(subset=['TOTAL'],how='any')
tot
```
OUTPUT:

10) FIll the Null values
```
df.fillna(0)
```
OURPUT:

![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/29425d3e-843c-4b09-95b1-5668d65dfce9)
11) Finding the mean value
```
mn=df.TOTAL.mean()
mn
```
OUTPUT:

![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/320df42a-3374-4054-8295-a560e98fbe15)

12) Fill Null value with Mean value
```
df.head()
```
OUTPUT:

df.TOTAL.fillna(mn,inplace=True) df

13) Final output
```
for x in df.index:
  if df.loc[x,"AVG"]>100:
    df.drop(x,inplace=True)
df
```
OUTPUT:

![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/d389cae3-3ddc-40a7-b271-79ff1f77b36e)

14) Outlier detection and removal
```
import pandas as pd
import seaborn as sns
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
dff=pd.DataFrame(age)
dff
```
OUTPUT:

![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/c8ea461e-a487-4814-8bc1-760879982ef5)

15) Boxplot
```
dsf=sns.boxplot(dff)
```
OUTPUT:

![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/76d8ce83-66fa-4a27-9640-f17e46bd9d29)

16) Scatterplot
```
dsf=sns.scatterplot(dff)
```
OUTPUT:
![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/8e95381a-6730-4a28-bff3-e28609072194)

17) IQR
```
q1=dff.quantile(0.25)
q2=dff.quantile(0.5)
q3=dff.quantile(0.75)
iqr=q3-q1
iqr
```
OUTPUT:

![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/5bd83af5-842a-4c52-b998-1d2f76286e68)


18) Checking the high and low value
```
low=q1-1.5*iqr
low
high=q3+1.5*iqr
high
```
OUTPUT:

![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/929cd6a9-3784-4778-a05f-029d53f663e6)

![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/6ecef55c-ed09-4d8c-ad24-871a7d64017b)

19) Filtering outlier value
```
dff=dff[((dff>=low)&(dff<=high))]
dff
```
OUTPUT:
![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/90442260-5740-4ec7-b430-9deb8eccd14f)

20) Dropping the null value
```
dff.dropna()
```
OUTPUT:
![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/f35f2b70-3d74-4f09-ab82-44fa5dbdc97d)

21) Box plotting after filtering outlier
```
sns.boxplot(data=dff)
```
OUTPUT:
![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/21695d44-2e24-43cf-8689-d32ec9121b5d)

22) Z Score
```
import pandas as pd
import seaborn as sns
import numpy as np
from scipy import stats
data={'weight':[12,15,18,21, 24, 27, 30, 33, 36, 39, 42, 45, 48, 51, 54, 57,60,63,66,69,202,72, 75, 78, 81, 84, 232, 87, 90, 93,96,99,258]}
ds=pd.DataFrame(data)
ds
```
OUTPUT:
![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/07e1aac1-056c-43d5-93b9-01ff3193766c)

23) Z Score
```
import pandas as pd
import seaborn as sns
import numpy as np
from scipy import stats
data={'weight':[12,15,18,21, 24, 27, 30, 33, 36, 39, 42, 45, 48, 51, 54, 57,60,63,66,69,202,72, 75, 78, 81, 84, 232, 87, 90, 93,96,99,258]}
ds=pd.DataFrame(data)
ds
```
OUTPUT:
![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/6445b14d-f882-4b56-a360-72b3648d1171)

24) Z Score
```
sns.boxplot(data=ds)
```
OUTPUT:
![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/3ea1ee08-3ac8-48c0-b043-94283fa1694b)

25) Z Score
```
z=np.abs(stats.zscore(ds))
z
```
OUTPUT:
![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/4633aabd-073f-4d98-996f-7eab2b09e292)

26)Z score
```
print(ds[z['weight']>3])
```
OUTPUT:
![image](https://github.com/JOHNSUBIK/exno1/assets/150279319/1111afb7-1de1-43d3-8426-f24816426469)

# Result
    Thus the program executed succesfully
