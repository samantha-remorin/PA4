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
fig, ave_by_track = plt.subplots()
```
- Create a figure (fig) and a single set of axes (ave_by_track) for plotting

```
ave_by_track.bar(df['Track'], df['Average'])
```
- Plot a bar chart on the axes, using 'Track' as categories (x-axis)
- and 'Average' as the corresponding bar heights (y-axis)

```
ave_by_track.set(title= 'Average by Track', ylabel='Average', xlabel='Track in College')
```
- Set the title and axis labels

```
plt.show()
```
- Show the plot


<br>

**How does gender contributes to average grade**
```
fig, ave_by_gender = plt.subplots()
```
- Create a figure (fig) and a single set of axes (gender) for plotting

```
ave_by_gender.bar(df['Gender'], df['Average'])
```
- Plot a bar chart on the axes, using 'Gender' as categories (x-axis)
- and 'Average' as the corresponding bar heights (y-axis)

```
ave_by_gender.set(title= 'Average by Gender', ylabel='Average', xlabel='Gender')
```
- Set the title and axis labels

```
plt.show()
```
- Show the plot

<br>

**How does hometown contributes to average grade**
```
fig, ave_by_hometown = plt.subplots()
```
- Create a figure (fig) and a single set of axes (ave_by_hometown) for plotting

```
ave_by_hometown.bar(df['Track'], df['Average'])
```
- Plot a bar chart on the axes, using 'Hometown' as categories (x-axis)
- and 'Average' as the corresponding bar heights (y-axis)

```
ave_by_hometown.set(title= 'Average by Track', ylabel='Average', xlabel='Track in College')
```
- Set the title and axis labels

```
plt.show()
```
- Show the plot




