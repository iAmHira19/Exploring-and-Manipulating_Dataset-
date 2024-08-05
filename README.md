# Exploring-and-Manipulating_Dataset-
Exploring and Manipulating the Titanic Dataset in Google Colab

Exploring and Manipulating the Titanic Dataset in Google Colab
Objective: To demonstrate the process of exploring and manipulating the Titanic dataset using Google Colab.

Steps and Description
Step 1: Install Kaggle API and Download the Dataset
python
Copy code
# Install Kaggle API
!pip install kaggle

# Upload kaggle.json (you need to upload the file manually to Colab)
import os
os.makedirs('/root/.kaggle', exist_ok=True)
!mv kaggle.json /root/.kaggle/
!chmod 600 /root/.kaggle/kaggle.json

# Download the Titanic dataset
!kaggle competitions download -c titanic -f train.csv
!unzip train.csv.zip
Step 2: Load the Dataset
python
Copy code
import pandas as pd

# Load the dataset
df = pd.read_csv('train.csv')
print("Initial DataFrame:")
print(df.head())
Step 3: Exploring the Dataset
Basic Information:

python
Copy code
# Display basic information about the dataset
print("\nBasic Information:")
print(df.info())
Summary Statistics:

python
Copy code
# Display summary statistics
print("\nSummary Statistics:")
print(df.describe())
Checking for Missing Values:

python
Copy code
# Check for missing values
print("\nMissing Values:")
print(df.isnull().sum())
Unique Values in Each Column:

python
Copy code
# Display unique values in each column
for column in df.columns:
    print(f"\nUnique values in {column}:")
    print(df[column].unique())
Step 4: Manipulating the Dataset
Filtering Data:

python
Copy code
# Filter passengers who survived
survived = df[df['Survived'] == 1]
print("\nPassengers who survived:")
print(survived.head())

# Filter passengers who did not survive
not_survived = df[df['Survived'] == 0]
print("\nPassengers who did not survive:")
print(not_survived.head())
Sorting Data:

python
Copy code
# Sort by Age
sorted_by_age = df.sort_values(by='Age')
print("\nDataFrame sorted by Age:")
print(sorted_by_age.head())
Creating New Columns:

python
Copy code
# Create a new column 'FamilySize' as the sum of 'SibSp' and 'Parch' plus one (for the passenger themselves)
df['FamilySize'] = df['SibSp'] + df['Parch'] + 1
print("\nDataFrame with 'FamilySize' column:")
print(df.head())
Grouping Data:

python
Copy code
# Group by 'Pclass' and calculate the mean age
mean_age_by_pclass = df.groupby('Pclass')['Age'].mean()
print("\nMean Age by Pclass:")
print(mean_age_by_pclass)
Aggregating Data:

python
Copy code
# Aggregate data to get the mean 'Fare' and 'Age' for each 'Pclass'
aggregate_data = df.groupby('Pclass').agg({'Fare': 'mean', 'Age': 'mean'})
print("\nAggregated data (mean 'Fare' and 'Age' by 'Pclass'):")
print(aggregate_data)
