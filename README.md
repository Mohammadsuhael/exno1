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

## DATA CLEANING
1.
```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![Screenshot 2025-03-07 110441](https://github.com/user-attachments/assets/09fbd754-83e1-4cc4-9c85-d1cba8e7a2f5)

2.
```
df.head()

```
![Screenshot 2025-03-07 110555](https://github.com/user-attachments/assets/27aacd11-c642-4ed7-b2be-90b13df9e465)


3.
```
df.tail()
```
![Screenshot 2025-03-07 110702](https://github.com/user-attachments/assets/d4bd07ce-35f5-4cfb-991e-907110c7b67e)

4.
```
df.fillna("XXXXXXXX")
```

![Screenshot 2025-03-07 110834](https://github.com/user-attachments/assets/0d3f5ccd-f971-4094-a585-f470b05f2b55)

5.
```
df.notnull()
```

![Screenshot 2025-03-07 110917](https://github.com/user-attachments/assets/6fd56d01-4d4a-4cc4-99c5-d72d7450c61a)
6.
```
df.isnull()
```
![Screenshot 2025-03-07 111004](https://github.com/user-attachments/assets/3dcd6b06-1251-48fe-908f-4197a1d5131d)
7.
```
df.dropna(axis=0)
```
![Screenshot 2025-03-07 111046](https://github.com/user-attachments/assets/0dcbca1b-6631-4c2c-b8ee-df397ebc4ec3)

8.
```
df.dropna(axis=1)
```
![Screenshot 2025-03-07 111053](https://github.com/user-attachments/assets/d8d4bf44-9024-47de-9d91-497cb7a1183d)

9.
```
df.isnull().sum()
```

![Screenshot 2025-03-07 111102](https://github.com/user-attachments/assets/32f17ffa-4020-49cf-b596-e9fcd269a6bb)

10.
```
df.isnull().any()
```
![Screenshot 2025-03-07 111108](https://github.com/user-attachments/assets/47750938-5b77-47ff-8fd7-7033a75c9ed8)

11.

```
df.fillna(method= 'ffill')
```
![Screenshot 2025-03-07 111456](https://github.com/user-attachments/assets/31592ef8-5a77-406e-9ace-8715a1b54108)

12.
```
df.fillna(method ='bfill')
```
![Screenshot 2025-03-07 111509](https://github.com/user-attachments/assets/6fa75e7a-d681-459e-8b6f-8bcfc186fad6)

13.
```
df.fillna({'NAME':'SRI','GENDER':'MALE','ADDRESS':'CROMPET','M1':'00','M2':'00','M3':'00','M4':'00','TOTAL':'00','AVG':'00'})
```
![Screenshot 2025-03-07 111517](https://github.com/user-attachments/assets/4080bc58-644c-4cf7-a2ae-fc22af5ebfb5)

## IQR(Inter Quartile Range)


14.
```
import pandas as pd
df=pd.read_csv("/content/iris.csv")
df
```
![Screenshot 2025-03-07 111522](https://github.com/user-attachments/assets/c4ee94a5-c8b6-44e2-80c3-24701453a53d)

15.
```
df.describe()
```
![Screenshot 2025-03-07 111527](https://github.com/user-attachments/assets/e3c9e573-e576-4145-960b-55beca7664f5)

16.

```
df.info()
```
![Screenshot 2025-03-07 111532](https://github.com/user-attachments/assets/875b48ca-1be2-480f-8a63-c85b41916d57)

17.
```
df.shape
```
![Screenshot 2025-03-07 112218](https://github.com/user-attachments/assets/62c8135c-4908-4a49-9bda-3d88a798238f)

18.
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=df)
```
![Screenshot 2025-03-07 111536](https://github.com/user-attachments/assets/38233d9f-beae-45d7-b656-3637f112fa15)

19.
```
import seaborn as sns
sns.boxplot(x='sepal_length',data=df)
```

![Screenshot 2025-03-07 111542](https://github.com/user-attachments/assets/03fe5f9d-edb0-41b7-92f2-3116bc1d2ddf)

20.

```
q1=df.sepal_width.quantile(0.25)
q3=df.sepal_width.quantile(0.75)
iq=q3-q1
print(q1,q3,iq)
```
![Screenshot 2025-03-07 111548](https://github.com/user-attachments/assets/35873bd6-f4e5-48e5-94fb-95dd6da8e14d)

21.
```
q3+ 1.5 *iq
```
![Screenshot 2025-03-07 111551](https://github.com/user-attachments/assets/88c05f7c-bc1d-46ea-a748-98c76b7d5aa1)

22.
```
  rid=df[((df.sepal_width<(q1-1.5*iq))|(df.sepal_width>(q3+1.5*iq)))]
  rid["sepal_width"]
```
![Screenshot 2025-03-07 111556](https://github.com/user-attachments/assets/d3cc72ea-8ea5-4e18-b1ba-f1970ab112b4)

23.
```
  delid=df[~((df.sepal_width<(q1-1.5*iq))|(df.sepal_width>(q3+1.5*iq)))]
  delid["sepal_width"]
```
![Screenshot 2025-03-07 111601](https://github.com/user-attachments/assets/45febfb0-a0fc-48e0-9eb5-d8a2b81e4dad)


## ZSCORE

24.
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
```
![Screenshot 2025-03-07 113129](https://github.com/user-attachments/assets/78d77542-087e-4d42-a554-4356527ecf08)

25.
```
low = q1 - 1.5*iqr
low
```
![Screenshot 2025-03-07 113133](https://github.com/user-attachments/assets/9c58feae-c66d-4d2e-a316-cbcf65b3b9ef)

26.

```
high = q3 + 1.5*iqr
high
```
![Screenshot 2025-03-07 113138](https://github.com/user-attachments/assets/44da246d-9cf1-4d24-8eba-9e893e65d593)

27.

```

df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```



![Screenshot 2025-03-07 113142](https://github.com/user-attachments/assets/55b66613-c7a3-4085-a171-125f304b996d)

28.
```
z = np.abs(stats.zscore(df['height']))
z
```

![Screenshot 2025-03-07 113147](https://github.com/user-attachments/assets/e051ba83-55a5-4112-9c81-05418fda0086)

29.
```
df1 = df[z>3]
df1
```
![Screenshot 2025-03-07 113152](https://github.com/user-attachments/assets/0d546dde-245a-4ed7-9792-cda3e79ea4cc)

30.
```
df1 = df[z<3]
df1
```
![Screenshot 2025-03-07 113159](https://github.com/user-attachments/assets/41dc899d-c775-463f-b1fa-88c839b6a92e)



# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method
