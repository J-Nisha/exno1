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
          import numpy as np
          import seaborn as sns
          import os 
          df=pd.read_csv("SAMPLEIDS.csv")
          df
```
![Screenshot 2025-03-13 133336](https://github.com/user-attachments/assets/0aa645be-35b8-4759-9c27-9feb0c6efd51)
```
df.isnull().sum()
```
![Screenshot 2025-03-13 133430](https://github.com/user-attachments/assets/e3002655-2dea-40d3-bf50-4bdd0eedea9c)
```
df.isnull().any()
```
![Screenshot 2025-03-13 133558](https://github.com/user-attachments/assets/5ac64f47-5900-4371-8be3-cb0b83090f7b)
```
df.dropna()
```
![Screenshot 2025-03-13 133644](https://github.com/user-attachments/assets/1cb47ea8-4f27-4c50-a6d1-b828e213ec58)
```
df.fillna(0)
```
![Screenshot 2025-03-13 133724](https://github.com/user-attachments/assets/5d32ee23-1c8f-4db5-bdec-cef50604db40)
```
df.fillna(method = 'ffill')
```
![Screenshot 2025-03-13 133926](https://github.com/user-attachments/assets/630d3478-8454-4125-a6d5-55a880378210)

```
df.fillna(method = 'bfill')
```
![Screenshot 2025-03-13 135459](https://github.com/user-attachments/assets/a3584cba-2307-4e72-8553-2be91227b061)
```
df_dropped = df.dropna()
df_dropped
```
![Screenshot 2025-03-13 135601](https://github.com/user-attachments/assets/3ec164d2-f33d-4544-9740-f602f0f73961)
```
df.fillna({'GENDER':'MALE','NAME':'KANISHKAR','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![Screenshot 2025-03-13 135644](https://github.com/user-attachments/assets/974ebca9-64c5-4389-b84c-af231dbd08a2)
```
import pandas as pd
         
ir=pd.read_csv('iris.csv')
ir
```
![Screenshot 2025-03-13 135826](https://github.com/user-attachments/assets/2c1ce3ec-09f6-47ba-90fe-a207d74075a7)
```
ir.describe()
```
![Screenshot 2025-03-13 135912](https://github.com/user-attachments/assets/2f84e4e6-a50b-4a80-8925-60e088e60827)
```
sns.boxplot(x='sepal_width',data=ir)
```
![Screenshot 2025-03-13 140024](https://github.com/user-attachments/assets/412b5b06-93fa-4129-a4ba-424bf4bd21dd)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```

![Screenshot 2025-03-13 140236](https://github.com/user-attachments/assets/38b436d6-6941-4163-bf1d-b4e1fed657fe)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```

![Screenshot 2025-03-13 140418](https://github.com/user-attachments/assets/6179703a-b9c8-4f86-a81e-fc269daa1ea6)
```
sns.boxplot(x='sepal_width',data=delid)
```

![Screenshot 2025-03-13 140513](https://github.com/user-attachments/assets/9b3dd6b6-be33-4ae5-94da-28ccda25c038)

```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats

dataset=pd.read_csv("heights.csv")
dataset
```

![Screenshot 2025-03-13 140906](https://github.com/user-attachments/assets/71d88635-840a-4dcc-9804-fd633507ae34)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
            
iqr = q3-q1
iqr
```

![Screenshot 2025-03-13 141023](https://github.com/user-attachments/assets/8e4fe96a-1b29-4e3b-912b-287e086c5a5d)
```
low = q1 - 1.5*iqr
low
```

![Screenshot 2025-03-13 141102](https://github.com/user-attachments/assets/ada91948-c3c1-4701-a609-e1d11294a4a4)
```
high = q3 + 1.5*iqr
high
```
![Screenshot 2025-03-13 141153](https://github.com/user-attachments/assets/6f2c73e2-bae4-40f4-ba07-3d5519ec2727)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```

![Screenshot 2025-03-13 141315](https://github.com/user-attachments/assets/ddf5f9f2-993f-4c65-aa41-1d102beba4ad)

```
z = np.abs(stats.zscore(df['height']))
z
```

![Screenshot 2025-03-13 141507](https://github.com/user-attachments/assets/0e16fc7c-d22e-4502-b02c-6b9641d662ff)
```
df1 = df[z<3]
df1
```

![Screenshot 2025-03-13 141550](https://github.com/user-attachments/assets/30ce20c8-e2ba-4b95-9fa2-fdcb5ff7ee96)

# Result
  Hence the data was cleaned , outliers were detected and removed.
          
