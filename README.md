# Multivariate_Analysis
## ODD2023-Datascience-Ex-04
## AIM
To perform Multivariate EDA on the given data set.

## Explanation:
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

## ALGORITHM:
### STEP 1
Import the built libraries required to perform EDA and outlier removal.

### STEP 2
Read the given csv file

### STEP 3
Convert the file into a dataframe and get information of the data.

### STEP 4
Return the objects containing counts of unique values using (value_counts()).

### STEP 5
Plot the counts in the form of Histogram or Bar Graph.

### STEP 6
Use seaborn the bar graph comparison of data can be viewed.

### STEP 7
Find the pairwise correlation of all columns in the dataframe.corr()

### STEP 8
Save the final data set into the file

## PROGRAM
~~~
import pandas as pd
from scipy import stats
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
~~~
~~~
from google.colab import files
uploaded = files.upload()
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/e6107443-5485-483a-b28e-177cdf08a693)

~~~
df = pd.read_csv('diabetes.csv')
df
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/e26ed41c-cbde-4e44-acd0-414c33adec44)

~~~
df.isnull().sum()
~~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/fa79a84f-0560-41be-9b82-d9108f1ae9d2)

~~~
q1 = df.quantile(0.25)
q3 = df.quantile(0.75)
iqr = q3 - q1
iqr
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/7ef393cf-de36-4f9b-8695-a64aba0b0688)

~~~
sns.boxplot(df)
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/84375714-c2e8-4b42-b062-e2b397f64050)

~~~
plt.figure(figsize = (14,6))
sns.scatterplot(x = 'Glucose',y='BloodPressure',data = df)
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/470d5163-647a-4aed-a773-93cf25cd3edb)

~~~
sns.scatterplot(x = 'Glucose',y='Insulin',data = df)
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/e01ed90e-ce39-477a-ab1e-49cfcab33815)

~~~
sns.scatterplot(x = 'Glucose',y='DiabetesPedigreeFunction',data = df)
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/003e67e1-6465-4d4e-a9d9-a9286b90034c)

~~~
sns.scatterplot(x = 'Glucose',y='Age',data = df)
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/bf7dba38-e019-46ae-b74d-6ee5ad5f5b0c)

~~~
sns.heatmap(df.corr(),annot = True)
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/cd11464e-28ef-439f-b4f5-32ac523c2f88)

~~~
from google.colab import files
uploaded = files.upload()
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/59c64c4e-90cb-41e3-a0df-37985f99bf28)

~~~
df = pd.read_csv('employeesal.csv')
df
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/e3d3bfd8-4cc9-4026-992d-394b72649555)

~~~
df.isnull().sum()
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/bd1cd0ee-b399-4d24-87ae-845ddd858af1)

~~~
numeric_cols = df.select_dtypes(include=[int, float])
q1 = numeric_cols.quantile(0.25);
q3 = numeric_cols.quantile(0.75);
iqr = q3 - q1
iqr
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/1cc92292-fa4d-44f4-969e-773e2eb1e355)

~~~
low = q1 - 1.5*iqr
high = q1 + 1.5*iqr
numeric_cols = numeric_cols[(numeric_cols >= low) & (numeric_cols <= high)]
numeric_cols.dropna()
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/805b0cb4-cac4-4b80-a068-4d6468ffb58b)

~~~
sns.boxplot(numeric_cols)
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/50695ad5-e577-41c0-ab2a-f5e9f3a963cf)

~~~
sns.scatterplot(x = 'Salary',y='Age',data = numeric_cols)
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/564265df-d83c-4989-8473-5ff4c2e51c68)

~~~
sns.scatterplot(x = 'Experience_Years',y='Salary',data = numeric_cols)
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/b6c026ec-872c-4924-a931-7121d30451c3)

~~~
sns.scatterplot(x = 'Experience_Years',y='Age',data = numeric_cols)
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/f1036adf-036f-4796-8ca3-3ee5ec9a988d)

~~~
sns.heatmap(numeric_cols.corr(),annot = True)
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/6c2c6ed6-3f73-414d-b030-4c3e13c04443)

~~~
from google.colab import files
uploaded = files.upload()
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/9752b443-23e0-404e-9f34-e4fbaefaab75)

~~~
df = pd.read_csv('SuperStore.csv')
df
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/a5b09253-e0ef-4697-b6aa-c190b97285b8)

~~~
df.isnull().sum()
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/09906d2f-2b2d-4723-8e74-547e9b60fcb6)

~~~
df.dropna()
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/0aaa46f0-e4d9-4eb5-8367-e698238940d2)

~~~
df.dtypes
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/dd56b8c6-dd76-4d8f-800a-186c03535231)

~~~
numeric_cols = df.select_dtypes(include=[int,float])
q1 = numeric_cols.quantile(0.25);
q3 = numeric_cols.quantile(0.75);
iqr = q3 - q1
iqr
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/15dc5503-fb48-40c2-b58a-98f8c2896879)

~~~
low = q1 - 1.5*iqr
high = q1 + 1.5*iqr
numeric_cols = numeric_cols[(numeric_cols >= low) & (numeric_cols <= high)]
~~~
~~~
sns.boxplot(numeric_cols)
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/75e99ef2-fdbf-42ce-922a-86d9dfb12e79)

~~~
sns.heatmap(numeric_cols.corr(),annot = True)
~~~
![image](https://github.com/Kulaganachi/Multivariate_Analysis/assets/133641126/0f0e95f4-9550-4bc6-87ef-ebd0e40ab270)


## RESULT
Thus we have read the given data and performed the multivariate analysis with different types of plots.

