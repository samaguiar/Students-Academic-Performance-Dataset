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
<div>
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
      <th>107</th>
      <td>M</td>
      <td>KW</td>
      <td>KuwaIT</td>
      <td>lowerlevel</td>
      <td>G-02</td>
      <td>B</td>
      <td>IT</td>
      <td>F</td>
      <td>Father</td>
      <td>70</td>
      <td>90</td>
      <td>41</td>
      <td>33</td>
      <td>Yes</td>
      <td>Bad</td>
      <td>Under-7</td>
      <td>H</td>
    </tr>
    <tr>
      <th>68</th>
      <td>F</td>
      <td>USA</td>
      <td>USA</td>
      <td>HighSchool</td>
      <td>G-12</td>
      <td>A</td>
      <td>IT</td>
      <td>F</td>
      <td>Mum</td>
      <td>70</td>
      <td>69</td>
      <td>35</td>
      <td>30</td>
      <td>Yes</td>
      <td>Good</td>
      <td>Under-7</td>
      <td>H</td>
    </tr>
    <tr>
      <th>74</th>
      <td>M</td>
      <td>KW</td>
      <td>KuwaIT</td>
      <td>MiddleSchool</td>
      <td>G-07</td>
      <td>B</td>
      <td>IT</td>
      <td>F</td>
      <td>Father</td>
      <td>12</td>
      <td>0</td>
      <td>6</td>
      <td>13</td>
      <td>No</td>
      <td>Bad</td>
      <td>Under-7</td>
      <td>L</td>
    </tr>
    <tr>
      <th>474</th>
      <td>F</td>
      <td>Jordan</td>
      <td>Jordan</td>
      <td>MiddleSchool</td>
      <td>G-08</td>
      <td>A</td>
      <td>Chemistry</td>
      <td>F</td>
      <td>Father</td>
      <td>2</td>
      <td>7</td>
      <td>4</td>
      <td>8</td>
      <td>No</td>
      <td>Bad</td>
      <td>Above-7</td>
      <td>L</td>
    </tr>
    <tr>
      <th>21</th>
      <td>F</td>
      <td>KW</td>
      <td>KuwaIT</td>
      <td>MiddleSchool</td>
      <td>G-07</td>
      <td>B</td>
      <td>IT</td>
      <td>F</td>
      <td>Father</td>
      <td>10</td>
      <td>12</td>
      <td>4</td>
      <td>80</td>
      <td>No</td>
      <td>Bad</td>
      <td>Under-7</td>
      <td>M</td>
    </tr>
    <tr>
      <th>298</th>
      <td>M</td>
      <td>Jordan</td>
      <td>Jordan</td>
      <td>lowerlevel</td>
      <td>G-04</td>
      <td>A</td>
      <td>Science</td>
      <td>F</td>
      <td>Father</td>
      <td>18</td>
      <td>17</td>
      <td>26</td>
      <td>34</td>
      <td>No</td>
      <td>Good</td>
      <td>Above-7</td>
      <td>M</td>
    </tr>
    <tr>
      <th>71</th>
      <td>M</td>
      <td>KW</td>
      <td>KuwaIT</td>
      <td>MiddleSchool</td>
      <td>G-07</td>
      <td>A</td>
      <td>IT</td>
      <td>F</td>
      <td>Father</td>
      <td>29</td>
      <td>22</td>
      <td>9</td>
      <td>20</td>
      <td>Yes</td>
      <td>Good</td>
      <td>Under-7</td>
      <td>M</td>
    </tr>
    <tr>
      <th>266</th>
      <td>M</td>
      <td>Jordan</td>
      <td>Jordan</td>
      <td>MiddleSchool</td>
      <td>G-06</td>
      <td>A</td>
      <td>English</td>
      <td>F</td>
      <td>Father</td>
      <td>19</td>
      <td>80</td>
      <td>12</td>
      <td>17</td>
      <td>Yes</td>
      <td>Good</td>
      <td>Above-7</td>
      <td>M</td>
    </tr>
    <tr>
      <th>419</th>
      <td>M</td>
      <td>Palestine</td>
      <td>Jordan</td>
      <td>MiddleSchool</td>
      <td>G-07</td>
      <td>B</td>
      <td>Biology</td>
      <td>S</td>
      <td>Father</td>
      <td>99</td>
      <td>96</td>
      <td>89</td>
      <td>84</td>
      <td>Yes</td>
      <td>Good</td>
      <td>Under-7</td>
      <td>H</td>
    </tr>
    <tr>
      <th>73</th>
      <td>F</td>
      <td>KW</td>
      <td>KuwaIT</td>
      <td>MiddleSchool</td>
      <td>G-07</td>
      <td>A</td>
      <td>English</td>
      <td>F</td>
      <td>Father</td>
      <td>19</td>
      <td>30</td>
      <td>26</td>
      <td>19</td>
      <td>Yes</td>
      <td>Bad</td>
      <td>Above-7</td>
      <td>M</td>
    </tr>
  </tbody>
