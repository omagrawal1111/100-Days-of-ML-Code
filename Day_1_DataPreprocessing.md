## Step 1: Importing the libraries
```Python
import numpy as np
import pandas as pd
```
## Step 2: Importing dataset
```python
dataset = pd.read_csv('Data.csv')
X = dataset.iloc[ : , :-1].values
Y = dataset.iloc[ : , 3].values
```
## Step 3: Handling the missing data
```python
from sklearn.impute import SimpleImputer
simp = SimpleImputer(missing_values = 'NaN', strategy = 'mean')
simp = SimpleImputer().fit(X[:, 1:3]) 
X[:, 1:3] = simp.transform(X[:, 1:3])
```
## Step 4: Encoding categorical data
```python
from sklearn.preprocessing import LabelEncoder, OneHotEncoder
labelencoder_X = LabelEncoder()
X[ : , 0] = labelencoder_X.fit_transform(X[ : , 0])
