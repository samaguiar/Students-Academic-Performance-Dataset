# Students-Academic-Performance-Dataset

### The Data
The data was obtain from Kaggle (https://www.kaggle.com/datasets/aljarah/xAPI-Edu-Data/data). This analysis was created for the course MSDS 530 at University of Cumberland.

### Setting up the Data
I retrieved the dataset, Students' Academic Performance Database, from Kaggle. This dataset contains16 different attributes, representing both qualitative and quantitative variables (Aljarah, 2016). 
I first began by loading the needed packages and the csv file containing the data  into Juypter Notebooks as follows: 
```
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```
```
# use pandas to read the csv dataset
df = pd.read_csv('/Users/samaguiar/Desktop/university-of-the-cumberlands/MSDS_530/week_1/xAPI-Edu-Data.csv')
```
After storing the data frame as a variable, I began to explore and clean the data. First, I looked a the first five values in the data set to get an idea of the attributes and values:
```
df.head()
```
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>gender</th>
      <th>NationalITy</th>
      <th>PlaceofBirth</th>
      <th>StageID</th>
      <th>GradeID</th>
      <th>SectionID</th>
      <th>Topic</th>
      <th>Semester</th>
      <th>Relation</th>
      <th>raisedhands</th>
      <th>VisITedResources</th>
      <th>AnnouncementsView</th>
      <th>Discussion</th>
      <th>ParentAnsweringSurvey</th>
      <th>ParentschoolSatisfaction</th>
      <th>StudentAbsenceDays</th>
      <th>Class</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>M</td>
      <td>KW</td>
      <td>KuwaIT</td>
      <td>lowerlevel</td>
      <td>G-04</td>
      <td>A</td>
      <td>IT</td>
      <td>F</td>
      <td>Father</td>
      <td>15</td>
      <td>16</td>
      <td>2</td>
      <td>20</td>
      <td>Yes</td>
      <td>Good</td>
      <td>Under-7</td>
      <td>M</td>
    </tr>
    <tr>
      <th>1</th>
      <td>M</td>
      <td>KW</td>
      <td>KuwaIT</td>
      <td>lowerlevel</td>
      <td>G-04</td>
      <td>A</td>
      <td>IT</td>
      <td>F</td>
      <td>Father</td>
      <td>20</td>
      <td>20</td>
      <td>3</td>
      <td>25</td>
      <td>Yes</td>
      <td>Good</td>
      <td>Under-7</td>
      <td>M</td>
    </tr>
    <tr>
      <th>2</th>
      <td>M</td>
      <td>KW</td>
      <td>KuwaIT</td>
      <td>lowerlevel</td>
      <td>G-04</td>
      <td>A</td>
      <td>IT</td>
      <td>F</td>
      <td>Father</td>
      <td>10</td>
      <td>7</td>
      <td>0</td>
      <td>30</td>
      <td>No</td>
      <td>Bad</td>
      <td>Above-7</td>
      <td>L</td>
    </tr>
    <tr>
      <th>3</th>
      <td>M</td>
      <td>KW</td>
      <td>KuwaIT</td>
      <td>lowerlevel</td>
      <td>G-04</td>
      <td>A</td>
      <td>IT</td>
      <td>F</td>
      <td>Father</td>
      <td>30</td>
      <td>25</td>
      <td>5</td>
      <td>35</td>
      <td>No</td>
      <td>Bad</td>
      <td>Above-7</td>
      <td>L</td>
    </tr>
    <tr>
      <th>4</th>
      <td>M</td>
      <td>KW</td>
      <td>KuwaIT</td>
      <td>lowerlevel</td>
      <td>G-04</td>
      <td>A</td>
      <td>IT</td>
      <td>F</td>
      <td>Father</td>
      <td>40</td>
      <td>50</td>
      <td>12</td>
      <td>50</td>
      <td>No</td>
      <td>Bad</td>
      <td>Above-7</td>
      <td>M</td>
    </tr>
  </tbody>
</table>
</div>
The table above is the partial output of df.head(). I investigated the attributes GradeID, Topic, and raisedhands. 
Next, I wanted to ensure that I did not have any missing values in my data set that could skew results. I used the following code:
```
df.isnull().value_counts()
```
```
gender  NationalITy  PlaceofBirth  StageID  GradeID  SectionID  Topic 
False   False        False         False    False    False      False  
Semester  Relation  raisedhands  VisITedResources  AnnouncementsView  
False       False     False        False             False              
Discussion  ParentAnsweringSurvey  ParentschoolSatisfaction  
False              False                     False
StudentAbsenceDays  Class
False               False         
480
Name: count, dtype: int64
```

This output told me that there were no missing values in each attribute. Next, I determine the type of the attributes that I selected using the following code: 
```
df['raisedhands'].dtypes
```
```
dtype('int64')
```
This output told me that the attribute raisedhands was a quantitative variable. On the other hand, both GradeID and Topic were qualitative variables as shown below with an output of dtype('0'):
```
df['GradeID'].dtypes
```
```
dtype('0')
```
```
df['Topic'].dtypes
```
```
dtype('0')
```
Further investigation on GradeID and Topic showed that GradeID had a specific hierarchy, or order, to the entries, while Topic was classified into different topics of classes, like mathematics or science, as seen below:
```
#get 10 random samples
df.sample(10)
```
Again, the output was cut to focus on the attributes that were chosen to investigate.

### Analysis

### References