</table>
</div>

### Analysis
#### Nominal Data
According to Petty, nominal data is entries that can be organized into categories, without the need of a specific order (Petty, 2011). In this data set, I have chosen the attribute Topic as my nominal data, as it does not have a specific order to the categorical data. 
I began my investigate by exploring the data with the following code to get a brief overview of what I was working with:
```
# look at classes - explore nominal data 
df['Topic'].describe()
```
```
count     480
unique     12
top        IT
freq       95
Name: Topic, dtype: object
```

This showed me the mode, or most common course, was IT with 95 entries in this attribute. I then created a frequency table to see the breakdown of each class:
```
topic_counts_df = df['Topic'].value_counts().reset_index()
topic_counts_df
```

This showed me that IT was the most popular course and History was the least popular course. It also showed me that Chemistry and Geology had the same popularity. Next, I wanted to understand the percentage of students taking each class. To do this, I created a for loop that would determine the percentage of each course from the total and add to an empty list. I then created a new column in the frequency table called “Percentage”. Here is my code:
```
percentages = []
for c in topic_counts_df['count']:
    percent = round((c/df['Topic'].count())*100, 2)
    percentages.append(percent)
topic_counts_df['Percentage']=percentages
topic_counts_df
```

Now, the frequency table effectively communicates the percentage of the total. This also allows me to create different graphical representations, like a pie chart and pareto chart, to visualize the trends (Favero & Belfiore, 2019). First, I created a pie chart using the following code:
```
plt.pie(topic_counts_df['count'], autopct='%1.1f%%', textprops={'fontsize': 8})
plt.legend(labels=topic_counts_df['Topic'], title='Categories', loc='center left', bbox_to_anchor=(1, 0.5))
```

However, I noticed that there were categories sharing the same color, IT and Math, as well as French and History. To ensure the reader would be able to correctly identify the courses and their corresponding percentages without the frequency table, I updated the code to the following:
```
colors = ["blue", "orange", "green", "red", "purple", "brown", "pink", "grey", "yellow", "tan", "#ADD8E6", "#90EE90"]
```
```
plt.pie(topic_counts_df['count'], autopct='%1.1f%%', textprops={'fontsize': 8}, colors=colors)
plt.legend(labels=topic_counts_df['Topic'], title='Categories', loc='center left', bbox_to_anchor=(1, 0.5))
```

This pie chart better communicates the percentage of each class from the total. 
#### Ordinal Data
Similar to nominal data, ordinal data is categorical. However, ordinal data has a specific order, or ranking, to the categories (Petty, 2011). Because of this, I have chosen GradeID as my ordinal attribute, as students must progress through lower levels to reach high school level courses. 
I began my investigation by exploring the data with the following code:
```
# explore ordinal data
df['GradeID'].describe()


count      480
unique      10
top       G-02
freq       147
Name: GradeID, dtype: object
```
This output tells me that the most common grade level is 2nd Grade and it appears 147 times out of the 480 entries. There are also 10 unique grades. This required additional investigation as I did not know the starting and ending grade levels of the data set nor the frequency of the other grades.
So, I used the following code to create a frequency table:
```
df['GradeID'].value_counts().reset_index()
```

Here I noticed that the most frequent grade level was 2nd grade and the least frequent grade level was 5th grade. I also noticed that 3rd grade was not included and the grade levels stopped at 12th grade.
Next, I decided to clean the grade level labels to make them more readable to the common eye. I did by first creating a for loop that would loop through the numbers 2 to 12 to rename each GradeID as “Grade #”:
```
# Rename "G_0{i}" to "Grade {i}" or G-{i} to Grade {i}
for i in range(2,13):
#if the grade level is one digit
    if i<10:
        old_val = f'G-0{i}'
#if the grade level is more than one digit but less than 13
    else:
        old_val = f'G-{i}'
    new_val = f'Grade {i}'
    df['GradeID'] = df['GradeID'].replace(old_val, new_val)
```

Next, I recreated the frequency table:
```
grade_counts = df['GradeID'].value_counts().reset_index(
grade_counts
```

Lastly, I then wanted to showcase the frequency of the data in a bar graph. To do this, I had to make sure I created a custom order of the grade levels to ensure the hierarchy was clearly stated. I created an empty list. Next, I created another for loop that iterates through 2 to 12, and at each iteration, the grade level was added to the empty list. The code I used is below:
```
# Define the custom order for the x-axis
custom_order = []

for i in range(2,13):
    new_grade = f'Grade {i}'
    custom_order.append(new_grade)

custom_order
```
```
['Grade 2',
 'Grade 3',
 'Grade 4',
 'Grade 5',
 'Grade 6',
 'Grade 7',
 'Grade 8',
 'Grade 9',
 'Grade 10',
 'Grade 11',
 'Grade 12']
```

