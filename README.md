## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
### Name : LINGARAJA L
### Ref No : 212222040086

```python

import pandas as pd
df=pd.read_csv("/content/Encoding Data.csv")
df
```
![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/cc340a1e-f3a2-400e-ac49-5b7bf117d5b5)

```
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["ord_2"]])
```
![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/28366754-2cdd-4b9e-b8fa-5c14d8ca8246)


```
df['bo2']=e1.fit_transform(df[["ord_2"]])
df
```

![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/8bc656e8-e43f-4de3-8b59-bee2cadfb3a8)


```
le=LabelEncoder()
dfc=df.copy()
dfc['ord_2']=le.fit_transform(dfc['ord_2'])
dfc
```
![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/278befe7-e32c-4f95-8ec2-783d9f8676a8)


```
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse=False)
df2=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[["nom_0"]]))
```

![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/98b553e3-fc38-4f0a-bc62-0e4c8b59b4e4)


```
df2=pd.concat([df2,enc],axis=1)
df2
```

![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/05905b28-3bab-439a-93d2-ab3c8755784c)


```
pd.get_dummies(df2,columns=["nom_0"])
```

![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/2ae2a20d-9c3c-4e97-a23b-75b9fb1f1b31)


```
pip install --upgrade category_encoders
```
![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/695e0d3b-a033-4c63-95c8-3800f9531032)


```
from category_encoders import BinaryEncoder
df=pd.read_csv("/content/data.csv")
df
```

![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/b6e590b9-92ca-472b-97be-53b11e3285dd)


```
be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])
df
```

![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/4b777c13-2102-4e43-b958-33da8257d763)


```
dfb=pd.concat([df,nd],axis=1)
dfb
```

![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/cb77f4e7-372b-4eb4-9b59-d8b5f6221364)


```
from category_encoders import TargetEncoder
te=TargetEncoder()
CC=df.copy()
new=te.fit_transform(X=CC["City"],y=CC["Target"])
CC=pd.concat([CC,new],axis=1)
CC
```

![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/1835f03b-60f5-4f7d-8cdb-a828cc2ec365)


```
import pandas as pd
from scipy import stats
import numpy as np
df=pd.read_csv("/content/Data_to_Transform.csv")
df
```

![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/916e5147-6338-41b5-b634-83c82b14d7db)


```
df.skew()
```

![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/0e51a43e-348b-4548-aff4-6991090ea7ef)


```
np.log(df["Highly Positive Skew"])
```

![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/a3f6559f-c64e-4231-be46-d1551e14294b)


```
np.reciprocal(df["Moderate Positive Skew"])
```

![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/593ffb36-2642-446c-bfb3-1c5a56526fe7)


```
np.sqrt(df["Highly Positive Skew"])
```

![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/4f9de43f-70cf-4a43-99cb-a2a470074871)


```
np.square(df["Highly Positive Skew"])
```

![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/d2c46f82-745a-4ed6-8255-783c52171db5)


```
df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])
df
```

![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/465118fe-93a9-46e8-8eac-48158abf99d7)


```
df.skew()
```
![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/a9a788d9-fd58-4176-849f-a6059eda05c9)


```
df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
```

![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/5733d06e-6c36-467c-90a9-66120905f17d)


```
import seaborn as sns
import statsmodels.api as sm
import matplotlib.pyplot as plt
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```

![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/ebcd8f9c-c5be-409e-970f-154ada76cb16)



```
sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
plt.show()
```

![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/279cc6b3-6ae4-4d0a-a6cf-5d10f0acf240)



```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)

df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])

sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```

![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/364797e3-1fc8-4e02-a722-a76605211320)



```
df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
sm.qqplot(df["Highly Negative Skew"],line='45')
plt.show()
```

![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/04d2c438-5e05-46de-92cb-80554f9569ed)



```
sm.qqplot(df["Highly Negative Skew_1"],line='45')
plt.show()
```

![image](https://github.com/silambarasan2004/EXNO-3-DS/assets/119559917/63af3c45-4261-4953-9ccb-0910c3181a3e)




## RESULT:
Thus the given data, Feature Encoding, Transformation process and save the data to a file was performed successfully.
       
