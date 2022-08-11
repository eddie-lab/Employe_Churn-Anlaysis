# Reason_for_Resignation_Analysis

This project aims at cleaning and analyzing Employee Exit Survey responses from employees of Department of Education, Training and Employment (DETE), and the Technical and Further Education (TAFE) body of the Queensland government in Australia.

Specifically, I looked to gain answers to the following questions:

   Are employees who only worked for the institutes for a short period of time resigning due to some kind of dissatisfaction? What about employees who have been there longer?
   
   Are younger employees resigning due to some kind of dissatisfaction? What about older employees?

i had to combine the two datasets containing results for both surveys to answer the above questions. However, although both used the same survey template, one of them customized some of the answers - something that introduced some complications into my work.


# Data Cleaning

 *    Unnecessary columns for our goals were dropped.
 *   Column names were standardized as much as possible across both columns, to facilitate table merging. In particular:
       *  Capitalization was made lowercase
        * Spaces were replaced with underscores
        * Trailing whitespace from the ends of the strings were removed
  *   Reduced dataframes to include only employees who resigned, and not those who left because they found jobs elsewhere, or retired because of age.
 *    Created a new column that calculates an employee's duration of employment, by calculating the difference between their resignation date and hire           date, using the datetime library.
  *   Identified columns that corresponded to employee dissatisfaction, and more explicitly outlined employee dissatisfaction by creating a new column           that indicated dissatisfaction using Boolean values of True or False, or NaN in the case of
       *  Columns with very large numbers of missing values (> 500) were dropped.
  *  After Merging, it was noticed that institute_service column contained data in inconsistent formats, such as "11-20", and "More than 20 years".            Regular expressions were used to standardize this column into digits, and then the digits were categorized into 4 categories of work experience:
       *  New: Less than 3 years at a company
       *  Experienced: 3-6 years at a company
       *  Established: 7-10 years at a company
       *  Veteran: 11 or more years at a company
   *  Another column was created to reflect this category.
   *  Missing values in the dissatisfied column were filled with False, since that was the most frequent value in that column.

