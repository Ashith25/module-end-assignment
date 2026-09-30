# ASSIGNMENT 3
## Healthcare Data Analysis and Insight Solutions

# DATA CLEANING
1. Check for the number of missing values marked with '?' in each column of the “Medical
  Examinations” Table and "Hospitalization Details" Table.
   * The number of missing values was found using a povit table and *COUNTIF* function syntax **=COUNTIF(table1[customer id],"?")**
2) Fill in the missing values of ‘month’ with Sep and ‘year’ with its average rounded to the
nearest integer.
   * missing values of month replace with sep- syntax **=IF(C2="?","sep",[@month])**
   * missing value of year replace with Average of year syntax **=IF([@year]="?","1983",[@year])**
 3) Determine the most frequently occurring values in the ‘smoker’, 'Hospital tier' and 'City
tier' columns, and fill in the missing values accordingly.
    * The most frequently occurring values were found using a PivotTable.
     Smoker syntax **=IF([@smoker2]="?","no",[@smoker2])**
    * Hospital tier syntax **=IF([@[Hospital tier]]="?","tier - 2",[@[Hospital tier]])**
    * City tier syntax **=IF([@[City tier]]="?","tier - 2",[@[City tier]])**
  4) If any 'State ID' values are missing, consider filling them with 'Unknown' or using another
appropriate strategy.
     * **Replaced with Find and Replace**
  # Data Transformation 
   1) Split the ‘names’ column in the “Customer Names” Table into 3 meaningful columns:
‘Title’, ‘First Name’, and ‘Last Name’.
        * **Names were split using Text to Columns**
   2) Convert the "NumberOfMajorSurgeries" column in the “Medical Examinations” Table to
numerical data by replacing non-numeric characters with meaningful numerical values.
      * **Replaced with Find and Replace**
   3) Check for inconsistencies in the 'Heart Issues' and 'smoker' columns and propose
corrective actions if necessary.

        Inconsistencies were corrected using the UPPER function 
       * Syntax **=UPPER(Table1[@Smoker2])**
       * Syntax **=UPPER(Table1[@Heart issue])**
 4) Create a new column named “Weight Status” that categorizes BMI into different
categories as below;
       * BMI was categorized into different weight statuses using the IF function. 
Syntax   **=IF(Table1[@BMI]<18.5,"Under Weight",IF(Table1[@BMI]<24.9,"Normal Weight",IF(Table1[@BMI]<29.9,"Overweight","Obesity")))**
5) Create a new column named “Diabetes Status” and fill it as per the information given;
   * HBA1C was categorized into different diabetic statuses using “IF” function 
Syntax **=IF(Table1[@HBA1C]<5.7,"Normal",IF(Table1[@HBA1C]<6.4,"Prediabetes","Diabetes"))**
6) Merge ‘year’, ‘month’ and ‘date’ columns in the “Hospitalization Details” Table into one
column named ‘Date of Birth’ and format it in ‘DD-MMM-YYYY’ custom format.
    * Merged by using CONCATENATE function 
Syntax  **=CONCATENATE([@date],"-",[@Month2],"-",[@Year2])**
7) Calculate the ‘Age’ of each customer based on their ‘Date of Birth’ and the date of
collection of the dataset, which is 8th June 2023.
     * Age was calculated using the DATEDIF function. 
Syntax **=DATEDIF([@[Date of Birth]],DATE(2023,6,8),"Y")**
 8) Format ‘charges’ column as currency ($).
      * Charges column format changed  to currency
 # Data Exploration, Analysis & Visualization:
 ➢ Create a new sheet named “Healthcare", combine all three tables into one, using
Customer ID as the common column, utilizing VLOOKUP.

 ➢ Retain the following necessary columns: Customer ID, First Name, BMI, HBA1C, Heart
Issues, Any Transplants, Cancer history, NumberOfMajorSurgeries, smoker, Weight
Status, Diabetes Status, Date of Birth, charges, Hospital tier, City tier, State ID, Age.
* combined table by using VLOOKUP function
Syntax **=VLOOKUP(Table1[[#Headers],[HBA1C]],Table1[[#All],[HBA1C]],1,FALSE)** 
### Create pivot tables if required to do the following analysis, then visualize through charts:
Analysis using Pie/Donut Chart:

 ➢ What is the distribution of cancer history among smokers and non-smokers?
 
 ➢ How does the total number of major surgeries and average HbA1C differ between
patients with and without a history of transplants?
* values where obtained using pivot table and pie chart added
Analysis using Column/Bar Chart:

➢ How do healthcare charges vary based on different weight statuses and diabetes
statuses?

➢ Can you compare the average charges for each hospital tier within different states?
  * values where obtained using pivot table and column chart was added
Analysis using Line/Scatter Plot:

➢ Is there any correlation between age and both BMI and HbA1C in the dataset?

➢ Explore the relationship between age and healthcare charges.

   * values where obtained using a pivot table
# Dashboard Creation:
➢ Build an interactive dashboard that consolidates all key insights using the above
visualizations. Ensure visual clarity and ease of interpretation for all chart types.

  * The dashboard was created with all charts 
      
➢ Add slicers for the fields “Weight Status” and “Diabetes Status” to enable filtering across
all visualizations, supporting comparison of health outcomes and charges based on body
weight and diabetes condition.

  * slicers where added by using pivot analyze - insert slicers
