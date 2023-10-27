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