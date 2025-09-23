# Programming Assignment 4
## Data Wrangling and Data Visualization

### Description:
The goal of this repository is to be able to showcase the process of data wrangling and data visualization

### Intended Learning Outcomes:
1. To identify the codes and functions needed in cleaning and visualizing data
2. To be able to apply and use the different codes and functions in creating a Python program that will
be used in data wrangling and data visualization

###  **Problems**
### ECE BOARD EXAM PROBLEM:
This program creates uses data wrangling and data visualization techniqe with storytelling.

#### Creation of the data frames based on the format provided:
Example:  Vis = [“Name”, “Gender”, “Track”, “Math<70”]; hometown is constant as Visayas
**Sample Output:**
<img width="748" height="129" alt="image" src="https://github.com/user-attachments/assets/3522852d-f4b9-45ee-930a-2c3bf77bc3e7" />

**Implementation:**

```
import pandas as pd
```
- Since the problem uses data frames, we need to access pandas library


```
df = pd.read_excel("board2.xlsx")  
df
```
- Load the Excel dataset "board2.xlsx" into a DataFrame called df
- It will then display the contents of the DataFrame

  
**a. Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as
Instrumentation and hometown Luzon**
```
Instru = df.loc[df['Electronics']>70, ['Name','GEAS','Electronics']]
```
-  It creates a data frame based on the Format given.
-  The data frame is called Instru in which it filters rows where grades in Electronics are greater than 70 and it showcases the Name,GEAS, and Electronics
```
Instru['Track'] = 'Instrumentation'
```
- This adds a column where it will show track as Instrumentation
```
Instru['Hometown'] = 'Luzon'
```
- It adds another column Hometown with the constant value Luzon.
```
Instru
```
- Display the Instru DataFrame

<br><br>
**b. Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is
constant as Mindanao and gender Female**
```
df['Average'] = df[['Math','Electronics','GEAS','Communication']].mean(axis = 1)
```
- Average is calculated for the four subjects.
- Axis 1 is used to get the average (row-wise)
```
Mindy = df.loc[df['Average'] >= 55, ['Name','Track','Electronics']]
```
- Create a data frame based on the Format given.
- Data frame is called Mindy in which it filters rows where the average is greater than or equal  to 55
- Showcases the Name,Track, and Electronics columns

```
Mindy['Hometown'] = 'Mindanao'
```
- Add column where it will set hometown as Mindanao

```
Mindy['Gender'] = 'Female'
```
- Add column where it will set gender as Female

```
Mindy
```
- Print Mindy DataFrame

<br><br>
#### Creation of a visualization that shows how the different features contributes to average grade. 
Does chosen track in college, gender, or hometown contributes to a higher average score
```
import matplotlib.pyplot as plt
```
- Import libraries for data visualization
```
df['Average'] = df[['Math','Electronics','GEAS','Communication']].mean(axis=1)
```
- Compute first the average of each row or per student for 4 subjects
<br>


**How does chosen track in college contributes to average grade**
```
ave_by_track = df.groupby('Track')['Average'].mean()
```
- Group the data by Track and Calaculate the average score per track
```
fig, ax = plt.subplots()
```
- Create a figure (fig) and a single set of axes (ax) for plotting
```
ax.bar(ave_by_track.index, ave_by_track.values)
```
- Plot a bar chart showing the average score for each track
```
ax.set(title='Average by Track', ylabel='Average', xlabel='Track in College')
```
- Set the title and axis labels
```
plt.show()
```
- Show the plot


**Output:**
- <img width="630" height="507" alt="image" src="https://github.com/user-attachments/assets/aa9afb14-e08a-407a-af83-97ad2f96c29a" />
- Based on the graph, the chosen track in college contributes to higher average scores, with the Communication track obtaining the highest average, closely followed by Microelectronics, while Instrumentation recorded the lowest average.


**How does gender contributes to average grade**
```
ave_by_gender = df.groupby('Gender')['Average'].mean()
```
- Group the data by Gender and Calaculate the average score per Gender
```
fig, ax = plt.subplots()
```
- Create a figure (fig) and a single set of axes (ax) for plotting
```
ax.bar(ave_by_gender.index, ave_by_gender.values)
```
- Plot a bar chart showing the average score for each gender
```
ax.set(title='Average by Gender', ylabel='Average', xlabel='Gender')
```
- Set the title and axis labels
```
plt.show()
```
- Show the plot



**Output:**
- <img width="624" height="501" alt="image" src="https://github.com/user-attachments/assets/0144d202-67a9-4f33-b8c3-a39a4aa2ffc9" />
- Based on the graph, gender contributes to higher average scores, with male students obtaining slightly higher average than female students.

<br>

**How does hometown contributes to average grade**
```
ave_by_hometown = df.groupby('Hometown')['Average'].mean()
```
- Group the data by Hometown and Calaculate the average score per hometown
```
fig, ax = plt.subplots()
```
- Create a figure (fig) and a single set of axes (ax) for plotting
```
ax.bar(ave_by_hometown.index, ave_by_hometown.values)
```
- Plot a bar chart showing the average score for each hometown
```
ax.set(title='Average by Hometown', ylabel='Average', xlabel='Hometown')
```
- Set the title and axis labels
```
plt.show()
```
- Show the plot



**Output:**
- <img width="626" height="508" alt="image" src="https://github.com/user-attachments/assets/42f49b73-bb2c-4317-bb6d-2c57b6bd286f" />
- Based on the graph, hometown contributes to higher average scores, with Luzon obtaining the highest average, followed by Mindanao, while Visayas recorded the lowest average.




