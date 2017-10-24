---
title: Getting Data Into SPSS and R
author: William Murrah
date: '2017-10-22'
slug: getting-data-into-spss-and-r
categories: []
tags: []
header:
  caption: ''
  image: ''
---

The first step in analyzing data is often getting the data into your chosen software.
In this tutorial, I demonstrate how to manually enter data into SPSS and R as well as how to import existing date from two common formats.

## Manually Entering Data 

Let's assume you had the following data on five students grades you wanted to enter into SPSS and R. You have 5 cases, in this example students, and two variables, the student's name and their grade.

Student | Grade
--------|-----
Bob     | 95
Sarah   | 98
Mary    | 80
Frank   | 82
Pat     | 78

### SPSS

In SPSS you can enter data the same way you would for many spreadsheet programs (e. g. Excel, Googlesheets). 
But before you do that you will want to enter information about the two variables.
Click on the variable tab in the lower left corner of the SPSS Data Editor.
Then enter the information about each variable.
Name the variable, select the appropriate variable type, label the variable so it is clear what information is captured by each variable, and select the appropriate scale of measurement.

![](static/img/spss/manualVar.jpg)
![](static/img/spss/manualVar2.jpg)

With your variables defined, you are ready to enter the data.
Click the data view in the bottom left corner of SPSS and enter the data in the empty cells. 
The rows represent different cases, and the columns diffeent variables.
Enter the values as below:

![](static/img/spss/manualData.png)
You can also enter data manually using SPSS syntax.

```
data list list
/ Name Grade.
begin data 
1   95
2   98
3   80
4   82
5   78
end data.

value labels 
Name
1 'Bob'
2 'Sarah'
3 'Mary'
4 'Frank'
5 'Pat'.

variable labels
Name "Student names"
Grade "Student grade".

variable level
Name (Nominal)
Grade (scale).
```

Notice that the `Name` variable was entered as unique numbers and then labelled with the names using the `VALUE LABELS` command. 
This is not the only way to do this, but makes the most sense to me.
Note I also labels the variables and set the measurement scale using syntax.
See the *SPSS Command Syntax Reference* manual accessible in the help menu for more details about these and other commands.

### R

To manually enter the data into R you want to create a dataframe.
You can do this with the following code:


```r
student_grades <- data.frame(
  name = c("Bob", "Sarah", "Mary", "Frank", "Pat"),
  grade = c(95, 98, 80, 82, 78)
)
```

This creates an object named `df` that contains the two varibles and related data.

You can view the data frame by typing the name of the object into R as you see below followed by the resulting output.


```r
student_grades
```

```
   name grade
1   Bob    95
2 Sarah    98
3  Mary    80
4 Frank    82
5   Pat    78
```


## Importing Data

### SPSS

To import a file into SPSS click the folder icon in the upper left corner, navigate to the folder that contains the csv file, then change the *Files of type* menu to look for the type of file you are importing (.csv). 

![image1](/img/spss/importcsv1.jpg)
Then select the file you wish to open and click **Open**.
![](/img/spss/importcsv2.jpg)
This will open a dialog box with 6 steps. 

**Step 1.** If you are not using a predefined format click next.

![](/img/spss/importcsv3.jpg)

**Step 2.** Make sure thet **Yes** is selected if there are variable names included in the top of the csv, and select **No** otherwise.
In this example you can see in the preview in the bottom of the dialog box that the variable names "height" and "gender" are included.

![](/img/spss/importcsv4.jpg)

**Step 3.** You can click next on step 3 most of the time.

 
**Step 4.** Make sure only the appropriate delimiters are selected on step 4 (here only Comma as this is a csv). Sometimes Space will also be selected and must be unselected to import the data correctly.

![](/img/spss/importcsv5.jpg)


**Step 5.** Click next on step 5 unless you which to change the variable names.

**Step 6.** Finally look over the preview to ensure everything looks okay, an click **Finish**. 
Your data should now be properly imported into SPSS.

### R

To import a csv file into R, use the `read.csv` function as follows:


```r
height <- read.csv(file = "height.csv", header = TRUE)
```

Note that you will need to include the file path to the file name in the file argument if it is not in the current directory. 
The header argument is set to TRUE if the variable names are in the first row of the csv, and FALSE if not.