Lastly, I used the following code to create the bar graph and title, as well as label the x- and y-axis:
```
# Create a bar plot with the custom order
plt.figure(figsize=(8, 6)) 
sns.barplot(x='GradeID', y='count', data=grade_counts_df, order=custom_order)
plt.xlabel('Grade Level')
plt.ylabel('Frequency')
plt.title('Frequency vs. Grade Level')
plt.xticks(rotation=45)
```


#### Ratio Data
I chose the attribute raisedhands as my ratio data.  raisedhands represents the amount of times a student chose to raise their hand to answer a question in class. This is classified as ratio data because there is a zero point to this attribute. For example, a student could choose not to participate, and therefore, not raise their hands. Because the absence of the action leads to zero, this is classified as a ratio data over interval data (Favero & Belfiore, 2019). 
Because  raisedhands is a quantitative variable, I can calculate a statistical summary. I used the following code:
```
# get statistics for interval data
df['raisedhands'].describe()
```
```
count    480.000000
mean      46.775000
std       30.779223
min        0.000000
25%       15.750000
50%       50.000000
75%       75.000000
max      100.000000
Name: raisedhands, dtype: float64
```

This output shows the average number of handraises was 46.78 times with a standard deviation of 30.78. The mean gives me an idea of the typical level of participation in the class over the semester. The standard deviation indicates there is some variability to the number of times students raised their hands in class. In this case, students could have significantly raised their hands more than the average, or less than the average. The quartiles break the data into four equal parts, providing information on the distribution (Favero & Belfiore, 2019) The first quartile has a value of 15.75. This means that 25% of students raise their hands about 16 times per semester. On the other hand, the third quartile suggests that 75% of students raise their hand about 75 times per semester. This suggests that the majority of students are participating quite frequently in class.
Next, I calculated the mode using the following code to determine the most common amount of hands raised by students:
```
st.mode(df['raisedhands'])
```
```
10
```
The output shows the mode of the attribute is 10. This means students most frequently raised their hands 10 times during the semester. I also noticed that the average number of handraises was 46.78, while the median number of handraises was 50. This indicated that the data might have a slight right skew in the distribution (Bruce & Bruce, 2020). To investigate the skewness and variability, I created a histogram using the following code to help me visualize the distribution:
```
# Create a histogram for interval data
plt.hist(df['raisedhands'], bins=10, color='skyblue', edgecolor='black')
plt.xlabel('Number of Raised Hands')
plt.ylabel('Frequency')
plt.title('Engagement: Frequency vs. Number of Raised Hands')
```

This histogram shows that there is a slight tendency for more of the data to be on the left, which corresponds with the statistics showing the mean is less than the median (Bruce & Bruce, 2020). This means that there are more students who are participating less than 50% of the time. However, I believe this histogram shows a bimodal distribution more clearly than the right skewed that was suggested by the relationship to the mean. This most likely means that students tend to either have low participation or high participation, with few participating about 50% of the time. There are likely other factors that are contributing to the amount of times students are raising their hands. Looking into additional contributing factors could shed more light on why the distribution is bimodal.

#### Conclusion
The type of data is very important in determining the analysis you can perform. Nominal and ordinal data are qualitative. This type of data cannot have statistics produced, aside from the mode, to generalize any trends seen. As a result, frequency tables and graphical representations, like bar charts, pie charts, and Pareto charts, are used to highlight the frequency of occurrence of each category. Interval and ratio data, on the other hand, is quantitative, so statistical analysis can be performed. In this analysis, generalizations can be made from statistics like mean, median, quartiles, and types of variance. This then can lead to creating different visualizations, like histograms, line plot, and scatterplot, to investigate trends or relationships in the data set (Favero & Belfiore, 2019). Quantitative data also lends itself to creating models, like linear regression, to help predict future values (Bruce & Bruce, 2020). 

### References
Aljarah, I. (2016, November 26). Students’ academic performance dataset. Kaggle. https://www.kaggle.com/datasets/aljarah/xAPI-Edu-Data?rvi=1 
Bruce, P., Bruce, A., & Gedeck, P. (2020). Practical Statistics for Data Scientists (2nd ed.). O'Reilly Media, Inc.. https://reader2.yuzu.com/books/9781492072898
Favero, L. P., & Belfiore, P. (2019). Data Science for Business and Decision Making. Elsevier S & T. https://reader2.yuzu.com/books/9780128112175
Petty, N. (2011, December 13). Types of data: Nominal, ordinal, Interval/Ratio - statistics help. YouTube. https://www.youtube.com/watch?v=hZxnzfnt5v8&embeds_referring_euri=https%3A%2F%2Fucumberlands.blackboard.com%2F&source_ve_path=MzY4NDIsMjg2NjY&feature=emb_logo&themeRefresh=1 
