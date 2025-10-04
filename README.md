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

import pandas as pd

data=pd.read_csv("Data_set.csv")

df=pd.DataFrame(data)

print(df)


<img width="929" height="512" alt="image" src="https://github.com/user-attachments/assets/ba8be5b7-15e3-40cc-bd0e-a60c323601b4" />


import pandas as pd

data=pd.read_csv("Data_set.csv")

df=pd.DataFrame(data)

df.info()


<img width="384" height="266" alt="image" src="https://github.com/user-attachments/assets/f42fd45c-d90a-403d-8d74-cb772cb74fc8" />



import pandas as pd

data=pd.read_csv("Data_set.csv")

df=pd.DataFrame(data)

print(df.describe())


<img width="398" height="318" alt="image" src="https://github.com/user-attachments/assets/07f6ce0e-80ac-4853-9056-7ce63e5fce4b" />


import pandas as pd

data=pd.read_csv("Data_set.csv")

df=pd.DataFrame(data)

print(df.isnull())


<img width="839" height="375" alt="image" src="https://github.com/user-attachments/assets/a32ae26f-ef81-45ea-9005-3c22f82a9570" />


import pandas as pd

data=pd.read_csv("Data_set.csv")

df=pd.DataFrame(data)

print(df.isnull().sum())



<img width="231" height="157" alt="image" src="https://github.com/user-attachments/assets/0bc246b7-ebb5-4115-be2c-90c74596db62" />


import pandas as pd

data=pd.read_csv("Data_set.csv")

df=pd.DataFrame(data)

dfd=df.dropna()

dfd


<img width="956" height="506" alt="image" src="https://github.com/user-attachments/assets/74b003dc-83e3-4e42-839e-32035a9daae7" />



import pandas as pd

data=pd.read_csv("Data_set.csv")

df=pd.DataFrame(data)

dfd=df.dropna(axis=1)

dfd

<img width="452" height="340" alt="image" src="https://github.com/user-attachments/assets/83ce66fd-be80-4b57-97b7-f09ce63f89eb" />


import pandas as pd 

data = pd.read_csv("Data_set.csv")

df = pd.DataFrame(data)

dff = df.fillna(0)

dff


<img width="940" height="494" alt="image" src="https://github.com/user-attachments/assets/172ebf4b-8cc3-40fb-995a-02c8c85a252a" />


import pandas as pd 
data = pd.read_csv("Data_set.csv")
df = pd.DataFrame(data)
dff = df.ffill()
dff


<img width="957" height="536" alt="image" src="https://github.com/user-attachments/assets/659bd47e-290a-4752-8013-73c7c8b5ba92" />



import pandas as pd 
data = pd.read_csv("Data_set.csv")
df = pd.DataFrame(data)
dff = df.fillna(method='bfill')
dff

<img width="988" height="380" alt="image" src="https://github.com/user-attachments/assets/590681c9-a25a-4485-bfc9-395896f5c4b4" />


import pandas as pd 
data = pd.read_csv("Data_set.csv")
df = pd.DataFrame(data)
df["watchers"]= df["watchers"].fillna(df["watchers"].mean())
df

<img width="961" height="488" alt="image" src="https://github.com/user-attachments/assets/a884e0da-6b37-427a-9f93-566dd7f3164b" />


import pandas as pd 
data = pd.read_csv("Data_set.csv")
df = pd.DataFrame(data)
df.interpolate(method = "linear")


<img width="979" height="338" alt="image" src="https://github.com/user-attachments/assets/c863c6c3-0b60-4b22-b172-2d1fa4c455a2" />


import pandas as pd 
data = pd.read_csv("Data_set.csv")
df = pd.DataFrame(data)
df.drop_duplicates()
df

<img width="947" height="534" alt="image" src="https://github.com/user-attachments/assets/7f245745-f4b3-486a-91b9-32bb7adbef60" />



from scipy import stats
import pandas as pd 
import numpy as np
data_set = pd.read_csv("iris.csv")
df = pd.DataFrame(data_set)

z_scores = np.abs(stats.zscore(df.select_dtypes(include=[np.number])))

df_cleaned = df[(z_scores < 3).all(axis=1)]
df_cleaned

<img width="432" height="382" alt="image" src="https://github.com/user-attachments/assets/40e91ac3-e0c8-4c5a-b261-88c91b99f02f" />

import pandas as pd 

import numpy as np

data_set = pd.read_csv("iris.csv")

df = pd.DataFrame(data_set)

Q1 = df["sepal_width"].quantile(0.25)
Q3 = df["sepal_width"].quantile(0.75)

IQR = Q3 - Q1

lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR

print("The Orginal DataSet")
print(df)

outliers = df[(df['sepal_width'] < lower_bound) | (df['sepal_width'] > upper_bound)]

print("The Outliers")
print(outliers)

df_clean = df[(df['sepal_width'] >= lower_bound) & (df['sepal_width'] <= upper_bound)]

print("The Dataset after removing the outliers")
print(df_clean)


<img width="593" height="672" alt="image" src="https://github.com/user-attachments/assets/6cd18071-3c37-44a4-a3ea-fd8be11b3be1" />


# Result
          
