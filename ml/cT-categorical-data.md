### Categorical Data

有的数据是categorical，又分为nominal和ordinal两类，其中nominal是无序的，而ordinal是有序的。  

**Nominal** basically refers to categorically discrete data such as name of your school, type of car you drive or color of a bike.  

**Ordinal** refers to quantities that have a natural ordering.  The rating scale from 1 to 5,  cloth size ranging from 'M' to 'L' and to 'XL'.

### Handling Categorical Data

#### Ordinal Data

Just convert the categorical string values into integers. 数据类别是有序的，直接转化为数值类型即可。

```python
size_mapping = {"XL": 3, "L": 2, "M": 1 }
```

#### Nominal Data

对nominal data，也需要转化为数值表征，但数值知识一个类别，而不表征数值关系；但建模过程中，数值会被认为有大小之分，比如会认为2大于1，所以需要one-hot encoding，需要使用dummy variable，比如blue可以表示为`blue = 1, green = 0, red = 0`。

```python
import pandas as pd
df = pd.DataFrame({'color':['green','red','blue'],'size':[1,2,3]})
X = df.values

# map color to numerical
from sklearn.preprocessing import LabelEncoder
color_le = LabelEncoder()
X[:, 0] = color_le.fit_transform(X[:, 0])
# array([[1, 1],
#       [2, 2],
#       [0, 3]], dtype=object)

# map with one-hot encoding
from sklearn.preprocessing import OneHotEncoder
ohe = OneHotEncoder(categorical_features=[0], sparse=False)
ohe.fit_transform(X)
# array([[  0. ,   1. ,   0. ,   1. ],
#        [  0. ,   0. ,   1. ,   2. ],
#        [  1. ,   0. ,   0. ,   3. ]])
```

也可以用pandas的`get_dummies()`方法实现相同的功能。