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
### Developed By: LATHIKESHWARAN J
### Register Number: 212222230072
```

### 1) Read and display DataFrame
```Python
import pandas as pd
df=pd.read_csv('/content/SAMPLEDS.csv')
df
```
      
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/13c8033c-7cdb-4b51-bcce-1bf186ca33a7)
</td>
</tr>
<tr>
  <td width=50%>
              
### 2) Display head
```Python
df.head()
```

              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/7e8163c1-7aff-42aa-a9d9-a9be834b0125)


### 3) Display tail
```Python
df.tail()
```

              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/31eb0ada-9761-499d-8cf2-31e043eac8e0)


### 4) Info of datafram
```Python
df.info()
```

              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/22cd4eee-0b3f-4a2f-9ff7-c5fea86d5703)


### 5) Describe about the dataframe
```Python
df.describe()
```
     
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/28cfed13-f10d-4062-8b88-3da61848e96c)

### 6) Shape of the datafram
```Python
df.shape
```

              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/5814ae95-6244-4dd0-bb1b-43bf0bd5583b)


### 7) Checking tha NUll values
```Python
df.isnull().sum()
```

              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/1c352767-c32d-4d18-9fce-3e600d7af552)


### 8) Drop the Null values
```Python
x=df.dropna(how='any')
x
```

              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/fdff72dd-a19b-4c72-b492-6fed41b35f54)


### 9) Drop the Null values in Total
```Python
tot=df.dropna(subset=['TOTAL'],how='any')
tot
```
              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/d21f329a-35aa-4cd7-912f-99fe36f258b7)


### 10) FIll the Null values
```Python
df.fillna(0)
```
       
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/8d35ac83-889f-451e-bc63-78fbcf44fb04)

### 11) Finding the mean value
```Python
mn=df.TOTAL.mean()
mn
```

              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/489a50a1-eb88-449c-8d7e-bff5e42c5af0)



### 12) Fill Null value with Mean value
```Python
df.head()
```
              
#### OUTPUT:

df.TOTAL.fillna(mn,inplace=True)
df


### 13) Final output
```Python
for x in df.index:
  if df.loc[x,"AVG"]>100:
    df.drop(x,inplace=True)
df
```

              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/fb8391ca-d62a-4e26-a1aa-a15d27a884f9)

### 14) Outlier detection and removal
```Python
import pandas as pd
import seaborn as sns
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
dff=pd.DataFrame(age)
dff
```
              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/28a59ebe-bdcc-4f04-93be-c29c353cdcb0)

### 15) Boxplot
```Python
dsf=sns.boxplot(dff)
```
     
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/9876bce8-ef7f-49b2-8a97-114162113c71)


### 16) Scatterplot
```Python
dsf=sns.scatterplot(dff)
```
   
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/8144b619-8a24-44fd-a670-d317c88e81f9)



### 17) IQR
```Python
q1=dff.quantile(0.25)
q2=dff.quantile(0.5)
q3=dff.quantile(0.75)
iqr=q3-q1
iqr
```

              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/5ce6b72c-20d6-4542-a6ef-f607de82fc3d)

    
### 18) Checking the high and low value
```Python
low=q1-1.5*iqr
low
high=q3+1.5*iqr
high
```

              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/23185839-8632-43ee-bd1c-33da6ec53f9c)

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/aef8585c-4c27-4d68-a0cb-653026339b45)


    
### 19) Filtering outlier value
```Python
dff=dff[((dff>=low)&(dff<=high))]
dff
```
     
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/a350867b-a6c0-4d3a-94fa-7e13b6874499)

    
### 20) Dropping the null value
```Python
dff.dropna()
```

              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/e89a47bf-418b-4d60-9c75-f4e150bde470)


    
### 21) Box plotting after filtering outlier
```Python
sns.boxplot(data=dff)
```
     
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/b26c5fa9-3286-4299-a3e0-462659b72e6d)

  
### 22) Z Score
```Python
import pandas as pd
import seaborn as sns
import numpy as np
from scipy import stats
data={'weight':[12,15,18,21, 24, 27, 30, 33, 36, 39, 42, 45, 48, 51, 54, 57,60,63,66,69,202,72, 75, 78, 81, 84, 232, 87, 90, 93,96,99,258]}
ds=pd.DataFrame(data)
ds
```
 
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/c81cd121-42a2-4608-892b-33755423d018)

### 23) Z Score
```Python
import pandas as pd
import seaborn as sns
import numpy as np
from scipy import stats
data={'weight':[12,15,18,21, 24, 27, 30, 33, 36, 39, 42, 45, 48, 51, 54, 57,60,63,66,69,202,72, 75, 78, 81, 84, 232, 87, 90, 93,96,99,258]}
ds=pd.DataFrame(data)
ds
```

#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/c81cd121-42a2-4608-892b-33755423d018)

    
### 24) Z Score
```Python
sns.boxplot(data=ds)
```

              
#### OUTPUT:
![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/a1afb418-e531-4eaa-9f0f-db5be7b0c20c)

    
 ### 25) Z Score
```Python
z=np.abs(stats.zscore(ds))
z
```
   
#### OUTPUT:
![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/f52c84e7-00eb-4c8e-b5a7-653ea094ed1f)




### 26)Z score 
```Python
print(ds[z['weight']>3])
```


#### OUTPUT:
![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/5deaf50a-9342-48f4-ae99-1cc751d39320)


# Result
          Therefore program was successfully executed
